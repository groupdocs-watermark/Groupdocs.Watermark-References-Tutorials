---
title: Obtenha informações do documento do disco local
linktitle: Obtenha informações do documento do disco local
second_title: API GroupDocs.Watermark .NET
description: Aprenda como adicionar, remover e extrair marcas d'água em documentos usando GroupDocs Watermark for .NET com este guia passo a passo abrangente.
weight: 11
url: /pt/net/document-manipulation/get-document-info-local-disk/
---
## Introdução
Bem-vindo ao guia definitivo sobre como usar GroupDocs.Watermark para .NET! Quer você seja um desenvolvedor experiente ou esteja apenas começando, este artigo irá orientá-lo nos fundamentos da marca d'água em seus documentos com esta ferramenta poderosa. No final, você será um profissional em incorporar marcas d'água em seus documentos, garantindo que eles sejam protegidos e marcados de acordo com suas especificações.
## Pré-requisitos
Antes de mergulhar no guia passo a passo, existem alguns pré-requisitos que você precisa atender:
1.  .NET Framework: Certifique-se de ter o .NET Framework instalado em seu sistema. GroupDocs.Watermark for .NET é compatível com várias versões do .NET Framework, portanto verifique o[documentação](https://tutorials.groupdocs.com/Watermark/net/) para detalhes de compatibilidade.
2.  GroupDocs.Watermark for .NET Library: Baixe e instale a versão mais recente do[página de download](https://releases.groupdocs.com/Watermark/net/).
3. Ambiente de Desenvolvimento: Você deve ter um ambiente de desenvolvimento configurado. Visual Studio é uma escolha popular para desenvolvimento .NET.
4. Conhecimento básico de C#: Compreender os fundamentos da programação C# o ajudará a acompanhar os exemplos.
## Importar namespaces
Antes de poder usar o GroupDocs.Watermark for .NET, você precisa importar os namespaces necessários para o seu projeto. Este é um processo simples e essencial para acessar os recursos da biblioteca.
```csharp
using System;
using GroupDocs.Watermark.Common;
```
Vamos dividir o processo de colocar marca d’água em um documento em etapas claras e gerenciáveis. Cada etapa foi projetada para ajudá-lo a compreender e implementar a funcionalidade com facilidade.
## Etapa 1: carregue seu documento
 A primeira etapa é carregar o documento que deseja colocar marca d’água. Isto é feito usando o`Watermarker` class, que permite acessar e manipular seu documento.
```csharp
using (Watermarker watermarker = new Watermarker("Your Document Path"))
{
    // O documento agora está carregado e pronto para marca d'água
}
```
 Nesta etapa, substitua`"Your Document Path"` com o caminho real para o seu documento. Isso inicializa o`Watermarker`objeto, dando acesso a várias funcionalidades de marca d’água.
## Etapa 2: Obtenha informações do documento
Antes de adicionar uma marca d'água, você pode reunir algumas informações sobre o documento. Isso pode ser útil para personalizar sua marca d’água com base nas propriedades do documento.

```csharp
using (Watermarker watermarker = new Watermarker("Your Document Path"))
{
    IDocumentInfo info = watermarker.GetDocumentInfo();
    Console.WriteLine("File type: {0}", info.FileType);
    Console.WriteLine("Number of pages: {0}", info.PageCount);
    Console.WriteLine("Document size: {0} bytes", info.Size);
}
```
 Nesta etapa, o`GetDocumentInfo` O método recupera detalhes como tipo de arquivo, contagem de páginas e tamanho do documento. Essas informações são impressas no console, mas você pode usá-las em seu aplicativo conforme necessário.
## Etapa 3: adicionar uma marca d’água de texto
Agora que você carregou seu documento e suas informações em mãos, é hora de adicionar uma marca d’água. Começaremos com uma marca d'água de texto simples.

```csharp
using (Watermarker watermarker = new Watermarker("Your Document Path"))
{
    TextWatermark textWatermark = new TextWatermark("Confidential", new Font("Arial", 36));
    textWatermark.ForegroundColor = Color.Red;
    textWatermark.BackgroundColor = Color.Yellow;
    textWatermark.Opacity = 0.5;
    textWatermark.RotateAngle = 45;
    watermarker.Add(textWatermark);
    watermarker.Save("Watermarked Document Path");
}
```
 Aqui você cria um`TextWatermark` objeto com o texto, fonte e estilo desejados. Ajuste propriedades como cor, opacidade e ângulo de rotação para atender às suas necessidades. Finalmente, a marca d'água é adicionada ao documento e salva em um caminho especificado.
## Etapa 4: adicionar uma marca d’água de imagem
Marcas d'água de texto são ótimas, mas e se você quiser adicionar um logotipo ou outra imagem? Esta etapa aborda como adicionar uma marca d'água de imagem.

```csharp
using (Watermarker watermarker = new Watermarker("Your Document Path"))
{
    using (ImageWatermark imageWatermark = new ImageWatermark("Path to Your Image"))
    {
        imageWatermark.Opacity = 0.5;
        imageWatermark.RotateAngle = 30;
        watermarker.Add(imageWatermark);
        watermarker.Save("Watermarked Document Path");
    }
}
```
 Substituir`"Path to Your Image"` com o caminho para sua imagem de marca d'água. Defina propriedades como opacidade e ângulo de rotação para personalizar a aparência da marca d'água da sua imagem. O processo de adicionar e salvar a marca d’água é semelhante ao de uma marca d’água de texto.
## Etapa 5: remover marcas d'água existentes
 Às vezes, pode ser necessário remover marcas d'água existentes de um documento. Isto pode ser feito usando o`Remove` método fornecido pelo`Watermarker` aula.

```csharp
using (Watermarker watermarker = new Watermarker("Your Document Path"))
{
    watermarker.Remove(WatermarkType.Text);
    watermarker.Save("Cleaned Document Path");
}
```
 Aqui o`Remove` método é usado para remover marcas d’água de texto do documento. Você pode especificar diferentes tipos de marcas d'água para remover, como imagem ou texto, dependendo de suas necessidades. Salve o documento em um novo caminho para ver as alterações.
## Etapa 6: extrair marcas d'água
Se você precisar extrair e inspecionar marcas d'água de um documento, o GroupDocs.Watermark for .NET torna isso possível com facilidade.

```csharp
using (Watermarker watermarker = new Watermarker("Your Document Path"))
{
    IEnumerable<Watermark> watermarks = watermarker.GetWatermarks();
    foreach (Watermark watermark in watermarks)
    {
        Console.WriteLine("Watermark type: {0}", watermark.GetType().Name);
        // Propriedades e lógica adicionais para cada marca d'água
    }
}
```
 Esta etapa envolve o uso do`GetWatermarks`método para recuperar todas as marcas d'água em um documento. Você pode então percorrer a lista de marcas d'água e inspecionar suas propriedades ou executar ações adicionais conforme necessário.
## Conclusão
 Parabéns! Agora você aprendeu como usar GroupDocs.Watermark for .NET para adicionar, remover e extrair marcas d'água de seus documentos. Com essas habilidades, você pode proteger e marcar seus documentos de maneira eficaz. Lembre o[documentação](https://tutorials.groupdocs.com/Watermark/net/) está sempre disponível se você precisar de informações mais detalhadas ou funcionalidades avançadas.
## Perguntas frequentes
### Posso usar GroupDocs.Watermark for .NET com qualquer versão .NET?
 Sim, GroupDocs.Watermark for .NET é compatível com várias versões do .NET Framework. Verifica a[documentação](https://tutorials.groupdocs.com/Watermark/net/) para detalhes.
### Onde posso baixar GroupDocs.Watermark para .NET?
 Você pode baixar a versão mais recente no site[página de download](https://releases.groupdocs.com/Watermark/net/).
### Como faço para obter uma licença temporária?
 Você pode obter uma licença temporária do[página de licença temporária](https://purchase.groupdocs.com/temporary-license/).
### Existe um teste gratuito disponível?
 Sim, você pode iniciar uma avaliação gratuita visitando o[página de teste gratuito](https://releases.groupdocs.com/).
### Onde posso obter suporte se encontrar problemas?
 O suporte está disponível no[Fórum de marca d'água GroupDocs](https://forum.groupdocs.com/c/watermark/19).