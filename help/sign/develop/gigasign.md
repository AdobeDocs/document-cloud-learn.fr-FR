---
title: Rassemblement de documents en grand volume à l’aide de GigaSign
description: Gigasign vous permet d’envoyer, de collecter et de suivre des documents pour signature à des milliers de personnes en même temps.
role: User, Admin
product: adobe sign
level: Intermediate
topic-revisit: Integrations
thumbnail: 328113.jpg
exl-id: a59eab61-fe61-45c6-8137-f074e1f2b3ed
source-git-commit: 7d82422e442cbbed9420050c30ca70821e9a2cdd
workflow-type: tm+mt
source-wordcount: '268'
ht-degree: 4%

---

# Rassemblement de documents volumineux à l’aide de GigaSign

Gigasign vous permet d’envoyer, de collecter et de suivre des documents pour signature à des milliers de personnes en même temps. Il est conçu pour les communications en grand volume avec vos employés et vos clients, prenant en charge jusqu’à 2 500 destinataires par envoi en bloc. GigaSign utilise l’API Adobe Sign pour fournir les mêmes fonctionnalités que MegaSign et prend en charge plusieurs signataires, groupes de destinataires, rôles de destinataire, noms d’accord, copie carbone, etc.

>[!VIDEO](https://video.tv.adobe.com/v/328113?hidetitle=true)

## Téléchargement et installation de l’application GigaSign

[Télécharger le fichier Zip GigaSign](https://documentcloud.adobe.com/link/track?uri=urn:aaid:scds:US:8975dbca-98d5-4e66-9164-d21163c91c7f)

[Lien de téléchargement Java 1.8 (uniquement si nécessaire)](https://www.oracle.com/java/technologies/javase/javase8-archive-downloads.html) {target=&quot;_blank&quot;}

[Adresses IP de la liste blanche (uniquement si nécessaire)](https://helpx.adobe.com/fr/sign/system-requirements.html#IPs){target=&quot;_blank&quot;}

## Instructions de configuration de base

1. Connectez-vous à votre compte Adobe Sign.

1. Cliquez sur **[!UICONTROL Groupe]** ou **[!UICONTROL Compte]**, selon ce que vous voyez en haut.

1. Saisissez &quot;Jetons d’accès&quot; dans le champ de recherche situé à gauche de l’écran.

1. Appuyez sur l’icône &quot;+&quot; sur le côté droit.

1. Créez une clé avec les domaines nécessaires (User_Read, Agreement_Read, Agreement_Write, Agreement_Send, Library_Read).

1. Double-cliquez sur la touche que vous avez créée et copiez le texte PLEIN (il s&#39;affiche à droite pour que vous puissiez tout obtenir).

1. Ouvrez GigaSign.

1. Cliquez sur l’icône **[!UICONTROL Paramètres]** en haut à droite.

1. Collez la clé d’intégration sur la première ligne.

1. Entrez l’adresse électronique du compte utilisé pour créer cette clé sur la deuxième ligne.

1. Cliquez sur **[!UICONTROL Envoyer]**.
