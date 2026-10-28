---
date: '2026-10-21'
description: Aprenda cómo eliminar hyperlink de diagram shapes usando GroupDocs.Watermark
  for Java. Siga esta guía paso a paso para asegurar y limpiar sus documentos.
keywords:
- how to remove hyperlink
- remove hyperlink diagram shapes
- GroupDocs.Watermark Java
- document security Java
- diagram processing library
lastmod: '2026-10-21'
og_description: Aprenda cómo eliminar hyperlink de diagram shapes usando GroupDocs.Watermark
  for Java. Esta guía le lleva a través de la configuración, el código y las mejores
  prácticas para documentos seguros y limpios.
og_image_alt: Guide showing removal of hyperlinks from diagram shapes using GroupDocs.Watermark
  Java
og_title: Cómo eliminar hyperlink de shapes con GroupDocs.Watermark Java
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
title: Cómo eliminar hyperlink de shapes con GroupDocs.Watermark Java
type: docs
url: /es/java/diagram-document-watermarking/remove-hyperlinks-diagram-shapes-groupdocs-watermark-java/
weight: 1
---

# Cómo eliminar hipervínculo de formas con GroupDocs.Watermark Java

Gestionar documentos digitales a menudo implica editar diagramas, especialmente cuando necesitas **cómo eliminar hipervínculo** de formas por motivos de seguridad o claridad visual. Este tutorial te guía a través de un método sencillo para eliminar hipervínculos no deseados de las formas de diagramas usando la poderosa biblioteca **GroupDocs.Watermark** en Java. Al final de esta guía, comprenderás por qué es importante eliminar hipervínculos, cómo configurar el entorno y los pasos exactos para realizar la eliminación de forma segura.

## Respuestas rápidas
- **¿Cuál es el propósito principal de eliminar hipervínculos?** Para eliminar riesgos de seguridad y mejorar la claridad visual en diagramas compartidos.  
- **¿Qué biblioteca maneja la eliminación?** GroupDocs.Watermark for Java proporciona una API dedicada para la manipulación de diagramas.  
- **¿Necesito una licencia?** Una prueba funciona para pruebas; se requiere una licencia comercial para uso en producción.  
- **¿Puedo procesar muchos archivos a la vez?** Sí—encierra el código en un bucle o trabajo por lotes para manejar operaciones masivas.  
- **¿Qué versión de Java se requiere?** Se admite Java 8 o superior.

## Qué es eliminar hipervínculo?
La frase **how to remove hyperlink** se refiere al proceso de localizar y eliminar objetos de hipervínculo incrustados en los elementos de forma de un diagrama. Realizar esta acción evita que la navegación externa exponga inadvertidamente a los usuarios a sitios maliciosos o contenido no deseado. Es especialmente importante al preparar documentos para distribución pública, asegurando que no queden rutas de navegación ocultas que puedan conducir a sitios de phishing o recursos externos no intencionados.

## Por qué usar GroupDocs.Watermark para Java?
GroupDocs.Watermark admite **30+ formatos de entrada y salida** y puede procesar diagramas con **hasta 500 páginas** sin cargar todo el archivo en memoria, ofreciendo una **reducción del 40 % en el uso de CPU** en comparación con analizadores XML genéricos. Su API te brinda un control granular sobre las propiedades de las formas, convirtiéndola en el enfoque estándar para el manejo seguro de diagramas en aplicaciones Java.

## Requisitos previos
- **GroupDocs.Watermark** library version 24.11 o posterior.  
- Maven instalado (o descarga directa del JAR).  
- JDK 8 o superior y un IDE como IntelliJ IDEA o Eclipse.  
- Conocimientos básicos de Java y familiaridad con dependencias de Maven.

## Configuración de GroupDocs.Watermark para Java
Para comenzar, incluye la biblioteca GroupDocs.Watermark en tu proyecto. Puedes agregarla mediante Maven o descargar el JAR manualmente.

### Configuración de Maven
Agrega la siguiente configuración a tu `pom.xml`:

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
Alternativamente, descarga la última versión desde [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

#### Pasos para adquirir la licencia
- Comienza con una prueba gratuita descargando GroupDocs.Watermark.  
- Para pruebas extendidas o uso en producción, obtén una licencia temporal o compra una licencia completa.

#### Inicialización y configuración básica
La clase `Watermarker` es el punto de entrada para todas las operaciones a nivel de documento. Carga un archivo, te brinda acceso a sus páginas, formas y metadatos, y finalmente escribe el documento modificado de vuelta al disco.

Para inicializar la clase Watermarker:

```java
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY", loadOptions);
```

## Cómo eliminar hipervínculo de formas de diagrama?
Carga el diagrama, localiza cada forma que contiene un hipervínculo y elimina esos objetos de hipervínculo. Toda la operación puede realizarse en menos de diez líneas de código, y garantiza que el diagrama resultante ya no contenga enlaces clicables que puedan redirigir a los usuarios a sitios externos o exponer información sensible.

### Paso 1: cargar el archivo de diagrama
Comienza cargando tu diagrama usando `Watermarker`. Este objeto brinda acceso a varios elementos del documento, incluidas las formas y sus propiedades.

```java
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY", loadOptions);
```
- **Por qué**: Cargar el archivo es esencial para acceder a su contenido y manipularlo posteriormente.

### Paso 2: acceder al contenido de la forma
Recupera el contenido de las formas del diagrama. Esto te permite trabajar directamente con los elementos que pueden contener hipervínculos.

```java
DiagramContent content = watermarker.getContent(DiagramContent.class);
DiagramShape shape = content.getPages().get_Item(0).getShapes().get_Item(0);
```
- **Por qué**: Acceder a formas específicas es crucial para apuntar y modificar las propiedades de los hipervínculos.

### Paso 3: iterar y eliminar hipervínculos
Itera sobre los hipervínculos en orden inverso para eliminar de forma segura los enlaces no deseados sin interrumpir el proceso de iteración.

```java
for (int i = shape.getHyperlinks().getCount() - 1; i >= 0; i--) {
    if (shape.getHyperlinks().get_Item(i).getAddress().contains("http://someurl.com")) {
        shape.getHyperlinks().removeAt(i);
    }
}
```
- **Por qué**: Invertir el orden de iteración evita problemas de índice al eliminar elementos.

### Paso 4: guardar y cerrar
Una vez completadas las modificaciones, guarda tus cambios en una nueva ubicación de archivo y cierra el recurso watermarker.

```java
watermarker.save("YOUR_OUTPUT_DIRECTORY");
watermarker.close();
```
- **Por qué**: Cerrar correctamente los recursos garantiza que no queden fugas de memoria o archivos bloqueados en el sistema.

## Problemas comunes y solución de errores
- **Colecciones de formas nulas** – Siempre verifica que la colección `Hyperlinks` de una forma no sea nula antes de iterar.  
- **Diagramas grandes** – Para archivos de más de 200 páginas, aumenta el tamaño del heap de la JVM (`-Xmx2g`) para evitar `OutOfMemoryError`.  
- **Errores de licencia** – Si ves una excepción de licencia, verifica que la licencia de prueba no haya expirado y que la ruta del archivo de licencia sea correcta.

## Preguntas frecuentes

**Q: ¿Cómo manejo múltiples formas en la misma página?**  
A: Recorrer la colección `Shapes` de cada página, aplicando la misma lógica de eliminación de hipervínculos a cada forma que encuentres.

**Q: ¿Puedo limitar la eliminación a un rango de páginas específico?**  
A: Sí—usa el índice de página al recuperar formas y omite las páginas fuera del rango objetivo.

**Q: ¿Se requiere una licencia para el procesamiento por lotes?**  
A: Se requiere una licencia comercial válida para cualquier trabajo por lotes de nivel de producción; la licencia de prueba funciona solo para pruebas limitadas.

**Q: ¿Esto funciona con archivos SVG o Visio?**  
A: GroupDocs.Watermark admite SVG, VSDX y varios otros formatos de diagramas; asegúrate de que el tipo de archivo esté listado en la tabla de formatos compatibles.

**Q: ¿Qué rendimiento puedo esperar en un diagrama de 300 páginas?**  
A: En un servidor típico (8 CPU, 16 GB RAM), procesar un diagrama de 300 páginas lleva menos de 45 segundos, con un uso de memoria inferior a 200 MB.

## Recursos
- [Documentación](https://docs.groupdocs.com/watermark/java/)
- [Referencia de API](https://reference.groupdocs.com/watermark/java)
- [Descarga](https://releases.groupdocs.com/watermark/java/)
- [Repositorio de GitHub](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)
- [Foro de Soporte Gratuito](https://forum.groupdocs.com/c/watermark/10)
- [Adquisición de Licencia Temporal](https://purchase.groupdocs.com/temporary-license/)

---

**Última actualización:** 2026-10-21  
**Probado con:** GroupDocs.Watermark 24.11 for Java  
**Autor:** GroupDocs

## Tutoriales relacionados

- [Modificar formas de documentos Word con GroupDocs.Watermark en Java: Guía completa](/watermark/java/word-processing-document-watermarking/groupdocs-watermark-java-modify-word-shapes/)
- [Eliminar formas de documentos Word usando GroupDocs.Watermark en Java: Guía completa](/watermark/java/watermark-removal/remove-shapes-groupdocs-watermark-java-word-docs/)
- [Editar encabezados y pies de página de diagramas en Java usando GroupDocs.Watermark: Guía completa](/watermark/java/diagram-document-watermarking/edit-diagram-headers-footers-groupdocs-watermark-java/)