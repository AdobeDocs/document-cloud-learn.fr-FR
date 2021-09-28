---
title: Mises à jour importantes des produits Acrobat DC pour les clients ETLA
description: Découvrez les modifications importantes apportées aux droits Acrobat DC inclus dans les offres ETLA (Enterprise Term License Agreement) de début août 2020 à fin novembre 2020.
role: Admin
product: adobe acrobat
level: Intermediate
thumbnail: KT-7269.jpg
exl-id: 1a8d3f7d-96a4-4811-b4e9-9c55287b92ea
source-git-commit: 018cbcfd1d1605a8ff175a0cda98f0bfb4d528a8
workflow-type: tm+mt
source-wordcount: '740'
ht-degree: 3%

---

# Mises à jour importantes des produits Acrobat DC pour les clients ETLA

[!DNL Adobe Sign Individual] (également connu sous le nom d’Adobe Sign Pro) seront désactivés de tous les droits Acrobat DC inclus dans l’offre ETLA (Enterprise Term License Agreement) à compter d’août 2020 et continueront jusqu’au 20 novembre 2020. [!DNL Adobe Sign Individual] ne fournit pas de fonctionnalités de niveau entreprise et doit être remplacé par Adobe Sign Enterprise pour les clients d’entreprise. Cela inclut la licence Acrobat DC en tant qu’application autonome et la licence Acrobat DC en tant que membre du Creative Cloud pour entreprise - Toutes les applications.

L&#39;accès à [!DNL Adobe Sign Individual] est disponible dans Acrobat via l&#39;outil **Adobe Sign** ou l&#39;outil **Fill &amp; Sign** (Demander des signatures).

![[!DNL Adobe Sign Individual] accès dans Acrobat DC](../assets/Deploy_SignEntitle1.png)

Si vous n’avez pas mis à jour Acrobat DC vers la dernière version, l’outil peut être étiqueté &quot;Send for Signature&quot;.

## Pourquoi désapprovisionnons-nous cela ?

[En octobre 2018, nous avons sorti un tout nouveau Acrobat DC](https://news.adobe.com/news/news-details/2018/Adobe-Redefines-What-Is-Possible-With-PDF-With-All-New-Acrobat-DC). Cette dernière version comprend de nouveaux outils et fonctionnalités pour une meilleure utilisation des fichiers PDF sur les appareils mobiles, le web et les postes de travail, ainsi que de tout nouveaux outils de collaboration. En tant qu’abonné à Acrobat DC, vous devriez déjà disposer de ces fonctionnalités exceptionnelles. Une autre mise à jour majeure que nous avons publiée a été notre solution de signature électronique Adobe Sign.

Avant la version d’octobre 2018, les utilisateurs d’Acrobat DC ont pu envoyer des documents pour signature électronique à l’aide d’outils dans Acrobat étiquetés &quot;Fill &amp; Sign&quot; (ou &quot;Adobe Sign&quot; ou &quot;Send for Signature&quot;) qui étaient fournis avec le droit [!DNL Adobe Sign Individual].

Bien que cette option ait fourni un excellent moyen de capturer des signatures électroniques, nous désactivons [!DNL Adobe Sign Individual], car elle ne fournit pas la fonctionnalité de niveau Enterprise disponible par le biais d’Adobe Sign Enterprise, telle que :

* Possibilité de gérer de manière centralisée les utilisateurs autorisés à envoyer des accords ou à les signer
* Autoriser les administrateurs à gérer les accords envoyés et utilisés dans l’ensemble de l’organisation
* Fourniture de contrôles détaillés pour la gestion des signatures électroniques dans l’ensemble de l’organisation

En outre, Adobe Sign Enterprise offre davantage de fonctionnalités par rapport à ce qui était disponible dans le droit [!DNL Adobe Sign Individual], notamment, mais sans s&#39;y limiter :

* Administration
   * Authentification unique
   * Délégation de compte
* Intégrations
   * Intégrations d’entreprise prédéfinies avec Dropbox, Salesforce, Workday, etc.
   * Adobe Sign est la solution de signature électronique préférée dans le portefeuille d’entreprises [Microsoft](https://acrobat.adobe.com/us/en/business/integrations/microsoft.html), y compris Office 365, SharePoint, Dynamics, Teams et Flow.
* Personnalisation et optimisation
   * Authentification améliorée des signatures électroniques, vérification avancée de l’identité des signataires basée sur l’ID, concepteur de flux de travaux, prise en charge linguistique avancée, etc.

Adobe Sign est la solution mondialement reconnue par le secteur pour capturer des signatures conformes à la loi. Adobe Sign a été entièrement conçu pour répondre aux besoins de votre organisation en matière de signature électronique. Grâce à des outils conviviaux pour les administrateurs informatiques, vous et vos utilisateurs utiliserez des signatures électroniques conformes aux diverses réglementations régionales et industrielles en matière de signature électronique. Pour plus d’informations sur la gestion de Sign via [Adobe Admin Console](https://helpx.adobe.com/fr/enterprise/using/admin-console.html), consultez [ici](https://helpx.adobe.com/fr/enterprise/using/adobe-sign-for-enterprise.html).

Contactez votre Adobe pour discuter de la façon dont vous pouvez continuer à fournir des fonctionnalités de signature électronique à votre organisation via notre plate-forme de documents numériques plus large qui inclut Acrobat DC et Adobe Sign Enterprise.

## Accès aux accords existants

Les utilisateurs pourront toujours accéder aux accords envoyés avant cette action via Adobe Document Cloud en se connectant avec leur Adobe ID à l’adresse https://documentcloud.adobe.com. Si cet utilisateur est planifié pour la migration vers Sign Enterprise, il devra suivre les [instructions](https://helpx.adobe.com/sign/kb/how-to-download-signed-documents---adobe-sign.html) suivantes.

## Expérience Acrobat DC sans droits [!DNL Sign Individual]

Les utilisateurs disposant de droits Adobe Sign Enterprise pourront envoyer des accords dans Acrobat à l’aide de l’outil Adobe Sign ou [!UICONTROL Fill &amp; Sign] (Demander des signatures).
Les utilisateurs qui ne disposent pas de droits Adobe Sign Enterprise ne pourront pas envoyer de nouveaux accords et recevront un message d’erreur. Le graphique ci-dessous décrit les résultats possibles.

![Message d’erreur pour l’expérience Acrobat DC](../assets/Deploy_SignEntitle2.png)

## Expérience Web Adobe Document Cloud sans droit individuel Sign

Les utilisateurs pourront se connecter à l’adresse https://documentcloud.adobe.com/ pour accéder aux accords qui ont été envoyés et les télécharger avant de désactiver les droits de l’utilisateur Adobe Sign Individual.

![Message d’erreur pour l’expérience web Document Cloud](../assets/Deploy_SignEntitle3.png)

## Pour plus d’informations, consultez les pages ci-dessous :

* [Connexion à Adobe Document Cloud](https://helpx.adobe.com/document-cloud/help/sign-in.html)
* [Gestion des fichiers (Où sont mes fichiers ?)](https://helpx.adobe.com/document-cloud/help/manage-files.html)
* [Utilisation de  [!UICONTROL Acrobat Customization ] Wizard pour la configuration](https://www.adobe.com/devnet-docs/acrobatetk/tools/Wizard/WizardDC/index.html)
* [Présentation du  [!UICONTROL Admin Console]](https://helpx.adobe.com/enterprise/using/admin-console.html)
* [Gestion d&#39;Adobe Sign sur le  [!UICONTROL Admin Console]](https://helpx.adobe.com/enterprise/using/adobe-sign-for-enterprise.html)

**Révisions** le 20 mai 2020; post original - août 2019
