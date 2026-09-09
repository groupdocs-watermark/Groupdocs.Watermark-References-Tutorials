---
date: '2026-02-13'
description: Aprenda cómo agregar marcas de agua en Java y enumerar eficientemente
  los formatos de archivo compatibles con GroupDocs.Watermark, garantizando la compatibilidad
  entre los tipos de documentos.
keywords:
- GroupDocs Watermark Java
- list supported file formats GroupDocs
- Java watermarking library
title: 'Agregar marca de agua Java: lista de formatos compatibles con GroupDocs'
type: docs
url: /es/java/document-information/groupdocs-watermark-java-list-supported-formats/
weight: 1
---

# Add Watermark Java: Lista de formatos compatibles con GroupDocs

Trabajar con múltiples tipos de documentos puede ser un desafío cuando necesitas **add watermark java** y asegurar que tu aplicación solo procese archivos que la biblioteca soporta. La biblioteca GroupDocs.Watermark simplifica esto proporcionando una lista completa de formatos compatibles, permitiéndote aplicar marcas de agua con confianza en PDFs, imágenes, documentos Word y más.

## Respuestas rápidas
- **¿Qué hace la biblioteca?** Permite **add watermark java** a muchos tipos de documentos y recuperar los formatos compatibles.  
- **¿Qué método lista los formatos?** `FileType.getSupportedFileTypes()` devuelve todos los tipos disponibles.  
- **¿Necesito una licencia?** Una prueba funciona para pruebas; se requiere una licencia paga para producción.  
- **¿Puedo usar esto con Maven?** Sí, solo agrega el repositorio y la dependencia de GroupDocs.  
- **¿Es Java 8 suficiente?** Sí, se soporta JDK 8 o superior.

## Qué es “add watermark java”

Agregar una marca de agua en Java significa superponer programáticamente texto o una imagen sobre un documento para protegerlo o marcarlo. GroupDocs.Watermark proporciona una API limpia que se encarga del trabajo pesado para docenas de tipos de archivo.

## Por qué listar los formatos compatibles

Conocer los formatos exactos te ayuda a **retrieve file types java**‑compatible con la biblioteca, previene errores en tiempo de ejecución y te permite crear lógica de validación dinámica para las cargas de usuarios.

## Requisitos previos

- **Bibliotecas requeridas**: GroupDocs.Watermark para Java versión 24.11 o posterior.  
- **Entorno**: JDK 8 + y Maven instalado.  
- **Conocimientos**: Java básico y gestión de dependencias con Maven.

## Configuración de GroupDocs.Watermark para Java

### Instalación mediante Maven

Agrega el repositorio y la dependencia a tu `pom.xml`:

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

Alternativamente, descarga la última versión de GroupDocs.Watermark para Java desde [Versiones de GroupDocs](https://releases.groupdocs.com/watermark/java/).

#### Obtención de licencia

Para usar GroupDocs.Watermark, obtén una licencia. Las opciones incluyen comenzar con una prueba gratuita o solicitar una licencia temporal.

### Inicialización y configuración

Después de agregar la dependencia o descargar la biblioteca, inicialízala en tu proyecto Java:

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.common.FileType;

public class WatermarkExample {
    public static void main(String[] args) {
        // Initialize a watermarker object for demonstration purposes
        Watermarker watermarker = new Watermarker("path/to/your/file");
        
        // Your code to list supported file formats will go here

        watermarker.close();
    }
}
```

## Cómo add watermark java y listar los formatos de archivo compatibles

### Paso 1: Recuperar todos los tipos de archivo compatibles  

Utiliza la clase `FileType` para obtener cada formato que la biblioteca puede manejar:

```java
// STEP 1: Retrieve all supported file types from the GroupDocs library
FileType[] fileTypes = FileType.getSupportedFileTypes();
```

### Paso 2: Iterar e imprimir los nombres de los tipos de archivo  

Recorre el arreglo y muestra el nombre de cada formato:

```java
// STEP 2: Iterate over each file type and print its name
for (FileType fileType : fileTypes) {
    System.out.println(fileType);
}
```

Ejecutar este código imprime una lista como `PDF`, `DOCX`, `PNG`, etc., dándote una visión clara de lo que puedes **list supported formats java**.

## Problemas comunes y soluciones

- **Errores de dependencia** – Verifica que las coordenadas de Maven coincidan con la versión que agregaste.  
- **Versión de Java no compatible** – La biblioteca requiere JDK 8 o superior; actualiza si ves advertencias de compatibilidad.  
- **Consejo de rendimiento** – Para un gran número de formatos, considera registrar en un archivo en lugar de `System.out.println` para evitar cuellos de botella en la consola.

## Aplicaciones prácticas

1. **Sistemas de gestión de documentos** – Validar dinámicamente las cargas verificando contra la lista recuperada antes de aplicar marcas de agua.  
2. **Plataformas de publicación de contenido** – Asegurar que solo los tipos de imagen y PDF compatibles reciban marcas de agua de marca.  
3. **Flujos de trabajo de documentos legales** – Proteger automáticamente los archivos confidenciales en todos los formatos que la biblioteca soporta.

## Consideraciones de rendimiento

- **Uso de recursos** – Cierra las instancias de `Watermarker` rápidamente (como se muestra en el ejemplo de inicialización) para liberar memoria.  
- **Escalabilidad** – Al procesar miles de archivos, agrupa las verificaciones de formato y reutiliza una única instancia de `Watermarker` cuando sea posible.

## Conclusión

En este tutorial aprendiste cómo **add watermark java** mientras también **retrieve file types java** y **list supported formats java** usando GroupDocs.Watermark. Con este conocimiento, puedes crear pipelines de documentos robustos que solo manejen archivos compatibles y apliquen marcas de agua con confianza.

### Próximos pasos

Explora capacidades adicionales como agregar marcas de agua de texto o imagen, personalizar la opacidad y la posición. La API ofrece opciones avanzadas para adaptar la marca de agua a las necesidades de tu marca.

## Sección de preguntas frecuentes

1. **¿Qué formatos de archivo soporta GroupDocs.Watermark?**  
   - La biblioteca soporta una amplia gama de tipos de documento, incluidos PDFs, imágenes, documentos Word, etc.  
2. **¿Cómo soluciono problemas con GroupDocs.Watermark?**  
   - Verifica tus dependencias de Maven y asegura la compatibilidad con tu versión de Java.  
3. **¿Puedo usar GroupDocs.Watermark con fines comerciales?**  
   - Sí, pero deberás comprar una licencia después del período de prueba.  
4. **¿Qué debo hacer si mi aplicación es lenta al listar los formatos de archivo?**  
   - Optimiza la gestión de recursos cerrando archivos y objetos rápidamente.  
5. **¿Dónde puedo encontrar más ejemplos de uso de GroupDocs.Watermark?**  
   - Consulta el [repositorio de GitHub de GroupDocs](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java) para obtener muestras de código adicionales.

## Preguntas frecuentes

**P: ¿Cómo puedo comprobar programáticamente si un tipo de archivo específico es compatible?**  
R: Después de recuperar el `FileType[]`, compara `fileType.toString()` con la extensión deseada.

**P: ¿Es posible filtrar la lista solo a formatos de imagen?**  
R: Sí, recorre el arreglo y usa `fileType.isImage()` (o verifica la extensión) para seleccionar los tipos de imagen.

**P: ¿La biblioteca soporta PDFs protegidos con contraseña al listar formatos?**  
R: Listar formatos es independiente del contenido del archivo, por lo que la protección con contraseña no afecta la recuperación.

**P: ¿Puedo obtener la lista sin inicializar una instancia de `Watermarker`?**  
R: Absolutamente. El método `FileType.getSupportedFileTypes()` es estático y no requiere un `Watermarker`.

## Recursos

- **Documentación**: [Documentación de GroupDocs Watermark Java](https://docs.groupdocs.com/watermark/java/)  
- **Referencia de API**: [Referencia de API de GroupDocs](https://reference.groupdocs.com/watermark/java)  
- **Descarga**: [Última versión](https://releases.groupdocs.com/watermark/java/)  
- **GitHub**: [GitHub de GroupDocs.Watermark Java](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)  
- **Soporte gratuito**: [Foro de GroupDocs](https://forum.groupdocs.com/c/watermark/10)  
- **Licencia temporal**: [Comprar licencia temporal](https://purchase.groupdocs.com/temporary-license/) 

¡Emprende tu viaje con GroupDocs.Watermark para Java hoy y desbloquea potentes capacidades de procesamiento de documentos en tus aplicaciones!

---

**Última actualización:** 2026-02-13  
**Probado con:** GroupDocs.Watermark 24.11 for Java  
**Autor:** GroupDocs