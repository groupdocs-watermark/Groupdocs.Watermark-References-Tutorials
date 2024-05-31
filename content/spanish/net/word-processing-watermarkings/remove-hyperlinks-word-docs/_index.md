---
title: Eliminar hipervínculos en documentos de Word
linktitle: Eliminar hipervínculos en documentos de Word
second_title: API GroupDocs.Watermark .NET
description: Aprenda cómo eliminar hipervínculos de documentos de Word usando GroupDocs.Watermark para .NET. Mejore la seguridad de los documentos sin esfuerzo.
type: docs
weight: 29
url: /es/net/word-processing-watermarkings/remove-hyperlinks-word-docs/
---
## Introducción
En el mundo digital actual, donde la información fluye sin problemas, proteger sus documentos es primordial. Ya sea que esté compartiendo datos comerciales confidenciales o creando una obra maestra, proteger su contenido contra el acceso y la manipulación no autorizados es crucial. Con la llegada de GroupDocs.Watermark para .NET, puede garantizar la integridad de sus documentos agregando, eliminando y detectando marcas de agua con facilidad.
## Requisitos previos
Antes de sumergirse en el mundo de las marcas de agua en documentos con GroupDocs.Watermark para .NET, existen algunos requisitos previos que debe cumplir:
1.  Instalación de GroupDocs.Watermark para .NET: visite el[enlace de descarga](https://releases.groupdocs.com/Watermark/net/) para adquirir los archivos necesarios para la instalación. Siga las instrucciones de instalación proporcionadas en la documentación.
2. Comprensión básica de .NET Framework: familiarícese con .NET Framework y sus fundamentos para navegar por los ejemplos de codificación sin esfuerzo.
3. Acceso a un editor de texto o IDE: asegúrese de tener un editor de texto o un entorno de desarrollo integrado (IDE), como Visual Studio, instalado en su sistema para fines de codificación.

## Importar espacios de nombres
Antes de profundizar en la guía paso a paso, asegúrese de importar los espacios de nombres necesarios en su proyecto C#:
```csharp
using GroupDocs.Watermark.Contents.WordProcessing;
using GroupDocs.Watermark.Options.WordProcessing;
using System.IO;
using System;
```
## Paso 1: cargue el documento
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
```
## Paso 2: obtenga contenido de procesamiento de textos
```csharp
    WordProcessingContent content = watermarker.GetContent<WordProcessingContent>();
```
## Paso 3: reemplazar el hipervínculo
```csharp
    // Reemplazar hipervínculo
    content.Sections[0].Shapes[0].Hyperlink = "https://www.groupdocs.com/”;
```
## Paso 4: eliminar el hipervínculo
```csharp
    // Eliminar hipervínculo
    content.Sections[0].Shapes[1].Hyperlink = null;
```
## Paso 5: guarde el documento
```csharp
    watermarker.Save(outputFileName);
}
```

## Conclusión
GroupDocs.Watermark para .NET permite a los desarrolladores manipular marcas de agua sin esfuerzo, garantizando la seguridad e integridad de los documentos. Si sigue la guía paso a paso descrita anteriormente, podrá eliminar sin problemas los hipervínculos de los documentos de Word, mejorando así la confidencialidad y el profesionalismo.
## Preguntas frecuentes
### ¿GroupDocs.Watermark es compatible con otros formatos de documentos?
Sí, GroupDocs.Watermark admite una amplia gama de formatos de documentos, incluidos PDF, Excel, PowerPoint y más.
### ¿Puedo personalizar la apariencia de las marcas de agua usando GroupDocs.Watermark?
¡Absolutamente! GroupDocs.Watermark ofrece amplias opciones de personalización para marcas de agua, lo que le permite ajustar su posición, tamaño, opacidad y más.
### ¿GroupDocs.Watermark proporciona soporte para el procesamiento por lotes?
Sí, puedes procesar por lotes varios documentos simultáneamente con GroupDocs, ahorrando tiempo y esfuerzo.
### ¿Existe una versión de prueba disponible para GroupDocs.Watermark?
 Sí, puede explorar las funciones de GroupDocs.Watermark descargando la versión de prueba gratuita desde[aquí](https://releases.groupdocs.com/).
### ¿Cómo puedo obtener licencias temporales para GroupDocs.Watermark?
 Las licencias temporales para GroupDocs se pueden obtener en el sitio web.[aquí](https://purchase.groupdocs.com/temporary-license/).