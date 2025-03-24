---
title: Agregar marca de agua de texto
linktitle: Agregar marca de agua de texto
second_title: API GroupDocs.Watermark .NET
description: Aprenda a agregar marcas de agua de texto a sus documentos usando Groupdocs Watermark para .NET con esta guía paso a paso.
weight: 11
url: /es/net/watermarking-basics/add-text-watermark/
---
## Introducción
GroupDocs.Watermark para .NET es una potente biblioteca que permite a los desarrolladores agregar, buscar y eliminar marcas de agua de varios formatos de documentos en aplicaciones .NET. En este tutorial, nos centraremos en agregar una marca de agua de texto a un documento usando GroupDocs.Watermark.
## Requisitos previos
Antes de comenzar, asegúrese de tener los siguientes requisitos previos:
1. Conocimientos básicos del lenguaje de programación C#.
2. Visual Studio instalado en su sistema.
3.  GroupDocs.Watermark para la biblioteca .NET instalada. Puedes descargarlo desde[aquí](https://releases.groupdocs.com/Watermark/net/).

## Importar espacios de nombres
Primero, necesita importar los espacios de nombres necesarios a su proyecto C#.
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Watermarks;
using System;
using System.IO;
```
## Paso 1: definir la ruta del documento y el directorio de salida
Defina la ruta a su documento de entrada y el directorio de salida donde se guardará el documento con marca de agua.
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
 Reemplazar`"Your Document Path"` con la ruta absoluta o relativa a su documento de entrada, por ejemplo:`@"C:\Docs\document.pdf"`. Además, especifique el directorio donde desea guardar el documento con marca de agua.
## Paso 2: agregar marca de agua de texto
 Instanciar el`Watermarker` clase con la ruta del documento de entrada. Luego, crea un`TextWatermark` objeto con el texto y la configuración de fuente deseados.
```csharp
using (Watermarker watermarker = new Watermarker(documentPath))
{
    TextWatermark watermark = new TextWatermark("top secret", new Font("Arial", 36));
    watermark.ForegroundColor = Color.Red;
    watermark.HorizontalAlignment = HorizontalAlignment.Center;
    watermark.VerticalAlignment = VerticalAlignment.Center;
    watermarker.Add(watermark);
    watermarker.Save(outputFileName);
}
```

## Conclusión
En este tutorial, hemos aprendido cómo agregar una marca de agua de texto a un documento usando GroupDocs.Watermark para .NET. Con su API intuitiva, los desarrolladores pueden manipular fácilmente marcas de agua en varios formatos de documentos.
## Preguntas frecuentes
### ¿GroupDocs.Watermark para .NET es compatible con todos los formatos de documentos?
GroupDocs.Watermark admite una amplia gama de formatos de documentos, incluidos PDF, Microsoft Word, Excel, PowerPoint y muchos más.
### ¿Puedo personalizar la apariencia de la marca de agua del texto?
Sí, puedes personalizar varias propiedades como fuente, color, alineación y opacidad de la marca de agua del texto.
### ¿GroupDocs.Watermark proporciona soporte para eliminar marcas de agua de documentos?
Sí, GroupDocs.Watermark ofrece funcionalidad para buscar y eliminar marcas de agua de documentos.
### ¿Puedo probar GroupDocs.Watermark para .NET antes de comprarlo?
 Sí, puedes descargar una versión de prueba gratuita desde[aquí](https://releases.groupdocs.com/).
### ¿Cómo puedo obtener soporte técnico para GroupDocs.Watermark?
 Puede obtener soporte técnico visitando el[Foro GroupDocs.Watermark](https://forum.groupdocs.com/c/watermark/19).