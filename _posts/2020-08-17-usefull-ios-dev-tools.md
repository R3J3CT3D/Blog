---
layout: post
title: XX outils utiles pour les développeurs iOS
subtitle: Simplifier vous la vie grâce à ces outils
tags: [dev, tools, ios]
comments: true
---

Connaissez-vous la section [Explore](https://github.com/explore) de Github ? Pour ceux d'entre vous qui ne la connaiseraient pas, c'est une section dans laquelle vous pouvez retouvez les projets en `trending` du moment (ceux qui ont été le plus de stars aujourd'hui), mais aussi des projets basés sur vos intérêts sur Github. Par exemple, si vous avez tendance à star des projets iOS ou même à en créer, Github vous proposera des projets suceptible de vous intérésser. Nous reviendrons sur cette fonctionnalité de Github, ainsi que bien d'autres, dans un futur article.

Aujourd'hui je vais vous présenter différents outils que j'ai pu découvrir dans cette fameuse section. Bien entendu, étant majoritairement porté sur le développement iOS, ces outils seront portés sur ce sujet, c'est parti !


# SimSim


[SimSim](https://github.com/dsmelov/simsim) est un outil développé par [Daniil Smelov](https://github.com/dsmelov). Celui-ci permet d'explorer les dossiers systèmes des applications que vous développer depuis les différents simulateurs iOS. Il se présente comme ceci:


![1](https://raw.githubusercontent.com/sonnyfournier/blog/master/assets/img/usefull-ios-dev-tools/1.png){: .mx-auto.d-block :}


Comme vous le voyez, celui-ci permet plusieurs choses:
- Visualiser les différentes installations de nos applications sur les différents simulateurs
- Effacer les données de des applications
- Ouvrir le dossier système de l'application dans le Finder
- Ouvrir le dossier système de l'application dans un terminal

SimSim se révèle très pratique lorsque vous devez par exemple vérifier que la décompression d'une archive se fait bien ou encore lors du téléchargement de fichiers sur l'appareil.


# CiChlid

[CiChlid](https://github.com/dealforest/Cichlid), développé par [Toshihiro Morimoto](https://github.com/dealforest), est un outil permettant de supprimer les `derived datas` (se traduisant littéralement en `données dérivése`) de manière simple et/ou automatique.

Pour que vous comprenniez mieux l'utilité de cet outil, je vais vous expliquer en quoi il peut s'avérer utile de supprimer ces fameuses `derived datas`.

Il arrive parfois qu'une application ne réagisse pas comme elle le devrait, ou encore qu'elle ne se lance même pas car certaines données d'une précédente compilation sont restées dans le dossier `DerivedData`. Il arrive alors que l'on doive supprimer ce dossier afin de corriger les problèmes.

Pour supprimer le dossier `DerivedData` en temps normal, il faut se rendre dans Xcode, puis dans les préférences de celui-ci, il faut ensuite se rendre dans l'onglet `Locations`, puis appuyer sur le bouton situé sous `DerivedData path` qui ouvrira le dossier `DerivedData` dans le Finder. Pour finir il faudra le supprimer à la main. Une méthode qui peut s'avérée très longue et ennuyante quand nous nous retrouvons confronté au même problème plusieurs dois d'affilées.

C'est la que `CiChlid` entre en jeu. Cet outil se présente de la manière suivante:


![2](https://raw.githubusercontent.com/sonnyfournier/blog/master/assets/img/usefull-ios-dev-tools/2.png){: .mx-auto.d-block :}


Comme vous le voyez, il permet simplement d'ouvrir le dossier `DerivedData` ou encore de supprimer celui-ci depuis la barre d'état d'Xcode. De plus, à chaque fois que vous effecturez un `clean` de votre projet, il supprimera les `derived datas` automatiquement en même temps.


# OpenInTerminal

[OpenInTerminal](https://github.com/Ji4n1ng/OpenInTerminal), développé par [Jianing Wang](https://github.com/Ji4n1ng), est un outil au nom assez explicite. Celui-ci permet d'ouvrir, depuis le Finder, le dossier actuellement ouvert dans votre terminal par défaut.

Cet outil est très simple, il se contente d'ajouter un bouton dans le Finder pour ouvrir le dossier sélectionner dans divers endroits:


![3](https://raw.githubusercontent.com/sonnyfournier/blog/master/assets/img/usefull-ios-dev-tools/3.png){: .mx-auto.d-block :}


`OpenInTerminal` est compatible avec de multiples terminaux et éditeurs de texte.


# Control Room

[Control Room](https://github.com/twostraws/ControlRoom) est développé par [Paul Hudson](https://github.com/twostraws), le créateur du site [Hacking With Swift](https://www.hackingwithswift.com/) très connu dans le milieu du développement Swift.

`Control Room` a initialement été développé de manière personnelle par `Paul hudson`. Celui-ci avait besoin de pouvoir customiser facilement les simulateurs iOS et a donc développé cet outil. Après un avoir fait une démonstration sur [Twitter](https://twitter.com/twostraws/status/1227619436187803648), il a reçu beaucoup de requêtes lui demandant de partager son programme, c'est ainsi que `Control Room` est né.

Cet outil permet une customisation très avancée des simulateurs iOS proposés par Xcode. Grâce à celui-ci vous pourrez notamment:

- Changer l'heure et la date du simulateur
- Basculer entre le light mode et le dark mode
- Changer l'état de la batterie (le pourcentage et si en charge ou non)
- Changer le nom du fournisseur d'accès internet
- Changer la qualité du signal affichée
- Choisir une géolocalisation précise
- Et bien d'autres


![4](https://raw.githubusercontent.com/sonnyfournier/blog/master/assets/img/usefull-ios-dev-tools/4.png){: .mx-auto.d-block :}


![5](https://raw.githubusercontent.com/sonnyfournier/blog/master/assets/img/usefull-ios-dev-tools/5.png){: .mx-auto.d-block :}


`Control Room` peut s'avérer très utile pour tester le dark mode, ou encore pour prendre des captures d'écran avec des informations personnalisées dans le but de les mettre sur l'Apple Store par exemple.


# Conclusion


Et voilà les différents outils que j'avais à vous proposer aujourd'hui. J'espère que ceux-ci vous serons utiles dans le futur.

Je vous invite fortement à allez jeter un oeil sur la fameuse section [Explore](https://github.com/explore) de Github de manière régulière, vous pourrez peut-être dénicher de nouvelles pépites. D'ailleurs, si c'était le cas, je vous invite à m'en faire part pour que je puisse les transmettre au plus grand nombre !