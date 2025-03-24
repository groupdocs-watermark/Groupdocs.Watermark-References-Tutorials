---
title: Supprimer le filigrane d'un PDF
linktitle: Supprimer le filigrane d'un PDF
second_title: API GroupDocs.Watermark .NET
description: Découvrez comment supprimer les filigranes des fichiers PDF à l'aide de GroupDocs.Watermark pour .NET. Étapes simples pour l’édition professionnelle de documents.
weight: 34
url: /fr/net/pdf-watermarking-attachments/remove-watermark-pdf/
---
## Introduction
À l’ère numérique d’aujourd’hui, la protection des documents sensibles avec des filigranes est une pratique courante. Cependant, il existe des cas où vous devrez peut-être supprimer les filigranes des fichiers PDF pour diverses raisons. Que vous modifiiez un document ou que vous ayez simplement besoin d'une version propre pour la présentation, GroupDocs.Watermark for .NET fournit une solution transparente pour supprimer les filigranes des fichiers PDF.
## Conditions préalables
Avant de commencer à supprimer les filigranes des fichiers PDF à l'aide de GroupDocs.Watermark pour .NET, assurez-vous que vous disposez des conditions préalables suivantes :
1.  GroupDocs.Watermark pour la bibliothèque .NET : téléchargez et installez la bibliothèque à partir de[ici](https://releases.groupdocs.com/Watermark/net/).
2. Environnement de développement : installez Visual Studio ou tout autre IDE compatible sur votre système.
3. Document avec filigrane : préparez un document PDF contenant le filigrane que vous souhaitez supprimer.

## Importation d'espaces de noms
Dans votre projet C#, commencez par importer les espaces de noms nécessaires :
```csharp
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Search;
using GroupDocs.Watermark.Search.SearchCriteria;
using System.IO;
using System;
```
## Étape 1 : Charger le document PDF
```csharp
string documentPath = "YourDocumentPath.pdf";
string outputDirectory = "YourOutputDirectory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
var loadOptions = new PdfLoadOptions();
```
Dans cette étape, spécifiez le chemin d'accès à votre document PDF et le répertoire dans lequel vous souhaitez enregistrer le fichier de sortie.
## Étape 2 : initialiser le filigrane et les critères de recherche
```csharp
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    ImageSearchCriteria imageSearchCriteria = new ImageDctHashSearchCriteria(Constants.LogoPng);
    TextSearchCriteria textSearchCriteria = new TextSearchCriteria("Company Name");
```
Initialisez l'objet Watermarker avec le chemin du document PDF et les options de chargement. Ensuite, définissez les critères de recherche pour le filigrane que vous souhaitez supprimer. Vous pouvez rechercher des filigranes basés sur des images ou du texte.
## Étape 3 : Rechercher et supprimer les filigranes
```csharp
    PdfContent pdfContent = watermarker.GetContent<PdfContent>();
    PossibleWatermarkCollection possibleWatermarks = pdfContent.Pages[0].Search(imageSearchCriteria.Or(textSearchCriteria));
    // Supprimer tous les filigranes trouvés
    for (int i = possibleWatermarks.Count - 1; i >= 0; i--)
    {
        possibleWatermarks.RemoveAt(i);
    }
    watermarker.Save(outputFileName);
}
```
Recherchez d'éventuels filigranes sur la première page du document PDF en fonction des critères de recherche définis. Ensuite, parcourez la collection de filigranes possibles et supprimez-les un par un. Enfin, enregistrez le document PDF modifié sans le filigrane.

## Conclusion
La suppression des filigranes des fichiers PDF est une tâche cruciale dans divers scénarios, de l'édition de documents à la préparation d'une présentation. Avec GroupDocs.Watermark pour .NET, vous pouvez facilement supprimer les filigranes des fichiers PDF à l'aide d'un simple code C#, garantissant ainsi que vos documents sont propres et professionnels.
## FAQ
### GroupDocs.Watermark pour .NET est-il compatible avec toutes les versions de Visual Studio ?
Oui, GroupDocs.Watermark pour .NET est compatible avec toutes les versions de Visual Studio, y compris Visual Studio 2019 et Visual Studio 2022.
### Puis-je supprimer plusieurs filigranes d’un seul document PDF à l’aide de GroupDocs.Watermark pour .NET ?
Oui, vous pouvez rechercher et supprimer plusieurs filigranes d'un seul document PDF en spécifiant des critères de recherche appropriés.
### GroupDocs.Watermark pour .NET prend-il en charge d'autres formats de documents que le PDF ?
Oui, GroupDocs.Watermark pour .NET prend en charge un large éventail de formats de documents, notamment les documents Word, les feuilles de calcul Excel, les présentations PowerPoint, etc.
### Existe-t-il une version d’essai disponible pour GroupDocs.Watermark pour .NET ?
 Oui, vous pouvez télécharger une version d'essai gratuite de GroupDocs.Watermark pour .NET à partir de[ici](https://releases.groupdocs.com/).
### Où puis-je trouver un support et une assistance supplémentaires pour GroupDocs.Watermark pour .NET ?
 Pour une assistance supplémentaire, vous pouvez visiter le forum GroupDocs.Watermark[ici](https://forum.groupdocs.com/c/watermark/19).