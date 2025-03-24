---
title: Ajouter un filigrane à une page spécifique dans Word Docs
linktitle: Ajouter un filigrane à une page spécifique dans Word Docs
second_title: API GroupDocs.Watermark .NET
description: Découvrez comment ajouter des filigranes à des pages spécifiques dans des documents Word à l'aide de GroupDocs pour .NET. Protégez votre contenu sans effort.
weight: 14
url: /fr/net/word-processing-watermarkings/add-watermark-specific-page-word-docs/
---

# Ajouter un filigrane à une page spécifique dans Word Docs

## Introduction
Le filigrane des documents est un aspect crucial de la sécurité des documents et de l'image de marque. Dans ce didacticiel, nous verrons comment ajouter un filigrane à une page spécifique dans des documents Word à l'aide de GroupDocs.Watermark pour .NET.
## Conditions préalables
Avant de commencer, assurez-vous de disposer des prérequis suivants :
- Connaissance de base de la programmation C#.
- IDE Visual Studio installé.
- GroupDocs.Watermark pour .NET installé dans votre projet.

## Importation d'espaces de noms
Avant de plonger dans le code, assurez-vous d'importer les espaces de noms nécessaires :
```csharp
using GroupDocs.Watermark.Contents.WordProcessing;
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Étape 1 : Charger le document
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Votre code ira ici
}
```
## Étape 2 : ajouter le filigrane
```csharp
// Définir le texte et le style du filigrane
TextWatermark textWatermark = new TextWatermark("DRAFT", new Font("Arial", 42));
// Ajouter un filigrane à la dernière page
WordProcessingContent content = watermarker.GetContent<WordProcessingContent>();
WordProcessingWatermarkPagesOptions options = new WordProcessingWatermarkPagesOptions();
options.PageNumbers = new int[] {content.PageCount};
watermarker.Add(textWatermark, options);
```
## Étape 3 : Enregistrez le document
```csharp
// Enregistrez le document avec le filigrane
watermarker.Save(outputFileName);
```

## Conclusion
Dans ce didacticiel, nous avons appris à ajouter un filigrane à une page spécifique dans des documents Word à l'aide de GroupDocs.Watermark pour .NET. En suivant ces étapes, vous pouvez protéger efficacement vos documents et ajouter des éléments de marque si nécessaire.
## FAQ
### Puis-je personnaliser le texte et le style du filigrane ?
Oui, vous pouvez personnaliser le texte, la police, la taille, la couleur et la position du filigrane selon vos besoins.
### GroupDocs.Watermark pour .NET est-il compatible avec d’autres formats de documents ?
Oui, GroupDocs.Watermark prend en charge divers formats de documents, notamment Word, Excel, PowerPoint, PDF, etc.
### Puis-je ajouter plusieurs filigranes à un seul document ?
Absolument, vous pouvez ajouter plusieurs filigranes avec des contenus et des styles différents au même document.
### Existe-t-il un essai gratuit disponible pour GroupDocs.Watermark pour .NET ?
 Oui, vous pouvez explorer les fonctionnalités de GroupDocs.Watermark avec un essai gratuit. Visitez simplement le lien fourni pour commencer[ici](https://releases.groupdocs.com/).
### Où puis-je obtenir une assistance technique pour GroupDocs.Watermark ?
 Vous pouvez trouver des ressources utiles et obtenir une assistance technique auprès de[ici](https://forum.groupdocs.com/c/watermark/19)le forum GroupDocs.Watermark. Visitez le lien fourni pour rejoindre la communauté.