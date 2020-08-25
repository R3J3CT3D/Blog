---
layout: post
title: (Rédaction en cours) Quelques astuces pratiques pour Xcode
subtitle: Soyez plus productif avec votre IDE
tags: [xcode]
comments: true
---


Si vous suivez régulièrement les articles présents sur ce blog, il y a fort à parier que vous baignez dans le milieu du développement iOS et donc que vous utilisez régulièrement l'IDE adéquat, j'ai nommé: Xcode.

Ce n'est un secret pour personne, pour être productif et efficace, vous devez connaitre vos outis. C'est pourquoi dans cet article nous allons voir quelques astuces afin d'être plus productif et de gagner du temps lors de l'utilisation d'Xcode. 


# Ouvrir rapidemment un fichier


Comme vous le savez, le développement d'applications iOS requiert un équipement adapté: un mac, ou tout appareil tournant sous le système d'exploitation MacOS. Et, il existe sur MacOS une fonctionnalité très puissante nommée la `Recherche Spotlight`.
Il s'agit d'une barre de recherche universelle qui permet de rechercher n'importe quoi sur votre mac, d'ouvrir des logiciels, d'effectuer des calculs, de faire des recherches Google, et bien d'autres choses.


![1](https://raw.githubusercontent.com/sonnyfournier/blog/master/assets/img/xcode-tips/1.png){: .mx-auto.d-block :}


La barre de recherche peut être invoquée soit en cliquant sur la loupe en haut à droite de votre écran, soit en effectuant le raccourci clavier `CMD` + `Espace`.

> Mais quel rapport avec Xcode ?

J'y arrive. Figurez vous qu'il existe une barre de recherche quelque peu similaire dans Xcode. Quelque peu parce que celle-ci n'offre pas tous les avantages de la `Recherche Spotlight` (ce qui serait inutile puisque vous pouvez invoquer Spotlight à tout moment), mais elle permet d'ouvrir rapidement des fichiers.

Habituellement pour ouvrir un fichier dans Xcode, vous devez le chercher depuis la barre latérale, ce qui n'est pas toujours aisé quand vous avez une grande arborescence de dossiers.


![2](https://raw.githubusercontent.com/sonnyfournier/blog/master/assets/img/xcode-tips/2.png){: .mx-auto.d-block :}


Et bien ceci appartient au passé, puisque comme énoncé précédemment, il existe une barre permettant de chercher et d'ouvrir rapidement un fichier:


![3](https://raw.githubusercontent.com/sonnyfournier/blog/master/assets/img/xcode-tips/3.png){: .mx-auto.d-block :}


Il vous suffira d'effectuer le raccourci clavier `CMD` + `Maj` + `O` et d'écrire les premières lettres de votre fichier pour l'ouvrir. Vous pourrez même rechercher des noms de classes, de structures, et bien d'autres, voilà qui devrait vous faire gagner du temps.


# Retrouver dans le navigateur


Il arrive parfois que vous soyez un train de modifier un fichier et que vous aillez besoin de le retrouver dans le navigateur de projet (l'arborescence des fichiers).

Pour ceci rien de plus simple, il suffit d'effectuer le raccourci clavier `CMD` + `Maj` + `J` afin de le localiser facilement.


# Afficher la documentation


Voilà une astuces que beaucoup doivent déjà connaître, mais pour les moins initiés d'entre vous nul doute qu'elle se révelera très utile.

Ce n'est pas un secret, la documentation est la meilleure amie du développeur. Et bien sachez que toutes les fonctions, méthodes, classes et autres du Swift ont étés documentées.

Pour afficher la documententation d'un élément, il vous suffit de maintenir la touche `Option` (ou `Alt`) et de cliquer sur cet élément.


![4](https://raw.githubusercontent.com/sonnyfournier/blog/master/assets/img/xcode-tips/4.png){: .mx-auto.d-block :}


Dans cet exemple j'ai affiché la documentation de la méthode `point`. En affichant cette documentation je peux lire la description de cette méthode, sa déclaration, et une description des ses paramêtres.
Sachez que vous pouvez aussi afficher la documentation des éléments de votre propre projet.


# Editer dans tout le fichier


Beaucoup d'éditeurs de texte et d'IDE proposent une focntionnalité très pratique, les multis curseurs. Xcode ne dispose malheureusement pas de cette fonctionnalité, mais il existe un équivalent appelé `Edit All in Scope`. Cette fonctionnalité vous permet de modifier toutes les occurences des éléments sélectionnés et de les modifier tous à la fois. Pour utiliser cette fonction, il vous suffit de sélectionner ce que vous souhaitez et d'utiliser le raccourci clavier `Control` + `CMD` + `E`.


![5](https://raw.githubusercontent.com/sonnyfournier/blog/master/assets/img/xcode-tips/5.png){: .mx-auto.d-block :}


Toutes les occurences correspondantes à votre sélection seront alors sélectionnées et vous pourrez modifier toutes ces occurences d'un coup. Cela peut se montrer très utile lorsque vous voulez renommer une variable par exemple.


# Les breakpoints améliorés


Les `breakpoints` sont des éléments indispensables pour débugguer vos projets. Pour les non-initiés, un `breakpoint` est un outil de débug qui permet de mettre en pause l'éxécution de votre programme/application à un moment souhaité. Pour créer un breakpoint, il vous suffit simplement de cliquer sur le numéro de ligne à l'endroit où vous souhaitez le placer (ici ligne `44`).


![6](https://raw.githubusercontent.com/sonnyfournier/blog/master/assets/img/xcode-tips/6.png){: .mx-auto.d-block :}


Et bien sachez qu'il est possible d'améliorer ces breakpoints afin de leurs faire effectuer des actions en plus de mettre l'éxécution en pause. Pour se faire, faites un clic droit sur le breakpoint et cliquer sur `Edit Breakpoint...`


![7](https://raw.githubusercontent.com/sonnyfournier/blog/master/assets/img/xcode-tips/7.png){: .mx-auto.d-block :}


Vous pourrez alors ajouter des fonctionnalités à ce brakpoint telles que par exemple: 
- Un nom
- Des actions: 
    - Jouer un son quand le breakpoint est atteinds
    - Lancer une commande
    - Afficher des logs
- Une condition
- Et bien d'autres...

De cette manière vous pourrez utiliser les breakpoints de manière bien plus efficace et bien plus poussée.


# Conclusion


Voilà pour ces quelques astuces concernant Xcode. J'espère vous avoir appris certaines d'entre elles et qu'elles se montrerons utiles dans votre développement.

Il existe bien évidemment d'autres astuces, c'est pourquoi je vous invite à me faire part de celles que vous connaissez, celles-ci feront peut-être l'object d'un prochain article. 
