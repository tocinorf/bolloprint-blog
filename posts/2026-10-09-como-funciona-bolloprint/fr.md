---
slug: how-bolloprint-works
title: "Design, Pièce, Variante, Produit : la carte de BolloPrint en cinq minutes"
description: Les quatre éléments derrière chaque commande, la question à laquelle répond chacun et pourquoi ils sont quatre et pas une seule fiche. Avec un support de téléphone en exemple, du début à la fin.
date: 2026-10-09
updated: 2026-10-12
tags: [tutoriels]
cover: 01-el-mapa.webp
draft: true
---

Une commande arrive : **deux supports de téléphone, en blanc**. Avant que vous ne fassiez quoi que ce soit, BolloPrint sait déjà **ce que vous coûte** leur fabrication, **ce que vous rapporte** leur vente et **où se trouvent les fichiers** pour les imprimer.

Il le sait parce que derrière cette ligne de commande, il y a quatre éléments que vous avez préparés une seule fois : un **Design**, une **Pièce**, une **Variante** et un **Produit**. Ce sont les quatre mots que vous verrez le plus dans BolloPrint. Vous verrez ici ce qu'est chacun, pourquoi ils sont quatre et pas un seul, et comment ils finissent dans une commande.

::animation{id="how-it-works"}

## Quatre questions, quatre éléments

Pour ne pas les confondre, pensez à la question à laquelle répond chacun :

| | Répond à… | Ce qu'il contient |
|---|---|---|
| **Design** | Qu'est-ce que c'est ? | Les fichiers 3D (STL, 3MF…), les photos et vos notes. Ni coût ni prix. |
| **Pièce** | Comment le fabriquer ? | Le matériau, la couleur, la finition, le poids et le temps. **Elle a un coût.** |
| **Variante** | À combien le vendre ? | Le prix et la marge. **C'est ce qui entre dans une commande.** |
| **Produit** | Comment le présenter ? | Le nom, les photos et la description. Il regroupe les variantes. |

Si vous ne retenez que ce tableau, vous avez déjà la moitié de l'article.

## Montons-le : un support de téléphone

Préparons le support de la commande, dans l'ordre où vous le feriez vous-même.

**1. Le Design.** Vous importez le STL du support et quelques photos. Le Design, c'est cela : le modèle et rien de plus. Vous n'avez pas encore décidé dans quoi vous allez l'imprimer : il n'a donc pas de coût.

**2. Les Pièces.** Maintenant, vous décidez comment vous le fabriquez : en **PLA noir** et en **PETG blanc**. Ce sont deux Pièces du même Design. Chacune a son matériau, son poids et son temps d'impression, donc chacune a **son coût**, et BolloPrint le calcule tout seul.

![Le détail du design du support, avec ses deux pièces en dessous : PLA noir et PETG blanc](/blog/media/2026-10-09-como-funciona-bolloprint/02-diseno-y-piezas.png)

:::info 💡 Une Pièce dépend toujours d'un Design
C'est pourquoi il n'y a pas de liste de Pièces à part : vous les trouvez à l'intérieur du Design auquel elles appartiennent.
:::

**3. Les Variantes.** Maintenant, vous décidez à combien vous le vendez. Vous créez la Variante « PLA noir » à **12,90 €** et la Variante « PETG blanc » à **15,90 €**. Chacune sait de quelle Pièce elle est faite, et donc ce qu'elle coûte ; avec le prix, elle calcule toute seule **la marge**.

**4. Le Produit.** Enfin, ce que voit le client : le Produit « Support téléphone réglable », avec son nom, ses photos et sa description. Il contient les deux Variantes, comme les options de couleur de n'importe quelle boutique en ligne. C'est ce que vous publiez, par exemple, sur Etsy.

![Les variantes du support en onglets, avec celle en PETG blanc ouverte : son coût, sa marge, son prix et la pièce dont elle est faite](/blog/media/2026-10-09-como-funciona-bolloprint/03-producto-y-variantes.png)

## Pourquoi quatre et pas une seule fiche ?

Parce que **chacun des quatre éléments change pour une raison différente** :

- Le **Design**, quand vous corrigez le modèle.
- La **Pièce**, quand vous changez de matériau ou que votre coût horaire augmente.
- La **Variante**, quand vous touchez au prix.
- Le **Produit**, quand vous changez les photos ou la description.

Avec une seule fiche, corriger le STL vous obligerait à le modifier dans chaque couleur que vous vendez. En séparant, vous le corrigez une fois, dans le Design, et cela vaut pour tout ce qui en dépend.

Autrement dit : le Design est la recette, la Pièce est le plat cuisiné et la Variante est ce qui figure sur la carte, avec son prix.

### La preuve : un pack

Imaginez que vous vendez aussi un **range-câbles** et qu'il vous vient l'idée d'un pack : le support noir et le range-câbles ensemble, à 19,90 €.

Il n'y a rien de nouveau à préparer. Vous créez une Variante « Pack bureau » avec **deux Pièces à l'intérieur** : celle du support noir et celle du range-câbles. BolloPrint additionne ce que coûtent les deux et, avec le prix, vous donne la marge du pack.

![La variante Pack bureau, composée de deux pièces ; et la pièce du support noir, utilisée à la fois par la variante seule et par le pack](/blog/media/2026-10-09-como-funciona-bolloprint/04-variante-de-dos-piezas.webp)

Désormais, **la Pièce du support noir est utilisée par deux Variantes** : la variante seule et le pack. Si demain le PLA augmente, vous modifiez cette Pièce une seule fois et BolloPrint vous indique quelles Variantes l'utilisent pour que vous revoyiez leur prix. C'est pour cela que Pièce et Variante sont deux choses distinctes.

Le même principe vaut pour vendre plusieurs exemplaires du même article : un « Pack x3 » est une Variante avec trois fois la même Pièce.

![Le bloc Pièces qui composent la variante, avec les deux pièces du pack](/blog/media/2026-10-09-como-funciona-bolloprint/05-piezas-de-la-variante.png)

## La commande boucle la boucle

Revenons à la commande du début. Quand vous créez une commande, ce que vous ajoutez **est une Variante** : vous cherchez « support », vous choisissez « PETG blanc », vous indiquez 2 unités et le prix se remplit tout seul.

Comme cette Variante sait de quelles Pièces elle est faite, la ligne de commande apporte déjà tout le reste :

- **ce que ça coûte et ce que ça rapporte**, parce que les Pièces ont un coût et la Variante a un prix ;
- **le matériau, la couleur et le poids**, qui viennent de ses Pièces ;
- **les fichiers à imprimer** : depuis la ligne, l'option **Designs** vous mène aux modèles 3D de chaque Pièce.

Une fois l'impression faite, vous marquez la ligne comme **imprimée** et la commande poursuit son chemin dans Production.

![Une commande avec deux lignes, le support blanc et le pack, et à côté les pièces à imprimer pour l'honorer](/blog/media/2026-10-09-como-funciona-bolloprint/06-del-pedido-a-la-impresora.webp)

Voilà ce que les quatre éléments vous épargnent : vous ne notez pas le coût de chaque commande, vous ne cherchez pas le STL dans un dossier et vous ne recalculez pas la marge à la main. Vous l'avez préparé une fois et chaque commande en hérite.

![Les lignes d'une commande, avec le menu ouvert sur l'option Designs](/blog/media/2026-10-09-como-funciona-bolloprint/07-lineas-del-pedido.png)

## Tout ça à chaque fois ? Non

Pour un seul support, cela peut sembler beaucoup de travail, et c'est à cela que sert la **Création express**. Vous lui donnez le STL, le matériau, la couleur et le prix dans un seul formulaire, et BolloPrint crée d'un coup le Design, la Pièce, la Variante et le Produit.

Le résultat est exactement le même que si vous l'aviez fait étape par étape. Le jour où vous voudrez ajouter une autre couleur ou monter un pack, tout sera déjà à sa place.

![Le formulaire de Création express, avec le fichier, le matériau, la couleur et le prix](/blog/media/2026-10-09-como-funciona-bolloprint/08-creacion-express.png)

:::info 💡 Des questions ?
Écrivez-nous depuis la [page de contact](/contact) ou ouvrez un fil sur [notre Discord](/help/soporte-por-discord). Dites-nous ce que vous vendez, et nous vous aiderons à le mettre en place.
:::

## Documentation associée

- [Catalogue](/help/catalogo) : les quatre niveaux, dans la référence
- [Designs](/help/disenos) : les fichiers, les photos et les étiquettes
- [Pièces](/help/piezas) : le matériau et le calcul du coût
- [Produits et Variantes](/help/productos-y-variantes) : le prix, la marge et les pièces de chaque variante
- [Commandes](/help/pedidos) : de la vente à la livraison
- [Création express](/help/creacion-express) : les quatre d'un coup
- [Ce que coûte vraiment une pièce imprimée](/blog/calculate-your-3d-printing-costs) — d'où vient le coût de chaque Pièce
