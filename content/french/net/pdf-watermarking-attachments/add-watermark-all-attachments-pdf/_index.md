---
title: Ajouter un filigrane à toutes les pièces jointes du PDF
linktitle: Ajouter un filigrane à toutes les pièces jointes du PDF
second_title: API GroupDocs.Watermark .NET
description: Découvrez comment ajouter des filigranes aux pièces jointes PDF à l'aide de GroupDocs.Watermark pour .NET. Sécurisez facilement vos documents avec des filigranes personnalisés.
weight: 16
url: /fr/net/pdf-watermarking-attachments/add-watermark-all-attachments-pdf/
---
## Introduction
L'ajout de filigranes aux pièces jointes PDF peut être une étape cruciale dans la gestion des documents, en particulier lorsqu'il s'agit de garantir la sécurité ou l'image de marque. GroupDocs.Watermark for .NET offre une solution complète pour intégrer de manière transparente des filigranes dans des fichiers PDF. Dans ce didacticiel, nous vous guiderons tout au long du processus d'ajout d'un filigrane à toutes les pièces jointes d'un document PDF à l'aide de GroupDocs.Watermark pour .NET.
## Conditions préalables
Avant de commencer, assurez-vous d'avoir les éléments suivants :
1.  GroupDocs.Watermark pour .NET : si vous ne l'avez pas déjà fait, téléchargez et installez GroupDocs.Watermark pour .NET à partir du[site web](https://releases.groupdocs.com/Watermark/net/).
2. Environnement de développement : configurez un environnement de développement approprié avec Visual Studio ou tout autre IDE compatible .NET.
3. Document PDF : préparez le document PDF auquel vous souhaitez ajouter des filigranes, ainsi que les pièces jointes que vous souhaitez filigraner.

## Importation d'espaces de noms
Avant de plonger dans le code, assurez-vous d'importer les espaces de noms nécessaires pour accéder aux fonctionnalités de GroupDocs.Watermark pour .NET :
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Étape 1 : Définir le chemin du document et le répertoire de sortie
Tout d'abord, définissez le chemin d'accès à votre document PDF d'entrée et le répertoire dans lequel le document filigrané sera enregistré :
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
## Étape 2 : initialiser les options de chargement et le filigrane
Ensuite, initialisez les options de chargement du document PDF et créez un filigrane de texte :
```csharp
var loadOptions = new PdfLoadOptions();
TextWatermark watermark = new TextWatermark("This is WaterMark on Attachment", new Font("Arial", 19));
```
## Étape 3 : Charger le document et les pièces jointes
Chargez le document PDF et parcourez ses pièces jointes :
```csharp
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    PdfContent pdfContent = watermarker.GetContent<PdfContent>();
    foreach (PdfAttachment attachment in pdfContent.Attachments)
    {
```
## Étape 4 : Vérifiez la prise en charge des pièces jointes
Vérifiez si le fichier joint est pris en charge par GroupDocs.Watermark :
```csharp
        IDocumentInfo info = attachment.GetDocumentInfo();
        if (info.FileType != FileType.Unknown && !info.IsEncrypted)
        {
```
## Étape 5 : ajouter un filigrane aux pièces jointes
Chargez le document ci-joint et ajoutez le filigrane :
```csharp
            using (Watermarker attachedWatermarker = attachment.CreateWatermarker())
            {
                attachedWatermarker.Add(watermark);
                attachedWatermarker.Save();
            }
        }
    }
```
## Étape 6 : Enregistrer les modifications
Enfin, enregistrez les modifications apportées au document PDF filigrané :
```csharp
    watermarker.Save(outputFileName);
}
```

## Conclusion
Dans ce didacticiel, nous avons expliqué comment ajouter des filigranes à toutes les pièces jointes d'un document PDF à l'aide de GroupDocs.Watermark pour .NET. En suivant le guide étape par étape, vous pouvez intégrer de manière transparente des filigranes dans vos fichiers PDF, garantissant ainsi la sécurité et l'image de marque des documents.
## FAQ
### Puis-je personnaliser l’apparence du filigrane ?
Oui, vous pouvez personnaliser divers aspects tels que le texte, la police, la taille, la couleur et la position du filigrane en fonction de vos besoins.
### GroupDocs.Watermark prend-il en charge d'autres formats de documents que le PDF ?
Oui, GroupDocs.Watermark prend en charge un large éventail de formats de documents, notamment Microsoft Word, Excel, PowerPoint, Visio, Outlook et Images.
### Existe-t-il une version d’essai disponible pour GroupDocs.Watermark ?
Oui, vous pouvez explorer les fonctionnalités de GroupDocs.Watermark en téléchargeant la version d'essai gratuite sur le site Web.
### Puis-je ajouter plusieurs filigranes à un seul document ?
Absolument, GroupDocs.Watermark vous permet d'ajouter simultanément plusieurs filigranes, notamment du texte, des images et des annotations, pour améliorer la sécurité et l'image de marque des documents.
### Une assistance technique est-elle disponible pour les utilisateurs de GroupDocs.Watermark ?
Oui, GroupDocs fournit une assistance technique complète via des forums et des canaux d'assistance dédiés pour aider les utilisateurs pour toute question ou problème qu'ils pourraient rencontrer.