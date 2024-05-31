---
title: Agregar marca de agua con efectos de texto en documentos de Word
linktitle: Agregar marca de agua con efectos de texto en documentos de Word
second_title: API GroupDocs.Watermark .NET
description: Aprenda a agregar marcas de agua personalizadas con efectos de texto a documentos de Word usando GroupDocs.Watermark para .NET. Documente la seguridad y el atractivo visual sin esfuerzo.
type: docs
weight: 21
url: /es/net/word-processing-watermarkings/add-watermark-text-effects-word-docs/
---
## Introducción
En este tutorial, exploraremos cómo agregar una marca de agua con efectos de texto a documentos de Word usando GroupDocs.Watermark para .NET. Si sigue estas instrucciones paso a paso, podrá mejorar sus documentos con marcas de agua personalizadas que incluyen varios efectos de texto.
## Requisitos previos
Antes de comenzar, asegúrese de tener lo siguiente:
1.  GroupDocs.Watermark para .NET: descargue e instale la biblioteca desde[sitio web](https://releases.groupdocs.com/Watermark/net/).
2. Ruta del documento: conozca la ruta del documento de Word al que desea agregar la marca de agua.
3. Directorio de salida: tenga un directorio donde desea guardar el documento modificado.

## Importar espacios de nombres
Asegúrese de importar los espacios de nombres necesarios para acceder a las clases y métodos requeridos:
```csharp
using GroupDocs.Watermark.Contents;
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Paso 1: cargue el documento
Cargue el documento de Word al que desea agregar la marca de agua.
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // El código para agregar una marca de agua va aquí
}
```
## Paso 2: agregue una marca de agua con efectos de texto
Cree una marca de agua de texto con el texto y la fuente deseados, luego defina efectos de texto como el formato de línea.
```csharp
TextWatermark watermark = new TextWatermark("Test watermark", new Font("Arial", 19));
WordProcessingTextEffects effects = new WordProcessingTextEffects();
effects.LineFormat.Enabled = true;
effects.LineFormat.Color = Color.Red;
effects.LineFormat.DashStyle = OfficeDashStyle.DashDotDot;
effects.LineFormat.LineStyle = OfficeLineStyle.Triple;
effects.LineFormat.Weight = 1;
```
## Paso 3: personaliza las opciones de marca de agua
Defina opciones de sección de marca de agua, como efectos de texto, y asígnelas a la marca de agua.
```csharp
WordProcessingWatermarkSectionOptions options = new WordProcessingWatermarkSectionOptions();
options.Effects = effects;
watermarker.Add(watermark, options);
```
## Paso 4: guarde el documento
Guarde el documento modificado con la marca de agua agregada.
```csharp
watermarker.Save(outputFileName);
```

## Conclusión
Agregar marcas de agua con efectos de texto a documentos de Word puede mejorar significativamente su atractivo y protección visual. Con GroupDocs.Watermark para .NET, este proceso se simplifica y se puede personalizar, lo que le permite crear documentos de apariencia profesional de manera eficiente.
## Preguntas frecuentes
### ¿Puedo personalizar la fuente y el tamaño del texto de la marca de agua?
Sí, puede especificar la fuente y el tamaño al crear el objeto TextWatermark.
### ¿Es posible agregar varias marcas de agua a un solo documento?
Por supuesto, GroupDocs.Watermark para .NET admite agregar múltiples marcas de agua con diferentes configuraciones a un solo documento.
### ¿GroupDocs.Watermark admite otros formatos de documentos además de Word?
Sí, admite una amplia gama de formatos de documentos, incluidos PDF, Excel, PowerPoint y más.
### ¿Puedo eliminar una marca de agua una vez agregada a un documento?
Sí, la biblioteca proporciona métodos para eliminar fácilmente marcas de agua de los documentos.
### ¿Existe una versión de prueba disponible para fines de prueba?
 Sí, puedes descargar una versión de prueba gratuita desde[aquí](https://releases.groupdocs.com/).