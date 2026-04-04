---
date: '2026-04-04'
description: Aprenda como remover links de formas de diagramas com o GroupDocs.Watermark
  Java, garantindo a segurança e a clareza dos documentos.
keywords:
- how to strip links
- remove hyperlinks java
- java diagram editing
title: Como remover links de formas de diagrama usando GroupDocs.Watermark Java
type: docs
url: /pt/java/diagram-document-watermarking/remove-hyperlinks-diagram-shapes-groupdocs-watermark-java/
weight: 1
---

# Como remover links de formas de diagrama usando GroupDocs.Watermark Java

Gerenciar documentos digitais frequentemente envolve a edição de diagramas, especialmente quando você precisa **como remover links** para segurança ou clareza. Neste tutorial, você aprenderá um método simples, passo a passo, para remover hyperlinks indesejados de formas de diagrama usando a poderosa biblioteca **GroupDocs.Watermark** para Java. Ao final, você terá diagramas limpos, sem links, seguros para compartilhar.

## Respostas Rápidas
- **O que significa “como remover links”?** Refere‑se à remoção de objetos hyperlink incorporados nas formas do diagrama.  
- **Qual biblioteca lida com isso?** GroupDocs.Watermark for Java (versão 24.11 ou mais recente).  
- **Preciso de licença?** Um teste gratuito funciona para testes; uma licença válida é necessária para produção.  
- **Posso processar vários arquivos de uma vez?** Sim – envolva o código em um loop ou tarefa em lote.  
- **Esta abordagem é específica de linguagem?** O exemplo é Java, mas o mesmo conceito se aplica a outras APIs .NET/Java.

## O que é “como remover links” na edição de diagramas?
Remover links significa localizar objetos hyperlink anexados a formas dentro de um diagrama (por exemplo, Visio *.vsdx) e excluí‑los. Isso elimina URLs externas que poderiam expor informações sensíveis ou interromper o fluxo da apresentação.

## Por que usar GroupDocs.Watermark para Java?
- **Precisão** – Acesso direto a objetos de forma e suas coleções de hyperlinks.  
- **Desempenho** – Otimizado para diagramas grandes sem carregar todo o documento na memória.  
- **Suporte a múltiplos formatos** – Funciona com vários formatos de diagrama (Visio, Draw.io, etc.).

## Pré‑requisitos
- Biblioteca **GroupDocs.Watermark** ≥ 24.11.  
- Maven (ou inclusão manual de JAR).  
- Java JDK 8 ou superior.  
- Uma IDE como IntelliJ IDEA ou Eclipse.

## Configurando GroupDocs.Watermark para Java
### Configuração Maven
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

### Download Direto
Se preferir não usar Maven, obtenha o JAR mais recente no site oficial:  
[GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

#### Etapas de Aquisição de Licença
- Comece com o download da versão de teste gratuita.  
- Para produção, obtenha uma licença temporária ou completa no portal GroupDocs.

#### Inicialização e Configuração Básicas
Crie uma instância `Watermarker` que aponta para a pasta contendo seu diagrama:

```java
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY", loadOptions);
```

## Como Remover Links de Formas de Diagrama
A seguir está um processo conciso de quatro etapas que demonstra **remove hyperlinks java** em ação.

### Etapa 1: Carregar o Arquivo de Diagrama
```java
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY", loadOptions);
```
*Por quê?* Carregar o arquivo fornece acesso programático às suas páginas, formas e coleções de hyperlinks.

### Etapa 2: Acessar o Conteúdo da Forma
```java
DiagramContent content = watermarker.getContent(DiagramContent.class);
DiagramShape shape = content.getPages().get_Item(0).getShapes().get_Item(0);
```
*Por quê?* Você precisa de uma referência à forma específica que pode conter hyperlinks.

### Etapa 3: Iterar e Remover Hyperlinks
```java
for (int i = shape.getHyperlinks().getCount() - 1; i >= 0; i--) {
    if (shape.getHyperlinks().get_Item(i).getAddress().contains("http://someurl.com")) {
        shape.getHyperlinks().removeAt(i);
    }
}
```
*Por quê?* Iterar em ordem reversa evita problemas de deslocamento de índice ao excluir itens da coleção.

### Etapa 4: Salvar e Fechar
```java
watermarker.save("YOUR_OUTPUT_DIRECTORY");
watermarker.close();
```
*Por quê?* Salvar grava o diagrama limpo no disco, e fechar libera os manipuladores de arquivo para evitar vazamentos de memória.

## Aplicações Práticas da Remoção de Links
1. **Segurança** – Remover URLs externas que podem levar a phishing ou vazamento de dados.  
2. **Conformidade** – Garantir que os diagramas atendam às políticas internas antes da distribuição.  
3. **Limpeza de Apresentação** – Eliminar áreas clicáveis desnecessárias que distraem os espectadores.

## Considerações de Desempenho
- **Eficiência de Loop** – Use o padrão de iteração reversa mostrado acima.  
- **Gerenciamento de Recursos** – Prefira `try‑with‑resources` ou chamadas explícitas a `close()`.  
- **Arquivos Grandes** – Monitore CPU/memória; considere processar páginas em lotes.

## Problemas Comuns e Soluções
- **Nenhum hyperlink encontrado** – Verifique se o diagrama realmente contém objetos hyperlink; alguns formatos os armazenam de forma diferente.  
- **IndexOutOfBoundsException** – Sempre itere em ordem reversa ao remover itens de uma coleção.  
- **Erros de licença** – Certifique‑se de que seu arquivo de licença está corretamente colocado ou passado ao construtor `Watermarker`.

## Perguntas Frequentes

**Q: Como lidar com múltiplas formas em várias páginas?**  
A: Percorra `content.getPages()` e depois a coleção `getShapes()` de cada página, aplicando a mesma lógica de remoção a cada forma.

**Q: Posso filtrar links por domínio em vez de uma URL completa?**  
A: Sim – altere a verificação `contains` para procurar a string do domínio (por exemplo, `"example.com"`).

**Q: Existe uma maneira de registrar quais links foram removidos?**  
A: Dentro do loop, capture `shape.getHyperlinks().get_Item(i).getAddress()` antes da remoção e escreva em um arquivo de log.

**Q: Isso funciona com diagramas PDF incorporados em outros documentos?**  
A: O GroupDocs.Watermark suporta muitos formatos; certifique‑se de que o tipo de arquivo seja reconhecido como um diagrama (Visio, VDX, etc.).

**Q: Que licenciamento é necessário para processamento em lote?**  
A: É necessária uma licença de produção completa para quaisquer operações de alto volume que não sejam de teste.

## Conclusão
Agora você tem um método completo e pronto para produção para **how to strip links** de formas de diagrama usando GroupDocs.Watermark para Java. Incorpore isso em seus pipelines de processamento de documentos para melhorar a segurança, conformidade e qualidade visual.

### Próximos Passos
- Explore outros recursos de manipulação, como adicionar marcas d'água ou carimbar texto.  
- Combine esta rotina com um serviço de monitoramento de arquivos para limpar diagramas automaticamente ao serem enviados.

---

**Última atualização:** 2026-04-04  
**Testado com:** GroupDocs.Watermark 24.11 for Java  
**Autor:** GroupDocs  

## Recursos
- [Documentação](https://docs.groupdocs.com/watermark/java/)
- [Referência da API](https://reference.groupdocs.com/watermark/java)
- [Download](https://releases.groupdocs.com/watermark/java/)
- [Repositório GitHub](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)
- [Fórum de Suporte Gratuito](https://forum.groupdocs.com/c/watermark/10)
- [Aquisição de Licença Temporária](https://purchase.groupdocs.com/temporary-license/)