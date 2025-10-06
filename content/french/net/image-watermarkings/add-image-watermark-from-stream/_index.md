---
title: Ajouter un filigrane d'image à partir d'un flux
linktitle: Ajouter un filigrane d'image à partir d'un flux
second_title: API GroupDocs.Watermark .NET
description: Découvrez comment ajouter des filigranes d’image aux documents à l’aide de GroupDocs.Watermark pour .NET. Suivez notre guide étape par étape pour une intégration transparente des filigranes.
weight: 12
url: /fr/net/image-watermarkings/add-image-watermark-from-stream/
type: docs
---
# Ajouter un filigrane d'image à partir d'un flux

## Introduction
Dans le domaine de la gestion et de la sécurité des documents, l’incorporation de filigranes dans les fichiers revêt une importance primordiale. Qu'il s'agisse de l'image de marque, de la protection des droits d'auteur ou du maintien de l'intégrité des documents, les filigranes jouent un rôle crucial. Heureusement, GroupDocs.Watermark pour .NET fournit une solution robuste pour ajouter, supprimer et rechercher des filigranes dans différents formats de documents.
## Conditions préalables
Avant de vous lancer dans l'implémentation des filigranes à l'aide de GroupDocs.Watermark pour .NET, assurez-vous que les conditions préalables suivantes sont remplies :
1.  Installez GroupDocs.Watermark pour .NET : Téléchargez et installez la bibliothèque GroupDocs.Watermark pour .NET à partir du[lien de téléchargement](https://releases.groupdocs.com/Watermark/net/).
2. Accès au document : accédez au document sur lequel vous souhaitez ajouter ou supprimer des filigranes.
3. Connaissance de base de C# : Une connaissance du langage de programmation C# est nécessaire pour comprendre et mettre en œuvre les extraits de code fournis.

## Importer des espaces de noms
Avant de procéder à l'ajout de filigranes d'image à partir d'un flux, importez les espaces de noms nécessaires :
```csharp
using GroupDocs.Watermark.Watermarks;
using System;
using System.IO;
```

## Étape 1 : Définir le chemin du document et le répertoire de sortie
Tout d'abord, définissez le chemin du document où vous souhaitez ajouter le filigrane et spécifiez le répertoire de sortie du document traité.
```csharp
string documentPath = Constants.WatermarkJpg;
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
## Étape 2 : ouvrir le flux de filigrane
 Ouvrez le fichier image du filigrane sous forme de flux à l'aide du`File.OpenRead` méthode.
```csharp
using (Stream watermarkStream = File.OpenRead(documentPath))
{
    // La logique de traitement du filigrane ira ici
}
```
## Étape 3 : ajouter un filigrane au document
 Initialiser un`Watermarker` objet avec le chemin du document, puis créez un`ImageWatermark` objet avec le flux de filigrane obtenu à l’étape 2. Ajoutez le filigrane au document à l’aide du`Add` méthode du`Watermarker` objet.
```csharp
using (Watermarker watermarker = new Watermarker("Your Document Path"))
{
    using (ImageWatermark watermark = new ImageWatermark(watermarkStream))
    {
        // Ajouter un filigrane au document
        watermarker.Add(watermark);
        // Enregistrez le document avec un filigrane
        watermarker.Save(outputFileName);
    }
}
```

## Conclusion
GroupDocs.Watermark for .NET fournit une solution transparente pour ajouter des filigranes aux documents, garantissant ainsi l'identité de la marque, la protection des droits d'auteur et l'intégrité des documents. En suivant les étapes décrites et en utilisant les extraits de code fournis, les utilisateurs peuvent facilement incorporer des filigranes dans leurs documents.
## FAQ
### GroupDocs.Watermark est-il compatible avec différents formats de documents ?
Oui, GroupDocs.Watermark prend en charge un large éventail de formats de documents, notamment les documents Word, les feuilles de calcul Excel, les présentations PowerPoint, les PDF, etc.
### Puis-je personnaliser l’apparence et la position des filigranes ?
Absolument, GroupDocs.Watermark offre de nombreuses options pour personnaliser l'apparence, la position, la transparence, la rotation et bien plus encore du filigrane pour répondre à des exigences spécifiques.
### GroupDocs.Watermark fournit-il des API pour supprimer les filigranes existants ?
Oui, GroupDocs.Watermark permet aux utilisateurs non seulement d'ajouter des filigranes, mais également de supprimer facilement les filigranes existants des documents.
### Une assistance technique est-elle disponible pour les utilisateurs de GroupDocs.Watermark ?
 Oui, les utilisateurs peuvent bénéficier d'un support technique et d'une assistance via le service dédié.[Forum GroupDocs.Watermark](https://forum.groupdocs.com/c/watermark/19).
### Puis-je évaluer GroupDocs.Watermark avant d’acheter ?
Certes, les utilisateurs peuvent opter pour un essai gratuit de GroupDocs.Watermark pour explorer ses caractéristiques et fonctionnalités avant de prendre une décision d'achat.