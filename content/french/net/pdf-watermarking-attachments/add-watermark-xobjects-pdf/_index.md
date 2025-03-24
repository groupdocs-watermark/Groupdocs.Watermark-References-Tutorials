---
title: Ajouter un filigrane aux XObjects en PDF
linktitle: Ajouter un filigrane aux XObjects en PDF
second_title: API GroupDocs.Watermark .NET
description: Découvrez comment ajouter des filigranes aux XObjects dans un PDF à l'aide de Groupdocs.Watermark pour .NET. Suivez notre guide étape par étape pour une mise en œuvre facile.
weight: 20
url: /fr/net/pdf-watermarking-attachments/add-watermark-xobjects-pdf/
---
## Introduction
Le filigrane des PDF est une étape cruciale pour garantir que vos documents sont protégés contre toute utilisation non autorisée. Avec Groupdocs.Watermark pour .NET, ajouter des filigranes aux XObjects dans vos PDF n'a jamais été aussi simple. Dans ce didacticiel, nous vous guiderons pas à pas tout au long du processus, afin que vous puissiez appliquer en toute confiance des filigranes à vos documents PDF. Commençons!
## Conditions préalables
Avant de plonger dans le didacticiel, assurons-nous que vous disposez de tout ce dont vous avez besoin pour suivre sans problème :
-  Groupdocs.Watermark pour .NET : téléchargez et installez la dernière version à partir de[ici](https://releases.groupdocs.com/Watermark/net/).
- .NET Framework : assurez-vous que .NET Framework est installé sur votre ordinateur de développement.
- Environnement de développement : utilisez Visual Studio ou tout autre IDE prenant en charge le développement .NET.
-  Permis temporaire : obtenez un[permis temporaire](https://purchase.groupdocs.com/temporary-license/) si vous évaluez le produit.
Une fois ces conditions préalables remplies, vous êtes prêt à commencer à filigraner vos PDF.
## Importer des espaces de noms
Tout d’abord, vous devrez importer les espaces de noms nécessaires dans votre projet. Ouvrez votre projet C# et ajoutez les directives using suivantes :
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Étape 1 : Configurez vos chemins de documents
La première étape consiste à configurer les chemins de votre document. Définissez le chemin où se trouve votre PDF et où vous souhaitez enregistrer le PDF filigrané.
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
 Remplacer`"Your Document Path"` et`"Your Document Directory"` avec les chemins réels sur votre machine.
## Étape 2 : initialiser les options de chargement du PDF
Ensuite, vous devrez initialiser les options de chargement du PDF. Ceci est crucial pour charger correctement le contenu PDF.
```csharp
var loadOptions = new PdfLoadOptions();
```
## Étape 3 : Charger le document PDF
À l'aide des options de chargement, chargez le document PDF avec le`Watermarker` classe.
```csharp
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    PdfContent pdfContent = watermarker.GetContent<PdfContent>();
```
## Étape 4 : Créer le filigrane
Maintenant, vous devez créer le filigrane qui sera ajouté au PDF. Pour ce didacticiel, nous allons créer un filigrane de texte.
```csharp
TextWatermark watermark = new TextWatermark("Protected image", new Font("Arial", 8))
{
    HorizontalAlignment = HorizontalAlignment.Center,
    VerticalAlignment = VerticalAlignment.Center,
    RotateAngle = 45,
    SizingType = SizingType.ScaleToParentDimensions,
    ScaleFactor = 1
};
```
## Étape 5 : ajouter un filigrane aux XObjects
Parcourez chaque page et chaque XObject dans le PDF pour appliquer le filigrane.
```csharp
foreach (PdfPage page in pdfContent.Pages)
{
    foreach (PdfXObject xObject in page.XObjects)
    {
        if (xObject.Image != null)
        {
            // Ajouter un filigrane à l'image
            xObject.Image.Add(watermark);
        }
    }
}
```
## Étape 6 : Enregistrez le PDF filigrané
Enfin, enregistrez le PDF filigrané dans le fichier de sortie spécifié.
```csharp
    watermarker.Save(outputFileName);
}
```
Et voila! Votre PDF contient désormais des filigranes sur tous ses XObjects.
## Conclusion
 L'ajout de filigranes à vos documents PDF à l'aide de Groupdocs pour .NET est un processus simple qui fournit une couche de sécurité supplémentaire. En suivant les étapes décrites dans ce didacticiel, vous pouvez vous assurer que vos documents sont protégés contre toute utilisation non autorisée. N'oubliez pas que vous pouvez toujours vous référer au[Documentation](https://tutorials.groupdocs.com/Watermark/net/) pour des informations plus détaillées et des fonctionnalités avancées.
## FAQ
### Puis-je utiliser une image comme filigrane au lieu du texte ?
Oui, Groupdocs.Watermark pour .NET prend en charge les filigranes de texte et d’image.
### Comment puis-je tester Groupdocs.Watermark sans l’acheter ?
 Vous pouvez utiliser un[permis temporaire](https://purchase.groupdocs.com/temporary-license/) pour évaluer le produit.
### Est-il possible de personnaliser l'apparence du filigrane ?
Absolument! Vous pouvez personnaliser la police, la taille, l'angle de rotation, etc.
### Groupdocs.Watermark prend-il en charge d’autres formats de documents ?
Oui, il prend en charge différents formats, notamment Word, Excel et PowerPoint.
### Où puis-je obtenir de l'aide si je rencontre des problèmes ?
 Vous pouvez bénéficier du soutien du[Forum Groupdocs](https://forum.groupdocs.com/c/watermark/19).