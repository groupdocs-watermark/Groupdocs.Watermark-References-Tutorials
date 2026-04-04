---
date: '2026-04-04'
description: GroupDocs.Watermark Java के साथ डायग्राम शैप्स से लिंक हटाना सीखें, जिससे
  दस्तावेज़ की सुरक्षा और स्पष्टता सुनिश्चित हो।
keywords:
- how to strip links
- remove hyperlinks java
- java diagram editing
title: GroupDocs.Watermark Java का उपयोग करके डायग्राम शैप्स से लिंक हटाने का तरीका
type: docs
url: /hi/java/diagram-document-watermarking/remove-hyperlinks-diagram-shapes-groupdocs-watermark-java/
weight: 1
---

# GroupDocs.Watermark Java का उपयोग करके डायग्राम शैप्स से लिंक हटाने का तरीका

डिजिटल दस्तावेज़ों का प्रबंधन अक्सर डायग्राम संपादन शामिल करता है, विशेष रूप से जब आपको सुरक्षा या स्पष्टता के लिए **how to strip links** की आवश्यकता होती है। इस ट्यूटोरियल में आप जावा के लिए शक्तिशाली **GroupDocs.Watermark** लाइब्रेरी का उपयोग करके डायग्राम शैप्स से अनचाहे हाइपरलिंक हटाने का एक सरल, चरण‑दर‑चरण तरीका सीखेंगे। अंत तक, आपके पास साफ़, लिंक‑रहित डायग्राम होंगे जिन्हें सुरक्षित रूप से साझा किया जा सकता है।

## त्वरित उत्तर
- **how to strip links** का क्या अर्थ है? यह डायग्राम शैप्स में एम्बेडेड हाइपरलिंक ऑब्जेक्ट्स को हटाने को दर्शाता है।  
- **यह कौन सी लाइब्रेरी संभालती है?** GroupDocs.Watermark for Java (version 24.11 or newer).  
- **क्या मुझे लाइसेंस की आवश्यकता है?** एक फ्री ट्रायल परीक्षण के लिए काम करता है; उत्पादन के लिए वैध लाइसेंस आवश्यक है।  
- **क्या मैं एक साथ कई फ़ाइलें प्रोसेस कर सकता हूँ?** हाँ – कोड को लूप या बैच जॉब में रैप करें।  
- **क्या यह तरीका भाषा‑विशिष्ट है?** उदाहरण जावा का है, लेकिन वही अवधारणा अन्य .NET/Java APIs पर भी लागू होती है।

## डायग्राम संपादन में “how to strip links” क्या है?
लिंक हटाने का मतलब है डायग्राम (जैसे Visio *.vsdx) के भीतर शैप्स से जुड़े हाइपरलिंक ऑब्जेक्ट्स को ढूँढ़ना और उन्हें हटाना। इससे बाहरी URLs हट जाते हैं जो संवेदनशील जानकारी उजागर कर सकते हैं या प्रस्तुति प्रवाह को बाधित कर सकते हैं।

## जावा के लिए GroupDocs.Watermark का उपयोग क्यों करें?
- **Precision** – शैप ऑब्जेक्ट्स और उनके हाइपरलिंक कलेक्शन तक सीधा पहुँच।  
- **Performance** – पूरे दस्तावेज़ को मेमोरी में लोड किए बिना बड़े डायग्राम के लिए अनुकूलित।  
- **Cross‑format support** – कई डायग्राम फॉर्मैट्स (Visio, Draw.io, आदि) के साथ काम करता है।  

## पूर्वापेक्षाएँ
- **GroupDocs.Watermark** लाइब्रेरी ≥ 24.11।  
- Maven (या मैन्युअल JAR इंक्लूजन)।  
- Java JDK 8 या नया।  
- IntelliJ IDEA या Eclipse जैसे IDE।  

## जावा के लिए GroupDocs.Watermark सेटअप
### Maven सेटअप
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

### डायरेक्ट डाउनलोड
यदि आप Maven का उपयोग नहीं करना चाहते हैं, तो आधिकारिक साइट से नवीनतम JAR डाउनलोड करें:  
[GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

#### लाइसेंस प्राप्त करने के चरण
- फ़्री ट्रायल डाउनलोड से शुरू करें।  
- प्रोडक्शन के लिए, GroupDocs पोर्टल से टेम्पररी या फुल लाइसेंस प्राप्त करें।

#### बेसिक इनिशियलाइज़ेशन और सेटअप
एक `Watermarker` इंस्टेंस बनाएं जो आपके डायग्राम वाले फ़ोल्डर की ओर इशारा करता हो:

```java
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY", loadOptions);
```

## डायग्राम शैप्स से लिंक हटाने का तरीका
नीचे एक संक्षिप्त, चार‑स्टेप प्रक्रिया दी गई है जो **remove hyperlinks java** को कार्रवाई में दिखाती है।

### चरण 1: डायग्राम फ़ाइल लोड करें
```java
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY", loadOptions);
```
*क्यों?* फ़ाइल लोड करने से आपको उसके पेज, शैप्स और हाइपरलिंक कलेक्शन तक प्रोग्रामेटिक एक्सेस मिलती है।

### चरण 2: शैप कंटेंट तक पहुँचें
```java
DiagramContent content = watermarker.getContent(DiagramContent.class);
DiagramShape shape = content.getPages().get_Item(0).getShapes().get_Item(0);
```
*क्यों?* आपको उस विशिष्ट शैप का रेफ़रेंस चाहिए जिसमें हाइपरलिंक हो सकते हैं।

### चरण 3: इटरेट करें और हाइपरलिंक हटाएँ
```java
for (int i = shape.getHyperlinks().getCount() - 1; i >= 0; i--) {
    if (shape.getHyperlinks().get_Item(i).getAddress().contains("http://someurl.com")) {
        shape.getHyperlinks().removeAt(i);
    }
}
```
*क्यों?* रिवर्स में लूप करने से कलेक्शन से आइटम हटाते समय इंडेक्स‑शिफ्ट समस्याओं से बचा जा सकता है।

### चरण 4: सहेजें और बंद करें
```java
watermarker.save("YOUR_OUTPUT_DIRECTORY");
watermarker.close();
```
*क्यों?* सहेजने से साफ़ किया हुआ डायग्राम डिस्क पर लिखा जाता है, और बंद करने से फ़ाइल हैंडल रिलीज़ होते हैं जिससे मेमोरी लीक नहीं होती।

## लिंक हटाने के व्यावहारिक उपयोग
- **Security** – फ़िशिंग या डेटा लीक का कारण बन सकने वाले बाहरी URLs हटाएँ।  
- **Compliance** – वितरण से पहले सुनिश्चित करें कि डायग्राम आंतरिक नीतियों के अनुरूप हों।  
- **Presentation Cleanliness** – अनावश्यक क्लिकेबल एरिया हटाएँ जो दर्शकों को भटकाते हैं।  

## प्रदर्शन संबंधी विचार
- **Loop Efficiency** – ऊपर दिखाए गए रिवर्स‑इटरेशन पैटर्न का उपयोग करें।  
- **Resource Management** – `try‑with‑resources` या स्पष्ट `close()` कॉल्स को प्राथमिकता दें।  
- **Large Files** – CPU/मेमोरी की निगरानी करें; पेजेस को बैच में प्रोसेस करने पर विचार करें।  

## सामान्य समस्याएँ और समाधान
- **No hyperlinks found** – पुष्टि करें कि डायग्राम में वास्तव में हाइपरलिंक ऑब्जेक्ट्स हैं; कुछ फॉर्मैट्स उन्हें अलग तरीके से स्टोर करते हैं।  
- **IndexOutOfBoundsException** – कलेक्शन से आइटम हटाते समय हमेशा रिवर्स में इटरेट करें।  
- **License errors** – सुनिश्चित करें कि आपका लाइसेंस फ़ाइल सही स्थान पर रखी गई है या `Watermarker` कन्स्ट्रक्टर को पास की गई है।  

## अक्सर पूछे जाने वाले प्रश्न

**Q: मैं कई पेजों पर कई शैप्स को कैसे हैंडल करूँ?**  
A: `content.getPages()` पर लूप करें और फिर प्रत्येक पेज की `getShapes()` कलेक्शन पर, हर शैप पर समान हटाने की लॉजिक लागू करें।

**Q: क्या मैं पूर्ण URL के बजाय डोमेन द्वारा लिंक फ़िल्टर कर सकता हूँ?**  
A: हाँ – `contains` चेक को बदलकर डोमेन स्ट्रिंग (जैसे `"example.com"`) देखें।

**Q: हटाए गए लिंक को लॉग करने का कोई तरीका है?**  
A: लूप के अंदर, हटाने से पहले `shape.getHyperlinks().get_Item(i).getAddress()` को कैप्चर करें और उसे लॉग फ़ाइल में लिखें।

**Q: क्या यह अन्य दस्तावेज़ों में एम्बेडेड PDF डायग्राम के साथ काम करता है?**  
A: GroupDocs.Watermark कई फॉर्मैट्स को सपोर्ट करता है; सुनिश्चित करें कि फ़ाइल टाइप को डायग्राम (Visio, VDX, आदि) के रूप में पहचाना गया है।

**Q: बैच प्रोसेसिंग के लिए कौन सा लाइसेंस आवश्यक है?**  
A: किसी भी नॉन‑ट्रायल, हाई‑वॉल्यूम ऑपरेशन के लिए पूर्ण प्रोडक्शन लाइसेंस आवश्यक है।

## निष्कर्ष
अब आपके पास GroupDocs.Watermark for Java का उपयोग करके डायग्राम शैप्स से **how to strip links** हटाने की एक पूर्ण, प्रोडक्शन‑रेडी विधि है। इसे अपने दस्तावेज़‑प्रोसेसिंग पाइपलाइन में शामिल करें ताकि सुरक्षा, अनुपालन और दृश्य गुणवत्ता बढ़े।

### अगले कदम
- वॉटरमार्क जोड़ने या टेक्स्ट स्टैम्प करने जैसी अन्य मैनिपुलेशन सुविधाओं का अन्वेषण करें।  
- इस रूटीन को फ़ाइल‑वॉचर सर्विस के साथ मिलाएँ ताकि अपलोड होते ही डायग्राम स्वचालित रूप से साफ़ हो जाएँ।

---

**अंतिम अपडेट:** 2026-04-04  
**परीक्षण किया गया:** GroupDocs.Watermark 24.11 for Java  
**लेखक:** GroupDocs  

## संसाधन
- [डॉक्यूमेंटेशन](https://docs.groupdocs.com/watermark/java/)
- [API रेफ़रेंस](https://reference.groupdocs.com/watermark/java)
- [डाउनलोड](https://releases.groupdocs.com/watermark/java/)
- [GitHub रिपॉज़िटरी](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)
- [फ़्री सपोर्ट फ़ोरम](https://forum.groupdocs.com/c/watermark/10)
- [टेम्पररी लाइसेंस प्राप्ति](https://purchase.groupdocs.com/temporary-license/)