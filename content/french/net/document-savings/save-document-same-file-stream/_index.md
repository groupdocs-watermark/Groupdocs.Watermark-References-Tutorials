---
title: Enregistrer le document dans le même fichier ou flux
linktitle: Enregistrer le document dans le même fichier ou flux
second_title: API GroupDocs.Watermark .NET
description: Découvrez comment ajouter des filigranes aux documents à l'aide de Groupdocs.Watermark pour .NET. Ce guide fournit des instructions pour garantir la protection et l’intégrité des documents.
weight: 10
url: /fr/net/document-savings/save-document-same-file-stream/
---
## Introduction
À l’ère numérique d’aujourd’hui, l’ajout de filigranes aux documents est devenu essentiel pour protéger la propriété intellectuelle et garantir l’intégrité de la marque. Groupdocs.Watermark for .NET offre une solution robuste pour les développeurs cherchant à intégrer des filigranes dans des documents de manière transparente. Ce guide complet vous guidera à travers les étapes d'enregistrement d'un document avec un filigrane dans le même fichier ou flux à l'aide de Groupdocs.Watermark pour .NET.
## Conditions préalables
Avant de plonger dans le didacticiel, assurez-vous d'avoir les éléments suivants :
1. Environnement de développement : Visual Studio installé sur votre machine.
2. .NET Framework : assurez-vous que vous disposez de .NET Framework 4.0 ou version ultérieure.
3.  Groupdocs.Watermark pour .NET : téléchargez et installez la dernière version à partir du[site](https://releases.groupdocs.com/Watermark/net/).
4.  Licence : Obtenez une licence temporaire ou permanente auprès de[ici](https://purchase.groupdocs.com/temporary-license/).
## Importer des espaces de noms
Pour commencer à utiliser Groupdocs.Watermark dans votre projet .NET, vous devez importer les espaces de noms nécessaires :
```csharp
using System;
using System.IO;
using GroupDocs.Watermark.Watermarks;
```
## Étape 1 : Configurez votre projet
Avant d'ajouter des filigranes à nos documents, nous devons configurer notre projet .NET. Voici comment:
1. Créer un nouveau projet : ouvrez Visual Studio et créez une nouvelle application console.
2. Ajouter une référence Groupdocs.Watermark : cliquez avec le bouton droit sur le projet dans l'Explorateur de solutions, choisissez « Gérer les packages NuGet » et installez le package Groupdocs.Watermark.
## Étape 2 : Copiez le document vers un nouvel emplacement
Pour éviter de modifier directement le document original, il est conseillé de le copier d'abord vers un nouvel emplacement. Voici comment procéder :
```csharp
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName("Your Document Path"));
File.Copy("Your Document Path", outputFileName);
```
## Étape 3 : initialiser le filigrane
Maintenant que notre document est copié, nous pouvons initialiser la classe Watermarker pour ajouter notre filigrane :
```csharp
using (Watermarker watermarker = new Watermarker(outputFileName))
{
    // Le filigrane va ici
}
```
## Étape 4 : Créer et ajouter un filigrane de texte
Ensuite, nous créons un filigrane de texte et l'ajoutons à notre document :
```csharp
TextWatermark watermark = new TextWatermark("Test watermark", new Font("Arial", 12));
watermarker.Add(watermark);
```
## Étape 5 : Enregistrez le document
Enfin, enregistrez le document avec le filigrane appliqué :
```csharp
watermarker.Save();
```
## Conclusion
L'ajout de filigranes à vos documents à l'aide de Groupdocs pour .NET est simple et efficace. En suivant les étapes décrites ci-dessus, vous pouvez protéger vos documents et maintenir leur intégrité sans effort. Pour plus de détails, vous pouvez vous référer au[Documentation](https://tutorials.groupdocs.com/Watermark/net/).
## FAQ
### Puis-je utiliser une image comme filigrane au lieu du texte ?
Oui, Groupdocs.Watermark vous permet d'utiliser des images, des formes et du texte comme filigranes.
### Comment supprimer un filigrane d'un document ?
 Vous pouvez supprimer un filigrane en accédant à la collection de filigranes dans le document et en utilisant l'outil`Remove` méthode.
### Est-il possible de personnaliser l'apparence du filigrane ?
Absolument. Vous pouvez personnaliser la police, la taille, la couleur et la position du filigrane.
### Puis-je appliquer plusieurs filigranes à un seul document ?
 Oui, vous pouvez ajouter plusieurs filigranes en appelant le`Add` méthode plusieurs fois avec différents objets de filigrane.
### Groupdocs.Watermark est-il compatible avec tous les formats de documents ?
Groupdocs.Watermark prend en charge un large éventail de formats de documents, notamment PDF, DOCX, PPTX et bien d'autres.