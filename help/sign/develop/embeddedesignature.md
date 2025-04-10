---
title: Création d’expériences de signature électronique et de document intégrées
description: Découvrez comment utiliser les API Acrobat Sign pour intégrer des expériences de signature électronique et de document dans vos plateformes web et systèmes de gestion de contenu et de document
feature: Integrations, Workflow
role: Developer
level: Intermediate
topic: Integrations
jira: KT-7489
thumbnail: KT-7489.jpg
kt: 7489
exl-id: db300cb9-6513-4a64-af60-eadedcd4858e
source-git-commit: 0a299592f0616988b6208fc98d3140f4ac22057e
workflow-type: tm+mt
source-wordcount: '832'
ht-degree: 0%

---

# Création d’expériences de signature électronique et de document intégrées

Découvrez comment utiliser les API Acrobat Sign pour intégrer des expériences de signature électronique et de document dans vos plateformes web et systèmes de gestion de contenu et de document. Ce tutoriel pratique se divise en quatre parties.

## Partie 1 : Ce dont vous avez besoin

Dans la partie 1, découvrez comment prendre en main tout ce dont vous avez besoin pour les parties 2 à 4. Commençons par obtenir les identifiants d’API.

+++Voir les détails sur la façon d’obtenir des identifiants d’API

* [Compte développeur Acrobat Sign](https://www.adobe.com/acrobat/business/developer-form.html)
* [Code de démarrage](https://github.com/benvanderberg/adobe-sign-api-tutorial)
* [Code VS (ou éditeur de votre choix)](https://code.visualstudio.com)
* Python 3.x
   * Mac — Homebrew
   * Linux : programme d&#39;installation intégré
   * Windows — Chocolatey
   * Tous — https://www.python.org/downloads/

+++

## Partie 2 : Code faible/nul — la puissance des formulaires web

Dans la deuxième partie, explorez l’option de codage faible/sans code de l’utilisation des formulaires web. Il est toujours bon de voir si vous pouvez éviter d’écrire du code au début.

+++Afficher des détails sur la création d’un formulaire web

1. Accédez à Acrobat Sign avec votre compte développeur.

1. Sélectionnez **Publish un formulaire web** sur la page d’accueil.

   ![Page d’accueil Acrobat Sign de capture d’écran](assets/embeddedesignature/embed_1.png)

1. Créez votre accord.

   ![Capture d’écran expliquant comment créer un formulaire web](assets/embeddedesignature/embed_2.png)

1. Incorporer votre accord sur une page de HTML plat.

1. Testez l’ajout dynamique de paramètres de requête.

   ![Capture d&#39;écran de l&#39;ajout des paramètres de requête](assets/embeddedesignature/embed_3.png)

+++

## Partie 3 : Envoi d’un accord avec un formulaire et fusion des données

Dans la partie 3, créez des accords de manière dynamique.

+++Afficher des détails sur la création dynamique d’accords

Tout d’abord, vous devez établir l’accès. Avec Acrobat Sign, il existe deux façons de se connecter via une API. Jetons et clés d’intégration OAuth. À moins d’avoir une raison très spécifique d’utiliser OAuth avec votre application, vous devez d’abord explorer les clés d’intégration.

1. Sélectionnez **Clé d&#39;intégration** dans le menu **Informations sur l&#39;API** sous l&#39;onglet **Compte** dans Acrobat Sign.

   ![Capture d&#39;écran de l&#39;emplacement de la clé d&#39;intégration](assets/embeddedesignature/embed_4.png)

Maintenant que vous avez accès à l’API et que vous pouvez interagir avec elle, découvrez ce que vous pouvez faire avec l’API.

1. Accédez aux [méthodes de l’API REST Acrobat Sign version 6](http://adobesign.com/public/docs/restapi/v6).

   ![Capture d’écran de la navigation dans les méthodes de l’API REST Acrobat Sign version 6](assets/embeddedesignature/embed_5.png)

1. Utilisez le jeton comme valeur « porteur ».

   ![Capture d&#39;écran de bearer value](assets/embeddedesignature/embed_6.png)

Pour envoyer votre premier accord, il est préférable de comprendre comment utiliser l’API.

1. Créer un document temporaire et l’envoyer.

>[!NOTE]
>
>Les appels de requête JSON disposent d’une option « Modèle » et « Schéma de modèle minimal ». Vous obtenez ainsi des spécifications et une charge utile minimale.

![Capture d&#39;écran de la création d&#39;un document temporaire](assets/embeddedesignature/embed_7.png)

Après avoir envoyé un accord pour la première fois, vous pouvez ajouter la logique. Il est toujours bon d&#39;établir des aides pour minimiser les répétitions. En voici quelques exemples :

**Validation**

![Capture d&#39;écran de la logique de validation](assets/embeddedesignature/embed_8.png)

**En-têtes/Auth**

![Capture d&#39;écran des en-têtes/logique d&#39;authentification](assets/embeddedesignature/embed_9.png)

**URI de base**

![Capture d&#39;écran de la logique URI de base](assets/embeddedesignature/embed_10.png)

Sachez où les documents temporaires atterrissent dans le grand schéma de l’écosystème Sign.
Transitoire -> Accord
Temporaire -> Modèle -> Accord
Temporaire -> Widget -> Accord

Cet exemple utilise un modèle comme source du document. Il s’agit généralement du meilleur moyen, à moins que vous n’ayez une raison sérieuse de générer dynamiquement des documents pour signature (par exemple, un code hérité ou une génération de document).

Le code est assez simple : il utilise un document de bibliothèque (modèle) comme source du document. Les premier et deuxième signataires sont attribués dynamiquement. L&#39;état `IN_PROCESS` signifie que le document est envoyé immédiatement. En outre, `mergeFieldInfo` est utilisé pour remplir les champs de manière dynamique.

![Capture d’écran du code pour ajouter des signatures de manière dynamique](assets/embeddedesignature/embed_11.png)

+++

## Partie 4 : Intégration de l’expérience de signature, des redirections et plus encore

Dans de nombreux scénarios, vous pouvez autoriser le participant déclencheur à signer immédiatement un accord. Ceci est utile pour les applications et les kiosques orientés client.

+++Voir les détails sur l’intégration de l’expérience de signature

Si vous ne souhaitez pas que le premier e-mail envoyé se déclenche, une façon simple de gérer le comportement consiste à modifier l’appel API.

![Capture d&#39;écran du code pour ne pas déclencher l&#39;envoi d&#39;un e-mail](assets/embeddedesignature/embed_12.png)

Voici comment contrôler la redirection post-signature :

![Capture d’écran du code pour contrôler la redirection post-signature](assets/embeddedesignature/embed_13.png)

Après la mise à jour du processus de création de l’accord, l’étape finale consiste à générer l’URL de signature. Cet appel est également assez simple et génère une URL qu’un signataire peut utiliser pour accéder à sa partie du processus de signature.

![Capture d’écran du code pour générer une URL de signataire](assets/embeddedesignature/embed_14.png)

>[!NOTE]
>
>Notez que l’appel de création d’accord est techniquement asynchrone. Cela signifie qu’un appel d’accord « POST » peut être effectué, mais que l’accord n’est pas encore prêt. La meilleure pratique consiste à établir une boucle de nouvelle tentative. Utilisez une nouvelle tentative ou toute autre méthode adaptée à votre environnement.

![Capture d&#39;écran indiquant qu&#39;il est recommandé d&#39;établir une boucle de nouvelle tentative](assets/embeddedesignature/embed_15.png)

Lorsque tout est mis ensemble, la solution est assez simple. Vous créez un accord, puis générez une URL de signature sur laquelle le signataire peut cliquer pour commencer le rituel de signature.

+++

## Rubriques supplémentaires

* [Événements JS](https://www.adobe.io/apis/documentcloud/sign/docs.html#!adobedocs/adobe-sign/master/events.md)
* Événements de webhook
   * [API REST](https://sign-acs.na1.echosign.com/public/docs/restapi/v6#!/webhooks/createWebhook)
   * [Webhooks dans Acrobat Sign v6](https://www.adobe.io/apis/documentcloud/sign/docs.html#!adobedocs/adobe-sign/master/webhooks.md)
* [Réactiver les e-mails de demande (avec les événements)](https://sign-acs.na1.echosign.com/public/docs/restapi/v6#!/agreements/updateAgreement)
* [Remplacer le délai d&#39;expiration par une nouvelle tentative](https://stackoverflow.com/questions/23267409/how-to-implement-retry-mechanism-into-python-requests-library)
* Rappels personnalisés
   * Avec la création initiale

     ![Capture d’écran de la navigation vers Power Automate](assets/embeddedesignature/embed_16.png)

   * Ou ajoutez-en un [en cours](https://sign-acs.na1.echosign.com/public/docs/restapi/v6#!/agreements/createReminderOnParticipant)
