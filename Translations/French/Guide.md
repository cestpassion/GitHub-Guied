# 😽 Tutoriel Git
<br>

## 📄 Sommaire : <br><br>
<br>

- [Télécharger Git sur Linux](#télécharger-git-linux)
- [Télécharger Git sur Windows](#télécharger-git-windows)
- [Configurer votre utilisateur](#configurer-votre-utilisateur)
- [Clé SSH](#clé-ssh)
- [Commandes - Dépôts](#commandes---dépôts)
- [Branches](#branches)
- [Messages pour les commits](#messages-pour-les-commits)
- [Fiches pratiques](#fiches-pratiques)
---
<br>

## 🔶 Télécharger Git Linux
<br>

Pour installer Git sur Linux, vous pouvez utiliser le gestionnaire de paquets de votre distribution. Voici les commandes pour certaines distributions populaires :
<br>

- **Ubuntu/Debian** :

  ```bash
  sudo apt update
  sudo apt install git
  ```
>#### ⚠️ Il est important d'exécuter la commande `sudo apt update` avant d'installer quelque chose sur Linux pour plusieurs raisons fondamentales : met à jour la liste des paquets disponibles ; garantit que vous installez la version la plus récente ; synchronise avec les dépôts ; améliore la sécurité ; évite les problèmes de dépendance.

- **Vérifier la version installée** :

  ```bash
  git --version
  ```
---
<br>

## 🔶 Télécharger Git Windows
<br>

Pour installer Git sur Windows :

1. **Téléchargez l'installateur** : Accédez à [git-scm.com](https://git-scm.com/download/win) et téléchargez la version la plus récente de Git pour Windows.
2. **Exécutez l'installateur** : Suivez les instructions de l'installateur, en acceptant les paramètres par défaut ou en les personnalisant si nécessaire. Faites attention aux options, notamment aux paramètres de PATH et à la manière dont vous souhaitez utiliser Git Bash.
3. **Vérifiez l'installation** : Après l'installation, ouvrez le terminal (Git Bash ou CMD) et exécutez :

   ```bash
   git --version
   ```
---
<br>

## 🔶 Configurer votre utilisateur
<br>

Pour configurer votre nom et votre e-mail, qui seront utilisés dans vos commits, utilisez les commandes suivantes :
<br>

### 🔹 Pour une configuration globale (valable pour tous les dépôts de l'utilisateur sur la machine) :

```bash
git config --global user.name "Votre Nom"
git config --global user.email "votre-email@example.com"
```
<br>

### 🔹 Pour une configuration locale (valable uniquement pour un dépôt spécifique) :

```bash
git config user.name "Votre Nom"
git config user.email "votre-email@exemple.com"
```
---
<br>

## 🔶 Clé SSH
<br>
La clé SSH est une méthode d'authentification sécurisée qui vous permet de vous connecter à des dépôts distants sans avoir à saisir vos identifiants à chaque fois.
<br><br>

1. **Générer une nouvelle clé SSH** :<br><br>
   ```bash
   ssh-keygen -t rsa -b 4096 -C "votre-email@example.com"
   ```
   Appuyez sur `Entrée` pour accepter l'emplacement par défaut du fichier, ou spécifiez un emplacement différent. Ensuite, vous serez invité à saisir un mot de passe optionnel.
<br>

2. **Ajouter la clé SSH à l'agent SSH** :<br><br>
   ```bash
   eval "$(ssh-agent -s)"
   ssh-add ~/.ssh/id_rsa
   ```
<br>

3. **Ajouter la clé SSH à votre GitHub** :
   Copiez le contenu de la clé publique : <br><br>
   ```bash
   cat ~/.ssh/id_rsa.pub
   ```
<br>

4. **Et ajoutez-le sur GitHub à :**
   
    `Paramètres > Clés SSH et GPG > Nouvelle clé SSH`
<br>

- Testez la connexion à GitHub en utilisant :<br><br>
  ```bash
   ssh -T git@github.com
   ```
  Vous devriez voir un message de succès.

---
<br>

## 🔶 Commandes - Dépôts
<br>

### 🔹 Créer un nouveau dépôt :
  
  ```bash
  git init
  ```
  Initialise un nouveau dépôt Git dans le répertoire actuel. Cela crée un répertoire `.git` qui stocke tous les fichiers et métadonnées du dépôt.
<br>
<br>
<br>

### 🔹 Cloner un dépôt :
  
  ```bash
  git clone <url-du-dépôt>
  ```
  Clone le dépôt distant vers le répertoire local. Remplacez `<url-du-dépôt>` par l'URL du dépôt que vous souhaitez cloner.

  *Exemple :* `git clone https://github.com/utilisateur/dépôt.git`
<br>
<br>
<br>

### 🔹 Ajouter un nouveau dépôt distant :
  
  ```bash
  git remote add origin <url-du-dépôt>
  ```
  Ajoute un dépôt distant avec le nom `origin` (ou un autre nom de votre choix) et l'URL fournie. Cela est utile pour associer un dépôt local à un dépôt distant.

  *Exemple :* `git remote add origin https://github.com/utilisateur/dépôt.git`
<br>
<br>
<br>

### 🔹 Lister les dépôts distants :
  
  ```bash
  git remote -v
  ```
  Affiche la liste des dépôts distants associés au dépôt local, y compris leurs URLs.
<br>
<br>
<br>

### 🔹 Supprimer un dépôt distant :
  
  ```bash
  git remote remove <nom-du-dépôt>
  ```
  Supprime un dépôt distant associé au dépôt local. Remplacez `<nom-du-dépôt>` par le nom du dépôt distant que vous souhaitez supprimer.

  *Exemple :* `git remote remove origin`
<br>
<br>
<br>

### 🔹 Changer l'URL d'un dépôt distant :
  
  ```bash
  git remote set-url origin <nouvelle-url-du-dépôt>
  ```
  Met à jour l'URL associée au dépôt distant `origin`. Utilisez cette commande si l'URL du dépôt distant change.
<br>
<br>
<br>

### 🔹 Renommer un dépôt distant :
  
  ```bash
  git remote rename <ancien-nom> <nouveau-nom>
  ```
  Change le nom d'un dépôt distant.

  *Exemple :* `git remote rename origin upstream`
<br>
<br>
<br>

### 🔹 Vérifier le statut des fichiers :
  
  ```bash
  git status
  ```
  Affiche le statut des fichiers dans le dépôt, montrant quels fichiers ont été modifiés, lesquels sont prêts pour le commit et lesquels ne sont pas suivis.
<br>
<br>
<br>

### 🔹 Ajouter des fichiers à l'étape (pour être commis) :
  
  ```bash
  git add <fichier>
  ```
  Ajoute un fichier spécifique à l'étape, le préparant pour le commit. 

  *Exemple :* `git add index.html`
  
  **OU**
  
  ```bash
  git add .
  ```
  Ajoute tous les fichiers modifiés.
<br>
<br>
<br>

### 🔹 Faire un commit des changements :
  
  ```bash
  git commit -m "Message du commit"
  ```
  Enregistre les changements dans le dépôt avec un message descriptif. Le message doit expliquer ce qui a été modifié.

  *Exemple :* `git commit -m "[FEAT][WIP] Introduit une nouvelle méthode de paiement"`
<br>
<br>
<br>

### 🔹 Pousser :
  
  ```bash
  git push
  ```
  Envoie les changements du dépôt local vers le dépôt distant associé. Par défaut, la commande envoie au branche actuelle.
<br>
<br>
<br>

### 🔹 Tirer des changements du dépôt distant :
  
  ```bash
  git pull
  ```
  Télécharge et intègre les changements du dépôt distant vers le dépôt local. Combine `git fetch` et `git merge` en une seule commande.
<br>
<br>
<br>

### 🔹 Rechercher des mises à jour du dépôt distant :
  
  ```bash
  git fetch
  ```
  Télécharge les changements du dépôt distant sans les intégrer dans le dépôt local. C'est utile pour vérifier les mises à jour avant de faire un merge ou un rebase.
<br>
<br>
<br>

### 🔹 Fusionner les changements du dépôt distant :
  
  ```bash
  git merge <branche>
  ```
  Fusionne les changements de la branche spécifiée dans la branche actuelle. Remplacez `<branche>` par le nom de la branche que vous souhaitez fusionner.

  *Exemple :* `git merge feature/nouvelle-fonctionnalité`

---
<br>

## 🔶 Branches
<br>

Les branches (ou ramifications) vous permettent de travailler sur différentes versions du projet simultanément.

### 🔹 Créer une nouvelle branche :

```bash
git branch <nom-de-la-branche>
```
Crée une nouvelle branche.

*Exemple :* `git branch nouvelle-fonctionnalité`
<br>
<br>
<br>

### 🔹 Changer pour une branche existante :

```bash
git checkout <nom-de-la-branche>
```

*Exemple :* `git checkout nouvelle-fonctionnalité`
<br>
<br>
<br>

### 🔹 Créer et changer pour une nouvelle branche :

```bash
git checkout -b <

nom-de-la-branche>
```

*Exemple :* `git checkout -b nouvelle-fonctionnalité`
<br>
<br>
<br>

### 🔹 Lister toutes les branches :

```bash
git branch
```
<br>

### 🔹 Fusionner une branche dans une autre :

```bash
git merge <nom-de-la-branche>
```
Fusionne la branche spécifiée dans la branche actuelle.
<br>
<br>
<br>

### 🔹 Rebaser les changements d'une branche :
  
  ```bash
  git rebase <branche>
  ```
  Réapplique vos changements sur la branche spécifiée. Le rebase est utile pour maintenir un historique linéaire lors de l'intégration des changements.

  *Exemple :* `git rebase main`
<br>
<br>
<br>

### 🔹 Supprimer une branche :

```bash
git branch -d <nom-de-la-branche>
```
Supprime une branche locale. Utilisez `-D` pour forcer la suppression.

*Exemple :* 
`git branch -d nouvelle-fonctionnalité`

---
<br>

## 🔶 Fiches pratiques
<br>

Voici quelques liens vers des fiches pratiques utiles pour Git :

- [Fiche pratique Git](https://education.github.com/git-cheat-sheet-education.pdf)
- [Fiche de commandes Git](https://github.github.io/git-cheat-sheet/)
