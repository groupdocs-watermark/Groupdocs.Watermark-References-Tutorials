---
title: Obtenha dimensões do PDF
linktitle: Obtenha dimensões do PDF
second_title: API GroupDocs.Watermark .NET
description: Proteja seus documentos com facilidade usando Groupdocs.Watermark for .NET. Adicione marcas d'água, carimbos e anotações sem esforço.
weight: 26
url: /pt/net/pdf-watermarking-attachments/get-pdf-dimensions/
type: docs
---
# Obtenha dimensões do PDF

## Introdução
Na era digital de hoje, proteger seus documentos é fundamental. Quer você seja um profissional de negócios, um especialista jurídico ou um artista criativo, proteger sua propriedade intelectual é essencial. Groupdocs.Watermark for .NET oferece uma solução robusta para adicionar marcas d'água, carimbos e anotações aos seus documentos, garantindo sua segurança e autenticidade.
## Pré-requisitos
Antes de mergulhar no mundo do Groupdocs.Watermark for .NET, certifique-se de ter os seguintes pré-requisitos em vigor:
1.  Instalação do Groupdocs.Watermark for .NET: Baixe e instale o Groupdocs.Watermark for .NET do[Link para Download](https://releases.groupdocs.com/Watermark/net/).
2.  Chave de licença (opcional): Embora Groupdocs.Watermark for .NET ofereça uma avaliação gratuita, você pode optar por uma licença temporária ou adquirir uma licença completa de[aqui](https://purchase.groupdocs.com/buy) para funcionalidade estendida.
3. Familiaridade com C#: Recomenda-se conhecimento básico da linguagem de programação C# para compreender e implementar os exemplos fornecidos.
4. Documento a ser protegido: Tenha um documento de amostra (por exemplo, PDF, Word, Excel) pronto em sua máquina local para experimentar.

## Importar namespaces
Para começar a trabalhar com Groupdocs.Watermark for .NET, você precisa importar os namespaces necessários para seu projeto C#.
```csharp
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using System;
using System.IO;
```
### Etapa 1: declarar variáveis
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
### Etapa 2: carregar o documento
```csharp
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
```
### Etapa 3: Obtenha conteúdo PDF
```csharp
PdfContent pdfContent = watermarker.GetContent<PdfContent>();
```
### Etapa 4: recuperar dimensões
```csharp
Console.WriteLine(pdfContent.Pages[0].Width);
Console.WriteLine(pdfContent.Pages[0].Height);
```

## Conclusão
Concluindo, Groupdocs.Watermark for .NET oferece uma solução abrangente para proteger seus documentos contra uso e distribuição não autorizados. Seguindo as etapas descritas acima e aproveitando o poder do Groupdocs.Watermark for .NET, você pode garantir a segurança e a integridade de seus valiosos ativos digitais.
## Perguntas frequentes
### Posso usar Groupdocs.Watermark for .NET gratuitamente?
Sim, Groupdocs.Watermark for .NET oferece uma versão de teste gratuita para fins de avaliação. No entanto, para funcionalidade estendida, você pode considerar adquirir uma licença completa.
### O Groupdocs.Watermark oferece suporte a vários formatos de documentos?
Sim, o Groupdocs suporta uma ampla variedade de formatos de documentos, incluindo PDF, Word, Excel, PowerPoint e muito mais.
### Posso personalizar marcas d'água e carimbos com Groupdocs.Watermark?
Absolutamente! Groupdocs.Watermark oferece amplas opções de personalização para marcas d’água, carimbos e anotações para atender às suas necessidades específicas.
### O suporte técnico está disponível para usuários do Groupdocs.Watermark?
 Sim, você pode obter assistência técnica e interagir com a comunidade Groupdocs através do[Fórum de suporte](https://forum.groupdocs.com/c/watermark/19).
### Como posso obter uma licença temporária para Groupdocs.Watermark?
 Você pode obter uma licença temporária para Groupdocs.Watermark em[aqui](https://purchase.groupdocs.com/temporary-license/).