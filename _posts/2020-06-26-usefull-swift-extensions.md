---
layout: post
title: Quelques extensions Swift utiles
subtitle: Simplifiez vous la vie au quotidien
tags: [ios, xcode]
comments: true
---

Il existe en Swift ce que l'on appelle des `extensions`. Les extensions permettent d'ajouter des fonctionnalités à des classes, des structures, des protocoles ou des énumérations existantes. Comme le nom l'indique, les extensions permettent _*d'étendre*_ les fonctionnalités, et non de passer outre les fonctionnalités existantes.

Je vais aujourd'hui vous présenter diverses extensions que j'ai pu mettre au point et qui vous simplifirions la vie à coups sûrs.


# String

Nous allons commencer par voir une petite extension très pratiques concernant la classe `String`

Il existe en Swift des méthodes qui permettent de rendre en minuscules ou en majuscules tous les caractères présents dans une chaîne de caractère.

```swift
let cafe = "Café"
print(cafe.uppercased())
// Affiche "CAFÉ"
print(cafe.lowercases())
// Affiche "café"
```

Malheureusement, il n'existe aucune méthode permettant de mettre uniquement la première lettre en majuscule, c'est pourquoi je vous propose dès maintenant notre première extension, `capitalizeFirstLetter`:

```swift
extension String {
    func capitalizeFirstLetter() -> String {
      return prefix(1).capitalized + dropFirst()
    }
}
```

Nous pouvons à présent utiliser cette nouvelle fonctionnalité de la classe String de la manière suivante:

```swift
let cafe = "CAFÉ"
print(cafe.capitalizeFirstLetter())
// Affiche "Café"
```


# UIView

Passons sans plus tarder à une autre extension qui peut s'avérer très utile (surtout si vous avez suivi les précédents articles et que vous développez vos interfaces utilisateurs grâce au code), j'ai nommé `addSubviews` !

En effet, imaginons que nous devions ajouter plusieurs `views` à une autre, nous allons nous retrouver rapidement avec plein de lignes similaires sans grand intérêt:

```swift
let containerView = UIView()

let view1 = UIView()
let view2 = UIView()
let view3 = UIView()

// Nous allons devoir toutes les ajouter une par une..
containerView.addSubview(view1)
containerView.addSubview(view2)
containerView.addSubview(view3)
```

C'est ainsi que je vous propose la méthode `addSubviews`:

```swift
extension UIView {
    func addSubviews(_ subviews: UIView...) {
        subviews.forEach(addSubview)
    }
}
```

Comme son nom l'indique, cette méthode permet d'ajouter plusieurs `subviews` d'un seul coup, nous pouvons à présent écrire:


```swift
let containerView = UIView()

let view1 = UIView()
let view2 = UIView()
let view3 = UIView()

// Nous pouvons ajouter toutes nos views d'un seul coup
containerView.addSubviews(view1, view2, view3)
```


# Cells

Lorsque nous utilisons des cellules dans des éléments tels que des `UICollectionView` ou des `UITableView`, il faut que chaque cellule possède un identifiant qu'il lui est propre, appelé le `reuseIdentifier`, c'est pourquoi je vous propose une petite extension qui permettra que chaque cellule est toujours un identifiant unique sans aucun effort:

```swift
extension UICollectionViewCell {
    static var reuseIdentifier: String {
      return String(describing: self)
    }
}
```

Je vous invite à répliquer le même procédé en créant une extention pour les `UITableViewCell`


# UIButton

Si vous ne le saviez pas, il est conseillé que pour chaque action demandant du temps variable d'execution, l'utilisateur en soit informé. Par exemple, quand vous appuyez sur un bouton "S'inscrire" sur une application, celle-ci affiche généralement une animation de chargement afin d'aventir l'utilisateur que l'application travaille et que celui-ci soit informé qu'il doit attendre.
Celà fait parti des bonnes pratiques de l'UI/UX dont nous parlerons dans un futur article.

En attendant, je vous propose une petite extension permettant justement, d'afficher une petite animation de chargement à l'intérieur d'un bouton lorsque celui-ci à été appuyé et que des actions se passent:

```swift
extension UIButton {
    func loadingIndicator(_ show: Bool) {
        if show {
            isEnabled = false
            titleLabel?.alpha = 0

            let indicator = UIActivityIndicatorView()
            indicator.center = CGPoint(x: bounds.size.width / 2, y: bounds.size.height / 2)
            addSubview(indicator)
            indicator.startAnimating()
        } else {
            isEnabled = true
            titleLabel?.alpha = 1.0

            for subview in subviews where (subview as? UIActivityIndicatorView) != nil {
                (subview as? UIActivityIndicatorView)?.stopAnimating()
                subview.removeFromSuperview()
            }
        }
    }
}
```

Cette méthode aura pour effet de cacher le texte du bouton et d'afficher à la place une animation de chargement, vous pouvez l'utilisez de la menière suivante:

```swift
// Appeler la méthode de cette manière quand on veut afficher l'animation
loginButton.loadingIndicator(true)
// Et l'appeler de cette manière quand on veut arrêter l'animation
loginButton.loadingIndicator(false)
```


# Conclusion

Et bien voilà, je vous ai présenté quelques extensions qui je pense vous serons utile. J'ai sélectionné celles-ci car je les utilise moi-même dans chaque projet, ou presque, que je créer.
N'hésitez pas à créer vos propres extensions, et si selon vous, elles valent le détour, n'hésitez surtout pas à les partager autour de vous, ou même de me les envoyer pour que je les ajoutes à cet article.