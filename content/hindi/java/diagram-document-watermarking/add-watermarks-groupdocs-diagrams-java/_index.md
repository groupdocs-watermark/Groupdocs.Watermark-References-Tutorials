---
date: '2026-02-16'
description: GroupDocs.Watermark for Java का उपयोग करके विशिष्ट डायग्राम पेज पर वॉटरमार्क
  कैसे लगाएँ, जिसमें इमेज वॉटरमार्क जोड़ना और अपनी फ़ाइलों को सुरक्षित करना शामिल
  है।
keywords:
- GroupDocs Watermark Java
- adding watermarks diagrams
- Java diagram document watermarking
title: GroupDocs.Watermark for Java का उपयोग करके विशिष्ट डायग्राम पेज पर वॉटरमार्क।
type: docs
url: /hi/java/diagram-document-watermarking/add-watermarks-groupdocs-diagrams-java/
weight: 1
---

# GroupDocs.Watermark for Java का उपयोग करके विशिष्ट डायग्राम पेज पर वॉटरमार्क

अपने डायग्राम की सुरक्षा अत्यंत महत्वपूर्ण है, विशेष रूप से जब आपको बौद्धिक संपदा की सुरक्षा या ब्रांड एट्रिब्यूशन के लिए **watermark specific diagram page** की आवश्यकता होती है। इस ट्यूटोरियल में आप चरण‑बद्ध तरीके से सीखेंगे कि कैसे **GroupDocs.Watermark for Java** का उपयोग करके एक डायग्राम फ़ाइल के चयनित पेजों पर टेक्स्ट और इमेज दोनों वॉटरमार्क जोड़ें। अंत तक, आप अपने डायग्राम को सुरक्षित करने और प्रत्येक वॉटरमार्क के प्रकट होने के स्थान को नियंत्रित करने के लिए तैयार होंगे।

## त्वरित उत्तर
- **मुख्य उद्देश्य क्या है?** चयनित डायग्राम पेजों पर वॉटरमार्क जोड़ना।  
- **कौन सी लाइब्रेरी आवश्यक है?** GroupDocs.Watermark for Java (Maven या सीधे डाउनलोड)।  
- **क्या मैं जावा में इमेज वॉटरमार्क जोड़ सकता हूँ?** हाँ – `ImageWatermark` को पेज‑स्पेसिफिक विकल्पों के साथ उपयोग करें।  
- **क्या मुझे लाइसेंस चाहिए?** परीक्षण के लिए एक टेम्पररी ट्रायल लाइसेंस काम करता है; प्रोडक्शन के लिए पूर्ण लाइसेंस आवश्यक है।  
- **कोड की कितनी लाइन्स चाहिए?** पूर्ण टेक्स्ट + इमेज वॉटरमार्क वर्कफ़्लो के लिए 30 लाइनों से कम।

## “watermark specific diagram page” क्या है?
एक **watermark specific diagram page** का अर्थ है एक दृश्य मार्कर—टेक्स्ट या इमेज—को केवल उन पेजों पर लागू करना जो आप एक मल्टी‑पेज डायग्राम (जैसे Visio . vsdx) के भीतर चुनते हैं। यह आपको ब्रांडिंग, गोपनीयता नोटिस या कॉपीराइट स्टेटमेंट्स पर सूक्ष्म नियंत्रण देता है बिना पूरे दस्तावेज़ को प्रभावित किए।

## GroupDocs.Watermark for Java का उपयोग क्यों करें?
- **Full page control** – आपको आवश्यक किसी भी पेज इंडेक्स को टार्गेट करने की सुविधा देता है।  
- **Rich styling** – फ़ॉन्ट, रंग, अपारदर्शिता, घूर्णन, और इमेज स्केलिंग सभी कॉन्फ़िगर करने योग्य हैं।  
- **Performance‑optimized** – बड़े डायग्राम को कुशलतापूर्वक प्रोसेस करता है और Maven बिल्ड्स के साथ सहजता से इंटीग्रेट होता है।  
- **Cross‑format support** – Visio, SVG और कई अन्य डायग्राम फ़ॉर्मैट्स के साथ काम करता है।

## पूर्वापेक्षाएँ
- **GroupDocs.Watermark for Java** लाइब्रेरी संस्करण 24.11 या बाद का।  
- Maven या सीधे JAR डाउनलोड।  
- बेसिक Java डेवलपमेंट सेटअप (JDK 8+ की सिफ़ारिश)।

## GroupDocs.Watermark for Java सेटअप करना
### Maven groupdocs watermark का उपयोग
Include GroupDocs.Watermark in your project via Maven by adding this to your `pom.xml`:

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

### सीधे डाउनलोड
Alternatively, download the latest version directly from [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/)।

#### लाइसेंस प्राप्ति
Start with a free trial by downloading a temporary license. Purchase options are available on their official site if you choose to continue using GroupDocs.Watermark.

### बेसिक इनिशियलाइज़ेशन और सेटअप
Once installed, initialize the `Watermarker` class for watermarking operations:

```java
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/diagram.vsdx", loadOptions);
```

## इम्प्लीमेंटेशन गाइड
### विशिष्ट पेज पर टेक्स्ट वॉटरमार्क जोड़ना
To add a text watermark, create and configure it before specifying the target page.

#### टेक्स्ट वॉटरमार्क बनाएं
Define your text watermark with customizable content, font style, size, etc.:

```java
TextWatermark textWatermark = new TextWatermark("Confidential", new Font("Arial", 18));
textWatermark.setForegroundColor(Color.BLUE);
textWatermark.setOpacity(0.5f);
```

#### वॉटरमार्क के लिए पेज इंडेक्स सेट करें
Determine which diagram page will display the watermark using `DiagramPageWatermarkOptions`:

```java
DiagramPageWatermarkOptions textWatermarkOptions = new DiagramPageWatermarkOptions();
textWatermarkOptions.setPageIndex(0); // First page (index 0)
```

#### टेक्स्ट वॉटरमार्क जोड़ें
Add your configured watermark to the diagram:

```java
watermarker.add(textWatermark, textWatermarkOptions);
```

### विशिष्ट पेज पर इमेज वॉटरमार्क जोड़ना
Follow similar steps for image watermarks using an `ImageWatermark` object.

#### इमेज वॉटरमार्क बनाएं
Create an instance of `ImageWatermark` with the desired watermark image path:

```java
ImageWatermark imageWatermark = new ImageWatermark("YOUR_DOCUMENT_DIRECTORY/logo.png");
imageWatermark.setOpacity(0.7f);
```

#### वॉटरमार्क के लिए पेज इंडेक्स सेट करें
Specify which page should display the image watermark:

```java
DiagramPageWatermarkOptions imageWatermarkOptions = new DiagramPageWatermarkOptions();
imageWatermarkOptions.setPageIndex(1); // Second page (index 1)
```

#### इमेज वॉटरमार्क जोड़ें
Add the image to your specified diagram page:

```java
watermarker.add(imageWatermark, imageWatermarkOptions);
```

### संसाधनों को सेव और क्लोज करें
Remember to save changes and close resources to prevent leaks:

```java
watermarker.save("YOUR_OUTPUT_DIRECTORY/output_diagram.vsdx");
watermarker.close();
textWatermark.close();
imageWatermark.close();
```

## व्यावहारिक अनुप्रयोग
- **Document Security** – संवेदनशील स्कीमैटिक्स वाले पेजों पर ही गोपनीय वॉटरमार्क लागू करें।  
- **Branding** – कवर पेज पर कंपनी लोगो रखें और अंदरूनी पेजों को साफ़ रखें।  
- **Copyright Protection** – तकनीकी डायग्राम पैक के अंतिम पेज पर कॉपीराइट नोटिस जोड़ें।

## प्रदर्शन संबंधी विचार
- **Memory Management** – सेव करने के बाद प्रत्येक वॉटरमार्क ऑब्जेक्ट को बंद करें ताकि नेटिव रिसोर्सेज़ मुक्त हों।  
- **Image Optimization** – प्रोसेसिंग तेज़ रखने के लिए उपयुक्त आकार की PNG/JPEG फ़ाइलें उपयोग करें।  
- **Batch Processing** – कई डायग्राम संभालते समय जहाँ संभव हो एक ही `Watermarker` इंस्टेंस का पुनः उपयोग करें।

## सामान्य समस्याएँ और समाधान
| लक्षण | संभावित कारण | समाधान |
|---------|--------------|-----|
| वॉटरमार्क दिखाई नहीं दे रहा | गलत `pageIndex` (शून्य‑आधारित) | सुनिश्चित करें कि इंडेक्स इच्छित पेज से मेल खाता है। |
| इमेज विकृत दिख रही है | उच्च‑रिज़ॉल्यूशन स्रोत इमेज | `ImageWatermark` बनाने से पहले इमेज का आकार बदलें। |
| प्रोडक्शन में लाइसेंस त्रुटि | ट्रायल लाइसेंस की समाप्ति के बाद उपयोग करना | `License.setLicense("path/to/license.json")` के माध्यम से पूर्ण लाइसेंस फ़ाइल लागू करें। |

## अक्सर पूछे जाने वाले प्रश्न

**Q1: क्या मैं एक ही डायग्राम पेज पर कई वॉटरमार्क जोड़ सकता हूँ?**  
A1: हाँ, बस `watermarker.add()` को विभिन्न वॉटरमार्क ऑब्जेक्ट्स के साथ उसी पेज इंडेक्स के लिए कॉल करें।

**Q2: GroupDocs.Watermark for Java कौन से फ़ाइल फ़ॉर्मैट्स को सपोर्ट करता है?**  
A2: यह विभिन्न डायग्राम और इमेज फ़ॉर्मैट्स को सपोर्ट करता है। पूरी सूची के लिए [API documentation](https://reference.groupdocs.com/watermark/java) देखें।

**Q3: ट्रायल संस्करण का उपयोग करते समय लाइसेंसिंग समस्याओं को कैसे संभालें?**  
A3: GroupDocs से एक मुफ्त टेम्पररी लाइसेंस लेकर शुरू करें। प्रोडक्शन के लिए सभी फीचर्स अनलॉक करने हेतु पूर्ण लाइसेंस खरीदें।

**Q4: यदि वॉटरमार्क अपेक्षित रूप से नहीं दिखते तो कुछ सामान्य ट्रबलशूटिंग टिप्स क्या हैं?**  
A4: सुनिश्चित करें कि पेज इंडेक्स सही है और इमेज रिसोर्सेज़ के फ़ाइल पाथ को दोबारा जांचें। साथ ही यह भी पुष्टि करें कि वॉटरमार्क की अपारदर्शिता 0 पर सेट नहीं है।

**Q5: मैं वॉटरमार्क की उपस्थिति को और कैसे कस्टमाइज़ कर सकता हूँ?**  
A5: `TextWatermark` या `ImageWatermark` पर उपलब्ध मेथड्स का उपयोग करके फ़ॉन्ट साइज, अपारदर्शिता, घूर्णन और पोजिशनिंग को समायोजित करें।

## संसाधन
- [GroupDocs.Watermark दस्तावेज़ीकरण](https://docs.groupdocs.com/watermark/java/)
- [API रेफ़रेंस गाइड](https://reference.groupdocs.com/watermark/java)
- [लाइब्रेरी डाउनलोड करें](https://releases.groupdocs.com/watermark/java/)
- [GitHub रिपॉज़िटरी](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)
- [मुफ़्त सपोर्ट फ़ोरम](https://forum.groupdocs.com/c/watermark/10)
- [टेम्पररी लाइसेंस जानकारी](https://purchase.groupdocs.com/temporary-license/)

इन संसाधनों का अन्वेषण करें ताकि GroupDocs.Watermark for Java के साथ आपकी समझ और क्षमताएँ गहरी हों। Happy watermarking!

---

**अंतिम अपडेट:** 2026-02-16  
**परीक्षित संस्करण:** GroupDocs.Watermark 24.11 for Java  
**लेखक:** GroupDocs