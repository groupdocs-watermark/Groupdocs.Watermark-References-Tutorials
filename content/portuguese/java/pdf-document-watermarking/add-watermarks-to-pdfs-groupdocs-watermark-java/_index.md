---
date: '2026-08-09'
description: Aprenda como adicionar marca d'água a PDF usando GroupDocs.Watermark
  for Java. Este java pdf watermark example mostra marcas d'água de texto e imagem,
  salvando PDFs com marca d'água.
keywords:
- add watermark to pdf
- save pdf with watermark
- java pdf watermark example
lastmod: '2026-08-09'
og_description: Aprenda como adicionar marca d'água a PDF usando GroupDocs.Watermark
  for Java. Este passo a passo java pdf watermark example ajuda você a salvar PDF
  com marca d'água rapidamente.
og_image_alt: Guide showing how to add text and image watermarks to PDF files in Java
og_title: Adicionar marca d'água ao PDF com GroupDocs.Watermark for Java
schemas:
- author: GroupDocs
  dateModified: '2026-08-09'
  description: Learn how to add watermark to PDF using GroupDocs.Watermark for Java.
    This java pdf watermark example shows text and image watermarks, saving PDFs with
    watermark.
  headline: Add watermark to PDF with GroupDocs.Watermark for Java
  type: TechArticle
- description: Learn how to add watermark to PDF using GroupDocs.Watermark for Java.
    This java pdf watermark example shows text and image watermarks, saving PDFs with
    watermark.
  name: Add watermark to PDF with GroupDocs.Watermark for Java
  steps:
  - name: create TextWatermark instance
    text: 'Create a `TextWatermark` using the desired text and font settings: This
      example sets the watermark text to “Protected image” using Arial, size 8.'
  - name: set alignment
    text: 'Center the watermark horizontally and vertically for uniform positioning:'
  - name: rotate watermark
    text: 'Apply a 45‑degree rotation to make the watermark harder to remove:'
  - name: configure sizing
    text: 'Scale the watermark relative to the target image dimensions:'
  - name: load image file
    text: 'Load the watermark image from disk: Replace the placeholder path with the
      actual location of your logo or seal.'
  - name: set alignment
    text: 'Center the image watermark for balanced visual impact:'
  - name: rotate image watermark
    text: 'Apply a –30‑degree rotation to introduce visual variation:'
  - name: configure sizing
    text: 'Define the image size as a percentage of the underlying image’s width:'
  - name: open the document
    text: 'Instantiate a `Watermarker` with the path to your source PDF:'
  - name: retrieve images
    text: 'Collect all images from the PDF that can receive a watermark:'
  type: HowTo
- questions:
  - answer: Yes. Open the document with `new Watermarker("file.pdf", "password")`
      and then apply the watermark as usual.
    question: Can I add a watermark to a password‑protected PDF?
  - answer: Absolutely. Loop through a folder of PDFs, instantiate a `Watermarker`
      for each file, apply the same watermark objects, and save the results.
    question: Does the API support batch processing of multiple PDFs?
  - answer: The library can handle **500+ watermarks per document** without performance
      degradation, thanks to its optimized rendering engine.
    question: What is the maximum number of watermarks I can add to a single PDF?
  - answer: Yes. Use the `setOpacity(0)` method on the watermark object to embed it
      invisibly for forensic tracking.
    question: Is it possible to make the watermark invisible (metadata only)?
  - answer: GroupDocs.Watermark for Java supports JDK 8, 11, and 17, ensuring compatibility
      with both legacy and modern applications.
    question: Which Java versions are officially supported?
  type: FAQPage
tags:
- pdf watermark
- GroupDocs.Watermark
- Java document security
title: Adicionar marca d'água ao PDF com GroupDocs.Watermark for Java
type: docs
url: /pt/java/pdf-document-watermarking/add-watermarks-to-pdfs-groupdocs-watermark-java/
weight: 1
---

# Adicionar marca d'água a PDF com GroupDocs.Watermark para Java

## Introdução

No cenário digital atual, proteger a propriedade intelectual é crucial, e **add watermark to PDF** é uma das maneiras mais eficazes de fazer isso. Este tutorial orienta você a usar o GroupDocs.Watermark para Java para incorporar marcas d'água de texto e imagem em arquivos PDF. Ao final, você será capaz de:

- Inicializar marcas d'água de texto e imagem
- Aplicar marcas d'água condicionalmente com base nas dimensões da imagem
- **save PDF with watermark** preservando a qualidade original

Pronto para proteger seus documentos? Vamos começar!

## Respostas rápidas
- **Qual biblioteca adiciona marcas d'água a PDFs em Java?** GroupDocs.Watermark for Java.
- **Posso adicionar marcas d'água de texto e imagem?** Yes, the API supports both types in a single run.
- **Preciso de licença para desenvolvimento?** A free trial works for testing; a permanent license is required for production.
- **Quais formatos de arquivo são suportados?** Over 30 formats, including PDF, DOCX, PPTX, and images.
- **Qual o tamanho máximo de PDF que pode ser processado?** Up to 2,000 pages without loading the whole file into memory.

## O que é adicionar marca d'água a PDF?
**Add watermark to PDF** significa incorporar marcas visíveis ou invisíveis — como cadeias de texto ou logotipos — diretamente em um arquivo PDF para indicar propriedade, confidencialidade ou branding. Esse processo modifica as camadas visuais do documento enquanto mantém o conteúdo original intacto.

## Por que usar GroupDocs.Watermark para Java?
GroupDocs.Watermark suporta **30+ formatos de documento**, pode processar PDFs de até **2.000 páginas** em uma única passagem e adiciona até **500 marcas d'água por documento** sem impacto perceptível de desempenho. Sua API é totalmente thread‑safe, tornando‑a ideal para ambientes de servidor de alta taxa de transferência.

## Pré-requisitos

Antes de prosseguir, confirme que você tem:

1. **Java Development Kit (JDK):** Versão 8 ou mais recente instalada.
2. **GroupDocs.Watermark for Java:** Versão 24.11 (ou mais recente) adicionada ao seu projeto.
3. **Ferramenta de compilação:** Maven preferido, mas um download direto de JAR também funciona.

### Configuração do ambiente

#### Configuração do Maven

Adicione o repositório GroupDocs e a dependência ao seu arquivo `pom.xml`:

```xml
<repositories>
   <repository>
      <id>repository.groupdocs.com</id>
      <name>GroupDocs Repository</name>
      <url>https://releases.groupdocs.com/watermark/java/</url>
   </repository>
</repositories>

<dependencies>
   <dependency>
      <groupId>com.groupdocs</groupId>
      <artifactId>groupdocs-watermark</artifactId>
      <version>24.11</version>
   </dependency>
</dependencies>
```

#### Download direto

Alternativamente, faça download do JAR mais recente na página oficial de lançamentos: [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

### Aquisição de licença

Para um teste gratuito ou uma licença temporária, visite o portal de licenciamento: [GroupDocs Licensing](https://purchase.groupdocs.com/temporary-license). Implantações em produção devem usar uma licença adquirida para remover todas as limitações de teste.

## Configurando o GroupDocs.Watermark para Java

Após adicionar a biblioteca, importe as classes necessárias ao seu arquivo fonte Java:

```java
import com.groupdocs.watermark.Watermarker;
```

## Guia de implementação

Dividiremos a implementação em seções lógicas, cada uma respondendo a uma pergunta específica.

### Como adicionar marca d'água a PDF em Java?

`Watermarker` é a classe principal que carrega um documento e permite que marcas d'água sejam aplicadas.  
Carregue seu PDF com `new Watermarker("input.pdf")` e então aplique um objeto de marca d'água antes de chamar `save("output.pdf")`. Essa abordagem em duas etapas lida com marcas d'água de texto e imagem em uma única passagem, garantindo que o arquivo seja **saved PDF with watermark** de forma eficiente.

### Inicializar marca d'água de texto

**Definition anchor:** `TextWatermark` é a classe que representa uma sobreposição textual que pode ser colocada em páginas, imagens ou gráficos vetoriais dentro de um documento.

#### Etapa 1: criar instância TextWatermark

Crie um `TextWatermark` usando o texto desejado e as configurações de fonte:

```java
// Create a text watermark with custom settings
TextWatermark textWatermark = new TextWatermark("Protected image", new Font("Arial", 8));
```

Este exemplo define o texto da marca d'água como “Protected image” usando Arial, tamanho 8.

#### Etapa 2: definir alinhamento

Centralize a marca d'água horizontal e verticalmente para posicionamento uniforme:

```java
// Align watermark to the center of images
textWatermark.setHorizontalAlignment(HorizontalAlignment.Center);
textWatermark.setVerticalAlignment(VerticalAlignment.Center);
```

#### Etapa 3: girar a marca d'água

Aplique uma rotação de 45 graus para tornar a marca d'água mais difícil de remover:

```java
// Rotate the watermark by 45 degrees
textWatermark.setRotateAngle(45);
```

#### Etapa 4: configurar dimensionamento

Escalone a marca d'água em relação às dimensões da imagem alvo:

```java
// Scale watermark based on parent image size
textWatermark.setSizingType(SizingType.ScaleToParentDimensions);
textWatermark.setScaleFactor(1);
```

### Inicializar marca d'água de imagem

**Definition anchor:** `ImageWatermark` encapsula uma imagem (PNG, JPEG, BMP, etc.) que será sobreposta ao conteúdo do documento como marca d'água.

#### Etapa 1: carregar arquivo de imagem

Carregue a imagem da marca d'água do disco:

```java
// Load an image file as a watermark
ImageWatermark imageWatermark = new ImageWatermark("YOUR_DOCUMENT_DIRECTORY\ProtectJpg");
```

Substitua o caminho placeholder pela localização real do seu logotipo ou selo.

#### Etapa 2: definir alinhamento

Centralize a marca d'água de imagem para um impacto visual equilibrado:

```java
// Align image watermark to the center
imageWatermark.setHorizontalAlignment(HorizontalAlignment.Center);
imageWatermark.setVerticalAlignment(VerticalAlignment.Center);
```

#### Etapa 3: girar a marca d'água de imagem

Aplique uma rotação de –30 graus para introduzir variação visual:

```java
// Rotate the image watermark by -45 degrees
textWatermark.setRotateAngle(-45);
```

#### Etapa 4: configurar dimensionamento

Defina o tamanho da imagem como uma porcentagem da largura da imagem subjacente:

```java
// Scale the image watermark relative to its parent dimensions
imageWatermark.setSizingType(SizingType.ScaleToParentDimensions);
imageWatermark.setScaleFactor(1);
```

### Adicionar marcas d'água a imagens em um documento

**Definition anchor:** `Watermarker` é a classe central que carrega um documento, fornece acesso aos seus elementos e grava marcas d'água de volta no arquivo.

#### Etapa 1: abrir o documento

Instancie um `Watermarker` com o caminho para o seu PDF de origem:

```java
// Open the PDF containing images for watermarking
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY\document.pdf");
```

#### Etapa 2: recuperar imagens

Colete todas as imagens do PDF que podem receber uma marca d'água:

```java
// Get a collection of all images within the PDF
WatermarkableImageCollection images = watermarker.getImages();
```

#### Etapa 3: adicionar marcas d'água condicionalmente

Para cada imagem, verifique suas dimensões; se a largura exceder 300 px, aplique a marca d'água de texto, caso contrário use a marca d'água de imagem:

```java
for (int i = 0; i < images.getCount(); i++) {
    // Check if the image exceeds specific size criteria
    if (images.get_Item(i).getWidth() > 100 && images.get_Item(i).getHeight() > 100) {
        // Alternate between text and image watermarks
        if (i % 2 == 0) {
            images.get_Item(i).add(textWatermark);
        } else {
            images.get_Item(i).add(imageWatermark);
        }
    }
}
```

Essa lógica condicional garante que apenas imagens adequadas recebam a sobreposição de texto mais proeminente, otimizando o tempo de processamento.

#### Etapa 4: liberar recursos de imagem

Após o processamento, feche o objeto de marca d'água de imagem para liberar recursos nativos:

```java
// Close the image watermark instance after use
imageWatermark.close();
```

#### Etapa 5: salvar alterações

Persista as modificações salvando o documento em um novo arquivo:

```java
// Save the PDF with added watermarks in a new file
watermarker.save("YOUR_OUTPUT_DIRECTORY\document.pdf");
```

O arquivo resultante é uma versão **save PDF with watermark** pronta para distribuição.

#### Etapa 6: limpeza

Descarte a instância `Watermarker` para evitar vazamentos de memória:

```java
// Close the main watermarker to release document resources
watermarker.close();
```

## Problemas comuns e solução de problemas

- **License errors:** Certifique-se de que o caminho do arquivo de licença está definido corretamente via `License.setLicense("license_file_path")`. Uma licença ausente ou expirada lança uma `LicenseException`.
- **Large PDFs:** Para documentos com mais de 1.000 páginas, habilite o modo de streaming chamando `watermarker.setStreamMode(true)` para manter baixo o consumo de memória.
- **Unsupported image formats:** GroupDocs.Watermark suporta PNG, JPEG, BMP e GIF. Converter outros formatos para PNG antes de carregar evita `UnsupportedFormatException`.

## Perguntas frequentes

**Q: Posso adicionar uma marca d'água a um PDF protegido por senha?**  
A: Yes. Open the document with `new Watermarker("file.pdf", "password")` and then apply the watermark as usual.

**Q: A API suporta processamento em lote de múltiplos PDFs?**  
A: Absolutely. Loop through a folder of PDFs, instantiate a `Watermarker` for each file, apply the same watermark objects, and save the results.

**Q: Qual é o número máximo de marcas d'água que posso adicionar a um único PDF?**  
A: The library can handle **500+ watermarks per document** without performance degradation, thanks to its optimized rendering engine.

**Q: É possível tornar a marca d'água invisível (apenas metadados)?**  
A: Yes. Use the `setOpacity(0)` method on the watermark object to embed it invisibly for forensic tracking.

**Q: Quais versões do Java são oficialmente suportadas?**  
A: GroupDocs.Watermark for Java supports JDK 8, 11, and 17, ensuring compatibility with both legacy and modern applications.

## Aplicações práticas

Adicionar marcas d'água pode servir a diversos cenários reais:

1. **Document security:** Marcar arquivos confidenciais para desencorajar compartilhamento não autorizado.
2. **Brand protection:** Sobrepor logotipos da empresa em PDFs de marketing.
3. **Copyright assertion:** Incorporar nomes de autores ou símbolos de copyright em obras publicadas.
4. **Version control:** Carimbar números de versão ou datas em documentos de rascunho.

## Conclusão

Seguindo este **java pdf watermark example**, você agora tem uma solução completa e pronta para produção para **add watermark to PDF** usando o GroupDocs.Watermark para Java. Você pode personalizar texto, imagens, rotação e dimensionamento, bem como aplicar marcas d'água condicionalmente com base nas dimensões da imagem — tudo mantendo o processo rápido e eficiente em memória.

---  

**Última atualização:** 2026-08-09  
**Testado com:** GroupDocs.Watermark 24.11 for Java  
**Autor:** GroupDocs

## Tutoriais relacionados

- [Como adicionar marcas d'água de texto e imagem a páginas PDF específicas usando GroupDocs.Watermark para Java](/watermark/java/pdf-document-watermarking/add-watermarks-pdf-pages-groupdocs-java/)
- [Adicionar marcas d'água apenas para impressão a PDFs usando GroupDocs.Watermark Java: Um guia abrangente](/watermark/java/pdf-document-watermarking/groupdocs-watermark-java-print-only-pdf-watermark/)
- [Acessar e iterar sobre artefatos PDF usando GroupDocs.Watermark em Java para marca d'água de documentos](/watermark/java/pdf-document-watermarking/access-iterate-pdf-artifacts-groupdocs-watermark-java/)