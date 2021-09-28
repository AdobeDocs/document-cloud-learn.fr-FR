---
title: Envoi de notifications à l’aide d’Adobe Sign pour Microsoft Dynamics 365 et Marketo
description: Découvrez comment envoyer un message texte, un courrier électronique ou une notification push afin de faire savoir au signataire qu’un accord est en cours d’envoi.
role: Admin
product: adobe sign
solution: Adobe Sign, Marketo, Document Cloud
level: Intermediate
topic-revisit: Integrations
thumbnail: KT-7249.jpg
exl-id: 2e0de48c-70bf-4dc5-8251-88e7399f588a
source-git-commit: bcddb0ee106239f2786debaed908b2a2ec5ce792
workflow-type: tm+mt
source-wordcount: '690'
ht-degree: 1%

---

# Envoi de notifications à l’aide d’Adobe Sign pour Microsoft Dynamics 365 et Marketo

Découvrez comment envoyer un message texte, un courrier électronique ou une notification Push pour informer le signataire qu’un accord est en cours d’envoi à l’aide d’Adobe Sign, Adobe Sign pour Microsoft Dynamic, Marketo et Marketo Microsoft Dynamics Sync. Pour envoyer des notifications depuis Marketo, vous devez d’abord acheter ou configurer une fonctionnalité de gestion des SMS Marketo. Cette procédure pas à pas utilise [Twilio SMS](https://launchpoint.marketo.com/twilio/twilio-sms-for-marketo/), mais d&#39;autres solutions Marketo SMS sont disponibles.

## Conditions préalables

1. Installez Marketo Microsoft Dynamics Sync.

   Les informations et le dernier module externe pour Microsoft Dynamics Sync sont disponibles [ici.](https://experienceleague.adobe.com/docs/marketo/using/product-docs/crm-sync/microsoft-dynamics/marketo-plugin-releases-for-microsoft-dynamics.html)

1. Installez Adobe Sign pour Microsoft Dynamics.

   Des informations sur ce module externe sont disponibles [ici.](https://helpx.adobe.com/ca/sign/using/microsoft-dynamics-integration-installation-guide.html)

## Recherche de l’objet personnalisé

Une fois les configurations Marketo Microsoft Dynamics Sync et Adobe Sign for Dynamics terminées, deux nouvelles options apparaissent dans le terminal d’administration Marketo.

![Administrateur](assets/adminTerminal.png)

* Cliquez sur **[!UICONTROL Synchronisation des entités Dynamics]**.

   La synchronisation doit être désactivée avant de synchroniser les entités personnalisées. Si c&#39;est votre première fois, cliquez sur **[!UICONTROL Synchroniser le schéma]**. Sinon, cliquez sur **[!UICONTROL Actualiser le schéma]**.

   ![Actualiser](assets/refreshSchema.png)

## Synchronisation de l’objet personnalisé

1. Sur le côté droit, recherchez les objets personnalisés basés sur [!UICONTROL Piste], [!UICONTROL Contact] et [!UICONTROL Compte].

   * **[!UICONTROL Activez]** Synchroniser pour les objets situés sous Piste si vous souhaitez déclencher lorsqu’une Piste est ajoutée à un accord dans Dynamics.

   * **[!UICONTROL Activez]** Synchroniser pour les objets sous Contact si vous souhaitez déclencher lorsqu’un Contact est ajouté à un accord dans Dynamics.

   * **[!UICONTROL Activez]** Synchroniser pour les objets sous Compte si vous souhaitez déclencher lorsqu’un compte est ajouté à un accord dans Dynamics.

   * **Activez** Synchroniser pour l’objet Accord sous le parent souhaité (Piste, Contact ou Compte).

   ![Objets personnalisés](assets/enableSyncDynamics.png)

1. Dans la nouvelle fenêtre, sélectionnez les propriétés souhaitées sous Accord.

   Activez les cases sous **[!UICONTROL Contrainte]** et **[!UICONTROL Déclencheur]** pour les exposer à vos activités marketing.

   ![Synchronisation personnalisée 1](assets/entitySync1.png)

   ![Synchronisation personnalisée 2](assets/entitySync2.png)

1. Réactivez la synchronisation après avoir activé la synchronisation sur les objets personnalisés.

   Revenez au [!UICONTROL terminal d&#39;administration], cliquez sur **[!UICONTROL Microsoft Dynamics]**, puis sur **[!UICONTROL Activer la synchronisation]**.

   ![Microsoft Dynamics ](assets/microsoftDynamics.png)

   ![Activer Global](assets/enableGlobalDynamics.png)

## Création du programme

1. Dans [!UICONTROL Activités marketing], cliquez avec le bouton droit de la souris sur **[!UICONTROL Activités marketing]** dans la barre de gauche, sélectionnez **[!UICONTROL Nouveau dossier de campagne]**, puis nommez-le.

   ![Nouveau dossier](assets/newFolder.png)

1. Cliquez avec le bouton droit de la souris sur le dossier créé, sélectionnez **[!UICONTROL Nouveau programme]**, puis donnez-lui un nom.

   Conservez tous les autres paramètres par défaut, puis cliquez sur **[!UICONTROL Créer]**.

   ![Nouveau programme 1](assets/newProgram1.png)

   ![Nouveau programme 2](assets/newProgram2.png)

## Configurer [!DNL Twilio] SMS

Assurez-vous d&#39;abord que vous disposez d&#39;un compte [!DNL Twilio] actif et achetez les fonctionnalités SMS dont vous avez besoin.

La configuration du webhook Marketo - [!DNL Twilio] SMS nécessite trois paramètres [!DNL Twilio] de votre compte.

* SID du compte
* Jeton de compte
* Numéro de téléphone Twilio

Récupérez ces paramètres de votre compte, puis ouvrez votre instance Marketo.

1. Cliquez sur **[!UICONTROL Admin]** en haut à droite.

   ![Administrateur](assets/adminTab.png)

1. Cliquez sur **[!UICONTROL Webhooks]**, puis sur **[!UICONTROL Nouveau Webhook]**.

   ![Webhooks](assets/webhooks.png)

1. Entrez un **[!UICONTROL nom de Webhook]** et une **[!UICONTROL description]**.

1. Entrez l&#39;URL suivante et veillez à remplacer `ACCOUNT_SID` et `AUTH_TOKEN` par vos informations d&#39;identification [!DNL Twilio].

   ```
   https://[ACCOUNT_SID]:[AUTH_TOKEN]@API.TWILIO.COM/2010-04-01/ACCOUNTS/[ACCOUNT_SID]/Messages.json
   ```

1. Sélectionnez **[!UICONTROL POST]** comme type de demande.

1. Entrez le **modèle** suivant et veillez à remplacer `MY_TWILIO_NUMBER` par votre [!DNL Twilio] numéro de téléphone et `YOUR_MESSAGE` par un message de votre choix.

   ```
   From=%2B1[MY_TWILIO_NUMBER]&To=%2B1{{lead.Mobile Phone Number:default=edit me}}&Body=[YOUR_MESSAGE]
   ```

1. Définissez le codage de jeton de demande **[!UICONTROL Request Token]** sur *Form/URL*.

1. Définissez le type de réponse sur *JSON*, puis cliquez sur **[!UICONTROL Enregistrer]**.

## Configuration du déclencheur Smart Campaign

1. Dans la section Activités marketing, cliquez avec le bouton droit de la souris sur le programme que vous avez créé, puis sélectionnez **[!UICONTROL Nouvelle campagne dynamique]**.

   ![Smart Campaign 1](assets/smartCampaign1.png)

1. Nommez-le, puis cliquez sur **[!UICONTROL Créer]**.

   ![Smart Campaign 2](assets/smartCampaign3.png)

   Plusieurs déclencheurs doivent être disponibles sous le dossier Microsoft.

1. Cliquez sur **[!UICONTROL Ajouter à l&#39;accord]** et faites-le glisser vers la **[!UICONTROL liste dynamique]**, puis ajoutez les contraintes que vous souhaitez appliquer au déclencheur.

   ![Ajouté à l’accord](assets/addedToAgreementDynamics.png)

## Configuration du flux de campagne dynamique

1. Cliquez sur l&#39;onglet **[!UICONTROL Flux]** dans la [!UICONTROL campagne dynamique].

   Recherchez et faites glisser l’enchaînement **Appeler Webhook** sur la zone de travail, puis sélectionnez le webhook que vous avez créé dans la section précédente.

   ![Appeler Webhook](assets/callWebhook.png)

1. Votre campagne d’avis par SMS pour les prospects qui sont ajoutés à un accord est maintenant configurée.
>[!TIP]
>
>Ce tutoriel fait partie du cours [Accélération des cycles de vente avec Adobe Sign pour Microsoft Dynamics et Marketo](https://experienceleague.adobe.com/?recommended=Sign-U-1-2021.1) disponible gratuitement sur Experience League !