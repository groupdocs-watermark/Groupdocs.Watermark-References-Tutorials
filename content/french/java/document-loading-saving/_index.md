---
date: 2026-09-16
description: Apprenez comment ajouter un filigrane à un PDF, charger des documents
  depuis diverses sources et enregistrer les fichiers filigranés en utilisant GroupDocs.Watermark
  pour Java.
keywords:
- add watermark to pdf
- load password protected document
- load document from disk
- load document from stream
- java load password protected
lastmod: 2026-09-16
og_description: Ajoutez rapidement un filigrane à un PDF avec GroupDocs.Watermark
  pour Java. Apprenez à charger des documents, gérer les mots de passe et enregistrer
  les fichiers filigranés.
og_image_alt: Guide showing how to add watermark to pdf using GroupDocs.Watermark
  Java SDK
og_title: Ajouter un filigrane à un PDF avec GroupDocs.Watermark pour Java
schemas:
- author: GroupDocs
  dateModified: '2026-09-16'
  description: Learn how to add watermark to pdf, load documents from various sources,
    and save watermarked files using GroupDocs.Watermark for Java.
  headline: How to add watermark to pdf with GroupDocs.Watermark for Java
  type: TechArticle
- questions:
  - answer: Yes. Call `watermarker.add()` repeatedly with different `TextWatermark`
      or `ImageWatermark` objects; each will be layered in the order added.
    question: Can I add multiple watermarks to the same PDF?
  - answer: Absolutely. All original PDF objects, including annotations, form fields,
      and metadata, remain untouched unless you explicitly modify them.
    question: Does the library preserve existing annotations?
  - answer: Yes. Pass a `PageRange` (e.g., `new PageRange(2, 4)`) to the `add` method
      to limit the watermark to specific pages.
    question: Is it possible to watermark only selected pages?
  - answer: The SDK can handle files up to **2 GB** without loading the entire document
      into memory, thanks to its streaming architecture.
    question: What is the maximum file size supported?
  - answer: Use `watermarker.remove(watermarkId)` where `watermarkId` is the identifier
      returned when you initially added the watermark.
    question: How do I remove a watermark after it has been added?
  type: FAQPage
tags:
- watermark pdf
- GroupDocs.Watermark
- Java document processing
- add watermark to pdf
- load document
title: Comment ajouter un filigrane à un PDF avec GroupDocs.Watermark pour Java
type: docs
url: /fr/java/document-loading-saving/
weight: 2
---

# Ajouter un filigrane à un PDF avec GroupDocs.Watermark pour Java

Dans ce guide, vous apprendrez comment **ajouter un filigrane à un PDF** en utilisant le SDK Java de GroupDocs.Watermark. Nous parcourrons le chargement des documents depuis le disque, les flux ou des sources protégées par mot de passe, l'application de filigranes texte ou image, et enfin l'enregistrement du PDF mis à jour. Que vous construisiez un processeur par lots ou un service à fichier unique, ces étapes vous offrent une solution fiable et prête pour la production.

## Réponses rapides
- **Puis-je ajouter un filigrane à un PDF protégé par mot de passe ?** Oui – transmettez le mot de passe lors du chargement du document, puis appliquez le filigrane normalement.  
- **Quels formats peuvent être filigranés ?** Plus de 30 formats, y compris PDF, DOCX, PPTX et images.  
- **Ai-je besoin d’une licence pour le développement ?** Une licence temporaire suffit pour les tests ; une licence complète est requise pour la production.  
- **Quelle version de Java est requise ?** Java 8 ou supérieur est pris en charge.  
- **Le streaming est‑il pris en charge ?** Absolument – vous pouvez charger depuis `InputStream` et enregistrer vers `OutputStream` sans toucher le système de fichiers.

## Qu’est‑ce que l’ajout de filigrane à un PDF ?
*Ajouter un filigrane à un PDF* désigne le processus de superposition de texte ou d'images semi‑transparentes sur chaque page d'un document PDF afin de transmettre la propriété, la confidentialité ou la marque. GroupDocs.Watermark pour Java fournit une API à appel unique qui gère automatiquement le positionnement, l'opacité et la sélection de plages de pages.

## Pourquoi utiliser GroupDocs.Watermark pour Java ?
GroupDocs.Watermark prend en charge **plus de 35 formats de fichiers** et peut traiter des **PDF de 500 pages en moins de 2 secondes** sur un CPU de serveur typique. La bibliothèque fonctionne entièrement en mémoire, vous n’avez donc jamais besoin d’installer Microsoft Office ou Adobe Acrobat. Son API est thread‑safe, ce qui la rend idéale pour les services web à haut débit.

## Prérequis
- Java 8 ou version plus récente installé.  
- Projet Maven ou Gradle configuré avec la dépendance `groupdocs-watermark`.  
- Une licence valide GroupDocs.Watermark (licence temporaire pour l’évaluation).  
- Fichiers PDF que vous souhaitez protéger, éventuellement avec des mots de passe.

## Comment ajouter un filigrane à un PDF – étape par étape

Chargez le document source, appliquez un filigrane, puis enregistrez le résultat. Les sections suivantes répondent directement à chaque sous‑tâche.

### Comment charger un document depuis le disque ?
`Watermarker` est la classe principale utilisée pour charger et manipuler les documents en vue de les filigraner. Fournissez le chemin complet du fichier au constructeur `Watermarker` ; le SDK détecte automatiquement le format du fichier, valide le contenu et charge le document en mémoire, prêt pour toute opération de filigrane. Cette approche fonctionne pour les PDF, les fichiers Word, les images et de nombreux autres types pris en charge.  
Après cette ligne, le PDF est entièrement chargé en mémoire, prêt pour toute opération de filigrane.  
```java
Watermarker watermarker = new Watermarker("C:/files/input.pdf");
```

### Comment charger un document depuis un flux ?
`Watermarker` peut également accepter un `InputStream` pour charger les documents directement depuis la mémoire. Lorsque vous recevez un fichier via HTTP ou une file d’attente de messages, encapsulez le tableau d’octets dans un `ByteArrayInputStream` et passez‑le au constructeur `Watermarker` qui accepte un `InputStream`. Le SDK lit le flux sans écrire sur le disque, préservant les performances et la sécurité, et prend en charge les gros fichiers en traitant les données par blocs. Cette méthode est idéale pour les services web et les architectures micro‑services.  
Le SDK lit le flux sans écrire sur le disque, préservant les performances et la sécurité.  
```java
InputStream pdfStream = new ByteArrayInputStream(pdfBytes);
Watermarker watermarker = new Watermarker(pdfStream);
```

### Comment charger un document protégé par mot de passe ?
`Watermarker` prend en charge le chargement de PDF protégés par mot de passe en fournissant le mot de passe comme deuxième argument. Fournissez le mot de passe comme second argument du constructeur. Le SDK déchiffre le PDF à la volée, après quoi vous pouvez le traiter comme n’importe quel autre document. Si le mot de passe est correct, toutes les pages deviennent accessibles pour le filigrane ; sinon la bibliothèque lève une exception claire que vous pouvez capturer et consigner pour le dépannage.  
Si le mot de passe est incorrect, le SDK lève une exception informative que vous pouvez capturer et consigner.  
```java
Watermarker watermarker = new Watermarker("C:/files/secure.pdf", "mySecretPwd");
```

### Comment appliquer un filigrane texte ?
`TextWatermark` représente un filigrane textuel qui peut être appliqué aux pages avec un style personnalisable. Créez un objet `TextWatermark` avec le texte, la police, la taille et la couleur souhaités. Ensuite, appelez `add` sur l’instance `Watermarker`, en spécifiant éventuellement des plages de pages. Le filigrane est rendu avec l’opacité et la rotation spécifiées, et il peut être positionné à l’aide d’emplacements prédéfinis ou de coordonnées personnalisées, garantissant une apparence cohérente sur toutes les pages.  
Cet appel place le filigrane sur chaque page par défaut ; vous pouvez le restreindre avec `new PageRange(1, 5)` si nécessaire.  
```java
TextWatermark watermark = new TextWatermark("Confidential", new Font("Arial", 36));
watermark.setColor(Color.RED);
watermark.setTransparency(0.5);
watermarker.add(watermark);
```

### Comment appliquer un filigrane image ?
`ImageWatermark` représente un filigrane basé sur une image, tel qu’un logo ou un sceau. Instanciez un `ImageWatermark` avec le chemin ou le flux de votre logo, puis ajoutez‑le de la même manière que le filigrane texte. Le SDK redimensionne automatiquement l’image pour l’adapter à la page tout en préservant son ratio d’aspect, et vous pouvez ajuster l’opacité, la rotation et le placement pour obtenir l’effet visuel souhaité sans déformer le contenu original.  
Le SDK redimensionne l’image pour l’adapter à la page tout en préservant le ratio d’aspect.  
```java
ImageWatermark imgWatermark = new ImageWatermark("C:/images/logo.png");
imgWatermark.setTransparency(0.3);
watermarker.add(imgWatermark);
```

### Comment enregistrer le document filigrané ?
`save` écrit le document modifié à l’emplacement spécifié dans le format choisi. Appelez `save` avec le chemin de sortie et le format désiré. Le même format que la source est utilisé lorsque vous omettez le paramètre de format. La méthode écrit le PDF modifié sur le disque, préservant tout le contenu original sauf les nouvelles couches de filigrane, et prend en charge l’enregistrement vers des flux pour un traitement ultérieur.  
La méthode écrit le PDF modifié sur le disque, préservant tout le contenu original sauf les nouvelles couches de filigrane.  
```java
watermarker.save("C:/files/output.pdf");
```

## Tutoriels disponibles

### [Comment charger des documents protégés par mot de passe en Java avec GroupDocs.Watermark](./groupdocs-watermark-java-password-protected-documents/)
Apprenez à charger et gérer les filigranes dans des documents protégés par mot de passe en utilisant GroupDocs.Watermark pour Java. Ce guide fournit des instructions étape par étape, des exemples pratiques et des conseils de dépannage.

### [Comment charger et filigraner des documents Word protégés par mot de passe avec GroupDocs.Watermark en Java](./groupdocs-watermark-java-password-protected-word-docs/)
Apprenez à utiliser GroupDocs.Watermark avec Java pour charger, gérer et filigraner efficacement des documents Word protégés par mot de passe.

## Ressources supplémentaires

- [Documentation GroupDocs.Watermark pour Java](https://docs.groupdocs.com/watermark/java/)
- [Référence API GroupDocs.Watermark pour Java](https://reference.groupdocs.com/watermark/java/)
- [Télécharger GroupDocs.Watermark pour Java](https://releases.groupdocs.com/watermark/java/)
- [Forum GroupDocs.Watermark](https://forum.groupdocs.com/c/watermark)
- [Support gratuit](https://forum.groupdocs.com/)
- [Licence temporaire](https://purchase.groupdocs.com/temporary-license/)

## Problèmes courants et solutions
- **Erreur de mot de passe invalide** – vérifiez à nouveau la chaîne du mot de passe ; elle doit être encodée en UTF‑8.  
- **Mémoire insuffisante sur de gros PDF** – activez le mode streaming en utilisant les constructeurs `Watermarker` qui acceptent `InputStream` et `OutputStream`.  
- **Filigrane non visible** – assurez‑vous que l’opacité du filigrane est supérieure à 0,1 et que la couleur contraste avec le fond de la page.

## Questions fréquentes

**Q : Puis‑je ajouter plusieurs filigranes au même PDF ?**  
R : Oui. Appelez `watermarker.add()` de façon répétée avec différents objets `TextWatermark` ou `ImageWatermark` ; chacun sera superposé dans l’ordre d’ajout.

**Q : La bibliothèque préserve‑t‑elle les annotations existantes ?**  
R : Absolument. Tous les objets PDF originaux, y compris les annotations, les champs de formulaire et les métadonnées, restent intacts à moins que vous ne les modifiiez explicitement.

**Q : Est‑il possible de filigraner uniquement des pages sélectionnées ?**  
R : Oui. Passez un `PageRange` (par ex., `new PageRange(2, 4)`) à la méthode `add` pour limiter le filigrane à des pages spécifiques.

**Q : Quelle est la taille maximale de fichier prise en charge ?**  
R : Le SDK peut gérer des fichiers jusqu’à **2 Go** sans charger l’ensemble du document en mémoire, grâce à son architecture de streaming.

**Q : Comment supprimer un filigrane après l’avoir ajouté ?**  
R : Utilisez `watermarker.remove(watermarkId)` où `watermarkId` est l’identifiant retourné lors de l’ajout initial du filigrane.

---

**Dernière mise à jour :** 2026-09-16  
**Testé avec :** GroupDocs.Watermark 23.9 for Java  
**Auteur :** GroupDocs

## Tutoriels associés

- [Comment ajouter un filigrane texte à un PDF avec GroupDocs.Watermark pour Java (Guide 2023)](/watermark/java/pdf-document-watermarking/add-text-watermark-pdf-java/)
- [Comment ajouter des filigranes texte et image à des pages PDF spécifiques avec GroupDocs.Watermark pour Java](/watermark/java/pdf-document-watermarking/add-watermarks-pdf-pages-groupdocs-java/)
- [Comment charger des documents protégés par mot de passe en Java avec GroupDocs.Watermark](/watermark/java/document-loading-saving/groupdocs-watermark-java-password-protected-documents/)