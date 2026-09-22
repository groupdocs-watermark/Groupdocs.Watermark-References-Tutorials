---
date: '2025-12-19'
description: Aprende cómo eliminar hipervínculos de las formas de diagramas usando
  GroupDocs.Watermark Java, un paso clave para la seguridad de documentos Java y la
  eliminación masiva de hipérlinks.
keywords:
- remove hyperlinks diagram shapes GroupDocs Watermark Java
- manage digital documents diagrams
- GroupDocs Watermark library Java
title: Cómo eliminar hipervínculos de formas de diagrama usando GroupDocs.Watermark
  Java
type: docs
url: /es/java/diagram-document-watermarking/remove-hyperlinks-diagram-shapes-groupdocs-watermark-java/
weight: 1
---

# Cómo eliminar hipervínculos de formas de diagramas usando GroupDocs.Watermark Java

Gestionar documentos digitales a menudo implica editar diagramas, especialmente al **eliminar hipervínculos** por motivos de seguridad o claridad. En este tutorial, aprenderás **cómo eliminar hipervínculos** de las formas de diagramas con GroupDocs.Watermark para Java, asegurando que tus archivos permanezcan limpios, seguros y profesionales.

## Respuestas rápidas
- **¿Cuál es el propósito principal?** Eliminar hipervínculos no deseados de las formas de diagramas para una mejor seguridad del documento.  
- **¿Qué biblioteca se utiliza?** GroupDocs.Watermark para Java (versión 24.11 o posterior).  
- **¿Necesito una licencia?** Una prueba funciona para pruebas; se requiere una licencia válida para producción.  
- **¿Puedo procesar muchos archivos a la vez?** Sí, la misma lógica se puede colocar dentro de un bucle por lotes.  
- **¿Es Java 8 suficiente?** Java 8+ es compatible; se recomiendan JDK más recientes.

## Qué significa “eliminar hipervínculos” en el contexto de diagramas?
Eliminar hipervínculos significa borrar las referencias URL adjuntas a las formas dentro de un archivo de diagrama (p. ej., Visio *.vsdx). Esta operación evita la navegación accidental a sitios externos y ayuda a cumplir con las políticas de cumplimiento o seguridad interna.

## ¿Por qué usar GroupDocs.Watermark Java para esta tarea?
- **Compatibilidad robusta de formatos** – funciona con una amplia gama de tipos de diagramas.  
- **API de gran granularidad** – le permite dirigirse a formas individuales y sus colecciones de hipervínculos.  
- **Optimizado para rendimiento** – adecuado tanto para archivos individuales como para procesamiento por lotes.  

## Requisitos previos
- **Biblioteca GroupDocs.Watermark** versión 24.11 o posterior.  
- Maven o descarga directa del JAR (ver los pasos de configuración a continuación).  
- Java Development Kit (JDK 8 o superior) y un IDE como IntelliJ IDEA o Eclipse.  

## Configuración de GroupDocs.Watermark para Java
Para comenzar, incluya la biblioteca en su proyecto mediante Maven o descargando el JAR.

### Configuración de Maven
Add the following configuration to your `pom.xml`:

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
Alternatively, download the latest version from [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

#### Pasos para obtener la licencia
- Comience con una prueba gratuita para evaluar la API.  
- Para producción, obtenga una licencia temporal o completa del portal de GroupDocs.

#### Inicialización y configuración básica
```java
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY", loadOptions);
```

## Cómo eliminar hipervínculos de formas de diagramas
A continuación se muestra una guía paso a paso que le lleva a cargar un diagrama, localizar formas y eliminar los hipervínculos no deseados.

### Paso 1: Cargar el archivo de diagrama
```java
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY", loadOptions);
```
*¿Por qué?* Cargar el archivo le brinda acceso programático a su estructura interna.

### Paso 2: Acceder al contenido de la forma
```java
DiagramContent content = watermarker.getContent(DiagramContent.class);
DiagramShape shape = content.getPages().get_Item(0).getShapes().get_Item(0);
```
*¿Por qué?* Necesita una referencia a la forma específica que puede contener hipervínculos.

### Paso 3: Iterar y eliminar hipervínculos
```java
for (int i = shape.getHyperlinks().getCount() - 1; i >= 0; i--) {
    if (shape.getHyperlinks().get_Item(i).getAddress().contains("http://someurl.com")) {
        shape.getHyperlinks().removeAt(i);
    }
}
```
*¿Por qué?* Iterar en sentido inverso evita errores de índice al eliminar elementos de la colección.

### Paso 4: Guardar y cerrar
```java
watermarker.save("YOUR_OUTPUT_DIRECTORY");
watermarker.close();
```
*¿Por qué?* Persistir los cambios y liberar recursos evita fugas de memoria y archivos bloqueados.

## Eliminación por lotes de hipervínculos (caso de uso avanzado)
Si necesita limpiar muchos diagramas a la vez, envuelva la lógica anterior dentro de un bucle que recorra una lista de rutas de archivos. Se aplican las mismas llamadas a la API; simplemente cambie los directorios de entrada y salida para cada iteración. Este enfoque se alinea con los requisitos de **eliminación por lotes de hipervínculos** para grandes repositorios de documentos.

## Aplicaciones prácticas
1. **Propósitos de seguridad** – Evitar enlaces externos que podrían exponer su red a phishing o malware.  
2. **Cumplimiento** – Cumplir con políticas corporativas que prohíben URLs externas en documentos compartidos.  
3. **Claridad** – Generar presentaciones más limpias donde los hipervínculos son innecesarios o distractores.  

## Consideraciones de rendimiento
### Optimización del rendimiento
- Utilice el patrón de iteración inversa mostrado arriba para mantener los bucles eficientes.  
- Cierre el objeto `Watermarker` tan pronto como termine para liberar memoria.

### Directrices de uso de recursos
- Monitoree CPU y RAM al procesar diagramas grandes.  
- Para trabajos por lotes, considere transmitir los archivos en lugar de cargarlos todos a la vez.

### Mejores prácticas para la gestión de memoria en Java
- Evite crear objetos dentro de bucles intensos.  
- Use try‑with‑resources donde sea aplicable para la limpieza automática.

## Preguntas frecuentes
1. **¿Cómo manejo múltiples formas?**  
   Itere sobre todas las páginas y sus formas, aplicando la misma lógica de eliminación de hipervínculos a cada forma.  

2. **¿Puede automatizarse este proceso para grandes lotes de diagramas?**  
   Sí, incorpore el código en una rutina de procesamiento por lotes o intégralo con su sistema de gestión documental.  

3. **¿Qué pasa si solo necesito eliminar hipervínculos de páginas específicas?**  
   Acceda a la página deseada por su índice (`content.getPages().get_Item(pageIndex)`) y dirija las formas solo en esa página.  

4. **¿Se requiere alguna licencia para el uso en producción de GroupDocs.Watermark?**  
   Se requiere una licencia comercial válida más allá del período de prueba.  

5. **¿Puede este método funcionar con otros formatos de diagramas?**  
   GroupDocs.Watermark admite muchos tipos de diagramas; verifique la compatibilidad en la documentación oficial.  

**Preguntas adicionales**

**P:** *¿Es posible registrar qué hipervínculos fueron eliminados?*  
**R:** Sí, antes de llamar a `removeAt(i)`, capture `shape.getHyperlinks().get_Item(i).getAddress()` y escríbalo en un archivo de registro.

**P:** *¿Eliminar los hipervínculos afectará la apariencia visual de la forma?*  
**R:** No. La geometría de la forma permanece sin cambios; solo se elimina la metadata del enlace.

**P:** *¿Necesito volver a aplicar algún estilo después de la eliminación?*  
**R:** Normalmente no. La eliminación del hipervínculo no altera los estilos de relleno, línea o texto.

## Conclusión
Ahora dispone de un método completo y listo para producción para **eliminar hipervínculos** de formas de diagramas usando GroupDocs.Watermark para Java. Siguiendo los pasos anteriores, puede asegurar sus diagramas, cumplir con las políticas y mantener sus documentos con un aspecto pulido.

## Recursos
- [Documentation](https://docs.groupdocs.com/watermark/java/)  
- [API Reference](https://reference.groupdocs.com/watermark/java)  
- [Download](https://releases.groupdocs.com/watermark/java/)  
- [GitHub Repository](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)  
- [Free Support Forum](https://forum.groupdocs.com/c/watermark/10)  
- [Temporary License Acquisition](https://purchase.groupdocs.com/temporary-license/)

---

**Last Updated:** 2025-12-19  
**Tested With:** GroupDocs.Watermark 24.11 for Java  
**Author:** GroupDocs  
