---
cloud: Document Cloud
solution: Acrobat
product_v2: id: b12c730b-5ddb-4a2d-ba42-da774988b909
usetq: true
feature-set: Document Cloud
role: User
type: Tutorial
solution-title: Document Cloud
mini-toc-levels: 2
git-repo: https://github.com/AdobeDocs/document-cloud-learn.en
index: true
source-git-commit: f6dc02139caacbab8468d056fbcaef3534c09e1d
workflow-type: tm+mt
source-wordcount: 149
ht-degree: 0%

---


# Métadonnées pour un usage interne

Le fichier metadata.md inclut des métadonnées au niveau du référentiel qui sont transmises aux fichiers TOC.md du guide de l’utilisateur dans le référentiel. Si vous souhaitez modifier le contenu metadata.md pour n’importe quel guide de l’utilisateur, faites-le dans n’importe quel fichier TOC.md.

| métadonnées | ce qu&#39;il fait |
|--- |--- |
| solution-title | Utilisé dans l’en-tête de l’article en tant que lien |
| solution-hub-url | Ouvre la page du hub d’aide |
| solution-icon | Affiche l&#39;icône de la solution à côté du titre de la solution. Pas encore mise en œuvre |
| getting-started-url | Lien vers la page de prise en main des aides |
| tutorials-url | Lien vers les tutoriels vidéo : tutoriels d’aide ou tutoriels d’application des connaissances |
| mini-niveaux de table des matières | Détermine le nombre de niveaux d’intitulé qui apparaissent dans le rail de droite. la valeur par défaut est 2 |
| git-repo | Spécifie l&#39;emplacement du référentiel maître pour une utilisation interne |

Dans le fichier TOC.md

| métadonnées | ce qu&#39;il fait |
|--- |--- |
| user-guide-title | Utilisé dans l’en-tête de l’article en tant que lien |
| user-guide-url | Ouvre la page du hub d’aide |
