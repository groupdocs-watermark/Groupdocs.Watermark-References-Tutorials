---
date: '2026-04-07'
description: Apprenez à rechercher le corps d’un e‑mail en Java avec GroupDocs.Watermark,
  y compris comment rechercher plusieurs mots‑clés dans l’e‑mail et comment supprimer
  les filigranes d’e‑mail.
keywords:
- search email body java
- search multiple keywords email
- how to remove email watermarks
title: 'Recherche du corps d’e-mail Java avec GroupDocs.Watermark : Guide complet'
type: docs
url: /fr/java/email-document-watermarking/master-groupdocs-watermark-java-email-text-search/
weight: 1
---

# Recherche du corps d'e-mail Java avec GroupDocs.Watermark

Si vous devez **search email body java** rapidement et de manière fiable, vous êtes au bon endroit. Dans ce tutoriel, nous expliquerons comment GroupDocs.Watermark pour Java vous permet de localiser du texte spécifique dans les objets des e‑mails, les corps HTML et les corps en texte brut, et comment vous pouvez nettoyer les filigranes indésirables par la suite. À la fin, vous serez capable de mettre en œuvre une solution robuste qui fonctionne avec un ou plusieurs mots‑clés et même supprime les filigranes d'e‑mail si nécessaire.

## Réponses rapides
- **Que signifie “search email body java” ?** Cela fait référence à l’utilisation du code Java (avec GroupDocs.Watermark) pour trouver du texte dans le contenu d’un e‑mail.  
- **Puis‑je rechercher plusieurs mots‑clés d’e‑mail en même temps ?** Oui – créez des objets `SearchCriteria` séparés et combinez‑les.  
- **Comment supprimer les filigranes d’e‑mail ?** Utilisez la méthode `PossibleWatermarkCollection.clear()` après une recherche.  
- **Ai‑je besoin d’une licence ?** Un essai gratuit suffit pour les tests ; une licence permanente est requise pour la production.  
- **Quel IDE fonctionne le mieux ?** IntelliJ IDEA ou Eclipse sont tous deux entièrement pris en charge.

## Ce que vous apprendrez
- Installation et configuration de GroupDocs.Watermark pour Java.  
- Configuration des critères de recherche pour **search email body java** dans les objets et les corps.  
- Techniques pour **search multiple keywords email** en une seule exécution.  
- Les étapes exactes **how to remove email watermarks** après les avoir localisés.  

## Pourquoi rechercher le corps d’e‑mail Java avec GroupDocs.Watermark ?
GroupDocs.Watermark fournit une API de haut niveau qui abstrait les complexités de l’analyse des fichiers .msg, de la gestion des différents formats de corps et de la gestion des filigranes. Cela vous fait gagner du temps par rapport à la création d’un analyseur personnalisé et garantit des résultats cohérents sur de grands lots d’e‑mails.

## Prérequis
- Java Development Kit (JDK) 8 ou supérieur.  
- Maven (ou la possibilité d’ajouter des JARs manuellement).  
- Familiarité de base avec Java et les formats de fichiers e‑mail (.msg, .eml).  

## Configuration de GroupDocs.Watermark pour Java
GroupDocs.Watermark pour Java simplifie l’ajout de filigranes et la recherche de texte dans les documents, y compris les e‑mails. Voici les deux méthodes les plus courantes pour ajouter la bibliothèque à votre projet.

### Configuration Maven
Incluez ce qui suit dans votre fichier `pom.xml` pour ajouter GroupDocs.Watermark en tant que dépendance:
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
Alternativement, vous pouvez télécharger la dernière version directement depuis [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

### Étapes d’obtention de licence
- **Essai gratuit :** Commencez par un essai gratuit pour tester les fonctionnalités de base.  
- **Licence temporaire :** Obtenez une licence temporaire pour un accès étendu et des tests.  
- **Achat :** Envisagez d’acheter si GroupDocs.Watermark répond à vos besoins.

#### Initialisation de base
Initialisez la classe `Watermarker` comme indiqué ci‑dessous :
```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.EmailLoadOptions;

EmailLoadOptions loadOptions = new EmailLoadOptions();
Watermarker watermarker = new Watermarker("input_email.msg", loadOptions);
```

## Guide de mise en œuvre

### Fonctionnalité 1 : Recherche de texte dans le corps d’e‑mail
Cette fonctionnalité permet de rechercher du texte spécifique dans l’objet et le corps d’un e‑mail.

#### Vue d’ensemble
Nous montrerons comment configurer GroupDocs.Watermark pour rechercher dans différentes parties d’un message e‑mail à l’aide de code Java.

##### Étape 1 : Définir les chemins des documents
Configurez vos chemins d’entrée et de sortie pour le traitement des e‑mails :
```java
String inputDocumentPath = "YOUR_DOCUMENT_DIRECTORY/message.msg";
String outputDocumentPath = "YOUR_OUTPUT_DIRECTORY/output_message.msg";
```

##### Étape 2 : Configurer les options de chargement et le Watermarker
Initialisez `EmailLoadOptions` et `Watermarker` pour travailler avec votre document e‑mail.
```java
EmailLoadOptions loadOptions = new EmailLoadOptions();
Watermarker watermarker = new Watermarker(inputDocumentPath, loadOptions);
```

##### Étape 3 : Créer les critères de recherche
Définissez les critères de recherche de texte. Nous utiliserons une recherche insensible à la casse pour le mot‑clé **"test"** :
```java
import com.groupdocs.watermark.search.SearchCriteria;
import com.groupdocs.watermark.search.TextSearchCriteria;

SearchCriteria criteria = new TextSearchCriteria("test", false);
```

##### Étape 4 : Spécifier les emplacements de recherche
Configurez la recherche pour couvrir à la fois l’objet et le corps des e‑mails :
```java
watermarker.getSearchableObjects().setEmailSearchableObjects(
    EmailSearchableObjects.Subject |
    EmailSearchableObjects.HtmlBody | 
    EmailSearchableObjects.PlainTextBody);
```

##### Étape 5 : Exécuter la recherche et nettoyer les filigranes
Effectuez la recherche et supprimez les filigranes trouvés :
```java
import com.groupdocs.watermark.search.PossibleWatermarkCollection;

PossibleWatermarkCollection watermarks = watermarker.search(criteria);
watermarks.clear();
```

##### Étape 6 : Enregistrer les modifications
Après le traitement, enregistrez vos modifications dans un nouveau document :
```java
watermarker.save(outputDocumentPath);
// Close the Watermarker instance to release resources
watermarker.close();
```

#### Conseils de dépannage
- **Problème courant :** Si les résultats de recherche sont vides, assurez‑vous que le texte est présent dans le corps ou l’objet de l’e‑mail.  
- **Conseil de performance :** Optimisez en limitant les recherches aux seules sections dont vous avez réellement besoin.

### Fonctionnalité 2 : Options de chargement du document e‑mail
Cette section explique comment configurer des options supplémentaires lors du chargement d’un document e‑mail pour le traitement avec GroupDocs.Watermark.

#### Vue d’ensemble
Configurer les options de chargement permet un meilleur contrôle sur la façon dont les documents sont gérés, comme la spécification de la protection par mot de passe ou des paramètres d’encodage.

##### Étape 1 : Configurer les options de chargement
Voici une configuration de base pour `EmailLoadOptions` :
```java
EmailLoadOptions loadOptions = new EmailLoadOptions();
// Additional configurations can be added here.
```

#### Options de configuration clés
- **Protection par mot de passe :** Spécifiez les mots de passe si vos e‑mails sont chiffrés.  
- **Paramètres d’encodage :** Définissez les types d’encodage spécifiques selon les besoins.

## Comment rechercher plusieurs mots‑clés d’e‑mail
Si vous devez localiser plusieurs termes en une seule passe, créez plusieurs objets `SearchCriteria` et combinez‑les à l’aide des opérateurs logiques **OR** ou **AND**. L’API vous permet d’enchaîner les critères, ainsi vous pouvez rechercher « invoice » **ou** « receipt » sans exécuter de boucles séparées.

## Comment supprimer les filigranes d’e‑mail
Après avoir localisé les filigranes (ou tout texte correspondant à vos critères), la méthode `PossibleWatermarkCollection.clear()` les supprime du document e‑mail. C’est l’étape exacte que nous avons utilisée dans **Step 5** ci‑dessus, et elle fonctionne pour n’importe quel nombre de correspondances.

## Applications pratiques

### Cas d’utilisation 1 : Traitement automatisé des e‑mails
Automatisez le filtrage et le traitement de gros volumes d’e‑mails pour trouver efficacement du contenu spécifique.

### Cas d’utilisation 2 : Vérifications de conformité légale
Assurez la conformité en recherchant des informations sensibles dans les e‑mails d’entreprise.

### Cas d’utilisation 3 : Automatisation du support client
Rationalisez les flux de travail du support en localisant rapidement des mots‑clés ou des phrases dans les demandes des clients.

## Considérations de performance
Lors de l’utilisation de GroupDocs.Watermark, prenez en compte les éléments suivants pour optimiser les performances :
- **Gestion des ressources :** Gérez efficacement la mémoire et la puissance de traitement pour manipuler de grands ensembles de données d’e‑mail.  
- **Meilleures pratiques de gestion de la mémoire Java :** Surveillez régulièrement l’utilisation des ressources et libérez les ressources rapidement.

## Questions fréquemment posées

**Q :** Comment gérer les e‑mails chiffrés avec GroupDocs.Watermark ?  
**R :** Utilisez `EmailLoadOptions` pour spécifier les mots de passe lors de l’initialisation du `Watermarker`.

**Q :** Puis‑je rechercher plusieurs mots‑clés en même temps ?  
**R :** Oui, créez des instances `SearchCriteria` séparées et combinez‑les à l’aide d’opérations logiques.

**Q :** GroupDocs.Watermark Java est‑il gratuit à utiliser ?  
**R :** Un essai gratuit est disponible ; envisagez d’acheter une licence pour des fonctionnalités étendues.

**Q :** Comment gérer efficacement de gros volumes d’e‑mails ?  
**R :** Optimisez vos recherches en ciblant des sections spécifiques des e‑mails et en gérant les ressources efficacement.

**Q :** Où puis‑je trouver de l’aide ou du support supplémentaire ?  
**R :** Visitez le [forum GroupDocs](https://forum.groupdocs.com/c/watermark/10) pour le support communautaire ou contactez leur canal de support gratuit.

## Ressources
- **Documentation :** Explorez les guides détaillés sur [GroupDocs Documentation](https://docs.groupdocs.com/watermark/java/).  
- **Référence API :** Accédez aux détails techniques sur [GroupDocs API](https://apireference.groupdocs.com/watermark/java/).

---

**Dernière mise à jour :** 2026-04-07  
**Testé avec :** GroupDocs.Watermark 24.11 for Java  
**Auteur :** GroupDocs