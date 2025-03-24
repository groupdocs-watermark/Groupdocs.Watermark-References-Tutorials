---
title: Adicionar marca d'água a artefatos de imagem em PDF
linktitle: Adicionar marca d'água a artefatos de imagem em PDF
second_title: API GroupDocs.Watermark .NET
description: Proteja seus arquivos PDF com marcas d'água personalizadas usando GroupDocs.Watermark for .NET. Adicione facilmente marcas d'água de texto ou imagem a artefatos de imagem em documentos PDF.
weight: 18
url: /pt/net/pdf-watermarking-attachments/add-watermark-image-artifacts-pdf/
---
## Introdução
Neste tutorial, orientaremos você no processo de adição de uma marca d'água a artefatos de imagem em um documento PDF usando GroupDocs.Watermark for .NET. Seguindo essas etapas, você pode proteger seus arquivos PDF de maneira eficiente com marcas d’água personalizadas.
## Pré-requisitos
Antes de começarmos, certifique-se de ter os seguintes pré-requisitos:
1.  GroupDocs.Watermark for .NET: Baixe e instale a biblioteca GroupDocs.Watermark for .NET em[aqui](https://releases.groupdocs.com/Watermark/net/).
2. Caminho do Documento: Tenha o caminho para o documento PDF onde deseja adicionar a marca d’água.
3. Diretório de saída: Crie um diretório onde o documento com marca d’água será salvo.

## Importar namespaces
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Etapa 1: carregue o documento e inicialize o marca d'água
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
```
## Passo 2: Obtenha conteúdo PDF e adicione marca d’água
```csharp
	PdfContent pdfContent = watermarker.GetContent<PdfContent>();
	// Inicializar imagem ou marca d'água de texto
	TextWatermark watermark = new TextWatermark("Protected image", new Font("Arial", 8));
	watermark.HorizontalAlignment = HorizontalAlignment.Center;
	watermark.VerticalAlignment = VerticalAlignment.Center;
	watermark.RotateAngle = 45;
	watermark.SizingType = SizingType.ScaleToParentDimensions;
	watermark.ScaleFactor = 1;
	foreach (PdfPage page in pdfContent.Pages)
	{
		foreach (PdfArtifact artifact in page.Artifacts)
		{
			if (artifact.Image != null)
			{
				// Adicione marca d'água à imagem
				artifact.Image.Add(watermark);
			}
		}
	}
```
## Etapa 3: salve o documento com marca d’água
```csharp
	watermarker.Save(outputFileName);
}
```

## Conclusão
Com o GroupDocs.Watermark for .NET, adicionar marcas d'água a artefatos de imagem em documentos PDF torna-se um processo contínuo. Seguindo este tutorial, você poderá proteger seus arquivos PDF de forma eficiente com marcas d'água personalizadas, garantindo sua segurança e autenticidade.
## Perguntas frequentes
### Posso adicionar marcas d'água de imagem e texto ao meu documento PDF?
Sim, GroupDocs.Watermark for .NET suporta a adição de marcas d'água de imagem e texto simultaneamente.
### Existe alguma limitação no número de marcas d'água que posso adicionar a um documento?
Não, você pode adicionar várias marcas d'água a um documento sem quaisquer limitações.
### Posso personalizar a aparência e a posição da marca d'água?
Com certeza, você tem controle total sobre a aparência, posição e propriedades da marca d’água.
### O GroupDocs.Watermark for .NET oferece suporte a outros formatos de documento além do PDF?
Sim, suporta vários formatos de documentos, incluindo Word, Excel, PowerPoint e muito mais.
### Existe uma maneira de remover marcas d'água de um documento?
Sim, GroupDocs.Watermark for .NET fornece métodos para remover marcas d'água de documentos, se necessário.