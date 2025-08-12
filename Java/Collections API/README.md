# Collection Framework

## Introdução
- Uma coleção é uma estrutura de dados que serve para agrupar muitos elementos em uma única unidade, estes elementos precisam ser **Objetos** ( ex: Integer e não int).
- Coleções são contêineres que armazenam vários dados como uma única unidade. Por exemplo, se armazenarmos os nomes de todos os funcionários em uma única lista e a nomearmos como Employee, ela formará uma coleção.
As duas interfaces raiz da classe collection Java são:
    - Interface de coleção (java.util.collection)
    - Interface de mapa (java.util.Map)
- Uma **Collection** pode ter coleções homogêneas e heterogeneas, normalmente utilizamos coleções homogêneas de um tipo específico.
- O núcleo principal das coleções é formado pelas interfaces da figura abaixo; essas interfaces permitem manipular a coleção independentemente do nível de detalhe que elas representam.
- Temos quatro grandes tipos de coleções: List (lista), Set (conjunto), Queue (fila) e Map (mapa). A partir dessas interfaces, temos muitas subclasses concretas que implementam várias formas diferentes de se trabalhar com cada coleção.

<img width="1318" height="737" alt="image" src="https://github.com/user-attachments/assets/b42adea8-f741-40b7-b11d-f2621319d6f4" />

> Embora a interface Map não seja filha direta da interface Collection, ela também é considerada uma coleção devido à sua função.

## Objetivos do Collection Framework em Java:
- Para aumentar a eficiência de coleções fundamentais, como matrizes dinâmicas, árvores, listas encadeadas e tabelas de hash, etc.
- Para aumentar a compatibilidade permitindo que todas as coleções funcionem de maneira idêntica.
- Para aumentar a flexibilidade ao estender e/ou adaptar facilmente uma coleção.
- Aumentar a eficiência do código devido à alta otimização da estrutura de coleta.
- Para aumentar a exclusividade dos dados fornecendo a interface definida.
- Para facilitar a organização de dados, armazenando-os em pares chave-valor usando a interface Map.
- Para aumentar a flexibilidade de matrizes usando a classe ArrayList.

## Visão geral do Collections Framework
- O Collections Framework fornece:
   - Interfaces: contratos que definem como as coleções se comportam (List, Set, Map, Queue…).
   - Implementações: classes concretas que realizam essas interfaces (ArrayList, HashSet, HashMap, etc.).
   - Algoritmos utilitários: métodos em Collections e Arrays para ordenar, buscar, embaralhar, etc.
 
>
## [Projeto que usei Collection Framework](https://github.com/andressasmedeiros/exercicio-collections)
---

# List
<img width="1296" height="725" alt="image" src="https://github.com/user-attachments/assets/b6752b30-3d2c-43bd-aeb2-23cffdbdfd42" />

- A interface <code>List</code> é uma coleção ordenada que permite a inclusão de elementos duplicados.
- É um dos tipos de coleção mais utilizados em Java, e as classes de implementação comuns são <code>ArrayList</code> e <code>LinkedList</code>.
- A <code>List</code> se assemelha a uma matriz com comprimento dinâmico, permitindo adicionar ou remover elementos.
- A interface <code>List</code> fornece métodos úteis para adicionar elementos em posições específicas, remover ou substituir elementos com base no índice e obter sublistas usando índices.
- A classe <code>Collections</code> fornece algoritmos úteis para manipulação de <code>List</code>, como ordenação (sort), embaralhamento (shuffle), reversão (reverse) e busca binária (binarySearch).

> ##### *ArrayList*: O ArrayList é uma implementação da interface List que armazena os elementos em uma estrutura de array redimensionável. Isso significa que ele pode crescer automaticamente à medida que novos elementos são adicionados. A principal vantagem do ArrayList é o acesso rápido aos elementos por meio de índices, o que permite recuperar um elemento específico de forma eficiente. No entanto, adicionar ou remover elementos no meio da lista pode ser mais lento, pois requer a realocação de elementos.

> ##### *LinkedList*: O LinkedList é uma implementação da interface List que armazena os elementos em uma lista duplamente vinculada. Cada elemento contém referências para o elemento anterior e próximo na lista. A principal vantagem do LinkedList é a eficiência na adição ou remoção de elementos no início ou no final da lista, pois não é necessário realocar elementos. No entanto, o acesso aos elementos por meio de índices é mais lento, pois requer percorrer a lista até o elemento desejado.

> ##### *Vector*: O Vector é uma implementação antiga da interface List que é semelhante ao ArrayList, mas é sincronizada, ou seja, é thread-safe. Isso significa que várias threads podem manipular um objeto Vector ao mesmo tempo sem causar problemas de concorrência. No entanto, essa sincronização adiciona uma sobrecarga de desempenho, tornando o Vector menos eficiente do que o ArrayList em cenários em que a concorrência não é um problema. Por esse motivo, o uso do Vector é menos comum em aplicações modernas.

Exemplo:
```java
List<String> nomes = new ArrayList<>();
nomes.add("Ana");
nomes.add("Bruno");
nomes.add("Ana"); // duplicado permitido
```
---
# Set
<img width="1132" height="652" alt="image" src="https://github.com/user-attachments/assets/f2531898-1888-4935-97dd-17fdd58ee024" />

- A interface `Set` é uma coleção que não pode conter elementos duplicados.
- Essa interface representa o conceito matemático de um conjunto e é usada para representar conjuntos, como um baralho de cartas.
- A plataforma Java possui três implementações de `Set` de uso geral: `HashSet`, `TreeSet` e `LinkedHashSet`.
- A interface `Set` não permite acesso aleatório a um elemento na coleção.
- Para percorrer os elementos de um `Set`, você pode usar um iterador ou um loop foreach.

> ##### *HashSet*: O HashSet é uma implementação da interface Set que armazena os elementos em uma tabela hash. Ele não mantém uma ordem específica dos elementos. A principal vantagem do HashSet é que ele oferece um desempenho de busca muito eficiente, pois usa funções hash para indexar os elementos. No entanto, a ordem em que os elementos são adicionados pode não ser preservada ao percorrer o conjunto.

> ##### *TreeSet*: O TreeSet é uma implementação da interface Set que armazena os elementos em uma árvore binária balanceada. Isso significa que os elementos são armazenados em uma ordem classificada e são mantidos automaticamente em ordem crescente. A principal vantagem do TreeSet é que os elementos são sempre retornados na ordem classificada, o que facilita a obtenção de elementos em uma determinada ordem. No entanto, a busca e a inserção são um pouco mais lentas em comparação com o HashSet.

> ##### *LinkedHashSet*: O LinkedHashSet é uma implementação da interface Set que mantém a ordem de inserção dos elementos, além de usar uma tabela hash para obter um bom desempenho de busca. Ele é semelhante ao HashSet, mas também mantém uma lista duplamente vinculada que preserva a ordem de inserção. Isso permite que os elementos sejam percorridos na ordem em que foram adicionados. O LinkedHashSet é útil quando você precisa manter a ordem de inserção dos elementos e também ter um bom desempenho de busca.

Exemplo:
```java
Set<Integer> numeros = new HashSet<>();
numeros.add(1);
numeros.add(2);
numeros.add(1); // ignorado
```
---
# Map
<img width="1125" height="640" alt="image" src="https://github.com/user-attachments/assets/1ee1dc85-420d-4a57-acfb-cc2658542192" />

- A interface `Map` é usada para mapear dados na forma de chaves e valores.
- O `Map` do Java é um objeto que mapeia chaves para valores.
- Um `Map` não pode conter chaves duplicadas: cada chave pode mapear no máximo um valor.
- A plataforma Java possui três implementações gerais de `Map`: `HashMap`, `TreeMap` e `LinkedHashMap`.
- As operações básicas do `Map` são: `put` (inserir ou atualizar), `get` (obter), `containsKey` (verificar se contém uma chave), `containsValue` (verificar se contém um valor), `size` (obter o tamanho) e `isEmpty` (verificar se está vazio).

> ##### *HashTable* é uma implementação antiga da interface Map no Java que é sincronizada e thread-safe, tornando-a adequada para uso em ambientes concorrentes. Ela não permite chaves ou valores nulos e os elementos não são mantidos em uma ordem específica.

> ##### *LinkedHashMap*, por outro lado, é uma implementação da interface Map que preserva a ordem de inserção dos elementos. Cada elemento possui referências ao próximo e ao anterior, formando uma lista encadeada. Isso permite que os elementos sejam iterados na ordem em que foram inseridos. Além disso, o LinkedHashMap também permite chaves ou valores nulos.

> ##### *HashMap* é uma implementação da interface Map que não mantém uma ordem específica dos elementos. Ele armazena os elementos internamente usando uma função de hash para melhorar a eficiência das operações de pesquisa e acesso. O HashMap também permite chaves ou valores nulos.


Exemplo:
```java
Map<String, Integer> idades = new HashMap<>();
idades.put("Ana", 25);
idades.put("Bruno", 30);
idades.put("Ana", 26); // sobrescreve o valor anterior
```
---
# Queue
<img width="974" height="542" alt="image" src="https://github.com/user-attachments/assets/18fc9a9a-8e4e-4a1d-affb-2ed1d52fec11" />

- A interface `Queue` representa uma coleção projetada para **armazenar elementos antes de processá-los**, seguindo principalmente o princípio **FIFO** (*First In, First Out*), onde o primeiro elemento inserido é o primeiro a ser removido.
- É amplamente utilizada para **filas de processamento**, **gerenciamento de tarefas** e **sistemas de mensageria**.
- A `Queue` define operações específicas para **inserir, remover e inspecionar elementos** de forma controlada, retornando valores especiais ou exceções em caso de falha, dependendo do método usado.
- A plataforma Java fornece implementações como `LinkedList`, `PriorityQueue` e `ArrayDeque`, cada uma adequada para diferentes necessidades de ordenação e performance.
- Algumas filas podem ordenar elementos de forma natural ou por um `Comparator` definido, como no caso da `PriorityQueue`.
- As operações básicas da Queue são: `add` (adicionar elemento e lançar exceção se não for possível), `offer` (adicionar elemento e retornar false se não for possível), `remove` (remover e retornar o primeiro elemento, lançando exceção se estiver vazia), `poll` (remover e retornar o primeiro elemento ou null se estiver vazia), `element` (obter o primeiro elemento sem remover, lançando exceção se estiver vazia) e `peek` (obter o primeiro elemento sem remover ou null se estiver vazia).

> ##### *LinkedList* Implementa a interface `Queue` usando uma **lista duplamente encadeada**. Oferece boa performance para inserção e remoção nas extremidades, mas acesso lento por índice. Pode ser usada tanto como fila (FIFO) quanto como pilha (LIFO) quando usada via `Deque`.

> ##### *PriorityQueue* Uma fila de prioridade que ordena automaticamente os elementos com base em sua **ordem natural** (via `Comparable`) ou usando um **Comparator** customizado. Não garante ordenação total ao iterar, apenas que o **cabeça da fila** (head) é o elemento com maior prioridade.

> ##### *ArrayDeque* Uma implementação de deque (fila dupla) altamente eficiente, baseada em **array redimensionável**. Permite inserção e remoção em ambas as extremidades da fila com excelente performance.

Exemplo:
```java
Queue<String> fila = new LinkedList<>();
fila.add("Primeiro");
fila.add("Segundo");
System.out.println(fila.poll()); // "Primeiro" sai primeiro
```
---
# Resumo

| Interface | Permite duplicados? | Mantém ordem? | Estrutura interna comum | Uso típico |
|-----------|--------------------|---------------|------------------------|------------|
| **List**  | Sim                | Sim (ordem de inserção) | Array / Lista encadeada | Sequência de elementos com acesso por índice |
| **Set**   | Não                | Depende da implementação | Hash table / Árvore    | Conjunto único de elementos, sem repetição |
| **Queue** | Depende (normalmente sim) | FIFO ou prioridade | Lista / Heap / Array   | Processamento de elementos em ordem ou por prioridade |
| **Map**   | Chaves: Não / Valores: Sim | Depende da implementação | Hash table / Árvore    | Associação de pares chave-valor |

# Quando usar cada um

| Interface | Quando usar | Exemplos práticos |
|-----------|-------------|-------------------|
| **List**  | Quando precisa armazenar elementos em **ordem** e permitir **duplicatas**, com acesso rápido por índice. | Lista de tarefas ordenadas, histórico de páginas visitadas, carrinho de compras onde produtos repetidos são permitidos. |
| **Set**   | Quando precisa garantir que **não haja elementos duplicados** e não se importa necessariamente com a ordem (ou quer ordem controlada). | Lista de e-mails únicos, cadastro de CPFs, conjunto de IDs de produtos sem repetição. |
| **Queue** | Quando precisa processar elementos **na ordem de chegada** (FIFO) ou por **prioridade**. | Fila de impressão, sistema de atendimento (chamando clientes na ordem), processamento de jobs em segundo plano. |
| **Map**   | Quando precisa associar **chaves únicas a valores** para consultas rápidas. | Agenda telefônica (nome → telefone), dicionário (palavra → definição), cache de dados (URL → conteúdo da página). |

---
  - [Informações completas das Collections](https://data-flair.training/blogs/collection-framework-in-java/)
  - [Sumário dos métodos](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/util/Collection.html)

---
> ⚠️ **Observação:** Este módulo de estudos foi desenvolvido com base no curso disponibilizado pela plataforma DIO. Algumas imagens e conteúdos utilizados pertencem à plataforma e são empregados aqui exclusivamente para fins didáticos, visando a fixação do meu aprendizado.
