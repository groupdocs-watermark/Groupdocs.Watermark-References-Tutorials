---
date: '2026-08-25'
description: Apprenez à éditer des diagram files et à supprimer les hyperlinks en
  utilisant GroupDocs.Watermark for Java. Sécurisez vos diagrammes rapidement grâce
  à un guide étape par étape.
keywords:
- how to edit diagram
- remove hyperlinks diagram shapes
- GroupDocs.Watermark Java
lastmod: '2026-08-25'
og_description: Apprenez à éditer des diagram files et à supprimer les hyperlinks
  en utilisant GroupDocs.Watermark for Java. Suivez des étapes claires pour protéger
  vos documents.
og_image_alt: Guide showing how to edit diagram and remove hyperlinks using GroupDocs.Watermark
  Java
og_title: Comment éditer un diagram et supprimer les hyperlinks avec Java
tags:
- edit diagram
- remove hyperlinks
- GroupDocs.Watermark
- Java document processing
- diagram security
title: Comment éditer un diagram et supprimer les hyperlinks avec Java
type: docs
url: /fr/java/diagram-document-watermarking/remove-hyperlinks-diagram-shapes-groupdocs-watermark-java/
weight: 1
---

# Comment modifier un diagramme et supprimer les hyperliens avec Java  

La gestion des documents numériques implique souvent la modification de diagrammes, surtout lorsque vous devez **edit diagram** des fichiers pour supprimer les hyperliens afin d'améliorer la sécurité ou la clarté visuelle. Ce tutoriel vous montre exactement comment modifier les fichiers de diagramme et supprimer les hyperliens indésirables des formes du diagramme en utilisant la puissante bibliothèque **GroupDocs.Watermark** pour Java. À la fin de ce guide, vous disposerez d'un diagramme propre, sans lien, prêt à être distribué.  

## Réponses rapides  
- **Quel est l'objectif principal ?** Supprimer tous les hyperliens des formes du diagramme afin d'améliorer la sécurité et la présentation.  
- **Quelle bibliothèque est requise ?** GroupDocs.Watermark for Java, version 24.11 ou plus récente.  
- **Ai-je besoin d'une licence ?** Un essai gratuit fonctionne pour les tests ; une licence commerciale est requise pour la production.  
- **Puis-je traiter plusieurs fichiers à la fois ?** Oui – le même code peut être placé dans une boucle pour gérer des lots.  
- **Quelle version de Java est prise en charge ?** Java 8 ou supérieure (Java 11 recommandé).  

## Qu’est‑ce que « how to edit diagram » ?  
**How to edit diagram** désigne le processus d'ouverture programmatique d'un fichier de diagramme, de modification de ses éléments internes (tels que les formes, le texte ou les hyperliens) et d'enregistrement du résultat. Avec GroupDocs.Watermark, vous pouvez modifier les fichiers de diagramme sans avoir besoin de l'outil d'édition original.  

## Pourquoi utiliser GroupDocs.Watermark pour Java ?  
GroupDocs.Watermark prend en charge **30+ formats de diagramme et d'image** (y compris VSDX, SVG et WMF) et peut traiter des fichiers jusqu'à **500 Mo** sans charger l'intégralité du document en mémoire, offrant une vitesse de traitement **20 % plus rapide** comparée à de nombreux concurrents.  

## Prérequis  
- **GroupDocs.Watermark** library version 24.11 ou ultérieure.  
- Maven installé (ou les fichiers JAR si vous préférez une configuration manuelle).  
- Java Development Kit 8 ou plus récent et un IDE tel qu'IntelliJ IDEA ou Eclipse.  

### Bibliothèques requises, versions et dépendances  
- GroupDocs.Watermark 24.11+  
- Maven 3.6+ (si vous utilisez l'approche Maven)  

### Exigences de configuration de l'environnement  
Assurez-vous que le répertoire `bin` du JDK est présent dans votre `PATH` et que votre IDE pointe vers la bonne version du JDK.  

### Prérequis de connaissances  
Vous devez être à l'aise avec la syntaxe Java de base, la gestion des dépendances Maven et les opérations d'E/S de fichiers.  

## Comment configurer GroupDocs.Watermark pour Java ?  
La classe `Watermarker` fournit le point d'entrée de l'API pour charger et modifier les documents.  

Pour commencer à utiliser GroupDocs.Watermark, ajoutez ses coordonnées Maven à votre `pom.xml` de projet. Cela récupère la bibliothèque et ses dépendances, vous permettant d'instancier la classe Watermarker et de travailler avec des fichiers de diagramme directement depuis le code Java. Vous pouvez ensuite configurer la licence et définir les options de sortie avant de traiter tout document.  

Ajoutez la dépendance GroupDocs.Watermark à votre `pom.xml`.  

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

Si vous préférez ne pas utiliser Maven, téléchargez le dernier JAR depuis la page officielle des releases.  

[GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/)  

#### Étapes d'obtention de licence  
- Commencez par un essai gratuit pour évaluer l'API.  
- Pour la production, obtenez une licence temporaire ou permanente via le portail du fournisseur.  

#### Initialisation et configuration de base  
La classe `Watermarker` est le point d'entrée pour toutes les opérations de traitement de documents.  

```java
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY", loadOptions);
```  

## Comment modifier un diagramme et supprimer les hyperliens avec GroupDocs.Watermark ?  
La classe `Watermarker` fournit le point d'entrée de l'API pour charger et modifier les documents.  

Tout d'abord, chargez le fichier de diagramme dans une instance de Watermarker. Ensuite, récupérez la collection de formes, identifiez celles contenant des objets hyperlien, et parcourez‑les en ordre inverse afin de supprimer chaque lien en toute sécurité sans affecter l'indexation de la collection. Cela garantit que toutes les URL intégrées sont supprimées tout en préservant l'intégrité visuelle du diagramme.  

```java
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY", loadOptions);
```  

- **Pourquoi cette étape est importante** : Le chargement du fichier vous donne un accès programmatique à chaque forme et à ses propriétés associées.  

## Comment accéder au contenu des formes dans un diagramme ?  
L'objet `DiagramShape` représente une forme individuelle au sein d'un diagramme, exposant ses propriétés et ses métadonnées associées.  

Après avoir chargé le diagramme, appelez `getShapes()` sur le Watermarker pour obtenir une liste d'objets `DiagramShape`. Chaque forme peut être inspectée pour les collections d'hyperliens, permettant un ciblage précis des liens à supprimer ou à modifier. Vous pouvez également lire le texte, les couleurs et la géométrie de la forme si des ajustements supplémentaires sont nécessaires.  

```java
DiagramContent content = watermarker.getContent(DiagramContent.class);
DiagramShape shape = content.getPages().get_Item(0).getShapes().get_Item(0);
```  

- **Pourquoi cette étape est importante** : Cibler la forme exacte garantit que vous ne supprimez que les liens indésirables sans affecter les autres éléments visuels.  

## Comment itérer et supprimer les hyperliens en toute sécurité ?  
La méthode `removeHyperlink(int index)` supprime un hyperlien à la position spécifiée au sein de la collection d'hyperliens d'une forme.  

Itérez sur la liste des hyperliens du dernier indice jusqu'à zéro. Cette boucle inverse empêche le décalage d'index qui se produit lorsque des éléments sont supprimés, garantissant que chaque hyperlien est traité sans être sauté. Après la suppression, vous pouvez rafraîchir l'état de la forme ou passer à la forme suivante du diagramme.  

```java
for (int i = shape.getHyperlinks().getCount() - 1; i >= 0; i--) {
    if (shape.getHyperlinks().get_Item(i).getAddress().contains("http://someurl.com")) {
        shape.getHyperlinks().removeAt(i);
    }
}
```  

- **Pourquoi cette étape est importante** : Une boucle inverse garantit que tous les hyperliens sont supprimés sans en omettre aucun.  

## Comment enregistrer le diagramme modifié et libérer les ressources ?  
La méthode `save(String path)` écrit le document modifié à l'emplacement de fichier spécifié, finalisant toutes les modifications.  

Une fois tous les hyperliens supprimés, invoquez la méthode `save` sur l'instance Watermarker, en fournissant un nouveau nom de fichier pour éviter d'écraser l'original. Puis appelez `close()` pour libérer les descripteurs de fichiers et libérer la mémoire, ce qui est essentiel pour les processus batch de longue durée. Cela garantit que le fichier est correctement fermé et prêt à être utilisé.  

```java
watermarker.save("YOUR_OUTPUT_DIRECTORY");
watermarker.close();
```  

- **Pourquoi cette étape est importante** : Fermer correctement les ressources évite les fuites de mémoire et les problèmes de verrouillage de fichiers sur le serveur.  

## Applications pratiques  
Supprimer les hyperliens des formes de diagramme peut être bénéfique dans plusieurs scénarios réels :  

1. **Sécurité** – Empêcher les liens externes pouvant mener à des sites malveillants.  
2. **Conformité** – Respecter les politiques d'entreprise qui interdisent les URL intégrées dans les actifs partagés.  
3. **Clarté** – Produire des présentations plus épurées où les liens seraient distrayants.  

Vous pouvez intégrer cette logique dans des pipelines d'automatisation plus vastes, comme des tâches batch nocturnes qui désinfectent tous les diagrammes avant leur publication sur un intranet.  

## Considérations de performance  

### Optimisation des performances  
- Utilisez une seule instance `Watermarker` par fichier pour réduire la surcharge.  
- Privilégiez l'itération inverse (comme montré) pour éviter le re‑indexage coûteux des listes.  

### Directives d'utilisation des ressources  
- Pour les diagrammes supérieurs à 200 Mo, surveillez l'utilisation du tas et envisagez d'augmenter le drapeau JVM `-Xmx`.  
- Des outils de profilage comme VisualVM peuvent aider à identifier les goulets d'étranglement lors de traitements batch à grande échelle.  

### Bonnes pratiques pour la gestion de la mémoire Java  
- Déclarez les objets dans la portée la plus petite possible.  
- Utilisez try‑with‑resources lors de la manipulation de flux pour garantir une fermeture automatique.  

## Questions fréquemment posées  

**Q : Comment gérer les diagrammes contenant des milliers de formes ?**  
R : Traitez le diagramme page par page et libérez les ressources de chaque page avant de passer à la suivante afin de maintenir une faible consommation de mémoire.  

**Q : Puis‑je limiter la suppression des hyperliens à des pages spécifiques uniquement ?**  
R : Oui – récupérez l'indice de page souhaité, puis appliquez la boucle de suppression uniquement aux formes de cette page.  

**Q : Une licence commerciale est‑elle obligatoire pour le traitement par lots ?**  
R : Une licence valide est requise pour tout déploiement en production ; l'essai gratuit est limité à 30 jours et 5 documents.  

**Q : GroupDocs.Watermark prend‑il en charge les diagrammes SVG ?**  
R : Absolument – SVG fait partie des plus de 30 formats pris en charge, et les hyperliens peuvent être supprimés en utilisant les mêmes appels d'API.  

**Q : Que se passe‑t‑il si une forme possède plusieurs hyperliens ?**  
R : La boucle d'itération inverse supprime chaque entrée d'hyperlien individuellement, garantissant que tous les liens sont effacés.  

## Ressources  
- [Documentation](https://docs.groupdocs.com/watermark/java/)  
- [Référence API](https://reference.groupdocs.com/watermark/java)  
- [Téléchargement](https://releases.groupdocs.com/watermark/java/)  
- [Référentiel GitHub](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)  
- [Forum d'assistance gratuit](https://forum.groupdocs.com/c/watermark/10)  
- [Obtention de licence temporaire](https://purchase.groupdocs.com/temporary-license/)  

---  

**Dernière mise à jour :** 2026-08-25  
**Testé avec :** GroupDocs.Watermark 24.11 for Java  
**Auteur :** GroupDocs  

## Tutoriels associés  

- [Tutoriels de filigrane de diagramme pour GroupDocs.Watermark Java](/watermark/java/diagram-document-watermarking/)  
- [Modifier les en‑têtes et pieds‑de‑page de diagramme en Java avec GroupDocs.Watermark : Guide complet](/watermark/java/diagram-document-watermarking/edit-diagram-headers-footers-groupdocs-watermark-java/)  
- [Supprimer efficacement les formes des diagrammes avec GroupDocs.Watermark pour Java](/watermark/java/watermark-removal/remove-shapes-diagrams-groupdocs-watermark-java/)