---
title: Generar vista previa del documento
linktitle: Generar vista previa del documento
second_title: API GroupDocs.Watermark .NET
description: Aprenda a generar vistas previas de documentos utilizando GroupDocs.Watermark para .NET con esta guía. Mejore la seguridad y gestión de sus documentos sin esfuerzo.
weight: 10
url: /es/net/document-manipulation/generate-document-preview/
type: docs
---
# Generar vista previa del documento

## Introducción
En el mundo de la gestión de documentos digitales, la marca de agua juega un papel crucial para garantizar la seguridad y autenticidad de los documentos. GroupDocs.Watermark para .NET es una poderosa herramienta que permite a los desarrolladores agregar marcas de agua a documentos sin esfuerzo. En este tutorial, lo guiaremos a través del proceso de generación de vistas previas de documentos usando GroupDocs.Watermark para .NET. Ya sea que sea un desarrollador experimentado o recién esté comenzando, esta guía le brindará un proceso integral paso a paso para lograr su objetivo.
## Requisitos previos
Antes de profundizar en la implementación, asegurémonos de tener todo lo que necesita para comenzar:
- Un conocimiento básico de C# y .NET framework.
- Visual Studio instalado en su máquina.
- GroupDocs.Watermark para la biblioteca .NET. Puede[descarguelo aqui](https://releases.groupdocs.com/Watermark/net/).
-  Una licencia válida para GroupDocs.Watermark. Puedes comprarlo[aquí](https://purchase.groupdocs.com/buy) u obtener un[licencia temporal](https://purchase.groupdocs.com/temporary-license/) para fines de evaluación.
## Importar espacios de nombres
Para comenzar a usar GroupDocs.Watermark en su proyecto, deberá importar los espacios de nombres necesarios. Esto se puede hacer agregando las siguientes directivas de uso a su código:
```csharp
using System;
using System.IO;
using GroupDocs.Watermark.Options;
```
Estos espacios de nombres proporcionarán acceso a las clases y métodos necesarios para colocar marcas de agua y generar vistas previas de documentos.

Dividamos el proceso de generación de una vista previa de un documento en pasos simples y fáciles de seguir.
## Paso 1: configura tu proyecto
Lo primero es lo primero, configure su proyecto .NET en Visual Studio. Si aún no tienes un proyecto, crea uno nuevo siguiendo estos pasos:
1. Abra Visual Studio.
2. Haga clic en "Crear un nuevo proyecto".
3. Seleccione "Aplicación de consola (.NET Core)" y haga clic en "Siguiente".
4. Nombra tu proyecto y elige una ubicación para guardarlo, luego haz clic en "Crear".
## Paso 2: Instale GroupDocs.Watermark para .NET
Para utilizar GroupDocs.Watermark en su proyecto, necesita instalar la biblioteca. Esto se puede hacer usando el Administrador de paquetes NuGet:
1. Haga clic derecho en su proyecto en el Explorador de soluciones.
2. Seleccione "Administrar paquetes NuGet".
3. Busque "GroupDocs.Watermark" en la pestaña Examinar.
4. Haga clic en "Instalar" para agregar la biblioteca a su proyecto.
Alternativamente, puede instalarlo a través de la Consola del Administrador de paquetes:
```powershell
Install-Package GroupDocs.Watermark
```
## Paso 3: Definir la ruta del documento y el directorio de salida
Antes de generar la vista previa, debe especificar la ruta del documento que desea obtener una vista previa y el directorio donde se guardarán las imágenes de la vista previa:
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
```
Reemplace "La ruta de su documento" con la ruta a su documento y "Su directorio de documentos" con el directorio donde desea guardar las imágenes de vista previa.
## Paso 4: inicializar el objeto de marca de agua
Crear una instancia del`Watermarker` clase pasando la ruta del documento a su constructor. Este objeto se utilizará para realizar todas las operaciones de marca de agua:
```csharp
using (Watermarker watermarker = new Watermarker(documentPath))
{
    // Tu código aquí
}
```
## Paso 5: crear métodos delegados para el manejo de transmisiones
Para generar la vista previa, debe definir métodos delegados para crear y publicar transmisiones. Estos métodos manejarán la creación y publicación de secuencias para cada página del documento:
```csharp
CreatePageStream createPageStreamDelegate = delegate(int number)
{
    string previewImageFileName = Path.Combine(outputDirectory, string.Format("page{0}.png", number));
    return File.OpenWrite(previewImageFileName);
};
ReleasePageStream releasePageStreamDelegate = delegate(int number, Stream stream)
{
    stream.Close();
};
```
 El`createPageStreamDelegate` El método crea una secuencia para cada página del documento, mientras que el`releasePageStreamDelegate` El método cierra la secuencia después de generar la vista previa.
## Paso 6: configurar las opciones de vista previa
 A continuación, configure las opciones de vista previa creando una instancia del`PreviewOptions` clase. Especifique los métodos delegados y establezca el formato de vista previa en PNG. También puede especificar qué páginas incluir en la vista previa:
```csharp
PreviewOptions previewOptions = new PreviewOptions(createPageStreamDelegate, releasePageStreamDelegate)
{
    PreviewFormat = PreviewOptions.PreviewFormats.PNG,
    PageNumbers = new[] { 1, 2 }
};
```
En este ejemplo, estamos generando vistas previas de las dos primeras páginas del documento.
## Paso 7: generar la vista previa del documento
 Finalmente, llame al`GeneratePreview` método en el`Watermarker`objeto, pasando el configurado`PreviewOptions`. Esto generará las imágenes de vista previa y las guardará en el directorio especificado:
```csharp
watermarker.GeneratePreview(previewOptions);
```
## Conclusión
Generar vistas previas de documentos usando GroupDocs.Watermark para .NET es un proceso sencillo que se puede lograr con solo unas pocas líneas de código. Si sigue los pasos descritos en esta guía, podrá configurar fácilmente su proyecto, configurar las opciones necesarias y generar vistas previas de sus documentos. Esta poderosa biblioteca no solo simplifica el proceso de creación de marcas de agua, sino que también proporciona funciones sólidas para administrar y manipular marcas de agua.
 Si tiene alguna pregunta o necesita más ayuda, no dude en visitar el[Foro de soporte de GroupDocs.Watermark](https://forum.groupdocs.com/c/watermark/19) o referirse a la[documentación](https://tutorials.groupdocs.com/Watermark/net/).
## Preguntas frecuentes
### ¿Qué formatos de archivo son compatibles con GroupDocs.Watermark para .NET?
 GroupDocs.Watermark para .NET admite una amplia gama de formatos de archivo, incluidos PDF, DOCX, PPTX, XLSX y muchos más. Para obtener una lista completa de los formatos compatibles, consulte la[documentación](https://tutorials.groupdocs.com/Watermark/net/).
### ¿Puedo personalizar la apariencia de las marcas de agua?
Sí, GroupDocs.Watermark le permite personalizar completamente la apariencia de las marcas de agua, incluidas marcas de agua de texto, imágenes y formas. Puede ajustar propiedades como fuente, color, tamaño y transparencia.
### ¿Hay una versión de prueba disponible?
 Sí, puedes obtener un[prueba gratis](https://releases.groupdocs.com/) de GroupDocs.Watermark para .NET para evaluar sus características antes de realizar una compra.
### ¿Cómo puedo comprar una licencia para GroupDocs.Watermark?
 Puede adquirir una licencia para GroupDocs.Watermark[aquí](https://purchase.groupdocs.com/buy). Hay varias opciones de licencia disponibles para satisfacer diferentes necesidades.
### ¿Puedo utilizar GroupDocs.Watermark en un proyecto comercial?
 Sí, con una licencia válida, puede utilizar GroupDocs.Watermark en proyectos comerciales. Asegúrese de revisar los términos y condiciones de la licencia en el[pagina de compra](https://purchase.groupdocs.com/buy).