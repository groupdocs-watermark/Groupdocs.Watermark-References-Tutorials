---
date: '2026-02-18'
description: GroupDocs.Watermark for Java के साथ .vsdx जैसे डायग्राम फ़ाइलों में वॉटरमार्क
  कैसे जोड़ें और कैसे हटाएँ, सीखें। GroupDocs Watermark Java के साथ दस्तावेज़ की अखंडता
  की रक्षा करें।
keywords:
- GroupDocs.Watermark Java
- manage watermarks in diagrams
- Java diagram document watermarking
title: GroupDocs.Watermark for Java का उपयोग करके डायग्राम में वॉटरमार्क कैसे जोड़ें
type: docs
url: /hi/java/diagram-document-watermarking/manage-watermarks-groupdocs-java-diagrams/
weight: 1
---

# How to Add Watermark to Diagrams using GroupDocs.Watermark for Java

डायग्राम फ़ाइलों में वॉटरमार्क का प्रबंधन बौद्धिक संपदा की सुरक्षा और सार्वजनिक वितरण के लिए दस्तावेज़ों को साफ़ रखने का एक मुख्य हिस्सा है। इस गाइड में आप Visio डायग्राम में **वॉटरमार्क कैसे जोड़ें** और जब इसकी आवश्यकता न रहे तो **वॉटरमार्क कैसे हटाएँ** सीखेंगे, सभी **groupdocs watermark java** लाइब्रेरी के साथ। चाहे आप एंटरप्राइज़‑ग्रेड दस्तावेज़ पाइपलाइन बना रहे हों या एक त्वरित यूटिलिटी स्क्रिप्ट, ये चरण आपको डायग्राम वॉटरमार्किंग पर पूर्ण नियंत्रण देंगे।

## Quick Answers
- **Java में डायग्राम वॉटरमार्क को संभालने वाली लाइब्रेरी कौन सी है?** GroupDocs.Watermark for Java.  
- **क्या मैं एक ही रन में वॉटरमार्क जोड़ और हटा सकता हूँ?** हाँ – डायग्राम को एक बार लोड करें और दोनों जोड़ने व हटाने के ऑपरेशन लागू करें।  
- **कौन से फ़ाइल फ़ॉर्मेट समर्थित हैं?** Visio फ़ॉर्मेट जैसे `.vsdx`, `.vdx`, साथ ही अन्य डायग्राम प्रकार।  
- **क्या मुझे लाइसेंस चाहिए?** डेवलपमेंट के लिए ट्रायल लाइसेंस काम करता है; प्रोडक्शन के लिए पूर्ण लाइसेंस आवश्यक है।  
- **कौन सा Java संस्करण आवश्यक है?** JDK 8 या उससे ऊपर।

## What is “how to add watermark” in the context of diagrams?
वॉटरमार्क जोड़ना का मतलब है एक दृश्यमान या अदृश्य मार्कर—टेक्स्ट, लोगो या इमेज—को डायग्राम फ़ाइल में एम्बेड करना। यह मार्कर फ़ाइल के साथ रहता है, जिससे स्वामित्व साबित करना या ड्राफ्ट संस्करण को चिह्नित करना आसान हो जाता है।

## Why use GroupDocs.Watermark for Java?
* **Rich API** – कुछ ही कोड लाइनों से टेक्स्ट और इमेज दोनों वॉटरमार्क को खोजें, जोड़ें और हटाएँ।  
* **Cross‑format support** – Visio (`.vsdx`, `.vdx`) और कई अन्य डायग्राम प्रकारों के साथ काम करता है।  
* **Performance‑focused** – वॉटरमार्क ऑपरेशन्स के लिए आवश्यक भागों को ही लोड करता है, जिससे मेमोरी उपयोग कम रहता है।

## Prerequisites
1. **Java Development Kit (JDK) 8+** – सुनिश्चित करें कि `java -version` 1.8 या नया दिखा रहा है।  
2. **IDE** – IntelliJ IDEA, Eclipse, या कोई भी एडिटर जो आप पसंद करते हैं।  
3. **GroupDocs.Watermark for Java** – इसे अपने प्रोजेक्ट में Maven या सीधे JAR डाउनलोड के माध्यम से जोड़ें।  

### Required Libraries and Dependencies
अपने `pom.xml` में रिपॉज़िटरी और डिपेंडेंसी जोड़ें:

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

*यदि आप Maven का उपयोग नहीं करना चाहते हैं, तो आप नवीनतम JAR [GroupDocs.Watermark for Java रिलीज़](https://releases.groupdocs.com/watermark/java/) से डाउनलोड कर सकते हैं।*

### License Acquisition
- **Free Trial:** लाइसेंस कुंजी के बिना सभी फीचर टेस्ट करें।  
- **Temporary License:** मूल्यांकन के लिए समय‑सीमित कुंजी का अनुरोध करें।  
- **Full License:** अनलिमिटेड प्रोडक्शन उपयोग के लिए सब्सक्रिप्शन खरीदें।

## Setting Up GroupDocs.Watermark for Java
1. **Add the library** को अपने प्रोजेक्ट में जोड़ें (Maven या मैन्युअल JAR)।  
2. **Create a `Watermarker` instance** – यह ऑब्जेक्ट डायग्राम लोड करने, खोजने, जोड़ने और हटाने के लिए एंट्री पॉइंट है।

## Implementation Guide

### Loading a Diagram Document
लोडिंग वह पहला कदम है जिससे आप **वॉटरमार्क जोड़ें** या **वॉटरमार्क हटाएँ** कर सकते हैं। नीचे दिया गया कोड दिखाता है कि कैसे कस्टम लोड ऑप्शन्स के साथ `.vsdx` फ़ाइल खोलें।

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.DiagramLoadOptions;

public class LoadDiagramDocument {
    public static void main(String[] args) {
        String inputFilePath = "YOUR_DOCUMENT_DIRECTORY/diagram.vsdx";
        DiagramLoadOptions loadOptions = new DiagramLoadOptions();
        
        Watermarker watermarker = new Watermarker(inputFilePath, loadOptions);
        watermarker.close();
    }
}
```

### Searching for Text Watermarks
नया वॉटरमार्क जोड़ने से पहले आप यह जांचना चाह सकते हैं कि कोई टेक्स्ट वॉटरमार्क पहले से मौजूद है या नहीं। यह स्निपेट “Company Name” वाक्यांश की खोज करता है।

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.contents.DiagramContent;
import com.groupdocs.watermark.search.TextSearchCriteria;
import com.groupdocs.watermark.search.PossibleWatermarkCollection;

public class SearchTextWatermarks {
    public static void main(String[] args) throws Exception {
        String inputFilePath = "YOUR_DOCUMENT_DIRECTORY/diagram.vsdx";
        Watermarker watermarker = new Watermarker(inputFilePath);

        DiagramContent content = watermarker.getContent(DiagramContent.class);
        
        TextSearchCriteria textSearchCriteria = new TextSearchCriteria("Company Name");
        PossibleWatermarkCollection possibleWatermarks = content.getPages().get_Item(0).search(textSearchCriteria);

        watermarker.close();
    }
}
```

### Searching for Image Watermarks
यदि आपको किसी लोगो या इमेज को ढूँढना है जो वॉटरमार्क के रूप में उपयोग हुई थी, तो `ImageDctHashSearchCriteria` का उपयोग करें। यह तब उपयोगी है जब आप ज्ञात लोगो से मेल खाने वाला **वॉटरमार्क हटाएँ** चाहते हैं।

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.contents.DiagramContent;
import com.groupdocs.watermark.search.ImageDctHashSearchCriteria;
import com.groupdocs.watermark.search.PossibleWatermarkCollection;

public class SearchImageWatermarks {
    public static void main(String[] args) throws Exception {
        String inputFilePath = "YOUR_DOCUMENT_DIRECTORY/diagram.vsdx";
        String imagePath = "YOUR_DOCUMENT_DIRECTORY/logo.png";
        
        Watermarker watermarker = new Watermarker(inputFilePath);
        DiagramContent content = watermarker.getContent(DiagramContent.class);

        ImageDctHashSearchCriteria imageSearchCriteria = new ImageDctHashSearchCriteria(imagePath);
        PossibleWatermarkCollection possibleWatermarks = content.getPages().get_Item(0).search(imageSearchCriteria);

        watermarker.close();
    }
}
```

### Removing Watermarks
एक बार जब आप वॉटरमार्क—टेक्स्ट, इमेज या दोनों—की पहचान कर लेते हैं, तो आप उन्हें डायग्राम से साफ़ कर सकते हैं। नीचे दिया गया उदाहरण संयुक्त हटाने का ऑपरेशन दर्शाता है।

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.contents.DiagramContent;
import com.groupdocs.watermark.search.TextSearchCriteria;
import com.groupdocs.watermark.search.ImageDctHashSearchCriteria;
import com.groupdocs.watermark.search.PossibleWatermarkCollection;

public class RemoveWatermarks {
    public static void main(String[] args) throws Exception {
        String inputFilePath = "YOUR_DOCUMENT_DIRECTORY/diagram.vsdx";
        String outputFilePath = "YOUR_OUTPUT_DIRECTORY/updated_diagram.vsdx";

        Watermarker watermarker = new Watermarker(inputFilePath);
        DiagramContent content = watermarker.getContent(DiagramContent.class);

        TextSearchCriteria textSearchCriteria = new TextSearchCriteria("Company Name");
        ImageDctHashSearchCriteria imageSearchCriteria = new ImageDctHashSearchCriteria("YOUR_DOCUMENT_DIRECTORY/logo.png");

        PossibleWatermarkCollection possibleWatermarks = content.getPages().get_Item(0).search(textSearchCriteria.or(imageSearchCriteria));
        possibleWatermarks.clear();

        watermarker.save(outputFilePath);
        watermarker.close();
    }
}
```

## Practical Applications
1. **Enterprise Software Integration** – अपने ERP या दस्तावेज़‑जनरेशन प्लेटफ़ॉर्म में वॉटरमार्क प्रबंधन को एम्बेड करें ताकि ब्रांडिंग लागू हो सके।  
2. **Content Management Systems (CMS)** – अपलोड किए गए डायग्राम को स्वचालित रूप से अनधिकृत लोगो के लिए स्कैन करें और उन्हें हटा दें।  
3. **Legal Document Handling** – ड्राफ्ट चरण में “Confidential” टेक्स्ट वॉटरमार्क जोड़ें और अंतिम फ़ाइलिंग से पहले **वॉटरमार्क हटाएँ**।

## Common Issues and Solutions
| Symptom | Likely Cause | Fix |
|---------|--------------|-----|
| No watermarks are found | Search text/image does not exactly match | Use `or()` to combine criteria or adjust case‑sensitivity settings. |
| `OutOfMemoryError` on large files | Diagram loaded entirely into memory | Use `DiagramLoadOptions.setLoadPages()` to load only needed pages. |
| Saved file is corrupted | `watermarker.save()` called before clearing all watermarks | Ensure `possibleWatermarks.clear()` completes and `watermarker.close()` is invoked after saving. |

## Frequently Asked Questions

**Q: क्या मैं टेक्स्ट और इमेज दोनों को एक साथ खोज सकता हूँ?**  
A: हाँ। `TextSearchCriteria` और `ImageDctHashSearchCriteria` को `or()` मेथड के साथ मिलाएँ, जैसा कि हटाने के उदाहरण में दिखाया गया है।

**Q: क्या वॉटरमार्क हटाते समय डायग्राम को नुकसान पहुँच सकता है?**  
A: बिल्कुल नहीं। लाइब्रेरी वॉटरमार्क ऑब्जेक्ट को अलग करती है, इसलिए `clear()` कॉल करने से केवल वॉटरमार्क लेयर हटती है जबकि मूल डायग्राम कंटेंट बना रहता है।

**Q: क्या GroupDocs.Watermark कई डायग्राम फ़ॉर्मेट को सपोर्ट करता है?**  
A: हाँ। `.vsdx`, `.vdx` और अन्य Visio‑compatible फ़ाइलें पूरी तरह सपोर्टेड हैं।

**Q: बड़े पैमाने पर दस्तावेज़ों को कुशलता से कैसे संभालूँ?**  
A: बैच प्रोसेसिंग लूप लागू करें, जहाँ संभव हो एक ही `Watermarker` इंस्टेंस को पुनः उपयोग करें, और `DiagramLoadOptions` के साथ पेज लोडिंग को सीमित करें।

**Q: क्या CI/CD पाइपलाइन में वॉटरमार्क डिटेक्शन को ऑटोमेट करने का कोई तरीका है?**  
A: आप प्रदान किए गए Java स्निपेट को अपने बिल्ड स्क्रिप्ट (जैसे Maven या Gradle) में एम्बेड कर सकते हैं ताकि रिलीज़ से पहले यह वैलिडेट किया जा सके कि कोई अनधिकृत वॉटरमार्क मौजूद नहीं है।

---

**अंतिम अपडेट:** 2026-02-18  
**परीक्षित संस्करण:** GroupDocs.Watermark 24.11 for Java  
**लेखक:** GroupDocs