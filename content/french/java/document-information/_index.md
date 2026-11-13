---
date: 2026-11-13
description: Apprenez comment extraire les metadata, list supported formats, et retrieve
  document information en utilisant GroupDocs.Watermark for Java.
keywords:
- how to extract metadata
- list supported formats
- extract document metadata
- retrieve document info
- extract slide background
lastmod: 2026-11-13
og_description: Comment extraire les metadata avec GroupDocs.Watermark for Java. Apprenez
  à list supported formats, retrieve document info, et extract slide backgrounds en
  quelques minutes.
og_image_alt: Guide showing metadata extraction and format listing with GroupDocs.Watermark
  for Java
og_title: Comment extraire les metadata avec GroupDocs.Watermark for Java
schemas:
- author: GroupDocs
  dateModified: '2026-11-13'
  description: Learn how to extract metadata, list supported formats, and retrieve
    document information using GroupDocs.Watermark for Java.
  headline: How to extract metadata with GroupDocs.Watermark for Java
  type: TechArticle
- questions:
  - answer: Yes, provide the password when opening the document; the API will decrypt
      it in memory and then read the metadata.
    question: Can I extract metadata from password‑protected documents?
  - answer: The core extraction features are compatible with Android API 21+ when
      bundled as a standard JAR.
    question: Does the library work on Android?
  - answer: Use the `getCustomProperties()` method on the `DocumentInfo` object; it
      returns a map of key‑value pairs you can iterate over.
    question: How do I handle custom metadata fields?
  - answer: Wrap the extraction logic in a loop and reuse a single `Watermark` instance;
      the SDK is designed for high‑throughput scenarios.
    question: Is there a way to batch‑process many files?
  - answer: GroupDocs.Watermark offers perpetual, subscription, and temporary licenses;
      the temporary license is ideal for evaluation and CI pipelines.
    question: What licensing options are available?
  type: FAQPage
tags:
- metadata extraction
- GroupDocs.Watermark
- Java document processing
- supported formats
title: Comment extraire les metadata avec GroupDocs.Watermark for Java
type: docs
url: /fr/java/document-information/
weight: 14
---

# Comment extraire les métadonnées avec GroupDocs.Watermark pour Java

Dans ce guide, vous découvrirez **comment extraire les métadonnées** d’un large éventail de types de documents en utilisant GroupDocs.Watermark pour Java. Que vous ayez besoin de lire le type de fichier, le nombre de pages, les détails de l’auteur ou des propriétés personnalisées, la bibliothèque vous donne un accès programmatique à ces informations afin que vous puissiez prendre des décisions intelligentes concernant le placement des filigranes, le routage des documents ou les contrôles de conformité. Le tutoriel montre également comment lister les formats pris en charge, extraire les données d’arrière‑plan des diapositives et récupérer d’autres caractéristiques utiles du document.

## Réponses rapides
- **Puis-je extraire des métadonnées des fichiers PDF et Word ?** Oui, l'API lit les métadonnées de plus de 70 formats courants.  
- **Ai-je besoin d'une licence pour le développement ?** Une licence temporaire gratuite fonctionne pour les tests ; une licence complète est requise pour la production.  
- **Quelle version de Java est requise ?** Java 8 ou supérieur est supporté.  
- **La bibliothèque est‑elle thread‑safe ?** Les classes d'extraction principales sont conçues pour une utilisation concurrente.  
- **Combien de formats sont reconnus ?** Plus de 70 formats d'entrée et de sortie sont reconnus dès l'installation.

## Qu'est-ce que l'extraction de métadonnées ?
L'extraction de métadonnées est le processus de lecture d'informations intégrées — telles que l'auteur, la date de création, le nombre de pages et les propriétés personnalisées — à partir d'un fichier document sans en modifier le contenu. Elle permet des flux de travail automatisés qui dépendent des attributs du document. Elle inclut généralement des propriétés comme le titre, les mots‑clés et les horodatages de modification, qui peuvent être exploités pour l'indexation et les rapports de conformité.

## Pourquoi utiliser GroupDocs.Watermark pour Java ?
GroupDocs.Watermark pour Java prend en charge **plus de 70 formats de fichiers**, y compris PDF, DOCX, PPTX, XLSX et les types d'images, et peut traiter des documents jusqu’à 500 Mo sans charger le fichier complet en mémoire. Son API renvoie les métadonnées dans un objet unique et cohérent, réduisant le besoin de parseurs spécifiques à chaque format et diminuant le temps de développement jusqu’à 40 %.

## Prérequis
- Java 8 ou version plus récente installé sur votre machine de développement.  
- Maven ou Gradle pour gérer la dépendance `groupdocs-watermark`.  
- Un fichier de licence temporaire ou complet GroupDocs.Watermark.

## Comment extraire les métadonnées étape par étape

### Comment récupérer les informations de base du document ?
La classe `Watermark` représente un document et fournit l’accès à ses métadonnées. La méthode `getDocumentInfo()` extrait l’objet de métadonnées du document chargé. Chargez le document avec la classe `Watermark`, puis appelez `getDocumentInfo()` pour obtenir un objet contenant le type de fichier, la taille, le nombre de pages et la date de création. Cette unique appel renvoie toutes les métadonnées principales en moins d’une seconde pour des fichiers typiques de moins de 100 Mo. L’objet `DocumentInfo` retourné inclut également l’auteur du document, la date de dernière modification et toutes les propriétés personnalisées intégrées, offrant ainsi une vue d’ensemble complète.

### Comment puis‑je lister tous les formats de fichiers pris en charge ?
L’utilitaire `SupportedFormats` fournit un catalogue de tous les types de fichiers que le SDK peut traiter. Utilisez l’utilitaire `SupportedFormats` fourni par le SDK. Il renvoie une collection d’identifiants de format que vous pouvez afficher ou valider avant de télécharger des fichiers, assurant ainsi la compatibilité et évitant les erreurs d’exécution. Chaque entrée comprend le nom du format, l’extension de fichier typique et une brève description de ses capacités, aidant les développeurs à valider les entrées avant le traitement.

### Comment extraire les détails d'arrière‑plan des diapositives d'un fichier PowerPoint ?
`SlideInfo` est un objet qui décrit les propriétés visuelles d’une diapositive, telles que l’image d’arrière‑plan et les dimensions. `getSlides()` renvoie une collection d’objets `SlideInfo` pour chaque diapositive de la présentation. L’objet `SlideInfo` expose les dimensions de l’image d’arrière‑plan, la taille du fichier et la profondeur de couleur. Accédez‑y via la collection `getSlides()`, puis itérez sur chaque diapositive pour lire ses propriétés d’arrière‑plan — utile pour le style dynamique ou la génération de miniatures. Ces détails peuvent être utilisés pour générer des miniatures, appliquer un style cohérent ou remplacer les arrière‑plans de façon programmatique sur plusieurs présentations.

## Problèmes courants et solutions
- **Métadonnées manquantes :** Certains fichiers plus anciens peuvent ne pas contenir de propriétés standard. Dans ce cas, activez le drapeau `extractCustomProperties` pour récupérer les champs définis par l'utilisateur.  
- **Les gros fichiers provoquent des dépassements de temps :** Augmentez le paramètre `maxMemory` du SDK ou traitez le document en mode streaming pour éviter de charger le fichier complet en RAM.  
- **Erreur de format non pris en charge :** Vérifiez le format par rapport à la liste renvoyée par `SupportedFormats` avant de tenter l'extraction.

## Questions fréquentes

**Q : Puis‑je extraire des métadonnées des documents protégés par mot de passe ?**  
R : Oui, fournissez le mot de passe lors de l’ouverture du document ; l’API le déchiffrera en mémoire puis lira les métadonnées.

**Q : La bibliothèque fonctionne‑t‑elle sur Android ?**  
R : Les fonctionnalités d’extraction principales sont compatibles avec Android API 21+ lorsqu’elles sont empaquetées en tant que JAR standard.

**Q : Comment gérer les champs de métadonnées personnalisés ?**  
R : Utilisez la méthode `getCustomProperties()` sur l’objet `DocumentInfo` ; elle renvoie une map de paires clé‑valeur que vous pouvez parcourir.

**Q : Existe‑t‑il un moyen de traiter en lot de nombreux fichiers ?**  
R : Encapsulez la logique d’extraction dans une boucle et réutilisez une seule instance `Watermark` ; le SDK est conçu pour les scénarios à haut débit.

**Q : Quelles options de licence sont disponibles ?**  
R : GroupDocs.Watermark propose des licences perpétuelles, d’abonnement et temporaires ; la licence temporaire est idéale pour l’évaluation et les pipelines CI.

## Tutoriels disponibles

### [Extraire les informations du document avec GroupDocs.Watermark pour Java&#58; Guide complet](./extract-document-info-groupdocs-watermark-java/)
Apprenez à extraire efficacement les métadonnées d’un document telles que le type de fichier, le nombre de pages et la taille en utilisant GroupDocs.Watermark pour Java. Ce guide couvre l’installation, l’implémentation et les applications pratiques.

### [Extraire les dimensions des pages PDF en Java avec GroupDocs.Watermark&#58; Guide complet](./get-pdf-page-dimensions-groupdocs-watermark-java/)
Apprenez à extraire les dimensions des pages PDF avec GroupDocs.Watermark pour Java. Ce guide couvre l’installation, des exemples de code et des applications pratiques.

### [Extraire les formes des documents Word avec GroupDocs.Watermark en Java](./extract-shapes-word-docs-groupdocs-watermark-java/)
Apprenez à extraire et analyser les formes des documents Word en utilisant GroupDocs.Watermark pour Java, améliorant l’automatisation et la manipulation de documents.

### [Comment extraire les informations d'arrière‑plan des diapositives avec GroupDocs.Watermark pour Java](./groupdocs-watermark-java-extract-slide-backgrounds/)
Apprenez à extraire les détails d’arrière‑plan des diapositives tels que les dimensions de l’image et la taille du fichier avec GroupDocs.Watermark pour Java. Idéal pour la personnalisation, l’analyse ou la documentation.

### [Comment lister les formats de fichiers pris en charge avec GroupDocs.Watermark pour Java&#58; Guide complet](./groupdocs-watermark-java-list-supported-formats/)
Apprenez à lister efficacement les formats de fichiers pris en charge avec GroupDocs.Watermark en Java, assurant la compatibilité avec divers types de documents.

### [Comment récupérer les informations du document avec GroupDocs.Watermark pour Java&#58; Guide étape par étape](./retrieve-document-info-groupdocs-watermark-java/)
Apprenez à récupérer efficacement les informations d’un document telles que le type de fichier, le nombre de pages et la taille en utilisant GroupDocs.Watermark pour Java. Suivez notre guide détaillé avec des exemples de code.

### [Comment récupérer les propriétés de section dans les documents Word avec GroupDocs.Watermark pour Java](./groupdocs-java-word-section-properties-retrieval/)
Apprenez à récupérer et manipuler efficacement les propriétés de section dans les documents Word en utilisant GroupDocs.Watermark pour Java. Parfait pour les développeurs souhaitant améliorer la gestion des documents.

## Ressources supplémentaires

- [Documentation GroupDocs.Watermark pour Java](https://docs.groupdocs.com/watermark/java/)
- [Référence API GroupDocs.Watermark pour Java](https://reference.groupdocs.com/watermark/java/)
- [Télécharger GroupDocs.Watermark pour Java](https://releases.groupdocs.com/watermark/java/)
- [Forum GroupDocs.Watermark](https://forum.groupdocs.com/c/watermark)
- [Support gratuit](https://forum.groupdocs.com/)
- [Licence temporaire](https://purchase.groupdocs.com/temporary-license/)

---

**Dernière mise à jour :** 2026-11-13  
**Testé avec :** GroupDocs.Watermark 23.12 for Java  
**Auteur :** GroupDocs

## Tutoriels associés

- [Comment lister les formats de fichiers pris en charge avec GroupDocs.Watermark pour Java : Guide complet](/watermark/java/document-information/groupdocs-watermark-java-list-supported-formats/)
- [Comment récupérer les informations du document avec GroupDocs.Watermark pour Java : Guide étape par étape](/watermark/java/document-information/retrieve-document-info-groupdocs-watermark-java/)
- [Extraire les informations du document avec GroupDocs.Watermark pour Java : Guide complet](/watermark/java/document-information/extract-document-info-groupdocs-watermark-java/)