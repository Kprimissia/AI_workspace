# Guia Técnico: Java Moderno (Java 17 / 21 LTS e Spring Boot)

## 1. Visão Geral e Conceitos Fundamentais

O ecossistema **Java LTS (17 e 21)** combinado ao **Spring Boot 3+** é amplamente utilizado no desenvolvimento de APIs corporativas, microsserviços e sistemas de alta confiabilidade.

### Recursos Essenciais do Java Moderno
- **`record` (Java 16+):** Classes de dados imutáveis ideais para DTOs (*Data Transfer Objects*) de requisição e resposta, gerando construtor canônico, *getters*, `equals()`, `hashCode()` e `toString()` automaticamente.
- **`sealed classes` / `interfaces` (Java 17+):** Restringem quais classes podem estender ou implementar um tipo, permitindo *Pattern Matching* exaustivo em `switch`.
- **Virtual Threads — Project Loom (Java 21 LTS):** Threads leves gerenciadas pela JVM que permitem alta vazão em operações bloqueantes de I/O (banco de dados, chamadas HTTP) sem complexidade reativa.
- **`Optional<T>`:** Representa explicitamente o retorno possivelmente ausente de um método, evitando `NullPointerException`.

---

## 2. Boas Práticas de Desenvolvimento

1. **Separação Estrita entre Entidades JPA e DTOs:**
   - Nunca exponha entidades `@Entity` diretamente nos controladores REST (`@RestController`). Utilize `record` para DTOs de entrada (com Bean Validation `@Valid`) e saída.
2. **Injeção de Dependências via Construtor:**
   - Declare dependências como `private final` e injete via construtor (nunca use `@Autowired` diretamente em atributos de classe), facilitando testes unitários e garantindo imutabilidade.
3. **Tratamento Centralizado de Exceções (`@RestControllerAdvice`):**
   - Padronize erros da API utilizando a especificação **RFC 7807 / RFC 9457 (`ProblemDetail` nativo do Spring 6)** sem vazar *stack traces* ou detalhes internos do banco de dados.
4. **Mapeamento Relacional Seguro (JPA / Hibernate):**
   - Configure relacionamentos `@ManyToOne` e `@OneToOne` com `fetch = FetchType.LAZY` para evitar consultas `N+1` acidentais.
   - Delimite transações com `@Transactional` na camada de serviço (`@Service`), usando `@Transactional(readOnly = true)` em métodos exclusivamente de leitura.

---

## 3. Exemplos Práticos

### 3.1. DTO Imutável com `record` e Bean Validation

```java
package br.com.projeto.dto;

import jakarta.validation.constraints.Email;
import jakarta.validation.constraints.NotBlank;
import jakarta.validation.constraints.Positive;

public record NotificacaoContempladoRequest(
    @NotBlank(message = "O nome do consorciado é obrigatório")
    String nomeCliente,

    @NotBlank(message = "O e-mail é obrigatório")
    @Email(message = "Formato de e-mail inválido")
    String email,

    @Positive(message = "O número da cota deve ser positivo")
    Integer numeroCota
) {}
```

### 3.2. Controller e Service com Injeção por Construtor

```java
package br.com.projeto.controller;

import br.com.projeto.dto.NotificacaoContempladoRequest;
import br.com.projeto.dto.NotificacaoResponse;
import br.com.projeto.service.NotificacaoService;
import jakarta.validation.Valid;
import org.springframework.http.HttpStatus;
import org.springframework.http.ResponseEntity;
import org.springframework.web.bind.annotation.*;

@RestController
@RequestMapping("/api/notificacoes")
public class NotificacaoController {

    private final NotificacaoService notificacaoService;

    public NotificacaoController(NotificacaoService notificacaoService) {
        this.notificacaoService = notificacaoService;
    }

    @PostMapping
    public ResponseEntity<NotificacaoResponse> criar(
            @Valid @RequestBody NotificacaoContempladoRequest request) {
        NotificacaoResponse criada = notificacaoService.registrarNotificacao(request);
        return ResponseEntity.status(HttpStatus.CREATED).body(criada);
    }
}
```

---

## 4. Erros Comuns e Como Evitá-los

| Erro Comum | Problema | Solução Recomendada |
| :--- | :--- | :--- |
| **Expor `@Entity` na resposta JSON** | Causa `LazyInitializationException`, recursão infinita em relacionamentos bidirecionais e vulnerabilidade de *Mass Assignment*. | Converter sempre para DTO (`record`) antes de retornar no Controller. |
| **Usar `Optional.get()` sem verificação** | Lança `NoSuchElementException`, trocando um `NullPointerException` por outra exceção não tratada. | Usar `.orElseThrow(() -> new RecursoNaoEncontradoException(...))`, `.map()` ou `.orElse(...)`. |
| **Problema de consultas `N+1` no Hibernate** | Buscar uma lista de `N` registros e executar `1` query adicional por item ao iterar sobre uma coleção `LAZY`. | Usar `JOIN FETCH` em JPQL, `@EntityGraph` ou projeções DTO diretas no repositório. |
| **Usar `float` ou `double` para valores monetários** | Erros de arredondamento binário em cálculos financeiros. | Utilizar exclusivamente `BigDecimal` com escala e `RoundingMode` explícitos. |

---

## 5. Referências Oficiais

- **Java Documentation (Oracle / OpenJDK):** https://docs.oracle.com/en/java/javase/21/
- **Spring Boot Reference Documentation:** https://docs.spring.io/spring-boot/index.html
- **Jakarta Persistence (JPA) Specification:** https://jakarta.ee/specifications/persistence/

