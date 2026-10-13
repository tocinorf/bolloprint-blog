---
slug: connect-bambu-lab-printers-cloud
title: "Connectez vos imprimantes Bambu Lab à BolloPrint en cinq minutes"
description: Sans rien installer. Vous connectez votre compte Bambu Lab, vous confirmez un code et vos imprimantes apparaissent toutes seules, avec ce qu'elles impriment et tout leur historique.
date: 2026-10-12
tags: [tutoriels]
cover: 01-portada.webp
---

Si vous avez plusieurs Bambu en service, vous connaissez sans doute la routine : pour savoir où elles en sont, vous allez voir l'écran de chacune. La première a-t-elle terminé ? Reste-t-il du matériau dans la deuxième ? Combien d'heures avez-vous imprimées ce mois-ci ?

Vous pouvez avoir tout cela sur un seul écran, et **sans rien installer**. Vous connectez votre compte Bambu Lab à BolloPrint et vos imprimantes apparaissent toutes seules. Comptez environ cinq minutes.

::animation{id="bambu-cloud"}

## Ce que vous verrez de chaque imprimante

En temps réel et sans rien toucher :

- si elle est allumée et connectée ;
- ce qu'elle imprime, le **pourcentage** atteint et ce qu'il lui reste ;
- les températures de la buse et du plateau ;
- les **matériaux** chargés, bac par bac, si vous avez un AMS ;
- les avertissements de la machine elle-même.

Et ce qui se remarque le plus en fin de mois : **chaque impression est enregistrée**, avec sa durée, son matériau et son coût. Vous n'avez rien à noter.

![La fiche d'une imprimante en cours d'impression, avec la progression et les températures](/blog/media/2026-09-08-impresoras-por-la-nube/06-ficha-impresora.png "42%")

## Ce dont vous avez besoin

Avant de commencer, gardez ces trois éléments à portée de main :

- Un accès à BolloPrint en tant que **Propriétaire** ou **Admin**. Avec un autre rôle, cet écran ne s'affiche pas.
- L'**e-mail et le mot de passe** de votre compte Bambu Lab.
- La **boîte mail** de ce compte ouverte : Bambu va vous envoyer un code.

:::warning ⚠️ Si vous vous connectez à Bambu avec Google, Apple ou Facebook
BolloPrint a besoin de l'**e-mail et du mot de passe** du compte. Si vous n'avez jamais défini de mot de passe parce que vous utilisez toujours « Continuer avec Google », créez-en un d'abord sur le site de Bambu Lab, puis revenez.
:::

## Ouvrez l'écran des imprimantes

Tout se passe au même endroit : **Paramètres → Imprimantes**. Vous y verrez trois onglets :

- **Imprimantes** : la liste de toutes vos machines, d'où qu'elles viennent.
- **Agent local** : pour les connecter via votre propre réseau. Nous l'expliquons dans [un autre article](/blog/connect-printers-local-network-agent).
- **Bambu Cloud** : celui dont vous avez besoin maintenant.

Ouvrez **Bambu Cloud**.

![L'écran Paramètres → Imprimantes avec ses trois onglets](/blog/media/2026-09-08-impresoras-por-la-nube/02-tres-pestanas.png)

## Saisissez l'e-mail et le mot de passe Bambu

Utilisez ceux de votre compte Bambu Lab (cet e-mail-là, pas un autre des vôtres), puis cliquez sur **Se connecter à BambuLab**.

![Le formulaire Bambu Cloud, avec l'e-mail du compte saisi et le mot de passe encore à saisir](/blog/media/2026-09-08-impresoras-por-la-nube/03-email-password.png)

:::info 💡 Votre mot de passe n'est pas enregistré
Il reste **uniquement dans votre navigateur**, et seulement jusqu'à la fin de la vérification.
:::

## Confirmez le code reçu par e-mail

Bambu vous enverra un **code à 6 chiffres** depuis `noreply@bambulab.com`. Si vous ne le voyez pas, **regardez dans le dossier des spams** : il y atterrit souvent. Saisissez-le sur ce même écran et cliquez sur **Vérifier et connecter**.

![Le champ du code à 6 chiffres et le bouton Vérifier et connecter](/blog/media/2026-09-08-impresoras-por-la-nube/04-codigo-verificacion.png)

Deux détails vous éviteront une deuxième tentative :

- Le code **expire au bout d'environ 5 minutes**. S'il a expiré, cliquez sur **Renvoyer le code**.
- Vous pouvez le **coller tel qu'il arrive** : les espaces et les tirets sont supprimés automatiquement.

Une fois le code accepté, vous verrez **Compte vérifié et connecté**.

## Vos imprimantes sont déjà là

Inutile de les enregistrer une par une : **toutes les imprimantes de ce compte apparaissent toutes seules** dans l'onglet **Imprimantes**, chacune avec son nom et son numéro de série.

![La liste des imprimantes avec les machines Bambu qui viennent d'apparaître](/blog/media/2026-09-08-impresoras-por-la-nube/05-impresoras-aparecidas.png)

En haut, vous verrez un compteur du type `3 / 6 actives` : ce sont les imprimantes incluses dans votre forfait. L'interrupteur de chaque ligne vous permet d'activer ou de désactiver celles que vous voulez. Une imprimante désactivée ne compte pas dans la limite, mais **conserve tout son historique**. Et si vous connectez un parc entier et qu'il n'y a pas de place pour toutes, celles qui sont en trop arrivent désactivées au lieu de dépasser la limite de votre forfait.

## Ce que vous ne pouvez pas faire via le cloud

Mieux vaut le savoir dès le départ, pour ne pas chercher des options qui n'existent pas :

- **C'est en lecture seule.** Via le cloud, impossible de mettre en pause, de reprendre ou d'annuler depuis BolloPrint : Bambu n'accepte ces ordres que via votre réseau local, avec l'imprimante dans un mode précis. Nous y revenons à la fin.
- **Pas de caméra.** Vous voyez en revanche l'image du tranchage du travail, qui est un aperçu, pas ce qui se passe à l'intérieur de la machine.
- **Cela dépend de deux connexions internet**, la vôtre et celle de Bambu. Si l'une des deux tombe, l'imprimante apparaît déconnectée alors qu'elle imprime normalement.
- **La session expire de temps en temps** et il faut reconnecter le compte. Nous vous prévenons à l'écran.

Et un point qui vaut pour tous les modes de connexion : **BolloPrint n'envoie pas de travaux à imprimer**. Vous continuez à envoyer le fichier depuis votre trancheur ; BolloPrint lit ce que fait la machine et l'enregistre.

## Problèmes fréquents

### Pourquoi Bambu indique-t-il un mot de passe incorrect alors que c'est le bon ?

C'est le problème le plus courant. Le message **« Compte ou mot de passe Bambu Lab incorrect »** apparaît presque toujours avec un mot de passe tout juste créé et encore jamais utilisé : la vérification de l'e-mail du compte est en attente, et Bambu ne l'indique pas. Connectez-vous **une fois** sur le site de Bambu avec cet e-mail et ce mot de passe, faites ce qui vous est demandé, puis réessayez.

### Et si vous vous connectez à Bambu avec Google ou Apple ?

Cette méthode ne fonctionne pas ici. Créez un mot de passe sur le site de Bambu Lab et utilisez l'e-mail avec ce mot de passe.

### Pourquoi est-il indiqué qu'aucun compte n'existe avec cet e-mail ?

Si vous voyez **« Aucun compte Bambu Lab n'existe avec cet email »**, ce n'est pas l'e-mail de votre compte Bambu. Vérifiez avec lequel vous vous connectez dans son application.

### Que faire si une vérification en deux étapes est demandée ?

Vous devrez la désactiver dans votre compte Bambu pour pouvoir le connecter.

### Que faire si le code n'arrive pas ou s'il est refusé ?

S'il n'arrive pas, regardez dans le dossier des spams et cliquez sur **Renvoyer le code**. S'il est refusé, il a très probablement expiré : demandez-en un autre et collez-le en entier.

## Pour aller plus loin : l'agent local

Le cloud vous montre toutes les informations, mais ne vous permet pas d'agir sur les imprimantes, et il n'existe que pour Bambu Lab. Si vous avez besoin de plus, la solution est l'**agent local** : un petit programme que vous installez sur un ordinateur de votre atelier et qui communique avec les imprimantes via votre propre réseau. Un seul suffit pour tout le parc, et il vous apporte :

- **presque toutes les marques** : Prusa, Elegoo, Klipper, QIDI, Sovol, FlashForge, Voron… ;
- **la caméra**, en direct et avec une photo finale conservée à chaque impression ;
- **mettre en pause, reprendre et annuler** depuis BolloPrint, sans vous déplacer jusqu'à la machine ;
- **la résistance aux coupures d'internet** : il continue de lire vos imprimantes et transmet tout au retour de la connexion.

:::info 💡 Pour envoyer des ordres à une Bambu
L'imprimante doit être en **Mode LAN** et en **Mode développeur**. Les deux s'activent sur son écran.
:::

Nous l'expliquons pas à pas dans [connecter vos imprimantes via votre propre réseau](/blog/connect-printers-local-network-agent).

Pour toute question, écrivez-nous depuis la [page de contact](/contact) ou sur [notre Discord](/help/soporte-por-discord).

Profitez de toutes vos imprimantes réunies sur un seul écran.

![Bollo, la mascotte de BolloPrint, avec des lunettes d'atelier, rêvant d'une imprimante 3D](/blog/media/2026-09-08-impresoras-por-la-nube/07-bollo.webp "60%")

## Documentation associée

- [Connecter des imprimantes](/help/conectar-impresoras) : les deux façons de le faire et celle qui vous convient
- [Imprimantes via le cloud](/help/impresoras-por-la-nube) : la référence complète de cet écran
- [Imprimantes compatibles](/help/impresoras-compatibles) : cherchez votre modèle ici
- [Types de connexion](/help/tipos-de-conexion) : ce que permet chaque type d'imprimante
