---
title: Ajouter un filigrane avec le type de marge de page dans un PDF
linktitle: Ajouter un filigrane avec le type de marge de page dans un PDF
second_title: API GroupDocs.Watermark .NET
description: Découvrez comment ajouter des filigranes avec un type de marge de page dans un PDF à l'aide de Groupdocs Watermark for .NET. Sécurisez vos documents sans effort.
type: docs
weight: 21
url: /fr/net/pdf-watermarking-attachments/add-watermark-page-margin-type-pdf/
---
## Introduction
À l’ère numérique d’aujourd’hui, la sécurisation des documents est plus cruciale que jamais. Une façon de garantir l’intégrité et l’authenticité de vos documents consiste à ajouter des filigranes. Groupdocs.Watermark pour .NET est un outil exceptionnel conçu pour rendre ce processus sans effort. Dans ce didacticiel, nous vous guiderons à travers les étapes pour ajouter un filigrane avec un type de marge de page dans un PDF à l'aide de Groupdocs.Watermark pour .NET.
## Conditions préalables
Avant de plonger dans le didacticiel, assurez-vous que les conditions préalables suivantes sont remplies :
-  Groupdocs.Watermark pour .NET : téléchargez et installez le[dernière version](https://releases.groupdocs.com/Watermark/net/) de Groupdocs.Watermark pour .NET.
- Environnement de développement : un environnement de développement .NET comme Visual Studio.
- Connaissance de base de C# : Familiarité avec le langage de programmation C#.
- Document PDF : un document PDF auquel vous souhaitez ajouter un filigrane.
## Importer des espaces de noms
Tout d’abord, vous devez importer les espaces de noms nécessaires dans votre projet C#. Ces espaces de noms donneront accès aux fonctionnalités de Groupdocs.
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
Maintenant, décomposons le processus en étapes gérables. Suivez attentivement chaque étape pour ajouter un filigrane à votre document PDF.
## Étape 1 : Configurez le chemin de votre document et votre répertoire de sortie
Tout d'abord, vous devrez spécifier le chemin d'accès à votre document et le répertoire de sortie dans lequel le PDF filigrané sera enregistré.
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
## Étape 2 : Chargez votre document PDF
 Ensuite, vous chargerez votre document PDF à l'aide du`PdfLoadOptions` classe. Cette classe vous permet de spécifier toutes les options nécessaires au chargement de votre PDF.
```csharp
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
```
## Étape 3 : Créer le filigrane de texte
Il est maintenant temps de créer le filigrane. Dans cet exemple, nous allons créer un filigrane de texte avec des propriétés spécifiques telles que la police, la taille et l'alignement.
```csharp
TextWatermark watermark = new TextWatermark("Test watermark", new Font("Arial", 42));
watermark.HorizontalAlignment = HorizontalAlignment.Right;
watermark.VerticalAlignment = VerticalAlignment.Top;
watermark.SizingType = SizingType.ScaleToParentDimensions;
watermark.ScaleFactor = 1;
```
## Étape 4 : Définir le type de marge de page
 Pour positionner votre filigrane de manière appropriée, vous devrez définir le type de marge de page. Ici, nous définissons le type de marge de la page sur`BleedBox`.
```csharp
PdfContent pdfContent = watermarker.GetContent<PdfContent>();
pdfContent.PageMarginType = PdfPageMarginType.BleedBox;
watermark.ConsiderParentMargins = true;
```
## Étape 5 : ajouter et enregistrer le filigrane
Enfin, ajoutez le filigrane à votre document et enregistrez le PDF modifié dans le répertoire de sortie spécifié.
```csharp
watermarker.Add(watermark);
watermarker.Save(outputFileName);
}
```
## Conclusion
Et voila! En suivant ces étapes, vous pouvez facilement ajouter un filigrane avec un type de marge de page spécifique à vos documents PDF à l'aide de Groupdocs.Watermark pour .NET. Cela contribue non seulement à protéger vos documents, mais garantit également leur authenticité. Qu'il s'agisse de rapports confidentiels, de documents juridiques ou d'œuvres créatives, le filigrane est un moyen simple mais efficace de protéger votre contenu.
## FAQ
### Qu’est-ce que Groupdocs.Watermark pour .NET ?
Groupdocs.Watermark pour .NET est une bibliothèque puissante permettant d'ajouter des filigranes à divers formats de documents par programme. Il prend en charge les images, le texte et bien plus encore, permettant une personnalisation étendue.
### Puis-je utiliser cette méthode pour filigraner d’autres types de documents ?
Oui, Groupdocs.Watermark pour .NET prend en charge un large éventail de formats de documents, notamment Word, Excel, PowerPoint et les images. Le processus est similaire mais peut impliquer différentes options et classes.
### Comment puis-je obtenir un essai gratuit de Groupdocs.Watermark pour .NET ?
 Tu peux[Téléchargez un essai gratuit](https://releases.groupdocs.com/) depuis le site Web Groupdocs pour explorer les caractéristiques et fonctionnalités de la bibliothèque.
### Est-il possible de personnaliser l’apparence du filigrane ?
Absolument! Vous pouvez personnaliser la police, la taille, la couleur, l'opacité, l'alignement et d'autres propriétés du filigrane en fonction de vos besoins.
### Où puis-je obtenir de l’assistance pour Groupdocs.Watermark pour .NET ?
 Pour obtenir de l'aide, vous pouvez visiter le[Forum d'assistance sur les filigranes Groupdocs](https://forum.groupdocs.com/c/watermark/19) où vous pouvez poser des questions et obtenir de l'aide de la communauté et de l'équipe Groupdocs.