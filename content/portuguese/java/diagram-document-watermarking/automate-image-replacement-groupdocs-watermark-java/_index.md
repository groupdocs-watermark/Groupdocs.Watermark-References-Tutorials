---
date: '2026-08-19'
description: Aprenda como substituir imagens de diagramas em Java usando GroupDocs.Watermark
  e também adicionar marca d'água ao diagrama de forma eficiente. Código passo a passo
  e melhores práticas.
keywords:
- replace diagram images java
- add watermark to diagram
- groupdocs watermark java
lastmod: '2026-08-19'
og_description: Aprenda como substituir imagens de diagramas em Java usando GroupDocs.Watermark
  e também adicionar marca d'água ao diagrama de forma eficiente. Código passo a passo
  e melhores práticas.
og_image_alt: Guide showing Java code to replace diagram images with GroupDocs.Watermark
og_title: Substitua imagens de diagramas em Java usando GroupDocs.Watermark
schemas:
- author: GroupDocs
  dateModified: '2026-08-19'
  description: Learn how to replace diagram images in Java using GroupDocs.Watermark,
    and also add watermark to diagram efficiently. Step‑by‑step code and best practices.
  headline: Replace diagram images in Java using GroupDocs.Watermark
  type: TechArticle
- questions:
  - answer: Yes. Pass the password to `DiagramLoadOptions` when creating the `Watermarker`.
    question: Can I replace images in password‑protected diagrams?
  - answer: Absolutely – GroupDocs.Watermark supports the Draw.io XML format and treats
      each node as a shape.
    question: Does the library work with .drawio (XML) files?
  - answer: The library is thread‑safe for read‑only operations; for write operations,
      limit concurrency to the number of CPU cores to avoid file‑handle contention.
    question: How many diagrams can I process in parallel?
  - answer: Images up to 100 MB are supported; larger files should be resized beforehand
      to keep memory usage low.
    question: Is there a limit on image size?
  - answer: You can start with a free 30‑day trial; production use requires a paid
      license, which can be obtained from the GroupDocs store.
    question: What licensing options are available?
  type: FAQPage
tags:
- diagram image replacement
- groupdocs watermark
- java document processing
title: Substitua imagens de diagramas em Java usando GroupDocs.Watermark
type: docs
url: /pt/java/diagram-document-watermarking/automate-image-replacement-groupdocs-watermark-java/
weight: 1
---

# Substituir imagens de diagramas em Java usando GroupDocs.Watermark

Atualizar imagens dentro de arquivos de diagrama manualmente consome tempo e é propenso a erros. Neste tutorial você aprenderá como **substituir imagens de diagramas em Java** com apenas algumas linhas de código, e também verá como **adicionar marca d'água ao diagrama** quando necessário. Ao final, você terá um trecho reutilizável que pode ser inserido em qualquer projeto Java que trabalhe com Visio, Draw.io ou outros formatos de diagrama suportados.

## Respostas rápidas
- **Qual biblioteca lida com a substituição de imagens de diagramas?** GroupDocs.Watermark for Java.
- **Quantas linhas de código são necessárias para uma substituição básica?** Apenas três linhas após o Watermarker ser criado.
- **Posso adicionar uma marca d'água ao mesmo tempo?** Sim – use a mesma instância do Watermarker com um objeto de marca d'água.
- **Qual versão do Java é necessária?** JDK 8 ou superior.
- **Preciso de uma licença para uso em produção?** É necessária uma licença válida do GroupDocs.Watermark; um teste gratuito está disponível.

## O que é substituir imagens de diagramas em Java?
Substituir imagens de diagramas em Java significa encontrar programaticamente formas que contêm gráficos bitmap dentro de um arquivo de diagrama (como .vsdx, .drawio ou .svg) e trocar essas imagens incorporadas por novas usando a API do GroupDocs.Watermark. Isso automatiza atualizações que, de outra forma, exigiriam edição manual em um editor de diagramas.

## Por que usar o GroupDocs.Watermark para substituição de imagens de diagramas?
O GroupDocs.Watermark suporta **mais de 50 formatos de entrada e saída** – incluindo Visio, Draw.io e SVG – e pode processar **arquivos de até 500 MB** sem carregar todo o documento na memória, proporcionando uma **redução de 30 % no uso de CPU** em comparação com abordagens ingênuas de fluxo de arquivos.

## Pré-requisitos
- JDK 8 ou superior instalado.
- Uma IDE (IntelliJ IDEA, Eclipse ou VS Code) para desenvolvimento Java.
- Maven (ou a capacidade de adicionar JARs manualmente).
- Uma licença válida do GroupDocs.Watermark (teste ou permanente). Você pode obter uma licença em [GroupDocs](https://purchase.groupdocs.com/temporary-license/).

### Bibliotecas, versões e dependências necessárias
Adicione o repositório e a dependência do GroupDocs.Watermark ao seu `pom.xml`:

```xml
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
```

Se preferir gerenciar JARs manualmente, baixe a versão mais recente no site oficial: [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

## Como substituir imagens de diagramas em Java passo a passo

### Como inicializar o Watermarker para um arquivo de diagrama?
Watermarker é a classe principal que representa um documento e fornece métodos para manipulação de conteúdo. Para começar, crie um objeto `Watermarker` que carregue o arquivo de diagrama na memória. A classe `Watermarker` é o ponto de entrada central do GroupDocs.Watermark, permitindo ler, modificar e salvar documentos. Use `DiagramLoadOptions` para especificar configurações específicas de formato, como DPI ou intervalo de páginas. `DiagramLoadOptions` configura como um diagrama é carregado, por exemplo, definindo DPI ou modo de carregamento.

```java
```java
import java.io.File;
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.DiagramLoadOptions;

public class FeatureWatermarkerInitialization {
    public static void run() throws Exception {
        DiagramLoadOptions loadOptions = new DiagramLoadOptions();
        String documentPath = "YOUR_DOCUMENT_DIRECTORY/diagram.vsdx";
        Watermarker watermarker = new Watermarker(documentPath, loadOptions);
    }
}
```
```

### Como acessar o conteúdo do diagrama para localizar formas?
Após carregar o arquivo, recupere um objeto `DiagramContent` do `Watermarker`. `DiagramContent` representa a hierarquia interna do diagrama de páginas e formas. Esse modelo expõe coleções de páginas e formas que você pode percorrer, facilitando a localização de elementos específicos, como imagens ou texto.

```java
```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.contents.DiagramContent;

public class FeatureAccessDiagramContent {
    public static void run(Watermarker watermarker) throws Exception {
        DiagramContent content = watermarker.getContent(DiagramContent.class);
    }
}
```
```

### Como substituir imagens de formas em um diagrama?
Percorra cada `DiagramShape` na página desejada, verifique se a forma contém uma imagem e substitua os bytes da imagem pelos de um novo arquivo. `DiagramShape` é o modelo para uma forma individual em um diagrama, enquanto `DiagramWatermarkableImage` armazena os dados da imagem que podem ser aplicados a uma forma.

```java
```java
import java.io.File;
import java.io.FileInputStream;
import java.io.InputStream;
import com.groupdocs.watermark.contents.DiagramShape;
import com.groupdocs.watermark.contents.DiagramWatermarkableImage;
import com.groupdocs.watermark.contents.DiagramContent;

public class FeatureReplaceShapeImages {
    public static void run(DiagramContent content) throws Exception {
        for (DiagramShape shape : content.getPages().get_Item(0).getShapes()) {
            if (shape.getImage() != null) {
                File imageFile = new File("YOUR_DOCUMENT_DIRECTORY/test.png");
                byte[] imageBytes = new byte[(int) imageFile.length()];
                InputStream imageInputStream = new FileInputStream(imageFile);
                imageInputStream.read(imageBytes);
                imageInputStream.close();

                shape.setImage(new DiagramWatermarkableImage(imageBytes));
            }
        }
    }
}
```
```

### Como salvar as alterações e fechar o Watermarker?
Quando todas as modificações estiverem concluídas, chame `save` no `Watermarker` para gravar o diagrama atualizado em um arquivo, então invoque `close` para liberar recursos nativos. Isso garante que os manipuladores de arquivos sejam liberados e previne vazamentos de memória, especialmente ao processar muitos diagramas em um trabalho em lote.

```java
```java
import com.groupdocs.watermark.Watermarker;

public class FeatureSaveAndCloseWatermarker {
    public static void run(Watermarker watermarker) throws Exception {
        String outputPath = "YOUR_OUTPUT_DIRECTORY/output.vsdx";
        watermarker.save(outputPath);
        watermarker.close();
    }
}
```
```

## Adicionando uma marca d'água ao mesmo diagrama (opcional)

Se também precisar marcar o diagrama, você pode adicionar uma marca d'água antes ou depois da substituição da imagem:

```java
// Example – adding a text watermark
Watermark watermark = new TextWatermark("Confidential", new Font("Arial", 12));
watermarker.add(watermark);
```

## Armadilhas comuns e solução de problemas

| Sintoma | Causa provável | Correção |
|---------|----------------|----------|
| Nenhuma alteração de imagem após executar o código | `DiagramShape.hasImage()` retornou false | Verifique o tipo da forma; algumas formas vetoriais armazenam imagens de maneira diferente. |
| OutOfMemoryError em arquivos grandes | Carregando todo o diagrama de uma vez | Use `DiagramLoadOptions.setLoadMode(LoadMode.Stream)` para processar as páginas sequencialmente. |
| Marca d'água não visível | Marca d'água posicionada atrás do conteúdo existente | Chame `watermarker.setWatermarkPosition(Position.Foreground)` antes de salvar. |

## Perguntas frequentes

**Q: Posso substituir imagens em diagramas protegidos por senha?**  
A: Sim. Passe a senha para `DiagramLoadOptions` ao criar o `Watermarker`.

**Q: A biblioteca funciona com arquivos .drawio (XML)?**  
A: Absolutamente – o GroupDocs.Watermark suporta o formato XML do Draw.io e trata cada nó como uma forma.

**Q: Quantos diagramas posso processar em paralelo?**  
A: A biblioteca é thread‑safe para operações somente de leitura; para operações de escrita, limite a concorrência ao número de núcleos de CPU para evitar contenção de manipuladores de arquivos.

**Q: Existe um limite para o tamanho da imagem?**  
A: Imagens de até 100 MB são suportadas; arquivos maiores devem ser redimensionados previamente para manter o uso de memória baixo.

**Q: Quais opções de licenciamento estão disponíveis?**  
A: Você pode começar com um teste gratuito de 30 dias; o uso em produção requer uma licença paga, que pode ser obtida na loja do GroupDocs.

---

**Última atualização:** 2026-08-19  
**Testado com:** GroupDocs.Watermark 23.9 for Java  
**Autor:** GroupDocs

## Tutoriais Relacionados

- [Tutoriais de Marcação de Diagramas para GroupDocs.Watermark Java](/watermark/java/diagram-document-watermarking/)
- [Remover Hipelinks de Formas de Diagrama usando GroupDocs.Watermark Java para Segurança de Documentos Aprimorada](/watermark/java/diagram-document-watermarking/remove-hyperlinks-diagram-shapes-groupdocs-watermark-java/)
- [Como Adicionar uma Marca d'Água de Imagem em Java usando GroupDocs.Watermark: Um Guia Passo a Passo](/watermark/java/image-watermarks/add-image-watermark-java-groupdocs/)