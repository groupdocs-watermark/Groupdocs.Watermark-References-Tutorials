---
title: Rasterizar documento PDF
linktitle: Rasterizar documento PDF
second_title: API GroupDocs.Watermark .NET
description: Aprenda como rasterizar documentos PDF usando GroupDocs.Watermark for .NET. Aumente a segurança dos documentos e o apelo visual sem esforço.
weight: 27
url: /pt/net/pdf-watermarking-attachments/rasterize-pdf-document/
---
## Introdução
No domínio do gerenciamento e manipulação de documentos, GroupDocs.Watermark for .NET se destaca como uma ferramenta poderosa, oferecendo recursos robustos para adicionar, remover e pesquisar marcas d'água em vários formatos de documentos. Seja protegendo seus documentos com avisos de direitos autorais, adicionando logotipos corporativos para marca ou simplesmente anotando documentos com carimbos, GroupDocs.Watermark simplifica o processo com sua API intuitiva e amplo conjunto de recursos.
## Pré-requisitos
Antes de mergulhar no mundo da marca d'água com GroupDocs.Watermark for .NET, certifique-se de ter os seguintes pré-requisitos em vigor:
### 1. Instale o .NET Framework
Certifique-se de ter o .NET Framework instalado em sua máquina de desenvolvimento. Você pode baixá-lo no site da Microsoft ou usar o gerenciador de pacotes de sua preferência.
#### Etapa 1: Baixe o .NET Framework
Visite a página de download do Microsoft .NET Framework.
#### Etapa 2: instalar o .NET Framework
Siga as instruções de instalação fornecidas na página de download para instalar o .NET Framework em seu sistema.
### 2. Obtenha a licença GroupDocs.Watermark
Para utilizar todos os recursos do GroupDocs.Watermark, você precisa de uma licença válida. Você pode comprar uma licença ou obter uma licença temporária para fins de avaliação.
#### Etapa 1: Obtenha uma licença
Visite a página de compra do GroupDocs.Watermark.
#### Etapa 2: Adquira ou obtenha uma licença temporária
Escolha a opção de licenciamento apropriada com base em suas necessidades: adquira uma licença para uso contínuo ou adquira uma licença temporária para fins de avaliação.

## Importar namespaces
Antes de começar a colocar marcas d'água em seus documentos, certifique-se de importar os namespaces necessários para acessar a funcionalidade do GroupDocs perfeitamente.
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```

Agora que você configurou tudo, vamos começar a rasterizar um documento PDF usando GroupDocs.Watermark for .NET. A rasterização converte cada página do documento PDF em um formato de imagem raster, como PNG.
## Etapa 1: inicializar variáveis
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
Certifique-se de substituir “Your Document Path” e “Your Document Directory” pelo caminho real para o seu documento PDF e o diretório de saída desejado, respectivamente.
## Etapa 2: carregar o documento e adicionar marca d’água
```csharp
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Inicializar imagem ou marca d'água de texto
    TextWatermark watermark = new TextWatermark("Do not copy", new Font("Arial", 8));
    watermark.HorizontalAlignment = HorizontalAlignment.Center;
    watermark.VerticalAlignment = VerticalAlignment.Center;
    watermark.RotateAngle = 45;
    watermark.SizingType = SizingType.ScaleToParentDimensions;
    watermark.ScaleFactor = 1;
    watermark.Opacity = 0.5;
    // Adicione marca d'água de qualquer tipo primeiro
    watermarker.Add(watermark);
    PdfContent pdfContent = watermarker.GetContent<PdfContent>();
    // Rasterizar todas as páginas
    pdfContent.Rasterize(100, 100, PdfImageConversionFormat.Png);
    // O conteúdo de todas as páginas é substituído por imagens rasterizadas
    watermarker.Save(outputFileName);
}
```
Nesta etapa, carregamos o documento PDF e inicializamos uma marca d’água de texto com propriedades especificadas como texto, fonte, alinhamento, ângulo de rotação, tipo de dimensionamento, fator de escala e opacidade. Em seguida, adicionamos a marca d'água ao documento. A seguir, recuperamos o conteúdo do documento PDF e rasterizamos todas as páginas para o formato PNG com resolução de 100 DPI. Por fim, salvamos o documento modificado com conteúdo rasterizado.

## Conclusão
GroupDocs.Watermark for .NET oferece uma solução abrangente para adicionar marcas d'água a vários formatos de documentos com facilidade. Seguindo as etapas descritas neste tutorial, você pode rasterizar documentos PDF com eficácia e aumentar sua segurança e apelo visual.
## Perguntas frequentes
### O GroupDocs.Watermark é compatível com outros formatos de documento além do PDF?
Sim, GroupDocs.Watermark oferece suporte a uma ampla variedade de formatos de documentos, incluindo Microsoft Word, Excel, PowerPoint, Visio, Outlook e muitos mais.
### Posso personalizar a aparência das marcas d'água adicionadas usando GroupDocs.Watermark?
Absolutamente! GroupDocs.Watermark oferece amplas opções para personalizar propriedades de marca d'água, como texto, fonte, cor, tamanho, opacidade, rotação e posição.
### O GroupDocs.Watermark oferece suporte para processamento em lote?
Sim, você pode processar facilmente vários documentos em lote usando GroupDocs, economizando tempo e esforço ao colocar marcas d'água em grandes conjuntos de arquivos.
### Existe uma versão de teste disponível para GroupDocs.Watermark?
Sim, você pode baixar uma versão de teste gratuita do GroupDocs.Watermark do site para avaliar seus recursos antes de fazer uma compra.
### Como posso obter assistência se encontrar algum problema ou tiver dúvidas sobre GroupDocs.Watermark?
Você pode visitar o fórum GroupDocs.Watermark para buscar suporte da comunidade ou entrar em contato com a equipe de suporte do GroupDocs para obter assistência.