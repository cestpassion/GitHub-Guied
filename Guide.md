Here’s the translation of your Git tutorial into English:

# 😽 Git Tutorial
<br>

## 📄 Table of Contents: <br><br>
<br>

- [Download Git on Linux](#download-git-linux)
- [Download Git on Windows](#download-git-windows)
- [Configure Your User](#configure-your-user)
- [SSH Key](#ssh-key)
- [Commands - Repositories](#commands---repositories)
- [Branches](#branches)
- [Commit Messages](#commit-messages)
- [Cheat Sheets](#cheat-sheets)
---
<br>

## 🔶 Download Git Linux
<br>

To install Git on Linux, you can use your distribution's package manager. Here are the commands for some popular distributions:
<br>

- **Ubuntu/Debian**:

  ```bash
  sudo apt update
  sudo apt install git
  ```
>#### ⚠️ It is important to run the command `sudo apt update` before installing anything on Linux for several fundamental reasons: it updates the list of available packages; ensures you are installing the latest version; synchronizes with the repositories; improves security; and avoids dependency issues.

- **Check the installed version**:
 
  ```bash
  git --version
  ```
---
<br>

## 🔶 Download Git Windows
<br>

To install Git on Windows:

1. **Download the installer**: Visit [git-scm.com](https://git-scm.com/download/win) and download the latest version of Git for Windows.
2. **Run the installer**: Follow the instructions in the installer, accepting the default settings or customizing them as needed. Pay attention to the options, especially the PATH settings and how you want to use Git Bash.
3. **Verify the installation**: After installation, open the terminal (Git Bash or CMD) and run:

   ```bash
   git --version
   ```
---
<br>

## 🔶 Configure Your User
<br>

To set your name and email, which will be used in your commits, use the following commands:
<br>

### 🔹 For global configuration (valid for all user repositories on the machine):

```bash
git config --global user.name "Your Name"
git config --global user.email "your-email@example.com"
```
<br>

### 🔹 For local configuration (valid only for a specific repository):

```bash
git config user.name "Your Name"
git config user.email "your-email@example.com"
```
---
<br>

## 🔶 SSH Key
<br>
An SSH key is a secure form of authentication that allows you to connect to remote repositories without having to enter your credentials every time.
<br><br>

1. **Generate a new SSH key**:<br><br>
   ```bash
   ssh-keygen -t rsa -b 4096 -C "your-email@example.com"
   ```
   Press `Enter` to accept the default file location, or specify a different location. You will then be prompted to enter an optional passphrase.
<br>

2. **Add the SSH key to the SSH agent**:<br><br>
   ```bash
   eval "$(ssh-agent -s)"
   ssh-add ~/.ssh/id_rsa
   ```
<br>

3. **Add the SSH key to your GitHub**:
   Copy the contents of the public key: <br><br>
   ```bash
   cat ~/.ssh/id_rsa.pub
   ```
<br>

4. **And add it on GitHub at:**
   
    `Settings > SSH and GPG keys > New SSH key`
<br>

- Test the connection to GitHub using:<br><br>
  ```bash
   ssh -T git@github.com
   ```
  You should see a success message.

---
<br>

## 🔶 Commands - Repositories
<br>

### 🔹 Create a new repository:
  
  ```bash
  git init
  ```
  Initializes a new Git repository in the current directory. This creates a `.git` directory that stores all the files and metadata of the repository.
<br>
<br>
<br>

### 🔹 Clone a repository:
  
  ```bash
  git clone <repository-url>
  ```
  Clones the remote repository to the local directory. Replace `<repository-url>` with the URL of the repository you wish to clone.

  *Example:* `git clone https://github.com/user/repository.git`
<br>
<br>
<br>

### 🔹 Add a new remote repository:
  
  ```bash
  git remote add origin <repository-url>
  ```
  Adds a remote repository with the name `origin` (or another name you choose) and the provided URL. This is useful for associating a local repository with a remote repository.

  *Example:* `git remote add origin https://github.com/user/repository.git`
<br>
<br>
<br>

### 🔹 List remote repositories:
  
  ```bash
  git remote -v
  ```
  Shows the list of remote repositories associated with the local repository, including their URLs.
<br>
<br>
<br>

### 🔹 Remove a remote repository:
  
  ```bash
  git remote remove <repository-name>
  ```
  Removes a remote repository associated with the local repository. Replace `<repository-name>` with the name of the remote repository you wish to remove.

  *Example:* `git remote remove origin`
<br>
<br>
<br>

### 🔹 Change the URL of a remote repository:
  
  ```bash
  git remote set-url origin <new-repository-url>
  ```
  Updates the URL associated with the remote repository `origin`. Use this command if the URL of the remote repository changes.
<br>
<br>
<br>

### 🔹 Rename a remote repository:
  
  ```bash
  git remote rename <old-name> <new-name>
  ```
  Changes the name of a remote repository.

  *Example:* `git remote rename origin upstream`
<br>
<br>
<br>

### 🔹 Check the status of files:
  
  ```bash
  git status
  ```
  Displays the status of files in the repository, showing which files have been modified, which are staged for commit, and which are untracked.
<br>
<br>
<br>

### 🔹 Add files to the staging area (to be committed):
  
  ```bash
  git add <file>
  ```
  Adds a specific file to the staging area, preparing it for commit. 

  *Example:* `git add index.html`
  
  **OR**
  
  ```bash
  git add .
  ```
  Adds all modified files.
<br>
<br>
<br>

### 🔹 Commit the changes:
  
  ```bash
  git commit -m "Commit message"
  ```
  Records the changes in the repository with a descriptive message. The message should explain what was changed.

  *Example:* `git commit -m "[FEAT][WIP] Introduces a new payment method"`
<br>
<br>
<br>

### 🔹 Push:
  
  ```bash
  git push
  ```
  Sends changes from the local repository to the associated remote repository. By default, the command pushes to the current branch.
<br>
<br>
<br>

### 🔹 Pull changes from the remote repository:
  
  ```bash
  git pull
  ```
  Downloads and integrates changes from the remote repository into the local repository. It combines `git fetch` and `git merge` into a single command.
<br>
<br>
<br>

### 🔹 Fetch updates from the remote repository:
  
  ```bash
  git fetch
  ```
  Downloads changes from the remote repository without integrating them into the local repository. It is useful for checking updates before performing a merge or rebase.
<br>
<br>
<br>

### 🔹 Merge changes from the remote repository:
  
  ```bash
  git merge <branch>
  ```
  Merges changes from the specified branch into the current branch. Replace `<branch>` with the name of the branch you wish to merge.

  *Example:* `git merge feature/new-feature`

---
<br>

## 🔶 Branches
<br>

Branches allow you to work on different versions of a project simultaneously.

### 🔹 Create a new branch:

```bash
git branch <branch-name>
```
Creates a new branch.

*Example:* `git branch new-feature`
<br>
<br>
<br>

### 🔹 Switch to an existing branch:

```bash
git checkout <branch-name>
```

*Example:* `git checkout new-feature`
<br>
<br>
<br>

### 🔹 Create and switch to a new branch:

```bash
git checkout -b <branch-name>
```

*Example:* `git checkout -b new-feature`
<br>
<br>
<br>

### 🔹 List all branches:

```bash
git branch
```
<br>

### 🔹 Merge one branch into another:

```bash
git merge <branch-name>
```
Merges the specified branch into the current branch.
<br>
<br>
<br>

### 🔹 Rebase the changes from a branch:
  
  ```bash
  git rebase <branch>
  ```
  Reapplies your changes on top of the specified branch. Rebasing is useful for maintaining a linear history when integrating changes.

  *Example:* `git rebase main`
<br>
<br>
<br>

### 🔹 Delete a branch:

```bash
git branch -d <branch-name>
```
Removes a local branch. Use `-D` to force deletion.

*Example:* 
`git branch -d new-feature`

---
<br>

## 🔶 Cheat Sheets
<br>

Here are some links to useful Git cheat sheets:

- [Git Cheat Sheet](https://education.github.com/git-cheat-sheet-education.pdf)
- [Git Command Cheatsheet](https://github.github.io/git-cheat-sheet/)
