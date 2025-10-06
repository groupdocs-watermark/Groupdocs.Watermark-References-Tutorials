---
title: Ajouter un filigrane d'image à tous les en-têtes dans Word Docs
linktitle: Ajouter un filigrane d'image à tous les en-têtes dans Word Docs
second_title: API GroupDocs.Watermark .NET
description: Ajoutez facilement des filigranes d'image à tous les en-têtes des documents Word à l'aide de GroupDocs.Watermark pour .NET. Suivez notre guide étape par étape avec des exemples de code détaillés.
weight: 10
url: /fr/net/word-processing-watermarkings/add-image-watermark-all-headers-word-docs/
type: docs
---
# Ajouter un filigrane d'image à tous les en-têtes dans Word Docs

## Introduction
Les filigranes peuvent constituer un élément essentiel de la gestion des documents, car ils permettent d'intégrer des informations telles que la propriété, la confidentialité ou la marque dans les documents. Dans ce didacticiel, nous passerons en revue les étapes permettant d'ajouter un filigrane d'image à tous les en-têtes des documents Word à l'aide de GroupDocs.Watermark pour .NET. Que vous soyez débutant en programmation ou développeur expérimenté, ce guide vous aidera à atteindre facilement vos objectifs en matière de filigrane.
## Conditions préalables
Avant de plonger dans le code, assurons-nous que nous disposons de tout ce dont nous avons besoin. Voici une liste de contrôle pour vous aider à démarrer :
1.  GroupDocs.Watermark pour .NET : téléchargez la dernière version à partir de[ici](https://releases.groupdocs.com/Watermark/net/).
2. Environnement de développement : Visual Studio ou tout autre IDE compatible .NET.
3. .NET Framework : assurez-vous que le framework .NET est installé.
4. Exemple de document Word : un document Word dans lequel vous souhaitez ajouter le filigrane.
5. Image pour filigrane : un fichier image que vous souhaitez utiliser comme filigrane.
Une fois que vous les avez prêts, nous pouvons commencer à mettre en place notre projet.
## Importer des espaces de noms
Tout d’abord, importons les espaces de noms nécessaires. Ces espaces de noms contiennent des classes et des méthodes qui nous aideront à travailler avec des filigranes dans nos documents.
```csharp
using GroupDocs.Watermark.Contents.WordProcessing;
using GroupDocs.Watermark.Options.Spreadsheet;
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Étape 1 : Configuration de votre projet
Pour commencer, créez une nouvelle application console dans Visual Studio. Ajoutez des références à la DLL GroupDocs.Watermark dans votre projet. Cela peut être fait en installant le package GroupDocs.Watermark NuGet.
```bash
Install-Package GroupDocs.Watermark
```
## Étape 2 : Chargez votre document
 La première étape pour ajouter un filigrane consiste à charger le document dans lequel le filigrane sera ajouté. Ici, nous utiliserons le`WordProcessingLoadOptions` pour charger un document Word.
```csharp
string documentPath = "Your Document Path";
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Le code pour ajouter un filigrane ira ici
}
```
## Étape 3 : Créer le filigrane de l'image
Ensuite, nous allons créer un filigrane d’image. Cela implique de spécifier le fichier image que vous souhaitez utiliser comme filigrane.
```csharp
using (ImageWatermark watermark = new ImageWatermark("Your Image Path"))
{
    // Le code pour appliquer le filigrane ira ici
}
```
## Étape 4 : ajouter un filigrane aux en-têtes de la première section
 Nous devons ajouter le filigrane à tous les en-têtes de la première section du document Word. Pour cela, nous utilisons`WordProcessingWatermarkSectionOptions` et spécifiez l'index de la section.
```csharp
WordProcessingWatermarkSectionOptions options = new WordProcessingWatermarkSectionOptions
{
    SectionIndex = 0
};
watermarker.Add(watermark, options);
```
## Étape 5 : Lier les en-têtes et les pieds de page
Pour garantir que le filigrane apparaisse dans les en-têtes de toutes les sections, nous lions tous les autres en-têtes et pieds de page aux en-têtes et pieds de page de la première section.
```csharp
WordProcessingContent content = watermarker.GetContent<WordProcessingContent>();
for (int i = 1; i < content.Sections.Count; i++)
{
    content.Sections[i].HeadersFooters.LinkToPrevious(true);
}
```
## Étape 6 : Enregistrez le document
Enfin, nous enregistrons le document filigrané dans un chemin spécifié. Cette étape garantit que vos modifications sont écrites dans un nouveau fichier, préservant ainsi le document d'origine.
```csharp
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
watermarker.Save(outputFileName);
```
## Conclusion
Et voila! Vous avez ajouté avec succès un filigrane d’image à tous les en-têtes d’un document Word à l’aide de GroupDocs.Watermark pour .NET. Cette puissante bibliothèque facilite la gestion et l'application de filigranes à différents types de documents, garantissant ainsi la protection de votre contenu et sa marque professionnelle.
## FAQ
### Puis-je utiliser d’autres types de filigranes en plus des images ?
Oui, GroupDocs prend en charge les filigranes de texte, d'image et même composites.
### Est-il possible de filigraner d’autres parties du document en plus des en-têtes ?
Absolument! Vous pouvez filigraner les pieds de page, le corps et même des pages ou sections spécifiques.
### GroupDocs.Watermark prend-il en charge d’autres formats de documents ?
Oui, il prend en charge un large éventail de formats, notamment les PDF, Excel, PowerPoint, etc.
### Puis-je personnaliser la position et l'apparence du filigrane ?
Oui, vous pouvez personnaliser la taille, la position, l'opacité et de nombreuses autres propriétés du filigrane.
### Existe-t-il un essai gratuit disponible pour GroupDocs.Watermark ?
 Oui, vous pouvez télécharger un essai gratuit à partir de[ici](https://releases.groupdocs.com/).