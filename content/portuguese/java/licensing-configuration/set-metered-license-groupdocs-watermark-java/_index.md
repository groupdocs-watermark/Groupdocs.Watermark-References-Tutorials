---
date: '2026-01-21'
description: Aprenda como definir a licença para o GroupDocs Watermark em Java, incluindo
  como aplicar marca d'água em PDF e gerenciar o uso com uma licença por medição.
keywords:
- metered license GroupDocs Watermark Java
- GroupDocs.Watermark setup Java
- Java document security watermarks
title: Como definir a licença do GroupDocs Watermark (por uso) em Java
type: docs
url: /pt/java/licensing-configuration/set-metered-license-groupdocs-watermark-java/
weight: 1
---

# Como Definir Licença para GroupDocs Watermark (Metered) em Java

Proteger a propriedade intelectual é uma prioridade máxima para empresas modernas, e marcas d'água são uma forma comprovada de fazer isso. Neste tutorial você aprenderá **como definir licença** para GroupDocs.Watermark usando uma abordagem metered, para que possa **aplicar marca d'água em PDFs** mantendo controle total sobre o uso. Vamos percorrer tudo, desde pré‑requisitos até cenários de uso no mundo real, e mostrar exatamente onde **usar chaves públicas e privadas** para ativar a licença.

## Respostas Rápidas
- **O que é uma licença metered?** Um modelo de licenciamento baseado em uso que rastreia cada chamada de API.
- **Preciso de um arquivo de licença?** Não – a ativação é feita com chaves públicas e privadas.
- **Qual versão do Java é necessária?** Java 8 ou superior.
- **Posso adicionar marca d'água em documentos PDF?** Sim, a API suporta PDF, DOCX, PPTX e imagens.
- **Este método é seguro?** Sim, as chaves são transmitidas via HTTPS e nunca armazenadas em texto puro.

## O que é uma Licença Metered e Por Que Usá‑la?
Uma licença metered permite que você pague apenas pelo que realmente consome, tornando‑a ideal para arquiteturas SaaS ou de microsserviços. Ela fornece recursos de **document security watermark** sem a sobrecarga de gerenciar arquivos de licença tradicionais, e você pode escalar seu uso para cima ou para baixo instantaneamente.

## Pré‑requisitos
Antes de começar, verifique se você tem:

1. **GroupDocs.Watermark para Java** ≥ 24.11 (a versão mais recente).  
2. **JDK 8+** instalado e `JAVA_HOME` configurado.  
3. **Chaves públicas e privadas** obtidas na sua conta GroupDocs (você as usará no código).  

## Configurando GroupDocs.Watermark para Java

### Informações de Instalação
Integre o GroupDocs.Watermark ao seu projeto Maven:

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

> **Dica:** A mesma URL do repositório também é usada para a opção de download direto abaixo.

#### Download Direto
Baixe o JAR mais recente na página oficial de lançamentos: [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

### Aquisição de Licença
Para desbloquear recursos premium, você precisa de uma licença temporária ou de avaliação. Inscreva‑se no [site da GroupDocs](https://purchase.groupdocs.com/temporary-license/) e copie as chaves públicas/privadas fornecidas.

### Inicialização Básica
Depois que a biblioteca estiver no seu classpath, você pode inicializá‑la:

```java
import com.groupdocs.watermark.License;

public class InitializeWatermark {
    public static void main(String[] args) throws Exception {
        License license = new License();
        // Apply the license using your path to the license file
        license.setLicense("path/to/your/license/file.lic");
    }
}
```

> **Por que isso importa:** Mesmo ao usar uma licença metered, inicializar o objeto `License` garante que o SDK esteja pronto para aceitar a ativação baseada em chave mais adiante no fluxo de trabalho.

## Guia de Implementação

### Definindo uma Licença Metered

#### Etapa 1: Definir as Chaves Públicas e Privadas
```java
// Step 1: Define the public and private keys for the metered license.
String publicKey = "*****"; // Replace with your actual public key
String privateKey = "*****"; // Replace with your actual private key
```
Essas chaves **usam chaves públicas e privadas** para identificar sua conta de forma segura.

#### Etapa 2: Criar uma Instância da Classe Metered
```java
// Step 2: Create an instance of Metered class.
Metered metered = new Metered();
```
A classe `Metered` lida com todo o rastreamento de uso nos bastidores.

#### Etapa 3: Definir a Licença Metered Usando as Chaves Fornecidas
```java
// Step 3: Set the metered license using the provided keys.
metered.setMeteredKey(publicKey, privateKey);
```
Após esta chamada, o SDK está totalmente licenciado e você pode começar a **adicionar marca d'água em PDFs** ou **criar documentos com marca d'água**.

### Por Que Usar Chaves Públicas/Privadas Em Vez de um Arquivo de Licença?
- **Segurança:** As chaves nunca são gravadas em disco em texto puro.  
- **Flexibilidade:** Troque de ambientes (dev, teste, prod) sem copiar arquivos.  
- **Escalabilidade:** Perfeito para implantações cloud‑native onde os contêineres são imutáveis.

## Aplicações Práticas

1. **Segurança de Documentos:** Incorpore uma marca d'água visível ou invisível em PDFs para impedir a distribuição não autorizada.  
2. **Rastreamento de Uso:** Monitore quantos documentos são processados a cada mês, ajudando a permanecer dentro da sua cota metered.  
3. **Integração CMS:** Aplique automaticamente **marca d'água em PDFs** a cada arquivo enviado em um sistema de gerenciamento de conteúdo.

## Considerações de Desempenho

- **Aplique marca d'água somente quando necessário** – evite processar lotes grandes sem necessidade.  
- **Reutilize a instância `Metered`** entre requisições para reduzir a sobrecarga de criação de objetos.  
- **Monitore a memória** ao lidar com imagens de alta resolução; o SDK oferece APIs de streaming para manter a pegada baixa.

## Problemas Comuns e Soluções
| Problema | Solução |
|----------|---------|
| As chaves são rejeitadas | Verifique se não há espaços extras ou quebras de linha nas strings. |
| Licença não ativada | Certifique‑se de chamar `metered.setMeteredKey(...)` **antes** de qualquer operação de marca d'água. |
| Erros de falta de memória em PDFs grandes | Use `WatermarkOptions.setUseMemoryCache(true)` para descarregar o processamento para disco. |

## Perguntas Frequentes

**P: O que é uma licença metered e por que devo usá‑la?**  
R: Uma licença metered rastreia cada chamada de API, permitindo que você pague apenas pelo uso real e escale sua aplicação facilmente.

**P: Posso alternar entre um arquivo de licença de avaliação e uma chave metered?**  
R: Sim. Basta chamar `license.setLicense("path/to/file.lic")` para a avaliação e, depois, substituí‑la por `metered.setMeteredKey(...)`.

**P: O que acontece se a chave pública ou privada for inserida incorretamente?**  
R: O SDK lançará uma exceção de autenticação e bloqueará o acesso aos recursos premium.

**P: Existem limites de quantas marcas d'água posso adicionar por mês?**  
R: Os limites dependem do contrato que você tem com a GroupDocs; verifique seu painel para quotas exatas.

**P: Isso funciona com arquivos de imagem assim como PDFs?**  
R: Absolutamente. A mesma API suporta JPEG, PNG, BMP e outros formatos de imagem comuns.

## Recursos

- [Documentação](https://docs.groupdocs.com/watermark/java/)
- [Referência da API](https://reference.groupdocs.com/watermark/java)
- [Download](https://releases.groupdocs.com/watermark/java/)
- [Repositório no GitHub](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)
- [Fórum de Suporte Gratuito](https://forum.groupdocs.com/c/watermark/10)
- [Aquisição de Licença Temporária](https://purchase.groupdocs.com/temporary-license/)

---

**Última Atualização:** 2026-01-21  
**Testado Com:** GroupDocs.Watermark 24.11 para Java  
**Autor:** GroupDocs