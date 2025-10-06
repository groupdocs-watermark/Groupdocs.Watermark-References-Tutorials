---
title: Obtenez les formats de fichiers pris en charge
linktitle: Obtenez les formats de fichiers pris en charge
second_title: API GroupDocs.Watermark .NET
description: Ajoutez sans effort des filigranes à vos documents à l'aide de GroupDocs.Watermark pour .NET. Suivez notre guide complet étape par étape pour protéger vos actifs numériques.
weight: 13
url: /fr/net/document-manipulation/get-supported-file-formats/
type: docs
---
# Obtenez les formats de fichiers pris en charge

## Introduction
Le filigrane de vos documents est une étape cruciale dans la sauvegarde de vos actifs numériques. Qu'il s'agisse de protéger la propriété intellectuelle, d'assurer la confidentialité ou simplement de créer une image de marque, les filigranes jouent un rôle essentiel. Si vous êtes un développeur .NET cherchant à intégrer des fonctionnalités de filigrane dans vos applications, GroupDocs.Watermark for .NET est un outil puissant et polyvalent que vous devriez envisager. Ce didacticiel vous guidera à travers les bases de l'utilisation de GroupDocs.Watermark, de l'installation à l'application de votre premier filigrane, en décomposant chaque étape pour vous assurer que vous pouvez facilement suivre.
## Conditions préalables
Avant d'entrer dans les détails, assurons-nous que vous disposez de tout ce dont vous avez besoin pour commencer :
1.  Visual Studio : assurez-vous que Visual Studio est installé sur votre ordinateur. Vous pouvez le télécharger depuis le[Site Web de Visual Studio](https://visualstudio.microsoft.com/).
2. .NET Framework : GroupDocs.Watermark prend en charge différentes versions du .NET Framework. Assurez-vous que votre projet cible une version compatible.
3. GroupDocs.Watermark pour .NET : vous pouvez télécharger la dernière version à partir du[page de sortie](https://releases.groupdocs.com/Watermark/net/).
4. Connaissance de base de C# : ce didacticiel suppose que vous possédez une compréhension fondamentale du développement C# et .NET.
## Importer des espaces de noms
Tout d’abord, importons les espaces de noms nécessaires dans votre projet. Ouvrez votre fichier C# et ajoutez les directives using suivantes en haut :
```csharp
using System;
using System.Collections.Generic;
using GroupDocs.Watermark.Common;
```
Une fois ces espaces de noms importés, vous êtes prêt à commencer à ajouter des filigranes à vos documents.

## Étape 1 : initialiser le moteur de filigrane
 La première étape consiste à initialiser le moteur de tatouage. Cela implique de créer une instance du`Watermarker` classe avec le document que vous souhaitez filigraner.
```csharp
string documentPath = "path/to/your/document.pdf";
Watermarker watermarker = new Watermarker(documentPath);
```
 Cet extrait de code configure le`Watermarker` objet, que vous utiliserez pour appliquer des filigranes à votre document.
## Étape 2 : ajouter un filigrane de texte
Maintenant, ajoutons un simple filigrane de texte à votre document. Les filigranes de texte sont parfaits pour ajouter des étiquettes telles que « Confidentiel » ou « Brouillon ».
```csharp
TextWatermark textWatermark = new TextWatermark("Confidential", new Font("Arial", 36));
textWatermark.ForegroundColor = Color.Red;
textWatermark.HorizontalAlignment = HorizontalAlignment.Center;
textWatermark.VerticalAlignment = VerticalAlignment.Center;
watermarker.Add(textWatermark);
```
 Ici, nous avons créé un`TextWatermark`objet avec le texte « Confidentiel », définissez sa police et sa couleur, puis alignez-le au centre du document.
## Étape 3 : ajouter un filigrane d'image
Si vous préférez utiliser une image comme filigrane, GroupDocs.Watermark vous facilite la tâche.
```csharp
ImageWatermark imageWatermark = new ImageWatermark("path/to/watermark.png");
imageWatermark.Width = 100;
imageWatermark.Height = 100;
imageWatermark.HorizontalAlignment = HorizontalAlignment.Right;
imageWatermark.VerticalAlignment = VerticalAlignment.Top;
watermarker.Add(imageWatermark);
```
 Dans cet exemple, nous créons un`ImageWatermark` objet, définissez ses dimensions et alignez-le sur le coin supérieur droit du document.
## Étape 4 : Enregistrez le document
Après avoir ajouté les filigranes souhaités, la dernière étape consiste à enregistrer le document modifié.
```csharp
watermarker.Save("path/to/output/document.pdf");
watermarker.Dispose();
```
 Cela enregistrera le document filigrané dans le chemin spécifié et libérera toutes les ressources utilisées par celui-ci.`Watermarker` exemple.
## Étape 5 : Obtenez les formats de fichiers pris en charge
Pour voir quels formats de fichiers sont pris en charge par GroupDocs.Watermark, vous pouvez utiliser l'extrait de code suivant :
```csharp
IEnumerable<FileType> supportedFileTypes = FileType.GetSupportedFileTypes();
foreach (FileType fileType in supportedFileTypes)
{
    Console.WriteLine(fileType);
}
```
Cela imprimera tous les types de fichiers que GroupDocs.Watermark peut gérer, vous donnant une vue complète de ses capacités.
## Conclusion
Le filigrane de vos documents avec GroupDocs pour .NET est simple et efficace. En suivant ce didacticiel, vous avez appris à initialiser le moteur de filigrane, à ajouter des filigranes de texte et d'image, à enregistrer vos documents filigranés et à répertorier les formats de fichiers pris en charge. Avec ces outils, vous pouvez protéger vos documents en toute confiance.
 Si vous avez des questions ou avez besoin d'aide supplémentaire, n'hésitez pas à visiter le[Forum d'assistance GroupDocs.Watermark](https://forum.groupdocs.com/c/watermark/19).
## FAQ
### Comment installer GroupDocs.Watermark pour .NET ?
 Vous pouvez le télécharger depuis le[page de sortie](https://releases.groupdocs.com/Watermark/net/) et ajoutez la DLL à votre projet.
### Puis-je essayer GroupDocs.Watermark gratuitement ?
 Oui, vous pouvez demander un[essai gratuit](https://releases.groupdocs.com/) pour évaluer le logiciel avant de l'acheter.
### Quels formats de fichiers sont pris en charge par GroupDocs.Watermark ?
Vous pouvez utiliser l'extrait de code fourni pour répertorier tous les formats de fichiers pris en charge.
### Comment puis-je acheter une licence pour GroupDocs.Watermark ?
 Les licences peuvent être achetées directement auprès du[page d'achat](https://purchase.groupdocs.com/buy).
### Existe-t-il une documentation disponible pour GroupDocs.Watermark ?
 Oui, une documentation complète est disponible[ici](https://tutorials.groupdocs.com/Watermark/net/).