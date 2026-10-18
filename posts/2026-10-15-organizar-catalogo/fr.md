---
slug: organize-your-3d-printing-catalog
title: "Des fichiers STL aux produits de votre boutique : comment organiser votre catalogue d'impression 3D"
description: Apprenez à structurer vos fichiers STL, à calculer le coût de chaque pièce et à créer les variantes de vos produits pour votre boutique d'impression 3D, sans vous compliquer la vie.
date: 2026-10-18
tags: [tutoriels]
cover: 01-portada.webp
---

Si vous imprimez en 3D pour vendre, vous connaissez sûrement cette scène : des dizaines de dossiers sur l'ordinateur, avec des fichiers nommés `llavero_V2_FINAL_definitivo.stl`, sans vous rappeler combien de filament consommait cette version ni quel profil de tranchage vous aviez utilisé. Et quand une commande arrive sur Etsy, vous calculez vos coûts à vue de nez en espérant ne pas perdre d'argent.

Dans un atelier ou une ferme d'impression 3D, le désordre technique et le désordre commercial se mélangent si vous ne les séparez pas. C'est pourquoi BolloPrint les traite séparément. Dans ce guide, nous vous expliquons comment s'articulent **Designs, Pièces, Produits et Variantes**, pour que vous passiez d'un tas de fichiers épars à un catalogue bien rangé.

::animation{id="how-it-works"}

## Séparez le technique du commercial

L'une des erreurs les plus courantes dans la gestion d'un atelier consiste à traiter un fichier STL comme s'il était le produit que vous vendez. En pratique, un même modèle 3D peut être imprimé dans différents matériaux, comporter plusieurs parties ou être vendu en lot.

C'est pourquoi BolloPrint organise votre catalogue en trois niveaux.

### Designs : la bibliothèque technique

Le **Design** est le conteneur de vos fichiers sources : les STL, OBJ ou projets 3MF, ainsi que les photos du modèle et vos notes internes.

- **Voyez le Design comme le plan ou l'idée.** Il ne comporte ni temps ni grammes de filament, car un même STL peut être imprimé à différentes échelles ou dans différents matériaux.

![Le design « Keyring BolloPrint », avec son fichier STL, sa photo, ses notes internes et ses deux pièces : de 5 cm et de 10 cm](/blog/media/2026-10-15-organizar-catalogo/02-diseno.png)

### Pièces : l'objet physique

Une **Pièce** est le résultat obtenu lorsque vous prenez un Design et lui donnez une configuration d'impression précise : le matériau et sa consommation (par exemple, du PLA noir), les dimensions et le temps d'impression.

- **Un Design, plusieurs Pièces.** Avec le même STL, vous pouvez imprimer une figurine en deux tailles, 5 cm et 10 cm : ce Design aura deux Pièces, « Petit porte-clés » et « Grand porte-clés ». Il en va de même pour des couleurs ou des matériaux différents.
- **Votre fichier tranché fait les calculs.** Si vous ajoutez à la Pièce le fichier du trancheur (`.gcode`, `.gcode.3mf`, `.bgcode` ou `.goo` pour la résine), BolloPrint lit le poids et le temps d'impression et vous les propose. Lorsque vous les appliquez, il calcule ce que vous coûte la fabrication de cette pièce précise. Vous pouvez aussi saisir ou corriger les données à la main.

:::info 💡 Un 3MF de projet ne convient pas ici
Le trancheur doit avoir tranché le plateau pour connaître le poids et le temps. Un `.3mf` de projet ne les contient pas : il va dans le Design. Pour la Pièce, ajoutez le `.gcode.3mf` exporté par le trancheur.
:::

### Produits et Variantes : ce que votre client voit et achète

Le **Produit** est votre vitrine : ce que vous publiez dans votre boutique ou sur une marketplace comme Etsy. La **Variante** est l'option précise que choisit le client.

- **Une Variante peut contenir une ou plusieurs Pièces**, chacune avec sa quantité.
- **Par exemple :** votre Produit est « Figurine de Bollo », notre chien. Une Variante peut être « Vert », une autre « Orange » et une autre le lot « Vert + Orange », avec les deux Pièces à l'intérieur. Vous pouvez combiner matériaux, tailles, finitions ou lots comme vous le souhaitez.

![La variante Green+Orange, avec ses deux pièces, une orange et une verte, ainsi que son coût, sa marge et son prix](/blog/media/2026-10-15-organizar-catalogo/04-variante-pack.png)

:::info 💡 Un pack peut mélanger plusieurs Designs
Une Variante peut contenir des Pièces de Designs différents : par exemple, un « Pack bureau » avec le support téléphone et le range-câbles.
:::

- **La marge se calcule toute seule.** Comme chaque Variante sait de quelles Pièces elle est faite, BolloPrint compare votre prix de vente au coût réel de production et vous affiche la marge. Si vous changez le prix, la marge se met à jour, et inversement.

![La variante Green, avec une seule pièce : un coût de 7,06 €, une marge de 70 % et un prix de 23,54 €](/blog/media/2026-10-15-organizar-catalogo/03-variante.png)

## Vous manquez de temps ? Utilisez la Création rapide

Si vous débutez ou si vous avez des centaines de modèles à importer, configurer les Designs, les Pièces et les Produits un par un prend du temps.

C'est à cela que sert le bouton **Création rapide** du catalogue. Sur un seul écran, vous importez votre fichier 3D, vous indiquez le matériau, le poids, le temps et le prix, et BolloPrint crée d'un coup le Design, la Pièce, le Produit et sa Variante. Le résultat est le même que si vous procédiez étape par étape : vous pouvez donc ensuite affiner ce que vous voulez.

![Le formulaire de Création rapide : le fichier 3D, les photos, le matériau, le poids, le temps, les couleurs, le coût et le prix](/blog/media/2026-10-15-organizar-catalogo/05-creacion-express.webp "50%")

## Vos étiquettes passent toutes seules au produit

Autre détail qui vous fait gagner du temps : les **étiquettes** d'un Design passent toutes seules à ses Produits.

Si vous étiquetez un Design « Porte-clés » ou « Figurines », lorsque vous ajoutez ses Pièces à une Variante, ces étiquettes s'ajoutent au Produit. Et si vous vendez sur Etsy, au moment de publier l'annonce, elles apparaissent déjà comme *tags*, qui aident les acheteurs à vous trouver. Etsy en accepte jusqu'à 13, de 20 caractères maximum, et vous pouvez les retoucher avant de publier.

## Commencez à organiser votre catalogue

Avoir un catalogue bien organisé n'est pas qu'une question d'ordre : c'est le moyen de savoir combien vous coûte chaque pièce, combien vous gagnez sur chaque commande, et de faire grandir votre atelier sans en perdre le contrôle.

Si vous voulez voir plus en détail comment configurer votre catalogue ou créer des variantes avancées, jetez un œil à la [documentation du catalogue](/help/catalogo). Et si vous vous demandez d'où vient le coût de chaque Pièce, nous l'expliquons dans [ce que coûte vraiment une pièce imprimée](/blog/calculate-your-3d-printing-costs).

Découvrez [comment piloter la production de votre atelier avec BolloPrint](/features), votre logiciel pour fermes d'impression 3D.

Que votre catalogue reste, en grandissant, aussi bien rangé qu'à ses débuts.

![Bollo, la mascotte de BolloPrint, avec ses lunettes d'atelier, à côté de son modèle 3D en maillage](/blog/media/2026-10-15-organizar-catalogo/07-bollo.webp "60%")

## Documentation associée

- [Catalogue](/help/catalogo) : les niveaux du catalogue, dans la référence
- [Designs](/help/disenos) : les fichiers, les photos et les étiquettes
- [Pièces](/help/piezas) : le matériau, le fichier tranché et le coût
- [Produits et Variantes](/help/productos-y-variantes) : le prix, la marge et les pièces de chaque variante
- [Création rapide](/help/creacion-rapida) : tout d'un coup
- [Étiquettes](/help/etiquetas) : comment les créer et les gérer
