# Lambda Expressions e Method References no Java

As **Lambda Expressions** e **Method References** foram introduzidas no Java 8 e são recursos fundamentais para escrever código mais conciso e expressivo, especialmente quando trabalhamos com a **Stream API** e **programação funcional**.

---

## Lambda Expressions

### O que é?
- É uma forma curta de implementar **interfaces funcionais** (interfaces com apenas um método abstrato).
- Permite passar comportamentos como parâmetros.
- Substitui o uso de classes anônimas.
- Só funcionam em interfaces funcionais (exemplo da Stream API)

Exemplo
```java
// ============================
// SEM LAMBDA (classe anônima)
// ============================
import java.util.Arrays;
import java.util.List;
import java.util.function.Consumer;

public class ExemploSemLambda {
    public static void main(String[] args) {
        List<String> nomes = Arrays.asList("Ana", "Bruno", "Carlos");

        // Implementação de Consumer usando classe anônima
        nomes.forEach(new Consumer<String>() {
            @Override
            public void accept(String nome) {
                System.out.println(nome);
            }
        });
    }
}
```
```java
// ============================
// COM LAMBDA
// ============================
import java.util.Arrays;
import java.util.List;

public class ExemploComLambda {
    public static void main(String[] args) {
        List<String> nomes = Arrays.asList("Ana", "Bruno", "Carlos");

        // Implementação de Consumer usando lambda
        nomes.forEach(nome -> System.out.println(nome));
    }
}
```
---

## Method References

### O que é?
- É uma forma **ainda mais curta** de escrever lambdas que apenas chamam um método existente.
- Usa a sintaxe `Classe::metodo` ou `objeto::metodo`.
- Funciona apenas quando a expressão lambda **apenas delega a chamada** de um método.

**Tipos principais:**
1. **Referência a método estático**
   ```java
   Function<String, Integer> parser = Integer::parseInt;
   ```
2. **Referência a método de instância**
   ```java
   String texto = "Java";
   Supplier<Integer> tamanho = texto::length;
   ```
3. **Referência a método de instância de um objeto arbitrário**
   ```java
   List<String> lista = List.of("a", "bb", "ccc");
   lista.stream().map(String::length).forEach(System.out::println);
   ```
4. **Referência a construtor**
   ```java
   Supplier<List<String>> criarLista = ArrayList::new;
   ```
```java
// ============================
// COM METHOD REFERENCE
// ============================
import java.util.Arrays;
import java.util.List;

public class ExemploComMethodReference {
    public static void main(String[] args) {
        List<String> nomes = Arrays.asList("Ana", "Bruno", "Carlos");

        // Method Reference para System.out.println
        nomes.forEach(System.out::println);
    }
}
```
---

## Comparação Lambda vs Method Reference

| Característica        | Lambda                                             | Method Reference                              |
|-----------------------|----------------------------------------------------|-----------------------------------------------|
| **Objetivo**          | Criar funções de forma concisa                     | Encaminhar uma chamada de método já existente |
| **Sintaxe**           | `(param) -> expressão`                             | `Classe::metodo` ou `objeto::metodo`          |
| **Flexibilidade**     | Pode ter lógica personalizada no corpo do lambda   | Apenas chama um método existente              |
| **Legibilidade**      | Pode ficar mais verboso                            | Mais limpo quando só chama método existente   |

---

## Exemplo com Stream API

**Usando Lambda:**
```java
List<String> nomes = List.of("Ana", "Bruno", "Carlos");

nomes.stream()
     .filter(nome -> nome.startsWith("A"))
     .forEach(nome -> System.out.println(nome));
```

**Usando Method Reference:**
```java
List<String> nomes = List.of("Ana", "Bruno", "Carlos");

nomes.stream()
     .filter(nome -> nome.startsWith("A"))
     .forEach(System.out::println);
```

---

## Resumo didático

- **Lambda** é como escrever um **bilhete** dizendo o que fazer com cada item.  
- **Method Reference** é como **apontar** e dizer: "Use aquela receita que já está pronta ali".

- Muitas vezes você começa com um lambda e percebe que ele **só chama um método**, e aí pode encurtar usando method reference.

---

**Resumo rápido**:
- Lambda → define o que fazer de forma direta.  
- Method Reference → reutiliza um método que já existe.  
- Ambos trabalham muito bem juntos com a **Stream API**.
