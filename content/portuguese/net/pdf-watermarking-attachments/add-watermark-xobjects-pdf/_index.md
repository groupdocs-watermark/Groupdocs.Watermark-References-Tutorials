---
title: Adicionar marca d'água em XObjects em PDF
linktitle: Adicionar marca d'água em XObjects em PDF
second_title: API GroupDocs.Watermark .NET
description: Aprenda como adicionar marcas d'água em XObjects em PDF usando Groupdocs.Watermark for .NET. Siga nosso guia passo a passo para fácil implementação.
weight: 20
url: /pt/net/pdf-watermarking-attachments/add-watermark-xobjects-pdf/
type: docs
---
# Adicionar marca d'água em XObjects em PDF

## Introdução
Marcar PDFs com marca d'água é uma etapa crucial para garantir que seus documentos estejam protegidos contra uso não autorizado. Com Groupdocs.Watermark for .NET, adicionar marcas d'água em XObjects dentro de seus PDFs nunca foi tão fácil. Neste tutorial, orientaremos você no processo passo a passo, garantindo que você possa aplicar marcas d'água em seus documentos PDF com segurança. Vamos começar!
## Pré-requisitos
Antes de mergulhar no tutorial, vamos garantir que você tenha tudo o que precisa para acompanhar perfeitamente:
-  Groupdocs.Watermark for .NET: Baixe e instale a versão mais recente em[aqui](https://releases.groupdocs.com/Watermark/net/).
- .NET Framework: certifique-se de ter o .NET Framework instalado em sua máquina de desenvolvimento.
- Ambiente de desenvolvimento: Use Visual Studio ou qualquer outro IDE que suporte desenvolvimento .NET.
-  Licença Temporária: Obtenha uma[licença temporária](https://purchase.groupdocs.com/temporary-license/) se você estiver avaliando o produto.
Depois de cumprir esses pré-requisitos, você estará pronto para começar a colocar marcas d'água em seus PDFs.
## Importar namespaces
Primeiro, você precisará importar os namespaces necessários para o seu projeto. Abra seu projeto C# e adicione o seguinte usando diretivas:
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Etapa 1: configure os caminhos do seu documento
A primeira etapa envolve configurar os caminhos do seu documento. Defina o caminho onde seu PDF está localizado e onde deseja salvar o PDF com marca d’água.
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
 Substituir`"Your Document Path"` e`"Your Document Directory"` com os caminhos reais em sua máquina.
## Etapa 2: inicializar as opções de carregamento do PDF
Em seguida, você precisará inicializar as opções de carregamento do PDF. Isto é crucial para carregar o conteúdo do PDF corretamente.
```csharp
var loadOptions = new PdfLoadOptions();
```
## Passo 3: Carregue o Documento PDF
Usando as opções de carregamento, carregue o documento PDF com o`Watermarker` aula.
```csharp
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    PdfContent pdfContent = watermarker.GetContent<PdfContent>();
```
## Etapa 4: crie a marca d’água
Agora você precisa criar a marca d'água que será adicionada ao PDF. Para este tutorial, criaremos uma marca d'água de texto.
```csharp
TextWatermark watermark = new TextWatermark("Protected image", new Font("Arial", 8))
{
    HorizontalAlignment = HorizontalAlignment.Center,
    VerticalAlignment = VerticalAlignment.Center,
    RotateAngle = 45,
    SizingType = SizingType.ScaleToParentDimensions,
    ScaleFactor = 1
};
```
## Passo 5: Adicionar Marca D'água aos XObjects
Itere cada página e cada XObject dentro do PDF para aplicar a marca d'água.
```csharp
foreach (PdfPage page in pdfContent.Pages)
{
    foreach (PdfXObject xObject in page.XObjects)
    {
        if (xObject.Image != null)
        {
            // Adicione marca d'água à imagem
            xObject.Image.Add(watermark);
        }
    }
}
```
## Etapa 6: salve o PDF com marca d'água
Finalmente, salve o PDF com marca d'água no arquivo de saída especificado.
```csharp
    watermarker.Save(outputFileName);
}
```
E aí está! Seu PDF agora contém marcas d'água em todos os seus XObjects.
## Conclusão
 Adicionar marcas d'água aos seus documentos PDF usando o Groupdocs Watermark for .NET é um processo simples que fornece uma camada adicional de segurança. Seguindo as etapas descritas neste tutorial, você pode garantir que seus documentos estejam protegidos contra uso não autorizado. Lembre-se, você sempre pode consultar o[documentação](https://tutorials.groupdocs.com/Watermark/net/) para obter informações mais detalhadas e recursos avançados.
## Perguntas frequentes
### Posso usar uma imagem como marca d’água em vez de texto?
Sim, Groupdocs.Watermark for .NET oferece suporte a marcas d'água de texto e imagem.
### Como posso testar o Groupdocs.Watermark sem comprá-lo?
 Você pode usar um[licença temporária](https://purchase.groupdocs.com/temporary-license/) para avaliar o produto.
### É possível personalizar a aparência da marca d’água?
Absolutamente! Você pode personalizar a fonte, o tamanho, o ângulo de rotação e muito mais.
### O Groupdocs.Watermark oferece suporte a outros formatos de documento?
Sim, suporta vários formatos, incluindo Word, Excel e PowerPoint.
### Onde posso obter suporte se encontrar problemas?
 Você pode obter suporte do[Fórum de documentos de grupo](https://forum.groupdocs.com/c/watermark/19).