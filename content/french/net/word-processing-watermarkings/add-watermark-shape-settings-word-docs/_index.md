---
title: Ajouter un filigrane avec les paramètres de forme dans Word Docs
linktitle: Ajouter un filigrane avec les paramètres de forme dans Word Docs
second_title: API GroupDocs.Watermark .NET
description: Découvrez comment ajouter des filigranes avec des paramètres de forme aux documents Word à l'aide de GroupDocs pour .NET. Protégez efficacement vos documents.
weight: 20
url: /fr/net/word-processing-watermarkings/add-watermark-shape-settings-word-docs/
---
## Introduction
Dans ce didacticiel, nous allons parcourir le processus d'ajout d'un filigrane avec des paramètres de forme aux documents Word à l'aide de GroupDocs.Watermark pour .NET.
## Conditions préalables
Avant de commencer, assurez-vous d'avoir les éléments suivants :
1.  GroupDocs.Watermark pour .NET installé. Vous pouvez le télécharger depuis[ici](https://releases.groupdocs.com/Watermark/net/).
2. Connaissance de base de la programmation C#.
3. Une compréhension du traitement des documents Word.

## Importer des espaces de noms
Tout d’abord, vous devez importer les espaces de noms nécessaires pour accéder aux classes et méthodes requises.
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Étape 1 : Charger le document
Chargez le document Word à l'endroit où vous souhaitez ajouter le filigrane.
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Le code d'ajout du filigrane va ici
}
```
## Étape 2 : ajouter un filigrane
 Instancier un`TextWatermark` objet et spécifiez le texte que vous souhaitez utiliser comme filigrane.
```csharp
TextWatermark watermark = new TextWatermark("Test watermark", new Font("Arial", 19));
```
## Étape 3 : Personnaliser les paramètres du filigrane
Définissez divers paramètres pour le filigrane, tels que l'alignement, l'angle de rotation, la couleur et l'opacité.
```csharp
watermark.VerticalAlignment = VerticalAlignment.Center;
watermark.HorizontalAlignment = HorizontalAlignment.Center;
watermark.RotateAngle = 25.0;
watermark.ForegroundColor = Color.Red;
watermark.Opacity = 1.0;
```
## Étape 4 : Définir les options de la section Filigrane
Définissez les options pour la section du filigrane, telles que le nom de la forme et le texte alternatif.
```csharp
WordProcessingWatermarkSectionOptions options = new WordProcessingWatermarkSectionOptions();
options.Name = "Shape 1";
options.AlternativeText = "Test watermark";
```
## Étape 5 : ajouter un filigrane au document
Ajoutez le filigrane au document avec les options spécifiées.
```csharp
watermarker.Add(watermark, options);
```
## Étape 6 : Enregistrez le document
Enregistrez le document avec le filigrane ajouté.
```csharp
watermarker.Save(outputFileName);
```

## Conclusion
L'ajout de filigranes avec des paramètres de forme aux documents Word à l'aide de GroupDocs pour .NET est un processus simple. En suivant les étapes décrites dans ce didacticiel, vous pouvez protéger efficacement vos documents avec des filigranes personnalisés.
## FAQ
### Puis-je ajouter plusieurs filigranes au même document ?
Oui, vous pouvez ajouter plusieurs filigranes avec des paramètres différents au même document.
### GroupDocs.Watermark prend-il en charge d’autres formats de documents que Word ?
Oui, GroupDocs.Watermark prend en charge divers formats de documents, notamment Excel, PowerPoint, PDF, etc.
### Puis-je personnaliser davantage l’apparence du filigrane ?
Absolument, vous pouvez ajuster divers paramètres tels que la taille de la police, le style, la couleur et la position en fonction de vos besoins.
### Existe-t-il une version d’essai disponible pour GroupDocs.Watermark pour .NET ?
 Oui, vous pouvez bénéficier d'un essai gratuit auprès de[ici](https://releases.groupdocs.com/).
### Où puis-je trouver de l’assistance pour GroupDocs.Watermark ?
 Vous pouvez trouver de l'aide et poser des questions sur le forum GroupDocs[ici](https://forum.groupdocs.com/c/watermark/19).