---
date: '2026-02-05'
description: Aprende cómo extraer formas de documentos Word usando GroupDocs.Watermark
  para Java, incluyendo cómo cargar un documento Word en Java y manipular los datos
  de las formas.
keywords:
- GroupDocs.Watermark
- extract shapes from Word documents
- Java document manipulation
title: Cómo extraer formas de documentos Word con GroupDocs.Watermark Java
type: docs
url: /es/java/document-information/extract-shapes-word-docs-groupdocs-watermark-java/
weight: 1
---

# Cómo extraer formas de documentos Word usando GroupDocs.Watermark en Java

En este tutorial descubrirá **cómo extraer formas** de documentos Word con la biblioteca GroupDocs.Watermark para Java. Ya sea que necesite analizar diagramas, extraer imágenes incrustadas o automatizar la generación de informes, extraer los metadatos de las formas le brinda el control para crear pipelines de procesamiento de documentos más inteligentes. Recorreremos la configuración de la biblioteca, la carga de un documento Word y la obtención de información detallada de las formas, todo con código Java claro y paso a paso.

## Respuestas rápidas
- **¿Qué significa “extraer formas”?** Recuperar metadatos (tipo, tamaño, posición, texto, imágenes) de cada objeto de dibujo en un archivo Word.  
- **¿Qué biblioteca maneja esto?** GroupDocs.Watermark para Java.  
- **¿Necesito una licencia?** Una versión de prueba funciona para desarrollo; una licencia completa elimina los límites de uso.  
- **¿Puedo también obtener imágenes de las formas?** Sí – la API expone los bytes de la imagen para las formas de tipo picture.  
- **¿Qué versión de Java se requiere?** JDK 8 o superior.

## ¿Qué es “Cómo extraer formas” en el contexto de documentos Word?
Extraer formas significa acceder programáticamente a cada elemento de dibujo — imágenes, WordArt, auto‑formas, gráficos e incluso formas incrustadas en encabezados o pies de página. Esta información puede usarse para validación, migración o análisis basados en contenido.

## ¿Por qué usar GroupDocs.Watermark para Java?
GroupDocs.Watermark proporciona una API de alto nivel y eficiente en memoria que abstrae la complejidad del formato Office Open XML subyacente. Le permite:
- Cargar documentos rápidamente (`WordProcessingLoadOptions`).  
- Recorrer secciones y formas sin lidiar con XML de bajo nivel.  
- Recuperar datos de imagen, texto, alineación y rotación en una sola llamada.  
- Integrarse sin problemas en servicios Java existentes o micro‑servicios.

## Requisitos previos
- **Java Development Kit (JDK)** 8 o superior.  
- **IDE** como IntelliJ IDEA o Eclipse.  
- Conocimientos básicos de Java I/O.  
- Acceso a una licencia o prueba de **GroupDocs.Watermark para Java**.

## Configuración de GroupDocs.Watermark para Java
Integre la biblioteca mediante Maven o una descarga directa.

### Usando Maven
Agregue el repositorio y la dependencia a su `pom.xml`:

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
Alternativamente, descargue el JAR más reciente desde [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

### Obtención de licencia
Una prueba gratuita es suficiente para pruebas. Para producción, solicite una licencia permanente para desbloquear todas las funciones.

## Guía de implementación
Dividiremos la implementación en dos pasos claros: **cargar el documento Word** y **extraer información de las formas**.

### Paso 1: Cargar un documento Word (load word document java)
Primero, configure las opciones de carga y cree una instancia de `Watermarker`. Esto prepara el documento para una inspección posterior.

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.WordProcessingLoadOptions;

public void loadDocument() {
    // Configure load options for loading a Word document
    WordProcessingLoadOptions loadOptions = new WordProcessingLoadOptions();
    
    // Create an instance of Watermarker with the specified document and load options
    Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/document.docx", loadOptions);
    
    // Close the watermarker to release resources
    watermarker.close();
}
```

> **Consejo profesional:** Mantenga la instancia de `Watermarker` con el alcance más limitado posible; cerrarla rápidamente libera recursos nativos y evita fugas de memoria.

### Paso 2: Extraer información de las formas (extract images from shapes)
Ahora extraeremos los detalles de cada forma, incluidas las imágenes incrustadas. El código recorre cada sección y cada forma, imprimiendo metadatos útiles.

```java
import com.groupdocs.watermark.contents.WordProcessingContent;

public void extractShapeInformation() {
    // Load the Word document as configured previously
    WordProcessingLoadOptions loadOptions = new WordProcessingLoadOptions();
    Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/document.docx", loadOptions);

    // Obtain WordProcessingContent from the watermarker
    WordProcessingContent content = watermarker.getContent(WordProcessingContent.class);

    // Iterate over each section in the document's content
    for (var section : content.getSections()) {
        // Iterate over each shape within the current section
        for (var shape : section.getShapes()) {
            // Check if the shape is part of a header or footer
            if (shape.getHeaderFooter() != null) {
                System.out.println("In header/footer");
            }
            
            // Output details about each shape, such as type and dimensions
            System.out.println(shape.getShapeType());
            System.out.println(shape.getWidth());
            System.out.println(shape.getHeight());
            System.out.println(shape.isWordArt());
            System.out.println(shape.getRotateAngle());
            System.out.println(shape.getAlternativeText());
            System.out.println(shape.getName());
            System.out.println(shape.getX());
            System.out.println(shape.getY());
            System.out.println(shape.getText());

            // If the shape contains an image, output its details
            if (shape.getImage() != null) {
                System.out.println(shape.getImage().getWidth());
                System.out.println(shape.getImage().getHeight());
                System.out.println(shape.getImage().getBytes().length);
            }
            
            // Output alignment information of the shape
            System.out.println(shape.getHorizontalAlignment());
            System.out.println(shape.getVerticalAlignment());
            System.out.println(shape.getRelativeHorizontalPosition());
            System.out.println(shape.getRelativeVerticalPosition());
        }
    }

    // Close the watermarker to release resources
    watermarker.close();
}
```

**Qué hace este código:**  
- Obtiene el **tipo** de cada forma (p. ej., picture, WordArt).  
- Imprime los valores de **tamaño**, **posición** y **rotación**.  
- Muestra el **texto alternativo** y el **nombre**, útiles para verificaciones de accesibilidad.  
- Si la forma contiene una imagen, imprime las **dimensiones en píxeles** y el **tamaño en bytes** de la imagen — perfecto para extraer imágenes de formas.  

### Errores comunes y cómo solucionarlos
| Problema | Causa | Solución |
|----------|-------|----------|
| `FileNotFoundException` | Ruta de archivo incorrecta o permisos faltantes | Verifique la ruta absoluta/relativa y asegúrese de que el archivo sea legible. |
| Null `shape.getImage()` | La forma no es una imagen (p. ej., auto‑shape) | Proteja con `if (shape.getImage() != null)` como se muestra. |
| Alto consumo de memoria en documentos grandes | Cargar todo el documento de una vez | Procese secciones una a la vez o aumente el heap de JVM (`-Xmx`). |
| Faltan formas en encabezado/pie de página | No se verifica `shape.getHeaderFooter()` | El ejemplo ya registra cuando una forma pertenece a un encabezado/pie de página. |

## Aplicaciones prácticas
1. **Generación automática de informes** – Extraiga gráficos y diagramas para incrustarlos en PDFs posteriores.  
2. **Auditoría de cumplimiento** – Verifique que todas las formas contengan texto alternativo apropiado para accesibilidad.  
3. **Migración de contenido** – Exporte imágenes incrustadas de archivos Word heredados a un sistema de gestión de activos digitales.  

## Consideraciones de rendimiento
- **Liberar recursos**: Siempre llame a `watermarker.close()` en un bloque `finally` o use try‑with‑resources si envuelve la API.  
- **Procesamiento por fragmentos**: Para documentos que superen los 50 MB, considere procesar cada sección por separado para mantener bajo el consumo de memoria.  
- **Seguridad en hilos**: Las instancias de `Watermarker` no son seguras para hilos; cree una nueva instancia por hilo.

## Conclusión
Ahora sabe **cómo extraer formas** de documentos Word usando GroupDocs.Watermark para Java, desde la carga del archivo hasta la lectura de los metadatos de cada forma y los datos de imágenes incrustadas. Esta capacidad abre puertas a análisis avanzados de documentos, pipelines de contenido automatizados y validación de accesibilidad.

### Próximos pasos
- Experimente modificando propiedades de las formas (p. ej., cambiar tamaño o reposicionar).  
- Combine este enfoque con **GroupDocs.Parser** para extraer el texto circundante.  
- Integre la lógica de extracción en un servicio REST para procesamiento bajo demanda.

## Sección de preguntas frecuentes
**Q: ¿Qué es GroupDocs.Watermark para Java?**  
A: Es una biblioteca integral diseñada para gestionar marcas de agua y contenido de documentos en varios formatos, permitiendo tareas como extracción de formas, recuperación de imágenes y manipulación de texto.

**Q: ¿Puedo extraer imágenes de las formas sin una licencia?**  
A: La versión de prueba permite la extracción, pero una licencia completa elimina los límites de uso y permite el despliegue comercial.

**Q: ¿Esto funciona con archivos `.doc` (binarios)?**  
A: Sí, la API soporta tanto formatos `.docx` como los legados `.doc`.

**Q: ¿Cómo manejo documentos protegidos con contraseña?**  
A: Proporcione la contraseña mediante `WordProcessingLoadOptions.setPassword("yourPassword")` antes de crear el `Watermarker`.

**Q: ¿Hay una forma de exportar los datos de las formas extraídas a JSON?**  
A: Puede mapear los valores impresos a un POJO y usar cualquier biblioteca JSON (p. ej., Jackson) para serializar la colección.

---

**Última actualización:** 2026-02-05  
**Probado con:** GroupDocs.Watermark 24.11 para Java  
**Autor:** GroupDocs