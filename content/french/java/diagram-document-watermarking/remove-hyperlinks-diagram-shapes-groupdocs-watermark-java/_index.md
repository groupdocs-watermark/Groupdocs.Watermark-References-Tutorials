---
date: '2026-04-04'
description: Apprenez comment supprimer les liens des formes de diagramme avec GroupDocs.Watermark
  Java, en assurant la sécurité et la clarté du document.
keywords:
- how to strip links
- remove hyperlinks java
- java diagram editing
title: Comment supprimer les liens des formes de diagramme avec GroupDocs.Watermark
  Java
type: docs
url: /fr/java/diagram-document-watermarking/remove-hyperlinks-diagram-shapes-groupdocs-watermark-java/
weight: 1
---

# Comment supprimer les liens des formes de diagramme avec GroupDocs.Watermark Java

La gestion des documents numériques implique souvent la modification de diagrammes, surtout lorsque vous devez **supprimer les liens** pour des raisons de sécurité ou de clarté. Dans ce tutoriel, vous apprendrez une méthode simple, étape par étape, pour enlever les hyperliens indésirables des formes de diagramme en utilisant la puissante bibliothèque **GroupDocs.Watermark** pour Java. À la fin, vous disposerez de diagrammes propres, sans lien, sûrs à partager.

## Réponses rapides
- **Que signifie « supprimer les liens » ?** Il s'agit de supprimer les objets hyperlien intégrés dans les formes du diagramme.  
- **Quelle bibliothèque gère cela ?** GroupDocs.Watermark for Java (version 24.11 ou plus récente).  
- **Ai-je besoin d'une licence ?** Un essai gratuit suffit pour les tests ; une licence valide est requise pour la production.  
- **Puis-je traiter de nombreux fichiers à la fois ?** Oui – encapsulez le code dans une boucle ou un travail par lots.  
- **Cette approche est‑elle spécifique à un langage ?** L'exemple est en Java, mais le même concept s'applique aux autres API .NET/Java.

## Qu’est‑ce que « supprimer les liens » dans l’édition de diagrammes ?
Supprimer les liens consiste à localiser les objets hyperlien attachés aux formes d’un diagramme (par ex., Visio *.vsdx) et à les supprimer. Cela élimine les URL externes qui pourraient divulguer des informations sensibles ou interrompre le déroulement de la présentation.

## Pourquoi utiliser GroupDocs.Watermark pour Java ?
- **Précision** – Accès direct aux objets forme et à leurs collections d’hyperliens.  
- **Performance** – Optimisé pour les grands diagrammes sans charger le document complet en mémoire.  
- **Prise en charge multi‑format** – Fonctionne avec de nombreux formats de diagrammes (Visio, Draw.io, etc.).  

## Prérequis
- **Bibliothèque GroupDocs.Watermark** ≥ 24.11.  
- Maven (ou inclusion manuelle du JAR).  
- Java JDK 8 ou plus récent.  
- Un IDE tel qu’IntelliJ IDEA ou Eclipse.

## Configuration de GroupDocs.Watermark pour Java
### Configuration Maven
Ajoutez le dépôt et la dépendance à votre `pom.xml` :

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
Si vous préférez ne pas utiliser Maven, téléchargez le dernier JAR depuis le site officiel :

[GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

#### Étapes d’obtention de licence
- Commencez par télécharger la version d’essai gratuite.  
- Pour la production, obtenez une licence temporaire ou complète depuis le portail GroupDocs.

#### Initialisation et configuration de base
Créez une instance `Watermarker` qui pointe vers le dossier contenant votre diagramme :

```java
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY", loadOptions);
```

## Comment supprimer les liens des formes de diagramme
Voici un processus concis en quatre étapes qui montre **remove hyperlinks java** en action.

### Étape 1 : Charger le fichier de diagramme
```java
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY", loadOptions);
```
*Pourquoi ?* Charger le fichier vous donne un accès programmatique à ses pages, formes et collections d’hyperliens.

### Étape 2 : Accéder au contenu de la forme
```java
DiagramContent content = watermarker.getContent(DiagramContent.class);
DiagramShape shape = content.getPages().get_Item(0).getShapes().get_Item(0);
```
*Pourquoi ?* Vous avez besoin d’une référence à la forme spécifique qui peut contenir des hyperliens.

### Étape 3 : Parcourir et supprimer les hyperliens
```java
for (int i = shape.getHyperlinks().getCount() - 1; i >= 0; i--) {
    if (shape.getHyperlinks().get_Item(i).getAddress().contains("http://someurl.com")) {
        shape.getHyperlinks().removeAt(i);
    }
}
```
*Pourquoi ?* Parcourir en sens inverse évite les problèmes de décalage d’index lors de la suppression d’éléments de la collection.

### Étape 4 : Enregistrer et fermer
```java
watermarker.save("YOUR_OUTPUT_DIRECTORY");
watermarker.close();
```
*Pourquoi ?* L’enregistrement écrit le diagramme nettoyé sur le disque, et la fermeture libère les handles de fichier pour éviter les fuites de mémoire.

## Applications pratiques du retrait de liens
1. **Sécurité** – Supprimer les URL externes pouvant mener à du phishing ou à des fuites de données.  
2. **Conformité** – Garantir que les diagrammes respectent les politiques internes avant distribution.  
3. **Propreté de la présentation** – Éliminer les zones cliquables inutiles qui distraient les spectateurs.

## Considérations de performance
- **Efficacité de la boucle** – Utilisez le modèle d’itération inverse présenté ci‑dessus.  
- **Gestion des ressources** – Privilégiez `try‑with‑resources` ou les appels explicites à `close()`.  
- **Fichiers volumineux** – Surveillez le CPU/mémoire ; envisagez de traiter les pages par lots.

## Problèmes courants et solutions
- **Aucun hyperlien trouvé** – Vérifiez que le diagramme contient réellement des objets hyperlien ; certains formats les stockent différemment.  
- **IndexOutOfBoundsException** – Parcourez toujours en sens inverse lors de la suppression d’éléments d’une collection.  
- **Erreurs de licence** – Assurez‑vous que votre fichier de licence est correctement placé ou transmis au constructeur `Watermarker`.

## Questions fréquemment posées

**Q : Comment gérer plusieurs formes sur plusieurs pages ?**  
R : Parcourez `content.getPages()` puis la collection `getShapes()` de chaque page, en appliquant la même logique de suppression à chaque forme.

**Q : Puis‑je filtrer les liens par domaine au lieu d’une URL complète ?**  
R : Oui – modifiez la vérification `contains` pour rechercher la chaîne du domaine (par ex., `"example.com"`).

**Q : Existe‑t‑il un moyen de consigner quels liens ont été supprimés ?**  
R : À l’intérieur de la boucle, capturez `shape.getHyperlinks().get_Item(i).getAddress()` avant la suppression et écrivez‑le dans un fichier de journal.

**Q : Cette méthode fonctionne‑t‑elle avec des diagrammes PDF intégrés dans d’autres documents ?**  
R : GroupDocs.Watermark prend en charge de nombreux formats ; assurez‑vous que le type de fichier est reconnu comme un diagramme (Visio, VDX, etc.).

**Q : Quelle licence est requise pour le traitement par lots ?**  
R : Une licence de production complète est nécessaire pour toute opération non‑essai à haut volume.

## Conclusion
Vous disposez maintenant d’une méthode complète, prête pour la production, pour **supprimer les liens** des formes de diagramme avec GroupDocs.Watermark pour Java. Intégrez‑la à vos pipelines de traitement de documents afin d’améliorer la sécurité, la conformité et la qualité visuelle.

### Prochaines étapes
- Explorez d’autres fonctionnalités de manipulation comme l’ajout de filigranes ou le tamponnage de texte.  
- Combinez cette routine avec un service de surveillance de fichiers pour nettoyer automatiquement les diagrammes lors de leur téléchargement.

---

**Dernière mise à jour :** 2026-04-04  
**Testé avec :** GroupDocs.Watermark 24.11 for Java  
**Auteur :** GroupDocs  

## Ressources
- [Documentation](https://docs.groupdocs.com/watermark/java/)
- [Référence API](https://reference.groupdocs.com/watermark/java)
- [Téléchargement](https://releases.groupdocs.com/watermark/java/)
- [Référentiel GitHub](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)
- [Forum d’assistance gratuit](https://forum.groupdocs.com/c/watermark/10)
- [Obtention de licence temporaire](https://purchase.groupdocs.com/temporary-license/)