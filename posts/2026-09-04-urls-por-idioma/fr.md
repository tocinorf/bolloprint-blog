---
slug: nouveautes-v0-14-une-url-par-langue
title: "Nouveautés v0.14 : chaque langue a désormais sa propre adresse"
description: BolloPrint.com parlait six langues mais Google n'en voyait qu'une. C'est corrigé — et cela a débloqué 174 pages du manuel au passage.
version: v0.14
date: 2026-09-04
updated: 2026-09-04
tags: [nouveautes]
draft: false
---

Jusqu'à cette version, `bolloprint.com/pricing` servait les six langues à **la
même adresse** : le serveur regardait la langue de votre navigateur et vous
servait la vôtre. Pour une personne, cela fonctionne très bien. Pour un moteur de
recherche, non.

Google explore sans langue préférée, il recevait donc toujours la version
anglaise — la seule qu'il indexait. Les cinq autres ne se positionnaient pas
mal : elles **n'existaient pas** pour le moteur, faute d'URL à laquelle se
référer.

## Ce qui change

Chaque langue reçoit sa propre adresse. L'anglais reste exactement où il était —
aucune URL existante ne change — et les cinq autres portent la langue dans le
chemin :

- `bolloprint.com/pricing` — anglais
- `bolloprint.com/es/pricing` — espagnol
- `bolloprint.com/fr/pricing` — français

Et ainsi de suite pour les six. Elles se déclarent mutuellement comme des
traductions, afin de ne pas se concurrencer : le moteur comprend qu'il s'agit de
la même page dans une autre langue et montre à chaque visiteur la sienne.

:::info
Si vous partagez un lien, il arrive désormais dans la langue où vous l'avez vu.
Auparavant, chacun l'ouvrait dans la sienne — pas toujours celle que vous
vouliez montrer.
:::

## Le gain le plus visible

Le manuel utilisateur compte 29 documents traduits en six langues — **174
pages** — qui jusqu'ici étaient indexées comme 29, en anglais. Ce contenu était
déjà écrit et traduit ; il lui manquait seulement une adresse.

## Et une chose qui ne change pas

Les pages de connexion et de compte se comportent exactement comme avant, en
détectant votre langue comme elles l'ont toujours fait. Elles ne sont pas
indexées : elles n'avaient donc pas besoin d'adresse propre.
