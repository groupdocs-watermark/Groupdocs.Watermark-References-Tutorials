---
title: Adicionar marca d'água de texto
linktitle: Adicionar marca d'água de texto
second_title: API GroupDocs.Watermark .NET
description: Aprenda como adicionar marcas d'água de texto aos seus documentos usando Groupdocs Watermark for .NET com este guia passo a passo.
weight: 11
url: /pt/net/watermarking-basics/add-text-watermark/
type: docs
---
# Adicionar marca d'água de texto

## Introdução
GroupDocs.Watermark for .NET é uma biblioteca poderosa que permite aos desenvolvedores adicionar, pesquisar e remover marcas d'água de vários formatos de documentos em aplicativos .NET. Neste tutorial, vamos nos concentrar em adicionar uma marca d'água de texto a um documento usando GroupDocs.Watermark.
## Pré-requisitos
Antes de começarmos, certifique-se de ter os seguintes pré-requisitos:
1. Conhecimento básico da linguagem de programação C#.
2. Visual Studio instalado em seu sistema.
3.  Biblioteca GroupDocs.Watermark para .NET instalada. Você pode baixá-lo em[aqui](https://releases.groupdocs.com/Watermark/net/).

## Importar namespaces
Primeiro, você precisa importar os namespaces necessários para o seu projeto C#.
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Watermarks;
using System;
using System.IO;
```
## Etapa 1: definir o caminho do documento e o diretório de saída
Defina o caminho para o seu documento de entrada e o diretório de saída onde o documento com marca d’água será salvo.
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
 Substituir`"Your Document Path"` pelo caminho absoluto ou relativo para o seu documento de entrada, por exemplo:`@"C:\Docs\document.pdf"`. Além disso, especifique o diretório onde deseja salvar o documento com marca d'água.
## Etapa 2: adicionar marca d’água de texto
 Instancie o`Watermarker` class com o caminho do documento de entrada. Então, crie um`TextWatermark` objeto com as configurações de texto e fonte desejadas.
```csharp
using (Watermarker watermarker = new Watermarker(documentPath))
{
    TextWatermark watermark = new TextWatermark("top secret", new Font("Arial", 36));
    watermark.ForegroundColor = Color.Red;
    watermark.HorizontalAlignment = HorizontalAlignment.Center;
    watermark.VerticalAlignment = VerticalAlignment.Center;
    watermarker.Add(watermark);
    watermarker.Save(outputFileName);
}
```

## Conclusão
Neste tutorial, aprendemos como adicionar uma marca d'água de texto a um documento usando GroupDocs.Watermark for .NET. Com sua API intuitiva, os desenvolvedores podem manipular facilmente marcas d'água em vários formatos de documentos.
## Perguntas frequentes
### O GroupDocs.Watermark for .NET é compatível com todos os formatos de documentos?
GroupDocs.Watermark oferece suporte a uma ampla variedade de formatos de documentos, incluindo PDF, Microsoft Word, Excel, PowerPoint e muitos mais.
### Posso personalizar a aparência da marca d'água do texto?
Sim, você pode personalizar várias propriedades, como fonte, cor, alinhamento e opacidade da marca d'água do texto.
### O GroupDocs.Watermark oferece suporte para remoção de marcas d'água de documentos?
Sim, GroupDocs.Watermark oferece funcionalidade para pesquisar e remover marcas d'água de documentos.
### Posso experimentar o GroupDocs.Watermark for .NET antes de comprar?
 Sim, você pode baixar uma versão de avaliação gratuita em[aqui](https://releases.groupdocs.com/).
### Como posso obter suporte técnico para GroupDocs.Watermark?
 Você pode obter suporte técnico visitando o[Fórum GroupDocs.Watermark](https://forum.groupdocs.com/c/watermark/19).