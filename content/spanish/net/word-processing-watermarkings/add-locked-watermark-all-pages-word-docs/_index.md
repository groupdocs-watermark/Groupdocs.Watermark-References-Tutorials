---
title: Agregar marca de agua bloqueada a todas las páginas en documentos de Word
linktitle: Agregar marca de agua bloqueada a todas las páginas en documentos de Word
second_title: API GroupDocs.Watermark .NET
description: Proteja sus documentos agregando marcas de agua bloqueadas usando Groupdocs.Watermark para .NET. Siga nuestra guía paso a paso para una fácil implementación.
weight: 11
url: /es/net/word-processing-watermarkings/add-locked-watermark-all-pages-word-docs/
type: docs
---
# Agregar marca de agua bloqueada a todas las páginas en documentos de Word

## Introducción
Agregar marcas de agua a sus documentos es un paso vital para proteger y marcar su contenido. Ya sea que esté evitando el uso no autorizado o simplemente agregando un toque profesional, las marcas de agua pueden servir para múltiples propósitos. En este tutorial, lo guiaremos a través del proceso de agregar una marca de agua bloqueada a todas las páginas de un documento de Word usando Groupdocs.Watermark para .NET.
## Requisitos previos
Antes de sumergirnos en la guía paso a paso, asegurémonos de que tiene todo lo que necesita:
1. Groupdocs.Watermark para .NET: descargue la última versión desde[aquí](https://releases.groupdocs.com/Watermark/net/).
2. .NET Framework: asegúrese de tener .NET Framework instalado en su máquina.
3. Entorno de desarrollo: un entorno de desarrollo como Visual Studio.
4.  Licencia: Puedes optar por una[prueba gratis](https://releases.groupdocs.com/) o comprar un[licencia temporal](https://purchase.groupdocs.com/temporary-license/).
## Importar espacios de nombres
Lo primero es lo primero: debe importar los espacios de nombres necesarios en su proyecto. Estos son esenciales para acceder a las clases y métodos proporcionados por Groupdocs.Watermark.
```csharp
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Paso 1: configura tu proyecto

Abra su entorno de desarrollo y cree un nuevo proyecto .NET. Puede ser una aplicación de consola o cualquier otro tipo que se adapte a sus necesidades.

Debe agregar el paquete Groupdocs.Watermark a su proyecto. Esto se puede hacer a través del Administrador de paquetes NuGet. Ejecute el siguiente comando en la consola del Administrador de paquetes NuGet:
```sh
Install-Package GroupDocs.Watermark
```
## Paso 2: cargue el documento de Word
### Definir la ruta del documento
Especifique la ruta a su documento de Word. Este será el documento donde deseas agregar la marca de agua.
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
```
### Establecer opciones de carga
 Crear una instancia de`WordProcessingLoadOptions` para cargar su documento de Word con opciones específicas.
```csharp
var loadOptions = new WordProcessingLoadOptions();
```
## Paso 3: crea la marca de agua
### Inicializar marcador de agua
 Utilizando el`Watermarker`clase, cargue el documento con las opciones de carga especificadas.
```csharp
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Se realizarán más pasos dentro de este bloque usando
}
```
### Definir propiedades de marca de agua
 Crear un`TextWatermark` instancia con el texto, fuente y color que desee.
```csharp
TextWatermark watermark = new TextWatermark("Watermark text", new Font("Arial", 19));
watermark.ForegroundColor = Color.Red;
```
## Paso 4: aplicar marca de agua a todas las páginas
### Establecer opciones de marca de agua
 Definir`WordProcessingWatermarkPagesOptions` y establecer el`IsLocked` propiedad en verdadero para bloquear la marca de agua. Esto asegura que la marca de agua no se pueda eliminar fácilmente.
```csharp
WordProcessingWatermarkPagesOptions options = new WordProcessingWatermarkPagesOptions();
options.IsLocked = true;
options.LockType = WordProcessingLockType.AllowOnlyFormFields;
```
### Opcional: agregar protección con contraseña
Si desea agregar una capa adicional de seguridad, puede establecer una contraseña para la marca de agua.
```csharp
// Para proteger con contraseña
// opciones.Contraseña = "7654321";
```
### Agregar la marca de agua
 Utilizar el`Add` método de la`Watermarker` clase para agregar la marca de agua al documento con las opciones especificadas.
```csharp
watermarker.Add(watermark, options);
```
## Paso 5: guarde el documento
Finalmente, guarde el documento modificado en el archivo de salida especificado.
```csharp
watermarker.Save(outputFileName);
```

## Conclusión
Si sigue estos pasos, puede agregar fácilmente una marca de agua bloqueada a todas las páginas de sus documentos de Word usando Groupdocs.Watermark para .NET. Esto no sólo ayuda a proteger sus documentos del uso no autorizado sino que también agrega un toque profesional a su contenido. Groupdocs.Watermark ofrece una solución integral para las necesidades de marcas de agua, garantizando que sus documentos permanezcan seguros y con marca.
## Preguntas frecuentes
### ¿Puedo usar una imagen como marca de agua en lugar de texto?
 Sí, Groupdocs admite marcas de agua de texto e imagen. puedes reemplazar`TextWatermark` con`ImageWatermark` y especifica tu imagen.
### ¿Es posible personalizar la posición de la marca de agua?
 ¡Absolutamente! Puede establecer la posición de la marca de agua usando propiedades como`HorizontalAlignment` y`VerticalAlignment`.
### ¿Puedo aplicar diferentes marcas de agua a diferentes páginas del documento?
 Sí, puedes personalizar marcas de agua para páginas específicas usando el`PageIndex` propiedad en el`WordProcessingWatermarkPagesOptions`.
### ¿Groupdocs.Watermark admite otros formatos de documentos además de Word?
Sí, Groupdocs admite varios formatos, incluidos PDF, Excel, PowerPoint y más.
### ¿Cuáles son los requisitos del sistema para utilizar Groupdocs.Watermark?
Necesita un sistema con .NET Framework instalado y un entorno de desarrollo como Visual Studio.