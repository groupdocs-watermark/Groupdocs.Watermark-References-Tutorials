---
title: Ajouter un filigrane d'image
linktitle: Ajouter un filigrane d'image
second_title: API GroupDocs.Watermark .NET
description: Découvrez comment ajouter des filigranes d'image à vos documents à l'aide de GroupDocs.Watermark pour .NET grâce à notre didacticiel détaillé étape par étape.
type: docs
weight: 11
url: /fr/net/image-watermarkings/add-image-watermark/
---
## Introduction
Bienvenue dans ce guide complet sur l'ajout de filigranes d'image à l'aide de GroupDocs.Watermark pour .NET ! Le filigrane est un moyen puissant de protéger vos documents et images contre toute utilisation non autorisée, garantissant ainsi la sécurité de votre propriété intellectuelle. Dans ce didacticiel, nous vous guiderons tout au long du processus, de la configuration de votre environnement à l'application d'un filigrane à vos documents. Que vous soyez un développeur chevronné ou que vous débutiez tout juste, vous trouverez ce guide utile et facile à suivre.
## Conditions préalables
Avant de plonger dans le didacticiel, assurons-nous que vous disposez de tout ce dont vous avez besoin :
- Environnement de développement : Visual Studio ou tout IDE compatible .NET
- .NET Framework : .NET Framework 4.0 ou version ultérieure
-  GroupDocs.Watermark pour .NET : vous pouvez le télécharger à partir du[Site Web GroupDocs](https://releases.groupdocs.com/Watermark/net/)
-  Fichier image : un fichier image à utiliser comme filigrane (par exemple,`watermark.jpg`)
- Fichier de document : un document auquel vous souhaitez ajouter le filigrane (par exemple,`presentation.pptx`)
## Importer des espaces de noms
Pour commencer, vous devrez importer les espaces de noms nécessaires dans votre projet. Ceci est essentiel pour accéder aux fonctionnalités de GroupDocs.
```csharp
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
Dans cette section, nous décomposerons le processus d'ajout d'un filigrane d'image en étapes claires et gérables. Suivez attentivement chaque étape pour réussir à filigraner votre document.
## Étape 1 : Configurez votre environnement
 Tout d’abord, assurez-vous que votre environnement de développement est correctement configuré. Installez la bibliothèque GroupDocs.Watermark en la téléchargeant depuis le[Site Web GroupDocs](https://releases.groupdocs.com/Watermark/net/).
1. Ouvrez votre projet dans Visual Studio.
2. Cliquez avec le bouton droit sur votre projet dans l'Explorateur de solutions.
3. Sélectionnez « Gérer les packages NuGet… »
4.  Rechercher`GroupDocs.Watermark` et installez-le.
## Étape 2 : Définir les chemins de fichiers
Ensuite, vous devrez définir les chemins de votre document d'entrée et du répertoire de sortie. Cela aide le programme à localiser les fichiers avec lesquels il doit travailler.
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
 Remplacer`"Your Document Path"` et`"Your Document Directory"` avec les chemins réels vers votre document et le répertoire de sortie souhaité.
## Étape 3 : initialiser le filigrane
Maintenant, initialisez le`Watermarker` class avec le chemin d’accès à votre document. Cette classe est responsable de la gestion du processus de tatouage.
```csharp
using (Watermarker watermarker = new Watermarker(documentPath))
{
    // Passez aux étapes suivantes dans ce bloc using
}
```
## Étape 4 : Créer un filigrane d'image
 Au sein du`Watermarker` bloc, créez une instance du`ImageWatermark` classe en utilisant le chemin d’accès à votre image de filigrane. Cette classe représente l'image que vous souhaitez utiliser comme filigrane.
```csharp
using (ImageWatermark watermark = new ImageWatermark("path/to/your/watermark.jpg"))
{
    // Passez à l'étape suivante dans ce bloc using
}
```
## Étape 5 : ajouter un filigrane au document
 Avec le`ImageWatermark` instance prête, ajoutez-la à votre document en utilisant le`Add` méthode du`Watermarker` classe.
```csharp
watermarker.Add(watermark);
```
## Étape 6 : Enregistrez le document
Enfin, enregistrez le document filigrané dans le répertoire de sortie spécifié. Cette étape garantit que vos modifications sont écrites dans un nouveau fichier.
```csharp
watermarker.Save(outputFileName);
```
## Conclusion
Toutes nos félicitations! Vous avez ajouté avec succès un filigrane d’image à votre document à l’aide de GroupDocs.Watermark pour .NET. En suivant ce guide étape par étape, vous pouvez facilement protéger vos documents avec des filigranes personnalisés. N'oubliez pas que le filigrane est une étape cruciale pour protéger vos actifs numériques contre toute utilisation non autorisée.

## FAQ
### Quels formats de fichiers sont pris en charge par GroupDocs.Watermark ?
GroupDocs.Watermark prend en charge un large éventail de formats de fichiers, notamment PDF, DOCX, PPTX, XLSX et des fichiers image tels que JPEG et PNG.
### Puis-je utiliser GroupDocs.Watermark avec .NET Core ?
Oui, GroupDocs.Watermark est compatible avec .NET Framework et .NET Core.
### Comment puis-je obtenir une licence temporaire pour GroupDocs.Watermark ?
 Vous pouvez obtenir une licence temporaire auprès du[Site Web GroupDocs](https://purchase.groupdocs.com/temporary-license/).
### Est-il possible d'ajouter plusieurs filigranes à un seul document ?
 Absolument! Vous pouvez ajouter plusieurs filigranes en appelant le`Add` méthode plusieurs fois avec différentes instances de filigrane.
### Où puis-je trouver plus d’exemples et de documentation ?
 Pour plus d'exemples et une documentation détaillée, visitez le[Documentation GroupDocs.Watermark](https://reference.groupdocs.com/Watermark/net/).