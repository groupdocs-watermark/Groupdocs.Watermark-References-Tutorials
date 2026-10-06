---
date: 2026-09-16
description: Aprenda como adicionar watermark a PDF, carregar documentos de várias
  fontes e salvar arquivos watermarked usando GroupDocs.Watermark for Java.
keywords:
- add watermark to pdf
- load password protected document
- load document from disk
- load document from stream
- java load password protected
lastmod: 2026-09-16
og_description: Adicione watermark a PDF rapidamente usando GroupDocs.Watermark for
  Java. Aprenda a carregar documentos, lidar com senhas e salvar arquivos watermarked.
og_image_alt: Guide showing how to add watermark to pdf using GroupDocs.Watermark
  Java SDK
og_title: Adicionar watermark a PDF com GroupDocs.Watermark for Java
schemas:
- author: GroupDocs
  dateModified: '2026-09-16'
  description: Learn how to add watermark to pdf, load documents from various sources,
    and save watermarked files using GroupDocs.Watermark for Java.
  headline: How to add watermark to pdf with GroupDocs.Watermark for Java
  type: TechArticle
- questions:
  - answer: Yes. Call `watermarker.add()` repeatedly with different `TextWatermark`
      or `ImageWatermark` objects; each will be layered in the order added.
    question: Can I add multiple watermarks to the same PDF?
  - answer: Absolutely. All original PDF objects, including annotations, form fields,
      and metadata, remain untouched unless you explicitly modify them.
    question: Does the library preserve existing annotations?
  - answer: Yes. Pass a `PageRange` (e.g., `new PageRange(2, 4)`) to the `add` method
      to limit the watermark to specific pages.
    question: Is it possible to watermark only selected pages?
  - answer: The SDK can handle files up to **2 GB** without loading the entire document
      into memory, thanks to its streaming architecture.
    question: What is the maximum file size supported?
  - answer: Use `watermarker.remove(watermarkId)` where `watermarkId` is the identifier
      returned when you initially added the watermark.
    question: How do I remove a watermark after it has been added?
  type: FAQPage
tags:
- watermark pdf
- GroupDocs.Watermark
- Java document processing
- add watermark to pdf
- load document
title: Como adicionar watermark a PDF com GroupDocs.Watermark for Java
type: docs
url: /pt/java/document-loading-saving/
weight: 2
---

# Adicionar marca d'água a PDF com GroupDocs.Watermark para Java

Neste guia você aprenderá como **adicionar marca d'água a PDF** usando o SDK Java do GroupDocs.Watermark. Vamos percorrer o carregamento de documentos a partir de disco, streams ou fontes protegidas por senha, aplicar marcas d'água de texto ou imagem e, finalmente, salvar o PDF atualizado. Seja construindo um processador em lote ou um serviço de arquivo único, estas etapas fornecem uma solução confiável e pronta para produção.

## Respostas rápidas
- **Posso adicionar uma marca d'água a um PDF protegido por senha?** Sim – passe a senha ao carregar o documento, então aplique a marca d'água normalmente.  
- **Quais formatos podem receber marca d'água?** Mais de 30 formatos, incluindo PDF, DOCX, PPTX e imagens.  
- **Preciso de uma licença para desenvolvimento?** Uma licença temporária funciona para testes; uma licença completa é necessária para produção.  
- **Qual versão do Java é necessária?** Java 8 ou superior é suportado.  
- **O streaming é suportado?** Absolutamente – você pode carregar de `InputStream` e salvar para `OutputStream` sem tocar no sistema de arquivos.

## O que é adicionar marca d'água a PDF?
*Adicionar marca d'água a PDF* refere-se ao processo de sobrepor texto ou imagens semitransparentes em cada página de um documento PDF para transmitir propriedade, confidencialidade ou branding. O GroupDocs.Watermark para Java fornece uma API de chamada única que gerencia posicionamento, opacidade e seleção de intervalo de páginas automaticamente.

## Por que usar o GroupDocs.Watermark para Java?
O GroupDocs.Watermark suporta **mais de 35 formatos de arquivo** e pode processar **PDFs de 500 páginas em menos de 2 segundos** em uma CPU de servidor típica. A biblioteca funciona totalmente na memória, portanto você nunca precisa do Microsoft Office ou do Adobe Acrobat instalados. Sua API é thread‑safe, tornando‑a ideal para serviços web de alta taxa de transferência.

## Pré-requisitos
- Java 8 ou mais recente instalado.  
- Projeto Maven ou Gradle configurado com a dependência `groupdocs-watermark`.  
- Uma licença válida do GroupDocs.Watermark (licença temporária para avaliação).  
- Arquivos PDF que você deseja proteger, opcionalmente com senhas.

## Como adicionar marca d'água a PDF – passo a passo

Carregue o documento fonte, aplique uma marca d'água e, em seguida, salve o resultado. As seções a seguir respondem a cada sub‑tarefa diretamente.

### Como carregar um documento do disco?

`Watermarker` é a classe principal usada para carregar e manipular documentos para marca d'água. Forneça o caminho completo do arquivo ao construtor `Watermarker`; o SDK detecta automaticamente o formato do arquivo, valida o conteúdo e carrega o documento na memória pronto para qualquer operação de marca d'água. Esta abordagem funciona para PDFs, arquivos Word, imagens e muitos outros tipos suportados.  
```java
Watermarker watermarker = new Watermarker("C:/files/input.pdf");
```

Após esta linha, o PDF está totalmente carregado na memória, pronto para qualquer operação de marca d'água.

### Como carregar um documento a partir de stream?

`Watermarker` também pode aceitar um `InputStream` para carregar documentos diretamente da memória. Quando você recebe um arquivo via HTTP ou fila de mensagens, envolva o array de bytes em um `ByteArrayInputStream` e passe‑o ao construtor `Watermarker` que aceita um `InputStream`. O SDK lê o stream sem gravar no disco, preservando desempenho e segurança, e suporta arquivos grandes processando os dados em blocos. Este método é ideal para serviços web e arquiteturas de microsserviços.  
```java
InputStream pdfStream = new ByteArrayInputStream(pdfBytes);
Watermarker watermarker = new Watermarker(pdfStream);
```

O SDK lê o stream sem gravar no disco, preservando desempenho e segurança.

### Como carregar um documento protegido por senha?

`Watermarker` suporta o carregamento de PDFs protegidos por senha ao fornecer a senha como segundo argumento. Forneça a senha como segundo argumento ao construtor. O SDK descriptografa o PDF em tempo real, após o que você pode tratá‑lo como qualquer outro documento. Se a senha estiver correta, todas as páginas ficam acessíveis para marca d'água; caso contrário, a biblioteca lança uma exceção clara que você pode capturar e registrar para solução de problemas.  
```java
Watermarker watermarker = new Watermarker("C:/files/secure.pdf", "mySecretPwd");
```

Se a senha estiver incorreta, o SDK lança uma exceção informativa que você pode capturar e registrar.

### Como aplicar uma marca d'água de texto?

`TextWatermark` representa uma marca d'água textual que pode ser aplicada às páginas com estilo personalizável. Crie um objeto `TextWatermark` com o texto desejado, fonte, tamanho e cor. Em seguida, chame `add` na instância `Watermarker`, opcionalmente especificando intervalos de páginas. A marca d'água é renderizada com a opacidade e rotação especificadas, e pode ser posicionada usando locais predefinidos ou coordenadas personalizadas, garantindo aparência consistente em todas as páginas.  
```java
TextWatermark watermark = new TextWatermark("Confidential", new Font("Arial", 36));
watermark.setColor(Color.RED);
watermark.setTransparency(0.5);
watermarker.add(watermark);
```

Esta chamada coloca a marca d'água em todas as páginas por padrão; você pode restringi‑la com `new PageRange(1, 5)` se necessário.

### Como aplicar uma marca d'água de imagem?

`ImageWatermark` representa uma marca d'água baseada em imagem, como um logotipo ou selo. Instancie um `ImageWatermark` com o caminho ou stream do seu logotipo, então adicione‑o de forma semelhante à marca d'água de texto. O SDK dimensiona automaticamente a imagem para caber na página preservando sua proporção, e você pode ajustar opacidade, rotação e posicionamento para obter o efeito visual desejado sem distorcer o conteúdo original.  
```java
ImageWatermark imgWatermark = new ImageWatermark("C:/images/logo.png");
imgWatermark.setTransparency(0.3);
watermarker.add(imgWatermark);
```

O SDK dimensiona a imagem para caber na página preservando a proporção.

### Como salvar o documento com marca d'água?

`save` grava o documento modificado no local especificado no formato escolhido. Chame `save` com o caminho de saída e o formato desejado. O mesmo formato da fonte é usado quando você omite o parâmetro de formato. O método grava o PDF modificado no disco, preservando todo o conteúdo original, exceto as novas camadas de marca d'água, e suporta salvar em streams para processamento adicional.  
```java
watermarker.save("C:/files/output.pdf");
```

O método grava o PDF modificado no disco, preservando todo o conteúdo original, exceto as novas camadas de marca d'água.

## Tutoriais disponíveis

### [Como carregar documentos protegidos por senha em Java usando GroupDocs.Watermark](./groupdocs-watermark-java-password-protected-documents/)
Aprenda como carregar e gerenciar marcas d'água em documentos protegidos por senha usando o GroupDocs.Watermark para Java. Este guia fornece instruções passo a passo, exemplos práticos e dicas de solução de problemas.

### [Como carregar e aplicar marca d'água em documentos Word protegidos por senha usando GroupDocs.Watermark em Java](./groupdocs-watermark-java-password-protected-word-docs/)
Aprenda como usar o GroupDocs.Watermark com Java para carregar, gerenciar e aplicar marca d'água em documentos Word protegidos por senha de forma eficiente.

## Recursos adicionais

- [Documentação do GroupDocs.Watermark para Java](https://docs.groupdocs.com/watermark/java/)
- [Referência da API do GroupDocs.Watermark para Java](https://reference.groupdocs.com/watermark/java/)
- [Download do GroupDocs.Watermark para Java](https://releases.groupdocs.com/watermark/java/)
- [Fórum do GroupDocs.Watermark](https://forum.groupdocs.com/c/watermark)
- [Suporte gratuito](https://forum.groupdocs.com/)
- [Licença temporária](https://purchase.groupdocs.com/temporary-license/)

## Problemas comuns e soluções
- **Erro de senha inválida** – verifique a string da senha; ela deve estar codificada em UTF‑8.  
- **Falta de memória em PDFs grandes** – habilite o modo de streaming usando os construtores `Watermarker` que aceitam `InputStream` e `OutputStream`.  
- **Marca d'água não visível** – certifique-se de que a opacidade da marca d'água esteja acima de 0.1 e que a cor contraste com o fundo da página.

## Perguntas frequentes

**Q: Posso adicionar várias marcas d'água ao mesmo PDF?**  
A: Sim. Chame `watermarker.add()` repetidamente com diferentes objetos `TextWatermark` ou `ImageWatermark`; cada um será sobreposto na ordem em que for adicionado.

**Q: A biblioteca preserva as anotações existentes?**  
A: Absolutamente. Todos os objetos PDF originais, incluindo anotações, campos de formulário e metadados, permanecem intactos, a menos que você os modifique explicitamente.

**Q: É possível aplicar marca d'água apenas em páginas selecionadas?**  
A: Sim. Passe um `PageRange` (por exemplo, `new PageRange(2, 4)`) ao método `add` para limitar a marca d'água a páginas específicas.

**Q: Qual é o tamanho máximo de arquivo suportado?**  
A: O SDK pode lidar com arquivos de até **2 GB** sem carregar o documento inteiro na memória, graças à sua arquitetura de streaming.

**Q: Como remover uma marca d'água depois de adicionada?**  
A: Use `watermarker.remove(watermarkId)` onde `watermarkId` é o identificador retornado quando você adicionou a marca d'água inicialmente.

---

**Última atualização:** 2026-09-16  
**Testado com:** GroupDocs.Watermark 23.9 for Java  
**Autor:** GroupDocs

## Tutoriais relacionados

- [Como adicionar marca d'água de texto a PDF usando GroupDocs.Watermark para Java (Guia 2023)](/watermark/java/pdf-document-watermarking/add-text-watermark-pdf-java/)
- [Como adicionar marcas d'água de texto e imagem a páginas específicas de PDF usando GroupDocs.Watermark para Java](/watermark/java/pdf-document-watermarking/add-watermarks-pdf-pages-groupdocs-java/)
- [Como carregar documentos protegidos por senha em Java usando GroupDocs.Watermark](/watermark/java/document-loading-saving/groupdocs-watermark-java-password-protected-documents/)