---
date: '2026-04-04'
description: Aprende a eliminar enlaces de las formas de diagramas con GroupDocs.Watermark
  Java, garantizando la seguridad y claridad del documento.
keywords:
- how to strip links
- remove hyperlinks java
- java diagram editing
title: Cómo eliminar enlaces de las formas de diagrama usando GroupDocs.Watermark
  Java
type: docs
url: /es/java/diagram-document-watermarking/remove-hyperlinks-diagram-shapes-groupdocs-watermark-java/
weight: 1
---

# Cómo eliminar enlaces de formas de diagramas usando GroupDocs.Watermark Java

Gestionar documentos digitales a menudo implica editar diagramas, especialmente cuando necesitas **cómo eliminar enlaces** por seguridad o claridad. En este tutorial aprenderás una forma simple, paso a paso, de eliminar hipervínculos no deseados de las formas de diagramas usando la poderosa biblioteca **GroupDocs.Watermark** para Java. Al final, tendrás diagramas limpios, sin enlaces, que son seguros para compartir.

## Respuestas rápidas
- **¿Qué significa “how to strip links”?** Se refiere a eliminar objetos de hipervínculo incrustados en las formas del diagrama.  
- **¿Qué biblioteca maneja esto?** GroupDocs.Watermark for Java (versión 24.11 o posterior).  
- **¿Necesito una licencia?** Una prueba gratuita funciona para pruebas; se requiere una licencia válida para producción.  
- **¿Puedo procesar muchos archivos a la vez?** Sí – envuelve el código en un bucle o trabajo por lotes.  
- **¿Este enfoque es específico de un lenguaje?** El ejemplo es Java, pero el mismo concepto se aplica a otras API .NET/Java.

## Qué es “how to strip links” en la edición de diagramas
Eliminar enlaces significa localizar objetos de hipervínculo adjuntos a formas dentro de un diagrama (p. ej., Visio *.vsdx) y borrarlos. Esto elimina URLs externas que podrían exponer información sensible o interrumpir el flujo de la presentación.

## ¿Por qué usar GroupDocs.Watermark para Java?
- **Precisión** – Acceso directo a los objetos de forma y sus colecciones de hipervínculos.  
- **Rendimiento** – Optimizado para diagramas grandes sin cargar todo el documento en memoria.  
- **Compatibilidad multiplataforma** – Funciona con muchos formatos de diagramas (Visio, Draw.io, etc.).  

## Requisitos previos
- **Biblioteca GroupDocs.Watermark** ≥ 24.11.  
- Maven (o inclusión manual de JAR).  
- Java JDK 8 o posterior.  
- Un IDE como IntelliJ IDEA o Eclipse.

## Configuración de GroupDocs.Watermark para Java
### Configuración de Maven
Add the repository and dependency to your `pom.xml`:

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
Si prefieres no usar Maven, descarga el JAR más reciente del sitio oficial:  
[GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

#### Pasos para adquirir la licencia
- **Comienza con una descarga de prueba gratuita.**  
- **Para producción, obtén una licencia temporal o completa del portal de GroupDocs.**

#### Inicialización y configuración básicas
Create a `Watermarker` instance that points to the folder containing your diagram:

```java
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY", loadOptions);
```

## Cómo eliminar enlaces de formas de diagramas
A continuación se muestra un proceso conciso de cuatro pasos que muestra **remove hyperlinks java** en acción.

### Paso 1: Cargar el archivo de diagrama
```java
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY", loadOptions);
```
*¿Por qué?* Cargar el archivo te brinda acceso programático a sus páginas, formas y colecciones de hipervínculos.

### Paso 2: Acceder al contenido de la forma
```java
DiagramContent content = watermarker.getContent(DiagramContent.class);
DiagramShape shape = content.getPages().get_Item(0).getShapes().get_Item(0);
```
*¿Por qué?* Necesitas una referencia a la forma específica que puede contener hipervínculos.

### Paso 3: Iterar y eliminar hipervínculos
```java
for (int i = shape.getHyperlinks().getCount() - 1; i >= 0; i--) {
    if (shape.getHyperlinks().get_Item(i).getAddress().contains("http://someurl.com")) {
        shape.getHyperlinks().removeAt(i);
    }
}
```
*¿Por qué?* Iterar en sentido inverso evita problemas de desplazamiento de índices al eliminar elementos de la colección.

### Paso 4: Guardar y cerrar
```java
watermarker.save("YOUR_OUTPUT_DIRECTORY");
watermarker.close();
```
*¿Por qué?* Guardar escribe el diagrama limpio en disco, y cerrar libera los manejadores de archivo para evitar fugas de memoria.

## Aplicaciones prácticas de la eliminación de enlaces
1. **Seguridad** – Eliminar URLs externas que podrían conducir a phishing o filtración de datos.  
2. **Cumplimiento** – Garantizar que los diagramas cumplan con las políticas internas antes de la distribución.  
3. **Limpieza de la presentación** – Eliminar áreas clicables innecesarias que distraen a los espectadores.

## Consideraciones de rendimiento
- **Eficiencia del bucle** – Usa el patrón de iteración inversa mostrado arriba.  
- **Gestión de recursos** – Prefiere `try‑with‑resources` o llamadas explícitas a `close()`.  
- **Archivos grandes** – Monitorea CPU/memoria; considera procesar páginas en lotes.

## Problemas comunes y soluciones
- **No se encontraron hipervínculos** – Verifica que el diagrama realmente contenga objetos de hipervínculo; algunos formatos los almacenan de manera diferente.  
- **IndexOutOfBoundsException** – Siempre itera en sentido inverso al eliminar elementos de una colección.  
- **Errores de licencia** – Asegúrate de que tu archivo de licencia esté colocado correctamente o pasado al constructor de `Watermarker`.

## Preguntas frecuentes

**Q: ¿Cómo manejo múltiples formas en múltiples páginas?**  
A: Loop through `content.getPages()` and then through each page’s `getShapes()` collection, applying the same removal logic to every shape.

**Q: ¿Puedo filtrar enlaces por dominio en lugar de una URL completa?**  
A: Yes – change the `contains` check to look for the domain string (e.g., `"example.com"`).

**Q: ¿Hay una forma de registrar qué enlaces fueron eliminados?**  
A: Inside the loop, capture `shape.getHyperlinks().get_Item(i).getAddress()` before removal and write it to a log file.

**Q: ¿Esto funciona con diagramas PDF incrustados en otros documentos?**  
A: GroupDocs.Watermark supports many formats; ensure the file type is recognized as a diagram (Visio, VDX, etc.).

**Q: ¿Qué licencia se requiere para el procesamiento por lotes?**  
A: A full production license is needed for any non‑trial, high‑volume operations.

## Conclusión
Ahora tienes un método completo y listo para producción para **cómo eliminar enlaces** de formas de diagramas usando GroupDocs.Watermark para Java. Incorpora esto en tus flujos de procesamiento de documentos para mejorar la seguridad, el cumplimiento y la calidad visual.

### Próximos pasos
- Explora otras funciones de manipulación como agregar marcas de agua o estampar texto.  
- Combina esta rutina con un servicio de observador de archivos para limpiar automáticamente los diagramas a medida que se cargan.

---

**Last Updated:** 2026-04-04  
**Tested With:** GroupDocs.Watermark 24.11 for Java  
**Author:** GroupDocs  

## Recursos
- [Documentación](https://docs.groupdocs.com/watermark/java/)
- [Referencia de API](https://reference.groupdocs.com/watermark/java)
- [Descarga](https://releases.groupdocs.com/watermark/java/)
- [Repositorio de GitHub](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)
- [Foro de soporte gratuito](https://forum.groupdocs.com/c/watermark/10)
- [Adquisición de licencia temporal](https://purchase.groupdocs.com/temporary-license/)