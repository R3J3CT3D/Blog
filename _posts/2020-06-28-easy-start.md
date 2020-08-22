---
layout: post
title: Éviter la répétition lors d'un nouveau projet
subtitle: Ne refaites pas les mêmes choses encore et encore
tags: [ios, xcode]
comments: true
---

Si vous avez suivi les précédents articles, vous avez pu apercevoir que je me suis positionné sur une méthode bien particulière de développement de mes applications iOS.

En effet, je n'utilise pas de storyboards, j'utilise Snapkit pour créer et gérer mes contraintes et pour construires mes interfaces utilisateurs grâce au code, j'utilise SwiftLint pour suivre des règles de développement et ainsi m'assurer d'avoir un code propre et lisible, j'ai créer des extensions utiles qui me suivent de projet en projet, bref, tant de choses que je dois faire et refaire à chaque nouveau projet.

Aujourd'hui, je vais vous montrez comment j'ai créer un template d'applications sur Github afin de le réutiliser tout le temps dans le but d'éviter de répéter sans cesse les mêmes actions.

# La création du projet

Je vais commencer par créer un projet Xcode tout ce qu'il y a de plus banal que je vais nommer `SwiftTemplate` et retirer le storyboard principal comme je vous l'ai montré dans un précédent article ([Démarrer un projet sans storyboard](https://sonnyfournier.github.io/blog/2020-06-23-how-to-no-storyboards/)).

# Les Pods

Depuis un terminal, je vais à présent créer un `Podfile` pour nos futurs Pods avec la commande suivante:

```shell
pod init
```

Ensuite je vais ajouter les Pods Snapkit (voir [les librairies pour des meilleures contraintes](https://sonnyfournier.github.io/blog/2020-06-24-libs-for-constraints/)) et SwiftLint en ajoutant les lignes suivantes dans mon `Podfile``

```ruby
    pod 'SnapKit'
    pod 'SwiftLint' 
```

Et je les installe avec la commande suivante:

```shell
pod install
```

Les Pods sont maintenant installés.

# Configuration de SwiftLint

Je vais maintenant définir mes règles SwiftLint afin de conserver un code lisible et propre, je configure alors mon fichier comme il suit:

```yml
excluded:
  - Pods
line_length: 130
nesting:
  type_level:
    warning: 3
```

Vous pouvez voir que je mets par défaut assez peu de règles car celles configurées par défaut par SwiftLint me conviennent parfaitement. J'ajouterai peut-être des exceptions concernant certains noms de variables par la suite (voir [les bonnes pratiques en Swift](https://sonnyfournier.github.io/blog/2020-06-25-swift-best-practices/)).

# Configuration des git hooks

Pour résumer simplement, les git hooks sont des actions qui peuvent être réalisées en fonctions des actions git. Par exemple, on peut executer un script shell à chaque fois que quelqu'un commit quelque chose.

Dans mon cas, j'aimerai forcer SwiftLint à vérifier que je n'ai pas commis d'erreur avant chaque commit.

Pour ce faire, je créer un fichier nommé `pre-commit` et le placer dans le dossier `.git/hooks`.

> Ne pas oublier de lui donner les droits d'excution avec la commande `chmod`

Ce fichier étant générique je ne vais pas posté son contenu ici, vous pourrez le retrouver à la fin de cet article.

# Configuration du .gitignore

Pour les non-initiés, le fichier `.gitignore` permet de préciser les fichiers qui ne devront pas être push sur le repo git. J'utilise personnellement un template de `.gitignore` proposé par Github que je modifie à ma guise (Notamment pour le dossier Pods, voir [Faut-il push le dossier Pods](https://sonnyfournier.github.io/blog/2020-06-27-pods-or-not-pods/)) que vous pouvez retrouver [ici](https://github.com/github/gitignore/blob/master/Swift.gitignore).

# Les extensions

Je vais maintenant ajouter les extensions que j'utilise régulièrement dans mon projet (voir [quelques extensions Swift utiles](https://sonnyfournier.github.io/blog/2020-06-26-usefull-swift-extensions/)), et je vais en profiter pour créer une belle arborescence de fichiers que vous verrez par la suite.

# Le template

Notre projet est maintenant basique, mais fonctionnel, nous avons mis ensemble les bases qui pourront servir à tous nos nouveaux projets.

Je vais maitenant vous montrez comment créer un template sur Github.

Pour ce faire, nous allons nous rendre dans les paramètres du repo et de cocher la case `Template repository` située sous le nom du repo (voir [Creating a template repository](https://docs.github.com/en/github/creating-cloning-and-archiving-repositories/creating-a-template-repository)).

# La fin ?

Parfait, notre repo template est maintenant terminé, un bouton `Use this template` est maintenant apparu à côté du bouton `Clone` sur la page de notre repo, mais est-ce finit pour autant ?

Et bien la réponse est.. oui et non. Oui parce que vis-à-vis du template nous n'avons plus rien à faire. Non parce que lorsqu'un utilisateur va vouloir utiliser ce template, il va se retrouver avec un beau projet tout propre, mais nommé `SwiftTemplate`, et ça c'est par forcément l'idéal..

# Le setup

L'utilisateur aura donc deux choix, soit il va devoir renommer tous les endroits où il est mentionné `SwiftTemplate`, soit il utilisera un script, un script que j'ai donc du créer.

Je ne vais pas poster le code du script ici car cela n'est pas très important, mais je vais vous résumer tout ce que celui-ci effectue.

Le script s'execute de la manière suivante:

```shell
./setup.swift LeNomDuProjetQueLonSouhaite
```

1. Il va commencer par vérifier que toutes les dépendances nécéssaires sont installés sur l'ordinateur de l'utilisateur, comme Cocoapods par exemple.

2. Supprimer le dossier Pods, car ceux-ci sont générés en fonction du nom du projet, et comme nous allons le renommer, nous les génererons plus tard.

3. Il va ensuite renommer tous les fichiers contenant `SwiftTemplate`, en remplaçant `SwiftTemplate` par le nom désiré.

4. Par la suite il va remplacer les occurences de `SwiftTemplate` par le nom du projet à l'intérieur de tous les fichiers.

5. Il va ensuite procéder à la réinstallation des Pods.

6. Il va remettre en place les `git hooks` sur le repo actuel.

7. Ensuite, le script va ouvrir le projet dans Xcode.

8. Pour finir, le script va s'auto-détruire et se supprimer lui-même.

Et voilà !

# Conclusion

Tout est terminé, maintenant, dès que je voudrai créer un nouveau projet, je n'aurai que deux petites étapes à effectuer:

1. Cliquer sur le bouton `Use this template`

2. Lancer le script `setup.swift`

Et c'est tout, un gain de temps considérable !

Pour ceux d'entre vous qui seraient interéssés, vous pouvez retrouver le template [ici](https://github.com/sonnyfournier/SwiftTemplate).

C'est tout pour aujourd'hui. J'ajouterai que j'aimerai beaucoup que Github permette d'éxecuter un script juste après qu'un utilisateur appuie sur `Use this template` afin que tout se fasse de manière automatique et d'éviter à l'utilisateur de lancer manuellement notre script.