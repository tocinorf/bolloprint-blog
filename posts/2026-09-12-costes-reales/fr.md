---
slug: calculate-your-3d-printing-costs
title: "Ce que coûte vraiment une pièce imprimée (et comment le calculer sans vous arracher les cheveux)"
description: Cette pièce à 1,60 € de filament vous coûte 9,36 €. Nous vous montrons comment répartir les dépenses de votre atelier sur vos heures d'impression et laisser BolloPrint l'appliquer tout seul à chaque pièce.
date: 2026-09-12
updated: 2026-10-12
tags: [tutoriels]
cover: 01-portada.webp
draft: true
---

Une pièce de 6 heures et 80 grammes de PLA. Combien vous coûte-t-elle ?

Si vous avez pensé « 80 grammes à 20 € le kilo, **1,60 €** », vous avez calculé ce que coûte le **matériau**. Ce qui, dans un atelier normal, n'est **qu'une petite partie** de ce que cette pièce vous coûte réellement.

Le calcul complet, dans un atelier de trois imprimantes et avec la pièce peinte et emballée, donne ceci :

| | |
|---|---|
| Matériau | 1,60 € |
| 6 heures d'imprimante | 5,16 € |
| Finition (peinte) | 2,00 € |
| Coûts supplémentaires (emballage) | 0,60 € |
| **Coût réel de la pièce** | **9,36 €** |

**Presque six fois plus.** Et l'écart n'est pas un arrondi : c'est le loyer, l'électricité, les imprimantes qui s'usent, le comptable et les pièces ratées. Tout ça, vous le payez. La question, c'est de savoir si vous le facturez.

C'est ce qu'on va régler ici. Et la bonne nouvelle, c'est que **ça se configure une fois**, puis ça s'applique tout seul à chaque pièce que vous créez.

::animation{id="part-cost"}

## D'où sortent ces 5,16 €

D'une idée simple : vous prenez **tout ce que vous coûte l'atelier chaque mois**, vous le divisez par **les heures où vous imprimez vraiment**, et vous savez ainsi ce que vous coûte **une heure d'imprimante**. Ensuite, vous multipliez par les heures de la pièce.

Dans l'exemple ci-dessus :

> Trois imprimantes, dix heures par jour, vingt-cinq jours par mois → **750 heures**.
>
> Entre le loyer, le comptable, les logiciels et l'amortissement des machines, il part environ **516 € par mois**. Réparti : 0,69 € de l'heure. Avec l'électricité, le **coût de base** s'établit à **0,72 €**.
>
> Plus 5 % de maintenance, 10 % de taux d'échec et 5 % d'imprévus : **0,86 € de l'heure**. Pour six heures, 5,16 €.

C'est exactement ce que calcule la section **Coûts** de BolloPrint, dans **Paramètres → Coûts**. Seuls le **Propriétaire** et les **Admins** la voient.

![La section Coûts dans les Paramètres](/blog/media/2026-09-12-costes-reales/02-seccion-costes.png)

## Étape 1 — Les heures où vous imprimez vraiment

C'est le chiffre que le plus de gens calculent mal, et celui qui change le plus le résultat. Il se trouve dans **Coût horaire → Heures d'impression**, et ce sont trois champs :

**Imprimantes × Heures / jour × Jours / mois**

Le seul conseil qui compte : **ne mettez pas le maximum théorique, mettez ce qui se passe vraiment**. Si vous avez trois imprimantes mais qu'en moyenne elles travaillent huit heures par jour, c'est huit. Pas vingt-quatre.

C'est tentant de mettre le gros chiffre, parce que plus il est élevé, moins l'heure revient cher. Mais si vous gonflez les heures, vous vous mentez à vous-même : ces dépenses, vous les payez quand même, et ce que vous ne répartissez pas sur les pièces, c'est vous qui l'encaissez en fin de mois.

![L'onglet Heures d'impression, avec les trois champs et le résultat](/blog/media/2026-09-12-costes-reales/03-horas-impresion.png)

## Étape 2 — Ce que vous coûte l'atelier

Dans **Coût de base**, vous saisissez vos dépenses. BolloPrint les classe par type et ne vous demande pour chacune que ce dont il a besoin :

| Type | Ce que vous indiquez |
|---|---|
| **Coût fixe** | Loyer, internet, comptable, assurances… le montant par mois |
| **Imprimante** | Ce qu'elle vous a coûté et sur combien d'années vous l'amortissez |
| **Logiciel** | L'abonnement au trancheur, à BolloPrint, à ce que vous utilisez |
| **Salaires** | Le salaire et le nombre de personnes |
| **Électricité** | Les kW que consomme une imprimante et le prix du kWh qu'on vous facture |

Pas besoin d'être exact au centime près. Un chiffre raisonnable aujourd'hui vaut bien mieux que le chiffre parfait l'an prochain.

:::warning ⚠️ Ne saisissez pas deux fois la même dépense
Les montants **mensuels** décrivent **tout l'atelier** : le loyer ne se saisit qu'une seule fois. Ceux qui sont **par heure imprimée** — comme l'électricité à la consommation — décrivent **une seule imprimante** : indiquez-y la consommation d'une machine moyenne, pas celle de toute la ferme.
:::

Tout en bas, vous avez le calcul tout fait, celui du début :

> **dépenses du mois ÷ vos heures d'impression = ce que vous coûte une heure « au net »**

C'est le **coût de base par heure**. Dans l'exemple ci-dessus, 0,72 €.

## Étape 3 — Ce qui arrive forcément

Le coût de base laisse de côté des choses qui arrivent et qui n'ont pas de facture fixe : des buses cassent, et **de temps en temps une pièce rate et il faut la réimprimer**.

C'est à ça que sert le **Coût total** : des pourcentages sur le coût de base. Maintenance, taux d'échec et imprévus.

Le taux d'échec est le plus important, et celui que la plupart des gens oublient. Si une pièce sur dix finit à la poubelle, **les neuf bonnes paient pour la mauvaise**. Si vous ne le mettez pas ici, c'est vous qui payez.

Le résultat est votre **coût total par heure** — 0,86 € dans l'exemple. C'est votre vrai chiffre, et c'est celui qui s'applique à chaque pièce.

:::info 💡 La marge bénéficiaire ne va pas ici
Ici, il n'y a que des **coûts**. Ce que vous voulez gagner se décide ensuite, dans le produit, parce que c'est une décision commerciale.
:::

## Étape 4 — Le matériau et les extras

La partie facile, dans **Valeurs par défaut** :

- **Le prix de chaque matériau**, au kilo. C'est **par type**, pas par famille : le PLA et le TPU ne coûtent pas la même chose.
- **Les finitions** : le supplément que vous appliquez si la pièce est post-traitée ou peinte.
- **Les coûts supplémentaires** : emballage, visserie, aimants, inserts, main-d'œuvre. Pour chacun, vous choisissez s'il est compté **par unité** ou **par plateau**.
- **Les marges** : celle que vous voulez par défaut, et à partir de quel pourcentage nous vous alertons en rouge ou en orange.

:::info 💡 Si le matériau est dans l'inventaire, c'est l'inventaire qui l'emporte
Ces prix sont des références, pour quand il n'y a rien derrière. Si la pièce sort d'une bobine enregistrée avec son coût réel, c'est ce coût-là que nous utilisons.
:::

## Et voilà comment ça arrive jusqu'à votre pièce

Les quatre étapes aboutissent à un seul chiffre : **ce que vous coûte une heure d'imprimante**. À partir de là, chaque pièce est une addition :

> ses **heures × votre coût horaire**
> **+** le **matériau** qu'elle utilise
> **+** la **finition**, si elle est post-traitée ou peinte
> **+** les **coûts supplémentaires** que vous lui ajoutez

Il y a un détail qu'il vaut mieux comprendre, parce qu'il explique pourquoi on a intérêt à remplir le plateau : **le calcul se fait par plateau, pas par pièce**. BolloPrint calcule ce que coûte le plateau entier et le **répartit entre les pièces qui en sortent**. C'est pourquoi, parmi les coûts supplémentaires, ceux que vous marquez **par plateau** ne sont comptés qu'une seule fois — que vous imprimiez à l'unité ou par vingt — tandis que ceux **par unité** sont comptés sur chaque pièce.

Et chaque pièce **conserve le coût horaire avec lequel elle a été calculée**. Ce n'est pas un oubli : c'est ce qui fait que le coût de ce que vous avez imprimé l'an dernier reste celui de l'époque, et c'est la raison d'être du bouton **Recalculer**, un peu plus bas.

## Maintenant, vous avez votre chiffre

Dans **Coûts → Résumé**, le bloc **Exemple** prend un plateau d'exemple et vous montre le calcul complet **avec vos valeurs** : combien pour le matériau, combien pour l'impression, combien pour la finition, et combien revient la pièce.

![Le bloc Exemple avec le détail complet d'une pièce](/blog/media/2026-09-12-costes-reales/04-ejemplo-coste.png)

## Quand vos dépenses changent

L'électricité augmente, vous achetez une autre imprimante, vous changez de local. Vous modifiez les chiffres et… **les pièces que vous aviez déjà ne changent pas toutes seules**. C'est voulu : chaque pièce conserve le coût avec lequel elle a été calculée, et vous ne voudriez pas que le coût de tout ce que vous avez fait l'an dernier soit réécrit.

Quand vous voulez l'appliquer à tout, vous avez dans **Résumé** un compteur de pièces **à recalculer** et un bouton **Recalculer**. C'est vous qui décidez quand.

:::info 💡 Vos prix de vente ne bougent pas
Recalculer met à jour le **coût** et le prix *suggéré*. Celui que vous avez fixé à la main reste tel quel. Ce que vous allez voir bouger, c'est l'indicateur de **marge**.
:::

## Est-ce que j'achète une autre imprimante ?

C'est **la** question, et vous pouvez maintenant y répondre avec des chiffres. Dans le **Comparateur de ferme**, vous faites varier les imprimantes, les heures ou les jours et vous voyez ce qui arriverait à votre coût horaire. Cela ne change rien à votre configuration : c'est une simple simulation.

Il y a une chose qu'il montre très bien : **la courbe cesse de baisser**. Passer d'une imprimante à cinq divise le coût horaire presque par cinq. Passer de vingt à cent ne le fait presque plus bouger, parce que certaines dépenses — comme l'électricité — se paient à chaque heure imprimée et ne se répartissent pas.

![Le comparateur de ferme, avec la courbe du coût horaire](/blog/media/2026-09-12-costes-reales/05-comparador.png)

Ce sont quatre écrans et un moment, un après-midi. En échange, chaque pièce que vous créerez portera son coût réel, et vous saurez si vous gagnez de l'argent sans faire le calcul à la main.

:::info 💡 On vous aide avec vos chiffres ?
Si vous ne savez pas par où commencer, écrivez-nous depuis la [page de contact](/contact) ou passez sur [notre Discord](/help/soporte-por-discord). Nous l'avons déjà fait plus d'une fois.
:::

## Documentation associée

- [Coûts](/help/costes) — la référence complète de la section
- [Pièces](/help/piezas) — comment se calcule le coût de chaque pièce
- [Produits et Variantes](/help/productos-y-variantes) — du coût au prix de vente
- [Inventaire](/help/inventario) — pour que le matériau soit compté à son coût réel
