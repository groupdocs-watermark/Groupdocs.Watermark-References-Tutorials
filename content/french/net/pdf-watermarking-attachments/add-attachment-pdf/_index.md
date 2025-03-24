---
title: Ajouter une pièce jointe au PDF
linktitle: Ajouter une pièce jointe au PDF
second_title: API GroupDocs.Watermark .NET
description: Améliorez vos capacités de gestion de documents .NET avec GroupDocs.Watermark pour un filigrane et une gestion transparente des pièces jointes.
weight: 12
url: /fr/net/pdf-watermarking-attachments/add-attachment-pdf/
---

# Ajouter une pièce jointe au PDF

## Introduction
Dans le domaine du développement .NET, GroupDocs.Watermark se distingue comme un outil puissant pour gérer les filigranes, les annotations et bien plus encore dans divers formats de documents. Que vous travailliez avec des PDF, des documents Word ou des images, GroupDocs.Watermark pour .NET offre une intégration transparente qui permet aux développeurs de manipuler facilement des documents.
## Conditions préalables
Avant de plonger dans les subtilités de l'utilisation de GroupDocs.Watermark pour .NET, assurez-vous que les conditions préalables suivantes sont en place :
1.  Installation : assurez-vous d'avoir installé GroupDocs.Watermark pour .NET. Vous pouvez le télécharger depuis le[page de sortie](https://releases.groupdocs.com/Watermark/net/).
2. Préparation du document : préparez un document sur lequel vous souhaitez effectuer un filigrane ou d'autres opérations.
3. Connaissance de base de C# : Familiarisez-vous avec les bases du langage de programmation C#, car nous l'utiliserons pour interagir avec l'API GroupDocs.Watermark.

## Importer des espaces de noms
Avant de commencer l'implémentation, il est crucial d'importer les espaces de noms nécessaires pour accéder aux fonctionnalités de GroupDocs.Watermark. Vous trouverez ci-dessous les espaces de noms requis :
```csharp
using System;
using System.IO;
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
```
## Étape 1 : Charger le document
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
```
 Dans cette étape, nous spécifions le chemin d'accès au document avec lequel nous voulons travailler et créons un`PdfLoadOptions` objet pour charger des documents PDF. Ensuite, nous initialisons un`Watermarker` objet avec le chemin du document et les options de chargement.
## Étape 2 : Obtenez le contenu PDF
```csharp
PdfContent pdfContent = watermarker.GetContent<PdfContent>();
```
 Ici, nous obtenons le contenu du document PDF en utilisant le`GetContent<PdfContent>()` méthode.
## Étape 3 : ajouter une pièce jointe
```csharp
pdfContent.Attachments.Add(File.ReadAllBytes("Your Document Path"), "sample doc", "sample doc as attachment");
```
Cette étape consiste à ajouter une pièce jointe au document PDF. Vous devez fournir les octets, le nom et la description du fichier joint.
## Étape 4 : Enregistrer les modifications
```csharp
watermarker.Save(outputFileName);
```
Enfin, nous enregistrons les modifications apportées au document avec la pièce jointe ajoutée.

## Conclusion
GroupDocs.Watermark for .NET offre une solution robuste pour gérer de manière transparente les filigranes et les pièces jointes des documents. En suivant les étapes décrites ci-dessus, vous pouvez facilement intégrer des fonctionnalités de filigrane et de pièce jointe dans vos applications .NET.
## FAQ
### GroupDocs.Watermark est-il compatible avec tous les frameworks .NET ?
Oui, GroupDocs.Watermark prend en charge .NET Framework 2.0 et versions ultérieures.
### Puis-je supprimer les filigranes ajoutés à l’aide de GroupDocs.Watermark ?
Oui, GroupDocs.Watermark fournit des méthodes pour supprimer les filigranes des documents.
### GroupDocs.Watermark prend-il en charge le cryptage des documents ?
Oui, GroupDocs.Watermark vous permet de travailler avec des documents cryptés.
### Puis-je personnaliser l’apparence des filigranes ?
Absolument, GroupDocs.Watermark propose diverses options de personnalisation des filigranes.
### Existe-t-il une version d'essai disponible à des fins de test ?
 Oui, vous pouvez accéder à la version d'essai à partir du[page des versions](https://releases.groupdocs.com/).