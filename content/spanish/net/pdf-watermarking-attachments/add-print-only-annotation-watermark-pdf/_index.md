---
title: Agregar marca de agua de anotación de solo impresión a PDF
linktitle: Agregar marca de agua de anotación de solo impresión a PDF
second_title: API GroupDocs.Watermark .NET
description: Aprenda a agregar marcas de agua de anotaciones de solo impresión a archivos PDF usando GroupDocs.Watermark para .NET. Mejore la seguridad de los documentos y la marca sin esfuerzo.
weight: 13
url: /es/net/pdf-watermarking-attachments/add-print-only-annotation-watermark-pdf/
---

# Agregar marca de agua de anotación de solo impresión a PDF

## Introducción
En este tutorial, profundizaremos en el proceso de agregar una marca de agua de anotación de solo impresión a un PDF usando GroupDocs.Watermark para .NET. La marca de agua en los documentos es un aspecto crucial de la seguridad y la marca de los documentos, y GroupDocs.Watermark proporciona una solución perfecta para que los desarrolladores de .NET lo logren.
## Requisitos previos
Antes de comenzar, asegúrese de tener los siguientes requisitos previos:
- Conocimientos básicos del lenguaje de programación C#.
- Visual Studio instalado en su máquina.
- Biblioteca GroupDocs.Watermark para .NET instalada en su proyecto.

## Importar espacios de nombres
Para comenzar, asegúrese de importar los espacios de nombres necesarios:
```csharp
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Paso 1: cargue el documento
 En primer lugar, debe cargar el documento PDF al que desea ponerle una marca de agua. Reemplazar`"Your Document Path"` con la ruta a su archivo PDF y`"Your Document Directory"` con el directorio donde desea guardar el archivo de salida.
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // El código de marca de agua se agregará aquí
}
```
## Paso 2: agregar marca de agua
 continuación, cree un objeto de marca de agua de texto con el texto y la fuente deseados. Colocar`isPrintOnly` a`true` para garantizar que la marca de agua solo sea visible cuando se imprime el documento, no en el modo de visualización.
```csharp
TextWatermark textWatermark = new TextWatermark("This is a print only test watermark. It won't appear in view mode.", new Font("Arial", 8));
bool isPrintOnly = true;
```
## Paso 3: configurar las opciones de marca de agua
Defina opciones para la marca de agua, como el índice de la página donde se debe agregar la marca de agua y especificarla como una anotación de solo impresión.
```csharp
PdfAnnotationWatermarkOptions options = new PdfAnnotationWatermarkOptions();
options.PageIndex = 0;
options.PrintOnly = isPrintOnly;
```
## Paso 4: aplicar marca de agua
Agregue la marca de agua al documento usando las opciones especificadas y guarde el archivo de salida.
```csharp
watermarker.Add(textWatermark, options);
watermarker.Save(outputFileName);
```

## Conclusión
En este tutorial, aprendimos cómo agregar una marca de agua de anotación de solo impresión a un documento PDF usando GroupDocs.Watermark para .NET. Esto permite a los desarrolladores mejorar la seguridad de los documentos y la marca con facilidad.
## Preguntas frecuentes
### ¿GroupDocs.Watermark es compatible con otros formatos de documentos además de PDF?
Sí, GroupDocs admite varios formatos de documentos, como Word, Excel, PowerPoint e imágenes.
### ¿Puedo personalizar la apariencia de la marca de agua?
Ciertamente, GroupDocs.Watermark ofrece amplias opciones para personalizar el texto, la fuente, el color, el tamaño y la posición de la marca de agua.
### ¿GroupDocs.Watermark ofrece capacidades de procesamiento por lotes?
Por supuesto, los desarrolladores pueden marcar varios documentos simultáneamente utilizando funciones de procesamiento por lotes.
### ¿Existe una versión de prueba disponible para GroupDocs.Watermark?
Sí, puede acceder a una versión de prueba gratuita de GroupDocs.Watermark desde el enlace proporcionado.
### ¿Cómo puedo obtener soporte técnico para GroupDocs.Watermark?
Puede buscar asistencia técnica en el foro GroupDocs.Watermark disponible en el enlace de soporte proporcionado.