# Guia Técnico: Autenticação, Autorização e Gerenciamento de Sessão

## 1. Visão Geral e Conceitos Fundamentais

Segurança de acesso divide-se em dois conceitos distintos que nunca devem ser confundidos:
- **Autenticação (*Authentication — AuthN*):** Verifica **quem** é o usuário (ex.: login com e-mail/senha, OAuth2/OIDC, validação de token JWT ou cookie de sessão). Falhas retornam **`401 Unauthorized`**.
- **Autorização (*Authorization — AuthZ*):** Verifica **o que** o usuário autenticado tem permissão para fazer ou acessar (RBAC — *Role-Based Access Control* ou ABAC — *Attribute-Based Access Control*). Falhas retornam **`403 Forbidden`**.

> **Regra de Ouro:** Restrições visuais ou de rota no Front-end (`<ProtectedRoute>`, ocultar botões) servem **apenas para experiência do usuário (UX)**. Toda verificação de autenticação e autorização **deve ser obrigatoriamente aplicada no Back-end**.

---

## 2. Boas Práticas de Implementação

1. **Armazenamento Seguro de Senhas:**
   - Nunca armazene senhas em texto puro ou com hashes rápidos (`MD5`, `SHA-1`, `SHA-256` simples).
   - Utilize algoritmos adaptativos com *salt* embutido: **Argon2id** (recomendação principal OWASP) ou **bcrypt** (fator de custo `>= 10`).
2. **Tokens JWT (*JSON Web Tokens*) e Sessões:**
   - Assine tokens com chaves criptográficas fortes (mínimo de 256 bits para `HS256` ou par de chaves assimétricas `RS256`/`ES256`) carregadas via variáveis de ambiente.
   - Defina tempo de expiração curto (`exp`) para *Access Tokens* (ex.: 15 a 60 minutos) e valide `iss` (*issuer*), `aud` (*audience*) e `exp` em todas as requisições.
   - Nunca armazene dados sensíveis (senhas, dados bancários, segredos) no payload do JWT, pois ele é apenas codificado em Base64URL (qualquer pessoa pode decodificá-lo).
3. **Prevenção contra IDOR (*Broken Object Level Authorization*):**
   - Ao acessar `/api/clientes/{id}/documentos`, o servidor não deve apenas verificar se o usuário está logado; deve validar se o `{id}` pertence ao usuário autenticado (extraído do token/sessão no servidor) ou se o usuário possui perfil administrativo autorizado.
4. **Proteção contra Força Bruta e Enumeração de Usuários:**
   - Retorne mensagens genéricas no login (`"E-mail ou senha inválidos"`) com tempo de resposta constante para não revelar quais e-mails estão cadastrados.
   - Aplique *Rate Limiting* nos endpoints `/login`, `/cadastro` e `/recuperar-senha`.

---

## 3. Exemplos Práticos

### 3.1. Fluxo de Autorização Baseada em Perfil (RBAC) e Propriedade do Recurso

```typescript
export interface UsuarioAutenticado {
  sub: string;
  perfil: 'ADMIN' | 'FUNCIONARIO' | 'CLIENTE';
}

export function podeAcessarProcessoConsorcio(
  usuario: UsuarioAutenticado,
  proprietarioClienteId: string
): boolean {
  if (usuario.perfil === 'ADMIN' || usuario.perfil === 'FUNCIONARIO') {
    return true;
  }
  // Perfil CLIENTE só pode acessar registros dos quais é titular
  return usuario.perfil === 'CLIENTE' && usuario.sub === proprietarioClienteId;
}
```

### 3.2. Redirecionamento por Perfil no Front-end (UX Complementar ao Back-end)

```tsx
// Exemplo alinhado a projetos com múltiplos perfis (ex.: Admin vs. Portal do Cliente)
export function obterRotaInicialPorPerfil(perfil: string): string {
  switch (perfil) {
    case 'ADMIN':
    case 'FUNCIONARIO':
      return '/admin';
    case 'CLIENTE':
      return '/portal';
    default:
      return '/login';
  }
}
```

---

## 4. Erros Comuns e Como Evitá-los

| Erro Comum | Problema | Solução Recomendada |
| :--- | :--- | :--- |
| **Confiar no `userId` ou `role` enviado no corpo/query da requisição** | Um usuário mal-intencionado altera `{"role": "ADMIN"}` no JSON e ganha acesso indevido. | Extrair a identidade e o perfil **exclusivamente** do token/sessão validado no servidor. |
| **Aceitar algoritmo `none` na validação de JWT** | Permite forjar tokens sem assinatura válida. | Fixar explicitamente a lista de algoritmos permitidos no verificador JWT (ex.: `algorithms: ['HS256']`). |
| **Expor segredo JWT (`JWT_SECRET`) no código ou `.env` commitado** | Compromete todos os tokens emitidos pela aplicação. | Ler exclusivamente de variáveis de ambiente seguras e manter `.env` no `.gitignore`. |
| **Não limpar estado e token no Logout ou em resposta `401`** | Mantém dados de outro usuário visíveis na tela compartilhada. | Limpar armazenamento de sessão, estado em memória e redirecionar imediatamente para `/login`. |

---

## 5. Referências Oficiais

- **OWASP Authentication Cheat Sheet:** https://cheatsheetseries.owasp.org/cheatsheets/Authentication_Cheat_Sheet.html
- **OWASP Authorization Cheat Sheet:** https://cheatsheetseries.owasp.org/cheatsheets/Authorization_Cheat_Sheet.html
- **RFC 7519 — JSON Web Token (JWT):** https://datatracker.ietf.org/doc/html/rfc7519

