---
title: Eliminar marca de agua de PDF
linktitle: Eliminar marca de agua de PDF
second_title: API GroupDocs.Watermark .NET
description: Aprenda a eliminar marcas de agua de archivos PDF usando GroupDocs.Watermark para .NET. Pasos sencillos para la edición profesional de documentos.
weight: 34
url: /es/net/pdf-watermarking-attachments/remove-watermark-pdf/
---

# Eliminar marca de agua de PDF

## Introducción
En la era digital actual, proteger documentos confidenciales con marcas de agua es una práctica común. Sin embargo, hay casos en los que es posible que necesites eliminar marcas de agua de archivos PDF por diversos motivos. Ya sea que esté editando un documento o simplemente necesite una versión limpia para la presentación, GroupDocs.Watermark para .NET proporciona una solución perfecta para eliminar marcas de agua de archivos PDF.
## Requisitos previos
Antes de sumergirnos en la eliminación de marcas de agua de archivos PDF usando GroupDocs.Watermark para .NET, asegúrese de tener los siguientes requisitos previos:
1.  GroupDocs.Watermark para la biblioteca .NET: descargue e instale la biblioteca desde[aquí](https://releases.groupdocs.com/Watermark/net/).
2. Entorno de desarrollo: Tenga Visual Studio o cualquier IDE compatible instalado en su sistema.
3. Documento con marca de agua: prepare un documento PDF que contenga la marca de agua que desea eliminar.

## Importando espacios de nombres
En su proyecto C#, comience importando los espacios de nombres necesarios:
```csharp
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Search;
using GroupDocs.Watermark.Search.SearchCriteria;
using System.IO;
using System;
```
## Paso 1: cargue el documento PDF
```csharp
string documentPath = "YourDocumentPath.pdf";
string outputDirectory = "YourOutputDirectory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
var loadOptions = new PdfLoadOptions();
```
En este paso, especifique la ruta a su documento PDF y el directorio donde desea guardar el archivo de salida.
## Paso 2: Inicializar el marcador de agua y los criterios de búsqueda
```csharp
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    ImageSearchCriteria imageSearchCriteria = new ImageDctHashSearchCriteria(Constants.LogoPng);
    TextSearchCriteria textSearchCriteria = new TextSearchCriteria("Company Name");
```
Inicialice el objeto Watermarker con la ruta del documento PDF y las opciones de carga. Luego, define los criterios de búsqueda para la marca de agua que deseas eliminar. Puede buscar marcas de agua basadas en imágenes o texto.
## Paso 3: buscar y eliminar marcas de agua
```csharp
    PdfContent pdfContent = watermarker.GetContent<PdfContent>();
    PossibleWatermarkCollection possibleWatermarks = pdfContent.Pages[0].Search(imageSearchCriteria.Or(textSearchCriteria));
    // Eliminar todas las marcas de agua encontradas
    for (int i = possibleWatermarks.Count - 1; i >= 0; i--)
    {
        possibleWatermarks.RemoveAt(i);
    }
    watermarker.Save(outputFileName);
}
```
Busque posibles marcas de agua en la primera página del documento PDF según los criterios de búsqueda definidos. Luego, recorra la colección de posibles marcas de agua y elimínelas una por una. Finalmente, guarde el documento PDF modificado sin la marca de agua.

## Conclusión
Eliminar marcas de agua de archivos PDF es una tarea crucial en varios escenarios, desde la edición de documentos hasta la preparación de presentaciones. Con GroupDocs.Watermark para .NET, puede eliminar fácilmente marcas de agua de archivos PDF usando un código C# simple, garantizando que sus documentos estén limpios y profesionales.
## Preguntas frecuentes
### ¿GroupDocs.Watermark para .NET es compatible con todas las versiones de Visual Studio?
Sí, GroupDocs.Watermark para .NET es compatible con todas las versiones de Visual Studio, incluidos Visual Studio 2019 y Visual Studio 2022.
### ¿Puedo eliminar varias marcas de agua de un único documento PDF usando GroupDocs.Watermark para .NET?
Sí, puede buscar y eliminar varias marcas de agua de un único documento PDF especificando los criterios de búsqueda adecuados.
### ¿GroupDocs.Watermark para .NET admite otros formatos de documentos además de PDF?
Sí, GroupDocs.Watermark para .NET admite una amplia gama de formatos de documentos, incluidos documentos de Word, hojas de cálculo de Excel, presentaciones de PowerPoint y más.
### ¿Existe una versión de prueba disponible para GroupDocs.Watermark para .NET?
 Sí, puede descargar una versión de prueba gratuita de GroupDocs.Watermark para .NET desde[aquí](https://releases.groupdocs.com/).
### ¿Dónde puedo encontrar soporte y asistencia adicional para GroupDocs.Watermark para .NET?
 Para obtener soporte adicional, puede visitar el foro GroupDocs.Watermark[aquí](https://forum.groupdocs.com/c/watermark/19).