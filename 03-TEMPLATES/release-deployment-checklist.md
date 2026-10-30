# Checklist de Preparação de Release e Deploy — [VERSÃO vX.Y.Z]

**Projeto:** `[Nome do Projeto]`  
**Repositório (`Front-end` / `Back-end`):** `[Repositório alvo]`  
**Ambiente de Destino:** `[Development | Testing | Staging / Homologação | Production]`  
**Versão / Branch / Commit:** `[vX.Y.Z — branch — hash]`  
**Autorização Explícita Confirmada?** `[Sim / Não — Deploy em produção exige autorização explícita]`

---

## 1. Verificação de Repositório e Escopo (Pré-Release)

- [ ] A branch de origem está correta e atualizada em relação à branch alvo.
- [ ] `git status` foi verificado e não existem alterações acidentais ou arquivos temporários não rastreados.
- [ ] Todos os commits incluídos na versão pertencem ao escopo aprovado da entrega.
- [ ] Nenhuma credencial, token, chave privada ou arquivo `.env` foi incluído no histórico.

---

## 2. Validação Técnica e Qualidade (Quality Gate)

| Etapa de Validação | Comando Executado | Status (`Aprovado` / `Reprovado` / `Não Aplicável`) |
| :--- | :--- | :--- |
| **Linting** | `[Ex.: npm run lint]` | `[Status]` |
| **Verificação de Tipos** | `[Ex.: npx tsc --noEmit]` | `[Status]` |
| **Testes Unitários / Integração** | `[Ex.: npm test]` | `[Status]` |
| **Auditoria de Dependências** | `[Ex.: npm audit --production]` | `[Status]` |
| **Build de Produção** | `[Ex.: npm run build]` | `[Status]` |

---

## 3. Configuração do Ambiente de Destino e Banco de Dados

- [ ] Variáveis de ambiente do ambiente de destino foram conferidas (ex.: `VITE_API_URL`, `CORS_ALLOWED_ORIGINS`, banco de dados).
- [ ] Configurações de roteamento SPA (*fallback* para `/index.html`) estão ativas no servidor de hospedagem (para projetos Front-end React Router).
- [ ] **Banco de Dados (quando aplicável ao Back-end):**
  - [ ] Migrations pendentes foram revisadas e não contêm operações destrutivas não autorizadas.
  - [ ] Existência e integridade de backup recente foram verificadas antes da execução de migrations.
  - [ ] Compatibilidade de rollback entre código e banco foi avaliada.

---

## 4. Plano de Rollback (Contingência)

- **Versão Anterior Estável:** `[vX.Y.Z-anterior / commit hash]`
- **Procedimento de Reversão da Aplicação:** `[Passos exatos para restaurar a versão anterior]`
- **Procedimento de Reversão de Dados/Configuração:** `[Passos aplicáveis sem perda de dados]`

---

## 5. Validação Pós-Deploy (Smoke Tests)

- [ ] A aplicação está acessível na URL do ambiente de destino sem erros de certificado/HTTPS.
- [ ] A página inicial e as rotas principais carregam sem erros `404` ou falhas no Console.
- [ ] A comunicação entre Front-end e Back-end (autenticação e consulta principal) responde dentro do esperado.
- [ ] Os logs iniciais da aplicação foram inspecionados e não apresentam erros críticos (`500` / exceções não tratadas).

---

## 6. Registro Final da Release

- **Resultado da Publicação:** `[Apenas Preparada (Aguardando Autorização) | Publicada e Validada | Revertida (Rollback)]`
- **Limitações ou Observações:** `[Registrar qualquer ponto de atenção pós-deploy]`

