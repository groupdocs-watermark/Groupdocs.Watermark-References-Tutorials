---
title: Charger un document à partir du disque local
linktitle: Charger un document à partir du disque local
second_title: API GroupDocs.Watermark .NET
description: Protégez et gérez vos documents avec Groupdocs Watermark pour .NET. Suivez notre guide détaillé pour ajouter des filigranes en toute transparence.
weight: 10
url: /fr/net/document-loadings/load-document-from-local-disk/
---
## Introduction
Le tatouage des documents est essentiel à l'ère numérique d'aujourd'hui pour garantir la protection du contenu, l'affirmation de la propriété et la confidentialité. Groupdocs.Watermark for .NET est une bibliothèque puissante qui permet aux développeurs d'ajouter, de rechercher et de gérer des filigranes dans différents formats de documents. Dans ce didacticiel, nous passerons en revue le processus d'utilisation de Groupdocs.Watermark pour .NET pour ajouter des filigranes à vos documents avec des instructions détaillées étape par étape.
## Conditions préalables
Avant de vous lancer dans la mise en œuvre, assurez-vous de disposer des éléments suivants :
1. Visual Studio installé : vous aurez besoin de Visual Studio ou d'un autre IDE .NET compatible.
2.  Groupdocs.Watermark pour .NET : téléchargez la bibliothèque à partir du[lien de téléchargement](https://releases.groupdocs.com/Watermark/net/).
3. .NET Framework : assurez-vous que .NET Framework 4.6.1 ou version ultérieure est installé.
4. Un exemple de document : préparez un exemple de document pour tester le processus de filigrane.
## Importer des espaces de noms
Pour commencer, vous devrez importer les espaces de noms nécessaires dans votre projet. Ceux-ci sont essentiels pour accéder aux classes et méthodes requises pour le tatouage.
```csharp
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Étape 1 : Charger le document à partir du disque local
Tout d’abord, vous devez charger le document depuis votre disque local. Ce document sera celui auquel vous ajouterez un filigrane.
Définissez le chemin du document que vous souhaitez filigraner.
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
```
## Étape 2 : initialiser les options de chargement
 Ensuite, initialisez les options de chargement. Par exemple, si vous travaillez avec un document Word, vous utiliserez`WordProcessingLoadOptions`.
```csharp
var loadOptions = new WordProcessingLoadOptions();
```
## Étape 3 : Créer et configurer un filigrane
 Maintenant, vous allez créer une instance de`Watermarker` classe. Cette instance sera utilisée pour gérer et appliquer des filigranes à votre document.
```csharp
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Ce bloc contiendra d'autres étapes pour ajouter et enregistrer le filigrane
}
```
## Étape 4 : Créer un filigrane
Créez un filigrane de texte. Ce filigrane peut contenir n’importe quel texte de votre choix. Ici, nous utiliserons « Test du filigrane ».
```csharp
TextWatermark watermark = new TextWatermark("Test watermark", new Font("Arial", 12));
```
## Étape 5 : ajouter un filigrane au document
Ajoutez le filigrane créé au document à l'aide du`Add` méthode du`Watermarker` classe.
```csharp
watermarker.Add(watermark);
```
## Étape 6 : Enregistrez le document filigrané
Enfin, enregistrez le document filigrané dans le chemin spécifié.
```csharp
watermarker.Save(outputFileName);
```

## Conclusion
L'ajout de filigranes à vos documents à l'aide de Groupdocs pour .NET est simple et efficace. Ce guide vous a accompagné tout au long du processus, depuis la configuration de votre environnement jusqu'à l'enregistrement d'un document filigrané. Avec cet outil puissant, vous pouvez garantir la protection de vos documents et la sécurité de votre propriété intellectuelle. 
 Pour plus de détails, consultez le[Documentation](https://tutorials.groupdocs.com/Watermark/net/) , et si vous rencontrez des problèmes, le[forum d'entraide](https://forum.groupdocs.com/c/watermark/19) est un excellent endroit pour obtenir de l'aide. 
## FAQ
### Puis-je utiliser des polices personnalisées pour les filigranes ?
Oui, Groupdocs prend en charge les polices personnalisées. Vous pouvez spécifier n'importe quelle police installée sur votre système.
### Quels types de documents sont pris en charge ?
Groupdocs.Watermark prend en charge un large éventail de formats de documents, notamment Word, Excel, PDF, PowerPoint, etc.
### Comment puis-je supprimer un filigrane d’un document ?
 Vous pouvez utiliser le`Remove` méthode fournie par le`Watermarker` classe pour supprimer les filigranes.
### Est-il possible d'ajouter des filigranes d'image ?
 Oui, vous pouvez ajouter des filigranes d'image à l'aide de l'outil`ImageWatermark` classe.
### Puis-je essayer Groupdocs.Watermark gratuitement ?
 Absolument, vous pouvez télécharger un[essai gratuit](https://releases.groupdocs.com/) pour évaluer la bibliothèque avant de l'acheter.