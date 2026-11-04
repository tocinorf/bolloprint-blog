---
slug: whats-new-september-november-2026
title: "BolloPrint se met à jour ! Les nouveautés qui vous aident dans votre atelier d'impression 3D"
description: "Toutes les nouveautés de BolloPrint du 14 septembre au 3 novembre 2026 : de l'agent local sans conteneurs aux factures légales et au tout nouveau Finances."
date: 2026-11-03
tags: [nouveautes]
cover: 01-bollo.webp
---

Depuis la mi-septembre, nous avons publié **41 mises à jour** de BolloPrint.
Certaines sont de grands changements importants. D'autres sont de petites
améliorations qui rendent votre quotidien plus confortable. Voici l'essentiel.

![En sept semaines : plus de 400 améliorations visibles, plus de 250 changements à l'écran, environ 190 bugs corrigés, 11 pays avec factures légales, 9 langues dans l'application et 102 imprimantes de 15 marques](/blog/media/2026-11-03-novedades-otono/02-cifras-fr.webp)

## Commençons par le plus intéressant : ce qui change votre façon de travailler

### 1. L'agent local, désormais sans rien connaître aux conteneurs

Nous savons que Docker peut être compliqué. Alors maintenant, c'est plus simple.
Installez l'agent sur ce que vous avez déjà : votre NAS, l'ordinateur de l'atelier
ou votre Home Assistant.

![Les logos de Synology, QNAP, Windows, Home Assistant et TrueNAS](/blog/media/2026-11-03-novedades-otono/03-agentes.webp)

| Où | Comment l'installer |
|---|---|
| **Synology et QNAP** | Téléchargez le paquet de votre NAS et installez-le manuellement depuis son centre de paquets. |
| **Windows** | Un installateur pour l'ordinateur de l'atelier. |
| **Home Assistant** | Le bouton « Ajouter à Home Assistant », et c'est tout. |
| **TrueNAS** | Collez dans ses applications la configuration que nous vous donnons. |

Ouvrez ensuite sa page et cliquez sur **« Associer à BolloPrint »** : le
propriétaire de l'atelier le confirme en un clic, sans copier de codes. Comme tous
les agents, il se met à jour tout seul. Docker et Kubernetes fonctionnent toujours
comme avant.

:::info
Vous le trouverez dans **Paramètres → Imprimantes → Agent local → « Nouvel agent »**.
[Comment installer l'agent](/help/el-agente-local)
:::

---

### 2. Vos imprimantes, mieux suivies et mieux comptées

- **Caméra en direct** et une photo finale de chaque impression dans son historique.
- **Chaque impression dit tout** : combien de temps elle a duré par rapport à l'estimation, chaque bobine avec son emplacement AMS, et le nom du modèle MakerWorld avec son lien.
- **La consommation réelle** : une impression échouée ou annulée n'est plus comptée en entier, et celles en résine enregistrent leurs millilitres.
- **Bambu Lab**, par le cloud sans mot de passe (votre e-mail et un code, et la session se renouvelle toute seule) et par le réseau local avec pause, reprise et annulation depuis BolloPrint, avec le mode développeur activé.
- **Ajouter par IP** est maintenant un assistant par marque ; plus besoin de savoir quel « protocole » parle votre machine.
- **L'agent local se met à jour tout seul**, jamais au milieu d'une impression, et chaque marque d'imprimante s'améliore de son côté.
- **Anycubic** (Kobra 3, S1, 4 et X) et **Creality** avec son firmware d'usine (K1, K2, Ender-3 V3 et Hi) arrivent, en bêta.

[Voir les imprimantes compatibles](/help/impresoras-compatibles)

---

### 3. Migration Smart

Importez clients, modèles, pièces, produits, commandes, devis et stock depuis les
dossiers et tableurs de votre ordinateur. BolloPrint lit ce que vous apportez et
vous propose comment l'intégrer ; vous le vérifiez avant que quoi que ce soit
n'entre, et en cas d'erreur, tout s'annule.

:::warning
Trois étapes : **Préparer · Comprendre · Migrer**. À partir de l'offre Pro, dans
Chrome ou Edge sur ordinateur. Avec Max et Business, si vous préférez, nous le
faisons pour vous.
:::

---

### 4. Des factures légales directement depuis la commande

Émettez la facture d'une commande sans quitter BolloPrint : avec sa numérotation,
sa taxe et votre logo. Avant de l'émettre, vous voyez la facture **exactement
telle qu'elle sortira**, et s'il manque quelque chose, nous vous disons quoi et où
le corriger.

- **Encaissements** : en attente, en retard ou payée, et un ZIP avec toutes vos
  factures.
- **Ventes sans TVA aux entreprises de l'UE**, avec la mention légale incluse et
  le numéro vérifié dans VIES.
- **Facture électronique allemande, QR-bill suisse** et factures dans une autre
  devise.

Déjà disponible dans 11 pays : Allemagne, Autriche, Chypre, Irlande, Luxembourg,
Pays-Bas, Pologne (via KSeF), Royaume-Uni, Suède, Suisse et Tchéquie.

:::warning
**Pas encore en Espagne** : elle arrivera quand nous aurons intégré VeriFactu, et
nous vous le dirons.
:::

[Voir les pays avec facturation](/help/paises-con-facturacion)

---

### 5. Des devis plus professionnels

- Le PDF du devis a **la forme d'une facture** : numéro, date, validité et, avec
  les offres payantes, votre propre logo.
- **Numérotation par année** (« 2026-00001 ») et sans trous, même si vous en
  supprimez un.
- **Remise** en € ou en %, qui apparaît comme une ligne de plus.
- Fiches client **Particulier ou Entreprise**, et des données fiscales plus
  simples.
- Création automatique d'une **commande à l'acceptation** du devis.

[Voir les devis](/help/presupuestos)

---

### 6. Un module Finances entièrement nouveau

Six onglets pour voir vos recettes, vos dépenses, vos taxes et votre bénéfice sur
la période de votre choix (mensuelle, trimestrielle, annuelle…).

Ajoutez vos dépenses avec notre agent IA et archivez les factures de vos
fournisseurs pour voir d'un coup d'œil où va votre argent. Suivez les taxes que
vous devez payer à chaque période.

:::info
**Le meilleur :** exportez ces données pour votre comptable dans un ZIP, en un seul clic.
:::

[Voir Finances](/help/financiero)

---

### 7. « Avis » : les problèmes de votre atelier, d'un coup d'œil

Une imprimante arrêtée sur une erreur, une boutique Etsy déconnectée, un paiement
qui n'est pas passé, le stockage presque plein… Nous vous prévenons uniquement de
ce qui demande vraiment une action, et chaque avis se ferme tout seul une fois le
problème réglé.

Vous pouvez mettre un avis en sourdine quelques jours ou pour toujours. Les
rouges, ceux qui bloquent quelque chose d'important, ne s'affichent en rouge qu'à
la personne qui peut les régler ; le reste de l'équipe les voit avec un
« Prévenez le propriétaire de l'atelier ».

---

### 8. Exportez votre inventaire, en Excel ou en PDF

Vous pouvez maintenant sortir une liste de ce que vous avez en stock : produits,
filaments, résines, fournitures…

| Format | Ce que vous obtenez |
|---|---|
| **Excel** | Un classeur avec un résumé et une feuille par section, avec filtres, totaux et les ruptures de stock en rouge. |
| **PDF** | Un document par section, avec votre logo, les photos de vos pièces et les couleurs de chaque bobine. |

Dans toutes les offres, et toujours avec toutes les lignes, pas seulement celles
affichées à l'écran.

---

### 9. Dans votre langue et à votre façon

BolloPrint parle désormais **🇵🇱 polonais, 🇳🇱 néerlandais et 🇨🇿 tchèque**. Cela
fait neuf langues au total.

Les dates et les montants s'écrivent **comme dans le pays de votre atelier**, à
l'écran, dans le PDF et dans les e-mails.

Et il y a un **nouvel Accueil** qui commence par l'urgent, avec « Créer » pour une
commande, un devis ou une création rapide, et « Premiers pas » avec sa barre de
progression.

## Et ce n'est pas tout, car les petits changements comptent aussi

| Où | Ce qui change |
|---|---|
| **Écrans** | Pendant un chargement, vous voyez sa forme, jamais une fausse liste vide ; en cas d'échec, un « Réessayer ». Les filtres sont les mêmes dans toutes les listes, sur mobile aussi. |
| **Envois de fichiers** | Chaque fichier affiche sa progression et reprend tout seul après une coupure réseau. Les fichiers tranchés peuvent peser jusqu'à 5 Go. |
| **Coûts** | 29 familles de filament et 9 de résine, avec des prix au kilo actualisés ; les marges, avec une barre de couleurs et un exemple. |
| **Clients** | La liste recherche et trie par n'importe quelle colonne, et un client sans alias s'affiche avec son nom complet. |
| **Etsy** | Importer une annonce est jusqu'à 8 fois plus rapide, les commandes avec deux variations passent, et avant de synchroniser une annonce, vous voyez valeur par valeur ce qui va changer. Paramètres → Marketplaces est maintenant une galerie, avec une page par boutique. |
| **Expéditions** | Des transporteurs et canaux de vente propres pour l'Autriche, l'Allemagne, le Royaume-Uni, la Pologne, la Tchéquie et les Pays-Bas. |
| **Manuel et blog** | Le manuel passe de 49 à 70 pages, dans les neuf langues, et le blog compte six nouveaux articles : de l'agent local au vrai coût d'une pièce. |
| **Au quotidien** | L'application supporte mieux les pics, revient toute seule après une coupure réseau, le traducteur de Chrome ne la casse plus, et une imprimante dont l'agent s'éteint en cours d'impression ne laisse plus d'impressions fantômes. |

## Où nous en sommes

| Quoi | Où et combien |
|---|---|
| 🧾 **Factures légales dans 11 pays** | 🇩🇪 Allemagne · 🇦🇹 Autriche · 🇨🇾 Chypre · 🇮🇪 Irlande · 🇱🇺 Luxembourg · 🇳🇱 Pays-Bas · 🇵🇱 Pologne · 🇬🇧 Royaume-Uni · 🇸🇪 Suède · 🇨🇭 Suisse · 🇨🇿 Tchéquie |
| 🌍 **Un atelier peut s'ouvrir depuis 53 pays d'Europe** | Avec sa devise, ses taxes et ses transporteurs. Paiement en euros, livres, złotys ou couronnes tchèques. |
| 🖨️ **102 modèles d'imprimantes, filament et résine** | Bambu Lab · Prusa · Elegoo · FlashForge · Anycubic · Creality · QIDI · Snapmaker · Voron · RatRig · Sovol · Artillery · Longer · Phrozen · Two Trees |
| ✅ **10 testées par nous sur de vraies machines** | Bambu Lab A1, A2L, P1P, P1S, P2S, X1 Carbon, X2D, H2C, H2D et H2S. |

## Il vous manque quelque chose ?

Dites-le-nous à
[info@bolloprint.com](mailto:info@bolloprint.com) ou sur notre
[canal Discord](/help/soporte-por-discord). Nous lisons tout. Une grande partie de
ce que vous voyez ici est née de messages comme le vôtre.

Si vous voulez plus de détails sur le fonctionnement, tout est dans le
[manuel](/help).

Et nous ne nous arrêtons pas : nous continuons à travailler chaque jour pour faire
de BolloPrint le meilleur outil pour votre atelier d'impression 3D.

![Bollo, la mascotte de BolloPrint, avec ses lunettes d'atelier et sa ceinture à outils, sur un plan](/blog/media/2026-11-03-novedades-otono/01-bollo.webp "60%")
