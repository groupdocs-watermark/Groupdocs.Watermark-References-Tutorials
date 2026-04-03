---
date: '2025-12-31'
description: Aprende a buscar texto en correos electrónicos usando GroupDocs.Watermark
  para Java, gestiona cuerpos, asuntos y archivos adjuntos de manera eficiente.
keywords:
- GroupDocs Watermark Java
- search text in email body
- manage email watermarks
title: Cómo buscar texto de correo electrónico con GroupDocs.Watermark Java – Guía
  completa
type: docs
url: /es/java/email-document-watermarking/master-groupdocs-watermark-java-email-text-search/
weight: 1
---

# Cómo buscar texto de correo electrónico con GroupDocs.Watermark Java

Encontrar una frase específica dentro del asunto, cuerpo o archivos adjuntos de un correo electrónico puede ser un dolor de cabeza, sobre todo cuando se manejan decenas o cientos de mensajes. En este tutorial descubrirás **cómo buscar texto en correos electrónicos** de forma rápida y precisa usando **GroupDocs.Watermark para Java**. Recordaremos la configuración, el código y consejos de buenas prácticas para que puedas integrar la búsqueda de texto en correos electrónicos en tus propias aplicaciones con confianza.

## Respuestas rápidas
- **¿Qué biblioteca me permite buscar texto de correo electrónico en Java?**GroupDocs.Watermark para Java.
- **¿Necesito una licencia?**Una prueba gratuita funciona para realizar pruebas; Se requiere una licencia paga para la producción.
- **¿Puedo buscar tanto por asunto como por cuerpo?**Sí: configure `EmailSearchableObjects` para incluir Asunto, HtmlBody y PlainTextBody.
- ¿La API distingue entre mayúsculas y minúsculas? Puede configurar búsquedas que no distingan entre mayúsculas y minúsculas estableciendo la bandera correspondiente en `TextSearchCriteria`.

- ¿Qué versión de Java se requiere? JDK 8 o superior; se recomienda Maven para la gestión de dependencias.

## ¿Cómo se busca en correos electrónicos con GroupDocs.Watermark?

GroupDocs.Watermark proporciona una API unificada para localizar, eliminar o modificar marcas de agua y texto sin formato en diversos tipos de documentos, incluidos los **mensajes de correo electrónico** (`.msg`, `.eml`). Gracias a su modelo de objetos de búsqueda, puede seleccionar con precisión las partes de un correo electrónico que le interesan, lo que hace que el procesamiento masivo sea rápido y fiable.

## ¿Por qué usar GroupDocs.Watermark Java para la búsqueda de correos electrónicos?

- **API unificada**: funciona con PDF, imágenes, archivos de Office y correos electrónicos utilizando los mismos patrones de código.

- **Optimizado para el rendimiento**: las operaciones de búsqueda se ejecutan en memoria sin necesidad de servicios externos. - **Gestión robusta**: Admite HTML y texto plano, archivos adjuntos e incluso correos electrónicos protegidos con contraseña.

- **Fácil integración**: Compatible con Maven/Gradle, con documentación clara y soporte activo.

## Requisitos previos

- **Java Development Kit (JDK)** 8 o posterior.

- **Maven** (o Gradle) para la gestión de dependencias.

- Un IDE como **IntelliJ IDEA** o **Eclipse**.

- Conocimientos básicos de sintaxis Java y formatos de archivo de correo electrónico (`.msg`, `.eml`).

## Configuración de GroupDocs.Watermark para Java
### Configuración de Maven
Añade el repositorio y la dependencia a tu `pom.xml`:

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

### Descarga directa
Alternativamente, puede descargar el archivo JAR más reciente desde [GroupDocs.Watermark para versiones de Java](https://releases.groupdocs.com/watermark/java/).

### Adquisición de licencia
- **Prueba gratuita:** Pruebe las funciones principales sin una clave de licencia.

- **Licencia temporal:** Solicite una clave por tiempo limitado para una evaluación extendida.

- **Licencia de pago:** Adquiera una licencia para uso ilimitado en producción.

#### Inicialización básica
```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.EmailLoadOptions;

EmailLoadOptions loadOptions = new EmailLoadOptions();
Watermarker watermarker = new Watermarker("input_email.msg", loadOptions);
```

## Guía de implementación

### Función 1: Búsqueda de texto en el cuerpo del correo electrónico

#### Descripción general
Configuraremos la API para escanear el **asunto**, el **cuerpo HTML** y el **cuerpo de texto sin formato** de un correo electrónico en busca de una palabra clave específica.

#### Paso 1: Definir las rutas del documento
```java
String inputDocumentPath = "YOUR_DOCUMENT_DIRECTORY/message.msg";
String outputDocumentPath = "YOUR_OUTPUT_DIRECTORY/output_message.msg";
```

#### Paso 2: Configurar las opciones de carga y la marca de agua
```java
EmailLoadOptions loadOptions = new EmailLoadOptions();
Watermarker watermarker = new Watermarker(inputDocumentPath, loadOptions);
```

#### Paso 3: Crear criterios de búsqueda
```java
import com.groupdocs.watermark.search.SearchCriteria;
import com.groupdocs.watermark.search.TextSearchCriteria;

SearchCriteria criteria = new TextSearchCriteria("test", false);
```

#### Paso 4: Especificar las ubicaciones de búsqueda
```java
watermarker.getSearchableObjects().setEmailSearchableObjects(
    EmailSearchableObjects.Subject |
    EmailSearchableObjects.HtmlBody | 
    EmailSearchableObjects.PlainTextBody);
```

#### Paso 5: Ejecutar la búsqueda y borrar las marcas de agua
```java
import com.groupdocs.watermark.search.PossibleWatermarkCollection;

PossibleWatermarkCollection watermarks = watermarker.search(criteria);
watermarks.clear();
```

#### Paso 6: Guardar los cambios
```java
watermarker.save(outputDocumentPath);
// Close the Watermarker instance to release resources
watermarker.close();
```

#### Consejos para la resolución de problemas
- **Resultados vacíos:** Verifique que la palabra clave aparezca realmente en las partes del correo electrónico seleccionadas.

- **Rendimiento:** Limite los objetos que se pueden buscar a solo aquellos que necesite (por ejemplo, Asunto + Cuerpo del mensaje) para acelerar el procesamiento de grandes lotes.

### Función 2: Opciones de carga de documentos de correo electrónico

#### Descripción general
`EmailLoadOptions` le permite controlar cómo se analiza el correo electrónico, lo cual es útil para mensajes cifrados o codificaciones personalizadas.

#### Paso 1: Configurar las opciones de carga
```java
EmailLoadOptions loadOptions = new EmailLoadOptions();
// Additional configurations can be added here.
```

#### Opciones de configuración clave
- **Protección con contraseña:** Configure `loadOptions.setPassword("tuContraseña")` para los archivos `.msg` cifrados.

- **Configuración de codificación:** Ajuste `loadOptions.setEncoding(Charset.forName("UTF-8"))` cuando trabaje con conjuntos de caracteres no estándar.

## Aplicaciones prácticas

- **Procesamiento automatizado de correo electrónico:** Analice masivamente los tickets de soporte entrantes en busca de palabras clave como "reembolso" o "error".

- **Verificaciones de cumplimiento legal:** Localice rápidamente términos confidenciales (p. ej., número de la seguridad social, números de tarjetas de crédito) en los archivos de correo corporativos.

- **Automatización de la atención al cliente:** Dirija los correos electrónicos según las frases detectadas al equipo de soporte adecuado.

## Consideraciones de rendimiento
- **Gestión de recursos:** Llame a `watermarker.close()` tan pronto como finalice el procesamiento para liberar recursos nativos.
- **Mejores prácticas de memoria:** Al gestionar miles de mensajes, procéselos en lotes y reutilice la instancia de `Watermarker` siempre que sea posible.

## Conclusión
Ahora dispone de un método sólido y listo para producción para **buscar** contenido de correo electrónico con GroupDocs.Watermark Java. La flexibilidad de la API le permite seleccionar partes específicas de un correo electrónico, eliminar marcas de agua no deseadas e integrar la lógica en flujos de trabajo más amplios.

### Próximos pasos
- Experimente con **múltiples criterios de búsqueda** (por ejemplo, combinar «factura» + «vencida»).

- Explore la **adición de marcas de agua** para marcar correos electrónicos que contengan datos confidenciales.

- Profundice en otros tipos de documentos (PDF, DOCX) utilizando el mismo flujo de trabajo de Watermarker.

## Preguntas frecuentes

**P1:** ¿Cómo puedo gestionar correos electrónicos cifrados con GroupDocs.Watermark?
**R1:** Utilice `EmailLoadOptions.setPassword("tuContraseña")` antes de crear la instancia de `Watermarker`.

**P2:** ¿Puedo buscar varias palabras clave a la vez?

**R2:** Sí, cree objetos `SearchCriteria` separados para cada palabra clave y combínelos con operadores lógicos (por ejemplo, `OrSearchCriteria`).

**P3:** ¿Es gratuito usar GroupDocs.Watermark Java?

**R3:** Hay una versión de prueba gratuita disponible para su evaluación. Para su uso en producción, se requiere una licencia de pago.

**P4:** ¿Cómo puedo gestionar grandes volúmenes de correos electrónicos de forma eficiente?

**R4:** Limite los objetos de búsqueda solo a los necesarios, procese los correos electrónicos en lotes y cierre siempre `Watermarker` para liberar recursos.

**P5:** ¿Dónde puedo encontrar ayuda o soporte adicional?
**A5:** Visita el [foro de GroupDocs](https://forum.groupdocs.com/c/watermark/10) para obtener ayuda de la comunidad o contacta directamente con el soporte de GroupDocs.

## Recursos
- **Documentación:** Consulta guías detalladas en la [Documentación de GroupDocs](https://docs.groupdocs.com/watermark/java/).

- **Referencia de la API:** Accede a los detalles técnicos en la [API de GroupDocs](https://apireference.groupdocs.com/watermark/java/).

--

**Última actualización:** 31/12/2025
**Probado con:** GroupDocs.Watermark 24.11 para Java
**Autor:** GroupDocs  

---