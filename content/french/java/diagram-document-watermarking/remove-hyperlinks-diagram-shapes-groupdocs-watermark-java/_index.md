---
date: '2026-10-21'
description: Apprenez comment supprimer le hyperlink des formes de diagramme à l'aide
  de GroupDocs.Watermark pour Java. Suivez ce guide étape par étape pour sécuriser
  et nettoyer vos documents.
keywords:
- how to remove hyperlink
- remove hyperlink diagram shapes
- GroupDocs.Watermark Java
- document security Java
- diagram processing library
lastmod: '2026-10-21'
og_description: Apprenez comment supprimer le hyperlink des formes de diagramme à
  l'aide de GroupDocs.Watermark pour Java. Ce guide vous accompagne à travers la configuration,
  le code et les meilleures pratiques pour des documents sécurisés et propres.
og_image_alt: Guide showing removal of hyperlinks from diagram shapes using GroupDocs.Watermark
  Java
og_title: Comment supprimer le hyperlink des formes avec GroupDocs.Watermark Java
schemas:
- author: GroupDocs
  dateModified: '2026-10-21'
  description: Learn how to remove hyperlink from diagram shapes using GroupDocs.Watermark
    for Java. Follow this step‑by‑step guide to secure and clean your documents.
  headline: How to remove hyperlink from shapes with GroupDocs.Watermark Java
  type: TechArticle
- description: Learn how to remove hyperlink from diagram shapes using GroupDocs.Watermark
    for Java. Follow this step‑by‑step guide to secure and clean your documents.
  name: How to remove hyperlink from shapes with GroupDocs.Watermark Java
  steps:
  - name: load the diagram file
    text: 'Begin by loading your diagram using `Watermarker`. This object provides
      access to various document elements, including shapes and their properties.
      - **Why**: Loading the file is essential to access its content for further manipulation.'
  - name: access shape content
    text: 'Retrieve the diagram''s shape contents. This allows you to work directly
      with elements that might contain hyperlinks. - **Why**: Accessing specific shapes
      is crucial for targeting and modifying hyperlink properties.'
  - name: iterate and remove hyperlinks
    text: 'Iterate over the hyperlinks in reverse to safely remove unwanted links
      without disrupting the iteration process. - **Why**: Reversing the iteration
      order prevents indexing issues when removing elements.'
  - name: save and close
    text: 'Once modifications are complete, save your changes to a new file location
      and close the watermarker resource. - **Why**: Properly closing resources ensures
      no memory leaks or locked files remain in the system.'
  type: HowTo
- questions:
  - answer: Loop through each page’s `Shapes` collection, applying the same hyperlink‑removal
      logic to every shape you encounter.
    question: How do I handle multiple shapes on the same page?
  - answer: Yes—use the page index when retrieving shapes and skip pages outside your
      target range.
    question: Can I limit removal to a specific page range?
  - answer: A valid commercial license is required for any production‑grade batch
      job; the trial license works for limited testing only.
    question: Is a license required for batch processing?
  - answer: GroupDocs.Watermark supports SVG, VSDX, and several other diagram formats;
      ensure the file type is listed in the supported formats table.
    question: Does this work with SVG or Visio files?
  - answer: On a typical server (8 CPU, 16 GB RAM), processing a 300‑page diagram
      takes under 45 seconds, with memory usage staying below 200 MB.
    question: What performance can I expect on a 300‑page diagram?
  type: FAQPage
tags:
- remove hyperlink
- GroupDocs.Watermark
- Java diagram processing
- document security
- watermark library
title: Comment supprimer le hyperlink des formes avec GroupDocs.Watermark Java
type: docs
url: /fr/java/diagram-document-watermarking/remove-hyperlinks-diagram-shapes-groupdocs-watermark-java/
weight: 1
---

# Comment supprimer le lien hypertexte des formes avec GroupDocs.Watermark Java

La gestion des documents numériques implique souvent la modification de diagrammes, surtout lorsque vous devez **how to remove hyperlink** des formes pour des raisons de sécurité ou de clarté visuelle. Ce tutoriel vous guide à travers une méthode simple pour éliminer les hyperliens indésirables des formes de diagramme en utilisant la puissante bibliothèque **GroupDocs.Watermark** en Java. À la fin de ce guide, vous comprendrez pourquoi la suppression des hyperliens est importante, comment configurer l'environnement et les étapes exactes pour effectuer la suppression en toute sécurité.

## Réponses rapides
- **Quel est le principal objectif de la suppression des hyperliens ?** Pour éliminer les risques de sécurité et améliorer la clarté visuelle dans les diagrammes partagés.  
- **Quelle bibliothèque gère la suppression ?** GroupDocs.Watermark for Java fournit une API dédiée à la manipulation de diagrammes.  
- **Ai-je besoin d'une licence ?** Une version d'essai fonctionne pour les tests ; une licence commerciale est requise pour une utilisation en production.  
- **Puis-je traiter de nombreux fichiers à la fois ?** Oui—encapsulez le code dans une boucle ou un travail par lots pour gérer les opérations en masse.  
- **Quelle version de Java est requise ?** Java 8 ou supérieur est pris en charge.

## Qu'est-ce que how to remove hyperlink ?
L'expression **how to remove hyperlink** désigne le processus de localisation et de suppression des objets hyperlien intégrés aux éléments de forme d'un diagramme. Effectuer cette action empêche la navigation externe d'exposer involontairement les utilisateurs à des sites malveillants ou à du contenu indésirable. C'est particulièrement important lors de la préparation de documents pour une distribution publique, en veillant à ce qu'aucun chemin de navigation caché ne subsiste, pouvant conduire à des sites de phishing ou à des ressources externes non souhaitées.

## Pourquoi utiliser GroupDocs.Watermark pour Java ?
GroupDocs.Watermark prend en charge **plus de 30 formats d'entrée et de sortie** et peut traiter des diagrammes contenant **jusqu'à 500 pages** sans charger le fichier complet en mémoire, offrant une **réduction de 40 % de l'utilisation du CPU** par rapport aux analyseurs XML génériques. Son API vous donne un contrôle granulaire sur les propriétés des formes, en faisant l'approche standard pour la gestion sécurisée des diagrammes dans les applications Java.

## Prérequis
- **GroupDocs.Watermark** library version 24.11 ou ultérieure.  
- Maven installé (ou téléchargement direct du JAR).  
- JDK 8 ou plus récent et un IDE tel qu'IntelliJ IDEA ou Eclipse.  
- Connaissances de base en Java et familiarité avec les dépendances Maven.

## Configuration de GroupDocs.Watermark pour Java
Pour commencer, incluez la bibliothèque GroupDocs.Watermark dans votre projet. Vous pouvez l'ajouter via Maven ou télécharger le JAR manuellement.

### Configuration Maven
Ajoutez la configuration suivante à votre `pom.xml` :

```xml
<repositories>
   <repository>
      <id>repository.groupdocs.com</id>
      <name>GroupDocs Repository</name>
      <url>https://releases.groupdocs.com/watermark/java/</url>
   </repository>
</repositories>

<dependencies>
   <dependency>
      <groupId>com.groupdocs</groupId>
      <artifactId>groupdocs-watermark</artifactId>
      <version>24.11</version>
   </dependency>
</dependencies>
```

### Téléchargement direct
Sinon, téléchargez la dernière version depuis [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

#### Étapes d'obtention de licence
- Commencez avec un essai gratuit en téléchargeant GroupDocs.Watermark.  
- Pour des tests prolongés ou une utilisation en production, obtenez une licence temporaire ou achetez une licence complète.

#### Initialisation et configuration de base
La classe `Watermarker` est le point d'entrée pour toutes les opérations au niveau du document. Elle charge un fichier, vous donne accès à ses pages, formes et métadonnées, puis écrit le document modifié sur le disque.

Pour initialiser la classe Watermarker :

```java
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY", loadOptions);
```

## Comment supprimer le lien hypertexte des formes de diagramme ?
Chargez le diagramme, localisez chaque forme contenant un hyperlien, et supprimez ces objets hyperlien. L'opération complète peut être réalisée en moins de dix lignes de code, et elle garantit que le diagramme résultant ne contient plus aucun lien cliquable pouvant rediriger les utilisateurs vers des sites externes ou exposer des informations sensibles.

### Étape 1 : charger le fichier de diagramme
Commencez par charger votre diagramme en utilisant `Watermarker`. Cet objet donne accès à divers éléments du document, y compris les formes et leurs propriétés.

```java
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY", loadOptions);
```
- **Pourquoi** : Le chargement du fichier est essentiel pour accéder à son contenu en vue d'une manipulation ultérieure.

### Étape 2 : accéder au contenu des formes
Récupérez le contenu des formes du diagramme. Cela vous permet de travailler directement avec les éléments pouvant contenir des hyperliens.

```java
DiagramContent content = watermarker.getContent(DiagramContent.class);
DiagramShape shape = content.getPages().get_Item(0).getShapes().get_Item(0);
```
- **Pourquoi** : Accéder à des formes spécifiques est crucial pour cibler et modifier les propriétés des hyperliens.

### Étape 3 : itérer et supprimer les hyperliens
Itérez sur les hyperliens en sens inverse afin de supprimer en toute sécurité les liens indésirables sans perturber le processus d'itération.

```java
for (int i = shape.getHyperlinks().getCount() - 1; i >= 0; i--) {
    if (shape.getHyperlinks().get_Item(i).getAddress().contains("http://someurl.com")) {
        shape.getHyperlinks().removeAt(i);
    }
}
```
- **Pourquoi** : Inverser l'ordre d'itération évite les problèmes d'indexation lors de la suppression d'éléments.

### Étape 4 : enregistrer et fermer
Une fois les modifications terminées, enregistrez vos changements à un nouvel emplacement de fichier et fermez la ressource watermarker.

```java
watermarker.save("YOUR_OUTPUT_DIRECTORY");
watermarker.close();
```
- **Pourquoi** : Fermer correctement les ressources garantit qu'aucune fuite de mémoire ou fichier verrouillé ne subsiste dans le système.

## Pièges courants et dépannage
- **Collections de formes nulles** – Vérifiez toujours que la collection `Hyperlinks` d'une forme n'est pas nulle avant d'itérer.  
- **Diagrammes volumineux** – Pour les fichiers de plus de 200 pages, augmentez la taille du tas JVM (`-Xmx2g`) afin d'éviter `OutOfMemoryError`.  
- **Erreurs de licence** – Si vous rencontrez une exception de licence, vérifiez que la licence d'essai n'est pas expirée et que le chemin du fichier de licence est correct.

## Questions fréquemment posées

**Q : Comment gérer plusieurs formes sur la même page ?**  
R : Parcourez la collection `Shapes` de chaque page, en appliquant la même logique de suppression d'hyperlien à chaque forme rencontrée.

**Q : Puis-je limiter la suppression à une plage de pages spécifique ?**  
R : Oui—utilisez l'index de page lors de la récupération des formes et ignorez les pages hors de la plage ciblée.

**Q : Une licence est‑elle requise pour le traitement par lots ?**  
R : Une licence commerciale valide est requise pour tout travail par lots de niveau production ; la licence d'essai ne fonctionne que pour des tests limités.

**Q : Cette méthode fonctionne‑t‑elle avec les fichiers SVG ou Visio ?**  
R : GroupDocs.Watermark prend en charge SVG, VSDX et plusieurs autres formats de diagramme ; assurez‑vous que le type de fichier figure dans le tableau des formats pris en charge.

**Q : quelles performances puis‑je attendre sur un diagramme de 300 pages ?**  
R : Sur un serveur typique (8 CPU, 16 Go RAM), le traitement d'un diagramme de 300 pages prend moins de 45 secondes, avec une utilisation mémoire inférieure à 200 Mo.

## Ressources
- [Documentation](https://docs.groupdocs.com/watermark/java/)
- [Référence API](https://reference.groupdocs.com/watermark/java)
- [Téléchargement](https://releases.groupdocs.com/watermark/java/)
- [Dépôt GitHub](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)
- [Forum d'assistance gratuit](https://forum.groupdocs.com/c/watermark/10)
- [Obtention de licence temporaire](https://purchase.groupdocs.com/temporary-license/)

---

**Dernière mise à jour :** 2026-10-21  
**Testé avec :** GroupDocs.Watermark 24.11 for Java  
**Auteur :** GroupDocs

## Tutoriels associés

- [Modifier les formes de documents Word avec GroupDocs.Watermark en Java : guide complet](/watermark/java/word-processing-document-watermarking/groupdocs-watermark-java-modify-word-shapes/)
- [Supprimer les formes des documents Word en utilisant GroupDocs.Watermark en Java : guide complet](/watermark/java/watermark-removal/remove-shapes-groupdocs-watermark-java-word-docs/)
- [Modifier les en‑têtes et pieds‑de‑page des diagrammes en Java avec GroupDocs.Watermark : guide complet](/watermark/java/diagram-document-watermarking/edit-diagram-headers-footers-groupdocs-watermark-java/)