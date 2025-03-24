---
title: Ajouter un filigrane de texte
linktitle: Ajouter un filigrane de texte
second_title: API GroupDocs.Watermark .NET
description: Découvrez comment ajouter des filigranes de texte à vos documents à l'aide de Groupdocs Watermark for .NET avec ce guide étape par étape.
weight: 11
url: /fr/net/watermarking-basics/add-text-watermark/
---

# Ajouter un filigrane de texte

## Introduction
GroupDocs.Watermark for .NET est une bibliothèque puissante qui permet aux développeurs d'ajouter, de rechercher et de supprimer des filigranes de divers formats de documents dans les applications .NET. Dans ce didacticiel, nous nous concentrerons sur l'ajout d'un filigrane de texte à un document à l'aide de GroupDocs.Watermark.
## Conditions préalables
Avant de commencer, assurez-vous d'avoir les prérequis suivants :
1. Connaissance de base du langage de programmation C#.
2. Visual Studio installé sur votre système.
3.  Bibliothèque GroupDocs.Watermark pour .NET installée. Vous pouvez le télécharger depuis[ici](https://releases.groupdocs.com/Watermark/net/).

## Importer des espaces de noms
Tout d’abord, vous devez importer les espaces de noms nécessaires dans votre projet C#.
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Watermarks;
using System;
using System.IO;
```
## Étape 1 : Définir le chemin du document et le répertoire de sortie
Définissez le chemin d'accès à votre document d'entrée et le répertoire de sortie où le document filigrané sera enregistré.
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
 Remplacer`"Your Document Path"` avec le chemin absolu ou relatif vers votre document d'entrée, par exemple :`@"C:\Docs\document.pdf"`. Spécifiez également le répertoire dans lequel vous souhaitez enregistrer le document filigrané.
## Étape 2 : ajouter un filigrane de texte
 Instancier le`Watermarker` classe avec le chemin du document d’entrée. Ensuite, créez un`TextWatermark` objet avec les paramètres de texte et de police souhaités.
```csharp
using (Watermarker watermarker = new Watermarker(documentPath))
{
    TextWatermark watermark = new TextWatermark("top secret", new Font("Arial", 36));
    watermark.ForegroundColor = Color.Red;
    watermark.HorizontalAlignment = HorizontalAlignment.Center;
    watermark.VerticalAlignment = VerticalAlignment.Center;
    watermarker.Add(watermark);
    watermarker.Save(outputFileName);
}
```

## Conclusion
Dans ce didacticiel, nous avons appris à ajouter un filigrane de texte à un document à l'aide de GroupDocs.Watermark pour .NET. Grâce à son API intuitive, les développeurs peuvent facilement manipuler les filigranes dans différents formats de documents.
## FAQ
### GroupDocs.Watermark pour .NET est-il compatible avec tous les formats de documents ?
GroupDocs.Watermark prend en charge un large éventail de formats de documents, notamment PDF, Microsoft Word, Excel, PowerPoint et bien d'autres.
### Puis-je personnaliser l’apparence du filigrane de texte ?
Oui, vous pouvez personnaliser diverses propriétés telles que la police, la couleur, l'alignement et l'opacité du filigrane de texte.
### GroupDocs.Watermark prend-il en charge la suppression des filigranes des documents ?
Oui, GroupDocs.Watermark offre des fonctionnalités permettant de rechercher et de supprimer les filigranes des documents.
### Puis-je essayer GroupDocs.Watermark pour .NET avant d'acheter ?
 Oui, vous pouvez télécharger une version d'essai gratuite à partir de[ici](https://releases.groupdocs.com/).
### Comment puis-je obtenir une assistance technique pour GroupDocs.Watermark ?
 Vous pouvez obtenir une assistance technique en visitant le[Forum GroupDocs.Watermark](https://forum.groupdocs.com/c/watermark/19).