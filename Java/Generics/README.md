# Generics

## O que são Generics?
Um **tipo genérico** é uma **classe** ou **interface** que é **parametrizada em relação a tipos**.  
Eles permitem criar código que funciona com **qualquer tipo de dado** de forma segura, evitando casts desnecessários e erros de tipo em tempo de execução.

---

## Exemplo inicial — Sem Generics
```java
public class Box {
    private Object object;

    public void set(Object object) { this.object = object; }
    public Object get() { return object; }
}
```
> Problema: É necessário fazer *casting* ao recuperar o valor, e erros de tipo só aparecem em **tempo de execução**.

---

## Atualizando para usar Generics
O símbolo `<>` é chamado de **diamond** ou **diamond operator**.  
Foi introduzido no **Java 7** e serve para **inferir automaticamente o tipo** com base no contexto.

Ao transformar a classe `Box` para ser genérica, alteramos:
public class Box
para:
public class Box<T>

---

## Versão Genérica da Classe Box
```java
/**
 * Versão genérica da classe Box.
 * @param <T> o tipo do valor sendo armazenado
 */
public class Box<T> {
    // T representa "Type" (tipo)
    private T t;

    public void set(T t) { this.t = t; }
    public T get() { return t; }
}
```
Agora, todas as ocorrências de `Object` foram substituídas por `T`.

---

## Variáveis de Tipo Comuns
| Letra | Significado | Uso comum |
|-------|-------------|-----------|
| **E** | Element     | Usado extensivamente no Java Collections Framework |
| **K** | Key         | Representa uma chave em um Map |
| **N** | Number      | Usado para números (Integer, Double, etc.) |
| **T** | Type        | Tipo genérico principal |
| **V** | Value       | Representa valor em um Map |
| **S, U, V...** | Segundo, terceiro, quarto tipos | Quando há mais de um tipo genérico |

> Uma variável de tipo pode ser qualquer tipo **não primitivo**: classe, interface, array ou até outra variável de tipo.

---

## Vantagens de usar Generics em Collections
1. **Segurança do tipo de dados:**  
   Garante que apenas objetos de um tipo específico possam ser adicionados à coleção.
2. **Código mais legível:**  
   Especifica o tipo de dados esperado/retornado, tornando o código mais claro.
3. **Detecção de erros mais cedo:**  
   O compilador identifica erros de tipo já na compilação.
4. **Reutilização de código:**  
   Uma única classe ou método genérico pode funcionar com diferentes tipos.
5. **Melhor desempenho:**  
   Evita casts desnecessários e permite otimizações pelo compilador.

---

## Exemplo de uso com Collections
```java
List<String> nomes = new ArrayList<>(); 
nomes.add("Ana");
nomes.add("Bruno");
// nomes.add(10); // Erro em tempo de compilação
```
> Aqui, `List<String>` garante que apenas Strings podem ser inseridas.

---

📌 **Resumo:**  
Generics tornam o código mais **seguro, reutilizável e legível**, sendo amplamente utilizados no **Java Collections Framework** e em APIs modernas.

--- 
<br><br>


# Exemplos bem didáticos:
 **Voltando à metáfora da caixa**  
Se você cria a caixa, mas não sabe ainda o que vai guardar nela, você coloca um rótulo genérico:

```java
public class Caixa<T> {
    private T item;

    public void setItem(T item) {
        this.item = item;
    }

    public T getItem() {
        return item;
    }
}
```
Aqui o **`T`** é como dizer:  
> "Não sei ainda o que vai aqui dentro, mas quando alguém for usar, vai dizer qual é o tipo."

---

**Quando você usa a caixa, você decide o tipo**
```java
Caixa<String> caixaDeStrings = new Caixa<>();
caixaDeStrings.setItem("Olá mundo"); // T virou String

Caixa<Integer> caixaDeInteiros = new Caixa<>();
caixaDeInteiros.setItem(42); // T virou Integer
```
No primeiro caso, **`T`** foi substituído por `String`.  
No segundo caso, **`T`** foi substituído por `Integer`.

### `E` — *Element* (usado em coleções)
```java
public class ListaPersonalizada<E> {
    private List<E> elementos = new ArrayList<>();

    public void adicionar(E elemento) {
        elementos.add(elemento);
    }

    public E get(int indice) {
        return elementos.get(indice);
    }
}
```
Uso:
```java
ListaPersonalizada<String> listaDeNomes = new ListaPersonalizada<>();
listaDeNomes.adicionar("Ana");
listaDeNomes.adicionar("Bruno");

ListaPersonalizada<Integer> listaDeNumeros = new ListaPersonalizada<>();
listaDeNumeros.adicionar(10);
listaDeNumeros.adicionar(20);
```
---

### `K` e `V` — *Key* (chave) e *Value* (valor)
```java
public class Par<K, V> {
    private K chave;
    private V valor;

    public Par(K chave, V valor) {
        this.chave = chave;
        this.valor = valor;
    }

    public K getChave() { return chave; }
    public V getValor() { return valor; }
}
```
Uso:
```java
Par<String, Integer> idadePessoa = new Par<>("João", 30);
Par<Integer, String> codigoProduto = new Par<>(101, "Notebook");
```
---

### `N` — *Number*
```java
public class Calculadora<N extends Number> {
    public double somar(N a, N b) {
        return a.doubleValue() + b.doubleValue();
    }
}
```
Uso:
```java
Calculadora<Integer> calcInt = new Calculadora<>();
System.out.println(calcInt.somar(5, 10)); // 15.0

Calculadora<Double> calcDouble = new Calculadora<>();
System.out.println(calcDouble.somar(2.5, 3.7)); // 6.2
```

---
> ⚠️ **Observação:** Este módulo de estudos foi desenvolvido com base no curso disponibilizado pela plataforma DIO. Algumas imagens e conteúdos utilizados pertencem à plataforma e são empregados aqui exclusivamente para fins didáticos, visando a fixação do meu aprendizado.
