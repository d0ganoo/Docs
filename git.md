[Git](https://github.com/d0ganoo/Docs/blob/master/git.md) | [JS Natif](https://github.com/d0ganoo/Docs/blob/master/JS_Natif.md)   | [React](https://github.com/d0ganoo/Docs/blob/master/react.md) | [React native](https://github.com/d0ganoo/Docs/blob/master/react_native.md) | [Nuxt Js](https://github.com/d0ganoo/Docs/blob/master/nuxt.md) | [Test js](https://github.com/d0ganoo/Docs/blob/master/testJS.md) | [BEM](https://github.com/d0ganoo/Docs/blob/master/BEM.md) | [Jest](https://github.com/d0ganoo/Docs/blob/master/Jest.md)


* * * 

Configuration
---
Configurer les informations utilisateur pour tous les repos locaux

<code>git config --global user.name "[name]"</code><br>
Définit le nom que vous souhaitez attacher à vos commits

<code>git config --global user.email "[email address]"</code><br>

<code>git config --global color.ui auto</code><br>
Permet une coloration des lignes de commandes en sortie

Créer des répertoires
---
Démarrer un nouveau repo ou en obtenir un à partir d'une URL existante

<code>git init [project-name]</code><br>
Crée un nouveau repo local avec le nom spécifié

<code>git clone [url]</code><br>
Télécharge un projet et son historique de version

Ajout de fichiers et commit
---

<code>git status</code><br>
Répertorie tous les nouveaux fichiers ou modifiés à être validés

<code>git diff</code><br>
Affiche les différences entre les fichiers qui n'ont pas encore été stage (avant git add .) et les fichiers du dernier commit

<code>git add [file]</code><br>
Mise en zone de staging. Prepare les fichiers pour le versionning

<code>git diff --staged</code><br>
Affiche les différences entre les fichiers dans la zone de staging et les fichiers du dernier commit

<code>git diff-tree --no-commit-id --name-only -r <commit></code><br>
Lister tous les fichiers concernés par un commit

<code>git reset [file]</code><br>
Enlève le fichier de la zone de staging en gardant les modifications apportées au fichier

<code>git commit -m "[descriptive message]"</code><br>
Enregistre les fichiers de la zone de staging dans l'historique de versionning

Branches
---

<code>git branch</code><br>
Liste toutes les branches locales du repo courant

<code>git branch [branch-name]</code><br>
Crée une nouvelle branche

<code>git branch --contains <commit></code><br>
Lister les branches qui contiennent un commit en particulier

<code>git checkout [branch-name]</code><br>
Se déplacer sur une branch

<code>git checkout -b [branch-name]</code><br>
Crée la branche et se positionne dessus

<code>git merge [branch]</code><br>
Combine l'historique de la branche spécifiée dans la branche courante

<code>git branch -d [branch-name]</code><br>
Supprimer une branche

Déplacer et supprimer des fichiers versionnés
---

<code>git rm [file]</code><br>
Supprime le fichier du répertoire de travail et envoye dans la zone de staging le fichier supprimer

<code>git mv [file-original] [file-renamed]</code><br>
Modifie le nom du fichier et le prépare pour le commit (zone de staging)

Voir l'historique
----

<code>git log</code><br>
Liste l'historique des versions de la branche courante

<code>git log --follow [file]</code><br>
Liste l'historique de version pour un fichier spécifique, y compris les fichiers renommés

<code>git log master..[branch-name]</code><br>
Liste uniquement les commit de [branch-name] même si on merge master sur [branch-name]

<code>git diff [first-branch]...[second-branch]</code><br>
Affiche les différences de contenu entre deux branches

<code>git show [commit]</code><br>
Affiche les métadonnées et les changements de contenu pour le commit spécifié

Ignorer les fichiers
---
Exclure les fichiers temporaires et les chemins d'accès
```
*.log
build/
temp-*
```
Un fichier nommé .gitignore permet d'ignorer certains fichiers/dossiers de l'historique de versions

<code>git ls-files --other --ignored --exclude-standard</code><br>
Liste tous les fichiers ignorés dans ce projet

Rétablir un commit
---

<code>git reset [commit]</code><br>
Défait tous les commits après le commit spécifié et garde les modifications localement

<code>git reset --hard [commit]</code><br>
Défait tous les commits après le commit spécifié et et supprime le modification locale.
Permet de revenir à la version du code au moment du commit spécifié

<code>git reflog</code><br>
Revenir sur certaines commandes trop impulsives (comme un reset ou un rebase)

Stash
---
Mettre de côté ou restaurer des modifications incomplètes

<code>git stash</code><br>
Stocke temporairement tous les fichiers modifiés mais pas encore en zone de staging

<code>git stash pop</code><br>
Restaure les fichiers qui ont été stash

<code>git stash list</code><br>
Liste tous les fichiers en zone de stash

Synchroniser les modifications
---

<code>git fetch [bookmark]</code><br>
Télécharge tout l'historique du repo bookmark

<code>git merge [bookmark]</code><br>
Fusionne la branche bookmark avec la branche courante (Se positionner sur la branche sur laquelle on veut faire la fusion)

<code>git push [alias] [branch]</code><br>
Upload tous les commits 

<code>git pull</code><br>
Télécharge tous les commits

Rebase interactif
---

Le rebase interactif permet de retravailler son historique avant de merge<br>

<code>git rebase -i [code commit]</code><br>

pick => utiliser le commit<br>
reword => renommer un commit<br>
squash => permet de fusionner le commit avec le commit précédent <br>
fixup => peremt de fusionner le commit avec le commit précédent mais supprime le log message<br>
drop => supprime un commit<br>

<code>git rebase --abort</code><br>
Permet de quitter le mode rebase 





