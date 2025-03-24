---
title: Agregar marca de agua a artefactos de imagen en PDF
linktitle: Agregar marca de agua a artefactos de imagen en PDF
second_title: API GroupDocs.Watermark .NET
description: Proteja sus archivos PDF con marcas de agua personalizadas usando GroupDocs.Watermark para .NET. Agregue fácilmente marcas de agua de texto o imágenes a artefactos de imagen en documentos PDF.
weight: 18
url: /es/net/pdf-watermarking-attachments/add-watermark-image-artifacts-pdf/
---
## Introducción
En este tutorial, lo guiaremos a través del proceso de agregar una marca de agua a los artefactos de imagen en un documento PDF usando GroupDocs.Watermark para .NET. Si sigue estos pasos, podrá proteger eficazmente sus archivos PDF con marcas de agua personalizadas.
## Requisitos previos
Antes de comenzar, asegúrese de tener los siguientes requisitos previos:
1.  GroupDocs.Watermark para .NET: descargue e instale la biblioteca GroupDocs.Watermark para .NET desde[aquí](https://releases.groupdocs.com/Watermark/net/).
2. Ruta del documento: tenga la ruta al documento PDF donde desea agregar la marca de agua.
3. Directorio de salida: cree un directorio donde se guardará el documento con marca de agua.

## Importar espacios de nombres
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Paso 1: cargue el documento e inicialice el marcador de agua
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
```
## Paso 2: obtenga contenido PDF y agregue una marca de agua
```csharp
	PdfContent pdfContent = watermarker.GetContent<PdfContent>();
	// Inicializar imagen o marca de agua de texto
	TextWatermark watermark = new TextWatermark("Protected image", new Font("Arial", 8));
	watermark.HorizontalAlignment = HorizontalAlignment.Center;
	watermark.VerticalAlignment = VerticalAlignment.Center;
	watermark.RotateAngle = 45;
	watermark.SizingType = SizingType.ScaleToParentDimensions;
	watermark.ScaleFactor = 1;
	foreach (PdfPage page in pdfContent.Pages)
	{
		foreach (PdfArtifact artifact in page.Artifacts)
		{
			if (artifact.Image != null)
			{
				// Agregar marca de agua a la imagen
				artifact.Image.Add(watermark);
			}
		}
	}
```
## Paso 3: guarde el documento con marca de agua
```csharp
	watermarker.Save(outputFileName);
}
```

## Conclusión
Con GroupDocs.Watermark para .NET, agregar marcas de agua a elementos de imagen en documentos PDF se convierte en un proceso fluido. Si sigue este tutorial, podrá proteger eficientemente sus archivos PDF con marcas de agua personalizadas, garantizando su seguridad y autenticidad.
## Preguntas frecuentes
### ¿Puedo agregar marcas de agua de imagen y texto a mi documento PDF?
Sí, GroupDocs.Watermark para .NET admite la adición simultánea de marcas de agua de imagen y texto.
### ¿Existe alguna limitación en la cantidad de marcas de agua que puedo agregar a un documento?
No, puedes agregar varias marcas de agua a un documento sin ninguna limitación.
### ¿Puedo personalizar la apariencia y posición de la marca de agua?
Absolutamente, tienes control total sobre la apariencia, posición y propiedades de la marca de agua.
### ¿GroupDocs.Watermark para .NET admite otros formatos de documentos además de PDF?
Sí, admite varios formatos de documentos, incluidos Word, Excel, PowerPoint y más.
### ¿Existe alguna forma de eliminar marcas de agua de un documento?
Sí, GroupDocs.Watermark para .NET proporciona métodos para eliminar marcas de agua de los documentos si es necesario.