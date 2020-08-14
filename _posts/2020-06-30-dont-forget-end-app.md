---
layout: post
title: Les choses à ne pas oublier à la fin d'un projet
subtitle: N'oubliez pas ce qu'on a tendance à oublier
tags: [ios, xcode]
comments: true
---

Ça y est, c'est enfin le grand moment ! Vous avez terminer votre application (grâce au précédent article et à mon super template peut-être ?) et vous êtes prêt à partir à la conquête de l'AppStore ? Et bien permettez moi de frener un peu vos ardeur et vous rappelez qu'on oublie parfois certaines choses.

Aujourd'hui nous allons voir les étapes trop souvent oubliées à la fin d'un projet, les petits détails qui empêchent nos applications d'atteindre la perfection, vous êtes prêt ? C'est parti !


# Tester sur plusieurs appareil

Et oui, un iPhone n'est pas un iPad, et vice-versa. Si vous avez dans l'ambition de sortir votre application pour les deux plateformes, pensez à bien tester sur les deux plateformes, ça paraît bête et pourtant.. (Oui c'est vous que je vise Instagram).

Bien entendu, si vous testez sur plusieurs appareils, pensez aussi à..


# Tester sur plusieurs tailles d'écrans

Pendant tout le temps du développement vous avez tester sur votre iPhone XR, c'est très bien, mais il ne faut pas oublier de tester sur les version `Max`qui sont plus grandes, sur les iPhone `6`, `7`, `8`, `SE`, etc.. Parce que les tailles varient, et donc le contenu aussi.

Il va sans dire que ce point est aussi valable pour les iPads, il y a une énorme différence en un iPad `mini` et un iPad `Pro 13 pouces`.


# Pensez aux traductions

Que vous ayez comme projet de rendre votre applications disponibles dans d'autres pays ou non, il est vivement conseillé d'avoir toujours au moins l'anglais et le français comme langues dans votre applications.

En effet, un bon nombre de personne en France ont mis leurs téléphones en anglais, il serait dommage qu'ils tombent face à des clefs de traduction non reseignées.


# Le dark mode

Un point essentiel des applications depuis iOS 13, le dark mode a pourtant tendance à être souvent délaissé. Pensez à faire un tour complet de votre application, en light mode comme en dark mode. Si possible, passez de l'un à l'autre sur chaque écran de votre application, il arrive parfois que le changement de l'un à l'autre ne se passe pas très bien sur certains éléments, comme les `layers` par exemple.


# Les grandes polices

Voici un autre élément trop souvent négligé également. Il est possible de modifier la taille de tous les textes d'iOS depuis `Réglages > Luminosité et affichage > Taille du texte`. Pensez à changer ce paramêtres et de refaire un tour de passe dans votre application. Il est possible qu'en augmentant la taille des polices, certains textes se comportent mal ou encore qu'ils sortent de l'écran.


# L'accessibilité

Tout comme la taille des textes, il existe des réglages d'accessibilité permettant à certaines personnes, notamment les mal-voyants, d'utiliser leurs smartphones de manière plus agréables.

Pensez donc à activer certains de ces réglages afin de voir comment votre application se comporte. Voici une liste non exhaustive et non complète des réglages qu'il peut être interéssant à tester (dans `Réglages > Accessibilité`):
- VoiceOver
- Zoom
- Tous les réglages situés dans `Affichage et taille du texte`
- Réduire les animations

Vous n'êtes bien évidemment pas obligé de vous conformer à toutes les options d'accessibilités, très peu de développeurs (indépendant j'entends) mettent en place le VoiceOver par exemple. Même si dans un monde parfait, toutes devraient être comblées.


# Tester sans connexion

Si votre application nécéssite internet pour fonctionner, pensez à tester comment celle-ci réagit lorsqu'il n'y a pas de connexion. Pensez aussi à tester ceci partout où une action nécéssitant internet est présente (connexion, inscription, actualisation, etc..).


# Demander à un testeur tier

Lorsque vous tester votre application vous n'êtes pas impartial et vous testez sûrement tout le temps de la même manière. Si vous le pouvez, demander à une tierce personne de tester votre application pendant 5 minutes. Cette personne ne connaissant pas votre application la testera d'une manière différente de vous et vous pourrez peut-être constater des bugs ou des comportements non désirés.


# Conclusion

Comme vous pouvez le constater, une application n'est jamais vraiment terminée. Il y a sans cesse de nouvelles choses à penser, des nouveaux bugs à corriger, des nouveautés à implémenter.

J'espère que cette liste vous aura été utile et vous aura fait pensez à tester et vérifier des éléments que vous auriez pû oublier. D'ailleurs, je ne suis pas à l'abri d'avoir moi-même oublier certaines choses, si vous vous rendez compte d'un oubli, n'hésitez pas à m'en faire part que je mette cette article à jour afin que toutes nos futures application approche la perfection !