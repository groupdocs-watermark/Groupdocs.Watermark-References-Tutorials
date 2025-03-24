---
title: Pixelliser un document PDF
linktitle: Pixelliser un document PDF
second_title: API GroupDocs.Watermark .NET
description: Découvrez comment pixelliser des documents PDF à l'aide de GroupDocs.Watermark pour .NET. Améliorez la sécurité des documents et leur attrait visuel sans effort.
weight: 27
url: /fr/net/pdf-watermarking-attachments/rasterize-pdf-document/
---
## Introduction
Dans le domaine de la gestion et de la manipulation de documents, GroupDocs.Watermark pour .NET se présente comme un outil puissant, offrant des fonctionnalités robustes pour ajouter, supprimer et rechercher des filigranes dans divers formats de documents. Qu'il s'agisse de protéger vos documents avec des mentions de droits d'auteur, d'ajouter des logos d'entreprise pour la marque ou simplement d'annoter des documents avec des tampons, GroupDocs.Watermark simplifie le processus grâce à son API intuitive et à son ensemble complet de fonctionnalités.
## Conditions préalables
Avant de plonger dans le monde du filigrane avec GroupDocs.Watermark pour .NET, assurez-vous d'avoir les conditions préalables suivantes en place :
### 1. Installez .NET Framework
Assurez-vous que le .NET Framework est installé sur votre ordinateur de développement. Vous pouvez le télécharger depuis le site Web de Microsoft ou utiliser votre gestionnaire de packages préféré.
#### Étape 1 : Téléchargez .NET Framework
Visitez la page de téléchargement de Microsoft .NET Framework.
#### Étape 2 : installer .NET Framework
Suivez les instructions d'installation fournies sur la page de téléchargement pour installer le .NET Framework sur votre système.
### 2. Obtenez la licence GroupDocs.Watermark
Pour utiliser toutes les capacités de GroupDocs.Watermark, vous avez besoin d'une licence valide. Vous pouvez soit acheter une licence, soit en obtenir une temporaire à des fins d'évaluation.
#### Étape 1 : Obtenez une licence
Visitez la page d'achat GroupDocs.Watermark.
#### Étape 2 : Achetez ou obtenez une licence temporaire
Choisissez l'option de licence appropriée en fonction de vos besoins : achetez une licence pour une utilisation continue ou acquérez une licence temporaire à des fins d'évaluation.

## Importer des espaces de noms
Avant de commencer à filigraner vos documents, assurez-vous d'importer les espaces de noms nécessaires pour accéder de manière transparente aux fonctionnalités de GroupDocs.
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```

Maintenant que tout est configuré, passons à la rastérisation d'un document PDF à l'aide de GroupDocs.Watermark pour .NET. La rastérisation convertit chaque page du document PDF en un format d'image raster, tel que PNG.
## Étape 1 : initialiser les variables
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
Assurez-vous de remplacer « Votre chemin de document » et « Votre répertoire de documents » par le chemin réel de votre document PDF et le répertoire de sortie souhaité, respectivement.
## Étape 2 : Charger le document et ajouter un filigrane
```csharp
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Initialiser le filigrane d'une image ou d'un texte
    TextWatermark watermark = new TextWatermark("Do not copy", new Font("Arial", 8));
    watermark.HorizontalAlignment = HorizontalAlignment.Center;
    watermark.VerticalAlignment = VerticalAlignment.Center;
    watermark.RotateAngle = 45;
    watermark.SizingType = SizingType.ScaleToParentDimensions;
    watermark.ScaleFactor = 1;
    watermark.Opacity = 0.5;
    // Ajoutez d'abord un filigrane de n'importe quel type
    watermarker.Add(watermark);
    PdfContent pdfContent = watermarker.GetContent<PdfContent>();
    // Pixelliser toutes les pages
    pdfContent.Rasterize(100, 100, PdfImageConversionFormat.Png);
    // Le contenu de toutes les pages est remplacé par des images raster
    watermarker.Save(outputFileName);
}
```
Dans cette étape, nous chargeons le document PDF et initialisons un filigrane de texte avec des propriétés spécifiées telles que le texte, la police, l'alignement, l'angle de rotation, le type de dimensionnement, le facteur d'échelle et l'opacité. Ensuite, nous ajoutons le filigrane au document. Ensuite, nous récupérons le contenu du document PDF et rastérisons toutes les pages au format PNG avec une résolution de 100 DPI. Enfin, nous enregistrons le document modifié avec le contenu rastérisé.

## Conclusion
GroupDocs.Watermark pour .NET offre une solution complète pour ajouter facilement des filigranes à divers formats de documents. En suivant les étapes décrites dans ce didacticiel, vous pouvez rastériser efficacement les documents PDF et améliorer leur sécurité et leur attrait visuel.
## FAQ
### GroupDocs.Watermark est-il compatible avec d'autres formats de documents que le PDF ?
Oui, GroupDocs.Watermark prend en charge un large éventail de formats de documents, notamment Microsoft Word, Excel, PowerPoint, Visio, Outlook et bien d'autres.
### Puis-je personnaliser l’apparence des filigranes ajoutés à l’aide de GroupDocs.Watermark ?
Absolument! GroupDocs.Watermark fournit des options étendues pour personnaliser les propriétés du filigrane telles que le texte, la police, la couleur, la taille, l'opacité, la rotation et la position.
### GroupDocs.Watermark offre-t-il une prise en charge du traitement par lots ?
Oui, vous pouvez facilement traiter plusieurs documents en mode batch à l'aide de GroupDocs, économisant ainsi du temps et des efforts lors du filigrane de grands ensembles de fichiers.
### Existe-t-il une version d’essai disponible pour GroupDocs.Watermark ?
Oui, vous pouvez télécharger une version d'essai gratuite de GroupDocs.Watermark à partir du site Web pour évaluer ses fonctionnalités avant de faire un achat.
### Comment puis-je obtenir de l'aide si je rencontre des problèmes ou si j'ai des questions sur GroupDocs.Watermark ?
Vous pouvez visiter le forum GroupDocs.Watermark pour demander l'aide de la communauté ou contacter l'équipe d'assistance GroupDocs pour obtenir de l'aide.