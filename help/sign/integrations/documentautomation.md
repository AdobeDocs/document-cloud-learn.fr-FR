---
title: Document Automation avec Acrobat Sign pour Microsoft Power Platform
description: Découvrez comment activer et utiliser les connecteurs Acrobat Sign et Adobe PDF Tools pour Microsoft Power Apps. Créez des workflows qui automatisent les processus d’approbation et de signature de l’entreprise rapidement et en toute sécurité, sans aucun code
feature: Integrations, Workflow
role: User, Developer
level: Intermediate
topic: Integrations
thumbnail: KT-7488.jpg
jira: KT-7488
exl-id: 4113bc3f-293c-44a8-94ab-e1dbac74caed
source-git-commit: 452299b2b786beab9df7a5019da4f3840d9cdec9
workflow-type: tm+mt
source-wordcount: '2448'
ht-degree: 0%

---

# Automatisation des documents avec Acrobat Sign pour Microsoft Power Platform

Découvrez comment activer et utiliser les connecteurs Acrobat Sign et Adobe PDF Tools pour Microsoft Power Apps. Créez des workflows qui automatisent les processus d’approbation et de signature de l’entreprise rapidement et en toute sécurité, sans aucun code. Ce tutoriel pratique est divisé en quatre parties, comme indiqué dans les liens ci-dessous :

<table style="table-layout:fixed">
<tr>
  <td>
    <a href="documentautomation.md#part1">
        <img alt="Partie 1 : Stocker l’accord signé dans SharePoint avec Acrobat Sign" src="assets/documentautomation/AutomationPart1_thumb.jpg" />
    </a>
    <div>
    <a href="documentautomation.md#part1"><strong>Partie 1 : Stocker l’accord signé dans SharePoint avec Acrobat Sign</strong></a>
    </div>
  </td>
  <td>
    <a href="documentautomation.md#part2">
        <img alt="Partie 2 : Processus d’approbation automatisé pour obtenir une signature électronique avec Acrobat Sign" src="assets/documentautomation/AutomationPart2_thumb.jpg" />
    </a>
    <div>
    <a href="documentautomation.md#part2"><strong>Partie 2 : processus d’approbation automatisé pour obtenir une signature électronique avec Acrobat Sign</strong></a>
    </div>
  </td>
  <td>
   <a href="documentautomation.md#part3">
      <img alt="Partie 3 : ROC automatisée des documents avec les outils Adobe PDF" src="assets/documentautomation/AutomationPart3_thumb.jpg" />
   </a>
    <div>
    <a href="documentautomation.md#part3"><strong>Partie 3 : ROC de document automatisée avec les outils Adobe PDF</strong></a>
    </div>
  </td>
  <td>
   <a href="documentautomation.md#part4">
      <img alt="Partie 4 : Assemblage automatisé de documents avec Adobe PDF Tools" src="assets/documentautomation/AutomationPart4_thumb.jpg" />
   </a>
    <div>
    <a href="documentautomation.md#part4"><strong>Partie 4 : Assemblage automatisé de documents avec Adobe PDF Tools</strong></a>
    </div>
  </td>
</tr>
</table>

## Conditions préalables

* Familiarité avec Microsoft 365 et Power Automate
* Connaissances Acrobat Sign
* Compte Microsoft 365 avec accès à SharePoint et Power Automate (Basic pour Acrobat Sign, Premium pour Adobe PDF Tools)
* Compte de développeur Acrobat Sign abonnement Entreprise ou Acrobat Sign

**Exercices 1 et 2**

* Compte Acrobat Sign avec accès à l’API. Un compte Développeur ou un compte Entreprise.
* Site SharePoint accessible par Power Automate pour lequel vous disposez d’autorisations de modification. Un accès administrateur complet est recommandé.
* Exemple de document pour la demande d’approbation et la signature de la signature.

**Exercices 3 et 4**

Télécharger les matériaux [ici](https://github.com/benvanderberg/adobe-sign-pdftools-powerautomate-tutorial)

## Partie 1 : Stocker l’accord signé dans SharePoint avec Acrobat Sign {#part1}

Dans la première partie, vous utiliserez un modèle de flux Power Automate pour configurer un workflow automatisé qui enregistrera tous les accords signés sur votre site SharePoint.

1. Accédez à Power Automate.
1. Recherchez Acrobat Sign.

   ![Capture d’écran de la navigation vers Power Automate](assets/documentautomation/automation_1.png)

1. Sélectionnez **Enregistrer un accord Acrobat Sign terminé dans la bibliothèque SharePoint**.

   ![Capture d’écran de l’action Enregistrer un accord Acrobat Sign terminé pour la bibliothèque SharePoint](assets/documentautomation/automation_2.png)

1. Passez en revue l’écran et configurez les connexions nécessaires. Activez la connexion Acrobat Sign.
1. Cliquez sur le symbole bleu `+`.

   ![Capture d’écran de la connexion de flux Acrobat Sign et SharePoint](assets/documentautomation/automation_3.png)

1. Saisissez l’adresse e-mail de votre compte Acrobat Sign et cliquez sur le champ de mot de passe dans la nouvelle fenêtre.

   ![Capture d’écran de l’écran de connexion Acrobat Sign](assets/documentautomation/automation_4.png)

   Attendez un instant que l’Adobe vérifie votre compte.

   >[!NOTE]
   >
   >Cette vérification vous dirigera vers la connexion appropriée si vous utilisez une authentification unique Adobe ID ou notre authentification unique d’entreprise.

1. Terminer la connexion.
1. Cliquez sur **Continuer** pour accéder à l&#39;écran de modification Flux.
1. Nommez le déclencheur.

   ![Capture d&#39;écran du nom du déclencheur](assets/documentautomation/automation_5.png)

1. Configurez vos paramètres SharePoint.

   ![Capture d&#39;écran de la configuration de vos paramètres SharePoint](assets/documentautomation/automation_6.png)

   **Adresse du site :** votre site SharePoint
   **Chemin du dossier :** chemin d&#39;accès aux documents partagés que vous souhaitez utiliser
   **Nom du fichier :** acceptez la valeur par défaut
   **Contenu du fichier :** acceptez la valeur par défaut

1. Enregistrez le flux.

   ![Capture d&#39;écran de l&#39;icône Enregistrer](assets/documentautomation/automation_7.png)

1. Accédez à l’écran de présentation du flux avec la flèche bleue vers l’arrière. Vous allez tester ce flux dans la partie 2.

   ![Capture d&#39;écran de l&#39;écran de présentation du flux](assets/documentautomation/automation_8.png)

Vous testerez ce flux dans la partie suivante.

## Partie 2 : Processus d’approbation automatisé pour obtenir une signature électronique avec Acrobat Sign {#part2}

Dans la deuxième partie, nous construisons la première partie avec un flux plus robuste et testons les deux flux pour les voir en action.

1. Sélectionnez **Modèles** sur le côté gauche à partir de l’interface Power Automate.

   ![Capture d&#39;écran de la sélection des modèles](assets/documentautomation/automation_9.png)

1. Recherchez « approbation du responsable ».
1. Sélectionnez **Demander l&#39;approbation du responsable pour un fichier sélectionné**.

   ![Capture d&#39;écran de la sélection de l&#39;approbation du gestionnaire de demandes pour un fichier sélectionné](assets/documentautomation/automation_10.png)

   Passez en revue les connexions et ajoutez celles qui vous manquent.

   >[!NOTE]
   >
   >S’il s’agit du premier flux que vous effectuez avec les approbations, elles seront entièrement configurées lors de l’exécution du flux.

1. Cliquez sur **Continuer** pour accéder à l&#39;écran de modification du flux.

   Ce flux comporte de nombreuses étapes préconfigurées, notamment la vérification des erreurs et les étapes conditionnelles imbriquées.

1. Configurez **pour un fichier sélectionné** comme suit :
   **Adresse du site :** votre site SharePoint
   **Nom de la bibliothèque :** votre référentiel Documents
1. Ajoutez une entrée comme suit :
   **Type** : E-mail
   **Nom** : Adresse E-Mail Du Signataire

   ![Capture d&#39;écran de la configuration du flux](assets/documentautomation/automation_11.png)

1. Configurez les **propriétés du fichier Get:** comme suit :
   **Adresse du site :** votre site SharePoint
   **Nom de la bibliothèque :** votre référentiel Documents

1. Faites défiler vers le bas et recherchez **Si oui**.

   ![Capture d&#39;écran de la configuration Si oui](assets/documentautomation/automation_12.png)

1. Cliquez sur **Ajouter une action** dans la zone **Si oui** (pas la plus basse) pour ajouter les étapes à envoyer pour signature.

   ![Capture d&#39;écran de l&#39;ajout d&#39;une action dans la zone Si oui](assets/documentautomation/automation_13.png)

1. Recherchez **SharePoint obtenir le contenu du fichier** et choisissez **Obtenir le contenu du fichier**.

   ![Capture d&#39;écran de la zone de recherche](assets/documentautomation/automation_14.png)

1. Configurez **Obtenir le contenu du fichier** comme suit :

   ![Capture d&#39;écran de la configuration Obtenir le contenu du fichier](assets/documentautomation/automation_15.png)

   **Adresse du site :** votre site SharePoint.
   **Identificateur de fichier :** recherchez « identifiant » et choisissez Identificateur à l&#39;étape **Obtenir les propriétés du fichier**.
1. Recherchez « Adobe » et choisissez **Acrobat Sign** pour ajouter une autre action.

   ![Capture d&#39;écran du menu de recherche](assets/documentautomation/automation_16.png)

1. Entrez « upload » dans la zone de recherche pour Acrobat Sign et sélectionnez **Upload a document and get a document ID**.
1. Recherchez la variable dynamique **Nom** pour obtenir le nom de l&#39;élément/du document sélectionné dans le déclencheur sous **Nom de fichier**.
1. Cliquez sur **Expression** dans l&#39;assistant de variable sous **Contenu du fichier**.

   ![Capture d&#39;écran de l&#39;écran Télécharger un document et obtenir un ID de document](assets/documentautomation/automation_17.png)

1. Ajoutez une seule apostrophe, puis cliquez à nouveau sur **Contenu dynamique**, supprimez votre apostrophe, sélectionnez **Contenu du fichier**, puis cliquez sur **OK**.

   Assurez-vous qu’il n’y a pas d’apostrophes supplémentaires et qu’elles ressemblent à l’exemple ci-dessous.

   ![Capture d’écran de l’apparence de l’écran Contenu dynamique](assets/documentautomation/automation_18.png)

1. Recherchez « créer » dans la zone de recherche d’Acrobat Sign pour ajouter une autre action Acrobat Sign.
1. Sélectionnez **Créer un accord à partir d’un document chargé et l’envoyer pour signature**.

   ![Capture d&#39;écran de la recherche de create](assets/documentautomation/automation_19.png)

1. Configurez les informations requises :
Choisissez **Nom** dans l’assistant de variable dynamique dans **Nom de l’accord**.
Choisissez **Document ID** dans l&#39;assistant de variable dynamique dans **Document ID**.
Choisissez **E-mail du signataire** dans l’assistant de variable dynamique dans **E-mail du participant**.
Saisissez « 1 » dans **Ordre des participants**.
Choisissez **Signataire** dans le menu déroulant dans **Rôle de participant**.

   ![Capture d&#39;écran des informations requises](assets/documentautomation/automation_20.png)

1. **Économisez** le flux.

### Test de l’écoulement

Accédez au référentiel de documents de votre site SharePoint pour le tester.

1. Sélectionnez le document et choisissez **Automatiser** et le **Flux** que vous venez de créer.

   ![Capture d&#39;écran de la sélection du menu et du flux Automatiser](assets/documentautomation/automation_21.png)

1. Démarrez le flux pour valider les connexions (première exécution du flux uniquement).
1. Entrez un message positif à l&#39;approbateur dans **Message**.
1. Saisissez l’adresse électronique du signataire du document dans **E-mail du signataire**.
1. Cliquez sur **Exécuter le flux**.

L’approbateur configuré pour l’utilisateur démarrant le flux reçoit une demande d’approbation. Vous pouvez approuver par e-mail ou via le menu Actions Power Automate.
Une fois l’approbation obtenue, signez le document. Selon votre utilisateur et s’il est connecté à Sign, vous devrez peut-être ouvrir les fenêtres de signature dans une fenêtre de navigateur privé.

![Capture d&#39;écran de l&#39;ouverture dans une fenêtre de navigateur privée](assets/documentautomation/automation_22.png)

Terminez la signature, puis revenez dans votre dossier SharePoint.

![Capture d&#39;écran du dossier SharePoint](assets/documentautomation/automation_23.png)

## Partie 3 : ROC automatisée des documents avec les outils Adobe PDF {#part3}

Dans la troisième partie, vous apprendrez à automatiser la reconnaissance optique des caractères dans PDF lorsqu’ils sont importés dans Microsoft SharePoint. Cela résout un problème qui se produit avec les documents de PDF numérisés qui ne peuvent pas être recherchés dans SharePoint.

![Capture d&#39;écran du document PDF dans le navigateur](assets/documentautomation/automation_24.png)

### Configuration d’un dossier dans SharePoint

Accédez à Microsoft SharePoint où vous souhaitez stocker des documents.

1. Cliquez sur **+ Nouveau** pour créer un dossier appelé « Contrats traités ».
1. Cliquez sur **+ Nouveau** pour créer un dossier appelé « Anciens contrats ».

   ![Capture d&#39;écran des nouveaux dossiers](assets/documentautomation/automation_25.png)

Ces dossiers sont désormais référencés dans le cadre de votre flux Power Automate.

### Création d’un enchaînement à partir d’un modèle

1. Connectez-vous à l’adresse https://flow.microsoft.com.
1. Cliquez sur **Modèles** dans la barre latérale.

   ![Capture d&#39;écran de la sélection des modèles](assets/documentautomation/automation_26.png)

1. Sélectionnez **Convertir les fichiers nouvellement ajoutés en PDF textuel dans SharePoint**.
1. Cliquez sur le symbole **+** en regard des outils Adobe PDF.

   ![Capture d&#39;écran de la sélection du symbole +](assets/documentautomation/automation_27.png)

1. Accédez à https://www.adobe.com/go/powerautomate_getstarted_fr dans un nouvel onglet.
1. Cliquez sur **Démarrer**.

   ![Capture d&#39;écran du bouton Commencer](assets/documentautomation/automation_28.png)

1. Connectez-vous au moyen de votre ID Adobe.

   ![Capture d’écran de l’écran de connexion](assets/documentautomation/automation_29.png)

1. Saisissez le nom et la description des informations d&#39;identification et cliquez sur **Créer des informations d&#39;identification**.

   ![Capture d&#39;écran de l&#39;écran Créer des informations d&#39;identification](assets/documentautomation/automation_30.png)

   Laissez la fenêtre ouverte avec les informations d’identification. Vous devrez les saisir dans Microsoft Power Automate.

   ![Capture d&#39;écran de l&#39;onglet du navigateur pour rester ouvert](assets/documentautomation/automation_31.png)

1. Saisissez les informations d&#39;identification et cliquez sur **Créer dans Microsoft Power Automate**.

   ![Capture d&#39;écran de la saisie des informations d&#39;identification des outils de PDF](assets/documentautomation/automation_32.png)

1. Cliquez sur **Continuer**.

   ![Capture d&#39;écran de l&#39;emplacement où cliquer pour continuer](assets/documentautomation/automation_33.png)

   Vous pouvez maintenant voir une vue du workflow et vous devrez la configurer pour votre environnement.

1. Sélectionnez le champ Adresse du site et choisissez le site SharePoint que vous utilisez sous le déclencheur **Lorsqu&#39;un fichier est créé dans un dossier**.

   ![Capture d&#39;écran de la sélection Lors de la création d&#39;un fichier dans un déclencheur de dossier](assets/documentautomation/automation_34.png)

1. Cliquez sur l’icône de dossier pour accéder au dossier Anciens contrats situé sous ID de dossier.

   ![Capture d&#39;écran de la sélection du dossier Anciens contrats](assets/documentautomation/automation_35.png)

1. Modifiez l&#39;action **Créer un fichier** en bas de l&#39;enchaînement :

   Remplacez **Adresse du site** par votre adresse de site.
Spécifiez l’emplacement du dossier Contrats traités dans le chemin d’accès au dossier.

1. Cliquez sur **Enregistrer** dans le coin supérieur droit.
1. Cliquez sur **Tester**.
1. Sélectionnez **Manuellement**.
1. Cliquez sur **Tester**.

   ![Capture d&#39;écran du flux de test](assets/documentautomation/automation_36.png)

### Essayer votre nouveau flux

1. Accédez au dossier Anciens contrats dans SharePoint.
1. Accédez à E03/Anciens contrats dans les fichiers d’exercice que vous avez téléchargés.
1. Copiez les fichiers ReleaseFormXX.pdf dans le dossier Old Contracts dans SharePoint.

   ![Capture d&#39;écran de la copie des fichiers](assets/documentautomation/automation_37.png)

Désormais, si vous accédez au dossier Contrats traités, vous pouvez voir vos PDF disponibles après que le flux a eu quelques instants pour s’exécuter. Si vous ouvrez les PDF, vous constatez que le texte peut être sélectionné.
En outre, SharePoint indexe le document, ce qui vous permet d’effectuer des recherches dans le contenu de vos documents à partir de la barre de recherche de SharePoint.

## Partie 4 : Assemblage automatisé de documents avec Adobe PDF Tools {#part4}

Dans la quatrième partie, vous apprendrez à fusionner de nombreux documents en fonction des informations fournies lors de la sélection et du démarrage d’un flux à partir de Microsoft SharePoint. Dans ce scénario, le flux :

* Demandez des informations pour choisir les éléments à inclure dans un pack pour un client.
* En fonction des informations fournies, il fusionne de nombreux documents. Ces documents comprennent une page de couverture et des livres blancs facultatifs.
* Le document fusionné est enregistré dans SharePoint.

### Importation de fichiers d’exercice dans SharePoint

1. Ouvrez le dossier E04 dans les fichiers Exercice.
1. Importez les dossiers Devis, Modèles et Documents générés dans SharePoint.

   ![Capture d&#39;écran de l&#39;importation de dossiers](assets/documentautomation/automation_38.png)

Ces dossiers seront utilisés à titre de référence. En particulier, vous utiliserez le fichier Proposal.docx pour votre devis.

Dans le dossier Templates, il existe un dossier Covers qui comprend des designs de page de garde pour différentes villes. Il existe également un dossier de livres blancs contenant des livres blancs supplémentaires facultatifs qui seront joints à la fin s’ils sont sélectionnés.

### Importation du flux dans Microsoft Power Automate

1. Connexion à Microsoft Power Automate (https://flow.microsoft.com).
1. Cliquez sur **Mes flux**.

   ![Capture d’écran de l’emplacement de sélection de mes flux](assets/documentautomation/automation_39.png)

1. Cliquez sur **Importer**.

   ![Capture d&#39;écran de l&#39;écran d&#39;importation](assets/documentautomation/automation_40.png)

1. Cliquez sur **Télécharger** et choisissez le dossier GenerateProposal_20210311231623.zip dans E04/Flows/.

   ![Capture d&#39;écran de la sélection du dossier](assets/documentautomation/automation_41.png)

1. Cliquez sur **Importer**.

1. Cliquez sur l&#39;icône en forme de clé sous Action en regard de **Envoyer la proposition au client**.

   ![Capture d&#39;écran de l&#39;icône en forme de clé à molette](assets/documentautomation/automation_42.png)

1. Sélectionnez **Créer en tant que nouveau** sous Configuration.
1. Définissez le nom du flux sous Nom de la ressource.
1. Cliquez sur **Enregistrer**.

   Répétez cette opération pour les autres ressources associées et sélectionnez votre connexion.

   ![Capture d&#39;écran de l&#39;enregistrement du fichier](assets/documentautomation/automation_43.png)

1. Cliquez sur **Importer** après avoir établi toutes vos connexions.

### Définir pour un fichier sélectionné

Une fois l’enchaînement créé, procédez comme suit :

1. Cliquez sur **Modifier**.

   ![Capture d&#39;écran de l&#39;emplacement où sélectionner modifier](assets/documentautomation/automation_44.png)

1. Sélectionnez le déclencheur **Pour un fichier sélectionné**.

   Ajoutez votre site SharePoint à l’adresse du site.
Ajoutez votre bibliothèque dans la bibliothèque.

   ![Capture d&#39;écran du déclencheur terminé](assets/documentautomation/automation_45.png)

### Set templateFolderPath

1. Cliquez sur la variable templateFolderPath.
1. Définissez le chemin d’accès du dossier Modèles situé dans le site SharePoint que vous avez importé.

### Définir le contenu du fichier de récupération de couverture

1. Cliquez sur l&#39;action **Couvrir**, ce qui étend la portée.
1. Développer **Couverture : Obtenir le contenu du fichier**.

   Définissez l’adresse du site sur votre site SharePoint.

   ![Capture d&#39;écran de la couverture étendue](assets/documentautomation/automation_46.png)



### Définir le fichier sélectionné

1. Développez l&#39;action de portée **Fichier sélectionné**.

   Remplacez l&#39;adresse du site et le nom de la bibliothèque par votre site et votre bibliothèque SharePoint respectivement sous **Obtenir les propriétés du fichier**.
Remplacez l&#39;adresse du site par votre site SharePoint sous **Obtenir le contenu du fichier**.

   ![Capture d&#39;écran de l&#39;action développée Fichier sélectionné](assets/documentautomation/automation_47.png)

### Définition de livres blancs

1. Cliquez sur **Livres blancs**.
1. Développer la **condition : ajoutez un livre blanc**.

   ![Capture d&#39;écran de la condition Ajouter un livre blanc étendue](assets/documentautomation/automation_48.png)

1. Développez **Livre blanc 1 : obtenir le contenu du fichier à l&#39;aide du chemin**.
Modifiez l&#39;adresse du site SharePoint spécifié.

Répétez les mêmes étapes pour la **condition : ajouter un livre blanc 2**.

### Définir Créer un fichier

1. Développez **Créer un fichier**.

   Modifiez l’adresse du site et le chemin du dossier vers le site SharePoint et le chemin du dossier Documents générés.

1. Cliquez sur **Enregistrer**.

### Testez votre flux

1. Accédez au dossier Devis dans SharePoint.
1. Sélectionnez le dossier Devis.docx.

   ![Capture d&#39;écran de la sélection du dossier de devis](assets/documentautomation/automation_49.png)

1. Sélectionnez votre flux dans le menu **Automatiser**.

   ![Capture d&#39;écran de Sélection du menu Automatisation](assets/documentautomation/automation_50.png)

1. Cliquez sur **Continuer** pour commencer le flux.

   ![Capture d&#39;écran de la sélection du bouton Continuer](assets/documentautomation/automation_51.png)

1. Choisissez votre couverture et les livres blancs que vous souhaitez ajouter.
1. Cliquez sur **Exécuter le flux**.

   ![Capture d&#39;écran du bouton Exécuter le flux](assets/documentautomation/automation_52.png)

Accédez au dossier Générer des documents. Votre fichier de PDF généré devrait maintenant s’afficher.

![Capture d&#39;écran du répertoire SharePoint avec le nouveau fichier de PDF](assets/documentautomation/automation_53.png)

### Ajout de Protect et d’autres actions au flux

Maintenant que vous avez réussi à créer un flux, vous allez modifier votre flux pour chiffrer le document de mot de PDF avec un mot de passe. Cette section explique également comment utiliser d’autres actions.

1. Revenez à la fin de votre flux.
1. Cliquez sur le symbole **+** entre **Fusionner les PDF** et **Créer un fichier**.

   ![Capture d&#39;écran de l&#39;emplacement où sélectionner le symbole +](assets/documentautomation/automation_54.png)

1. Sélectionnez **Ajouter une action**.
1. Recherchez « Outils Adobe PDF ».

   ![Capture d&#39;écran de la recherche d&#39;Adobe PDF](assets/documentautomation/automation_55.png)

1. Sélectionnez **Protect PDF dans Affichage**.
1. Utilisez le contenu dynamique pour définir le champ Nom de fichier sur **Nom de fichier du PDF à partir du PDF de fusion**.

   ![Capture d&#39;écran du contenu dynamique](assets/documentautomation/automation_56.png)

   Dans le déclencheur, un champ Mot de passe fait partie du formulaire d’initiation. Nous pouvons l&#39;utiliser ici.

1. Recherchez le **champ Mot de passe** à l&#39;aide du contenu dynamique, puis placez-le dans le champ Mot de passe.

   ![Capture d&#39;écran de la recherche de mot de passe](assets/documentautomation/automation_57.png)

1. Utilisez le contenu dynamique pour le définir sur **Contenu du fichier de PDF à partir de Fusionner les PDF** dans le champ Contenu du fichier.
1. Modifiez **Créer un fichier** pour obtenir le contenu du fichier à partir du PDF Protect plutôt que de Fusionner les PDF.
1. Développez **Créer un fichier**.
1. Effacez le champ Contenu du fichier.
1. Utilisez le contenu dynamique pour importer le **contenu du fichier PDF** à partir du **PDF Protect à partir de l&#39;affichage**.

### Testez votre flux

1. Accédez au dossier Devis dans SharePoint.
1. Sélectionnez Devis.docx.

   ![Capture d&#39;écran de la sélection du dossier Devis](assets/documentautomation/automation_58.png)

1. Sélectionnez **Automatiser** pour choisir votre flux.

   ![Capture d&#39;écran de la sélection d&#39;Automate dans le menu](assets/documentautomation/automation_59.png)

1. Cliquez sur **Continuer** pour commencer le flux.

   ![Capture d&#39;écran de la sélection Continuer](assets/documentautomation/automation_60.png)

1. Choisissez la couverture et les livres blancs que vous souhaitez ajouter.
1. Définissez le champ Mot de passe sur le mot de passe que vous souhaitez définir.
1. Cliquez sur **Exécuter le flux**.

   ![Capture d&#39;écran des fichiers sélectionnés et bouton Exécuter le flux](assets/documentautomation/automation_61.png)

1. Accédez au dossier Générer des documents.
Votre fichier de PDF généré devrait s’afficher. Ouvrez le fichier de mot de PDF qui vous invite à saisir votre mot de PDF.

   ![Capture d&#39;écran du PDF généré dans le répertoire SharePoint](assets/documentautomation/automation_62.png)
