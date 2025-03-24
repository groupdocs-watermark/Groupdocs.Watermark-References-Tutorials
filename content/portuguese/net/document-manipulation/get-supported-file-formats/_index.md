---
title: Obtenha formatos de arquivo suportados
linktitle: Obtenha formatos de arquivo suportados
second_title: API GroupDocs.Watermark .NET
description: Adicione marcas d'água aos seus documentos sem esforço usando GroupDocs.Watermark for .NET. Siga nosso guia passo a passo abrangente para proteger seus ativos digitais.
weight: 13
url: /pt/net/document-manipulation/get-supported-file-formats/
---
## Introdução
Colocar marcas d'água em seus documentos é uma etapa crucial para proteger seus ativos digitais. Seja para proteger a propriedade intelectual, garantir a confidencialidade ou simplesmente promover a marca, as marcas d'água desempenham um papel vital. Se você é um desenvolvedor .NET que deseja integrar recursos de marca d'água em seus aplicativos, o GroupDocs.Watermark for .NET é uma ferramenta poderosa e versátil que você deve considerar. Este tutorial irá guiá-lo através dos fundamentos do uso do GroupDocs.Watermark, desde a instalação até a aplicação de sua primeira marca d'água, detalhando cada etapa para garantir que você possa acompanhar facilmente.
## Pré-requisitos
Antes de nos aprofundarmos nos detalhes, vamos ter certeza de que você tem tudo o que precisa para começar:
1.  Visual Studio: certifique-se de ter o Visual Studio instalado em sua máquina. Você pode baixá-lo no[Site do Visual Studio](https://visualstudio.microsoft.com/).
2. .NET Framework: GroupDocs.Watermark oferece suporte a várias versões do .NET Framework. Certifique-se de que seu projeto tenha como alvo uma versão compatível.
3. GroupDocs.Watermark for .NET: você pode baixar a versão mais recente no[página de lançamento](https://releases.groupdocs.com/Watermark/net/).
4. Conhecimento básico de C#: este tutorial pressupõe que você tenha um conhecimento fundamental de desenvolvimento em C# e .NET.
## Importar namespaces
Primeiro, vamos importar os namespaces necessários para o seu projeto. Abra seu arquivo C# e adicione o seguinte usando diretivas na parte superior:
```csharp
using System;
using System.Collections.Generic;
using GroupDocs.Watermark.Common;
```
Com esses namespaces importados, você está pronto para começar a adicionar marcas d'água aos seus documentos.

## Etapa 1: inicializar o mecanismo de marca d’água
 A primeira etapa é inicializar o mecanismo de marca d'água. Isso envolve a criação de uma instância do`Watermarker` class com o documento que você deseja colocar marca d'água.
```csharp
string documentPath = "path/to/your/document.pdf";
Watermarker watermarker = new Watermarker(documentPath);
```
 Este trecho de código configura o`Watermarker` objeto, que você usará para aplicar marcas d'água ao seu documento.
## Etapa 2: adicionar uma marca d'água de texto
Agora, vamos adicionar uma marca d'água de texto simples ao seu documento. Marcas d’água de texto são ótimas para adicionar rótulos como “Confidencial” ou “Rascunho”.
```csharp
TextWatermark textWatermark = new TextWatermark("Confidential", new Font("Arial", 36));
textWatermark.ForegroundColor = Color.Red;
textWatermark.HorizontalAlignment = HorizontalAlignment.Center;
textWatermark.VerticalAlignment = VerticalAlignment.Center;
watermarker.Add(textWatermark);
```
 Aqui, criamos um`TextWatermark`objeto com o texto "Confidencial", defina sua fonte e cor e alinhe-o ao centro do documento.
## Etapa 3: adicionar uma marca d'água de imagem
Se você preferir usar uma imagem como marca d'água, GroupDocs.Watermark facilita isso.
```csharp
ImageWatermark imageWatermark = new ImageWatermark("path/to/watermark.png");
imageWatermark.Width = 100;
imageWatermark.Height = 100;
imageWatermark.HorizontalAlignment = HorizontalAlignment.Right;
imageWatermark.VerticalAlignment = VerticalAlignment.Top;
watermarker.Add(imageWatermark);
```
 Neste exemplo, criamos um`ImageWatermark` objeto, defina suas dimensões e alinhe-o com o canto superior direito do documento.
## Etapa 4: salve o documento
Após adicionar as marcas d'água desejadas, a etapa final é salvar o documento modificado.
```csharp
watermarker.Save("path/to/output/document.pdf");
watermarker.Dispose();
```
 Isto salvará o documento com marca d'água no caminho especificado e liberará quaisquer recursos usados por ele`Watermarker` instância.
## Etapa 5: Obtenha formatos de arquivo suportados
Para ver quais formatos de arquivo são suportados pelo GroupDocs.Watermark, você pode usar o seguinte trecho de código:
```csharp
IEnumerable<FileType> supportedFileTypes = FileType.GetSupportedFileTypes();
foreach (FileType fileType in supportedFileTypes)
{
    Console.WriteLine(fileType);
}
```
Isso imprimirá todos os tipos de arquivo que GroupDocs.Watermark pode manipular, proporcionando uma visão abrangente de seus recursos.
## Conclusão
Marcar seus documentos com marca d’água com GroupDocs para .NET é simples e eficiente. Seguindo este tutorial, você aprendeu como inicializar o mecanismo de marca d'água, adicionar marcas d'água de texto e imagem, salvar seus documentos com marca d'água e listar os formatos de arquivo suportados. Com essas ferramentas, você pode proteger seus documentos com confiança.
 Se você tiver alguma dúvida ou precisar de mais assistência, não hesite em visitar o[Fórum de suporte GroupDocs.Watermark](https://forum.groupdocs.com/c/watermark/19).
## Perguntas frequentes
### Como instalo o GroupDocs.Watermark para .NET?
 Você pode baixá-lo no[página de lançamento](https://releases.groupdocs.com/Watermark/net/) e adicione a DLL ao seu projeto.
### Posso experimentar GroupDocs.Watermark gratuitamente?
 Sim, você pode solicitar um[teste grátis](https://releases.groupdocs.com/) avaliar o software antes de comprar.
### Quais formatos de arquivo são suportados pelo GroupDocs.Watermark?
Você pode usar o trecho de código fornecido para listar todos os formatos de arquivo suportados.
### Como posso comprar uma licença para GroupDocs.Watermark?
 As licenças podem ser adquiridas diretamente no[página de compra](https://purchase.groupdocs.com/buy).
### Existe alguma documentação disponível para GroupDocs.Watermark?
 Sim, documentação abrangente está disponível[aqui](https://tutorials.groupdocs.com/Watermark/net/).