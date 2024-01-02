---
title: Collecte de documents volumineux à l’aide de GigaSign
description: Gigasign vous permet d’envoyer, de collecter et de suivre des documents pour signature à des milliers de personnes en même temps
feature: Workflow
role: Developer
level: Intermediate
jira: KT-6626
topic-revisit: Integrations
thumbnail: 328113.jpg
exl-id: a59eab61-fe61-45c6-8137-f074e1f2b3ed
source-git-commit: 84aa3c18e0da0d4e5c83130c4e3303407ebf784a
workflow-type: tm+mt
source-wordcount: '244'
ht-degree: 1%

---

# Collecte de documents volumineux à l’aide de GigaSign

Gigasign vous permet d’envoyer, de collecter et de suivre des documents pour signature à des milliers de personnes en même temps. Il est conçu pour les communications en masse avec vos employés et clients. Il prend en charge jusqu’à 2 500 destinataires par envoi en masse. GigaSign utilise l’API Acrobat Sign pour fournir les mêmes fonctionnalités que MegaSign. GigaSign prend en charge plusieurs signataires, groupes de destinataires, rôles des destinataires, noms des accords, copie carbone, etc.

>[!VIDEO](https://video.tv.adobe.com/v/328113?quality=12&learn=on&hidetitle=true)

## Téléchargement et installation de l’application GigaSign

[Télécharger le fichier zip GigaSign](https://acrobat.adobe.com/link/track?uri=urn:aaid:scds:US:d1a3f4f2-0f7b-466f-9785-81dff2217776)

[Lien de téléchargement Java 1.8 (uniquement si nécessaire)](https://www.oracle.com/java/technologies/javase/javase8-archive-downloads.html) {target="_blank"}

[Adresses IP vers la liste blanche (uniquement si nécessaire)](https://helpx.adobe.com/fr/sign/system-requirements.html#IPs){target="_blank"}

## Instructions de configuration de base

1. Connectez-vous à votre compte Acrobat Sign.

1. Cliquez sur **[!UICONTROL Groupe]** ou **[!UICONTROL Compte]**, selon ce que vous voyez en haut.

1. Tapez « Jetons d’accès » dans le champ de recherche sur le côté gauche de l’écran.

1. Appuyez sur l’icône « + » sur le côté droit.

1. Créez une clé avec les portées nécessaires (User_Read, Agreement_Read, Agreement_Write, Agreement_Send, Library_Read).

1. Double-cliquez sur la touche que vous avez créée et copiez le texte COMPLET (il sort de l’écran à droite, assurez-vous donc de l’obtenir entièrement).

1. Ouvrez GigaSign.

1. Cliquez sur le bouton **[!UICONTROL Paramètres]** en haut à droite.

1. Collez la clé d’intégration sur la première ligne.

1. Entrez l’adresse e-mail du compte utilisé pour créer cette clé à la deuxième ligne.

1. Cliquez sur **[!UICONTROL Envoyer]**.
