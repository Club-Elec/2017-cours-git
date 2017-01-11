# Introduction à Git
![](assets/git_logo.png)<!-- .element: class="plain" style="height: 40%; width: auto; opacity: 0.8;" -->


## Who am I?

![](assets/pp-moz-round.png)<!-- .element: class="plain" width="300px" -->

**Brendan Abolivier**

M1 Télécoms et Réseaux

[@BrenAbolivier](https://twitter.com/BrenAbolivier)


## Git: WTF?

* Travail collaboratif
* Gestion de version
	- Trace de tous les changements
	- "Voyage dans le temps"

--------------------

# Quelques notions

--------------------

# Serveur / local
<!-- .slide: data-background="assets/connection.gif" -->

Deux utilisations distinctes


## Local

*Garder une trace de toutes ses modifications*

Utile pour :

* Travailler hors ligne
* Garder une trace d'un état stable
* Revenir en arrière sur un mauvais travail
* ...


## Local : Je travaille où ?

Sur mon ordinateur !


## Serveur

*Travailler en équipe*

Utile pour :

* Développer un projet à plusieurs
* Garder une sauvegarde de son travail en ligne
* Publier les sources de son projet
* ...


## Serveur : Je travaille où ?

Sur l'infrastructure d'un hébergeur

* GitHub (https://github.com/)
* GitLab (https://gitlab.com/)

Sur ma propre infrastructure

* GitLab (https://gitlab.com/)
* Gitea (https://gitea.io/)
* SSH
* ...


## Serveur : Le push-pull

* Push : J'envoie mes modifications
* Pull : Je récupère des modifications

--------------------

# Dépôts

<!-- .slide: data-background="assets/cnh-home.gif" -->


## L'emplacement de votre projet

* Se situe sur le serveur
* Contient toutes les ressources du projet
* "Lieu" de consultation et de modification

--------------------

# Commits

<!-- .slide: data-background="assets/bttf.gif" -->


## Repères

Trace datée du moindre changement dans le projet

![](assets/commit.png)


## Les commits, ça s'empile

![](assets/stack.gif)

--------------------

## En résumé

* Mon projet est à deux endroits à la fois :
	- Sur **mon ordinateur**
	- Sur **un serveur**
* Il se trouve dans un **dépôt** (sur le serveur)
* Je décris mes modifications dans un **commit**
* J'envoie mes modifications sur le serveur avec un **push** (je **pousse** mes modifications)
* Je récupère les modifications d'un autre depuis le serveur avec un **pull** (je **tire** les modifications)

--------------------

# En pratique


## Création d'un dépôt

Ça se fait côté serveur

![](assets/new-repo.png)


## (GitHub)

![](assets/new-repo-github.png) <!-- .element: width="60%" -->


## Récupération du dépôt en local

```bash
git clone https://web.isen-bretagne.fr/gitlab/baboli18/test.git
``` 
<!-- .element: style="font-size:62%;text-align:center" -->

Ici, l'adresse de mon dépôt est https://web.isen-bretagne.fr/gitlab/baboli18/test.git


## Envoi de modifications

Création du commit

```bash
git add [...]
git rm [...]
git commit -m "Mon super commit"
```
<!-- .element: style="font-size:100%;" -->

Envoi du commit

```bash
git push
```
<!-- .element: style="font-size:100%;" -->


## Fragmenter ses modifications

Création de plusieurs commits

```bash
git add app.js
git commit -m "Fonctionnalité X"
git rm obsolete.js
git commit -m "Suppression de obsolete"
```
<!-- .element: style="font-size:100%;" -->


Envoi
```bash
git push
```
<!-- .element: style="font-size:100%;" -->


## Récupérer des modifications

```bash
git pull
```
<!-- .element: style="font-size:100%;" -->

--------------------

# Les branches

Ton projet est un arbre

![](assets/tree.gif) <!-- .element: width="30%" -->


## Kékecé ?

* Branche initiale : *master*
* On "tire une branche" pour :
	- Développer des fonctionnalités
	- Effectuer des relectures de code
	- Assurer la stabilité du projet
* Généralement une copie à un moment t de *master* + changements

## Conventions

La plupart du temps, on gère son projet en suivant ces conventions :

* *master* : Branche principale du projet
* *dev* : Contient les développements en cours
* *feature/[...]* : Développement d'une fonctionnalité
* *fix/[...]* : Développement d'une correction de bug

Note : Seule *master* est créée automatiquement


## Passer d'une branche à l'autre

On demande la **fusion** d'une branche dans une autre

* GitLab : *Merge requests*
* GitHub : *Pull requests*

(mais en vrai, c'est la même chose)


## Les merge requests

![](assets/merge-request.png) <!-- .element: width="70%" -->


## Exemple

__Alice et Bob travaillent sur un projet.__

__Alice veut ajouter un formulaire au projet.__

0. Elle crée la branche *feature/formulaire*
0. Elle y développe le formulaire
0. Elle ouvre une merge request de *feature/formulaire* vers *dev*
0. Bob relit le code d'Alice et fusionne sa branche

__Le formulaire d'Alice est maintenant dans *dev*__


## Le cas de *master*

* Branche principale du projet
* État **stable** du projet
	* N'importe qui doit pouvoir l'utiliser

__On fusionne dans *master* quand :__

* On sort une nouvelle version du projet
* On sort un correctif d'un bug critique


## Exemple, seconde partie

__Alice et Bob ont rajouté plusieurs fonctionnalités à leur projet.__

0. L'un.e des deux ouvre une merge request de *dev* vers *master*
0. Les deux relisent les changements depuis la dernière mise à jour de *master*
0. L'autre fusionne *dev* dans *master*

--------------------