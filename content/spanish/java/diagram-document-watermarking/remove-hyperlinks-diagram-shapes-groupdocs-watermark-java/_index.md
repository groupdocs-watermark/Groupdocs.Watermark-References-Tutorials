---
date: '2026-08-25'
description: Aprenda a editar archivos de diagramas y eliminar hipervínculos usando
  GroupDocs.Watermark para Java. Proteja sus diagramas rápidamente con una guía paso
  a paso.
keywords:
- how to edit diagram
- remove hyperlinks diagram shapes
- GroupDocs.Watermark Java
lastmod: '2026-08-25'
og_description: Aprenda a editar archivos de diagramas y eliminar hipervínculos usando
  GroupDocs.Watermark para Java. Siga pasos claros para proteger sus documentos.
og_image_alt: Guide showing how to edit diagram and remove hyperlinks using GroupDocs.Watermark
  Java
og_title: Cómo editar diagramas y eliminar hipervínculos con Java
tags:
- edit diagram
- remove hyperlinks
- GroupDocs.Watermark
- Java document processing
- diagram security
title: Cómo editar diagramas y eliminar hipervínculos con Java
type: docs
url: /es/java/diagram-document-watermarking/remove-hyperlinks-diagram-shapes-groupdocs-watermark-java/
weight: 1
---

# Cómo editar diagramas y eliminar hipervínculos con Java  

Gestionar documentos digitales a menudo implica editar diagramas, especialmente cuando necesitas **edit diagram** archivos para eliminar hipervínculos por motivos de seguridad o claridad visual. Este tutorial te muestra exactamente cómo editar archivos de diagramas y eliminar los hipervínculos no deseados de las formas del diagrama usando la poderosa biblioteca **GroupDocs.Watermark** para Java. Al final de esta guía tendrás un diagrama limpio, sin enlaces, listo para distribuir.  

## Respuestas rápidas  
- **¿Cuál es el objetivo principal?** Eliminar todos los hipervínculos de las formas del diagrama para mejorar la seguridad y la presentación.  
- **¿Qué biblioteca se requiere?** GroupDocs.Watermark for Java, version 24.11 or newer.  
- **¿Necesito una licencia?** Una prueba gratuita funciona para pruebas; se requiere una licencia comercial para producción.  
- **¿Puedo procesar muchos archivos a la vez?** Sí – el mismo código puede colocarse dentro de un bucle para manejar lotes.  
- **¿Qué versión de Java es compatible?** Java 8 o superior (se recomienda Java 11).  

## Qué es “how to edit diagram”?  
**How to edit diagram** se refiere al proceso de abrir programáticamente un archivo de diagrama, modificar sus elementos internos (como formas, texto o hipervínculos) y guardar el resultado. Usando GroupDocs.Watermark puedes editar archivos de diagramas sin necesitar la herramienta de autoría original.  

## Por qué usar GroupDocs.Watermark para Java?  
GroupDocs.Watermark soporta **más de 30 formatos de diagramas e imágenes** (incluidos VSDX, SVG y WMF) y puede procesar archivos de hasta **500 MB** sin cargar todo el documento en memoria, ofreciendo una velocidad de procesamiento **un 20 % más rápida** en comparación con muchos competidores.  

## Requisitos previos  
- **GroupDocs.Watermark** versión 24.11 o posterior.  
- Maven instalado (o los archivos JAR si prefieres configuración manual).  
- Java Development Kit 8 o más reciente y un IDE como IntelliJ IDEA o Eclipse.  

### Bibliotecas requeridas, versiones y dependencias  
- GroupDocs.Watermark 24.11+  
- Maven 3.6+ (si utilizas el enfoque Maven)  

### Requisitos de configuración del entorno  
Asegúrate de que el directorio `bin` del JDK esté en tu `PATH` y de que tu IDE apunte a la versión correcta del JDK.  

### Prerrequisitos de conocimientos  
Debes estar cómodo con la sintaxis básica de Java, la gestión de dependencias con Maven y las operaciones de E/S de archivos.  

## Cómo configurar GroupDocs.Watermark para Java?  
La clase `Watermarker` proporciona el punto de entrada de la API para cargar y modificar documentos.  
Para comenzar a usar GroupDocs.Watermark, agrega sus coordenadas Maven a tu `pom.xml` del proyecto. Esto descarga la biblioteca y sus dependencias, permitiéndote instanciar la clase Watermarker y trabajar con archivos de diagramas directamente desde código Java. Luego puedes configurar la licencia y establecer opciones de salida antes de procesar cualquier documento.  

Agrega la dependencia de GroupDocs.Watermark a tu `pom.xml`.  

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

Si prefieres no usar Maven, descarga el JAR más reciente desde la página oficial de lanzamientos.  

[GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/)  

#### Pasos para adquirir la licencia  
- Comienza con una prueba gratuita para evaluar la API.  
- Para producción, obtén una licencia temporal o permanente del portal del proveedor.  

#### Inicialización y configuración básicas  
La clase `Watermarker` es el punto de entrada para todas las operaciones de procesamiento de documentos.  

```java
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY", loadOptions);
```  

## Cómo editar diagramas y eliminar hipervínculos con GroupDocs.Watermark?  
La clase `Watermarker` proporciona el punto de entrada de la API para cargar y modificar documentos.  
Primero, carga el archivo de diagrama en una instancia de Watermarker. Luego recupera la colección de formas, identifica aquellas que contienen objetos de hipervínculo y recorre la colección en orden inverso para eliminar de forma segura cada enlace sin afectar la indexación de la colección. Esto garantiza que todas las URL incrustadas se eliminen mientras se preserva la integridad visual del diagrama.  

```java
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY", loadOptions);
```  

- **Por qué este paso es importante**: Cargar el archivo te brinda acceso programático a cada forma y sus propiedades asociadas.  

## Cómo acceder al contenido de la forma en un diagrama?  
El objeto `DiagramShape` representa una forma individual dentro de un diagrama, exponiendo sus propiedades y metadatos adjuntos.  
Después de cargar el diagrama, llama a `getShapes()` en el Watermarker para obtener una lista de objetos `DiagramShape`. Cada forma puede inspeccionarse para colecciones de hipervínculos, lo que permite apuntar con precisión los enlaces para su eliminación o modificación. También puedes leer el texto de la forma, colores y geometría si se requieren ajustes adicionales.  

```java
DiagramContent content = watermarker.getContent(DiagramContent.class);
DiagramShape shape = content.getPages().get_Item(0).getShapes().get_Item(0);
```  

- **Por qué este paso es importante**: Apuntar a la forma exacta garantiza que solo elimines los enlaces no deseados sin afectar otros elementos visuales.  

## Cómo iterar y eliminar hipervínculos de forma segura?  
El método `removeHyperlink(int index)` elimina un hipervínculo en la posición especificada dentro de la colección de hipervínculos de una forma.  
Itera sobre la lista de hipervínculos desde el último índice hasta cero. Este bucle inverso evita el desplazamiento de índices que ocurre cuando se eliminan elementos, garantizando que cada hipervínculo se procese sin omisiones. Después de la eliminación, puedes actualizar el estado de la forma o continuar con la siguiente forma en el diagrama.  

```java
for (int i = shape.getHyperlinks().getCount() - 1; i >= 0; i--) {
    if (shape.getHyperlinks().get_Item(i).getAddress().contains("http://someurl.com")) {
        shape.getHyperlinks().removeAt(i);
    }
}
```  

- **Por qué este paso es importante**: Un bucle inverso garantiza que todos los hipervínculos se eliminen sin omitir ninguna entrada.  

## Cómo guardar el diagrama editado y liberar recursos?  
El método `save(String path)` escribe el documento modificado en la ubicación de archivo especificada, finalizando todos los cambios.  
Una vez que se eliminen todos los hipervínculos, invoca el método `save` en la instancia de Watermarker, proporcionando un nuevo nombre de archivo para evitar sobrescribir el original. Luego llama a `close()` para liberar los manejadores de archivo y liberar memoria, lo cual es esencial para procesos por lotes de larga duración. Esto asegura que el archivo se cierre correctamente y esté listo para su uso posterior.  

```java
watermarker.save("YOUR_OUTPUT_DIRECTORY");
watermarker.close();
```  

- **Por qué este paso es importante**: Cerrar correctamente los recursos evita fugas de memoria y problemas de bloqueo de archivos en el servidor.  

## Aplicaciones prácticas  
Eliminar hipervínculos de las formas de diagramas puede ser beneficioso en varios escenarios del mundo real:  

1. **Seguridad** – Evita enlaces externos que podrían llevar a sitios maliciosos.  
2. **Cumplimiento** – Cumple con las políticas corporativas que prohíben URL incrustadas en activos compartidos.  
3. **Claridad** – Produce presentaciones más limpias donde los enlaces resultarían distractores.  

Puedes incrustar esta lógica en pipelines de automatización más grandes, como trabajos por lotes nocturnos que sanitizan todos los diagramas antes de que se publiquen en una intranet.  

## Consideraciones de rendimiento  

### Optimización del rendimiento  
- Usa una única instancia de `Watermarker` por archivo para reducir la sobrecarga.  
- Prefiere la iteración inversa (como se muestra) para evitar la costosa reindexación de listas.  

### Directrices de uso de recursos  
- Para diagramas mayores de 200 MB, monitorea el uso del heap y considera aumentar la bandera JVM `-Xmx`.  
- Herramientas de perfilado como VisualVM pueden ayudar a identificar cuellos de botella en ejecuciones por lotes a gran escala.  

### Mejores prácticas para la gestión de memoria en Java  
- Declara objetos dentro del alcance más pequeño posible.  
- Usa try‑with‑resources al trabajar con streams para asegurar el cierre automático.  

## Preguntas frecuentes  

**P: ¿Cómo manejo diagramas que contienen miles de formas?**  
R: Procesa el diagrama página por página y libera los recursos de cada página antes de pasar a la siguiente para mantener bajo el uso de memoria.  

**P: ¿Puedo limitar la eliminación de hipervínculos solo a páginas específicas?**  
R: Sí – recupera el índice de página que deseas, luego aplica el bucle de eliminación solo a las formas de esa página.  

**P: ¿Es obligatoria una licencia comercial para el procesamiento por lotes?**  
R: Se requiere una licencia válida para cualquier despliegue a nivel de producción; la prueba gratuita está limitada a 30 días y 5 documentos.  

**P: ¿GroupDocs.Watermark soporta diagramas SVG?**  
R: Absolutamente – SVG está entre los más de 30 formatos soportados, y los hipervínculos pueden eliminarse usando las mismas llamadas a la API.  

**P: ¿Qué pasa si una forma tiene varios hipervínculos?**  
R: El bucle de iteración inversa elimina cada entrada de hipervínculo individualmente, asegurando que todos los enlaces se eliminen.  

## Recursos  

- [Documentación](https://docs.groupdocs.com/watermark/java/)  
- [Referencia de API](https://reference.groupdocs.com/watermark/java)  
- [Descarga](https://releases.groupdocs.com/watermark/java/)  
- [Repositorio de GitHub](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)  
- [Foro de soporte gratuito](https://forum.groupdocs.com/c/watermark/10)  
- [Adquisición de licencia temporal](https://purchase.groupdocs.com/temporary-license/)  

---  

**Última actualización:** 2026-08-25  
**Probado con:** GroupDocs.Watermark 24.11 for Java  
**Autor:** GroupDocs  

## Tutoriales relacionados  

- [Tutoriales de marcas de agua en diagramas para GroupDocs.Watermark Java](/watermark/java/diagram-document-watermarking/)  
- [Editar encabezados y pies de página de diagramas en Java usando GroupDocs.Watermark: Guía completa](/watermark/java/diagram-document-watermarking/edit-diagram-headers-footers-groupdocs-watermark-java/)  
- [Eliminar formas de diagramas de manera eficiente usando GroupDocs.Watermark para Java](/watermark/java/watermark-removal/remove-shapes-diagrams-groupdocs-watermark-java/)