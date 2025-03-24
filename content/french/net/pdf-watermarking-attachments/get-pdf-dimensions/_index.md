---
title: Obtenir les dimensions PDF
linktitle: Obtenir les dimensions PDF
second_title: API GroupDocs.Watermark .NET
description: Protégez facilement vos documents à l'aide de Groupdocs.Watermark pour .NET. Ajoutez des filigranes, des tampons et des annotations sans effort.
weight: 26
url: /fr/net/pdf-watermarking-attachments/get-pdf-dimensions/
---

# Obtenir les dimensions PDF

## Introduction
À l’ère numérique d’aujourd’hui, la protection de vos documents est primordiale. Que vous soyez un professionnel des affaires, un juriste ou un artiste créatif, la protection de votre propriété intellectuelle est essentielle. Groupdocs.Watermark for .NET offre une solution robuste pour ajouter des filigranes, des tampons et des annotations à vos documents, garantissant ainsi leur sécurité et leur authenticité.
## Conditions préalables
Avant de plonger dans le monde de Groupdocs.Watermark pour .NET, assurez-vous d'avoir les conditions préalables suivantes en place :
1.  Installation de Groupdocs.Watermark pour .NET : Téléchargez et installez Groupdocs.Watermark pour .NET à partir du[lien de téléchargement](https://releases.groupdocs.com/Watermark/net/).
2.  Clé de licence (facultatif) : bien que Groupdocs.Watermark pour .NET propose un essai gratuit, vous pouvez opter pour une licence temporaire ou acheter une licence complète auprès de[ici](https://purchase.groupdocs.com/buy) pour des fonctionnalités étendues.
3. Familiarité avec C# : Une connaissance de base du langage de programmation C# est recommandée pour comprendre et mettre en œuvre les exemples fournis.
4. Document à protéger : préparez un exemple de document (par exemple, PDF, Word, Excel) sur votre ordinateur local pour pouvoir l'expérimenter.

## Importer des espaces de noms
Pour commencer à travailler avec Groupdocs.Watermark pour .NET, vous devez importer les espaces de noms nécessaires dans votre projet C#.
```csharp
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using System;
using System.IO;
```
### Étape 1 : déclarer les variables
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
### Étape 2 : Charger le document
```csharp
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
```
### Étape 3 : Obtenez le contenu PDF
```csharp
PdfContent pdfContent = watermarker.GetContent<PdfContent>();
```
### Étape 4 : Récupérer les dimensions
```csharp
Console.WriteLine(pdfContent.Pages[0].Width);
Console.WriteLine(pdfContent.Pages[0].Height);
```

## Conclusion
En conclusion, Groupdocs.Watermark for .NET offre une solution complète pour protéger vos documents contre toute utilisation et distribution non autorisées. En suivant les étapes décrites ci-dessus et en tirant parti de la puissance de Groupdocs.Watermark pour .NET, vous pouvez garantir la sécurité et l'intégrité de vos précieux actifs numériques.
## FAQ
### Puis-je utiliser Groupdocs.Watermark pour .NET gratuitement ?
Oui, Groupdocs.Watermark pour .NET propose une version d'essai gratuite à des fins d'évaluation. Cependant, pour des fonctionnalités étendues, vous pouvez envisager d'acheter une licence complète.
### Groupdocs.Watermark prend-il en charge plusieurs formats de documents ?
Oui, Groupdocs prend en charge un large éventail de formats de documents, notamment PDF, Word, Excel, PowerPoint, etc.
### Puis-je personnaliser les filigranes et les tampons avec Groupdocs.Watermark ?
Absolument! Groupdocs.Watermark fournit des options de personnalisation étendues pour les filigranes, les tampons et les annotations afin de répondre à vos besoins spécifiques.
### Un support technique est-il disponible pour les utilisateurs de Groupdocs.Watermark ?
 Oui, vous pouvez bénéficier d'une assistance technique et interagir avec la communauté Groupdocs via le[forum d'entraide](https://forum.groupdocs.com/c/watermark/19).
### Comment puis-je obtenir une licence temporaire pour Groupdocs.Watermark ?
 Vous pouvez obtenir une licence temporaire pour Groupdocs.Watermark auprès de[ici](https://purchase.groupdocs.com/temporary-license/).