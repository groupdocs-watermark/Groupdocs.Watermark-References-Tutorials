---
title: Rasterizar página PDF
linktitle: Rasterizar página PDF
second_title: API GroupDocs.Watermark .NET
description: Aumente a segurança dos documentos com GroupDocs para .NET. Adicione marcas d'água a PDF e outros formatos perfeitamente.
weight: 28
url: /pt/net/pdf-watermarking-attachments/rasterize-pdf-page/
---
## Introdução
GroupDocs.Watermark for .NET é uma API poderosa que permite aos desenvolvedores adicionar marcas d'água perfeitamente a vários formatos de documentos, incluindo PDF, Word, Excel, PowerPoint e muito mais. Com sua interface intuitiva e recursos abrangentes, GroupDocs.Watermark simplifica o processo de adição de marcas d’água de texto ou imagem a documentos, permitindo que os usuários protejam sua propriedade intelectual e melhorem a segurança dos documentos sem esforço.
## Pré-requisitos
Antes de começar a usar GroupDocs.Watermark for .NET, certifique-se de ter os seguintes pré-requisitos em vigor:
1. Instalação: Baixe e instale GroupDocs.Watermark for .NET do[página de download](https://releases.groupdocs.com/Watermark/net/).
2.  Licença: Adquira uma licença para GroupDocs.Watermark for .NET. Você pode obter uma licença temporária para fins de avaliação em[aqui](https://purchase.groupdocs.com/temporary-license/) ou adquira uma licença completa do[página de compra](https://purchase.groupdocs.com/buy).
3. .NET Framework: certifique-se de ter o .NET Framework instalado em sua máquina de desenvolvimento.
4. Documento: Prepare o documento ao qual deseja adicionar marcas d'água.

## Importar namespaces
Para começar a usar o GroupDocs.Watermark for .NET, importe os namespaces necessários para o seu projeto:
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Etapa 1: carregue o documento
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Seu código vai aqui
}
```
## Etapa 2: inicializar a marca d’água
```csharp
TextWatermark watermark = new TextWatermark("Do not copy", new Font("Arial", 8));
watermark.HorizontalAlignment = HorizontalAlignment.Center;
watermark.VerticalAlignment = VerticalAlignment.Center;
watermark.RotateAngle = 45;
watermark.SizingType = SizingType.ScaleToParentDimensions;
watermark.ScaleFactor = 1;
watermark.Opacity = 0.5;
```
## Etapa 3: adicionar marca d'água
```csharp
PdfArtifactWatermarkOptions options = new PdfArtifactWatermarkOptions();
options.PageIndex = 0;
watermarker.Add(watermark, options);
```
## Etapa 4: rasterizar a página
```csharp
PdfContent pdfContent = watermarker.GetContent<PdfContent>();
pdfContent.Pages[0].Rasterize(100, 100, PdfImageConversionFormat.Png);
```
## Etapa 5: salve o documento
```csharp
watermarker.Save(outputFileName);
```

## Conclusão
Concluindo, GroupDocs.Watermark for .NET oferece uma solução perfeita para adicionar marcas d'água a PDF e outros formatos de documentos. Seguindo o guia passo a passo descrito acima, os desenvolvedores podem rasterizar páginas PDF com eficiência e aumentar a segurança dos documentos com facilidade.
## Perguntas frequentes
### O GroupDocs.Watermark é compatível com outros formatos de documento além do PDF?
Sim, GroupDocs.Watermark oferece suporte a uma ampla variedade de formatos de documentos, incluindo Word, Excel, PowerPoint, Visio e muito mais.
### Posso personalizar a aparência da marca d'água adicionada ao documento?
Absolutamente! GroupDocs.Watermark oferece amplas opções de personalização para marcas d'água de texto e imagem, permitindo aos usuários ajustar a fonte, tamanho, cor, opacidade e posicionamento de acordo com suas preferências.
### O GroupDocs.Watermark é adequado para uso pessoal e comercial?
Sim, o GroupDocs.Watermark oferece opções flexíveis de licenciamento para atender às necessidades individuais e empresariais, tornando-o adequado para projetos pessoais, bem como para aplicações comerciais em grande escala.
### O GroupDocs.Watermark oferece suporte técnico para desenvolvedores?
Sim, os desenvolvedores podem acessar suporte técnico abrangente por meio do fórum GroupDocs.Watermark, onde podem buscar assistência, compartilhar experiências e interagir com outros desenvolvedores.
### Posso experimentar o GroupDocs.Watermark antes de fazer uma compra?
Certamente! Você pode aproveitar uma versão de teste gratuita do GroupDocs.Watermark no site[página de lançamentos](https://releases.groupdocs.com/), permitindo que você explore seus recursos e funcionalidades antes de se comprometer com uma compra.