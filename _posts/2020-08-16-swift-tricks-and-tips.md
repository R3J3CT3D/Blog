---
layout: post
title: 3 astuces pour améliorer votre code en Swift
subtitle: Écrire du meilleur code c'est gagner du temps
tags: [ios, xcode]
comments: true
---

Si vous faites parti de mes lecteurs régulier, vous devez très certainement bercer dans le milieu du développement iOS, et plus particulière en Swift.

Bien que les bases du Swift soient facile à apprendre et à maitriser, le fait d'ulitiser le language au quotidien permets d'apprendre et de découvrir des fonctionnalités moins connues. Aujourd'hui, je vais vous montrez quelques astuces que j'ai découvert avec le temps. J'espère que celles-ci vous seront utiles et qu'elles permettront d'améliorer la qualité de votre code et sa lisibilité.

Commençons sans plus tarder !


# Des extensions pour vos constantes


Comme vous le savez certainement, je me passe des storyboards dans mon développement et j'écris toutes mes interfaces utilisateurs directement avec du code grâce à la librairie `Snapkit` pour gérer mes contraintes (voir [Démarrer un projet Xcode sans storyboard](https://sonnyfournier.github.io/blog/2020-06-23-how-to-no-storyboards/) et [Des librairies pour des meilleures contraintes](https://sonnyfournier.github.io/blog/2020-06-24-libs-for-constraints/)).

Et il arrive très souvent que nous aillons recours à des nombres constants lors de l'écritures de contraintes, par exemple, pour créer des marges:


```swift
private func setupConstraints() {
    titleLabel.snp.makeConstraints {
        $0.leading.equalToSuperview().offset(20)    // Applique une marge de 20 sur le côté gauche
        $0.trailing.equalToSuperview().offset(-20)   // Applique une marge de 20 sur le côté droit
    }
}
```


Le problème avec ceci, c'est que ce n'est pas facilement maintenable. En effet, si un jour je veux réduire ces marges, je devrais chercher partout où j'ai spécifiée de marges de `20`et les modifier une à une.

C'est pourquoi je vous propose la solution suivante: nous allons créer une extension de notre view controller, dans lequel nous allons créer une énumération nommée `Layout`, et c'est dans celle-ci que nous écrirons nos constantes, ainsi, elles seront toutes situées au même endroit et seront beaucoup plus facile à modifier.


```swift
extension MyViewController {
    enum Layout {
        enum TitleLabel {
            static let horizontalOffset: CGFloat = 20
        }
    }
}
```


Ce qui nous permet de transformer le code précédent en ceci:


```swift
private func setupConstraints() {
    titleLabel.snp.makeConstraints {
        $0.leading.equalToSuperview().offset(Layout.TitleLabel.horizontalOffset)
        $0.trailing.equalToSuperview().offset(-Layout.TitleLabel.horizontalOffset)
    }
}
```

Et voilà, notre code est devenu beaucoup plus facile à maintenir, et beaucoup plus facile à lire !

Bien entendu, je vous ai montré cette astuce avec des constantes en rapport avec de l'UI, mais elle est aussi applicable dans le cas d'autres constantes, comme par exemple, un nombre de secondes à attendre pour un timer.


# Améliorer la lisibilité des constantes globales


Premièrement, si vous n'utilisez pas de constantes globales, je vous encourage à le faire, deuxièmement, si vous en utilisez, il est fort probables qu'elles ressemblent à ceci:


```swift
struct Constants {
    static let myBaseUrl = "https://sonnyfournier.github.io/"
    static let myBlogEndpoint = "blog/"

    static let twitterApiBaseUrl = "https://api.twitter.com/1.1/"
    static let twitterTimelineEndpoint = "timeline/"
}
```


Ce que je vous propose aujourd'hui, c'est de tirer avantage des `nested structures`, autrement dit, des structures dans d'autres structures, afin d'améliorer l'utilisation et la lisibilité de ces constantes.


```swift
struct Constants {
    struct MySiteApi {
        static let baseUrl = "https://sonnyfournier.github.io/"
        static let blogEndpoint = "blog/"
    }

    struct TwitterApi {
        static let baseUrl = "https://api.twitter.com/1.1/"
        static let timelineEndpoint = "timeline/"
    }
}
```

De cette manière, toutes vos constantes seront proprement isolées les unes des autres et seront d'autant plus faciles à utiliser:

```swift
let url = Constants.TwitterApi.baseUrl
```

En lisant ce code on sait imméditement à quoi on accède et on évite les noms de variables à rallonge.

# Defer

Bien qu'introduit avec Swift 2.0, l'instruction `defer` semble méconnue par beaucoup de développeurs iOS.

Cette instruction permet un moyen sûr et simple d'executer du code juste avant de quitter le scope d'une fonction.

```swift
func myFunc() {
    defer {
        print("Defer here")
    }

    print("End of function")
}

// Affichera:
// "End of function"
// "Defer here"
```

`Defer` peut se montrer très utile dans les cas où un nettoyage est nécéssaire avant de quitter une fonction par exemple.


# Conserver les initialisateurs par défaut


Swift est un langage intelligent et automatise beaucoup de choses pour nous. Par exemple, si je définis une structure `Vehicule` de la sorte:

```swift
struct Vehicule {
    let wheelsCount: Int
    let seatsCount: Int
}
```

Swift va alors créer un initialisateur automatiquement pour cette structure (`init(wheelsCount:seatsCount:)`) que nous pourrons utiliser de la manière suivante:


```swift
let car = Vehicule(wheelsCount: 4, seatsCount: 5)
```

Malheureusement, cet initialisateur par défaut ne sera plus disponible si nous définissons un initialisateur custom:


```swift
struct Vehicule {
    let wheelsCount: Int
    let seatsCount: Int

    init(dictionary: [String: Int]) {
        self.wheelsCount = dictionary["wheelsCount"] ?? 4
        self.seatsCount = dictionary["seatsCount"] ?? 5
    }
}
```

L'initialisateur `init(wheelsCount:seatsCount:)` ne sera plus disponible et nous devrons utiliser celui que nous venons de définir. Or parfois, il est utile de conserver celui par défaut. Heureusement pour nous, il existe une solution très simple pour celà: il suffit de créer une extension de notre structure dans laquelle nous allons définir notre initialisateur custom:


```swift
struct Vehicule {
    let wheelsCount: Int
    let seatsCount: Int
}

extension Vehicule {
    init(dictionary: [String: Int]) {
        self.wheelsCount = dictionary["wheelsCount"] ?? 4
        self.seatsCount = dictionary["seatsCount"] ?? 5
    }
}
```


Grâce à cette manipulation, nous pourrons désormais utilser les deux initialisateurs, celui par défaut, et le notre !


# Conclusion


Nous avons fait les tour aujourd'hui des astuces que j'avais à vous proposer, j'espère sincèrement que celles-ci vous auront étés utiles si vous ne les connaisiez pas.

Comme à mon habitude je vous invite à me partager vos astuces si vous en avez, je me ferais une joie de les partager dans un futur article !