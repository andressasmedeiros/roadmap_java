# `equals()` e `hashCode()` — Essenciais para coleções no Java

Quando trabalhamos com coleções como `HashSet`, `HashMap` ou qualquer outra baseada em **hash**, é fundamental sobrescrever corretamente os métodos `equals()` e `hashCode()` para garantir que a comparação de objetos e a busca funcionem de forma consistente.

---

## O que é `equals()`?
- Método herdado de `Object`.
- Usado para **comparar se dois objetos são logicamente iguais**.
- Por padrão, compara referências (endereços de memória), mas pode ser sobrescrito para comparar atributos.

---

## O que é `hashCode()`?
- Também herdado de `Object`.
- Retorna um número inteiro (código de hash) usado por coleções baseadas em hash para organizar e buscar elementos rapidamente.
- **Contrato importante**:  
  1. Se `a.equals(b)` é **true**, então `a.hashCode() == b.hashCode()` **deve** ser true.  
  2. Se `a.equals(b)` é **false**, `a.hashCode()` **pode** ser igual ou diferente (mas diferente ajuda na performance).

---

## Problema ao não sobrescrever
```java
import java.util.HashSet;

class Pessoa {
    String nome;
    int idade;

    public Pessoa(String nome, int idade) {
        this.nome = nome;
        this.idade = idade;
    }
}

public class Main {
    public static void main(String[] args) {
        HashSet<Pessoa> pessoas = new HashSet<>();
        pessoas.add(new Pessoa("Ana", 25));
        pessoas.add(new Pessoa("Ana", 25));

        System.out.println(pessoas.size()); // Resultado: 2 (esperávamos 1)
    }
}
```
> Isso acontece porque, por padrão, `equals()` e `hashCode()` não foram sobrescritos, e a comparação está usando referência de memória.

---

## Solução: sobrescrever `equals()` e `hashCode()`
```java
import java.util.Objects;

class Pessoa {
    String nome;
    int idade;

    public Pessoa(String nome, int idade) {
        this.nome = nome;
        this.idade = idade;
    }

    @Override
    public boolean equals(Object o) {
        if (this == o) return true; // mesma referência
        if (o == null || getClass() != o.getClass()) return false;
        Pessoa pessoa = (Pessoa) o;
        return idade == pessoa.idade && Objects.equals(nome, pessoa.nome);
    }

    @Override
    public int hashCode() {
        return Objects.hash(nome, idade);
    }
}

public class Main {
    public static void main(String[] args) {
        HashSet<Pessoa> pessoas = new HashSet<>();
        pessoas.add(new Pessoa("Ana", 25));
        pessoas.add(new Pessoa("Ana", 25));

        System.out.println(pessoas.size()); // Resultado: 1 (agora funciona como esperado)
    }
}
```

---

## Resumo rápido
- `equals()` → Define **quando dois objetos são iguais**.
- `hashCode()` → Garante que coleções baseadas em hash funcionem corretamente.
- **Regra de ouro**: Sempre que sobrescrever `equals()`, também sobrescreva `hashCode()`.
- Juntos → fazem coleções como `HashSet` e `HashMap` funcionarem rápido e corretamente.

---
<br><br>


# Resumo didático

Imagina que você tem uma **caixa de brinquedos** e quer saber se um brinquedo já está lá dentro antes de colocar.

- O **`equals()`** é como **comparar o brinquedo que você quer colocar com os que já estão na caixa** para ver se eles são **iguais**.
- O **`hashCode()`** é como **um número secreto ou etiqueta** que o brinquedo tem colado nele, para ajudar você a achar o brinquedo mais rápido na caixa.


Por que precisa dos dois?
- Quando você coloca um brinquedo na caixa (ex.: `HashSet`), o Java **primeiro olha a etiqueta** (`hashCode()`) para encontrar o possível lugar dele.
- Depois, **confirma se é o mesmo brinquedo** usando o `equals()`.

Se o **número da etiqueta não bater**, ele nem perde tempo comparando.  
Se o **número da etiqueta bater**, ele usa o `equals()` para ter certeza.

---

## Comparação entre `equals()` e `hashCode()`

| Característica        | `equals()` | `hashCode()` |
|-----------------------|------------|--------------|
| **O que faz**         | Diz se dois objetos são iguais. | Dá um número (código de hash) para ajudar a localizar o objeto. |
| **Retorno**           | `true` ou `false` | Um número inteiro (`int`). |
| **Baseado em**        | Comparação de atributos. | Cálculo numérico a partir dos atributos. |
| **Quando é chamado**  | Depois que os códigos de hash são iguais, para confirmar. | Primeiro passo em coleções baseadas em hash (como `HashSet`, `HashMap`). |
| **Regra importante**  | Se `equals()` é `true`, os `hashCode()` devem ser iguais. | Pode ter objetos diferentes com o mesmo `hashCode()` (mas não é bom para performance). |

---

**Dica**: Use `Objects.equals()` e `Objects.hash()` para simplificar e evitar erros.
