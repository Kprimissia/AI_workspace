# Guia Técnico: Build, Release e Deployment de Aplicações

## 1. Visão Geral e Conceitos Fundamentais

O processo de **Release e Deployment** transforma o código validado em uma versão executável e publicada com segurança no ambiente de destino (`Development`, `Testing`, `Staging` / Homologação ou `Production`).

### Conceitos Essenciais
- **Paridade entre Ambientes (*12-Factor App*):** O código-fonte e o artefato de build devem ser os mesmos; o que muda entre ambientes são exclusivamente as **configurações injetadas por variáveis de ambiente**.
- **Versionamento Semântico (*SemVer — `MAJOR.MINOR.PATCH`*):**
  - `MAJOR`: Alterações incompatíveis de contrato/API (*breaking changes*).
  - `MINOR`: Novas funcionalidades mantendo compatibilidade retroativa.
  - `PATCH`: Correções de bugs compatíveis.
- **CI/CD (*Continuous Integration / Continuous Delivery*):** Automação de lint, typecheck, testes automatizados e build a cada Pull Request antes de qualquer publicação.

---

## 2. Boas Práticas de Preparação e Publicação

1. **Portão de Qualidade Pré-Deploy (*Quality Gate*):**
   - Nenhuma versão deve ser publicada sem que os seguintes passos tenham sido executados e aprovados:
     1. Verificação de estado limpo do Git e branch correta.
     2. Análise estática (`lint` e `typecheck`).
     3. Execução da suíte de testes automatizados.
     4. Execução do build de produção (`npm run build`, `mvn package`, etc.).
2. **Atenção a Variáveis de Ambiente no Front-end (Vite):**
   - No Vite, variáveis expostas ao navegador precisam do prefixo `VITE_` (ex.: `VITE_API_URL`) e são substituídas estaticamente em tempo de build.
   - **Nunca** coloque chaves privadas ou segredos de servidor em variáveis `VITE_*`, pois elas ficam visíveis no bundle JavaScript público enviado ao navegador.
3. **Configuração de Roteamento SPA (*Single Page Application*) em Produção:**
   - Aplicações com `React Router DOM` (BrowserRouter) exigem configuração de *fallback* no servidor web (Nginx `try_files $uri $uri/ /index.html;`, `vercel.json` rewrites ou `_redirects` no Netlify) para evitar erro `404` ao recarregar rotas como `/portal` ou `/admin`.
4. **Estratégia de Rollback e Migrations de Banco:**
   - Reverter o código da aplicação **não** reverte alterações feitas no banco de dados. Toda migration executada em produção deve ser retrocompatível com a versão imediatamente anterior da aplicação, permitindo rollback seguro em caso de incidente.

---

## 3. Exemplos Práticos

### 3.1. Configuração Nginx para SPA (React Router) e Proxy Reverso de API

```nginx
server {
    listen 80;
    server_name _;
    root /usr/share/nginx/html;
    index index.html;

    # Suporte a rotas do React Router DOM (SPA Fallback)
    location / {
        try_files $uri $uri/ /index.html;
    }

    # Cache longo para assets com hash gerado pelo Vite
    location /assets/ {
        expires 1y;
        add_header Cache-Control "public, immutable";
    }
}
```

### 3.2. Verificação Pós-Deploy (*Smoke Test Checklist*)

1. **Healthcheck da API:** `GET /health` ou endpoint de status responde `200 OK`?
2. **Carregamento Inicial do Front-end:** A página carrega sem erros `404` de assets ou erros no Console do navegador?
3. **Comunicação Front-end ↔ Back-end:** `VITE_API_URL` e cabeçalhos `CORS` permitem requisições do domínio publicado?
4. **Fluxo Crítico:** Login, autenticação e a principal jornada do usuário estão operacionais?

---

## 4. Erros Comuns e Como Evitá-los

| Erro Comum | Problema | Solução Recomendada |
| :--- | :--- | :--- |
| **Esquecer o *SPA Fallback* ao publicar React Router** | Acessar `/` funciona, mas atualizar a página (F5) em `/portal` retorna `404 Not Found` do servidor estático. | Configurar rewrite/fallback para `/index.html` no servidor ou plataforma de hospedagem. |
| **Manter proxy de desenvolvimento do Vite como única configuração de API** | `server.proxy` no `vite.config.ts` só existe no `vite dev`; não existe após o `vite build`. | Usar `import.meta.env.VITE_API_URL` configurada corretamente para o ambiente de produção ou proxy reverso no servidor. |
| **Erro de CORS após o deploy** | O back-end estava configurado apenas para `http://localhost:5173` e bloqueia o domínio real do front-end. | Parametrizar as origens permitidas (`CORS_ALLOWED_ORIGINS`) via variável de ambiente no back-end. |

---

## 5. Referências Oficiais

- **Vite — Building for Production & Env Variables:** https://vite.dev/guide/build
- **The Twelve-Factor App (Metodologia):** https://12factor.net/pt_br/
- **Semantic Versioning 2.0.0:** https://semver.org/lang/pt-BR/

