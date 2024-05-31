---
title: Cargar documento desde el disco local
linktitle: Cargar documento desde el disco local
second_title: API GroupDocs.Watermark .NET
description: Proteja y administre sus documentos con Groupdocs. Siga nuestra guía detallada para agregar marcas de agua sin problemas.
type: docs
weight: 10
url: /es/net/document-loadings/load-document-from-local-disk/
---
## Introducción
Poner marcas de agua en los documentos es esencial en la era digital actual para garantizar la protección del contenido, la afirmación de la propiedad y la confidencialidad. Groupdocs.Watermark para .NET es una poderosa biblioteca que permite a los desarrolladores agregar, buscar y administrar marcas de agua en varios formatos de documentos. En este tutorial, recorreremos el proceso de uso de Groupdocs.Watermark para .NET para agregar marcas de agua a sus documentos con instrucciones detalladas paso a paso.
## Requisitos previos
Antes de sumergirse en la implementación, asegúrese de tener lo siguiente:
1. Visual Studio instalado: necesitará Visual Studio u otro IDE .NET compatible.
2.  Groupdocs.Watermark para .NET: descargue la biblioteca desde[enlace de descarga](https://releases.groupdocs.com/Watermark/net/).
3. .NET Framework: asegúrese de tener instalado .NET Framework 4.6.1 o superior.
4. Un documento de muestra: prepare un documento de muestra para probar el proceso de marca de agua.
## Importar espacios de nombres
Para comenzar, deberá importar los espacios de nombres necesarios en su proyecto. Estos son esenciales para acceder a las clases y métodos necesarios para la marca de agua.
```csharp
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Paso 1: cargar el documento desde el disco local
Primero, debe cargar el documento desde su disco local. Este documento será aquel al que le agregarás una marca de agua.
Defina la ruta del documento al que desea ponerle una marca de agua.
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
```
## Paso 2: Inicializar las opciones de carga
 A continuación, inicialice las opciones de carga. Por ejemplo, si está trabajando con un documento de Word, usará`WordProcessingLoadOptions`.
```csharp
var loadOptions = new WordProcessingLoadOptions();
```
## Paso 3: crear y configurar el marcador de agua
 Ahora, creará una instancia del`Watermarker` clase. Esta instancia se utilizará para administrar y aplicar marcas de agua a su documento.
```csharp
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Este bloque contendrá pasos adicionales para agregar y guardar la marca de agua.
}
```
## Paso 4: crea una marca de agua
Crea una marca de agua de texto. Esta marca de agua puede contener cualquier texto que elija. Aquí usaremos "Marca de agua de prueba".
```csharp
TextWatermark watermark = new TextWatermark("Test watermark", new Font("Arial", 12));
```
## Paso 5: agregue una marca de agua al documento
Agregue la marca de agua creada al documento usando el`Add` método de la`Watermarker` clase.
```csharp
watermarker.Add(watermark);
```
## Paso 6: guarde el documento con marca de agua
Finalmente, guarde el documento con marca de agua en la ruta especificada.
```csharp
watermarker.Save(outputFileName);
```

## Conclusión
Agregar marcas de agua a sus documentos usando Groupdocs Watermark para .NET es sencillo y eficiente. Esta guía lo ha guiado a través de todo el proceso, desde configurar su entorno hasta guardar un documento con marca de agua. Con esta poderosa herramienta, puede asegurarse de que sus documentos estén protegidos y su propiedad intelectual esté segura. 
 Para más detalles, consulte el[documentación](https://reference.groupdocs.com/Watermark/net/) , y si encuentra algún problema, el[Foro de soporte](https://forum.groupdocs.com/c/watermark/19) es un excelente lugar para recibir asistencia. 
## Preguntas frecuentes
### ¿Puedo usar fuentes personalizadas para marcas de agua?
Sí, Groupdocs admite fuentes personalizadas. Puede especificar cualquier fuente instalada en su sistema.
### ¿Qué tipos de documentos se admiten?
Groupdocs.Watermark admite una amplia gama de formatos de documentos, incluidos Word, Excel, PDF, PowerPoint y más.
### ¿Cómo puedo eliminar una marca de agua de un documento?
 Puedes usar el`Remove` método proporcionado por el`Watermarker` clase para eliminar marcas de agua.
### ¿Es posible agregar marcas de agua a las imágenes?
 Sí, puedes agregar marcas de agua a las imágenes usando el`ImageWatermark` clase.
### ¿Puedo probar Groupdocs.Watermark gratis?
 Por supuesto, puedes descargar un[prueba gratis](https://releases.groupdocs.com/) evaluar la biblioteca antes de comprarla.