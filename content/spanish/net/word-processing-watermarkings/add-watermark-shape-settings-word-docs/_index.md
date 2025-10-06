---
title: Agregar marca de agua con configuración de forma en documentos de Word
linktitle: Agregar marca de agua con configuración de forma en documentos de Word
second_title: API GroupDocs.Watermark .NET
description: Aprenda a agregar marcas de agua con configuraciones de forma a documentos de Word usando GroupDocs para .NET. Proteja sus documentos de manera efectiva.
weight: 20
url: /es/net/word-processing-watermarkings/add-watermark-shape-settings-word-docs/
type: docs
---
# Agregar marca de agua con configuración de forma en documentos de Word

## Introducción
En este tutorial, recorreremos el proceso de agregar una marca de agua con configuraciones de forma a documentos de Word usando GroupDocs.Watermark para .NET.
## Requisitos previos
Antes de comenzar, asegúrese de tener lo siguiente:
1.  GroupDocs.Watermark para .NET instalado. Puedes descargarlo desde[aquí](https://releases.groupdocs.com/Watermark/net/).
2. Conocimientos básicos de programación en C#.
3. Comprensión del procesamiento de documentos de Word.

## Importar espacios de nombres
Primero, debe importar los espacios de nombres necesarios para acceder a las clases y métodos requeridos.
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Paso 1: cargue el documento
Cargue el documento de Word donde desea agregar la marca de agua.
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // El código de adición de marca de agua va aquí
}
```
## Paso 2: agregar marca de agua
 Crear una instancia de`TextWatermark` objeto y especifique el texto que desea utilizar como marca de agua.
```csharp
TextWatermark watermark = new TextWatermark("Test watermark", new Font("Arial", 19));
```
## Paso 3: personaliza la configuración de la marca de agua
Establezca varias configuraciones para la marca de agua, como alineación, ángulo de rotación, color y opacidad.
```csharp
watermark.VerticalAlignment = VerticalAlignment.Center;
watermark.HorizontalAlignment = HorizontalAlignment.Center;
watermark.RotateAngle = 25.0;
watermark.ForegroundColor = Color.Red;
watermark.Opacity = 1.0;
```
## Paso 4: definir las opciones de la sección de marca de agua
Defina opciones para la sección de marca de agua, como el nombre de la forma y el texto alternativo.
```csharp
WordProcessingWatermarkSectionOptions options = new WordProcessingWatermarkSectionOptions();
options.Name = "Shape 1";
options.AlternativeText = "Test watermark";
```
## Paso 5: agregar marca de agua al documento
Agregue la marca de agua al documento con las opciones especificadas.
```csharp
watermarker.Add(watermark, options);
```
## Paso 6: guarde el documento
Guarde el documento con la marca de agua agregada.
```csharp
watermarker.Save(outputFileName);
```

## Conclusión
Agregar marcas de agua con configuraciones de forma a documentos de Word usando GroupDocs para .NET es un proceso sencillo. Si sigue los pasos descritos en este tutorial, podrá proteger eficazmente sus documentos con marcas de agua personalizadas.
## Preguntas frecuentes
### ¿Puedo agregar varias marcas de agua al mismo documento?
Sí, puedes agregar varias marcas de agua con diferentes configuraciones al mismo documento.
### ¿GroupDocs.Watermark admite otros formatos de documentos además de Word?
Sí, GroupDocs.Watermark admite varios formatos de documentos, incluidos Excel, PowerPoint, PDF y más.
### ¿Puedo personalizar aún más la apariencia de la marca de agua?
Por supuesto, puede ajustar varios parámetros, como el tamaño de fuente, el estilo, el color y la posición, para adaptarlos a sus necesidades.
### ¿Existe una versión de prueba disponible para GroupDocs.Watermark para .NET?
 Sí, puedes obtener una prueba gratuita desde[aquí](https://releases.groupdocs.com/).
### ¿Dónde puedo encontrar soporte para GroupDocs.Watermark?
 Puede encontrar soporte y hacer preguntas en el foro de GroupDocs.[aquí](https://forum.groupdocs.com/c/watermark/19).