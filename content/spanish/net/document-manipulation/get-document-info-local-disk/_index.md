---
title: Obtener información del documento desde el disco local
linktitle: Obtener información del documento desde el disco local
second_title: API GroupDocs.Watermark .NET
description: Aprenda a agregar, eliminar y extraer marcas de agua en documentos usando GroupDocs Watermark para .NET con esta guía completa paso a paso.
type: docs
weight: 11
url: /es/net/document-manipulation/get-document-info-local-disk/
---
## Introducción
¡Bienvenido a la guía definitiva sobre el uso de GroupDocs.Watermark para .NET! Ya sea que sea un desarrollador experimentado o recién esté comenzando, este artículo lo guiará a través de los aspectos esenciales para agregar marcas de agua a sus documentos con esta poderosa herramienta. Al final, serás un profesional incrustando marcas de agua en tus documentos, asegurándote de que estén protegidos y con la marca según tus especificaciones.
## Requisitos previos
Antes de sumergirse en la guía paso a paso, existen algunos requisitos previos que deberá cumplir:
1.  .NET Framework: asegúrese de tener .NET Framework instalado en su sistema. GroupDocs.Watermark para .NET es compatible con varias versiones de .NET Framework, así que verifique la[documentación](https://reference.groupdocs.com/Watermark/net/) para detalles de compatibilidad.
2.  GroupDocs.Watermark para la biblioteca .NET: descargue e instale la última versión desde[pagina de descarga](https://releases.groupdocs.com/Watermark/net/).
3. Entorno de desarrollo: debe tener configurado un entorno de desarrollo. Visual Studio es una opción popular para el desarrollo .NET.
4. Conocimientos básicos de C#: comprender los conceptos básicos de la programación en C# le ayudará a seguir los ejemplos.
## Importar espacios de nombres
Antes de poder utilizar GroupDocs.Watermark para .NET, debe importar los espacios de nombres necesarios a su proyecto. Este es un proceso sencillo y esencial para acceder a las funciones de la biblioteca.
```csharp
using System;
using GroupDocs.Watermark.Common;
```
Dividamos el proceso de poner una marca de agua en un documento en pasos claros y manejables. Cada paso está diseñado para ayudarle a comprender e implementar la funcionalidad con facilidad.
## Paso 1: cargue su documento
 El primer paso es cargar el documento al que desea ponerle una marca de agua. Esto se hace usando el`Watermarker` clase, que le permite acceder y manipular su documento.
```csharp
using (Watermarker watermarker = new Watermarker("Your Document Path"))
{
    // El documento ahora está cargado y listo para la marca de agua.
}
```
 En este paso, reemplace`"Your Document Path"` con la ruta real a su documento. Esto inicializa el`Watermarker`objeto, dándole acceso a varias funcionalidades de marcas de agua.
## Paso 2: Obtenga información del documento
Antes de agregar una marca de agua, es posible que desee recopilar información sobre el documento. Esto puede resultar útil para personalizar su marca de agua según las propiedades del documento.

```csharp
using (Watermarker watermarker = new Watermarker("Your Document Path"))
{
    IDocumentInfo info = watermarker.GetDocumentInfo();
    Console.WriteLine("File type: {0}", info.FileType);
    Console.WriteLine("Number of pages: {0}", info.PageCount);
    Console.WriteLine("Document size: {0} bytes", info.Size);
}
```
 En este paso, el`GetDocumentInfo` El método recupera detalles como el tipo de archivo, el número de páginas y el tamaño del documento. Esta información se imprime en la consola, pero puede usarla en su aplicación según sea necesario.
## Paso 3: agregue una marca de agua de texto
Ahora que tienes tu documento cargado y su información a mano, es hora de agregar una marca de agua. Comenzaremos con una simple marca de agua de texto.

```csharp
using (Watermarker watermarker = new Watermarker("Your Document Path"))
{
    TextWatermark textWatermark = new TextWatermark("Confidential", new Font("Arial", 36));
    textWatermark.ForegroundColor = Color.Red;
    textWatermark.BackgroundColor = Color.Yellow;
    textWatermark.Opacity = 0.5;
    textWatermark.RotateAngle = 45;
    watermarker.Add(textWatermark);
    watermarker.Save("Watermarked Document Path");
}
```
 Aquí creas un`TextWatermark` objeto con el texto, la fuente y el estilo que desee. Ajuste propiedades como color, opacidad y ángulo de rotación para satisfacer sus necesidades. Finalmente, la marca de agua se agrega al documento y se guarda en una ruta específica.
## Paso 4: agregue una marca de agua de imagen
Las marcas de agua de texto son geniales, pero ¿qué pasa si quieres agregar un logotipo u otra imagen? Este paso cubre cómo agregar una marca de agua de imagen.

```csharp
using (Watermarker watermarker = new Watermarker("Your Document Path"))
{
    using (ImageWatermark imageWatermark = new ImageWatermark("Path to Your Image"))
    {
        imageWatermark.Opacity = 0.5;
        imageWatermark.RotateAngle = 30;
        watermarker.Add(imageWatermark);
        watermarker.Save("Watermarked Document Path");
    }
}
```
 Reemplazar`"Path to Your Image"` con la ruta a la imagen de su marca de agua. Establezca propiedades como la opacidad y el ángulo de rotación para personalizar la apariencia de la marca de agua de su imagen. El proceso de agregar y guardar la marca de agua es similar al de una marca de agua de texto.
## Paso 5: eliminar las marcas de agua existentes
 A veces, es posible que necesites eliminar marcas de agua existentes de un documento. Esto se puede hacer usando el`Remove` método proporcionado por el`Watermarker` clase.

```csharp
using (Watermarker watermarker = new Watermarker("Your Document Path"))
{
    watermarker.Remove(WatermarkType.Text);
    watermarker.Save("Cleaned Document Path");
}
```
 Aquí el`Remove` El método se utiliza para eliminar marcas de agua de texto del documento. Puede especificar diferentes tipos de marcas de agua para eliminar, como imagen o texto, según sus necesidades. Guarde el documento en una nueva ruta para ver los cambios.
## Paso 6: extraer marcas de agua
Si necesita extraer e inspeccionar marcas de agua de un documento, GroupDocs.Watermark para .NET lo hace posible con facilidad.

```csharp
using (Watermarker watermarker = new Watermarker("Your Document Path"))
{
    IEnumerable<Watermark> watermarks = watermarker.GetWatermarks();
    foreach (Watermark watermark in watermarks)
    {
        Console.WriteLine("Watermark type: {0}", watermark.GetType().Name);
        // Propiedades y lógica adicionales para cada marca de agua.
    }
}
```
 Este paso implica utilizar el`GetWatermarks`Método para recuperar todas las marcas de agua en un documento. Luego puede recorrer la lista de marcas de agua e inspeccionar sus propiedades o realizar acciones adicionales según sea necesario.
## Conclusión
 ¡Felicidades! Ahora ha aprendido a utilizar GroupDocs.Watermark para .NET para agregar, eliminar y extraer marcas de agua de sus documentos. Con estas habilidades, podrá proteger y marcar sus documentos de forma eficaz. Recuerda el[documentación](https://reference.groupdocs.com/Watermark/net/) Siempre está ahí si necesita información más detallada o funcionalidad avanzada.
## Preguntas frecuentes
### ¿Puedo usar GroupDocs.Watermark para .NET con cualquier versión de .NET?
 Sí, GroupDocs.Watermark para .NET es compatible con varias versiones de .NET Framework. Comprobar el[documentación](https://reference.groupdocs.com/Watermark/net/) para detalles.
### ¿Dónde puedo descargar GroupDocs.Watermark para .NET?
 Puede descargar la última versión desde[pagina de descarga](https://releases.groupdocs.com/Watermark/net/).
### ¿Cómo obtengo una licencia temporal?
 Puede obtener una licencia temporal del[página de licencia temporal](https://purchase.groupdocs.com/temporary-license/).
### ¿Hay una prueba gratuita disponible?
 Sí, puedes iniciar una prueba gratuita visitando el[página de prueba gratuita](https://releases.groupdocs.com/).
### ¿Dónde puedo obtener asistencia si tengo problemas?
 El soporte está disponible en el[Foro de marcas de agua de GroupDocs](https://forum.groupdocs.com/c/watermark/19).