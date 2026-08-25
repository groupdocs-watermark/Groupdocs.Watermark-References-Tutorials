---
date: '2026-08-25'
description: Aprenda a editar arquivos de diagramas e remover hyperlinks usando o
  GroupDocs.Watermark for Java. Proteja seus diagramas rapidamente com orientações
  passo a passo.
keywords:
- how to edit diagram
- remove hyperlinks diagram shapes
- GroupDocs.Watermark Java
lastmod: '2026-08-25'
og_description: Aprenda a editar arquivos de diagramas e remover hyperlinks usando
  o GroupDocs.Watermark for Java. Siga passos claros para proteger seus documentos.
og_image_alt: Guide showing how to edit diagram and remove hyperlinks using GroupDocs.Watermark
  Java
og_title: Como editar diagramas e remover hyperlinks com Java
tags:
- edit diagram
- remove hyperlinks
- GroupDocs.Watermark
- Java document processing
- diagram security
title: Como editar diagramas e remover hyperlinks com Java
type: docs
url: /pt/java/diagram-document-watermarking/remove-hyperlinks-diagram-shapes-groupdocs-watermark-java/
weight: 1
---

# Como editar diagrama e remover hyperlinks com Java  

Gerenciar documentos digitais frequentemente envolve a edição de diagramas, especialmente quando você precisa **editar diagrama** arquivos para remover hyperlinks por questões de segurança ou clareza visual. Este tutorial mostra exatamente como editar arquivos de diagrama e remover hyperlinks indesejados de formas de diagrama usando a poderosa biblioteca **GroupDocs.Watermark** para Java. Ao final deste guia, você terá um diagrama limpo, sem links, pronto para distribuição.  

## Respostas rápidas  
- **Qual é o objetivo principal?** Remover todos os hyperlinks das formas do diagrama para melhorar a segurança e a apresentação.  
- **Qual biblioteca é necessária?** GroupDocs.Watermark para Java, versão 24.11 ou mais recente.  
- **Preciso de licença?** Um teste gratuito funciona para avaliação; uma licença comercial é necessária para produção.  
- **Posso processar vários arquivos de uma vez?** Sim – o mesmo código pode ser colocado dentro de um loop para lidar com lotes.  
- **Qual versão do Java é suportada?** Java 8 ou superior (Java 11 recomendado).  

## O que é “como editar diagrama”?  
**Como editar diagrama** refere-se ao processo de abrir programaticamente um arquivo de diagrama, modificar seus elementos internos (como formas, texto ou hyperlinks) e salvar o resultado. Usando o GroupDocs.Watermark, você pode editar arquivos de diagrama sem precisar da ferramenta de autoria original.  

## Por que usar GroupDocs.Watermark para Java?  
GroupDocs.Watermark suporta **mais de 30 formatos de diagramas e imagens** (incluindo VSDX, SVG e WMF) e pode processar arquivos de até **500 MB** sem carregar todo o documento na memória, oferecendo uma velocidade de processamento **20 % mais rápida** em comparação com muitos concorrentes.  

## Pré-requisitos  
- **GroupDocs.Watermark** versão 24.11 ou posterior.  
- Maven instalado (ou os arquivos JAR se preferir configuração manual).  
- Java Development Kit 8 ou mais recente e uma IDE como IntelliJ IDEA ou Eclipse.  

### Bibliotecas necessárias, versões e dependências  
- GroupDocs.Watermark 24.11+  
- Maven 3.6+ (se você usar a abordagem Maven)  

### Requisitos de configuração do ambiente  
Certifique-se de que o diretório `bin` do JDK esteja no seu `PATH` e que sua IDE aponte para a versão correta do JDK.  

### Pré-requisitos de conhecimento  
Você deve estar confortável com a sintaxe básica de Java, gerenciamento de dependências Maven e operações de I/O de arquivos.  

## Como configurar o GroupDocs.Watermark para Java?  
A classe `Watermarker` fornece o ponto de entrada da API para carregar e modificar documentos.  
Para começar a usar o GroupDocs.Watermark, adicione suas coordenadas Maven ao `pom.xml` do seu projeto. Isso traz a biblioteca e suas dependências, permitindo instanciar a classe Watermarker e trabalhar com arquivos de diagrama diretamente a partir do código Java. Você pode então configurar a licença e definir opções de saída antes de processar qualquer documento.  

Adicione a dependência do GroupDocs.Watermark ao seu `pom.xml`.  

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

Se preferir não usar Maven, faça o download do JAR mais recente na página oficial de releases.  

[GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/)  

#### Etapas para obtenção de licença  
- Comece com um teste gratuito para avaliar a API.  
- Para produção, obtenha uma licença temporária ou permanente no portal do fornecedor.  

#### Inicialização e configuração básicas  
A classe `Watermarker` é o ponto de entrada para todas as operações de processamento de documentos.  

```java
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY", loadOptions);
```  

## Como editar diagrama e remover hyperlinks com GroupDocs.Watermark?  
A classe `Watermarker` fornece o ponto de entrada da API para carregar e modificar documentos.  
Primeiro, carregue o arquivo de diagrama em uma instância de Watermarker. Em seguida, recupere a coleção de formas, identifique aquelas que contêm objetos de hyperlink e itere sobre elas em ordem reversa para excluir com segurança cada link sem afetar a indexação da coleção. Isso garante que todas as URLs incorporadas sejam removidas, preservando a integridade visual do diagrama.  

```java
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY", loadOptions);
```  

- **Por que esta etapa é importante**: Carregar o arquivo fornece acesso programático a cada forma e suas propriedades associadas.  

## Como acessar o conteúdo de forma em um diagrama?  
O objeto `DiagramShape` representa uma forma individual dentro de um diagrama, expondo suas propriedades e metadados associados.  
Após carregar o diagrama, chame `getShapes()` no Watermarker para obter uma lista de objetos `DiagramShape`. Cada forma pode ser inspecionada quanto a coleções de hyperlinks, permitindo direcionamento preciso de links para remoção ou modificação. Você também pode ler o texto da forma, cores e geometria se ajustes adicionais forem necessários.  

```java
DiagramContent content = watermarker.getContent(DiagramContent.class);
DiagramShape shape = content.getPages().get_Item(0).getShapes().get_Item(0);
```  

- **Por que esta etapa é importante**: Alvo na forma exata garante que você remova apenas os links indesejados sem afetar outros elementos visuais.  

## Como iterar e remover hyperlinks com segurança?  
O método `removeHyperlink(int index)` exclui um hyperlink na posição especificada dentro da coleção de hyperlinks de uma forma.  
Itere sobre a lista de hyperlinks do último índice até zero. Esse loop reverso impede o deslocamento de índices que ocorre quando itens são removidos, garantindo que cada hyperlink seja processado sem ser pulado. Após a remoção, você pode atualizar o estado da forma ou continuar para a próxima forma no diagrama.  

```java
for (int i = shape.getHyperlinks().getCount() - 1; i >= 0; i--) {
    if (shape.getHyperlinks().get_Item(i).getAddress().contains("http://someurl.com")) {
        shape.getHyperlinks().removeAt(i);
    }
}
```  

- **Por que esta etapa é importante**: Um loop reverso garante que todos os hyperlinks sejam removidos sem pular nenhuma entrada.  

## Como salvar o diagrama editado e liberar recursos?  
O método `save(String path)` grava o documento modificado no local de arquivo especificado, finalizando todas as alterações.  
Depois que todos os hyperlinks forem removidos, invoque o método `save` na instância Watermarker, fornecendo um novo nome de arquivo para evitar sobrescrever o original. Em seguida, chame `close()` para liberar os manipuladores de arquivo e liberar memória, o que é essencial para processos em lote de longa duração. Isso garante que o arquivo seja fechado corretamente e esteja pronto para uso futuro.  

```java
watermarker.save("YOUR_OUTPUT_DIRECTORY");
watermarker.close();
```  

- **Por que esta etapa é importante**: Fechar corretamente os recursos evita vazamentos de memória e problemas de bloqueio de arquivos no servidor.  

## Aplicações práticas  
Remover hyperlinks de formas de diagramas pode ser benéfico em vários cenários reais:  

1. **Segurança** – Impedir links externos que podem levar a sites maliciosos.  
2. **Conformidade** – Atender às políticas corporativas que proíbem URLs incorporados em ativos compartilhados.  
3. **Clareza** – Produzir apresentações mais limpas onde os links seriam distrativos.  

Você pode incorporar essa lógica em pipelines de automação maiores, como jobs em lote noturnos que sanitizam todos os diagramas antes de serem publicados em uma intranet.  

## Considerações de desempenho  

### Otimizando desempenho  
- Use uma única instância `Watermarker` por arquivo para reduzir a sobrecarga.  
- Prefira iteração reversa (como mostrado) para evitar reindexação custosa da lista.  

### Diretrizes de uso de recursos  
- Para diagramas maiores que 200 MB, monitore o uso de heap e considere aumentar a flag JVM `-Xmx`.  
- Ferramentas de profiling como VisualVM podem ajudar a identificar gargalos em execuções em lote de grande escala.  

### Melhores práticas para gerenciamento de memória Java  
- Declare objetos dentro do escopo menor possível.  
- Use try‑with‑resources ao trabalhar com streams para garantir o fechamento automático.  

## Perguntas frequentes  

**Q: Como lidar com diagramas que contêm milhares de formas?**  
A: Processar o diagrama página por página e liberar os recursos de cada página antes de passar para a próxima, mantendo o uso de memória baixo.  

**Q: Posso limitar a remoção de hyperlinks a páginas específicas apenas?**  
A: Sim – recupere o índice da página desejada e aplique o loop de remoção apenas às formas nessa página.  

**Q: Uma licença comercial é obrigatória para processamento em lote?**  
A: Uma licença válida é necessária para qualquer implantação em nível de produção; o teste gratuito é limitado a 30 dias e 5 documentos.  

**Q: O GroupDocs.Watermark suporta diagramas SVG?**  
A: Absolutamente – SVG está entre os mais de 30 formatos suportados, e hyperlinks podem ser removidos usando as mesmas chamadas de API.  

**Q: E se uma forma tiver múltiplos hyperlinks?**  
A: O loop de iteração reversa remove cada entrada de hyperlink individualmente, garantindo que todos os links sejam apagados.  

## Recursos  

- [Documentation](https://docs.groupdocs.com/watermark/java/)  
- [API Reference](https://reference.groupdocs.com/watermark/java)  
- [Download](https://releases.groupdocs.com/watermark/java/)  
- [GitHub Repository](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)  
- [Free Support Forum](https://forum.groupdocs.com/c/watermark/10)  
- [Temporary License Acquisition](https://purchase.groupdocs.com/temporary-license/)  

---  

**Última atualização:** 2026-08-25  
**Testado com:** GroupDocs.Watermark 24.11 for Java  
**Autor:** GroupDocs  

## Tutoriais relacionados

- [Tutoriais de marca d'água de diagramas para GroupDocs.Watermark Java](/watermark/java/diagram-document-watermarking/)  
- [Editar cabeçalhos e rodapés de diagramas em Java usando GroupDocs.Watermark: Um guia abrangente](/watermark/java/diagram-document-watermarking/edit-diagram-headers-footers-groupdocs-watermark-java/)  
- [Remover formas de diagramas de forma eficiente usando GroupDocs.Watermark para Java](/watermark/java/watermark-removal/remove-shapes-diagrams-groupdocs-watermark-java/)