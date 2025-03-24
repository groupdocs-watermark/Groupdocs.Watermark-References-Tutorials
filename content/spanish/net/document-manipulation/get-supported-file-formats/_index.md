---
title: Obtenga formatos de archivo compatibles
linktitle: Obtenga formatos de archivo compatibles
second_title: API GroupDocs.Watermark .NET
description: Agregue marcas de agua a sus documentos sin esfuerzo usando GroupDocs.Watermark para .NET. Siga nuestra guía completa paso a paso para proteger sus activos digitales.
weight: 13
url: /es/net/document-manipulation/get-supported-file-formats/
---
## Introducción
Poner marcas de agua en sus documentos es un paso crucial para proteger sus activos digitales. Ya sea para proteger la propiedad intelectual, garantizar la confidencialidad o simplemente la marca, las marcas de agua desempeñan un papel vital. Si es un desarrollador de .NET y busca integrar capacidades de marcas de agua en sus aplicaciones, GroupDocs.Watermark para .NET es una herramienta poderosa y versátil que debe considerar. Este tutorial lo guiará a través de los conceptos básicos del uso de GroupDocs.Watermark, desde la instalación hasta la aplicación de su primera marca de agua, desglosando cada paso para garantizar que pueda seguirlo fácilmente.
## Requisitos previos
Antes de profundizar en los detalles, asegurémonos de que tiene todo lo que necesita para comenzar:
1.  Visual Studio: asegúrese de tener Visual Studio instalado en su máquina. Puedes descargarlo desde el[Sitio web de Visual Studio](https://visualstudio.microsoft.com/).
2. .NET Framework: GroupDocs.Watermark admite varias versiones de .NET Framework. Asegúrese de que su proyecto tenga como objetivo una versión compatible.
3. GroupDocs.Watermark para .NET: puede descargar la última versión desde[página de lanzamiento](https://releases.groupdocs.com/Watermark/net/).
4. Conocimientos básicos de C#: este tutorial asume que tiene un conocimiento fundamental del desarrollo de C# y .NET.
## Importar espacios de nombres
Primero, importemos los espacios de nombres necesarios en su proyecto. Abra su archivo C# y agregue lo siguiente usando directivas en la parte superior:
```csharp
using System;
using System.Collections.Generic;
using GroupDocs.Watermark.Common;
```
Una vez importados estos espacios de nombres, estará listo para comenzar a agregar marcas de agua a sus documentos.

## Paso 1: inicialice el motor de marca de agua
 El primer paso es inicializar el motor de marcas de agua. Esto implica crear una instancia del`Watermarker` clase con el documento al que desea ponerle una marca de agua.
```csharp
string documentPath = "path/to/your/document.pdf";
Watermarker watermarker = new Watermarker(documentPath);
```
 Este fragmento de código configura el`Watermarker` objeto, que utilizará para aplicar marcas de agua a su documento.
## Paso 2: agregue una marca de agua de texto
Ahora, agreguemos una marca de agua de texto simple a su documento. Las marcas de agua de texto son excelentes para agregar etiquetas como "Confidencial" o "Borrador".
```csharp
TextWatermark textWatermark = new TextWatermark("Confidential", new Font("Arial", 36));
textWatermark.ForegroundColor = Color.Red;
textWatermark.HorizontalAlignment = HorizontalAlignment.Center;
textWatermark.VerticalAlignment = VerticalAlignment.Center;
watermarker.Add(textWatermark);
```
 Aquí hemos creado un`TextWatermark`objeto con el texto "Confidencial", establezca su fuente y color, y lo alineó con el centro del documento.
## Paso 3: agregue una marca de agua de imagen
Si prefiere utilizar una imagen como marca de agua, GroupDocs.Watermark se lo pone fácil.
```csharp
ImageWatermark imageWatermark = new ImageWatermark("path/to/watermark.png");
imageWatermark.Width = 100;
imageWatermark.Height = 100;
imageWatermark.HorizontalAlignment = HorizontalAlignment.Right;
imageWatermark.VerticalAlignment = VerticalAlignment.Top;
watermarker.Add(imageWatermark);
```
 En este ejemplo, creamos un`ImageWatermark` objeto, establezca sus dimensiones y alinéelo con la esquina superior derecha del documento.
## Paso 4: guarde el documento
Después de agregar las marcas de agua deseadas, el último paso es guardar el documento modificado.
```csharp
watermarker.Save("path/to/output/document.pdf");
watermarker.Dispose();
```
 Esto guardará el documento con marca de agua en la ruta especificada y liberará todos los recursos utilizados por él.`Watermarker` instancia.
## Paso 5: obtenga formatos de archivo compatibles
Para ver qué formatos de archivo son compatibles con GroupDocs.Watermark, puede utilizar el siguiente fragmento de código:
```csharp
IEnumerable<FileType> supportedFileTypes = FileType.GetSupportedFileTypes();
foreach (FileType fileType in supportedFileTypes)
{
    Console.WriteLine(fileType);
}
```
Esto imprimirá todos los tipos de archivos que GroupDocs.Watermark puede manejar, brindándole una vista completa de sus capacidades.
## Conclusión
Poner marcas de agua en sus documentos con GroupDocs Watermark para .NET es sencillo y eficiente. Siguiendo este tutorial, habrá aprendido cómo inicializar el motor de marcas de agua, agregar marcas de agua de texto e imágenes, guardar sus documentos con marcas de agua y enumerar los formatos de archivo admitidos. Con estas herramientas, puedes proteger tus documentos con confianza.
 Si tiene alguna pregunta o necesita más ayuda, no dude en visitar el[Foro de soporte de GroupDocs.Watermark](https://forum.groupdocs.com/c/watermark/19).
## Preguntas frecuentes
### ¿Cómo instalo GroupDocs.Watermark para .NET?
 Puedes descargarlo desde el[página de lanzamiento](https://releases.groupdocs.com/Watermark/net/) y agregue la DLL a su proyecto.
### ¿Puedo probar GroupDocs.Watermark gratis?
 Sí, puedes solicitar un[prueba gratis](https://releases.groupdocs.com/) evaluar el software antes de comprarlo.
### ¿Qué formatos de archivo son compatibles con GroupDocs.Watermark?
Puede utilizar el fragmento de código proporcionado para enumerar todos los formatos de archivo compatibles.
### ¿Cómo puedo comprar una licencia para GroupDocs.Watermark?
 Las licencias se pueden comprar directamente desde el[pagina de compra](https://purchase.groupdocs.com/buy).
### ¿Hay alguna documentación disponible para GroupDocs.Watermark?
 Sí, hay documentación completa disponible[aquí](https://tutorials.groupdocs.com/Watermark/net/).