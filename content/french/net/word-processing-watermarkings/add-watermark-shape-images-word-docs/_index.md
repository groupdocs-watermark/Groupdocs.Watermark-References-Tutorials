---
title: Ajouter un filigrane pour façonner les images dans Word Docs
linktitle: Ajouter un filigrane pour façonner les images dans Word Docs
second_title: API GroupDocs.Watermark .NET
description: Découvrez comment ajouter des filigranes pour façonner des images dans des documents Word à l'aide de GroupDocs.Watermark pour .NET. Améliorez la sécurité des documents avec ce didacticiel.
weight: 17
url: /fr/net/word-processing-watermarkings/add-watermark-shape-images-word-docs/
---

# Ajouter un filigrane pour façonner les images dans Word Docs

## Introduction
Dans ce didacticiel, nous allons explorer comment ajouter un filigrane pour façonner des images dans des documents Word à l'aide de GroupDocs.Watermark pour .NET. Le filigrane est un aspect crucial de la protection des documents, en particulier lorsqu'il s'agit d'informations sensibles ou confidentielles. En ajoutant des filigranes pour façonner les images, vous pouvez garantir l'intégrité et la sécurité de vos documents.
## Conditions préalables
Avant de commencer, assurez-vous d'avoir les éléments suivants :
1.  GroupDocs.Watermark pour .NET : téléchargez et installez la bibliothèque GroupDocs.Watermark à partir du[page de téléchargement](https://releases.groupdocs.com/Watermark/net/).
2. Document : Préparez le document Word dans lequel vous souhaitez ajouter le filigrane.
3. Environnement de développement : configurez votre environnement de développement .NET préféré.
## Importer des espaces de noms
Avant d'écrire le code, assurez-vous d'importer les espaces de noms nécessaires :
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.WordProcessing;
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Étape 1 : Charger le document
Tout d'abord, définissez le chemin d'accès à votre document et spécifiez le nom du fichier de sortie :
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
```
## Étape 2 : initialiser le filigrane
 Instancier un`Watermarker` objet en fournissant le chemin du document et les options de chargement facultatives :
```csharp
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Ajoutez une logique de filigrane ici
}
```
## Étape 3 : Créer un filigrane de texte
Définissez le filigrane de texte avec les propriétés souhaitées telles que le texte, la police, l'alignement, la rotation, le dimensionnement, etc. :
```csharp
TextWatermark watermark = new TextWatermark("Protected image", new Font("Arial", 8));
watermark.HorizontalAlignment = HorizontalAlignment.Center;
watermark.VerticalAlignment = VerticalAlignment.Center;
watermark.RotateAngle = 45;
watermark.SizingType = SizingType.ScaleToParentDimensions;
watermark.ScaleFactor = 1;
```
## Étape 4 : appliquer un filigrane aux images de forme
Parcourez les sections et les formes du document pour identifier les images de forme et ajoutez le filigrane :
```csharp
WordProcessingContent content = watermarker.GetContent<WordProcessingContent>();
foreach (WordProcessingSection section in content.Sections)
{
    foreach (WordProcessingShape shape in section.Shapes)
    {
        if (shape.HeaderFooter == null && shape.Image != null)
        {
            shape.Image.Add(watermark);
        }
    }
}
```
## Étape 5 : Enregistrez le document
Enregistrez le document avec le filigrane ajouté dans le fichier de sortie spécifié :
```csharp
watermarker.Save(outputFileName);
```

## Conclusion
Dans ce didacticiel, nous avons appris à ajouter des filigranes pour façonner des images dans des documents Word à l'aide de GroupDocs.Watermark pour .NET. En suivant le guide étape par étape et en tirant parti des puissantes fonctionnalités de GroupDocs.Watermark, vous pouvez améliorer efficacement la sécurité et la protection de vos documents.
## FAQ
### Puis-je personnaliser l’apparence du texte du filigrane ?
Oui, vous pouvez ajuster diverses propriétés telles que la police, la taille, la couleur, l'angle de rotation et l'alignement pour personnaliser le filigrane selon vos préférences.
### GroupDocs.Watermark prend-il en charge d’autres formats de documents que Word ?
Oui, GroupDocs.Watermark prend en charge un large éventail de formats de documents, notamment PDF, Excel, PowerPoint, etc.
### Est-il possible d'ajouter plusieurs filigranes à un seul document ?
Absolument, vous pouvez ajouter plusieurs filigranes avec un contenu, des styles et des positions différents dans le même document.
### Puis-je supprimer les filigranes des documents à l’aide de GroupDocs.Watermark ?
Oui, GroupDocs.Watermark propose des fonctionnalités pour détecter et supprimer efficacement les filigranes des documents.
### GroupDocs.Watermark offre-t-il une compatibilité multiplateforme ?
Oui, GroupDocs.Watermark est compatible avec .NET Framework, .NET Core et .NET Standard, garantissant une intégration transparente sur différentes plates-formes.