---
title: Gerar visualização do documento
linktitle: Gerar visualização do documento
second_title: API GroupDocs.Watermark .NET
description: Aprenda como gerar visualizações de documentos usando GroupDocs.Watermark for .NET com este guia. Melhore a segurança e o gerenciamento de seus documentos sem esforço.
weight: 10
url: /pt/net/document-manipulation/generate-document-preview/
type: docs
---
# Gerar visualização do documento

## Introdução
No mundo da gestão de documentos digitais, a marca d'água desempenha um papel crucial para garantir a segurança e autenticidade dos documentos. GroupDocs.Watermark for .NET é uma ferramenta poderosa que permite aos desenvolvedores adicionar marcas d’água a documentos sem esforço. Neste tutorial, orientaremos você no processo de geração de visualizações de documentos usando GroupDocs.Watermark for .NET. Quer você seja um desenvolvedor experiente ou esteja apenas começando, este guia fornecerá um processo passo a passo abrangente para atingir seu objetivo.
## Pré-requisitos
Antes de mergulhar na implementação, vamos ter certeza de que você tem tudo o que precisa para começar:
- Uma compreensão básica do C# e do .NET framework.
- Visual Studio instalado em sua máquina.
- GroupDocs.Watermark para biblioteca .NET. Você pode[baixe aqui](https://releases.groupdocs.com/Watermark/net/).
-  Uma licença válida para GroupDocs.Watermark. Você pode comprá-lo[aqui](https://purchase.groupdocs.com/buy) ou obter um[licença temporária](https://purchase.groupdocs.com/temporary-license/) para fins de avaliação.
## Importar namespaces
Para começar a usar GroupDocs.Watermark em seu projeto, você precisará importar os namespaces necessários. Isso pode ser feito adicionando as seguintes diretivas using ao seu código:
```csharp
using System;
using System.IO;
using GroupDocs.Watermark.Options;
```
Esses namespaces fornecerão acesso às classes e métodos necessários para colocar marcas d'água e gerar visualizações de documentos.

Vamos dividir o processo de geração de uma visualização de documento em etapas simples e fáceis de seguir.
## Etapa 1: configure seu projeto
Primeiramente, configure seu projeto .NET no Visual Studio. Se você ainda não tem um projeto, crie um novo seguindo estas etapas:
1. Abra o Visual Studio.
2. Clique em “Criar um novo projeto”.
3. Selecione “Aplicativo de console (.NET Core)” e clique em “Avançar”.
4. Dê um nome ao seu projeto e escolha um local para salvá-lo e clique em “Criar”.
## Etapa 2: Instale GroupDocs.Watermark para .NET
Para usar GroupDocs.Watermark em seu projeto, você precisa instalar a biblioteca. Isso pode ser feito usando o Gerenciador de Pacotes NuGet:
1. Clique com o botão direito em seu projeto no Solution Explorer.
2. Selecione "Gerenciar pacotes NuGet".
3. Procure por "GroupDocs.Watermark" na guia Navegar.
4. Clique em “Instalar” para adicionar a biblioteca ao seu projeto.
Alternativamente, você pode instalá-lo através do Console do Gerenciador de Pacotes:
```powershell
Install-Package GroupDocs.Watermark
```
## Etapa 3: definir o caminho do documento e o diretório de saída
Antes de gerar a visualização, você precisa especificar o caminho do documento que deseja visualizar e o diretório onde as imagens de visualização serão salvas:
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
```
Substitua “Your Document Path” pelo caminho do seu documento e “Your Document Directory” pelo diretório onde você deseja salvar as imagens de visualização.
## Etapa 4: inicializar o objeto Watermarker
Crie uma instância do`Watermarker` classe passando o caminho do documento para seu construtor. Este objeto será usado para realizar todas as operações de marca d’água:
```csharp
using (Watermarker watermarker = new Watermarker(documentPath))
{
    // Seu código aqui
}
```
## Etapa 5: Criar métodos delegados para manipulação de fluxo
Para gerar a visualização, você precisa definir métodos delegados para criar e liberar fluxos. Estes métodos cuidarão da criação e liberação de fluxos para cada página do documento:
```csharp
CreatePageStream createPageStreamDelegate = delegate(int number)
{
    string previewImageFileName = Path.Combine(outputDirectory, string.Format("page{0}.png", number));
    return File.OpenWrite(previewImageFileName);
};
ReleasePageStream releasePageStreamDelegate = delegate(int number, Stream stream)
{
    stream.Close();
};
```
 O`createPageStreamDelegate` método cria um fluxo para cada página do documento, enquanto o método`releasePageStreamDelegate` O método fecha o fluxo após a geração da visualização.
## Etapa 6: configurar opções de visualização
 A seguir, configure as opções de visualização criando uma instância do`PreviewOptions` aula. Especifique os métodos delegados e defina o formato de visualização como PNG. Você também pode especificar quais páginas incluir na visualização:
```csharp
PreviewOptions previewOptions = new PreviewOptions(createPageStreamDelegate, releasePageStreamDelegate)
{
    PreviewFormat = PreviewOptions.PreviewFormats.PNG,
    PageNumbers = new[] { 1, 2 }
};
```
Neste exemplo, estamos gerando visualizações para as duas primeiras páginas do documento.
## Etapa 7: gerar a visualização do documento
 Por fim, ligue para o`GeneratePreview` método no`Watermarker`objeto, passando o configurado`PreviewOptions`. Isso irá gerar as imagens de visualização e salvá-las no diretório especificado:
```csharp
watermarker.GeneratePreview(previewOptions);
```
## Conclusão
Gerar visualizações de documentos usando GroupDocs.Watermark for .NET é um processo simples que pode ser realizado com apenas algumas linhas de código. Seguindo as etapas descritas neste guia, você pode facilmente configurar seu projeto, configurar as opções necessárias e gerar visualizações para seus documentos. Esta poderosa biblioteca não apenas simplifica o processo de criação de marcas d'água, mas também fornece recursos robustos para gerenciar e manipular marcas d'água.
 Se você tiver alguma dúvida ou precisar de mais assistência, não hesite em visitar o[Fórum de suporte GroupDocs.Watermark](https://forum.groupdocs.com/c/watermark/19) ou consulte o[documentação](https://tutorials.groupdocs.com/Watermark/net/).
## Perguntas frequentes
### Quais formatos de arquivo são suportados pelo GroupDocs.Watermark for .NET?
 GroupDocs.Watermark for .NET oferece suporte a uma ampla variedade de formatos de arquivo, incluindo PDF, DOCX, PPTX, XLSX e muitos mais. Para obter uma lista completa de formatos suportados, consulte o[documentação](https://tutorials.groupdocs.com/Watermark/net/).
### Posso personalizar a aparência das marcas d’água?
Sim, GroupDocs.Watermark permite que você personalize totalmente a aparência das marcas d'água, incluindo texto, imagem e formas de marcas d'água. Você pode ajustar propriedades como fonte, cor, tamanho e transparência.
### Existe uma versão de teste disponível?
 Sim, você pode obter um[teste grátis](https://releases.groupdocs.com/) do GroupDocs.Watermark for .NET para avaliar seus recursos antes de fazer uma compra.
### Como posso adquirir uma licença do GroupDocs.Watermark?
 Você pode comprar uma licença para GroupDocs.Watermark[aqui](https://purchase.groupdocs.com/buy). Existem várias opções de licenciamento disponíveis para atender a diferentes necessidades.
### Posso usar GroupDocs.Watermark em um projeto comercial?
 Sim, com uma licença válida, você pode usar GroupDocs.Watermark em projetos comerciais. Certifique-se de revisar os termos e condições de licenciamento no[página de compra](https://purchase.groupdocs.com/buy).