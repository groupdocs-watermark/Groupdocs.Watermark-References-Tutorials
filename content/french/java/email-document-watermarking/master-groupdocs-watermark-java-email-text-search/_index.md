---
date: '2025-12-31'
description: Apprenez à rechercher du texte d’e‑mail avec GroupDocs.Watermark pour
  Java, gérez efficacement les corps, les sujets et les pièces jointes.
keywords:
- GroupDocs Watermark Java
- search text in email body
- manage email watermarks
title: Comment rechercher du texte d'e-mail avec GroupDocs.Watermark Java – Guide
  complet
type: docs
url: /fr/java/email-document-watermarking/master-groupdocs-watermark-java-email-text-search/
weight: 1
---

# Comment rechercher du texte d'e-mail avec GroupDocs.Watermark Java

Trouver une phrase précise dans l’objet, le corps ou les pièces jointes d’un e‑mail peut être un vrai casse‑tête—surtout lorsqu’on gère des dizaines ou des centaines de messages. Dans ce tutoriel, vous découvrirez **comment rechercher du texte d’e‑mail** rapidement et avec précision en utilisant **GroupDocs.Watermark pour Java**. Nous passerons en revue l’installation, le code et les meilleures pratiques afin que vous puissiez intégrer la recherche de texte d’e‑mail dans vos propres applications en toute confiance.

## Réponses rapides
- **Quelle bibliothèque permet de rechercher du texte d’e‑mail en Java ?** GroupDocs.Watermark pour Java.  
- **Ai‑je besoin d’une licence ?** Une version d’essai gratuite suffit pour les tests ; une licence payante est requise en production.  
- **Puis‑je rechercher à la fois l’objet et le corps ?** Oui—configurez `EmailSearchableObjects` pour inclure Subject, HtmlBody et PlainTextBody.  
- **L’API est‑elle sensible à la casse ?** Vous pouvez choisir des recherches insensibles à la casse en définissant le drapeau approprié dans `TextSearchCriteria`.  
- **Quelle version de Java est requise ?** JDK 8 ou supérieur ; Maven est recommandé pour la gestion des dépendances.

## Qu’est‑ce que le “comment rechercher un e‑mail” avec GroupDocs.Watermark ?
GroupDocs.Watermark fournit une API unifiée pour localiser, supprimer ou modifier les filigranes et le texte brut à travers de nombreux types de documents—y compris les **messages e‑mail** (`.msg`, `.eml`). En exploitant son modèle d’objets recherchables, vous pouvez cibler exactement les parties d’un e‑mail qui vous intéressent, rendant le traitement en masse rapide et fiable.

## Pourquoi utiliser GroupDocs.Watermark Java pour la recherche d’e‑mail ?
- **API unifiée** – Fonctionne avec les PDF, images, fichiers Office et e‑mails en utilisant les mêmes modèles de code.  
- **Performance optimisée** – Les opérations de recherche s’exécutent en mémoire sans nécessiter de services externes.  
- **Gestion robuste** – Prend en charge les corps HTML et texte brut, les pièces jointes, et même les e‑mails protégés par mot de passe.  
- **Intégration facile** – Prêt pour Maven/Gradle, avec une documentation claire et un support actif.

## Prérequis

- **Java Development Kit (JDK)** 8 ou plus récent.  
- **Maven** (ou Gradle) pour la gestion des dépendances.  
- Un IDE tel que **IntelliJ IDEA** ou **Eclipse**.  
- Une connaissance de base de la syntaxe Java et des formats de fichiers e‑mail (`.msg`, `.eml`).

## Installation de GroupDocs.Watermark pour Java

### Configuration Maven
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
Vous pouvez également télécharger le JAR le plus récent depuis [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

### Acquisition de licence
- **Essai gratuit :** Testez les fonctionnalités principales sans clé de licence.  
- **Licence temporaire :** Demandez une clé à durée limitée pour une évaluation prolongée.  
- **Licence payante :** Achetez-la pour un usage illimité en production.

#### Initialisation de base
```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.EmailLoadOptions;

EmailLoadOptions loadOptions = new EmailLoadOptions();
Watermarker watermarker = new Watermarker("input_email.msg", loadOptions);
```

## Guide d’implémentation

### Fonctionnalité 1 : Recherche de texte dans le corps de l’e‑mail

#### Vue d’ensemble
Nous allons configurer l’API pour analyser l’**objet**, le **corps HTML** et le **corps texte brut** d’un e‑mail à la recherche d’un mot‑clé donné.

#### Étape 1 : Définir les chemins des documents
```java
String inputDocumentPath = "YOUR_DOCUMENT_DIRECTORY/message.msg";
String outputDocumentPath = "YOUR_OUTPUT_DIRECTORY/output_message.msg";
```

#### Étape 2 : Configurer les options de chargement et le Watermarker
```java
EmailLoadOptions loadOptions = new EmailLoadOptions();
Watermarker watermarker = new Watermarker(inputDocumentPath, loadOptions);
```

#### Étape 3 : Créer les critères de recherche
```java
import com.groupdocs.watermark.search.SearchCriteria;
import com.groupdocs.watermark.search.TextSearchCriteria;

SearchCriteria criteria = new TextSearchCriteria("test", false);
```

#### Étape 4 : Spécifier les emplacements de recherche
```java
watermarker.getSearchableObjects().setEmailSearchableObjects(
    EmailSearchableObjects.Subject |
    EmailSearchableObjects.HtmlBody | 
    EmailSearchableObjects.PlainTextBody);
```

#### Étape 5 : Exécuter la recherche et supprimer les filigranes
```java
import com.groupdocs.watermark.search.PossibleWatermarkCollection;

PossibleWatermarkCollection watermarks = watermarker.search(criteria);
watermarks.clear();
```

#### Étape 6 : Enregistrer les modifications
```java
watermarker.save(outputDocumentPath);
// Close the Watermarker instance to release resources
watermarker.close();
```

#### Conseils de dépannage
- **Résultats vides :** Vérifiez que le mot‑clé apparaît réellement dans les parties d’e‑mail sélectionnées.  
- **Performance :** Limitez les objets recherchables aux seuls dont vous avez besoin (par ex. Subject + PlainTextBody) pour accélérer le traitement de gros lots.

### Fonctionnalité 2 : Options de chargement du document e‑mail

#### Vue d’ensemble
`EmailLoadOptions` vous permet de contrôler la façon dont l’e‑mail est analysé—utile pour les messages chiffrés ou les encodages personnalisés.

#### Étape 1 : Configurer les options de chargement
```java
EmailLoadOptions loadOptions = new EmailLoadOptions();
// Additional configurations can be added here.
```

#### Options de configuration clés
- **Protection par mot de passe :** Définissez `loadOptions.setPassword("yourPassword")` pour les fichiers `.msg` chiffrés.  
- **Paramètres d’encodage :** Ajustez `loadOptions.setEncoding(Charset.forName("UTF-8"))` lorsque vous traitez des jeux de caractères non standard.

## Applications pratiques

- **Traitement automatisé des e‑mails :** Analysez en masse les tickets de support entrants à la recherche de mots‑clés comme « remboursement » ou « erreur ».  
- **Vérifications de conformité légale :** Localisez rapidement des termes confidentiels (ex. : SSN, numéros de carte de crédit) dans les archives de messagerie d’entreprise.  
- **Automatisation du support client :** Dirigez les e‑mails en fonction des phrases détectées vers l’équipe de support appropriée.

## Considérations de performance
- **Gestion des ressources :** Appelez `watermarker.close()` dès que vous avez terminé le traitement afin de libérer les ressources natives.  
- **Bonnes pratiques mémoire :** Lors du traitement de milliers de messages, traitez-les par lots et réutilisez l’instance `Watermarker` autant que possible.

## Conclusion
Vous disposez maintenant d’une approche solide, prête pour la production, pour **comment rechercher du texte d’e‑mail** à l’aide de GroupDocs.Watermark Java. La flexibilité de l’API vous permet de cibler des parties spécifiques d’un e‑mail, de supprimer les filigranes indésirables et d’intégrer cette logique dans des flux de travail plus larges.

### Prochaines étapes
- Expérimentez avec **plusieurs critères de recherche** (par ex. combinez « facture » + « en retard »).  
- Explorez **l’ajout de filigranes** pour marquer les e‑mails contenant des données sensibles.  
- Plongez dans d’autres types de documents (PDF, DOCX) en utilisant le même workflow Watermarker.

## Foire aux questions

**Q1 :** Comment gérer les e‑mails chiffrés avec GroupDocs.Watermark ?  
**R1 :** Utilisez `EmailLoadOptions.setPassword("yourPassword")` avant de créer l’instance `Watermarker`.

**Q2 :** Puis‑je rechercher plusieurs mots‑clés simultanément ?  
**R2 :** Oui—créez des objets `SearchCriteria` séparés pour chaque mot‑clé et combinez‑les avec des opérateurs logiques (ex. `OrSearchCriteria`).

**Q3 :** GroupDocs.Watermark Java est‑il gratuit ?  
**R3 :** Une version d’essai gratuite est disponible pour l’évaluation. Pour un usage en production, une licence payante est requise.

**Q4 :** Comment gérer efficacement de gros volumes d’e‑mails ?  
**R4 :** Limitez les objets recherchables aux seuls nécessaires, traitez les e‑mails par lots et fermez toujours le `Watermarker` pour libérer les ressources.

**Q5 :** Où puis‑je trouver de l’aide ou du support supplémentaire ?  
**R5 :** Consultez le [forum GroupDocs](https://forum.groupdocs.com/c/watermark/10) pour l’assistance communautaire ou contactez directement le support GroupDocs.

## Ressources
- **Documentation :** Explorez les guides détaillés sur [GroupDocs Documentation](https://docs.groupdocs.com/watermark/java/).  
- **Référence API :** Accédez aux détails techniques sur [GroupDocs API](https://apireference.groupdocs.com/watermark/java/).

---

**Dernière mise à jour :** 2025-12-31  
**Testé avec :** GroupDocs.Watermark 24.11 pour Java  
**Auteur :** GroupDocs  

---