---
title: Agregar marca de agua bloqueada a páginas específicas en documentos de Word
linktitle: Agregar marca de agua bloqueada a páginas específicas en documentos de Word
second_title: API GroupDocs.Watermark .NET
description: Aprenda cómo agregar una marca de agua bloqueada a páginas específicas en documentos de Word usando GroupDocs.Watermark para .NET con nuestra sencilla guía paso a paso.
weight: 12
url: /es/net/word-processing-watermarkings/add-locked-watermark-specific-pages-word-docs/
type: docs
---
# Agregar marca de agua bloqueada a páginas específicas en documentos de Word

## Introducción
¿Está buscando agregar una marca de agua a páginas específicas de sus documentos de Word, pero desea bloquearla para que no se pueda eliminar o editar fácilmente? ¡Estás en el lugar correcto! En este tutorial, lo guiaremos a través del proceso de agregar una marca de agua bloqueada a páginas específicas en documentos de Word usando GroupDocs.Watermark para .NET. Esta poderosa biblioteca facilita la aplicación, administración y personalización de marcas de agua en una variedad de tipos de documentos. Si usted es un desarrollador o simplemente alguien que necesita proteger sus documentos, esta guía lo guiará a través de cada paso de manera sencilla.
## Requisitos previos
Antes de sumergirnos en el tutorial, asegurémonos de que tiene todo lo que necesita:
1.  GroupDocs.Watermark para .NET: puede[descargar](https://releases.groupdocs.com/Watermark/net/) la última versión.
2. Entorno de desarrollo: un IDE como Visual Studio.
3. Conocimientos básicos de C#: será útil estar familiarizado con la programación en C#.
4. Documento a marca de agua: un documento de Word (.docx o .doc) al que desea agregar una marca de agua.
## Importar espacios de nombres
Primero, necesita importar los espacios de nombres necesarios en su proyecto C#. Estos espacios de nombres brindan acceso a las clases y métodos necesarios para trabajar con GroupDocs.Watermark.
```csharp
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
Ahora que tenemos los requisitos previos cubiertos y los espacios de nombres necesarios importados, analicemos el proceso paso a paso.
## Paso 1: cargue el documento de Word
 Para empezar, debe cargar el documento de Word al que desea agregar una marca de agua. Esto se puede hacer usando el`Watermarker` clase junto con`WordProcessingLoadOptions`.
```csharp
string documentPath = "Your Document Path";
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Continuar con los siguientes pasos
}
```
## Paso 2: crea la marca de agua del texto
A continuación, cree una marca de agua de texto. Puede personalizar el texto, la fuente, el color y otras propiedades según sus requisitos.
```csharp
TextWatermark watermark = new TextWatermark("Watermark text", new Font("Arial", 19));
watermark.ForegroundColor = Color.Red;
```
## Paso 3: configurar las opciones de marca de agua
 Para aplicar la marca de agua a páginas específicas y bloquearla, configure el`WordProcessingWatermarkPagesOptions`Aquí, usted especifica los números de página donde debe aparecer la marca de agua y configura las opciones de bloqueo.
```csharp
WordProcessingWatermarkPagesOptions options = new WordProcessingWatermarkPagesOptions();
options.PageNumbers = new int[] { 1, 3 }; // Especificar las páginas
options.IsLocked = true; // Bloquear la marca de agua
options.LockType = WordProcessingLockType.AllowOnlyComments; // Establecer tipo de bloqueo
// Para proteger con contraseña
// opciones.Contraseña = "7654321";
```
## Paso 4: agregue la marca de agua al documento
Con su marca de agua y sus opciones configuradas, ahora puede agregar la marca de agua al documento.
```csharp
watermarker.Add(watermark, options);
```
## Paso 5: guarde el documento
Finalmente, guarde el documento con la marca de agua aplicada. Elija una ruta de salida adecuada y guarde el archivo.
```csharp
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
watermarker.Save(outputFileName);
```
## Conclusión
¡Felicidades! Ha agregado con éxito una marca de agua bloqueada a páginas específicas en un documento de Word usando GroupDocs.Watermark para .NET. Este tutorial cubrió todos los pasos esenciales desde cargar el documento hasta guardar el archivo con marca de agua. Si sigue estos pasos, puede asegurarse de que sus documentos tengan una marca de agua segura, protegiendo su contenido contra la edición y el uso no autorizados.
 Para obtener más información, puede consultar el[Documentación de GroupDocs.Watermark](https://tutorials.groupdocs.com/Watermark/net/) . Si tiene alguna pregunta o necesita más ayuda, no dude en visitar el[Foro de soporte](https://forum.groupdocs.com/c/watermark/19).
## Preguntas frecuentes
### ¿Qué es GroupDocs.Watermark para .NET?
GroupDocs.Watermark para .NET es una potente biblioteca que permite a los desarrolladores agregar marcas de agua a varios tipos de documentos, incluidos Word, PDF, Excel y más.
### ¿Puedo aplicar marcas de agua a varias páginas de un documento?
 Sí, puede especificar varios números de página en el`PageNumbers` matriz para aplicar marcas de agua a varias páginas.
### ¿Cómo protejo una marca de agua con una contraseña?
 Puede proteger una marca de agua con una contraseña configurando el`Password` propiedad en el`WordProcessingWatermarkPagesOptions`.
### ¿Es posible personalizar la apariencia de la marca de agua?
¡Absolutamente! Puede personalizar el texto, la fuente, el color, el tamaño y otras propiedades de la marca de agua para adaptarla a sus necesidades.
### ¿Dónde puedo obtener una licencia temporal para GroupDocs.Watermark?
 Puede obtener una licencia temporal de[aquí](https://purchase.groupdocs.com/temporary-license/).