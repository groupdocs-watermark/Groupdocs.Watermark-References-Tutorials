---
date: '2025-12-19'
description: Apprenez à supprimer les hyperliens des formes de diagramme à l'aide
  de GroupDocs.Watermark Java, une étape clé pour la sécurité des documents Java et
  la suppression en lot des hyperliens.
keywords:
- remove hyperlinks diagram shapes GroupDocs Watermark Java
- manage digital documents diagrams
- GroupDocs Watermark library Java
title: Comment supprimer les hyperliens des formes de diagramme à l'aide de GroupDocs.Watermark
  Java
type: docs
url: /fr/java/diagram-document-watermarking/remove-hyperlinks-diagram-shapes-groupdocs-watermark-java/
weight: 1
---

# Comment supprimer les hyperliens des formes de diagramme avec GroupDocs.Watermark Java

La gestion des documents numériques implique souvent la modification de diagrammes, notamment lors de la **suppression d'hyperliens** pour des raisons de sécurité ou de clarté. Dans ce tutoriel, vous apprendrez **comment supprimer les hyperliens** des formes de diagramme avec GroupDocs.Watermark pour Java, garantissant que vos fichiers restent propres, sûrs et professionnels.

## Réponses rapides
- **Quel est le but principal ?** Supprimer les hyperliens indésirables des formes de diagramme pour améliorer la sécurité des documents.  
- **Quelle bibliothèque est utilisée ?** GroupDocs.Watermark pour Java (version 24.11 ou ultérieure).  
- **Ai-je besoin d'une licence ?** Un essai fonctionne pour les tests ; une licence valide est requise en production.  
- **Puis-je traiter de nombreux fichiers à la fois ?** Oui – la même logique peut être placée dans une boucle de traitement par lots.  
- **Java 8 suffit‑il ?** Java 8+ est pris en charge ; les JDK plus récents sont recommandés.

## Qu’est‑ce que « comment supprimer les hyperliens » dans le contexte des diagrammes ?
Supprimer les hyperliens signifie effacer les références d'URL attachées aux formes d'un fichier de diagramme (par ex., Visio *.vsdx). Cette opération empêche la navigation accidentelle vers des sites externes et aide à respecter les exigences de conformité ou les politiques de sécurité internes.

## Pourquoi utiliser GroupDocs.Watermark Java pour cette tâche ?
- **Prise en charge robuste des formats** – fonctionne avec une large gamme de types de diagrammes.  
- **API fine‑grained** – vous permet de cibler des formes individuelles et leurs collections d'hyperliens.  
- **Optimisé pour la performance** – adapté aux fichiers uniques comme au traitement en masse.  

## Prérequis
- **Bibliothèque GroupDocs.Watermark** version 24.11 ou ultérieure.  
- Maven ou téléchargement direct du JAR (voir les étapes d'installation ci‑dessous).  
- Java Development Kit (JDK 8 ou plus récent) et un IDE tel qu'IntelliJ IDEA ou Eclipse.  

## Configuration de GroupDocs.Watermark pour Java
Pour commencer, incluez la bibliothèque dans votre projet via Maven ou en téléchargeant le JAR.

### Configuration Maven
Ajoutez la configuration suivante à votre `pom.xml` :

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
Sinon, téléchargez la dernière version depuis [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

#### Étapes d’obtention de licence
- Commencez avec un essai gratuit pour évaluer l'API.  
- Pour la production, obtenez une licence temporaire ou complète depuis le portail GroupDocs.

#### Initialisation et configuration de base
```java
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY", loadOptions);
```

## Comment supprimer les hyperliens des formes de diagramme
Voici un guide étape par étape qui vous montre comment charger un diagramme, localiser les formes et supprimer les hyperliens indésirables.

### Étape 1 : Charger le fichier de diagramme
```java
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY", loadOptions);
```
*Pourquoi ?* Charger le fichier vous donne un accès programmatique à sa structure interne.

### Étape 2 : Accéder au contenu de la forme
```java
DiagramContent content = watermarker.getContent(DiagramContent.class);
DiagramShape shape = content.getPages().get_Item(0).getShapes().get_Item(0);
```
*Pourquoi ?* Vous avez besoin d’une référence à la forme spécifique qui peut contenir des hyperliens.

### Étape 3 : Itérer et supprimer les hyperliens
```java
for (int i = shape.getHyperlinks().getCount() - 1; i >= 0; i--) {
    if (shape.getHyperlinks().get_Item(i).getAddress().contains("http://someurl.com")) {
        shape.getHyperlinks().removeAt(i);
    }
}
```
*Pourquoi ?* Parcourir à l’envers évite les erreurs d’index lors de la suppression d’éléments de la collection.

### Étape 4 : Enregistrer et fermer
```java
watermarker.save("YOUR_OUTPUT_DIRECTORY");
watermarker.close();
```
*Pourquoi ?* Persister les modifications et libérer les ressources évite les fuites de mémoire et les fichiers verrouillés.

## Suppression par lots d’hyperliens (cas d’utilisation avancé)
Si vous devez nettoyer de nombreux diagrammes à la fois, encapsulez la logique ci‑dessus dans une boucle qui itère sur une liste de chemins de fichiers. Les mêmes appels d’API s’appliquent ; il suffit de modifier les répertoires d’entrée et de sortie pour chaque itération. Cette approche correspond aux exigences de **suppression par lots d’hyperliens** pour les grands dépôts de documents.

## Applications pratiques
Supprimer les hyperliens des formes de diagramme peut être bénéfique dans plusieurs scénarios réels :

1. **Objectifs de sécurité** – Empêcher les liens externes qui pourraient exposer votre réseau au phishing ou aux logiciels malveillants.  
2. **Conformité** – Respecter les politiques d’entreprise qui interdisent les URL sortantes dans les documents partagés.  
3. **Clarté** – Produire des présentations plus épurées où les hyperliens sont inutiles ou distrayants.  

## Considérations de performance
### Optimisation des performances
- Utilisez le modèle d’itération inversée présenté ci‑dessus pour garder les boucles efficaces.  
- Fermez l’objet `Watermarker` dès que vous avez terminé pour libérer la mémoire.

### Directives d’utilisation des ressources
- Surveillez le CPU et la RAM lors du traitement de grands diagrammes.  
- Pour les traitements en masse, envisagez le streaming des fichiers plutôt que de les charger tous en même temps.

### Bonnes pratiques pour la gestion de la mémoire en Java
- Évitez de créer des objets à l’intérieur de boucles serrées.  
- Utilisez try‑with‑resources lorsque c’est possible pour le nettoyage automatique.

## Questions fréquemment posées
1. **Comment gérer plusieurs formes ?**  
   Itérez sur toutes les pages et leurs formes, en appliquant la même logique de suppression d’hyperliens à chaque forme.  

2. **Ce processus peut‑il être automatisé pour de grands lots de diagrammes ?**  
   Oui – intégrez le code dans une routine de traitement par lots ou intégrez‑le à votre système de gestion de documents.  

3. **Et si je dois supprimer les hyperliens uniquement de pages spécifiques ?**  
   Accédez à la page souhaitée par son indice (`content.getPages().get_Item(pageIndex)`) et ciblez uniquement les formes de cette page.  

4. **Une licence est‑elle requise pour l’utilisation en production de GroupDocs.Watermark ?**  
   Une licence commerciale valide est requise au‑delà de la période d’essai.  

5. **Cette méthode fonctionne‑t‑elle avec d’autres formats de diagramme ?**  
   GroupDocs.Watermark prend en charge de nombreux types de diagrammes ; vérifiez la compatibilité dans la documentation officielle.  

**Questions supplémentaires**

**Q:** *Est‑il possible d’enregistrer quels hyperliens ont été supprimés ?*  
**A:** Oui – avant d’appeler `removeAt(i)`, capturez `shape.getHyperlinks().get_Item(i).getAddress()` et écrivez‑le dans un fichier de journal.

**Q:** *La suppression des hyperliens affectera‑t‑elle l’apparence visuelle de la forme ?*  
**A:** Non. La géométrie de la forme reste inchangée ; seul le métadonnées du lien est supprimé.

**Q:** *Dois‑je réappliquer un style après la suppression ?*  
**A:** Pas généralement. La suppression d’un hyperlien n’altère pas le remplissage, le trait ou les styles de texte.

## Conclusion
Vous disposez maintenant d’une méthode complète et prête pour la production pour **supprimer les hyperliens** des formes de diagramme avec GroupDocs.Watermark pour Java. En suivant les étapes ci‑dessus, vous pouvez sécuriser vos diagrammes, respecter les politiques et garder vos documents impeccables.

---

**Dernière mise à jour :** 2025-12-19  
**Testé avec :** GroupDocs.Watermark 24.11 for Java  
**Auteur :** GroupDocs  

**Ressources**  
- [Documentation](https://docs.groupdocs.com/watermark/java/)  
- [Référence API](https://reference.groupdocs.com/watermark/java)  
- [Téléchargement](https://releases.groupdocs.com/watermark/java/)  
- [Dépôt GitHub](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)  
- [Forum d'assistance gratuit](https://forum.groupdocs.com/c/watermark/10)  
- [Acquisition de licence temporaire](https://purchase.groupdocs.com/temporary-license/)