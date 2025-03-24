---
title: Ajouter un filigrane verrouillé à des pages spécifiques dans Word Docs
linktitle: Ajouter un filigrane verrouillé à des pages spécifiques dans Word Docs
second_title: API GroupDocs.Watermark .NET
description: Découvrez comment ajouter un filigrane verrouillé à des pages spécifiques dans des documents Word à l'aide de GroupDocs.Watermark pour .NET grâce à notre guide étape par étape simple.
weight: 12
url: /fr/net/word-processing-watermarkings/add-locked-watermark-specific-pages-word-docs/
---

# Ajouter un filigrane verrouillé à des pages spécifiques dans Word Docs

## Introduction
Cherchez-vous à ajouter un filigrane à des pages spécifiques de vos documents Word, mais souhaitez-vous qu'il soit verrouillé afin qu'il ne puisse pas être facilement supprimé ou modifié ? Vous êtes au bon endroit ! Dans ce didacticiel, nous vous guiderons tout au long du processus d'ajout d'un filigrane verrouillé à des pages spécifiques dans des documents Word à l'aide de GroupDocs.Watermark pour .NET. Cette puissante bibliothèque facilite l'application, la gestion et la personnalisation des filigranes sur une variété de types de documents. Que vous soyez un développeur ou simplement quelqu'un qui a besoin de sécuriser ses documents, ce guide vous guidera pas à pas de manière simple.
## Conditions préalables
Avant de plonger dans le didacticiel, assurons-nous que vous disposez de tout ce dont vous avez besoin :
1.  GroupDocs.Watermark pour .NET : vous pouvez[télécharger](https://releases.groupdocs.com/Watermark/net/) la dernière version.
2. Environnement de développement : un IDE comme Visual Studio.
3. Connaissance de base de C# : Une connaissance de la programmation C# sera utile.
4. Document à filigraner : un document Word (.docx ou .doc) auquel vous souhaitez ajouter un filigrane.
## Importer des espaces de noms
Tout d’abord, vous devez importer les espaces de noms nécessaires dans votre projet C#. Ces espaces de noms donnent accès aux classes et méthodes requises pour travailler avec GroupDocs.Watermark.
```csharp
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
Maintenant que nous avons couvert les conditions préalables et importé les espaces de noms nécessaires, décomposons le processus étape par étape.
## Étape 1 : Charger le document Word
 Pour commencer, vous devez charger le document Word auquel vous souhaitez ajouter un filigrane. Cela peut être fait en utilisant le`Watermarker` classe avec`WordProcessingLoadOptions`.
```csharp
string documentPath = "Your Document Path";
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Passer aux étapes suivantes
}
```
## Étape 2 : Créer le filigrane de texte
Ensuite, créez un filigrane de texte. Vous pouvez personnaliser le texte, la police, la couleur et d'autres propriétés en fonction de vos besoins.
```csharp
TextWatermark watermark = new TextWatermark("Watermark text", new Font("Arial", 19));
watermark.ForegroundColor = Color.Red;
```
## Étape 3 : Configurer les options de filigrane
 Pour appliquer le filigrane à des pages spécifiques et le verrouiller, configurez le`WordProcessingWatermarkPagesOptions`Ici, vous spécifiez les numéros de page où le filigrane doit apparaître et définissez les options de verrouillage.
```csharp
WordProcessingWatermarkPagesOptions options = new WordProcessingWatermarkPagesOptions();
options.PageNumbers = new int[] { 1, 3 }; // Préciser les pages
options.IsLocked = true; // Verrouiller le filigrane
options.LockType = WordProcessingLockType.AllowOnlyComments; // Définir le type de verrouillage
// Protéger avec un mot de passe
// options.Mot de passe = "7654321";
```
## Étape 4 : ajouter le filigrane au document
Une fois votre filigrane et vos options configurés, vous pouvez maintenant ajouter le filigrane au document.
```csharp
watermarker.Add(watermark, options);
```
## Étape 5 : Enregistrez le document
Enfin, enregistrez le document avec le filigrane appliqué. Choisissez un chemin de sortie approprié et enregistrez le fichier.
```csharp
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
watermarker.Save(outputFileName);
```
## Conclusion
Toutes nos félicitations! Vous avez ajouté avec succès un filigrane verrouillé à des pages spécifiques d'un document Word à l'aide de GroupDocs.Watermark pour .NET. Ce didacticiel a couvert toutes les étapes essentielles, depuis le chargement du document jusqu'à l'enregistrement du fichier filigrané. En suivant ces étapes, vous pouvez vous assurer que vos documents sont filigranés en toute sécurité, protégeant ainsi votre contenu contre toute modification et utilisation non autorisées.
 Pour plus d'informations, vous pouvez vous référer au[Documentation GroupDocs.Watermark](https://tutorials.groupdocs.com/Watermark/net/) . Si vous avez des questions ou avez besoin d'aide supplémentaire, n'hésitez pas à visiter le[forum d'entraide](https://forum.groupdocs.com/c/watermark/19).
## FAQ
### Qu’est-ce que GroupDocs.Watermark pour .NET ?
GroupDocs.Watermark pour .NET est une bibliothèque puissante qui permet aux développeurs d'ajouter des filigranes à différents types de documents, notamment Word, PDF, Excel, etc.
### Puis-je appliquer des filigranes à plusieurs pages d’un document ?
 Oui, vous pouvez spécifier plusieurs numéros de page dans le`PageNumbers` tableau pour appliquer des filigranes à plusieurs pages.
### Comment protéger un filigrane avec un mot de passe ?
 Vous pouvez protéger un filigrane avec un mot de passe en définissant le`Password` propriété dans le`WordProcessingWatermarkPagesOptions`.
### Est-il possible de personnaliser l’apparence du filigrane ?
Absolument! Vous pouvez personnaliser le texte, la police, la couleur, la taille et d'autres propriétés du filigrane en fonction de vos besoins.
### Où puis-je obtenir une licence temporaire pour GroupDocs.Watermark ?
 Vous pouvez obtenir une licence temporaire auprès de[ici](https://purchase.groupdocs.com/temporary-license/).