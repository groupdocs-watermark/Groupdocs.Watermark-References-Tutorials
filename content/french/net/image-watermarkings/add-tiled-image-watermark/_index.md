---
title: Ajouter un filigrane d'image en mosaïque
linktitle: Ajouter un filigrane d'image en mosaïque
second_title: API GroupDocs.Watermark .NET
description: Découvrez comment ajouter des filigranes d’images en mosaïque à vos documents à l’aide de GroupDocs.Watermark for .NET. Facile, efficace et personnalisable.
weight: 10
url: /fr/net/image-watermarkings/add-tiled-image-watermark/
---

# Ajouter un filigrane d'image en mosaïque

## Introduction
GroupDocs.Watermark pour .NET est une API puissante qui permet aux développeurs d'ajouter, de supprimer et de rechercher par programme des filigranes dans divers formats de documents. Dans ce didacticiel, nous vous guiderons tout au long du processus d'ajout d'un filigrane d'image en mosaïque à vos documents à l'aide de GroupDocs.Watermark pour .NET.
## Conditions préalables
Avant de commencer, assurez-vous d'avoir les éléments suivants :
- Connaissance de base du langage de programmation C#.
- Visual Studio installé sur votre système.
- Bibliothèque GroupDocs.Watermark pour .NET ajoutée à votre projet. Vous pouvez le télécharger depuis[ici](https://releases.groupdocs.com/Watermark/net/).

## Importer des espaces de noms
Assurez-vous d'importer les espaces de noms nécessaires au début de votre fichier C# :
```csharp
using GroupDocs.Watermark.Watermarks;
using System;
using System.IO;
```
## Étape 1 : Définir le chemin du document et le répertoire de sortie
Définissez le chemin de votre document d'entrée et le répertoire dans lequel vous souhaitez enregistrer le document de sortie :
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
 Remplacer`"Your Document Path"` avec le chemin absolu ou relatif vers votre document d’entrée.
## Étape 2 : initialiser l'objet filigrane
Créez un objet Watermarker à l'aide du chemin du document d'entrée :
```csharp
using (Watermarker watermarker = new Watermarker(documentPath))
{
    // Ajouter un filigrane ici
}
```
## Étape 3 : Ajouter un filigrane d’image en mosaïque
Instanciez un objet ImageWatermark avec le chemin d'accès au fichier image que vous souhaitez utiliser comme filigrane :
```csharp
using (ImageWatermark watermark = new ImageWatermark("Path to Your Image"))
{
    // Configurer les options de vignette
    watermark.TileOptions = new TileOptions()
    {
        TileType = TileType.Offset,
        LineSpacing = new MeasureValue()
        {
            MeasureType = TileMeasureType.Percent,
            Value = 12
        },
        WatermarkSpacing = new MeasureValue()
        {
            MeasureType = TileMeasureType.Percent,
            Value = 10
        },
    };
    watermark.RotateAngle = -30;
    // Ajouter un filigrane au document
    watermarker.Add(watermark);
    // Enregistrez le document modifié
    watermarker.Save(outputFileName);
}
```
 Remplacer`"Path to Your Image"` avec le chemin réel vers votre fichier image en filigrane.

## Conclusion
En suivant ces étapes, vous pouvez facilement ajouter un filigrane d'image en mosaïque à vos documents à l'aide de GroupDocs.Watermark pour .NET. Expérimentez avec différentes options et configurations pour obtenir le résultat souhaité.
## FAQ
### Puis-je ajouter plusieurs filigranes à un seul document ?
Oui, vous pouvez ajouter plusieurs filigranes de différents types à un document à l'aide de GroupDocs.Watermark for .NET.
### GroupDocs.Watermark prend-il en charge tous les formats de documents ?
GroupDocs.Watermark prend en charge un large éventail de formats de documents, notamment PDF, Word, Excel, PowerPoint et bien d'autres.
### Existe-t-il une version d’essai disponible pour GroupDocs.Watermark ?
 Oui, vous pouvez télécharger une version d'essai gratuite à partir de[ici](https://releases.groupdocs.com/).
### Puis-je personnaliser l’apparence du filigrane ?
Oui, vous pouvez personnaliser différents aspects du filigrane, tels que la position, la taille, la rotation, la transparence, etc.
### GroupDocs.Watermark offre-t-il une assistance technique ?
 Oui, vous pouvez obtenir une assistance technique sur le forum GroupDocs.Watermark[ici](https://forum.groupdocs.com/c/watermark/19).