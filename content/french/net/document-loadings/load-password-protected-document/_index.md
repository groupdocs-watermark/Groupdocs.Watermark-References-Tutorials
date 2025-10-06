---
title: Charger un document protégé par mot de passe
linktitle: Charger un document protégé par mot de passe
second_title: API GroupDocs.Watermark .NET
description: Découvrez comment ajouter des filigranes à des documents protégés par mot de passe à l'aide de Groupdocs Watermark for .NET avec notre guide étape par étape. Sécurisez et marquez vos fichiers facilement.
weight: 13
url: /fr/net/document-loadings/load-password-protected-document/
type: docs
---
# Charger un document protégé par mot de passe

## Introduction
Cherchez-vous à protéger vos documents en ajoutant des filigranes, même s'ils sont protégés par mot de passe ? Groupdocs.Watermark for .NET est un outil puissant qui vous permet de faire exactement cela. Dans ce didacticiel, nous vous guiderons tout au long du processus de chargement d'un document protégé par mot de passe et d'ajout d'un filigrane à l'aide de Groupdocs.Watermark pour .NET. Allons-y !
## Conditions préalables
Avant de commencer, assurez-vous d'avoir les éléments suivants :
1. Visual Studio : toute version de Visual Studio installée sur votre ordinateur.
2. .NET Framework : assurez-vous que vous disposez de .NET Framework 4.6.1 ou version ultérieure.
3. Groupdocs.Watermark pour .NET : téléchargez et installez la bibliothèque Groupdocs.Watermark pour .NET à partir du[lien de téléchargement](https://releases.groupdocs.com/Watermark/net/).
## Importer des espaces de noms
Tout d’abord, nous devons importer les espaces de noms nécessaires dans notre projet. Cela garantit que nous pouvons accéder à toutes les méthodes et propriétés fournies par Groupdocs.Watermark pour .NET.
```csharp
using GroupDocs.Watermark.Options;
using GroupDocs.Watermark.Watermarks;
using System;
using System.IO;
```
Maintenant, décomposons le processus en étapes simples et faciles à suivre.
## Étape 1 : Configurez votre projet
Pour commencer, créez une nouvelle application console C# dans Visual Studio. Une fois votre projet configuré, installez la bibliothèque Groupdocs.Watermark pour .NET via NuGet Package Manager.
1. Ouvrez Visual Studio et créez une nouvelle application console (.NET Framework).
2.  Aller à`Tools` >`NuGet Package Manager` >`Manage NuGet Packages for Solution`.
3.  Rechercher`GroupDocs.Watermark` et installez le paquet.
## Étape 2 : Définir les chemins des documents
Ensuite, vous devrez définir le chemin d'accès à votre document protégé par mot de passe et le chemin du fichier de sortie où le document filigrané sera enregistré.
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
```
 Remplacer`"Your Document Path"` et`"Your Document Directory"` avec les chemins réels sur votre machine.
## Étape 3 : Définir les options de chargement avec mot de passe
Pour ouvrir un document protégé par mot de passe, vous devez fournir le mot de passe dans les options de chargement.
```csharp
LoadOptions loadOptions = new LoadOptions();
loadOptions.Password = "P@$w0rd";
```
 Remplacer`"P@$w0rd"` avec le mot de passe réel de votre document.
## Étape 4 : Charger le document
 Maintenant, chargeons le document en utilisant le`Watermarker` classe.
```csharp
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Votre code pour ajouter un filigrane ira ici
}
```
## Étape 5 : Créer un filigrane
Nous allons créer un filigrane de texte que nous pourrons ajouter au document. Vous pouvez personnaliser le texte, la police, la taille et d'autres propriétés selon vos besoins.
```csharp
TextWatermark watermark = new TextWatermark("Test watermark", new Font("Arial", 12));
```
 N'hésitez pas à changer`"Test watermark"`, `"Arial"` , et`12` à votre texte, police et taille préférés.
## Étape 6 : ajouter le filigrane
 Ajoutez le filigrane au document à l'aide du`Add` méthode du`Watermarker` classe.
```csharp
watermarker.Add(watermark);
```
## Étape 7 : Enregistrez le document filigrané
Enfin, enregistrez le document filigrané dans le chemin du fichier de sortie spécifié.
```csharp
watermarker.Save(outputFileName);
```
## Conclusion
L'ajout de filigranes à vos documents protégés par mot de passe est un processus simple avec Groupdocs Watermark for .NET. En suivant ces étapes simples, vous pouvez vous assurer que vos documents sont protégés et marqués selon vos besoins. Qu'il s'agisse de sécurité, de branding ou de conformité, filigraner vos documents n'a jamais été aussi simple.
## FAQ
### Puis-je ajouter des filigranes d’image à l’aide de Groupdocs.Watermark pour .NET ?
 Oui, vous pouvez ajouter des filigranes de texte et d’image. Utilisez simplement le`ImageWatermark` classe au lieu de`TextWatermark`.
### Est-il possible de supprimer les filigranes d’un document ?
Oui, Groupdocs.Watermark pour .NET fournit des méthodes pour rechercher et supprimer des filigranes.
### Groupdocs.Watermark pour .NET prend-il en charge d'autres formats de documents que les PDF ?
Oui, il prend en charge un large éventail de formats, notamment Word, Excel, PowerPoint, etc.
### Puis-je personnaliser l’apparence du filigrane ?
Absolument! Vous pouvez personnaliser la police, la taille, la couleur, l'opacité, etc.
### Où puis-je obtenir de l'aide si je rencontre des problèmes ?
 Vous pouvez visiter le[Forum d'assistance Groupdocs](https://forum.groupdocs.com/c/watermark/19) pour obtenir de l'aide et des conseils.