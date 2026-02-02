---
date: '2025-12-17'
description: GroupDocs.Watermark for Java का उपयोग करके विशिष्ट डायग्राम पेज पर वॉटरमार्क
  कैसे लगाएँ, डायग्राम में वॉटरमार्क जोड़ें और जावा में इमेज वॉटरमार्क जोड़ें। अपने
  आईपी की सुरक्षा के लिए चरण-दर-चरण गाइड।
keywords:
- GroupDocs Watermark Java
- adding watermarks diagrams
- Java diagram document watermarking
title: GroupDocs.Watermark for Java का उपयोग करके विशिष्ट आरेख पृष्ठ पर वॉटरमार्क
  लगाएँ
type: docs
url: /hi/java/diagram-document-watermarking/add-watermarks-groupdocs-diagrams-java/
weight: 1
---

# GroupDocs.Watermark for Java का उपयोग करके विशिष्ट डायग्राम पेज पर वाटरमार्क लगाना

अपने डायग्राम की सुरक्षा अत्यंत महत्वपूर्ण है, विशेषकर जब बात बौद्धिक संपदा की रक्षा या उचित श्रेय देने की हो। इस ट्यूटोरियल में आप **GroupDocs.Watermark for Java** के साथ **विशिष्ट डायग्राम पेज पर वाटरमार्क कैसे लगाएँ** सीखेंगे, चाहे आपको **डायग्राम में टेक्स्ट वाटरमार्क जोड़ना** हो या **इमेज वाटरमार्क जावा‑स्टाइल लोगो** जोड़ना हो। इस गाइड के अंत तक आप सक्षम होंगे:

- चुने हुए डायग्राम पेजों पर टेक्स्ट वाटरमार्क को सहजता से जोड़ना।  
- डायग्राम के निर्दिष्ट सेक्शन में इमेज वाटरमार्क सम्मिलित करना।  
- GroupDocs.Watermark का उपयोग करते समय प्रदर्शन को बढ़ाना।

आइए कोड में डुबकी लगाने से पहले सुनिश्चित करें कि पर्यावरण तैयार है।

## क्विक जवाब
- **“वॉटरमार्क स्पेसिफिक डायग्राम पेज” का क्या अर्थ है?** यह केवल चयनित पेजों पर वाटरमार्क लागू करने को दर्शाता है, जबकि अन्य पेज अपरिवर्तित रहते हैं।  
- **कौन सा लाइब्रेरी संस्करण आवश्यक है?** GroupDocs.Watermark 24.11 या नया।  
- **क्या मैं एक ही पेज पर टेक्स्ट और इमेज दोनों वाटरमार्क उपयोग कर सकता हूँ?** हाँ – प्रत्येक वाटरमार्क प्रकार के लिए `watermarker.add()` को कॉल करें।  
- **क्या विकास के लिए लाइसेंस चाहिए?** परीक्षण के लिए एक अस्थायी ट्रायल लाइसेंस काम करता है; उत्पादन के लिए पूर्ण लाइसेंस आवश्यक है।  
- **क्या Maven ही लाइब्रेरी जोड़ने का एकमात्र तरीका है?** नहीं – आप JAR को सीधे डाउनलोड भी कर सकते हैं (नीचे “Direct Download” देखें)।

## “वॉटरमार्क स्पेसिफिक डायग्राम पेज” क्या है?
एक **watermark specific diagram page** ऑपरेशन डायग्राम दस्तावेज़ (जैसे Visio *.vsdx*) के एकल पेज (या पेजों के सेट) को लक्षित करता है और उस पर टेक्स्ट या इमेज लेयर ओवरले करता है। यह गोपनीय ड्राफ्ट, ब्रांडिंग, या कॉपीराइट नोटिस को पूरी फ़ाइल को बदले बिना लागू करने में उपयोगी है।

## Java के लिए GroupDocs.Watermark का इस्तेमाल क्यों करें?
GroupDocs.Watermark एक हाई‑लेवल API प्रदान करता है जो डायग्राम फॉर्मेट की जटिलताओं को एब्स्ट्रैक्ट करता है, बैच प्रोसेसिंग को सपोर्ट करता है, और अपारदर्शिता, पोजिशनिंग, तथा पेज चयन पर फाइन‑ग्रेन कंट्रोल देता है। यह Maven और मानक Java बिल्ड टूल्स के साथ भी सहजता से इंटीग्रेट होता है।

## ज़रूरी शर्तें
- **GroupDocs.Watermark for Java** लाइब्रेरी संस्करण 24.11 या बाद का इंस्टॉल किया हुआ।  
- Maven (या JAR को मैन्युअली जोड़ने की क्षमता) वाला विकास पर्यावरण।  
- बेसिक Java ज्ञान और फ़ाइल‑सिस्टम एक्सेस।

## Java के लिए GroupDocs.Watermark सेट अप करना

### Maven का इस्तेमाल करना
अपने `pom.xml` में नीचे दिया गया कोड जोड़कर GroupDocs.Watermark को प्रोजेक्ट में शामिल करें:

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

### डायरेक्ट डाउनलोड
वैकल्पिक रूप से, लेटेस्ट वर्शन सीधे यहाँ से डाउनलोड करें: [GroupDocs.Watermark for Java रिलीज़](https://releases.groupdocs.com/watermark/java/)।

#### लाइसेंस एक्विजिशन
एक फ्री ट्रायल के साथ शुरू करें और टेम्पररी लाइसेंस डाउनलोड करें। अगर आप GroupDocs.Watermark का लगातार इस्तेमाल करना चाहते हैं तो उनकी ऑफिशियल साइट पर खरीदने का ऑप्शन अवेलेबल हैं।

### बेसिक इनिशियलाइज़ेशन और सेटअप
लाइब्रेरी उपलब्ध होने के बाद, एक `Watermarker` इंस्टेंस बनाएं जो उस डायग्राम की ओर इशारा करता हो जिसे आप सुरक्षित करना चाहते हैं:

```java
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/diagram.vsdx", loadOptions);
```

## डायग्राम में वॉटरमार्क कैसे जोड़ें – टेक्स्ट वॉटरमार्क

### टेक्स्ट वॉटरमार्क बनाएं
वह टेक्स्ट, फ़ॉन्ट, रंग, और अपारदर्शिता निर्धारित करें जिसे आप लागू करना चाहते हैं:

```java
TextWatermark textWatermark = new TextWatermark("Confidential", new Font("Arial", 18));
textWatermark.setForegroundColor(Color.BLUE);
textWatermark.setOpacity(0.5f);
```

### वॉटरमार्क के लिए पेज इंडेक्स सेट करें
वह पेज निर्दिष्ट करें जिसे आप वाटरमार्क करना चाहते हैं। पेज इंडेक्स शून्य‑आधारित होते हैं:

```java
DiagramPageWatermarkOptions textWatermarkOptions = new DiagramPageWatermarkOptions();
textWatermarkOptions.setPageIndex(0); // First page (index 0)
```

### टेक्स्ट वॉटरमार्क जोड़ें
चुने हुए पेज पर वाटरमार्क लागू करें:

```java
watermarker.add(textWatermark, textWatermarkOptions);
```

## **इमेज वॉटरमार्क जावा कैसे जोड़ें** – इमेज वॉटरमार्क

### एक इमेज वॉटरमार्क बनाएं
वह इमेज लोड करें जिसे आप ओवरले करना चाहते हैं (जैसे कंपनी का लोगो):

```java
ImageWatermark imageWatermark = new ImageWatermark("YOUR_DOCUMENT_DIRECTORY/logo.png");
imageWatermark.setOpacity(0.7f);
```

### इमेज वॉटरमार्क के लिए पेज इंडेक्स सेट करें
वह पेज चुनें जिस पर इमेज वाटरमार्क दिखेगा:

```java
DiagramPageWatermarkOptions imageWatermarkOptions = new DiagramPageWatermarkOptions();
imageWatermarkOptions.setPageIndex(1); // Second page (index 1)
```

### इमेज वॉटरमार्क जोड़ें
चुने हुए पेज पर इमेज वाटरमार्क डालें:

```java
watermarker.add(imageWatermark, imageWatermarkOptions);
```

## रिसोर्स सेव और बंद करें
सभी इच्छित वाटरमार्क जोड़ने के बाद बदलाव सहेजें और संसाधनों को साफ़ करें:

```java
watermarker.save("YOUR_OUTPUT_DIRECTORY/output_diagram.vsdx");
watermarker.close();
textWatermark.close();
imageWatermark.close();
```

## Practical Applications
- **Document Security** – फाइलों को भेजने से पहले ड्राफ्ट डायग्राम पर “Confidential” लेबल लगाएँ।
- **Branding** – Technical Skmatic के खास पेजों पर अपना लोगो स्टैम्प लगाएँ।
- **Copyright Protection** – ज़्यादा कीमत वाले डायग्राम पर कॉपीराइट नोटिस एम्बेड करें ताकि दुरुपयोग रोका जा सके।

## Performance Considerations
- बड़ी फाइलों के लिए मेमोरी को टाइप से मैनेज करें।
- इमेज को Watermark के रूप में इस्तेमाल करने से पहले उनका आकार कम करें ताकि प्रोसेसिंग तेज़ हो।
- डिलीट करने के बाद सभी Watermark ऑब्जेक्ट्स को बंद करके Java की Garbej Collection का फ़ायदा उठाएँ।

## Common Issues and Solutions
| Symptom | Likely Cause | Fix |
|---|---|---|
| Watermark not visible | Wrong page index | Verify the zero‑based index matches the intended page. |
| Image appears detroted | High‑resolution source image | इमेज का साइज़ सही साइज़ (जैसे, 300×300px) में बदलें। |
| प्रोडक्शन में लाइसेंस में गड़बड़ी | सिर्फ़ ट्रायल लाइसेंस इस्तेमाल कर रहे हैं | `License.setLicense("path/to/license.file")` के ज़रिए पूरी लाइसेंस फ़ाइल अप्लाई करें। |
| बड़े डायग्राम पर धीमी प्रोसेसिंग | बड़ा फ़ाइल साइज़ और बंद नहीं किए गए रिसोर्स | `Watermarker` और अलग-अलग वॉटरमार्क ऑब्जेक्ट को तुरंत बंद करें। |

## अक्सर पूछे जाने वाले सवाल

**Q1: ​​क्या मैं एक ही डायग्राम पेज पर कई वॉटरमार्क जोड़ सकता हूँ?**
A: हाँ, बस एक ही `DiagramPageWatermarkOptions` के लिए अलग-अलग वॉटरमार्क ऑब्जेक्ट के साथ `watermarker.add()` को कॉल करें।

**Q2: Java के लिए GroupDocs.Watermark कौन से फ़ाइल फ़ॉर्मेट सपोर्ट करता है?**
A: यह अलग-अलग डायग्राम और इमेज फ़ॉर्मेट को सपोर्ट करता है। पूरी लिस्ट के लिए [API डॉक्यूमेंटेशन](https://reference.groupdocs.com/watermark/java) देखें।

**Q3: ट्रायल वर्शन इस्तेमाल करते समय मैं लाइसेंसिंग से जुड़ी दिक्कतों को कैसे हैंडल करूँ?**
A: GroupDocs से एक फ़्री टेम्पररी लाइसेंस लेकर शुरू करें। प्रोडक्शन के लिए, सभी फ़ीचर अनलॉक करने के लिए पूरा लाइसेंस खरीदें।

**Q4: अगर वॉटरमार्क उम्मीद के मुताबिक नहीं दिखते हैं, तो कुछ आम ट्रबलशूटिंग टिप्स क्या हैं?**
A: पक्का करें कि पेज इंडेक्स सही है, इमेज रिसोर्स के लिए फ़ाइल पाथ वेरिफ़ाई करें, और कन्फ़र्म करें कि ओपेसिटी सेटिंग्स 0 पर सेट नहीं हैं।

**Q5: मैं वॉटरमार्क के अपीयरेंस को और कैसे कस्टमाइज़ कर सकता हूँ?**
A: `TextWatermark` या `ImageWatermark` पर मेथड का इस्तेमाल करके फ़ॉन्ट साइज़, ओपेसिटी, रोटेशन और पोज़िशनिंग को एडजस्ट करें।

**Q6: क्या एक कॉल में कई पेज पर वॉटरमार्क करना मुमकिन है?**
A: हाँ – आप एक `DiagramPageWatermarkOptions` इंस्टेंस बना सकते हैं, पेज इंडेक्स की एक लिस्ट सेट कर सकते हैं, और इसे `watermarker.add()` को पास कर सकते हैं।

**Q7: क्या GroupDocs.Watermark पासवर्ड से सुरक्षित डायग्राम फ़ाइलों को सपोर्ट करता है?**
A: हाँ, आप लोड करने से पहले `DiagramLoadOptions.setPassword("yourPassword")` के ज़रिए पासवर्ड दे सकते हैं।

## रिसोर्स
- [GroupDocs.Watermark डॉक्यूमेंटेशन](https://docs.groupdocs.com/watermark/java/)
- [API रेफरेंस गाइड](https://reference.groupdocs.com/watermark/java)
- [डाउनलोड लाइब्रेरी](https://releases.groupdocs.com/watermark/java/)
- [GitHub रिपॉजिटरी](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)
- [फ्री सपोर्ट फोरम](https://forum.groupdocs.com/c/watermark/10)
- [टेम्पररी लाइसेंस जानकारी](https://purchase.groupdocs.com/temporary-license/)

इन एप्लीकेशन का एक्सप्लोरेशन करें ताकि GroupDocs.Watermark for Java के साथ आपकी समझ और क्षमताएँ और गहराई हों। हैप्पी वॉटरमार्किंग!

---

**पिछला अपडेट:** 2025-12-17
**इसके साथ टेस्ट किया गया:** Java के लिए GroupDocs.Watermark 24.11
**लेखक:** GroupDocs