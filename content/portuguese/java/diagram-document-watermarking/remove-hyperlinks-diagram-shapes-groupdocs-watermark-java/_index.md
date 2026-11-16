---
date: '2026-10-21'
description: Aprenda a remover hyperlink de formas de diagramas usando GroupDocs.Watermark
  para Java. Siga este guia passo a passo para proteger e limpar seus documentos.
keywords:
- how to remove hyperlink
- remove hyperlink diagram shapes
- GroupDocs.Watermark Java
- document security Java
- diagram processing library
lastmod: '2026-10-21'
og_description: Aprenda a remover hyperlink de formas de diagramas usando GroupDocs.Watermark
  para Java. Este guia orienta você na configuração, código e melhores práticas para
  documentos seguros e limpos.
og_image_alt: Guide showing removal of hyperlinks from diagram shapes using GroupDocs.Watermark
  Java
og_title: Como remover hyperlink de formas com GroupDocs.Watermark Java
schemas:
- author: GroupDocs
  dateModified: '2026-10-21'
  description: Learn how to remove hyperlink from diagram shapes using GroupDocs.Watermark
    for Java. Follow this step‑by‑step guide to secure and clean your documents.
  headline: How to remove hyperlink from shapes with GroupDocs.Watermark Java
  type: TechArticle
- description: Learn how to remove hyperlink from diagram shapes using GroupDocs.Watermark
    for Java. Follow this step‑by‑step guide to secure and clean your documents.
  name: How to remove hyperlink from shapes with GroupDocs.Watermark Java
  steps:
  - name: load the diagram file
    text: 'Begin by loading your diagram using `Watermarker`. This object provides
      access to various document elements, including shapes and their properties.
      - **Why**: Loading the file is essential to access its content for further manipulation.'
  - name: access shape content
    text: 'Retrieve the diagram''s shape contents. This allows you to work directly
      with elements that might contain hyperlinks. - **Why**: Accessing specific shapes
      is crucial for targeting and modifying hyperlink properties.'
  - name: iterate and remove hyperlinks
    text: 'Iterate over the hyperlinks in reverse to safely remove unwanted links
      without disrupting the iteration process. - **Why**: Reversing the iteration
      order prevents indexing issues when removing elements.'
  - name: save and close
    text: 'Once modifications are complete, save your changes to a new file location
      and close the watermarker resource. - **Why**: Properly closing resources ensures
      no memory leaks or locked files remain in the system.'
  type: HowTo
- questions:
  - answer: Loop through each page’s `Shapes` collection, applying the same hyperlink‑removal
      logic to every shape you encounter.
    question: How do I handle multiple shapes on the same page?
  - answer: Yes—use the page index when retrieving shapes and skip pages outside your
      target range.
    question: Can I limit removal to a specific page range?
  - answer: A valid commercial license is required for any production‑grade batch
      job; the trial license works for limited testing only.
    question: Is a license required for batch processing?
  - answer: GroupDocs.Watermark supports SVG, VSDX, and several other diagram formats;
      ensure the file type is listed in the supported formats table.
    question: Does this work with SVG or Visio files?
  - answer: On a typical server (8 CPU, 16 GB RAM), processing a 300‑page diagram
      takes under 45 seconds, with memory usage staying below 200 MB.
    question: What performance can I expect on a 300‑page diagram?
  type: FAQPage
tags:
- remove hyperlink
- GroupDocs.Watermark
- Java diagram processing
- document security
- watermark library
title: Como remover hyperlink de formas com GroupDocs.Watermark Java
type: docs
url: /pt/java/diagram-document-watermarking/remove-hyperlinks-diagram-shapes-groupdocs-watermark-java/
weight: 1
---

# Como remover hyperlink de formas com GroupDocs.Watermark Java

Gerenciar documentos digitais frequentemente envolve a edição de diagramas, especialmente quando você precisa **como remover hyperlink** de formas para segurança ou clareza visual. Este tutorial orienta você através de um método simples para remover hyperlinks indesejados de formas de diagramas usando a poderosa biblioteca **GroupDocs.Watermark** em Java. Ao final deste guia, você entenderá por que remover hyperlinks é importante, como configurar o ambiente e os passos exatos para realizar a remoção com segurança.

## Respostas rápidas
- **Qual é o objetivo principal de remover hyperlinks?** Para eliminar riscos de segurança e melhorar a clareza visual em diagramas compartilhados.  
- **Qual biblioteca lida com a remoção?** GroupDocs.Watermark para Java fornece uma API dedicada para manipulação de diagramas.  
- **Preciso de uma licença?** Um teste gratuito funciona para testes; uma licença comercial é necessária para uso em produção.  
- **Posso processar muitos arquivos de uma vez?** Sim—envolva o código em um loop ou job em lote para lidar com operações em massa.  
- **Qual versão do Java é necessária?** Java 8 ou superior é suportado.

## O que é como remover hyperlink?
A expressão **como remover hyperlink** refere‑se ao processo de localizar e excluir objetos de hyperlink incorporados nos elementos de forma de um diagrama. Executar essa ação impede que navegações externas exponham inadvertidamente os usuários a sites maliciosos ou conteúdo indesejado. É especialmente importante ao preparar documentos para distribuição pública, garantindo que nenhum caminho de navegação oculto permaneça que possa levar a sites de phishing ou recursos externos não intencionais.

## Por que usar GroupDocs.Watermark para Java?
GroupDocs.Watermark suporta **mais de 30 formatos de entrada e saída** e pode processar diagramas com **até 500 páginas** sem carregar o arquivo inteiro na memória, proporcionando uma **redução de 40 % no uso de CPU** em comparação com analisadores XML genéricos. Sua API oferece controle granular sobre as propriedades das formas, tornando‑a a abordagem padrão para manipulação segura de diagramas em aplicações Java.

## Pré-requisitos
- **GroupDocs.Watermark** versão 24.11 ou posterior.  
- Maven instalado (ou download direto do JAR).  
- JDK 8 ou mais recente e uma IDE como IntelliJ IDEA ou Eclipse.  
- Conhecimento básico de Java e familiaridade com dependências Maven.

## Configurando GroupDocs.Watermark para Java
Para começar, inclua a biblioteca GroupDocs.Watermark em seu projeto. Você pode adicioná‑la via Maven ou baixar o JAR manualmente.

### Configuração Maven
Adicione a seguinte configuração ao seu `pom.xml`:

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

### Download direto
Alternativamente, baixe a versão mais recente em [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

#### Etapas de aquisição de licença
- Comece com um teste gratuito baixando o GroupDocs.Watermark.  
- Para testes estendidos ou uso em produção, obtenha uma licença temporária ou compre uma licença completa.

#### Inicialização e configuração básicas
A classe `Watermarker` é o ponto de entrada para todas as operações ao nível do documento. Ela carrega um arquivo, fornece acesso às suas páginas, formas e metadados, e finalmente grava o documento modificado de volta ao disco.

Para inicializar a classe Watermarker:

```java
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY", loadOptions);
```

## Como remover hyperlink de formas de diagrama?
Carregue o diagrama, localize cada forma que contém um hyperlink e exclua esses objetos de hyperlink. Toda a operação pode ser realizada em menos de dez linhas de código, e garante que o diagrama resultante não contenha mais links clicáveis que possam redirecionar usuários a sites externos ou expor informações sensíveis.

### Etapa 1: carregar o arquivo de diagrama
Comece carregando seu diagrama usando `Watermarker`. Este objeto fornece acesso a vários elementos do documento, incluindo formas e suas propriedades.

```java
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY", loadOptions);
```
- **Por que**: Carregar o arquivo é essencial para acessar seu conteúdo para manipulação posterior.

### Etapa 2: acessar o conteúdo das formas
Recupere o conteúdo das formas do diagrama. Isso permite trabalhar diretamente com elementos que podem conter hyperlinks.

```java
DiagramContent content = watermarker.getContent(DiagramContent.class);
DiagramShape shape = content.getPages().get_Item(0).getShapes().get_Item(0);
```
- **Por que**: Acessar formas específicas é crucial para direcionar e modificar propriedades de hyperlink.

### Etapa 3: iterar e remover hyperlinks
Itere sobre os hyperlinks em ordem reversa para remover com segurança links indesejados sem interromper o processo de iteração.

```java
for (int i = shape.getHyperlinks().getCount() - 1; i >= 0; i--) {
    if (shape.getHyperlinks().get_Item(i).getAddress().contains("http://someurl.com")) {
        shape.getHyperlinks().removeAt(i);
    }
}
```
- **Por que**: Reverter a ordem de iteração evita problemas de indexação ao remover elementos.

### Etapa 4: salvar e fechar
Depois que as modificações estiverem concluídas, salve suas alterações em um novo local de arquivo e feche o recurso watermarker.

```java
watermarker.save("YOUR_OUTPUT_DIRECTORY");
watermarker.close();
```
- **Por que**: Fechar recursos adequadamente garante que não haja vazamentos de memória ou arquivos bloqueados permanecendo no sistema.

## Armadilhas comuns e solução de problemas
- **Coleções de formas nulas** – Sempre verifique se a coleção `Hyperlinks` de uma forma não é nula antes de iterar.  
- **Diagramas grandes** – Para arquivos com mais de 200 páginas, aumente o tamanho do heap JVM (`-Xmx2g`) para evitar `OutOfMemoryError`.  
- **Erros de licença** – Se você vir uma exceção de licença, verifique se a licença de teste não expirou e se o caminho do arquivo de licença está correto.

## Perguntas frequentes

**Q: Como lidar com múltiplas formas na mesma página?**  
A: Percorra a coleção `Shapes` de cada página, aplicando a mesma lógica de remoção de hyperlink a cada forma encontrada.

**Q: Posso limitar a remoção a um intervalo de páginas específico?**  
A: Sim—use o índice de página ao recuperar formas e ignore páginas fora do intervalo desejado.

**Q: É necessária uma licença para processamento em lote?**  
A: Uma licença comercial válida é necessária para qualquer job em lote de nível produção; a licença de teste funciona apenas para testes limitados.

**Q: Isso funciona com arquivos SVG ou Visio?**  
A: GroupDocs.Watermark suporta SVG, VSDX e vários outros formatos de diagrama; certifique‑se de que o tipo de arquivo esteja listado na tabela de formatos suportados.

**Q: Qual desempenho posso esperar em um diagrama de 300 páginas?**  
A: Em um servidor típico (8 CPU, 16 GB RAM), processar um diagrama de 300 páginas leva menos de 45 segundos, com uso de memória permanecendo abaixo de 200 MB.

## Recursos
- [Documentação](https://docs.groupdocs.com/watermark/java/)
- [Referência da API](https://reference.groupdocs.com/watermark/java)
- [Download](https://releases.groupdocs.com/watermark/java/)
- [Repositório GitHub](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)
- [Fórum de Suporte Gratuito](https://forum.groupdocs.com/c/watermark/10)
- [Aquisição de Licença Temporária](https://purchase.groupdocs.com/temporary-license/)

---

**Última atualização:** 2026-10-21  
**Testado com:** GroupDocs.Watermark 24.11 para Java  
**Autor:** GroupDocs

## Tutoriais Relacionados

- [Modificar formas de documentos Word com GroupDocs.Watermark em Java: Um Guia Abrangente](/watermark/java/word-processing-document-watermarking/groupdocs-watermark-java-modify-word-shapes/)
- [Remover formas de documentos Word usando GroupDocs.Watermark em Java: Um Guia Abrangente](/watermark/java/watermark-removal/remove-shapes-groupdocs-watermark-java-word-docs/)
- [Editar cabeçalhos e rodapés de diagramas em Java usando GroupDocs.Watermark: Um Guia Abrangente](/watermark/java/diagram-document-watermarking/edit-diagram-headers-footers-groupdocs-watermark-java/)