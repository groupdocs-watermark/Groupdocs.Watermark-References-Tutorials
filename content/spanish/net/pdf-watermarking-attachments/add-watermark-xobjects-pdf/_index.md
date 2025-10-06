---
title: Agregar marca de agua a XObjects en PDF
linktitle: Agregar marca de agua a XObjects en PDF
second_title: API GroupDocs.Watermark .NET
description: Aprenda a agregar marcas de agua a XObjects en PDF usando Groupdocs.Watermark para .NET. Siga nuestra guía paso a paso para una fácil implementación.
weight: 20
url: /es/net/pdf-watermarking-attachments/add-watermark-xobjects-pdf/
type: docs
---
# Agregar marca de agua a XObjects en PDF

## Introducción
Poner marcas de agua en archivos PDF es un paso crucial para garantizar que sus documentos estén protegidos contra el uso no autorizado. Con Groupdocs.Watermark para .NET, agregar marcas de agua a XObjects dentro de sus archivos PDF nunca ha sido tan fácil. En este tutorial, lo guiaremos a través del proceso paso a paso, asegurándonos de que pueda aplicar marcas de agua con confianza a sus documentos PDF. ¡Empecemos!
## Requisitos previos
Antes de sumergirnos en el tutorial, asegurémonos de tener todo lo que necesita para seguirlo sin problemas:
-  Groupdocs.Watermark para .NET: descargue e instale la última versión desde[aquí](https://releases.groupdocs.com/Watermark/net/).
- .NET Framework: asegúrese de tener .NET Framework instalado en su máquina de desarrollo.
- Entorno de desarrollo: utilice Visual Studio o cualquier otro IDE que admita el desarrollo .NET.
-  Licencia Temporal: Obtener una[licencia temporal](https://purchase.groupdocs.com/temporary-license/) si estás evaluando el producto.
Una vez que tenga estos requisitos previos implementados, estará listo para comenzar a agregar marcas de agua a sus archivos PDF.
## Importar espacios de nombres
Primero, deberá importar los espacios de nombres necesarios en su proyecto. Abra su proyecto C# y agregue lo siguiente usando directivas:
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Paso 1: configure las rutas de sus documentos
El primer paso consiste en configurar las rutas de su documento. Defina la ruta donde se encuentra su PDF y donde desea guardar el PDF con marca de agua.
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
 Reemplazar`"Your Document Path"` y`"Your Document Directory"` con las rutas reales en su máquina.
## Paso 2: Inicialice las opciones de carga de PDF
A continuación, deberá inicializar las opciones de carga de PDF. Esto es crucial para cargar el contenido PDF correctamente.
```csharp
var loadOptions = new PdfLoadOptions();
```
## Paso 3: cargue el documento PDF
Usando las opciones de carga, cargue el documento PDF con el`Watermarker` clase.
```csharp
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    PdfContent pdfContent = watermarker.GetContent<PdfContent>();
```
## Paso 4: crea la marca de agua
Ahora necesitas crear la marca de agua que se agregará al PDF. Para este tutorial, crearemos una marca de agua de texto.
```csharp
TextWatermark watermark = new TextWatermark("Protected image", new Font("Arial", 8))
{
    HorizontalAlignment = HorizontalAlignment.Center,
    VerticalAlignment = VerticalAlignment.Center,
    RotateAngle = 45,
    SizingType = SizingType.ScaleToParentDimensions,
    ScaleFactor = 1
};
```
## Paso 5: agregar marca de agua a XObjects
Repita cada página y cada XObject dentro del PDF para aplicar la marca de agua.
```csharp
foreach (PdfPage page in pdfContent.Pages)
{
    foreach (PdfXObject xObject in page.XObjects)
    {
        if (xObject.Image != null)
        {
            // Agregar marca de agua a la imagen
            xObject.Image.Add(watermark);
        }
    }
}
```
## Paso 6: guarde el PDF con marca de agua
Finalmente, guarde el PDF con marca de agua en el archivo de salida especificado.
```csharp
    watermarker.Save(outputFileName);
}
```
¡Y ahí lo tienes! Su PDF ahora contiene marcas de agua en todos sus XObjects.
## Conclusión
 Agregar marcas de agua a sus documentos PDF usando Groupdocs Watermark para .NET es un proceso sencillo que proporciona una capa adicional de seguridad. Si sigue los pasos descritos en este tutorial, puede asegurarse de que sus documentos estén protegidos contra el uso no autorizado. Recuerde, siempre puede consultar el[documentación](https://tutorials.groupdocs.com/Watermark/net/) para obtener información más detallada y funciones avanzadas.
## Preguntas frecuentes
### ¿Puedo usar una imagen como marca de agua en lugar de texto?
Sí, Groupdocs.Watermark para .NET admite marcas de agua de texto e imagen.
### ¿Cómo puedo probar Groupdocs.Watermark sin comprarlo?
 Puedes usar un[licencia temporal](https://purchase.groupdocs.com/temporary-license/) para evaluar el producto.
### ¿Es posible personalizar la apariencia de la marca de agua?
¡Absolutamente! Puede personalizar la fuente, el tamaño, el ángulo de rotación y más.
### ¿Groupdocs.Watermark admite otros formatos de documentos?
Sí, admite varios formatos, incluidos Word, Excel y PowerPoint.
### ¿Dónde puedo obtener asistencia si tengo problemas?
 Puede obtener apoyo del[Foro de documentos grupales](https://forum.groupdocs.com/c/watermark/19).