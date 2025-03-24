---
title: Cargar documento protegido con contraseña
linktitle: Cargar documento protegido con contraseña
second_title: API GroupDocs.Watermark .NET
description: Aprenda a agregar marcas de agua a documentos protegidos con contraseña usando Groupdocs para .NET con nuestra guía paso a paso. Proteja y marque sus archivos fácilmente.
weight: 13
url: /es/net/document-loadings/load-password-protected-document/
---

# Cargar documento protegido con contraseña

## Introducción
¿Está buscando proteger sus documentos agregando marcas de agua, incluso si están protegidos con contraseña? Groupdocs.Watermark para .NET es una poderosa herramienta que le permite hacer precisamente eso. En este tutorial, lo guiaremos a través del proceso de cargar un documento protegido con contraseña y agregarle una marca de agua usando Groupdocs.Watermark para .NET. ¡Vamos a sumergirnos!
## Requisitos previos
Antes de comenzar, asegúrese de tener lo siguiente:
1. Visual Studio: cualquier versión de Visual Studio instalada en su máquina.
2. .NET Framework: asegúrese de tener .NET Framework 4.6.1 o posterior.
3. Groupdocs.Watermark para .NET: descargue e instale la biblioteca Groupdocs.Watermark para .NET desde[enlace de descarga](https://releases.groupdocs.com/Watermark/net/).
## Importar espacios de nombres
Primero, necesitamos importar los espacios de nombres necesarios a nuestro proyecto. Esto asegura que podamos acceder a todos los métodos y propiedades proporcionados por Groupdocs.Watermark para .NET.
```csharp
using GroupDocs.Watermark.Options;
using GroupDocs.Watermark.Watermarks;
using System;
using System.IO;
```
Ahora, dividamos el proceso en pasos simples y fáciles de seguir.
## Paso 1: configura tu proyecto
Para comenzar, cree una nueva aplicación de consola C# en Visual Studio. Una vez que su proyecto esté configurado, instale la biblioteca Groupdocs.Watermark para .NET a través del Administrador de paquetes NuGet.
1. Abra Visual Studio y cree una nueva aplicación de consola (.NET Framework).
2.  Ir a`Tools` >`NuGet Package Manager` >`Manage NuGet Packages for Solution`.
3.  Buscar`GroupDocs.Watermark` e instalar el paquete.
## Paso 2: definir rutas de documentos
A continuación, deberá definir la ruta a su documento protegido con contraseña y la ruta del archivo de salida donde se guardará el documento con marca de agua.
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
```
 Reemplazar`"Your Document Path"` y`"Your Document Directory"` con las rutas reales en su máquina.
## Paso 3: configurar las opciones de carga con contraseña
Para abrir un documento protegido con contraseña, debe proporcionar la contraseña en las opciones de carga.
```csharp
LoadOptions loadOptions = new LoadOptions();
loadOptions.Password = "P@$w0rd";
```
 Reemplazar`"P@$w0rd"` con la contraseña real de su documento.
## Paso 4: cargue el documento
 Ahora, carguemos el documento usando el`Watermarker` clase.
```csharp
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Su código para agregar marca de agua irá aquí
}
```
## Paso 5: crea una marca de agua
Crearemos una marca de agua de texto que podremos agregar al documento. Puede personalizar el texto, la fuente, el tamaño y otras propiedades según sea necesario.
```csharp
TextWatermark watermark = new TextWatermark("Test watermark", new Font("Arial", 12));
```
 Siéntete libre de cambiar`"Test watermark"`, `"Arial"` , y`12` según su texto, fuente y tamaño preferidos.
## Paso 6: agregue la marca de agua
 Agregue la marca de agua al documento usando el`Add` método de la`Watermarker` clase.
```csharp
watermarker.Add(watermark);
```
## Paso 7: guarde el documento con marca de agua
Finalmente, guarde el documento con marca de agua en la ruta del archivo de salida especificada.
```csharp
watermarker.Save(outputFileName);
```
## Conclusión
Agregar marcas de agua a sus documentos protegidos con contraseña es un proceso sencillo con Groupdocs para .NET. Si sigue estos sencillos pasos, puede asegurarse de que sus documentos estén protegidos y con la marca que cumpla con sus requisitos. Ya sea por seguridad, marca o cumplimiento, poner marcas de agua en sus documentos nunca ha sido tan fácil.
## Preguntas frecuentes
### ¿Puedo agregar marcas de agua a imágenes usando Groupdocs.Watermark para .NET?
 Sí, puede agregar marcas de agua de texto e imagen. Simplemente use el`ImageWatermark` clase en lugar de`TextWatermark`.
### ¿Es posible eliminar marcas de agua de un documento?
Sí, Groupdocs.Watermark para .NET proporciona métodos para buscar y eliminar marcas de agua.
### ¿Groupdocs.Watermark para .NET admite otros formatos de documentos además de los PDF?
Sí, admite una amplia gama de formatos, incluidos Word, Excel, PowerPoint y más.
### ¿Puedo personalizar la apariencia de la marca de agua?
¡Absolutamente! Puede personalizar la fuente, el tamaño, el color, la opacidad y más.
### ¿Dónde puedo obtener asistencia si tengo problemas?
 Puedes visitar el[Foro de soporte de Groupdocs](https://forum.groupdocs.com/c/watermark/19) para ayuda y orientación.