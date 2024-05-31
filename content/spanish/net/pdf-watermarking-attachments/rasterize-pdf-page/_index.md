---
title: Rasterizar página PDF
linktitle: Rasterizar página PDF
second_title: API GroupDocs.Watermark .NET
description: Mejore la seguridad de los documentos con GroupDocs Watermark para .NET. Agregue marcas de agua a PDF y otros formatos sin problemas.
type: docs
weight: 28
url: /es/net/pdf-watermarking-attachments/rasterize-pdf-page/
---
## Introducción
GroupDocs.Watermark para .NET es una potente API que permite a los desarrolladores agregar sin problemas marcas de agua a varios formatos de documentos, incluidos PDF, Word, Excel, PowerPoint y más. Con su interfaz intuitiva y amplias funciones, GroupDocs.Watermark simplifica el proceso de agregar marcas de agua de texto o imágenes a los documentos, lo que permite a los usuarios proteger su propiedad intelectual y mejorar la seguridad de los documentos sin esfuerzo.
## Requisitos previos
Antes de sumergirse en el uso de GroupDocs.Watermark para .NET, asegúrese de cumplir con los siguientes requisitos previos:
1. Instalación: Descargue e instale GroupDocs.Watermark para .NET desde[pagina de descarga](https://releases.groupdocs.com/Watermark/net/).
2.  Licencia: Adquiera una licencia de GroupDocs.Watermark para .NET. Puede obtener una licencia temporal para fines de evaluación en[aquí](https://purchase.groupdocs.com/temporary-license/) , o comprar una licencia completa de[pagina de compra](https://purchase.groupdocs.com/buy).
3. .NET Framework: asegúrese de tener .NET Framework instalado en su máquina de desarrollo.
4. Documento: Prepare el documento al que desea agregar marcas de agua.

## Importar espacios de nombres
Para comenzar a usar GroupDocs.Watermark para .NET, importe los espacios de nombres necesarios a su proyecto:
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Paso 1: cargue el documento
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Tu código va aquí
}
```
## Paso 2: inicializar la marca de agua
```csharp
TextWatermark watermark = new TextWatermark("Do not copy", new Font("Arial", 8));
watermark.HorizontalAlignment = HorizontalAlignment.Center;
watermark.VerticalAlignment = VerticalAlignment.Center;
watermark.RotateAngle = 45;
watermark.SizingType = SizingType.ScaleToParentDimensions;
watermark.ScaleFactor = 1;
watermark.Opacity = 0.5;
```
## Paso 3: agregar marca de agua
```csharp
PdfArtifactWatermarkOptions options = new PdfArtifactWatermarkOptions();
options.PageIndex = 0;
watermarker.Add(watermark, options);
```
## Paso 4: rasterizar la página
```csharp
PdfContent pdfContent = watermarker.GetContent<PdfContent>();
pdfContent.Pages[0].Rasterize(100, 100, PdfImageConversionFormat.Png);
```
## Paso 5: guarde el documento
```csharp
watermarker.Save(outputFileName);
```

## Conclusión
En conclusión, GroupDocs.Watermark para .NET ofrece una solución perfecta para agregar marcas de agua a PDF y otros formatos de documentos. Siguiendo la guía paso a paso descrita anteriormente, los desarrolladores pueden rasterizar páginas PDF de manera eficiente y mejorar la seguridad de los documentos con facilidad.
## Preguntas frecuentes
### ¿GroupDocs.Watermark es compatible con otros formatos de documentos además de PDF?
Sí, GroupDocs.Watermark admite una amplia gama de formatos de documentos, incluidos Word, Excel, PowerPoint, Visio y más.
### ¿Puedo personalizar la apariencia de la marca de agua agregada al documento?
¡Absolutamente! GroupDocs.Watermark ofrece amplias opciones de personalización para marcas de agua de texto e imágenes, lo que permite a los usuarios ajustar la fuente, el tamaño, el color, la opacidad y la posición según sus preferencias.
### ¿GroupDocs.Watermark es adecuado tanto para uso personal como comercial?
Sí, GroupDocs.Watermark ofrece opciones de licencia flexibles para satisfacer las necesidades individuales y empresariales, lo que lo hace adecuado tanto para proyectos personales como para aplicaciones comerciales a gran escala.
### ¿GroupDocs.Watermark ofrece soporte técnico para desarrolladores?
Sí, los desarrolladores pueden acceder a soporte técnico integral a través del foro GroupDocs.Watermark, donde pueden buscar asistencia, compartir experiencias e interactuar con otros desarrolladores.
### ¿Puedo probar GroupDocs.Watermark antes de realizar una compra?
¡Ciertamente! Puede aprovechar una versión de prueba gratuita de GroupDocs.Watermark desde el[página de lanzamientos](https://releases.groupdocs.com/), permitiéndole explorar sus características y funcionalidades antes de comprometerse con una compra.