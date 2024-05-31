---
title: Adicionar marca d'água com configurações de forma em documentos do Word
linktitle: Adicionar marca d'água com configurações de forma em documentos do Word
second_title: API GroupDocs.Watermark .NET
description: Aprenda como adicionar marcas d’água com configurações de forma a documentos do Word usando GroupDocs para .NET. Proteja seus documentos de forma eficaz.
type: docs
weight: 20
url: /pt/net/word-processing-watermarkings/add-watermark-shape-settings-word-docs/
---
## Introdução
Neste tutorial, percorreremos o processo de adição de uma marca d'água com configurações de forma a documentos do Word usando GroupDocs.Watermark for .NET.
## Pré-requisitos
Antes de começarmos, certifique-se de ter o seguinte:
1.  GroupDocs.Watermark para .NET instalado. Você pode baixá-lo em[aqui](https://releases.groupdocs.com/Watermark/net/).
2. Conhecimento básico de programação C#.
3. Uma compreensão do processamento de documentos do Word.

## Importar namespaces
Primeiro, você precisa importar os namespaces necessários para acessar as classes e métodos necessários.
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Etapa 1: carregue o documento
Carregue o documento do Word onde deseja adicionar a marca d’água.
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // O código de adição de marca d'água vai aqui
}
```
## Etapa 2: adicionar marca d'água
 Instanciar um`TextWatermark` objeto e especifique o texto que deseja usar como marca d'água.
```csharp
TextWatermark watermark = new TextWatermark("Test watermark", new Font("Arial", 19));
```
## Etapa 3: personalizar as configurações da marca d'água
Defina várias configurações para a marca d'água, como alinhamento, ângulo de rotação, cor e opacidade.
```csharp
watermark.VerticalAlignment = VerticalAlignment.Center;
watermark.HorizontalAlignment = HorizontalAlignment.Center;
watermark.RotateAngle = 25.0;
watermark.ForegroundColor = Color.Red;
watermark.Opacity = 1.0;
```
## Etapa 4: definir opções de seção de marca d'água
Defina opções para a seção de marca d'água, como nome da forma e texto alternativo.
```csharp
WordProcessingWatermarkSectionOptions options = new WordProcessingWatermarkSectionOptions();
options.Name = "Shape 1";
options.AlternativeText = "Test watermark";
```
## Etapa 5: adicionar marca d'água ao documento
Adicione a marca d’água ao documento com as opções especificadas.
```csharp
watermarker.Add(watermark, options);
```
## Etapa 6: salve o documento
Salve o documento com a marca d'água adicionada.
```csharp
watermarker.Save(outputFileName);
```

## Conclusão
Adicionar marcas d’água com configurações de forma a documentos do Word usando GroupDocs para .NET é um processo simples. Seguindo as etapas descritas neste tutorial, você pode proteger seus documentos de maneira eficaz com marcas d’água personalizadas.
## Perguntas frequentes
### Posso adicionar várias marcas d'água ao mesmo documento?
Sim, você pode adicionar várias marcas d'água com configurações diferentes ao mesmo documento.
### O GroupDocs.Watermark oferece suporte a outros formatos de documento além do Word?
Sim, GroupDocs.Watermark oferece suporte a vários formatos de documento, incluindo Excel, PowerPoint, PDF e muito mais.
### Posso personalizar ainda mais a aparência da marca d'água?
Com certeza, você pode ajustar vários parâmetros, como tamanho da fonte, estilo, cor e posição para atender às suas necessidades.
### Existe uma versão de teste disponível para GroupDocs.Watermark for .NET?
 Sim, você pode obter um teste gratuito em[aqui](https://releases.groupdocs.com/).
### Onde posso encontrar suporte para GroupDocs.Watermark?
 Você pode encontrar suporte e fazer perguntas no fórum GroupDocs[aqui](https://forum.groupdocs.com/c/watermark/19).