---
title: Mises à jour importantes du produit Acrobat DC pour les clients ETLA
description: Découvrez les modifications importantes apportées aux droits Acrobat DC dans les offres ETLA (contrat de licence d’entreprise) entre août 2020 et le 20 novembre 2020
role: Admin
product: adobe acrobat
level: Intermediate
thumbnail: KT-7269.jpg
exl-id: 1a8d3f7d-96a4-4811-b4e9-9c55287b92ea
source-git-commit: 018cbcfd1d1605a8ff175a0cda98f0bfb4d528a8
workflow-type: tm+mt
source-wordcount: '740'
ht-degree: 4%

---

# Mises à jour importantes du produit Acrobat DC pour les clients ETLA

[!DNL Adobe Sign Individual] (également appelé Adobe Sign Pro) ne sera plus provisionné de tous les droits Acrobat DC inclus dans les offres ETLA (contrat de licence d’entreprise) qu’à compter du mois d’août 2020 et continuera jusqu’au 20 novembre 2020. [!DNL Adobe Sign Individual] ne fournit pas de fonctionnalités adaptées aux exigences de l’entreprise et doit être remplacé par Adobe Sign Enterprise pour les clients Entreprise. Cela inclut Acrobat DC sous licence en tant qu’application autonome et Acrobat DC sous licence dans le cadre de Creative Cloud abonnement Entreprise - Toutes les applications.

Accès à [!DNL Adobe Sign Individual] est disponible dans Acrobat via le **Adobe Sign** ou le bouton **Fill &amp; Sign** (Demander des signatures).

![[!DNL Adobe Sign Individual] accès dans Acrobat DC](../assets/Deploy_SignEntitle1.png)

Si vous n’avez pas mis à jour Acrobat DC vers la dernière version, l’outil peut être étiqueté &quot;Send for Signature&quot;.

## Pourquoi ne provisionnons-nous pas ceci ?

[En octobre 2018, nous avons publié un tout nouveau Acrobat DC](https://news.adobe.com/news/news-details/2018/Adobe-Redefines-What-Is-Possible-With-PDF-With-All-New-Acrobat-DC). Cette dernière version inclut de nouveaux outils et fonctionnalités pour mieux utiliser les PDF sur les appareils mobiles, le web et les ordinateurs, ainsi que de tout nouveaux outils de collaboration. En tant qu’abonné à Acrobat DC, vous devriez déjà avoir accès à ces remarquables fonctionnalités. Une autre mise à jour majeure que nous avons publiée concerne notre solution de signature électronique Adobe Sign.

Avant la version d’octobre 2018, les utilisateurs d’Acrobat DC pouvaient envoyer des documents pour signature électronique à l’aide des outils Acrobat étiquetés &quot;Fill &amp; Sign&quot; (ou &quot;Adobe Sign&quot; ou &quot;Send for Signature&quot;) qui étaient fournis avec [!DNL Adobe Sign Individual] droits.

Bien que cette option ait fourni un excellent moyen de recueillir des signatures électroniques, nous désaffectons la mise en service [!DNL Adobe Sign Individual] car il ne fournit pas les fonctionnalités de niveau Enterprise disponibles via Adobe Sign Enterprise, telles que :

* Possibilité de gérer de manière centralisée les utilisateurs autorisés à envoyer des accords ou à signer
* Autorisation des administrateurs à gérer les accords envoyés et utilisés dans l’organisation
* Des contrôles précis pour gérer les signatures électroniques à l’échelle de l’entreprise

En outre, Adobe Sign Enterprise offre davantage de fonctionnalités par rapport à ce qui était disponible dans le [!DNL Adobe Sign Individual] , y compris, mais sans s&#39;y limiter :

* Administration
   * Authentification unique activée
   * Délégation de compte
* Intégrations
   * Intégrations d’entreprise prédéfinies avec Dropbox, Salesforce, Workday, etc.
   * Adobe Sign est la solution de signature électronique de référence dans le monde [Microsoft](https://acrobat.adobe.com/us/en/business/integrations/microsoft.html) portfolio d’entreprise, comprenant Office 365, SharePoint, Dynamics, Teams et Flow
* Personnalisation et optimisation
   * Authentification de signature électronique avancée, vérification avancée de l’identité des signataires basée sur une pièce d’identité, conception de workflows, prise en charge linguistique avancée, etc.

Adobe Sign est la solution de référence au niveau mondial pour la collecte de signatures conformes à la loi. Conçu de A à Z pour répondre aux besoins de signature électronique de votre entreprise, Adobe Sign offre des outils conçus pour les administrateurs IT afin que vous et vos utilisateurs utilisiez des signatures électroniques entièrement conformes aux diverses réglementations régionales et sectorielles. Veuillez consulter [ici](https://helpx.adobe.com/fr/enterprise/using/adobe-sign-for-enterprise.html) pour plus d’informations sur la gestion de Sign via [Adobe Admin Console](https://helpx.adobe.com/fr/enterprise/using/admin-console.html).

Contactez votre interlocuteur Adobe pour savoir comment continuer à fournir des fonctionnalités de signature électronique à votre entreprise via notre plateforme documentaire digitale élargie qui inclut Acrobat DC et Adobe Sign Enterprise.

## Accès aux accords existants

Les utilisateurs pourront toujours accéder aux accords envoyés avant cette action via Adobe Document Cloud en se connectant avec leur Adobe ID à l’adresse https://documentcloud.adobe.com. Si la migration de cet utilisateur vers Sign Enterprise est planifiée, il devra suivre ces instructions [instructions](https://helpx.adobe.com/fr/sign/kb/how-to-download-signed-documents---adobe-sign.html).

## Expérience Acrobat DC sans [!DNL Sign Individual] droit

Les utilisateurs disposant de droits Adobe Sign Enterprise pourront envoyer des accords dans Acrobat à l’aide du portail Adobe Sign ou [!UICONTROL Fill &amp; Sign] (Demander des signatures).
Les utilisateurs qui ne disposent pas de droits Adobe Sign Enterprise ne pourront pas envoyer de nouveaux accords et recevront un message d’erreur. Le graphique ci-dessous décrit les résultats possibles.

![Message d’erreur pour l’expérience Acrobat DC](../assets/Deploy_SignEntitle2.png)

## Expérience web Adobe Document Cloud sans droit individuel Sign

Les utilisateurs pourront se connecter à https://documentcloud.adobe.com/ pour accéder aux accords qui ont été envoyés et les télécharger avant de désactiver les droits individuels Adobe Sign.

![Message d’erreur pour l’expérience web Document Cloud](../assets/Deploy_SignEntitle3.png)

## Pour plus d’informations, consultez les pages ci-dessous :

* [Connexion à Adobe Document Cloud](https://helpx.adobe.com/document-cloud/help/sign-in.html)
* [Gestion des fichiers (où se trouvent mes fichiers ?)](https://helpx.adobe.com/document-cloud/help/manage-files.html)
* [Utilisation [!UICONTROL Acrobat Customization Wizard] pour la configuration](https://www.adobe.com/devnet-docs/acrobatetk/tools/Wizard/WizardDC/index.html)
* [Présentation de [!UICONTROL Admin Console]](https://helpx.adobe.com/enterprise/using/admin-console.html)
* [Gestion d’Adobe Sign sur le [!UICONTROL Admin Console]](https://helpx.adobe.com/enterprise/using/adobe-sign-for-enterprise.html)

**Révisions** 20 mai 2020 ; article original - août 2019
