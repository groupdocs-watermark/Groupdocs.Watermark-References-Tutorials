---
title: Adicionar marca d'água de anotação somente para impressão ao PDF
linktitle: Adicionar marca d'água de anotação somente para impressão ao PDF
second_title: API GroupDocs.Watermark .NET
description: Aprenda como adicionar marcas d'água de anotação somente para impressão em PDFs usando GroupDocs.Watermark for .NET. Melhore a segurança e a marca dos documentos sem esforço.
weight: 13
url: /pt/net/pdf-watermarking-attachments/add-print-only-annotation-watermark-pdf/
---
## Introdução
Neste tutorial, nos aprofundaremos no processo de adição de uma marca d’água de anotação somente para impressão a um PDF usando GroupDocs.Watermark for .NET. Colocar marcas d'água em documentos é um aspecto crucial da segurança e da marca de documentos, e o GroupDocs.Watermark fornece uma solução perfeita para os desenvolvedores .NET conseguirem isso.
## Pré-requisitos
Antes de começarmos, certifique-se de ter os seguintes pré-requisitos:
- Compreensão básica da linguagem de programação C#.
- Visual Studio instalado em sua máquina.
- Biblioteca GroupDocs.Watermark for .NET instalada em seu projeto.

## Importar namespaces
Para começar, certifique-se de importar os namespaces necessários:
```csharp
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Etapa 1: carregue o documento
 Em primeiro lugar, você precisa carregar o documento PDF que deseja colocar a marca d’água. Substituir`"Your Document Path"` com o caminho para o seu arquivo PDF e`"Your Document Directory"` com o diretório onde você deseja salvar o arquivo de saída.
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // O código da marca d'água será adicionado aqui
}
```
## Etapa 2: adicionar marca d'água
 seguir, crie um objeto de marca d’água de texto com o texto e a fonte desejados. Definir`isPrintOnly` para`true` para garantir que a marca d'água só fique visível quando o documento for impresso, não no modo de visualização.
```csharp
TextWatermark textWatermark = new TextWatermark("This is a print only test watermark. It won't appear in view mode.", new Font("Arial", 8));
bool isPrintOnly = true;
```
## Etapa 3: configurar opções de marca d'água
Defina opções para a marca d'água, como o índice da página onde a marca d'água deve ser adicionada e especificando-a como uma anotação somente para impressão.
```csharp
PdfAnnotationWatermarkOptions options = new PdfAnnotationWatermarkOptions();
options.PageIndex = 0;
options.PrintOnly = isPrintOnly;
```
## Etapa 4: aplicar marca d'água
Adicione a marca d’água ao documento usando as opções especificadas e salve o arquivo de saída.
```csharp
watermarker.Add(textWatermark, options);
watermarker.Save(outputFileName);
```

## Conclusão
Neste tutorial, aprendemos como adicionar uma marca d'água de anotação somente para impressão a um documento PDF usando GroupDocs.Watermark for .NET. Isso permite que os desenvolvedores melhorem a segurança e a marca dos documentos com facilidade.
## Perguntas frequentes
### O GroupDocs.Watermark é compatível com outros formatos de documento além do PDF?
Sim, o GroupDocs suporta vários formatos de documentos, como Word, Excel, PowerPoint e imagens.
### Posso personalizar a aparência da marca d'água?
Certamente, GroupDocs.Watermark oferece amplas opções para personalizar texto, fonte, cor, tamanho e posicionamento da marca d’água.
### O GroupDocs.Watermark oferece recursos de processamento em lote?
Com certeza, os desenvolvedores podem marcar vários documentos simultaneamente usando recursos de processamento em lote.
### Existe uma versão de teste disponível para GroupDocs.Watermark?
Sim, você pode acessar uma versão de teste gratuita do GroupDocs.Watermark no link fornecido.
### Como posso obter suporte técnico para GroupDocs.Watermark?
Você pode buscar assistência técnica no fórum GroupDocs.Watermark disponível no link de suporte fornecido.