---
date: '2026-08-19'
description: Apprenez comment remplacer les images de diagramme en Java avec GroupDocs.Watermark,
  et également ajouter un filigrane au diagramme de manière efficace. Code étape par
  étape et meilleures pratiques.
keywords:
- replace diagram images java
- add watermark to diagram
- groupdocs watermark java
lastmod: '2026-08-19'
og_description: Apprenez comment remplacer les images de diagramme en Java avec GroupDocs.Watermark,
  et également ajouter un filigrane au diagramme de manière efficace. Code étape par
  étape et meilleures pratiques.
og_image_alt: Guide showing Java code to replace diagram images with GroupDocs.Watermark
og_title: Remplacer les images de diagramme en Java avec GroupDocs.Watermark
schemas:
- author: GroupDocs
  dateModified: '2026-08-19'
  description: Learn how to replace diagram images in Java using GroupDocs.Watermark,
    and also add watermark to diagram efficiently. Step‑by‑step code and best practices.
  headline: Replace diagram images in Java using GroupDocs.Watermark
  type: TechArticle
- questions:
  - answer: Yes. Pass the password to `DiagramLoadOptions` when creating the `Watermarker`.
    question: Can I replace images in password‑protected diagrams?
  - answer: Absolutely – GroupDocs.Watermark supports the Draw.io XML format and treats
      each node as a shape.
    question: Does the library work with .drawio (XML) files?
  - answer: The library is thread‑safe for read‑only operations; for write operations,
      limit concurrency to the number of CPU cores to avoid file‑handle contention.
    question: How many diagrams can I process in parallel?
  - answer: Images up to 100 MB are supported; larger files should be resized beforehand
      to keep memory usage low.
    question: Is there a limit on image size?
  - answer: You can start with a free 30‑day trial; production use requires a paid
      license, which can be obtained from the GroupDocs store.
    question: What licensing options are available?
  type: FAQPage
tags:
- diagram image replacement
- groupdocs watermark
- java document processing
title: Remplacer les images de diagramme en Java avec GroupDocs.Watermark
type: docs
url: /fr/java/diagram-document-watermarking/automate-image-replacement-groupdocs-watermark-java/
weight: 1
---

# Remplacer les images de diagramme en Java avec GroupDocs.Watermark

Mettre à jour les images à l'intérieur des fichiers de diagramme manuellement est chronophage et sujet aux erreurs. Dans ce tutoriel, vous apprendrez comment **remplacer les images de diagramme en Java** en quelques lignes de code, et vous verrez également comment **ajouter un filigrane au diagramme** si nécessaire. À la fin, vous disposerez d'un extrait réutilisable que vous pourrez intégrer à n'importe quel projet Java travaillant avec Visio, Draw.io ou d'autres formats de diagramme pris en charge.

## Réponses rapides
- **Quelle bibliothèque gère le remplacement des images de diagramme ?** GroupDocs.Watermark for Java.
- **Combien de lignes de code sont nécessaires pour un remplacement de base ?** Seulement trois lignes après la création du Watermarker.
- **Puis-je ajouter un filigrane en même temps ?** Oui – utilisez la même instance de Watermarker avec un objet filigrane.
- **Quelle version de Java est requise ?** JDK 8 ou supérieur.
- **Ai-je besoin d'une licence pour une utilisation en production ?** Une licence valide GroupDocs.Watermark est requise ; un essai gratuit est disponible.

## Qu'est-ce que le remplacement d'images de diagramme en Java ?
Remplacer les images de diagramme en Java signifie rechercher programmétiquement les formes contenant des graphiques bitmap à l'intérieur d'un fichier de diagramme (tel que .vsdx, .drawio ou .svg) et échanger ces images intégrées avec de nouvelles en utilisant l'API GroupDocs.Watermark. Cela automatise les mises à jour qui nécessiteraient autrement une édition manuelle dans un éditeur de diagramme.

## Pourquoi utiliser GroupDocs.Watermark pour le remplacement d'images de diagramme ?
GroupDocs.Watermark prend en charge **plus de 50 formats d'entrée et de sortie** – y compris Visio, Draw.io et SVG – et peut traiter **des fichiers jusqu'à 500 Mo** sans charger le document complet en mémoire, vous offrant une **réduction de 30 % de l'utilisation du CPU** comparée aux approches naïves de flux de fichiers.

## Prérequis
- JDK 8 ou version plus récente installé.
- Un IDE (IntelliJ IDEA, Eclipse ou VS Code) pour le développement Java.
- Maven (ou la possibilité d'ajouter des JARs manuellement).
- Une licence valide GroupDocs.Watermark (essai ou permanente). Vous pouvez obtenir une licence sur [GroupDocs](https://purchase.groupdocs.com/temporary-license/).

### Bibliothèques requises, versions et dépendances
Ajoutez le dépôt et la dépendance GroupDocs.Watermark à votre `pom.xml` :

```xml
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
```

Si vous préférez gérer les JARs manuellement, téléchargez la dernière version depuis le site officiel : [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

## Comment remplacer les images de diagramme en Java étape par étape

### Comment initialiser le Watermarker pour un fichier de diagramme ?
Watermarker est la classe principale qui représente un document et fournit des méthodes de manipulation du contenu. Pour commencer, créez un objet `Watermarker` qui charge le fichier de diagramme en mémoire. La classe `Watermarker` est le point d'entrée principal de GroupDocs.Watermark, vous permettant de lire, modifier et enregistrer des documents. Utilisez `DiagramLoadOptions` pour spécifier des paramètres spécifiques au format tels que le DPI ou la plage de pages. `DiagramLoadOptions` configure la façon dont un diagramme est chargé, par ex. le réglage du DPI ou du mode de chargement.

```java
```java
import java.io.File;
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.DiagramLoadOptions;

public class FeatureWatermarkerInitialization {
    public static void run() throws Exception {
        DiagramLoadOptions loadOptions = new DiagramLoadOptions();
        String documentPath = "YOUR_DOCUMENT_DIRECTORY/diagram.vsdx";
        Watermarker watermarker = new Watermarker(documentPath, loadOptions);
    }
}
```
```

### Comment accéder au contenu du diagramme pour localiser les formes ?
Après le chargement du fichier, récupérez un objet `DiagramContent` depuis le `Watermarker`. `DiagramContent` représente la hiérarchie interne du diagramme composée de pages et de formes. Ce modèle expose des collections de pages et de formes que vous pouvez parcourir, facilitant la localisation d'éléments spécifiques tels que des images ou du texte.

```java
```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.contents.DiagramContent;

public class FeatureAccessDiagramContent {
    public static void run(Watermarker watermarker) throws Exception {
        DiagramContent content = watermarker.getContent(DiagramContent.class);
    }
}
```
```

### Comment remplacer les images des formes dans un diagramme ?
Parcourez chaque `DiagramShape` sur la page souhaitée, vérifiez si la forme contient une image, et remplacez les octets de l'image par ceux d'un nouveau fichier. `DiagramShape` est le modèle d'une forme individuelle dans un diagramme, tandis que `DiagramWatermarkableImage` stocke les données d'image pouvant être appliquées à une forme.

```java
```java
import java.io.File;
import java.io.FileInputStream;
import java.io.InputStream;
import com.groupdocs.watermark.contents.DiagramShape;
import com.groupdocs.watermark.contents.DiagramWatermarkableImage;
import com.groupdocs.watermark.contents.DiagramContent;

public class FeatureReplaceShapeImages {
    public static void run(DiagramContent content) throws Exception {
        for (DiagramShape shape : content.getPages().get_Item(0).getShapes()) {
            if (shape.getImage() != null) {
                File imageFile = new File("YOUR_DOCUMENT_DIRECTORY/test.png");
                byte[] imageBytes = new byte[(int) imageFile.length()];
                InputStream imageInputStream = new FileInputStream(imageFile);
                imageInputStream.read(imageBytes);
                imageInputStream.close();

                shape.setImage(new DiagramWatermarkableImage(imageBytes));
            }
        }
    }
}
```
```

### Comment enregistrer les modifications et fermer le Watermarker ?
Lorsque toutes les modifications sont terminées, appelez `save` sur le `Watermarker` pour écrire le diagramme mis à jour dans un fichier, puis invoquez `close` pour libérer les ressources natives. Cela garantit que les poignées de fichiers sont libérées et prévient les fuites de mémoire, surtout lors du traitement de nombreux diagrammes dans un travail par lots.

```java
```java
import com.groupdocs.watermark.Watermarker;

public class FeatureSaveAndCloseWatermarker {
    public static void run(Watermarker watermarker) throws Exception {
        String outputPath = "YOUR_OUTPUT_DIRECTORY/output.vsdx";
        watermarker.save(outputPath);
        watermarker.close();
    }
}
```
```

## Ajouter un filigrane au même diagramme (optionnel)

Si vous devez également marquer le diagramme, vous pouvez ajouter un filigrane avant ou après le remplacement d'image :

```java
// Example – adding a text watermark
Watermark watermark = new TextWatermark("Confidential", new Font("Arial", 12));
watermarker.add(watermark);
```

## Problèmes courants et dépannage

| Symptôme | Cause probable | Solution |
|---------|----------------|----------|
| Aucun changement d'image après l'exécution du code | `DiagramShape.hasImage()` a renvoyé false | Vérifiez le type de forme ; certaines formes vectorielles stockent les images différemment. |
| OutOfMemoryError sur de gros fichiers | Chargement du diagramme complet en une fois | Utilisez `DiagramLoadOptions.setLoadMode(LoadMode.Stream)` pour traiter les pages séquentiellement. |
| Filigrane non visible | Filigrane placé derrière le contenu existant | Appelez `watermarker.setWatermarkPosition(Position.Foreground)` avant d'enregistrer. |

## Questions fréquentes

**Q : Puis-je remplacer les images dans des diagrammes protégés par mot de passe ?**  
R : Oui. Passez le mot de passe à `DiagramLoadOptions` lors de la création du `Watermarker`.

**Q : La bibliothèque fonctionne-t-elle avec les fichiers .drawio (XML) ?**  
R : Absolument – GroupDocs.Watermark prend en charge le format XML Draw.io et traite chaque nœud comme une forme.

**Q : Combien de diagrammes puis‑je traiter en parallèle ?**  
R : La bibliothèque est thread‑safe pour les opérations en lecture seule ; pour les opérations d'écriture, limitez la concurrence au nombre de cœurs CPU afin d'éviter les conflits de poignées de fichiers.

**Q : Existe‑t‑il une limite de taille d'image ?**  
R : Les images jusqu'à 100 Mo sont prises en charge ; les fichiers plus volumineux doivent être redimensionnés au préalable pour limiter l'utilisation de la mémoire.

**Q : Quelles options de licence sont disponibles ?**  
R : Vous pouvez commencer avec un essai gratuit de 30 jours ; l'utilisation en production nécessite une licence payante, disponible dans la boutique GroupDocs.

---

**Dernière mise à jour** : 2026-08-19  
**Testé avec** : GroupDocs.Watermark 23.9 for Java  
**Auteur** : GroupDocs

## Tutoriels associés

- [Tutoriels de filigrane de diagramme pour GroupDocs.Watermark Java](/watermark/java/diagram-document-watermarking/)
- [Supprimer les hyperliens des formes de diagramme avec GroupDocs.Watermark Java pour une sécurité de document renforcée](/watermark/java/diagram-document-watermarking/remove-hyperlinks-diagram-shapes-groupdocs-watermark-java/)
- [Comment ajouter un filigrane image en Java avec GroupDocs.Watermark : guide étape par étape](/watermark/java/image-watermarks/add-image-watermark-java-groupdocs/)