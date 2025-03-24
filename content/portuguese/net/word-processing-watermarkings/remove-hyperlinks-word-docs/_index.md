---
title: Remover hiperlinks em documentos do Word
linktitle: Remover hiperlinks em documentos do Word
second_title: API GroupDocs.Watermark .NET
description: Aprenda como remover hiperlinks de documentos do Word usando GroupDocs.Watermark for .NET. Aumente a segurança dos documentos sem esforço.
weight: 29
url: /pt/net/word-processing-watermarkings/remove-hyperlinks-word-docs/
---

# Remover hiperlinks em documentos do Word

## Introdução
No mundo digital de hoje, onde a informação flui perfeitamente, proteger os seus documentos é fundamental. Esteja você compartilhando dados comerciais confidenciais ou criando uma obra-prima, proteger seu conteúdo contra acesso e manipulação não autorizados é crucial. Com o advento do GroupDocs.Watermark for .NET, você pode garantir a integridade de seus documentos adicionando, removendo e detectando marcas d'água com facilidade.
## Pré-requisitos
Antes de mergulhar no mundo da marca d'água de documentos com GroupDocs.Watermark for .NET, existem alguns pré-requisitos que você precisa ter em vigor:
1.  Instalação do GroupDocs.Watermark for .NET: Visite o[Link para Download](https://releases.groupdocs.com/Watermark/net/) para adquirir os arquivos necessários para instalação. Siga as instruções de instalação fornecidas na documentação.
2. Compreensão básica do .NET Framework: familiarize-se com o .NET Framework e seus fundamentos para navegar facilmente pelos exemplos de codificação.
3. Acesso a um editor de texto ou IDE: certifique-se de ter um editor de texto ou um ambiente de desenvolvimento integrado (IDE), como o Visual Studio, instalado em seu sistema para fins de codificação.

## Importar namespaces
Antes de se aprofundar no guia passo a passo, certifique-se de importar os namespaces necessários em seu projeto C#:
```csharp
using GroupDocs.Watermark.Contents.WordProcessing;
using GroupDocs.Watermark.Options.WordProcessing;
using System.IO;
using System;
```
## Etapa 1: carregue o documento
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
```
## Etapa 2: Obtenha o conteúdo do WordProcessing
```csharp
    WordProcessingContent content = watermarker.GetContent<WordProcessingContent>();
```
## Etapa 3: substituir o hiperlink
```csharp
    // Substituir hiperlink
    content.Sections[0].Shapes[0].Hyperlink = "https://www.groupdocs.com/”;
```
## Etapa 4: remover hiperlink
```csharp
    // Remover hiperlink
    content.Sections[0].Shapes[1].Hyperlink = null;
```
## Etapa 5: salve o documento
```csharp
    watermarker.Save(outputFileName);
}
```

## Conclusão
GroupDocs.Watermark for .NET capacita os desenvolvedores a manipular marcas d'água sem esforço, garantindo a segurança e integridade dos documentos. Seguindo o guia passo a passo descrito acima, você pode remover facilmente hiperlinks de documentos do Word, aumentando assim a confidencialidade e o profissionalismo.
## Perguntas frequentes
### O GroupDocs.Watermark é compatível com outros formatos de documento?
Sim, GroupDocs.Watermark oferece suporte a uma ampla variedade de formatos de documentos, incluindo PDF, Excel, PowerPoint e muito mais.
### Posso personalizar a aparência das marcas d'água usando GroupDocs.Watermark?
Absolutamente! GroupDocs.Watermark oferece amplas opções de personalização para marcas d'água, permitindo ajustar sua posição, tamanho, opacidade e muito mais.
### O GroupDocs.Watermark oferece suporte para processamento em lote?
Sim, você pode processar em lote vários documentos simultaneamente com GroupDocs, economizando tempo e esforço.
### Existe uma versão de teste disponível para GroupDocs.Watermark?
 Sim, você pode explorar os recursos do GroupDocs.Watermark baixando a versão de teste gratuita em[aqui](https://releases.groupdocs.com/).
### Como posso obter licenças temporárias para GroupDocs.Watermark?
 Licenças temporárias para GroupDocs podem ser obtidas no site.[aqui](https://purchase.groupdocs.com/temporary-license/).