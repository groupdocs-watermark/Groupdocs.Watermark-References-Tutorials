---
date: '2026-04-07'
description: Apprenez à créer un filigrane texte pour les pièces jointes d'e-mails
  en utilisant GroupDocs.Watermark pour Java, sécurisant les pièces jointes d'e-mails
  et protégeant les données confidentielles.
keywords:
- create text watermark
- secure email attachments
- groupdocs watermark java
title: Créer un filigrane texte pour les pièces jointes d'e‑mail avec GroupDocs Java
type: docs
url: /fr/java/email-document-watermarking/groupdocs-watermark-java-email-attachments/
weight: 1
---

# Comment ajouter des filigranes aux pièces jointes d'e‑mail à l'aide de GroupDocs.Watermark pour Java

Dans ce tutoriel, vous allez **créer des objets text watermark** et les appliquer à chaque pièce jointe prise en charge dans un message e‑mail. Ajouter un filigrane est un moyen efficace de **sécuriser les pièces jointes d'e‑mail**, de signaler la confidentialité et de renforcer l'identité de la marque — le tout en quelques lignes de code Java.

## Introduction

Protéger les informations sensibles lorsqu'elles circulent par e‑mail est plus important que jamais. Que vous deviez étiqueter des rapports internes, signaler des contrats juridiques ou simplement marquer les actifs marketing, un text watermark vous offre une couche de protection légère et difficile à falsifier. Ce guide vous accompagne pas à pas dans l’utilisation de **GroupDocs.Watermark pour Java** afin d’ajouter un filigrane personnalisé à chaque pièce jointe d’un fichier Outlook `.msg`.

### Ce que vous apprendrez
- Comment **créer des objets text watermark** avec des polices et des couleurs personnalisées.  
- Intégration étape par étape du filigrane dans un flux de traitement d’e‑mail Java.  
- Astuces pour optimiser les performances lors du traitement de pièces jointes volumineuses.  
- Scénarios concrets où le filigrane des pièces jointes d’e‑mail apporte de la valeur.

Vérifions que vous avez tout ce qu’il faut avant de commencer.

## Réponses rapides
- **Que signifie « create text watermark » ?** Cela consiste à instancier un objet `TextWatermark` qui définit le texte visible, la police, la taille et le style à superposer sur un document.  
- **Puis‑je filigraner des pièces jointes chiffrées ?** Non – GroupDocs.Watermark ne prend pas en charge les fichiers chiffrés pour des raisons de sécurité.  
- **Quels types de fichiers sont pris en charge ?** PDFs, Word, Excel, PowerPoint, images, et bien d’autres – consultez la documentation officielle pour la liste complète.  
- **Ai‑je besoin d’une licence ?** Une licence d’essai suffit pour le développement ; une licence commerciale est requise pour la production.  
- **Quelle est la rapidité du processus ?** Filigraner une pièce jointe typique de 2 Mo prend moins d’une seconde sur du matériel moderne.

## Prérequis

- **Java Development Kit (JDK)** – version 8 ou supérieure.  
- Un IDE tel qu’IntelliJ IDEA ou Eclipse.  
- **GroupDocs.Watermark pour Java** ajouté à votre projet (voir les étapes d’installation ci‑dessous).  
- Accès à un fichier e‑mail (`.msg`, `.eml`, etc.) contenant les pièces jointes que vous souhaitez protéger.

## Configuration de GroupDocs.Watermark pour Java

### Configuration Maven

Si vous gérez les dépendances avec Maven, ajoutez le dépôt et la dépendance à votre `pom.xml` :

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

Vous pouvez également télécharger le JAR le plus récent depuis le site officiel :  
[GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/)

#### Acquisition de licence
- **Essai :** Inscrivez‑vous sur le site GroupDocs et demandez une licence temporaire.  
- **Commerciale :** Achetez une licence complète ici : [purchase page](https://purchase.groupdocs.com/temporary-license/).

### Initialisation de base

Importez les classes principales dont vous aurez besoin dans votre fichier source Java :

```java
import com.groupdocs.watermark.Watermarker;
// Other imports as needed...
```

## Qu’est‑ce qu’un text watermark ?

Un **text watermark** est une chaîne de texte semi‑transparent qui est rendue au-dessus de chaque page d’un document. Avec GroupDocs.Watermark, vous pouvez contrôler la police, la taille, la couleur, la rotation et l’opacité, vous offrant ainsi une flexibilité totale pour créer un avis de marque ou de confidentialité qui s’intègre naturellement au contenu original.

## Pourquoi utiliser GroupDocs.Watermark pour les pièces jointes d’e‑mail ?

- **Sécuriser les pièces jointes d’e‑mail** en les marquant visiblement comme confidentielles.  
- **Maintenir la cohérence de la marque** sur tous les documents sortants.  
- **Traitement par lots** de plusieurs e‑mails avec une seule boucle, économisant du temps et réduisant les erreurs manuelles.  
- **Prise en charge multiplateforme** – le même code fonctionne pour les PDFs, les fichiers Word, les images, etc.

## Guide d’implémentation

Nous parcourrons chaque étape, en expliquant le *pourquoi* du code afin que vous puissiez l’adapter à vos propres projets.

### Étape 1 : Créer un text watermark

Instanciez d’abord un `TextWatermark` avec le texte à afficher et les paramètres de police souhaités.

```java
import com.groupdocs.watermark.watermarks.Font;
import com.groupdocs.watermark.watermarks.TextWatermark;

// Step 1: Create a text watermark.
TextWatermark watermark = new TextWatermark("Confidential", new Font("Arial", 19));
```

> **Astuce :** Ajustez la taille ou la couleur de la police pour correspondre à votre guide de style corporate. Vous pouvez également définir l’opacité via `watermark.setOpacity(0.5)` si vous désirez un effet plus subtil.

### Étape 2 : Configurer les options de chargement d’e‑mail

`EmailLoadOptions` indique à la bibliothèque comment interpréter le fichier e‑mail entrant.

```java
import com.groupdocs.watermark.options.EmailLoadOptions;

// Step 2: Setup the email load options.
EmailLoadOptions loadOptions = new EmailLoadOptions();
```

### Étape 3 : Initialiser le Watermarker pour votre fichier e‑mail

Pointez le constructeur `Watermarker` vers le fichier `.msg` (ou `.eml`) que vous souhaitez traiter.

```java
import com.groupdocs.watermark.Watermarker;

// Step 3: Initialize the watermarker with your email file.
String emailFilePath = "YOUR_DOCUMENT_DIRECTORY/email_file.msg";
Watermarker watermarker = new Watermarker(emailFilePath, loadOptions);
```

### Étape 4 : Récupérer le contenu de l’e‑mail

Extrayez la structure interne de l’e‑mail afin de pouvoir parcourir ses pièces jointes.

```java
import com.groupdocs.watermark.contents.EmailContent;

// Step 4: Retrieve the email content.
EmailContent content = watermarker.getContent(EmailContent.class);
```

### Étape 5 : Parcourir les pièces jointes

Pour chaque pièce jointe, nous vérifions que le type de fichier est pris en charge et qu’il n’est pas chiffré.

```java
import com.groupdocs.watermark.common.FileType;
import com.groupdocs.watermark.contents.EmailAttachment;
import com.groupdocs.watermark.common.IDocumentInfo;

// Step 5: Process each attachment.
for (EmailAttachment attachment : content.getAttachments()) {
    IDocumentInfo info = attachment.getDocumentInfo();
    
    // Check if file type is supported and not encrypted
    if (info.getFileType() != FileType.Unknown && !info.isEncrypted()) {
        // Proceed with watermarking...
    }
}
```

### Étape 6‑9 : Ajouter le filigrane aux pièces jointes prises en charge

Dans le bloc conditionnel, nous créons un `Watermarker` dédié pour la pièce jointe, appliquons le filigrane, puis réinjectons le contenu modifié dans l’e‑mail.

```java
// Step 6: Create a watermarker for the attached document.
Watermarker attachedWatermarker = attachment.createWatermarker();

// Step 7: Apply the text watermark.
attachedWatermarker.add(watermark);

// Step 8: Update with the new content.
attachment.updateContent(attachedWatermarker);

// Step 9: Close the attached watermarker.
attachedWatermarker.close();
```

### Étape 10 : Enregistrer l’e‑mail filigrané

Écrivez l’e‑mail mis à jour dans un nouveau fichier afin que l’original reste intact.

```java
// Step 10: Save the modified email.
String outputFilePath = "YOUR_OUTPUT_DIRECTORY/watermarked_email_file.msg";
watermarker.save(outputFilePath);
```

### Étape 11 : Nettoyage

Libérez toujours les ressources pour éviter les fuites de mémoire.

```java
// Step 11: Close the watermarker for cleanup.
watermarker.close();
```

## Problèmes courants et solutions

| Problème | Raison | Solution |
|----------|--------|----------|
| **Filigrane non visible** | Opacité trop faible ou couleur de police identique à l’arrière‑plan. | Augmentez l’opacité (`watermark.setOpacity(0.7)`) ou choisissez une couleur contrastante. |
| **Type de pièce jointe non pris en charge** | Le format de fichier ne figure pas dans la liste supportée par GroupDocs. | Convertissez le fichier en un format supporté d’abord (par ex., PDF) ou ignorez‑le avec un message de journal. |
| **OutOfMemoryError sur de gros PDFs** | Le chargement de pièces jointes très volumineuses consomme trop de heap. | Augmentez le heap JVM (`-Xmx2g`) ou traitez les pièces jointes par lots plus petits. |

## FAQ

**Q : Puis‑je ajouter des filigranes à des fichiers chiffrés ?**  
R : Non, GroupDocs.Watermark ne prend pas en charge le filigrane de fichiers chiffrés pour des raisons de sécurité.

**Q : Quels types de fichiers sont pris en charge pour le filigrane ?**  
R : Les types pris en charge incluent les PDFs, les documents Word, les classeurs Excel, les présentations PowerPoint et les formats d’image courants. Consultez la documentation officielle pour la liste complète.

**Q : Comment personnaliser l’apparence de mon filigrane ?**  
R : Utilisez la classe `Font` pour définir la taille, le style et la couleur, et appelez des méthodes comme `setOpacity` et `setRotationAngle` sur l’instance `TextWatermark`.

**Q : Le traitement par lots de plusieurs e‑mails est‑il possible ?**  
R : Oui. Enveloppez le flux complet dans une boucle qui itère sur les fichiers d’un répertoire, en réutilisant la même instance `TextWatermark` pour plus d’efficacité.

**Q : Mon filigrane est tronqué sur la dernière page—quel est le problème ?**  
R : Assurez‑vous que le filigrane tient dans les marges de la page. Vous pouvez ajuster sa position avec `watermark.setHorizontalAlignment` et `watermark.setVerticalAlignment`.

## Applications pratiques

1. **Partage interne de documents** : Intégrez la marque de l’entreprise ou un avis de confidentialité avant de diffuser des rapports au sein de l’organisation.  
2. **Communications client** : Étiquetez les contrats et propositions avec « Confidentiel » pour rappeler aux destinataires les politiques de gestion des données.  
3. **Marketing par e‑mail** : Ajoutez un filigrane de marque discret aux PDFs promotionnels joints aux newsletters, renforçant la reconnaissance de la marque sans perturber le design.

## Considérations de performance

- **Gestion de la mémoire** : Fermez chaque `attachedWatermarker` rapidement (voir l’étape 9) pour libérer les ressources natives.  
- **Limites de taille de fichier** : Pour les pièces jointes supérieures à 10 Mo, envisagez le streaming du fichier ou augmentez la taille du heap JVM.  
- **Traitement parallèle** : Utilisez `ExecutorService` de Java pour filigraner plusieurs e‑mails simultanément, tout en surveillant l’utilisation du CPU afin d’éviter les conflits.

## Conclusion

Vous disposez maintenant d’une recette complète, prête pour la production, pour **créer des objets text watermark** et les appliquer à chaque pièce jointe prise en charge d’un fichier e‑mail à l’aide de GroupDocs.Watermark pour Java. En intégrant ce flux de travail à votre pipeline de traitement d’e‑mail existant, vous renforcerez la sécurité des documents, appliquerez votre branding et assurerez la conformité avec un minimum d’effort.

Prêt à passer à l’étape suivante ? Essayez d’étendre le code pour traiter un dossier entier de fichiers `.msg`, ou explorez d’autres types de filigranes tels que les images et les QR codes.

---

**Dernière mise à jour :** 2026-04-07  
**Testé avec :** GroupDocs.Watermark 24.11 pour Java  
**Auteur :** GroupDocs  

**Ressources**  
- [Documentation](https://docs.groupdocs.com/watermark/java/)  
- [Référence API](https://reference.groupdocs.com/watermark/java)  
- [Télécharger GroupDocs.Watermark pour Java](https://releases.groupdocs.com/watermark/java/)