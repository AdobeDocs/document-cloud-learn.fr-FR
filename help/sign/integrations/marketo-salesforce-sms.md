---
title: Envoi de notifications à l’aide d’Acrobat Sign pour Salesforce et Marketo
description: Découvrez comment envoyer un SMS, un e-mail ou une notification push pour informer le signataire qu’un accord est en cours d’envoi.
feature: Integrations
role: Admin
solution: Acrobat Sign, Marketo Engage, Document Cloud
level: Intermediate
jira: KT-7247
topic: Integrations
topic-revisit: Integrations
thumbnail: KT-7248.jpg
exl-id: ac3334ec-b65f-4ce4-b323-884948f5e0a6
source-git-commit: a88ec5a68aa2a02ec2f118332ec31f47d3d5d300
workflow-type: tm+mt
source-wordcount: '646'
ht-degree: 0%

---

# Envoyer des notifications à l’aide d’Acrobat Sign pour [!DNL Salesforce] et [!DNL Marketo]

Découvrez comment envoyer un SMS, un e-mail ou une notification push pour informer le signataire qu’un accord est en cours d’envoi à l’aide d’Acrobat Sign, Acrobat Sign pour Salesforce, Marketo et la synchronisation Marketo Salesforce. Pour envoyer des notifications à partir de Marketo, vous devez d’abord acheter ou configurer une fonction de gestion des SMS Marketo. Cette procédure pas à pas utilise [Twilio SMS](https://launchpoint.marketo.com/twilio/twilio-sms-for-marketo/), mais d&#39;autres solutions Marketo SMS sont disponibles.

## Conditions préalables

1. Installez Marketo Salesforce Sync.

   Des informations et le dernier plug-in pour Salesforce Sync sont disponibles [ici](https://experienceleague.adobe.com/docs/marketo/using/product-docs/crm-sync/salesforce-sync/understanding-the-salesforce-sync.html).

1. Installez Acrobat Sign pour Salesforce.

   Des informations sur ce plug-in sont disponibles [ici](https://helpx.adobe.com/ca/sign/using/salesforce-integration-installation-guide.html).

## Recherche de l’objet personnalisé

Une fois les configurations Marketo Salesforce Sync et Acrobat Sign pour Salesforce terminées, plusieurs nouvelles options apparaissent dans le terminal d’administration Marketo.

![Administrateur](assets/adminTab.png)

![Synchronisation des objets](assets/salesforceAdmin.png)

1. Cliquez sur **Synchroniser le schéma** si c&#39;est votre première fois. Sinon, cliquez sur **Actualiser le schéma**.

   ![Actualiser](assets/refreshSchema1.png)

1. Si la synchronisation globale est en cours d&#39;exécution, désactivez-la en cliquant sur **Désactiver la synchronisation globale**.

   ![Désactiver](assets/disableGlobal.png)

1. Cliquez sur **Actualiser le schéma**.

   ![Actualiser 2](assets/refreshSchema2.png)

## Synchronisation des objets personnalisés

Sur le côté droit, voir Objets personnalisés Prospect, Contact et Compte.

**Activez la synchronisation** pour les objets sous Prospect si vous souhaitez déclencher lorsqu’un prospect est ajouté à un accord dans Salesforce.

**Activez la synchronisation** pour les objets sous Contact si vous souhaitez déclencher lorsqu’un contact est ajouté à un accord dans Salesforce.

**Activez la synchronisation** pour les objets sous Compte si vous souhaitez déclencher lorsqu’un compte est ajouté à un accord dans Salesforce.

1. **Activez la synchronisation** pour les objets personnalisés affichés sous le parent souhaité (prospect, contact ou compte).

   ![Objets personnalisés](assets/customObjects.png)

1. Les actifs suivants indiquent comment **activer la synchronisation**.

   ![Synchronisation personnalisée 1](assets/customObjectSync1.png)

   ![Synchronisation personnalisée 2](assets/customObjectSync2.png)

1. Une fois la synchronisation activée sur les objets personnalisés, réactivez-la.

   ![Activer Global](assets/enableGlobal.png)

## Création du programme

1. Dans la section Activités marketing de Marketo, cliquez avec le bouton droit de la souris sur **Activités marketing** dans la barre de gauche, sélectionnez **Nouveau dossier de campagne** et donnez-lui un nom.

   ![Nouveau dossier](assets/newFolder.png)

1. Cliquez avec le bouton droit de la souris sur le dossier créé, sélectionnez **Nouveau programme** et donnez-lui un nom. Laissez tout le reste comme défaut, puis cliquez sur **Créer**.

   ![Nouveau programme 1](assets/newProgram1.png)

   ![Nouveau programme 2](assets/newProgram2.png)

## Configuration de Twilio SMS

Assurez-vous d’abord d’avoir un compte Twilio actif et d’avoir acheté les fonctionnalités SMS dont vous avez besoin.

La configuration du webhook Marketo - Twilio SMS nécessite trois paramètres Twilio de votre compte.

- SID de compte
- Jeton de compte
- Numéro de téléphone Twilio

Récupérez ces paramètres de votre compte, puis ouvrez votre instance Marketo.

1. Cliquez sur **Administrateur** en haut à droite.

   ![Administrateur](assets/adminTab.png)

1. Cliquez sur **Webhooks**, puis sur **Nouveau webhook**.

   ![Webhooks](assets/webhooks.png)

1. Saisissez un **nom de webhook** et une **description**.

1. Entrez l&#39;URL suivante et assurez-vous de remplacer **[ACCOUNT_SID]** et **[AUTH_TOKEN]** par vos informations d&#39;identification Twilio.

   ```
   https://[ACCOUNT_SID]:[AUTH_TOKEN]@API.TWILIO.COM/2010-04-01/ACCOUNTS/[ACCOUNT_SID]/Messages.json
   ```

1. Sélectionnez **POST** comme type de demande.

1. Entrez le **modèle** suivant et assurez-vous de remplacer **[MY_TWILIO_NUMBER]** par votre numéro de téléphone Twilio et **[YOUR_MESSAGE]** par un message de votre choix.

   ```
   From=%2B1[MY_TWILIO_NUMBER]&To=%2B1{{lead.Mobile Phone Number:default=edit me}}&Body=[YOUR_MESSAGE]
   ```

1. Définissez le codage de jeton de demande sur Formulaire/URL.

1. Définissez le type de réponse sur JSON, puis cliquez sur **Enregistrer**.

## Configuration du déclencheur de campagne intelligent

1. Dans la section Activités marketing, cliquez avec le bouton droit sur le programme que vous avez créé, puis sélectionnez **Nouvelle campagne intelligente**.

   ![Campagne intelligente 1](assets/smartCampaign1.png)

1. Nommez-le, puis cliquez sur **Créer**.

   ![Campagne intelligente 2](assets/smartCampaign3.png)

   Si la configuration de la synchronisation d’objets personnalisés a été effectuée correctement, les déclencheurs suivants devraient être disponibles sous le dossier Salesforce.

1. Cliquez et faites glisser l’option Ajouté à l’accord dans la liste dynamique. Ajoutez les contraintes que vous souhaitez appliquer au déclencheur.

   ![Ajouté à l’accord 2](assets/addedToAgreement2.png)

## Configuration du flux de campagne intelligent

1. Cliquez sur l&#39;onglet **Flux** dans la campagne intelligente. Recherchez et faites glisser le flux **Appeler le webhook** sur la zone de travail et sélectionnez le webhook que vous avez créé dans la section précédente.

   ![Appeler Webhook](assets/callWebhook.png)

1. Votre campagne de notification par SMS pour les prospects ajoutés à un accord est maintenant configurée.
