---
title: Ajouter un filigrane aux images dans un PDF
linktitle: Ajouter un filigrane aux images dans un PDF
second_title: API GroupDocs.Watermark .NET
description: Apprenez à ajouter des filigranes aux images dans des documents PDF à l'aide de GroupDocs.Watermark for .NET grâce à notre didacticiel détaillé étape par étape. Sécurisez facilement vos PDF.
weight: 19
url: /fr/net/pdf-watermarking-attachments/add-watermark-images-pdf/
---
## Introduction
L'ajout de filigranes aux images d'un document PDF peut être essentiel pour protéger votre propriété intellectuelle ou garantir l'authenticité de vos documents. Grâce à GroupDocs.Watermark pour .NET, cette tâche peut être effectuée efficacement et facilement. Ce didacticiel vous guidera à travers chaque étape du processus, de la configuration de votre environnement à l'ajout de filigranes jusqu'à l'enregistrement du document final. Allons-y !
## Conditions préalables
Avant de commencer, assurez-vous d'avoir les éléments suivants :
1. Visual Studio : installez Visual Studio, l'environnement de développement intégré (IDE) pour les applications .NET.
2.  GroupDocs.Watermark pour .NET : téléchargez et installez la bibliothèque GroupDocs.Watermark pour .NET à partir du[page de sortie](https://releases.groupdocs.com/Watermark/net/).
3. Un document PDF : préparez un document PDF avec des images pour tester la fonctionnalité de filigrane.
4.  Permis temporaire : obtenez un[permis temporaire](https://purchase.groupdocs.com/temporary-license/) si vous évaluez le produit.
## Importer des espaces de noms
Tout d’abord, assurez-vous que les espaces de noms nécessaires sont importés dans votre projet. Cela inclura les espaces de noms de base requis pour travailler avec des documents PDF et des filigranes.
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.Image;
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Étape 1 : configurer le chemin du document et le répertoire de sortie
Pour commencer, définissez les chemins du document d'entrée et le répertoire de sortie où le document filigrané sera enregistré. Cette étape est cruciale pour garantir que votre programme sait où trouver le document source et où stocker le fichier traité.
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
## Étape 2 : Charger le document PDF
 Ensuite, vous devrez charger le document PDF en utilisant`PdfLoadOptions`. Cette classe vous permet de spécifier des options de chargement du PDF, comme la protection par mot de passe si nécessaire.
```csharp
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Votre code pour le filigrane ira ici
}
```
## Étape 3 : Créer le filigrane
Maintenant, initialisez le filigrane. Dans cet exemple, nous créons un filigrane de texte indiquant « Image protégée ». Personnalisez la police, l'alignement, la rotation et la mise à l'échelle en fonction de vos besoins.
```csharp
TextWatermark watermark = new TextWatermark("Protected image", new Font("Arial", 8));
watermark.HorizontalAlignment = HorizontalAlignment.Center;
watermark.VerticalAlignment = VerticalAlignment.Center;
watermark.RotateAngle = 45;
watermark.SizingType = SizingType.ScaleToParentDimensions;
watermark.ScaleFactor = 1;
```
## Étape 4 : Accéder au contenu PDF
Récupérez le contenu du document PDF. Plus précisément, nous devons accéder aux images du PDF. Ici, nous nous concentrons sur la première page, mais vous pouvez l'étendre à d'autres pages si nécessaire.
```csharp
PdfContent pdfContent = watermarker.GetContent<PdfContent>();
// Obtenez toutes les images de la première page
WatermarkableImageCollection images = pdfContent.Pages[0].FindImages();
```
## Étape 5 : appliquer le filigrane aux images
Parcourez chaque image trouvée sur la première page et appliquez le filigrane. Cela garantit que le filigrane sera appliqué à toutes les images de la page spécifiée.
```csharp
// Ajouter un filigrane à toutes les images trouvées
foreach (WatermarkableImage image in images)
{
    image.Add(watermark);
}
```
## Étape 6 : Enregistrez le document filigrané
Enfin, enregistrez le PDF filigrané dans le répertoire de sortie spécifié. Cette étape finalise le processus en écrivant les modifications dans un nouveau fichier.
```csharp
watermarker.Save(outputFileName);
```
## Conclusion
Et voila! L'ajout d'un filigrane aux images d'un PDF à l'aide de GroupDocs pour .NET est un processus simple qui peut considérablement améliorer la sécurité et l'authenticité de vos documents. En suivant ces étapes, vous pouvez vous assurer que votre propriété intellectuelle est protégée et que vos documents sont sécurisés.
## FAQ
### Qu’est-ce que GroupDocs.Watermark pour .NET ?
GroupDocs.Watermark for .NET est une bibliothèque complète qui permet aux développeurs d'ajouter, de rechercher et de supprimer des filigranes dans divers formats de documents, y compris les PDF.
### Puis-je ajouter des filigranes de texte et d’image à l’aide de GroupDocs.Watermark ?
Oui, GroupDocs.Watermark prend en charge les filigranes de texte et d'image, offrant ainsi une flexibilité pour différents types de besoins en matière de filigrane.
### Est-il possible de filigraner plusieurs pages dans un PDF ?
Absolument! Vous pouvez parcourir chaque page du PDF et appliquer des filigranes aux images de chaque page.
### Ai-je besoin d’une licence pour utiliser GroupDocs.Watermark pour .NET ?
 Oui, une licence est requise. Vous pouvez obtenir un[permis temporaire](https://purchase.groupdocs.com/temporary-license/) à des fins d’évaluation.
### Où puis-je trouver plus de documentation sur GroupDocs.Watermark pour .NET ?
 Vous pouvez trouver une documentation complète sur le[Page de documentation GroupDocs.Watermark](https://tutorials.groupdocs.com/Watermark/net/).