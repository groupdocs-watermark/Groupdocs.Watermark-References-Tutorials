---
title: Remplacer le texte de forme par du texte formaté dans Word Docs
linktitle: Remplacer le texte de forme par du texte formaté dans Word Docs
second_title: API GroupDocs.Watermark .NET
description: Découvrez comment remplacer le texte de forme par du texte formaté dans des documents Word à l'aide de GroupDocs.Watermark pour .NET. Vos capacités d’édition de documents sans effort.
weight: 34
url: /fr/net/word-processing-watermarkings/replace-shape-text-formatted-text-word-docs/
type: docs
---
# Remplacer le texte de forme par du texte formaté dans Word Docs

## Introduction
Dans ce didacticiel, nous vous guiderons tout au long du processus de remplacement du texte de forme par du texte formaté dans les documents Word à l'aide de GroupDocs.Watermark pour .NET. Cette bibliothèque fournit des fonctionnalités puissantes pour travailler avec des filigranes, notamment le remplacement de texte dans des formes.
## Conditions préalables
Avant de commencer, assurez-vous de disposer des prérequis suivants :
1.  GroupDocs.Watermark pour .NET : assurez-vous d'avoir installé et configuré GroupDocs.Watermark pour .NET. Vous pouvez le télécharger depuis[ici](https://releases.groupdocs.com/Watermark/net/).
2. Chemin du document : vous devriez avoir le chemin d’accès au document Word dans lequel vous souhaitez remplacer le texte.

## Importer des espaces de noms
Avant d'écrire le code, importez les espaces de noms nécessaires :
```csharp
using GroupDocs.Watermark.Contents.WordProcessing;
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Étape 1 : Charger le document
 Chargez le document Word à l'aide du`Watermarker` classe:
```csharp
string documentPath = "Your Document Path";
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Votre code continue ici...
}
```
## Étape 2 : obtenir du contenu et remplacer le texte
Une fois le document chargé, récupérez le contenu et remplacez le texte dans les formes :
```csharp
WordProcessingContent content = watermarker.GetContent<WordProcessingContent>();
foreach (WordProcessingShape shape in content.Sections[0].Shapes)
{
    if (shape.Text.Contains("Some text"))
    {
        shape.FormattedTextFragments.Clear();
        shape.FormattedTextFragments.Add("Another text", new Font("Calibri", 19, FontStyle.Bold), Color.Red, Color.Aqua);
    }
}
```
## Étape 3 : Enregistrez le document
Après avoir remplacé le texte, enregistrez le document modifié :
```csharp
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
watermarker.Save(outputFileName);
```

## Conclusion
Le remplacement du texte de forme par du texte formaté dans les documents Word est facilité avec GroupDocs pour .NET. En suivant les étapes décrites dans ce didacticiel, vous pouvez gérer et manipuler efficacement le texte de vos documents.

## FAQ
### Puis-je remplacer du texte dans d’autres types de documents à l’aide de GroupDocs.Watermark pour .NET ?
Oui, GroupDocs prend en charge divers formats de documents tels que PDF, Excel, PowerPoint, etc.
### GroupDocs.Watermark est-il compatible avec .NET Core ?
Oui, GroupDocs.Watermark prend en charge à la fois .NET Framework et .NET Core.
### GroupDocs.Watermark prend-il en charge l'ajout d'images sous forme de filigranes ?
Absolument, GroupDocs.Watermark vous permet d'ajouter des filigranes de texte et d'image à vos documents.
### Puis-je personnaliser l’apparence des filigranes ajoutés à l’aide de GroupDocs.Watermark ?
Oui, vous avez un contrôle total sur l’apparence, la position et d’autres propriétés des filigranes.
### Existe-t-il une version d’essai disponible pour GroupDocs.Watermark pour .NET ?
 Oui, vous pouvez télécharger un essai gratuit à partir de[ici](https://releases.groupdocs.com/).