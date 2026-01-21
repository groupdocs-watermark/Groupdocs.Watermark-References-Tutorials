---
date: '2026-01-21'
description: Aprende a configurar la licencia de GroupDocs Watermark en Java, incluyendo
  cómo aplicar una marca de agua a PDF y gestionar el uso con una licencia medida.
keywords:
- metered license GroupDocs Watermark Java
- GroupDocs.Watermark setup Java
- Java document security watermarks
title: Cómo establecer la licencia para GroupDocs Watermark (medido) en Java
type: docs
url: /es/java/licensing-configuration/set-metered-license-groupdocs-watermark-java/
weight: 1
---

# Cómo establecer la licencia para GroupDocs Watermark (medido) en Java

Proteger la propiedad intelectual es una prioridad principal para las empresas modernas, y las marcas de agua son una forma probada de hacerlo. En este tutorial aprenderá **cómo establecer la licencia** para GroupDocs.Watermark usando un enfoque medido, para que pueda **aplicar marcas de agua a archivos PDF** mientras mantiene el control total sobre el uso. Revisaremos todo, desde los requisitos previos hasta escenarios de uso del mundo real, y le mostraremos exactamente dónde **usar claves públicas y privadas** para activar la licencia.

## Respuestas rápidas
- **¿Qué es una licencia medida?** Un modelo de licencia basado en el uso que rastrea cada llamada a la API.  
- **¿Necesito un archivo de licencia?** No – se activa con claves públicas y privadas.  
- **¿Qué versión de Java se requiere?** Java 8 o superior.  
- **¿Puedo agregar marcas de agua a documentos PDF?** Sí, la API soporta PDF, DOCX, PPTX e imágenes.  
- **¿Es este método seguro?** Sí, las claves se transmiten por HTTPS y nunca se almacenan en texto plano.

## Qué es una licencia medida y por qué usarla?
Una licencia medida le permite pagar solo por lo que realmente consume, lo que la hace ideal para arquitecturas SaaS o de micro‑servicios. Proporciona capacidades de **marca de agua de seguridad de documentos** sin la sobrecarga de gestionar archivos de licencia tradicionales, y puede escalar su uso hacia arriba o hacia abajo instantáneamente.

## Requisitos previos
1. **GroupDocs.Watermark for Java** ≥ 24.11 (la última versión).  
2. **JDK 8+** instalado y `JAVA_HOME` configurado.  
3. **Claves públicas y privadas** obtenidas de su cuenta de GroupDocs (las usará en el código).  

## Configuración de GroupDocs.Watermark para Java

### Información de instalación
Integre GroupDocs.Watermark en su proyecto Maven:

```xml
<repositories>
   <repository>
      <id>repository.groupdocs.com</id>
      <name>GroupDocs Repository</name>
      <url>https://releases.groupdocs.com/watermark/java/</url>
   </repository>
</repositories>

<dependencies>
   <dependency>
      <groupId>com.groupdocs</groupId>
      <artifactId>groupdocs-watermark</artifactId>
      <version>24.11</version>
   </dependency>
</dependencies>
```

> **Consejo:** La misma URL del repositorio también se usa para la opción de descarga directa a continuación.

#### Descarga directa
Obtenga el último JAR de la página oficial de lanzamientos: [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

### Obtención de licencia
Para desbloquear funciones premium necesita una licencia temporal o de prueba. Regístrese en el [sitio web de GroupDocs](https://purchase.groupdocs.com/temporary-license/) y copie las claves públicas/privadas que proporcionan.

### Inicialización básica
Una vez que la biblioteca está en su classpath, puede inicializarla:

```java
import com.groupdocs.watermark.License;

public class InitializeWatermark {
    public static void main(String[] args) throws Exception {
        License license = new License();
        // Apply the license using your path to the license file
        license.setLicense("path/to/your/license/file.lic");
    }
}
```

> **Por qué es importante:** Incluso cuando usa una licencia medida, inicializar el objeto `License` garantiza que el SDK esté listo para aceptar la activación basada en claves más adelante en el flujo de trabajo.

## Guía de implementación

### Configuración de una licencia medida

#### Paso 1: Definir las claves públicas y privadas
```java
// Step 1: Define the public and private keys for the metered license.
String publicKey = "*****"; // Replace with your actual public key
String privateKey = "*****"; // Replace with your actual private key
```
Estas claves **usan claves públicas y privadas** para identificar de forma segura su cuenta.

#### Paso 2: Crear una instancia de la clase Metered
```java
// Step 2: Create an instance of Metered class.
Metered metered = new Metered();
```
La clase `Metered` maneja todo el seguimiento de uso en segundo plano.

#### Paso 3: Establecer la licencia medida usando las claves proporcionadas
```java
// Step 3: Set the metered license using the provided keys.
metered.setMeteredKey(publicKey, privateKey);
```
Después de esta llamada el SDK está completamente licenciado y puede comenzar a **agregar marcas de agua a archivos PDF** o **crear documentos con marca de agua**.

### ¿Por qué usar claves públicas/privadas en lugar de un archivo de licencia?
- **Seguridad:** Las claves nunca se escriben en disco en texto plano.  
- **Flexibilidad:** Cambiar de entornos (dev, test, prod) sin copiar archivos.  
- **Escalabilidad:** Perfecto para implementaciones nativas en la nube donde los contenedores son inmutables.

## Aplicaciones prácticas

1. **Seguridad de documentos:** Inserte una marca de agua visible o invisible en PDFs para disuadir la distribución no autorizada.  
2. **Seguimiento de uso:** Monitoree cuántos documentos se procesan cada mes, ayudándole a mantenerse dentro de su cuota medida.  
3. **Integración CMS:** Aplique automáticamente **marcas de agua a PDFs** a cada archivo subido en un sistema de gestión de contenidos.

## Consideraciones de rendimiento

- **Aplicar la marca de agua solo cuando sea necesario** – evite procesar lotes grandes innecesariamente.  
- **Reutilizar la instancia `Metered`** entre solicitudes para reducir la sobrecarga de creación de objetos.  
- **Monitorear la memoria** al manejar imágenes de alta resolución; el SDK proporciona APIs de streaming para mantener bajo el consumo.

## Problemas comunes y soluciones

| Problema | Solución |
|----------|----------|
| Las claves son rechazadas | Verifique que no haya espacios extra o saltos de línea en las cadenas. |
| Licencia no activada | Asegúrese de haber llamado a `metered.setMeteredKey(...)` **antes** de cualquier operación de marca de agua. |
| Errores de falta de memoria en PDFs grandes | Utilice `WatermarkOptions.setUseMemoryCache(true)` para descargar el procesamiento al disco. |

## Preguntas frecuentes

**P: ¿Qué es una licencia medida y por qué debería usarla?**  
R: Una licencia medida rastrea cada llamada a la API, permitiéndole pagar solo por el uso real y escalar fácilmente su aplicación.

**P: ¿Puedo cambiar entre un archivo de licencia de prueba y una clave medida?**  
R: Sí. Simplemente llame a `license.setLicense("path/to/file.lic")` para la prueba, y luego reemplácelo con `metered.setMeteredKey(...)`.

**P: ¿Qué ocurre si mi clave pública o privada se ingresa incorrectamente?**  
R: El SDK lanzará una excepción de autenticación y bloqueará el acceso a las funciones premium.

**P: ¿Hay límites en cuántas marcas de agua puedo agregar por mes?**  
R: Los límites dependen del acuerdo que tenga con GroupDocs; consulte su panel para conocer las cuotas exactas.

**P: ¿Esto funciona con archivos de imagen además de PDFs?**  
R: Absolutamente. La misma API soporta JPEG, PNG, BMP y otros formatos de imagen comunes.

## Recursos

- [Documentación](https://docs.groupdocs.com/watermark/java/)
- [Referencia de API](https://reference.groupdocs.com/watermark/java)
- [Descarga](https://releases.groupdocs.com/watermark/java/)
- [Repositorio de GitHub](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)
- [Foro de soporte gratuito](https://forum.groupdocs.com/c/watermark/10)
- [Obtención de licencia temporal](https://purchase.groupdocs.com/temporary-license/)

---

**Última actualización:** 2026-01-21  
**Probado con:** GroupDocs.Watermark 24.11 for Java  
**Autor:** GroupDocs