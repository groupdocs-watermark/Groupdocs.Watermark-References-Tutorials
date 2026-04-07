---
date: '2026-04-07'
description: Aprenda como pesquisar o corpo de e‑mail em Java usando o GroupDocs.Watermark,
  incluindo como pesquisar múltiplas palavras‑chave em e‑mail e como remover marcas
  d'água de e‑mail.
keywords:
- search email body java
- search multiple keywords email
- how to remove email watermarks
title: 'Pesquisar o Corpo do Email em Java com GroupDocs.Watermark: Um Guia Abrangente'
type: docs
url: /pt/java/email-document-watermarking/master-groupdocs-watermark-java-email-text-search/
weight: 1
---

# Pesquisar Corpo de Email Java com GroupDocs.Watermark

Se você precisa **search email body java** rapidamente e de forma confiável, você está no lugar certo. Neste tutorial, vamos mostrar como o GroupDocs.Watermark para Java permite localizar texto específico dentro dos assuntos de email, corpos HTML e corpos de texto simples, e como você pode limpar marcas d'água indesejadas posteriormente. Ao final, você será capaz de implementar uma solução robusta que funciona com palavras‑chave únicas ou múltiplas e até mesmo remove marcas d'água de email quando necessário.

## Respostas Rápidas
- **What does “search email body java” mean?** Refere‑se ao uso de código Java (com GroupDocs.Watermark) para encontrar texto dentro do conteúdo de um email.  
- **Can I search multiple keywords email at once?** Sim – crie objetos `SearchCriteria` separados e combine‑os.  
- **How to remove email watermarks?** Use o método `PossibleWatermarkCollection.clear()` após uma pesquisa.  
- **Do I need a license?** Um teste gratuito funciona para testes; uma licença permanente é necessária para produção.  
- **Which IDE works best?** IntelliJ IDEA ou Eclipse são ambos totalmente suportados.

## O que você aprenderá
- Instalar e configurar o GroupDocs.Watermark para Java.  
- Configurar critérios de pesquisa para **search email body java** em assuntos e corpos.  
- Técnicas para **search multiple keywords email** em uma única execução.  
- Os passos exatos **how to remove email watermarks** após localizá‑los.  

## Por que pesquisar corpo de email Java com GroupDocs.Watermark?
O GroupDocs.Watermark fornece uma API de alto nível que abstrai as complexidades de analisar arquivos .msg, lidar com diferentes formatos de corpo e gerenciar marcas d'água. Isso economiza tempo em comparação com a criação de um analisador personalizado e garante resultados consistentes em grandes lotes de email.

## Pré‑requisitos
- Java Development Kit (JDK) 8 ou superior.  
- Maven (ou a capacidade de adicionar JARs manualmente).  
- Familiaridade básica com Java e formatos de arquivos de email (.msg, .eml).  

## Configurando o GroupDocs.Watermark para Java
O GroupDocs.Watermark para Java simplifica a marcação d'água e a pesquisa de texto dentro de documentos, incluindo emails. Abaixo estão as duas maneiras mais comuns de adicionar a biblioteca ao seu projeto.

### Configuração Maven
Include the following in your `pom.xml` file to add GroupDocs.Watermark as a dependency:
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
Alternativamente, você pode baixar a versão mais recente diretamente de [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

### Etapas de Aquisição de Licença
- **Free Trial:** Comece com um teste gratuito para testar funcionalidades básicas.  
- **Temporary License:** Licença Temporária: Obtenha uma licença temporária para acesso estendido e testes.  
- **Purchase:** Compra: Considere comprar se o GroupDocs.Watermark atender às suas necessidades.

#### Inicialização Básica
Initialize the `Watermarker` class as shown below:
```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.EmailLoadOptions;

EmailLoadOptions loadOptions = new EmailLoadOptions();
Watermarker watermarker = new Watermarker("input_email.msg", loadOptions);
```

## Guia de Implementação

### Recurso 1: Pesquisar Texto no Corpo do Email
Este recurso permite pesquisar texto específico dentro do assunto e corpo de um email.

#### Visão Geral
Vamos demonstrar como configurar o GroupDocs.Watermark para pesquisar diferentes partes de uma mensagem de email usando código Java.

##### Etapa 1: Definir Caminhos dos Documentos
Set up your input and output paths for handling emails:
```java
String inputDocumentPath = "YOUR_DOCUMENT_DIRECTORY/message.msg";
String outputDocumentPath = "YOUR_OUTPUT_DIRECTORY/output_message.msg";
```

##### Etapa 2: Configurar Opções de Carregamento e Watermarker
Initialize the `EmailLoadOptions` and `Watermarker` to work with your email document.
```java
EmailLoadOptions loadOptions = new EmailLoadOptions();
Watermarker watermarker = new Watermarker(inputDocumentPath, loadOptions);
```

##### Etapa 3: Criar Critérios de Pesquisa
Define criteria for searching text. We'll use a case‑insensitive search for the keyword **"test"**:
```java
import com.groupdocs.watermark.search.SearchCriteria;
import com.groupdocs.watermark.search.TextSearchCriteria;

SearchCriteria criteria = new TextSearchCriteria("test", false);
```

##### Etapa 4: Especificar Locais de Pesquisa
Configure the search to cover both the subject and body of emails:
```java
watermarker.getSearchableObjects().setEmailSearchableObjects(
    EmailSearchableObjects.Subject |
    EmailSearchableObjects.HtmlBody | 
    EmailSearchableObjects.PlainTextBody);
```

##### Etapa 5: Executar Pesquisa e Limpar Marcas d'Água
Perform the search and remove any found watermarks:
```java
import com.groupdocs.watermark.search.PossibleWatermarkCollection;

PossibleWatermarkCollection watermarks = watermarker.search(criteria);
watermarks.clear();
```

##### Etapa 6: Salvar Alterações
After processing, save your changes to a new document:
```java
watermarker.save(outputDocumentPath);
// Close the Watermarker instance to release resources
watermarker.close();
```

#### Dicas de Solução de Problemas
- **Common Issue:** Problema Comum: Se os resultados da pesquisa estiverem vazios, certifique‑se de que o texto está presente no corpo ou assunto do email.  
- **Performance Tip:** Dica de Desempenho: Otimize limitando as pesquisas apenas às seções que realmente precisa.

### Recurso 2: Opções de Carregamento de Documento de Email
Esta seção discute como você pode configurar opções adicionais ao carregar um documento de email para processamento com o GroupDocs.Watermark.

#### Visão Geral
Configurar opções de carregamento permite maior controle sobre como os documentos são manipulados, como especificar proteção por senha ou configurações de codificação.

##### Etapa 1: Configurar Opções de Carregamento
Here's a basic setup for `EmailLoadOptions`:
```java
EmailLoadOptions loadOptions = new EmailLoadOptions();
// Additional configurations can be added here.
```

#### Opções de Configuração Principais
- **Password Protection:** Proteção por Senha: Especifique senhas se seus emails estiverem criptografados.  
- **Encoding Settings:** Configurações de Codificação: Defina tipos de codificação específicos conforme necessário.

## Como Pesquisar Várias Palavras‑Chave de Email
Se você precisar localizar vários termos em uma única passagem, crie múltiplos objetos `SearchCriteria` e combine‑os usando operadores lógicos **OR** ou **AND**. A API permite encadear critérios, para que você possa pesquisar por “invoice” **or** “receipt” sem executar loops separados.

## Como Remover Marcas d'Água de Email
Depois de localizar marcas d'água (ou qualquer texto que corresponda aos seus critérios), o método `PossibleWatermarkCollection.clear()` remove‑as do documento de email. Este é o passo exato que usamos na **Step 5** acima, e funciona para qualquer número de correspondências.

## Aplicações Práticas

### Caso de Uso 1: Processamento Automatizado de Email
Automatize a filtragem e o processamento de grandes volumes de dados de email para encontrar conteúdo específico de forma eficiente.

### Caso de Uso 2: Verificações de Conformidade Legal
Garanta a conformidade pesquisando informações sensíveis dentro de emails corporativos.

### Caso de Uso 3: Automação de Suporte ao Cliente
Simplifique fluxos de trabalho de suporte localizando rapidamente palavras‑chave ou frases nas solicitações dos clientes.

## Considerações de Desempenho
Ao usar o GroupDocs.Watermark, considere o seguinte para otimizar o desempenho:

- **Resource Management:** Gerenciamento de Recursos: Gerencie eficientemente memória e poder de processamento para lidar com grandes conjuntos de dados de email.  
- **Java Memory Management Best Practices:** Melhores Práticas de Gerenciamento de Memória Java: Monitore regularmente o uso de recursos e libere recursos prontamente.

## Perguntas Frequentes

**Q:** Como posso lidar com emails criptografados com o GroupDocs.Watermark?  
**A:** Use o `EmailLoadOptions` para especificar senhas ao inicializar o `Watermarker`.

**Q:** Posso pesquisar várias palavras‑chave de uma vez?  
**A:** Sim, crie instâncias `SearchCriteria` separadas e combine‑as usando operações lógicas.

**Q:** O GroupDocs.Watermark Java é gratuito para uso?  
**A:** Um teste gratuito está disponível; considere comprar uma licença para recursos avançados.

**Q:** Como lidar com grandes volumes de emails de forma eficiente?  
**A:** Otimize suas pesquisas direcionando seções específicas de email e gerenciando recursos efetivamente.

**Q:** Onde posso encontrar ajuda ou suporte adicional?  
**A:** Visite o [GroupDocs forum](https://forum.groupdocs.com/c/watermark/10) para suporte da comunidade ou entre em contato com o canal de suporte gratuito.

## Recursos
- **Documentation:** Documentação: Explore guias detalhados em [GroupDocs Documentation](https://docs.groupdocs.com/watermark/java/).  
- **API Reference:** Referência da API: Acesse detalhes técnicos em [GroupDocs API](https://apireference.groupdocs.com/watermark/java/).

---

**Última Atualização:** 2026-04-07  
**Testado com:** GroupDocs.Watermark 24.11 for Java  
**Autor:** GroupDocs