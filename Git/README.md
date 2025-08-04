# Git, Github, GitFlow e GitLab

## O que é Git?
<img width="312" height="312" alt="image" src="https://github.com/user-attachments/assets/f076e19b-2858-49ab-ba98-e875de0469ec" />

- Git é um sistema de controle de versão distribuído que permite gerenciar alterações em arquivos e coordenar o trabalho entre várias pessoas em um mesmo projeto.
- Principais características:
  - Histórico de alterações
  - Trabalho offline e remoto
  - Branches (ramificações) para desenvolvimento paralelo
  - Combinação e resolução de conflitos
 
## O que é GitHub?
<img width="280" height="280" alt="image" src="https://github.com/user-attachments/assets/3add66fb-533e-4463-bd8e-86fef6b51a22" />


- GitHub é uma plataforma de hospedagem de repositórios Git na nuvem, com funcionalidades adicionais, como:
  - Pull Requests
  - Issues para rastreamento de tarefas
  - Integração com CI/CD (GitHub Actions)
  - Comunidade para colaboração em código aberto
  > Quando usar: Ideal para projetos open-source ou privados com forte integração à comunidade, ampla compatibilidade com ferramentas externas e versionamento online.

## O que é GitLab?
<img width="282" height="282" alt="image" src="https://github.com/user-attachments/assets/d071b553-5fd3-473e-9a53-42618ba5bc16" />

- GitLab é uma plataforma semelhante ao GitHub, mas com foco em DevOps integrado, oferecendo:
  - Repositórios Git
  - Gestão de projetos
  - CI/CD nativo
  - Hospedagem própria ou em nuvem
    > Quando usar: Indicado para empresas que buscam mais controle e personalização, hospedagem self-managed ou pipelines de CI/CD robustos integrados diretamente à plataforma.

## O que é Git Flow?
<img width="601" height="300" alt="image" src="https://github.com/user-attachments/assets/feb0e2fa-af34-45ed-a902-c389f3ba7cf7" />


- Git Flow é um modelo de fluxo de trabalho para organização de branches em um projeto, geralmente usado com Git. Ele define convenções e processos para:
  - Branch principal (main ou master) – versão estável
  - Branch de desenvolvimento (develop)
  - Branches temporárias:
    1. feature/* – novas funcionalidades
    2. release/* – preparação para release
    3. hotfix/* – correções urgentes em produção
    > Quando usar: Projetos com ciclos de release bem definidos, equipes grandes e múltiplas funcionalidades em paralelo.

---
<br><br>

# Principais Conceitos do Git

## .gitignore
 - Define arquivos/pastas que não devem ser versionados (ex.: build, cache, senhas).
```bash
node_modules/
.env
dist/
*.log
```

## Branch (Ramificação)

- **O que é:**  
Uma **branch** é como uma "linha do tempo paralela" dentro do seu projeto. Ela permite que você trabalhe em novas funcionalidades, correções ou experimentos sem interferir diretamente no código principal (`main` ou `master`).

- **Pra que serve:**  
Permite desenvolver funcionalidades em paralelo, testar ideias e corrigir bugs sem quebrar a versão estável do projeto.

- **Exemplo de uso:**
```bash
git checkout -b nova-feature
```

## Stash (Armazenamento temporário)

- **O que é:**  
O **stash** é como uma "gaveta temporária" onde você pode guardar alterações não commitadas para limpar sua área de trabalho e voltar a um estado limpo, sem perder o que já fez.

- **Pra que serve:**  
Quando você precisa trocar de branch ou atualizar o repositório sem ainda querer criar um commit com suas alterações inacabadas.

- **Exemplo de uso:**
```bash
git stash
git stash pop
```

---

## Tag (Etiqueta de versão)

- **O que é:**  
Uma **tag** é um marcador fixo para identificar um ponto específico na linha do tempo do projeto, geralmente usado para sinalizar versões de lançamento (ex.: `v1.0`, `v2.5`).

- **Pra que serve:**  
Ajuda a identificar versões estáveis ou importantes, permitindo voltar ou distribuir essas versões facilmente.

- **Exemplo de uso:**
```bash
git tag -a v1.0 -m "Versão 1.0 estável"
git push origin v1.0
```

---

## Commit

- **O que é:**  
Um **commit** é um "registro" ou "foto" do estado dos arquivos no repositório em um determinado momento.

- **Pra que serve:**  
Permite rastrear o histórico de alterações, voltar a versões anteriores e colaborar com outros desenvolvedores.

- **Exemplo de uso:**
```bash
git commit -m "Adiciona nova funcionalidade de login"
```

---

## Merge

- **O que é:**  
O **merge** combina as alterações de uma branch com outra, geralmente para trazer o trabalho de uma branch de desenvolvimento para a principal (`main`).

- **Pra que serve:**  
Integra código desenvolvido separadamente, unindo histórico e alterações.

- **Exemplo de uso:**
```bash
git checkout main
git merge nova-feature
```

---

## Rebase

- **O que é:**  
O **rebase** reescreve o histórico da sua branch para parecer que foi criado a partir da última versão da branch base (ex.: `main`).

- **Pra que serve:**  
Mantém o histórico linear e organizado, evitando merges complexos.

- **Exemplo de uso:**
```bash
git checkout minha-branch
git rebase main
```

---

## Remote

- **O que é:**  
Um **remote** é uma referência a um repositório hospedado em um servidor (como GitHub, GitLab ou Bitbucket).

- **Pra que serve:**  
Permite sincronizar alterações locais com o repositório remoto (`push`, `pull`, `fetch`) e colaborar com outros desenvolvedores.

---

## HEAD

- **O que é:**  
O **HEAD** é um ponteiro para o commit atual em que você está trabalhando dentro do repositório.

- **Pra que serve:**  
Indica qual é a base para novos commits, merges e resets.

---

## Stage (Área de preparação)

- **O que é:**  
O **stage** é uma área intermediária onde você adiciona alterações que deseja incluir no próximo commit.

- **Pra que serve:**  
Permite selecionar quais modificações vão ser commitadas, evitando enviar tudo de uma vez.

- **Exemplo de uso:**
```bash
git add arquivo.txt
```

---
<br><br>

## 1. Boas Práticas de Uso do Git
### 1.1 Commits

- Faça commits **pequenos e frequentes**, facilitando rastrear mudanças.
- Use mensagens de commit **claras e descritivas**, indicando a intenção da alteração.
- Utilize o padrão **Conventional Commits** quando possível:
  - `feat:` para novas funcionalidades
  - `fix:` para correções de bugs
  - `docs:` para alterações de documentação
  - `refactor:` para melhorias de código sem mudança de comportamento
  - `test:` para adição ou modificação de testes
  - `chore:` para mudanças que não afetam código de produção

**Exemplo:**
```bash
git commit -m "feat: adiciona página de login com autenticação JWT"
```

### 1.2 Branches

- Sempre crie branches para desenvolver novas funcionalidades ou correções.
- Nomeie branches de forma descritiva, por exemplo:
  - `feature/nome-da-funcionalidade`
  - `bugfix/corrige-bug-login`
  - `hotfix/erro-producao`
- Atualize a branch com frequência usando `git pull` ou `git rebase` para evitar conflitos grandes.

### 1.3 Pull Requests / Merge Requests

- Revise o código antes de mesclar (`review`).
- Faça testes para garantir que a branch não quebra o projeto principal.
- Evite commits desnecessários como "teste", "corrigindo bug", prefira mensagens objetivas.

<br>
## 2. Resolução de Conflitos no Git

### 2.1 O que é um conflito?

Um conflito ocorre quando duas ou mais alterações afetam a **mesma parte de um arquivo**, e o Git não consegue decidir qual versão manter. Geralmente acontece durante `merge`, `pull` ou `rebase`.

---

### 2.2 Passos para identificar conflitos

1. Execute:
```bash
git status
```
O Git listará os arquivos com conflitos.

2. Abra o arquivo e procure os marcadores:
```text
<<<<<<< HEAD
Código da sua branch
=======
Código da outra branch
>>>>>>> nome-da-branch
```

---

### 2.3 Como resolver

1. Edite o arquivo, escolha a versão correta (ou combine as duas) e remova os marcadores `<<<<<<<`, `=======`, `>>>>>>>`.

2. Após corrigir todos os conflitos, adicione as mudanças:
```bash
git add nome-do-arquivo
```

3. Finalize o merge ou rebase:
```bash
git commit
```
*(no caso de rebase, use `git rebase --continue`)*

---

### 2.4 Dicas para evitar conflitos

- Atualize frequentemente sua branch:
```bash
git pull origin main
```
ou
```bash
git fetch && git rebase origin/main
```

- Trabalhe em arquivos diferentes sempre que possível.
- Use commits pequenos e claros para facilitar a análise de conflitos.
- Combine as alterações em equipe antes de um merge grande.

---

<br><br>

## Configurar o Git no seu computador com chave SSH
- Execute o comando abaixo (substitua seu e-mail do GitHub/GitLab):
```
  ssh-keygen -t ed25519 -C "seu-email@exemplo.com"
```
- Caso seu sistema não suporte ed25519, utilize:
```
ssh-keygen -t rsa -b 4096 -C "seu-email@exemplo.com"
```
- Adicione sua chave ao agente:
```
 ssh-add ~/.ssh/id_ed25519
```

## Copiar a chave pública
- Para copiar a chave para sua área de transferência:

- Linux/macOS:

```bash
cat ~/.ssh/id_ed25519.pub | pbcopy
```
- ou
```bash
xclip -sel clip < ~/.ssh/id_ed25519.pub
```

- Windows (Git Bash):

```bash
cat ~/.ssh/id_ed25519.pub | clip
```

## Adicionar a chave SSH no GitHub ou GitLab
- No GitHub:
  1. Acesse Configurações SSH do GitHub
  2. Clique em New SSH key
  3. Cole sua chave pública e salve.

- No GitLab:
  1. Vá até Preferences > SSH Keys ou GitLab SSH Keys
  2. Cole a chave pública.
  3. Salve.
 
## Configurar o repositório para usar SSH
- Se o seu repositório estiver usando HTTPS, altere a URL para SSH:
   - Git
```bash
  git remote set-url origin git@github.com:usuario/repo.git
```
  - GitLab:
```bash
git remote set-url origin git@gitlab.com:usuario/repo.git
```

---
<br><br>

## Fluxo básico de uso com Git Flow
- Inicializar o Git Flow
```bash
git flow init

```
- Criar branch de feature:
```bash
git flow feature start minha-feature
```
- Finalizar feature:
```bash
git flow feature finish minha-feature
```
- Criar release:
```bash
git flow release start 1.0.0
git flow release finish 1.0.0
```
- Criar hotfix:
```bash
git flow hotfix start correção-urgente
git flow hotfix finish correção-urgente
```
---
<br><br>

## Principais comandos Git
- Inicializa um novo repositório local
```bash
git init
```
- Clona um repositório remoto para a máquina local
```bash
git clone <url>
```

---
<br><br>
## Status e Visualização

- Mostra o estado atual dos arquivos no repositório
```bash
git status
```

- Exibe o histórico de commits
```bash
git log
```

- Exibe o histórico resumido de commits
```bash
git log --oneline
```

- Mostra alterações não adicionadas ao stage
```bash
git diff
```

- Mostra alterações já adicionadas ao stage
```bash
git diff --staged
```

- Mostra detalhes de um commit específico
```bash
git show <hash>
```
<br><br>
## Controle de Alterações

- Adiciona arquivo ao stage
```bash
git add <arquivo>
```

- Adiciona todos os arquivos modificados ao stage
```bash
git add .
```

- Remove um arquivo do stage sem descartar alterações
```bash
git reset <arquivo>
```

- Cria um commit com mensagem
```bash
git commit -m "mensagem"
```

- Modifica o último commit
```bash
git commit --amend
```

- Restaura um arquivo para o último estado commitado
```bash
git restore <arquivo>
```

- Remove arquivo do stage
```bash
git restore --staged <arquivo>
```

---
<br><br>

## Branches

- Lista todas as branches locais
```bash
git branch
```

- Cria uma nova branch
```bash
git branch <nome>
```

- Alterna para a branch especificada
```bash
git checkout <branch>
```

- Cria e muda para uma nova branch
```bash
git checkout -b <branch>
```

- Alternativa para checkout
```bash
git switch <branch>
```

- Mescla outra branch na atual
```bash
git merge <branch>
```

- Reaplica commits da branch atual sobre outra
```bash
git rebase <branch>
```

- Deleta branch local
```bash
git branch -d <branch>
```

- Força a exclusão da branch
```bash
git branch -D <branch>
```

---
<br><br>

## Trabalhando com Remotos

- Lista repositórios remotos configurados
```bash
git remote -v
```

- Adiciona um repositório remoto
```bash
git remote add origin <url>
```

- Remove um repositório remoto
```bash
git remote remove <nome>
```

- Envia commits para o repositório remoto
```bash
git push origin <branch>
```

- Configura a branch local para rastrear a remota
```bash
git push -u origin <branch>
```

- Atualiza branch local com alterações do remoto
```bash
git pull
```

- Busca alterações do remoto sem mesclar
```bash
git fetch
```

- Altera a URL do repositório remoto
```bash
git remote set-url origin <url>
```

---
<br><br>

## Tags

- Lista todas as tags
```bash
git tag
```

- Cria uma nova tag
```bash
git tag <nome>
```

- Cria uma tag anotada
```bash
git tag -a <nome> -m "mensagem"
```

- Mostra detalhes da tag
```bash
git show <tag>
```

- Envia uma tag para o repositório remoto
```bash
git push origin <tag>
```

- Envia todas as tags para o repositório remoto
```bash
git push origin --tags
```

---
<br><br>

## Stash

- Salva alterações temporariamente
```bash
git stash
```

- Salva alterações com descrição
```bash
git stash save "mensagem"
```

- Lista todos os stashes
```bash
git stash list
```

- Aplica stash sem removê-lo da lista
```bash
git stash apply
```

- Aplica e remove o stash da lista
```bash
git stash pop
```

- Remove stash específico
```bash
git stash drop
```

- Remove todos os stashes
```bash
git stash clear
```

---
<br><br>

## Reverter e Resetar

- Cria um novo commit revertendo outro commit
```bash
git revert <hash>
```

- Move HEAD para commit, mantendo alterações em stage
```bash
git reset --soft <hash>
```

- Move HEAD e remove do stage, mantendo alterações
```bash
git reset --mixed <hash>
```

- Restaura para commit descartando alterações
```bash
git reset --hard <hash>
```

---
<br><br>

## Busca e Comparação

- Busca texto no histórico de commits
```bash
git grep "texto"
```

- Mostra commits que adicionaram ou removeram determinado texto
```bash
git log -S "texto"
```

- Mostra qual commit alterou cada linha do arquivo
```bash
git blame <arquivo>
```

---
<br><br>

## Outros Úteis

- Remove arquivos não rastreados
```bash
git clean -f
```

- Cria um arquivo compactado do projeto
```bash
git archive --format=zip HEAD > projeto.zip
```

- Mostra histórico de alterações no HEAD
```bash
git reflog
```

- Aplica commit específico de outra branch
```bash
git cherry-pick <hash>
```
---
<br><br>

# Comandos Avançados do Git

## 1. Git Reflog
- **O que é:**  
Mostra todo o histórico de movimentação do ponteiro `HEAD`, incluindo commits deletados, resets e alterações que não aparecem em `git log`.
- **Exemplo:**
```bash
git reflog
```

---

## 2. Git Cherry-pick
- **O que é:**  
Aplica um commit específico de outra branch no seu histórico atual, sem fazer merge completo.
- **Exemplo:**
```bash
git cherry-pick <hash-do-commit>
```

---

## 3. Git Revert
- **O que é:**  
Cria um novo commit que desfaz as alterações de um commit anterior sem alterar o histórico.
- **Exemplo:**
```bash
git revert <hash-do-commit>
```

---

## 4. Git Reset
- **O que é:**  
Usado para mover o `HEAD` para um commit específico, com diferentes níveis de reversão:
- **Exemplos:**
```bash
git reset --soft <hash>    # Mantém alterações no stage
git reset --mixed <hash>   # Mantém alterações nos arquivos
git reset --hard <hash>    # Desfaz tudo e volta ao commit selecionado
```

---

## 5. Git Bisect
- **O que é:**  
Permite encontrar o commit que introduziu um bug testando cada ponto da linha do tempo de forma binária.
- **Exemplo:**
```bash
git bisect start
git bisect bad             # Marca o commit atual como defeituoso
git bisect good <hash>     # Marca commit onde o bug não existia
```

---

## 6. Git Blame
- **O que é:**  
Mostra quem alterou cada linha de um arquivo e em qual commit.
- **Exemplo:**
```bash
git blame nome-do-arquivo
```

---

## 7. Git Shortlog
- **O que é:**  
Mostra commits agrupados por autor, útil para relatórios.
- **Exemplo:**
```bash
git shortlog
```

---

## 8. Git Tag (assinada)
- **O que é:**  
Permite criar tags assinadas criptograficamente para releases oficiais.
- **Exemplo:**
```bash
git tag -s v1.0 -m "Versão assinada 1.0"
```

---

## 9. Git Archive
- **O que é:**  
Gera um arquivo compactado do projeto a partir de um commit específico.
- **Exemplo:**
```bash
git archive --format=zip HEAD > projeto.zip
```

---

## 10. Git Submodule
- **O que é:**  
Permite adicionar repositórios Git dentro de outro repositório (útil para dependências).
- **Exemplos:**
```bash
git submodule add <url-repositorio>
git submodule update --init --recursive
```

---

## 11. Git Clean
- **O que é:**  
Remove arquivos não rastreados e diretórios que não fazem parte do repositório.
- **Exemplos:**
```bash
git clean -f        # Remove arquivos não rastreados
git clean -fd       # Remove arquivos e pastas não rastreadas
```

---

## 12. Git Filter-branch (reescrita de histórico)
- **O que é:**  
Permite reescrever o histórico para alterar mensagens, autores ou remover arquivos de commits antigos.
- **Exemplo:**
```bash
git filter-branch --tree-filter 'rm -f arquivo-secreto.txt' HEAD
```
Atenção: altera o histórico, pode causar conflitos em repositórios compartilhados.

---

## 13. Git FSCK
- **O que é:**  
Verifica a integridade e consistência do repositório Git.
- **Exemplo:**
```bash
git fsck
```

---

## 14. Git Show
- **O que é:**  
Mostra detalhes de um commit ou tag específica.
- **Exemplo:**
```bash
git show <hash-ou-tag>
```

---

## 15. Git Describe
- **O que é:**  
Mostra a tag mais próxima de um commit, útil para saber em qual versão algo foi alterado.
- **Exemplo:**
```bash
git describe
```
---
<br><br>

# Links Úteis para Consultar sobre Git e GitHub

- [Documentação Oficial do Git](https://git-scm.com/doc)  
- [Livro Pro Git (gratuito e completo)](https://git-scm.com/book/pt-br/v2)  
- [Comandos Git (Git Cheat Sheet oficial)](https://training.github.com/downloads/pt_BR/github-git-cheat-sheet.pdf)  
- [GitHub Docs - Ajuda e Tutoriais](https://docs.github.com/pt)  
- [GitLab Docs - Ajuda e Tutoriais](https://docs.gitlab.com/)  
- [Guia prático de GitFlow](https://www.atlassian.com/git/tutorials/comparing-workflows/gitflow-workflow)  
- [Oh My Git! - Jogo interativo para aprender Git](https://ohmygit.org/)  
- [Learn Git Branching (treinamento interativo)](https://learngitbranching.js.org/?locale=pt_BR)  
- [Try Git - Curso online gratuito (GitHub)](https://try.github.io/)  
- [Coleção de boas práticas para Git](https://nvie.com/posts/a-successful-git-branching-model/)  

---
