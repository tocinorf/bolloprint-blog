---
slug: calculate-your-3d-printing-costs
title: "Ce que coûte vraiment une pièce imprimée (et comment le calculer simplement)"
description: Cette pièce à 1,60 € de filament vous coûte 9,36 €. Nous vous montrons comment répartir les dépenses de votre atelier sur vos heures d'impression pour que BolloPrint l'applique tout seul à chaque pièce.
date: 2026-09-12
updated: 2026-10-12
tags: [tutoriels]
cover: 01-portada.webp
draft: true
---

Une pièce de 6 heures et 80 grammes de PLA. Combien vous coûte-t-elle ?

Si vous avez pensé « 80 grammes à 20 € le kilo, **1,60 €** », vous n'avez calculé que le **matériau**. Dans un atelier normal, ce n'est **qu'une petite partie** de ce que la pièce vous coûte réellement.

Dans un atelier de trois imprimantes, avec la pièce peinte et emballée, le calcul complet est le suivant :

| | |
|---|---|
| Matériau | 1,60 € |
| 6 heures d'imprimante | 5,16 € |
| Finition (peinte) | 2,00 € |
| Coûts supplémentaires (emballage) | 0,60 € |
| **Coût réel de la pièce** | **9,36 €** |

**Presque six fois plus.** L'écart n'est pas un arrondi : c'est le loyer, l'électricité, l'usure des imprimantes, le comptable et les pièces ratées. Tout cela, vous le payez ; la question est de savoir si vous le facturez.

Vous verrez ici comment intégrer ces dépenses au coût de chaque pièce. **Cela se configure une fois**, puis s'applique tout seul à chaque pièce que vous créez.

::animation{id="part-cost"}

## D'où sortent ces 5,16 €

L'idée est simple : vous additionnez **tout ce que vous coûte l'atelier chaque mois** et vous le divisez par **les heures où vous imprimez vraiment**. Vous obtenez ainsi ce que vous coûte **une heure d'imprimante**, et il ne reste plus qu'à la multiplier par les heures de la pièce.

Avec les chiffres de l'exemple :

- **Heures :** trois imprimantes, dix heures par jour, vingt-cinq jours par mois → **750 heures**.
- **Dépenses :** entre le loyer, le comptable, les logiciels et l'amortissement des machines, il part environ **516 € par mois**. Réparti : 0,69 € de l'heure. Avec l'électricité, le **coût de base** s'établit à **0,72 €**.
- **Majorations :** 5 % de maintenance, 10 % de taux d'échec et 5 % d'imprévus le portent à **0,86 € de l'heure**. Pour six heures, 5,16 €.

C'est exactement le calcul que fait la section **Coûts** de BolloPrint, dans **Paramètres → Coûts**. Seuls le **Propriétaire** et les **Admins** la voient.

![La section Coûts dans les Paramètres](/blog/media/2026-09-12-costes-reales/02-seccion-costes.png)

## Les heures où vous imprimez vraiment

Commencez par les heures : c'est le chiffre que le plus de gens calculent mal, et celui qui change le plus le résultat. Il se trouve dans **Coût horaire → Heures d'impression**, et ce sont trois champs :

**Imprimantes × Heures / jour × Jours / mois**

Indiquez **ce qui se passe vraiment, pas le maximum théorique**. Si vous avez trois imprimantes mais qu'en moyenne elles travaillent huit heures par jour, c'est huit. Pas vingt-quatre.

Il est tentant de mettre un chiffre élevé, parce que plus il est élevé, moins l'heure revient cher. Mais ces dépenses, vous les payez quand même, et ce que vous ne répartissez pas sur les pièces, c'est vous qui le payez en fin de mois.

![L'onglet Heures d'impression, avec les trois champs et le résultat](/blog/media/2026-09-12-costes-reales/03-horas-impresion.png)

## Ce que vous coûte l'atelier

Une fois les heures définies, passez aux dépenses. Dans **Coût de base**, vous les ajoutez une à une ; BolloPrint les classe par type et ne vous demande pour chacune que ce dont il a besoin :

| Type | Ce que vous indiquez |
|---|---|
| **Coût fixe** | Loyer, internet, comptable, assurances… le montant par mois |
| **Imprimante** | Ce qu'elle vous a coûté et sur combien d'années vous l'amortissez |
| **Logiciel** | L'abonnement au trancheur, à BolloPrint, à ce que vous utilisez |
| **Salaires** | Le salaire et le nombre de personnes |
| **Électricité** | Les kW que consomme une imprimante et le prix du kWh qu'on vous facture |

Pas besoin d'être exact au centime près : un chiffre raisonnable aujourd'hui vaut mieux que le chiffre parfait l'an prochain.

:::warning ⚠️ Ne saisissez pas deux fois la même dépense
Les montants **mensuels** décrivent **tout l'atelier** : le loyer ne se saisit qu'une seule fois. Ceux qui sont **par heure imprimée** — comme l'électricité à la consommation — décrivent **une seule imprimante** : indiquez-y la consommation d'une machine moyenne, pas celle de toute la ferme.
:::

Tout en bas, vous avez le calcul tout fait, le même qu'au début :

> **dépenses du mois ÷ vos heures d'impression = ce que vous coûte une heure « au net »**

C'est le **coût de base par heure** : 0,72 € dans l'exemple.

![Les dépenses de l’atelier dans Coût de base, regroupées par type, et le calcul qui donne 0,72 € de l’heure](/blog/media/2026-09-12-costes-reales/03b-coste-base.png)

## Ce qui arrive forcément

Le coût de base laisse de côté ce qui arrive sans facture fixe : des buses cassent, et **de temps en temps une pièce rate et il faut la réimprimer**.

C'est à cela que sert le **Coût total**, qui ajoute des pourcentages au coût de base : maintenance, taux d'échec et imprévus.

Le taux d'échec est le plus important, et celui que la plupart des gens oublient. Si une pièce sur dix finit à la poubelle, **les neuf bonnes paient pour la mauvaise**. Si vous ne l'intégrez pas ici, c'est vous qui payez.

Le résultat est votre **coût total par heure** : 0,86 € dans l'exemple. C'est votre vrai chiffre, et c'est celui qui s'applique à chaque pièce.

:::info 💡 La marge bénéficiaire ne va pas ici
Ici, il n'y a que des **coûts**. Ce que vous voulez gagner se décide ensuite, dans le produit, parce que c'est une décision commerciale.
:::

![Les majorations d’entretien, de taux d’échec et d’imprévus sur le coût de base, jusqu’à 0,86 € de l’heure](/blog/media/2026-09-12-costes-reales/03c-coste-total.png)

## Le matériau et les extras

Reste la partie la plus simple, dans **Valeurs par défaut** :

- **Le prix de chaque matériau**, au kilo. C'est **par type**, pas par famille : le PLA et le TPU ne coûtent pas la même chose.
- **Les finitions** : le supplément que vous appliquez si la pièce est post-traitée ou peinte.
- **Les coûts supplémentaires** : emballage, visserie, aimants, inserts, main-d'œuvre. Pour chacun, vous choisissez s'il est compté **par unité** ou **par plateau**.
- **Les marges** : celle que vous voulez par défaut, et à partir de quel pourcentage nous vous alertons en rouge ou en orange.

:::info 💡 Si le matériau est dans l'inventaire, c'est l'inventaire qui l'emporte
Ces prix sont des références, pour quand il n'y a rien derrière. Si la pièce sort d'une bobine enregistrée avec son coût réel, c'est ce coût-là que nous utilisons.
:::

![Valeurs par défaut : les marges avec leurs alertes de couleur et le prix de chaque matériau au kilo](/blog/media/2026-09-12-costes-reales/03d-valores-por-defecto.png)

## Et voilà comment ça arrive jusqu'à votre pièce

Les quatre étapes précédentes aboutissent à un seul chiffre : **ce que vous coûte une heure d'imprimante**. À partir de là, chaque pièce est une addition :

> ses **heures × votre coût horaire**
> **+** le **matériau** qu'elle utilise
> **+** la **finition**, si elle est post-traitée ou peinte
> **+** les **coûts supplémentaires** que vous lui ajoutez

Un détail mérite d'être compris, parce qu'il explique pourquoi on a intérêt à remplir le plateau : **le calcul se fait par plateau, pas par pièce**. BolloPrint calcule ce que coûte le plateau entier et le **répartit entre les pièces qui en sortent**. C'est pourquoi, parmi les coûts supplémentaires, ceux que vous marquez **par plateau** ne sont comptés qu'une seule fois — que vous imprimiez les pièces à l'unité ou par vingt — et ceux **par unité** sont comptés sur chaque pièce.

De plus, chaque pièce **conserve le coût horaire avec lequel elle a été calculée**. C'est voulu : ainsi, le coût de ce que vous avez imprimé l'an dernier reste celui de l'époque. C'est aussi la raison d'être du bouton **Recalculer**, un peu plus bas.

## Maintenant, vous avez votre chiffre

Pour voir le résultat, allez dans **Coûts → Résumé**. Le bloc **Exemple** prend un plateau d'exemple et vous montre le calcul complet **avec vos valeurs** : combien pour le matériau, combien pour l'impression, combien pour la finition et combien revient la pièce.

![Le bloc Exemple avec le détail complet d'une pièce](/blog/media/2026-09-12-costes-reales/04-ejemplo-coste.png)

## Quand vos dépenses changent

Vos chiffres ne resteront pas toujours les mêmes : l'électricité augmente, vous achetez une autre imprimante ou vous changez de local. Quand vous les mettez à jour, **les pièces que vous aviez déjà ne changent pas toutes seules**. C'est voulu : chaque pièce conserve le coût avec lequel elle a été calculée, et vous ne voudriez pas que le coût de tout ce que vous avez fait l'an dernier soit réécrit.

Quand vous voulez l'appliquer à tout, vous avez dans **Résumé** un compteur de pièces **à recalculer** et le bouton **Recalculer**. C'est vous qui décidez quand.

:::info 💡 Vos prix de vente ne bougent pas
Recalculer met à jour le **coût** et le prix *suggéré*. Celui que vous avez fixé à la main reste tel quel. Ce que vous allez voir bouger, c'est l'indicateur de **marge**.
:::

## Est-ce que j'achète une autre imprimante ?

Une fois vos coûts configurés, vous pouvez répondre à cette question avec des chiffres. Dans le **Comparateur de ferme**, vous faites varier les imprimantes, les heures ou les jours et vous voyez ce qui arriverait à votre coût horaire. C'est une simple simulation : rien ne change dans votre configuration.

Ce qu'il montre le mieux, c'est que **la courbe cesse de baisser**. Passer d'une imprimante à cinq divise le coût horaire presque par cinq. Passer de vingt à cent ne le fait presque plus bouger, parce que certaines dépenses — comme l'électricité — se paient à chaque heure imprimée et ne se répartissent pas.

![Le comparateur de ferme, avec la courbe du coût horaire](/blog/media/2026-09-12-costes-reales/05-comparador.png)

La configuration, ce sont quatre écrans et une partie d'un après-midi. En échange, chaque pièce que vous créerez portera son coût réel, et vous saurez si vous gagnez de l'argent sans faire le calcul à la main.

:::info 💡 On vous aide avec vos chiffres ?
Si vous ne savez pas par où commencer, écrivez-nous depuis la [page de contact](/contact) ou sur [notre Discord](/help/soporte-por-discord). Nous l'avons déjà fait plus d'une fois.
:::

## Documentation associée

- [Coûts](/help/costes) : la référence complète de la section
- [Pièces](/help/piezas) : comment se calcule le coût de chaque pièce
- [Produits et Variantes](/help/productos-y-variantes) : du coût au prix de vente
- [Inventaire](/help/inventario) : pour que le matériau soit compté à son coût réel
