---
title: Ajouter un filigrane d'image
linktitle: Ajouter un filigrane d'image
second_title: API GroupDocs.Watermark .NET
description: Ajoutez sans effort des filigranes d'image à vos documents à l'aide de GroupDocs.Watermark pour .NET. Protégez votre propriété intellectuelle en toute simplicité.
type: docs
weight: 10
url: /fr/net/watermarking-basics/add-image-watermark/
---
## Introduction
Dans ce didacticiel, nous aborderons le processus d'ajout d'un filigrane d'image à vos documents à l'aide de GroupDocs.Watermark pour .NET. Le filigrane des documents est essentiel pour protéger la propriété intellectuelle et l’image de marque. Avec GroupDocs.Watermark pour .NET, vous pouvez intégrer de manière transparente des filigranes dans divers formats de documents tels que Word, Excel, PowerPoint, PDF et bien d'autres.
## Conditions préalables
Avant de commencer, assurez-vous que les conditions préalables suivantes sont remplies :
1.  Bibliothèque GroupDocs.Watermark pour .NET : téléchargez et installez la bibliothèque GroupDocs.Watermark pour .NET à partir du[site web](https://releases.groupdocs.com/Watermark/net/).
2. Document : Préparez le document auquel vous souhaitez ajouter le filigrane.
3. Image pour filigrane : préparez le fichier image que vous souhaitez utiliser comme filigrane.

## Importer des espaces de noms
```csharp
using System;
using System.IO;
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Options.Spreadsheet;
using GroupDocs.Watermark.Watermarks;
```
## Étape 1 : initialiser le chemin du document et le répertoire de sortie
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
 Remplacer`"Your Document Path"`avec le chemin absolu ou relatif de votre document et`"Your Document Directory"` avec le répertoire dans lequel vous souhaitez enregistrer le document filigrané.
## Étape 2 : ouvrir le flux de documents et initialiser le filigrane
```csharp
using (FileStream stream = File.Open(documentPath, FileMode.Open, FileAccess.ReadWrite))
{
    using (Watermarker watermarker = new Watermarker(stream))
    {
        // Le processus de filigrane se déroulera ici
    }
}
```
 Ouvrez le flux de documents en utilisant`FileStream` et initialiser le`Watermarker` objet.
## Étape 3 : ajouter un filigrane d'image
```csharp
using (ImageWatermark watermark = new ImageWatermark(Constants.LogoPng))
{
    watermark.HorizontalAlignment = HorizontalAlignment.Center;
    watermark.VerticalAlignment = VerticalAlignment.Center;
    watermarker.Add(watermark);
}
```
 Créé un`ImageWatermark` objet avec le chemin d’accès au fichier image que vous souhaitez utiliser comme filigrane. Définissez l’alignement horizontal et vertical du filigrane.
## Étape 4 : Enregistrer le document filigrané
```csharp
watermarker.Save(outputFileName);
```
Enregistrez le document filigrané dans le répertoire de sortie spécifié avec le nom de fichier souhaité.

## Conclusion
En conclusion, GroupDocs.Watermark pour .NET fournit une solution complète pour ajouter sans effort des filigranes à divers formats de documents. En suivant les étapes décrites dans ce didacticiel, vous pouvez ajouter efficacement des filigranes d'image à vos documents et protéger votre propriété intellectuelle.
## FAQ
### Puis-je ajouter des filigranes de texte à l’aide de GroupDocs.Watermark pour .NET ?
Oui, GroupDocs.Watermark pour .NET prend en charge l’ajout de filigranes d’image et de texte aux documents.
### GroupDocs.Watermark pour .NET est-il compatible avec différents formats de documents ?
Absolument, GroupDocs.Watermark pour .NET prend en charge un large éventail de formats de documents, notamment Word, Excel, PowerPoint, PDF, etc.
### GroupDocs.Watermark pour .NET fournit-il des options de personnalisation pour les filigranes ?
Oui, vous pouvez personnaliser divers aspects du filigrane tels que la position, la taille, l'opacité et la rotation.
### Puis-je supprimer les filigranes des documents à l’aide de GroupDocs.Watermark pour .NET ?
Oui, GroupDocs.Watermark pour .NET offre des fonctionnalités permettant de détecter et de supprimer les filigranes des documents.
### Existe-t-il une version d’essai disponible pour GroupDocs.Watermark pour .NET ?
 Oui, vous pouvez bénéficier d'une version d'essai gratuite sur le site Web pour explorer les fonctionnalités avant d'acheter.[ici](https://releases.groupdocs.com/).