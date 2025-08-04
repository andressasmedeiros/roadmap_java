# Markdown e Mermaid


> Este guia mostra como usar Markdown e Mermaid com exemplos práticos.

## Introdução
- O Markdown é uma linguagem de marcação leve, amplamente utilizada para criar documentação, READMEs e conteúdo em plataformas como GitHub, GitLab e Bitbucket.

## Sintaxe Básica do Markdown

### 1. Títulos
- Utilizamos # na frente dos títulos. A quantidade de # determina o tamanho do título.
```
# Título 1
## Título 2
### Título 3
#### Título 4
```
- Resultado:
# Título 1
## Título 2
### Título 3
#### Título 4
--- 

### 2. Texto
- Para deixar negrito, itálico, texto riscado e código inline
```
  **Negrito**  
*Itálico*  
~~Texto riscado~~  
`Código inline`
```
- Resultado:
**Negrito**  
*Itálico*  
~~Texto riscado~~  
`Código inline`
---

### 3. Listas e citações
- Para efeito lista usamos - e numerações 1 e citação usamos >
```
- Item 1
- Item 2
  - Subitem
1. Item numerado
2. Outro item
> Citação 1
>
> Citação 2
```
- Resultado:
- Item 1
- Item 2
  - Subitem
1. Item numerado
2. Outro item
> Citação 1
> 
> Citação 2
> 
---

### 4. Links e imagens
- O markdown não suporta vídeos diretos, apenas gifs. Para usar gifs você deve ter eles importado dentro da pasta.
```
[Visite o GitHub](https://github.com)

<img width="1300" height="650" alt="image" src="https://github.com/user-attachments/assets/e1fedc76-72a3-4999-a1e7-2d5f2ce04168" />

![Demonstração da aplicação](assets/spock-star-trek.gif)

```
- Resultado:
[Visite o GitHub](https://github.com)

<img width="300" height="300" alt="image" src="https://github.com/user-attachments/assets/e1fedc76-72a3-4999-a1e7-2d5f2ce04168" />

![Demonstração da aplicação](assets/spock-star-trek.gif)
---

### Blocos de código
- Você adicionar ``` em cima e em baixo da parte que quer que vire código, e pode colocar uma anotação como bash ou java para diferenciar da seguinte forma:
<img width="321" height="137" alt="image" src="https://github.com/user-attachments/assets/e084ae2a-9406-4948-98a0-02170aa4365f" />

- Resultado Com Java e Bash e json:
```java
public class HelloWorld {
    public static void main(String[] args) {
        System.out.println("Olá, Mundo!");
    }
}
```
```bash
public class HelloWorld {
    public static void main(String[] args) {
        System.out.println("Olá, Mundo!");
    }
}
```
```json
{
  "id": 1,
  "nome": "Mateus",
  "email": "mateus@email.com"
}
```
--- 
### Tabelas
- Você faz da seguinte forma:
```
<table>
  <tr>
    <th>Nome</th>
    <th>Idade</th>
    <th>Cidade</th>
  </tr>
  <tr>
    <td>Joaquim</td>
    <td>32</td>
    <td>Curitiba</td>
  </tr>
  <tr>
    <td>Ana</td>
    <td>25</td>
    <td>São Paulo</td>
  </tr>
</table>

```
- Resultado:
<table>
  <tr>
    <th>Nome</th>
    <th>Idade</th>
    <th>Cidade</th>
  </tr>
  <tr>
    <td>Joaquim</td>
    <td>32</td>
    <td>Curitiba</td>
  </tr>
  <tr>
    <td>Ana</td>
    <td>25</td>
    <td>São Paulo</td>
  </tr>
</table>

  > Dá pra utilizar de algumas anotações HTML
 ---
### Links com botões
```java
<p align="center">
  <a href="https://github.com" target="_blank">
    <img src="https://img.shields.io/badge/GitHub-Acessar%20Repositório-black?style=for-the-badge&logo=github">
  </a>
</p>
```
- Resultado:
<p align="center">
  <a href="https://github.com/andressasmedeiros" target="_blank">
    <img src="https://img.shields.io/badge/GitHub-Acessar%20Repositório-black?style=for-the-badge&logo=github">
  </a>
</p>

---

### Colapsar conteúdo (toggle)

```java
<details>
  <summary>📜 Clique para expandir</summary>
  <p>Esse texto fica oculto até o usuário clicar.</p>
</details>
```
- Resultado:
<details>
  <summary>📜 Clique para expandir</summary>
  <p>Esse texto fica oculto até o usuário clicar.</p>
</details>

---

### Layouts customizados
```
<div style="display: flex; justify-content: space-around;">
  <img src="https://github.githubassets.com/images/modules/logos_page/GitHub-Mark.png" width="120">
  <img src="https://avatars.githubusercontent.com/u/9919?s=200&v=4" width="120">
</div>

```

- Resultado:
<div style="display: flex; justify-content: space-around;">
  <img src="https://github.githubassets.com/images/modules/logos_page/GitHub-Mark.png" width="120">
  <img src="https://avatars.githubusercontent.com/u/9919?s=200&v=4" width="120">
</div>

---

### Badges (etiquetas)
```
![Status](https://img.shields.io/badge/status-online-brightgreen)
![Versão](https://img.shields.io/badge/versão-1.0-blue)
```

- Resultado:

![Status](https://img.shields.io/badge/status-online-brightgreen)
![Versão](https://img.shields.io/badge/versão-1.0-blue)

--- 

# Mermaid

## Introdução
- O Mermaid é uma extensão compatível com Markdown que permite criar diagramas e gráficos diretamente em arquivos .md usando código simples e intuitivo.

### Fluxograma (Flowchart)
```
```mermaid
flowchart TD
    A[Início] --> B{Decisão?}
    B -- Sim --> C[Ação 1]
    B -- Não --> D[Ação 2]
    C --> E[Fim]
    D --> E
```

- Resultado:
```mermaid
flowchart TD
    A[Início] --> B{Decisão?}
    B -- Sim --> C[Ação 1]
    B -- Não --> D[Ação 2]
    C --> E[Fim]
    D --> E
```

---

### Diagrama de sequência
```
```mermaid
sequenceDiagram
    Alice->>Bob: Olá Bob, tudo bem?
    Bob-->>Alice: Tudo ótimo!
    Alice-)Bob: Vamos marcar uma reunião
```
- Resultado:
```mermaid
sequenceDiagram
    Alice->>Bob: Olá Bob, tudo bem?
    Bob-->>Alice: Tudo ótimo!
    Alice-)Bob: Vamos marcar uma reunião
```

--- 

### Diagrama de classe
```
```mermaid
classDiagram
    Animal <|-- Cachorro
    Animal <|-- Gato
    Animal: +String nome
    Animal: +falar()
    Cachorro: +latir()
    Gato: +miar()
```

- Resultado:
```mermaid
classDiagram
    Animal <|-- Cachorro
    Animal <|-- Gato
    Animal: +String nome
    Animal: +falar()
    Cachorro: +latir()
    Gato: +miar()
```

### Gráfico de Gantt (para cronogramas)
```
```mermaid
gantt
    title Projeto Exemplo
    dateFormat  YYYY-MM-DD
    section Planejamento
    Tarefa A :done,    a1, 2025-08-01, 3d
    Tarefa B :active,  a2, 2025-08-04, 5d
    section Execução
    Tarefa C :         a3, after a2, 4d
```

- Resultado:
```mermaid
gantt
    title Projeto Exemplo
    dateFormat  YYYY-MM-DD
    section Planejamento
    Tarefa A :done,    a1, 2025-08-01, 3d
    Tarefa B :active,  a2, 2025-08-04, 5d
    section Execução
    Tarefa C :         a3, after a2, 4d
```

---
>  https://mermaid.js.org/ onde você encontra a documentação completa, tutoriais, guias de sintaxe
---
