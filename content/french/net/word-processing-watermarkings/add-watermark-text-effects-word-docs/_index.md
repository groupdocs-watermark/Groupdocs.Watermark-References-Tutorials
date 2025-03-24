---
title: Ajouter un filigrane avec des effets de texte dans Word Docs
linktitle: Ajouter un filigrane avec des effets de texte dans Word Docs
second_title: API GroupDocs.Watermark .NET
description: Découvrez comment ajouter des filigranes personnalisés avec des effets de texte aux documents Word à l'aide de GroupDocs.Watermark pour .NET. Documentez la sécurité et l’attrait visuel sans effort.
weight: 21
url: /fr/net/word-processing-watermarkings/add-watermark-text-effects-word-docs/
---
## Introduction
Dans ce didacticiel, nous verrons comment ajouter un filigrane avec des effets de texte aux documents Word à l'aide de GroupDocs.Watermark pour .NET. En suivant ces instructions étape par étape, vous pourrez améliorer vos documents avec des filigranes personnalisés incluant divers effets de texte.
## Conditions préalables
Avant de commencer, assurez-vous d'avoir les éléments suivants :
1.  GroupDocs.Watermark pour .NET : téléchargez et installez la bibliothèque à partir du[site web](https://releases.groupdocs.com/Watermark/net/).
2. Chemin du document : connaissez le chemin du document Word auquel vous souhaitez ajouter le filigrane.
3. Répertoire de sortie : disposez d'un répertoire dans lequel vous souhaitez enregistrer le document modifié.

## Importer des espaces de noms
Assurez-vous d'importer les espaces de noms nécessaires pour accéder aux classes et méthodes requises :
```csharp
using GroupDocs.Watermark.Contents;
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Étape 1 : Charger le document
Chargez le document Word sur lequel vous souhaitez ajouter le filigrane.
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Le code pour l'ajout d'un filigrane va ici
}
```
## Étape 2 : Ajouter un filigrane avec des effets de texte
Créez un filigrane de texte avec le texte et la police souhaités, puis définissez les effets de texte tels que le format de ligne.
```csharp
TextWatermark watermark = new TextWatermark("Test watermark", new Font("Arial", 19));
WordProcessingTextEffects effects = new WordProcessingTextEffects();
effects.LineFormat.Enabled = true;
effects.LineFormat.Color = Color.Red;
effects.LineFormat.DashStyle = OfficeDashStyle.DashDotDot;
effects.LineFormat.LineStyle = OfficeLineStyle.Triple;
effects.LineFormat.Weight = 1;
```
## Étape 3 : Personnaliser les options de filigrane
Définissez les options de la section du filigrane, telles que les effets de texte, et attribuez-les au filigrane.
```csharp
WordProcessingWatermarkSectionOptions options = new WordProcessingWatermarkSectionOptions();
options.Effects = effects;
watermarker.Add(watermark, options);
```
## Étape 4 : Enregistrez le document
Enregistrez le document modifié avec le filigrane ajouté.
```csharp
watermarker.Save(outputFileName);
```

## Conclusion
L'ajout de filigranes avec des effets de texte aux documents Word peut améliorer considérablement leur attrait visuel et leur protection. Avec GroupDocs.Watermark pour .NET, ce processus devient rationalisé et personnalisable, vous permettant de créer efficacement des documents d'aspect professionnel.
## FAQ
### Puis-je personnaliser la police et la taille du texte du filigrane ?
Oui, vous pouvez spécifier la police et la taille lors de la création de l'objet TextWatermark.
### Est-il possible d'ajouter plusieurs filigranes à un seul document ?
Absolument, GroupDocs.Watermark pour .NET prend en charge l'ajout de plusieurs filigranes avec différents paramètres à un seul document.
### GroupDocs.Watermark prend-il en charge d’autres formats de documents que Word ?
Oui, il prend en charge un large éventail de formats de documents, notamment PDF, Excel, PowerPoint, etc.
### Puis-je supprimer un filigrane une fois qu'il est ajouté à un document ?
Oui, la bibliothèque propose des méthodes pour supprimer facilement les filigranes des documents.
### Existe-t-il une version d'essai disponible à des fins de test ?
 Oui, vous pouvez télécharger une version d'essai gratuite à partir de[ici](https://releases.groupdocs.com/).