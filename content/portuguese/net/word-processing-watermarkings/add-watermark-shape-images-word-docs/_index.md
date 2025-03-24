---
title: Adicionar marca d’água a imagens de formato em documentos do Word
linktitle: Adicionar marca d’água a imagens de formato em documentos do Word
second_title: API GroupDocs.Watermark .NET
description: Aprenda como adicionar marcas d'água para moldar imagens em documentos do Word usando GroupDocs.Watermark for .NET. Aumente a segurança dos documentos com este tutorial.
weight: 17
url: /pt/net/word-processing-watermarkings/add-watermark-shape-images-word-docs/
---
## Introdução
Neste tutorial, exploraremos como adicionar uma marca d'água para moldar imagens em documentos do Word usando GroupDocs.Watermark for .NET. A marca d'água é um aspecto crucial da proteção de documentos, especialmente quando se trata de informações sensíveis ou confidenciais. Ao adicionar marcas d'água para moldar imagens, você pode garantir a integridade e segurança de seus documentos.
## Pré-requisitos
Antes de começarmos, certifique-se de ter o seguinte:
1.  GroupDocs.Watermark para .NET: Baixe e instale a biblioteca GroupDocs.Watermark do[página de download](https://releases.groupdocs.com/Watermark/net/).
2. Documento: Prepare o documento Word onde deseja adicionar a marca d'água.
3. Ambiente de desenvolvimento: configure seu ambiente de desenvolvimento .NET preferido.
## Importar namespaces
Antes de escrever o código, importe os namespaces necessários:
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.WordProcessing;
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Etapa 1: carregue o documento
Primeiro, defina o caminho para o seu documento e especifique o nome do arquivo de saída:
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
```
## Etapa 2: inicializar o marcador d’água
 Instanciar um`Watermarker` objeto fornecendo o caminho do documento e opções de carregamento opcionais:
```csharp
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Adicione lógica de marca d'água aqui
}
```
## Etapa 3: criar marca d'água de texto
Defina a marca d’água do texto com as propriedades desejadas, como texto, fonte, alinhamento, rotação, dimensionamento, etc.:
```csharp
TextWatermark watermark = new TextWatermark("Protected image", new Font("Arial", 8));
watermark.HorizontalAlignment = HorizontalAlignment.Center;
watermark.VerticalAlignment = VerticalAlignment.Center;
watermark.RotateAngle = 45;
watermark.SizingType = SizingType.ScaleToParentDimensions;
watermark.ScaleFactor = 1;
```
## Etapa 4: aplicar marca d’água em imagens de formato
Itere pelas seções e formas do documento para identificar imagens de formas e adicionar a marca d'água:
```csharp
WordProcessingContent content = watermarker.GetContent<WordProcessingContent>();
foreach (WordProcessingSection section in content.Sections)
{
    foreach (WordProcessingShape shape in section.Shapes)
    {
        if (shape.HeaderFooter == null && shape.Image != null)
        {
            shape.Image.Add(watermark);
        }
    }
}
```
## Etapa 5: salve o documento
Salve o documento com a marca d’água adicionada no arquivo de saída especificado:
```csharp
watermarker.Save(outputFileName);
```

## Conclusão
Neste tutorial, aprendemos como adicionar marcas d'água para moldar imagens em documentos do Word usando GroupDocs.Watermark for .NET. Seguindo o guia passo a passo e aproveitando os recursos poderosos do GroupDocs.Watermark, você pode aumentar a segurança e a proteção de seus documentos de forma eficaz.
## Perguntas frequentes
### Posso personalizar a aparência do texto da marca d'água?
Sim, você pode ajustar várias propriedades como fonte, tamanho, cor, ângulo de rotação e alinhamento para personalizar a marca d’água de acordo com suas preferências.
### O GroupDocs.Watermark oferece suporte a outros formatos de documento além do Word?
Sim, GroupDocs.Watermark oferece suporte para uma ampla variedade de formatos de documentos, incluindo PDF, Excel, PowerPoint e muito mais.
### É possível adicionar várias marcas d’água em um único documento?
Com certeza, você pode adicionar várias marcas d’água com diferentes conteúdos, estilos e posições no mesmo documento.
### Posso remover marcas d'água de documentos usando GroupDocs.Watermark?
Sim, GroupDocs.Watermark oferece recursos para detectar e remover marcas d’água de documentos com eficiência.
### O GroupDocs.Watermark oferece compatibilidade entre plataformas?
Sim, GroupDocs.Watermark é compatível com .NET Framework, .NET Core e .NET Standard, garantindo integração perfeita em diferentes plataformas.