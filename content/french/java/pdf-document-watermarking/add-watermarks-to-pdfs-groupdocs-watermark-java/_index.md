---
date: '2026-01-23'
description: Apprenez à ajouter des filigranes texte et image aux fichiers PDF avec
  GroupDocs.Watermark pour Java – un guide complet pour la sécurité des documents
  PDF.
keywords:
- GroupDocs Watermark Java
- PDF watermarking
- Java document security
- image watermark Java
title: Comment ajouter un filigrane à un PDF avec GroupDocs.Watermark pour Java
type: docs
url: /fr/java/pdf-document-watermarking/add-watermarks-to-pdfs-groupdocs-watermark-java/
weight: 1
---

# Comment ajouter un filigrane à un PDF avec GroupDocs.Watermark pour Java

Dans le monde numérique d’aujourd’hui, **comment ajouter un filigrane à un PDF** est une question fréquente pour quiconque doit protéger la propriété intellectuelle ou les actifs de marque. Ajouter des filigranes—qu’ils soient textuels ou graphiques—vous aide à renforcer la **sécurité des documents PDF** et rend la distribution non autorisée beaucoup plus difficile. Dans ce tutoriel, vous apprendrez, étape par étape, comment utiliser **GroupDocs.Watermark pour Java** afin d’ajouter des filigranes texte et image aux documents PDF.

## Réponses rapides
- **Quelle bibliothèque ajoute des filigranes aux PDF en Java ?** GroupDocs.Watermark pour Java.  
- **Puis‑je ajouter à la fois des filigranes texte et image ?** Oui, l’API prend en charge les deux types.  
- **Ai‑je besoin d’une licence ?** Un essai gratuit suffit pour l’évaluation ; une licence payante supprime les limitations.  
- **Quelle version de Java est requise ?** JDK 8 ou supérieur.  
- **Maven est‑il supporté ?** Absolument — il suffit d’ajouter le dépôt et la dépendance.

## Qu’est‑ce que le filigrane PDF et pourquoi l’utiliser ?
Le filigrane d’un PDF intègre un marqueur visible ou invisible qui identifie la propriété, la confidentialité ou la marque. C’est une méthode légère mais puissante pour décourager la copie, prouver l’auteur et se conformer aux politiques d’entreprise.

## Prérequis

Avant de commencer, assurez‑vous d’avoir :

1. **Java Development Kit (JDK) 8+** installé sur votre machine.  
2. **GroupDocs.Watermark pour Java** (la dernière version).  
3. **Maven** (ou la possibilité d’ajouter un JAR manuellement).

### Configuration de l’environnement

#### Configuration Maven
Ajoutez le dépôt GroupDocs et la dépendance watermark à votre `pom.xml` :

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
Si vous préférez ne pas utiliser Maven, vous pouvez télécharger le JAR directement depuis [GroupDocs.Watermark pour Java releases](https://releases.groupdocs.com/watermark/java/).

### Acquisition de licence
Pour commencer avec un essai gratuit ou obtenir une licence temporaire, rendez‑vous sur [GroupDocs Licensing](https://purchase.groupdocs.com/temporary-license). Pour une utilisation en production, achetez un abonnement afin de débloquer toutes les fonctionnalités.

## Configuration de GroupDocs.Watermark pour Java

Importez la classe principale qui pilote toutes les opérations de filigrane :

```java
import com.groupdocs.watermark.Watermarker;
```

Cette importation vous donne accès à la classe `Watermarker`, qui est le point d’entrée pour ajouter des filigranes à tout type de document supporté.

## Implémentation étape par étape

Nous décomposons le processus en sections logiques : création de filigranes texte, création de filigranes image, puis application aux images contenues dans un PDF.

### 1. Initialiser un filigrane texte

**Pourquoi un filigrane texte ?** Il est léger, recherchable et idéal pour ajouter des mentions de droits d’auteur ou des déclarations de confidentialité.

#### 1.1 Créer l’instance TextWatermark
```java
// Create a text watermark with custom settings
TextWatermark textWatermark = new TextWatermark("Protected image", new Font("Arial", 8));
```

#### 1.2 Définir l’alignement
```java
// Align watermark to the center of images
textWatermark.setHorizontalAlignment(HorizontalAlignment.Center);
textWatermark.setVerticalAlignment(VerticalAlignment.Center);
```

#### 1.3 Faire pivoter le filigrane
```java
// Rotate the watermark by 45 degrees
textWatermark.setRotateAngle(45);
```

#### 1.4 Configurer la taille
```java
// Scale watermark based on parent image size
textWatermark.setSizingType(SizingType.ScaleToParentDimensions);
textWatermark.setScaleFactor(1);
```

### 2. Initialiser un filigrane image

**Quand utiliser un filigrane image ?** Idéal pour le branding avec des logos ou pour ajouter des motifs visuels complexes.

#### 2.1 Charger le fichier image
```java
// Load an image file as a watermark
ImageWatermark imageWatermark = new ImageWatermark("YOUR_DOCUMENT_DIRECTORY\\ProtectJpg");
```

#### 2.2 Définir l’alignement
```java
// Align image watermark to the center
imageWatermark.setHorizontalAlignment(HorizontalAlignment.Center);
imageWatermark.setVerticalAlignment(VerticalAlignment.Center);
```

#### 2.3 Faire pivoter le filigrane image
```java
// Rotate the image watermark by -45 degrees
textWatermark.setRotateAngle(-45);
```

#### 2.4 Configurer la taille
```java
// Scale the image watermark relative to its parent dimensions
imageWatermark.setSizingType(SizingType.ScaleToParentDimensions);
imageWatermark.setScaleFactor(1);
```

### 3. Ajouter des filigranes aux images d’un PDF

Nous allons maintenant rassembler le tout : ouvrir un PDF, localiser chaque image et appliquer le filigrane texte ou image selon la taille.

#### 3.1 Ouvrir le document PDF
```java
// Open the PDF containing images for watermarking
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY\\document.pdf");
```

#### 3.2 Récupérer toutes les images
```java
// Get a collection of all images within the PDF
WatermarkableImageCollection images = watermarker.getImages();
```

#### 3.3 Appliquer les filigranes conditionnellement
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

#### 3.4 Libérer les ressources d’image
```java
// Close the image watermark instance after use
imageWatermark.close();
```

#### 3.5 Enregistrer le PDF modifié
```java
// Save the PDF with added watermarks in a new file
watermarker.save("YOUR_OUTPUT_DIRECTORY\\document.pdf");
```

#### 3.6 Nettoyage
```java
// Close the main watermarker to release document resources
watermarker.close();
```

## Applications pratiques du filigrane PDF

| Cas d’utilisation | Comment le filigrane aide |
|-------------------|---------------------------|
| **Sécurité des documents** | Marque les fichiers confidentiels, décourageant les fuites. |
| **Protection de la marque** | Intègre les logos sur les PDF marketing, renforçant l’identité de marque. |
| **Affirmation du droit d’auteur** | Ajoute le nom de l’auteur ou le symbole © pour revendiquer la propriété. |
| **Gestion des versions** | Affiche les numéros de version ou les dates directement sur la page. |

## Pièges courants & conseils

- **Séparateurs de chemin :** Utilisez les doubles antislashs (`\\`) sous Windows ou les barres obliques (`/`) sous Linux/macOS pour éviter `FileNotFoundException`.  
- **PDF volumineux :** Traitez les images par lots ousetRotateAngle` attend des degrés ; les valeurs négatives tournent dans le sens par mot de passe ?**  
R : Oui. Ouvrez le document avec le mot de` qui accepte une chaîne de mot de passe.

**Q : La bibliothèque supporte‑t‑elle d’autres formats comme DOCX ou PPTX ?**  
R : Absolument. GroupDocs.Watermark fonctionne également avec Word, PowerPoint, Excel et les fichiers image.

**Q : Comment modifier l’opacité d’un filigrane ?**  
R : Utilisez `setOpacity(float opacity)` sur l’objet filigraneigrane uniquementR : Récupérez la collection de pages via `watermarker.getPages()` et appliquez le filigrane à l’indice de page souhaité.

**Q : Que faire si je dois ajouter un filigrane à un PDF stocké dans un bucket cloud ?**  
R : Chargez le PDF dans un `InputStream` et passez‑le au constructeur `Watermarker` ; après traitement, écrivez le flux de sortie de nouveau vers le cloud.

## Conclusion

Vous disposez maintenant d’une méthode complète, prête pour la production, pour **comment ajouter un filigrane à un PDF** en utilisant GroupDocs.Watermark pour texte et image, vous pouvez obtenir fonctionnalités de la