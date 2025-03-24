---
title: Carregar documento do disco local
linktitle: Carregar documento do disco local
second_title: API GroupDocs.Watermark .NET
description: Proteja e gerencie seus documentos com Groupdocs para .NET. Siga nosso guia detalhado para adicionar marcas d'água perfeitamente.
weight: 10
url: /pt/net/document-loadings/load-document-from-local-disk/
---
## Introdução
Colocar marcas d'água em documentos é essencial na era digital atual para garantir a proteção do conteúdo, a afirmação de propriedade e a confidencialidade. Groupdocs.Watermark for .NET é uma biblioteca poderosa que permite aos desenvolvedores adicionar, pesquisar e gerenciar marcas d'água em vários formatos de documentos. Neste tutorial, percorreremos o processo de uso do Groupdocs.Watermark for .NET para adicionar marcas d'água aos seus documentos com instruções passo a passo detalhadas.
## Pré-requisitos
Antes de mergulhar na implementação, certifique-se de ter o seguinte:
1. Visual Studio instalado: você precisará do Visual Studio ou outro IDE .NET compatível.
2.  Groupdocs.Watermark for .NET: Baixe a biblioteca do[Link para Download](https://releases.groupdocs.com/Watermark/net/).
3. .NET Framework: certifique-se de ter o .NET Framework 4.6.1 ou superior instalado.
4. Um documento de amostra: Prepare um documento de amostra para testar o processo de marca d’água.
## Importar namespaces
Para começar, você precisará importar os namespaces necessários para o seu projeto. Eles são essenciais para acessar as classes e métodos necessários para a marca d'água.
```csharp
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Etapa 1: carregar o documento do disco local
Primeiro, você precisa carregar o documento do seu disco local. Este documento será aquele ao qual você adicionará uma marca d'água.
Defina o caminho do documento que deseja colocar marca d'água.
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
```
## Etapa 2: inicializar opções de carregamento
 Em seguida, inicialize as opções de carregamento. Por exemplo, se estiver trabalhando com um documento do Word, você usará`WordProcessingLoadOptions`.
```csharp
var loadOptions = new WordProcessingLoadOptions();
```
## Etapa 3: criar e configurar o marcador d’água
 Agora, você criará uma instância do`Watermarker` aula. Esta instância será usada para gerenciar e aplicar marcas d'água ao seu documento.
```csharp
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Este bloco conterá outras etapas para adicionar e salvar a marca d’água
}
```
## Etapa 4: crie uma marca d'água
Crie uma marca d'água de texto. Esta marca d'água pode conter qualquer texto que você escolher. Aqui, usaremos "Teste de marca d'água".
```csharp
TextWatermark watermark = new TextWatermark("Test watermark", new Font("Arial", 12));
```
## Etapa 5: adicionar marca d'água ao documento
Adicione a marca d'água criada ao documento usando o`Add` método do`Watermarker` aula.
```csharp
watermarker.Add(watermark);
```
## Etapa 6: salve o documento com marca d’água
Finalmente, salve o documento com marca d’água no caminho especificado.
```csharp
watermarker.Save(outputFileName);
```

## Conclusão
Adicionar marcas d’água aos seus documentos usando o Groupdocs para .NET é simples e eficiente. Este guia orientou você durante todo o processo, desde a configuração do seu ambiente até salvar um documento com marca d’água. Com esta ferramenta poderosa, você pode garantir que seus documentos estejam protegidos e que sua propriedade intelectual esteja segura. 
 Para mais detalhes, verifique o[documentação](https://tutorials.groupdocs.com/Watermark/net/) , e se você encontrar algum problema, o[Fórum de suporte](https://forum.groupdocs.com/c/watermark/19) é um excelente lugar para assistência. 
## Perguntas frequentes
### Posso usar fontes personalizadas para marcas d’água?
Sim, Groupdocs suporta fontes personalizadas. Você pode especificar qualquer fonte instalada em seu sistema.
### Que tipos de documentos são suportados?
Groupdocs.Watermark oferece suporte a uma ampla variedade de formatos de documentos, incluindo Word, Excel, PDF, PowerPoint e muito mais.
### Como posso remover uma marca d'água de um documento?
 Você pode usar o`Remove` método fornecido pelo`Watermarker` classe para remover marcas d’água.
### É possível adicionar marcas d'água de imagem?
 Sim, você pode adicionar marcas d'água de imagem usando o`ImageWatermark` aula.
### Posso experimentar o Groupdocs.Watermark gratuitamente?
 Com certeza, você pode baixar um[teste grátis](https://releases.groupdocs.com/) avaliar a biblioteca antes de comprar.