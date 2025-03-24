---
title: Salvar documento em local especificado
linktitle: Salvar documento em local especificado
second_title: API GroupDocs.Watermark .NET
description: Aprenda como adicionar marcas d'água facilmente aos seus documentos usando GroupDocs.Watermark for .NET com este guia passo a passo. Aumente a segurança dos documentos.
weight: 11
url: /pt/net/document-savings/save-document-specified-location/
---

# Salvar documento em local especificado

## Introdução
Na era digital, a proteção de documentos tornou-se mais crucial do que nunca. A marca d'água é uma forma eficaz de proteger seus documentos contra uso não autorizado. GroupDocs.Watermark for .NET oferece uma solução robusta para adicionar marcas d'água aos seus documentos. Quer você seja um desenvolvedor que deseja integrar marcas d'água em seu aplicativo ou alguém interessado em proteger seus documentos, este tutorial irá guiá-lo passo a passo pelo processo.
## Pré-requisitos
Antes de mergulhar no tutorial, certifique-se de ter os seguintes pré-requisitos em vigor:
- Ambiente de desenvolvimento .NET: certifique-se de ter o Visual Studio ou qualquer outro ambiente de desenvolvimento .NET instalado.
-  GroupDocs.Watermark for .NET Library: Baixe e faça referência à biblioteca em seu projeto.[Baixe GroupDocs.Watermark para .NET](https://releases.groupdocs.com/Watermark/net/)
- Conhecimento básico de programação C#: Compreender os conceitos básicos de programação C# será útil.
- Documento para marca d'água: tenha um documento de amostra pronto ao qual deseja aplicar a marca d'água.
## Importar namespaces
Antes de começarmos com o exemplo, você precisa importar os namespaces necessários. Adicione as seguintes instruções using na parte superior do seu arquivo de código:
```csharp
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
Vamos dividir o processo de adição de uma marca d'água a um documento usando GroupDocs.Watermark for .NET em etapas gerenciáveis. Siga estas etapas para aplicar uma marca d’água com êxito e salvar seu documento em um local especificado.
## Etapa 1: configure seu projeto
Comece criando um novo projeto .NET no Visual Studio. Você pode escolher um aplicativo de console para simplificar.
1. Abra o Visual Studio.
2.  Selecione`File` >`New` >`Project`.
3.  Escolher`Console App (.NET Core)` ou`Console App (.NET Framework)`.
4.  Nomeie seu projeto e clique`Create`.

## Etapa 2: prepare seu documento e texto de marca d'água
### Especifique o caminho do documento
Defina o caminho do documento que deseja colocar marca d'água. Para este exemplo, vamos usar um caminho de espaço reservado.
```csharp
string documentPath = "Your Document Path";
```
### Definir caminho de saída
Configure o caminho de saída onde deseja que o documento com marca d’água seja salvo.
```csharp
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
```
## Etapa 3: carregue o documento
 Use o`Watermarker` class para carregar seu documento. Esta classe fornece métodos para adicionar, remover e editar marcas d'água.
```csharp
using (Watermarker watermarker = new Watermarker(documentPath))
{
    // Adicione lógica de marca d'água aqui
}
```
## Etapa 4: criar e adicionar uma marca d’água

### Criar marca d'água de texto
 Instanciar um`TextWatermark` objeto com as propriedades de texto e fonte desejadas.
```csharp
TextWatermark watermark = new TextWatermark("Test watermark", new Font("Arial", 12));
```
### Adicionar marca d'água ao documento
 Adicione a marca d'água criada ao seu documento usando o`Add` método do`Watermarker` aula.
```csharp
watermarker.Add(watermark);
```
## Etapa 5: salve o documento
Por fim, salve o documento com a marca d'água no local especificado.
```csharp
watermarker.Save(outputFileName);
```
## Conclusão
Marcar seus documentos com marca d’água usando GroupDocs para .NET é um processo simples que pode aumentar significativamente a segurança de seus documentos. Seguindo este guia passo a passo, você pode facilmente adicionar marcas d'água aos seus documentos e salvá-los no local desejado. Esteja você protegendo a propriedade intelectual, garantindo a autenticidade do documento ou simplesmente adicionando um toque profissional, o GroupDocs.Watermark for .NET fornece as ferramentas que você precisa.
## Perguntas frequentes
### Posso usar imagens como marcas d'água com GroupDocs.Watermark for .NET?
Sim, você pode usar marcas d’água de texto e imagem com GroupDocs para .NET. A biblioteca oferece suporte a vários tipos de marcas d'água para atender às suas necessidades.
### Existe uma avaliação gratuita disponível para GroupDocs.Watermark for .NET?
 Sim, você pode baixar uma versão de avaliação gratuita no site[local na rede Internet](https://releases.groupdocs.com/).
### Como posso adquirir uma licença do GroupDocs.Watermark for .NET?
 Você pode comprar uma licença no[página de compra](https://purchase.groupdocs.com/buy).
### O GroupDocs.Watermark for .NET suporta marca d'água em lote?
Sim, você pode marcar vários documentos em um processo em lote iterando uma lista de documentos e aplicando marcas d'água.
### Onde posso obter suporte para GroupDocs.Watermark for .NET?
 O suporte está disponível no[Fórum GroupDocs](https://forum.groupdocs.com/c/watermark/19).