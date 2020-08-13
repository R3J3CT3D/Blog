---
layout: post
title: Des librairies pour des meilleures contraintes
subtitle: Simplifions nous la vie sans storyboards
tags: [ios, xcode]
comments: true
---

Dans le précédent article nous avons vu comment se débarrasser des storyboards afin de développer à la main nos interfaces utilisateurs. À la fin de celui-ci j'avais parlé de librairies permettant de simplifier l'écriture des contraintes. Aujourd'hui nous allons donc voir comment passer de ceci:

```swift
view1.centerXAnchor.constraint(equalTo: superview.centerXAnchor).isActive = true
view1.centerYAnchor.constraint(equalTo: superview.centerYAnchor).isActive = true
```

À ceci:

```swift
view1.snp.makeConstraint {
    $0.center.equalToSuperview()
}
```

Ou encore en:

```swift
view1.center(in: superview)
```

Beaucoup plus simple et lisible non ?


Il existe une multitude de librairies permettant de simplifier l'écriture des contraintes en Swift. Aujourd'hui nous allons parler des deux plus connues, à savoir [Snapkit](https://github.com/SnapKit/SnapKit) (16.7k⭐️) et [TinyConstraints](https://github.com/roberthein/TinyConstraints) (3.5k⭐️).

# Snapkit


## Présentation

Commençons par Snapkit, développée par [Robert Payne](https://github.com/robertjpayne), c'est la librairie que j'utilise personnellement lors du développement de mes projets Swift.

Si j'utilise cette librairie en particulier c'est tout simplement parce que c'est celle-ci que j'ai connu en premier, et étant le plus connue, elle bénéficie de plus de stabilité et de plus de contributeurs.

Nous allons voir dans un premier temps comment installer Snapkit, et nous verrons ensuite comment l'utiliser.


## Installation

Nous allons voir comment installer Snapkit avec [CocoaPods](https://cocoapods.org/) (CocoaPods est gestionnaire de dépendances pour les projets en Objective-C et en Swift, c'est le plus connu et le plus utilisé). Si vous utilisé un autre gestionnaire de dépandence, veuillez vous référez au guide d'installation présent dans la documentation de Snapkit.

Pour installer Snapkit il suffit simplement d'ajouter la ligne suivante dans notre fichier `Podfile`

```ruby
pod 'SnapKit', '~> 5.0.0'
```

> Attention, si vous utilisez Swift 4, veuillez remplacer `5.0.0` par `4.0.0`. La version `5.0.0` étant réservée à Swift 5.

Une fois la ligne ajouter, il suffit de lancer la commande suivante pour procéder à l'installation de la librairie.

```shell
pod install
```



## Utilisation

Nous pouvons à présent utiliser Snapkit pour créer des contraintes dans notre code, voici l'exemple donné dans la documentation

```swift
view1.snp.makeConstraints { (make) -> Void in
    make.width.height.equalTo(50)
    make.center.equalTo(self.view)
}
```

Je propose une légère amélioration au code ci-dessus. En effet, en Swift, les paramètres non nommés peuvent-être remplacés par `$0`, `$1`, `$2`, etc..
Or, lors de la création d'une contrainte nous utilisons uniquement un seul argument (Dans l'exemple précedent `make`), nous pouvons alors le supprimer afin de simplifier le code comme il suit:

```swift
view1.snp.makeConstraints {
    $0.width.height.equalTo(50)
    $0.center.equalTo(self.view)
}
```



## Pour allez plus loin

> En lisant la documentation de Snapkit, vous vous rendrez compte que ce code peut encore être simplifié, notemment en changeant `width.height` en `size`. Je vous encourage grandement à lire la documentation.

Vous trouverez aussi, en complément de la fonction `makeConstraints`, les fonctions `updateConstraints`, `remakeConstraints` et `removeConstraints`, permettant respectivement de mettre à jour, de refaire entièrement ou de supprimer vos contraintes.

Cette article faisant office d'inititation, je vous laisse vous rendre dans la [documentation](http://snapkit.io/docs/) afin d'en apprendre plus sur ces fonctions et sur la librairie en général.


# TinyConstraints


## Présentation

Nous allons à présent survoler la librairie TinyConstraints, crée par [Robert-Hein Hooijmans](https://github.com/roberthein). Je parlerai moins de celle-ci car je l'ai personnelement beaucoup moins utilisée.


## Installation

Pour installer la librairie il suffit de rajouter la ligne suivante dans le `Podfile`

```ruby
pod 'TinyConstraints'
```

Et de lancer la commande suivante:

```shell
pod install
```



## Utilisation

Pour reprendre l'exemple précédent, TinyConstraints nous permet de transformer:

```swift
NSLayoutConstraint.activate([
    view.centerXAnchor.constraint(equalTo: superview.centerXAnchor, constant: 0)
    view.centerYAnchor.constraint(equalTo: superview.centerYAnchor, constant: 0)
])
```

En:

```swift
view.center(in: superview)
```



## Pour allez plus loin

Je ne détaillerai pas plus pour TinyConstraints car comme mentionné plus haut, je l'ai très peu utilisée, je vous redirige donc vers la [documentation](https://github.com/roberthein/TinyConstraints).

Comme vous pouvez le voir, les contraintes sont encore plus simples à écrire qu'avec Snapkit, c'est pourquoi je compte utiliser cette librairie en remplacement de Snapkit.


# Conclusion

Et voilà comment rendre beaucoup plus agréable, lisible et facile l'écriture des contraintes dans vos projets iOS. Après avoir utilisé plus longuement TinyConstraints, j'écrirai un article afin de comparer les deux.