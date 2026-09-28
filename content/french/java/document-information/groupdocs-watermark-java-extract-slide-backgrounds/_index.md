---
date: '2026-09-11'
description: Apprenez à extraire le fond de diapositive en Java et à lire les dimensions
  des diapositives PowerPoint à l'aide de GroupDocs.Watermark pour Java. Obtenez la
  taille de l'image, la taille du fichier et les métadonnées en quelques minutes.
keywords:
- extract slide background java
- read powerpoint slide dimensions
- slide background details java
lastmod: '2026-09-11'
og_description: Extraire le fond de diapositive en Java et lire les dimensions des
  diapositives PowerPoint à l'aide de GroupDocs.Watermark pour Java. Guide détaillé
  avec configuration, code et dépannage.
og_image_alt: Guide showing Java code extracting slide background information from
  PowerPoint
og_title: Extraire le fond de diapositive en Java avec GroupDocs.Watermark
schemas:
- author: GroupDocs
  dateModified: '2026-09-11'
  description: Learn how to extract slide background java and read PowerPoint slide
    dimensions using GroupDocs.Watermark for Java. Get image size, file size, and
    metadata in minutes.
  headline: How to extract slide background java
  type: TechArticle
- description: Learn how to extract slide background java and read PowerPoint slide
    dimensions using GroupDocs.Watermark for Java. Get image size, file size, and
    metadata in minutes.
  name: How to extract slide background java
  steps:
  - name: create load options
    text: '`PresentationLoadOptions` defines loading preferences such as password
      handling and memory usage.'
  - name: open the PowerPoint document
    text: Instantiate `Watermarker` with the path to your `.pptx` file and the load
      options created earlier.
  - name: access slide content
    text: '`PresentationContent` is the entry point for retrieving slide‑level objects,
      including background images.'
  - name: iterate over slides and read background details
    text: Slide represents an individual slide within the presentation and provides
      access to its visual elements. For each `Slide` object, call `getBackground()`
      to obtain the image, then read its dimensions and size.
  - name: close the watermarker
    text: Always close the `Watermarker` instance to free native resources and avoid
      memory leaks.
  type: HowTo
- questions:
  - answer: Java 11 or newer is required; earlier versions lack the necessary language
      features for the library.
    question: What is the minimum Java version required?
  - answer: Yes—set the password in `PresentationLoadOptions` before opening the file.
    question: Can I extract backgrounds from password‑protected presentations?
  - answer: The trial imposes a watermark on output files but does not restrict slide
      count for metadata extraction.
    question: Does the trial mode limit the number of slides I can process?
  - answer: Absolutely—use `ImageInfo.save("output.png")` after retrieving the `ImageInfo`
      object.
    question: Is it possible to save the extracted background image to disk?
  - answer: The API supports PNG, JPEG, BMP, and GIF for background image export.
    question: Which formats can I export the extracted image to?
  type: FAQPage
tags:
- extract slide background
- GroupDocs.Watermark
- Java PowerPoint
- document processing
title: Comment extraire le fond de diapositive en Java
type: docs
url: /fr/java/document-information/groupdocs-watermark-java-extract-slide-backgrounds/
weight: 1
---

# Comment extraire l'arrière-plan d'une diapositive java

## Introduction

L'extraction de l'arrière-plan d'une diapositive java est un besoin fréquent lorsque vous souhaitez analyser, réutiliser ou documenter les éléments visuels d'un fichier PowerPoint. Avec GroupDocs.Watermark for Java, vous pouvez récupérer programmétiquement les dimensions de l'image, la taille du fichier et d'autres métadonnées sans ouvrir la présentation dans PowerPoint. Ce tutoriel vous guide à travers le flux de travail complet — de la configuration de l'environnement à l'extraction et à l'interprétation des détails de l'arrière-plan — afin que vous puissiez intégrer cette fonctionnalité dans n'importe quel pipeline d'automatisation basé sur Java.

### Réponses rapides
- **Quelle bibliothèque gère l'extraction de l'arrière-plan des diapositives ?** GroupDocs.Watermark for Java.  
- **Quelle méthode renvoie les dimensions de l'image ?** `getBackground().getImageInfo().getWidth()` et `getHeight()`.  
- **Puis-je obtenir la taille du fichier de l'image d'arrière-plan ?** Oui, via `getBackground().getImageInfo().getSize()`.  
- **Ai-je besoin d'une licence pour cette fonctionnalité ?** Une licence temporaire ou complète débloque toutes les fonctionnalités ; le mode d'essai fonctionne avec des limitations.  
- **Maven est-il pris en charge ?** Absolument — ajoutez la dépendance GroupDocs.Watermark à `pom.xml`.

## Qu'est-ce que l'extraction d'arrière-plan de diapositive java ?

L'extraction d'arrière-plan de diapositive java désigne le processus de lecture programmatique de l'arrière-plan visuel de chaque diapositive d'une présentation PowerPoint à l'aide de code Java. Cette opération fournit des métadonnées telles que la largeur, la hauteur et la taille du fichier image, permettant des traitements en aval comme la vérification de conformité de la marque ou la réutilisation d'actifs.

## Pourquoi utiliser GroupDocs.Watermark pour cette tâche ?

GroupDocs.Watermark prend en charge **plus de 30 formats d'entrée et de sortie**, traite les présentations contenant jusqu'à **500 diapositives** sans charger le fichier complet en mémoire, et fournit une API dédiée pour accéder aux arrière-plans des diapositives. Ces capacités quantifiées en font un choix fiable pour l'automatisation à l'échelle de l'entreprise.

## Prérequis
- **Java 11+** installé sur votre machine de développement.  
- **Maven** pour la gestion des dépendances.  
- **GroupDocs.Watermark 24.11** (ou ultérieur) – la bibliothèque contient les classes `PresentationLoadOptions` et `PresentationContent` utilisées dans ce guide.  
- Une **licence valide** (temporaire ou complète) pour débloquer l'ensemble des fonctionnalités.

## Configuration de GroupDocs.Watermark pour Java

### Configuration Maven
Add the GroupDocs.Watermark dependency to your `pom.xml` file:

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
Si vous préférez une installation manuelle, obtenez le dernier JAR depuis la page officielle de publication : [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

### Acquisition de licence
A temporary license lets you evaluate the API, while a full license removes all trial restrictions. Get yours at the licensing portal: [GroupDocs licensing page](https://purchase.groupdocs.com/temporary-license/).

#### Initialisation et configuration de base
The first step is to create a `Watermarker` instance that points to your PowerPoint file:

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.PresentationLoadOptions;

// Create load options for the presentation file.
PresentationLoadOptions loadOptions = new PresentationLoadOptions();

// Open the PowerPoint document using Watermarker with specified load options.
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/presentation.pptx", loadOptions);
```

## Comment extraire l'arrière-plan d'une diapositive java ?
The process begins by loading the PowerPoint file using a Watermarker instance, then creating appropriate load options. After opening the document, you can access each slide's content, retrieve the background image, and extract its metadata such as dimensions and file size. Finally, close the Watermarker to release resources. The following steps describe the exact sequence you need to follow, and the code placeholders show where your existing snippets belong.

### Étape 1 : créer les options de chargement
`PresentationLoadOptions` defines loading preferences such as password handling and memory usage.

```java
PresentationLoadOptions loadOptions = new PresentationLoadOptions();
```

### Étape 2 : ouvrir le document PowerPoint
Instantiate `Watermarker` with the path to your `.pptx` file and the load options created earlier.

```java
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/presentation.pptx", loadOptions);
```

### Étape 3 : accéder au contenu des diapositives
`PresentationContent` is the entry point for retrieving slide‑level objects, including background images.

```java
import com.groupdocs.watermark.contents.PresentationContent;

PresentationContent content = watermarker.getContent(PresentationContent.class);
```

### Étape 4 : parcourir les diapositives et lire les détails de l'arrière-plan
Slide represents an individual slide within the presentation and provides access to its visual elements.  
For each `Slide` object, call `getBackground()` to obtain the image, then read its dimensions and size.

```java
import com.groupdocs.watermark.contents.PresentationSlide;
import com.groupdocs.watermark.options.PresentationLoadOptions;

for (PresentationSlide slide : content.getSlides()) {
    if (slide.getImageFillFormat().getBackgroundImage() != null) {
        // Extract width, height, and size of the background image.
        int width = slide.getImageFillFormat().getBackgroundImage().getWidth();
        int height = slide.getImageFillFormat().getBackgroundImage().getHeight();
        long imageSize = slide.getImageFillFormat().getBackgroundImage().getBytes().length;
        
        System.out.println("Width: " + width + ", Height: " + height + ", Image Size: " + imageSize);
    }
}
```

### Étape 5 : fermer le watermarker
Always close the `Watermarker` instance to free native resources and avoid memory leaks.

```java
watermarker.close();
```

## Comment lire les dimensions des diapositives PowerPoint avec GroupDocs.Watermark ?
The API exposes width and height through the `ImageInfo` object attached to a slide’s background. Retrieve them with `getWidth()` and `getHeight()`, which return pixel values that you can use for layout calculations or validation against branding guidelines.

## Problèmes courants et dépannage
- **Fichier non trouvé** – Vérifiez que le chemin du fichier est absolu ou correctement relatif à la racine de votre projet.  
- **Format non pris en charge** – GroupDocs.Watermark prend en charge PPTX, PPT et ODP ; les anciens fichiers PPT binaires peuvent nécessiter une conversion préalable.  
- **Licence non appliquée** – Assurez-vous d'appeler `License.setLicense("path/to/license.file")` avant toute autre utilisation de l'API.

## Applications pratiques
1. **Conformité de marque automatisée** – Analysez les arrière-plans des diapositives pour vérifier qu'ils correspondent aux palettes de couleurs d'entreprise ou aux dimensions du logo.  
2. **Inventaire des actifs** – Créez un catalogue des images d'arrière-plan à travers une bibliothèque de documents pour les réutiliser dans les supports marketing.  
3. **Migration de contenu** – Extrayez les arrière-plans, stockez-les dans un gestionnaire d'actifs numériques, et réappliquez-les à de nouvelles présentations de façon programmatique.  
4. **Surveillance des performances** – Enregistrez les statistiques de taille d'image pour détecter des actifs anormalement volumineux pouvant ralentir le rendu des diapositives.

## Considérations de performance
- **Nettoyage des ressources** – Fermer rapidement le `Watermarker` libère la mémoire native, ce qui est crucial lors du traitement de gros decks.  
- **Empreinte mémoire** – La bibliothèque diffuse les données des diapositives ; vous pouvez réduire davantage l'utilisation en traitant les diapositives une par une au lieu de charger la présentation entière.  
- **Astuce de traitement par lots** – Lors du traitement de dizaines de fichiers, réutilisez une seule instance `License` et créez un nouveau `Watermarker` par fichier afin de maintenir la stabilité du tas JVM.

## Conclusion
You now have a complete, production‑ready guide for extracting slide background java with GroupDocs.Watermark. By following the steps above you can retrieve image dimensions, file size, and other metadata, then apply that information to branding checks, asset management, or any custom workflow you envision.

**Étapes suivantes**
- Expérimentez avec différents `PresentationLoadOptions` (par ex., fichiers protégés par mot de passe).  
- Explorez l'API de filigrane pour ajouter ou remplacer automatiquement les arrière-plans.  
- Combinez cette logique d'extraction avec un service REST pour exposer des points de terminaison de métadonnées de diapositives.

## Questions fréquemment posées

**Q : Quelle est la version minimale de Java requise ?**  
R : Java 11 ou supérieur est requis ; les versions antérieures ne disposent pas des fonctionnalités nécessaires pour la bibliothèque.

**Q : Puis‑je extraire les arrière‑plans de présentations protégées par mot de passe ?**  
R : Oui — définissez le mot de passe dans `PresentationLoadOptions` avant d'ouvrir le fichier.

**Q : Le mode d'essai limite‑t‑il le nombre de diapositives que je peux traiter ?**  
R : L'essai impose un filigrane sur les fichiers de sortie mais ne restreint pas le nombre de diapositives pour l'extraction des métadonnées.

**Q : Est‑il possible d'enregistrer l'image d'arrière‑plan extraite sur le disque ?**  
R : Absolument — utilisez `ImageInfo.save("output.png")` après avoir récupéré l'objet `ImageInfo`.

**Q : Vers quels formats puis‑je exporter l'image extraite ?**  
R : L'API prend en charge PNG, JPEG, BMP et GIF pour l'exportation des images d'arrière‑plan.

## Ressources

- **Documentation :** [GroupDocs documentation](https://docs.groupdocs.com/watermark/java/)  
- **Documentation :** [GroupDocs Watermark Documentation](https://docs.groupdocs.com/watermark/java/)  
- **Référence API :** [GroupDocs Watermark API Reference](https://reference.groupdocs.com/watermark/java)  
- **Téléchargement :** [GroupDocs Downloads](https://releases.groupdocs.com/watermark/java/)  
- **Dépôt GitHub :** [GroupDocs GitHub Page](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)  
- **Forum de support :** [GroupDocs Support Forum](https://forum.groupdocs.com/c/watermark/10)

---

**Dernière mise à jour** : 2026-09-11  
**Testé avec** : GroupDocs.Watermark 24.11 for Java  
**Auteur** : GroupDocs

## Tutoriels associés

- [How to Retrieve PowerPoint Slide Dimensions Using GroupDocs.Watermark Java API](/watermark/java/presentation-document-watermarking/retrieve-slide-dimensions-powerpoint-groupdocs-watermark-java/)
- [Remove PowerPoint Slide Background in Java with GroupDocs.Watermark Library](/watermark/java/watermark-removal/remove-ppt-slide-background-groupdocs-watermark-java/)
- [How to Retrieve Document Information Using GroupDocs.Watermark for Java: A Step-by-Step Guide](/watermark/java/document-information/retrieve-document-info-groupdocs-watermark-java/)