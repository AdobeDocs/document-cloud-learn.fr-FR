---
title: Envoi de notifications à l’aide d’Acrobat Sign pour Microsoft Dynamics 365 et Marketo
description: Découvrez comment envoyer un SMS, un e-mail ou une notification push pour informer le signataire qu’un accord est en cours d’envoi.
feature: Integrations
role: Admin
solution: Acrobat Sign, Marketo Engage, Document Cloud
level: Intermediate
topic: Integrations
topic-revisit: Integrations
jira: KT-7249
thumbnail: KT-7249.jpg
exl-id: 2e0de48c-70bf-4dc5-8251-88e7399f588a
source-git-commit: a88ec5a68aa2a02ec2f118332ec31f47d3d5d300
workflow-type: tm+mt
source-wordcount: '652'
ht-degree: 0%

---

# Envoi de notifications à l’aide d’Acrobat Sign pour Microsoft Dynamics 365 et Marketo

Découvrez comment envoyer un SMS, un e-mail ou une notification push pour informer le signataire qu’un accord est en cours d’envoi à l’aide d’Acrobat Sign, Acrobat Sign pour Microsoft Dynamic, Marketo et Marketo Microsoft Dynamics Sync. Pour envoyer des notifications à partir de Marketo, vous devez d’abord acheter ou configurer une fonction de gestion des SMS Marketo. Cette procédure pas à pas utilise [Twilio SMS](https://launchpoint.marketo.com/twilio/twilio-sms-for-marketo/), mais d&#39;autres solutions Marketo SMS sont disponibles.

## Conditions préalables

1. Installez Marketo Microsoft Dynamics Sync.

   Des informations et le dernier plug-in pour Microsoft Dynamics Sync sont disponibles [ici](https://experienceleague.adobe.com/docs/marketo/using/product-docs/crm-sync/microsoft-dynamics/marketo-plugin-releases-for-microsoft-dynamics.html?lang=fr).

1. Installez Acrobat Sign pour Microsoft Dynamics.

   Des informations sur ce plug-in sont disponibles [ici](https://helpx.adobe.com/ca/sign/using/microsoft-dynamics-integration-installation-guide.html).

## Recherche de l’objet personnalisé

Une fois les configurations Marketo Microsoft Dynamics Sync et Acrobat Sign pour Dynamics terminées, deux nouvelles options apparaissent dans le terminal d’administration Marketo.

![Administrateur](assets/adminTerminal.png)

* Cliquez sur **[!UICONTROL Synchronisation des entités Dynamics]**.

  La synchronisation doit être désactivée avant de synchroniser les entités personnalisées. Cliquez sur **[!UICONTROL Synchroniser le schéma]** si c&#39;est votre première fois. Sinon, cliquez sur **[!UICONTROL Actualiser le schéma]**.

  ![Actualiser](assets/refreshSchema.png)

## Synchronisation de l’objet personnalisé

1. Sur le côté droit, recherchez les objets personnalisés basés sur [!UICONTROL Lead], [!UICONTROL Contact] et [!UICONTROL Compte].

   * **[!UICONTROL Activez la synchronisation]** pour les objets sous Prospect si vous souhaitez déclencher lorsqu’un prospect est ajouté à un accord dans Dynamics.

   * **[!UICONTROL Activez la synchronisation]** pour les objets sous Contact si vous souhaitez qu’un contact soit déclenché lorsqu’un contact est ajouté à un accord dans Dynamics.

   * **[!UICONTROL Activez la synchronisation]** pour les objets sous Compte si vous souhaitez déclencher lorsqu’un compte est ajouté à un accord dans Dynamics.

   * **Activez la synchronisation** pour l’objet Accord sous le parent souhaité (prospect, contact ou compte).

   ![Objets personnalisés](assets/enableSyncDynamics.png)

1. Dans la nouvelle fenêtre, sélectionnez les propriétés souhaitées sous Accord.

   Activez les zones sous **[!UICONTROL Contrainte]** et **[!UICONTROL Déclencheur]** pour les exposer à vos activités marketing.

   ![Synchronisation personnalisée 1](assets/entitySync1.png)

   ![Synchronisation personnalisée 2](assets/entitySync2.png)

1. Réactivez la synchronisation après avoir activé la synchronisation sur les objets personnalisés.

   Revenez au [!UICONTROL terminal d&#39;administration], cliquez sur **[!UICONTROL Microsoft Dynamics]**, puis sur **[!UICONTROL Activer la synchronisation]**.

   ![Microsoft Dynamics](assets/microsoftDynamics.png)

   ![Activer Global](assets/enableGlobalDynamics.png)

## Création du programme

1. Dans [!UICONTROL Activités marketing], cliquez avec le bouton droit de la souris sur **[!UICONTROL Activités marketing]** dans la barre de gauche, sélectionnez **[!UICONTROL Nouveau dossier de campagne]** et nommez-le.

   ![Nouveau dossier](assets/newFolder.png)

1. Cliquez avec le bouton droit de la souris sur le dossier créé, sélectionnez **[!UICONTROL Nouveau programme]** et donnez-lui un nom.

   Laissez tout le reste comme défaut, puis cliquez sur **[!UICONTROL Créer]**.

   ![Nouveau programme 1](assets/newProgram1.png)

   ![Nouveau programme 2](assets/newProgram2.png)

## Configurer [!DNL Twilio] SMS

Vérifiez d&#39;abord que vous disposez d&#39;un compte [!DNL Twilio] actif et que vous avez acheté les fonctionnalités SMS dont vous avez besoin.

La configuration du webhook Marketo - [!DNL Twilio] SMS nécessite trois paramètres [!DNL Twilio] de votre compte.

* SID de compte
* Jeton de compte
* Numéro de téléphone Twilio

Récupérez ces paramètres de votre compte, puis ouvrez votre instance Marketo.

1. Cliquez sur **[!UICONTROL Administrateur]** en haut à droite.

   ![Administrateur](assets/adminTab.png)

1. Cliquez sur **[!UICONTROL Webhooks]**, puis sur **[!UICONTROL Nouveau webhook]**.

   ![Webhooks](assets/webhooks.png)

1. Saisissez un **[!UICONTROL nom de webhook]** et une **[!UICONTROL description]**.

1. Entrez l&#39;URL suivante et assurez-vous de remplacer les `ACCOUNT_SID` et `AUTH_TOKEN` par vos informations d&#39;identification [!DNL Twilio].

   ```
   https://[ACCOUNT_SID]:[AUTH_TOKEN]@API.TWILIO.COM/2010-04-01/ACCOUNTS/[ACCOUNT_SID]/Messages.json
   ```

1. Sélectionnez **[!UICONTROL POST]** comme type de demande.

1. Saisissez le **modèle** suivant et assurez-vous de remplacer `MY_TWILIO_NUMBER` par votre numéro de téléphone [!DNL Twilio] et `YOUR_MESSAGE` par un message de votre choix.

   ```
   From=%2B1[MY_TWILIO_NUMBER]&To=%2B1{{lead.Mobile Phone Number:default=edit me}}&Body=[YOUR_MESSAGE]
   ```

1. Définissez le **[!UICONTROL codage de jeton de demande]** sur *Formulaire/URL*.

1. Définissez le type de réponse sur *JSON*, puis cliquez sur **[!UICONTROL Enregistrer]**.

## Configuration du déclencheur de campagne intelligent

1. Dans la section Activités marketing, cliquez avec le bouton droit sur le programme que vous avez créé, puis sélectionnez **[!UICONTROL Nouvelle campagne intelligente]**.

   ![Campagne intelligente 1](assets/smartCampaign1.png)

1. Nommez-le, puis cliquez sur **[!UICONTROL Créer]**.

   ![Campagne intelligente 2](assets/smartCampaign3.png)

   Plusieurs déclencheurs sont disponibles sous le dossier Microsoft.

1. Cliquez sur **[!UICONTROL Ajouté à l’accord]** et faites-le glisser vers la **[!UICONTROL liste dynamique]**, puis ajoutez les contraintes que vous souhaitez appliquer au déclencheur.

   ![Ajouté à l’accord](assets/addedToAgreementDynamics.png)

## Configuration du flux de campagne intelligent

1. Cliquez sur l&#39;onglet **[!UICONTROL Flux]** dans la [!UICONTROL Campagne intelligente].

   Recherchez et faites glisser le flux **Appeler le webhook** sur la zone de travail et sélectionnez le webhook que vous avez créé dans la section précédente.

   ![Appeler Webhook](assets/callWebhook.png)

1. Votre campagne de notification par SMS pour les prospects ajoutés à un accord est maintenant configurée.
