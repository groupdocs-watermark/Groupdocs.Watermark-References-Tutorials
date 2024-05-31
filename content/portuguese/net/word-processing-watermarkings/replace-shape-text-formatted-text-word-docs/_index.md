---
title: Substitua o texto da forma por texto formatado em documentos do Word
linktitle: Substitua o texto da forma por texto formatado em documentos do Word
second_title: API GroupDocs.Watermark .NET
description: Aprenda como substituir texto de forma por texto formatado em documentos do Word usando GroupDocs.Watermark for .NET. Seus recursos de edição de documentos sem esforço.
type: docs
weight: 34
url: /pt/net/word-processing-watermarkings/replace-shape-text-formatted-text-word-docs/
---
## Introdução
Neste tutorial, orientaremos você no processo de substituição de texto de forma por texto formatado em documentos do Word usando GroupDocs.Watermark for .NET. Esta biblioteca oferece recursos poderosos para trabalhar com marcas d'água, incluindo a substituição de texto em formas.
## Pré-requisitos
Antes de começarmos, certifique-se de ter os seguintes pré-requisitos:
1.  GroupDocs.Watermark for .NET: certifique-se de ter instalado e configurado GroupDocs.Watermark for .NET. Você pode baixá-lo em[aqui](https://releases.groupdocs.com/Watermark/net/).
2. Caminho do documento: você deve ter o caminho para o documento do Word onde deseja substituir o texto.

## Importar namespaces
Antes de escrever o código, importe os namespaces necessários:
```csharp
using GroupDocs.Watermark.Contents.WordProcessing;
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Etapa 1: carregue o documento
 Carregue o documento do Word usando o`Watermarker` aula:
```csharp
string documentPath = "Your Document Path";
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Seu código continua aqui...
}
```
## Etapa 2: obter conteúdo e substituir texto
Assim que o documento for carregado, obtenha o conteúdo e substitua o texto nas formas:
```csharp
WordProcessingContent content = watermarker.GetContent<WordProcessingContent>();
foreach (WordProcessingShape shape in content.Sections[0].Shapes)
{
    if (shape.Text.Contains("Some text"))
    {
        shape.FormattedTextFragments.Clear();
        shape.FormattedTextFragments.Add("Another text", new Font("Calibri", 19, FontStyle.Bold), Color.Red, Color.Aqua);
    }
}
```
## Etapa 3: salve o documento
Após substituir o texto, salve o documento modificado:
```csharp
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
watermarker.Save(outputFileName);
```

## Conclusão
Substituir texto de forma por texto formatado em documentos do Word é facilitado com GroupDocs para .NET. Seguindo as etapas descritas neste tutorial, você pode gerenciar e manipular texto de maneira eficiente em seus documentos.

## Perguntas frequentes
### Posso substituir texto em outros tipos de documentos usando GroupDocs.Watermark for .NET?
Sim, o GroupDocs suporta vários formatos de documentos, como PDF, Excel, PowerPoint e muito mais.
### O GroupDocs.Watermark é compatível com o .NET Core?
Sim, GroupDocs.Watermark oferece suporte a .NET Framework e .NET Core.
### O GroupDocs.Watermark oferece suporte para adição de imagens como marcas d'água?
Com certeza, GroupDocs.Watermark permite adicionar marcas d’água de texto e imagem aos seus documentos.
### Posso personalizar a aparência das marcas d'água adicionadas usando GroupDocs.Watermark?
Sim, você tem controle total sobre a aparência, posição e outras propriedades das marcas d’água.
### Existe uma versão de teste disponível para GroupDocs.Watermark for .NET?
 Sim, você pode baixar uma avaliação gratuita em[aqui](https://releases.groupdocs.com/).