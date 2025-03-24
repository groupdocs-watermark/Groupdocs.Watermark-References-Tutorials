---
title: Carregar documento do stream
linktitle: Carregar documento do stream
second_title: API GroupDocs.Watermark .NET
description: Aprenda como adicionar marcas d'água a documentos usando GroupDocs.Watermark for .NET com este guia. Perfeito para desenvolvedores que buscam aprimorar a segurança dos documentos.
weight: 11
url: /pt/net/document-loadings/load-document-from-stream/
---

# Carregar documento do stream

## Introdução
Você deseja adicionar marcas d'água aos seus documentos de maneira integrada usando .NET? Não procure mais! GroupDocs.Watermark for .NET é uma biblioteca poderosa e fácil de usar que permite gerenciar marcas d’água em vários formatos de documentos. Esteja você trabalhando com PDFs, documentos do Word ou imagens, esta ferramenta tem o que você precisa. Neste tutorial, orientaremos você no processo de carregamento de um documento de um fluxo e adição de uma marca d’água passo a passo. Então, vamos mergulhar de cabeça!
## Pré-requisitos
Antes de começarmos, certifique-se de ter a seguinte configuração:
1. Visual Studio: qualquer versão recente do Visual Studio funcionará bem.
2. .NET Framework: certifique-se de ter o .NET Framework 4.0 ou superior instalado.
3.  GroupDocs.Watermark para .NET: você pode baixá-lo em[aqui](https://releases.groupdocs.com/Watermark/net/).
4. Conhecimento básico de C#: Familiaridade com C# e conceitos de programação orientada a objetos será útil.

## Importar namespaces
Para usar GroupDocs.Watermark em seu projeto, você precisará importar os namespaces necessários. Isso permitirá que você acesse os recursos da biblioteca sem problemas.
```csharp
using System;
using System.IO;
using GroupDocs.Watermark.Watermarks;
```
## Etapa 1: configurando seu projeto
Primeiramente, você precisa configurar seu projeto no Visual Studio. Veja como você faz isso:
1. Crie um novo projeto: abra o Visual Studio e crie um novo projeto de aplicativo de console C#.
2.  Instale GroupDocs.Watermark: Instale a biblioteca GroupDocs.Watermark por meio do NuGet Package Manager. Basta procurar por`GroupDocs.Watermark` e instale-o.
## Etapa 2: definir caminhos de documentos
Em seguida, você precisa definir os caminhos do seu documento e o arquivo de saída onde o documento com marca d'água será salvo.
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
```
 Substituir`"Your Document Path"` com o caminho real do documento que você deseja colocar marca d'água e`"Your Document Directory"` com o diretório onde deseja salvar o documento com marca d'água.
## Etapa 3: carregar o documento de um fluxo
Agora, vamos carregar o documento de um stream. Isso envolve abrir o documento como um fluxo e, em seguida, usar o`Watermarker` class da biblioteca GroupDocs.Watermark para gerenciá-lo.
```csharp
using (Stream document = File.OpenRead(documentPath))
using (Watermarker watermarker = new Watermarker(document))
{
    // Seu código para gerenciar marcas d'água irá aqui
}
```
 Este trecho de código garante que o documento seja aberto como um fluxo e o`Watermarker` class é inicializada com este fluxo. O`using` As declarações garantem que os recursos sejam descartados adequadamente após o uso.
## Etapa 4: criar e adicionar uma marca d’água
Criar uma marca d'água é simples com GroupDocs.Watermark. Neste exemplo, criaremos uma marca d’água de texto simples.
```csharp
TextWatermark watermark = new TextWatermark("Test watermark", new Font("Arial", 12));
watermarker.Add(watermark);
```
 Aqui, criamos um`TextWatermark` objeto com o texto "Testar marca d'água" e especifique os detalhes da fonte. Em seguida, adicionamos esta marca d'água ao documento usando o`Add` método do`Watermarker` aula.
## Etapa 5: salve o documento com marca d'água
Finalmente, salve o documento com marca d'água no caminho de saída especificado.
```csharp
watermarker.Save(outputFileName);
```
 Este código salva o documento com a marca d'água recém-adicionada`outputFileName` caminho que você definiu anteriormente.

## Conclusão
Parabéns! Você adicionou com sucesso uma marca d'água ao seu documento usando GroupDocs.Watermark for .NET. Esta biblioteca torna incrivelmente fácil gerenciar marcas d'água em vários formatos de documentos. Se você precisa adicionar texto, imagens ou outros tipos de marcas d’água, GroupDocs.Watermark tem as ferramentas que você precisa. Não esqueça de conferir o[documentação](https://tutorials.groupdocs.com/Watermark/net/) para recursos mais avançados e opções de personalização.
## Perguntas frequentes
### Que tipos de marcas d'água posso adicionar usando GroupDocs.Watermark for .NET?
Você pode adicionar marcas d'água de texto, marcas d'água de imagem e até formas e logotipos complexos. A biblioteca oferece suporte a uma ampla gama de opções de personalização.
### Posso remover marcas d'água de documentos usando GroupDocs.Watermark?
Sim, GroupDocs.Watermark também permite remover marcas d’água existentes de documentos.
### Existe um teste gratuito disponível para GroupDocs.Watermark?
 Sim, você pode baixar uma avaliação gratuita em[aqui](https://releases.groupdocs.com/).
### Como posso adquirir uma licença para GroupDocs.Watermark?
Você pode comprar uma licença diretamente do[Site GroupDocs](https://purchase.groupdocs.com/buy).
### Onde posso obter suporte se encontrar problemas?
 Para suporte, você pode visitar o[Fórum de suporte GroupDocs.Watermark](https://forum.groupdocs.com/c/watermark/19).