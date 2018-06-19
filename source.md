# Formation GIT

![image](images/Git-Icon.png)



#  Kevin MARCELLIER

<i class="fab fa-github"></i> Dunska

<i class="fab fa-twitter"></i> Buck_LSN

![image](images/Apside.png)

Note:
* Apside depuis 7 ans
* Formation de formateur occasionnel



# Objectifs

* Comprendre le fonctionnement général de GIT
* Savoir utiliser les commandes de bases de GIT
* Etre autonome sur GIT
* Connaitre les outils autour de GIT



# Plan de la Formation

- GIT, un SCM décentralisé
- Les objets GIT
- Mise en place de GIT
- Les bases : Le staging et les commits
- Les commandes de bases
- Les remotes



# Plan de la Formation

- Les branches
- Jouer avec les commits
- Les alias
- Les hooks
- GitHub et les Pull Request
- Les IHM et outils



# Tour de table

![image](images/meeting.gif)


====

# Git, c'est quoi ?

> Git is a free and open source distributed version control system designed to handle everything from small to very large projects with speed and efficiency.



# SCM

* CVS
* Subversion
* Perforce
* ClearCase
* Mercurial



# Histoire

* 1991 → 2002 : Linux utilise tarball
* 2002 : Passage à BitKeeper (licences offertes)
* Avril 2005 : Fin de la licence gratuite
* 7 Avril 2005 : Première version de Git

> I'm an egotistical bastard, and I name all my projects after myself. First 'Linux', now 'git'.



## Décentralisé

![image](images/DCVS.png)

Note:
* Techniquement, pas besoin de serveur
* Presque tout se passe donc en local
* Après un clone, tout l'historique du projet est en local et ne nécessite plus aucun accès réseau pour le manipuler


==== 

# Les 4 types d'objets

* Blob
* Tree
* Commit
* Tag



# Blob

Contenu d'un fichier identifié par un hash

![image](images/object-blob.png)



# Tree

Liste de références vers des hashes

![image](images/object-tree.png)



# Commit

Référence le hash d'un tree + métadonnées

![image](images/object-commit.png)

Note: 
* Identifié par un hash _SHA-1_
* Version courte ≥ 4 caractères possible (si non ambiguë)



If all __6.5 billion humans__ on Earth were programming, and __every second__, each one was producing code that was the equivalent of the __entire Linux kernel history__ (1 million Git objects) and pushing it into one enormous Git repository, it would take __5 years until__ that repository contained enough objects to have a __50%__ probability of a single SHA-1 object collision.

![image](images/unbelievable.gif)



# Tag

Nom donné à un commit + métadonnées

![image](images/object-tag.png)



# Un commit

![image](images/commit.png)



# Les commits

![image](images/commits.png)



# Orienté contenu

![image](images/snapshots-vs-delta.png)

Note:
Des Snapshots, pas des diffs...


====

# On commence ?

<pre><code class="bash">$ git --version
git version 2.7.4
</code></pre>

<pre><code class="bash">$ git config --global user.name "Kevin Marcellier"
$ git config --global user.email kevin@marcellier.fr
</code></pre><!-- .element: class="fragment" -->

Note:
* Global vs Local



# Créer un repo

<pre><code class="bash">$ mkdir mon-projet-git
$ cd mon-projet-git
$ git init
Initialized empty Git repository in mon-projet-git/.git/
$ git commit -m "Initial commit" --allow-empty
[master (root-commit) 53b89fc] Initial commit
</code></pre>



### Le staging et les commits

![image](images/areas.png)



# Mon premier commit 

<pre><code class="bash">$ touch monFichier.txt
$ git add monFichier.txt
$ git commit -m "Création d'un premier fichier."
[master 2ce6ac4] Création d'un premier fichier.
0 files changed
create mode 100644 monFichier.txt
</code></pre>

====

## Des commandes de bases

![image](images/coder.gif)



# Log


<pre><code class="bash">$ git log --pretty=oneline

$ git log --pretty=format:"%h - %an, %ar : %s"

$ git log --pretty="%h - %s" --author=gitster 
--since="2008-10-01" --before="2008-11-01" --no-merges

$ git log -p -2

$ git log --graph 
--pretty=format:"%Cred%h%Creset -%C(yellow)%d%Creset %s 
%Cgreen(%cr) %C(bold blue)<%an>%Creset"
--abbrev-commit -12
</code></pre>



# Diff

<pre><code class="bash">$ git diff 
$ git diff 15a2f5d6 1299bb45a
</code></pre>



# Tag

<pre><code class="bash">$ git tag -a v1.4 -m "my version 1.4"
$ git tag -a v1.2 9fceb02
$ git tag --list "v1.8.5*"
</code></pre>



# Reflog

Un filet de sécurité qui peut vous sauver la vie

<pre><code class="bash">$ git reflog
2ce6ac4 HEAD@{0}: checkout: moving from nouvellebranche to master
07df291 HEAD@{1}: checkout: moving from 07df291f4d7fc93b10f28ae25c04fff67d674f30 to nouvellebranche
07df291 HEAD@{2}: commit: Nouveau commit
53b89fc HEAD@{3}: checkout: moving from master to 53b89fc
2ce6ac4 HEAD@{4}: commit: Création du premier fichier indispensable.
53b89fc HEAD@{5}: commit (initial): Initial commit
</code></pre>

