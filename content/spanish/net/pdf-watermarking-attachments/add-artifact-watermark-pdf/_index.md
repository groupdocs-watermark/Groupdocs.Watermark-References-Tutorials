---
title: Agregar marca de agua de artefacto a PDF
linktitle: Agregar marca de agua de artefacto a PDF
second_title: API GroupDocs.Watermark .NET
description: Aprenda a agregar marcas de agua de artefactos a archivos PDF sin esfuerzo usando Groupdocs.Watermark para .NET. Proteja sus documentos con facilidad.
weight: 11
url: /es/net/pdf-watermarking-attachments/add-artifact-watermark-pdf/
---
## Introducción
Agregar marcas de agua a archivos PDF es un aspecto crucial de la gestión de documentos, especialmente cuando se trata de proteger la propiedad intelectual o los documentos de marca. Groupdocs.Watermark para .NET proporciona una solución sólida para agregar marcas de agua a archivos PDF sin esfuerzo. En este tutorial, recorreremos paso a paso el proceso de agregar una marca de agua de artefacto a archivos PDF.
## Requisitos previos
Antes de comenzar, asegúrese de tener los siguientes requisitos previos:
1.  Groupdocs.Watermark para .NET: descargue e instale Groupdocs.Watermark para .NET desde[aquí](https://releases.groupdocs.com/Watermark/net/).
2. Entorno de desarrollo: Tener configurado un entorno de desarrollo .NET.
3. Documento PDF: prepare el documento PDF al que desea agregar la marca de agua.
4. Directorio de salida: cree un directorio para guardar el archivo PDF con marca de agua.

## Importando espacios de nombres
Para empezar, importe los espacios de nombres necesarios en su proyecto C#:
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Paso 1: cargue el documento PDF
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
```
## Paso 2: definir opciones de marca de agua
```csharp
PdfArtifactWatermarkOptions options = new PdfArtifactWatermarkOptions();
```
## Paso 3: agregar marca de agua de texto
```csharp
TextWatermark textWatermark = new TextWatermark("This is an artifact watermark", new Font("Arial", 8));
textWatermark.HorizontalAlignment = HorizontalAlignment.Right;
watermarker.Add(textWatermark, options);
```
## Paso 4: agregar marca de agua a la imagen
```csharp
using (ImageWatermark imageWatermark = new ImageWatermark(Constants.LogoBmp))
{
    watermarker.Add(imageWatermark, options);
}
```
## Paso 5: guarde el PDF con marca de agua
```csharp
watermarker.Save(outputFileName);
```

## Conclusión
En este tutorial, aprendimos cómo agregar marcas de agua de artefactos a archivos PDF usando Groupdocs.Watermark para .NET. Si sigue estos pasos, podrá integrar perfectamente la funcionalidad de marcas de agua en sus aplicaciones .NET, garantizando la seguridad e integridad de sus documentos.
## Preguntas frecuentes
### ¿Puedo personalizar la apariencia de la marca de agua del texto?
Sí, puedes personalizar varios aspectos como la fuente, el tamaño, el color y la alineación de la marca de agua del texto según tus preferencias.
### ¿Grupodocs.Watermark admite la adición de marcas de agua a otros formatos de documentos?
Sí, Groupdocs.Watermark admite la adición de marcas de agua a una amplia gama de formatos de documentos, incluidos Word, Excel, PowerPoint y más.
### ¿Existe una versión de prueba disponible para Groupdocs.Watermark para .NET?
 Sí, puedes descargar una versión de prueba gratuita desde[aquí](https://releases.groupdocs.com/).
### ¿Cómo puedo obtener asistencia para cualquier problema o consulta relacionada con Groupdocs.Watermark?
 Puede obtener soporte en el foro de la comunidad Groupdocs.[aquí](https://forum.groupdocs.com/c/watermark/19).
### ¿Puedo utilizar Groupdocs.Watermark con fines comerciales?
Sí, puede adquirir una licencia para uso comercial en[aquí](https://purchase.groupdocs.com/buy).