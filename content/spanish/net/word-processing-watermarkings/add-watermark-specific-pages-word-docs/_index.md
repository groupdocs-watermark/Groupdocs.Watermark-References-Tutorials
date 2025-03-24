---
title: Agregar marca de agua a páginas específicas en documentos de Word
linktitle: Agregar marca de agua a páginas específicas en documentos de Word
second_title: API GroupDocs.Watermark .NET
description: Aprenda a agregar marcas de agua a páginas específicas en documentos de Word sin esfuerzo usando Groupdocs para .NET. Mejore la seguridad de los documentos y la marca.
weight: 18
url: /es/net/word-processing-watermarkings/add-watermark-specific-pages-word-docs/
---

# Agregar marca de agua a páginas específicas en documentos de Word

## Introducción
En este tutorial, recorreremos el proceso de agregar marcas de agua a páginas específicas en documentos de Word usando Groupdocs.Watermark para .NET. La marca de agua es un aspecto crucial de la gestión de documentos, ya que proporciona seguridad y marca para sus documentos. Con Groupdocs.Watermark para .NET, puede agregar fácilmente marcas de agua de texto o imágenes a sus documentos de Word con precisión y eficiencia.
## Requisitos previos
Antes de comenzar, asegúrese de tener los siguientes requisitos previos:
1.  Groupdocs.Watermark para .NET: descargue e instale Groupdocs.Watermark para .NET desde[aquí](https://releases.groupdocs.com/Watermark/net/).
2. Documento: tenga listo el documento de Word al que desea ponerle una marca de agua.
3. Entorno de desarrollo: configure su entorno de desarrollo con Visual Studio o cualquier otra herramienta de desarrollo .NET.

## Importar espacios de nombres
Antes de profundizar en el código, importemos los espacios de nombres necesarios:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
```
## Paso 1: cargue el documento
Primero, necesitamos cargar el documento de Word en el objeto de marca de agua.
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Agregar código de marca de agua irá aquí
}
```
## Paso 2: agregar marca de agua
Ahora, agreguemos una marca de agua de texto a páginas específicas del documento.
```csharp
TextWatermark textWatermark = new TextWatermark("DRAFT", new Font("Arial", 42));
textWatermark.PagesSetup = new PagesSetup
{
    Pages = new List<int> { 2, 3 } // Especifique las páginas para agregar la marca de agua.
};
watermarker.Add(textWatermark);
```
## Paso 3: guarde el documento
Finalmente, guarde el documento con marca de agua en la ubicación deseada.
```csharp
watermarker.Save(outputFileName);
```

## Conclusión
En este tutorial, aprendimos cómo agregar marcas de agua a páginas específicas en documentos de Word usando Groupdocs.Watermark para .NET. Con sólo unas pocas líneas de código, puede mejorar la seguridad y la marca de sus documentos sin esfuerzo.
## Preguntas frecuentes
### ¿Puedo agregar varias marcas de agua a un solo documento?
Sí, puede agregar varias marcas de agua repitiendo el proceso de adición de marcas de agua para cada marca de agua.
### ¿Groupdocs.Watermark admite otros formatos de documentos además de Word?
Sí, Groupdocs admite una amplia gama de formatos de documentos, incluidos PDF, Excel, PowerPoint y más.
### ¿Hay una versión de prueba disponible?
 Sí, puedes descargar una versión de prueba gratuita desde[aquí](https://releases.groupdocs.com/).
### ¿Puedo personalizar la apariencia de la marca de agua?
Por supuesto, puedes personalizar varios aspectos de la marca de agua, como la fuente, el tamaño, el color y la opacidad.
### ¿Hay soporte técnico disponible?
 Sí, puedes encontrar soporte técnico y recursos en el foro de Groupdocs.[aquí](https://forum.groupdocs.com/c/watermark/19).