---
layout: post
title: Démarrer un projet Xcode sans storyboard
subtitle: Libérez vous de la contrainte des storyboards
tags: [ios, xcode]
comments: true
---

Dans le milieu du développement iOS, l'utilisation des storyboards est assez controversée. Aujourd'hui nous allons voir comment se passer des storyboards et gérer nos interfaces utilisateurs à la main.

# Qu'est-ce qu'un storyboard ?

Pour reprendre la définition officielle d'Apple:
> Un storyboard est une représentation visuelle de l'interface utilisateur d'une application iOS, montrant des écrans de contenu et les connexions entre ces écrans. Un storyboard est composé d'une séquence de scènes, chacune représentant un contrôleur de vue et ses vues ; les scènes sont reliées par des objets enchaînés, qui représentent une transition entre deux contrôleurs de vue.

Nous pouvons retrouver dans Xcode un éditeur de storyboard qui permet de rajouter facilement des éléments dans nos écrans avec un simple glisser-déposer.

![Storyboard](https://raw.githubusercontent.com/sonnyfournier/blog/master/assets/img/how-to-no-storyboards/intro.png){: .mx-auto.d-block :}

# Pourquoi supprimer les storyboards ?

Comme dit plus haut, l'utilisation des storyboards est assez controversée et certains développeurs préfèrent s'en passer et créer le design de leurs applications avec du code directement.

Mais pourquoi vouloir supprimer les storyboards ? Bien qu'il existe une multitude de réponses à cette question je me contenterai de citer les deux qui m'ont fait me passer des storyboards.

### 1. C'est lent
On retrouve dans un storyboard toutes les informations d'un écran jusqu'à ses moindres subtilités. Que ce soit la taille de l'écran, la couleur d'un bouton, à combien de pixel ce bouton doit se situer du côté droit de l'écran, du côté gauche de l'écran, et j'en passe..

Le problème avec ceci c'est qu'Xcode affiche toutes ces informations dans son éditeur de storyboard, et plus le projet va grandir, plus ça deviendra long d'ouvrir et d'éditer ces fameux storyboards.

### 2. Les modifications sont fastidieuses
Une fois que tous vos écrans sont créés il devient très difficile de modifier certaines choses. Par exemple, si un jour vous décidez de changer la police d'écriture de votre application, vous devrez parcourir tous les éléments suceptible d'afficher du texte, dans tous les écrans, dans tous vos storyboards. Une tâche qui peut se montrer très longue et fastidieuse, sans compter les multitude d'oublis potentiels.

# Comment procéder ?

## 1. Créer un nouveau projet
Nous allons commencer par créer un nouveau projet.

![1](https://raw.githubusercontent.com/sonnyfournier/blog/master/assets/img/how-to-no-storyboards/1.png){: .mx-auto.d-block :}

Il faut bien veiller à ce que `User interface` soit bien définit sur `Storyboard` et non sur `SwiftUI`.

![2](https://raw.githubusercontent.com/sonnyfournier/blog/master/assets/img/how-to-no-storyboards/2.png){: .mx-auto.d-block :}

## 2. Supprimer le storyboard
Une fois le projet crée, nous allons sélectionner `Main.storyboard` dans le Navigateur (à gauche) et nous allons le supprimer. Sur la pop-up qui va s'afficher, nous appuierons sur `Move to trash`.

![3](https://raw.githubusercontent.com/sonnyfournier/blog/master/assets/img/how-to-no-storyboards/3.png){: .mx-auto.d-block :}

## 3. Supprimer l'interface principale
Nous allons maintenant sélectionner notre projet dans le Navigateur (ici NoStoryboards), et nous rendre sur l'onglet `General`. Puis, dans le champ `Main Interface` et nous allons supprimer le mot `Main` qui s'y trouve.

![4](https://raw.githubusercontent.com/sonnyfournier/blog/master/assets/img/how-to-no-storyboards/4.png){: .mx-auto.d-block :}

## 4. Supprimer la référence dans le fichier Info.plist
Ouvrons le fichier `Info.plist`, nous allons localiser la valeur `Storyboard Name` située dans `Application Scene Manifest` > `Scene Configuration` > `Application Session Role` > `Item 0 (Default Configuration)` et appuyer sur le bouton `-` pour la supprimer.

![5](https://raw.githubusercontent.com/sonnyfournier/blog/master/assets/img/how-to-no-storyboards/5.png){: .mx-auto.d-block :}

## 5. Ajouter la vue de base
À présent nous allons nous rendre dans le fichier `SceneDelegate.swift` et ajouter le code suivant dans la fonction `scene(_ scene: UIScene, willConnectTo session: UISceneSession, options connectionOptions: UIScene.ConnectionOptions)`

```swift
guard let windowScene = (scene as? UIWindowScene) else { return }

window = UIWindow(frame: windowScene.coordinateSpace.bounds)
window?.windowScene = windowScene
window?.rootViewController = ViewController()
window?.rootViewController?.view.backgroundColor = .white
window?.makeKeyAndVisible()
```

![6](https://raw.githubusercontent.com/sonnyfournier/blog/master/assets/img/how-to-no-storyboards/6.png){: .mx-auto.d-block :}

Et voilà ! Notre application peut désormais se lancer sans storyboard. Mais ce n'est pas finit pour autant, il nous faut maintenant voir comment ajouter des éléments d'interface directement depuis le code.

# Comment ajouter des éléments

Pour l'exemple, nous allons voir comment ajouter un simple label dans notre application. Commençons par ouvrir le fichier `ViewController.swift`.

Nous allons commencer par créer un simple label comme il suit:

```swift
let label = UILabel()
```

Par la suite nous allons pouvoir customiser notre label dans la fonction `viewDidLoad`. Dans cette exemple, nous allons lui assigner du texte comme ceci:

```swift
label.text = "Hello World"
label.translatesAutoresizingMaskIntoConstraints = false
```

Il faut ensuite l'ajouter en tant que subView dans la view du viewController:

```swift
view.addSubview(label)
```

Il ne nous reste plus qu'a définir les contraintes de notre label afin de le postionner ou nous voulons. Ici nous allons le placer au centre de la vue.
Nous allons placer le code des contraintes dans une fonctions à part que nous appelerons depuis `viewDidLoad` pour plus de clarté et de propreté.

```swift
private func setupConstraints() {
    label.centerXAnchor.constraint(equalTo: view.centerXAnchor).isActive = true
    label.centerYAnchor.constraint(equalTo: view.centerYAnchor).isActive = true
}
```

Ce qui nous donne pour finir:

![7](https://raw.githubusercontent.com/sonnyfournier/blog/master/assets/img/how-to-no-storyboards/7.png){: .mx-auto.d-block :}

Et sur le simulateur:

![8](https://raw.githubusercontent.com/sonnyfournier/blog/master/assets/img/how-to-no-storyboards/8.png){: .mx-auto.d-block :}

Et voilà comment ajouter des nouveaux éléments depuis du code.
Pour ma part, je trouve que la gestion des contraintes n'est pas très intuitive nativement. Dans un prochain article je vous montrerai quelques librairies qui ont pour but de rendre l'écriture des contraintes beaucoup plus simple et intuitive.