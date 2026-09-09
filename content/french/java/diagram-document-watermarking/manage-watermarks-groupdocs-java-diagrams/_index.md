---
date: '2025-12-19'
description: Apprenez à utiliser GroupDocs Watermark Maven pour gérer les filigranes
  dans les fichiers de diagramme tels que .vsdx avec Java, améliorant l'intégrité
  des documents et protégeant la propriété intellectuelle.
keywords:
- GroupDocs.Watermark Java
- manage watermarks in diagrams
- Java diagram document watermarking
- groupdocs watermark maven
title: groupdocs watermark maven – Gérer les filigranes de diagrammes avec Java
type: docs
url: /fr/java/diagram-document-watermarking/manage-watermarks-groupdocs-java-diagrams/
weight: 1
---

# groupdocs watermark maven – Gérer les filigranes de diagrammes avec Java

La gestion des filigranes dans les documents est essentielle pour protéger la propriété intellectuelle et maintenir l'intégrité des documents. **Dans ce tutoriel, nous vous montrerons comment utiliser groupdocs watermark maven pour charger, rechercher et supprimer efficacement les filigranes des fichiers de diagrammes tels que `.vsdx`**. Que vous développiez des logiciels d'entreprise ou automatisiez des flux de travail de documents, maîtriser ces techniques vous donnera un contrôle complet sur la gestion des filigranes de diagrammes.

## Réponses rapides
- **Quelle bibliothèque est nécessaire ?** GroupDocs.Watermark for Java (disponible via Maven).  
- **Quels formats de diagrammes sont pris en charge ?** `.vsdx`, `.vdx` et autres formats Visio.  
- **Puis-je rechercher à la fois des filigranes texte et image ?** Oui – combinez les critères de recherche avec `or()`.  
- **Une licence est‑elle requise pour la production ?** Une licence valide GroupDocs.Watermark est requise.  
- **Comment l’intégrer à Maven ?** Ajoutez le dépôt et la dépendance indiqués ci‑dessous.

## Qu’est‑ce que groupdocs watermark maven ?
`groupdocs watermark maven` désigne l’intégration basée sur Maven de la bibliothèque GroupDocs.Watermark pour Java. En déclarant la bibliothèque dans votre `pom.xml`, Maven résout automatiquement tous les binaires requis, vous permettant de vous concentrer sur le code qui charge les diagrammes, recherche les filigranes et les supprime de manière programmatique.

## Pourquoi utiliser GroupDocs.Watermark pour la gestion des filigranes de diagrammes ?
- **API complète** – prend en charge les filigranes texte, image et forme sur de nombreux types de diagrammes.  
- **Suppression précise** – élimine les filigranes sans corrompre la mise en page originale du diagramme.  
- **Évolutif** – adapté au traitement par lots de grandes collections de diagrammes.  
- **Compatible Maven** – gestion simple des dépendances, gardant votre projet propre.

## Prérequis
1. **Java Development Kit (JDK) 8+** – assure la compatibilité avec la bibliothèque.  
2. **IDE** – IntelliJ IDEA, Eclipse ou tout éditeur compatible Java.  
3. **GroupDocs.Watermark for Java** – ajouté via Maven (recommandé) ou téléchargement direct du JAR.  

### Bibliothèques et dépendances requises
#### Configuration Maven
Ajoutez la configuration suivante à votre fichier `pom.xml` :

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
Sinon, téléchargez la dernière version depuis [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

### Acquisition de licence
- **Essai gratuit :** Testez la bibliothèque avec une licence d'essai.  
- **Licence temporaire :** Demandez une clé à court terme pour l'évaluation.  
- **Achat :** Obtenez une licence de production pour une utilisation illimitée.

## Utiliser groupdocs watermark maven pour charger un document de diagramme
Charger un document de diagramme est la première étape avant toute opération de filigrane. Voici un exemple minimal qui crée une instance `Watermarker` avec `DiagramLoadOptions`.

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

- **Paramètres :**  
  - `inputFilePath` – chemin vers votre fichier `.vsdx`.  
  - `loadOptions` – vous permet de contrôler la façon dont le diagramme est analysé (par ex., protection par mot de passe).

## Recherche de filigranes avec groupdocs watermark maven
### Filigranes texte
Pour localiser les filigranes basés sur du texte, définissez un `TextSearchCriteria` et interrogez la première page du diagramme.

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

- **Méthodes clés :**  
  - `TextSearchCriteria` – spécifie le texte exact à rechercher.  
  - `PossibleWatermarkCollection` – stocke les correspondances trouvées.

### Filigranes image
Si votre diagramme contient des filigranes logo ou image, utilisez `ImageDctHashSearchCriteria` pour comparer avec une image de référence.

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

- **Méthodes clés :**  
  - `ImageDctHashSearchCriteria` – crée un hachage perceptuel de l'image de référence pour une correspondance robuste.

## Suppression des filigranes
Une fois que vous avez identifié les filigranes indésirables, vous pouvez les effacer et enregistrer une copie propre du diagramme.

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

- **Méthode clé :** `clear()` supprime chaque filigrane trouvé par les critères combinés, laissant le diagramme intact.

## Applications pratiques
1. **Intégration de logiciels d’entreprise** – Intégrez la gestion des filigranes dans les applications métier pour protéger les diagrammes propriétaires.  
2. **Systèmes de gestion de contenu (CMS)** – Automatisez la détection et la suppression des logos non autorisés avant la publication.  
3. **Flux de travail de documents juridiques** – Ajoutez ou retirez des filigranes à différentes étapes du traitement des contrats.  

## Problèmes courants & dépannage
- **Erreurs de licence :** Assurez‑vous que le fichier de licence est correctement référencé avant de créer un `Watermarker`.  
- **Fichiers volumineux :** Utilisez les API de streaming ou augmentez la taille du tas JVM (`-Xmx2g`) pour les diagrammes > 100 Mo.  
- **Filigranes manquants :** Vérifiez que les critères de recherche (casse du texte, seuil de similarité d’image) correspondent au contenu réel du filigrane.

## Questions fréquemment posées
**Q : Puis‑je rechercher à la fois du texte et des images simultanément ?**  
R : Oui. Combinez les critères avec `or()` comme indiqué dans l’exemple de suppression.

**Q : Est‑il sûr de supprimer les filigranes sans altérer la mise en page du diagramme ?**  
R : Absolument. L’API cible précisément les objets filigrane, préservant tous les autres éléments du diagramme.

**Q : Quels formats de diagrammes GroupDocs.Watermark prend‑il en charge ?**  
R : Il prend en charge les formats Visio comme `.vsdx`, `.vdx`, ainsi que d’autres types de diagrammes vectoriels.

**Q : Comment puis‑je traiter efficacement des centaines de diagrammes ?**  
R : Implémentez une boucle batch, réutilisez une seule instance `Watermarker` lorsque c’est possible, et envisagez le traitement parallèle avec le `ExecutorService` de Java.

**Q : Puis‑je intégrer la détection de filigranes dans un pipeline CI/CD ?**  
R : Oui. Incluez les extraits Java dans vos scripts de build (par ex., plugins Maven ou tâches Gradle) pour valider les diagrammes avant le déploiement.

## Conclusion
En exploitant **groupdocs watermark maven**, vous obtenez une solution puissante, gérée par Maven, pour charger, rechercher et supprimer les filigranes des fichiers de diagrammes avec Java. Cette capacité renforce la sécurité des documents, rationalise les flux de contenu et s’adapte facilement aux grandes collections de documents.

---

**Dernière mise à jour :** 2025-12-19  
**Testé avec :** GroupDocs.Watermark 24.11 for Java  
**Auteur :** GroupDocs