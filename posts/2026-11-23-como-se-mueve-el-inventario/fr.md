---
slug: how-your-inventory-keeps-itself-up-to-date
title: "Stock automatique : votre inventaire s'ajuste tout seul avec vos ventes"
description: Vous vendez une figurine, une bobine de filament ou vous partez sur un salon maker, et votre inventaire reste à jour tout seul. On vous explique ce que fait BolloPrint de votre stock dans chaque situation.
date: 2026-11-23
tags: [tutoriels]
cover: 08-stock-del-pedido-en.png
---

Avoir un inventaire à jour, c'est bien, mais ce qui fait vraiment gagner du
temps, c'est qu'il reste à jour tout seul. Vous vendez une figurine que vous
aviez déjà imprimée, vous encaissez une bobine de filament sur un marché, vous
emportez deux caisses pleines sur un salon… et au retour, vous n'avez pas envie
de passer l'après-midi à compter ce qu'il reste.

Dans ce guide, on vous explique ce que fait BolloPrint de votre stock dans
chaque situation.

## D'abord, ce que contient votre inventaire

Dans **Inventaire**, BolloPrint sépare deux choses :

- **Le Stock** : les **pièces déjà imprimées** que vous avez en réserve, prêtes à
  assembler un produit ou à être vendues.
- **Le matériau** : vos bobines de **Filament**, vos flacons de **Résine** et les
  **Fournitures** (boîtes, aimants, inserts…). C'est ce que vous achetez,
  même si vous pouvez aussi le vendre !

## Vous pouvez aussi vendre votre matériau !

En plus de vos produits 3D, vous pouvez ajouter du **filament, de la résine et
des fournitures** à vos commandes et à vos devis, et les vendre depuis le point
de vente. Un client vous achète une bobine ? Elle sort de votre inventaire comme
n'importe quelle autre vente.

## Ce que vous vendez sort du stock

Quand vous enregistrez une commande ou acceptez un devis, BolloPrint vérifie
votre inventaire pour voir ce que vous avez et ce qui manque, et vous montre ce
qui sort :

- Les **matériaux** que vous vendez : bobines, flacons ou fournitures.
- Les **pièces** des produits 3D que vous vendez. Si un produit est composé de
  plusieurs pièces, elles sortent toutes du Stock.

Et c'est vous qui choisissez **Retirer du stock** ou **Ne pas retirer du stock**.

![À la création d'une commande, ce qui sort du stock : une bobine d'ABS orange et un porte-clés, chacun sous forme de soustraction (vous avez, retirés, restants), une pièce à imprimer parce qu'il n'en reste plus, et les options Retirer du stock et Ne pas retirer du stock](/blog/media/2026-11-23-como-se-mueve-el-inventario/08-stock-del-pedido-en.png "80%")

S'il n'y en a pas assez, BolloPrint retire ce qu'il y a (le stock ne passe
jamais en négatif) et vous dit ce qui manque : une pièce **est à imprimer** et un
matériau **est à acheter**. Rien n'est bloqué. Et si une ligne sort entièrement
du Stock, elle est marquée comme **imprimée**, puisqu'il n'y a plus besoin de
l'imprimer.

En plus :

- Un **devis** ne touche pas au stock tant que vous ne l'acceptez pas.
- Si vous **annulez** une commande, seul ce qui en était sorti revient dans le
  stock.
- Le stock **ne change jamais le statut de la commande** : la passer en « Prêt à
  expédier », c'est vous qui le décidez, car il reste peut-être à l'emballer.

## Commandes Etsy et autres marketplaces

Une commande qui arrive toute seule de votre boutique n'a personne à qui poser la
question, elle arrive donc en **stock à décider**. La première fois que vous
l'ouvrez, BolloPrint vous demande quoi faire du stock. Et si l'acheteur l'annule
sur la marketplace, ce qui avait été retiré revient tout seul.

## Au point de vente

Au **Point de vente**, pas de question : encaisser, c'est déjà décider. Ce que
vous vendez sort du stock et, si vous annulez la vente, il revient. Plus de
détails dans [Point de vente](/help/punto-de-venta).

## Ce que vous emportez sur un salon

Si vous allez sur un marché ou un salon maker, en créant un événement dans
**Événements** vous indiquez **ce que vous emportez** : des pièces du Stock et du
matériau de l'inventaire. À l'enregistrement, BolloPrint vous montre ce qui sort
du Stock et ce qu'il faut imprimer, comme pour une commande. Ce que vous emportez
ne compte plus dans votre stock et passe dans le stock de l'événement. Ce que
vous n'avez pas dans le Stock est considéré comme imprimé pour l'occasion.

- Ce que vous **vendez pendant l'événement** avec le point de vente est déduit de
  ce que vous avez emporté, pas une deuxième fois de votre inventaire.
- En **clôturant l'événement**, vous indiquez ce qui revient : ce qui reste
  **revient dans le stock** et ce qui ne revient pas (quelque chose de cassé,
  quelque chose d'offert) compte comme **perte de l'événement**, à son coût.
- La clôture vous indique aussi si **vous avez vendu des produits que vous
  n'aviez pas emportés**, par exemple une commande que vous livrerez plus tard.

![Ce que vous emportez sur un événement clôturé : pour chaque pièce, combien vous en avez emporté, combien vous en avez vendu, combien sont revenues et combien ne sont pas revenues](/blog/media/2026-11-23-como-se-mueve-el-inventario/09-que-te-llevas-en.png)

:::info 💡 Vous l'avez imprimé exprès pour l'événement ?
Choisissez **Ne pas toucher au stock** : ce que vous emportez n'est pas retiré de
l'inventaire, et ce qui reste s'y ajoute à la clôture.
:::

Étape par étape, dans l'aide Événements :
[Ce que vous emportez](/help/eventos#ce-que-vous-emportez) et
[Clôturer l'événement](/help/eventos#clôturer-lévénement).

## Tout est noté dans l'Historique

Chaque modification de l'inventaire est notée dans **Inventaire → Historique** :
quand, quoi, pourquoi (une commande, le point de vente, un événement, une
modification manuelle), combien et qui l'a faite. Depuis le menu **⋯** de chaque
ligne, **Voir l'historique** vous montre uniquement ce qui concerne ce matériau
ou cette pièce. Plus de détails dans l'aide de
l'[Historique](/help/inventario#historique).

Les achats se notent à la main, avec le **+** de la ligne ou avec « Ajouter avec
une photo ». Une dépense dans **Finances** ne modifie pas l'inventaire : ainsi,
la même bobine n'est pas comptée deux fois.

## Commencez avec un inventaire à jour

Tout cela fonctionne mieux si ce qu'il y a dans BolloPrint correspond à ce qu'il
y a sur vos étagères. Si vous n'avez pas encore saisi vos bobines et vos résines,
faites-le en photographiant les étiquettes : on vous l'explique dans
[gérez votre inventaire avec l'appareil photo de votre téléphone](/blog/filament-inventory-from-a-photo).
À partir de là, vos commandes, votre point de vente et vos événements le
tiennent à jour pour vous.

![Bollo, la mascotte de BolloPrint, avec ses lunettes d'atelier, entre des cartons, des bobines de filament, des flacons de résine et des étagères de pièces imprimées](/blog/media/2026-11-23-como-se-mueve-el-inventario/11-bollo.jpg "60%")

## Documentation associée

- [Inventaire](/help/inventario) : filament, résine, fournitures et Stock
- [Matériel en vente](/help/material-a-la-venta) : vendre des bobines et des fournitures
- [Détails d'une commande](/help/detalles-de-un-pedido) : les lignes et le stock
- [Commandes des marketplaces](/help/pedidos-de-marketplaces) : les commandes qui arrivent toutes seules
- [Point de vente](/help/punto-de-venta) : vendre en personne
- [Événements](/help/eventos) : préparer, vendre et clôturer un événement
