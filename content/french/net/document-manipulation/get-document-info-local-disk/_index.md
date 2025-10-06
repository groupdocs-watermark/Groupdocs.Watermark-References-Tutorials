---
title: Obtenir des informations sur le document à partir du disque local
linktitle: Obtenir des informations sur le document à partir du disque local
second_title: API GroupDocs.Watermark .NET
description: Découvrez comment ajouter, supprimer et extraire des filigranes dans des documents à l'aide de GroupDocs Watermark for .NET avec ce guide complet étape par étape.
weight: 11
url: /fr/net/document-manipulation/get-document-info-local-disk/
type: docs
---
# Obtenir des informations sur le document à partir du disque local

## Introduction
Bienvenue dans le guide ultime sur l'utilisation de GroupDocs.Watermark pour .NET ! Que vous soyez un développeur chevronné ou que vous débutiez tout juste, cet article vous expliquera les bases du filigrane de vos documents avec cet outil puissant. À la fin, vous serez un pro dans l'intégration de filigranes dans vos documents, en vous assurant qu'ils sont protégés et marqués selon vos spécifications.
## Conditions préalables
Avant de plonger dans le guide étape par étape, vous devrez remplir quelques conditions préalables :
1.  .NET Framework : assurez-vous que .NET Framework est installé sur votre système. GroupDocs.Watermark pour .NET est compatible avec différentes versions du .NET Framework, alors vérifiez le[Documentation](https://tutorials.groupdocs.com/Watermark/net/) pour les détails de compatibilité.
2.  GroupDocs.Watermark pour la bibliothèque .NET : téléchargez et installez la dernière version à partir du[page de téléchargement](https://releases.groupdocs.com/Watermark/net/).
3. Environnement de développement : vous devez disposer d'un environnement de développement. Visual Studio est un choix populaire pour le développement .NET.
4. Connaissances de base en C# : Comprendre les bases de la programmation C# vous aidera à suivre les exemples.
## Importer des espaces de noms
Avant de pouvoir utiliser GroupDocs.Watermark pour .NET, vous devez importer les espaces de noms nécessaires dans votre projet. Il s'agit d'un processus simple et essentiel pour accéder aux fonctionnalités de la bibliothèque.
```csharp
using System;
using GroupDocs.Watermark.Common;
```
Décomposons le processus de filigrane d'un document en étapes claires et gérables. Chaque étape est conçue pour vous aider à comprendre et à mettre en œuvre facilement la fonctionnalité.
## Étape 1 : Chargez votre document
 La première étape consiste à charger le document que vous souhaitez filigraner. Cela se fait en utilisant le`Watermarker` classe, qui vous permet d'accéder et de manipuler votre document.
```csharp
using (Watermarker watermarker = new Watermarker("Your Document Path"))
{
    // Le document est maintenant chargé et prêt pour le filigrane
}
```
 Dans cette étape, remplacez`"Your Document Path"` avec le chemin réel vers votre document. Cela initialise le`Watermarker`objet, vous donnant accès à diverses fonctionnalités de tatouage.
## Étape 2 : obtenir des informations sur le document
Avant d'ajouter un filigrane, vous souhaiterez peut-être recueillir des informations sur le document. Cela peut être utile pour personnaliser votre filigrane en fonction des propriétés du document.

```csharp
using (Watermarker watermarker = new Watermarker("Your Document Path"))
{
    IDocumentInfo info = watermarker.GetDocumentInfo();
    Console.WriteLine("File type: {0}", info.FileType);
    Console.WriteLine("Number of pages: {0}", info.PageCount);
    Console.WriteLine("Document size: {0} bytes", info.Size);
}
```
 Dans cette étape, le`GetDocumentInfo` La méthode récupère des détails tels que le type de fichier, le nombre de pages et la taille du document. Ces informations sont imprimées sur la console, mais vous pouvez les utiliser dans votre application selon vos besoins.
## Étape 3 : ajouter un filigrane de texte
Maintenant que votre document est chargé et que ses informations sont à portée de main, il est temps d'ajouter un filigrane. Nous allons commencer par un simple filigrane de texte.

```csharp
using (Watermarker watermarker = new Watermarker("Your Document Path"))
{
    TextWatermark textWatermark = new TextWatermark("Confidential", new Font("Arial", 36));
    textWatermark.ForegroundColor = Color.Red;
    textWatermark.BackgroundColor = Color.Yellow;
    textWatermark.Opacity = 0.5;
    textWatermark.RotateAngle = 45;
    watermarker.Add(textWatermark);
    watermarker.Save("Watermarked Document Path");
}
```
 Ici, vous créez un`TextWatermark` objet avec le texte, la police et le style souhaités. Ajustez les propriétés telles que la couleur, l'opacité et l'angle de rotation en fonction de vos besoins. Enfin, le filigrane est ajouté au document et enregistré dans un chemin spécifié.
## Étape 4 : ajouter un filigrane d'image
Les filigranes de texte sont excellents, mais que se passe-t-il si vous souhaitez ajouter un logo ou une autre image ? Cette étape explique comment ajouter un filigrane d'image.

```csharp
using (Watermarker watermarker = new Watermarker("Your Document Path"))
{
    using (ImageWatermark imageWatermark = new ImageWatermark("Path to Your Image"))
    {
        imageWatermark.Opacity = 0.5;
        imageWatermark.RotateAngle = 30;
        watermarker.Add(imageWatermark);
        watermarker.Save("Watermarked Document Path");
    }
}
```
 Remplacer`"Path to Your Image"` avec le chemin d’accès à votre image en filigrane. Définissez des propriétés telles que l'opacité et l'angle de rotation pour personnaliser l'apparence du filigrane de votre image. Le processus d'ajout et d'enregistrement du filigrane est similaire à celui d'un filigrane de texte.
## Étape 5 : Supprimer les filigranes existants
 Parfois, vous devrez peut-être supprimer les filigranes existants d'un document. Cela peut être fait en utilisant le`Remove` méthode fournie par le`Watermarker` classe.

```csharp
using (Watermarker watermarker = new Watermarker("Your Document Path"))
{
    watermarker.Remove(WatermarkType.Text);
    watermarker.Save("Cleaned Document Path");
}
```
 Ici le`Remove` La méthode est utilisée pour supprimer les filigranes de texte du document. Vous pouvez spécifier différents types de filigranes à supprimer, tels qu'une image ou un texte, en fonction de vos besoins. Enregistrez le document dans un nouveau chemin pour voir les modifications.
## Étape 6 : Extraire les filigranes
Si vous devez extraire et inspecter les filigranes d'un document, GroupDocs.Watermark for .NET rend cela possible en toute simplicité.

```csharp
using (Watermarker watermarker = new Watermarker("Your Document Path"))
{
    IEnumerable<Watermark> watermarks = watermarker.GetWatermarks();
    foreach (Watermark watermark in watermarks)
    {
        Console.WriteLine("Watermark type: {0}", watermark.GetType().Name);
        // Propriétés et logique supplémentaires pour chaque filigrane
    }
}
```
 Cette étape consiste à utiliser le`GetWatermarks`méthode pour récupérer tous les filigranes d’un document. Vous pouvez ensuite parcourir la liste des filigranes et inspecter leurs propriétés ou effectuer des actions supplémentaires si nécessaire.
## Conclusion
 Toutes nos félicitations! Vous avez maintenant appris à utiliser GroupDocs.Watermark pour .NET pour ajouter, supprimer et extraire des filigranes de vos documents. Grâce à ces compétences, vous pouvez protéger et marquer efficacement vos documents. Se souvenir du[Documentation](https://tutorials.groupdocs.com/Watermark/net/) est toujours là si vous avez besoin d'informations plus détaillées ou de fonctionnalités avancées.
## FAQ
### Puis-je utiliser GroupDocs.Watermark pour .NET avec n’importe quelle version de .NET ?
 Oui, GroupDocs.Watermark pour .NET est compatible avec différentes versions de .NET Framework. Vérifier la[Documentation](https://tutorials.groupdocs.com/Watermark/net/) pour des détails.
### Où puis-je télécharger GroupDocs.Watermark pour .NET ?
 Vous pouvez télécharger la dernière version à partir du[page de téléchargement](https://releases.groupdocs.com/Watermark/net/).
### Comment obtenir un permis temporaire ?
 Vous pouvez obtenir une licence temporaire auprès du[page de licence temporaire](https://purchase.groupdocs.com/temporary-license/).
### Existe-t-il un essai gratuit disponible ?
 Oui, vous pouvez démarrer un essai gratuit en visitant le[page d'essai gratuit](https://releases.groupdocs.com/).
### Où puis-je obtenir de l'aide si je rencontre des problèmes ?
 L'assistance est disponible sur le[Forum sur les filigranes GroupDocs](https://forum.groupdocs.com/c/watermark/19).