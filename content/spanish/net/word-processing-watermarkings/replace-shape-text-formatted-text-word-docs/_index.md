---
title: Reemplazar texto de forma con texto formateado en documentos de Word
linktitle: Reemplazar texto de forma con texto formateado en documentos de Word
second_title: API GroupDocs.Watermark .NET
description: Aprenda a reemplazar texto de forma con texto formateado en documentos de Word usando GroupDocs.Watermark para .NET. Sus capacidades de edición de documentos sin esfuerzo.
weight: 34
url: /es/net/word-processing-watermarkings/replace-shape-text-formatted-text-word-docs/
type: docs
---
# Reemplazar texto de forma con texto formateado en documentos de Word

## Introducción
En este tutorial, lo guiaremos a través del proceso de reemplazar texto de forma con texto formateado en documentos de Word usando GroupDocs.Watermark para .NET. Esta biblioteca proporciona potentes funciones para trabajar con marcas de agua, incluida la sustitución de texto dentro de formas.
## Requisitos previos
Antes de comenzar, asegúrese de tener los siguientes requisitos previos:
1.  GroupDocs.Watermark para .NET: asegúrese de haber instalado y configurado GroupDocs.Watermark para .NET. Puedes descargarlo desde[aquí](https://releases.groupdocs.com/Watermark/net/).
2. Ruta del documento: debe tener la ruta al documento de Word donde desea reemplazar el texto.

## Importar espacios de nombres
Antes de escribir el código, importe los espacios de nombres necesarios:
```csharp
using GroupDocs.Watermark.Contents.WordProcessing;
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Paso 1: cargue el documento
 Cargue el documento de Word usando el`Watermarker` clase:
```csharp
string documentPath = "Your Document Path";
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Tu código continúa aquí...
}
```
## Paso 2: obtener contenido y reemplazar texto
Una vez cargado el documento, obtenga el contenido y reemplace el texto dentro de las formas:
```csharp
WordProcessingContent content = watermarker.GetContent<WordProcessingContent>();
foreach (WordProcessingShape shape in content.Sections[0].Shapes)
{
    if (shape.Text.Contains("Some text"))
    {
        shape.FormattedTextFragments.Clear();
        shape.FormattedTextFragments.Add("Another text", new Font("Calibri", 19, FontStyle.Bold), Color.Red, Color.Aqua);
    }
}
```
## Paso 3: guarde el documento
Después de reemplazar el texto, guarde el documento modificado:
```csharp
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
watermarker.Save(outputFileName);
```

## Conclusión
Reemplazar texto de forma con texto formateado en documentos de Word es fácil con GroupDocs para .NET. Si sigue los pasos descritos en este tutorial, podrá administrar y manipular de manera eficiente el texto dentro de sus documentos.

## Preguntas frecuentes
### ¿Puedo reemplazar texto en otros tipos de documentos usando GroupDocs.Watermark para .NET?
Sí, GroupDocs admite varios formatos de documentos, como PDF, Excel, PowerPoint y más.
### ¿GroupDocs.Watermark es compatible con .NET Core?
Sí, GroupDocs.Watermark es compatible con .NET Framework y .NET Core.
### ¿GroupDocs.Watermark proporciona soporte para agregar imágenes como marcas de agua?
Por supuesto, GroupDocs.Watermark le permite agregar marcas de agua de texto e imagen a sus documentos.
### ¿Puedo personalizar la apariencia de las marcas de agua agregadas usando GroupDocs.Watermark?
Sí, tienes control total sobre la apariencia, posición y otras propiedades de las marcas de agua.
### ¿Existe una versión de prueba disponible para GroupDocs.Watermark para .NET?
 Sí, puedes descargar una prueba gratuita desde[aquí](https://releases.groupdocs.com/).