---
date: '2026-10-27'
description: Aprenda a excluir text watermark de arquivos de diagramas usando GroupDocs.Watermark
  for Java e detectar image watermark de forma eficiente. Guia passo a passo para
  desenvolvedores.
keywords:
- delete text watermark
- detect image watermark
- GroupDocs.Watermark Java
lastmod: '2026-10-27'
og_description: Excluir text watermark de arquivos de diagramas com GroupDocs.Watermark
  for Java. Aprenda a detectar image watermark, pesquisar e remover watermarks com
  code snippets.
og_image_alt: Diagram file with watermark management using GroupDocs.Watermark for
  Java
og_title: Excluir text watermark em arquivos de diagramas usando Java rapidamente
schemas:
- author: GroupDocs
  dateModified: '2026-10-27'
  description: Learn how to delete text watermark from diagram files using GroupDocs.Watermark
    for Java and detect image watermark efficiently. Step‑by‑step guide for developers.
  headline: How to delete text watermark in diagrams with Java
  type: TechArticle
- description: Learn how to delete text watermark from diagram files using GroupDocs.Watermark
    for Java and detect image watermark efficiently. Step‑by‑step guide for developers.
  name: How to delete text watermark in diagrams with Java
  steps:
  - name: '**Java Development Kit (JDK)** 8 or higher.'
    text: '**Java Development Kit (JDK)** 8 or higher.'
  - name: '**IDE** – IntelliJ IDEA, Eclipse, or any editor you prefer.'
    text: '**IDE** – IntelliJ IDEA, Eclipse, or any editor you prefer.'
  - name: '**GroupDocs.Watermark for Java** – the library JAR(s) must be on your classpath.'
    text: '**GroupDocs.Watermark for Java** – the library JAR(s) must be on your classpath.'
  - name: '**Install the library** – ensure the Maven repository and dependency entries
      are present, or place the JAR files in `libs/` and add them to your project’s
      build path.'
    text: '**Install the library** – ensure the Maven repository and dependency entries
      are present, or place the JAR files in `libs/` and add them to your project’s
      build path.'
  - name: '**Initialize the API** – create a `Watermarker` instance; this object is
      the entry point for loading diagrams and performing watermark operations.'
    text: '**Initialize the API** – create a `Watermarker` instance; this object is
      the entry point for loading diagrams and performing watermark operations.'
  - name: '**Enterprise software integration** – embed watermark management into document‑centric
      business applications to protect proprietary diagrams.'
    text: '**Enterprise software integration** – embed watermark management into document‑centric
      business applications to protect proprietary diagrams.'
  - name: '**Content Management Systems (CMS)** – automate detection of unauthorized
      logos before publishing user‑generated diagrams.'
    text: '**Content Management Systems (CMS)** – automate detection of unauthorized
      logos before publishing user‑generated diagrams.'
  - name: '**Legal document handling** – add or delete watermarks at different stages
      of a case file workflow, ensuring compliance with confidentiality policies.'
    text: '**Legal document handling** – add or delete watermarks at different stages
      of a case file workflow, ensuring compliance with confidentiality policies.'
  type: HowTo
- questions:
  - answer: Yes – combine `TextSearchCriteria` and `ImageDctHashSearchCriteria` with
      the `or()` operator to locate both types in a single pass.
    question: Can I search for both text and images simultaneously?
  - answer: Absolutely. The API isolates watermark objects and removes them, leaving
      the original diagram structure intact.
    question: Is it possible to delete watermarks without damaging the diagram?
  - answer: Yes – it supports over 20 formats, including `.vsdx`, `.vdx`, `.drawio`,
      and `.svg`, enabling broad‑range diagram management.
    question: Does GroupDocs.Watermark support multiple diagram formats?
  - answer: Use batch processing loops, reuse a single `Watermarker` instance where
      possible, and tune `LoadOptions` to stream pages instead of loading whole files.
    question: How do I handle large volumes of documents efficiently?
  - answer: Yes – the library is headless and can be called from Maven, Gradle, or
      any build script to validate diagram assets automatically.
    question: Can I integrate watermark detection into a CI/CD pipeline?
  type: FAQPage
tags:
- watermark management
- GroupDocs.Watermark
- Java diagram processing
title: Como excluir text watermark em arquivos de diagramas com Java
type: docs
url: /pt/java/diagram-document-watermarking/manage-watermarks-groupdocs-java-diagrams/
weight: 1
---

# Como excluir marca d'água de texto em diagramas com Java

Gerenciar marcas d'água em documentos é essencial para proteger a propriedade intelectual e manter a integridade dos documentos. Neste tutorial, você aprenderá como **excluir marca d'água de texto** de arquivos de diagramas como `.vsdx` usando GroupDocs.Watermark para Java, e também como **detectar marca d'água de imagem** quando necessário. Seja construindo um pipeline de documentos de nível empresarial ou automatizando um trabalho em lote simples, essas técnicas dão a você controle granular sobre as marcas d'água em diagramas.

**O que você aprenderá**
- Configurando a biblioteca GroupDocs.Watermark
- Carregando um documento de diagrama com opções específicas
- Pesquisando e excluindo marcas d'água de texto
- Detectando marcas d'água de imagem e removendo-as
- Dicas de boas práticas para processamento em grande escala

Pronto para mergulhar? Vamos preparar seu ambiente primeiro.

## Respostas rápidas
- **Posso excluir tanto marcas d'água de texto quanto de imagem de uma vez?** Sim – combine `TextSearchCriteria` e `ImageDctHashSearchCriteria` com uma condição `or()`.  
- **A biblioteca carrega todo o diagrama na memória?** Não – ela transmite páginas, permitindo arquivos de até 500 MB sem consumo total de memória.  
- **Quais formatos de diagrama são suportados?** Mais de 20 formatos, incluindo `.vsdx`, `.vdx` e `.drawio`.  
- **É necessária uma licença para produção?** É necessária uma licença válida do GroupDocs.Watermark para uso não‑trial.  
- **Posso executar isso em um pipeline CI/CD?** Absolutamente – a API é sem interface gráfica e funciona no Windows, Linux e macOS.

## O que é excluir marca d'água de texto?
Excluir marca d'água de texto significa remover objetos de sobreposição baseados em texto que foram adicionados a um documento para indicar propriedade, confidencialidade ou status de rascunho. No GroupDocs.Watermark, essa operação é realizada localizando os objetos de marca d'água com critérios de pesquisa e, em seguida, chamando `clear()` na coleção resultante.

## Por que detectar marca d'água de imagem?
Detectar marca d'água de imagem permite identificar logotipos ou selos gráficos que foram incorporados a um diagrama. Isso é crucial para verificações de conformidade, proteção de marca e moderação automática de conteúdo. O GroupDocs.Watermark usa hashing perceptual (DCT) para comparar imagens de forma rápida e precisa.

## Pré-requisitos
Antes de começarmos, certifique‑se de que você tem:
1. **Java Development Kit (JDK)** 8 ou superior.  
2. **IDE** – IntelliJ IDEA, Eclipse ou qualquer editor de sua preferência.  
3. **GroupDocs.Watermark for Java** – o(s) JAR da biblioteca devem estar no seu classpath.  

### Bibliotecas e dependências necessárias
Você pode adicionar a biblioteca via Maven ou baixar os JARs manualmente.

#### Configuração Maven
Add the following configuration to your `pom.xml` file:

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
Alternativamente, baixe a versão mais recente em [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

### Aquisição de licença
- **Teste gratuito** – teste todos os recursos sem uma chave de licença.  
- **Licença temporária** – solicite uma chave de tempo limitado para avaliação.  
- **Compra** – obtenha uma licença perpétua ou por assinatura para uso em produção.

## Configurando o GroupDocs.Watermark para Java
1. **Instalar a biblioteca** – certifique‑se de que o repositório Maven e as entradas de dependência estejam presentes, ou coloque os arquivos JAR em `libs/` e adicione‑os ao caminho de compilação do seu projeto.  
2. **Inicializar a API** – crie uma instância `Watermarker`; este objeto é o ponto de entrada para carregar diagramas e executar operações de marca d'água.

## Como excluir marca d'água de texto em diagramas com Java
Para excluir uma marca d'água de texto, carregue o diagrama com `Watermarker`, crie um `TextSearchCriteria` que corresponda ao texto da marca d'água, recupere a `PossibleWatermarkCollection` correspondente e chame `clear()` nela. Isso remove apenas as sobreposições de texto especificadas, mantendo o restante do diagrama intacto.

A classe `Watermarker` representa um único documento na memória e fornece métodos para carregar, pesquisar e modificar marcas d'água.

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.DiagramLoadOptions;

public class LoadDiagramDocument {
    public static void main(String[] args) {
        String inputFilePath = "YOUR_DOCUMENT_DIRECTORY/diagram.vsdx";
        DiagramLoadOptions loadOptions = new DiagramLoadOptions();
        
        Watermarker watermarker = new Watermarker(inputFilePath, loadOptions);
        watermarker.close();
    }
}
```
- **Parâmetros:**  
  - `inputFilePath`: Caminho para o seu arquivo `.vsdx`.  
  - `loadOptions`: Configura como o documento é carregado (ex.: intervalo de páginas, senha).

## Como detectar marca d'água de imagem em um arquivo de diagrama?
A detecção de uma marca d'água de imagem envolve criar um `ImageDctHashSearchCriteria` com uma imagem de referência, e então usar o `Watermarker` para pesquisar o diagrama. A API gera um hash perceptual de cada imagem incorporada e a compara com a referência, retornando correspondências com pontuações de similaridade para que você possa identificar e remover logotipos ou selos indesejados.

`ImageDctHashSearchCriteria` cria um hash da imagem de referência e a compara com as imagens incorporadas no diagrama, retornando correspondências com uma pontuação de similaridade.

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.contents.DiagramContent;
import com.groupdocs.watermark.search.TextSearchCriteria;
import com.groupdocs.watermark.search.PossibleWatermarkCollection;

public class SearchTextWatermarks {
    public static void main(String[] args) throws Exception {
        String inputFilePath = "YOUR_DOCUMENT_DIRECTORY/diagram.vsdx";
        Watermarker watermarker = new Watermarker(inputFilePath);

        DiagramContent content = watermarker.getContent(DiagramContent.class);
        
        TextSearchCriteria textSearchCriteria = new TextSearchCriteria("Company Name");
        PossibleWatermarkCollection possibleWatermarks = content.getPages().get_Item(0).search(textSearchCriteria);

        watermarker.close();
    }
}
```
- **Métodos principais:**  
  - `TextSearchCriteria` – cria critérios para marcas d'água baseadas em texto.  
  - `PossibleWatermarkCollection` – contém os resultados de qualquer operação de pesquisa.

## Como remover marcas d'água depois de encontrá‑las?
Uma vez que as marcas d'água são identificadas, você pode removê‑las chamando o método `clear()` na `PossibleWatermarkCollection` retornada pela pesquisa. Esta operação exclui os objetos de marca d'água enquanto preserva todos os demais elementos do diagrama, garantindo que o conteúdo original permaneça totalmente inalterado.

`clear()` remove todas as marcas d'água na coleção enquanto preserva o restante do conteúdo do diagrama.

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.contents.DiagramContent;
import com.groupdocs.watermark.search.ImageDctHashSearchCriteria;
import com.groupdocs.watermark.search.PossibleWatermarkCollection;

public class SearchImageWatermarks {
    public static void main(String[] args) throws Exception {
        String inputFilePath = "YOUR_DOCUMENT_DIRECTORY/diagram.vsdx";
        String imagePath = "YOUR_DOCUMENT_DIRECTORY/logo.png";
        
        Watermarker watermarker = new Watermarker(inputFilePath);
        DiagramContent content = watermarker.getContent(DiagramContent.class);

        ImageDctHashSearchCriteria imageSearchCriteria = new ImageDctHashSearchCriteria(imagePath);
        PossibleWatermarkCollection possibleWatermarks = content.getPages().get_Item(0).search(imageSearchCriteria);

        watermarker.close();
    }
}
```
- **Método principal:** `clear()` – exclui todas as marcas d'água na coleção fornecida sem alterar outros elementos do diagrama.

## Aplicações práticas
1. **Integração de software empresarial** – incorpore a gestão de marcas d'água em aplicações de negócios centradas em documentos para proteger diagramas proprietários.  
2. **Sistemas de Gerenciamento de Conteúdo (CMS)** – automatize a detecção de logotipos não autorizados antes de publicar diagramas gerados por usuários.  
3. **Manipulação de documentos legais** – adicione ou exclua marcas d'água em diferentes estágios de um fluxo de trabalho de arquivos de caso, garantindo conformidade com políticas de confidencialidade.

## Armadilhas comuns e solução de problemas
- **Arquivos grandes** – aumente a configuração `maxMemory` em `LoadOptions` se encontrar `OutOfMemoryError`.  
- **Diagramas protegidos por senha** – forneça a senha em `LoadOptions` para abrir o arquivo.  
- **Correspondências de hash de imagem ausentes** – certifique‑se de que a imagem de referência tenha resolução suficiente; imagens de baixa resolução podem gerar hashes fracos.

## Perguntas frequentes

**Q: Posso pesquisar tanto texto quanto imagens simultaneamente?**  
A: Sim – combine `TextSearchCriteria` e `ImageDctHashSearchCriteria` com o operador `or()` para localizar ambos os tipos em uma única passagem.

**Q: É possível excluir marcas d'água sem danificar o diagrama?**  
A: Absolutamente. A API isola os objetos de marca d'água e os remove, deixando a estrutura original do diagrama intacta.

**Q: O GroupDocs.Watermark suporta múltiplos formatos de diagrama?**  
A: Sim – ele suporta mais de 20 formatos, incluindo `.vsdx`, `.vdx`, `.drawio` e `.svg`, permitindo gerenciamento amplo de diagramas.

**Q: Como lidar com grandes volumes de documentos de forma eficiente?**  
A: Use loops de processamento em lote, reutilize uma única instância `Watermarker` quando possível e ajuste `LoadOptions` para transmitir páginas ao invés de carregar arquivos inteiros.

**Q: Posso integrar a detecção de marcas d'água em um pipeline CI/CD?**  
A: Sim – a biblioteca é sem interface gráfica e pode ser chamada a partir do Maven, Gradle ou qualquer script de build para validar ativos de diagramas automaticamente.

---

**Última atualização:** 2026-10-27  
**Testado com:** GroupDocs.Watermark 23.6 for Java  
**Autor:** GroupDocs

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.contents.DiagramContent;
import com.groupdocs.watermark.search.TextSearchCriteria;
import com.groupdocs.watermark.search.ImageDctHashSearchCriteria;
import com.groupdocs.watermark.search.PossibleWatermarkCollection;

public class RemoveWatermarks {
    public static void main(String[] args) throws Exception {
        String inputFilePath = "YOUR_DOCUMENT_DIRECTORY/diagram.vsdx";
        String outputFilePath = "YOUR_OUTPUT_DIRECTORY/updated_diagram.vsdx";

        Watermarker watermarker = new Watermarker(inputFilePath);
        DiagramContent content = watermarker.getContent(DiagramContent.class);

        TextSearchCriteria textSearchCriteria = new TextSearchCriteria("Company Name");
        ImageDctHashSearchCriteria imageSearchCriteria = new ImageDctHashSearchCriteria("YOUR_DOCUMENT_DIRECTORY/logo.png");

        PossibleWatermarkCollection possibleWatermarks = content.getPages().get_Item(0).search(textSearchCriteria.or(imageSearchCriteria));
        possibleWatermarks.clear();

        watermarker.save(outputFilePath);
        watermarker.close();
    }
}
```

## Tutoriais Relacionados

- [Como adicionar marcas d'água de texto a diagramas usando GroupDocs.Watermark em Java](/watermark/java/diagram-document-watermarking/add-text-watermarks-diagrams-groupdocs-watermark-java/)
- [Guia para adicionar marcas d'água a diagramas usando GroupDocs.Watermark para Java](/watermark/java/diagram-document-watermarking/add-watermarks-groupdocs-diagrams-java/)
- [Como recuperar informações de documento usando GroupDocs.Watermark para Java: um guia passo a passo](/watermark/java/document-information/retrieve-document-info-groupdocs-watermark-java/)