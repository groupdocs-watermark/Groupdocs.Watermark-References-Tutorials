---
title: Ajouter un filigrane aux artefacts d’image dans un PDF
linktitle: Ajouter un filigrane aux artefacts d’image dans un PDF
second_title: API GroupDocs.Watermark .NET
description: Protégez vos fichiers PDF avec des filigranes personnalisés à l'aide de GroupDocs.Watermark for .NET. Ajoutez facilement des filigranes de texte ou d’image aux artefacts d’image dans les documents PDF.
weight: 18
url: /fr/net/pdf-watermarking-attachments/add-watermark-image-artifacts-pdf/
---
## Introduction
Dans ce didacticiel, nous vous guiderons tout au long du processus d'ajout d'un filigrane aux artefacts d'image dans un document PDF à l'aide de GroupDocs.Watermark pour .NET. En suivant ces étapes, vous pouvez protéger efficacement vos fichiers PDF avec des filigranes personnalisés.
## Conditions préalables
Avant de commencer, assurez-vous de disposer des prérequis suivants :
1.  GroupDocs.Watermark pour .NET : téléchargez et installez la bibliothèque GroupDocs.Watermark pour .NET à partir de[ici](https://releases.groupdocs.com/Watermark/net/).
2. Chemin du document : indiquez le chemin d'accès au document PDF dans lequel vous souhaitez ajouter le filigrane.
3. Répertoire de sortie : créez un répertoire dans lequel le document filigrané sera enregistré.

## Importer des espaces de noms
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Étape 1 : charger le document et initialiser le filigrane
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
```
## Étape 2 : Obtenez le contenu PDF et ajoutez un filigrane
```csharp
	PdfContent pdfContent = watermarker.GetContent<PdfContent>();
	// Initialiser le filigrane d'une image ou d'un texte
	TextWatermark watermark = new TextWatermark("Protected image", new Font("Arial", 8));
	watermark.HorizontalAlignment = HorizontalAlignment.Center;
	watermark.VerticalAlignment = VerticalAlignment.Center;
	watermark.RotateAngle = 45;
	watermark.SizingType = SizingType.ScaleToParentDimensions;
	watermark.ScaleFactor = 1;
	foreach (PdfPage page in pdfContent.Pages)
	{
		foreach (PdfArtifact artifact in page.Artifacts)
		{
			if (artifact.Image != null)
			{
				// Ajouter un filigrane à l'image
				artifact.Image.Add(watermark);
			}
		}
	}
```
## Étape 3 : Enregistrez le document filigrané
```csharp
	watermarker.Save(outputFileName);
}
```

## Conclusion
Avec GroupDocs.Watermark pour .NET, l'ajout de filigranes aux artefacts d'image dans les documents PDF devient un processus transparent. En suivant ce tutoriel, vous pourrez protéger efficacement vos fichiers PDF avec des filigranes personnalisés, garantissant ainsi leur sécurité et leur authenticité.
## FAQ
### Puis-je ajouter des filigranes d’image et de texte à mon document PDF ?
Oui, GroupDocs.Watermark pour .NET prend en charge l’ajout simultané de filigranes d’image et de texte.
### Y a-t-il une limite au nombre de filigranes que je peux ajouter à un document ?
Non, vous pouvez ajouter plusieurs filigranes à un document sans aucune limitation.
### Puis-je personnaliser l’apparence et la position du filigrane ?
Absolument, vous avez un contrôle total sur l’apparence, la position et les propriétés du filigrane.
### GroupDocs.Watermark pour .NET prend-il en charge d'autres formats de documents que le PDF ?
Oui, il prend en charge divers formats de documents, notamment Word, Excel, PowerPoint, etc.
### Existe-t-il un moyen de supprimer les filigranes d’un document ?
Oui, GroupDocs.Watermark pour .NET fournit des méthodes pour supprimer les filigranes des documents si nécessaire.