---
date: '2025-12-20'
description: GroupDocs.Watermark for Java के साथ जावा में आकार जानकारी निकालना सीखें।
  डायग्राम फ़ाइलों से आयाम, स्थितियाँ और पाठ को कुशलतापूर्वक प्राप्त करें।
keywords:
- extract shape information Java
- GroupDocs.Watermark diagram processing
- Java diagram manipulation
title: 'जावा में आकार जानकारी निकालें: डायग्राम के लिए GroupDocs.Watermark का उपयोग'
type: docs
url: /hi/java/diagram-document-watermarking/retrieve-shape-info-groupdocs-watermark-java/
weight: 1
---

# GroupDocs.Watermark का उपयोग करके जावा में आकृति जानकारी निकालें (डायग्राम में)

जब आपको जटिल डायग्राम फ़ाइलों से **extract shape information java** निकालनी हो, तो इसे मैन्युअल रूप से करना जल्दी ही असंभव हो जाता है। यह ट्यूटोरियल दिखाता है कि कैसे GroupDocs.Watermark for Java का उपयोग करके प्रत्येक आकृति से आयाम, स्थिति, घूर्णन कोण, एम्बेडेड इमेज और टेक्स्ट जैसी जानकारी प्रोग्रामेटिकली प्राप्त की जा सकती है। अंत तक, आपके पास एक स्पष्ट, पुन: उपयोग योग्य पैटर्न होगा जिसे आप किसी भी जावा प्रोजेक्ट में ड्रॉप कर सकते हैं जो Visio‑स्टाइल डायग्राम के साथ काम करता है।

## परिचय

जटिल डायग्राम को मैनेज करने के लिए अक्सर उनके घटकों, जैसे आकृतियों और इमेजेज, की विस्तृत जानकारी तक पहुंच आवश्यक होती है। यदि आपको कभी जावा का उपयोग करके डायग्राम आकृतियों से आयाम, स्थिति या टेक्स्ट जैसी डेटा प्रोग्रामेटिकली प्राप्त करनी पड़ी हो, तो यह ट्यूटोरियल आपके लिए है। GroupDocs.Watermark लाइब्रेरी की शक्ति का उपयोग करके इस प्रक्रिया को जावा एप्लिकेशन में सरल बनाया जा सकता है। इस गाइड में, हम देखेंगे कि कैसे GroupDocs.Watermark का उपयोग करके **extract shape information java** को एक डायग्राम फ़ाइल से निकाला जाए।

## त्वरित उत्तर
- **कौन सी लाइब्रेरी उपयोग करनी चाहिए?** GroupDocs.Watermark for Java (v24.11+)।  
- **कौन से फ़ाइल फ़ॉर्मेट समर्थित हैं?** Visio (.vsdx, .vsd) और API डॉक्यूमेंटेशन में सूचीबद्ध अन्य डायग्राम प्रकार।  
- **क्या लाइसेंस की आवश्यकता है?** विकास के लिए फ्री ट्रायल काम करता है; प्रोडक्शन के लिए कमर्शियल लाइसेंस आवश्यक है।  
- **क्या मैं आकृतियों से इमेज डेटा प्राप्त कर सकता हूँ?** हाँ – API इमेज की चौड़ाई, ऊँचाई और रॉ बाइट डेटा प्रदान करता है।  
- **क्या Maven आवश्यक है?** Maven GroupDocs.Watermark डिपेंडेंसी को मैनेज करने का अनुशंसित तरीका है।

## “extract shape information java” क्या है?

Extract shape information java का अर्थ है प्रोग्रामेटिकली एक डायग्राम फ़ाइल पढ़ना और प्रत्येक आकृति की प्रॉपर्टीज़—आकार, स्थान, घूर्णन, टेक्स्ट और किसी भी एम्बेडेड इमेज—को जावा कोड के माध्यम से निकालना। यह स्वचालित विश्लेषण, रिपोर्टिंग या CAD टूल्स या डेटा‑विज़ुअलाइज़ेशन पाइपलाइन जैसे अन्य सिस्टम के साथ इंटीग्रेशन को सक्षम बनाता है।

## इस कार्य के लिए GroupDocs.Watermark क्यों उपयोग करें?

GroupDocs.Watermark डायग्राम फ़ॉर्मेट्स के ऊपर एक हाई‑लेवल एब्स्ट्रैक्शन प्रदान करता है, जिससे लो‑लेवल पार्सिंग आपके लिए संभाली जाती है। यह आपको बिजनेस लॉजिक पर फोकस करने देता है, न कि XML या बाइनरी स्पेसिफिकेशन पर, और यह समर्थित डायग्राम प्रकारों में लगातार काम करता है।

## पूर्वापेक्षाएँ

- **GroupDocs.Watermark for Java** (संस्करण 24.11 या बाद का)  
- Java Development Kit (JDK) 8 या उससे ऊपर  
- डिपेंडेंसी मैनेजमेंट के लिए Maven  
- IntelliJ IDEA या Eclipse जैसे IDE  

## GroupDocs.Watermark for Java सेट अप करना

अपने Maven `pom.xml` में रिपॉज़िटरी और डिपेंडेंसी जोड़ें:

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

वैकल्पिक रूप से, आप सीधे नवीनतम संस्करण [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/) से डाउनलोड कर सकते हैं।

### लाइसेंस प्राप्त करने के चरण
- **फ्री ट्रायल:** लाइब्रेरी का परीक्षण करने के लिए ट्रायल पैकेज डाउनलोड करें।  
- **टेम्पररी लाइसेंस:** विस्तारित मूल्यांकन के लिए एक टेम्पररी की प्राप्त करें।  
- **पर्चेज:** प्रोडक्शन उपयोग के लिए पूर्ण लाइसेंस खरीदें।

### बेसिक इनिशियलाइज़ेशन

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.contents.DiagramContent;
import com.groupdocs.watermark.options.DiagramLoadOptions;

DiagramLoadOptions diagramLoadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/diagram.vsdx", diagramLoadOptions);
```

## इम्प्लीमेंटेशन गाइड

अब हम ठीक‑ठीक चरणों के माध्यम से **extract shape information java** को एक डायग्राम डॉक्यूमेंट से निकालेंगे।

### लोड और कंटेंट रिट्रीव करना

#### ओवरव्यू
पहले हम डायग्राम फ़ाइल लोड करते हैं और एक `DiagramContent` ऑब्जेक्ट प्राप्त करते हैं, जो हमें पेजेज़ और आकृतियों तक पहुंच देता है।

#### चरण

**डायग्राम डॉक्यूमेंट लोड करना**

```java
// Create load options if necessary
DiagramLoadOptions diagramLoadOptions = new DiagramLoadOptions();
// Initialize watermarker with your document path
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/diagram.vsdx", diagramLoadOptions);
```

- **क्यों:** यह `Watermarker` ऑब्जेक्ट को इनिशियलाइज़ करता है, जिससे डॉक्यूमेंट की कंटेंट तक पहुंच मिलती है।

**डायग्राम कंटेंट एक्सेस करना**

```java
// Retrieve content of the diagram file as a DiagramContent object
DiagramContent content = watermarker.getContent(DiagramContent.class);
```

- **क्यों:** `DiagramContent` क्लास विभिन्न डायग्राम पहलुओं, जैसे पेजेज़ और आकृतियों, के साथ इंटरैक्ट करने के मेथड्स प्रदान करता है।

### आकृतियों के माध्यम से इटरेट करना

#### ओवरव्यू
`DiagramContent` हाथ में होने पर, हम प्रत्येक पेज और फिर प्रत्येक आकृति पर लूप लगाते हैं ताकि आवश्यक प्रॉपर्टीज़ निकाली जा सकें।

#### चरण

**पेजेज़ पर इटरेट करना**

```java
for (DiagramPage page : content.getPages()) {
    // Process each shape in the current page
}
```

- **क्यों:** डायग्राम कई पेजेज़ से बने होते हैं; हमें प्रत्येक पेज की आकृतियों को जांचना होता है।

**आकृति जानकारी निकालना**

```java
for (DiagramShape shape : page.getShapes()) {
    if (shape.getImage() != null) {
        // Access and print image-related properties
        System.out.println("Image Width: " + shape.getImage().getWidth());
        System.out.println("Image Height: " + shape.getImage().getHeight());
        System.out.println("Image Size: " + shape.getImage().getData().length);
    }
    
    // Print other shape attributes
    System.out.println("Shape Name: " + shape.getName());
    System.out.println("X Position: " + shape.getX());
    System.out.println("Y Position: " + shape.getY());
    System.out.println("Width: " + shape.getWidth());
    System.out.println("Height: " + shape.getHeight());
    System.out.println("Rotation Angle: " + shape.getRotationAngle());
    System.out.println("Text: " + (shape.getText() != null ? shape.getText() : "No text"));
    System.out.println("Shape ID: " + shape.getId());
}
```

- **क्यों:** यह लूप प्रत्येक आकृति की प्रॉपर्टीज़ जैसे आयाम, स्थिति, घूर्णन और किसी भी एम्बेडेड इमेज या टेक्स्ट को निकालता और प्रिंट करता है। ये एट्रिब्यूट्स समझने के लिए महत्वपूर्ण हैं कि आकृतियों को डायग्राम में कैसे कॉन्फ़िगर किया गया है।

### ट्रबलशूटिंग टिप्स
- फ़ाइल पाथ सही है और पढ़ने योग्य `.vsdx` (या समर्थित) फ़ाइल की ओर इशारा कर रहा है, यह सुनिश्चित करें।  
- एप्लिकेशन के पास डायग्राम फ़ाइल के लिए रीड परमिशन है, यह जांचें।  
- यदि “Unsupported format” त्रुटि आती है, तो पुष्टि करें कि आपका GroupDocs.Watermark संस्करण उस विशेष डायग्राम प्रकार को सपोर्ट करता है।

## व्यावहारिक अनुप्रयोग

**extract shape information java** की क्षमता के साथ आप कई वास्तविक‑दुनिया परिदृश्यों को सक्षम कर सकते हैं:

1. **डायग्राम विश्लेषण:** स्वचालित रूप से रिपोर्ट जेनरेट करें जो प्रत्येक आकृति का आकार, स्थान और टेक्स्ट सूचीबद्ध करे—गुणवत्ता‑असुरेंस ऑडिट के लिए उपयोगी।  
2. **डेटा विज़ुअलाइज़ेशन:** आकृति मीट्रिक्स को डैशबोर्ड में फीड करें ताकि लेआउट डेंसिटी को विज़ुअलाइज़ किया जा सके या ओवरसाइज़्ड एलिमेंट्स की पहचान की जा सके।  
3. **CAD इंटीग्रेशन:** डायग्राम डेटा को CAD पाइपलाइन में ब्रिज करें, जिससे स्वचालित री‑डिज़ाइन या वैलिडेशन स्टेप्स संभव हों।

## प्रदर्शन संबंधी विचार

बड़े डायग्राम प्रोसेस करते समय इन बेस्ट प्रैक्टिसेज़ को याद रखें:

- **रिसोर्सेज़ को तुरंत बंद करें:** मेमोरी मुक्त करने के लिए `watermarker.close()` कॉल करें (या try‑with‑resources का उपयोग करें)।  
- **हीप उपयोग मॉनिटर करें:** बड़े डायग्राम काफी मेमोरी खा सकते हैं; आवश्यकतानुसार JVM हीप (`-Xmx`) को समायोजित करें।  
- **बैच प्रोसेसिंग:** एक साथ कई फ़ाइलें लोड करने के बजाय बैच में प्रोसेस करें।

## निष्कर्ष

इस गाइड को फॉलो करके, आप अब जानते हैं कि **extract shape information java** को GroupDocs.Watermark for Java की मदद से कैसे किया जाए। आप किसी भी समर्थित डायग्राम फ़ाइल से आयाम, स्थान, घूर्णन कोण, एम्बेडेड इमेज और टेक्स्ट निकाल सकते हैं, जिससे स्वचालित विश्लेषण, रिपोर्टिंग और बड़े सिस्टम के साथ इंटीग्रेशन संभव हो जाता है। अगले कदम के लिए तैयार हैं? आधिकारिक [डॉक्यूमेंटेशन](https://docs.groupdocs.com/watermark/java/) में लाइब्रेरी की पूरी क्षमताओं का अन्वेषण करें और वॉटरमार्किंग, रेडैक्शन या कस्टम आकृति मैनिपुलेशन के साथ प्रयोग करें।

## अक्सर पूछे जाने वाले प्रश्न

**प्रश्न: GroupDocs.Watermark क्या है?**  
उत्तर: एक व्यापक जावा लाइब्रेरी जो विभिन्न डॉक्यूमेंट फ़ॉर्मेट्स, जिसमें डायग्राम भी शामिल हैं, से वॉटरमार्किंग और जानकारी निकालने के लिए डिज़ाइन की गई है।

**प्रश्न: क्या मैं इस लाइब्रेरी का उपयोग सभी प्रकार की डायग्राम फ़ाइलों को प्रोसेस करने के लिए कर सकता हूँ?**  
उत्तर: हाँ, लेकिन सुनिश्चित करें कि फ़ाइल फ़ॉर्मेट API रेफ़रेंस में सूचीबद्ध समर्थित फ़ॉर्मेट्स में से एक है ([API Reference](https://reference.groupdocs.com/watermark/java/))।

**प्रश्न: जावा और GroupDocs.Watermark का उपयोग करके डायग्राम से आकृति के आयाम और स्थान कैसे निकाले जाएँ?**  
उत्तर: डायग्राम लोड करें, `DiagramContent` प्राप्त करें, फिर प्रत्येक `DiagramShape` पर इटरेट करके चौड़ाई, ऊँचाई, X और Y जैसी प्रॉपर्टीज़ पढ़ें।

**प्रश्न: क्या GroupDocs.Watermark जावा के साथ डायग्राम आकृतियों में एम्बेडेड इमेज निकाल सकता है?**  
उत्तर: हाँ, यह आकृतियों के भीतर इमेज डेटा तक पहुंच प्रदान करता है, जिसमें आकार और रॉ बाइट एरे शामिल हैं, जिन्हें आप विश्लेषण या मॉडिफिकेशन के लिए उपयोग कर सकते हैं।

**प्रश्न: जावा में डायग्राम आकृति जानकारी निकालने के लिए क्या पूर्वापेक्षाएँ हैं?**  
उत्तर: Java JDK 8+, Maven सेटअप, GroupDocs.Watermark लाइब्रेरी (24.11+), और बेसिक जावा प्रोग्रामिंग ज्ञान।

---

**अंतिम अपडेट:** 2025-12-20  
**टेस्टेड विथ:** GroupDocs.Watermark 24.11 for Java  
**लेखक:** GroupDocs  

---