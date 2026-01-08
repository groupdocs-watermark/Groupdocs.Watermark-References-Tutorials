---
date: '2025-12-19'
description: GroupDocs.Watermark for Java के साथ आरेखों में टेक्स्ट वॉटरमार्क कैसे
  जोड़ें, सीखें। अपने दृश्य सामग्री की प्रभावी रूप से सुरक्षा करें और दस्तावेज़ की
  अखंडता सुनिश्चित करें।
keywords:
- text watermarks
- GroupDocs Watermark for Java
- diagram document watermarking
title: GroupDocs.Watermark for Java का उपयोग करके डायग्राम में टेक्स्ट वॉटरमार्क जोड़ें
  – एक व्यापक गाइड
type: docs
url: /hi/java/diagram-document-watermarking/groupdocs-watermark-java-add-text-watermarks-diagrams/
weight: 1
---

# डायग्राम में टेक्स्ट वॉटरमार्क जोड़ें GroupDocs.Watermark for Java का उपयोग करके: एक व्यापक गाइड

## परिचय
डायग्राम दस्तावेज़ों को अनधिकृत उपयोग से बचाना अत्यंत महत्वपूर्ण है, और **टेक्स्ट वॉटरमार्क जोड़ना** एक सरल yet प्रभावी समाधान प्रदान करता है। इस ट्यूटोरियल में आप सीखेंगे कि कैसे डायग्राम फ़ाइलें लोड करें, एक कस्टमाइज़ेबल टेक्स्ट वॉटरमार्क बनाएं, और इसे **GroupDocs.Watermark for Java** का उपयोग करके बैकग्राउंड पेज या विशिष्ट शैप्स पर लागू करें। गाइड के अंत तक आप अपने विज़ुअल एसेट्स को सुरक्षित रख पाएँगे जबकि मूल रूप और फ़ील को बरकरार रखेंगे।

### त्वरित उत्तर
- **What does “add text watermark” mean?**  
  इसका मतलब है दस्तावेज़ में एक अर्ध‑पारदर्शी टेक्स्ट ओवरले एम्बेड करना ताकि स्वामित्व या गोपनीयता दर्शाई जा सके।  
- **Which library supports diagram watermarking?**  
  GroupDocs.Watermark for Java मूल रूप से डायग्राम फ़ॉर्मेट (जैसे Visio, VSDX) के लिए समर्थन प्रदान करता है।  
- **Do I need a license?**  
  उत्पादन उपयोग के लिए एक टेम्पररी या पूर्ण लाइसेंस आवश्यक है; मूल्यांकन के लिए एक फ्री ट्रायल उपलब्ध है।  
- **Can I place the watermark on background pages?**  
  हाँ – बैकग्राउंड पेज वॉटरमार्क के लिए `DiagramWatermarkPlacementType.SeparateBackgrounds` विकल्प का उपयोग करें।  
- **Is the code compatible with Java 8+?**  
  बिल्कुल – लाइब्रेरी JDK 8 और उसके बाद के संस्करणों के साथ काम करती है।

## डायग्राम के लिए टेक्स्ट वॉटरमार्क क्या है?
एक टेक्स्ट वॉटरमार्क पढ़ने योग्य टेक्स्ट (अक्सर अर्ध‑पारदर्शी) का टुकड़ा है जो डायग्राम तत्वों के ऊपर या पीछे रेंडर किया जाता है। इसे ब्रांडिंग, कॉपीराइट सुरक्षा, या गोपनीय ड्राफ्ट को चिह्नित करने के लिए उपयोग किया जा सकता है।

## GroupDocs.Watermark for Java का उपयोग क्यों करें?
- **Broad format support** – Visio, VSDX और कई अन्य डायग्राम प्रकारों के साथ काम करता है।  
- **Fine‑grained placement** – फ़ोरग्राउंड, बैकग्राउंड, या विशिष्ट शैप वॉटरमार्किंग चुनें।  
- **Simple API** – कुछ ही लाइनों के Java कोड से वॉटरमार्क बनाएं और लागू करें।  

## पूर्वापेक्षाएँ
- **GroupDocs.Watermark for Java** (v24.11 या बाद का)  
- **Java Development Kit (JDK)** 8 या उससे ऊपर  
- Maven (या मैन्युअल JAR इन्क्लूज़न)  

## GroupDocs.Watermark for Java सेटअप करना
### Maven सेटअप
अपने `pom.xml` फ़ाइल में निम्न कॉन्फ़िगरेशन जोड़ें:

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

### सीधा डाउनलोड
नवीनतम संस्करण डाउनलोड करें यहाँ से: [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/)।

### लाइसेंस प्राप्ति
- **Free Trial** – बिना लाइसेंस कुंजी के सभी फीचर्स का मूल्यांकन करें।  
- **Temporary License** – विकास के दौरान पूर्ण कार्यक्षमता अनलॉक करने के लिए उपयोग करें।  
- **Purchase** – व्यावसायिक प्रोजेक्ट्स के लिए प्रोडक्शन लाइसेंस प्राप्त करें।  

### बुनियादी इनिशियलाइज़ेशन और सेटअप
सुनिश्चित करें कि आपके Java क्लास में निम्न इम्पोर्ट्स मौजूद हैं:

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.DiagramLoadOptions;
```

## चरण‑दर‑चरण कार्यान्वयन

### चरण 1: डायग्राम दस्तावेज़ लोड करें
पहले, लाइब्रेरी को अपने डायग्राम फ़ाइल की ओर इंगित करें और लोड विकल्पों को इनिशियलाइज़ करें।

```java
String inputPath = "YOUR_DOCUMENT_DIRECTORY";
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker(inputPath, loadOptions);
```

*Explanation*: `DiagramLoadOptions` आपको वॉटरमार्क लगाने से पहले डायग्राम कैसे पार्स किया जाता है, इसे नियंत्रित करने देता है।

### चरण 2: टेक्स्ट वॉटरमार्क बनाएं
अब वॉटरमार्क टेक्स्ट बनाएं और उसकी दृश्य शैली निर्धारित करें।

```java
TextWatermark textWatermark = new TextWatermark("Test watermark 1", new Font("Calibri", 19));
```

*Explanation*: यह `TextWatermark` को वाक्यांश **“Test watermark 1”** के साथ Calibri फ़ॉन्ट, आकार 19 पर बनाता है।

### चरण 3: प्लेसमेंट कॉन्फ़िगर करें – बैकग्राउंड पेज वॉटरमार्क
वॉटरमार्क कहाँ दिखना चाहिए, चुनें। **बैकग्राउंड पेज वॉटरमार्क** के लिए निम्न विकल्प उपयोग करें:

```java
DiagramShapeWatermarkOptions options = new DiagramShapeWatermarkOptions();
options.setPlacementType(DiagramWatermarkPlacementType.SeparateBackgrounds);
```

*Explanation*: `DiagramShapeWatermarkOptions` सटीक स्थान को नियंत्रित करता है। प्लेसमेंट टाइप को `SeparateBackgrounds` सेट करने से डायग्राम के प्रत्येक बैकग्राउंड पेज पर वॉटरमार्क जोड़ता है।

### चरण 4: वॉटरमार्क लागू करें और सहेजें
अंत में, वॉटरमार्क को दस्तावेज़ में जोड़ें, परिणाम सहेजें, और संसाधनों को रिलीज़ करें।

```java
watermarker.add(textWatermark, options);
String outputPath = "YOUR_OUTPUT_DIRECTORY";
watermarker.save(outputPath);
watermarker.close();
```

*Explanation*: `add` मेथड कॉन्फ़िगर किए गए `textWatermark` को प्लेसमेंट विकल्पों के साथ लागू करता है, फिर संशोधित डायग्राम `outputPath` पर सहेजा जाता है।

## व्यावहारिक उपयोग
- **Intellectual Property Protection** – प्रतिस्पर्धियों को स्वामित्व वाले डायग्राम पुनः उपयोग करने से रोकें।  
- **Brand Reinforcement** – सभी एक्सपोर्टेड डायग्राम पर कंपनी का नाम या लोगो टेक्स्ट वॉटरमार्क के रूप में एम्बेड करें।  
- **Legal Documentation** – इंजीनियरिंग स्कीमैटिक्स के गोपनीय ड्राफ्ट को चिह्नित करें।  
- **Academic Submissions** – प्लेज़रिज़्म ट्रैकिंग के लिए डायग्राम में छात्र आईडी या कोर्स कोड जोड़ें।  

## प्रदर्शन संबंधी विचार
- **Memory Management** – `Watermarker` इंस्टेंस (`watermarker.close()`) को बंद करके नेटिव रिसोर्सेज़ मुक्त करें, विशेषकर बड़े फ़ाइलों को प्रोसेस करते समय।  
- **Batch Processing** – डायग्राम पाथ्स के संग्रह पर लूप चलाएँ और जहाँ संभव हो एक ही `Watermarker` इंस्टेंस को पुनः उपयोग करें ताकि ओवरहेड कम हो।  

## सामान्य समस्याएँ और समाधान
| Issue | Solution |
|-------|----------|
| **OutOfMemoryError on large diagrams** | JVM हीप साइज बढ़ाएँ (`-Xmx2g`) और फ़ाइलों को एक‑एक करके प्रोसेस करें। |
| **Watermark not visible** | सुनिश्चित करें कि वॉटरमार्क का रंग पर्याप्त कंट्रास्ट रखता है; अपारदर्शिता `textWatermark.setOpacity(0.5)` से सेट करें। |
| **Unsupported diagram format** | जांचें कि फ़ॉर्मेट GroupDocs.Watermark द्वारा समर्थित फ़ॉर्मेट्स की डॉक्यूमेंटेशन में सूचीबद्ध है या नहीं। |

## अक्सर पूछे जाने वाले प्रश्न

**Q: वॉटरमार्क के लिए सबसे अच्छा फ़ॉन्ट साइज क्या है?**  
A: इष्टतम साइज डायग्राम के आयामों पर निर्भर करता है; अधिकांश मामलों में 12‑20 pt अच्छा काम करता है।

**Q: क्या मैं वॉटरमार्क के रंग कस्टमाइज़ कर सकता हूँ?**  
A: हाँ, `textWatermark.setColor(Color.GRAY)` (या कोई भी `java.awt.Color`) का उपयोग करें।

**Q: बड़े बैच में दस्तावेज़ों को कैसे हैंडल करूँ?**  
A: लाइब्रेरी के बैच API का उपयोग करें या एक लूप लिखें जो `Watermarker` ऑब्जेक्ट्स को पुनः उपयोग करके ओवरहेड कम करे।

**Q: GroupDocs.Watermark में कोई सीमाएँ हैं क्या?**  
A: लाइब्रेरी अधिकांश सामान्य डायग्राम फ़ॉर्मेट्स को सपोर्ट करती है, लेकिन कुछ प्रोपायटरी एक्सटेंशन पूरी तरह रेंडर नहीं हो सकते। विवरण के लिए [documentation](https://docs.groupdocs.com/watermark/java/) देखें।

**Q: यदि कोई समस्या आती है तो सपोर्ट कैसे प्राप्त करूँ?**  
A: समुदाय सहायता के लिए [GroupDocs Forum](https://forum.groupdocs.com/c/watermark/10) देखें या सीधे GroupDocs सपोर्ट से संपर्क करें।

## अतिरिक्त संसाधन
- **दस्तावेज़ीकरण**: [GroupDocs.Watermark Documentation](https://docs.groupdocs.com/watermark/java/)  
- **API रेफ़रेंस**: [Java API Reference](https://reference.groupdocs.com/watermark/java)  
- **डाउनलोड**: [Get GroupDocs.Watermark](https://releases.groupdocs.com/watermark/java/)  
- **GitHub रिपॉज़िटरी**: [GroupDocs Watermark Java](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)  
- **Free Support Forum**: [GroupDocs Forum](https://forum.groupdocs.com/c/watermark/10)  
- **Temporary License**: [Acquire Temporary License](https://purchase.groupdocs.com/temporary-license/)  

**अंतिम अपडेट:** 2025-12-19  
**परीक्षण किया गया:** GroupDocs.Watermark 24.11 for Java  
**लेखक:** GroupDocs