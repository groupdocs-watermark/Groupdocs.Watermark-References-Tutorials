---
title: Adicionar marca d'água de imagem lado a lado
linktitle: Adicionar marca d'água de imagem lado a lado
second_title: API GroupDocs.Watermark .NET
description: Aprenda como adicionar marcas d'água de imagem lado a lado aos seus documentos usando GroupDocs.Watermark for .NET. Fácil, eficiente e personalizável.
weight: 10
url: /pt/net/image-watermarkings/add-tiled-image-watermark/
type: docs
---
# Adicionar marca d'água de imagem lado a lado

## Introdução
GroupDocs.Watermark for .NET é uma API poderosa que permite aos desenvolvedores adicionar, remover e pesquisar marcas d'água em vários formatos de documentos de forma programática. Neste tutorial, orientaremos você no processo de adição de uma marca d'água de imagem lado a lado aos seus documentos usando GroupDocs.Watermark for .NET.
## Pré-requisitos
Antes de começar, certifique-se de ter o seguinte:
- Conhecimento básico da linguagem de programação C#.
- Visual Studio instalado em seu sistema.
- Biblioteca GroupDocs.Watermark for .NET adicionada ao seu projeto. Você pode baixá-lo em[aqui](https://releases.groupdocs.com/Watermark/net/).

## Importar namespaces
Certifique-se de importar os namespaces necessários no início do seu arquivo C#:
```csharp
using GroupDocs.Watermark.Watermarks;
using System;
using System.IO;
```
## Etapa 1: definir o caminho do documento e o diretório de saída
Defina o caminho do seu documento de entrada e o diretório onde deseja salvar o documento de saída:
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
 Substituir`"Your Document Path"` com o caminho absoluto ou relativo para o seu documento de entrada.
## Etapa 2: inicializar o objeto Watermarker
Crie um objeto Watermarker usando o caminho do documento de entrada:
```csharp
using (Watermarker watermarker = new Watermarker(documentPath))
{
    // Adicione marca d'água aqui
}
```
## Etapa 3: adicionar marca d'água de imagem lado a lado
Instancie um objeto ImageWatermark com o caminho para o arquivo de imagem que você deseja usar como marca d'água:
```csharp
using (ImageWatermark watermark = new ImageWatermark("Path to Your Image"))
{
    // Configurar opções de bloco
    watermark.TileOptions = new TileOptions()
    {
        TileType = TileType.Offset,
        LineSpacing = new MeasureValue()
        {
            MeasureType = TileMeasureType.Percent,
            Value = 12
        },
        WatermarkSpacing = new MeasureValue()
        {
            MeasureType = TileMeasureType.Percent,
            Value = 10
        },
    };
    watermark.RotateAngle = -30;
    // Adicione marca d'água ao documento
    watermarker.Add(watermark);
    // Salve o documento modificado
    watermarker.Save(outputFileName);
}
```
 Substituir`"Path to Your Image"` com o caminho real para o arquivo de imagem da marca d'água.

## Conclusão
Seguindo essas etapas, você pode adicionar facilmente uma marca d'água de imagem lado a lado aos seus documentos usando GroupDocs.Watermark for .NET. Experimente diferentes opções e configurações para alcançar o resultado desejado.
## Perguntas frequentes
### Posso adicionar várias marcas d'água a um único documento?
Sim, você pode adicionar várias marcas d’água de diferentes tipos a um documento usando GroupDocs.Watermark for .NET.
### O GroupDocs.Watermark oferece suporte a todos os formatos de documento?
GroupDocs.Watermark oferece suporte a uma ampla variedade de formatos de documentos, incluindo PDF, Word, Excel, PowerPoint e muitos mais.
### Existe uma versão de teste disponível para GroupDocs.Watermark?
 Sim, você pode baixar uma versão de avaliação gratuita em[aqui](https://releases.groupdocs.com/).
### Posso personalizar a aparência da marca d'água?
Sim, você pode personalizar vários aspectos da marca d'água, como posição, tamanho, rotação, transparência, etc.
### O GroupDocs.Watermark oferece suporte técnico?
 Sim, você pode obter suporte técnico no fórum GroupDocs.Watermark[aqui](https://forum.groupdocs.com/c/watermark/19).