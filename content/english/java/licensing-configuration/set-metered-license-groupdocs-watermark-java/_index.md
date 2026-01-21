---
title: "How to Set License for GroupDocs Watermark (Metered) in Java"
description: "Learn how to set license for GroupDocs Watermark in Java, including how to apply watermark pdf and manage usage with a metered license."
date: "2026-01-21"
weight: 1
url: "/java/licensing-configuration/set-metered-license-groupdocs-watermark-java/"
keywords:
- metered license GroupDocs Watermark Java
- GroupDocs.Watermark setup Java
- Java document security watermarks
type: docs
---

# How to Set License for GroupDocs Watermark (Metered) in Java

Protecting intellectual property is a top priority for modern businesses, and watermarks are a proven way to do it. In this tutorial you’ll learn **how to set license** for GroupDocs.Watermark using a metered approach, so you can **apply watermark pdf** files while keeping full control over usage. We'll walk through everything from prerequisites to real‑world usage scenarios, and show you exactly where to **use public private keys** to activate the license.

## Quick Answers
- **What is a metered license?** A usage‑based licensing model that tracks each API call.
- **Do I need a license file?** No – you activate with public and private keys.
- **Which Java version is required?** Java 8 or higher.
- **Can I add watermark pdf documents?** Yes, the API supports PDF, DOCX, PPTX, and images.
- **Is this method secure?** Yes, keys are transmitted over HTTPS and never stored in plain text.

## What is a Metered License and Why Use It?
A metered license lets you pay for what you actually consume, making it ideal for SaaS or micro‑service architectures. It provides **document security watermark** capabilities without the overhead of managing traditional license files, and you can scale your usage up or down instantly.

## Prerequisites
Before you begin, make sure you have:

1. **GroupDocs.Watermark for Java** ≥ 24.11 (the latest release).  
2. **JDK 8+** installed and `JAVA_HOME` configured.  
3. **Public and private keys** obtained from your GroupDocs account (you’ll use them in the code).  

## Setting Up GroupDocs.Watermark for Java

### Installation Information
Integrate GroupDocs.Watermark into your Maven project:

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

> **Tip:** The same repository URL is also used for the direct download option below.

#### Direct Download
Grab the latest JAR from the official release page: [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

### License Acquisition
To unlock premium features you need a temporary or trial license. Sign up on the [GroupDocs website](https://purchase.groupdocs.com/temporary-license/) and copy the public/private keys they provide.

### Basic Initialization
Once the library is on your classpath, you can initialize it:

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

> **Why this matters:** Even when you use a metered license, initializing the `License` object ensures the SDK is ready to accept key‑based activation later in the workflow.

## Implementation Guide

### Setting a Metered License

#### Step 1: Define the Public and Private Keys
```java
// Step 1: Define the public and private keys for the metered license.
String publicKey = "*****"; // Replace with your actual public key
String privateKey = "*****"; // Replace with your actual private key
```
These keys **use public private keys** to securely identify your account.

#### Step 2: Create an Instance of the Metered Class
```java
// Step 2: Create an instance of Metered class.
Metered metered = new Metered();
```
The `Metered` class handles all usage tracking behind the scenes.

#### Step 3: Set the Metered License Using Provided Keys
```java
// Step 3: Set the metered license using the provided keys.
metered.setMeteredKey(publicKey, privateKey);
```
After this call the SDK is fully licensed and you can start to **add watermark pdf** files or **create watermarked documents**.

### Why Use Public/Private Keys Instead of a License File?
- **Security:** Keys are never written to disk in plain text.  
- **Flexibility:** Switch environments (dev, test, prod) without copying files.  
- **Scalability:** Perfect for cloud‑native deployments where containers are immutable.

## Practical Applications

1. **Document Security:** Embed a visible or invisible watermark in PDFs to deter unauthorized distribution.  
2. **Usage Tracking:** Monitor how many documents are processed each month, helping you stay within your metered quota.  
3. **CMS Integration:** Automatically **apply watermark pdf** to every uploaded file in a content management system.

## Performance Considerations

- **Apply watermark only when needed** – avoid processing large batches unnecessarily.  
- **Reuse the `Metered` instance** across requests to reduce object creation overhead.  
- **Monitor memory** when handling high‑resolution images; the SDK provides streaming APIs to keep the footprint low.

## Common Issues and Solutions
| Issue | Solution |
|-------|----------|
| Keys are rejected | Double‑check that there are no extra spaces or line‑breaks in the strings. |
| License not activated | Ensure you called `metered.setMeteredKey(...)` **before** any watermark operation. |
| Out‑of‑memory errors on big PDFs | Use `WatermarkOptions.setUseMemoryCache(true)` to offload processing to disk. |

## Frequently Asked Questions

**Q: What is a metered license, and why should I use it?**  
A: A metered license tracks each API call, letting you pay only for actual usage and easily scale your application.

**Q: Can I switch between a trial license file and a metered key?**  
A: Yes. Just call `license.setLicense("path/to/file.lic")` for the trial, then later replace it with `metered.setMeteredKey(...)`.

**Q: What happens if my public or private key is entered incorrectly?**  
A: The SDK will throw an authentication exception and block access to premium features.

**Q: Are there limits on how many watermarks I can add per month?**  
A: Limits depend on the agreement you have with GroupDocs; check your dashboard for exact quotas.

**Q: Does this work with image files as well as PDFs?**  
A: Absolutely. The same API supports JPEG, PNG, BMP, and other common image formats.

## Resources

- [Documentation](https://docs.groupdocs.com/watermark/java/)
- [API Reference](https://reference.groupdocs.com/watermark/java)
- [Download](https://releases.groupdocs.com/watermark/java/)
- [GitHub Repository](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)
- [Free Support Forum](https://forum.groupdocs.com/c/watermark/10)
- [Temporary License Acquisition](https://purchase.groupdocs.com/temporary-license/)

---

**Last Updated:** 2026-01-21  
**Tested With:** GroupDocs.Watermark 24.11 for Java  
**Author:** GroupDocs