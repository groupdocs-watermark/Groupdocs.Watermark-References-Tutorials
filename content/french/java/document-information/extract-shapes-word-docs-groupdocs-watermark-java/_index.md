---
date: '2025-12-20'
description: Apprenez à extraire des images de documents Word et à extraire des formes
  à l'aide de GroupDocs.Watermark pour Java, idéal pour l'automatisation et la manipulation
  de documents.
keywords:
- GroupDocs.Watermark
- extract images from word
- how to extract shapes
- load word document java
title: Comment extraire des images de documents Word à l'aide de GroupDocs.Watermark
  en Java
type: docs
url: /fr/java/document-information/extract-shapes-word-docs-groupdocs-watermark-java/
weight: 1
---

# Comment extraire des images de documents Word à l'aide de GroupDocs.Watermark en Java

Dans les applications modernes de traitement de documents, **extraire des images de Word** est une exigence fréquente—que vous ayez besoin de réutiliser des graphiques, d'exécuter de l'OCR, ou simplement d'auditer le contenu. Ce tutoriel vous montre, étape par étape, comment charger un document Word en Java avec GroupDocs.Watermark puis **extraire des images de Word** tout en démontrant **comment extraire les formes**. À la fin, vous disposerez d'un extrait de code réutilisable qui s'intègre parfaitement à votre pipeline d'automatisation.

## Réponses rapides
- **Quelle bibliothèque gère l'extraction d'images ?** GroupDocs.Watermark for Java  
- **Puis-je extraire à la fois des images et des formes vectorielles ?** Oui – l'API fournit l'accès aux images et aux métadonnées des formes.  
- **Quelle version de Java est requise ?** JDK 8 ou supérieure.  
- **Ai‑je besoin d'une licence pour la production ?** Une licence commerciale est recommandée ; un essai gratuit fonctionne pour l'évaluation.  
- **Le processus est‑il efficace en mémoire pour les gros fichiers ?** Oui, vous pouvez libérer les ressources rapidement et traiter les sections de façon incrémentielle.

## Qu’est‑ce que « Extraire des images de Word » ?
Extraire des images de Word signifie localiser programmatiquement chaque image, dessin ou graphique intégré à l'intérieur d'un fichier `.docx` et récupérer ses données binaires ou ses métadonnées. Cela permet des tâches en aval telles que l'analyse d'images, la migration de contenu ou la génération de rapports dynamiques.

## Pourquoi utiliser GroupDocs.Watermark pour cette tâche ?
GroupDocs.Watermark propose une API de haut niveau qui abstrait les complexités du format OpenXML. Elle vous permet de **charger un document Word en Java** avec seulement quelques lignes de code, tout en exposant des informations détaillées sur les formes—parfait pour les développeurs qui ont besoin à la fois d'extraction d'images et d'analyse de formes.

## Prérequis
- **Java Development Kit (JDK)** 8 ou plus récent  
- **IDE** – IntelliJ IDEA, Eclipse, ou tout éditeur compatible Java  
- Connaissances de base en I/O Java  
- Accès à une licence GroupDocs.Watermark (l'essai fonctionne pour les tests)

## Configuration de GroupDocs.Watermark pour Java
Intégrez la bibliothèque via Maven ou téléchargement direct.

### Utilisation de Maven
Add the repository and dependency to your `pom.xml`:

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
Sinon, téléchargez le JAR le plus récent depuis [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

### Acquisition de licence
Pour une fonctionnalité complète, obtenez une clé de licence depuis le portail GroupDocs. Une licence d'essai temporaire peut être demandée pour explorer toutes les fonctionnalités sans restrictions.

## Guide d'implémentation
Nous diviserons l'implémentation en deux parties logiques :

1. **Comment charger un document Word en Java**  
2. **Comment extraire les formes et les images (c’est‑à‑dire extraire des images de Word)**

### Chargement d'un document Word
Tout d'abord, configurez les options de chargement et instanciez le `Watermarker`.

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.WordProcessingLoadOptions;

public void loadDocument() {
    // Configure load options for loading a Word document
    WordProcessingLoadOptions loadOptions = new WordProcessingLoadOptions();
    
    // Create an instance of Watermarker with the specified document and load options
    Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/document.docx", loadOptions);
    
    // Close the watermarker to release resources
    watermarker.close();
}
```

> **Astuce :** Remplacez `"YOUR_DOCUMENT_DIRECTORY/document.docx"` par un chemin absolu ou relatif pointant vers le fichier que vous souhaitez traiter.

### Extraction des informations de forme et d'image
Maintenant que le document est chargé, vous pouvez parcourir chaque section et chaque forme, en extrayant à la fois les données de forme vectorielle et les détails des images intégrées.

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.contents.WordProcessingContent;
import com.groupdocs.watermark.options.WordProcessingLoadOptions;

public void extractShapeInformation() {
    // Load the Word document as configured previously
    WordProcessingLoadOptions loadOptions = new WordProcessingLoadOptions();
    Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/document.docx", loadOptions);

    // Obtain WordProcessingContent from the watermarker
    WordProcessingContent content = watermarker.getContent(WordProcessingContent.class);

    // Iterate over each section in the document's content
    for (var section : content.getSections()) {
        // Iterate over each shape within the current section
        for (var shape : section.getShapes()) {
            // Check if the shape is part of a header or footer
            if (shape.getHeaderFooter() != null) {
                System.out.println("In header/footer");
            }
            
            // Output details about each shape, such as type and dimensions
            System.out.println(shape.getShapeType());
            System.out.println(shape.getWidth());
            System.out.println(shape.getHeight());
            System.out.println(shape.isWordArt());
            System.out.println(shape.getRotateAngle());
            System.out.println(shape.getAlternativeText());
            System.out.println(shape.getName());
            System.out.println(shape.getX());
            System.out.println(shape.getY());
            System.out.println(shape.getText());

            // If the shape contains an image, output its details (this is the core of “extract images from word”)
            if (shape.getImage() != null) {
                System.out.println("Image width: " + shape.getImage().getWidth());
                System.out.println("Image height: " + shape.getImage().getHeight());
                System.out.println("Image byte size: " + shape.getImage().getBytes().length);
            }
            
            // Output alignment information of the shape
            System.out.println(shape.getHorizontalAlignment());
            System.out.println(shape.getVerticalAlignment());
            System.out.println(shape.getRelativeHorizontalPosition());
            System.out.println(shape.getRelativeVerticalPosition());
        }
    }

    // Close the watermarker to release resources
    watermarker.close();
}
```

> **Pourquoi c’est important :** L'appel `shape.getImage()` vous donne un accès direct à la représentation binaire de chaque image, vous permettant de l'enregistrer sur disque, de l'envoyer sur un réseau, ou de la transmettre à une bibliothèque de traitement d'images.

## Problèmes courants et solutions
| Problème | Solution |
|---------|----------|
| **FileNotFoundException** – mauvais chemin | Vérifiez le chemin du fichier et assurez‑vous que l'application dispose des permissions de lecture. |
| **OutOfMemoryError** sur de gros documents | Traitez les sections une à une et appelez `watermarker.close()` dès que vous avez terminé un lot. |
| Les formes renvoient `null` pour `getImage()` | Toutes les formes ne sont pas des images ; certaines sont des objets de dessin. Vérifiez `shape.getShapeType()` avant d'accéder à l'image. |
| Licence non appliquée | Ajoutez `License.setLicense("path/to/license/file.lic");` avant de créer le `Watermarker`. |

## Applications pratiques
- **Génération de rapports automatisés :** Extraire les graphiques et logos des modèles pour les réutiliser dans les tableaux de bord.  
- **Audit de contenu :** Analyser les documents d'entreprise à la recherche de graphiques interdits.  
- **Projets de migration :** Exporter les images intégrées avant de transférer le contenu vers un nouveau CMS.

## Considérations de performance
- Libérez rapidement l'instance `Watermarker` (`watermarker.close()`).  
- Pour les fichiers volumineux (> 50 Mo), envisagez de diffuser les sections plutôt que de charger le document entier en mémoire.  
- Utilisez la dernière version de GroupDocs.Watermark pour des améliorations de performances.

## Conclusion
Vous disposez maintenant d'une approche complète, prête pour la production, pour **extraire des images de Word** et récupérer les métadonnées des formes à l'aide de GroupDocs.Watermark pour Java. Cette capacité ouvre des scénarios d'automatisation puissants, de la génération de rapports dynamiques à la réalisation d'audits de documents à grande échelle.

### Prochaines étapes
- Expérimentez la sauvegarde des images extraites sur disque (`Files.write(Paths.get("output.png"), shape.getImage().getBytes());`).  
- Explorez d'autres API comme la suppression ou l'ajout de filigranes.  
- Intégrez cette logique dans votre flux de travail de gestion de documents existant.

## Section FAQ
**Q : Qu’est‑ce que GroupDocs.Watermark pour Java ?**  
R : C’est une bibliothèque complète conçue pour gérer les filigranes et extraire les éléments visuels à travers divers formats de documents, améliorant l'automatisation des tâches de manipulation de documents.

**Q : Puis‑je extraire des images de fichiers Word protégés par mot de passe ?**  
R : Oui. Chargez le document avec `WordProcessingLoadOptions` incluant le mot de passe, puis poursuivez avec la même logique d'extraction.

**Q : L'API prend‑elle en charge les fichiers .doc (binaires) également ?**  
R : La bibliothèque cible principalement le format OpenXML `.docx`, mais elle peut également ouvrir les fichiers `.doc` hérités après conversion.

**Q : Comment enregistrer les images extraites sur le système de fichiers ?**  
R : Utilisez `java.nio.file.Files.write(Paths.get("image.png"), shape.getImage().getBytes());` à l'intérieur de la boucle où `shape.getImage()` n'est pas nul.

**Q : Existe‑t‑il une limite au nombre de formes que je peux traiter ?**  
R : Aucun plafond strict, mais la consommation de mémoire augmente avec la taille du document ; traitez les sections séquentiellement pour les très gros fichiers.

---

**Dernière mise à jour :** 2025-12-20  
**Testé avec :** GroupDocs.Watermark 24.11 for Java  
**Auteur :** GroupDocs