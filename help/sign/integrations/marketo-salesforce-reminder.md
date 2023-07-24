---
title: Envoyer des rappels à l’aide du Guide de configuration d’Acrobat Sign pour Salesforce et Marketo
description: Découvrez comment envoyer un rappel par e-mail depuis Marketo lorsqu’un accord n’est pas signé après un certain temps
role: Admin
solution: Acrobat Sign, Marketo, Document Cloud
level: Intermediate
topic: Integrations
jira: KT-7248
topic-revisit: Integrations
thumbnail: KT-7248.jpg
exl-id: 33aca2e0-2f27-4100-a16f-85ba652c17a3
source-git-commit: ad54f7afa78b0fbb31eccf455723a8890cb92355
workflow-type: tm+mt
source-wordcount: '953'
ht-degree: 1%

---

# Envoyer des rappels à l’aide du Guide de configuration d’Acrobat Sign pour Salesforce et Marketo

Découvrez comment envoyer un rappel par e-mail depuis Marketo lorsqu’un accord n’est pas signé après un certain temps. Cette intégration utilise Acrobat Sign, Acrobat Sign pour Salesforce, Marketo et Marketo et Salesforce Sync.

## Conditions préalables

1. Installez la synchronisation Salesforce de Marketo.

   Informations et le dernier plug-in pour Salesforce Sync est disponible [ici.](https://experienceleague.adobe.com/docs/marketo/using/product-docs/crm-sync/salesforce-sync/understanding-the-salesforce-sync.html)

1. Installez Acrobat Sign pour Salesforce.

   Des informations sur ce plugin sont disponibles [ici.](https://helpx.adobe.com/ca/sign/using/salesforce-integration-installation-guide.html)

## Recherche de l’objet personnalisé

Une fois les configurations Marketo Salesforce Sync et Acrobat Sign pour Salesforce terminées, plusieurs nouvelles options s’affichent dans le portail Marketo Admin Terminal.

![Administrateur](assets/adminTab.png)

![Synchronisation des objets](assets/salesforceAdmin.png)

1. Cliquez **Synchroniser le schéma** si c&#39;est votre première fois. Sinon, cliquez sur **Actualiser le schéma**.

   ![Actualiser](assets/refreshSchema1.png)

1. Si la synchronisation globale est en cours d’exécution, désactivez-la en cliquant sur **Désactiver la synchronisation globale**.

   ![Désactiver](assets/disableGlobal.png)

1. Cliquez **Actualiser le schéma**.

   ![Actualiser 2](assets/refreshSchema2.png)

## Synchronisation de l’objet personnalisé

Sur le côté droit, voir Objets personnalisés basés sur un prospect, un contact et un compte.

**Activer la synchronisation** pour les objets sous Piste si vous souhaitez envoyer un rappel lorsqu’une piste n’a pas signé d’accord dans Salesforce.

**Activer la synchronisation** pour les objets sous Contact si vous souhaitez envoyer un rappel lorsqu’un contact n’a pas signé d’accord dans Salesforce.

**Activer la synchronisation** pour les objets sous Compte si vous souhaitez envoyer un rappel lorsqu’un compte n’a pas signé d’accord dans Salesforce.

1. **Activer la synchronisation** pour le **Accord** affiché sous le parent souhaité (Prospect, Contact ou Compte). Effectuez cette opération pour tout autre objet personnalisé à synchroniser.

   ![Objet Accord](assets/agreementObject.png)

1. Les ressources suivantes expliquent comment procéder **Activer la synchronisation**.

   ![Synchronisation personnalisée 1](assets/customObjectSync1.png)

   ![Synchronisation personnalisée 2](assets/customObjectSync2.png)

## Exposer les champs d’objet personnalisés aux déclencheurs

1. Lorsque la synchronisation globale est désactivée, sélectionnez l’objet personnalisé Accord pour lequel vous avez activé la synchronisation, puis **Modifier les champs visibles**.

1. Cochez le champ &quot;Nom de l’accord&quot; dans la colonne Déclencheur pour l’exposer à vos déclencheurs d’action de campagne. Cochez les autres champs par lesquels vous souhaitez filtrer, puis **Enregistrer**.

   ![Modifier les champs visibles 1](assets/editVisible1.png)

   ![Modifier les champs visibles 2](assets/editVisible2.png)

1. Lorsque vous avez terminé d’activer la synchronisation sur les objets personnalisés et d’exposer les valeurs de déclencheur, n’oubliez pas de réactiver la synchronisation :

   ![Activer Global](assets/enableGlobal.png)

## Création du programme et du jeton

1. Dans la section Activités marketing de Marketo, cliquez avec le bouton droit de la souris sur **Activités marketing** dans la barre de gauche, sélectionnez **Nouveau dossier de campagne** et donnez-lui un nom.

   ![Nouveau dossier](assets/newFolder.png)

1. Cliquez avec le bouton droit de la souris sur le dossier créé, sélectionnez **Nouveau programme** et donnez-lui un nom. Laissez le reste par défaut, puis cliquez sur **Créer**.

   ![Nouveau programme 1](assets/newProgram1.png)

   ![Nouveau programme 2](assets/newProgram2.png)

1. Cliquez sur **Mes jetons**, puis faites glisser  **Email Script** sur la zone de travail.

   ![Email Script](assets/emailScript.png)

1. Donnez-lui un nom, puis cliquez sur **Cliquer pour modifier**.

   ![Nommer et modifier](assets/nameAndSave.png)

1. Développer **Objets personnalisés** sur le côté droit, puis développez la **Accord** objet. Recherchez et faites glisser le nom de l’accord, le statut de l’accord, la date de signature et l’URL de signature sur le canevas.

1. Rédigez un script Velocity à l’aide de ces jetons pour afficher l’URL d’un accord non signé pendant une semaine. Voici un exemple qui compare la date du jour à la Date d’envoi :

   ```
   #foreach($agreement in $echosign_dev1__SIGN_Agreement__cList)
       #if($agreement.echosign_dev1__Status__c == "Out for Signature")
           #set($todayCalObj = $date.toCalendar($date.toDate("yyyy-MM-dd",$date.get('yyyy-MM-dd'))) )
           #set($dateSentCalObj = $date.toCalendar($date.toDate("yyyy-MM-dd",$agreement.echosign_dev1__DateSent__c)) )
           #set($dateDiff = ($todayCalObj.getTimeInMillis() - $dateSentCalObj.getTimeInMillis()) / 86400000 )
   
           #if($dateDiff >= 7)
               #set($agreementName = $agreement.Name)
               #set($agreementURL = $agreement.echosign_dev1__Signing_URL__c.substring(8))
               #break
           #else
           #end
       #else
       #end
   #end
   
   #if(${agreementName})
       <a href="https://${agreementURL}">${agreementName}</a>
   #else
       Please contact us. 
   #end
   ```

1. Cliquez sur **Enregistrer**.

## Création du rappel et personnalisation

Voici quelques exemples de personnalisation : le nom du signataire, le nom de l’accord, un lien vers l’accord, etc.

1. Cliquez avec le bouton droit de la souris sur le programme que vous avez créé, puis cliquez sur **Nouvelle ressource locale**, puis sélectionnez **Email**.

   ![Nouvelle adresse électronique](assets/createNewEmail.png)

1. Dans le nouvel onglet, entrez un **Nom** et **Description** pour l’e-mail et sélectionnez un modèle dans le sélecteur de modèles. Cliquez sur **Créer**.

   ![Sélecteur de modèles](assets/templatePicker.png)

1. Définissez la **Nom de départ** et **Adresse source**.

   ![E-mail de rappel](assets/reminderEmail.png)

1. Cliquez sur le corps du message pour activer l&#39;éditeur. Cliquez sur le bouton **Insérer un jeton** , recherchez le jeton d’URL d’accord personnalisé que vous avez créé, puis cliquez sur **Insérer**. Terminez la personnalisation de votre courrier électronique, puis cliquez sur **Enregistrer**.

   ![Insérer un jeton](assets/insertToken.png)

1. Prévisualisez à l’aide d’un profil auquel un accord est affecté. Vous devriez voir un lien vers l’URL avec le nom de l’accord comme libellé.

   ![Lien de messagerie](assets/emailLink.png)

## Configuration du filtre de campagne dynamique

1. Cliquez avec le bouton droit sur le programme que vous avez créé, puis cliquez sur **Nouvelle campagne intelligente**.

   ![Smart Campaign 1](assets/smartCampaign1.png)

1. Donnez-lui le nom de votre choix, puis cliquez sur **Créer**.

   ![Smart Campaign 2](assets/smartCampaign2.png)

1. Rechercher, puis cliquer et faire glisser **A un accord** à la liste dynamique.

   ![A un accord](assets/hasAgreement.png)

1. Les champs que vous avez exposés au déclencheur doivent désormais être disponibles dans **Ajouter une contrainte**. Sélectionner **Statut des accords** et tout autre champ par lequel vous souhaitez filtrer. Pour chaque champ ajouté, définissez les valeurs de filtrage. Dans ce cas, il se déclenche uniquement lorsque l’attribut **Statut des accords** est Émis pour signature et **Date d&#39;envoi** est dans le passé avant 7 jours.

   ![État de l’accord](assets/agreementStatus.png)

   >[!NOTE]
   >
   > d un identifiant unique pour les contraintes, comme **Nom de contrat**, si vous souhaitez que cette campagne s’exécute uniquement pour certains accords.

1. Confirmez le public de la campagne et voyez qui sera éligible dans l&#39;onglet Programme.

   ![Qualificateurs](assets/qualifiers.png)

## Configuration du flux de campagnes intelligentes

Parce que le filtre de campagne **Jours non signés** a été utilisé, vous pouvez utiliser une périodicité planifiée pour la campagne.

1. Cliquez sur le bouton **Flux** dans la fenêtre Smart Campaign. Recherchez et faites glisser le **Envoyer un courrier électronique** dans la zone de travail et sélectionnez l’e-mail de rappel que vous avez créé dans la section précédente.

   ![Envoyer un courrier électronique](assets/sendEmail.png)

1. Cliquez sur le bouton **Planification** dans la fenêtre Smart Campaign. Assurez-vous que le flux de campagne est limité à une seule exécution par personne dans le **Paramètres Smart Campaign**. Cliquez ensuite sur l’icône **Planifier la périodicité** .

   ![Onglet Programme](assets/scheduleTab.png)

1. Définissez la **Planification** sur Quotidien, choisissez un jour et une heure de début, ainsi qu&#39;une date de fin pour la campagne si nécessaire.

   ![Paramètres de planification](assets/scheduleSettings.png)

>[!TIP]
>
>Ce tutoriel fait partie du cours [Accélérez les cycles de vente avec Acrobat Sign pour Salesforce et Marketo](https://experienceleague.adobe.com/?recommended=Sign-U-1-2021.1) qui est disponible gratuitement sur Experience League !
