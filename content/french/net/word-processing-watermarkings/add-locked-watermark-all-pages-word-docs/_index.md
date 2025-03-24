---
title: Ajouter un filigrane verrouillé à toutes les pages dans Word Docs
linktitle: Ajouter un filigrane verrouillé à toutes les pages dans Word Docs
second_title: API GroupDocs.Watermark .NET
description: Sécurisez vos documents en ajoutant des filigranes verrouillés à l'aide de Groupdocs.Watermark pour .NET. Suivez notre guide étape par étape pour une mise en œuvre facile.
weight: 11
url: /fr/net/word-processing-watermarkings/add-locked-watermark-all-pages-word-docs/
---
## Introduction
L'ajout de filigranes à vos documents est une étape essentielle pour sécuriser et personnaliser votre contenu. Que vous souhaitiez empêcher une utilisation non autorisée ou simplement ajouter une touche professionnelle, les filigranes peuvent servir à plusieurs fins. Dans ce didacticiel, nous vous guiderons tout au long du processus d'ajout d'un filigrane verrouillé à toutes les pages d'un document Word à l'aide de Groupdocs.Watermark pour .NET.
## Conditions préalables
Avant de plonger dans le guide étape par étape, assurons-nous que vous disposez de tout ce dont vous avez besoin :
1. Groupdocs.Watermark pour .NET : téléchargez la dernière version à partir de[ici](https://releases.groupdocs.com/Watermark/net/).
2. .NET Framework : assurez-vous que .NET Framework est installé sur votre ordinateur.
3. Environnement de développement : un environnement de développement comme Visual Studio.
4.  Licence : Vous pouvez opter pour une[essai gratuit](https://releases.groupdocs.com/) ou acheter un[permis temporaire](https://purchase.groupdocs.com/temporary-license/).
## Importer des espaces de noms
Tout d’abord, vous devez importer les espaces de noms nécessaires dans votre projet. Ceux-ci sont indispensables pour accéder aux classes et méthodes fournies par Groupdocs.Watermark.
```csharp
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Étape 1 : Configurez votre projet

Ouvrez votre environnement de développement et créez un nouveau projet .NET. Il peut s'agir d'une application console ou de tout autre type adapté à vos besoins.

Vous devez ajouter le package Groupdocs.Watermark à votre projet. Cela peut être fait via NuGet Package Manager. Exécutez la commande suivante dans la console du gestionnaire de packages NuGet :
```sh
Install-Package GroupDocs.Watermark
```
## Étape 2 : Charger le document Word
### Définir le chemin du document
Spécifiez le chemin d'accès à votre document Word. Ce sera le document dans lequel vous souhaitez ajouter le filigrane.
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
```
### Définir les options de chargement
 Créer une instance de`WordProcessingLoadOptions` pour charger votre document Word avec des options spécifiques.
```csharp
var loadOptions = new WordProcessingLoadOptions();
```
## Étape 3 : Créer le filigrane
### Initialiser le filigrane
 En utilisant le`Watermarker`classe, chargez le document avec les options de chargement spécifiées.
```csharp
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // D'autres étapes seront à l'intérieur de ce bloc using
}
```
### Définir les propriétés du filigrane
 Créer un`TextWatermark` exemple avec le texte, la police et la couleur souhaités.
```csharp
TextWatermark watermark = new TextWatermark("Watermark text", new Font("Arial", 19));
watermark.ForegroundColor = Color.Red;
```
## Étape 4 : appliquer un filigrane à toutes les pages
### Définir les options de filigrane
 Définir`WordProcessingWatermarkPagesOptions` et réglez le`IsLocked` propriété à true pour verrouiller le filigrane. Cela garantit que le filigrane ne peut pas être supprimé facilement.
```csharp
WordProcessingWatermarkPagesOptions options = new WordProcessingWatermarkPagesOptions();
options.IsLocked = true;
options.LockType = WordProcessingLockType.AllowOnlyFormFields;
```
### Facultatif : ajouter une protection par mot de passe
Si vous souhaitez ajouter une couche de sécurité supplémentaire, vous pouvez définir un mot de passe pour le filigrane.
```csharp
// Protéger avec un mot de passe
// options.Mot de passe = "7654321";
```
### Ajouter le filigrane
 Utilisez le`Add` méthode du`Watermarker` classe pour ajouter le filigrane au document avec les options spécifiées.
```csharp
watermarker.Add(watermark, options);
```
## Étape 5 : Enregistrez le document
Enfin, enregistrez le document modifié dans le fichier de sortie spécifié.
```csharp
watermarker.Save(outputFileName);
```

## Conclusion
En suivant ces étapes, vous pouvez facilement ajouter un filigrane verrouillé à toutes les pages de vos documents Word à l'aide de Groupdocs.Watermark pour .NET. Cela aide non seulement à protéger vos documents contre toute utilisation non autorisée, mais ajoute également une touche professionnelle à votre contenu. Groupdocs.Watermark offre une solution complète pour les besoins de filigrane, garantissant que vos documents restent sécurisés et marqués.
## FAQ
### Puis-je utiliser une image comme filigrane au lieu du texte ?
 Oui, Groupdocs prend en charge les filigranes de texte et d'image. Vous pouvez remplacer`TextWatermark` avec`ImageWatermark` et précisez votre image.
### Est-il possible de personnaliser la position du filigrane ?
 Absolument! Vous pouvez définir la position du filigrane à l'aide de propriétés telles que`HorizontalAlignment` et`VerticalAlignment`.
### Puis-je appliquer différents filigranes à différentes pages du document ?
 Oui, vous pouvez personnaliser les filigranes pour des pages spécifiques à l'aide de l'outil`PageIndex` propriété dans le`WordProcessingWatermarkPagesOptions`.
### Groupdocs.Watermark prend-il en charge d’autres formats de documents que Word ?
Oui, Groupdocs prend en charge divers formats, notamment PDF, Excel, PowerPoint, etc.
### Quelle est la configuration système requise pour utiliser Groupdocs.Watermark ?
Vous avez besoin d'un système sur lequel .NET Framework est installé et d'un environnement de développement tel que Visual Studio.