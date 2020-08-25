---
layout: post
title: Le nouveau Github
subtitle: La plateforme qui ne cesse de s'améliorer
tags: [dev, tools]
comments: true
---

Cela fait maintenant deux ans que `Microsoft` à racheté la plateforme `Github`. Cet évenement avait fait énormément de bruit à l'époque chez les développeurs car Microsoft avait la mauvaise réputation de "détruire" tout ce qu'il rachetait (`LinkedIn`, `Skype`, etc..).

À la grande surprise de tout le monde, c'est ici l'inverse qui s'est produit et le rachat de Github par Microsoft a été extrêmement bénéfique pour la plateforme et surtout pour ses utilisateurs. Nous allons voir aujourd'hui quelles sont les améliorations qui ont été apportées depuis cette fameuse acquisition.


# Un nouveau design


Nous allons commencer en douceur en parlant de la nouvelle apparence de Github. En effet, la plateforme a reçue un immense redesign, et bien que cela soit purement subjectif, celui-ci a permis de rendre la plateforme plus claire et notamment en ce qui concerne la visualisation des repos. Voici un exemple sur le repo officiel de [Linux](https://github.com/torvalds/linux). Ci-dessous, l'ancien design:


![1](https://raw.githubusercontent.com/sonnyfournier/blog/master/assets/img/new-github/1.png){: .mx-auto.d-block :}


Et voici le nouveau design:


![2](https://raw.githubusercontent.com/sonnyfournier/blog/master/assets/img/new-github/2.png){: .mx-auto.d-block :}


Comme vous pouvez le voir, l'interface est plus aérée et permet de visualiser des informations telles que les langages utilisés et les principaux contributeurs d'un simple coup d'oeil. Et vous, vous préferez l'ancien ou le nouveau design ?


# La section "Explore"


Évoquée dans un précédent article ([4 outils utiles pour les développeurs iOS](https://sonnyfournier.github.io/blog/2020-08-17-usefull-ios-dev-tools/)), je vous avais annoncé que nous reparlerions plus en détails de la section [Explore](https://github.com/explore) de Github dans le futur. Et bien ce moment est arrivé.

Dans le passé, la section `Explore` se composait de deux parties majeures:
- les `Trending` - les projets en `trending` du moment.
- les `Showcases` - un regroupement de projets autour d'un même thème.


![3](https://raw.githubusercontent.com/sonnyfournier/blog/master/assets/img/new-github/3.png){: .mx-auto.d-block :}


Maintenant, bien que la catégorie `Trending` soit restée, de nouvelles catégories ont fait leurs apparitions. Nous retrouvons alors les sections suivantes:
- `Explore` créée spécialement pour vous en fonction de vos intérêts et de vos projets.
- `Topics` qui reprend de manière plus approfondi le principe des `showcases`.
- `Trending` qui est restée la même.
- `Collections` regroupe des collections de ressources utiles pour les différents développeurs et contributeurs.
- `Events` où nous pouvons retrouver tous les évenements créer et/ou soutenu par Github.
- `Github Sponsors` qui regroupe une liste de projets ayant besoin de sponsors pour les financer.


![4](https://raw.githubusercontent.com/sonnyfournier/blog/master/assets/img/new-github/4.png){: .mx-auto.d-block :}


Comme vous pouvez le voir, la section `Explore` s'est grandement étoffée et offre maintenant des ressources utiles et une manière de découvrir de nouveaux projets et de nouvelles technologies de manière simple et efficace.


# Un plan gratuit


Voilà une fonctionnalité qui a été très chaleureusement accueillie par les développeurs, une réduction des tarifs de la plateforme et un plan gratuit. À l'époque, un simple compte personnel permettant l'accès à des repos public et privés illimités coutait la modique somme de `7$` par mois:


![5](https://raw.githubusercontent.com/sonnyfournier/blog/master/assets/img/new-github/5.png){: .mx-auto.d-block :}


Maintenant, un compte personnel pour développeur est totalement gratuit et présente les mêmes avantages qu'auparavant. De plus, les prix pour les équipes à presque diminuer de moitié: 


![6](https://raw.githubusercontent.com/sonnyfournier/blog/master/assets/img/new-github/6.png){: .mx-auto.d-block :}


Vous pouvez donc facilement comprendre pourquoi cette nouveauté à reçu un très bon accueil.


# Les Github Actions


Les `Github Actions` sont des outils mis en place par Github permettant toutes sortes de choses de manière automatique. C'est une fonctionnalité très poussée qui mérite son propre article. C'est pourquoi aujourd'hui nous allons uniquement survoler ces outils et nous les verrons plus en détails dans le futur.

Je vais vous présenter deux `Actions` très simple afin que vous compreniez le principe de celles-ci. Nous allons commencer par `Dependabot`.

`Dependabot` est un outil qui peut être directement intégré à vos projets sur Github. Il s'agit d'un robot qui va automatiquement analyser les dépendances de vos projets, et si des nouvelles versions de ces dépendances sont disponibles, celui-ci ouvrira automatiquement un `Pull request` avec la mise à jour effectuée. De cette manière vous vous assurez d'avoir toujours les dernières versions disponibles sans même devoir vous en préoccuper.

De plus, `Dependabot` vérifiera aussi si certaines dépendances possèdent des failles de sécurités et vous alertera afin que vous puissiez remédier au problème.


![7](https://raw.githubusercontent.com/sonnyfournier/blog/master/assets/img/new-github/7.png){: .mx-auto.d-block :}


Vos projets posséderont alors des dépendances toujours à jour et avec un risque de failles de sécurité réduit.


---


Nous allons maintenant voir une autre `Action` nommée `Imgbot`. Ce robot a pour but d'analyser les projets dans lesquels vous avez des images, et de les optimiser automatiquement. Donc à chaque fois que vous ajouterez des images dans votre projet, `Imgbot` va les analyser et les optimiser afin de réduire leurs tailles sans aucune perte de qualité. Vous vous retrouverez alors avec des images plus légères, ce qui vous permettra de conserver de l'espace tout en augmentant les vitesses de chargement de celles-ci.


![8](https://raw.githubusercontent.com/sonnyfournier/blog/master/assets/img/new-github/8.png){: .mx-auto.d-block :}


Côté fonctionnement, `Imgbot` fonctionne comme `Dependabot`. Celui-ci ouvrira une `Pull request` avec les images optimisées et vous n'aurez plus qu'à `mergé` celle-ci pour en profiter.


# Conclusion


Bien entendu je n'ai parlé ici que des principales nouveautés que j'ai pu constater mais il en existe bien d'autres.

De mon point de vue, le rachat de Github par Microsoft a été très bénéfique. La plateforme ne cesse de s'améliorer de jours en jours pour le plus grand bonheur des utilisateurs.

Comme vous avez pu l'apercevoir, les `Github Actions` sont des outils très puissants et nous en reparlerons à l'avenir, car en plus de permettre ce que je vous ai montré, celles-ci permettent aussi de lancer des tests ou des builds directement depuis Github.

Maintenant que nous avons fait le tour, j'aimerais avoir votre avis. Selon vous, Github s'est-il amélioré depuis que Microsoft l'a racheté ?


