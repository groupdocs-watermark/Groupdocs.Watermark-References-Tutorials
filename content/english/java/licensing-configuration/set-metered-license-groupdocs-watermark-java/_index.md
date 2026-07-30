---
date: '2026-07-30'
description: Learn how to set license for GroupDocs.Watermark in Java, protect your
  documents effectively and manage usage efficiently.
images:
- /java/licensing-configuration/set-metered-license-groupdocs-watermark-java/og-image.png
keywords:
- how to set license
- GroupDocs Watermark Java
- metered licensing Java
lastmod: '2026-07-30'
og_description: How to set license for GroupDocs.Watermark in Java. This guide walks
  you through installing the SDK, acquiring a metered key, and configuring the license
  to secure your documents.
og_image_alt: 'Guide: Set license for GroupDocs Watermark in Java'
og_title: How to Set License for GroupDocs Watermark in Java
schemas:
- author: GroupDocs
  dateModified: '2026-07-30'
  description: Learn how to set license for GroupDocs.Watermark in Java, protect your
    documents effectively and manage usage efficiently.
  headline: How to Set License for GroupDocs Watermark in Java
  type: TechArticle
- description: Learn how to set license for GroupDocs.Watermark in Java, protect your
    documents effectively and manage usage efficiently.
  name: How to Set License for GroupDocs Watermark in Java
  steps:
  - name: Define the public and private keys
    text: Enter the keys you received after registering for a temporary license. `Metered`
      is the GroupDocs.Watermark class that handles metered licensing and usage tracking.
      *Place your keys in a secure location (environment variables, encrypted config,
      etc.) before using them in code.*
  - name: Create an instance of the Metered class
    text: Instantiate the `Metered` object with your keys. This object will be passed
      to the watermark engine during initialization.
  - name: Set the metered license using the provided keys
    text: Call the `setLicense` method (or the equivalent API call) with your public
      and private keys. Once set, all subsequent watermark operations will be billed
      according to your usage. > **Pro tip:** Keep the keys out of source control.
      Use a secrets manager or encrypted properties file to avoid accidenta
  type: HowTo
- questions:
  - answer: A temporary license is time‑limited and ideal for evaluation, while a
      perpetual license provides unlimited use without recurring fees.
    question: What is the difference between a temporary and a perpetual license?
  - answer: Yes—replace the metered key initialization with a call to `engine.setLicense("path/to/license/file")`.
    question: Can I switch from a metered license to a perpetual one without code
      changes?
  - answer: The SDK falls back to offline mode; watermarking continues but usage won’t
      be reported until connectivity is restored.
    question: What happens if the metered service is unreachable?
  - answer: The SDK can handle files up to 1 GB; larger files should be split or processed
      in streaming mode.
    question: Are there file‑size limits for watermarking?
  - answer: It works on any platform that supports Java 8+, including Windows, Linux,
      and macOS.
    question: Does the metered license work on all operating systems?
  type: FAQPage
tags:
- set license
- GroupDocs Watermark
- Java licensing
- metered license
- document security
title: How to Set License for GroupDocs Watermark in Java
type: docs
url: /java/licensing-configuration/set-metered-license-groupdocs-watermark-java/
weight: 1
---

# How to Set License for GroupDocs Watermark in Java

Protecting intellectual property is a top priority for modern applications, and watermarks are a proven way to deter unauthorized distribution. If you’re using **GroupDocs.Watermark for Java**, you’ll need a license that can track usage and scale with demand. This tutorial explains **how to set license** for GroupDocs.Watermark in Java, from installing the SDK to configuring a metered key that reports consumption back to the service.

## Quick Answers
- **What is a metered license?** It’s a usage‑based license that records each API call, allowing you to pay only for what you consume.  
- **Do I need a trial first?** Yes, you can request a temporary license from the GroupDocs site to evaluate the product.  
- **Which Java version is required?** Java 8 or newer; the SDK is compiled for JDK 8+.  
- **Can I switch to a perpetual license later?** Absolutely – just replace the metered keys with a permanent license file.  
- **Is the setup compatible with Maven?** Yes, the Maven coordinates are provided for seamless dependency management.

## What is a metered license for GroupDocs Watermark?
A metered license is a cloud‑enabled entitlement provided by GroupDocs that records each watermarking operation performed by the SDK. Each API call is logged on GroupDocs’ licensing server, allowing pay‑as‑you‑go billing based on actual usage. This model gives developers real‑time insight into consumption and helps control costs while ensuring full feature access.

## Why use a metered license with GroupDocs Watermark?
GroupDocs.Watermark supports more than fifty input and output formats—including PDF, DOCX, PPTX, and various image types—and can process files up to 1 GB without loading the whole document into memory, which preserves performance. By using a metered license you only pay for the operations you actually run, allowing the solution to scale cost‑effectively while retaining full access to all features.

## Prerequisites
- **GroupDocs.Watermark for Java** version 24.11 or later.  
- A Java Development Kit (JDK) 8 or newer installed and configured.  
- Basic familiarity with Maven or manual JAR management.  
- A temporary or permanent license key from the GroupDocs portal.

## How to set a metered license for GroupDocs Watermark in Java?

Load your public and private keys, create a `Metered` instance, and apply the license—all in three concise steps. This approach guarantees that every watermarking request is counted against your account, giving you full visibility into consumption.

### Step 1: Define the public and private keys
Enter the keys you received after registering for a temporary license.

`Metered` is the GroupDocs.Watermark class that handles metered licensing and usage tracking.  
*Place your keys in a secure location (environment variables, encrypted config, etc.) before using them in code.*

### Step 2: Create an instance of the Metered class
Instantiate the `Metered` object with your keys. This object will be passed to the watermark engine during initialization.

```text
Metered metered = new Metered(System.getenv("GROUPDOCS_PUBLIC_KEY"),
                               System.getenv("GROUPDOCS_PRIVATE_KEY"));
```

### Step 3: Set the metered license using the provided keys
Call the `setLicense` method (or the equivalent API call) with your public and private keys. Once set, all subsequent watermark operations will be billed according to your usage.

```text
WatermarkEngine engine = new WatermarkEngine();
engine.setMeteredLicense(metered);
```

> **Pro tip:** Keep the keys out of source control. Use a secrets manager or encrypted properties file to avoid accidental exposure.

## Setting Up GroupDocs.Watermark for Java

### Installation Information

Integrate GroupDocs.Watermark into your project using Maven or by downloading the JAR directly.

**Maven Setup:**  
Add the following configuration in your `pom.xml` file:

```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>watermark</artifactId>
    <version>24.11</version>
</dependency>
```

**Direct Download:**  
Download the latest version from [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

### License Acquisition

To unlock full functionality, obtain a free trial or temporary license:

- Sign up on the [GroupDocs website](https://purchase.groupdocs.com/temporary-license/) to get started.  
- After acquiring your keys, integrate them into your project as shown in the implementation guide.

### Basic Initialization and Setup

Once the SDK is added to your project, import the necessary namespaces and create the watermark engine instance as demonstrated in the code snippets above.

## Troubleshooting Tips
- **Invalid keys:** Double‑check that the public and private keys match exactly; a single typo will prevent activation.  
- **License file path errors:** If you prefer a file‑based license, ensure the file path is absolute or correctly resolved relative to the working directory.  
- **Network issues:** Metered licensing requires outbound HTTPS calls; verify that your firewall allows traffic to `api.groupdocs.com`.

## Practical Applications
1. **Document Security:** Add visible or invisible watermarks to PDFs, Word documents, and images to protect sensitive corporate data.  
2. **Usage Tracking:** Generate reports on how many documents have been watermarked per day, useful for budgeting and compliance.  
3. **CMS Integration:** Automate watermark insertion during content publishing workflows, with licensing automatically enforced.

## Performance Considerations

**Optimizing Performance:**  
- Apply watermarks only when necessary; skip processing for already‑protected files.  
- For large batches, reuse the same `WatermarkEngine` instance to avoid repeated initialization overhead.  

**Best Practices:**  
- Monitor JVM heap usage when processing multi‑hundred‑page PDFs; consider streaming APIs if memory becomes a bottleneck.  
- Enable logging at the `INFO` level to capture licensing calls without overwhelming the console.

## Conclusion

In this guide we covered **how to set license** for GroupDocs.Watermark in Java, from Maven installation to metered key configuration. By following the steps, you gain precise usage tracking, flexible billing, and robust document protection—all without compromising performance.

**Next Steps:**  
- Experiment with different watermark styles (text, image, diagonal).  
- Explore advanced features such as conditional watermarks based on user roles.  
- Review the GroupDocs analytics dashboard to monitor consumption trends.

Ready to secure your documents? Implement the solution today and enjoy peace of mind knowing your assets are protected and your licensing costs are transparent.

## Frequently Asked Questions

**Q: What is the difference between a temporary and a perpetual license?**  
A: A temporary license is time‑limited and ideal for evaluation, while a perpetual license provides unlimited use without recurring fees.

**Q: Can I switch from a metered license to a perpetual one without code changes?**  
A: Yes—replace the metered key initialization with a call to `engine.setLicense("path/to/license/file")`.

**Q: What happens if the metered service is unreachable?**  
A: The SDK falls back to offline mode; watermarking continues but usage won’t be reported until connectivity is restored.

**Q: Are there file‑size limits for watermarking?**  
A: The SDK can handle files up to 1 GB; larger files should be split or processed in streaming mode.

**Q: Does the metered license work on all operating systems?**  
A: It works on any platform that supports Java 8+, including Windows, Linux, and macOS.

---

**Last Updated:** 2026-07-30  
**Tested With:** GroupDocs.Watermark 24.11 for Java  
**Author:** GroupDocs  

**Resources**

- [Documentation](https://docs.groupdocs.com/watermark/java/)
- [API Reference](https://reference.groupdocs.com/watermark/java)
- [Download](https://releases.groupdocs.com/watermark/java/)
- [GitHub Repository](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)
- [Free Support Forum](https://forum.groupdocs.com/c/watermark/10)
- [Temporary License Acquisition](https://purchase.groupdocs.com/temporary-license/)

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

```java
// Step 1: Define the public and private keys for the metered license.
String publicKey = "*****"; // Replace with your actual public key
String privateKey = "*****"; // Replace with your actual private key
```

```java
// Step 2: Create an instance of Metered class.
Metered metered = new Metered();
```

```java
// Step 3: Set the metered license using the provided keys.
metered.setMeteredKey(publicKey, privateKey);
```

## Related Tutorials

- [GroupDocs.Watermark for Java Licensing and Configuration Tutorials](/watermark/java/licensing-configuration/)
- [How to Set Up GroupDocs.Watermark Licensing in Java: A Complete Guide](/watermark/java/licensing-configuration/groupdocs-watermark-licensing-java-guide/)
- [Java Watermarking Guide: Secure Documents with GroupDocs.Watermark API](/watermark/java/getting-started/java-watermark-groupdocs-guide/)