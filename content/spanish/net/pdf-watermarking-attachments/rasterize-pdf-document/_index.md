---
title: Rasterizar documento PDF
linktitle: Rasterizar documento PDF
second_title: API GroupDocs.Watermark .NET
description: Aprenda a rasterizar documentos PDF utilizando GroupDocs.Watermark para .NET. Mejore la seguridad de los documentos y el atractivo visual sin esfuerzo.
type: docs
weight: 27
url: /es/net/pdf-watermarking-attachments/rasterize-pdf-document/
---
## Introducción
En el ámbito de la gestión y manipulación de documentos, GroupDocs.Watermark para .NET se destaca como una herramienta poderosa que ofrece capacidades sólidas para agregar, eliminar y buscar marcas de agua en varios formatos de documentos. Ya sea protegiendo sus documentos con avisos de derechos de autor, agregando logotipos corporativos para la marca o simplemente anotando documentos con sellos, GroupDocs.Watermark simplifica el proceso con su API intuitiva y su amplio conjunto de funciones.
## Requisitos previos
Antes de sumergirse en el mundo de las marcas de agua con GroupDocs.Watermark para .NET, asegúrese de cumplir con los siguientes requisitos previos:
### 1. Instale .NET Framework
Asegúrese de tener .NET Framework instalado en su máquina de desarrollo. Puede descargarlo del sitio web de Microsoft o utilizar su administrador de paquetes preferido.
#### Paso 1: descargue .NET Framework
Visite la página de descarga de Microsoft .NET Framework.
#### Paso 2: Instale .NET Framework
Siga las instrucciones de instalación proporcionadas en la página de descarga para instalar .NET Framework en su sistema.
### 2. Obtenga la licencia GroupDocs.Watermark
Para utilizar todas las capacidades de GroupDocs.Watermark, necesita una licencia válida. Puede comprar una licencia u obtener una temporal para fines de evaluación.
#### Paso 1: obtenga una licencia
Visite la página de compra de GroupDocs.Watermark.
#### Paso 2: comprar u obtener una licencia temporal
Elija la opción de licencia adecuada según sus necesidades: compre una licencia para uso continuo o adquiera una licencia temporal para fines de evaluación.

## Importar espacios de nombres
Antes de comenzar a poner marcas de agua en sus documentos, asegúrese de importar los espacios de nombres necesarios para acceder a la funcionalidad de GroupDocs sin problemas.
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```

Ahora que tiene todo configurado, profundicemos en la rasterización de un documento PDF usando GroupDocs.Watermark para .NET. La rasterización convierte cada página del documento PDF en un formato de imagen rasterizada, como PNG.
## Paso 1: Inicializar variables
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
Asegúrese de reemplazar "La ruta de su documento" y "Su directorio de documentos" con la ruta real a su documento PDF y el directorio de salida deseado, respectivamente.
## Paso 2: cargue el documento y agregue una marca de agua
```csharp
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Inicializar imagen o marca de agua de texto
    TextWatermark watermark = new TextWatermark("Do not copy", new Font("Arial", 8));
    watermark.HorizontalAlignment = HorizontalAlignment.Center;
    watermark.VerticalAlignment = VerticalAlignment.Center;
    watermark.RotateAngle = 45;
    watermark.SizingType = SizingType.ScaleToParentDimensions;
    watermark.ScaleFactor = 1;
    watermark.Opacity = 0.5;
    // Agregue primero una marca de agua de cualquier tipo
    watermarker.Add(watermark);
    PdfContent pdfContent = watermarker.GetContent<PdfContent>();
    // Rasterizar todas las páginas
    pdfContent.Rasterize(100, 100, PdfImageConversionFormat.Png);
    // El contenido de todas las páginas se reemplaza con imágenes rasterizadas.
    watermarker.Save(outputFileName);
}
```
En este paso, cargamos el documento PDF e inicializamos una marca de agua de texto con propiedades específicas como texto, fuente, alineación, ángulo de rotación, tipo de tamaño, factor de escala y opacidad. Luego, agregamos la marca de agua al documento. A continuación, recuperamos el contenido del documento PDF y rasterizamos todas las páginas al formato PNG con una resolución de 100 DPI. Finalmente guardamos el documento modificado con contenido rasterizado.

## Conclusión
GroupDocs.Watermark para .NET ofrece una solución integral para agregar marcas de agua a varios formatos de documentos con facilidad. Si sigue los pasos descritos en este tutorial, podrá rasterizar eficazmente documentos PDF y mejorar su seguridad y atractivo visual.
## Preguntas frecuentes
### ¿GroupDocs.Watermark es compatible con otros formatos de documentos además de PDF?
Sí, GroupDocs.Watermark admite una amplia gama de formatos de documentos, incluidos Microsoft Word, Excel, PowerPoint, Visio, Outlook y muchos más.
### ¿Puedo personalizar la apariencia de las marcas de agua agregadas usando GroupDocs.Watermark?
¡Absolutamente! GroupDocs.Watermark ofrece amplias opciones para personalizar las propiedades de la marca de agua, como texto, fuente, color, tamaño, opacidad, rotación y posición.
### ¿GroupDocs.Watermark ofrece soporte para el procesamiento por lotes?
Sí, puede procesar fácilmente varios documentos en modo por lotes utilizando GroupDocs, lo que ahorra tiempo y esfuerzo al aplicar marcas de agua a grandes conjuntos de archivos.
### ¿Existe una versión de prueba disponible para GroupDocs.Watermark?
Sí, puede descargar una versión de prueba gratuita de GroupDocs.Watermark desde el sitio web para evaluar sus funciones antes de realizar una compra.
### ¿Cómo puedo obtener ayuda si encuentro algún problema o tengo preguntas sobre GroupDocs.Watermark?
Puede visitar el foro GroupDocs.Watermark para buscar ayuda de la comunidad o comunicarse con el equipo de soporte de GroupDocs para obtener ayuda.