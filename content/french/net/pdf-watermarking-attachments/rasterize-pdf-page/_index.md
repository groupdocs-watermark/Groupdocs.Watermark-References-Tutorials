---
title: Pixelliser la page PDF
linktitle: Pixelliser la page PDF
second_title: API GroupDocs.Watermark .NET
description: Améliorez la sécurité des documents avec GroupDocs pour .NET. Ajoutez des filigranes aux PDF et à d’autres formats de manière transparente.
weight: 28
url: /fr/net/pdf-watermarking-attachments/rasterize-pdf-page/
---

# Pixelliser la page PDF

## Introduction
GroupDocs.Watermark for .NET est une API puissante qui permet aux développeurs d'ajouter de manière transparente des filigranes à divers formats de documents, notamment PDF, Word, Excel, PowerPoint, etc. Avec son interface intuitive et ses fonctionnalités étendues, GroupDocs.Watermark simplifie le processus d'ajout de filigranes de texte ou d'image aux documents, permettant aux utilisateurs de protéger leur propriété intellectuelle et d'améliorer la sécurité des documents sans effort.
## Conditions préalables
Avant de vous lancer dans l'utilisation de GroupDocs.Watermark pour .NET, assurez-vous que les conditions préalables suivantes sont en place :
1. Installation : Téléchargez et installez GroupDocs.Watermark pour .NET à partir du[page de téléchargement](https://releases.groupdocs.com/Watermark/net/).
2.  Licence : obtenez une licence pour GroupDocs.Watermark pour .NET. Vous pouvez obtenir une licence temporaire à des fins d'évaluation auprès de[ici](https://purchase.groupdocs.com/temporary-license/) , ou achetez une licence complète auprès du[page d'achat](https://purchase.groupdocs.com/buy).
3. .NET Framework : assurez-vous que le .NET Framework est installé sur votre ordinateur de développement.
4. Document : Préparez le document auquel vous souhaitez ajouter des filigranes.

## Importer des espaces de noms
Pour commencer à utiliser GroupDocs.Watermark pour .NET, importez les espaces de noms nécessaires dans votre projet :
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Étape 1 : Charger le document
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Votre code va ici
}
```
## Étape 2 : initialiser le filigrane
```csharp
TextWatermark watermark = new TextWatermark("Do not copy", new Font("Arial", 8));
watermark.HorizontalAlignment = HorizontalAlignment.Center;
watermark.VerticalAlignment = VerticalAlignment.Center;
watermark.RotateAngle = 45;
watermark.SizingType = SizingType.ScaleToParentDimensions;
watermark.ScaleFactor = 1;
watermark.Opacity = 0.5;
```
## Étape 3 : ajouter un filigrane
```csharp
PdfArtifactWatermarkOptions options = new PdfArtifactWatermarkOptions();
options.PageIndex = 0;
watermarker.Add(watermark, options);
```
## Étape 4 : pixelliser la page
```csharp
PdfContent pdfContent = watermarker.GetContent<PdfContent>();
pdfContent.Pages[0].Rasterize(100, 100, PdfImageConversionFormat.Png);
```
## Étape 5 : Enregistrez le document
```csharp
watermarker.Save(outputFileName);
```

## Conclusion
En conclusion, GroupDocs.Watermark pour .NET offre une solution transparente pour ajouter des filigranes au PDF et à d'autres formats de documents. En suivant le guide étape par étape décrit ci-dessus, les développeurs peuvent rastériser efficacement les pages PDF et améliorer facilement la sécurité des documents.
## FAQ
### GroupDocs.Watermark est-il compatible avec d'autres formats de documents que le PDF ?
Oui, GroupDocs.Watermark prend en charge un large éventail de formats de documents, notamment Word, Excel, PowerPoint, Visio, etc.
### Puis-je personnaliser l’apparence du filigrane ajouté au document ?
Absolument! GroupDocs.Watermark fournit des options de personnalisation étendues pour les filigranes de texte et d'image, permettant aux utilisateurs d'ajuster la police, la taille, la couleur, l'opacité et le positionnement en fonction de leurs préférences.
### GroupDocs.Watermark est-il adapté à un usage personnel et commercial ?
Oui, GroupDocs.Watermark propose des options de licence flexibles pour répondre aux besoins des particuliers et des entreprises, ce qui le rend adapté aux projets personnels ainsi qu'aux applications commerciales à grande échelle.
### GroupDocs.Watermark offre-t-il une assistance technique aux développeurs ?
Oui, les développeurs peuvent accéder à une assistance technique complète via le forum GroupDocs.Watermark, où ils peuvent demander de l'aide, partager leurs expériences et interagir avec d'autres développeurs.
### Puis-je essayer GroupDocs.Watermark avant de faire un achat ?
Certainement! Vous pouvez bénéficier d'une version d'essai gratuite de GroupDocs.Watermark à partir du[page des versions](https://releases.groupdocs.com/), vous permettant d'explorer ses caractéristiques et fonctionnalités avant de vous engager dans un achat.