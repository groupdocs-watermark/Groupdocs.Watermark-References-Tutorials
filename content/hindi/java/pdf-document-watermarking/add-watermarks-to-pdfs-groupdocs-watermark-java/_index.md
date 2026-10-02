---
date: '2026-01-23'
description: GroupDocs.Watermark for Java का उपयोग करके टेक्स्ट और इमेज वॉटरमार्क
  के साथ PDF फ़ाइलों को वॉटरमार्क करना सीखें – PDF दस्तावेज़ सुरक्षा के लिए एक पूर्ण
  गाइड।
keywords:
- GroupDocs Watermark Java
- PDF watermarking
- Java document security
- image watermark Java
title: GroupDocs.Watermark for Java का उपयोग करके PDF में वॉटरमार्क कैसे लगाएँ
type: docs
url: /hi/java/pdf-document-watermarking/add-watermarks-to-pdfs-groupdocs-watermark-java/
weight: 1
---

# GroupDocs.Watermark for Java का उपयोग करके PDF में वॉटर या ब्रांड एसेट्स की सुरक्षा करनी होती है। वॉटरमार्क जोड़ने—चाहे टेक्स्ट हो या इमेज—आपको **PDF दस्तावेज़ सुरक्षा** लागू करने में मदद करता है और अनधिकृत वितरण को बहुत कठिन बनाता है। इस‑चरण सीखेंगे कि **GroupDocs.Watermark for Java** का उपयोग करके PDF दस्तावेज़ों में टेक्स्ट और इमेज दोनों वॉटरमार्क कैसे जोड़ें।

## त्वरित उत्तर

- **Java में PDF में वॉटरमार्क जोड़ने वाली लाइब्रेरी कौन सी है?** GroupDocs.Watermark for Java.  
- **क्या मैं टेक्स्ट और इमेज जोड़ें और इसे क्यों उपयोग करें?

PDF में वॉटरमार्किंग एक दृश्यमान या अदृश्य मार्कर ए और कॉर्पोरेट नीतियों का पालन करने का एक हल्का लेकिन प्रभावी तरीका है।

## पूर्वापेक्षाएँ

शुरू करने से पहले, सुनिश्चित करें कि आपके पास हैं:

1. **Java Development Kit (JDK) 8+** आपके मशीन पर इंस्टॉल हो।  
2. **GroupDocs.Watermark for Java** (नवीनतम संस्करण)।  
3. **Maven** (या मैन्युअली JAR जोड़ने की क्षमता)।

### पर्यावरण सेटअप

#### Maven कॉन्फ़िगरेशन

Add the GroupDocs repository and the watermark dependency to your `pom.xml`:

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

#### डायरेक्ट डाउनलोड

यदि आप Maven का उपयोग नहीं करना चाहते हैं, तो आप JAR को सीधे [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/) से डाउनलोड कर सकते हैं।

### लाइसेंस प्राप्ति

फ़ेंस प्राप्त करने के लिए, [GroupDocs Licensing](https://purchase.groupdocs.com/.Watermark for Java सेटअप

सभी वॉटरमार्क ऑपरेशन्स को चलाने वाली कोर क्लास को इम्पोर्ट करें:

```java
import com.groupdocs.watermark.Watermarker;
```

यह इम्पोर्ट आपको `Watermarker` क्लास तक पहुँच देता है, जो किसी भी समर्थित दस्तावेज़ प्रकार में वॉटरमार्क जोड़ने का एंट्री पॉइंट्वयन

नीचे हम प्रक्रिया को तार्किक भागों में विभाजित करते हैं: टेक्स्ट वॉटरमार्क बनाना, इमेज वॉटरमार्क बनाना, और अंत में PDF के अंदर इमेज पर उन्हें लागू करना।

### 1. टेक्स्ट वॉटरमार्क को इनिशियलाइज़ करें

**टेक्स्ट वॉटरमार्क क्यों?** यह हल्का, सर्चेबल है, और कॉपीराइट नोटिस या गोपनीयता स्टेटमेंट जोड़ने के लिए उत्तम है।

#### 1.1 TextWatermark इंस्टेंस बनाएं
```java
// Create a text watermark with custom settings
TextWatermark textWatermark = new TextWatermark("Protected image", new Font("Arial", 8));
```

#### 1.2 अलाइनमेंट सेट करें
```java
// Align watermark to the center of images
textWatermark.setHorizontalAlignment(HorizontalAlignment.Center);
textWatermark.setVerticalAlignment(VerticalAlignment.Center);
```

#### 1.3 वॉटरमार्क को रोटेट करें
```java
// Rotate the watermark by 45 degrees
textWatermark.setRotateAngle(45);
```

#### 1.4 साइजिंग कॉन्फ़िगर करें
```java
// Scale watermark based on parent image size
textWatermark.setSizingType(SizingType.ScaleToParentDimensions);
textWatermark.setScaleFactor(1);
```

### 2. इमेज वॉटरमार्क को इनिशियलाइज़ करें

**इमेज वॉटरमार्क कब उपयोग करें?** यह लोगो के साथ ब्रांडिंग या जटिल विज़ुअल पैटर्न जोड़ने के लिए आदर्श है।

#### 2.1 इमेज फ़ाइल लोड करें
```java
// Load an image file as a watermark
ImageWatermark imageWatermark = new ImageWatermark("YOUR_DOCUMENT_DIRECTORY\\ProtectJpg");
```

#### 2.2 अलाइनमेंट सेट करें
```java
// Align image watermark to the center
imageWatermark.setHorizontalAlignment(HorizontalAlignment.Center);
imageWatermark.setVerticalAlignment(VerticalAlignment.Center);
```

#### 2.3 इमेज वॉटरमार्क को रोटेट करें
```java
// Rotate the image watermark by -45 degrees
textWatermark.setRotateAngle(-45);
```

#### 2.4 साइजिंग कॉन्फ़िगर करें
```java
// Scale the image watermark relative to its parent dimensions
imageWatermark.setSizingType(SizingType.ScaleToParentDimensions);
imageWatermark.setScaleFactor(1);
```

### 3. PDF के अंदर इमेज पर वॉटरमार्क जोड़ें

अब हम सब कुछ एक साथ करेंगे: PDF खोलें, हर इमेज को खोजें, और आकार के आधार पर टेक्स्ट या इमेज वॉटरमार्क लागू करें।

#### 3.1 PDF दस्तावेज़ खोलें
```java
// Open the PDF containing images for watermarking
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY\\document.pdf");
```

#### 3.2 सभी इमेज प्राप्त करें
```java
// Get a collection of all images within the PDF
WatermarkableImageCollection images = watermarker.getImages();
```

#### 3.3 शर्तानुसार वॉटरमार्क लागू करें
```java
for (int i = 0; i < images.getCount(); i++) {
    // Check if the image exceeds specific size criteria
    if (images.get_Item(i).getWidth() > 100 && images.get_Item(i).getHeight() > 100) {
        // Alternate between text and image watermarks
        if (i % 2 == 0) {
            images.get_Item(i).add(textWatermark);
        } else {
            images.get_Item(i).add(imageWatermark);
        }
    }
}
```

#### 3.4 इमेज रिसोर्सेज़ रिलीज़ करें
```java
// Close the image watermark instance after use
imageWatermark.close();
```

#### 3.5 संशोधित PDF सहेजें
```java
// Save the PDF with added watermarks in a new file
watermarker.save("YOUR_OUTPUT_DIRECTORY\\document.pdf");
```

#### 3.6 क्लीन अप
```java
// Close the main watermarker to release document resources
watermarker.close();
```

## PDF वॉटरमार्किंग के व्यावहारिक उपयोग

| उपयोग केस | वॉटरमार्किंग कैसे मदद करता है |
|----------|-------------------------------|
| **डॉक्यूमेंट सुरक्षा** | गोपनीय फ़ाइलों को मार्क करता है, लीक को रोकता है। |
| **ब्रांड सुरक्षा** | मार्केटिंग PDF पर लोगो एम्बेड करता है, ब्रांड पहचान को मजबूत करता है। |
| **कॉपीराइट दावा** | लेखक का नाम या © प्रतीक जोड़ता है ताकि स्वामित्व स्थापित हो। |
| **वर्ज़न कंट्रोल** | पेज पर सीधे वर्ज़न नंबर या तारीख दिखाता है। |

## सामान्य गड़बड़ियों और टिप्स

- **Path separators:** Windows पर डबल बैकस्लैश (`\\`) या Linux/macOS पर फ करें ताकि `FileNotFoundException` न आए।  
- **Large PDFs:** इमेज को बैच में प्रोसेस करें या JVM हीप साइज (`-Xmx2g`) बढ़ाएँ ताकि OutOfMemory त्रुटियाँ न हों।  
- **License limits:** ट्रायल वर्ज़न प्रोसेस की जाने वाली पेजों की संख्या सीमित कर सकता है; अनलिमिटेड उपयोग के लिए अपग्रेड करें।ाइज़ रोटेट करते हैं।  

## अक्सर पूछे जाने वाले प्रश्न

**प्र Power करता है।

**प्रश्न: वॉटर उपयोग करें (मान 0.0 से 1.0 के बीच)।

**प्रश्न: क्या केवल पहले पेज पर वॉटरमार्क जोड़ना संभव है?**  
**उत्तर:** `watermarker.getPages()` से पेज कलेक्शन प्राप्त करें और इच्छित पेज इंडेक्स पर वॉटरमार्क लागू करें।

**प्रश्न: यदि मुझे क्लाउड बकेट में संग्रहीत PDF पर वॉटरमार्क लगाना हो तो क्या करें?**  
**उत्तर:** PDF को `InputStream` में लोड करें और `Watermarker` कंस्ट्रक्टर को पास करें; प्रोसेसिंग के बाद, आउटपुट स्ट्रीम को फिर से क्लाउड में लिखें।

## निष्कर्ष

अब आपके पास GroupDocs.W फ़ाइलों के लिए एक पूर्ण, प्रोडक्शन‑रेडी विधि है। टेक्स्ट और इमेज वॉटरमार्क को मिलाकर, आप मजबूत **PDF दस्तावेज़ सुरक्षा** प्राप्त कर सकते हैं जो ब्रांडिंग और अनुपालन दोनों आवश्यकताओं को पूरा करती है। लाइब्रेरी की अन्य सुविधाओं—जैसे वॉटरमार्क हटाना या बैच प्रोसेसिंग—की जाँच करें ताकि अपने दस्तावेज़ वर्कफ़्लो को और विस्तारित कर सकें।

---

**अंतिम अपडेट:** 2026-01-23  
**परीक्षित संस्करण:** GroupDocs.Water