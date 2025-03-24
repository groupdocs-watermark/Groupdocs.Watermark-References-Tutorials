---
title: Ajouter un filigrane d'artefact au PDF
linktitle: Ajouter un filigrane d'artefact au PDF
second_title: API GroupDocs.Watermark .NET
description: Découvrez comment ajouter facilement des filigranes d'artefacts aux fichiers PDF à l'aide de Groupdocs.Watermark for .NET. Protégez vos documents en toute simplicité.
weight: 11
url: /fr/net/pdf-watermarking-attachments/add-artifact-watermark-pdf/
---

# Ajouter un filigrane d'artefact au PDF

## Introduction
L'ajout de filigranes aux fichiers PDF est un aspect crucial de la gestion documentaire, notamment lorsqu'il s'agit de protéger la propriété intellectuelle ou de brandir des documents. Groupdocs.Watermark pour .NET fournit une solution robuste pour ajouter sans effort des filigranes aux fichiers PDF. Dans ce didacticiel, nous verrons étape par étape le processus d'ajout d'un filigrane d'artefact aux fichiers PDF.
## Conditions préalables
Avant de commencer, assurez-vous de disposer des prérequis suivants :
1.  Groupdocs.Watermark pour .NET : téléchargez et installez Groupdocs.Watermark pour .NET à partir de[ici](https://releases.groupdocs.com/Watermark/net/).
2. Environnement de développement : disposez d'un environnement de développement .NET.
3. Document PDF : Préparez le document PDF auquel vous souhaitez ajouter le filigrane.
4. Répertoire de sortie : créez un répertoire pour enregistrer le fichier PDF filigrané.

## Importation d'espaces de noms
Pour commencer, importez les espaces de noms nécessaires dans votre projet C# :
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Étape 1 : Charger le document PDF
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
```
## Étape 2 : Définir les options de filigrane
```csharp
PdfArtifactWatermarkOptions options = new PdfArtifactWatermarkOptions();
```
## Étape 3 : ajouter un filigrane de texte
```csharp
TextWatermark textWatermark = new TextWatermark("This is an artifact watermark", new Font("Arial", 8));
textWatermark.HorizontalAlignment = HorizontalAlignment.Right;
watermarker.Add(textWatermark, options);
```
## Étape 4 : ajouter un filigrane d'image
```csharp
using (ImageWatermark imageWatermark = new ImageWatermark(Constants.LogoBmp))
{
    watermarker.Add(imageWatermark, options);
}
```
## Étape 5 : Enregistrez le PDF filigrané
```csharp
watermarker.Save(outputFileName);
```

## Conclusion
Dans ce didacticiel, nous avons appris à ajouter des filigranes d'artefact aux fichiers PDF à l'aide de Groupdocs.Watermark pour .NET. En suivant ces étapes, vous pouvez intégrer de manière transparente la fonctionnalité de filigrane dans vos applications .NET, garantissant ainsi la sécurité et l'intégrité de vos documents.
## FAQ
### Puis-je personnaliser l’apparence du filigrane de texte ?
Oui, vous pouvez personnaliser divers aspects tels que la police, la taille, la couleur et l'alignement du filigrane de texte selon vos préférences.
### Groupdocs.Watermark prend-il en charge l'ajout de filigranes à d'autres formats de documents ?
Oui, Groupdocs.Watermark prend en charge l'ajout de filigranes à un large éventail de formats de documents, notamment Word, Excel, PowerPoint, etc.
### Existe-t-il une version d’essai disponible pour Groupdocs.Watermark pour .NET ?
 Oui, vous pouvez télécharger une version d'essai gratuite à partir de[ici](https://releases.groupdocs.com/).
### Comment puis-je obtenir de l'aide pour tout problème ou requête lié à Groupdocs.Watermark ?
 Vous pouvez obtenir de l'aide sur le forum de la communauté Groupdocs[ici](https://forum.groupdocs.com/c/watermark/19).
### Puis-je utiliser Groupdocs.Watermark à des fins commerciales ?
Oui, vous pouvez acheter une licence pour un usage commercial auprès de[ici](https://purchase.groupdocs.com/buy).