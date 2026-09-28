---
date: '2026-01-03'
description: Apprenez à répertorier les destinataires d’e‑mail en Java avec GroupDocs.Watermark
  – automatisez l’extraction des champs À, CC et CCI à partir des documents e‑mail.
keywords:
- Java email parsing
- GroupDocs.Watermark Java
- listing email recipients
title: Lister les destinataires d'e-mails Java avec GroupDocs.Watermark
type: docs
url: /fr/java/email-document-watermarking/java-email-parsing-groupdocs-watermark-recipients/
weight: 1
---

# Liste des destinataires d'e‑mail Java avec GroupDocs.Watermark

Extraire chaque adresse **To**, **CC** et **BCC** d’un fichier e‑mail peut être fastidieux lorsqu’on traite des dizaines ou des centaines de messages. Dans ce tutoriel, vous apprendrez comment **lister les destinataires d’e‑mail java** rapidement et de façon fiable en tirant parti de la bibliothèque GroupDocs.Watermark pour Java. Nous parcourrons la configuration, les explications du code et des cas d’utilisation concrets afin que vous puissiez intégrer cette fonctionnalité dans vos propres applications.

## Réponses rapides
- **Que fait ce code ?** Il ouvre un fichier e‑mail et affiche toutes les adresses To, CC et BCC.  
- **Quelle bibliothèque est requise ?** GroupDocs.Watermark pour Java (version 24.11).  
- **Peut‑il lire les fichiers .msg et .eml ?** Oui – l’API prend en charge les formats d’e‑mail courants.  
- **Ai‑je besoin d’une licence ?** Un essai gratuit suffit pour les tests ; une licence complète est requise en production.  
- **Le traitement par lots est‑il possible ?** Absolument – vous pouvez boucler sur plusieurs fichiers en utilisant le même modèle.

## Introduction

En avez‑vous assez de parcourir manuellement les données d’e‑mail pour extraire les listes de destinataires ? L’automatisation de cette tâche permet de gagner du temps et de réduire les erreurs, surtout lorsqu’on manipule de gros volumes d’e‑mails. Ce guide vous montre comment exploiter la puissante bibliothèque GroupDocs.Watermark pour Java afin d’analyser les documents e‑mail et **lister les destinataires d’e‑mail java** de manière efficace.

**Ce que vous allez apprendre**
- Configurer votre environnement pour utiliser GroupDocs.Watermark pour Java  
- Charger et initialiser un document e‑mail avec l’API GroupDocs.Watermark  
- Récupérer les listes de destinataires To, CC et BCC à partir des documents e‑mail  
- Applications pratiques et considérations de performance  

Commençons par les prérequis.

## Prérequis

Avant de plonger dans le code, assurez‑vous que votre environnement est prêt :

### Bibliothèques requises, versions et dépendances

Vous devez disposer de GroupDocs.Watermark pour Java installé. Ce guide utilise la version 24.11.

### Exigences de configuration de l’environnement

- **Java Development Kit (JDK) :** version 8 ou supérieure  
- **Environnement de développement intégré (IDE) :** IntelliJ IDEA ou Eclipse recommandés  
- **Gestion des dépendances :** Maven ou configuration par téléchargement direct  

### Prérequis de connaissances

Une compréhension de base de la programmation Java et une familiarité avec la manipulation des formats d’e‑mail (comme les fichiers .msg) seront utiles.

## Installation de GroupDocs.Watermark pour Java

Pour commencer, vous devez configurer votre projet avec les dépendances nécessaires. Voici comment procéder :

**Configuration Maven**

Ajoutez la configuration suivante dans votre fichier `pom.xml` pour inclure GroupDocs.Watermark :

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

**Téléchargement direct**

Vous pouvez également télécharger la dernière version depuis [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

### Étapes d’obtention de licence

- **Essai gratuit :** Commencez avec un essai gratuit pour explorer les fonctionnalités.  
- **Licence temporaire :** Demandez une licence temporaire si vous avez besoin d’un accès prolongé pour les tests.  
- **Achat :** Envisagez d’acheter une licence pour une utilisation en production.

Une fois votre configuration prête, initialisons et préparons l’environnement pour le traitement des documents e‑mail.

## Comment lister les destinataires d’e‑mail Java – Guide d’implémentation

Cette section décompose chaque fonctionnalité en étapes gérables afin que vous puissiez implémenter l’analyse d’e‑mail efficacement avec GroupDocs.Watermark.

### Charger et initialiser le document e‑mail

**Vue d’ensemble**  
Le chargement d’un document e‑mail est la première étape de notre processus. Cette opération consiste à initialiser un objet `Watermarker`, qui sert de passerelle pour interagir avec les fichiers e‑mail.

**Étapes d’implémentation**

1. **Importer les classes requises**  
   ```java
   import com.groupdocs.watermark.Watermarker;
   import com.groupdocs.watermark.options.EmailLoadOptions;
   ```
2. **Définir le chemin du fichier e‑mail et les options de chargement**  
   Spécifiez le chemin vers votre document e‑mail. Remplacez `"YOUR_DOCUMENT_DIRECTORY/email.msg"` par le chemin réel.  
   ```java
   String emailFilePath = "YOUR_DOCUMENT_DIRECTORY/email.msg";
   EmailLoadOptions loadOptions = new EmailLoadOptions();
   Watermarker watermarker = new Watermarker(emailFilePath, loadOptions);
   ```
3. **Gestion des ressources**  
   N’oubliez jamais de fermer l’instance `Watermarker` après utilisation afin de libérer les ressources système.  
   ```java
   watermarker.close();
   ```

### Lister tous les destinataires directs d’un e‑mail

**Vue d’ensemble**  
Récupérer les destinataires directs (To) est simple une fois le document e‑mail initialisé.

**Étapes d’implémentation**

1. **Récupérer le contenu de l’e‑mail**  
   Assurez‑vous que l’objet `watermarker` est déjà initialisé comme indiqué dans la section précédente.  
   ```java
   import com.groupdocs.watermark.contents.EmailContent;
   
   EmailContent content = watermarker.getContent(EmailContent.class);
   ```
2. **Itérer et lister les destinataires**  
   Parcourez la liste des destinataires directs et affichez chaque adresse e‑mail.  
   ```java
   for (EmailAddress address : content.getTo()) {
       System.out.println("Direct Recipient: " + address.getEmailAddress());
   }
   ```

### Lister tous les destinataires CC d’un e‑mail

**Vue d’ensemble**  
Lister les destinataires CC suit un processus similaire à celui des destinataires directs, vous permettant d’accéder aux adresses supplémentaires présentes dans le champ CC.

**Étapes d’implémentation**

1. **Récupérer et itérer**  
   Utilisez l’objet `EmailContent` obtenu précédemment :  
   ```java
   for (EmailAddress address : content.getCc()) {
       System.out.println("CC Recipient: " + address.getEmailAddress());
   }
   ```

### Lister tous les destinataires BCC d’un e‑mail

**Vue d’ensemble**  
Même si les destinataires BCC ne sont pas visibles dans l’en‑tête de l’e‑mail, vous pouvez tout de même les récupérer avec GroupDocs.Watermark.

**Étapes d’implémentation**

1. **Accéder et afficher les adresses BCC**  
   ```java
   for (EmailAddress address : content.getBcc()) {
       System.out.println("BCC Recipient: " + address.getEmailAddress());
   }
   ```

## Applications pratiques

Ces fonctionnalités peuvent être intégrées à divers systèmes, tels que :

- **Systèmes de gestion d’e‑mail :** Automatiser la catégorisation et le traitement des e‑mails en fonction des listes de destinataires.  
- **Outils d’analyse de données :** Extraire les données de destinataires pour des analyses visant à identifier les schémas de communication au sein d’une organisation.  
- **Logiciels de sécurité :** Surveiller le trafic e‑mail afin de détecter des partages non autorisés ou des fuites d’information.  

## Considérations de performance

Lorsque vous traitez de grands volumes d’e‑mails, gardez à l’esprit les recommandations suivantes :

- **Optimiser l’utilisation des ressources :** Fermez rapidement l’objet `Watermarker` après usage.  
- **Gestion de la mémoire :** Soyez attentif au ramassage des ordures de Java et à la consommation mémoire lors du traitement de multiples fichiers.  
- **Traitement par lots :** Traitez les e‑mails par lots afin de réduire la charge sur les ressources système.  

## Questions fréquentes

**Q : Comment gérer les erreurs lors de l’analyse d’un e‑mail ?**  
R : Vérifiez que les chemins de fichiers sont corrects, que les fichiers respectent les formats attendus, et encapsulez votre code dans des blocs `try‑catch` pour capturer les `IOException` ou `GroupDocsException`.

**Q : Puis‑je utiliser cette bibliothèque avec d’autres formats d’e‑mail comme .eml ?**  
R : Oui, GroupDocs.Watermark prend en charge divers formats d’e‑mail. Consultez la documentation pour les options de chargement spécifiques à chaque format.

**Q : Quels sont les pièges courants lors de la liste des destinataires ?**  
R : Chemins de fichiers incorrects, types de fichiers non pris en charge ou oubli de fermer l’instance `Watermarker` peuvent entraîner des fuites de ressources.

**Q : Comment améliorer les performances lors de l’analyse d’un grand nombre d’e‑mails ?**  
R : Traitez les fichiers en parallèle à l’aide du `ExecutorService` de Java, tout en surveillant l’utilisation du CPU et de la mémoire pour éviter la surcharge.

**Q : Où puis‑je obtenir de l’aide en cas de problème ?**  
R : Visitez le [GroupDocs Free Support Forum](https://forum.groupdocs.com/c/watermark/10) pour obtenir de l’assistance communautaire et le support officiel.

## Ressources supplémentaires

- **Documentation :** [GroupDocs Watermark Java Docs](https://docs.groupdocs.com/watermark/java/)  
- **Référence API :** [GroupDocs API Reference](https://reference.groupdocs.com/watermark/java)  
- **Téléchargement :** [GroupDocs Watermark Releases](https://releases.groupdocs.com/watermark/java)  

## Conclusion

Vous avez maintenant appris comment **lister les destinataires d’e‑mail java** efficacement grâce à GroupDocs.Watermark pour Java. Cet outil puissant peut rationaliser vos processus de gestion d’e‑mail et ouvrir de nouvelles possibilités d’analyse de données et d’automatisation.

**Étapes suivantes**

- Explorez davantage de fonctionnalités dans l’[API GroupDocs.Watermark](https://docs.groupdocs.com/watermark/java/).  
- Intégrez ces extraits de code dans des projets plus vastes ou des pipelines de traitement par lots.  
- Expérimentez avec différentes configurations pour répondre à vos besoins spécifiques.

---

**Dernière mise à jour :** 2026-01-03  
**Testé avec :** GroupDocs.Watermark 24.11 pour Java  
**Auteur :** GroupDocs  

---