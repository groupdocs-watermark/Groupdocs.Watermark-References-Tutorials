---
title: Ajouter des filigranes au PDF
linktitle: Ajouter des filigranes au PDF
second_title: API GroupDocs.Watermark .NET
description: Découvrez comment ajouter des filigranes de texte et d'image à vos PDF à l'aide de GroupDocs.Watermark for .NET grâce à notre guide complet étape par étape.
type: docs
weight: 14
url: /fr/net/pdf-watermarking-attachments/add-watermarks-pdf/
---
## Introduction
Souhaitez-vous ajouter des filigranes à vos PDF pour protéger vos documents ou les marquer de votre logo ? Cherchez pas plus loin! Dans ce didacticiel, nous aborderons le processus d'utilisation de GroupDocs.Watermark pour .NET pour ajouter des filigranes de texte et d'image à vos fichiers PDF. Que vous soyez un développeur chevronné ou débutant, ce guide vous guidera à travers chaque étape, vous garantissant ainsi d'appliquer des filigranes avec facilité et précision.
## Conditions préalables
Avant de commencer, assurons-nous que vous disposez de tout ce dont vous avez besoin pour suivre ce tutoriel :
-  GroupDocs.Watermark pour .NET : assurez-vous que la dernière version est installée. Tu peux[Télécharger les ici](https://releases.groupdocs.com/Watermark/net/).
- Environnement de développement .NET : Visual Studio ou tout autre IDE prenant en charge .NET.
- Connaissance de base de C# : Comprendre les bases de la programmation C# vous aidera à suivre les étapes avec facilité.
- Document PDF : préparez un exemple de document PDF pour le filigrane.
- Image pour filigrane : si vous ajoutez un filigrane d'image, préparez votre fichier image.
## Importer des espaces de noms
Tout d’abord, vous devez importer les espaces de noms nécessaires dans votre projet C#. Cela vous permettra d'accéder à la fonctionnalité GroupDocs.Watermark.
```csharp
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
Maintenant, décomposons le processus en étapes gérables.
## Étape 1 : Chargez votre document PDF
La première étape consiste à charger votre document PDF dans le filigrane. Voici comment procéder :
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // D'autres étapes seront ajoutées ici
}
```
## Étape 2 : ajouter un filigrane de texte à la première page
Ensuite, nous ajouterons un filigrane de texte à la première page de votre PDF. Suivez ces instructions :
```csharp
// Ajouter un filigrane de texte à la première page
TextWatermark textWatermark = new TextWatermark("This is a test watermark", new Font("Arial", 8));
PdfArtifactWatermarkOptions textWatermarkOptions = new PdfArtifactWatermarkOptions();
textWatermarkOptions.PageIndex = 0;
watermarker.Add(textWatermark, textWatermarkOptions);
```

L'ajout d'un filigrane de texte peut aider à protéger votre document contre toute utilisation non autorisée ou simplement à le marquer. Imaginez tamponner votre document avec un sceau d'authenticité invisible.
## Étape 3 : ajouter un filigrane d'image à la deuxième page
Maintenant, ajoutons un filigrane d'image à la deuxième page. Ceci est particulièrement utile pour les logos ou tout filigrane graphique.
```csharp
// Ajouter un filigrane d'image à la deuxième page
using (ImageWatermark imageWatermark = new ImageWatermark("Your Image Path"))
{
    PdfArtifactWatermarkOptions imageWatermarkOptions = new PdfArtifactWatermarkOptions();
    imageWatermarkOptions.PageIndex = 1;
    watermarker.Add(imageWatermark, imageWatermarkOptions);
}
```

Les filigranes d’images peuvent donner à vos documents un aspect professionnel et garantir que votre marque est toujours visible. C'est comme ajouter votre signature à chaque page.
## Étape 4 : Enregistrez le PDF filigrané
Après avoir ajouté les filigranes, la dernière étape consiste à enregistrer le PDF filigrané à l'emplacement souhaité.
```csharp
watermarker.Save(outputFileName);
```
L'enregistrement du document finalise toutes les modifications que vous avez apportées. C’est le moment où vos efforts se concrétisent en un résultat tangible, prêt à être utilisé ou distribué.
## Conclusion
Toutes nos félicitations! Vous avez ajouté avec succès des filigranes de texte et d'image à votre PDF à l'aide de GroupDocs.Watermark pour .NET. Ce processus est non seulement simple mais également hautement personnalisable pour répondre à vos besoins spécifiques. Que vous protégiez vos documents ou que vous les marquiez, les filigranes sont un outil puissant à votre disposition.
## FAQ
### Puis-je ajouter plusieurs filigranes sur la même page ?
 Oui, vous pouvez ajouter plusieurs filigranes à la même page en appelant le`Add` méthode plusieurs fois avec différents objets de filigrane.
### Comment puis-je personnaliser l’apparence du filigrane de texte ?
 Vous pouvez personnaliser le filigrane de texte en ajustant les propriétés telles que la police, la taille, la couleur et l'opacité à l'aide de l'option`TextWatermark` objet.
### Est-il possible de filigraner uniquement des pages spécifiques d'un PDF ?
 Oui, vous pouvez spécifier les pages à filigraner en définissant le`PageIndex` propriété dans le`PdfArtifactWatermarkOptions`.
### Puis-je supprimer les filigranes d’un PDF ?
Oui, GroupDocs.Watermark fournit des fonctionnalités permettant de rechercher et de supprimer les filigranes des documents PDF.
### Comment puis-je obtenir une licence temporaire pour GroupDocs.Watermark ?
Vous pouvez obtenir un permis temporaire en visitant le[page de licence temporaire](https://purchase.groupdocs.com/temporary-license/).