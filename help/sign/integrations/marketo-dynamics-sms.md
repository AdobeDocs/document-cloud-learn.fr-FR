---
title: Envoi de notifications à l’aide d’Acrobat Sign pour Microsoft Dynamics 365 et Marketo
description: Découvrez comment envoyer un SMS, un e-mail ou une notification Push pour informer le signataire qu’un accord est en cours d’envoi
feature: Integrations
role: Admin
solution: Acrobat Sign, Marketo, Document Cloud
level: Intermediate
topic: Integrations
topic-revisit: Integrations
jira: KT-7249
thumbnail: KT-7249.jpg
exl-id: 2e0de48c-70bf-4dc5-8251-88e7399f588a
source-git-commit: 452299b2b786beab9df7a5019da4f3840d9cdec9
workflow-type: tm+mt
source-wordcount: '690'
ht-degree: 1%

---

# Envoi de notifications à l’aide d’Acrobat Sign pour Microsoft Dynamics 365 et Marketo

Découvrez comment envoyer un SMS, un e-mail ou une notification Push pour informer le signataire qu’un accord est en cours d’envoi à l’aide d’Acrobat Sign, Acrobat Sign pour Microsoft Dynamic, Marketo et Marketo Microsoft Dynamics Sync. Pour envoyer des notifications à partir de Marketo, vous devez d’abord acheter ou configurer une fonction de gestion des SMS de Marketo. Cette procédure pas à pas utilise [Twilio SMS](https://launchpoint.marketo.com/twilio/twilio-sms-for-marketo/), mais d’autres solutions SMS de Marketo sont disponibles.

## Conditions préalables

1. Installez Marketo Microsoft Dynamics Sync.

   Des informations et le dernier plug-in pour Microsoft Dynamics Sync sont disponibles [ici.](https://experienceleague.adobe.com/docs/marketo/using/product-docs/crm-sync/microsoft-dynamics/marketo-plugin-releases-for-microsoft-dynamics.html)

1. Installez Acrobat Sign pour Microsoft Dynamics.

   Des informations sur ce plugin sont disponibles [ici.](https://helpx.adobe.com/ca/sign/using/microsoft-dynamics-integration-installation-guide.html)

## Recherche de l’objet personnalisé

Une fois les configurations Marketo Microsoft Dynamics Sync et Acrobat Sign pour Dynamics terminées, deux nouvelles options s’affichent dans le terminal d’administration de Marketo.

![Administrateur](assets/adminTerminal.png)

* Cliquez **[!UICONTROL Synchronisation des entités Dynamics]**.

  La synchronisation doit être désactivée avant de synchroniser les entités personnalisées. Cliquez **[!UICONTROL Synchroniser le schéma]** si c&#39;est votre première fois. Sinon, cliquez sur **[!UICONTROL Actualiser le schéma]**.

  ![Actualiser](assets/refreshSchema.png)

## Synchronisation de l’objet personnalisé

1. Sur le côté droit, localisez [!UICONTROL Prospect], [!UICONTROL Contact], et [!UICONTROL Compte]Objets personnalisés basés sur des balises.

   * **[!UICONTROL Activer la synchronisation]** pour les objets sous Piste si vous souhaitez déclencher lorsqu’une piste est ajoutée à un accord dans Dynamics.

   * **[!UICONTROL Activer la synchronisation]** pour les objets sous Contact si vous souhaitez déclencher lorsqu’un contact est ajouté à un accord dans Dynamics.

   * **[!UICONTROL Activer la synchronisation]** pour les objets sous Compte si vous souhaitez le déclencher lorsqu’un compte est ajouté à un accord dans Dynamics.

   * **Activer la synchronisation** pour l’objet Accord sous le parent souhaité (Prospect, Contact ou Compte).

   ![Objets personnalisés](assets/enableSyncDynamics.png)

1. Dans la nouvelle fenêtre, sélectionnez les propriétés de votre choix sous Accord.

   Cochez les cases sous **[!UICONTROL Contrainte]** et **[!UICONTROL Déclencheur]** pour les exposer à vos activités marketing.

   ![Synchronisation personnalisée 1](assets/entitySync1.png)

   ![Synchronisation personnalisée 2](assets/entitySync2.png)

1. Réactivez la synchronisation après avoir activé la synchronisation sur les objets personnalisés.

   Revenez à la page [!UICONTROL Admin Terminal], puis cliquez sur **[!UICONTROL Microsoft Dynamics]**, puis cliquez sur **[!UICONTROL Activer la synchronisation]**.

   ![Microsoft Dynamics ](assets/microsoftDynamics.png)

   ![Activer Global](assets/enableGlobalDynamics.png)

## Création du programme

1. Dans [!UICONTROL Activités marketing], cliquez avec le bouton droit **[!UICONTROL Activités marketing]** dans la barre de gauche, sélectionnez **[!UICONTROL Nouveau dossier de campagne]** et donnez-lui un nom.

   ![Nouveau dossier](assets/newFolder.png)

1. Cliquez avec le bouton droit de la souris sur le dossier créé, sélectionnez **[!UICONTROL Nouveau programme]** et donnez-lui un nom.

   Laissez le reste par défaut, puis cliquez sur **[!UICONTROL Créer]**.

   ![Nouveau programme 1](assets/newProgram1.png)

   ![Nouveau programme 2](assets/newProgram2.png)

## Configuration [!DNL Twilio] SMS

Assurez-vous d’abord d’avoir un [!DNL Twilio] et acheté les fonctionnalités SMS dont vous avez besoin.

Configuration de Marketo - [!DNL Twilio] Le webhook SMS en requiert trois [!DNL Twilio] paramètres de votre compte.

* SID du compte
* Jeton de compte
* Numéro de téléphone Twilio

Récupérez ces paramètres depuis votre compte, puis ouvrez votre instance Marketo.

1. Cliquez **[!UICONTROL Administrateur]** en haut à droite.

   ![Administrateur](assets/adminTab.png)

1. Cliquez **[!UICONTROL Webhooks]**, puis cliquez sur **[!UICONTROL Nouveau webhook]**.

   ![Webhooks](assets/webhooks.png)

1. Saisissez un **[!UICONTROL Nom du webhook]** et **[!UICONTROL Description]**.

1. Entrez l’URL suivante et veillez à remplacer la `ACCOUNT_SID` et `AUTH_TOKEN` avec votre [!DNL Twilio] identifiants.

   ```
   https://[ACCOUNT_SID]:[AUTH_TOKEN]@API.TWILIO.COM/2010-04-01/ACCOUNTS/[ACCOUNT_SID]/Messages.json
   ```

1. Sélectionner **[!UICONTROL POST]** comme type de demande.

1. Saisissez les informations suivantes : **Modèle** et assurez-vous de remplacer `MY_TWILIO_NUMBER` avec votre [!DNL Twilio] numéro de téléphone et `YOUR_MESSAGE` avec un message de votre choix.

   ```
   From=%2B1[MY_TWILIO_NUMBER]&To=%2B1{{lead.Mobile Phone Number:default=edit me}}&Body=[YOUR_MESSAGE]
   ```

1. Définissez la **[!UICONTROL Demander le codage de jeton]** à *Formulaire/URL*.

1. Définissez le type de réponse sur *JSON* puis cliquez sur **[!UICONTROL Enregistrer]**.

## Configuration du déclencheur Smart Campaign

1. Dans la section Activités marketing , cliquez avec le bouton droit sur le programme que vous avez créé, puis sélectionnez **[!UICONTROL Nouvelle campagne intelligente]**.

   ![Smart Campaign 1](assets/smartCampaign1.png)

1. Nommez-le, puis cliquez sur **[!UICONTROL Créer]**.

   ![Smart Campaign 2](assets/smartCampaign3.png)

   Plusieurs déclencheurs doivent être disponibles sous le dossier Microsoft.

1. Cliquez et faites glisser **[!UICONTROL Ajouté à l’accord]** dans le **[!UICONTROL Liste dynamique]**, ajoutez ensuite les contraintes que vous souhaitez avoir sur le déclencheur.

   ![Ajouté à l’accord](assets/addedToAgreementDynamics.png)

## Configuration du flux de campagnes intelligentes

1. Cliquez sur le bouton **[!UICONTROL Flux]** dans la boîte de dialogue [!UICONTROL Smart Campaign].

   Recherchez et faites glisser le **Appeler Webhook** ouvrez la zone de travail et sélectionnez le webhook que vous avez créé dans la section précédente.

   ![Appeler Webhook](assets/callWebhook.png)

1. Votre campagne d’avis par SMS pour les prospects ajoutés à un accord est maintenant configurée.
>[!TIP]
>
>Ce tutoriel fait partie du cours [Accélérez les cycles de vente avec Acrobat Sign pour Microsoft Dynamics et Marketo](https://experienceleague.adobe.com/?recommended=Sign-U-1-2021.1) qui est disponible gratuitement sur Experience League !