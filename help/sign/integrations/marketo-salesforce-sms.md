---
title: Envoi de notifications à l’aide d’Acrobat Sign pour Salesforce et Marketo
description: Découvrez comment envoyer un SMS, un e-mail ou une notification Push pour informer le signataire qu’un accord est en cours d’envoi
role: Admin
product: adobe sign
solution: Acrobat Sign, Marketo, Document Cloud
level: Intermediate
topic-revisit: Integrations
thumbnail: KT-7248.jpg
exl-id: ac3334ec-b65f-4ce4-b323-884948f5e0a6
source-git-commit: e02b1250de94ec781e7984c6c146dbae993f5d31
workflow-type: tm+mt
source-wordcount: '690'
ht-degree: 1%

---

# Envoi de notifications à l’aide d’Acrobat Sign pour Salesforce et Marketo

Découvrez comment envoyer un SMS, un e-mail ou une notification push pour informer le signataire qu’un accord est en cours d’envoi à l’aide d’Acrobat Sign, Acrobat Sign pour Salesforce, Marketo et Marketo Salesforce Sync. Pour envoyer des notifications à partir de Marketo, vous devez d’abord acheter ou configurer une fonction de gestion des SMS de Marketo. Cette procédure pas à pas utilise [Twilio SMS](https://launchpoint.marketo.com/twilio/twilio-sms-for-marketo/), mais d’autres solutions SMS de Marketo sont disponibles.

## Conditions préalables

1. Installez la synchronisation Salesforce de Marketo.

   Informations et le dernier plug-in pour Salesforce Sync est disponible [ici.](https://experienceleague.adobe.com/docs/marketo/using/product-docs/crm-sync/salesforce-sync/understanding-the-salesforce-sync.html)

1. Installez Acrobat Sign pour Salesforce.

   Des informations sur ce plugin sont disponibles [ici.](https://helpx.adobe.com/ca/sign/using/salesforce-integration-installation-guide.html)

## Recherche de l’objet personnalisé

Une fois les configurations Marketo Salesforce Sync et Acrobat Sign pour Salesforce terminées, plusieurs nouvelles options apparaissent dans le terminal d’administration de Marketo.

![Administrateur](assets/adminTab.png)

![Synchronisation des objets](assets/salesforceAdmin.png)

1. Cliquez **Synchroniser le schéma** si c&#39;est votre première fois. Sinon, cliquez sur **Actualiser le schéma**.

   ![Actualiser](assets/refreshSchema1.png)

1. Si la synchronisation globale est en cours d’exécution, désactivez-la en cliquant sur **Désactiver la synchronisation globale**.

   ![Désactiver](assets/disableGlobal.png)

1. Cliquez **Actualiser le schéma**.

   ![Actualiser 2](assets/refreshSchema2.png)

## Synchronisation des objets personnalisés

Sur le côté droit, voir Objets personnalisés basés sur un prospect, un contact et un compte.

**Activer la synchronisation** pour les objets sous Piste si vous souhaitez le déclencher lorsqu’une piste est ajoutée à un accord dans Salesforce.

**Activer la synchronisation** pour les objets sous Contact si vous souhaitez déclencher lorsqu’un contact est ajouté à un accord dans Salesforce.

**Activer la synchronisation** pour les objets sous Compte si vous souhaitez le déclencher lorsqu’un compte est ajouté à un accord dans Salesforce.

1. **Activer la synchronisation** pour les objets personnalisés affichés sous le parent souhaité (Prospect, Contact ou Compte).

   ![Objets personnalisés](assets/customObjects.png)

1. Les ressources suivantes expliquent comment procéder **Activer la synchronisation**.

   ![Synchronisation personnalisée 1](assets/customObjectSync1.png)

   ![Synchronisation personnalisée 2](assets/customObjectSync2.png)

1. Lorsque vous avez terminé d’activer la synchronisation sur les objets personnalisés, réactivez la synchronisation.

   ![Activer Global](assets/enableGlobal.png)

## Création du programme

1. Dans la section Activités marketing de Marketo, cliquez avec le bouton droit de la souris sur **Activités marketing** dans la barre de gauche, sélectionnez **Nouveau dossier de campagne** et donnez-lui un nom.

   ![Nouveau dossier](assets/newFolder.png)

1. Cliquez avec le bouton droit de la souris sur le dossier créé, sélectionnez **Nouveau programme** et donnez-lui un nom. Laissez le reste par défaut, puis cliquez sur **Créer**.

   ![Nouveau programme 1](assets/newProgram1.png)

   ![Nouveau programme 2](assets/newProgram2.png)

## Configuration de Twilio SMS

Assurez-vous d&#39;abord d&#39;avoir un compte Twilio actif et acheté les fonctionnalités SMS dont vous avez besoin.

La configuration du webhook Marketo - Twilio SMS nécessite trois paramètres Twilio de votre compte.

- SID du compte
- Jeton de compte
- Numéro de téléphone Twilio

Récupérez ces paramètres de votre compte, puis ouvrez votre instance Marketo.

1. Cliquez sur **Administrateur** en haut à droite.

   ![Administrateur](assets/adminTab.png)

1. Cliquez sur **Webhooks**, puis **Nouveau webhook**.

   ![Webhooks](assets/webhooks.png)

1. Saisissez un **Nom du webhook** et **Description**.

1. Entrez l’URL suivante et veillez à remplacer la **[ACCOUNT_SID]** et **[AUTH_TOKEN]** avec vos identifiants Twilio.

   ```
   https://[ACCOUNT_SID]:[AUTH_TOKEN]@API.TWILIO.COM/2010-04-01/ACCOUNTS/[ACCOUNT_SID]/Messages.json
   ```

1. Sélectionner **POST** comme type de demande.

1. Saisissez les informations suivantes : **Modèle** et assurez-vous de remplacer **[MY_TWILIO_NUMBER]** avec votre numéro de téléphone Twilio et **[YOUR_MESSAGE]** avec un message de votre choix.

   ```
   From=%2B1[MY_TWILIO_NUMBER]&To=%2B1{{lead.Mobile Phone Number:default=edit me}}&Body=[YOUR_MESSAGE]
   ```

1. Définissez le codage du jeton de demande sur Formulaire/URL.

1. Définissez le type de réponse sur JSON, puis cliquez sur **Enregistrer**.

## Configuration du déclencheur Smart Campaign

1. Dans la section Activités marketing , cliquez avec le bouton droit sur le programme que vous avez créé, puis sélectionnez **Nouvelle campagne intelligente**.

   ![Smart Campaign 1](assets/smartCampaign1.png)

1. Nommez-le, puis cliquez sur **Créer**.

   ![Smart Campaign 2](assets/smartCampaign3.png)

   Si la configuration de la synchronisation d’objets personnalisée a été effectuée correctement, les déclencheurs suivants doivent être disponibles sous le dossier Salesforce.

1. Cliquez sur Ajouter à l’accord et faites-le glisser vers la liste dynamique. Ajoutez toutes les contraintes que vous souhaitez avoir sur le déclencheur.

   ![Ajouté à l’accord 2](assets/addedToAgreement2.png)

## Configuration du flux de campagnes intelligentes

1. Cliquez sur le bouton **Flux** dans la fenêtre Smart Campaign. Recherchez et faites glisser le **Appeler Webhook** ouvrez la zone de travail et sélectionnez le webhook que vous avez créé dans la section précédente.

   ![Appeler Webhook](assets/callWebhook.png)

1. Votre campagne d’avis par SMS pour les prospects ajoutés à un accord est maintenant configurée.

>[!TIP]
>
>Ce tutoriel fait partie du cours [Accélérez les cycles de vente avec Acrobat Sign pour Salesforce et Marketo](https://experienceleague.adobe.com/?recommended=Sign-U-1-2021.1) qui est disponible gratuitement sur Experience League !