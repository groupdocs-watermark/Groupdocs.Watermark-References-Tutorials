---
title: Guardar documento en la ubicación especificada
linktitle: Guardar documento en la ubicación especificada
second_title: API GroupDocs.Watermark .NET
description: Aprenda cómo agregar fácilmente marcas de agua a sus documentos usando GroupDocs.Watermark para .NET con esta guía paso a paso. Mejorar la seguridad de los documentos.
weight: 11
url: /es/net/document-savings/save-document-specified-location/
---

# Guardar documento en la ubicación especificada

## Introducción
En la era digital, proteger los documentos se ha vuelto más crucial que nunca. La marca de agua es una forma eficaz de proteger sus documentos del uso no autorizado. GroupDocs.Watermark para .NET ofrece una solución sólida para agregar marcas de agua a sus documentos. Si usted es un desarrollador que busca integrar marcas de agua en su aplicación o alguien interesado en proteger sus documentos, este tutorial lo guiará a través del proceso paso a paso.
## Requisitos previos
Antes de sumergirse en el tutorial, asegúrese de cumplir con los siguientes requisitos previos:
- Entorno de desarrollo .NET: asegúrese de tener instalado Visual Studio o cualquier otro entorno de desarrollo .NET.
-  GroupDocs.Watermark para la biblioteca .NET: descargue y haga referencia a la biblioteca en su proyecto.[Descargar GroupDocs.Watermark para .NET](https://releases.groupdocs.com/Watermark/net/)
- Conocimientos básicos de programación en C#: será útil comprender los conceptos básicos de programación en C#.
- Documento a marca de agua: tenga listo un documento de muestra al que desea aplicar la marca de agua.
## Importar espacios de nombres
Antes de comenzar con el ejemplo, debe importar los espacios de nombres necesarios. Agregue lo siguiente usando declaraciones en la parte superior de su archivo de código:
```csharp
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
Dividamos el proceso de agregar una marca de agua a un documento usando GroupDocs.Watermark para .NET en pasos manejables. Siga estos pasos para aplicar con éxito una marca de agua y guardar su documento en una ubicación específica.
## Paso 1: configura tu proyecto
Comience creando un nuevo proyecto .NET en Visual Studio. Puede elegir una aplicación de consola para simplificar.
1. Abra Visual Studio.
2.  Seleccionar`File` >`New` >`Project`.
3.  Elegir`Console App (.NET Core)` o`Console App (.NET Framework)`.
4.  Ponle un nombre a tu proyecto y haz clic`Create`.

## Paso 2: prepare su documento y el texto de la marca de agua
### Especificar ruta del documento
Defina la ruta del documento al que desea ponerle una marca de agua. Para este ejemplo, usemos una ruta de marcador de posición.
```csharp
string documentPath = "Your Document Path";
```
### Definir ruta de salida
Configure la ruta de salida donde desea guardar el documento con marca de agua.
```csharp
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
```
## Paso 3: cargue el documento
 Utilizar el`Watermarker` clase para cargar su documento. Esta clase proporciona métodos para agregar, eliminar y editar marcas de agua.
```csharp
using (Watermarker watermarker = new Watermarker(documentPath))
{
    // Agregue lógica de marca de agua aquí
}
```
## Paso 4: crea y agrega una marca de agua

### Crear marca de agua de texto
 Crear una instancia de`TextWatermark` objeto con el texto y las propiedades de fuente que desee.
```csharp
TextWatermark watermark = new TextWatermark("Test watermark", new Font("Arial", 12));
```
### Agregar marca de agua al documento
 Agregue la marca de agua creada a su documento usando el`Add` método de la`Watermarker` clase.
```csharp
watermarker.Add(watermark);
```
## Paso 5: guarde el documento
Finalmente, guarde el documento con la marca de agua en la ubicación especificada.
```csharp
watermarker.Save(outputFileName);
```
## Conclusión
Poner marcas de agua en sus documentos utilizando GroupDocs Watermark para .NET es un proceso sencillo que puede mejorar significativamente la seguridad de sus documentos. Siguiendo esta guía paso a paso, puede agregar fácilmente marcas de agua a sus documentos y guardarlos en la ubicación deseada. Ya sea que esté protegiendo la propiedad intelectual, garantizando la autenticidad de los documentos o simplemente agregando un toque profesional, GroupDocs.Watermark para .NET proporciona las herramientas que necesita.
## Preguntas frecuentes
### ¿Puedo utilizar imágenes como marcas de agua con GroupDocs.Watermark para .NET?
Sí, puede utilizar marcas de agua de texto e imagen con GroupDocs para .NET. La biblioteca admite varios tipos de marcas de agua para satisfacer sus necesidades.
### ¿Hay una prueba gratuita disponible para GroupDocs.Watermark para .NET?
 Sí, puedes descargar una prueba gratuita desde[sitio web](https://releases.groupdocs.com/).
### ¿Cómo puedo adquirir una licencia de GroupDocs.Watermark para .NET?
 Puede adquirir una licencia en el[pagina de compra](https://purchase.groupdocs.com/buy).
### ¿GroupDocs.Watermark para .NET admite marcas de agua por lotes?
Sí, puede marcar con agua varios documentos en un proceso por lotes recorriendo una lista de documentos y aplicando marcas de agua.
### ¿Dónde puedo obtener soporte para GroupDocs.Watermark para .NET?
 El soporte está disponible en el[Foro de documentos de grupo](https://forum.groupdocs.com/c/watermark/19).