---
title: Ajouter un filigrane aux images d'annotation dans un PDF
linktitle: Ajouter un filigrane aux images d'annotation dans un PDF
second_title: API GroupDocs.Watermark .NET
description: Découvrez comment protéger vos documents PDF en ajoutant des filigranes aux images d'annotation à l'aide de Groupdocs.Watermark for .NET.
weight: 17
url: /fr/net/pdf-watermarking-attachments/add-watermark-annotation-images-pdf/
---

# Ajouter un filigrane aux images d'annotation dans un PDF

## Introduction
Dans ce didacticiel, nous verrons comment ajouter des filigranes aux images d'annotation dans des documents PDF à l'aide de Groupdocs.Watermark pour .NET. Le filigrane est crucial pour protéger vos documents contre toute utilisation ou distribution non autorisée. En suivant ce guide étape par étape, vous apprendrez comment appliquer efficacement des filigranes de texte aux images d'annotation dans les PDF.
## Conditions préalables
Avant de continuer, assurez-vous d'avoir les éléments suivants :
1. Compréhension de base du langage de programmation C#.
2. Bibliothèque Groupdocs.Watermark pour .NET installée.
3. Accès à un environnement de développement tel que Visual Studio.
4. Un document PDF avec des images d'annotation à filigraner.

## Importation d'espaces de noms
Tout d’abord, vous devez importer les espaces de noms nécessaires dans votre code C# :
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.Pdf;
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
## Étape 2 : Obtenez le contenu PDF et initialisez le filigrane
```csharp
    PdfContent pdfContent = watermarker.GetContent<PdfContent>();
    // Initialiser le filigrane d'une image ou d'un texte
    TextWatermark watermark = new TextWatermark("Protected image", new Font("Arial", 8));
    watermark.HorizontalAlignment = HorizontalAlignment.Center;
    watermark.VerticalAlignment = VerticalAlignment.Center;
    watermark.RotateAngle = 45;
    watermark.SizingType = SizingType.ScaleToParentDimensions;
    watermark.ScaleFactor = 1;
```
## Étape 3 : Parcourir les pages PDF et les images d'annotation
```csharp
    foreach (PdfPage page in pdfContent.Pages)
    {
        foreach (PdfAnnotation annotation in page.Annotations)
        {
            if (annotation.Image != null)
            {
                // Ajouter un filigrane à l'image
                annotation.Image.Add(watermark);
            }
        }
    }
```
## Étape 4 : Enregistrez le document avec un filigrane
```csharp
    watermarker.Save(outputFileName);
}
```
Après avoir exécuté ces étapes, votre document PDF verra le filigrane spécifié ajouté aux images d'annotation.

## Conclusion
L'ajout de filigranes aux images d'annotation dans les PDF est essentiel pour protéger l'intégrité de vos documents et garantir qu'ils ne sont pas utilisés à mauvais escient. Avec Groupdocs.Watermark pour .NET, ce processus devient simple et efficace, vous permettant de sauvegarder efficacement vos fichiers PDF.
## FAQ
### Puis-je ajouter plusieurs filigranes au même document PDF ?
Oui, vous pouvez ajouter plusieurs filigranes au même document PDF à l'aide de Groupdocs.Watermark pour .NET.
### Groupdocs.Watermark prend-il en charge d'autres formats de documents que le PDF ?
Oui, Groupdocs prend en charge divers formats de documents, notamment Word, Excel, PowerPoint, etc.
### Est-il possible de personnaliser l’apparence du filigrane ?
Absolument, vous pouvez personnaliser le texte, la police, la couleur, la taille et la position du filigrane selon vos préférences.
### Puis-je supprimer les filigranes des documents PDF à l’aide de Groupdocs.Watermark ?
Oui, Groupdocs.Watermark fournit des fonctionnalités permettant de supprimer sans effort les filigranes des documents PDF.
### Existe-t-il un essai gratuit disponible pour Groupdocs.Watermark pour .NET ?
Oui, vous pouvez bénéficier d’un essai gratuit de Groupdocs.Watermark pour .NET à partir du site Web.