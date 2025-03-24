---
title: Adicionar marca d'água de artefato ao PDF
linktitle: Adicionar marca d'água de artefato ao PDF
second_title: API GroupDocs.Watermark .NET
description: Aprenda como adicionar marcas d’água de artefato a arquivos PDF sem esforço usando Groupdocs.Watermark for .NET. Proteja seus documentos com facilidade.
weight: 11
url: /pt/net/pdf-watermarking-attachments/add-artifact-watermark-pdf/
---
## Introdução
Adicionar marcas d'água a arquivos PDF é um aspecto crucial do gerenciamento de documentos, especialmente quando se trata de proteger a propriedade intelectual ou a marca de documentos. Groupdocs.Watermark for .NET fornece uma solução robusta para adicionar marcas d’água a arquivos PDF sem esforço. Neste tutorial, percorreremos passo a passo o processo de adição de uma marca d'água de artefato a arquivos PDF.
## Pré-requisitos
Antes de começarmos, certifique-se de ter os seguintes pré-requisitos:
1.  Groupdocs.Watermark para .NET: Baixe e instale Groupdocs.Watermark para .NET em[aqui](https://releases.groupdocs.com/Watermark/net/).
2. Ambiente de desenvolvimento: configure um ambiente de desenvolvimento .NET.
3. Documento PDF: Prepare o documento PDF ao qual deseja adicionar a marca d’água.
4. Diretório de saída: Crie um diretório para salvar o arquivo PDF com marca d'água.

## Importando Namespaces
Para começar, importe os namespaces necessários em seu projeto C#:
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Passo 1: Carregue o Documento PDF
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
```
## Etapa 2: definir opções de marca d’água
```csharp
PdfArtifactWatermarkOptions options = new PdfArtifactWatermarkOptions();
```
## Etapa 3: adicionar marca d’água de texto
```csharp
TextWatermark textWatermark = new TextWatermark("This is an artifact watermark", new Font("Arial", 8));
textWatermark.HorizontalAlignment = HorizontalAlignment.Right;
watermarker.Add(textWatermark, options);
```
## Etapa 4: adicionar marca d'água de imagem
```csharp
using (ImageWatermark imageWatermark = new ImageWatermark(Constants.LogoBmp))
{
    watermarker.Add(imageWatermark, options);
}
```
## Etapa 5: salve o PDF com marca d’água
```csharp
watermarker.Save(outputFileName);
```

## Conclusão
Neste tutorial, aprendemos como adicionar marcas d’água de artefato a arquivos PDF usando Groupdocs.Watermark for .NET. Seguindo essas etapas, você pode integrar perfeitamente a funcionalidade de marca d’água em seus aplicativos .NET, garantindo a segurança e a integridade de seus documentos.
## Perguntas frequentes
### Posso personalizar a aparência da marca d'água do texto?
Sim, você pode personalizar vários aspectos como fonte, tamanho, cor e alinhamento da marca d’água do texto de acordo com suas preferências.
### O Groupdocs.Watermark suporta a adição de marcas d'água a outros formatos de documentos?
Sim, Groupdocs.Watermark suporta a adição de marcas d'água a uma ampla variedade de formatos de documentos, incluindo Word, Excel, PowerPoint e muito mais.
### Existe uma versão de teste disponível para Groupdocs.Watermark for .NET?
 Sim, você pode baixar uma versão de avaliação gratuita em[aqui](https://releases.groupdocs.com/).
### Como posso obter suporte para quaisquer problemas ou dúvidas relacionadas ao Groupdocs.Watermark?
 Você pode obter suporte no fórum da comunidade Groupdocs[aqui](https://forum.groupdocs.com/c/watermark/19).
### Posso usar Groupdocs.Watermark para fins comerciais?
Sim, você pode adquirir uma licença para uso comercial em[aqui](https://purchase.groupdocs.com/buy).