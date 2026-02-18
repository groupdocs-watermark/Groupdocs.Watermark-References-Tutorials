---
date: '2026-02-18'
description: Apprenez comment ajouter un filigrane et comment le supprimer dans les
  fichiers de diagramme tels que .vsdx avec GroupDocs.Watermark pour Java. Protégez
  l'intégrité du document avec GroupDocs Watermark Java.
keywords:
- GroupDocs.Watermark Java
- manage watermarks in diagrams
- Java diagram document watermarking
title: Comment ajouter un filigrane aux diagrammes avec GroupDocs.Watermark pour Java
type: docs
url: /fr/java/diagram-document-watermarking/manage-watermarks-groupdocs-java-diagrams/
weight: 1
---

.# Comment ajouter un filigrane aux diagrammes avec GroupDocs.Watermark pour Java

La gestion des filigranes dans les fichiers de diagrammes est essentielle pour protéger la propriété intellectuelle et garder les documents propres pour la distribution publique. Dans ce guide, vous apprendrez **comment ajouter un filigrane** à un diagramme Visio, ainsi que **comment supprimer un filigrane** lorsqu’il n’est plus nécessaire, le tout avec la bibliothèque **groupdocs watermark java**. Que vous construisiez un pipeline de documents de niveau entreprise ou un script utilitaire rapide, ces étapes vous donneront un contrôle complet sur le filigrane des diagrammes.

## Réponses rapides
- **Quelle bibliothèque gère les filigranes de diagrammes en Java ?** GroupDocs.Watermark for Java.  
- **Puis-je ajouter et supprimer des filigranes dans la même exécution ?** Oui – chargez le diagramme une fois et appliquez les opérations d’ajout et de suppression.  
- **Quels formats de fichiers sont pris en charge ?** Formats Visio tels que `.vsdx`, `.vdx`, ainsi que d’autres types de diagrammes.  
- **Ai-je besoin d’une licence ?** Une licence d’essai fonctionne pour le développement ; une licence complète est requise pour la production.  
- **Quelle version de Java est requise ?** JDK 8 ou supérieur.

## Qu’est‑ce que « comment ajouter un filigrane » dans le contexte des diagrammes ?
Ajouter un filigrane signifie intégrer un marqueur visible ou invisible — texte, logo ou image — dans un fichier de diagramme. Ce marqueur voyage avec le fichier, facilitant la preuve de propriété ou le marquage des versions brouillon.

## Pourquoi utiliser GroupDocs.Watermark pour Java ?
* **API riche** – Recherchez, ajoutez et supprimez les filigranes texte et image en quelques lignes de code.  
* **Prise en charge multi‑format** – Fonctionne avec Visio (`.vsdx`, `.vdx`) et de nombreux autres types de diagrammes.  
* **Axé sur les performances** – Charge uniquement les parties d’un diagramme nécessaires aux opérations de filigrane, maintenant une faible utilisation de la mémoire.

## Prérequis
1. **Java Development Kit (JDK) 8+** – Assurez‑vous que `java -version` renvoie 1.8 ou une version plus récente.  
2. **IDE** – IntelliJ IDEA, Eclipse, ou tout éditeur de votre choix.  
3. **GroupDocs.Watermark pour Java** – Ajoutez‑le à votre projet via Maven ou un téléchargement direct du JAR.  

### Bibliothèques et dépendances requises
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

*Si vous préférez ne pas utiliser Maven, vous pouvez télécharger le dernier JAR depuis [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).*

### Acquisition de licence
- **Essai gratuit :** Testez toutes les fonctionnalités sans clé de licence.  
- **Licence temporaire :** Demandez une clé à durée limitée pour l’évaluation.  
- **Licence complète :** Achetez un abonnement pour une utilisation en production sans restriction.

## Configuration de GroupDocs.Watermark pour Java
1. **Ajoutez la bibliothèque** à votre projet (Maven ou JAR manuel).  
2. **Créez une instance `Watermarker`** – cet objet est le point d’entrée pour charger les diagrammes, rechercher, ajouter et supprimer les filigranes.

## Guide d’implémentation

### Chargement d’un document de diagramme
Le chargement est la première étape avant de pouvoir **ajouter un filigrane** ou **supprimer un filigrane**. Le code ci‑dessous montre comment ouvrir un fichier `.vsdx` avec des options de chargement personnalisées.

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.DiagramLoadOptions;

public class LoadDiagramDocument {
    public static void main(String[] args) {
        String inputFilePath = "YOUR_DOCUMENT_DIRECTORY/diagram.vsdx";
        DiagramLoadOptions loadOptions = new DiagramLoadOptions();
        
        Watermarker watermarker = new Watermarker(inputFilePath, loadOptions);
        watermarker.close();
    }
}
```

### Recherche de filigranes texte
Avant d’ajouter un nouveau filigrane, vous pouvez vérifier si un filigrane texte existe déjà. Cet extrait recherche la phrase « Company Name ».

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.contents.DiagramContent;
import com.groupdocs.watermark.search.TextSearchCriteria;
import com.groupdocs.watermark.search.PossibleWatermarkCollection;

public class SearchTextWatermarks {
    public static void main(String[] args) throws Exception {
        String inputFilePath = "YOUR_DOCUMENT_DIRECTORY/diagram.vsdx";
        Watermarker watermarker = new Watermarker(inputFilePath);

        DiagramContent content = watermarker.getContent(DiagramContent.class);
        
        TextSearchCriteria textSearchCriteria = new TextSearchCriteria("Company Name");
        PossibleWatermarkCollection possibleWatermarks = content.getPages().get_Item(0).search(textSearchCriteria);

        watermarker.close();
    }
}
```

### Recherche de filigranes image
Si vous devez localiser un logo ou toute image utilisée comme filigrane, utilisez le `ImageDctHashSearchCriteria`. Cela est pratique lorsque vous souhaitez **supprimer un filigrane** correspondant à un logo connu.

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.contents.DiagramContent;
import com.groupdocs.watermark.search.ImageDctHashSearchCriteria;
import com.groupdocs.watermark.search.PossibleWatermarkCollection;

public class SearchImageWatermarks {
    public static void main(String[] args) throws Exception {
        String inputFilePath = "YOUR_DOCUMENT_DIRECTORY/diagram.vsdx";
        String imagePath = "YOUR_DOCUMENT_DIRECTORY/logo.png";
        
        Watermarker watermarker = new Watermarker(inputFilePath);
        DiagramContent content = watermarker.getContent(DiagramContent.class);

        ImageDctHashSearchCriteria imageSearchCriteria = new ImageDctHashSearchCriteria(imagePath);
        PossibleWatermarkCollection possibleWatermarks = content.getPages().get_Item(0).search(imageSearchCriteria);

        watermarker.close();
    }
}
```

### Suppression des filigranes
Une fois que vous avez identifié les filigranes — texte, image ou les deux — vous pouvez les supprimer du diagramme. L’exemple ci‑dessous montre une opération de suppression combinée.

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.contents.DiagramContent;
import com.groupdocs.watermark.search.TextSearchCriteria;
import com.groupdocs.watermark.search.ImageDctHashSearchCriteria;
import com.groupdocs.watermark.search.PossibleWatermarkCollection;

public class RemoveWatermarks {
    public static void main(String[] args) throws Exception {
        String inputFilePath = "YOUR_DOCUMENT_DIRECTORY/diagram.vsdx";
        String outputFilePath = "YOUR_OUTPUT_DIRECTORY/updated_diagram.vsdx";

        Watermarker watermarker = new Watermarker(inputFilePath);
        DiagramContent content = watermarker.getContent(DiagramContent.class);

        TextSearchCriteria textSearchCriteria = new TextSearchCriteria("Company Name");
        ImageDctHashSearchCriteria imageSearchCriteria = new ImageDctHashSearchCriteria("YOUR_DOCUMENT_DIRECTORY/logo.png");

        PossibleWatermarkCollection possibleWatermarks = content.getPages().get_Item(0).search(textSearchCriteria.or(imageSearchCriteria));
        possibleWatermarks.clear();

        watermarker.save(outputFilePath);
        watermarker.close();
    }
}
```

## Applications pratiques
1. **Intégration de logiciels d’entreprise** – Intégrez la gestion des filigranes dans votre ERP ou plateforme de génération de documents pour appliquer la marque.  
2. **Systèmes de gestion de contenu (CMS)** – Scannez automatiquement les diagrammes téléchargés à la recherche de logos non autorisés et supprimez‑les.  
3. **Gestion de documents juridiques** – Ajoutez un filigrane texte « Confidential » pendant les phases de brouillon et supprimez‑le **avant le dépôt final**.

## Problèmes courants et solutions
| Symptôme | Cause probable | Solution |
|----------|----------------|----------|
| Aucun filigrane trouvé | Le texte/l’image recherché ne correspond pas exactement | Utilisez `or()` pour combiner les critères ou ajustez les paramètres de sensibilité à la casse. |
| `OutOfMemoryError` sur de gros fichiers | Diagramme chargé entièrement en mémoire | Utilisez `DiagramLoadOptions.setLoadPages()` pour ne charger que les pages nécessaires. |
| Le fichier enregistré est corrompu | `watermarker.save()` appelé avant d’avoir effacé tous les filigranes | Assurez‑vous que `possibleWatermarks.clear()` est terminé et que `watermarker.close()` est invoqué après l’enregistrement. |

## Questions fréquentes

**Q : Puis‑je rechercher à la fois du texte et des images simultanément ?**  
R : Oui. Combinez `TextSearchCriteria` et `ImageDctHashSearchCriteria` avec la méthode `or()`, comme montré dans l’exemple de suppression.

**Q : Est‑il possible de supprimer les filigranes sans endommager le diagramme ?**  
R : Absolument. La bibliothèque isole les objets filigrane, ainsi appeler `clear()` supprime uniquement les calques de filigrane tout en préservant le contenu original du diagramme.

**Q : GroupDocs.Watermark prend‑il en charge plusieurs formats de diagrammes ?**  
R : Oui. Les formats tels que `.vsdx`, `.vdx` et autres fichiers compatibles Visio sont entièrement pris en charge.

**Q : Comment gérer efficacement de gros volumes de documents ?**  
R : Mettez en œuvre des boucles de traitement par lots, réutilisez une seule instance `Watermarker` lorsque c’est possible, et limitez le chargement des pages avec `DiagramLoadOptions`.

**Q : Existe‑t‑il un moyen d’automatiser la détection des filigranes dans un pipeline CI/CD ?**  
R : Vous pouvez intégrer les extraits Java fournis dans vos scripts de construction (par ex., Maven ou Gradle) pour valider qu’aucun filigrane non autorisé n’est présent avant de publier les artefacts.

**Dernière mise à jour :** 2026-02-18  
**Testé avec :** GroupDocs.Watermark 24.11 pour Java  
**Auteur :** GroupDocs