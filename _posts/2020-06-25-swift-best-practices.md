---
layout: post
title: Les bonnes pratiques en Swift
subtitle: Codons oui, mais proprement
tags: [ios, xcode]
comments: true
---

En Swift, et comme dans tous les languages de programation, il est plus que conseillé d'écrire du code propre et lisible. En plus d'améliorer grandement la maintenabilité du code, il sera aussi plus agréable d'y travailler pour ajouter des fonctionnalités, pour corriger des bugs, ou encore, beaucoup plus facile à lire pour un nouvel arrivant sur le projet.

Dans cet article nous allons voir dans les grandes lignes les bonnes pratiques à adopter en Swift ainsi que des outils nous permettant de suivre ces bonnes pratiques.


# Les guides

Dans le milieu du développement Swift, des grands acteurs ont oeuvrés à la mise en place et à l'écriture de guide des bonnes pratiques et conduite à adopter, nous allons aujourd'hui voir les trois plus connus.

- [Raywenderlich](https://github.com/raywenderlich/swift-style-guide) (10.9k ⭐️)
- [AirBNB](https://github.com/airbnb/swift) (1k ⭐️)
- [Google](https://google.github.io/swift/)


# Raywenderlich

[Raywenderlich](https://www.raywenderlich.com/), créer par Ray Wenderlich, est devenu un site communautaire incontournable dans le milieu du développement. Celui-ci regroupe des miliers de tutoriels divers et variés, tous écrits avec une attention particulière sur la propreté et la qualité du code.

Qui dit site communautaire, dit aussi que n'importe qui (ou presque) peut y écrire des articles, c'est pourquoi le site à décidé d'écrire son propre [guide](https://github.com/raywenderlich/swift-style-guide) des bonnes pratiques en Swift, pour que le code soit toujours similaire malgré différents auteurs.


# AirBNB

[AirBNB](https://github.com/airbnb) est un acteur majeur du développement mobile. En effet, lorsque l'entreprise développe une fonctionnalité qui pourrait être utile aux autres développeurs, celle-ci n'hésite pas à en faire partager le monde et à en créer une librairie open-source à destination de tous.

Puisque l'entreprise propose beaucoup de librairies de manière open-source, n'importe qui peut modifier le code afin de proposer des améliorations à celui-ci. C'est pourquoi AirBNB ont eux aussi proposé leur [guide](https://github.com/airbnb/swift) de conduite à adopter, afin de tous ceux qui souhaiteraient améliorer leur code, le fasse avec les mêmes bonnes pratiques qu'en interne.


# Google

[Google](https://google.github.io/swift/) que l'on ne présente plus, on eux aussi proposé leur [guide](https://google.github.io/swift/) au grand public.

Celui-ci est basé sur les retours qu'ont émis les développeurs de l'entreprise lorsqu'ils travaillaient sur des applications en Swift.


# Quel guide utiliser ?

Je vous invite à lire entièrement les trois guides que je vous ai mis à dispositions un peu plus haut, car ce sont vraiment des bases dans le milieu du développement Swift.
De plus, certaines entreprises proposent leur propre guide à leur employés, et ceux-ci sont la majorité du temps basé sur ceux que nous avons vu.

Lors de votre lecture, vous trouverez certainement des pratiques que vous n'aimerez pas, ou encore, des pratiques qui sont différentes des autres guides. Par exemple, un guide nous dit d'utiliser 2 espaces plutôt que des tabs pour l'indentation, alors qu'un autre nous dit d'utiliser des tabs plutôt que des espaces.

Et c'est là toute l'importance du mot **guide**, ce ne sont pas des règles.


![1](https://raw.githubusercontent.com/sonnyfournier/blog/master/assets/img/swift-best-practices/1.jpg){: .mx-auto.d-block :}


Vous pouvez choisir de suivre aveuglément un guide, ou encore, de vous baser sur des éléments des trois, la seule clé pour coder proprement c'est de se tenir à ce que vous décidrez.
D'ailleurs, en parlant de ça..


# Comment tenir ses engagements envers mon guide ?

Et bien c'est facile, nous allons utiliser un linter !

Pour vulgariser, un linter est un outil dans lequel nous allons spécifier les règles que nous voulons suivres, et qui va s'assurer que nous les suivions bien.

Dans le milieu du développement Swift, il existe plusieurs linters, mais nous allons uniquement parler du plus utilisé et du plus connu ici, j'ai nommé [SwiftLint](https://github.com/realm/SwiftLint).

SwiftLint est un outil initialement développé par [Realm](https://github.com/realm) qui est un énorme acteur du développement iOS, et même du développement en règle générale.

