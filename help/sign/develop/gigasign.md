---
title: Rassembler des documents volumineux à l’aide de GigaSign
description: Gigasign permet d'envoyer, de collecter et de suivre des documents pour signature à des milliers de personnes simultanément
role: Developer
level: Intermediate
jira: KT-6626
topic-revisit: Integrations
thumbnail: 328113.jpg
exl-id: a59eab61-fe61-45c6-8137-f074e1f2b3ed
source-git-commit: ad54f7afa78b0fbb31eccf455723a8890cb92355
workflow-type: tm+mt
source-wordcount: '264'
ht-degree: 2%

---

# Rassemblez des documents volumineux à l’aide de GigaSign

Gigasign permet d&#39;envoyer, de collecter et de suivre des documents pour signature à des milliers de personnes simultanément. Conçu pour les communications en grand volume avec vos employés et clients, il prend en charge jusqu’à 2 500 destinataires par envoi en masse. GigaSign utilise l’API Acrobat Sign pour fournir les mêmes fonctionnalités que MegaSign. Elle prend en charge plusieurs signataires, groupes de destinataires, rôles des destinataires, noms des accords, copie carbone, etc.

>[!VIDEO](https://video.tv.adobe.com/v/328113?quality=12&learn=on&hidetitle=true)

## Téléchargement et installation de l’application GigaSign

[Télécharger le fichier zip GigaSign](https://documentcloud.adobe.com/link/track?uri=urn:aaid:scds:US:8975dbca-98d5-4e66-9164-d21163c91c7f)

[Lien de téléchargement de Java 1.8 (uniquement si nécessaire)](https://www.oracle.com/java/technologies/javase/javase8-archive-downloads.html) {target="_blank"}

[Adresses IP dans la liste blanche (uniquement si nécessaire)](https://helpx.adobe.com/fr/sign/system-requirements.html#IPs){target="_blank"}

## Instructions de configuration de base

1. Connectez-vous à votre compte Acrobat Sign.

1. Cliquez **[!UICONTROL Groupe]** ou **[!UICONTROL Compte]**, selon ce que vous voyez en haut.

1. Saisissez &quot;Jetons d’accès&quot; dans le champ de recherche sur le côté gauche de l’écran.

1. Appuyez sur l’icône &quot;+&quot; sur la droite.

1. Créez une clé avec les portées nécessaires (User_Read, Agreement_Read, Agreement_Write, Agreement_Send, Library_Read).

1. Double-cliquez sur la touche que vous avez créée et copiez le texte intégral (il sort de l&#39;écran à droite, alors assurez-vous de tout obtenir).

1. Ouvrez GigaSign.

1. Cliquez sur le bouton **[!UICONTROL Paramètres]** en haut à droite.

1. Collez la clé d’intégration sur la première ligne.

1. Saisissez l’adresse e-mail du compte utilisé pour créer cette clé sur la deuxième ligne.

1. Cliquez sur **[!UICONTROL Envoyer]**.
