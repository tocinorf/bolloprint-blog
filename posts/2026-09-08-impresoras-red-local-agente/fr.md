---
slug: connect-printers-local-network-agent
title: "Connectez vos imprimantes via votre propre réseau : l'agent local, pas à pas"
description: Bambu Lab, Prusa, Elegoo, Anycubic, FlashForge, Snapmaker, Klipper… Un petit agent sur un ordinateur de l'atelier, tout votre parc dans BolloPrint, sans toucher à la box.
date: 2026-10-12
updated: 2026-10-16
tags: [tutoriels]
cover: 01-portada.webp
---

Vos imprimantes sont à l'atelier, mais vous n'y êtes pas toujours. Et pour savoir si l'une d'elles imprime encore, si l'impression est réussie ou s'il lui reste du matériau, vous devez être devant.

C'est à ça que sert l'**agent local** : un petit programme qui tourne sur un ordinateur de votre atelier, parle à vos imprimantes via votre propre réseau et transmet à BolloPrint ce qu'il voit.

- **Vous ne touchez pas à la box** : pas de ports ouverts, pas d'IP fixe, pas de pare-feu.
- **Il est très léger** : n'importe quel ordinateur que vous laissez déjà allumé fait l'affaire.
- **Un seul suffit pour tout le parc**, quelle que soit sa taille.
- **Il se met à jour tout seul** : quand une nouvelle version sort, il l'installe lui-même.

::animation{id="local-agent"}

## Où l'installer

L'agent vit sur **n'importe quel ordinateur de l'atelier que vous n'éteignez pas** : un NAS, un mini-PC, un Raspberry Pi ou le PC de l'atelier. Il lui faut seulement être **toujours allumé** et avoir **Docker**.

L'idéal est qu'il soit **sur le même réseau que les imprimantes**, car il les trouve alors tout seul. Si ce n'est pas possible, vous les ajoutez à la main et elles fonctionnent pareil.

## Créez l'agent dans BolloPrint

Commencez dans BolloPrint. Allez dans **Paramètres → Imprimantes**. Vous y verrez trois onglets : **Imprimantes** (toutes vos machines, quelle que soit la façon dont elles sont connectées), **Agent local** et **Bambu Cloud**. Ouvrez **Agent local** et cliquez sur **Nouvel agent**.

Donnez-lui un nom qui vous parlera encore dans six mois : **nommez-le d'après l'endroit où il se trouve, pas d'après ce qu'il est**. « Rez-de-chaussée » ou « Hangar 2 » conviennent ; « Agent 1 », non. Cliquez ensuite sur **Créer l’agent**.

![L'onglet Agent local, avec deux agents en ligne et le bouton Nouvel agent](/blog/media/2026-09-08-impresoras-red-local-agente/02-nuevo-agente-fr.png)

## Copiez le manifeste

Lors de la création, BolloPrint vous montre un **manifeste** : un texte où tout ce qui vous concerne est **déjà écrit**, les clés de votre agent et la version à utiliser. Il n'y a rien à remplacer ni à remplir.

Choisissez le format que vous utilisez (**Docker Compose** est le format habituel), cliquez sur **Copier** puis, une fois le manifeste mis en lieu sûr, sur **Enregistrer**.

![Le manifeste de déploiement du nouvel agent, avec le bouton Copier](/blog/media/2026-09-08-impresoras-red-local-agente/03-plantilla-fr.png "75%")

:::warning 🔐 Copiez-le maintenant : les clés ne s'affichent qu'une fois
Nous ne les conservons pas, nous ne pouvons donc pas vous les montrer à nouveau. Si vous perdez le manifeste, rien de grave : ouvrez l'agent avec **Modifier** (dans son menu **⋮**), allez dans l'onglet **Déploiement** et cliquez sur **Régénérer les clés**. S'il ne s'est encore jamais connecté, rien n'est coupé.
:::

## Collez le manifeste sur votre ordinateur

Cette étape se passe sur votre ordinateur, pas dans BolloPrint, et dépend de l'endroit où vous l'installez :

- **NAS Synology** : installez **Container Manager** depuis le **Centre de paquets**, allez dans **Projet → Créer**, collez le manifeste et créez le projet. Sans taper une seule commande.
- **Windows ou Mac** : installez **Docker Desktop**, enregistrez le manifeste dans un dossier sous le nom `docker-compose.yml` et, depuis ce dossier, lancez `docker compose up -d`.
- **Linux** : installez **Docker** avec le gestionnaire de paquets de votre distribution, enregistrez le manifeste sous le nom `docker-compose.yml` et lancez-y `docker compose up -d`.
- **Portainer** : collez le même manifeste dans une stack et déployez-la.

:::info 💡 Sur Windows et Mac, les imprimantes ne sont pas découvertes automatiquement
Là, Docker tourne dans une machine virtuelle, qui ne voit pas les annonces que les imprimantes envoient sur votre réseau. L'agent fonctionne de la même façon, mais c'est vous qui ajoutez les imprimantes, comme expliqué plus bas.
:::

## Bloqué ? Cliquez sur « Installer »

Tant que l'agent ne s'est pas connecté au moins une fois, sa ligne indique **Non installé**. Ce n'est pas une erreur : rien n'est tombé en panne, il reste simplement à l'installer.

Sur cette même ligne, vous avez le bouton **Installer**. En cliquant dessus, vous retrouvez les étapes que vous venez de lire, en bref, avec un lien vers l'**Aide**, un autre vers cet **Article du blog** et un bouton pour nous poser vos questions sur **Discord**. Si vous n'avez pas gardé le manifeste, l'étape 3 vous mène directement à la génération d'un nouveau.

![Un agent non installé avec le panneau Installer ouvert : les trois étapes, l'aide et Discord](/blog/media/2026-09-08-impresoras-red-local-agente/04-instalar-fr.png)

## Vérifiez qu'il est en ligne

Revenez dans BolloPrint : en moins d'une minute, l'agent passe à **En ligne**, avec le nom de l'ordinateur sur lequel il tourne et sa version.

![L'agent à l'état En ligne](/blog/media/2026-09-08-impresoras-red-local-agente/05-en-linea-fr.png)

Sinon, c'est presque toujours l'une de ces trois causes : le manifeste **collé à moitié**, l'ordinateur **sans internet** ou un **pare-feu** qui bloque la sortie. Pour voir ce que l'agent lui-même remonte, ouvrez-le avec **Modifier** : l'onglet **État** donne le détail.

## Vos imprimantes apparaissent toutes seules

À partir de là, l'agent **cherche les imprimantes sur votre réseau** de lui-même toutes les 15 minutes. Quand il en trouve une, un avis s'affiche au-dessus des onglets et vous la voyez en bas de **Imprimantes sur le réseau local**, avec sa marque et son modèle. C'est vous qui décidez :

- **Ajouter** : vous l'enregistrez et elle commence à envoyer ses informations.
- **Ignorer** : elle n'est pas à vous ou vous ne la voulez pas ici.

![Une imprimante détectée par l'agent, avec les boutons Ignorer et Ajouter, et au-dessus Chercher maintenant et Ajouter par IP](/blog/media/2026-09-08-impresoras-red-local-agente/06-encontradas-fr.png)

Si vous venez d'allumer une machine et ne voulez pas attendre, cliquez sur **Chercher maintenant**. Si une imprimante va vous demander un code, sa ligne vous prévient (« demandera le code d'accès »), pour que vous l'ayez sous la main.

## Si l'une n'apparaît pas, ajoutez-la vous-même

Qu'une imprimante n'apparaisse pas toute seule est **normal** dans deux cas :

- **Elle est sur un autre réseau.** Les annonces des imprimantes ne passent pas d'un réseau à l'autre.
- **L'agent tourne sous Windows ou Mac.** Docker y tourne dans une machine virtuelle.

Vous n'y perdez rien : vous l'ajoutez vous-même et elle fonctionne exactement pareil, avec la caméra et les commandes si cette machine en dispose. Cliquez sur **Ajouter par IP**. Il y a trois étapes.

### 1. Choisissez la marque

Choisissez la marque de votre imprimante : chacune a sa carte, et celles qui ont un logo viennent en premier. Inutile de savoir comment votre machine communique : nous nous en chargeons. Si vous choisissez **Elegoo**, nous vous demandons **Quelle Elegoo avez-vous ?**, car elle a plusieurs familles. **Klipper** et **Autre imprimante résine (ChituBox)** sont à la fin, dans **Génériques**, pour une machine montée par vos soins ou une marque absente de la liste.

Si vous doutez que votre modèle soit pris en charge, vous avez **Vous hésitez ? Consultez la liste des compatibles** en bas ; et si votre imprimante n'y est pas, dites-le-nous sur Discord.

![La première étape d'Ajouter une imprimante par IP : les marques que vous pouvez connecter](/blog/media/2026-09-08-impresoras-red-local-agente/08-anadir-marca-fr.png)

### 2. Saisissez ses informations

Seulement l'essentiel :

- **Quel agent la connecte ?**, si vous en avez plusieurs. Vous ne pouvez choisir qu'un agent en ligne.
- **IP de l’imprimante**. Vous la trouverez sur l'écran de l'imprimante (Paramètres → Réseau) ou dans votre routeur.
- **Le code de l'imprimante**, si cette marque en demande un. Le champ porte le nom que lui donne le fabricant : sur une Bambu, **Code d'accès LAN**.
- **Nom**, si vous voulez lui en donner un à vous. C'est facultatif.

Vous **ne saisissez ni le modèle ni le numéro de série** : l'agent les demande à l'imprimante. Les champs obligatoires portent un **astérisque rouge** et sont encadrés de rouge tant qu'ils sont vides. En bas, l'encadré **N'oubliez pas** vous dit ce qu'il faut préparer sur cette marque avant de connecter.

![La deuxième étape : l'agent, l'IP, le code d'accès LAN obligatoire et l'encadré N'oubliez pas](/blog/media/2026-09-08-impresoras-red-local-agente/09-anadir-datos-fr.png)

### 3. Connectez

Cliquez sur **Connecter** et suivez l'avancement : l'agent reçoit la demande, cherche l'imprimante à cette adresse et s'y connecte. Une fois terminé, vous verrez **« Connectée. Elle figure maintenant dans votre liste d’imprimantes. »**

![La troisième étape : l'imprimante connectée et déjà dans la liste](/blog/media/2026-09-08-impresoras-red-local-agente/10-anadir-conexion-fr.png)

Si quelque chose ne va pas, nous vous le disons **avec des mots simples** : ce qui se passe et ce qu'il faut vérifier (rien ne répond à cette IP, l'imprimante refuse le code…). Avec **Retour**, vous corrigez l'information et vous réessayez. Le message d'origine de l'imprimante reste replié sous **Voir le détail technique** : si vous nous écrivez, copiez-le-nous, nous trouverons plus vite.

:::info 💡 Réservez-lui son IP dans la box
Si la box change l'adresse d'une imprimante, nous la retrouvons automatiquement, mais elle sera hors ligne un moment. Lui réserver son adresse évite ce trou. C'est un réglage de la box, pas de BolloPrint.
:::

## Ce que demande chaque marque

C'est là que se posent le plus de questions. C'est ce que vous rappelle l'étape 2, en résumé :

| Marque | Ce que vous devez faire sur la machine | Caméra | Pouvez-vous mettre en pause et annuler ? |
|---|---|---|---|
| **Bambu Lab** | Activer le **Mode LAN** sur son écran (Paramètres → Réseau) et utiliser le **code d'accès LAN** qu'elle affiche | Oui | Oui, si vous activez aussi le **Mode développeur** |
| **Prusa** (bêta : MK4, MK3.5, MK3.9, MINI, XL, CORE One) | Activer **PrusaLink** et utiliser le **mot de passe** qu'elle affiche (pas celui de Prusa Connect) | Pas encore | Oui |
| **Elegoo** (Saturn, Mars, Jupiter, Centauri Carbon) et **autres imprimantes résine (ChituBox)** | Rien, elles ne demandent pas de mot de passe | Sur les modèles qui en ont une | Oui |
| **Elegoo Centauri Carbon 2** | Rien ; seulement si vous avez défini un code sur son écran, saisissez-le | Oui | Pas encore |
| **Anycubic** (bêta : Kobra 3, Kobra S1, Kobra 4, Kobra X) | Activer le **Mode LAN** (Paramètres → Réseau). L'imprimante n'utilise alors plus le cloud ni l'application Anycubic | Pas encore | Pas encore |
| **FlashForge** (bêta : Adventurer 5M, 5M Pro, AD5X, Creator 5) | Activer **LAN Only** et utiliser le code de vérification de son menu réseau | Oui | Pas encore |
| **Snapmaker** (U1) | Rien | Oui | Oui |
| **Klipper** (QIDI, Sovol, Voron, RatRig, Creality K1…) | En général rien : seulement si vous avez défini une clé d'API dans Moonraker | Oui, si vous avez une webcam sur votre Klipper | Oui |

:::warning ⚠️ Bambu Lab : le code d'accès change
Chaque fois que vous activez ou désactivez le Mode LAN ou le Mode développeur, Bambu **génère un nouveau code**. Si une Bambu qui fonctionnait bien cesse soudain de se connecter, c'est la cause neuf fois sur dix : regardez à nouveau le code sur son écran et mettez-le à jour dans BolloPrint. Et gardez en tête que le **Mode développeur** la déconnecte de Bambu Cloud : à partir de là, vous ne la verrez plus que via l'agent.
:::

:::info 💡 Vous ne trouvez pas votre modèle dans le tableau ?
Consultez les [imprimantes compatibles](/help/impresoras-compatibles). Si elle tourne sous **Klipper** (n'importe quelle machine montée par vous-même ou modifiée), elle est prise en charge, même si la marque n'apparaît sur aucune liste.
:::

## Ce que vous apporte l'agent local

Une fois l'agent en marche, vous obtenez :

- **Presque toutes les marques** : Bambu Lab, Prusa, Elegoo, Anycubic, FlashForge, Snapmaker et tout ce qui tourne sous Klipper. Le cloud ne le propose pas : il n'existe que pour Bambu Lab.
- **La caméra** : en direct quand vous avez la page ouverte, une photo quand vous voulez et une photo finale conservée dans l'historique de chaque impression. Ce n'est pas de la vidéosurveillance : rien n'est enregistré.
- **Les commandes** : mettre en pause, reprendre et annuler depuis BolloPrint, sans vous déplacer jusqu'à la machine, sur celles qui le permettent (voir le tableau ci-dessus). Sur Bambu Lab, avec l'imprimante en **Mode LAN** et en **Mode développeur**.
- **La résistance aux coupures d'internet** : si votre ligne tombe, l'agent **continue de lire les imprimantes et garde une trace de ce qui se passe**. Quand la connexion revient, il envoie tout, et vous ne perdez pas ces heures d'historique.
- **L'indépendance vis-à-vis du fabricant**, et du fait que son cloud continue de fonctionner.

Ce qu'aucune voie ne permet, c'est d'**envoyer des travaux à imprimer** : le fichier, vous continuez à l'envoyer depuis votre trancheur.

## Questions fréquentes

Les questions qu'on nous pose le plus souvent.

### Dois-je ouvrir des ports sur la box ?

Non. Ni ports, ni IP fixe, ni règles de pare-feu. Il fonctionne derrière une box domestique ordinaire.

### Faut-il un agent par imprimante ?

Non. **Un seul gère tout le parc.** Il n'est utile d'en avoir plusieurs que si vous avez deux locaux ou deux réseaux séparés. Dans ce cas, **Ajouter par IP** vous demande lequel connecte l'imprimante.

### Que se passe-t-il si j'éteins l'ordinateur ou si une nouvelle version sort ?

Quand vous le rallumez, l'agent revient tout seul. Il se met aussi à jour tout seul : quand une nouvelle version sort, il la télécharge et redémarre avec, sans que vous ayez à toucher au manifeste. Vous n'aurez à intervenir que si nous vous prévenons à l'écran.

### Pourquoi ne puis-je pas cliquer sur « Ajouter par IP » ?

Parce qu'aucun de vos agents n'est connecté, et le texte sous le bouton vous l'indique. Si vous ne l'avez pas encore installé, utilisez **Installer** sur sa ligne ; s'il fonctionnait déjà, vérifiez que l'ordinateur est allumé et connecté à internet.

:::info 💡 Besoin d'aide ?
Écrivez-nous depuis la [page de contact](/contact) ou ouvrez un fil sur [notre Discord](/help/soporte-por-discord). Dites-nous quelles imprimantes vous avez, et nous vous dirons exactement quoi faire avec chacune.
:::

Profitez de tout votre parc sous les yeux, où que vous soyez.

![Bollo, la mascotte de BolloPrint, avec des lunettes d'atelier, devant une ferme d'imprimantes 3D en plein travail](/blog/media/2026-09-08-impresoras-red-local-agente/07-bollo.webp "60%")

## Documentation associée

- [Connecter des imprimantes](/help/conectar-impresoras) : les deux voies et celle qui vous convient
- [L'agent local](/help/el-agente-local) : la référence complète
- [Déployer l'agent](/help/desplegar-el-agente) : le détail technique, si vous en avez besoin
- [Types de connexion](/help/tipos-de-conexion) : ce que permet chaque famille d'imprimantes
- [Imprimantes compatibles](/help/impresoras-compatibles) : cherchez votre modèle ici
