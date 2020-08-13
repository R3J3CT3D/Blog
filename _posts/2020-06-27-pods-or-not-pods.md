---
layout: post
title: Faut-il push le dossier Pods ?
subtitle: Pods or not to pods
tags: [ios, xcode]
comments: true
---

Dans le développement d'applications iOS, il est courant d'utiliser des librairies (comme nous avons pu le voir dans de précédents articles avec notemment les très connus [Snapkit](https://github.com/SnapKit/SnapKit) et [SwiftLint](https://github.com/realm/SwiftLint)). Dans le monde de la pomme, les librairies s'appelent en réalité des `Pods`.

Pour ceux qui auraient précédemment bercé dans le développement web et/ou mobile hybride, cela s'apparante au fameux `node_modules` (en moins lourd 😅).

Une question subsiste concernant ces fameuses librairies, et plus particulièrement, concernant le dossier dans lequel elles sont installés, le dossiers `Pods`.

La question est la suivante:

**Faut-il push le dossier Pods ?**

Question à laquelle je vais répondre:

> Oui.. ou non.. enfin.. c'est pas si simple..


![1](https://raw.githubusercontent.com/sonnyfournier/blog/master/assets/img/pods-or-not-pods/1.jpg){: .mx-auto.d-block :}


En réalité, il n'existe pas qu'une seule réponse à cette question, et la réponse est différente pour chaque développeur iOS. C'est pourquoi nous allons voir ensemble les avantages de pousser le dossier Pods, et les avantages de ne pas le faire.


# Avantages de push le dossier Pods

1. Après avoir cloné le repo, le projet peut se lancer instatanément, sans avoir besoin de lancer la commande `pod install` et d'attendre que le téléchargement de tous les Pod se fasse. Pratique lorsqu'un nouveau membre rejoint le développement d'un projet ou quand vous changez de machine.

2. Vous aurez toujours le Pod disponible, même si le repo officiel de la librairie venait à disparaitre, vous pourrez continuer de l'utiliser car vous aurez le code du Pod directement dans votre repo.

> Pour l'anectode, j'ai une fois travailler avec une librairie, et les créateurs de cette librairie ont décidés pour je ne sais quelle raison de mettre le repo de celle-ci en privé. Je ne pouvais donc plus travailler car je ne pouvais plus accéder à cette librairie, ce qui a retardé pour travail de 2 jours en attendant qu'ils corrigent le tir.

3. Certaines CI proposent un temps de build pour les utilisateurs gratuit (Bitrise notemment). C'est à dire que si le processus de build de votre application dure plus de XX minutes, la CI l'arretera. Si le dossier Pods est déjà présent sur votre repo, la CI n'aura pas à tous les télécharger et cela vous fera économiser un certain temps.


# Avantages de ne pas push de dossier Pods

1. Mine de rien, le code qui constitue les librairies pèse un certain poid. Ne pas les push rendra votre repo moins lourd. De plus, si dans chaque projet que vous réalisez, vous ajoutez les mêmes librairies, vous consommerez plusieurs fois le même stockage pour la même chose.

2. Si certains de vos collaborateurs ont des versions différentes des librairies, cela ne créera pas de conflits lors des merges de branches.

3. Tant que le repo de la librairie est en ligne et public, il vous suffira d'un simple `pod install` pour récupérer cette librairie.


# Alternative

En alternative, vous pouvez récupérer le code des librairies que vous utilisez régulièrement et les push sur un seul et unique repo. Ainsi, si un jour le repo d'une des librairie est passé en privé, ou même supprimé, vous aurez toujours accès à votre propre instance de cette librairie en attendant de trouver une alternative à celle-ci.

De cette manière vous utiliserez l'espèce de stockage nécéssaire au Pods qu'une seule et unique fois, mais vous l'aurez toujours sous la main pour autant. Il serait même possible que créer son propre "Cocoapods" avec des sous-modules de git.

Si Cocoapods est entre guillements c'est parce que ce service ne se contente pas de juste cloner des repos. Il y a derrière une gestion des numéro de version, de mise à jour de librairies, d'intégration avec Xcode simplifiée. C'est pourquoi cette solution est marqué en tant qu'alternative et que je ne la conseille pas vraiment.


# Conclusion

Je pense qu'en lisant l'article vous avez senti que j'avais une préférence pour une des deux méthodes.
En effet, comme énoncé précédemment, j'ai une fois été confronté à une erreur de la part des créateurs d'un librairie et cette erreur m'a couté deux jours sur mon planning. Depuis ce jour j'ai décidé de push le dossier Pods à chaque fois, celà rends certes mes repos un peu plus lourds, mais c'est un inconvéniants que je suis prêt à accepter. De plus, je travaille principalement sur Github, qui propose des repos d'une taille illimité, je ne suis donc limité que part ma connexion lors du clonage de ce repo.

Je pense que vous avez maintenant compris pourquoi je disais précédemment qu'il n'existait pas de réponse simple à la question: **Faut-il push le dossier Pods ?**

J'espère vous avoir donné assez de raisons pour que vous pussiez y répondre par vous même et adopté la solution qui vous conviendra le mieux.