---
date: '2025-12-31'
description: Aprenda a pesquisar texto de e‑mail usando o GroupDocs.Watermark para
  Java, gerenciando corpos, assuntos e anexos de forma eficiente.
keywords:
- GroupDocs Watermark Java
- search text in email body
- manage email watermarks
title: Como pesquisar texto de e‑mail com GroupDocs.Watermark Java – Um guia abrangente
type: docs
url: /pt/java/email-document-watermarking/master-groupdocs-watermark-java-email-text-search/
weight: 1
---

# Como Pesquisar Texto de Email com GroupDocs.Watermark Java

Encontrar uma frase específica dentro do assunto, corpo ou anexos de um email pode ser um pesadelo—especialmente quando você está lidando com dezenas ou centenas de mensagens. Neste tutorial você descobrirá **como pesquisar email** rapidamente e com precisão usando **GroupDocs.Watermark for Java**. Vamos percorrer a configuração, o código e dicas de melhores práticas para que você possa integrar a pesquisa de texto de email em suas próprias aplicações com confiança.

## Respostas Rápidas
- **Qual biblioteca me permite pesquisar texto de email em Java?** GroupDocs.Watermark for Java.  
- **Preciso de uma licença?** Um teste gratuito funciona para avaliação; uma licença paga é necessária para produção.  
- **Posso pesquisar tanto o assunto quanto o corpo?** Sim—configure `EmailSearchableObjects` para incluir Subject, HtmlBody e PlainTextBody.  
- **A API diferencia maiúsculas de minúsculas?** Você pode escolher buscas sem diferenciação de maiúsculas/minúsculas definindo a flag apropriada em `TextSearchCriteria`.  
- **Qual versão do Java é necessária?** JDK 8 ou superior; Maven é recomendado para gerenciamento de dependências.

## O que é “como pesquisar email” com GroupDocs.Watermark?
GroupDocs.Watermark fornece uma API unificada para localizar, remover ou modificar marcas d'água e texto simples em diversos tipos de documentos—including **mensagens de email** (`.msg`, `.eml`). Ao aproveitar seu modelo de objetos pesquisáveis, você pode direcionar exatamente as partes de um email que lhe interessam, tornando o processamento em massa rápido e confiável.

## Por que usar GroupDocs.Watermark Java para pesquisa de email?
- **API Unificada** – Funciona com PDFs, imagens, arquivos Office e emails usando os mesmos padrões de código.  
- **Desempenho otimizado** – Operações de busca são executadas na memória sem necessidade de serviços externos.  
- **Manipulação robusta** – Suporta corpos HTML e texto simples, anexos e até emails protegidos por senha.  
- **Integração fácil** – Pronto para Maven/Gradle, com documentação clara e suporte ativo.

## Pré-requisitos
- **Java Development Kit (JDK)** 8 ou mais recente.  
- **Maven** (ou Gradle) para gerenciamento de dependências.  
- Uma IDE como **IntelliJ IDEA** ou **Eclipse**.  
- Familiaridade básica com a sintaxe Java e formatos de arquivos de email (`.msg`, `.eml`).

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
Alternativamente, você pode baixar o JAR mais recente em [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

### Aquisição de Licença
- **Teste Gratuito:** Teste os recursos principais sem uma chave de licença.  
- **Licença Temporária:** Solicite uma chave limitada no tempo para avaliação prolongada.  
- **Licença Pago:** Compre para uso ilimitado em produção.

#### Inicialização Básica
```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.EmailLoadOptions;

EmailLoadOptions loadOptions = new EmailLoadOptions();
Watermarker watermarker = new Watermarker("input_email.msg", loadOptions);
```

## Guia de Implementação

### Recurso 1: Pesquisar Texto no Corpo do Email

#### Visão Geral
Vamos configurar a API para analisar o **assunto**, **corpo HTML** e **corpo em texto simples** de um email em busca de uma palavra‑chave especificada.

#### Etapa 1: Definir Caminhos dos Documentos
```java
String inputDocumentPath = "YOUR_DOCUMENT_DIRECTORY/message.msg";
String outputDocumentPath = "YOUR_OUTPUT_DIRECTORY/output_message.msg";
```

#### Etapa 2: Configurar Opções de Carregamento e Watermarker
```java
EmailLoadOptions loadOptions = new EmailLoadOptions();
Watermarker watermarker = new Watermarker(inputDocumentPath, loadOptions);
```

#### Etapa 3: Criar Critérios de Busca
```java
import com.groupdocs.watermark.search.SearchCriteria;
import com.groupdocs.watermark.search.TextSearchCriteria;

SearchCriteria criteria = new TextSearchCriteria("test", false);
```

#### Etapa 4: Especificar Locais de Busca
```java
watermarker.getSearchableObjects().setEmailSearchableObjects(
    EmailSearchableObjects.Subject |
    EmailSearchableObjects.HtmlBody | 
    EmailSearchableObjects.PlainTextBody);
```

#### Etapa 5: Executar Busca e Limpar Marcas d'Água
```java
import com.groupdocs.watermark.search.PossibleWatermarkCollection;

PossibleWatermarkCollection watermarks = watermarker.search(criteria);
watermarks.clear();
```

#### Etapa 6: Salvar Alterações
```java
watermarker.save(outputDocumentPath);
// Close the Watermarker instance to release resources
watermarker.close();
```

#### Dicas de Solução de Problemas
- **Resultados vazios:** Verifique se a palavra‑chave realmente aparece nas partes selecionadas do email.  
- **Desempenho:** Limite os objetos pesquisáveis apenas ao que você precisa (ex.: Subject + PlainTextBody) para acelerar lotes grandes.

### Recurso 2: Opções de Carregamento de Documento de Email

#### Visão Geral
`EmailLoadOptions` permite controlar como o email é analisado—útil para mensagens criptografadas ou codificações personalizadas.

#### Etapa 1: Configurar Opções de Carregamento
```java
EmailLoadOptions loadOptions = new EmailLoadOptions();
// Additional configurations can be added here.
```

#### Opções de Configuração Principais
- **Proteção por Senha:** Defina `loadOptions.setPassword("yourPassword")` para arquivos `.msg` criptografados.  
- **Configurações de Codificação:** Ajuste `loadOptions.setEncoding(Charset.forName("UTF-8"))` ao lidar com conjuntos de caracteres não‑padrão.

## Aplicações Práticas
- **Processamento Automatizado de Email:** Escaneie em massa tickets de suporte recebidos em busca de palavras‑chave como “refund” ou “error”.  
- **Verificações de Conformidade Legal:** Localize rapidamente termos confidenciais (ex.: SSN, números de cartão de crédito) em arquivos de email corporativos.  
- **Automação de Suporte ao Cliente:** Direcione emails com base em frases detectadas para a equipe de suporte correta.

## Considerações de Desempenho
- **Gerenciamento de Recursos:** Chame `watermarker.close()` assim que terminar o processamento para liberar recursos nativos.  
- **Melhores Práticas de Memória:** Ao lidar com milhares de mensagens, processe-as em lotes e reutilize a instância `Watermarker` sempre que possível.

## Conclusão
Agora você tem uma abordagem sólida e pronta para produção para **como pesquisar email** usando GroupDocs.Watermark Java. A flexibilidade da API permite direcionar partes específicas de um email, remover marcas d'água indesejadas e integrar a lógica em fluxos de trabalho maiores.

### Próximos Passos
- Experimente **múltiplos critérios de busca** (ex.: combinar “invoice” + “overdue”).  
- Explore **adição de marca d'água** para sinalizar emails que contenham dados sensíveis.  
- Mergulhe em outros tipos de documentos (PDF, DOCX) usando o mesmo fluxo de trabalho Watermarker.

## Perguntas Frequentes

**Q1:** Como posso lidar com emails criptografados com GroupDocs.Watermark?  
**A1:** Use `EmailLoadOptions.setPassword("yourPassword")` antes de criar a instância `Watermarker`.

**Q2:** Posso pesquisar múltiplas palavras‑chave ao mesmo tempo?  
**A2:** Sim—crie objetos `SearchCriteria` separados para cada palavra‑chave e combine‑os com operadores lógicos (ex.: `OrSearchCriteria`).

**Q3:** O GroupDocs.Watermark Java é gratuito para uso?  
**A3:** Um teste gratuito está disponível para avaliação. Para uso em produção, é necessária uma licença paga.

**Q4:** Como lidar com grandes volumes de emails de forma eficiente?  
**A4:** Limite os objetos pesquisáveis apenas ao necessário, processe os emails em lotes e sempre feche o `Watermarker` para liberar recursos.

**Q5:** Onde posso encontrar ajuda ou suporte adicional?  
**A5:** Visite o [GroupDocs forum](https://forum.groupdocs.com/c/watermark/10) para assistência da comunidade ou entre em contato diretamente com o suporte da GroupDocs.

## Recursos
- **Documentação:** Explore guias detalhados em [GroupDocs Documentation](https://docs.groupdocs.com/watermark/java/).  
- **Referência da API:** Acesse detalhes técnicos em [GroupDocs API](https://apireference.groupdocs.com/watermark/java/).

---

**Última Atualização:** 2025-12-31  
**Testado com:** GroupDocs.Watermark 24.11 for Java  
**Autor:** GroupDocs  

---