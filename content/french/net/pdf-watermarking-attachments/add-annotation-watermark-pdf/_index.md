---
title: Ajouter un filigrane d'annotation au PDF
linktitle: Ajouter un filigrane d'annotation au PDF
second_title: API GroupDocs.Watermark .NET
description: Découvrez comment ajouter facilement des filigranes d'annotation aux documents PDF à l'aide de GroupDocs.Watermark for .NET. Améliorez facilement l’image de marque et la sécurité des documents.
weight: 10
url: /fr/net/pdf-watermarking-attachments/add-annotation-watermark-pdf/
---

# Ajouter un filigrane d'annotation au PDF

## Introduction
Dans le domaine de la gestion documentaire, l'ajout de filigranes aux fichiers PDF constitue un aspect crucial, notamment à des fins de branding, de sécurité et d'identification des documents. GroupDocs.Watermark for .NET est une bibliothèque puissante qui facilite l'intégration transparente des filigranes dans divers formats de documents, y compris les PDF. Dans ce didacticiel, nous aborderons étape par étape le processus d'ajout de filigranes d'annotation aux documents PDF, en utilisant les fonctionnalités fournies par GroupDocs.Watermark pour .NET.
## Conditions préalables
Avant de poursuivre le didacticiel, assurez-vous que les conditions préalables suivantes sont remplies :
1.  Bibliothèque GroupDocs.Watermark pour .NET : téléchargez et installez la bibliothèque GroupDocs.Watermark pour .NET à partir du[site web](https://releases.groupdocs.com/Watermark/net/).
2. Environnement de développement : configurez un environnement de développement approprié, tel que Visual Studio ou tout autre IDE .NET.
3. Compréhension de base de C# : Une connaissance des principes fondamentaux du langage de programmation C# est recommandée.

## Importation des espaces de noms nécessaires
Pour commencer, importez les espaces de noms requis dans votre projet C# :
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Options.Image;
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
	PdfAnnotationWatermarkOptions options = new PdfAnnotationWatermarkOptions();
```
## Étape 3 : ajouter un filigrane de texte
```csharp
	TextWatermark textWatermark = new TextWatermark("This is an annotation watermark", new Font("Arial", 8));
	textWatermark.HorizontalAlignment = HorizontalAlignment.Left;
	textWatermark.VerticalAlignment = VerticalAlignment.Top;
	watermarker.Add(textWatermark, options);
```
## Étape 4 : ajouter un filigrane d'image
```csharp
	using (ImageWatermark imageWatermark = new ImageWatermark(Constants.ProtectJpg))
	{
		imageWatermark.HorizontalAlignment = HorizontalAlignment.Right;
		imageWatermark.VerticalAlignment = VerticalAlignment.Top;
		watermarker.Add(imageWatermark, options);
	}
```
## Étape 5 : Enregistrez le document avec un filigrane
```csharp
	watermarker.Save(outputFileName);
}
```

## Conclusion
En conclusion, GroupDocs.Watermark pour .NET offre une solution complète pour ajouter par programme des filigranes d'annotation aux documents PDF. En suivant les étapes décrites, les utilisateurs peuvent intégrer de manière transparente des filigranes de texte et d'image dans leurs fichiers PDF, améliorant ainsi la personnalisation et la sécurité des documents.
## FAQ
### GroupDocs.Watermark est-il compatible avec d'autres formats de documents que le PDF ?
Oui, GroupDocs.Watermark prend en charge un large éventail de formats de documents, notamment Word, Excel, PowerPoint, etc.
### Puis-je personnaliser l’apparence du filigrane ?
Absolument! GroupDocs.Watermark fournit des options de personnalisation étendues pour les filigranes de texte et d'image, permettant aux utilisateurs d'ajuster la taille, la position, l'opacité et d'autres paramètres.
### GroupDocs.Watermark est-il adapté au traitement par lots de documents ?
Certainement! GroupDocs.Watermark offre des capacités de traitement par lots efficaces, permettant aux utilisateurs d'appliquer des filigranes à plusieurs documents simultanément.
### GroupDocs.Watermark prend-il en charge le développement .NET Core ?
Oui, GroupDocs.Watermark prend en charge .NET Core, permettant aux développeurs d'intégrer des fonctionnalités de filigrane dans des applications multiplateformes.
### Une assistance technique est-elle disponible pour les utilisateurs de GroupDocs.Watermark ?
Oui, GroupDocs fournit une assistance technique complète via ses forums dédiés et ses canaux de service client.