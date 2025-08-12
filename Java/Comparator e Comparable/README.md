# Comparable x Comparator

## Introdução
- Tanto Comparable quanto Comparator são interfaces do Java utilizadas para definir regras de comparação e ordenação de objetos.
> *Interface* é um tipo de referência que define um contrato: um conjunto de métodos que uma classe deve implementar. Interfaces são usadas para especificar o que uma classe deve fazer, mas não como ela deve fazer. Ao implementar uma interface, a classe se compromete a fornecer o código para todos os métodos definidos nela.

## Comparable

- `Comparable` fornece uma única sequência de ordenação. Em outras palavras, podemos ordenar a coleção com base em um único elemento, como id, nome e preço.
- `Comparable` afeta a classe original, ou seja, a classe atual é modificada.
- `Comparable` fornece o método `compareTo()` para ordenar elementos.
- `Comparable` está presente no pacote `java.lang`.
- Podemos ordenar os elementos da lista do tipo `Comparable` usando o método `Collections.sort(List)`.

## Comparator

- O `Comparator` fornece o método `compare()` para ordenar elementos.
- O `Comparator` fornece múltiplas sequências de ordenação. Em outras palavras, podemos ordenar a coleção com base em múltiplos elementos, como id, nome, preço, etc.
- O `Comparator` não afeta a classe original, ou seja, a classe atual não é modificada.
- Um `Comparator` está presente no pacote `java.util`.
- Podemos ordenar os elementos da lista do tipo `Comparator` usando o método `Collections.sort(List, Comparator)`.

[Respositório que usei Comparable e Comparator](https://github.com/andressasmedeiros/exercicio-collections)
---
Exemplo:
```java
import java.util.*;

// Classe Produto implementa Comparable (ordem natural por nome)
class Produto implements Comparable<Produto> {
    private String nome;
    private double preco;

    public Produto(String nome, double preco) {
        this.nome = nome;
        this.preco = preco;
    }

    public String getNome() {
        return nome;
    }
    public double getPreco() {
        return preco;
    }

    // Define a ordem natural (por nome)
    @Override
    public int compareTo(Produto outro) {
        return this.nome.compareTo(outro.nome);
    }

    @Override
    public String toString() {
        return nome + " - R$" + preco;
    }
}

// Comparator para ordenar por preço
class CompararPorPreco implements Comparator<Produto> {
    @Override
    public int compare(Produto p1, Produto p2) {
        return Double.compare(p1.getPreco(), p2.getPreco());
    }
}

public class Main {
    public static void main(String[] args) {
        List<Produto> produtos = new ArrayList<>();
        produtos.add(new Produto("Notebook", 3500.0));
        produtos.add(new Produto("Teclado", 150.0));
        produtos.add(new Produto("Mouse", 80.0));

        System.out.println("Lista original:");
        System.out.println(produtos);

        // Ordenando com Comparable (ordem natural por nome)
        Collections.sort(produtos);
        System.out.println("\nOrdenado por nome (Comparable):");
        System.out.println(produtos);

        // Ordenando com Comparator (por preço)
        Collections.sort(produtos, new CompararPorPreco());
        System.out.println("\nOrdenado por preço (Comparator):");
        System.out.println(produtos);
    }
}
```
### Comparable<Produto>
- Implementado na classe Produto.
- Define a ordem natural (por nome).

### Comparator<Produto>
- Criamos a classe CompararPorPreco.
- Define uma ordem alternativa (por preço).

### Collections.sort()
- Faz a ordenação da lista usando a lógica definida no Comparable ou Comparator.

---

## Collections

- A classe `Collections` é uma classe utilitária do Java para operações comuns em coleções.
- É uma classe utilitária do pacote java.util.
- É uma classe utilitária do pacote java.util.
- Fornece métodos estáticos para operar sobre coleções, como:
   - sort() — ordenar listas.
   - reverseOrder() — criar um comparador para ordem reversa.
   - shuffle() — embaralhar elementos.
   - binarySearch() — busca binária.
> Não é uma interface nem uma estrutura de dados — ela não armazena dados, apenas manipula outras coleções.

---
# Comparação

| Característica        | Comparable                                      | Comparator                                      |
|-----------------------|-------------------------------------------------|-------------------------------------------------|
| **Pacote**            | `java.lang`                                     | `java.util`                                     |
| **Método principal**  | `compareTo(T o)`                                | `compare(T o1, T o2)`                           |
| **Objetivo**          | Define a **ordem natural** do objeto            | Define uma **ordem personalizada**              |
| **Onde é implementado** | Na **própria classe** do objeto                | Em uma **classe separada** (ou expressão lambda)|
| **Número de ordenações possíveis** | Apenas **uma** (a ordem natural definida na classe) | **Várias** (cada Comparator define uma lógica diferente) |
| **Uso comum**         | Ordenação padrão em coleções (`Collections.sort(lista)`) | Ordenações alternativas sem alterar a classe   |
| **Necessita modificar a classe original?** | Sim, é preciso alterar a classe para implementar `Comparable` | Não, funciona mesmo sem alterar a classe       |
| **Quando usar**       | Quando há **uma ordem principal** que sempre será usada para comparação, como nome de produto, ID, matrícula | Quando precisa de **mais de um critério de ordenação** ou não pode/quer modificar a classe original |

---
> ⚠️ **Observação:** Este módulo de estudos foi desenvolvido com base no curso disponibilizado pela plataforma DIO. Algumas imagens e conteúdos utilizados pertencem à plataforma e são empregados aqui exclusivamente para fins didáticos, visando a fixação do meu aprendizado.

