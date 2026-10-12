---
slug: connect-printers-local-network-agent
title: "Connectez vos imprimantes via votre propre réseau : l'agent local, pas à pas"
description: Prusa, Elegoo, Klipper, FlashForge, Bambu… Un petit agent sur un ordinateur de l'atelier, tout votre parc dans BolloPrint, sans toucher à la box.
date: 2026-09-08
updated: 2026-10-12
tags: [tutoriels]
cover: 01-portada.webp
draft: true
---

Vos imprimantes sont à l'atelier. Vous, pas toujours. Et chaque fois que vous voulez savoir si l'une d'elles imprime encore, si l'impression est réussie ou s'il lui reste du matériau, vous devez être devant.

Qu'elles soient sur votre réseau ne veut pas dire que vous devez y être aussi. C'est à ça que sert l'**agent local** : un petit programme qui vit sur un ordinateur de votre atelier, parle à vos imprimantes via votre propre réseau et raconte à BolloPrint ce qu'il voit.

- **Vous ne touchez pas à la box.** Pas de ports à ouvrir, pas d'IP fixe, pas de pare-feu.
- **Ultra léger.** N'importe quel ordinateur que vous laissez déjà allumé fait l'affaire.
- **Un seul pour tout le parc**, aussi grand soit-il.

::animation{id="local-agent"}

## Où l'installer

Sur **n'importe quel ordinateur de l'atelier que vous n'éteignez pas** : un NAS, un mini-PC, un Raspberry Pi, le PC de l'atelier. Vous ne lui demandez que deux choses : qu'il soit **toujours allumé** et qu'il ait **Docker**.

Encore mieux s'il est **sur le même réseau que les imprimantes**, car il les trouve alors tout seul. Sinon, vous les ajoutez à la main et elles fonctionnent exactement pareil.

## Étape 1 — Créez-le dans BolloPrint

Allez dans **Paramètres → Imprimantes**, ouvrez l'onglet **Agent local** et cliquez sur **Nouvel agent**.

Donnez-lui un nom qui vous parlera encore dans six mois. Un conseil : **nommez-le d'après l'endroit où il se trouve, pas d'après ce qu'il est**. « Rez-de-chaussée » ou « Hangar 2 » conviennent ; « Agent 1 », non.

![L'onglet Agent local, avec le bouton Nouvel agent](/blog/media/2026-09-08-impresoras-red-local-agente/02-nuevo-agente.png)

## Étape 2 — Copiez le manifeste

Lors de la création, BolloPrint vous montre un **manifeste** : un texte où tout ce qui vous concerne — les clés de votre agent et la version à utiliser — est **déjà écrit**. Il n'y a rien à remplacer ni à remplir.

Choisissez le format que vous utilisez (**Docker Compose** est le format habituel) et cliquez sur **Copier**.

![Le manifeste de déploiement, avec le bouton pour le copier](/blog/media/2026-09-08-impresoras-red-local-agente/03-plantilla.png)

:::warning 🔐 Copiez-le maintenant : il ne s'affiche qu'une fois
Les clés n'expirent pas, mais nous ne les affichons plus. Si vous perdez le manifeste, rien de grave : ouvrez l'agent et utilisez **Régénérer les clés** pour en obtenir un nouveau.
:::

## Étape 3 — Collez-le là où vous allez le lancer

Cette fois, cela se passe sur votre ordinateur, pas dans BolloPrint. Tout dépend de l'endroit où vous l'installez :

**Sur un NAS Synology.** Installez **Container Manager** depuis le **Centre de paquets**. Allez dans **Projet → Créer**, collez le manifeste et cliquez sur créer. Sans taper une seule commande.

**Sur Windows ou Mac.** Installez **Docker Desktop**, enregistrez le manifeste dans un dossier sous le nom `docker-compose.yml` et lancez-le depuis ce dossier avec `docker compose up -d`.

**Sur Linux.** Installez **Docker** avec le gestionnaire de paquets de votre distribution, enregistrez le manifeste sous le nom `docker-compose.yml` et, depuis ce dossier, lancez `docker compose up -d`.

Vous utilisez **Portainer** ? Collez le même manifeste dans une stack et déployez.

:::info 💡 Sur Windows et Mac, les imprimantes ne sont pas découvertes automatiquement
Là, Docker tourne dans une machine virtuelle, qui ne voit pas les annonces que les imprimantes envoient sur votre réseau. L'agent fonctionne de la même façon, mais c'est vous qui ajoutez les imprimantes, comme à l'étape 6.
:::

## Étape 4 — Vérifiez qu'il est en ligne

Revenez dans BolloPrint. En moins d'une minute, l'agent passe à **En ligne**.

![L'agent à l'état En ligne](/blog/media/2026-09-08-impresoras-red-local-agente/04-agente-online.png)

S'il n'apparaît pas, c'est presque toujours l'une de ces trois causes : le manifeste **collé à moitié**, l'ordinateur **sans internet**, ou un **pare-feu** qui bloque la sortie.

## Étape 5 — Vos imprimantes apparaissent toutes seules

L'agent **cherche les imprimantes sur votre réseau** de lui-même, toutes les 15 minutes. Celles qu'il trouve apparaissent dans une liste avec leur marque et leur modèle, et c'est vous qui décidez :

- **Ajouter** — vous l'enregistrez et elle commence à envoyer ses informations.
- **Ignorer** — elle n'est pas à vous, ou vous ne la voulez pas ici.

![Les imprimantes trouvées sur le réseau, avec les boutons Ajouter et Ignorer](/blog/media/2026-09-08-impresoras-red-local-agente/05-encontradas.png)

Si vous venez d'allumer une machine et ne voulez pas attendre, il y a un bouton **Chercher maintenant**.

Certaines vous demanderont un **mot de passe** au moment de les ajouter. Cela dépend de la marque, et on y vient dans un instant.

## Étape 6 — Si l'une n'apparaît pas, ajoutez-la vous-même

Qu'une imprimante n'apparaisse pas toute seule est **normal** dans deux cas :

- **Elle est sur un autre réseau.** Les annonces des imprimantes ne passent pas d'un réseau à l'autre : elles ne sont donc pas découvertes automatiquement.
- **L'agent tourne sous Windows ou Mac.** Docker y tourne dans une machine virtuelle, et elles ne sont pas découvertes automatiquement non plus.

**Vous n'y perdez rien.** Vous l'ajoutez vous-même et elle fonctionne exactement pareil, avec la caméra et les commandes si cette machine en dispose. Cliquez sur **Ajouter par IP** et indiquez le type d'imprimante, son adresse sur votre réseau et, si elle en demande un, son mot de passe.

![Le formulaire pour ajouter une imprimante par son IP](/blog/media/2026-09-08-impresoras-red-local-agente/06-anadir-por-ip.png)

:::info 💡 Réservez-lui son IP dans la box
Si la box change l'adresse d'une imprimante, nous la retrouvons automatiquement, mais elle sera hors ligne un moment. Lui réserver son adresse évite ce trou. C'est un réglage de la box, pas de BolloPrint.
:::

## Ce que demande chaque marque

C'est là que les gens bloquent. En résumé :

| Marque | Ce que vous devez faire sur la machine | Caméra | Pouvez-vous mettre en pause et annuler ? |
|---|---|---|---|
| **Bambu Lab** | Activer le **Mode LAN** sur son écran et utiliser le **code d'accès** qu'elle affiche | Oui | Oui, si vous activez aussi le **Mode développeur** |
| **Prusa** (MK4, MK3.5, MK3.9, MINI, XL, CORE One) | Utiliser le **mot de passe** qu'affiche l'imprimante elle-même | Pas encore | Oui |
| **Klipper** (QIDI, Sovol, Voron, RatRig, Creality K1…) | En général rien : elle se connecte normalement sans mot de passe | Oui, si vous avez une webcam sur votre Klipper | Oui |
| **Elegoo à résine** (Mars, Saturn, Jupiter) | Rien, elle ne demande pas de mot de passe | Sur les modèles qui en ont une | Oui |
| **Elegoo Centauri Carbon 2** | Seulement si vous avez défini un code sur son écran | Oui | Pas encore |
| **FlashForge** (Adventurer 5M, 5M Pro, AD5X, Creator 5) | Activer **LAN Only** et utiliser le code de son écran | Oui | Pas encore |

:::warning ⚠️ Bambu Lab : le code d'accès CHANGE
Chaque fois que vous activez ou désactivez le Mode LAN, Bambu **génère un nouveau code**. Si une Bambu qui fonctionnait bien cesse soudain de se connecter, c'est ça neuf fois sur dix : regardez à nouveau le code sur son écran et mettez-le à jour dans BolloPrint.
:::

:::info 💡 Vous ne trouvez pas votre modèle dans le tableau ?
Consultez les [imprimantes compatibles](/help/impresoras-compatibles). Et si elle tourne sous **Klipper** — n'importe quelle machine montée par vous-même ou modifiée —, elle est prise en charge, même si la marque n'apparaît sur aucune liste.
:::

## Si vous aviez déjà des Bambu via le cloud, ne les dupliquez pas

Quand l'agent trouve sur votre réseau une machine que **vous aviez déjà connectée via le cloud**, BolloPrint le détecte et vous le dit : *« C'est « P1S-02 », que vous avez déjà via Bambu Cloud »*. Le bouton est **Connecter aussi en LAN**.

Cliquez dessus, et vous ne l'aurez pas en double :

- Elle reste **une seule imprimante**, avec son numéro, son nom et tout son historique.
- Elle n'occupe **qu'une seule place** dans votre forfait.
- Et elle gagne la **caméra**, que vous n'aviez pas via le cloud.

![L'avertissement indiquant que cette imprimante est déjà dans Bambu Cloud, avec le bouton Connecter aussi en LAN](/blog/media/2026-09-08-impresoras-red-local-agente/07-tambien-por-lan.png)

:::warning ⚠️ Le Mode LAN déconnecte le cloud de Bambu
Quand vous l'activez, l'imprimante cesse de communiquer avec le cloud de Bambu Lab. À partir de là, BolloPrint la voit via l'agent.
:::

## Ce que vous y gagnez, concrètement

- **Presque toutes les marques.** Prusa, Elegoo, Klipper, QIDI, Sovol, FlashForge, Voron… Le cloud ne vous donne pas ça : il n'existe que pour Bambu Lab.
- **La caméra.** La voir en direct quand vous avez la page sous les yeux, prendre une photo quand vous voulez, et une photo finale conservée dans l'historique de chaque impression. Ce n'est pas de la vidéosurveillance : rien n'est enregistré.
- **Les commandes.** Mettre en pause, reprendre et annuler depuis BolloPrint, sans vous déplacer jusqu'à la machine, sur celles qui le permettent (voir le tableau ci-dessus). Sur Bambu Lab, avec l'imprimante en **Mode LAN** et en **Mode développeur**.
- **Il résiste aux coupures d'internet.** Si votre ligne tombe, l'agent **continue de lire les imprimantes et garde une trace de ce qui se passe**. Quand elle revient, il envoie tout. Vous ne perdez pas ces heures d'historique.
- **Vous ne dépendez pas du fabricant**, ni du fait que son cloud continue de fonctionner.

Ce qui n'est possible par aucune voie : **envoyer des travaux à imprimer**. Le fichier, vous continuez à l'envoyer depuis votre trancheur.

## Les questions qu'on nous pose souvent

**Dois-je ouvrir des ports sur la box ?** Non. Ni ports, ni IP fixe, ni règles de pare-feu. Il fonctionne derrière une box domestique ordinaire.

**Faut-il un agent par imprimante ?** Non. **Un seul gère tout le parc.** Il n'est utile d'en avoir plusieurs que si vous avez deux locaux ou deux réseaux séparés.

**Et si j'éteins l'ordinateur, ou si une nouvelle version sort ?** Quand vous le rallumez, l'agent revient tout seul. Et il se met à jour tout seul : quand une nouvelle version sort, il la télécharge et redémarre avec. Vous n'aurez à intervenir que si nous vous prévenons à l'écran.

:::info 💡 Vous êtes bloqué ?
Écrivez-nous depuis la [page de contact](/contact) ou ouvrez un fil sur [notre Discord](/help/soporte-por-discord). Dites-nous quelles imprimantes vous avez, et nous vous dirons exactement quoi faire avec chacune.
:::

## Documentation associée

- [Connecter des imprimantes](/help/conectar-impresoras) — les deux voies et celle qui vous convient
- [L'agent local](/help/el-agente-local) — la référence complète
- [Déployer l'agent](/help/desplegar-el-agente) — le détail technique, si vous en avez besoin
- [Types de connexion](/help/tipos-de-conexion) — ce que permet chaque famille d'imprimantes
- [Imprimantes compatibles](/help/impresoras-compatibles) — cherchez votre modèle ici
