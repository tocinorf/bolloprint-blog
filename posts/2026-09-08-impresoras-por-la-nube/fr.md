---
slug: connect-bambu-lab-printers-cloud
title: "Connectez vos imprimantes Bambu Lab à BolloPrint en cinq minutes"
description: Sans rien installer. Vous connectez votre compte Bambu et vos machines apparaissent toutes seules, avec ce qu'elles impriment et tout leur historique.
date: 2026-09-08
updated: 2026-10-12
tags: [tutoriels]
cover: 01-portada.webp
draft: true
---

Vous avez trois Bambu qui tournent et, pour savoir où elles en sont, vous vous levez et vous allez regarder l'écran de chacune. La première a-t-elle terminé ? Reste-t-il du matériau dans la deuxième ? Combien d'heures avez-vous imprimées ce mois-ci ?

Il existe un moyen de tout voir depuis un seul écran, et **il n'y a rien à installer**. Vous connectez votre compte Bambu Lab à BolloPrint et vos machines apparaissent toutes seules. Cinq minutes.

::animation{id="bambu-cloud"}

## Voici ce que vous allez avoir

Pour chaque imprimante, en direct et sans rien toucher :

- si elle est allumée et connectée ;
- ce qu'elle imprime, le **pourcentage** et ce qu'il lui reste ;
- les températures de la buse et du plateau ;
- les **matériaux** chargés, bac par bac, si vous avez un AMS ;
- les avertissements de la machine elle-même.

Et en plus, ce qui change vraiment la donne en fin de mois : **chaque impression est enregistrée**, avec sa durée, son matériau et son coût. Sans rien noter à la main.

![La fiche d'une imprimante en cours d'impression, avec la progression et les températures](/blog/media/2026-09-08-impresoras-por-la-nube/06-ficha-impresora.png)

## Ce dont vous avez besoin

- Vous connecter à BolloPrint en tant que **Propriétaire** ou **Admin**. Avec un autre rôle, cet écran ne s'affiche pas.
- Votre compte **Bambu Lab**, avec son **e-mail et son mot de passe**.
- Pouvoir ouvrir la **boîte mail** de ce compte : Bambu va vous envoyer un code.

:::warning ⚠️ Si vous vous connectez à Bambu avec Google, Apple ou Facebook, cela ne fonctionnera pas
BolloPrint a besoin de l'**e-mail et du mot de passe** de votre compte Bambu. Si vous n'avez jamais défini de mot de passe parce que vous cliquez toujours sur « Continuer avec Google », créez-en un d'abord sur le site de Bambu Lab et revenez ici avec.
:::

## Étape 1 — Ouvrez l'écran des imprimantes

Allez dans **Paramètres → Imprimantes**. Vous verrez trois onglets :

- **Imprimantes** — la liste de toutes vos machines, d'où qu'elles viennent.
- **Agent local** — pour les connecter via votre réseau. Ça, c'est [un autre tutoriel](/blog/connect-printers-local-network-agent).
- **Bambu Cloud** — celui qui nous intéresse aujourd'hui.

Ouvrez **Bambu Cloud**.

![L'écran Paramètres → Imprimantes avec ses trois onglets](/blog/media/2026-09-08-impresoras-por-la-nube/02-tres-pestanas.png)

## Étape 2 — Saisissez votre e-mail et votre mot de passe Bambu

Ceux de votre compte Bambu Lab — cet e-mail-là, pas un autre des vôtres — puis cliquez sur **Se connecter à BambuLab**.

![Le formulaire Bambu Cloud avec l'e-mail et le mot de passe remplis](/blog/media/2026-09-08-impresoras-por-la-nube/03-email-password.png)

:::info 💡 Votre mot de passe n'est pas enregistré
Il reste **uniquement dans votre navigateur**, et seulement jusqu'à la fin de la vérification.
:::

## Étape 3 — Saisissez le code reçu par e-mail

Bambu vous envoie un **code à 6 chiffres** depuis `noreply@bambulab.com`. **Regardez aussi dans les spams** : il y atterrit plus souvent qu'il ne le devrait.

Saisissez les six chiffres sur ce même écran et cliquez sur **Vérifier et connecter**.

![Le champ du code à 6 chiffres et le bouton Vérifier et connecter](/blog/media/2026-09-08-impresoras-por-la-nube/04-codigo-verificacion.png)

Deux détails qui vous éviteront une deuxième tentative : **le code expire au bout d'environ 5 minutes** — si vous tardez, cliquez sur **Renvoyer le code** — et **collez-le en entier, tel quel** : s'il contient des espaces ou des tirets, ils sont nettoyés tout seuls.

Une fois le code accepté, vous verrez **Compte vérifié et connecté**.

## Étape 4 — Elles sont déjà là

Pas besoin d'enregistrer les imprimantes une par une. **Toutes les machines de ce compte apparaissent toutes seules** dans l'onglet **Imprimantes**, chacune avec son nom et son numéro de série.

![La liste des imprimantes avec les machines Bambu qui viennent d'apparaître](/blog/media/2026-09-08-impresoras-por-la-nube/05-impresoras-aparecidas.png)

En haut, il y a un compteur du type `3 / 6 actives` : les imprimantes incluses dans votre forfait. Avec l'interrupteur de chaque ligne, vous allumez et éteignez celles que vous voulez. Une imprimante éteinte ne compte pas pour la limite, mais **reste dans la liste avec tout son historique**.

Et si vous connectez une flotte entière et qu'il n'y a pas de place pour toutes, celles qui sont en trop entrent **désactivées** au lieu de casser votre forfait.

## Ce que vous NE pourrez PAS faire par ici

Mieux vaut le savoir maintenant que de chercher le bouton pendant une demi-heure :

- **C'est en lecture seule.** Via le cloud, impossible de mettre en pause, de reprendre ou d'annuler depuis BolloPrint : Bambu n'accepte ces ordres que via votre réseau local, et avec l'imprimante dans un mode spécial. On en parle à la fin.
- **Pas de caméra.** Via le cloud, elle n'arrive pas. Ce qui arrive, c'est l'image du tranchage du travail, c'est-à-dire l'aperçu, pas ce qui se passe à l'intérieur.
- **Cela dépend d'internet, deux fois :** du vôtre et de celui de Bambu. Si l'un des deux flanche, l'imprimante apparaît déconnectée alors qu'elle imprime parfaitement.
- **La session expire de temps en temps** et il faut reconnecter le compte. Nous vous prévenons à l'écran.

Et une règle qui vaut pour toutes les voies : **BolloPrint n'envoie pas de travaux à imprimer**. Le fichier, vous continuez à l'envoyer depuis votre trancheur. Ce que nous faisons, c'est lire ce que fait la machine et l'enregistrer.

## Si vous n'arrivez pas à vous connecter

| Ce que vous voyez | Ce que c'est en général |
|---|---|
| « Compte ou mot de passe Bambu Lab incorrect » alors que vous êtes sûr que c'est le bon | **C'est l'erreur qui fait perdre le plus de temps.** Si vous venez de créer ce mot de passe et ne l'avez jamais utilisé, le compte a la vérification de l'e-mail en attente, et Bambu ne vous le dit pas. Connectez-vous **une fois** sur le site de Bambu avec ces identifiants, faites ce qu'il vous demande, puis revenez. |
| « Compte ou mot de passe Bambu Lab incorrect » et vous vous connectez à Bambu avec Google ou Apple | Cette méthode ne fonctionne pas ici. Créez un mot de passe sur le site de Bambu. |
| « Aucun compte Bambu Lab n'existe avec cet email » | Ce n'est pas l'e-mail du compte Bambu. Regardez avec lequel vous vous connectez dans son application. |
| On vous parle de vérification en deux étapes | Il faut la désactiver chez Bambu pour pouvoir connecter le compte. |
| Le code n'arrive pas | Regardez dans les spams et cliquez sur **Renvoyer le code**. |
| Le code est refusé | Il a sans doute expiré. Demandez-en un autre et collez-le en entier. |

## Vous en voulez plus ? Essayez l'agent local

Le cloud vous montre tout, mais ne vous laisse toucher à rien, et il n'existe que pour Bambu Lab. Si vous voulez aller plus loin, ce qu'il vous faut, c'est l'**agent local** : un petit programme installé sur un ordinateur de votre atelier, qui parle aux imprimantes via votre propre réseau. Un seul suffit pour tout le parc, et il vous apporte :

- **presque toutes les marques** : Prusa, Elegoo, Klipper, QIDI, Sovol, FlashForge, Voron… ;
- **la caméra**, en direct pendant que vous la regardez, et une photo finale conservée à chaque impression ;
- **mettre en pause, reprendre et annuler** depuis BolloPrint, sans vous déplacer jusqu'à la machine ;
- et **il résiste aux coupures d'internet** : il continue de lire vos imprimantes et vous raconte tout au retour.

:::info 💡 Pour envoyer des ordres à une Bambu
L'imprimante doit être en **Mode LAN** et en **Mode développeur**. Les deux s'activent sur son écran. Attention : en Mode LAN, Bambu la déconnecte de son cloud ; à partir de là, BolloPrint la voit donc via l'agent. C'est toujours **la même imprimante**, avec son nom et tout son historique, et elle n'occupe **qu'une seule place** dans votre forfait.
:::

Vous avez tout, pas à pas, dans le tutoriel suivant : [connecter vos imprimantes via le réseau local](/blog/connect-printers-local-network-agent).

:::info 💡 Des questions ?
Écrivez-nous depuis la [page de contact](/contact) ou ouvrez un fil sur [notre Discord](/help/soporte-por-discord).
:::

## Documentation associée

- [Connecter des imprimantes](/help/conectar-impresoras) — les deux voies et celle qui vous convient
- [Imprimantes via le cloud](/help/impresoras-por-la-nube) — la référence complète de cet écran
- [Imprimantes compatibles](/help/impresoras-compatibles) — cherchez votre modèle ici
- [Types de connexion](/help/tipos-de-conexion) — ce que permet chaque famille d'imprimantes
