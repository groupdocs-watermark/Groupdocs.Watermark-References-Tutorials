---
title: Cargar documento desde la secuencia
linktitle: Cargar documento desde la secuencia
second_title: API GroupDocs.Watermark .NET
description: Aprenda a agregar marcas de agua a documentos usando GroupDocs.Watermark para .NET con esta guía. Perfecto para desarrolladores que buscan mejorar la seguridad de los documentos.
weight: 11
url: /es/net/document-loadings/load-document-from-stream/
type: docs
---
# Cargar documento desde la secuencia

## Introducción
¿Está buscando agregar marcas de agua a sus documentos sin problemas usando .NET? ¡No busque más! GroupDocs.Watermark para .NET es una biblioteca potente y fácil de usar que le permite administrar marcas de agua en varios formatos de documentos. Ya sea que esté trabajando con archivos PDF, documentos de Word o imágenes, esta herramienta lo tiene cubierto. En este tutorial, lo guiaremos a través del proceso de cargar un documento desde una secuencia y agregar una marca de agua paso a paso. Así que ¡vamos a sumergirnos de lleno!
## Requisitos previos
Antes de comenzar, asegúrese de tener la siguiente configuración:
1. Visual Studio: cualquier versión reciente de Visual Studio funcionará bien.
2. .NET Framework: asegúrese de tener instalado .NET Framework 4.0 o superior.
3.  GroupDocs.Watermark para .NET: puede descargarlo desde[aquí](https://releases.groupdocs.com/Watermark/net/).
4. Conocimientos básicos de C#: será útil estar familiarizado con C# y los conceptos de programación orientada a objetos.

## Importar espacios de nombres
Para usar GroupDocs.Watermark en su proyecto, deberá importar los espacios de nombres necesarios. Esto le permitirá acceder a las funciones de la biblioteca sin ningún problema.
```csharp
using System;
using System.IO;
using GroupDocs.Watermark.Watermarks;
```
## Paso 1: configurar su proyecto
Lo primero es lo primero: debe configurar su proyecto en Visual Studio. Así es como lo haces:
1. Cree un nuevo proyecto: abra Visual Studio y cree un nuevo proyecto de aplicación de consola C#.
2.  Instale GroupDocs.Watermark: instale la biblioteca GroupDocs.Watermark a través del Administrador de paquetes NuGet. Simplemente busque`GroupDocs.Watermark` e instalarlo.
## Paso 2: definir rutas de documentos
A continuación, debe definir las rutas de su documento y el archivo de salida donde se guardará el documento con marca de agua.
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
```
 Reemplazar`"Your Document Path"` con la ruta real del documento que desea marcar con marca de agua y`"Your Document Directory"` con el directorio donde desea guardar el documento con marca de agua.
## Paso 3: cargue el documento desde una secuencia
Ahora, carguemos el documento desde una secuencia. Esto implica abrir el documento como una secuencia y luego usar el`Watermarker` clase de la biblioteca GroupDocs.Watermark para administrarlo.
```csharp
using (Stream document = File.OpenRead(documentPath))
using (Watermarker watermarker = new Watermarker(document))
{
    // Tu código para gestionar marcas de agua irá aquí
}
```
 Este fragmento de código garantiza que el documento se abra como una secuencia y que el`Watermarker` La clase se inicializa con esta secuencia. El`using` Las declaraciones garantizan que los recursos se eliminen adecuadamente después de su uso.
## Paso 4: crea y agrega una marca de agua
Crear una marca de agua es sencillo con GroupDocs.Watermark. En este ejemplo, crearemos una marca de agua de texto simple.
```csharp
TextWatermark watermark = new TextWatermark("Test watermark", new Font("Arial", 12));
watermarker.Add(watermark);
```
 Aquí creamos un`TextWatermark` objeto con el texto "Marca de agua de prueba" y especifique los detalles de la fuente. Luego, agregamos esta marca de agua al documento usando el`Add` método de la`Watermarker` clase.
## Paso 5: guarde el documento con marca de agua
Finalmente, guarde el documento con marca de agua en la ruta de salida especificada.
```csharp
watermarker.Save(outputFileName);
```
 Este código guarda el documento con la marca de agua recién agregada.`outputFileName` camino que definiste anteriormente.

## Conclusión
¡Felicidades! Ha agregado exitosamente una marca de agua a su documento usando GroupDocs.Watermark para .NET. Esta biblioteca hace que sea increíblemente fácil administrar marcas de agua en una variedad de formatos de documentos. Ya sea que necesite agregar texto, imágenes u otros tipos de marcas de agua, GroupDocs.Watermark tiene las herramientas que necesita. No olvides consultar el[documentación](https://tutorials.groupdocs.com/Watermark/net/) para funciones más avanzadas y opciones de personalización.
## Preguntas frecuentes
### ¿Qué tipos de marcas de agua puedo agregar usando GroupDocs.Watermark para .NET?
Puede agregar marcas de agua de texto, marcas de agua de imágenes e incluso formas y logotipos complejos. La biblioteca admite una amplia gama de opciones de personalización.
### ¿Puedo eliminar marcas de agua de documentos usando GroupDocs.Watermark?
Sí, GroupDocs.Watermark también le permite eliminar marcas de agua existentes en los documentos.
### ¿Hay una prueba gratuita disponible para GroupDocs.Watermark?
 Sí, puedes descargar una prueba gratuita desde[aquí](https://releases.groupdocs.com/).
### ¿Cómo compro una licencia para GroupDocs.Watermark?
Puede comprar una licencia directamente desde el[Sitio web de GroupDocs](https://purchase.groupdocs.com/buy).
### ¿Dónde puedo obtener asistencia si tengo problemas?
 Para obtener soporte, puede visitar el[Foro de soporte de GroupDocs.Watermark](https://forum.groupdocs.com/c/watermark/19).