---
title: Adicionar marca d'água bloqueada a todas as páginas em documentos do Word
linktitle: Adicionar marca d'água bloqueada a todas as páginas em documentos do Word
second_title: API GroupDocs.Watermark .NET
description: Proteja seus documentos adicionando marcas d’água bloqueadas usando Groupdocs.Watermark for .NET. Siga nosso guia passo a passo para fácil implementação.
weight: 11
url: /pt/net/word-processing-watermarkings/add-locked-watermark-all-pages-word-docs/
---
## Introdução
Adicionar marcas d'água aos seus documentos é uma etapa vital para proteger e promover a marca do seu conteúdo. Esteja você evitando o uso não autorizado ou simplesmente adicionando um toque profissional, as marcas d'água podem servir a vários propósitos. Neste tutorial, orientaremos você no processo de adição de uma marca d'água bloqueada a todas as páginas de um documento do Word usando Groupdocs.Watermark for .NET.
## Pré-requisitos
Antes de mergulharmos no guia passo a passo, vamos garantir que você tenha tudo o que precisa:
1. Groupdocs.Watermark para .NET: Baixe a versão mais recente em[aqui](https://releases.groupdocs.com/Watermark/net/).
2. .NET Framework: certifique-se de ter o .NET Framework instalado em sua máquina.
3. Ambiente de desenvolvimento: um ambiente de desenvolvimento como o Visual Studio.
4.  Licença: Você pode optar por uma[teste grátis](https://releases.groupdocs.com/) ou compre um[licença temporária](https://purchase.groupdocs.com/temporary-license/).
## Importar namespaces
Em primeiro lugar, você precisa importar os namespaces necessários para o seu projeto. Estes são essenciais para acessar as classes e métodos fornecidos pelo Groupdocs.Watermark.
```csharp
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Etapa 1: configure seu projeto

Abra seu ambiente de desenvolvimento e crie um novo projeto .NET. Pode ser um aplicativo de console ou qualquer outro tipo que atenda às suas necessidades.

Você precisa adicionar o pacote Groupdocs.Watermark ao seu projeto. Isso pode ser feito por meio do Gerenciador de pacotes NuGet. Execute o seguinte comando no console do gerenciador de pacotes NuGet:
```sh
Install-Package GroupDocs.Watermark
```
## Etapa 2: carregue o documento do Word
### Defina o caminho do documento
Especifique o caminho para o seu documento do Word. Este será o documento onde você deseja adicionar a marca d’água.
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
```
### Definir opções de carregamento
 Crie uma instância de`WordProcessingLoadOptions` para carregar seu documento do Word com opções específicas.
```csharp
var loadOptions = new WordProcessingLoadOptions();
```
## Etapa 3: crie a marca d’água
### Inicializar marcador d'água
 Usando o`Watermarker`class, carregue o documento com as opções de carregamento especificadas.
```csharp
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Outras etapas estarão dentro deste bloco usando
}
```
### Definir propriedades da marca d'água
 Criar uma`TextWatermark` instância com o texto, fonte e cor desejados.
```csharp
TextWatermark watermark = new TextWatermark("Watermark text", new Font("Arial", 19));
watermark.ForegroundColor = Color.Red;
```
## Etapa 4: aplicar marca d'água a todas as páginas
### Definir opções de marca d'água
 Definir`WordProcessingWatermarkPagesOptions` e definir o`IsLocked` propriedade como true para bloquear a marca d'água. Isso garante que a marca d'água não possa ser removida facilmente.
```csharp
WordProcessingWatermarkPagesOptions options = new WordProcessingWatermarkPagesOptions();
options.IsLocked = true;
options.LockType = WordProcessingLockType.AllowOnlyFormFields;
```
### Opcional: Adicionar proteção por senha
Se quiser adicionar uma camada extra de segurança, você pode definir uma senha para a marca d’água.
```csharp
// Para proteger com senha
// opções.Senha = "7654321";
```
### Adicione a marca d'água
 Use o`Add` método do`Watermarker` class para adicionar a marca d'água ao documento com as opções especificadas.
```csharp
watermarker.Add(watermark, options);
```
## Etapa 5: salve o documento
Finalmente, salve o documento modificado no arquivo de saída especificado.
```csharp
watermarker.Save(outputFileName);
```

## Conclusão
Seguindo essas etapas, você pode adicionar facilmente uma marca d’água bloqueada a todas as páginas de seus documentos do Word usando Groupdocs.Watermark for .NET. Isso não só ajuda a proteger seus documentos contra uso não autorizado, mas também adiciona um toque profissional ao seu conteúdo. Groupdocs.Watermark oferece uma solução abrangente para necessidades de marca d'água, garantindo que seus documentos permaneçam seguros e com marca.
## Perguntas frequentes
### Posso usar uma imagem como marca d’água em vez de texto?
 Sim, o Groupdocs suporta marcas d'água de texto e imagem. Você pode substituir`TextWatermark` com`ImageWatermark` e especifique sua imagem.
### É possível personalizar a posição da marca d'água?
 Absolutamente! Você pode definir a posição da marca d'água usando propriedades como`HorizontalAlignment` e`VerticalAlignment`.
### Posso aplicar marcas d'água diferentes em páginas diferentes do documento?
 Sim, você pode personalizar marcas d'água para páginas específicas usando o`PageIndex` propriedade no`WordProcessingWatermarkPagesOptions`.
### O Groupdocs.Watermark oferece suporte a outros formatos de documento além do Word?
Sim, o Groupdocs suporta vários formatos, incluindo PDF, Excel, PowerPoint e muito mais.
### Quais são os requisitos de sistema para usar Groupdocs.Watermark?
Você precisa de um sistema com .NET Framework instalado e um ambiente de desenvolvimento como o Visual Studio.