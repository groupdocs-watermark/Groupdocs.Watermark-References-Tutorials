---
title: Guardar documento en el mismo archivo o secuencia
linktitle: Guardar documento en el mismo archivo o secuencia
second_title: API GroupDocs.Watermark .NET
description: Aprenda a agregar marcas de agua a documentos usando Groupdocs.Watermark para .NET. Esta guía proporciona instrucciones para garantizar la protección e integridad de los documentos.
weight: 10
url: /es/net/document-savings/save-document-same-file-stream/
---

# Guardar documento en el mismo archivo o secuencia

## Introducción
En la era digital actual, agregar marcas de agua a los documentos se ha vuelto esencial para proteger la propiedad intelectual y garantizar la integridad de la marca. Groupdocs.Watermark para .NET ofrece una solución sólida para los desarrolladores que buscan incrustar marcas de agua en documentos sin problemas. Esta guía completa lo guiará a través de los pasos para guardar un documento con una marca de agua en el mismo archivo o secuencia usando Groupdocs.Watermark para .NET.
## Requisitos previos
Antes de sumergirse en el tutorial, asegúrese de tener lo siguiente:
1. Entorno de desarrollo: Visual Studio instalado en su máquina.
2. .NET Framework: asegúrese de tener .NET Framework 4.0 o posterior.
3.  Groupdocs.Watermark para .NET: descargue e instale la última versión desde[sitio](https://releases.groupdocs.com/Watermark/net/).
4.  Licencia: Obtenga una licencia temporal o permanente de[aquí](https://purchase.groupdocs.com/temporary-license/).
## Importar espacios de nombres
Para comenzar a usar Groupdocs.Watermark en su proyecto .NET, necesita importar los espacios de nombres necesarios:
```csharp
using System;
using System.IO;
using GroupDocs.Watermark.Watermarks;
```
## Paso 1: configura tu proyecto
Antes de agregar marcas de agua a nuestros documentos, debemos configurar nuestro proyecto .NET. Así es cómo:
1. Cree un nuevo proyecto: abra Visual Studio y cree una nueva aplicación de consola.
2. Agregue la referencia de Groupdocs.Watermark: haga clic con el botón derecho en el proyecto en el Explorador de soluciones, seleccione "Administrar paquetes NuGet" e instale el paquete Groupdocs.Watermark.
## Paso 2: copie el documento en una nueva ubicación
Para evitar alterar el documento original directamente, es una buena práctica copiarlo primero en una nueva ubicación. Así es como lo haces:
```csharp
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName("Your Document Path"));
File.Copy("Your Document Path", outputFileName);
```
## Paso 3: inicializa el marcador de agua
Ahora que tenemos nuestro documento copiado, podemos inicializar la clase Watermarker para agregar nuestra marca de agua:
```csharp
using (Watermarker watermarker = new Watermarker(outputFileName))
{
    // La marca de agua va aquí
}
```
## Paso 4: cree y agregue una marca de agua de texto
A continuación, creamos una marca de agua de texto y la agregamos a nuestro documento:
```csharp
TextWatermark watermark = new TextWatermark("Test watermark", new Font("Arial", 12));
watermarker.Add(watermark);
```
## Paso 5: guarde el documento
Finalmente, guarde el documento con la marca de agua aplicada:
```csharp
watermarker.Save();
```
## Conclusión
Agregar marcas de agua a sus documentos usando Groupdocs Watermark para .NET es sencillo y eficiente. Si sigue los pasos descritos anteriormente, podrá proteger sus documentos y mantener su integridad sin esfuerzo. Para obtener más detalles, puede consultar el[documentación](https://tutorials.groupdocs.com/Watermark/net/).
## Preguntas frecuentes
### ¿Puedo usar una imagen como marca de agua en lugar de texto?
Sí, Groupdocs.Watermark te permite utilizar imágenes, formas y texto como marcas de agua.
### ¿Cómo elimino una marca de agua de un documento?
 Puede eliminar una marca de agua accediendo a la colección de marcas de agua en el documento y usando el`Remove` método.
### ¿Es posible personalizar la apariencia de la marca de agua?
Absolutamente. Puede personalizar la fuente, el tamaño, el color y la posición de la marca de agua.
### ¿Puedo aplicar varias marcas de agua a un solo documento?
 Sí, puede agregar varias marcas de agua llamando al`Add` método varias veces con diferentes objetos de marca de agua.
### ¿Groupdocs.Watermark es compatible con todos los formatos de documentos?
Groupdocs.Watermark admite una amplia gama de formatos de documentos, incluidos PDF, DOCX, PPTX y muchos otros.