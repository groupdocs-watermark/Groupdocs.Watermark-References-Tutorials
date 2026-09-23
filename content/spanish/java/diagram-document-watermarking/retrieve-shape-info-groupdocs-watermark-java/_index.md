---
date: '2026-02-13'
description: Aprende cómo extraer formas y obtener la imagen de una forma con GroupDocs.Watermark
  para Java, recuperando información detallada del diagrama de manera eficiente.
keywords:
- extract shape information Java
- GroupDocs.Watermark diagram processing
- Java diagram manipulation
title: Cómo extraer formas de diagramas usando GroupDocs.Watermark en Java
type: docs
url: /es/java/diagram-document-watermarking/retrieve-shape-info-groupdocs-watermark-java/
weight: 1
---

# Cómo extraer formas de diagramas usando GroupDocs.Watermark en Java

Cuando necesitas **cómo extraer formas** de un diagrama estilo Visio de forma programática, la biblioteca GroupDocs.Watermark te ofrece una manera limpia, centrada en Java, de obtener cada detalle: dimensiones, posiciones, imágenes incrustadas e incluso el texto dentro de cada forma. En este tutorial verás exactamente **cómo extraer formas**, por qué es importante y código paso a paso que puedes copiar en tu proyecto.

## Quick Answers
- **¿Qué biblioteca maneja la extracción de formas?** GroupDocs.Watermark for Java  
- **¿Qué versión de Java se requiere?** JDK 8 o superior  
- **¿Puedo obtener datos de imagen de una forma?** Sí – usa `shape.getImage()`  
- **¿Se puede acceder al texto dentro de una forma?** Absolutamente, mediante `shape.getText()`  
- **¿Necesito una licencia para producción?** Se requiere una licencia válida de GroupDocs.Watermark  

## Introduction

Gestionar diagramas complejos a menudo requiere acceder a información detallada sobre sus componentes, como formas e imágenes. Si alguna vez has necesitado recuperar programáticamente datos como dimensiones, posiciones o texto asociado a las formas de un diagrama usando Java, este tutorial es para ti. Aprovechar el poder de la biblioteca GroupDocs.Watermark puede simplificar este proceso en una aplicación Java. En esta guía, recorreremos **cómo extraer formas** de un archivo de diagrama y también te mostraremos cómo **extraer imagen de una forma** y **extraer texto de una forma**.

## What is “how to extract shapes”?

Extraer formas significa leer los objetos internos del diagrama (páginas, formas, imágenes, texto) para que puedas analizarlos, transformarlos o reutilizarlos en otras aplicaciones—perfecto para automatización, generación de informes o integración con herramientas CAD.

## Why use GroupDocs.Watermark for shape extraction?

- **Compatibilidad total de formatos** – funciona con VSDX, VDX y muchos otros tipos de diagramas.  
- **Modelo de objetos rico** – brinda acceso directo a la geometría de la forma, imágenes y texto.  
- **Sin dependencias externas** – puro Java, fácil de integrar en proyectos Maven.  

## Prerequisites

- **GroupDocs.Watermark for Java** (versión 24.11 o posterior)  
- Java Development Kit (JDK) 8 o superior  
- Maven para la gestión de dependencias  
- Un IDE como IntelliJ IDEA o Eclipse  

## Setting Up GroupDocs.Watermark for Java

Agrega la biblioteca a tu `pom.xml` de Maven:

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

También puedes descargar los binarios más recientes desde [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

### License Acquisition Steps
- **Prueba gratuita:** Descarga un paquete de prueba para evaluar la API.  
- **Licencia temporal:** Solicita una clave temporal para pruebas extendidas.  
- **Compra:** Obtén una licencia completa para uso en producción.

### Basic Initialization and Setup

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.contents.DiagramContent;
import com.groupdocs.watermark.options.DiagramLoadOptions;

DiagramLoadOptions diagramLoadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/diagram.vsdx", diagramLoadOptions);
```

## How to Extract Shapes – Implementation Guide

### Load and Retrieve Content

```java
// Create load options if necessary
DiagramLoadOptions diagramLoadOptions = new DiagramLoadOptions();
// Initialize watermarker with your document path
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/diagram.vsdx", diagramLoadOptions);
```

```java
// Retrieve content of the diagram file as a DiagramContent object
DiagramContent content = watermarker.getContent(DiagramContent.class);
```

### Iterate Through Shapes

```java
for (DiagramPage page : content.getPages()) {
    // Process each shape in the current page
}
```

```java
for (DiagramShape shape : page.getShapes()) {
    if (shape.getImage() != null) {
        // Access and print image-related properties
        System.out.println("Image Width: " + shape.getImage().getWidth());
        System.out.println("Image Height: " + shape.getImage().getHeight());
        System.out.println("Image Size: " + shape.getImage().getData().length);
    }
    
    // Print other shape attributes
    System.out.println("Shape Name: " + shape.getName());
    System.out.println("X Position: " + shape.getX());
    System.out.println("Y Position: " + shape.getY());
    System.out.println("Width: " + shape.getWidth());
    System.out.println("Height: " + shape.getHeight());
    System.out.println("Rotation Angle: " + shape.getRotationAngle());
    System.out.println("Text: " + (shape.getText() != null ? shape.getText() : "No text"));
    System.out.println("Shape ID: " + shape.getId());
}
```

### Cómo extraer imagen de una forma

La llamada `shape.getImage()` devuelve un objeto que contiene el mapa de bits sin procesar, sus dimensiones y el arreglo de bytes. Usa las propiedades mostradas arriba para almacenar la imagen en disco o alimentarla a otro pipeline de procesamiento.

### Cómo extraer texto de una forma

El método `shape.getText()` devuelve el texto plano dentro de la forma. Si la forma no contiene texto, el método devuelve `null`. El bucle de ejemplo ya imprime el texto, y puedes manipularlo más, por ejemplo, construyendo un índice de todas las etiquetas de forma.

## Troubleshooting Tips
- Verifica la ruta del archivo y los permisos de lectura.  
- Asegúrate de estar usando un formato de diagrama compatible (VSDX, VDX, etc.).  
- Si una forma aparece sin los datos esperados, revisa las notas de la versión de la biblioteca para peculiaridades específicas del formato.

## Practical Applications

1. **Análisis de diagramas:** Audita automáticamente los diagramas para cumplimiento verificando tamaños de formas o etiquetas faltantes.  
2. **Visualización de datos:** Alimenta las dimensiones extraídas a un panel de informes para visualizar la densidad del diseño.  
3. **Integración CAD:** Combina los datos de las formas con APIs CAD para sincronizar especificaciones de diseño entre herramientas.  

## Performance Considerations

- **Cerrar recursos:** Llama a `watermarker.close()` cuando termines para liberar recursos nativos.  
- **Gestión de memoria:** Los diagramas grandes pueden consumir una cantidad significativa de heap; monitorea la memoria y aumenta `-Xmx` si es necesario.  
- **Procesamiento por lotes:** Procesa archivos en lotes y reutiliza una única instancia de `Watermarker` cuando sea posible.

## Conclusion

Al seguir esta guía ahora sabes **cómo extraer formas**, cómo **extraer imagen de una forma**, y cómo **extraer texto de una forma** usando GroupDocs.Watermark para Java. Estas técnicas abren la puerta al análisis automatizado de diagramas, generación de informes e integración con otros sistemas de ingeniería. Como siguiente paso, explora la API completa revisando su [documentation](https://docs.groupdocs.com/watermark/java/) y prueba combinar la extracción de formas con lógica de negocio personalizada.

## FAQ Section

1. **¿Qué es GroupDocs.Watermark?**  
   - Una biblioteca Java integral diseñada para aplicar marcas de agua y extraer información de varios formatos de documentos, incluidos diagramas.  

2. **¿Puedo usar esta biblioteca para procesar todo tipo de archivos de diagramas?**  
   - Sí, pero asegúrate de que el formato de archivo sea compatible revisando la [API Reference](https://reference.groupdocs.com/watermark/java/).  

3. **¿Cómo extraigo dimensiones y posiciones de las formas de un diagrama usando Java y GroupDocs.Watermark?**  
   - Carga el diagrama, accede a `DiagramContent`, luego itera las formas para obtener propiedades como ancho, alto, X y Y.  

4. **¿Puede GroupDocs.Watermark extraer imágenes incrustadas en formas de diagramas con Java?**  
   - Sí, proporciona métodos para acceder a los datos de imagen dentro de las formas, incluido el tamaño y los datos de píxeles, útiles para análisis o modificación.  

5. **¿Cuáles son los requisitos previos para extraer información de formas de diagramas en Java?**  
   - Java JDK 8+, configuración de Maven, biblioteca GroupDocs.Watermark (24.11+), y conocimientos básicos de Java son esenciales para la implementación.  

---

**Última actualización:** 2026-02-13  
**Probado con:** GroupDocs.Watermark 24.11 for Java  
**Autor:** GroupDocs