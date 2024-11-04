# 😽 Git Tutorial 
<br>

## 📄 Sumário: <br><br>
<br>

- [Download do Git no Linux](#download-git-linux)
- [Download do Git no Windows](#download-git-windows)
- [Configurar seu Usuário](#configurar-seu-usuario)
- [Chave SSH](#chave-ssh)
- [Comandos - Repositórios](#comandos---repositórios)
- [Branches](#branches)
- [Mensagens para Commits](#mensagens-para-commits)
- [Cheat Sheets](#cheat-sheets)
---
<br>

## 🔶 Download Git Linux
<br>

Para instalar o Git no Linux, você pode usar o gerenciador de pacotes da sua distribuição. Aqui estão os comandos para algumas distribuições populares:
<br>

- **Ubuntu/Debian**:

  ```bash
  sudo apt update
  sudo apt install git
  ```
>#### ⚠️ É importante rodar o comando `sudo apt update` antes de instalar algo no linux por alguns motivos fundamentais: atualiza a lista de pacotes disponíveis; garante que você está instalando a versão mais recente; sincroniza com os repositórios; melhorias de segurança; evita problemas de dependência.

- **Verificar a versão instalada**:
 
  ```bash
  git --version
  ```
---
<br>

## 🔶 Download Git Windows
<br>

Para instalar o Git no Windows:

1. **Baixe o instalador**: Acesse [git-scm.com](https://git-scm.com/download/win) e faça o download da versão mais recente do Git para Windows.
2. **Execute o instalador**: Siga as instruções do instalador, aceitando as configurações padrão ou personalizando conforme necessário. Preste atenção às opções, especialmente nas configurações de PATH e em como você deseja usar o Git Bash.
3. **Verifique a instalação**: Após a instalação, abra o terminal (Git Bash ou CMD) e execute:

   ```bash
   git --version
   ```
---
<br>

## 🔶 Configurar seu Usuário
<br>

Para configurar seu nome e e-mail, que serão usados em seus commits, use os seguintes comandos:
<br>

### 🔹 Para configuração global (válida todos os repositórios do usuário na máquina):

```bash
git config --global user.name "Seu Nome"
git config --global user.email "seu-email@example.com"
```
<br>

### 🔹 Para configuração local (válida apenas para um repositório específico):

```bash
git config user.name "Seu Nome"
git config user.email "seu-email@exemplo.com"
```
---
<br>

## 🔶 Chave SSH
<br>
A chave SSH é uma forma segura de autenticação que permite que você se conecte a repositórios remotos sem precisar inserir suas credenciais toda vez.
<br><br>

1. **Gerar uma nova chave SSH**:<br><br>
   ```bash
   ssh-keygen -t rsa -b 4096 -C "seu-email@example.com"
   ```
   Pressione `Enter` para aceitar o local padrão do arquivo, ou especifique um local diferente. Em seguida, você será solicitado a inserir uma senha opcional.
<br>

2. **Adicionar a chave SSH ao agente SSH**:<br><br>
   ```bash
   eval "$(ssh-agent -s)"
   ssh-add ~/.ssh/id_rsa
   ```
<br>

3. **Adicionar a chave SSH ao seu GitHub**:
   Copie o conteúdo da chave pública: <br><br>
   ```bash
   cat ~/.ssh/id_rsa.pub
   ```
<br>

4. **E adicione no GitHub em:**
   
    `Settings > SSH and GPG keys > New SSH key`
<br>

- Teste a conexão com o GitHub usando:<br><br>
  ```bash
   ssh -T git@github.com
   ```
  Você deve ver uma mensagem de sucesso.

---
<br>

## 🔶 Comandos - Repositórios
<br>

### 🔹 Criar um novo repositório:
  
  ```bash
  git init
  ```
  Inicializa um novo repositório Git no diretório atual. Isso cria um diretório `.git` que armazena todos os arquivos e metadados do repositório.
<br>
<br>
<br>

### 🔹 Clonar um repositório:
  
  ```bash
  git clone <url-do-repositorio>
  ```
  Clona o repositório remoto para o diretório local. Substitua `<url-do-repositorio>` pela URL do repositório que você deseja clonar.

  *Exemplo:* `git clone https://github.com/usuario/repositorio.git`
<br>
<br>
<br>

### 🔹 Adicionar um novo repositório remoto:
  
  ```bash
  git remote add origin <url-do-repositorio>
  ```
  Adiciona um repositório remoto com o nome `origin` (ou outro nome que você escolher) e a URL fornecida. Isso é útil para associar um repositório local a um repositório remoto.

  *Exemplo:* `git remote add origin https://github.com/usuario/repositorio.git`
<br>
<br>
<br>

### 🔹 Listar repositórios remotos:
  
  ```bash
  git remote -v
  ```
  Mostra a lista de repositórios remotos associados ao repositório local, incluindo suas URLs.
<br>
<br>
<br>

### 🔹 Remover um repositório remoto:
  
  ```bash
  git remote remove <nome-do-repositorio>
  ```
  Remove um repositório remoto associado ao repositório local. Substitua `<nome-do-repositorio>` pelo nome do repositório remoto que você deseja remover.

  *Exemplo:* `git remote remove origin`
<br>
<br>
<br>

### 🔹 Alterar a URL de um repositório remoto:
  
  ```bash
  git remote set-url origin <nova-url-do-repositorio>
  ```
  Atualiza a URL associada ao repositório remoto `origin`. Use este comando se a URL do repositório remoto mudar.
<br>
<br>
<br>

### 🔹 Renomear um Repositório Remoto:
  
  ```bash
  git remote rename <nome-antigo> <nome-novo>
  ```
  Altera o nome de um repositório remoto.

  *Exemplo:* `git remote rename origin upstream`
<br>
<br>
<br>

### 🔹 Verificar o status dos arquivos:
  
  ```bash
  git status
  ```
  Exibe o status dos arquivos no repositório, mostrando quais arquivos foram modificados, quais estão prontos para o commit e quais não estão sendo rastreados.
<br>
<br>
<br>

### 🔹 Adicionar arquivos ao estágio (para serem comitados):
  
  ```bash
  git add <arquivo>
  ```
  Adiciona um arquivo específico ao estágio, preparando-o para o commit. 

  *Exemplo:* `git add index.html`
  
  **OU**
  
  ```bash
  git add .
  ```
  Adiciona todos os arquivos modificados.
<br>
<br>
<br>

### 🔹 Fazer commit das mudanças:
  
  ```bash
  git commit -m "Mensagem do commit"
  ```
  Registra as mudanças no repositório com uma mensagem descritiva. A mensagem deve explicar o que foi alterado.

  *Exemplo:* `git commit -m "[FEAT][WIP] Introduz um novo método de pagamento"`
<br>
<br>
<br>

### 🔹 Commitar:
  
  ```bash
  git push
  ```
  Envia as mudanças do repositório local para o repositório remoto associado. Por padrão, o comando envia para o branch atual.
<br>
<br>
<br>

### 🔹 Puxar mudanças do repositório remoto:
  
  ```bash
  git pull
  ```
  Baixa e integra as mudanças do repositório remoto para o repositório local. Combina `git fetch` e `git merge` em um único comando.
<br>
<br>
<br>

### 🔹 Buscar atualizações do repositório remoto:
  
  ```bash
  git fetch
  ```
  Baixa as mudanças do repositório remoto sem integrá-las ao repositório local. É útil para verificar atualizações antes de realizar um merge ou rebase.
<br>
<br>
<br>

### 🔹 Mesclar mudanças do repositório remoto:
  
  ```bash
  git merge <branch>
  ```
  Mescla as mudanças do branch especificado ao branch atual. Substitua `<branch>` pelo nome do branch que você deseja mesclar.

  *Exemplo:* `git merge feature/nova-funcionalidade`

---
<br>

## 🔶 Branches
<br>

Branches (ou ramificações) permitem que você trabalhe em diferentes versões do projeto simultaneamente.

### 🔹 Criar um novo branch:

```bash
git branch <nome-do-branch>
```
Cria um novo branch.

*Exemplo:* `git branch nova-funcionalidade`
<br>
<br>
<br>

### 🔹 Mudar para um branch existente:

```bash
git checkout <nome-do-branch>
```

*Exemplo:* `git checkout nova-funcionalidade`
<br>
<br>
<br>

### 🔹 Criar e mudar para um novo branch:

```bash
git checkout -b <nome-do-branch>
```

*Exemplo:* `git checkout -b nova-funcionalidade`
<br>
<br>
<br>

### 🔹 Listar todos os branches:

```bash
git branch
```
<br>

### 🔹 Mesclar um branch em outro:

```bash
git merge <nome-do-branch>
```
Mescla o branch especificado no branch atual.
<br>
<br>
<br>

### 🔹 Rebase as mudanças de um branch:
  
  ```bash
  git rebase <branch>
  ```
  Reaplica suas mudanças sobre o branch especificado. O rebase é útil para manter um histórico linear ao integrar mudanças.

  *Exemplo:* `git rebase main`
<br>
<br>
<br>

### 🔹 Excluir um branch:

```bash
git branch -d <nome-do-branch>
```
Remove um branch local. Use `-D` para forçar a exclusão.

*Exemplo:* 
`git branch -d nova-funcionalidade`

---
<br>

## 🔶 Cheat Sheets
<br>

Aqui estão alguns links para cheat sheets úteis de Git:

- [Git Cheat Sheet](https://education.github.com/git-cheat-sheet-education.pdf)
- [Git Command Cheatsheet](https://github.github.io/git-cheat-sheet/)
