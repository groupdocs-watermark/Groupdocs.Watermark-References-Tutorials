---
title: Salvar documento no mesmo arquivo ou fluxo
linktitle: Salvar documento no mesmo arquivo ou fluxo
second_title: API GroupDocs.Watermark .NET
description: Aprenda como adicionar marcas d'água a documentos usando Groupdocs.Watermark for .NET. Este guia fornece instruções para garantir a proteção e integridade dos documentos.
weight: 10
url: /pt/net/document-savings/save-document-same-file-stream/
---

# Salvar documento no mesmo arquivo ou fluxo

## Introdução
Na era digital de hoje, adicionar marcas d'água aos documentos tornou-se essencial para proteger a propriedade intelectual e garantir a integridade da marca. Groupdocs.Watermark for .NET oferece uma solução robusta para desenvolvedores que desejam incorporar marcas d'água em documentos de maneira integrada. Este guia completo orientará você nas etapas para salvar um documento com marca d'água no mesmo arquivo ou fluxo usando Groupdocs.Watermark for .NET.
## Pré-requisitos
Antes de mergulhar no tutorial, certifique-se de ter o seguinte:
1. Ambiente de Desenvolvimento: Visual Studio instalado em sua máquina.
2. .NET Framework: certifique-se de ter o .NET Framework 4.0 ou posterior.
3.  Groupdocs.Watermark for .NET: Baixe e instale a versão mais recente do[site](https://releases.groupdocs.com/Watermark/net/).
4.  Licença: Obtenha uma licença temporária ou permanente de[aqui](https://purchase.groupdocs.com/temporary-license/).
## Importar namespaces
Para começar a usar Groupdocs.Watermark em seu projeto .NET, você precisa importar os namespaces necessários:
```csharp
using System;
using System.IO;
using GroupDocs.Watermark.Watermarks;
```
## Etapa 1: configure seu projeto
Antes de adicionarmos marcas d'água aos nossos documentos, precisamos configurar nosso projeto .NET. Veja como:
1. Crie um novo projeto: abra o Visual Studio e crie um novo aplicativo de console.
2. Adicionar referência Groupdocs.Watermark: clique com o botão direito do mouse no projeto no Solution Explorer, escolha "Gerenciar pacotes NuGet" e instale o pacote Groupdocs.Watermark.
## Etapa 2: copie o documento para um novo local
Para evitar alterar diretamente o documento original, é uma boa prática copiá-lo primeiro para um novo local. Veja como você faz isso:
```csharp
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName("Your Document Path"));
File.Copy("Your Document Path", outputFileName);
```
## Etapa 3: inicializar o marcador d’água
Agora que copiamos nosso documento, podemos inicializar a classe Watermarker para adicionar nossa marca d'água:
```csharp
using (Watermarker watermarker = new Watermarker(outputFileName))
{
    // A marca d'água vai aqui
}
```
## Etapa 4: criar e adicionar uma marca d’água de texto
A seguir, criamos uma marca d'água de texto e a adicionamos ao nosso documento:
```csharp
TextWatermark watermark = new TextWatermark("Test watermark", new Font("Arial", 12));
watermarker.Add(watermark);
```
## Etapa 5: salve o documento
Por fim, salve o documento com a marca d'água aplicada:
```csharp
watermarker.Save();
```
## Conclusão
Adicionar marcas d’água aos seus documentos usando o Groupdocs para .NET é simples e eficiente. Seguindo as etapas descritas acima, você pode proteger seus documentos e manter sua integridade sem esforço. Para mais detalhes, você pode consultar o[documentação](https://tutorials.groupdocs.com/Watermark/net/).
## Perguntas frequentes
### Posso usar uma imagem como marca d’água em vez de texto?
Sim, Groupdocs.Watermark permite usar imagens, formas e texto como marcas d’água.
### Como removo uma marca d’água de um documento?
 Você pode remover uma marca d'água acessando a coleção de marcas d'água no documento e usando o botão`Remove` método.
### É possível personalizar a aparência da marca d’água?
Absolutamente. Você pode personalizar a fonte, o tamanho, a cor e a posição da marca d’água.
### Posso aplicar várias marcas d’água em um único documento?
 Sim, você pode adicionar várias marcas d'água chamando o`Add` método várias vezes com diferentes objetos de marca d'água.
### O Groupdocs.Watermark é compatível com todos os formatos de documento?
Groupdocs.Watermark oferece suporte a uma ampla variedade de formatos de documentos, incluindo PDF, DOCX, PPTX e muitos outros.