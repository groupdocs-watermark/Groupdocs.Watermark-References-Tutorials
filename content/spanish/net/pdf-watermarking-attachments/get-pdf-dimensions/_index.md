---
title: Obtener dimensiones en PDF
linktitle: Obtener dimensiones en PDF
second_title: API GroupDocs.Watermark .NET
description: Proteja sus documentos con facilidad utilizando Groupdocs.Watermark para .NET. Agregue marcas de agua, sellos y anotaciones sin esfuerzo.
type: docs
weight: 26
url: /es/net/pdf-watermarking-attachments/get-pdf-dimensions/
---
## Introducción
En la era digital actual, proteger sus documentos es primordial. Ya sea usted un profesional de negocios, un experto legal o un artista creativo, proteger su propiedad intelectual es esencial. Groupdocs.Watermark para .NET ofrece una solución sólida para agregar marcas de agua, sellos y anotaciones a sus documentos, garantizando su seguridad y autenticidad.
## Requisitos previos
Antes de sumergirse en el mundo de Groupdocs.Watermark para .NET, asegúrese de cumplir con los siguientes requisitos previos:
1.  Instalación de Groupdocs.Watermark para .NET: Descargue e instale Groupdocs.Watermark para .NET desde[enlace de descarga](https://releases.groupdocs.com/Watermark/net/).
2.  Clave de licencia (opcional): si bien Groupdocs.Watermark para .NET ofrece una prueba gratuita, puede optar por una licencia temporal o comprar una licencia completa en[aquí](https://purchase.groupdocs.com/buy) para una funcionalidad extendida.
3. Familiaridad con C#: se recomienda tener conocimientos básicos del lenguaje de programación C# para comprender e implementar los ejemplos proporcionados.
4. Documento a proteger: tenga un documento de muestra (p. ej., PDF, Word, Excel) listo en su máquina local para experimentar con él.

## Importar espacios de nombres
Para comenzar a trabajar con Groupdocs.Watermark para .NET, debe importar los espacios de nombres necesarios a su proyecto C#.
```csharp
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using System;
using System.IO;
```
### Paso 1: declarar variables
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
### Paso 2: cargar el documento
```csharp
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
```
### Paso 3: obtenga contenido PDF
```csharp
PdfContent pdfContent = watermarker.GetContent<PdfContent>();
```
### Paso 4: recuperar dimensiones
```csharp
Console.WriteLine(pdfContent.Pages[0].Width);
Console.WriteLine(pdfContent.Pages[0].Height);
```

## Conclusión
En conclusión, Groupdocs.Watermark para .NET ofrece una solución integral para proteger sus documentos del uso y distribución no autorizados. Si sigue los pasos descritos anteriormente y aprovecha el poder de Groupdocs.Watermark para .NET, puede garantizar la seguridad y la integridad de sus valiosos activos digitales.
## Preguntas frecuentes
### ¿Puedo utilizar Groupdocs.Watermark para .NET de forma gratuita?
Sí, Groupdocs.Watermark para .NET ofrece una versión de prueba gratuita con fines de evaluación. Sin embargo, para ampliar la funcionalidad, puede considerar comprar una licencia completa.
### ¿Groupdocs.Watermark admite múltiples formatos de documentos?
Sí, Groupdocs admite una amplia gama de formatos de documentos, incluidos PDF, Word, Excel, PowerPoint y más.
### ¿Puedo personalizar marcas de agua y sellos con Groupdocs.Watermark?
¡Absolutamente! Groupdocs.Watermark ofrece amplias opciones de personalización para marcas de agua, sellos y anotaciones para satisfacer sus necesidades específicas.
### ¿Hay soporte técnico disponible para los usuarios de Groupdocs.Watermark?
 Sí, puede obtener asistencia técnica e interactuar con la comunidad de Groupdocs a través del[Foro de soporte](https://forum.groupdocs.com/c/watermark/19).
### ¿Cómo puedo obtener una licencia temporal para Groupdocs.Watermark?
 Puede obtener una licencia temporal para Groupdocs.Watermark en[aquí](https://purchase.groupdocs.com/temporary-license/).