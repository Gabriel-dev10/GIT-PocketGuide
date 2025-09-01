# Olá, dev! Tudo bem?

Esse guia nasceu da minha própria experiência - enquanto trabalhava, várias dúvidas de Git iam surgindo e eu fui anotando tudo no meu bloco de notas.

Decidi compartilhar esse conhecimento com vocês de maneira organizada e direto ao ponto!

---

## Os 3 Estados do Seu Código

- **Modified** – Você alterou o arquivo, mas o Git ainda não sabe.
- **Staged** – Você avisou: "Ei, Git, presta atenção nesse arquivo!"
- **Committed** – Tudo seguro no banco de dados do Git.

---

## Preciso de Ajuda com comandos!

```bash
git help                     # Manual completo
git help commit              # Ajuda específica sobre commit
git status --help            # Outra forma de pedir ajuda
```

---

## Primeira Configuração (Faz só uma vez!)

```bash
# Quem é você?
git config --global user.name "Seu Nome"
git config --global user.email "seu.email@exemplo.com"

# Suas preferências
git config --global core.editor "code --wait"  # VS Code é vida!
git config --global merge.tool vimdiff

# Ver suas configs
git config --list
```

---

## O que o Git deve ignorar?

Crie um arquivo `.gitignore` na raiz do projeto:

```bash
# Coisas que não queremos versionar
node_modules/    # Dependências
*.log            # Logs
.env             # Variáveis de ambiente
```

---

## Trabalhando Localmente

```bash
# Começar um novo projeto
git init

# Ver o que tá rolando
git status
git status -s    # Versão compacta

# Preparar arquivos para commit
git add arquivo.txt      # Arquivo específico
git add .                # Tudo que foi modificado
git add -A               # Tudo mesmo!

# Salvar suas mudanças
git commit -m "Mensagem clara do que fez"
git commit -am "Mensagem"  # Atalho: add + commit para arquivos conhecidos

# Corrigir último commit
git commit --amend       # Esqueceu algo?

# Remover arquivos
git rm arquivo.txt           # Remove de vez
git rm --cached arquivo.txt  # Para de versionar, mas mantém na sua máquina
```

---

## Boas Práticas de Commit Messages

Para manter o histórico do Git organizado, é útil seguir convenções. Aqui estão exemplos:

```bash
git commit -m "feat: adicionar login de usuário"        # Nova funcionalidade
git commit -m "fix: corrigir bug na validação de email" # Correção de bug
git commit -m "chore: atualizar dependências"           # Tarefas gerais, manutenção
git commit -m "docs: atualizar README"                  # Alterações em documentação
git commit -m "style: ajustar formatação de código"     # Apenas estilo, sem funcionalidade
git commit -m "refactor: reorganizar funções de login"  # Refatoração sem alterar comportamento
git commit -m "test: adicionar testes unitários para login" # Adição de testes

```
---

## Histórico - Sua Linha do Tempo

```bash
git log               # Histórico completo
git log --oneline     # Só o essencial
git log --graph       # Visual maneira com branches
git log -p -2         # Mostra as mudanças dos últimos 2 commits

# Caça aos commits
git log --author="João"      # Tudo que o João fez
git log --since="2 days ago" # O que rolou esses dias
git log --grep="bug"         # Commits que mencionam bug

git blame arquivo.txt        # Quem fez o que e quando
```

---

## Arrependimentos? O Git perdoa!

```bash
# Desfazer mudanças não preparadas
git checkout -- arquivo.txt

# Tirar arquivo da área de preparação
git reset HEAD arquivo.txt

# Desfazer um commit específico (sem apagar história)
git revert <hash-do-commit>

# CUIDADO: esses alteram a história
git reset --soft <commit>   # Volta mas mantém mudanças preparadas
git reset --hard <commit>   # Volta e APAGA TUDO depois desse ponto
```

---

## Cheguei em um projeto novo!

```bash
# Conectar com repositório remoto
git remote add origin https://github.com/usuario/repo.git

# Ver conexões
git remote -v

# Baixar novidades
git fetch          # Só busca
git pull           # Busca e traz pra você
git pull --rebase  # Busca e reorganiza seus commits

# Enviar suas mudanças
git push origin main      # Primeira vez: git push -u origin main
git push --tags           # Enviar tags também
```

---

## Tags - Marcando Versões Importantes

```bash
# Criar tags
git tag v1.0.0                 # Tag simples
git tag -a v1.0.0 -m "Lançamento"  # Tag com mensagem

# Trabalhar com tags
git tag               # Listar tags
git push --tags       # Enviar tags pro remoto
git checkout v1.0.0   # Voltar no tempo
```

---

## Branches - Trabalho em Paralelo

```bash
# Ver branches
git branch           # Locais
git branch -r        # Remotos
git branch -a        # Todos

# Criar e navegar
git branch feature-nova          # Criar nova branch
git checkout feature-nova        # Ir para branch
git checkout -b feature-nova     # Criar e ir: ATALHO ÚTIL!

# Juntar trabalho
git merge outra-branch           # Unir branches
git rebase main                  # Reorganizar commits

# Limpeza
git branch -d branch-velha       # Deletar branch local
```
---

## Ferramentas Úteis

```bash
# Guardar trabalho incompleto temporariamente
git stash           # Guarda na gaveta
git stash list      # Olha na gaveta
git stash pop       # Pega da gaveta

# Caça ao bug - encontrar commit problemático
git bisect start
git bisect bad           # Commit atual com bug
git bisect good v1.0     # Versão que funcionava

# O Git vai te guiar!
git bisect reset         # Voltar ao normal
```

---

## Primeiro Projeto no GitHub

```bash
# Na pasta do seu projeto:
git init
git add .
git commit -m "Primeiro commit!"
git branch -M main
git remote add origin https://github.com/USUARIO/REPO.git
git push -u origin main
```

---

## Inspecionando Mudanças

```bash
git diff               # O que mudei mas não preparei?
git diff --staged      # O que está preparado?
git diff HEAD          # Tudo que mudei desde último commit

git show <commit>      # Detalhes de um commit específico
```

---

## Livros e Cursos Recomendados

- **Git e Github Essencial para o Desenvolvedor (Português)**  
  [Udemy](https://www.udemy.com/share/103bEv3@mDqK5XgdCfhmkgCNni3pnANYULbM3nauczenwkGY1zk6ukc2bBSz_bHI4ZvG8hz2Eg==/)

- **The Git & Github Bootcamp (Inglês)**  
  [Udemy](https://www.udemy.com/share/104c523@eNlrBVNz7udR9TlFi90enDhLA-bjEca8s5uOsu24NjzMEwAdReN9Ugt6aIlBHQPfVQ==/)

- **Livro Pro Git** – A bíblia do Git

- **GitHub Cheat Sheet** – Cola rápida

- **Git Flight Rules** – Salva-vidas para emergências
