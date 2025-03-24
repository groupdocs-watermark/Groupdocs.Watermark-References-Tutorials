---
title: Agregar marca de agua de imagen en mosaico
linktitle: Agregar marca de agua de imagen en mosaico
second_title: API GroupDocs.Watermark .NET
description: Aprenda a agregar marcas de agua de imágenes en mosaico a sus documentos usando GroupDocs.Watermark para .NET. Fácil, eficiente y personalizable.
weight: 10
url: /es/net/image-watermarkings/add-tiled-image-watermark/
---

# Agregar marca de agua de imagen en mosaico

## Introducción
GroupDocs.Watermark para .NET es una potente API que permite a los desarrolladores agregar, eliminar y buscar marcas de agua en varios formatos de documentos mediante programación. En este tutorial, lo guiaremos a través del proceso de agregar una marca de agua de imagen en mosaico a sus documentos usando GroupDocs.Watermark para .NET.
## Requisitos previos
Antes de comenzar, asegúrese de tener lo siguiente:
- Conocimientos básicos del lenguaje de programación C#.
- Visual Studio instalado en su sistema.
- Biblioteca GroupDocs.Watermark para .NET agregada a su proyecto. Puedes descargarlo desde[aquí](https://releases.groupdocs.com/Watermark/net/).

## Importar espacios de nombres
Asegúrese de importar los espacios de nombres necesarios al principio de su archivo C#:
```csharp
using GroupDocs.Watermark.Watermarks;
using System;
using System.IO;
```
## Paso 1: establecer la ruta del documento y el directorio de salida
Defina la ruta de su documento de entrada y el directorio donde desea guardar el documento de salida:
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
 Reemplazar`"Your Document Path"` con la ruta absoluta o relativa a su documento de entrada.
## Paso 2: inicializar el objeto de marca de agua
Cree un objeto Watermarker utilizando la ruta del documento de entrada:
```csharp
using (Watermarker watermarker = new Watermarker(documentPath))
{
    // Añadir marca de agua aquí
}
```
## Paso 3: agregar marca de agua de imagen en mosaico
Cree una instancia de un objeto ImageWatermark con la ruta al archivo de imagen que desea usar como marca de agua:
```csharp
using (ImageWatermark watermark = new ImageWatermark("Path to Your Image"))
{
    // Configurar opciones de mosaico
    watermark.TileOptions = new TileOptions()
    {
        TileType = TileType.Offset,
        LineSpacing = new MeasureValue()
        {
            MeasureType = TileMeasureType.Percent,
            Value = 12
        },
        WatermarkSpacing = new MeasureValue()
        {
            MeasureType = TileMeasureType.Percent,
            Value = 10
        },
    };
    watermark.RotateAngle = -30;
    // Agregar marca de agua al documento
    watermarker.Add(watermark);
    // Guardar el documento modificado
    watermarker.Save(outputFileName);
}
```
 Reemplazar`"Path to Your Image"` con la ruta real a su archivo de imagen de marca de agua.

## Conclusión
Si sigue estos pasos, puede agregar fácilmente una marca de agua de imagen en mosaico a sus documentos usando GroupDocs.Watermark para .NET. Experimente con diferentes opciones y configuraciones para lograr el resultado deseado.
## Preguntas frecuentes
### ¿Puedo agregar varias marcas de agua a un solo documento?
Sí, puede agregar varias marcas de agua de diferentes tipos a un documento utilizando GroupDocs.Watermark para .NET.
### ¿GroupDocs.Watermark admite todos los formatos de documentos?
GroupDocs.Watermark admite una amplia gama de formatos de documentos, incluidos PDF, Word, Excel, PowerPoint y muchos más.
### ¿Existe una versión de prueba disponible para GroupDocs.Watermark?
 Sí, puedes descargar una versión de prueba gratuita desde[aquí](https://releases.groupdocs.com/).
### ¿Puedo personalizar la apariencia de la marca de agua?
Sí, puedes personalizar varios aspectos de la marca de agua, como posición, tamaño, rotación, transparencia, etc.
### ¿GroupDocs.Watermark ofrece soporte técnico?
 Sí, puede obtener soporte técnico en el foro GroupDocs.Watermark.[aquí](https://forum.groupdocs.com/c/watermark/19).