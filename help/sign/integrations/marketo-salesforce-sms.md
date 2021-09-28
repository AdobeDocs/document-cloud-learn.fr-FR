---
title: Envoi de notifications à l’aide d’Adobe Sign pour Salesforce et Marketo
description: Découvrez comment envoyer un message texte, un courrier électronique ou une notification push afin de faire savoir au signataire qu’un accord est en cours d’envoi.
role: Admin
product: adobe sign
solution: Adobe Sign, Marketo, Document Cloud
level: Intermediate
topic-revisit: Integrations
thumbnail: KT-7248.jpg
exl-id: ac3334ec-b65f-4ce4-b323-884948f5e0a6
source-git-commit: bc79bbde966c99bdf32231ff073b49cfc759d928
workflow-type: tm+mt
source-wordcount: '690'
ht-degree: 1%

---

# Envoi de notifications à l’aide d’Adobe Sign pour Salesforce et Marketo

Découvrez comment envoyer un message texte, un courrier électronique ou une notification Push pour informer le signataire qu’un accord est en cours d’envoi à l’aide d’Adobe Sign, Adobe Sign pour Salesforce, Marketo et de Marketo Salesforce Sync. Pour envoyer des notifications depuis Marketo, vous devez d’abord acheter ou configurer une fonctionnalité de gestion des SMS Marketo. Cette procédure pas à pas utilise [Twilio SMS](https://launchpoint.marketo.com/twilio/twilio-sms-for-marketo/), mais d&#39;autres solutions Marketo SMS sont disponibles.

## Conditions préalables

1. Installez Marketo Salesforce Sync.

   Les informations et le dernier module externe pour la synchronisation Salesforce sont disponibles [ici.](https://experienceleague.adobe.com/docs/marketo/using/product-docs/crm-sync/salesforce-sync/understanding-the-salesforce-sync.html)

1. Installez Adobe Sign pour Salesforce.

   Des informations sur ce module externe sont disponibles [ici.](https://helpx.adobe.com/ca/sign/using/salesforce-integration-installation-guide.html)

## Recherche de l’objet personnalisé

Une fois que les configurations Marketo Salesforce Sync et Adobe Sign for Salesforce sont terminées, plusieurs nouvelles options apparaissent dans le terminal d’administration Marketo.

![Administrateur](assets/adminTab.png)

![Synchronisation d’objets](assets/salesforceAdmin.png)

1. Si c&#39;est votre première fois, cliquez sur **Synchroniser le schéma**. Sinon, cliquez sur **Actualiser le schéma**.

   ![Actualiser](assets/refreshSchema1.png)

1. Si la synchronisation globale est en cours d’exécution, désactivez-la en cliquant sur **Désactiver la synchronisation globale**.

   ![Désactiver](assets/disableGlobal.png)

1. Cliquez sur **Actualiser le schéma**.

   ![Actualiser 2](assets/refreshSchema2.png)

## Synchronisation des objets personnalisés

Sur le côté droit, voir Objets personnalisés basés sur une piste, un contact et un compte.

**Activez** Synchroniser les objets sous Piste si vous souhaitez déclencher lorsqu’une Piste est ajoutée à un accord dans Salesforce.

**Activez** Synchroniser pour les objets situés sous Contact si vous souhaitez déclencher lorsqu’un contact est ajouté à un accord dans Salesforce.

**Activez** Synchroniser pour les objets sous Compte si vous souhaitez déclencher lorsqu’un compte est ajouté à un accord dans Salesforce.

1. **Activez la** synchronisation pour les objets personnalisés affichés sous le parent souhaité (Piste, Contact ou Compte).

   ![Objets personnalisés](assets/customObjects.png)

1. Les actifs suivants montrent comment activer la **synchronisation**.

   ![Synchronisation personnalisée 1](assets/customObjectSync1.png)

   ![Synchronisation personnalisée 2](assets/customObjectSync2.png)

1. Lorsque vous avez terminé d’activer la synchronisation sur les objets personnalisés, réactivez la synchronisation.

   ![Activer Global](assets/enableGlobal.png)

## Création du programme

1. Dans la section Activités marketing de Marketo, cliquez avec le bouton droit de la souris sur **Activités marketing** dans la barre de gauche, sélectionnez **Nouveau dossier de campagne** et donnez-lui un nom.

   ![Nouveau dossier](assets/newFolder.png)

1. Cliquez avec le bouton droit de la souris sur le dossier créé, sélectionnez **Nouveau programme**, puis donnez-lui un nom. Conservez tous les autres paramètres par défaut, puis cliquez sur **Créer**.

   ![Nouveau programme 1](assets/newProgram1.png)

   ![Nouveau programme 2](assets/newProgram2.png)

## Configurer Twilio SMS

Assurez-vous d’abord d’avoir un compte Twilio actif et achetez les fonctionnalités SMS dont vous avez besoin.

La configuration du webhook Marketo - Twilio SMS nécessite trois paramètres Twilio de votre compte.

- SID du compte
- Jeton de compte
- Numéro de téléphone Twilio

Récupérez ces paramètres de votre compte, puis ouvrez votre instance Marketo.

1. Cliquez sur **Admin** en haut à droite.

   ![Administrateur](assets/adminTab.png)

1. Cliquez sur **Webhooks**, puis **Nouveau Webhook**.

   ![Webhooks](assets/webhooks.png)

1. Entrez un **nom de Webhook** et une **description**.

1. Entrez l’URL suivante et veillez à remplacer **[ACCOUNT_SID]** et **[AUTH_TOKEN]** par vos informations d’identification Twilio.

   ```
   https://[ACCOUNT_SID]:[AUTH_TOKEN]@API.TWILIO.COM/2010-04-01/ACCOUNTS/[ACCOUNT_SID]/Messages.json
   ```

1. Sélectionnez **POST** comme type de demande.

1. Entrez le **modèle** suivant et veillez à remplacer **[MY_TWILIO_NUMBER]** par votre numéro de téléphone Twilio et **[YOUR_MESSAGE]** par un message de votre choix.

   ```
   From=%2B1[MY_TWILIO_NUMBER]&To=%2B1{{lead.Mobile Phone Number:default=edit me}}&Body=[YOUR_MESSAGE]
   ```

1. Définissez le codage du jeton de demande sur Formulaire/URL.

1. Définissez le type de réponse sur JSON, puis cliquez sur **Enregistrer**.

## Configuration du déclencheur Smart Campaign

1. Dans la section Activités marketing, cliquez avec le bouton droit de la souris sur le programme que vous avez créé, puis sélectionnez **Nouvelle campagne dynamique**.

   ![Smart Campaign 1](assets/smartCampaign1.png)

1. Nommez-le, puis cliquez sur **Créer**.

   ![Smart Campaign 2](assets/smartCampaign3.png)

   Si la configuration de la synchronisation d’objets personnalisée a été effectuée correctement, vous devriez voir les déclencheurs suivants disponibles pour utilisation sous le dossier Salesforce.

1. Cliquez sur et faites glisser l’option Ajout à l’accord sur la liste dynamique. Ajoutez toutes les contraintes que vous souhaitez avoir sur le déclencheur.

   ![Ajouté à l’accord 2](assets/addedToAgreement2.png)

## Configuration du flux de campagne dynamique

1. Cliquez sur l&#39;onglet **Flux** dans la campagne dynamique. Recherchez et faites glisser l’enchaînement **Appeler Webhook** sur la zone de travail, puis sélectionnez le webhook que vous avez créé dans la section précédente.

   ![Appeler Webhook](assets/callWebhook.png)

1. Votre campagne d’avis par SMS pour les prospects qui sont ajoutés à un accord est maintenant configurée.

>[!TIP]
>
>Ce tutoriel fait partie du cours [Accélération des cycles de vente avec Adobe Sign pour Salesforce et Marketo](https://experienceleague.adobe.com/?recommended=Sign-U-1-2021.1) disponible gratuitement sur Experience League !