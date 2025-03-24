---
title: Agregar marca de agua a imágenes en PDF
linktitle: Agregar marca de agua a imágenes en PDF
second_title: API GroupDocs.Watermark .NET
description: Aprenda a agregar marcas de agua a imágenes en documentos PDF usando GroupDocs.Watermark para .NET con nuestro tutorial detallado paso a paso. Asegure sus archivos PDF fácilmente.
weight: 19
url: /es/net/pdf-watermarking-attachments/add-watermark-images-pdf/
---
## Introducción
Agregar marcas de agua a las imágenes de un documento PDF puede ser esencial para proteger su propiedad intelectual o garantizar la autenticidad de sus documentos. Con GroupDocs.Watermark para .NET, esta tarea se puede realizar de manera eficiente y sencilla. Este tutorial lo guiará a través de cada paso del proceso, desde configurar su entorno hasta agregar marcas de agua y guardar el documento final. ¡Vamos a sumergirnos!
## Requisitos previos
Antes de comenzar, asegúrese de tener lo siguiente:
1. Visual Studio: instale Visual Studio, el entorno de desarrollo integrado (IDE) para aplicaciones .NET.
2.  GroupDocs.Watermark para .NET: descargue e instale la biblioteca GroupDocs.Watermark para .NET desde[página de lanzamiento](https://releases.groupdocs.com/Watermark/net/).
3. Un documento PDF: tenga un documento PDF con imágenes listo para probar la funcionalidad de marca de agua.
4.  Licencia Temporal: Obtener una[licencia temporal](https://purchase.groupdocs.com/temporary-license/) si estás evaluando el producto.
## Importar espacios de nombres
Primero, asegúrese de haber importado los espacios de nombres necesarios en su proyecto. Esto incluirá los espacios de nombres principales necesarios para trabajar con documentos PDF y marcas de agua.
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.Image;
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Paso 1: configurar la ruta del documento y el directorio de salida
Para comenzar, defina las rutas para el documento de entrada y el directorio de salida donde se guardará el documento con marca de agua. Este paso es crucial para garantizar que su programa sepa dónde encontrar el documento fuente y dónde almacenar el archivo procesado.
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
## Paso 2: cargue el documento PDF
 A continuación, deberá cargar el documento PDF usando`PdfLoadOptions`. Esta clase le permite especificar opciones para cargar el PDF, como protección con contraseña si es necesario.
```csharp
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Su código para la marca de agua irá aquí
}
```
## Paso 3: crea la marca de agua
Ahora, inicializa la marca de agua. En este ejemplo, estamos creando una marca de agua de texto que dice "Imagen protegida". Personalice la fuente, la alineación, la rotación y la escala según sus necesidades.
```csharp
TextWatermark watermark = new TextWatermark("Protected image", new Font("Arial", 8));
watermark.HorizontalAlignment = HorizontalAlignment.Center;
watermark.VerticalAlignment = VerticalAlignment.Center;
watermark.RotateAngle = 45;
watermark.SizingType = SizingType.ScaleToParentDimensions;
watermark.ScaleFactor = 1;
```
## Paso 4: acceda al contenido PDF
Recupera el contenido del documento PDF. Específicamente, necesitamos acceder a las imágenes dentro del PDF. Aquí nos centramos en la primera página, pero puedes ampliarla a otras páginas según sea necesario.
```csharp
PdfContent pdfContent = watermarker.GetContent<PdfContent>();
// Obtener todas las imágenes desde la primera página.
WatermarkableImageCollection images = pdfContent.Pages[0].FindImages();
```
## Paso 5: aplique la marca de agua a las imágenes
Recorra cada imagen que se encuentra en la primera página y aplique la marca de agua. Esto garantiza que todas las imágenes de la página especificada tendrán aplicada la marca de agua.
```csharp
// Agregar marca de agua a todas las imágenes encontradas
foreach (WatermarkableImage image in images)
{
    image.Add(watermark);
}
```
## Paso 6: guarde el documento con marca de agua
Finalmente, guarde el PDF con marca de agua en el directorio de salida especificado. Este paso finaliza el proceso escribiendo los cambios en un nuevo archivo.
```csharp
watermarker.Save(outputFileName);
```
## Conclusión
¡Y ahí lo tienes! Agregar una marca de agua a imágenes dentro de un PDF usando GroupDocs Watermark para .NET es un proceso sencillo que puede mejorar enormemente la seguridad y autenticidad de sus documentos. Si sigue estos pasos, podrá asegurarse de que su propiedad intelectual esté protegida y sus documentos seguros.
## Preguntas frecuentes
### ¿Qué es GroupDocs.Watermark para .NET?
GroupDocs.Watermark para .NET es una biblioteca completa que permite a los desarrolladores agregar, buscar y eliminar marcas de agua en varios formatos de documentos, incluidos los PDF.
### ¿Puedo agregar marcas de agua de texto e imagen usando GroupDocs.Watermark?
Sí, GroupDocs.Watermark admite marcas de agua de texto e imagen, lo que brinda flexibilidad para diferentes tipos de necesidades de marcas de agua.
### ¿Es posible poner marcas de agua en varias páginas de un PDF?
¡Absolutamente! Puede recorrer cada página del PDF y aplicar marcas de agua a las imágenes de cada página.
### ¿Necesito una licencia para utilizar GroupDocs.Watermark para .NET?
 Sí, se requiere una licencia. Puedes obtener un[licencia temporal](https://purchase.groupdocs.com/temporary-license/) para fines de evaluación.
### ¿Dónde puedo encontrar más documentación sobre GroupDocs.Watermark para .NET?
 Puede encontrar documentación completa sobre el[Página de documentación de GroupDocs.Watermark](https://tutorials.groupdocs.com/Watermark/net/).