# Guia Técnico: Python Moderno (Python 3.11+)

## 1. Visão Geral e Conceitos Fundamentais

O **Python 3.11+** destaca-se no desenvolvimento de APIs de alta performance (FastAPI, Django, Flask), automação, engenharia de dados e integração com modelos de Inteligência Artificial.

### Conceitos Essenciais
- **Type Hints (PEP 484 / PEP 604):** Anotações de tipo nativas (`def buscar(id: int) -> Usuario | None:`) permitem validação estática via `mypy` ou `pyright` e validação em runtime com `Pydantic`.
- **Ambientes Virtuais Isolados (`venv`, `uv`, `poetry`):** Toda aplicação Python deve gerenciar dependências de forma isolada, nunca instalando pacotes diretamente no interpretador global do sistema operacional.
- **Gerenciadores de Contexto (`with`):** Garantem o fechamento determinístico de conexões de banco, arquivos e sessões HTTP mesmo quando ocorrem exceções.
- **`dataclasses` e `Pydantic BaseModel`:** Estruturas declarativas para modelagem de domínio e validação de esquemas de entrada/saída.

---

## 2. Boas Práticas de Desenvolvimento

1. **Seguir a PEP 8 e Ferramentas de Qualidade (`Ruff`):**
   - Utilize `snake_case` para funções, métodos e variáveis; `PascalCase` para classes; `UPPER_SNAKE_CASE` para constantes.
2. **Tipagem Explícita em Todas as Assinaturas:**
   - Anote parâmetros e valores de retorno em todas as funções de negócio e rotas de API.
3. **Nunca Usar Argumentos Padrão Mutáveis:**
   - Evite `def adicionar(item: str, lista: list[str] = []):`, pois a mesma lista é compartilhada entre chamadas sucessivas. Use `None` como padrão e inicialize dentro da função.
4. **Capturar Exceções Específicas:**
   - Nunca utilize `except:` genérico ou `except Exception: pass`. Capture a exceção exata (`ValueError`, `httpx.HTTPError`, `SQLAlchemyError`) e registre o contexto com o módulo `logging`.
5. **Configurações via Variáveis de Ambiente (`pydantic-settings`):**
   - Centralize variáveis de ambiente tipadas e validadas na inicialização da aplicação.

---

## 3. Exemplos Práticos

### 3.1. Validação de Contrato e Endpoint com FastAPI e Pydantic v2

```python
from datetime import datetime, timezone
from pydantic import BaseModel, EmailStr, Field
from fastapi import FastAPI, HTTPException, status

app = FastAPI(title="Serviço de Notificações")


class NotificacaoCreate(BaseModel):
    cliente_id: str = Field(min_length=3, max_length=64)
    email: EmailStr
    mensagem: str = Field(min_length=10, max_length=1000)


class NotificacaoResponse(BaseModel):
    id: str
    cliente_id: str
    enviado_em: datetime
    status: str


@app.post(
    "/api/notificacoes",
    response_model=NotificacaoResponse,
    status_code=status.HTTP_201_CREATED,
)
async def criar_notificacao(payload: NotificacaoCreate) -> NotificacaoResponse:
    if not payload.cliente_id.isalnum():
        raise HTTPException(
            status_code=status.HTTP_422_UNPROCESSABLE_ENTITY,
            detail="O identificador do cliente deve ser alfanumérico.",
        )
    return NotificacaoResponse(
        id="notif_01",
        cliente_id=payload.cliente_id,
        enviado_em=datetime.now(timezone.utc),
        status="ENFILEIRADO",
    )
```

### 3.2. Uso Seguro de `dataclass` com `field(default_factory=...)`

```python
from dataclasses import dataclass, field


@dataclass(frozen=True)
class RelatorioProcessamento:
    lote_id: str
    processados: int
    erros: list[str] = field(default_factory=list)
```

---

## 4. Erros Comuns e Como Evitá-los

| Erro Comum | Problema | Solução Recomendada |
| :--- | :--- | :--- |
| **Argumento default mutável (`def fn(x=[])`)** | O objeto mutável é criado apenas uma vez na definição da função, vazando estado entre chamadas. | Usar `def fn(x: list[str] | None = None): x = [] if x is None else x`. |
| **Bloquear o Event Loop em funções `async def`** | Chamar `time.sleep()` ou `requests.get()` síncrono dentro de uma rota assíncrona trava todo o servidor ASGI. | Usar `await asyncio.sleep()` e clientes assíncronos como `httpx.AsyncClient`. |
| **`datetime.utcnow()` (Depreciado no Python 3.12+)** | Cria um objeto `datetime` *naive* (sem fuso horário explícito), causando bugs de conversão. | Usar `datetime.now(timezone.utc)` (objeto *timezone-aware*). |
| **Concatenar caminhos de arquivo com strings (`+`)** | Quebra entre Windows (`\`) e Linux (`/`). | Utilizar `pathlib.Path` (`base_dir / "config" / "settings.json"`). |

---

## 5. Referências Oficiais

- **Python 3 Official Documentation:** https://docs.python.org/pt-br/3/
- **PEP 8 — Style Guide for Python Code:** https://peps.python.org/pep-0008/
- **FastAPI Documentation:** https://fastapi.tiangolo.com/pt/
- **Pydantic v2 Documentation:** https://docs.pydantic.dev/latest/

