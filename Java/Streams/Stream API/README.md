# Stream API — Processando dados de forma declarativa no Java

A **Stream API** foi introduzida no **Java 8** e permite processar coleções de dados (listas, conjuntos, mapas, etc.) de forma **declarativa**, ou seja, dizendo **o que fazer** e não **como fazer**.

<img width="2560" height="1108" alt="image" src="https://github.com/user-attachments/assets/5313bd08-c187-4bc3-a0dd-6353806fb0ce" />

---

## O que é a Stream API?
- É parte do pacote `java.util.stream`.
- Permite **encadear operações** para transformar, filtrar e reduzir dados.
- Não altera a coleção original, ela trabalha com **fluxos de dados**.
- Usa porogramação funcional.

---

## Características importantes
1. **Não é uma estrutura de dados** — é apenas uma visão dos dados existentes.
2. **Processamento em pipeline** — cada operação retorna uma nova stream até uma operação terminal ser chamada.
3. **Pode ser sequencial ou paralela** (`stream()` vs `parallelStream()`).
4. **Lida com dados de forma imutável** — não modifica os elementos originais.

---

## Tipos de operações
- **Intermediárias** (retornam uma nova stream)
  - `filter()`, `map()`, `sorted()`, `distinct()`, `limit()`
- **Terminais** (encerram o fluxo e retornam um resultado)
  - `forEach()`, `collect()`, `reduce()`, `count()`, `anyMatch()`

---

## Exemplo básico
```java
import java.util.List;

public class Main {
    public static void main(String[] args) {
        List<String> nomes = List.of("Ana", "Bruno", "Alice", "Carlos");

        nomes.stream() // cria uma Stream
             .filter(nome -> nome.startsWith("A")) // intermediária
             .map(String::toUpperCase) // intermediária
             .sorted() // intermediária
             .forEach(System.out::println); // terminal
    }
}
```
**Saída:**
```
ALICE
ANA
```

---

## Resumo didático
Imagina que você tem **um rio cheio de peixinhos** (os seus dados).

- A **Stream** é como uma **esteira rolante** que leva os peixinhos.
- As **operações intermediárias** (`filter`, `map`, `sorted`) são como **filtros e máquinas** na esteira que:
  - Tirar peixes pequenos.
  - Pintar os peixes de outra cor.
  - Colocar os peixes em ordem.
- A **operação terminal** (`forEach`, `collect`) é o **final da esteira**, onde você pega o resultado e guarda ou usa.

- Enquanto você não colocar uma operação terminal, **a esteira não liga**.

---

## Comparação:

| Característica              | For tradicional                                | Stream API                                       |
|-----------------------------|-----------------------------------------------|-------------------------------------------------|
| **Estilo**                  | Imperativo (passo a passo)                    | Declarativo (o que fazer)                       |
| **Código**                  | Mais verboso                                  | Mais conciso e expressivo                       |
| **Paralelismo**              | Manual                                        | Fácil (`parallelStream()`)                      |
| **Imutabilidade**            | Normalmente modifica a coleção                | Mantém a coleção original                       |
| **Encadeamento de operações**| Não                                           | Sim                                              |

---

 **Resumo simplificado**:
- **Stream API** → cria um fluxo de dados.
- **Intermediárias** → preparam, filtram e transformam.
- **Terminal** → pega o resultado.
- Perfeito para trabalhar com coleções de forma **limpa, concisa e funcional**.


---
<br><br>

## Programação Imperativa vs Programação Funcional

### Programação Imperativa
- Diz **como fazer** passo a passo.
- O foco está no **controle do fluxo** (loops, condicionais).
- Trabalha com **mudança de estado** (variáveis sendo alteradas ao longo do código).
- Mais próxima de “receita de bolo” detalhada.

**Exemplo imperativo:**
```java
List<String> resultado = new ArrayList<>();
for (String nome : nomes) {
    if (nome.startsWith("A")) {
        resultado.add(nome.toUpperCase());
    }
}
```

---

### Programação Funcional
- Diz **o que fazer**, sem detalhar todos os passos.
- O foco está nas **transformações de dados**.
- Evita modificar dados existentes (**imutabilidade**).
- Usa **funções como parâmetros** (lambdas, method references).

**Exemplo funcional (Stream API):**
```java
List<String> resultado = nomes.stream()
    .filter(nome -> nome.startsWith("A"))
    .map(String::toUpperCase)
    .toList();
```

---

## Comparação

| Característica        | Imperativa                               | Funcional                                |
|-----------------------|------------------------------------------|------------------------------------------|
| **Foco**              | Como fazer                               | O que fazer                              |
| **Estilo**            | Passo a passo                            | Declara intenções                        |
| **Mudança de estado** | Frequente (variáveis mutáveis)            | Evita (imutabilidade)                    |
| **Controle**          | Baseado em loops e condicionais          | Baseado em operações encadeadas          |
| **Funções**           | Chamadas diretas                         | Passadas como parâmetros (lambdas)       |
| **Legibilidade**      | Mais verboso                             | Mais conciso                             |

---

**Resumo rápido**:
- Imperativo → "faça isso, depois isso, depois isso..."
- Funcional → "pegue esses dados, filtre, transforme e me devolva o resultado".
