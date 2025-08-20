# Interfaces em Java

## O que são?
Uma **interface** em Java é um **contrato** que define métodos (e constantes) que uma classe deve implementar.  
Diferente de uma classe, a interface não descreve *como* as coisas são feitas, apenas *o que* precisa ser feito.  
A partir do Java 8, interfaces também podem conter métodos `default` (com implementação) e `static`.

### Explicação:
Você cria uma interface com variável que se comporta como polimorfismo, tipo implementa `Voar`, pode ser usada em `Passaro` e `Avião`. 
`Passaro` e `Avião` poderiam herdar de `Voar`(se não fosse uma interface), porém se `Passaro` já herda de `Animal` não poderia herdar também de `Voar`pois em Java uma classe só pode herdar de uma única outra classe.
Ex: em classe abstrata você coloca `Animal` pode ter métodos implementados: dormir, nome, idade... métodos com comportamentos padrão.
Na interface, somente um contrato sem se preocupar com implementação ou estado, interfaces não tem atributos apenas constantes.

Exemplo de interface:
```java
   interface Animal {
       void emitirSom();
   }
```
Exemplo de classe abstrata:
```java
  abstratic class Animal {
       String nome;
       void dormir() {
         System.out.println("dormindo");
       }
   abstratic void emitirSom();
   }
   ```
- Apartir do java 8 a ionterface pode ter instâncias
- Podem atributos porém
```java
public static final
```
- Não podem construtor
- Interface = comportamento
- Classe abstrata = comportamento + estado
---

## Quando usar interface?
- Use quando você quer definirum contrato de comportamento que várias classes (diferentes entre si) devem seguir
  > Podem fazer - coisas que algém pode fazer, mas não tem atributos em comum

## Quando usar classe abstrata
- Use quando você quer criar uma base com comportamento e atributos comuns e que outras classes vão herdar
  > É um tipo de - coisas que são de um mesmo tipo, com características e ações parecidas

## Porque usar Interface
- **Abstração**: esconde detalhes da implementação, focando apenas no comportamento esperado.  
- **Polimorfismo**: permite que diferentes classes implementem a mesma interface de formas distintas.  
- **Flexibilidade no design**: facilita trabalhar com abstrações ao invés de classes concretas (`List` ao invés de `ArrayList`).  
- **Contratos claros**: define um conjunto de métodos obrigatórios que a classe precisa fornecer.  
- **Desacoplamento**: facilita manutenção, evolução do código e testes.

---

## Tipos de interfaces
1. **Interface comum**  
   Define apenas métodos abstratos.  
   ```java
   interface Animal {
       void emitirSom();
   }

   class Cachorro implements Animal {
       public void emitirSom() {
           System.out.println("Au au!");
       }
   }
   ```

2. **Interface com métodos `default` (Java 8+)**  
   Permite fornecer uma implementação padrão.  
   ```java
   interface Veiculo {
       default void buzinar() {
           System.out.println("Buzina padrão!");
       }
   }
   ```

3. **Interface funcional (Functional Interface)**  
   - Possui **apenas UM método abstrato**.  
   - Usada em conjunto com **expressões lambda**.  
   - Identificada pela anotação `@FunctionalInterface`.  
   ```java
   @FunctionalInterface
   interface Operacao {
       int executar(int a, int b);
   }

   public class Teste {
       public static void main(String[] args) {
           Operacao soma = (a, b) -> a + b;
           System.out.println(soma.executar(5, 3));
       }
   }
   ```

---

## Interfaces e SOLID
As interfaces se conectam fortemente aos princípios **SOLID**:

- **I – Interface Segregation Principle (ISP)**  
  Uma classe não deve ser forçada a implementar métodos que não utiliza.  
  Prefira interfaces menores e mais específicas ao invés de interfaces genéricas e grandes.  

- **D – Dependency Inversion Principle (DIP)**  
  O código deve depender de **abstrações** (interfaces) e não de implementações concretas.  
  Isso aumenta o **desacoplamento**, facilita a **manutenção** e melhora a **testabilidade** do software.  

---

# Functional Interfaces em Java

As **Functional Interfaces** são interfaces que possuem **apenas um método abstrato** e podem ser usadas com **expressões lambda** e **Streams**.  
Elas fazem parte do pacote `java.util.function` introduzido no **Java 8**.  

---

## Consumer<T>
- **Descrição**: Representa uma operação que aceita um argumento do tipo `T` e não retorna resultado.  
- **Uso comum**: Executar ações com efeitos colaterais, como imprimir valores ou modificar objetos em um `Stream`.  
- **Exemplo**:
  ```java
  import java.util.function.Consumer;
  import java.util.Arrays;

  public class ExemploConsumer {
      public static void main(String[] args) {
          Consumer<String> imprimir = s -> System.out.println(s);
          Arrays.asList("A", "B", "C").forEach(imprimir);
      }
  }
  ```

---

## Supplier<T>
- **Descrição**: Representa uma operação que **não aceita argumentos** e retorna um resultado do tipo `T`.  
- **Uso comum**: Fornecer ou criar novos objetos de determinado tipo sob demanda.  
- **Exemplo**:
  ```java
  import java.util.function.Supplier;

  public class ExemploSupplier {
      public static void main(String[] args) {
          Supplier<Double> gerarNumero = () -> Math.random();
          System.out.println(gerarNumero.get());
      }
  }
  ```

---

## Function<T, R>
- **Descrição**: Representa uma função que aceita um argumento de tipo `T` e retorna um resultado de tipo `R`.  
- **Uso comum**: Transformar ou mapear elementos em Streams.  
- **Exemplo**:
  ```java
  import java.util.function.Function;

  public class ExemploFunction {
      public static void main(String[] args) {
          Function<String, Integer> tamanho = s -> s.length();
          System.out.println(tamanho.apply("Java")); // 4
      }
  }
  ```

---

## Predicate<T>
- **Descrição**: Representa uma função que aceita um argumento de tipo `T` e retorna um valor booleano.  
- **Uso comum**: Filtrar elementos em Streams com base em condições.  
- **Exemplo**:
  ```java
  import java.util.function.Predicate;
  import java.util.Arrays;

  public class ExemploPredicate {
      public static void main(String[] args) {
          Predicate<Integer> ehPar = n -> n % 2 == 0;
          Arrays.asList(1,2,3,4,5)
                .stream()
                .filter(ehPar)
                .forEach(System.out::println); // imprime 2 e 4
      }
  }
  ```

---

## BinaryOperator<T>
- **Descrição**: Representa uma operação que combina dois argumentos do tipo `T` e retorna um resultado do mesmo tipo.  
- **Uso comum**: Reduzir ou combinar elementos, como somar números ou concatenar strings.  
- **Exemplo**:
  ```java
  import java.util.function.BinaryOperator;
  import java.util.Arrays;

  public class ExemploBinaryOperator {
      public static void main(String[] args) {
          BinaryOperator<Integer> soma = (a, b) -> a + b;
          int resultado = Arrays.asList(1, 2, 3, 4)
                                 .stream()
                                 .reduce(0, soma);
          System.out.println(resultado); // 10
      }
  }
  ```

---

## Outras Functional Interfaces importantes
Além das que você anotou, existem outras bastante usadas:

- **UnaryOperator<T>**  
  Uma especialização de `Function<T, R>` onde o tipo de entrada e saída são iguais.  
  Exemplo: `x -> x * x` (calcular o quadrado de um número).

- **BiFunction<T, U, R>**  
  Recebe dois argumentos (`T` e `U`) e retorna um resultado do tipo `R`.  
  Exemplo: concatenar uma String e um Integer em um texto.

- **BiPredicate<T, U>**  
  Recebe dois argumentos (`T` e `U`) e retorna um boolean.  
  Exemplo: verificar se dois números são iguais.

- **BiConsumer<T, U>**  
  Recebe dois argumentos (`T` e `U`) e não retorna nada.  
  Exemplo: imprimir chave e valor de um `Map`.

---

## Resumo
- **Consumer<T>** → Consome um valor, não retorna nada.  
- **Supplier<T>** → Fornece um valor, sem entrada.  
- **Function<T, R>** → Transforma `T` em `R`.  
- **Predicate<T>** → Avalia uma condição booleana sobre `T`.  
- **BinaryOperator<T>** → Combina dois `T` em um `T`.  
- **Outros (BiConsumer, BiFunction, UnaryOperator, BiPredicate)** → variantes úteis para múltiplos argumentos.  

Essas interfaces são a base para trabalhar com **lambdas e Streams** no Java moderno.
---

# Onde entram os Generics nisso?
- Sem generics, você teria que criar uma interface diferente para cada tipo, o que deixaria o Java chato e repetitivo.  

---

## Resumo didático
- Consumer → Explicação: É como alguém que recebe um presente, abre e usa, mas não devolve nada.
> Exemplo do mundo real: Você dá um desenho para sua mãe e ela só pendura na geladeira.
- Supplier → Explicação: É como alguém que sempre te dá alguma coisa quando você pede.
> Exemplo do mundo real: Uma máquina de chicletes: você gira e ela te dá um doce.
- Function → Explicação: É como uma fábrica: você entrega algo e ela devolve algo transformado.
> Exemplo do mundo real: Você dá leite, a fábrica devolve queijo.
- Predicate → Explicação: É como fazer uma pergunta de sim ou não.
> Exemplo do mundo real: "Esse número é par?"
- BinaryOperator → Explicação: É como juntar duas coisas iguais e fazer uma só.
> Exemplo do mundo real: Juntar duas massinhas de cores diferentes e virar uma bola só.
- Generics → são etiquetas nas caixinhas, dizendo o que pode entrar e sair.

---
# Documentação Oficial – Interfaces e Functional Interfaces

## Interfaces
- [Java Language Specification – Chapter 9: Interfaces (Oracle)](https://docs.oracle.com/javase/specs/jls/se8/html/jls-9.html)
- [Tutorial Oficial da Oracle: Creating Interfaces](https://docs.oracle.com/javase/tutorial/java/IandI/createinterface.html)

## Functional Interfaces
- [Documentação oficial da anotação @FunctionalInterface (Java SE 8)](https://docs.oracle.com/javase/8/docs/api/java/lang/FunctionalInterface.html)
- [Pacote java.util.function – Resumo das Functional Interfaces (Java SE 8)](https://docs.oracle.com/javase/8/docs/api/java/util/function/package-summary.html)

## Versões mais recentes (Java SE 21)
- [@FunctionalInterface (Java SE 21)](https://docs.oracle.com/en/java/javase/21/docs/api/java.base/java/lang/FunctionalInterface.html)
- [Pacote java.util.function (Java SE 21)](https://docs.oracle.com/en/java/javase/21/docs/api/java.base/java/util/function/package-summary.html)

