# Git Tutorial 

## Sumário:
- [Download do Git no Linux](a)
- [Download do Git no Windows](a)
- [Configurar seu Usuário](a)
- [Chave SSH](a)
- [Comandos - Repositórios](a)
- [Banches](a)
- [Mensagens para Commits](a)
- [Cheat Sheets](a)


## Download Git Linux

Para instalar o Git no Linux, você pode usar o gerenciador de pacotes da sua distribuição. Aqui estão os comandos para algumas distribuições populares:
<br>

- **Ubuntu/Debian**:

  ```bash
  sudo apt update
  sudo apt install git
  ```
###### É importante rodar o comando `sudo apt update` antes de instalar algo no linux por alguns motivos fundamentais: atualiza a lista de pacotes disponíveis; garante que você está instalando a versão mais recente; sincroniza com os repositórios; melhorias de segurança; evita problemas de dependência.

- **Verificar a versão instalada**:
 
  ```bash
  git --version
  ```
<br>

## Download Git Linux

blablabla
<br>

## Configurar seu Usuário

Para configurar seu nome e e-mail, que serão usados em seus commits, use os seguintes comandos:
<br>

- **Para configuração global** (válida todos os repositórios do usuário na máquina):

```bash
git config --global user.name "Seu Nome"
git config --global user.email "seu-email@example.com"
```
<br>

- **Para configuração local** (válida apenas para um repositório específico):

```bash
git config user.name "Seu Nome"
git config user.email "seu-email@exemplo.com"
```
<br>

## Chave SSH
Para autenticar-se com repositórios remotos usando SSH, siga estes passos:
<br>

1. **Gerar uma nova chave SSH**:
   ```bash
   ssh-keygen -t rsa -b 4096 -C "seu-email@example.com"
   ```

2. **Adicionar a chave SSH ao agente SSH**:
   ```bash
   eval "$(ssh-agent -s)"
   ssh-add ~/.ssh/id_rsa
   ```

3. **Adicionar a chave SSH ao seu GitHub**:
   Copie o conteúdo da chave pública:
   ```bash
   cat ~/.ssh/id_rsa.pub
   ```

4. **E adicione no GitHub em:** Settings > SSH and GPG keys > New SSH key
<br>

## Comandos - Repositórios

#### Criar um novo repositório:
  
  ```bash
  git init
  ```
  Inicializa um novo repositório Git no diretório atual. Isso cria um diretório `.git` que armazena todos os arquivos e metadados do repositório.
<br>


#### Clonar um repositório:
  
  ```bash
  git clone <url-do-repositorio>
  ```
  Clona o repositório remoto para o diretório local. Substitua `<url-do-repositorio>` pela URL do repositório que você deseja clonar.

  *Exemplo:* `git clone https://github.com/usuario/repositorio.git`
<br>

#### Adicionar um novo repositório remoto:
  
  ```bash
  git remote add origin <url-do-repositorio>
  ```
  Adiciona um repositório remoto com o nome `origin` (ou outro nome que você escolher) e a URL fornecida. Isso é útil para associar um repositório local a um repositório remoto.

  *Exemplo:* `git remote add origin https://github.com/usuario/repositorio.git`
<br>

#### Listar repositórios remotos:
  
  ```bash
  git remote -v
  ```
  Mostra a lista de repositórios remotos associados ao repositório local, incluindo suas URLs.
<br>

#### Remover um repositório remoto:
  
  ```bash
  git remote remove <nome-do-repositorio>
  ```
  Remove um repositório remoto associado ao repositório local. Substitua `<nome-do-repositorio>` pelo nome do repositório remoto que você deseja remover.

  *Exemplo:* `git remote remove origin`
<br>

#### Alterar a URL de um repositório remoto:
  
  ```bash
  git remote set-url origin <nova-url-do-repositorio>
  ```
  Atualiza a URL associada ao repositório remoto `origin`. Use este comando se a URL do repositório remoto mudar.
<br>

#### Renomear um Repositório Remoto:
  
  Para 
  ```bash
  git remote rename <nome-antigo> <nome-novo>
  ```
  Altera o nome de um repositório remoto.

  *Exemplo:* `git remote rename origin upstream`
<br>

#### Verificar o status dos arquivos:
  
  ```bash
  git status
  ```
  Exibe o status dos arquivos no repositório, mostrando quais arquivos foram modificados, quais estão prontos para o commit e quais não estão sendo rastreados.
<br>

#### Adicionar arquivos ao estágio (para serem comitados):
  
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

#### Fazer commit das mudanças:
  
  ```bash
  git commit -m "Mensagem do commit"
  ```
  Registra as mudanças no repositório com uma mensagem descritiva. A mensagem deve explicar o que foi alterado.

  *Exemplo:* `git commit -m "[FEAT][WIP] Introduz um novo método de pagamento"`
<br>

#### Commitar:
  
  ```bash
  git push
  ```
  Envia as mudanças do repositório local para o repositório remoto associado. Por padrão, o comando envia para o branch atual.
<br>

#### Puxar mudanças do repositório remoto:
  
  ```bash
  git pull
  ```
  Baixa e integra as mudanças do repositório remoto para o repositório local. Combina `git fetch` e `git merge` em um único comando.
<br>

#### Buscar atualizações do repositório remoto:
  
  ```bash
  git fetch
  ```
  Baixa as mudanças do repositório remoto sem integrá-las ao repositório local. É útil para verificar atualizações antes de realizar um merge ou rebase.
<br>

#### Mesclar mudanças do repositório remoto:
  
  ```bash
  git merge <branch>
  ```
  Mescla as mudanças do branch especificado ao branch atual. Substitua `<branch>` pelo nome do branch que você deseja mesclar.

  *Exemplo:* `git merge feature/nova-funcionalidade`
<br>

## Branches

- **Rebase as mudanças de um branch**:
  
  ```bash
  git rebase <branch>
  ```
  Reaplica suas mudanças sobre o branch especificado. O rebase é útil para manter um histórico linear ao integrar mudanças.

  *Exemplo:* `git rebase main`
<br>

## Cheat Sheets
Aqui estão alguns links para cheat sheets úteis de Git:

- [Git Cheat Sheet](https://education.github.com/git-cheat-sheet-education.pdf)
- [Git Command Cheatsheet](https://github.github.io/git-cheat-sheet/)
