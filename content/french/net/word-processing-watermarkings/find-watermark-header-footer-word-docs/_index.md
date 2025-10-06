---
title: Rechercher un filigrane dans l'en-tête/pied de page dans Word Docs
linktitle: Rechercher un filigrane dans l'en-tête/pied de page dans Word Docs
second_title: API GroupDocs.Watermark .NET
description: Découvrez comment rechercher et supprimer efficacement les filigranes des documents Word à l'aide de GroupDocs Watermark for .NET, garantissant ainsi l'intégrité et le professionnalisme des documents.
weight: 22
url: /fr/net/word-processing-watermarkings/find-watermark-header-footer-word-docs/
type: docs
---
# Rechercher un filigrane dans l'en-tête/pied de page dans Word Docs

## Introduction
Dans le monde de la gestion et de la protection des documents, le filigrane joue un rôle central. Que ce soit à des fins de branding, de protection des droits d'auteur ou de suivi de documents, l'ajout de filigranes à vos documents est essentiel. Cependant, trouver et supprimer efficacement les filigranes, en particulier dans les grands ensembles de documents, peut s'avérer une tâche ardue. C'est là que GroupDocs.Watermark pour .NET entre en jeu. Dans ce didacticiel, nous verrons comment rechercher des filigranes dans les en-têtes et les pieds de page des documents Word à l'aide de GroupDocs.Watermark pour .NET, en décomposant chaque étape pour garantir une compréhension globale.
## Conditions préalables
Avant de plonger dans le didacticiel, assurez-vous que les conditions préalables suivantes sont remplies :
1. GroupDocs.Watermark pour .NET : assurez-vous que la bibliothèque GroupDocs.Watermark pour .NET est installée et configurée dans votre environnement de développement. Vous pouvez télécharger la bibliothèque depuis[ici](https://releases.groupdocs.com/Watermark/net/).
2. Accès aux documents Word : accédez aux documents Word contenant des filigranes que vous souhaitez manipuler.
3. Connaissance de base de C# : Familiarisez-vous avec les bases du langage de programmation C#, car ce didacticiel impliquera des extraits de code C#.
## Importer des espaces de noms
Avant de commencer avec le code, importez les espaces de noms nécessaires :
```csharp
using GroupDocs.Watermark.Contents;
using GroupDocs.Watermark.Contents.WordProcessing;
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Search;
using GroupDocs.Watermark.Search.SearchCriteria;
using System.IO;
using System;
```
## Étape 1 : Définir le chemin du document et le nom du fichier de sortie
Tout d'abord, définissez le chemin du document contenant le filigrane et le nom du fichier de sortie où le document modifié sera enregistré.
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
```
## Étape 2 : initialiser le filigrane
 Initialisez le`Watermarker` objet avec le chemin du document et les options de chargement.
```csharp
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Le code pour la manipulation du filigrane ira ici
}
```
## Étape 3 : Définir les critères de recherche
Définissez les critères de recherche pour trouver le filigrane. Cela peut être basé sur une image ou un texte.
```csharp
ImageSearchCriteria imageSearchCriteria = new ImageDctHashSearchCriteria(Constants.LogoPng);
TextSearchCriteria textSearchCriteria = new TextSearchCriteria("Company Name");
```
## Étape 4 : Rechercher des filigranes
Recherchez des filigranes dans l'en-tête principal du document à l'aide des critères de recherche définis.
```csharp
WordProcessingContent content = watermarker.GetContent<WordProcessingContent>();
PossibleWatermarkCollection possibleWatermarks = content.Sections[0]
                                                        .HeadersFooters[OfficeHeaderFooterType.HeaderPrimary]
                                                        .Search(textSearchCriteria.Or(imageSearchCriteria));
```
## Étape 5 : Supprimer les filigranes
Supprimez tous les filigranes trouvés du document.
```csharp
for (int i = possibleWatermarks.Count - 1; i >= 0; i--)
{
    possibleWatermarks.RemoveAt(i);
}
```
## Étape 6 : Enregistrer le document
Enregistrez le document modifié avec les filigranes supprimés.
```csharp
watermarker.Save(outputFileName);
```

## Conclusion
GroupDocs.Watermark pour .NET fournit une solution robuste pour rechercher et supprimer les filigranes des documents Word. En suivant les étapes décrites dans ce didacticiel, vous pouvez localiser et éliminer efficacement les filigranes des en-têtes et des pieds de page, garantissant ainsi l'intégrité et le professionnalisme de vos documents.
## FAQ
### GroupDocs.Watermark est-il compatible avec d’autres formats de documents ?
Oui, GroupDocs.Watermark prend en charge un large éventail de formats de documents, notamment Word, Excel, PowerPoint, PDF, etc.
### Puis-je personnaliser les critères de recherche des filigranes ?
Absolument, GroupDocs.Watermark propose des critères de recherche flexibles, vous permettant de rechercher des filigranes en fonction de divers paramètres tels que les propriétés du texte, de l'image, de la forme ou de l'objet.
### GroupDocs.Watermark préserve-t-il la mise en forme originale des documents ?
Oui, GroupDocs.Watermark garantit que le formatage original des documents reste intact tout en supprimant les filigranes, préservant ainsi l'esthétique et la mise en page du document.
### GroupDocs.Watermark est-il adapté au traitement par lots de documents ?
Certes, GroupDocs.Watermark fournit des API pour le traitement par lots, vous permettant de gérer facilement plusieurs documents simultanément.
### Où puis-je demander de l’aide ou du support pour GroupDocs.Watermark ?
 Pour toute question ou assistance concernant GroupDocs.Watermark, vous pouvez visiter le[Forum GroupDocs.Watermark](https://forum.groupdocs.com/c/watermark/19) ou contactez l’équipe d’assistance.