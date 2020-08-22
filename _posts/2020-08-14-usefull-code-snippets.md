---
layout: post
title: Quelques code snippets Xcode utiles
subtitle: Arrêtons d'écrire les mêmes choses
tags: [ios, xcode]
comments: true
---

Si vous avez suivi mes précédents articles, vous savez que je développe mes interfaces utilisateurs entièrement grâce à du code et que je n'utilise pas les storyboards d'Xcode (voir [Démarrer un projet Xcode sans storyboard](https://sonnyfournier.github.io/blog/2020-06-23-how-to-no-storyboards/)). Vous savez aussi que j'évite au maximum de me répéter et d'écrire et de faire les mêmes choses encore et encore (voir [Éviter la répétion lors d'un nouveau projet](https://sonnyfournier.github.io/blog/2020-06-28-easy-start/) et [Quelques extensions Swift utiles](https://sonnyfournier.github.io/blog/2020-06-26-usefull-swift-extensions/)).

Aujourd'hui je vais vous montrer quelques code snippets afin de continuer à réduire la répétition dans vos projets et de toujours plus vous simplifier la vie.


# Qu'est ce qu'un code snippet ?


Un `code snippet`, se traduisant littéralement par `extrait de code`, est comme son nom l'indique un extrait de code réutilisable.
Pour vulgariser, l'intérêt d'un `snippet` est d'écrire une seule fois un bout de code et de le relier à un raccourci afin de pouvoir l'inclure partout

Par exemple, si vous possédez un iPhone et que vous écrivez quelque part `jrv`, l'iPhone va vous proposez de corriger ça en `j'arrive !`. C'est un peu le fonctionnement d'un `code snippet`.


# Comment créer un snippet ?


Pour créer un snippet, rien de plus simple. Depuis Xcode, séléctionnez une portion de code que vous voulez transformer en snippet, faites un clic droit dessus et cliquer sur `Create Code Snippet`


![1](https://raw.githubusercontent.com/sonnyfournier/blog/master/assets/img/usefull-code-snippets/1.png){: .mx-auto.d-block :}


Une nouvelle fenêtre va alors apparaître, dans celle-ci vous verrez le code que vous avez sélectionner, vous pourrez alors donner un nom à votre snippet, ainsi qu'une `completion`, c'est à dire, le mot que vous devrez écrire pour invoquer votre bout de code.


![2](https://raw.githubusercontent.com/sonnyfournier/blog/master/assets/img/usefull-code-snippets/2.png){: .mx-auto.d-block :}


Je vais créer un snippet basique afin de mieux vous expliquer le fonctionnement. Imaginons qu'il m'arrive souvent de déclarer des variables de type `Int` contenant la valeur `42` (bien entendu, ceci n'est qu'un bête exemple), je vais commencer par écrire ceci dans n'importe quel fichier XCode, le sélectionner et appuyer sur `Create Code Snippet`:


```swift
var myInt: Int = 42
```


Je vais maintenant donner un nom à ce snippet ainsi qu'une completion:


![3](https://raw.githubusercontent.com/sonnyfournier/blog/master/assets/img/usefull-code-snippets/3.png){: .mx-auto.d-block :}


Ainsi, dès que je taperai `createInt` quelque part dans mon code, XCode me proposera le snippet que je viens d'écrire, il suffira d'appuyer sur la toucher `Entrer` pour l'ajouter dans mon code:


![4](https://raw.githubusercontent.com/sonnyfournier/blog/master/assets/img/usefull-code-snippets/4.png){: .mx-auto.d-block :}


![5](https://raw.githubusercontent.com/sonnyfournier/blog/master/assets/img/usefull-code-snippets/5.png){: .mx-auto.d-block :}


Comme vous pouvez le voir, le nom de la variable (ici `name`) est sélectionnée. C'est grâce à une fonctionnalité des snippets d'Xcode, vous pouvez indiqué pendant son écriture, quels seront les éléments variables dans votre bout de code afin que ceux-ci soient séléctionnés par défaut.

Pour ce faire, lors de la création d'un snippet il suffit d'ajouter `<#` et `#>` de part et d'autre de votre élément variable, j'ai donc écrit pour ce snippet:

```swift
var <#name#>: Int = 42
```

Vous devriez maintenant mieux comprendre l'utilité des snippets et la manière de les créer.


# Les snippets utiles


Comme précédemment annoncé au début de l'article, je créer toutes mes interfaces utilisateurs grâce au code, ce qui veut dire qu'a chaque nouvel écran je dois écrire un `view controller` de base qui ressemble à tout les précédents.

Je vais donc créer un snippet que je vais nommé `createVC` (pour `create view controller`) qui créera tout seul mon view controller de base:

```swift
import UIKit
import SnapKit

// Le `Name` sera sélectionné afin de me permettre de nommé facilement mon nouveau ViewController
class <#Name#>ViewController: UIViewController {

    // MARK: - UI Elements
    // C'est ici que j'ajouterai tous mes éléments UI tels que des boutons par exemple

    // MARK: - Life cycle
    override func viewDidLoad() {
        super.viewDidLoad()

        setupUI()
        setupConstraints()
    }

    // MARK: - UI setup
    // C'est dans cette fonction que j'initialise les éléments UI
    private func setupUI() {
        title = localizedString(for: "<#Name#>")
    }

    // MARK: - Constraints setup
    // C'est ici que seront définit les contraintes
    private func setupConstraints() {
        //
    }
}
```

Ainsi, quand je voudrai créer un nouvel écran, il me suffira d'écrire `createVC` et tout le code ci-dessus sera ajouter dans mon fichier sans aucun effort nécéssaire de ma part, je n'aurais plus qu'à nommer le view controller et écrire le code unique à cet écran !


--- 


Je vais maintenant vous proposer un snippet à peu près similaire mais permettant cette fois-ci de créer non pas un `view controller`, mais une `view`:

Je vais donc créer un snippet contenant le code suivant, qui sera invoqué quand je taperai `createView`:


```swift
import UIKit
import SnapKit

class <#Name#>View: UIView {

    // MARK: - UI elements
    //

    // MARK: - Properties
    //

    // MARK: - Initialization
    override init(frame: CGRect) {
        super.init(frame: .zero)

        setupUI()
        setupConstraints()
    }

    required init?(coder: NSCoder) {
        fatalError("init(coder:) has not been implemented")
    }

    // MARK: - UI setup
    private func setupUI() {
        //
    }

    // MARK: - Constraints setup
    private func setupConstraints() {
        //
    }
}
```


Et voilà, à chaque fois que j'aurai besoin de créer un vue custom, il me suffira d'écrire `createView` pour invoquer le code précédent, et ainsi gagner du temps !


---


Nous allons maintenant passer au troisième et dernier snippet. Comme je me passe des storyboards durant mon développement, je dois écrire mes contraintes à la main (d'où la fonction `setupConstraints` dans les snippets précédents).

Si vous avez suivi les précédents articles, vous devez savoir que j'utilise la librairie `SnapKit` pour écrire mes contraintes car celle-ci simplifie beaucoup l'écriture par rapport à la solution native proposée par Apple (voir [Des librairies pour des meilleures contraintes](https://sonnyfournier.github.io/blog/2020-06-24-libs-for-constraints/)).

Pour rappel, pour écrire des contraintes grâce à `SnapKit` vous devez utiliser une syntaxe propre à la librairie qui ressemble à ceci:


```swift
let view = UIView()

view.snp.makeConstraints {
    $0.size.equalTo(0)
}
```


Cela signifie qu'à chaque fois que je souhaite écrire de nouvelles constraintes pour une vue, je dois répéter le code suivant:


```swift
.snp.makeContraints {
    $0.
}
```


Ce n'est certe pas beaucoup, mais comme chaque vue à besoin de contraintes, nous nous retrouvons à devoir écrire ce bout de code un nombre incalculable de fois par projet.

J'ai donc créer un snippet qui ajoute le code précédent (précédé de `<#name#>`) à chaque fois que je tape le mot-clé `snp`.


# Conclusion


La création et l'utilisation de snippets est un outil formidable et pourtant beaucoup trop méconnu dans le milieu du développement. C'est pourquoi, en plus de vous proposer ceux que j'utilisent le plus, je vous ai montré comment créer les vôtres.

De cette manière j'éspère que vous aurez l'occasion de créer des snippets qui vous correspondent et qui pourront grandement vous faciliter la vie et vous faire gagner un temps considérable.

Je vous invite fortement à me faire part des snippets que vous créerez ou que vous utilisez déjà afin d'en faire profiter un plus grand nombre !