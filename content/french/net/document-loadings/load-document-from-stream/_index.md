---
title: Charger un document à partir d'un flux
linktitle: Charger un document à partir d'un flux
second_title: API GroupDocs.Watermark .NET
description: Découvrez comment ajouter des filigranes aux documents à l'aide de GroupDocs.Watermark pour .NET avec ce guide. Parfait pour les développeurs cherchant à améliorer la sécurité des documents.
weight: 11
url: /fr/net/document-loadings/load-document-from-stream/
---

# Charger un document à partir d'un flux

## Introduction
Cherchez-vous à ajouter des filigranes à vos documents de manière transparente à l’aide de .NET ? Cherchez pas plus loin! GroupDocs.Watermark for .NET est une bibliothèque puissante et facile à utiliser qui vous permet de gérer les filigranes dans différents formats de documents. Que vous travailliez avec des PDF, des documents Word ou des images, cet outil est là pour vous. Dans ce didacticiel, nous vous guiderons pas à pas tout au long du processus de chargement d'un document à partir d'un flux et d'ajout d'un filigrane. Alors, allons-y !
## Conditions préalables
Avant de commencer, assurez-vous d'avoir la configuration suivante :
1. Visual Studio : toute version récente de Visual Studio fonctionnera correctement.
2. .NET Framework : assurez-vous que .NET Framework 4.0 ou supérieur est installé.
3.  GroupDocs.Watermark pour .NET : vous pouvez le télécharger depuis[ici](https://releases.groupdocs.com/Watermark/net/).
4. Connaissance de base de C# : une connaissance du C# et des concepts de programmation orientée objet sera utile.

## Importer des espaces de noms
Pour utiliser GroupDocs.Watermark dans votre projet, vous devrez importer les espaces de noms nécessaires. Cela vous permettra d'accéder aux fonctionnalités de la bibliothèque sans aucun problème.
```csharp
using System;
using System.IO;
using GroupDocs.Watermark.Watermarks;
```
## Étape 1 : Configuration de votre projet
Tout d’abord, vous devez configurer votre projet dans Visual Studio. Voici comment procéder :
1. Créer un nouveau projet : ouvrez Visual Studio et créez un nouveau projet d'application console C#.
2.  Installer GroupDocs.Watermark : installez la bibliothèque GroupDocs.Watermark via NuGet Package Manager. Recherchez simplement`GroupDocs.Watermark` et installez-le.
## Étape 2 : Définir les chemins des documents
Ensuite, vous devez définir les chemins de votre document et le fichier de sortie dans lequel le document filigrané sera enregistré.
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
```
 Remplacer`"Your Document Path"` avec le chemin réel du document que vous souhaitez filigraner et`"Your Document Directory"` avec le répertoire dans lequel vous souhaitez enregistrer le document filigrané.
## Étape 3 : Charger le document à partir d'un flux
Maintenant, chargeons le document à partir d'un flux. Cela implique d'ouvrir le document sous forme de flux, puis d'utiliser le`Watermarker` classe de la bibliothèque GroupDocs.Watermark pour le gérer.
```csharp
using (Stream document = File.OpenRead(documentPath))
using (Watermarker watermarker = new Watermarker(document))
{
    // Votre code pour gérer les filigranes ira ici
}
```
 Cet extrait de code garantit que le document est ouvert sous forme de flux et que le`Watermarker` la classe est initialisée avec ce flux. Le`using` Les déclarations garantissent que les ressources sont correctement éliminées après utilisation.
## Étape 4 : Créer et ajouter un filigrane
La création d'un filigrane est simple avec GroupDocs.Watermark. Dans cet exemple, nous allons créer un simple filigrane de texte.
```csharp
TextWatermark watermark = new TextWatermark("Test watermark", new Font("Arial", 12));
watermarker.Add(watermark);
```
 Ici, nous créons un`TextWatermark` objet avec le texte « Test du filigrane » et spécifiez les détails de la police. Ensuite, nous ajoutons ce filigrane au document en utilisant le`Add` méthode du`Watermarker` classe.
## Étape 5 : Enregistrez le document filigrané
Enfin, enregistrez le document filigrané dans le chemin de sortie spécifié.
```csharp
watermarker.Save(outputFileName);
```
 Ce code enregistre le document avec le filigrane nouvellement ajouté`outputFileName` chemin que vous avez défini précédemment.

## Conclusion
Toutes nos félicitations! Vous avez ajouté avec succès un filigrane à votre document à l'aide de GroupDocs.Watermark pour .NET. Cette bibliothèque facilite incroyablement la gestion des filigranes dans une variété de formats de documents. Que vous ayez besoin d'ajouter du texte, des images ou d'autres types de filigranes, GroupDocs.Watermark dispose des outils dont vous avez besoin. N'oubliez pas de consulter le[Documentation](https://tutorials.groupdocs.com/Watermark/net/) pour des fonctionnalités plus avancées et des options de personnalisation.
## FAQ
### Quels types de filigranes puis-je ajouter à l’aide de GroupDocs.Watermark pour .NET ?
Vous pouvez ajouter des filigranes de texte, des filigranes d'image et même des formes et des logos complexes. La bibliothèque prend en charge un large éventail d'options de personnalisation.
### Puis-je supprimer les filigranes des documents à l’aide de GroupDocs.Watermark ?
Oui, GroupDocs.Watermark vous permet également de supprimer les filigranes existants des documents.
### Existe-t-il un essai gratuit disponible pour GroupDocs.Watermark ?
 Oui, vous pouvez télécharger un essai gratuit à partir de[ici](https://releases.groupdocs.com/).
### Comment acheter une licence pour GroupDocs.Watermark ?
Vous pouvez acheter une licence directement auprès du[Site Web GroupDocs](https://purchase.groupdocs.com/buy).
### Où puis-je obtenir de l'aide si je rencontre des problèmes ?
 Pour obtenir de l'aide, vous pouvez visiter le[Forum d'assistance GroupDocs.Watermark](https://forum.groupdocs.com/c/watermark/19).