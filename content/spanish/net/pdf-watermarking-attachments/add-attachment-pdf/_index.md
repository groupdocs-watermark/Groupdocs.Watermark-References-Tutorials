---
title: Agregar archivo adjunto a PDF
linktitle: Agregar archivo adjunto a PDF
second_title: API GroupDocs.Watermark .NET
description: Mejore sus capacidades de gestión de documentos .NET con GroupDocs.Watermark para una gestión perfecta de marcas de agua y archivos adjuntos.
weight: 12
url: /es/net/pdf-watermarking-attachments/add-attachment-pdf/
---
## Introducción
En el ámbito del desarrollo de .NET, GroupDocs.Watermark se destaca como una poderosa herramienta para administrar marcas de agua, anotaciones y más dentro de varios formatos de documentos. Ya sea que esté trabajando con archivos PDF, documentos de Word o imágenes, GroupDocs.Watermark para .NET proporciona una integración perfecta que permite a los desarrolladores manipular documentos con facilidad.
## Requisitos previos
Antes de profundizar en las complejidades del uso de GroupDocs.Watermark para .NET, asegúrese de cumplir con los siguientes requisitos previos:
1.  Instalación: asegúrese de haber instalado GroupDocs.Watermark para .NET. Puedes descargarlo desde el[página de lanzamiento](https://releases.groupdocs.com/Watermark/net/).
2. Preparación de documentos: tenga listo un documento en el que desee realizar marcas de agua u otras operaciones.
3. Conocimientos básicos de C#: familiarícese con los conceptos básicos del lenguaje de programación C#, ya que lo usaremos para interactuar con la API GroupDocs.Watermark.

## Importar espacios de nombres
Antes de comenzar con la implementación, es fundamental importar los espacios de nombres necesarios para acceder a la funcionalidad de GroupDocs.Watermark. A continuación se muestran los espacios de nombres requeridos:
```csharp
using System;
using System.IO;
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
```
## Paso 1: cargar el documento
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
```
 En este paso, especificamos la ruta al documento con el que queremos trabajar y creamos un`PdfLoadOptions` Objeto para cargar documentos PDF. Luego inicializamos un`Watermarker` objeto con la ruta del documento y las opciones de carga.
## Paso 2: obtenga contenido PDF
```csharp
PdfContent pdfContent = watermarker.GetContent<PdfContent>();
```
 Aquí obtenemos el contenido del documento PDF utilizando el`GetContent<PdfContent>()` método.
## Paso 3: agregar archivo adjunto
```csharp
pdfContent.Attachments.Add(File.ReadAllBytes("Your Document Path"), "sample doc", "sample doc as attachment");
```
Este paso implica agregar un archivo adjunto al documento PDF. Debe proporcionar los bytes, el nombre y la descripción del archivo adjunto.
## Paso 4: guardar cambios
```csharp
watermarker.Save(outputFileName);
```
Finalmente guardamos los cambios realizados en el documento con el archivo adjunto añadido.

## Conclusión
GroupDocs.Watermark para .NET ofrece una solución sólida para administrar marcas de agua y archivos adjuntos de documentos sin problemas. Si sigue los pasos descritos anteriormente, puede integrar fácilmente funciones de marcas de agua y archivos adjuntos en sus aplicaciones .NET.
## Preguntas frecuentes
### ¿GroupDocs.Watermark es compatible con todos los marcos .NET?
Sí, GroupDocs.Watermark es compatible con .NET Framework 2.0 y superior.
### ¿Puedo eliminar marcas de agua agregadas usando GroupDocs.Watermark?
Sí, GroupDocs.Watermark proporciona métodos para eliminar marcas de agua de documentos.
### ¿GroupDocs.Watermark admite el cifrado de documentos?
Sí, GroupDocs.Watermark le permite trabajar con documentos cifrados.
### ¿Puedo personalizar la apariencia de las marcas de agua?
Por supuesto, GroupDocs.Watermark ofrece varias opciones de personalización para marcas de agua.
### ¿Existe una versión de prueba disponible para fines de prueba?
 Sí, puedes acceder a la versión de prueba desde el[página de lanzamientos](https://releases.groupdocs.com/).