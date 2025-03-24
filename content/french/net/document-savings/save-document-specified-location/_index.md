---
title: Enregistrer le document à l'emplacement spécifié
linktitle: Enregistrer le document à l'emplacement spécifié
second_title: API GroupDocs.Watermark .NET
description: Découvrez comment ajouter facilement des filigranes à vos documents à l'aide de GroupDocs.Watermark for .NET avec ce guide étape par étape. Améliorez la sécurité des documents.
weight: 11
url: /fr/net/document-savings/save-document-specified-location/
---

# Enregistrer le document à l'emplacement spécifié

## Introduction
À l’ère du numérique, la sécurisation des documents est devenue plus cruciale que jamais. Le filigrane est un moyen efficace de protéger vos documents contre toute utilisation non autorisée. GroupDocs.Watermark for .NET offre une solution robuste pour ajouter des filigranes à vos documents. Que vous soyez un développeur cherchant à intégrer le filigrane dans votre application ou une personne intéressée par la protection de vos documents, ce didacticiel vous guidera pas à pas tout au long du processus.
## Conditions préalables
Avant de plonger dans le didacticiel, assurez-vous que les conditions préalables suivantes sont remplies :
- Environnement de développement .NET : assurez-vous que Visual Studio ou tout autre environnement de développement .NET est installé.
-  GroupDocs.Watermark pour la bibliothèque .NET : téléchargez et référencez la bibliothèque dans votre projet.[Téléchargez GroupDocs.Watermark pour .NET](https://releases.groupdocs.com/Watermark/net/)
- Connaissance de base de la programmation C# : Comprendre les concepts de base de la programmation C# sera utile.
- Document à filigraner : préparez un exemple de document auquel vous souhaitez appliquer le filigrane.
## Importer des espaces de noms
Avant de commencer avec l'exemple, vous devez importer les espaces de noms nécessaires. Ajoutez les instructions using suivantes en haut de votre fichier de code :
```csharp
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
Décomposons le processus d'ajout d'un filigrane à un document à l'aide de GroupDocs.Watermark pour .NET en étapes gérables. Suivez ces étapes pour appliquer avec succès un filigrane et enregistrer votre document à un emplacement spécifié.
## Étape 1 : Configurez votre projet
Commencez par créer un nouveau projet .NET dans Visual Studio. Vous pouvez choisir une application console pour plus de simplicité.
1. Ouvrez Visual Studio.
2.  Sélectionner`File` >`New` >`Project`.
3.  Choisir`Console App (.NET Core)` ou`Console App (.NET Framework)`.
4.  Nommez votre projet et cliquez`Create`.

## Étape 2 : Préparez votre document et le texte du filigrane
### Spécifier le chemin du document
Définissez le chemin du document que vous souhaitez filigraner. Pour cet exemple, utilisons un chemin d'espace réservé.
```csharp
string documentPath = "Your Document Path";
```
### Définir le chemin de sortie
Configurez le chemin de sortie où vous souhaitez que le document filigrané soit enregistré.
```csharp
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
```
## Étape 3 : Charger le document
 Utilisez le`Watermarker` classe pour charger votre document. Cette classe fournit des méthodes pour ajouter, supprimer et modifier des filigranes.
```csharp
using (Watermarker watermarker = new Watermarker(documentPath))
{
    // Ajoutez une logique de filigrane ici
}
```
## Étape 4 : Créer et ajouter un filigrane

### Créer un filigrane de texte
 Instancier un`TextWatermark` objet avec les propriétés de texte et de police souhaitées.
```csharp
TextWatermark watermark = new TextWatermark("Test watermark", new Font("Arial", 12));
```
### Ajouter un filigrane au document
 Ajoutez le filigrane créé à votre document à l'aide du`Add` méthode du`Watermarker` classe.
```csharp
watermarker.Add(watermark);
```
## Étape 5 : Enregistrez le document
Enfin, enregistrez le document avec le filigrane à l'emplacement spécifié.
```csharp
watermarker.Save(outputFileName);
```
## Conclusion
Le filigrane de vos documents à l'aide de GroupDocs pour .NET est un processus simple qui peut améliorer considérablement la sécurité de vos documents. En suivant ce guide étape par étape, vous pouvez facilement ajouter des filigranes à vos documents et les enregistrer à l'emplacement souhaité. Que vous protégiez la propriété intellectuelle, garantissiez l'authenticité d'un document ou ajoutiez simplement une touche professionnelle, GroupDocs.Watermark for .NET fournit les outils dont vous avez besoin.
## FAQ
### Puis-je utiliser des images comme filigranes avec GroupDocs.Watermark pour .NET ?
Oui, vous pouvez utiliser des filigranes de texte et d'image avec GroupDocs Watermark for .NET. La bibliothèque prend en charge différents types de filigranes pour répondre à vos besoins.
### Existe-t-il un essai gratuit disponible pour GroupDocs.Watermark pour .NET ?
 Oui, vous pouvez télécharger un essai gratuit à partir du[site web](https://releases.groupdocs.com/).
### Comment puis-je acheter une licence pour GroupDocs.Watermark pour .NET ?
 Vous pouvez acheter une licence auprès du[page d'achat](https://purchase.groupdocs.com/buy).
### GroupDocs.Watermark pour .NET prend-il en charge le filigrane par lots ?
Oui, vous pouvez filigraner plusieurs documents dans un processus par lots en parcourant une liste de documents et en appliquant des filigranes.
### Où puis-je obtenir de l’assistance pour GroupDocs.Watermark pour .NET ?
 L'assistance est disponible sur le[Forum GroupDocs](https://forum.groupdocs.com/c/watermark/19).