---
layout: post
title: Démarrer un projet Xcode sans storyboard
subtitle: Libérez vous des contraintes des storyboards
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
Commencez par créer un nouveau projet.

![1](https://raw.githubusercontent.com/sonnyfournier/blog/master/assets/img/how-to-no-storyboards/1.png){: .mx-auto.d-block :}

Veillez à ce que `User interface` soit bien définit sur `Storyboard` et non sur `SwiftUI`.

![2](https://raw.githubusercontent.com/sonnyfournier/blog/master/assets/img/how-to-no-storyboards/2.png){: .mx-auto.d-block :}

## 2. Supprimer le storyboard
Une fois le projet crée, séléctionnez Main.storyboard dans le Navigateur (à gauche) et supprimez le. Sur la pop-up qui va s'afficher, appuyez sur `Move to trash`.

![3](https://raw.githubusercontent.com/sonnyfournier/blog/master/assets/img/how-to-no-storyboards/3.png){: .mx-auto.d-block :}

## 3. Supprimer l'interface principale
Séléctionnez votre projet dans le Navigateur (ici NoStoryboards), et rendez-vous sur l'onglet `General`. Localisez le champ `Main Interface` et supprimez le mot `Main` qui s'y trouve.

![4](https://raw.githubusercontent.com/sonnyfournier/blog/master/assets/img/how-to-no-storyboards/4.png){: .mx-auto.d-block :}

## 4. Supprimer la référence dans le fichier Info.plist
Ouvrez le fichier `Info.plist`, localisez la valeur `Storyboard Name` située dans `Application Scene Manifest` > `Scene Configuration` > `Application Session Role` > `Item 0 (Default Configuration)` et appuyez sur le bouton `-`

![5](https://raw.githubusercontent.com/sonnyfournier/blog/master/assets/img/how-to-no-storyboards/5.png){: .mx-auto.d-block :}

## 5. Ajouter la vue de base
Ouvrez le fichier `SceneDelegate.swift` et ajoutez le code suivant dans la fonction `scene(_ scene: UIScene, willConnectTo session: UISceneSession, options connectionOptions: UIScene.ConnectionOptions)`

```swift
guard let windowScene = (scene as? UIWindowScene) else { return }

window = UIWindow(frame: windowScene.coordinateSpace.bounds)
window?.windowScene = windowScene
window?.rootViewController = ViewController()
window?.rootViewController?.view.backgroundColor = .white
window?.makeKeyAndVisible()
```

![6](https://raw.githubusercontent.com/sonnyfournier/blog/master/assets/img/how-to-no-storyboards/6.png){: .mx-auto.d-block :}

Et voilà ! Votre application peut désormais se lancer sans storyboard !