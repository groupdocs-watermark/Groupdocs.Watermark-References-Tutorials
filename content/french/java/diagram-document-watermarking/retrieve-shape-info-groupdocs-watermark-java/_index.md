---
date: '2026-02-13'
description: Apprenez comment extraire des formes et extraire l'image d'une forme
  avec GroupDocs.Watermark pour Java, en récupérant efficacement des informations
  détaillées sur le diagramme.
keywords:
- extract shape information Java
- GroupDocs.Watermark diagram processing
- Java diagram manipulation
title: Comment extraire des formes à partir de diagrammes en utilisant GroupDocs.Watermark
  en Java
type: docs
url: /fr/java/diagram-document-watermarking/retrieve-shape-info-groupdocs-watermark-java/
weight: 1
---

# Comment extraire des formes à partir de diagrammes avec GroupDocs.Watermark en Java

Lorsque vous devez **extraire des formes** d'un diagramme de type Visio de manière programmatique, la bibliothèque GroupDocs.Watermark vous offre une solution propre, centrée sur Java, pour récupérer chaque détail — dimensions, positions, images intégrées, et même le texte à l'intérieur de chaque forme. Dans ce tutoriel, vous verrez exactement **comment extraire des formes**, pourquoi c'est important, et du code étape par étape que vous pouvez copier dans votre projet.

## Réponses rapides
- **Quelle bibliothèque gère l'extraction des formes ?** GroupDocs.Watermark for Java  
- **Quelle version de Java est requise ?** JDK 8 ou supérieure  
- **Puis-je obtenir les données d'image d'une forme ?** Oui – utilisez `shape.getImage()`  
- **Le texte à l'intérieur d'une forme est-il accessible ?** Absolument, via `shape.getText()`  
- **Ai‑je besoin d'une licence pour la production ?** Une licence valide GroupDocs.Watermark est requise  

## Introduction

La gestion de diagrammes complexes nécessite souvent d'accéder à des informations détaillées sur leurs composants, comme les formes et les images. Si vous avez déjà eu besoin de récupérer de manière programmatique des données telles que les dimensions, les positions ou le texte associé aux formes d'un diagramme en Java, ce tutoriel est fait pour vous. Exploiter la puissance de la bibliothèque GroupDocs.Watermark peut simplifier ce processus dans une application Java. Dans ce guide, nous parcourrons **comment extraire des formes** d'un fichier de diagramme et nous vous montrerons également comment **extraire une image d'une forme** et **extraire le texte d'une forme**.

## Qu’est‑ce que « comment extraire des formes » ?

Extraire des formes signifie lire les objets internes du diagramme (pages, formes, images, texte) afin de pouvoir les analyser, les transformer ou les réutiliser dans d’autres applications — idéal pour l’automatisation, les rapports ou l’intégration avec des outils CAO.

## Pourquoi utiliser GroupDocs.Watermark pour l'extraction de formes ?

- **Prise en charge complète des formats** – fonctionne avec VSDX, VDX et de nombreux autres types de diagrammes.  
- **Modèle d'objet riche** – offre un accès direct à la géométrie des formes, aux images et au texte.  
- **Aucune dépendance externe** – pur Java, facile à intégrer dans des projets Maven.  

## Prérequis

- **GroupDocs.Watermark for Java** (version 24.11 ou ultérieure)  
- Java Development Kit (JDK) 8 ou supérieur  
- Maven pour la gestion des dépendances  
- Un IDE tel qu'IntelliJ IDEA ou Eclipse  

## Configuration de GroupDocs.Watermark pour Java

Ajoutez la bibliothèque à votre `pom.xml` Maven :

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

Vous pouvez également télécharger les dernières binaires depuis [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

### Étapes d'obtention de licence
- **Essai gratuit :** Téléchargez un package d'essai pour évaluer l'API.  
- **Licence temporaire :** Demandez une clé temporaire pour des tests prolongés.  
- **Achat :** Obtenez une licence complète pour l'utilisation en production.  

### Initialisation et configuration de base

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.contents.DiagramContent;
import com.groupdocs.watermark.options.DiagramLoadOptions;

DiagramLoadOptions diagramLoadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/diagram.vsdx", diagramLoadOptions);
```

## Comment extraire des formes – Guide d'implémentation

### Charger et récupérer le contenu

```java
// Create load options if necessary
DiagramLoadOptions diagramLoadOptions = new DiagramLoadOptions();
// Initialize watermarker with your document path
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/diagram.vsdx", diagramLoadOptions);
```

```java
// Retrieve content of the diagram file as a DiagramContent object
DiagramContent content = watermarker.getContent(DiagramContent.class);
```

### Parcourir les formes

```java
for (DiagramPage page : content.getPages()) {
    // Process each shape in the current page
}
```

```java
for (DiagramShape shape : page.getShapes()) {
    if (shape.getImage() != null) {
        // Access and print image-related properties
        System.out.println("Image Width: " + shape.getImage().getWidth());
        System.out.println("Image Height: " + shape.getImage().getHeight());
        System.out.println("Image Size: " + shape.getImage().getData().length);
    }
    
    // Print other shape attributes
    System.out.println("Shape Name: " + shape.getName());
    System.out.println("X Position: " + shape.getX());
    System.out.println("Y Position: " + shape.getY());
    System.out.println("Width: " + shape.getWidth());
    System.out.println("Height: " + shape.getHeight());
    System.out.println("Rotation Angle: " + shape.getRotationAngle());
    System.out.println("Text: " + (shape.getText() != null ? shape.getText() : "No text"));
    System.out.println("Shape ID: " + shape.getId());
}
```

### Comment extraire une image d'une forme

L'appel `shape.getImage()` renvoie un objet contenant le bitmap brut, ses dimensions et le tableau d'octets. Utilisez les propriétés affichées ci‑dessus pour enregistrer l'image sur le disque ou l'alimenter dans un autre pipeline de traitement.

### Comment extraire le texte d'une forme

La méthode `shape.getText()` renvoie le texte brut à l'intérieur de la forme. Si la forme ne contient aucun texte, la méthode renvoie `null`. La boucle d'exemple affiche déjà le texte, et vous pouvez le manipuler davantage — par exemple, créer un index de toutes les étiquettes de formes.

## Conseils de dépannage
- Vérifiez le chemin du fichier et les permissions de lecture.  
- Assurez‑vous d'utiliser un format de diagramme pris en charge (VSDX, VDX, etc.).  
- Si une forme apparaît sans les données attendues, consultez les notes de version de la bibliothèque pour les particularités propres aux formats.  

## Applications pratiques

1. **Analyse de diagrammes :** Auditez automatiquement les diagrammes pour la conformité en vérifiant les tailles des formes ou les étiquettes manquantes.  
2. **Visualisation de données :** Alimentez les dimensions extraites dans un tableau de bord de reporting pour visualiser la densité de la mise en page.  
3. **Intégration CAO :** Combinez les données des formes avec les API CAO pour synchroniser les spécifications de conception entre les outils.  

## Considérations de performance

- **Fermer les ressources :** Appelez `watermarker.close()` lorsque vous avez terminé pour libérer les ressources natives.  
- **Gestion de la mémoire :** Les grands diagrammes peuvent consommer beaucoup de heap ; surveillez la mémoire et augmentez `-Xmx` si nécessaire.  
- **Traitement par lots :** Traitez les fichiers par lots et réutilisez une seule instance de `Watermarker` lorsque c’est possible.  

## Conclusion

En suivant ce guide, vous savez maintenant **comment extraire des formes**, comment **extraire une image d'une forme**, et comment **extraire le texte d'une forme** en utilisant GroupDocs.Watermark pour Java. Ces techniques ouvrent la voie à l'analyse automatisée de diagrammes, aux rapports et à l'intégration avec d’autres systèmes d’ingénierie. Comme prochaine étape, explorez l'API complète en consultant sa [documentation](https://docs.groupdocs.com/watermark/java/) et essayez de combiner l'extraction de formes avec une logique métier personnalisée.

## Section FAQ

1. **Qu’est‑ce que GroupDocs.Watermark ?**  
   - Une bibliothèque Java complète conçue pour le filigrane et l'extraction d'informations à partir de divers formats de documents, y compris les diagrammes.  

2. **Puis‑je utiliser cette bibliothèque pour traiter tous les types de fichiers de diagrammes ?**  
   - Oui, mais assurez‑vous que le format de fichier est pris en charge en vérifiant la [API Reference](https://reference.groupdocs.com/watermark/java/).  

3. **Comment extraire les dimensions et les positions des formes d'un diagramme en Java avec GroupDocs.Watermark ?**  
   - Chargez le diagramme, accédez à `DiagramContent`, puis parcourez les formes pour obtenir des propriétés telles que la largeur, la hauteur, X et Y.  

4. **GroupDocs.Watermark peut‑il extraire les images intégrées dans les formes de diagrammes avec Java ?**  
   - Oui, il fournit des méthodes pour accéder aux données d'image au sein des formes, y compris la taille et les données de pixels, utiles pour l'analyse ou la modification.  

5. **Quels sont les prérequis pour extraire les informations des formes de diagrammes en Java ?**  
   - Java JDK 8+, configuration Maven, bibliothèque GroupDocs.Watermark (24.11+), et des connaissances de base en Java sont essentiels pour l'implémentation.  

---

**Dernière mise à jour :** 2026-02-13  
**Testé avec :** GroupDocs.Watermark 24.11 for Java  
**Auteur :** GroupDocs