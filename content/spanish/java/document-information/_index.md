---
date: 2026-11-13
description: Aprenda cómo extraer metadatos, enumerar los formatos compatibles y obtener
  información del documento usando GroupDocs.Watermark para Java.
keywords:
- how to extract metadata
- list supported formats
- extract document metadata
- retrieve document info
- extract slide background
lastmod: 2026-11-13
og_description: Cómo extraer metadatos usando GroupDocs.Watermark para Java. Aprenda
  a enumerar los formatos compatibles, obtener información del documento y extraer
  fondos de diapositivas en minutos.
og_image_alt: Guide showing metadata extraction and format listing with GroupDocs.Watermark
  for Java
og_title: Cómo extraer metadatos con GroupDocs.Watermark para Java
schemas:
- author: GroupDocs
  dateModified: '2026-11-13'
  description: Learn how to extract metadata, list supported formats, and retrieve
    document information using GroupDocs.Watermark for Java.
  headline: How to extract metadata with GroupDocs.Watermark for Java
  type: TechArticle
- questions:
  - answer: Yes, provide the password when opening the document; the API will decrypt
      it in memory and then read the metadata.
    question: Can I extract metadata from password‑protected documents?
  - answer: The core extraction features are compatible with Android API 21+ when
      bundled as a standard JAR.
    question: Does the library work on Android?
  - answer: Use the `getCustomProperties()` method on the `DocumentInfo` object; it
      returns a map of key‑value pairs you can iterate over.
    question: How do I handle custom metadata fields?
  - answer: Wrap the extraction logic in a loop and reuse a single `Watermark` instance;
      the SDK is designed for high‑throughput scenarios.
    question: Is there a way to batch‑process many files?
  - answer: GroupDocs.Watermark offers perpetual, subscription, and temporary licenses;
      the temporary license is ideal for evaluation and CI pipelines.
    question: What licensing options are available?
  type: FAQPage
tags:
- metadata extraction
- GroupDocs.Watermark
- Java document processing
- supported formats
title: Cómo extraer metadatos con GroupDocs.Watermark para Java
type: docs
url: /es/java/document-information/
weight: 14
---

# Cómo extraer metadatos con GroupDocs.Watermark para Java

En esta guía descubrirá **cómo extraer metadatos** de una amplia gama de tipos de documentos usando GroupDocs.Watermark para Java. Ya sea que necesite leer el tipo de archivo, el recuento de páginas, los detalles del autor o propiedades personalizadas, la biblioteca le brinda acceso programático a esta información para que pueda tomar decisiones inteligentes sobre la colocación de marcas de agua, el enrutamiento de documentos o verificaciones de cumplimiento. El tutorial también muestra cómo enumerar los formatos compatibles, obtener datos de fondo de diapositivas y recuperar otras características útiles del documento.

## Respuestas rápidas
- **¿Puedo extraer metadatos de archivos PDF y Word?** Sí, la API lee metadatos de más de 70 formatos comunes.  
- **¿Necesito una licencia para desarrollo?** Una licencia temporal gratuita funciona para pruebas; se requiere una licencia completa para producción.  
- **¿Qué versión de Java se requiere?** Se admite Java 8 o superior.  
- **¿La biblioteca es segura para subprocesos?** Las clases principales de extracción están diseñadas para uso concurrente.  
- **¿Cuántos formatos se reconocen?** Se reconocen más de 70 formatos de entrada y salida de forma predeterminada.

## Qué es la extracción de metadatos?
La extracción de metadatos es el proceso de leer información incrustada—como autor, fecha de creación, recuento de páginas y propiedades personalizadas—de un archivo de documento sin alterar su contenido. Permite flujos de trabajo automatizados que dependen de los atributos del documento. Normalmente incluye propiedades como título, palabras clave y marcas de tiempo de modificación, que pueden aprovecharse para la indexación y la generación de informes de cumplimiento.

## ¿Por qué usar GroupDocs.Watermark para Java?
GroupDocs.Watermark para Java admite **más de 70 formatos de archivo**, incluidos PDF, DOCX, PPTX, XLSX y tipos de imagen, y puede procesar documentos de hasta 500 MB sin cargar todo el archivo en memoria. Su API devuelve los metadatos en un único objeto coherente, reduciendo la necesidad de analizadores específicos de formato y disminuyendo el tiempo de desarrollo hasta en un 40 %.

## Requisitos previos
- Java 8 o posterior instalado en su máquina de desarrollo.  
- Maven o Gradle para gestionar la dependencia `groupdocs-watermark`.  
- Un archivo de licencia temporal o completo de GroupDocs.Watermark.

## Cómo extraer metadatos paso a paso

### ¿Cómo obtener información básica del documento?
La clase `Watermark` representa un documento y brinda acceso a sus metadatos. El método `getDocumentInfo()` extrae el objeto de metadatos del documento cargado. Cargue el documento con la clase `Watermark`, luego llame a `getDocumentInfo()` para obtener un objeto que contiene el tipo de archivo, tamaño, recuento de páginas y fecha de creación. Esta única llamada devuelve todos los metadatos principales en menos de un segundo para archivos típicos de menos de 100 MB. El objeto `DocumentInfo` devuelto también incluye el autor del documento, la fecha de última modificación y cualquier propiedad personalizada incrustada, proporcionando una visión completa.

### ¿Cómo puedo enumerar todos los formatos de archivo compatibles?
La utilidad `SupportedFormats` proporciona un catálogo de todos los tipos de archivo que el SDK puede procesar. Utilice la utilidad `SupportedFormats` proporcionada por el SDK. Devuelve una colección de identificadores de formato que puede mostrar o validar antes de subir archivos, garantizando la compatibilidad y evitando errores en tiempo de ejecución. Cada entrada incluye el nombre del formato, la extensión de archivo típica y una breve descripción de sus capacidades, ayudando a los desarrolladores a validar entradas antes del procesamiento.

### ¿Cómo extraer detalles del fondo de diapositiva de un archivo PowerPoint?
`SlideInfo` es un objeto que describe las propiedades visuales de una diapositiva, como la imagen de fondo y sus dimensiones. `getSlides()` devuelve una colección de objetos `SlideInfo` para cada diapositiva de la presentación. El objeto `SlideInfo` expone las dimensiones de la imagen de fondo, el tamaño del archivo y la profundidad de color. Acceda a él a través de la colección `getSlides()`, luego itere sobre cada diapositiva para leer sus propiedades de fondo—útil para estilo dinámico o generación de miniaturas. Estos detalles pueden usarse para generar miniaturas, aplicar un estilo coherente o reemplazar fondos programáticamente en múltiples presentaciones.

## Problemas comunes y soluciones
- **Metadatos faltantes:** Algunos archivos antiguos pueden no contener propiedades estándar. En ese caso, habilite la bandera `extractCustomProperties` para extraer cualquier campo definido por el usuario.  
- **Los archivos grandes provocan tiempos de espera:** Aumente la configuración `maxMemory` del SDK o procese el documento en modo de transmisión para evitar cargar todo el archivo en RAM.  
- **Error de formato no compatible:** Verifique el formato contra la lista devuelta por `SupportedFormats` antes de intentar la extracción.

## Preguntas frecuentes

**P: ¿Puedo extraer metadatos de documentos protegidos con contraseña?**  
R: Sí, proporcione la contraseña al abrir el documento; la API lo descifrará en memoria y luego leerá los metadatos.

**P: ¿La biblioteca funciona en Android?**  
R: Las funciones principales de extracción son compatibles con Android API 21+ cuando se empaquetan como un JAR estándar.

**P: ¿Cómo manejo campos de metadatos personalizados?**  
R: Utilice el método `getCustomProperties()` del objeto `DocumentInfo`; devuelve un mapa de pares clave‑valor que puede iterar.

**P: ¿Existe una forma de procesar por lotes muchos archivos?**  
R: Encierre la lógica de extracción en un bucle y reutilice una única instancia de `Watermark`; el SDK está diseñado para escenarios de alto rendimiento.

**P: ¿Qué opciones de licencia están disponibles?**  
R: GroupDocs.Watermark ofrece licencias perpetuas, por suscripción y temporales; la licencia temporal es ideal para evaluación y pipelines de CI.

## Tutoriales disponibles

### [Extraer información del documento usando GroupDocs.Watermark para Java&#58; Guía completa](./extract-document-info-groupdocs-watermark-java/)
Aprenda a extraer eficientemente metadatos de documentos como tipo de archivo, recuento de páginas y tamaño usando GroupDocs.Watermark para Java. Esta guía cubre la configuración, la implementación y aplicaciones prácticas.

### [Extraer dimensiones de página PDF en Java usando GroupDocs.Watermark&#58; Guía completa](./get-pdf-page-dimensions-groupdocs-watermark-java/)
Aprenda a extraer dimensiones de página PDF con GroupDocs.Watermark para Java. Esta guía cubre la configuración, ejemplos de código y aplicaciones prácticas.

### [Extraer formas de documentos Word usando GroupDocs.Watermark en Java](./extract-shapes-word-docs-groupdocs-watermark-java/)
Aprenda a extraer y analizar formas de documentos Word usando GroupDocs.Watermark para Java, mejorando la automatización y manipulación de documentos.

### [Cómo extraer información del fondo de diapositivas usando GroupDocs.Watermark para Java](./groupdocs-watermark-java-extract-slide-backgrounds/)
Aprenda a extraer detalles del fondo de diapositivas, como dimensiones de la imagen y tamaño del archivo, usando GroupDocs.Watermark para Java. Perfecto para personalización, análisis o documentación.

### [Cómo enumerar formatos de archivo compatibles usando GroupDocs.Watermark para Java&#58; Guía completa](./groupdocs-watermark-java-list-supported-formats/)
Aprenda a enumerar eficientemente los formatos de archivo compatibles con GroupDocs.Watermark en Java, asegurando la compatibilidad entre varios tipos de documentos.

### [Cómo recuperar información del documento usando GroupDocs.Watermark para Java&#58; Guía paso a paso](./retrieve-document-info-groupdocs-watermark-java/)
Aprenda a recuperar eficientemente información del documento como tipo de archivo, recuento de páginas y tamaño usando GroupDocs.Watermark para Java. Siga nuestra guía detallada con ejemplos de código.

### [Cómo recuperar propiedades de sección en documentos Word usando GroupDocs.Watermark para Java](./groupdocs-java-word-section-properties-retrieval/)
Aprenda a recuperar y manipular eficientemente propiedades de sección en documentos Word usando GroupDocs.Watermark para Java. Perfecto para desarrolladores que buscan mejorar el manejo de documentos.

## Recursos adicionales
- [Documentación de GroupDocs.Watermark para Java](https://docs.groupdocs.com/watermark/java/)
- [Referencia de API de GroupDocs.Watermark para Java](https://reference.groupdocs.com/watermark/java/)
- [Descargar GroupDocs.Watermark para Java](https://releases.groupdocs.com/watermark/java/)
- [Foro de GroupDocs.Watermark](https://forum.groupdocs.com/c/watermark)
- [Soporte gratuito](https://forum.groupdocs.com/)
- [Licencia temporal](https://purchase.groupdocs.com/temporary-license/)

---

**Última actualización:** 2026-11-13  
**Probado con:** GroupDocs.Watermark 23.12 para Java  
**Autor:** GroupDocs

## Tutoriales relacionados

- [Cómo enumerar formatos de archivo compatibles usando GroupDocs.Watermark para Java: Guía completa](/watermark/java/document-information/groupdocs-watermark-java-list-supported-formats/)
- [Cómo recuperar información del documento usando GroupDocs.Watermark para Java: Guía paso a paso](/watermark/java/document-information/retrieve-document-info-groupdocs-watermark-java/)
- [Extraer información del documento usando GroupDocs.Watermark para Java: Guía completa](/watermark/java/document-information/extract-document-info-groupdocs-watermark-java/)