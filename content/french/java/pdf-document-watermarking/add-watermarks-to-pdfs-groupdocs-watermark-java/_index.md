---
date: '2026-08-09'
description: Apprenez comment ajouter un watermark à un PDF en utilisant GroupDocs.Watermark
  for Java. Cet exemple java pdf watermark montre les watermarks texte et image, et
  l'enregistrement de PDFs avec watermark.
keywords:
- add watermark to pdf
- save pdf with watermark
- java pdf watermark example
lastmod: '2026-08-09'
og_description: Apprenez comment ajouter un watermark à un PDF en utilisant GroupDocs.Watermark
  for Java. Cet exemple java pdf watermark étape par étape vous aide à enregistrer
  rapidement un PDF avec watermark.
og_image_alt: Guide showing how to add text and image watermarks to PDF files in Java
og_title: Ajouter un watermark à un PDF avec GroupDocs.Watermark for Java
schemas:
- author: GroupDocs
  dateModified: '2026-08-09'
  description: Learn how to add watermark to PDF using GroupDocs.Watermark for Java.
    This java pdf watermark example shows text and image watermarks, saving PDFs with
    watermark.
  headline: Add watermark to PDF with GroupDocs.Watermark for Java
  type: TechArticle
- description: Learn how to add watermark to PDF using GroupDocs.Watermark for Java.
    This java pdf watermark example shows text and image watermarks, saving PDFs with
    watermark.
  name: Add watermark to PDF with GroupDocs.Watermark for Java
  steps:
  - name: create TextWatermark instance
    text: 'Create a `TextWatermark` using the desired text and font settings: This
      example sets the watermark text to “Protected image” using Arial, size 8.'
  - name: set alignment
    text: 'Center the watermark horizontally and vertically for uniform positioning:'
  - name: rotate watermark
    text: 'Apply a 45‑degree rotation to make the watermark harder to remove:'
  - name: configure sizing
    text: 'Scale the watermark relative to the target image dimensions:'
  - name: load image file
    text: 'Load the watermark image from disk: Replace the placeholder path with the
      actual location of your logo or seal.'
  - name: set alignment
    text: 'Center the image watermark for balanced visual impact:'
  - name: rotate image watermark
    text: 'Apply a –30‑degree rotation to introduce visual variation:'
  - name: configure sizing
    text: 'Define the image size as a percentage of the underlying image’s width:'
  - name: open the document
    text: 'Instantiate a `Watermarker` with the path to your source PDF:'
  - name: retrieve images
    text: 'Collect all images from the PDF that can receive a watermark:'
  type: HowTo
- questions:
  - answer: Yes. Open the document with `new Watermarker("file.pdf", "password")`
      and then apply the watermark as usual.
    question: Can I add a watermark to a password‑protected PDF?
  - answer: Absolutely. Loop through a folder of PDFs, instantiate a `Watermarker`
      for each file, apply the same watermark objects, and save the results.
    question: Does the API support batch processing of multiple PDFs?
  - answer: The library can handle **500+ watermarks per document** without performance
      degradation, thanks to its optimized rendering engine.
    question: What is the maximum number of watermarks I can add to a single PDF?
  - answer: Yes. Use the `setOpacity(0)` method on the watermark object to embed it
      invisibly for forensic tracking.
    question: Is it possible to make the watermark invisible (metadata only)?
  - answer: GroupDocs.Watermark for Java supports JDK 8, 11, and 17, ensuring compatibility
      with both legacy and modern applications.
    question: Which Java versions are officially supported?
  type: FAQPage
tags:
- pdf watermark
- GroupDocs.Watermark
- Java document security
title: Ajouter un watermark à un PDF avec GroupDocs.Watermark for Java
type: docs
url: /fr/java/pdf-document-watermarking/add-watermarks-to-pdfs-groupdocs-watermark-java/
weight: 1
---

# Ajouter un filigrane à un PDF avec GroupDocs.Watermark pour Java

## Introduction

Dans le paysage numérique actuel, protéger la propriété intellectuelle est crucial, et **add watermark to PDF** est l'une des méthodes les plus efficaces pour le faire. Ce tutoriel vous guide dans l'utilisation de GroupDocs.Watermark pour Java afin d'intégrer des filigranes texte et image dans des fichiers PDF. À la fin, vous serez capable de :

- Initialiser des filigranes texte et image
- Appliquer des filigranes de manière conditionnelle en fonction des dimensions de l'image
- **save PDF with watermark** tout en préservant la qualité originale

Prêt à sécuriser vos documents ? Commençons !

## Réponses rapides

- **Quelle bibliothèque ajoute des filigranes aux PDF en Java ?** GroupDocs.Watermark for Java.  
- **Puis-je ajouter à la fois des filigranes texte et image ?** Oui, l'API prend en charge les deux types en une seule exécution.  
- **Ai-je besoin d'une licence pour le développement ?** Un essai gratuit suffit pour les tests ; une licence permanente est requise pour la production.  
- **Quels formats de fichiers sont pris en charge ?** Plus de 30 formats, dont PDF, DOCX, PPTX et les images.  
- **Quelle taille de PDF peut être traitée ?** Jusqu'à 2 000 pages sans charger le fichier complet en mémoire.  

## Qu'est-ce que add watermark to PDF ?

**Add watermark to PDF** signifie l'intégration de marques visibles ou invisibles — telles que des chaînes de texte ou des logos — directement dans un fichier PDF pour indiquer la propriété, la confidentialité ou la marque. Ce processus modifie les calques visuels du document tout en conservant le contenu original.

## Pourquoi utiliser GroupDocs.Watermark pour Java ?

GroupDocs.Watermark prend en charge **plus de 30 formats de documents**, peut traiter des PDF jusqu'à **2 000 pages** en un seul passage, et ajoute jusqu'à **500 filigranes par document** sans impact notable sur les performances. Son API est entièrement thread‑safe, ce qui le rend idéal pour les environnements serveur à haut débit.

## Prérequis

Avant de continuer, assurez‑vous que vous avez :

1. **Java Development Kit (JDK) :** Version 8 ou plus récente installée.  
2. **GroupDocs.Watermark for Java :** Version 24.11 (ou plus récente) ajoutée à votre projet.  
3. **Outil de construction :** Maven préféré, mais un téléchargement direct du JAR fonctionne également.  

### Configuration de l'environnement

#### Configuration Maven

Ajoutez le dépôt GroupDocs et la dépendance à votre fichier `pom.xml` :

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

#### Téléchargement direct

Sinon, téléchargez le dernier JAR depuis la page officielle des versions : [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

### Acquisition de licence

Pour un essai gratuit ou une licence temporaire, visitez le portail de licence : [GroupDocs Licensing](https://purchase.groupdocs.com/temporary-license). Les déploiements en production doivent utiliser une licence achetée pour supprimer toutes les limitations d'essai.

## Configuration de GroupDocs.Watermark pour Java

Après avoir ajouté la bibliothèque, importez les classes requises dans votre fichier source Java :

```java
import com.groupdocs.watermark.Watermarker;
```

## Guide d'implémentation

Nous diviserons l'implémentation en sections logiques, chacune répondant à une question spécifique.

### Comment ajouter un filigrane à un PDF en Java ?

`Watermarker` est la classe principale qui charge un document et permet d'appliquer des filigranes.  
Chargez votre PDF avec `new Watermarker("input.pdf")` puis appliquez un objet filigrane avant d'appeler `save("output.pdf")`. Cette approche en deux étapes gère à la fois les filigranes texte et image en un seul passage, garantissant que le fichier est **saved PDF with watermark** efficacement.

### Initialiser un filigrane texte

**Définition d'ancre :** `TextWatermark` est la classe représentant une superposition textuelle qui peut être placée sur des pages, des images ou des graphiques vectoriels au sein d'un document.

#### Étape 1 : créer une instance TextWatermark

Créez un `TextWatermark` en utilisant le texte souhaité et les paramètres de police :

```java
// Create a text watermark with custom settings
TextWatermark textWatermark = new TextWatermark("Protected image", new Font("Arial", 8));
```

Cet exemple définit le texte du filigrane à « Protected image » en utilisant Arial, taille 8.

#### Étape 2 : définir l'alignement

Centrer le filigrane horizontalement et verticalement pour un positionnement uniforme :

```java
// Align watermark to the center of images
textWatermark.setHorizontalAlignment(HorizontalAlignment.Center);
textWatermark.setVerticalAlignment(VerticalAlignment.Center);
```

#### Étape 3 : faire pivoter le filigrane

Appliquer une rotation de 45 degrés pour rendre le filigrane plus difficile à enlever :

```java
// Rotate the watermark by 45 degrees
textWatermark.setRotateAngle(45);
```

#### Étape 4 : configurer la taille

Redimensionner le filigrane proportionnellement aux dimensions de l'image cible :

```java
// Scale watermark based on parent image size
textWatermark.setSizingType(SizingType.ScaleToParentDimensions);
textWatermark.setScaleFactor(1);
```

### Initialiser un filigrane image

**Définition d'ancre :** `ImageWatermark` encapsule une image (PNG, JPEG, BMP, etc.) qui sera superposée au contenu du document en tant que filigrane.

#### Étape 1 : charger le fichier image

Chargez l'image du filigrane depuis le disque :

```java
// Load an image file as a watermark
ImageWatermark imageWatermark = new ImageWatermark("YOUR_DOCUMENT_DIRECTORY\ProtectJpg");
```

Remplacez le chemin de l'espace réservé par l'emplacement réel de votre logo ou sceau.

#### Étape 2 : définir l'alignement

Centrer le filigrane image pour un impact visuel équilibré :

```java
// Align image watermark to the center
imageWatermark.setHorizontalAlignment(HorizontalAlignment.Center);
imageWatermark.setVerticalAlignment(VerticalAlignment.Center);
```

#### Étape 3 : faire pivoter le filigrane image

Appliquer une rotation de –30 degrés pour introduire une variation visuelle :

```java
// Rotate the image watermark by -45 degrees
textWatermark.setRotateAngle(-45);
```

#### Étape 4 : configurer la taille

Définir la taille de l'image en pourcentage de la largeur de l'image sous-jacente :

```java
// Scale the image watermark relative to its parent dimensions
imageWatermark.setSizingType(SizingType.ScaleToParentDimensions);
imageWatermark.setScaleFactor(1);
```

### Ajouter des filigranes aux images d'un document

**Définition d'ancre :** `Watermarker` est la classe principale qui charge un document, donne accès à ses éléments, et écrit les filigranes dans le fichier.

#### Étape 1 : ouvrir le document

Instanciez un `Watermarker` avec le chemin de votre PDF source :

```java
// Open the PDF containing images for watermarking
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY\document.pdf");
```

#### Étape 2 : récupérer les images

Collectez toutes les images du PDF pouvant recevoir un filigrane :

```java
// Get a collection of all images within the PDF
WatermarkableImageCollection images = watermarker.getImages();
```

#### Étape 3 : ajouter des filigranes conditionnellement

Pour chaque image, vérifiez ses dimensions ; si la largeur dépasse 300 px, appliquez le filigrane texte, sinon utilisez le filigrane image :

```java
for (int i = 0; i < images.getCount(); i++) {
    // Check if the image exceeds specific size criteria
    if (images.get_Item(i).getWidth() > 100 && images.get_Item(i).getHeight() > 100) {
        // Alternate between text and image watermarks
        if (i % 2 == 0) {
            images.get_Item(i).add(textWatermark);
        } else {
            images.get_Item(i).add(imageWatermark);
        }
    }
}
```

Cette logique conditionnelle garantit que seules les images appropriées reçoivent la superposition texte la plus visible, optimisant le temps de traitement.

#### Étape 4 : libérer les ressources d'image

Après le traitement, fermez l'objet filigrane image pour libérer les ressources natives :

```java
// Close the image watermark instance after use
imageWatermark.close();
```

#### Étape 5 : enregistrer les modifications

Conservez les modifications en enregistrant le document dans un nouveau fichier :

```java
// Save the PDF with added watermarks in a new file
watermarker.save("YOUR_OUTPUT_DIRECTORY\document.pdf");
```

Le fichier résultant est une version **save PDF with watermark** prête pour la distribution.

#### Étape 6 : nettoyage

Disposez de l'instance `Watermarker` pour éviter les fuites de mémoire :

```java
// Close the main watermarker to release document resources
watermarker.close();
```

## Problèmes courants et dépannage

- **Erreurs de licence :** Assurez‑vous que le chemin du fichier de licence est correctement défini via `License.setLicense("license_file_path")`. Une licence manquante ou expirée lève une `LicenseException`.  
- **PDF volumineux :** Pour les documents de plus de 1 000 pages, activez le mode streaming en appelant `watermarker.setStreamMode(true)` afin de réduire la consommation de mémoire.  
- **Formats d'image non pris en charge :** GroupDocs.Watermark prend en charge PNG, JPEG, BMP et GIF. Convertir d'autres formats en PNG avant le chargement évite `UnsupportedFormatException`.  

## Questions fréquemment posées

**Q : Puis‑je ajouter un filigrane à un PDF protégé par mot de passe ?**  
R : Oui. Ouvrez le document avec `new Watermarker("file.pdf", "password")` puis appliquez le filigrane comme d'habitude.

**Q : L'API prend‑elle en charge le traitement par lots de plusieurs PDF ?**  
R : Absolument. Parcourez un dossier de PDF, instanciez un `Watermarker` pour chaque fichier, appliquez les mêmes objets filigrane et enregistrez les résultats.

**Q : Quel est le nombre maximal de filigranes que je peux ajouter à un seul PDF ?**  
R : La bibliothèque peut gérer **plus de 500 filigranes par document** sans dégradation des performances, grâce à son moteur de rendu optimisé.

**Q : Est‑il possible de rendre le filigrane invisible (métadonnées uniquement) ?**  
R : Oui. Utilisez la méthode `setOpacity(0)` sur l'objet filigrane pour l'intégrer invisiblement à des fins de suivi judiciaire.

**Q : Quelles versions de Java sont officiellement prises en charge ?**  
R : GroupDocs.Watermark pour Java prend en charge JDK 8, 11 et 17, assurant la compatibilité avec les applications anciennes et modernes.

## Applications pratiques

L'ajout de filigranes peut servir à divers scénarios réels :

1. **Sécurité des documents :** Marquez les fichiers confidentiels pour décourager le partage non autorisé.  
2. **Protection de la marque :** Superposez les logos de l'entreprise sur les PDF marketing.  
3. **Affirmation du droit d'auteur :** Intégrez les noms d'auteur ou les symboles de copyright sur les œuvres publiées.  
4. **Gestion des versions :** Apposez des numéros de version ou des dates sur les documents de brouillon.  

## Conclusion

En suivant cet **exemple de filigrane PDF Java**, vous disposez désormais d'une solution complète, prête pour la production, pour **add watermark to PDF** avec GroupDocs.Watermark pour Java. Vous pouvez personnaliser le texte, les images, la rotation et la taille, ainsi qu'appliquer conditionnellement des filigranes en fonction des dimensions de l'image — tout en maintenant le processus rapide et efficace en mémoire.

---  

**Dernière mise à jour :** 2026-08-09  
**Testé avec :** GroupDocs.Watermark 24.11 for Java  
**Auteur :** GroupDocs

## Tutoriels associés

- [Comment ajouter des filigranes texte et image à des pages PDF spécifiques en utilisant GroupDocs.Watermark pour Java](/watermark/java/pdf-document-watermarking/add-watermarks-pdf-pages-groupdocs-java/)
- [Ajouter des filigranes imprimables uniquement aux PDF avec GroupDocs.Watermark Java : Guide complet](/watermark/java/pdf-document-watermarking/groupdocs-watermark-java-print-only-pdf-watermark/)
- [Accéder et itérer sur les artefacts PDF avec GroupDocs.Watermark en Java pour le filigrane de documents](/watermark/java/pdf-document-watermarking/access-iterate-pdf-artifacts-groupdocs-watermark-java/)