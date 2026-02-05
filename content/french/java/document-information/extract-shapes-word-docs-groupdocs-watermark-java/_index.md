---
date: '2026-02-05'
description: Apprenez à extraire les formes des documents Word à l'aide de GroupDocs.Watermark
  pour Java, y compris comment charger un document Word en Java et manipuler les données
  de forme.
keywords:
- GroupDocs.Watermark
- extract shapes from Word documents
- Java document manipulation
title: Comment extraire des formes des documents Word à l'aide de GroupDocs.Watermark
  Java
type: docs
url: /fr/java/document-information/extract-shapes-word-docs-groupdocs-watermark-java/
weight: 1
---

# Comment extraire des formes de documents Word à l'aide de GroupDocs.Watermark en Java

Dans ce tutoriel, vous découvrirez **comment extraire des formes** des documents Word avec la bibliothèque Java GroupDocs.Watermark. Que vous ayez besoin d'analyser des diagrammes, d'extraire des images intégrées ou d'automatiser la génération de rapports, l'extraction des métadonnées des formes vous donne le contrôle nécessaire pour créer des pipelines de traitement de documents plus intelligents. Nous parcourrons la configuration de la bibliothèque, le chargement d'un document Word et l'extraction d'informations détaillées sur les formes — le tout en code Java clair, étape par étape.

## Réponses rapides
- **Que signifie « extraire des formes » ?** Récupérer les métadonnées (type, taille, position, texte, images) pour chaque objet de dessin dans un fichier Word.  
- **Quelle bibliothèque gère cela ?** GroupDocs.Watermark for Java.  
- **Ai-je besoin d'une licence ?** Une version d'essai suffit pour le développement ; une licence complète supprime les limites d'utilisation.  
- **Puis-je également obtenir des images des formes ?** Oui – l'API expose les octets d'image pour les formes image.  
- **Quelle version de Java est requise ?** JDK 8 ou plus récent.

## Qu’est‑ce que « Comment extraire des formes » dans le contexte des documents Word ?
Extraire des formes signifie accéder programmatique à chaque élément de dessin — images, WordArt, formes automatiques, graphiques, et même les formes intégrées dans les en‑têtes ou pieds de page. Ces informations peuvent être utilisées pour la validation, la migration ou l'analyse basée sur le contenu.

## Pourquoi utiliser GroupDocs.Watermark pour Java ?
GroupDocs.Watermark fournit une API de haut niveau, efficace en mémoire, qui abstrait la complexité du format Office Open XML sous‑jacent. Elle vous permet de :
- Charger les documents rapidement (`WordProcessingLoadOptions`).  
- Parcourir les sections et les formes sans gérer le XML de bas niveau.  
- Récupérer les données d'image, le texte, l'alignement et la rotation en un seul appel.  
- S’intégrer de façon transparente aux services Java existants ou aux micro‑services.

## Prérequis
- **Java Development Kit (JDK)** 8 ou supérieur.  
- **IDE** tel qu'IntelliJ IDEA ou Eclipse.  
- Connaissances de base en I/O Java.  
- Accès à une licence **GroupDocs.Watermark for Java** ou à une version d'essai.

## Configuration de GroupDocs.Watermark pour Java
Intégrez la bibliothèque via Maven ou un téléchargement direct.

### Utilisation de Maven
Ajoutez le dépôt et la dépendance à votre `pom.xml` :

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
Alternativement, téléchargez le JAR le plus récent depuis [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

### Acquisition de licence
Une version d'essai gratuite suffit pour les tests. Pour la production, demandez une licence permanente afin de débloquer toutes les fonctionnalités.

## Guide d'implémentation
Nous diviserons l'implémentation en deux étapes claires : **charger le document Word** et **extraire les informations de forme**.

### Étape 1 : Charger un document Word (load word document java)
Tout d'abord, configurez les options de chargement et créez une instance `Watermarker`. Cela prépare le document pour une inspection plus approfondie.

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

> **Conseil pro :** Gardez l'instance `Watermarker` aussi limitée que possible ; la fermer rapidement libère les ressources natives et évite les fuites de mémoire.

### Étape 2 : Extraire les informations de forme (extract images from shapes)
Nous allons maintenant extraire les détails de chaque forme, y compris les images intégrées. Le code parcourt chaque section et chaque forme, affichant des métadonnées utiles.

```java
import com.groupdocs.watermark.contents.WordProcessingContent;

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

            // If the shape contains an image, output its details
            if (shape.getImage() != null) {
                System.out.println(shape.getImage().getWidth());
                System.out.println(shape.getImage().getHeight());
                System.out.println(shape.getImage().getBytes().length);
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

**Ce que fait ce code :**  
- Récupère le **type** de chaque forme (par ex., image, WordArt).  
- Affiche les valeurs de **taille**, **position** et **rotation**.  
- Montre le **texte alternatif** et le **nom**, utiles pour les vérifications d'accessibilité.  
- Si la forme contient une image, il affiche les **dimensions en pixels** et la **taille en octets** — idéal pour extraire des images des formes.

### Problèmes courants et comment les résoudre
| Problème | Cause | Solution |
|----------|-------|----------|
| `FileNotFoundException` | Chemin de fichier incorrect ou permissions manquantes | Vérifiez le chemin absolu/relatif et assurez‑vous que le fichier est lisible. |
| Null `shape.getImage()` | La forme n'est pas une image (ex. forme automatique) | Protégez avec `if (shape.getImage() != null)` comme indiqué. |
| High memory usage on large docs | Chargement du document complet en une fois | Traitez les sections une à une ou augmentez le tas JVM (`-Xmx`). |
| Missing header/footer shapes | Pas de vérification de `shape.getHeaderFooter()` | L'exemple consigne déjà lorsqu'une forme appartient à un en‑tête/pied de page. |

## Applications pratiques
- **Génération de rapports automatisée** – Extraire les graphiques et diagrammes pour les intégrer dans des PDF en aval.  
- **Audit de conformité** – Vérifier que toutes les formes contiennent un texte alternatif approprié pour l'accessibilité.  
- **Migration de contenu** – Exporter les images intégrées des fichiers Word anciens vers un système de gestion d'actifs numériques.  

## Considérations de performance
- **Release resources** : Toujours appeler `watermarker.close()` dans un bloc `finally` ou utiliser try‑with‑resources si vous encapsulez l'API.  
- **Chunk processing** : Pour les documents dépassant 50 Mo, envisagez de traiter chaque section séparément afin de limiter l'empreinte mémoire.  
- **Thread safety** : Les instances `Watermarker` ne sont pas thread‑safe ; créez une nouvelle instance par thread.

## Conclusion
Vous savez maintenant **comment extraire des formes** des documents Word à l'aide de GroupDocs.Watermark pour Java, depuis le chargement du fichier jusqu'à la lecture de chaque métadonnée de forme et des données d'image intégrées. Cette capacité ouvre la voie à des analyses avancées de documents, des pipelines de contenu automatisés et des validations d'accessibilité.

### Prochaines étapes
- Expérimentez la modification des propriétés des formes (par ex., redimensionnement ou repositionnement).  
- Combinez cette approche avec **GroupDocs.Parser** pour extraire le texte environnant.  
- Intégrez la logique d'extraction dans un service REST pour un traitement à la demande.

## Section FAQ
**Q : Qu’est‑ce que GroupDocs.Watermark for Java ?**  
R : C’est une bibliothèque complète conçue pour gérer les filigranes et le contenu des documents à travers différents formats, permettant des tâches comme l'extraction de formes, la récupération d'images et la manipulation de texte.

**Q : Puis‑je extraire des images des formes sans licence ?**  
R : La version d'essai permet l'extraction, mais une licence complète supprime les limites d'utilisation et autorise le déploiement commercial.

**Q : Cette fonctionnalité fonctionne‑t‑elle avec les fichiers `.doc` (binaires) ?**  
R : Oui, l'API prend en charge les formats `.docx` ainsi que les anciens formats `.doc`.

**Q : Comment gérer les documents protégés par mot de passe ?**  
R : Fournissez le mot de passe via `WordProcessingLoadOptions.setPassword("yourPassword")` avant de créer le `Watermarker`.

**Q : Existe‑t‑il un moyen d'exporter les données de forme extraites au format JSON ?**  
R : Vous pouvez mapper les valeurs affichées à un POJO et utiliser n'importe quelle bibliothèque JSON (par ex., Jackson) pour sérialiser la collection.

---

**Dernière mise à jour :** 2026-02-05  
**Testé avec :** GroupDocs.Watermark 24.11 for Java  
**Auteur :** GroupDocs