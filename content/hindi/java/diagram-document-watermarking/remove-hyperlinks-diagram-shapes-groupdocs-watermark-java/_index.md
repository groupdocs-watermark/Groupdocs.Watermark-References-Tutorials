---
date: '2025-12-19'
description: GroupDocs.Watermark Java का उपयोग करके डायग्राम शेप्स से हाइपरलिंक्स
  हटाना सीखें, जो जावा दस्तावेज़ सुरक्षा के लिए एक महत्वपूर्ण कदम है और हाइपरलिंक्स
  को बैच में हटाता है।
keywords:
- remove hyperlinks diagram shapes GroupDocs Watermark Java
- manage digital documents diagrams
- GroupDocs Watermark library Java
title: GroupDocs.Watermark Java का उपयोग करके डायग्राम शैप्स से हाइपरलिंक्स कैसे हटाएँ
type: docs
url: /hi/java/diagram-document-watermarking/remove-hyperlinks-diagram-shapes-groupdocs-watermark-java/
weight: 1
---

# GroupDocs.Watermark Java का उपयोग करके डायग्राम शैप्स से हाइपरलिंक्स हटाना

डिजिटल दस्तावेज़ों का प्रबंधन अक्सर डायग्राम को संपादित करने में शामिल होता है, विशेष रूप से जब सुरक्षा या स्पष्टता के लिए **हाइपरलिंक्स हटाने** की आवश्यकता होती है। इस ट्यूटोरियल में, आप GroupDocs.Watermark for Java के साथ डायग्राम शैप्स से **हाइपरलिंक्स कैसे हटाएँ** सीखेंगे, जिससे आपके फ़ाइलें साफ़, सुरक्षित और पेशेवर बनी रहेंगी।

## त्वरित उत्तर
- **मुख्य उद्देश्य क्या है?** बेहतर दस्तावेज़ सुरक्षा के लिए डायग्राम शैप्स से अनावश्यक हाइपरलिंक्स हटाना।  
- **कौन सी लाइब्रेरी उपयोग की जाती है?** GroupDocs.Watermark for Java (version 24.11 या बाद का)।  
- **क्या मुझे लाइसेंस चाहिए?** परीक्षण के लिए ट्रायल काम करता है; उत्पादन के लिए वैध लाइसेंस आवश्यक है।  
- **क्या मैं एक साथ कई फ़ाइलें प्रोसेस कर सकता हूँ?** हाँ – वही लॉजिक बैच लूप में रखा जा सकता है।  
- **क्या Java 8 पर्याप्त है?** Java 8+ समर्थित है; नए JDK की सलाह दी जाती है।  

## डायग्राम के संदर्भ में “हाइपरलिंक्स कैसे हटाएँ” क्या है?
हाइपरलिंक्स हटाने का मतलब है कि डायग्राम फ़ाइल (जैसे Visio *.vsdx) के भीतर शैप्स से जुड़े URL रेफ़रेंसेज़ को हटाना। यह ऑपरेशन अनजाने में बाहरी साइटों पर नेविगेशन को रोकता है और अनुपालन या आंतरिक सुरक्षा नीतियों को पूरा करने में मदद करता है।

## इस कार्य के लिए GroupDocs.Watermark Java का उपयोग क्यों करें?
- **Robust format support** – विभिन्न प्रकार के डायग्राम फ़ॉर्मेट्स के साथ काम करता है।  
- **Fine‑grained API** – आपको व्यक्तिगत शैप्स और उनके हाइपरलिंक कलेक्शन को टार्गेट करने देता है।  
- **Performance‑optimized** – सिंगल फ़ाइल और बैच प्रोसेसिंग दोनों के लिए उपयुक्त।  

## पूर्वापेक्षाएँ
- **GroupDocs.Watermark** लाइब्रेरी version 24.11 या बाद का।  
- Maven या सीधे JAR डाउनलोड (नीचे सेटअप चरण देखें)।  
- Java Development Kit (JDK 8 या नया) और IntelliJ IDEA या Eclipse जैसे IDE।  

## GroupDocs.Watermark for Java सेटअप करना
शुरू करने के लिए, Maven के माध्यम से या JAR डाउनलोड करके लाइब्रेरी को अपने प्रोजेक्ट में शामिल करें।

### Maven सेटअप
अपने `pom.xml` में निम्न कॉन्फ़िगरेशन जोड़ें:

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
वैकल्पिक रूप से, नवीनतम संस्करण को यहाँ से डाउनलोड करें: [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/)।

#### लाइसेंस प्राप्त करने के चरण
- API का मूल्यांकन करने के लिए मुफ्त ट्रायल से शुरू करें।  
- उत्पादन के लिए, GroupDocs पोर्टल से एक टेम्पररी या फुल‑साइज़ लाइसेंस प्राप्त करें।

#### बुनियादी इनिशियलाइज़ेशन और सेटअप
```java
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY", loadOptions);
```

## डायग्राम शैप्स से हाइपरलिंक्स हटाने का तरीका
नीचे एक चरण‑दर‑चरण गाइड है जो आपको डायग्राम लोड करने, शैप्स खोजने और अनावश्यक हाइपरलिंक्स हटाने में मदद करेगा।

### चरण 1: डायग्राम फ़ाइल लोड करें
```java
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY", loadOptions);
```
*Why?* फ़ाइल को लोड करने से आपको उसकी आंतरिक संरचना तक प्रोग्रामेटिक एक्सेस मिलता है।

### चरण 2: शैप कंटेंट एक्सेस करें
```java
DiagramContent content = watermarker.getContent(DiagramContent.class);
DiagramShape shape = content.getPages().get_Item(0).getShapes().get_Item(0);
```
*Why?* आपको उस विशिष्ट शैप का रेफ़रेंस चाहिए जिसमें हाइपरलिंक्स हो सकते हैं।

### चरण 3: इटररेट करें और हाइपरलिंक्स हटाएँ
```java
for (int i = shape.getHyperlinks().getCount() - 1; i >= 0; i--) {
    if (shape.getHyperlinks().get_Item(i).getAddress().contains("http://someurl.com")) {
        shape.getHyperlinks().removeAt(i);
    }
}
```
*Why?* बैकवर्ड लूपिंग करने से कलेक्शन से आइटम डिलीट करते समय इंडेक्स एरर से बचा जा सकता है।

### चरण 4: सेव करें और बंद करें
```java
watermarker.save("YOUR_OUTPUT_DIRECTORY");
watermarker.close();
```
*Why?* बदलावों को सहेजना और रिसोर्सेज़ रिलीज़ करना मेमोरी लीक्स और लॉक्ड फ़ाइलों से बचाता है।

## बैच में हाइपरलिंक्स हटाना (उन्नत उपयोग केस)
यदि आपको कई डायग्राम एक साथ साफ़ करने हैं, तो ऊपर दिया गया लॉजिक फ़ाइल पाथ्स की सूची पर इटररेट करने वाले लूप में रखें। वही API कॉल्स लागू होते हैं; प्रत्येक इटरेशन के लिए इनपुट और आउटपुट डायरेक्टरी बदलें। यह तरीका बड़े दस्तावेज़ रिपॉज़िटरी के लिए **batch remove hyperlinks** आवश्यकताओं के अनुरूप है।

## व्यावहारिक अनुप्रयोग
डायग्राम शैप्स से हाइपरलिंक्स हटाना कई वास्तविक परिदृश्यों में लाभदायक हो सकता है:

1. **Security Purposes** – फ़िशिंग या मैलवेयर से बचाने के लिए बाहरी लिंक को रोकें।  
2. **Compliance** – साझा दस्तावेज़ों में आउटबाउंड URL को प्रतिबंधित करने वाली कॉर्पोरेट नीतियों को पूरा करें।  
3. **Clarity** – ऐसे प्रेज़ेंटेशन बनाएं जहाँ हाइपरलिंक्स अनावश्यक या ध्यान भंग करने वाले न हों।  

## प्रदर्शन संबंधी विचार
### प्रदर्शन अनुकूलन
- ऊपर दिखाए गए रिवर्स‑इटरेशन पैटर्न का उपयोग करके लूप को कुशल रखें।  
- काम समाप्त होते ही `Watermarker` ऑब्जेक्ट को बंद करें ताकि मेमोरी मुक्त हो सके।

### संसाधन उपयोग दिशानिर्देश
- बड़े डायग्राम प्रोसेस करते समय CPU और RAM की निगरानी रखें।  
- बैच जॉब्स के लिए फ़ाइलों को एक साथ लोड करने के बजाय स्ट्रीमिंग पर विचार करें।

### जावा मेमोरी प्रबंधन के लिए सर्वोत्तम प्रैक्टिस
- टाइट लूप्स के अंदर ऑब्जेक्ट्स बनाना टालें।  
- जहाँ लागू हो, `try‑with‑resources` का उपयोग करके ऑटोमैटिक क्लीनअप करें।

## अक्सर पूछे जाने वाले प्रश्न
1. **मैं कई शैप्स को कैसे हैंडल करूँ?**  
   सभी पेजों और उनके शैप्स पर इटररेट करें, और प्रत्येक शैप पर वही हाइपरलिंक‑रिमूवल लॉजिक लागू करें।  

2. **क्या इस प्रोसेस को बड़े बैच डायग्राम के लिए ऑटोमेट किया जा सकता है?**  
   हाँ – कोड को बैच‑प्रोसेसिंग रूटीन में एम्बेड करें या इसे अपने डॉक्यूमेंट‑मैनेजमेंट सिस्टम के साथ इंटीग्रेट करें।  

3. **यदि मुझे केवल विशिष्ट पेजों से हाइपरलिंक्स हटाने हैं तो क्या करें?**  
   इच्छित पेज को उसके इंडेक्स (`content.getPages().get_Item(pageIndex)`) से एक्सेस करें और केवल उस पेज के शैप्स को टार्गेट करें।  

4. **GroupDocs.Watermark के प्रोडक्शन उपयोग के लिए कोई लाइसेंस आवश्यक है क्या?**  
   ट्रायल अवधि के बाद एक वैध कमर्शियल लाइसेंस आवश्यक है।  

5. **क्या यह मेथड अन्य डायग्राम फ़ॉर्मेट्स के साथ काम कर सकता है?**  
   GroupDocs.Watermark कई डायग्राम प्रकारों को सपोर्ट करता है; आधिकारिक डॉक्यूमेंटेशन में संगतता जाँचें।  

**Additional Q&A**

**Q:** *क्या हटाए गए हाइपरलिंक्स को लॉग किया जा सकता है?*  
**A:** हाँ – `removeAt(i)` कॉल करने से पहले `shape.getHyperlinks().get_Item(i).getAddress()` को कैप्चर करके लॉग फ़ाइल में लिखें।

**Q:** *हाइपरलिंक्स हटाने से शैप की विज़ुअल अपीयरेंस पर असर पड़ेगा?*  
**A:** नहीं। शैप की ज्योमेट्री अपरिवर्तित रहती है; केवल लिंक मेटाडेटा हटाया जाता है।

**Q:** *हटाने के बाद मुझे कोई स्टाइलिंग फिर से लागू करनी पड़ेगी?*  
**A:** आमतौर पर नहीं। हाइपरलिंक हटाने से फ़िल, लाइन या टेक्स्ट स्टाइल्स पर कोई असर नहीं पड़ता।

## निष्कर्ष
आपके पास अब GroupDocs.Watermark for Java का उपयोग करके डायग्राम शैप्स से **हाइपरलिंक्स कैसे हटाएँ** की एक पूर्ण, प्रोडक्शन‑रेडी विधि है। ऊपर दिए गए चरणों का पालन करके आप अपने डायग्राम को सुरक्षित बना सकते हैं, नीतियों का पालन कर सकते हैं, और अपने दस्तावेज़ को पॉलिश्ड रख सकते हैं।

---

**Last Updated:** 2025-12-19  
**Tested With:** GroupDocs.Watermark 24.11 for Java  
**Author:** GroupDocs  

**Resources**  
- [Documentation](https://docs.groupdocs.com/watermark/java/)  
- [API Reference](https://reference.groupdocs.com/watermark/java)  
- [Download](https://releases.groupdocs.com/watermark/java/)  
- [GitHub Repository](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)  
- [Free Support Forum](https://forum.groupdocs.com/c/watermark/10)  
- [Temporary License Acquisition](https://purchase.groupdocs.com/temporary-license/)