🖥 # Cômodos de git
# Guia Completo do Git

## O que é Git?

Git é um sistema de controle de versão distribuído que permite rastrear mudanças no código-fonte durante o desenvolvimento de software. Ele foi criado por Linus Torvalds em 2005 e é amplamente utilizado por desenvolvedores ao redor do mundo.

## Conceitos Fundamentais

### Repository (Repositório)
Um repositório é um diretório que contém todos os arquivos do projeto e o histórico completo de mudanças.

### Commit
Um commit é um snapshot (instantâneo) do estado do seu projeto em um determinado momento. Cada commit possui um hash único e uma mensagem descritiva.

### Branch (Ramificação)
Uma branch é uma linha independente de desenvolvimento. A branch principal é geralmente chamada de `main` ou `master`.

### Working Directory, Staging Area e Repository
- **Working Directory**: Onde você edita os arquivos
- **Staging Area**: Área temporária onde você prepara os arquivos para commit
- **Repository**: Onde os commits são armazenados permanentemente

## Instalação

### Linux (Ubuntu/Debian)
```bash
sudo apt update
sudo apt install git
```

### Linux (CentOS/RHEL)
```bash
sudo yum install git
```

### macOS
```bash
brew install git
```

### Windows
Baixe o Git for Windows em: https://git-scm.com/download/win

## Configuração Inicial

```bash
# Configurar nome de usuário
git config --global user.name "Seu Nome"

# Configurar email
git config --global user.email "seu.email@exemplo.com"

# Configurar editor padrão
git config --global core.editor "code --wait"  # Para VS Code

# Verificar configurações
git config --list
```

## Comandos Básicos

### Inicializar um Repositório
```bash
# Criar um novo repositório
git init

# Clonar um repositório existente
git clone https://github.com/usuario/repositorio.git
```

### Verificar Status
```bash
# Ver status dos arquivos
git status

# Ver diferenças não commitadas
git diff

# Ver diferenças na staging area
git diff --staged
```

### Adicionar e Commitar
```bash
# Adicionar arquivo específico
git add arquivo.txt

# Adicionar todos os arquivos
git add .

# Adicionar arquivos por padrão
git add *.js

# Fazer commit
git commit -m "Mensagem descritiva do commit"

# Adicionar e commitar em um comando
git commit -am "Mensagem do commit"
```

### Visualizar Histórico
```bash
# Ver histórico de commits
git log

# Ver histórico resumido
git log --oneline

# Ver histórico com gráfico
git log --graph --oneline --all

# Ver commits de um arquivo específico
git log arquivo.txt
```

## Trabalhando com Branches

### Criar e Gerenciar Branches
```bash
# Listar branches
git branch

# Criar nova branch
git branch nova-feature

# Mudar para uma branch
git checkout nova-feature

# Criar e mudar para nova branch
git checkout -b nova-feature

# Deletar branch
git branch -d nome-da-branch

# Deletar branch forçadamente
git branch -D nome-da-branch
```

### Merge (Fusão)
```bash
# Fazer merge de uma branch
git checkout main
git merge nova-feature

# Merge com mensagem personalizada
git merge nova-feature -m "Merge da feature X"
```

### Rebase
```bash
# Rebase da branch atual
git rebase main

# Rebase interativo
git rebase -i HEAD~3
```

## Trabalhando com Repositórios Remotos

### Configurar Remotes
```bash
# Adicionar remote
git remote add origin https://github.com/usuario/repositorio.git

# Listar remotes
git remote -v

# Renomear remote
git remote rename origin upstream

# Remover remote
git remote remove origin
```

### Push e Pull
```bash
# Enviar commits para o remote
git push origin main

# Enviar nova branch
git push -u origin nova-feature

# Baixar mudanças do remote
git pull origin main

# Fetch (baixar sem fazer merge)
git fetch origin
```

## Comandos Avançados

### Stash (Armazenamento Temporário)
```bash
# Salvar trabalho atual temporariamente
git stash

# Salvar com mensagem
git stash save "Trabalho em progresso"

# Listar stashes
git stash list

# Aplicar último stash
git stash apply

# Aplicar e remover stash
git stash pop

# Remover stash
git stash drop
```

### Reset e Revert
```bash
# Desfazer último commit (mantém mudanças)
git reset --soft HEAD~1

# Desfazer último commit (remove mudanças da staging)
git reset --mixed HEAD~1

# Desfazer último commit (remove tudo)
git reset --hard HEAD~1

# Reverter commit específico
git revert <hash-do-commit>
```

### Cherry-pick
```bash
# Aplicar commit específico de outra branch
git cherry-pick <hash-do-commit>
```

## Arquivo .gitignore

Crie um arquivo `.gitignore` na raiz do projeto para ignorar arquivos/diretórios:

```
# Dependências
node_modules/
vendor/

# Arquivos de sistema
.DS_Store
Thumbs.db

# Arquivos de IDE
.vscode/
.idea/

# Arquivos de build
dist/
build/
*.log

# Arquivos de ambiente
.env
.env.local
```

## Boas Práticas

### Mensagens de Commit
- Use verbos no imperativo: "Add", "Fix", "Update"
- Seja conciso mas descritivo
- Primeira linha com até 50 caracteres
- Deixe uma linha em branco antes da descrição detalhada

Exemplo:
```
Add user authentication system

- Implement login/logout functionality
- Add password hashing with bcrypt
- Create user session management
```

### Estrutura de Branches
- `main/master`: Branch principal, sempre estável
- `develop`: Branch de desenvolvimento
- `feature/*`: Branches para novas funcionalidades
- `hotfix/*`: Branches para correções urgentes
- `release/*`: Branches para preparação de releases

### Workflow Recomendado
1. Crie uma branch para cada feature
2. Faça commits pequenos e frequentes
3. Escreva mensagens de commit claras
4. Teste antes de fazer merge
5. Use pull requests para revisão de código

## Comandos de Emergência

```bash
# Desfazer mudanças não commitadas
git checkout -- arquivo.txt

# Desfazer todas as mudanças não commitadas
git checkout -- .

# Limpar arquivos não rastreados
git clean -fd

# Reflog (histórico de referências)
git reflog

# Recuperar commit "perdido"
git checkout <hash-do-reflog>
```

## Aliases Úteis

```bash
# Configurar aliases
git config --global alias.st status
git config --global alias.co checkout
git config --global alias.br branch
git config --global alias.ci commit
git config --global alias.unstage 'reset HEAD --'
git config --global alias.last 'log -1 HEAD'
git config --global alias.visual '!gitk'
```

## Ferramentas Visuais

### Interfaces Gráficas
- **GitKraken**: Interface moderna e intuitiva
- **SourceTree**: Gratuita da Atlassian
- **GitHub Desktop**: Simples e integrada ao GitHub
- **GitLab**: Interface web integrada

### Extensões para Editores
- **VS Code**: GitLens, Git Graph
- **Sublime Text**: SublimeGit
- **Vim**: fugitive.vim

## Recursos Adicionais

### Documentação Oficial
- [Git Documentation](https://git-scm.com/doc)
- [Pro Git Book](https://git-scm.com/book)

### Tutoriais Interativos
- [Learn Git Branching](https://learngitbranching.js.org/)
- [Git Immersion](https://gitimmersion.com/)

### Comandos de Referência Rápida
```bash
# Ver todas as configurações
git config --list --show-origin

# Ver autor de cada linha
git blame arquivo.txt

# Buscar texto no histórico
git log -S "texto-procurado"

# Comparar branches
git diff main..develop

# Ver arquivos modificados entre commits
git diff --name-only HEAD~2 HEAD
```

Este guia cobre os aspectos fundamentais e avançados do Git. Pratique regularmente esses comandos para se tornar proficiente no uso desta ferramenta essencial para desenvolvimento de software.
