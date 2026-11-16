---
date: '2026-03-20'
description: Apprenez comment ajouter un filigrane en utilisant le SDK Java GroupDocs.Watermark
  pour ajouter un filigrane image à une feuille de calcul Excel, parfait pour l'image
  de marque et la sécurité des documents.
keywords:
- GroupDocs.Watermark Java
- add image watermark Excel
- Java SDK spreadsheet watermark
title: 'Comment ajouter un filigrane : filigrane d’image dans une feuille de calcul
  Excel à l’aide du SDK Java GroupDocs.Watermark'
type: docs
url: /fr/java/spreadsheet-document-watermarking/add-image-watermark-spreadsheet-groupdocs-java/
weight: 1
---

# Comment ajouter un filigrane à une feuille de calcul Excel à l'aide du SDK Java GroupDocs.Watermark

Protéger vos fichiers Excel contre la distribution non autorisée ou simplement renforcer l'identité de votre marque peut être réalisé en ajoutant une marque visuelle qui reste visible quel que soit le mode de visualisation du fichier. Dans ce tutoriel, vous apprendrez **comment ajouter un filigrane** — plus précisément un filigrane image — au **en‑tête ou pied de page** d’une feuille de calcul Excel avec le **GroupDocs.Watermark Java SDK**. À la fin du guide, vous serez capable d’intégrer un logo, un badge de confidentialité ou toute image personnalisée directement dans votre classeur sans modifier les données des cellules.

## Réponses rapides
- **À quoi fait‑référence « how to add watermark » ?** Ajout d’une superposition d’image (ou de texte) qui apparaît sur chaque page imprimée ou sur des sections spécifiques telles que les en‑têtes/pieds de page.  
- **Quelle bibliothèque prend‑en‑charge cela en Java ?** `GroupDocs.Watermark` Java SDK (dernière version).  
- **Ai‑je besoin d’une licence ?** Une version d’essai gratuite suffit pour le développement ; une licence commerciale est requise pour la production.  
- **Puis‑je ajouter un logo à l’en‑tête ?** Oui – utilisez le filigrane image et définissez l’option d’en‑tête (`add logo to header`).  
- **Est‑il possible de traiter plusieurs feuilles simultanément ?** Parcourez les indices de feuilles de calcul et appliquez le même filigrane à chaque feuille.

## Prérequis

Pour suivre ce tutoriel, assurez‑vous d’avoir :

- **GroupDocs.Watermark for Java SDK** (version 24.11 ou plus récente).  
- **Java Development Kit (JDK)** 8 ou supérieur.  
- Une connaissance de base de Java et de la structure des fichiers Excel.  

## Configuration du SDK GroupDocs.Watermark pour Java

Tout d’abord, ajoutez les dépendances Maven nécessaires afin que le SDK soit disponible sur votre classpath.

### Configuration Maven

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

Si vous préférez ne pas utiliser Maven, récupérez le JAR le plus récent depuis la page officielle des releases : [GroupDocs releases](https://releases.groupdocs.com/watermark/java/).

**Acquisition de licence**  
- Obtenez une version d’essai gratuite ou une clé de licence temporaire pour évaluer toutes les fonctionnalités.  
- Achetez une licence complète pour les déploiements commerciaux.

### Initialisation et configuration

Créez une instance de `Watermarker` qui chargera le fichier Excel et servira de point d’entrée pour toutes les opérations de filigrane.

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.SpreadsheetLoadOptions;

// Initialize Load Options
SpreadsheetLoadOptions loadOptions = new SpreadsheetLoadOptions();

// Create Watermarker instance with your spreadsheet file path
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/spreadsheet.xlsx", loadOptions);
```

## Comment ajouter un filigrane à l’en‑tête/pied de page d’une feuille de calcul

Voici le processus étape par étape qui démontre la fonctionnalité **java add image watermark** et montre également comment **add logo to header**.

### Étape 1 : Configurer les options de chargement

Nous commençons par définir les options de chargement et ré‑instancier le `Watermarker`. Cela garantit que le SDK lit correctement le classeur.

```java
import com.groupdocs.watermark.common.HorizontalAlignment;
import com.groupdocs.watermark.common.VerticalAlignment;
import com.groupdocs.watermark.options.SpreadsheetLoadOptions;

// Load the document with specified load options
SpreadsheetLoadOptions loadOptions = new SpreadsheetLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/spreadsheet.xlsx", loadOptions);
```

### Étape 2 : Créer et configurer le filigrane image

Créez un objet `ImageWatermark` qui pointe vers l’image que vous souhaitez intégrer (par ex., un logo ou un badge « CONFIDENTIAL »). Ajustez son alignement et son redimensionnement afin qu’il s’insère correctement dans la zone d’en‑tête/pied de page.

```java
import com.groupdocs.watermark.watermarks.ImageWatermark;
import com.groupdocs.watermark.watermarks.SizingType;

// Initialize the image watermark with your logo or desired image
ImageWatermark watermark = new ImageWatermark("YOUR_DOCUMENT_DIRECTORY/logo.png");

// Set alignment and scaling for a proper fit within the header/footer
watermark.setVerticalAlignment(VerticalAlignment.Top);
watermark.setHorizontalAlignment(HorizontalAlignment.Center);
watermark.setSizingType(SizingType.ScaleToParentDimensions); // Scales with parent dimensions
watermark.setScaleFactor(1); // Adjust scale factor as needed
```

### Étape 3 : Configurer les options d’en‑tête/pied de page

Indiquez au SDK quelle feuille de calcul et quelle partie (en‑tête ou pied de page) doit recevoir le filigrane. C’est ici que vous pouvez **add logo to header** ou choisir le pied de page à la place.

```java
import com.groupdocs.watermark.options.SpreadsheetWatermarkHeaderFooterOptions;

// Set options for applying the watermark
SpreadsheetWatermarkHeaderFooterOptions headerFooterOptions = new SpreadsheetWatermarkHeaderFooterOptions();
headerFooterOptions.setWorksheetIndex(0); // Apply to first worksheet (index 0)
```

### Étape 4 : Ajouter le filigrane

Attachez maintenant le filigrane image préparé à l’emplacement d’en‑tête/pied de page sélectionné.

```java
// Add the configured watermark
watermarker.add(watermark, headerFooterOptions);
```

### Étape 5 : Enregistrer et fermer

Enregistrez les modifications dans un nouveau fichier afin que le classeur original reste intact, puis libérez les ressources.

```java
// Save the watermarked document
watermarker.save("YOUR_OUTPUT_DIRECTORY/out_spreadsheet.xlsx");

// Release resources by closing the Watermarker instance
watermarker.close();
```

#### Conseils de dépannage

- Vérifiez le chemin de l’image ; un chemin incorrect déclenche une `FileNotFoundException`.  
- Les indices de feuilles de calcul commencent à 0 ; assurez‑vous que l’indice que vous définissez existe réellement.  
- Si le filigrane apparaît déformé, ajustez `setScaleFactor` ou changez le `SizingType` en `StretchToParentDimensions`.

## Pourquoi choisir le SDK Java GroupDocs.Watermark ?

- **Prise en charge multi‑format** – fonctionne avec Excel, Word, PowerPoint, PDF et images.  
- **Édition sans perte** – les données originales des cellules restent intactes.  
- **Optimisé pour les performances** – adapté aux classeurs volumineux et au traitement par lots.  

## Cas d’utilisation pratiques

| Scénario | Comment le filigrane aide |
|----------|---------------------------|
| **Rapports confidentiels** | Ajoutez une image « CONFIDENTIAL » à chaque page imprimée. |
| **Renforcement de la marque** | Placez le logo de votre entreprise dans l’en‑tête des factures. |
| **Suivi de version** | Intégrez un badge de numéro de version qui se met à jour automatiquement. |
| **Conformité légale** | Marquez les feuilles de calcul réglementées avec un sceau de conformité. |

## Considérations de performance

- **Utilisation de la mémoire** – Surveillez le tas JVM lors du traitement de très grands classeurs.  
- **Traitement par lots** – Traitez les fichiers par groupes pour maintenir une faible empreinte mémoire.  
- **Réutilisation des objets** – Réutiliser une même instance de `Watermarker` pour plusieurs fichiers réduit la surcharge.

## FAQ

**Q : Puis‑je ajouter plusieurs filigranes à un même document ?**  
R : Oui, créez des instances supplémentaires de `ImageWatermark` et configurez chacune avant d’appeler `watermarker.add()`.

**Q : Comment supprimer un filigrane existant d’une feuille de calcul ?**  
R : Actuellement, GroupDocs.Watermark se concentre sur l’ajout de filigranes. Pour en supprimer un, vous devrez recréer le classeur sans le filigrane ou utiliser un outil qui prend en charge l’extraction de filigranes.

**Q : Quels formats d’image sont pris en charge pour les filigranes ?**  
R : Les formats courants comme PNG et JPEG sont supportés, mais consultez la [documentation GroupDocs](https://docs.groupdocs.com/watermark/java/) pour la liste complète des formats compatibles.

**Q : Est‑il possible de filigraner des feuilles de calcul protégées par mot de passe ?**  
R : Oui, tant que vous fournissez le mot de passe nécessaire lors de l’ouverture du fichier.

**Q : Comment appliquer des filigranes à toutes les feuilles d’un document ?**  
R : Parcourez chaque indice de feuille et répétez les étapes de filigrane, en définissant `headerFooterOptions.setWorksheetIndex(i)` pour chaque itération.

## Conclusion

Vous disposez maintenant d’une méthode complète et prête pour la production afin de **java add excel watermark**—plus précisément un filigrane image—en utilisant le **GroupDocs.Watermark Java SDK**. Cette approche ajoute du branding, des mentions de confidentialité ou tout autre indice visuel directement dans l’en‑tête ou le pied de page de vos fichiers Excel tout en préservant les données sous‑jacentes. N’hésitez pas à explorer d’autres types de filigranes (texte, forme) et à les combiner pour une protection de document plus riche.

---

**Dernière mise à jour :** 2026-03-20  
**Testé avec :** GroupDocs.Watermark 24.11 pour Java  
**Auteur :** GroupDocs