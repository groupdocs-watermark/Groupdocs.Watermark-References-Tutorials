---
title: Extraiga todos los archivos adjuntos del PDF
linktitle: Extraiga todos los archivos adjuntos del PDF
second_title: API GroupDocs.Watermark .NET
description: Aprenda a extraer todos los archivos adjuntos de un PDF usando Groupdocs.Watermark para .NET. Siga nuestra guía paso a paso para un proceso de extracción perfecto.
weight: 22
url: /es/net/pdf-watermarking-attachments/extract-all-attachments-pdf/
type: docs
---
# Extraiga todos los archivos adjuntos del PDF

## Introducción
¿Está buscando extraer archivos adjuntos de un documento PDF sin esfuerzo? Bueno, ¡estás en el lugar correcto! En este completo tutorial, lo guiaremos a través del proceso de extracción de todos los archivos adjuntos de un PDF usando Groupdocs.Watermark para .NET. Esta poderosa biblioteca permite a los desarrolladores administrar marcas de agua en varios formatos de documentos, pero también incluye capacidades sólidas para extraer archivos incrustados. Ya sea que sea un desarrollador experimentado o esté comenzando, esta guía paso a paso hará que el proceso sea muy sencillo.
## Requisitos previos
Antes de profundizar en el código, cubramos los conceptos básicos que necesitará para comenzar. Aquí hay una lista de verificación rápida para asegurarse de que esté listo:
1. Entorno .NET: asegúrese de tener configurado un entorno de desarrollo .NET. Puede utilizar Visual Studio o cualquier otro IDE .NET de su elección.
2.  Groupdocs.Watermark para .NET: descargue e instale la última versión de Groupdocs.Watermark para .NET desde[aquí](https://releases.groupdocs.com/Watermark/net/).
3. Habilidades de desarrollo: comprensión básica de la programación en C# y familiaridad con las bibliotecas .NET.
4. Documento PDF de muestra: tenga un documento PDF de muestra con archivos adjuntos que pueda utilizar para realizar pruebas.
## Importar espacios de nombres
Antes de comenzar a codificar, deberá importar los espacios de nombres necesarios. Esto ayuda a organizar su código y le brinda acceso a las clases y métodos que utilizará.
```csharp
using System;
using System.IO;
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
```
## Paso 1: configura tu proyecto
Primero lo primero, configuremos su proyecto. Abra su entorno de desarrollo .NET y cree una nueva aplicación de consola.
### Crear un nuevo proyecto
1. Abra Visual Studio.
2. Seleccione "Crear un nuevo proyecto".
3. Elija "Aplicación de consola (.NET Core)" o ".NET Framework" según sus preferencias.
4. Ponle un nombre a tu proyecto y haz clic en "Crear".
### Agregar Groupdocs.Watermark para .NET
1. Haga clic derecho en su proyecto en el Explorador de soluciones.
2. Seleccione "Administrar paquetes NuGet".
3. Busque "Groupdocs.Watermark" e instale la última versión.
## Paso 2: define tus caminos
A continuación, debe definir las rutas de su documento y directorio de salida. Aquí es donde se almacenarán su PDF y los archivos adjuntos extraídos.

 En tus`Program.cs` archivo, agregue el siguiente código para definir sus rutas:
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
 Reemplazar`"Your Document Path"` y`"Your Document Directory"` con las rutas reales en su sistema.
## Paso 3: cargue su documento PDF
 Ahora, carguemos su documento PDF usando Groupdocs.Watermark. Este paso implica crear opciones de carga e inicializar el`Watermarker` clase.
### Crear opciones de carga
 Primero, cree una instancia de`PdfLoadOptions`:
```csharp
var loadOptions = new PdfLoadOptions();
```
### Inicializar marcador de agua
 A continuación, utilice el`Watermarker` clase para cargar su documento:
```csharp
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Tu código irá aquí
}
```
## Paso 4: extraer archivos adjuntos
Con su documento cargado, es hora de extraer los archivos adjuntos. Usarás el`PdfContent` class para acceder a los archivos adjuntos y luego guardarlos en el directorio de salida especificado.
### Obtener contenido PDF
 Dentro de`using` bloquear, obtener el contenido del PDF:
```csharp
PdfContent pdfContent = watermarker.GetContent<PdfContent>();
```
### Recorrer archivos adjuntos
Recorra cada archivo adjunto en el PDF:
```csharp
foreach (PdfAttachment attachment in pdfContent.Attachments)
{
    Console.WriteLine("Name: {0}", attachment.Name);
    Console.WriteLine("Description: {0}", attachment.Description);
    Console.WriteLine("File type: {0}", attachment.GetDocumentInfo().FileType);
    // Guarde el archivo adjunto en el disco
    File.WriteAllBytes(Path.Combine(outputDirectory, attachment.Name), attachment.Content);
}
```
Este código extrae cada archivo adjunto y lo guarda en su directorio de salida. También imprime información básica sobre cada archivo adjunto a la consola.
## Conclusión
¡Y ahí lo tienes! Ha extraído correctamente los archivos adjuntos de un PDF utilizando Groupdocs.Watermark para .NET. Este tutorial lo guió paso a paso a través de la configuración de su proyecto, la carga de su documento y la extracción de los archivos adjuntos. Con estas habilidades, ahora puede administrar y manipular archivos adjuntos PDF en sus aplicaciones .NET con facilidad.
## Preguntas frecuentes
### ¿Qué es Groupdocs.Watermark para .NET?
Groupdocs.Watermark para .NET es una biblioteca completa para agregar, eliminar y administrar marcas de agua en varios formatos de documentos, incluidos PDF. También ofrece capacidades para extraer archivos incrustados.
### ¿Puedo extraer otros tipos de archivos incrustados en un PDF?
Sí, Groupdocs.Watermark para .NET le permite extraer cualquier tipo de archivo incrustado en un PDF, no solo los archivos adjuntos.
### ¿Hay una prueba gratuita disponible?
 Sí, puede descargar una prueba gratuita de Groupdocs.Watermark para .NET desde[aquí](https://releases.groupdocs.com/).
### ¿Cómo puedo obtener soporte si tengo problemas?
 Puede obtener soporte visitando el[Foro de soporte de Groupdocs.Watermark](https://forum.groupdocs.com/c/watermark/19).
### ¿Necesito una licencia para usar Groupdocs.Watermark para .NET?
 Sí, necesita una licencia para utilizar la biblioteca en producción. Puedes comprar una licencia[aquí](https://purchase.groupdocs.com/buy) u obtener una licencia temporal[aquí](https://purchase.groupdocs.com/temporary-license/).