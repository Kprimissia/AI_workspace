# Guia Técnico: Docker e Containerização de Aplicações

## 1. Visão Geral e Conceitos Fundamentais

O **Docker** empacota aplicações e suas dependências em containers isolados e reprodutíveis, eliminando divergências entre os ambientes de desenvolvimento, homologação e produção.

### Conceitos Essenciais
- **Imagem vs. Container:** A **Imagem** é um pacote imutável em camadas construído a partir de um `Dockerfile`; o **Container** é a instância em execução dessa imagem.
- **Multi-Stage Builds:** Separam o estágio de compilação/build (que contém compiladores, SDKs e `devDependencies`) do estágio final de execução (*runtime*), reduzindo drasticamente o tamanho da imagem e a superfície de ataque.
- **Docker Compose (`compose.yaml`):** Orquestra múltiplos serviços locais (ex.: `frontend`, `backend`, `postgres`), redes isoladas e volumes persistentes de dados.
- **`.dockerignore`:** Impede que pastas pesadas ou sensíveis (`node_modules`, `.git`, `.env`, `target`, `dist`) sejam enviadas para o contexto de build.

---

## 2. Boas Práticas de Segurança e Performance

1. **Fixar Versões das Imagens Base:**
   - Nunca utilize `:latest` (ex.: `node:latest` ou `postgres:latest`). Especifique versões exatas e enxutas, como `node:22-alpine`, `eclipse-temurin:21-jre-alpine`, `python:3.12-slim` ou `postgres:16-alpine`.
2. **Ordenar Camadas para Maximizar o Cache:**
   - Copie primeiro os arquivos de manifesto de dependências (`package.json` + `package-lock.json`, `pom.xml`, `requirements.txt`), instale as dependências e só depois copie o código-fonte (`COPY . .`).
3. **Executar Containers com Usuário Não-Root:**
   - Nunca rode processos de aplicação como `root` dentro do container em produção. Utilize a instrução `USER` (ex.: `USER node` ou um usuário dedicado sem privilégios).
4. **Não Embutir Segredos na Imagem:**
   - Nunca coloque senhas, chaves privadas ou arquivos `.env` de produção dentro de instruções `ENV` ou `COPY` no `Dockerfile`, pois ficam gravados no histórico das camadas da imagem. Injete variáveis em tempo de execução.
5. **Configurar `HEALTHCHECK`:**
   - Permita que o orquestrador saiba se a aplicação dentro do container está realmente pronta para responder requisições, e não apenas com o processo iniciado.

---

## 3. Exemplos Práticos

### 3.1. `Dockerfile` Multi-Stage para Front-end (React + Vite + Nginx)

```dockerfile
# Estágio 1: Build da aplicação
FROM node:22-alpine AS build
WORKDIR /app

COPY package.json package-lock.json ./
RUN npm ci

COPY . .
RUN npm run build

# Estágio 2: Servidor estático leve de produção
FROM nginx:1.27-alpine AS runtime
COPY --from=build /app/dist /usr/share/nginx/html
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
```

### 3.2. `compose.yaml` com Banco de Dados e `healthcheck`

```yaml
services:
  db:
    image: postgres:16-alpine
    environment:
      POSTGRES_DB: ${POSTGRES_DB:-app_db}
      POSTGRES_USER: ${POSTGRES_USER:-app_user}
      POSTGRES_PASSWORD: ${POSTGRES_PASSWORD:?Defina POSTGRES_PASSWORD no .env}
    ports:
      - "5432:5432"
    volumes:
      - pgdata:/var/lib/postgresql/data
    healthcheck:
      test: ["CMD-SHELL", "pg_isready -U $${POSTGRES_USER:-app_user} -d $${POSTGRES_DB:-app_db}"]
      interval: 10s
      timeout: 5s
      retries: 5

volumes:
  pgdata:
```

---

## 4. Erros Comuns e Como Evitá-los

| Erro Comum | Problema | Solução Recomendada |
| :--- | :--- | :--- |
| **Ausência de `.dockerignore`** | O comando `COPY . .` copia `node_modules` local (incompatível com o SO do container) e `.env`, deixando o build lento e inseguro. | Criar `.dockerignore` ignorando `node_modules`, `.git`, `.env*`, `dist`, `coverage`. |
| **Usar `npm install` em vez de `npm ci` no Dockerfile** | Pode instalar versões diferentes das travadas no `package-lock.json`. | Usar `npm ci` para builds determinísticos e reprodutíveis. |
| **Usar `depends_on` simples achando que aguarda o banco ficar pronto** | `depends_on` padrão apenas aguarda o container iniciar, não o SGBD aceitar conexões. | Combinar `healthcheck` no banco com `depends_on: db: condition: service_healthy`. |
| **Executar `docker compose down -v` sem atenção** | A flag `-v` apaga todos os volumes nomeados e destrói os dados do banco local. | Nunca usar `-v` sem autorização explícita e certeza de que os dados podem ser descartados. |

---

## 5. Referências Oficiais

- **Docker Official Documentation:** https://docs.docker.com/
- **Dockerfile Best Practices:** https://docs.docker.com/build/building/best-practices/
- **Docker Compose Specification:** https://docs.docker.com/compose/

