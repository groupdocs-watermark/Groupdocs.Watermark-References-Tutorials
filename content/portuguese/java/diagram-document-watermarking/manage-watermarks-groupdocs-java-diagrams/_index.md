---
date: '2026-02-18'
description: Aprenda como adicionar marca d'água e como remover marca d'água em arquivos
  de diagrama, como .vsdx, com o GroupDocs.Watermark para Java. Proteja a integridade
  do documento com o GroupDocs.Watermark para Java.
keywords:
- GroupDocs.Watermark Java
- manage watermarks in diagrams
- Java diagram document watermarking
title: Como adicionar marca d'água a diagramas usando GroupDocs.Watermark para Java
type: docs
url: /pt/java/diagram-document-watermarking/manage-watermarks-groupdocs-java-diagrams/
weight: 1
---

 for any missed shortcodes: none.

Make sure to keep code block placeholders unchanged.

Proceed.# Como Adicionar Marca d'água a Diagramas usando GroupDocs.Watermark para Java

Gerenciar marcas d'água em arquivos de diagramas é uma parte essencial da proteção da propriedade intelectual e de manter os documentos limpos para distribuição pública. Neste guia você aprenderá **como adicionar marca d'água** a um diagrama Visio, bem como **como remover marca d'água** quando não for mais necessária, tudo com a biblioteca **groupdocs watermark java**. Seja construindo um pipeline de documentos de nível empresarial ou um script utilitário rápido, estas etapas lhe darão controle total sobre a marcação de diagramas.

## Quick Answers
- **Qual biblioteca lida com marcas d'água em diagramas em Java?** GroupDocs.Watermark for Java.  
- **Posso adicionar e remover marcas d'água na mesma execução?** Sim – carregue o diagrama uma vez e aplique as operações de adicionar e remover.  
- **Quais formatos de arquivo são suportados?** Formatos Visio como `.vsdx`, `.vdx`, além de outros tipos de diagramas.  
- **Preciso de uma licença?** Uma licença de avaliação funciona para desenvolvimento; uma licença completa é necessária para produção.  
- **Qual versão do Java é necessária?** JDK 8 ou superior.

## O que significa “como adicionar marca d'água” no contexto de diagramas?
Adicionar uma marca d'água significa incorporar um marcador visível ou invisível — texto, logotipo ou imagem — em um arquivo de diagrama. Esse marcador viaja com o arquivo, facilitando a comprovação de propriedade ou a sinalização de versões de rascunho.

## Why use GroupDocs.Watermark for Java?
* **API rica** – Pesquise, adicione e exclua marcas d'água de texto e imagem com poucas linhas de código.  
* **Suporte a múltiplos formatos** – Funciona com Visio (`.vsdx`, `.vdx`) e muitos outros tipos de diagramas.  
* **Foco em desempenho** – Carrega apenas as partes de um diagrama necessárias para operações de marca d'água, mantendo o uso de memória baixo.

## Prerequisites
1. **Java Development Kit (JDK) 8+** – Certifique‑se de que `java -version` exibe 1.8 ou superior.  
2. **IDE** – IntelliJ IDEA, Eclipse ou qualquer editor que preferir.  
3. **GroupDocs.Watermark for Java** – Adicione ao seu projeto via Maven ou download direto do JAR.  

### Required Libraries and Dependencies
Adicione o repositório e a dependência ao seu `pom.xml`:

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

*Se preferir não usar Maven, você pode baixar o JAR mais recente em [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).*

### License Acquisition
- **Teste gratuito:** Teste todos os recursos sem chave de licença.  
- **Licença temporária:** Solicite uma chave de tempo limitado para avaliação.  
- **Licença completa:** Compre uma assinatura para uso em produção sem restrições.

## Setting Up GroupDocs.Watermark for Java
1. **Adicione a biblioteca** ao seu projeto (Maven ou JAR manual).  
2. **Crie uma instância `Watermarker`** – este objeto é o ponto de entrada para carregar diagramas, pesquisar, adicionar e remover marcas d'água.

## Implementation Guide

### Loading a Diagram Document
Carregar é o primeiro passo antes de poder **adicionar marca d'água** ou **remover marca d'água**. O código abaixo mostra como abrir um arquivo `.vsdx` com opções de carregamento personalizadas.

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

### Searching for Text Watermarks
Antes de adicionar uma nova marca d'água, você pode querer verificar se já existe uma marca d'água de texto. Este trecho procura a frase “Company Name”.

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

### Searching for Image Watermarks
Se precisar localizar um logotipo ou qualquer imagem usada como marca d'água, use o `ImageDctHashSearchCriteria`. Isso é útil quando você deseja **remover marca d'água** que corresponde a um logotipo conhecido.

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

### Removing Watermarks
Depois de identificar as marcas d'água — texto, imagem ou ambas — você pode removê‑las do diagrama. O exemplo abaixo demonstra uma operação de remoção combinada.

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

## Practical Applications
1. **Integração de Software Empresarial** – Incorpore a gestão de marcas d'água ao seu ERP ou plataforma de geração de documentos para reforçar a identidade visual.  
2. **Sistemas de Gerenciamento de Conteúdo (CMS)** – Analise automaticamente diagramas enviados em busca de logotipos não autorizados e remova‑os.  
3. **Manipulação de Documentos Legais** – Adicione uma marca d'água de texto “Confidencial” durante as fases de rascunho e depois **remova a marca d'água** antes da entrega final.

## Common Issues and Solutions
| Symptom | Likely Cause | Fix |
|---------|--------------|-----|
| Nenhuma marca d'água encontrada | O texto/imagem de pesquisa não corresponde exatamente | Use `or()` para combinar critérios ou ajuste as configurações de sensibilidade a maiúsculas/minúsculas. |
| `OutOfMemoryError` em arquivos grandes | Diagrama carregado completamente na memória | Use `DiagramLoadOptions.setLoadPages()` para carregar apenas as páginas necessárias. |
| Arquivo salvo está corrompido | `watermarker.save()` chamado antes de limpar todas as marcas d'água | Garanta que `possibleWatermarks.clear()` seja concluído e que `watermarker.close()` seja invocado após a gravação. |

## Frequently Asked Questions

**Q: Posso pesquisar tanto texto quanto imagens simultaneamente?**  
A: Sim. Combine `TextSearchCriteria` e `ImageDctHashSearchCriteria` com o método `or()`, como mostrado no exemplo de remoção.

**Q: É possível remover marcas d'água sem danificar o diagrama?**  
A: Absolutamente. A biblioteca isola os objetos de marca d'água, de modo que chamar `clear()` remove apenas as camadas de marca d'água enquanto preserva o conteúdo original do diagrama.

**Q: O GroupDocs.Watermark suporta vários formatos de diagrama?**  
A: Sim. Formatos como `.vsdx`, `.vdx` e outros arquivos compatíveis com Visio são totalmente suportados.

**Q: Como lidar com grandes volumes de documentos de forma eficiente?**  
A: Implemente loops de processamento em lote, reutilize uma única instância `Watermarker` sempre que possível e limite o carregamento de páginas com `DiagramLoadOptions`.

**Q: Existe uma maneira de automatizar a detecção de marcas d'água em um pipeline CI/CD?**  
A: Você pode incorporar os trechos de Java fornecidos em seus scripts de build (por exemplo, Maven ou Gradle) para validar que não há marcas d'água não autorizadas antes de liberar os artefatos.

---

**Last Updated:** 2026-02-18  
**Tested With:** GroupDocs.Watermark 24.11 for Java  
**Author:** GroupDocs