---
title: Création de signatures électroniques et d’expériences documentaires incorporées
description: Découvrez comment utiliser les API Acrobat Sign pour incorporer la signature électronique et les expériences documentaires dans vos plateformes web et systèmes de gestion de contenu et de documents
role: User, Developer
level: Intermediate
topic: Integrations
thumbnail: KT-7489.jpg
kt: 7489
exl-id: db300cb9-6513-4a64-af60-eadedcd4858e
source-git-commit: e02b1250de94ec781e7984c6c146dbae993f5d31
workflow-type: tm+mt
source-wordcount: '928'
ht-degree: 3%

---

# Créer des expériences documentaires et de signature électronique intégrées

Découvrez comment utiliser les API Acrobat Sign pour incorporer la signature électronique et les expériences documentaires dans vos plateformes web et systèmes de gestion de contenu et de documents. Ce tutoriel pratique comporte quatre parties, décrites dans les liens ci-dessous :

<table style="table-layout:fixed">
<tr>
  <td>
    <a href="embeddedesignature.md#part1">
        <img alt="Ce dont vous aurez besoin" src="assets/embeddedesignature/EmbedPart1_thumb.png" />
    </a>
    <div>
    <a href="embeddedesignature.md#part1"><strong>Partie 1 : Ce dont vous aurez besoin</strong></a>
    </div>
  </td>
  <td>
    <a href="embeddedesignature.md#part2">
        <img alt="Partie 2 : Code faible/sans — la puissance des formulaires web" src="assets/embeddedesignature/EmbedPart2_thumb.png" />
    </a>
    <div>
    <a href="embeddedesignature.md#part2"><strong>Partie 2 : Code faible/sans — la puissance des formulaires web</strong></a>
    </div>
  </td>
  <td>
   <a href="embeddedesignature.md#part3">
      <img alt="Partie 3 : Envoi d’un accord avec un formulaire, fusion des données" src="assets/embeddedesignature/EmbedPart3_thumb.png" />
   </a>
    <div>
    <a href="embeddedesignature.md#part3"><strong>Partie 3 : Envoi d’un accord avec un formulaire et fusion des données</strong></a>
    </div>
  </td>
  <td>
   <a href="embeddedesignature.md#part4">
      <img alt="Partie 4 : Intégrer l’expérience de signature, les redirections, etc." src="assets/embeddedesignature/EmbedPart4_thumb.png" />
   </a>
    <div>
    <a href="embeddedesignature.md#part4"><strong>Partie 4 : Intégrer l’expérience de signature, les redirections, etc.</strong></a>
    </div>
  </td>
</tr>
</table>

## Partie 1 : Ce dont vous aurez besoin {#part1}

Dans la première partie, vous apprendrez à utiliser tout ce dont vous avez besoin pour les parties 2 à 4. Commençons par obtenir les identifiants d’API.

* [Compte développeur Acrobat Sign](https://acrobat.adobe.com/fr/fr/sign/developer-form.html)
* [Code de démarrage](https://github.com/benvanderberg/adobe-sign-api-tutorial)
* [Code VS (ou éditeur de votre choix)](https://code.visualstudio.com)
* Python 3.x
   * Mac — Homebrew
   * Linux — Programme d&#39;installation intégré
   * Windows — Chocolatey
   * Tous — https://www.python.org/downloads/

## Partie 2 : Code faible/sans — la puissance des formulaires web {#part2}

Dans la deuxième partie, vous découvrirez l’option low/no-code lorsque vous utilisez des formulaires web. Il est toujours judicieux d’éviter d’écrire du code au début.

1. Accédez à Acrobat Sign avec votre compte développeur.
1. Cliquez **Publication d’un formulaire web** sur la page d’accueil.

   ![Capture d’écran page d’accueil Acrobat Sign](assets/embeddedesignature/embed_1.png)

1. Créez votre accord.

   ![Capture d’écran de la création d’un formulaire web](assets/embeddedesignature/embed_2.png)

1. Incorporez votre accord dans une page de HTML plate.
1. Essayez d&#39;ajouter des paramètres de requête de manière dynamique.

   ![Capture d&#39;écran de l&#39;ajout de paramètres](assets/embeddedesignature/embed_3.png)

## Partie 3 : Envoi d’un accord avec un formulaire et fusion des données {#part3}

Dans la troisième partie, vous allez créer des accords de manière dynamique.

Tout d&#39;abord, vous devez établir l&#39;accès. Avec Acrobat Sign, il existe deux façons de se connecter via l’API. Jetons OAuth et clés d’intégration. À moins que vous n’ayez une raison très spécifique d’utiliser OAuth avec votre application, vous devez d’abord explorer les clés d’intégration.

1. Sélectionner **Clé d’intégration** dans le **Informations API** sous le menu **Compte** dans Acrobat Sign.

   ![Capture d’écran indiquant où trouver la clé d’intégration](assets/embeddedesignature/embed_4.png)

Maintenant que vous avez accès à l’API et pouvez interagir avec celle-ci, découvrez ce que vous pouvez faire avec elle.

1. Accédez à l’onglet [Méthodes de l’API REST Acrobat Sign version 6](http://adobesign.com/public/docs/restapi/v6).

   ![Capture d’écran des méthodes de navigation dans l’API REST Acrobat Sign version 6](assets/embeddedesignature/embed_5.png)

1. Utilisez le jeton en tant que valeur &quot;porteur&quot;.

   ![Capture d’écran de la valeur du porteur](assets/embeddedesignature/embed_6.png)

Pour envoyer votre premier accord, il est préférable de comprendre comment utiliser l’API.

1. Créez un document temporaire et envoyez-le.

>[!NOTE]
>
>Les appels de requête basés sur JSON ont une option &quot;Modèle&quot; et &quot;Schéma de modèle minimal&quot;. Cela donne des spécifications et une charge utile minimale définie.

![Capture d&#39;écran de la création d&#39;un document temporaire](assets/embeddedesignature/embed_7.png)

Après avoir envoyé un accord pour la première fois, vous êtes prêt à ajouter la logique. Il est toujours judicieux de créer des assistants pour limiter les répétitions. Voici quelques exemples :

**Validation**

![Capture d&#39;écran de la logique de validation](assets/embeddedesignature/embed_8.png)

**En-têtes/authentification**

![Capture d&#39;écran de la logique headers/auth](assets/embeddedesignature/embed_9.png)

**URI de base**

![Capture d&#39;écran de la logique URI de base](assets/embeddedesignature/embed_10.png)

Soyez conscient de l’emplacement des documents transitoires dans le grand schéma de l’écosystème Sign.
Transitoire -> Accord temporaire -> Modèle -> Accord temporaire -> Widget -> Accord

Cet exemple utilise un modèle comme source de document. C’est généralement le meilleur itinéraire, sauf si vous avez une bonne raison de générer dynamiquement des documents pour signature (par exemple, génération de code hérité ou de documents).

Le code est assez simple ; il utilise un document de bibliothèque (modèle) pour la source du document. Les premier et second signataires sont assignés dynamiquement. La `IN_PROCESS` état signifie que le document est envoyé immédiatement. En outre, `mergeFieldInfo` permet de remplir les champs de manière dynamique.

![Capture d&#39;écran du code pour ajouter dynamiquement des signatures](assets/embeddedesignature/embed_11.png)

## Partie 4 : Intégrer l’expérience de signature, les redirections, etc. {#part4}

Dans de nombreux scénarios, vous pouvez autoriser le participant déclencheur à signer immédiatement un accord. Cette fonction est utile pour les applications orientées client et les bornes interactives.

Si vous ne souhaitez pas que le premier e-mail d’envoi se déclenche, un moyen simple consiste à gérer le comportement en modifiant l’appel d’API.

![Capture d’écran du code pour ne pas déclencher l’envoi du courrier électronique](assets/embeddedesignature/embed_12.png)

Voici comment contrôler la redirection post-signature :

![Capture d’écran du code pour contrôler la redirection post-signature](assets/embeddedesignature/embed_13.png)

Après avoir mis à jour le processus de création de l’accord, l’étape finale consiste à générer l’URL de signature. Cet appel est également assez simple et génère une URL qu’un signataire peut utiliser pour accéder à sa partie du processus de signature.

![Capture d’écran du code permettant de générer l’URL du signataire](assets/embeddedesignature/embed_14.png)

>[!NOTE]
>
>Notez que l’appel de création d’accord est techniquement asynchrone. Cela signifie qu’un appel d’accord &quot;POST&quot; peut être effectué, mais que l’accord n’est pas encore prêt. La meilleure pratique consiste à établir une boucle de nouvelle tentative. Utilisez une nouvelle tentative ou n’importe quelle autre bonne pratique pour votre environnement.

![Capture d&#39;écran indiquant qu&#39;il est recommandé d&#39;établir une boucle de nouvelle tentative](assets/embeddedesignature/embed_15.png)

Quand tout est mis en place, la solution est assez simple. Vous créez un accord, puis générez une URL de signature sur laquelle le signataire peut cliquer pour commencer le rituel de signature.

### Rubriques supplémentaires

* [Événements JS](https://www.adobe.io/apis/documentcloud/sign/docs.html#!adobedocs/adobe-sign/master/events.md)
* Événements Webhook
   * [API REST](https://sign-acs.na1.echosign.com/public/docs/restapi/v6#!/webhooks/createWebhook)
   * [Webhooks dans Acrobat Sign v6](https://www.adobe.io/apis/documentcloud/sign/docs.html#!adobedocs/adobe-sign/master/webhooks.md)
* [Réactiver les e-mails de demande (avec événements)](https://sign-acs.na1.echosign.com/public/docs/restapi/v6#!/agreements/updateAgreement)
* [Remplacer le délai d’expiration par une nouvelle tentative](https://stackoverflow.com/questions/23267409/how-to-implement-retry-mechanism-into-python-requests-library)

   <br> 
* Rappels personnalisés
   * Avec la création initiale

      ![Capture d’écran de la navigation vers Power Automate](assets/embeddedesignature/embed_16.png)

   * Ou ajoutez-en un [en vol](https://sign-acs.na1.echosign.com/public/docs/restapi/v6#!/agreements/createReminderOnParticipant)

## Ressources supplémentaires

http://bit.ly/Summit21-T126

Inclut :
* Compte développeur Acrobat Sign
* Documentation des API Acrobat Sign
* Exemple de code
* Code Visual Studio
* Python
