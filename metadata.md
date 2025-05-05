---
cloud: Document Cloud
solution-title: Document Cloud
solution-hub-url: https://helpx.adobe.com/fr/support/document-cloud.html
getting-started-title: Getting Started
getting-started-url: https://helpx.adobe.com/fr/acrobat/get-started.html
tutorials-title: Tutorials
tutorials-url: https://helpx.adobe.com/fr/acrobat/tutorials.html
mini-toc-levels: 2
git-repo: https://github.com/AdobeDocs/document-cloud-learn.fr-FR
index: true
type: Tutorial
source-git-commit: 95764e25c3d393b751f52eea5c475add8528ac38
workflow-type: tm+mt
source-wordcount: '130'
ht-degree: 1%

---


# Métadonnées pour utilisation interne

Le fichier metadata.md comprend des métadonnées au niveau du référentiel qui sont transmises aux fichiers TOC.md du guide d’utilisation dans le référentiel. Si vous souhaitez modifier le contenu metadata.md pour n’importe quel guide d’utilisation, faites-le dans n’importe quel fichier TOC.md.

| Métadonnées | ce que cela produit |
|--- |--- |
| solution-title | Utilisé dans l’en-tête d’article comme lien |
| solution-hub-url | Ouvre la page centrale helpx |
| solution-icon | Affiche l’icône de la solution en regard du titre. Pas encore mis en oeuvre |
| getting-started-url | Lien vers la page Prise en main helpx |
| tutorials-url | Lien vers des tutoriels vidéo : tutoriels helpx ou tutoriels KT |
| mini-toc-levels | Détermine le nombre de niveaux de titre qui apparaissent dans le rail droit. la valeur par défaut est 2 |
| git-repo | Spécifie l&#39;emplacement du référentiel maître pour une utilisation interne |

Dans le fichier TOC.md

| Métadonnées | ce que cela produit |
|--- |--- |
| user-guide-title | Utilisé dans l’en-tête d’article comme lien |
| user-guide-url | Ouvre la page centrale helpx |
