---
title: Ajouter un filigrane d'annotation pour impression uniquement au PDF
linktitle: Ajouter un filigrane d'annotation pour impression uniquement au PDF
second_title: API GroupDocs.Watermark .NET
description: Découvrez comment ajouter des filigranes d'annotation pour impression uniquement aux PDF à l'aide de GroupDocs.Watermark for .NET. Améliorez la sécurité des documents et l’image de marque sans effort.
weight: 13
url: /fr/net/pdf-watermarking-attachments/add-print-only-annotation-watermark-pdf/
---

# Ajouter un filigrane d'annotation pour impression uniquement au PDF

## Introduction
Dans ce didacticiel, nous aborderons le processus d'ajout d'un filigrane d'annotation pour impression uniquement à un PDF à l'aide de GroupDocs.Watermark pour .NET. Le filigrane des documents est un aspect crucial de la sécurité des documents et de l'image de marque, et GroupDocs.Watermark fournit une solution transparente aux développeurs .NET pour y parvenir.
## Conditions préalables
Avant de commencer, assurez-vous de disposer des prérequis suivants :
- Compréhension de base du langage de programmation C#.
- Visual Studio installé sur votre ordinateur.
- Bibliothèque GroupDocs.Watermark pour .NET installée dans votre projet.

## Importer des espaces de noms
Pour commencer, assurez-vous d'importer les espaces de noms nécessaires :
```csharp
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Étape 1 : Charger le document
 Tout d'abord, vous devez charger le document PDF que vous souhaitez filigraner. Remplacer`"Your Document Path"` avec le chemin d'accès à votre fichier PDF et`"Your Document Directory"` avec le répertoire dans lequel vous souhaitez enregistrer le fichier de sortie.
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Le code de filigrane sera ajouté ici
}
```
## Étape 2 : ajouter un filigrane
Ensuite, créez un objet filigrane de texte avec le texte et la police souhaités. Ensemble`isPrintOnly` à`true` pour garantir que le filigrane n'est visible que lorsque le document est imprimé, et non en mode d'affichage.
```csharp
TextWatermark textWatermark = new TextWatermark("This is a print only test watermark. It won't appear in view mode.", new Font("Arial", 8));
bool isPrintOnly = true;
```
## Étape 3 : Configurer les options de filigrane
Définissez les options pour le filigrane, telles que l'index de la page où le filigrane doit être ajouté et en le spécifiant comme annotation à imprimer uniquement.
```csharp
PdfAnnotationWatermarkOptions options = new PdfAnnotationWatermarkOptions();
options.PageIndex = 0;
options.PrintOnly = isPrintOnly;
```
## Étape 4 : appliquer un filigrane
Ajoutez le filigrane au document en utilisant les options spécifiées et enregistrez le fichier de sortie.
```csharp
watermarker.Add(textWatermark, options);
watermarker.Save(outputFileName);
```

## Conclusion
Dans ce didacticiel, nous avons appris à ajouter un filigrane d'annotation pour impression uniquement à un document PDF à l'aide de GroupDocs.Watermark pour .NET. Cela permet aux développeurs d’améliorer facilement la sécurité des documents et l’image de marque.
## FAQ
### GroupDocs.Watermark est-il compatible avec d'autres formats de documents que le PDF ?
Oui, GroupDocs prend en charge divers formats de documents tels que Word, Excel, PowerPoint et les images.
### Puis-je personnaliser l’apparence du filigrane ?
Certes, GroupDocs.Watermark fournit de nombreuses options pour personnaliser le texte, la police, la couleur, la taille et le positionnement du filigrane.
### GroupDocs.Watermark offre-t-il des capacités de traitement par lots ?
Absolument, les développeurs peuvent filigraner plusieurs documents simultanément à l'aide des fonctionnalités de traitement par lots.
### Existe-t-il une version d’essai disponible pour GroupDocs.Watermark ?
Oui, vous pouvez accéder à une version d'essai gratuite de GroupDocs.Watermark à partir du lien fourni.
### Comment puis-je obtenir une assistance technique pour GroupDocs.Watermark ?
Vous pouvez demander une assistance technique sur le forum GroupDocs.Watermark disponible sur le lien d'assistance fourni.