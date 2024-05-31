---
title: Agregar marcas de agua a PDF
linktitle: Agregar marcas de agua a PDF
second_title: API GroupDocs.Watermark .NET
description: Aprenda a agregar marcas de agua de texto e imágenes a sus archivos PDF usando GroupDocs.Watermark para .NET con nuestra guía completa paso a paso.
type: docs
weight: 14
url: /es/net/pdf-watermarking-attachments/add-watermarks-pdf/
---
## Introducción
¿Está buscando agregar marcas de agua a sus archivos PDF para proteger sus documentos o marcarlos con su logotipo? ¡No busque más! En este tutorial, profundizaremos en el proceso de uso de GroupDocs.Watermark para .NET para agregar marcas de agua de texto e imagen a sus archivos PDF. Ya sea que sea un desarrollador experimentado o recién esté comenzando, esta guía lo guiará en cada paso, asegurándole que pueda aplicar marcas de agua con facilidad y precisión.
## Requisitos previos
Antes de comenzar, asegurémonos de que tiene todo lo que necesita para seguir este tutorial:
-  GroupDocs.Watermark para .NET: asegúrese de tener instalada la última versión. Puede[descarguelo aqui](https://releases.groupdocs.com/Watermark/net/).
- Entorno de desarrollo .NET: Visual Studio o cualquier otro IDE que admita .NET.
- Conocimientos básicos de C#: comprender los conceptos básicos de la programación en C# le ayudará a seguir los pasos con facilidad.
- Documento PDF: tenga un documento PDF de muestra listo para colocarle una marca de agua.
- Imagen para marca de agua: si está agregando una marca de agua de imagen, tenga listo su archivo de imagen.
## Importar espacios de nombres
Primero, necesita importar los espacios de nombres necesarios en su proyecto C#. Esto le permitirá acceder a la funcionalidad GroupDocs.Watermark.
```csharp
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
Ahora, dividamos el proceso en pasos manejables.
## Paso 1: cargue su documento PDF
El primer paso es cargar su documento PDF en la marca de agua. Así es como puedes hacerlo:
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Se agregarán más pasos aquí.
}
```
## Paso 2: agregue una marca de agua de texto a la primera página
continuación, agregaremos una marca de agua de texto a la primera página de su PDF. Siga estas instrucciones:
```csharp
// Agregar marca de agua de texto a la primera página
TextWatermark textWatermark = new TextWatermark("This is a test watermark", new Font("Arial", 8));
PdfArtifactWatermarkOptions textWatermarkOptions = new PdfArtifactWatermarkOptions();
textWatermarkOptions.PageIndex = 0;
watermarker.Add(textWatermark, textWatermarkOptions);
```

Agregar una marca de agua de texto puede ayudar a proteger su documento contra el uso no autorizado o simplemente marcarlo. Imagínese sellar su documento con un sello invisible de autenticidad.
## Paso 3: agregue una marca de agua de imagen a la segunda página
Ahora, agreguemos una marca de agua de imagen a la segunda página. Esto es particularmente útil para logotipos o cualquier marca de agua gráfica.
```csharp
// Agregar marca de agua de imagen a la segunda página
using (ImageWatermark imageWatermark = new ImageWatermark("Your Image Path"))
{
    PdfArtifactWatermarkOptions imageWatermarkOptions = new PdfArtifactWatermarkOptions();
    imageWatermarkOptions.PageIndex = 1;
    watermarker.Add(imageWatermark, imageWatermarkOptions);
}
```

Las marcas de agua de imagen pueden hacer que sus documentos luzcan profesionales y garantizar que su marca esté siempre visible. Es como agregar tu firma a cada página.
## Paso 4: guarde el PDF con marca de agua
Después de agregar las marcas de agua, el último paso es guardar el PDF con la marca de agua en la ubicación deseada.
```csharp
watermarker.Save(outputFileName);
```
Al guardar el documento se finalizan todos los cambios realizados. Este es el momento en que sus esfuerzos se solidifican en un resultado tangible, listo para su uso o distribución.
## Conclusión
¡Felicidades! Ha agregado con éxito marcas de agua de texto e imagen a su PDF usando GroupDocs.Watermark para .NET. Este proceso no sólo es sencillo sino también altamente personalizable para adaptarse a sus necesidades específicas. Ya sea que esté protegiendo sus documentos o poniéndoles una marca, las marcas de agua son una poderosa herramienta a su disposición.
## Preguntas frecuentes
### ¿Puedo agregar varias marcas de agua a la misma página?
 Sí, puede agregar varias marcas de agua a la misma página llamando al`Add` método varias veces con diferentes objetos de marca de agua.
### ¿Cómo puedo personalizar la apariencia de la marca de agua del texto?
 Puede personalizar la marca de agua del texto ajustando propiedades como fuente, tamaño, color y opacidad usando el`TextWatermark` objeto.
### ¿Es posible poner marcas de agua solo en páginas específicas de un PDF?
 Sí, puede especificar qué páginas agregar marcas de agua configurando el`PageIndex` propiedad en el`PdfArtifactWatermarkOptions`.
### ¿Puedo eliminar marcas de agua de un PDF?
Sí, GroupDocs.Watermark proporciona funcionalidad para buscar y eliminar marcas de agua de documentos PDF.
### ¿Cómo obtengo una licencia temporal para GroupDocs.Watermark?
Puede obtener una licencia temporal visitando el[página de licencia temporal](https://purchase.groupdocs.com/temporary-license/).