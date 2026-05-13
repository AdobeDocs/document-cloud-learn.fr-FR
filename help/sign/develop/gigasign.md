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
TQID: https://experienceleague.adobe.com/62xUXPGJ-H5XyknrYgKSEErD-mW0zIZc-qxQJvzXgCM
product_v2:
  - id: b12c730b-5ddb-4a2d-ba42-da774988b909
  - id: c1c5fb98-9105-44ed-9df1-9e04d062a784
  - id: dc5cf79d-43c4-4731-bffa-1df5d7549cb1
  - id: e43347a8-f2c5-4aa4-8623-6f13875d7e3a
  - id: f002a92a-b99f-47a4-90c8-65e0e415bc7a
feature_v2:
  - id: a1028f9a-6dbc-4a4f-adf5-eb9f85a408a6
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2:
  - id: aa2f3246-cb95-4b30-8899-fdf7d73550cc
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
source-git-commit: d92345097c162b68b9d8405122534371c87c5f1a
workflow-type: tm+mt
source-wordcount: 331
ht-degree: 2%

---

# Collecte de documents volumineux à l’aide de GigaSign

Gigasign vous permet d’envoyer, de collecter et de suivre des documents pour signature à des milliers de personnes en même temps. Il est conçu pour les communications en masse avec vos employés et clients. Il prend en charge jusqu’à 2 500 destinataires par envoi en masse. GigaSign utilise l’API Acrobat Sign pour fournir les mêmes fonctionnalités que MegaSign. GigaSign prend en charge plusieurs signataires, groupes de destinataires, rôles des destinataires, noms des accords, copie carbone, etc.

>[!IMPORTANT]
>
>GigaSign n’est plus mis à jour vers la dernière version de Java ou d’Acrobat Sign et ne bénéficiera que d’une prise en charge limitée. Les fonctionnalités de GigaSign sont ajoutées au produit sous la fonctionnalité [Envoyer en masse](https://experienceleague.adobe.com/docs/document-cloud-learn/sign-learning-hub/admin-set-up/getting-started-admin/megasign.html ?). Utilisez Envoyer en masse pour tous les cas d’utilisation qui ne nécessitent pas explicitement l’utilisation de GigaSign.

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
