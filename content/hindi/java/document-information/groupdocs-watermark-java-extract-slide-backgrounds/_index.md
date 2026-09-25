---
date: '2026-09-11'
description: Java में slide background निकालने और GroupDocs.Watermark for Java का
  उपयोग करके PowerPoint slide dimensions पढ़ने का तरीका सीखें। कुछ ही मिनटों में image
  size, file size, और metadata प्राप्त करें।
keywords:
- extract slide background java
- read powerpoint slide dimensions
- slide background details java
lastmod: '2026-09-11'
og_description: GroupDocs.Watermark for Java का उपयोग करके slide background java निकालें
  और PowerPoint slide dimensions पढ़ें। setup, code, और troubleshooting के साथ विस्तृत
  गाइड।
og_image_alt: Guide showing Java code extracting slide background information from
  PowerPoint
og_title: GroupDocs.Watermark के साथ slide background java निकालें
schemas:
- author: GroupDocs
  dateModified: '2026-09-11'
  description: Learn how to extract slide background java and read PowerPoint slide
    dimensions using GroupDocs.Watermark for Java. Get image size, file size, and
    metadata in minutes.
  headline: How to extract slide background java
  type: TechArticle
- description: Learn how to extract slide background java and read PowerPoint slide
    dimensions using GroupDocs.Watermark for Java. Get image size, file size, and
    metadata in minutes.
  name: How to extract slide background java
  steps:
  - name: create load options
    text: '`PresentationLoadOptions` defines loading preferences such as password
      handling and memory usage.'
  - name: open the PowerPoint document
    text: Instantiate `Watermarker` with the path to your `.pptx` file and the load
      options created earlier.
  - name: access slide content
    text: '`PresentationContent` is the entry point for retrieving slide‑level objects,
      including background images.'
  - name: iterate over slides and read background details
    text: Slide represents an individual slide within the presentation and provides
      access to its visual elements. For each `Slide` object, call `getBackground()`
      to obtain the image, then read its dimensions and size.
  - name: close the watermarker
    text: Always close the `Watermarker` instance to free native resources and avoid
      memory leaks.
  type: HowTo
- questions:
  - answer: Java 11 or newer is required; earlier versions lack the necessary language
      features for the library.
    question: What is the minimum Java version required?
  - answer: Yes—set the password in `PresentationLoadOptions` before opening the file.
    question: Can I extract backgrounds from password‑protected presentations?
  - answer: The trial imposes a watermark on output files but does not restrict slide
      count for metadata extraction.
    question: Does the trial mode limit the number of slides I can process?
  - answer: Absolutely—use `ImageInfo.save("output.png")` after retrieving the `ImageInfo`
      object.
    question: Is it possible to save the extracted background image to disk?
  - answer: The API supports PNG, JPEG, BMP, and GIF for background image export.
    question: Which formats can I export the extracted image to?
  type: FAQPage
tags:
- extract slide background
- GroupDocs.Watermark
- Java PowerPoint
- document processing
title: Java में slide background निकालने का तरीका
type: docs
url: /hi/java/document-information/groupdocs-watermark-java-extract-slide-backgrounds/
weight: 1
---

# स्लाइड बैकग्राउंड जावा को निकालने का तरीका

## परिचय

स्लाइड बैकग्राउंड जावा को निकालना एक सामान्य आवश्यकता है जब आप PowerPoint फ़ाइल के भीतर दृश्य संपत्तियों का विश्लेषण, पुन: उपयोग या दस्तावेज़ीकरण करना चाहते हैं। GroupDocs.Watermark for Java के साथ आप प्रोग्रामेटिक रूप से इमेज के आयाम, फ़ाइल आकार और अन्य मेटाडेटा प्राप्त कर सकते हैं बिना PowerPoint में प्रस्तुति खोले। यह ट्यूटोरियल आपको संपूर्ण कार्यप्रवाह—पर्यावरण सेटअप से लेकर बैकग्राउंड विवरण निकालने और समझने तक—के माध्यम से ले जाता है, ताकि आप इस क्षमता को किसी भी Java‑आधारित ऑटोमेशन पाइपलाइन में एकीकृत कर सकें।

### त्वरित उत्तर
- **स्लाइड बैकग्राउंड एक्सट्रैक्शन को कौनसी लाइब्रेरी संभालती है?** GroupDocs.Watermark for Java.  
- **इमेज के आयाम लौटाने वाली मेथड कौनसी है?** `getBackground().getImageInfo().getWidth()` और `getHeight()`.  
- **क्या मैं बैकग्राउंड इमेज का फ़ाइल आकार प्राप्त कर सकता हूँ?** हाँ, `getBackground().getImageInfo().getSize()` के माध्यम से।  
- **क्या इस फीचर के लिए लाइसेंस आवश्यक है?** एक अस्थायी या पूर्ण लाइसेंस पूरी कार्यक्षमता अनलॉक करता है; ट्रायल मोड सीमाओं के साथ काम करता है।  
- **क्या Maven समर्थित है?** बिल्कुल—`pom.xml` में GroupDocs.Watermark डिपेंडेंसी जोड़ें।

## स्लाइड बैकग्राउंड जावा निकालना क्या है?

स्लाइड बैकग्राउंड जावा निकालना वह प्रक्रिया है जिसमें Java कोड का उपयोग करके PowerPoint प्रस्तुति की प्रत्येक स्लाइड के दृश्य बैकग्राउंड को प्रोग्रामेटिक रूप से पढ़ा जाता है। यह ऑपरेशन इमेज की चौड़ाई, ऊँचाई और फ़ाइल आकार जैसी मेटाडेटा प्रदान करता है, जिससे ब्रांडिंग जांच या संपत्ति पुन: उपयोग जैसी डाउनस्ट्रीम प्रोसेसिंग संभव होती है।

## इस कार्य के लिए GroupDocs.Watermark क्यों उपयोग करें?

GroupDocs.Watermark **30+ इनपुट और आउटपुट फ़ॉर्मेट** को सपोर्ट करता है, **500 स्लाइड** तक की प्रस्तुतियों को पूरी फ़ाइल को मेमोरी में लोड किए बिना प्रोसेस करता है, और स्लाइड बैकग्राउंड तक पहुँचने के लिए एक समर्पित API प्रदान करता है। ये मापी गई क्षमताएँ इसे एंटरप्राइज़‑स्तर की ऑटोमेशन के लिए एक विश्वसनीय विकल्प बनाती हैं।

## पूर्वापेक्षाएँ
- **Java 11+** आपके विकास मशीन पर स्थापित होना चाहिए।  
- **Maven** डिपेंडेंसी प्रबंधन के लिए।  
- **GroupDocs.Watermark 24.11** (या बाद का संस्करण) – इस लाइब्रेरी में इस गाइड में उपयोग किए गए `PresentationLoadOptions` और `PresentationContent` क्लासेस शामिल हैं।  
- एक **वैध लाइसेंस** (अस्थायी या पूर्ण) पूरी फीचर सेट को अनलॉक करने के लिए।

## Java के लिए GroupDocs.Watermark सेटअप करना

### Maven कॉन्फ़िगरेशन
`pom.xml` फ़ाइल में GroupDocs.Watermark डिपेंडेंसी जोड़ें:

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
यदि आप मैन्युअल इंस्टॉलेशन पसंद करते हैं, तो आधिकारिक रिलीज़ पेज से नवीनतम JAR प्राप्त करें: [GroupDocs.Watermark for Java रिलीज़](https://releases.groupdocs.com/watermark/java/)।

### लाइसेंस प्राप्ति
एक अस्थायी लाइसेंस आपको API का मूल्यांकन करने देता है, जबकि पूर्ण लाइसेंस सभी ट्रायल प्रतिबंधों को हटा देता है। लाइसेंसिंग पोर्टल पर अपना लाइसेंस प्राप्त करें: [GroupDocs लाइसेंसिंग पेज](https://purchase.groupdocs.com/temporary-license/)।

#### बुनियादी इनिशियलाइज़ेशन और सेटअप
पहला कदम यह है कि आप एक `Watermarker` इंस्टेंस बनाएं जो आपके PowerPoint फ़ाइल की ओर इशारा करता हो:

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.PresentationLoadOptions;

// Create load options for the presentation file.
PresentationLoadOptions loadOptions = new PresentationLoadOptions();

// Open the PowerPoint document using Watermarker with specified load options.
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/presentation.pptx", loadOptions);
```

## स्लाइड बैकग्राउंड जावा को कैसे निकालें?

प्रक्रिया Watermarker इंस्टेंस का उपयोग करके PowerPoint फ़ाइल को लोड करने से शुरू होती है, फिर उपयुक्त लोड विकल्प बनाते हैं। दस्तावेज़ खोलने के बाद, आप प्रत्येक स्लाइड की सामग्री तक पहुँच सकते हैं, बैकग्राउंड इमेज प्राप्त कर सकते हैं, और उसके मेटाडेटा जैसे आयाम और फ़ाइल आकार निकाल सकते हैं। अंत में, संसाधनों को मुक्त करने के लिए Watermarker को बंद करें। नीचे दिए गए चरण वह सटीक क्रम दर्शाते हैं जिसे आपको पालन करना है, और कोड प्लेसहोल्डर दिखाते हैं कि आपके मौजूदा स्निपेट्स कहाँ रखे जाने चाहिए।

### चरण 1: लोड विकल्प बनाएं
`PresentationLoadOptions` लोडिंग प्राथमिकताओं को परिभाषित करता है जैसे पासवर्ड हैंडलिंग और मेमोरी उपयोग।

```java
PresentationLoadOptions loadOptions = new PresentationLoadOptions();
```

### चरण 2: PowerPoint दस्तावेज़ खोलें
पहले बनाए गए लोड विकल्पों के साथ अपने `.pptx` फ़ाइल के पथ को उपयोग करके `Watermarker` का इंस्टेंस बनाएं।

```java
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/presentation.pptx", loadOptions);
```

### चरण 3: स्लाइड सामग्री तक पहुँचें
`PresentationContent` स्लाइड‑स्तर के ऑब्जेक्ट्स, जिसमें बैकग्राउंड इमेजेज शामिल हैं, को प्राप्त करने का प्रवेश बिंदु है।

```java
import com.groupdocs.watermark.contents.PresentationContent;

PresentationContent content = watermarker.getContent(PresentationContent.class);
```

### चरण 4: स्लाइड्स पर इटररेट करें और बैकग्राउंड विवरण पढ़ें
Slide प्रस्तुति के भीतर एक व्यक्तिगत स्लाइड को दर्शाता है और इसके दृश्य तत्वों तक पहुँच प्रदान करता है।  
प्रत्येक `Slide` ऑब्जेक्ट के लिए, इमेज प्राप्त करने हेतु `getBackground()` कॉल करें, फिर उसके आयाम और आकार पढ़ें।

```java
import com.groupdocs.watermark.contents.PresentationSlide;
import com.groupdocs.watermark.options.PresentationLoadOptions;

for (PresentationSlide slide : content.getSlides()) {
    if (slide.getImageFillFormat().getBackgroundImage() != null) {
        // Extract width, height, and size of the background image.
        int width = slide.getImageFillFormat().getBackgroundImage().getWidth();
        int height = slide.getImageFillFormat().getBackgroundImage().getHeight();
        long imageSize = slide.getImageFillFormat().getBackgroundImage().getBytes().length;
        
        System.out.println("Width: " + width + ", Height: " + height + ", Image Size: " + imageSize);
    }
}
```

### चरण 5: Watermarker को बंद करें
सदैव `Watermarker` इंस्टेंस को बंद करें ताकि नेटिव संसाधन मुक्त हों और मेमोरी लीक से बचा जा सके।

```java
watermarker.close();
```

## GroupDocs.Watermark का उपयोग करके PowerPoint स्लाइड आयाम कैसे पढ़ें?

API स्लाइड के बैकग्राउंड से जुड़े `ImageInfo` ऑब्जेक्ट के माध्यम से चौड़ाई और ऊँचाई को उजागर करता है। इन्हें `getWidth()` और `getHeight()` से प्राप्त करें, जो पिक्सेल मान लौटाते हैं जिन्हें आप लेआउट गणनाओं या ब्रांडिंग दिशानिर्देशों के विरुद्ध वैधता के लिए उपयोग कर सकते हैं।

## सामान्य समस्याएँ और ट्रबलशूटिंग
- **फ़ाइल नहीं मिली** – सुनिश्चित करें कि फ़ाइल पथ पूर्ण (absolute) है या आपके प्रोजेक्ट रूट के सापेक्ष सही है।  
- **असमर्थित फ़ॉर्मेट** – GroupDocs.Watermark PPTX, PPT, और ODP को सपोर्ट करता है; पुराने बाइनरी PPT फ़ाइलों को पहले रूपांतरण की आवश्यकता हो सकती है।  
- **लाइसेंस लागू नहीं हुआ** – किसी भी अन्य API उपयोग से पहले `License.setLicense("path/to/license.file")` कॉल करना सुनिश्चित करें।

## व्यावहारिक अनुप्रयोग
1. **स्वचालित ब्रांडिंग अनुपालन** – स्लाइड बैकग्राउंड को स्कैन करें ताकि यह पुष्टि हो सके कि वे कॉर्पोरेट रंग पैलेट या लोगो आयामों से मेल खाते हैं।  
2. **संपत्ति इन्वेंटरी** – दस्तावेज़ लाइब्रेरी में बैकग्राउंड इमेजेज का कैटलॉग बनाएं ताकि उन्हें मार्केटिंग संपत्तियों में पुन: उपयोग किया जा सके।  
3. **सामग्री माइग्रेशन** – बैकग्राउंड को निकालें, उन्हें डिजिटल एसेट मैनेजर में संग्रहीत करें, और प्रोग्रामेटिक रूप से नई प्रस्तुतियों में पुनः लागू करें।  
4. **परफॉर्मेंस मॉनिटरिंग** – इमेज आकार सांख्यिकी लॉग करें ताकि असामान्य रूप से बड़े एसेट्स का पता चल सके जो स्लाइड रेंडरिंग को धीमा कर सकते हैं।

## प्रदर्शन संबंधी विचार
- **संसाधन सफाई** – `Watermarker` को शीघ्र बंद करने से नेटिव मेमोरी मुक्त होती है, जो बड़े डेक प्रोसेस करते समय महत्वपूर्ण है।  
- **मेमोरी फुटप्रिंट** – लाइब्रेरी स्लाइड डेटा को स्ट्रीम करती है; आप पूरी प्रस्तुति लोड करने के बजाय एक समय में एक स्लाइड प्रोसेस करके उपयोग को और घटा सकते हैं।  
- **बैच प्रोसेसिंग टिप** – जब दर्जनों फ़ाइलों को संभाल रहे हों, तो एक ही `License` इंस्टेंस को पुन: उपयोग करें और प्रत्येक फ़ाइल के लिए नया `Watermarker` बनाएं ताकि JVM हीप स्थिर रहे।

## निष्कर्ष

अब आपके पास GroupDocs.Watermark के साथ स्लाइड बैकग्राउंड जावा निकालने के लिए एक पूर्ण, प्रोडक्शन‑रेडी गाइड है। ऊपर दिए गए चरणों का पालन करके आप इमेज आयाम, फ़ाइल आकार और अन्य मेटाडेटा प्राप्त कर सकते हैं, फिर इस जानकारी को ब्रांडिंग जांच, एसेट मैनेजमेंट, या किसी भी कस्टम वर्कफ़्लो में लागू कर सकते हैं।

**अगले कदम**
- विभिन्न `PresentationLoadOptions` (जैसे, पासवर्ड‑सुरक्षित फ़ाइलें) के साथ प्रयोग करें।  
- `watermarking` API का अन्वेषण करें ताकि बैकग्राउंड को स्वचालित रूप से जोड़ या बदल सकें।  
- इस एक्सट्रैक्शन लॉजिक को एक REST सेवा के साथ मिलाकर स्लाइड‑मेटाडेटा एंडपॉइंट्स को एक्सपोज़ करें।

## अक्सर पूछे जाने वाले प्रश्न

**प्र: न्यूनतम Java संस्करण क्या आवश्यक है?**  
**उ:** Java 11 या नया आवश्यक है; पुराने संस्करणों में लाइब्रेरी के लिए आवश्यक भाषा सुविधाएँ नहीं होतीं।

**प्र: क्या मैं पासवर्ड‑सुरक्षित प्रस्तुतियों से बैकग्राउंड निकाल सकता हूँ?**  
**उ:** हाँ—फ़ाइल खोलने से पहले `PresentationLoadOptions` में पासवर्ड सेट करें।

**प्र: क्या ट्रायल मोड प्रोसेस की जाने वाली स्लाइड्स की संख्या को सीमित करता है?**  
**उ:** ट्रायल आउटपुट फ़ाइलों पर वॉटरमार्क लगाता है लेकिन मेटाडेटा एक्सट्रैक्शन के लिए स्लाइड संख्या को सीमित नहीं करता।

**प्र: क्या निकाली गई बैकग्राउंड इमेज को डिस्क पर सेव करना संभव है?**  
**उ:** बिल्कुल—`ImageInfo` ऑब्जेक्ट प्राप्त करने के बाद `ImageInfo.save("output.png")` का उपयोग करें।

**प्र: किन फ़ॉर्मेट्स में मैं निकाली गई इमेज को एक्सपोर्ट कर सकता हूँ?**  
**उ:** API बैकग्राउंड इमेज एक्सपोर्ट के लिए PNG, JPEG, BMP, और GIF को सपोर्ट करता है।

## संसाधन

- **डॉक्यूमेंटेशन:** [GroupDocs डॉक्यूमेंटेशन](https://docs.groupdocs.com/watermark/java/)  
- **डॉक्यूमेंटेशन:** [GroupDocs Watermark डॉक्यूमेंटेशन](https://docs.groupdocs.com/watermark/java/)  
- **API रेफ़रेंस:** [GroupDocs Watermark API रेफ़रेंस](https://reference.groupdocs.com/watermark/java)  
- **डाउनलोड:** [GroupDocs डाउनलोड्स](https://releases.groupdocs.com/watermark/java/)  
- **GitHub रिपॉजिटरी:** [GroupDocs GitHub पेज](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)  
- **सपोर्ट फ़ोरम:** [GroupDocs सपोर्ट फ़ोरम](https://forum.groupdocs.com/c/watermark/10)

---

**अंतिम अपडेट:** 2026-09-11  
**परीक्षित संस्करण:** GroupDocs.Watermark 24.11 for Java  
**लेखक:** GroupDocs

## संबंधित ट्यूटोरियल्स

- [GroupDocs.Watermark Java API का उपयोग करके PowerPoint स्लाइड आयाम प्राप्त करने का तरीका](/watermark/java/presentation-document-watermarking/retrieve-slide-dimensions-powerpoint-groupdocs-watermark-java/)  
- [GroupDocs.Watermark लाइब्रेरी के साथ Java में PowerPoint स्लाइड बैकग्राउंड हटाएँ](/watermark/java/watermark-removal/remove-ppt-slide-background-groupdocs-watermark-java/)  
- [GroupDocs.Watermark for Java का उपयोग करके दस्तावेज़ जानकारी प्राप्त करने का चरण‑दर‑चरण गाइड](/watermark/java/document-information/retrieve-document-info-groupdocs-watermark-java/)