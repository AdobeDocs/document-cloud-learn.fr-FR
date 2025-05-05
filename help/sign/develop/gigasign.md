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
source-git-commit: ba9931920ab3bfb6ea38a92cac4a35da1d0295cd
workflow-type: tm+mt
source-wordcount: '298'
ht-degree: 1%

---

# Collecte de documents volumineux à l’aide de GigaSign

Gigasign vous permet d’envoyer, de collecter et de suivre des documents pour signature à des milliers de personnes en même temps. Il est conçu pour les communications en masse avec vos employés et clients. Il prend en charge jusqu’à 2 500 destinataires par envoi en masse. GigaSign utilise l’API Acrobat Sign pour fournir les mêmes fonctionnalités que MegaSign. GigaSign prend en charge plusieurs signataires, groupes de destinataires, rôles des destinataires, noms des accords, copie carbone, etc.

>[!IMPORTANT]
>
>GigaSign n’est plus mis à jour vers la dernière version de Java ou d’Acrobat Sign et ne bénéficiera que d’une prise en charge limitée. Les fonctionnalités de GigaSign sont ajoutées au produit sous la fonctionnalité [Envoyer en masse](https://experienceleague.adobe.com/docs/document-cloud-learn/sign-learning-hub/admin-set-up/getting-started-admin/megasign.html?). Utilisez Envoyer en masse pour tous les cas d’utilisation qui ne nécessitent pas explicitement l’utilisation de GigaSign.

>[!VIDEO](https://video.tv.adobe.com/v/328113?quality=12&learn=on&hidetitle=true)

## Téléchargement et installation de l’application GigaSign

[Télécharger le fichier zip GigaSign](https://acrobat.adobe.com/id/urn:aaid:sc:US:001cf62d-1cab-46c7-aa96-661ac8680206)

[Lien de téléchargement Java 1.8 (uniquement si nécessaire)](https://www.oracle.com/java/technologies/javase/javase8-archive-downloads.html){target="_blank"} 

[Adresses IP vers la liste blanche (uniquement si nécessaire)](https://helpx.adobe.com/fr/sign/system-requirements.html#IPs){target="_blank"}

## Instructions de configuration de base

1. Connectez-vous à votre compte Acrobat Sign.

1. Cliquez sur **[!UICONTROL Groupe]** ou **[!UICONTROL Compte]**, selon ce que vous voyez en haut.

1. Tapez « Jetons d’accès » dans le champ de recherche sur le côté gauche de l’écran.

1. Appuyez sur l’icône « + » sur le côté droit.

1. Créez une clé avec les portées nécessaires (User_Read, Agreement_Read, Agreement_Write, Agreement_Send, Library_Read).

1. Double-cliquez sur la touche que vous avez créée et copiez le texte COMPLET (il sort de l’écran à droite, assurez-vous donc de l’obtenir entièrement).

1. Ouvrez GigaSign.

1. Cliquez sur l&#39;icône **[!UICONTROL Paramètres]** en haut à droite.

1. Collez la clé d’intégration sur la première ligne.

1. Entrez l’adresse e-mail du compte utilisé pour créer cette clé à la deuxième ligne.

1. Cliquez sur **[!UICONTROL Envoyer]**.
