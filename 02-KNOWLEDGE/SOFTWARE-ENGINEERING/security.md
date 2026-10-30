# Guia Técnico: Segurança da Informação, OWASP Top 10 e LGPD

## 1. Visão Geral e Conceitos Fundamentais

A segurança deve ser tratada desde o design (*Security by Design* e *Defense in Depth*), garantindo **Confidencialidade**, **Integridade** e **Disponibilidade** dos sistemas e a proteção dos dados pessoais conforme a **LGPD (Lei nº 13.709/2018)**.

---

## 2. Prevenção às Principais Vulnerabilidades (OWASP Top 10)

### 2.1. A01 — Quebra de Controle de Acesso (*Broken Access Control*)
- **Risco:** Usuários acessam rotas administrativas ou manipulam IDs na URL/JSON (IDOR) para visualizar ou alterar dados de outros clientes.
- **Prevenção:** Negar acesso por padrão (*Deny by Default*), validar perfil e titularidade do recurso no servidor em **todas** as requisições e nunca confiar em validações feitas apenas no Front-end.

### 2.2. A02 — Falhas Criptográficas e Exposição de Segredos
- **Risco:** Vazamento de chaves de API, tokens, senhas de banco de dados ou dados pessoais em código-fonte, git history ou logs.
- **Prevenção:** Usar variáveis de ambiente (`.env` fora do controle de versão), HTTPS/TLS em trânsito, Argon2id/bcrypt para senhas e mascaramento de dados sensíveis nos logs.

### 2.3. A03 — Injeção (SQL Injection, NoSQL Injection, Command Injection, XSS)
- **Risco:** Dados não confiáveis enviados pelo usuário são interpretados como comandos pelo banco de dados, shell do sistema ou navegador.
- **Prevenção:**
  - **SQL Injection:** Usar exclusivamente consultas parametrizadas (*Prepared Statements*).
  - **XSS (*Cross-Site Scripting*):** Confiar no escape automático do React (`{variavel}`) e **evitar** `dangerouslySetInnerHTML` ou `innerHTML` com dados não sanitizados. Validar URLs antes de colocá-las em `<a href={url}>` (bloquear esquema `javascript:`).
  - **Command Injection:** Nunca passar entradas do usuário para comandos de sistema operacional (`exec`, `spawn` com shell).

### 2.4. A05 — Configuração Incorreta de Segurança (*Security Misconfiguration*)
- **Risco:** `CORS: *` com credenciais, modo debug ativo em produção, *stack traces* expostas ao cliente ou cabeçalhos HTTP de segurança ausentes.
- **Prevenção:** Restringir origens no CORS, retornar mensagens de erro padronizadas sem detalhes internos e configurar cabeçalhos como `Content-Security-Policy`, `X-Content-Type-Options: nosniff` e `Strict-Transport-Security`.

### 2.5. A07 & A10 — Falhas de Autenticação e SSRF (*Server-Side Request Forgery*)
- **Risco:** Quando o servidor faz requisições HTTP para URLs fornecidas pelo usuário sem validação, permitindo acessar serviços internos da rede local (`127.0.0.1`, metadados de nuvem).
- **Prevenção:** Nunca permitir que o cliente defina livremente URLs de destino para o servidor buscar; validar domínios contra uma *allowlist* estrita.

---

## 3. Proteção de Dados Pessoais (LGPD no Desenvolvimento)

1. **Minimização de Dados:** Coletar, armazenar e retornar nas APIs apenas os campos estritamente necessários para a finalidade da funcionalidade.
2. **Higiene de Logs:** É proibido registrar nos logs da aplicação senhas, tokens JWT, chaves de API, números completos de cartão ou documentos sensíveis sem necessidade legal/auditoria segura.
3. **Ambientes de Teste e Desenvolvimento:** Nunca utilizar bancos de dados reais de clientes de produção em ambientes locais ou de teste sem anonimização e autorização.

---

## 4. Checklist Rápido de Auditoria de Segurança (Pré-Entrega)

- [ ] Existe alguma chave, token ou senha hardcoded no código ou em arquivos versionados? *(Deve ser ZERO)*
- [ ] Todos os dados de entrada (body, query, path params) possuem validação de tipo, tamanho e formato no servidor?
- [ ] Todas as rotas protegidas verificam autenticação (`401`) e autorização/titularidade (`403`) no back-end?
- [ ] As consultas ao banco de dados utilizam parâmetros seguros sem concatenação de strings?
- [ ] As respostas de erro ocultam detalhes internos de infraestrutura e *stack traces*?
- [ ] As dependências adicionadas são mantidas, conhecidas e livres de vulnerabilidades críticas (`npm audit` / `pip-audit`)?

---

## 5. Referências Oficiais

- **OWASP Top 10 Official Page:** https://owasp.org/www-project-top-ten/
- **OWASP Cheat Sheet Series:** https://cheatsheetseries.owasp.org/
- **OWASP Application Security Verification Standard (ASVS):** https://owasp.org/www-project-application-security-verification-standard/

