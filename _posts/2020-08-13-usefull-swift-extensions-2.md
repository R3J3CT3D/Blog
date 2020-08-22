---
layout: post
title: D'autres extensions Swift utiles
subtitle: Parce qu'on a jamais finit de se simplifier la vie
tags: [ios, xcode]
comments: true
---

Dans un [précédent article](https://sonnyfournier.github.io/blog/2020-06-26-usefull-swift-extensions/), nous avons il y a quelques temps vu quelques extensions Swift utiles et pratiques qui avaient pour but de nous simplifier la vie et nous faire gagner du temps durant le développement d'un projet.

Aujourd'hui nous allons voir d'autres extensions toutes aussi pratiques et utiles que vous pourrez intégrer dans vos projets.


# String


Commençons une nouvelle fois par explorer quelques extensions de la classe `String`.

Avant tout, si vous ne le saviez pas, une grande source potentielle de failles et de bugs dans les divers programmes et applications de nos jours sont dûes aux utilisateurs. En effet, plus l'utilisateur a d'occasions de rentrer lui-même des informations dans votre programme, plus il y a de chance que votre programme ne sache pas comment les interpréter.

Par exemple, si un utilisateur rentre son adresse mail, mais par mégarde ajoute un espace à la fin. Suivant votre manière de gérer les choses, il se peut que l'utilisateur ne reçoive jamais les mails que vous lui envoyez car pour un programme `"mail@mail.com"` est différent de `"mail@mail.com  "`.

De même, si vous demandez à l'utilisateur de rentrer son nom entier, celui-ci pourrait par mégarde ajouter des espaces utiles de la sorte: `Jean      Dupont`.

Nous allons donc voir notre première extension, celle-ci permet de supprimer les espaces inutiles:

```swift
extension String {
    func condenseWhitespace() -> String {
        return self.components(separatedBy: CharacterSet.whitespacesAndNewlines)
            .filter { !$0.isEmpty }
            .joined(separator: " ")
    }
}
```


Elle s'utilise de la manière suivante:


```swift
let email = "thisis@mymail.com  "
print(email.condenseWhitespace())
// Affiche "thisis@mymail.com"

let fullname = "Jean      Dupont"
print(fullname.condenseWhitespace())
// Affiche "Jean Dupont"
```


Et voilà, finit les espaces inutiles !

---

Nous allons voir une deuxième extension de la classe `String`, beaucoup plus simple mais tout aussi efficace et utile. 

Celle-ci permet tout simplement de vérifier si une chaîne de caractère contient une autre chaîne de caractère.

```swift
extension String {
    func isContains(string: String) -> Bool{
        return self.range(of: string) != nil
    }
}
```

Et nous l'utiliserons comme ceci:

```swift
let string1 = "This is my big string"
print(string1.isContains("big"))
// Affiche "true"

print(string1.isContains("world"))
// Affiche "false"
```

Vous pourrez maintenant vérifier de manière simple si une chaîne de caractère est incluse dans une autre.


--- 

Nous allons à présent voir la dernière extension concernant la classe `String`, cellc-ci permet tout simplement de compter le nombre de mot contenus dans une chaîne de caractère, cela peut se montrer utile si vous voulez compter le nombre de mots présents dans un article par exemple.

```swift
extension String {
    func wordCount() -> Int {
        let chararacterSet = CharacterSet.whitespacesAndNewlines.union(.punctuationCharacters)
        let comps = components(separatedBy: chararacterSet)
        let words = comps.filter { !$0.isEmpty }
        return words.count
    }
}
```

Elle s'utilise de la manière suivante:

```swift
let string = "This is a simple string"
print(string.wordCount())
// Affiche "5"
```

Vous pourrez bien entendu toujours compter le nombre de caractères grâce à `.count`


# UIView


Nous allons à présent voir une extension très pratique concernant la classe `UIView`. Celle-ci permet d'ajouter facile des contours autour de vos vues. De plus, comme tous les éléments d'UIKit ou presque héritent d'`UIView`, vous pourrez aussi appliquer des contours aux `UIButton`, `UILabel`, `UITextField`, etc..

```swift
extension UIView {
    enum BorderSide {
        case top, bottom, left, right, all
    }

    func setBorder(to sides: [BorderSide] = [ .all ], ofColor color: UIColor = .label, andThickness thickness: CGFloat = 1) {

        for side in sides {

            let border = CALayer()
            border.backgroundColor = color.cgColor

            switch side {
            case .top:
                border.frame = CGRect(x: 0, y: 0, width: frame.width, height: thickness)
                layer.addSublayer(border)
            case .bottom:
                border.frame = CGRect(x: 0, y: frame.size.height - thickness, width: frame.size.width, height: thickness)
                layer.addSublayer(border)
            case .left:
                border.frame = CGRect(x: 0, y: 0, width: thickness, height: frame.size.height)
                layer.addSublayer(border)
            case .right:
                border.frame = CGRect(x: frame.size.width - thickness, y: 0, width: thickness, height: frame.size.height)
                layer.addSublayer(border)
            case .all:
                layer.borderColor = color.cgColor
                layer.borderWidth = thickness
            }
        }
    }
}
```

Cette extension étant un peu plus complexe que les autres je vais la détaillée ici.

Tout d'abord vous pouvez voir que j'ai crée ici une énumération nommée `BorderSide`, celle-ci nous permettra de préciser sur quel(s) côté(s) de notre vue nous voulons appliquer un contour.

La fonction `setBorder` prend 3 paramètres:
- `sides`: le(s) côté(s) sur lesquels nous voulons une bordure
- `color`: la couleur de la bordure (j'ai ici mis `.label` en couleur par défaut, cela permet d'appliquer par défaut une couleur noire lorsque nous sommes en light mode et une couleur blanche lorsque nous sommes en dark mode)
- `thickness`: l'épaisseur de la bordure (j'ai ici mis `1` en épaisseur par défaut)

Nous pouvons à présent appliquer des bordures à nos vues facilement:

```swift
let view = UIView()

view.setBorder(to: [ .all ])
// Applique une bordure sur tous les côtés de notre vue, avec la couleur des labels et une épaisseur de 1

let button = UIButton()

button.setBorder(to: [ .left, .right ], ofColor: .red, andThickness: 5)
// Applique une bordure sur les côtés gauche et droit de notre bouton, de couleur rouge et avec une épaisseur de 5
```

Nous pouvons à présent facilement ajouter des bordures à toutes nos vues !


# Conclusion


Voilà, nous avons fait le tour des extensions que j'avais à vous proposer pour aujourd'hui, comme la dernière fois, n'hésitez pas à me proposer les vôtres pour quelles apparaissent peut-être dans un futur article !