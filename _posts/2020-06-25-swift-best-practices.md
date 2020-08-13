---
layout: post
title: Les bonnes pratiques en Swift
subtitle: Codons oui, mais proprement
tags: [ios, xcode]
comments: true
---

En Swift, comme dans tous les langages de programmation, il est plus que conseillé d'écrire du code propre et lisible. En plus d'améliorer grandement l'évolution du code, il sera aussi plus agréable d'y travailler pour ajouter des fonctionnalités, pour corriger des bugs, ou encore, beaucoup plus facile à lire pour un nouvel arrivant sur le projet.

Dans cet article nous allons voir dans les grandes lignes les bonnes pratiques à adopter en Swift ainsi que des outils nous permettant de suivre ces bonnes pratiques.


# Les guides

Dans le milieu du développement Swift, de grands acteurs ont oeuvrés à la mise en place et à l'écriture de guide de bonnes pratiques et conduite à adopter, nous allons aujourd'hui voir les trois plus connus.

- [Raywenderlich](https://github.com/raywenderlich/swift-style-guide) (10.9k ⭐️)
- [AirBNB](https://github.com/airbnb/swift) (1k ⭐️)
- [Google](https://google.github.io/swift/)


# Raywenderlich

[Raywenderlich](https://www.raywenderlich.com/), créer par Ray Wenderlich, est devenu un site communautaire incontournable dans le milieu du développement. Celui-ci regroupe des milliers de tutoriels divers et variés, tous écrits avec une attention particulière sur la propreté et la qualité du code.

Qui dit site communautaire, dit aussi que n'importe qui (ou presque) peut y écrire des articles, c'est pourquoi le site à décider d'écrire son propre [guide](https://github.com/raywenderlich/swift-style-guide) de bonnes pratiques en Swift, pour que le code soit toujours similaire malgré différents auteurs.


# AirBNB

[AirBNB](https://github.com/airbnb) est un acteur majeur du développement mobile. En effet, lorsque l'entreprise développe une fonctionnalité qui pourrait être utile aux autres développeurs, celle-ci n'hésite pas à la partager le monde et à créer une librairie open-source à destination de tous.

Puisque l'entreprise propose beaucoup de librairies de manière open-source, n'importe qui peut modifier le code afin de proposer des améliorations à celui-ci. C'est pourquoi AirBNB ont eux aussi proposé leur [guide](https://github.com/airbnb/swift) de conduite à adopter, afin de tous ceux qui souhaiteraient améliorer leur code, le fasse avec les mêmes bonnes pratiques qu'en interne.


# Google

[Google](https://google.github.io/swift/) que l'on ne présente plus, on eux aussi proposé leur [guide](https://google.github.io/swift/) au grand public.

Celui-ci est basé sur les retours qu'ont émis les développeurs de l'entreprise lorsqu'ils travaillaient sur des applications en Swift.


# Quel guide utiliser ?

Je vous invite à lire entièrement les trois guides que je vous ai mis à dispositions un peu plus haut, car ce sont vraiment des bases dans le milieu du développement Swift.
De plus, certaines entreprises proposent leur propre guide à leurs employés, et ceux-ci sont la majorité du temps basé sur ceux que nous avons vu.

Lors de votre lecture, vous trouverez certainement des pratiques que vous n'aimerez pas, ou encore, des pratiques qui sont différentes des autres guides. Par exemple, un guide nous dit d'utiliser 2 espaces plutôt que des tabs pour l'indentation, alors qu'un autre nous dit d'utiliser des tabs plutôt que des espaces.

Et c'est la toute l'importance du mot **guide**, ce ne sont pas des règles.


![1](https://raw.githubusercontent.com/sonnyfournier/blog/master/assets/img/swift-best-practices/1.jpg){: .mx-auto.d-block :}


Vous pouvez choisir de suivre aveuglément un guide, ou encore, de vous baser sur des éléments des trois, la seule clé pour coder proprement c'est de se tenir à ce que vous déciderez.
D'ailleurs, en parlant de ça..


# Comment tenir ses engagements envers mon guide ?

Et bien c'est facile, nous allons utiliser un linter !

Pour vulgariser, un linter est un outil dans lequel nous allons spécifier les règles que nous voulons suivres, et qui va s'assurer que nous les suivions bien.

Dans le milieu du développement Swift, il existe plusieurs linters, mais nous allons uniquement parler du plus utilisé et du plus connu ici, j'ai nommé [SwiftLint](https://github.com/realm/SwiftLint).

SwiftLint est un outil initialement développé par [Realm](https://github.com/realm) qui est un énorme acteur du développement iOS, et même du développement en règle générale.

Une fois installé et configuré dans Xcode (tout est expliqué dans le Readme du projet), SwiftLint va lire les règles que nous aurons définit et s'assurer que nous les respections.

Les règles sont définit dans un fichier nommé `.swiftlint.yml`, qui ressemble à ceci:

```yml
# Une règle qui produira un warning si un fichier dépasser les 500 lignes
# Et qui produira une erreur (qui nous empechera de compiler) si ça dépasse les 1200 lignes
file_length:
  warning: 500
  error: 1200
# Une règle qui agit sur les noms de variables
type_name:
  min_length: 4 # Un nom de variable doit faire 4 caractères minimum
  max_length:
    warning: 40 # Produira un warning si un nom de variable fait plus de 40 caractères
    error: 50 # Produira une erreur si un nom de variable fait plus de 50 caractères
  excluded: id # id étant un nom de variable très utile et utilisé, celui-ci ne sera pas impacté par la règle des 4 caractères minimum
```

Comme vous pouvez le voir, SwiftLint nous permet de définir des règles assez poussées, et en créant des warnings et des erreurs, s'assure que nous suivions toujours les règles que nous nous sommes imposées.

> Il existe beaucoup de règles paramétrables, vous pourrez retrouver toutes les informations nécessaires dans la [documentation](https://github.com/realm/SwiftLint)


# Conclusion

Bien qu'il existe une multitude de guides, je vous conseille de créer le votre en piochant dans les plus connu, et d'entrer toutes les règles que vous voulez/devez suivre dans SwiftLint (que je vous conseille d'installer à chaque projet Swift que vous créerez) afin de produire du code qui se ressemblera toujours, et sera toujours agréable et facile à lire et à maintenir.

Nous verrons dans un prochain article comment commencé un projet iOS facilement sans storyboards, avec SnapKit et SwiftLint d'installer par défaut pour éviter la répétition à chaque nouveau projet.