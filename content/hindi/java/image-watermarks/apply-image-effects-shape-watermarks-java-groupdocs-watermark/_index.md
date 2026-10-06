---
date: '2026-08-04'
description: GroupDocs का उपयोग करके Java प्रस्तुतियों में shape watermarks पर image
  effects—brightness, contrast, chroma key, borders—जोड़ना सीखें, GroupDocs.Watermark
  के साथ।
keywords:
- how to use groupdocs
- apply image effects to shape watermarks in java
- groupdocs watermark java
lastmod: '2026-08-04'
og_description: GroupDocs का उपयोग करके Java प्रस्तुतियों में shape watermarks पर
  brightness, contrast, chroma key और border effects जोड़ने का तरीका जानें। डेवलपर्स
  के लिए चरण‑दर‑चरण गाइड।
og_image_alt: Guide showing GroupDocs.Watermark Java code for applying image effects
  to shape watermarks
og_title: GroupDocs का उपयोग कैसे करें – Java में shape watermarks पर image effects
  लागू करें
schemas:
- author: GroupDocs
  dateModified: '2026-08-04'
  description: Learn how to use GroupDocs to add image effects—brightness, contrast,
    chroma key, borders—to shape watermarks in Java presentations with GroupDocs.Watermark.
  headline: How to use GroupDocs to apply image effects to shape watermarks in Java
  type: TechArticle
- description: Learn how to use GroupDocs to add image effects—brightness, contrast,
    chroma key, borders—to shape watermarks in Java presentations with GroupDocs.Watermark.
  name: How to use GroupDocs to apply image effects to shape watermarks in Java
  steps:
  - name: load the presentation file
    text: The `Watermarker` class is the entry point for all watermark operations
      on a document.
  - name: create an image watermark instance
    text: The `ImageWatermark` class represents a raster image (e.g., a logo) that
      can be placed onto a shape as a watermark.
  - name: configure image effects
    text: The `PresentationImageEffects` class lets you modify brightness, contrast,
      chroma‑key transparency, and border settings for image watermarks in presentations.
  - name: add the configured watermark to the presentation
    text: The `PresentationWatermarkOptions` class specifies where and how a watermark
      is applied, such as target slides and positioning.
  - name: save the modified presentation and release resources
    text: Always close the `Watermarker` to free file handles and memory buffers.
  type: HowTo
- questions:
  - answer: Call `setOpacity(double opacity)` on the `PresentationImageEffects` object;
      values range from 0.0 (fully transparent) to 1.0 (fully opaque).
    question: How do I adjust the transparency of an image watermark?
  - answer: Yes. Use `PresentationWatermarkOptions.setSlideIndices(int... indices)`
      to target individual slide numbers.
    question: Can I apply watermarks to specific slides only?
  - answer: PNG, JPEG, BMP, GIF, TIFF, and WebP are all supported, giving you flexibility
      for logos and graphics.
    question: What image formats are supported for watermarking?
  - answer: Wrap the workflow in a try‑catch block and catch `WatermarkException`
      to obtain detailed error codes and messages.
    question: How should I handle errors during watermark processing?
  - answer: Absolutely. Iterate over a collection of file paths, instantiate a `Watermarker`
      for each, and apply the same watermark configuration.
    question: Is batch processing of many presentations possible?
  type: FAQPage
tags:
- groupdocs watermark
- java image effects
- shape watermarks
- presentation security
title: GroupDocs का उपयोग करके Java में shape watermarks पर image effects लागू करने
  का तरीका
type: docs
url: /hi/java/image-watermarks/apply-image-effects-shape-watermarks-java-groupdocs-watermark/
weight: 1
---

# GroupDocs का उपयोग करके जावा में आकार वॉटरमार्क पर इमेज इफ़ेक्ट्स कैसे लागू करें

अपनी प्रेज़ेंटेशन फ़ाइलों की सुरक्षा किसी भी पेशेवर के लिए शीर्ष प्राथमिकता है जो स्लाइड्स को सार्वजनिक या आंतरिक रूप से साझा करता है। **GroupDocs का उपयोग कैसे करें** इमेज इफ़ेक्ट्स—जैसे ब्राइटनेस, कॉन्ट्रास्ट, क्रोमा‑की ट्रांसपेरेंसी, और कस्टम बॉर्डर—जोड़ने से आपको वॉटरमार्क की दिखावट पर सूक्ष्म नियंत्रण मिलता है जबकि मूल सामग्री अपरिवर्तित रहती है। इस ट्यूटोरियल में आप पूरी वर्कफ़्लो सीखेंगे, प्रोजेक्ट सेटअप से लेकर अंतिम फ़ाइल को सहेजने तक, और आप देखेंगे कि GroupDocs.Watermark इस कार्य के लिए सबसे फीचर‑रिच लाइब्रेरी क्यों है।

## त्वरित उत्तर
- **कौन सी लाइब्रेरी वॉटरमार्क पर इमेज इफ़ेक्ट्स जोड़ती है?** GroupDocs.Watermark for Java.  
- **क्या मैं ब्राइटनेस और कॉन्ट्रास्ट एक साथ बदल सकता हूँ?** Yes, via `PresentationImageEffects`.  
- **क्या बॉर्डर वैकल्पिक है?** You can enable or disable it with `setBorderColor` and `setBorderWidth`.  
- **क्या उत्पादन के लिए लाइसेंस चाहिए?** A valid GroupDocs license is required for unrestricted use.  
- **कौन से फ़ाइल फ़ॉर्मेट समर्थित हैं?** Over 50 formats, including PPTX, PPT, and PDF.

## GroupDocs.Watermark for Java क्या है?
GroupDocs.Watermark for Java एक व्यापक लाइब्रेरी है जो डेवलपर्स को 50 से अधिक दस्तावेज़ और इमेज फ़ॉर्मेट पर वॉटरमार्क जोड़ने, संपादित करने और हटाने की सुविधा देती है। यह पूरी तरह से सर्वर साइड पर चलता है, तृतीय‑पक्ष एप्लिकेशन की आवश्यकता को समाप्त करता है, और सूक्ष्म दृश्य अनुकूलन, बैच प्रोसेसिंग, और हाई‑परफ़ॉर्मेंस स्ट्रीमिंग के लिए समृद्ध API प्रदान करता है।

## आकार वॉटरमार्क पर इमेज इफ़ेक्ट्स क्यों उपयोग करें?
इमेज इफ़ेक्ट्स लागू करने से आप वॉटरमार्क के दृश्य प्रभाव को पढ़ने की क्षमता को नुकसान पहुंचाए बिना अनुकूलित कर सकते हैं। ब्राइटनेस या कॉन्ट्रास्ट को समायोजित करने से लोगो स्लाइड बैकग्राउंड के साथ सूक्ष्मता से मिश्रित हो सकता है, जबकि क्रोमा‑की ट्रांसपेरेंसी अनचाहे रंगों को हटा देती है। बॉर्डर जोड़ने से एक स्पष्ट दृश्य सीमा बनती है, जो ब्रांड पहचान को मजबूत करती है और वॉटरमार्क को हटाना या अनदेखा करना कठिन बनाती है।

## पूर्वापेक्षाएँ
- **GroupDocs.Watermark for Java** — Version 24.11 or later.  
- Java Development Kit 8 or newer.  
- IntelliJ IDEA या Eclipse जैसे IDE.  
- बुनियादी Java प्रोग्रामिंग ज्ञान और प्रेज़ेंटेशन (PPTX) फ़ाइलों की परिचितता।

## GroupDocs.Watermark for Java को कैसे सेट अप करें
लाइब्रेरी को अपने Maven प्रोजेक्ट में लोड करें और किसी भी API कॉल से पहले लाइसेंस उपलब्ध हो, यह सुनिश्चित करें।

**Maven कॉन्फ़िगरेशन**  
`pom.xml` में निम्नलिखित डिपेंडेंसी जोड़ें:

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

**डायरेक्ट डाउनलोड**  
आप आधिकारिक रिलीज़ पेज से JAR भी डाउनलोड कर सकते हैं: [GroupDocs.Watermark for Java रिलीज़](https://releases.groupdocs.com/watermark/java/).

### लाइसेंस प्राप्ति
मूल्यांकन के लिए एक मुफ्त ट्रायल उपलब्ध है। उत्पादन उपयोग के लिए, अस्थायी लाइसेंस का अनुरोध करें या GroupDocs पोर्टल से पूर्ण लाइसेंस खरीदें।

## प्रेज़ेंटेशन में आकार वॉटरमार्क पर इमेज इफ़ेक्ट्स कैसे लागू करें
अपनी प्रेज़ेंटेशन लोड करें, एक इमेज वॉटरमार्क बनाएं, इच्छित इफ़ेक्ट्स कॉन्फ़िगर करें, और परिणाम सहेजें। नीचे दिए गए चरण आपको एक संक्षिप्त, अंत‑से‑अंत समाधान देते हैं, और प्रत्येक चरण में एक छोटा कोड उदाहरण शामिल है जिसे आप सीधे अपने प्रोजेक्ट में कॉपी कर सकते हैं।

### चरण 1: प्रेज़ेंटेशन फ़ाइल लोड करें
`Watermarker` क्लास दस्तावेज़ पर सभी वॉटरमार्क ऑपरेशन्स के लिए एंट्री पॉइंट है।

```java
PresentationLoadOptions loadOptions = new PresentationLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/presentation.pptx", loadOptions);
```

### चरण 2: इमेज वॉटरमार्क इंस्टेंस बनाएं
`ImageWatermark` क्लास एक रास्टर इमेज (जैसे, लोगो) को दर्शाता है जिसे आकार पर वॉटरमार्क के रूप में रखा जा सकता है।

```java
PresentationLoadOptions loadOptions = new PresentationLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/presentation.pptx", loadOptions);
```

### चरण 3: इमेज इफ़ेक्ट्स कॉन्फ़िगर करें
`PresentationImageEffects` क्लास आपको प्रेज़ेंटेशन में इमेज वॉटरमार्क के लिए ब्राइटनेस, कॉन्ट्रास्ट, क्रोमा‑की ट्रांसपेरेंसी, और बॉर्डर सेटिंग्स को संशोधित करने की अनुमति देता है।

```java
ImageWatermark watermark = new ImageWatermark("YOUR_DOCUMENT_DIRECTORY/logo.png");
```

### चरण 4: कॉन्फ़िगर किया गया वॉटरमार्क प्रेज़ेंटेशन में जोड़ें
`PresentationWatermarkOptions` क्लास यह निर्दिष्ट करती है कि वॉटरमार्क कहाँ और कैसे लागू किया जाए, जैसे लक्ष्य स्लाइड्स और पोजिशनिंग।

```java
PresentationImageEffects effects = new PresentationImageEffects();
effects.setBrightness(0.7); // Set brightness to 70% of original.
effects.setContrast(0.6);   // Set contrast to 60% of original.
effects.setChromaKey(Color.getRed()); // Apply chroma key using the color red for transparency.

// Enable and configure border line settings
effects.getBorderLineFormat().setEnabled(true);
effects.getBorderLineFormat().setWeight(1); // Set border weight to 1.
```

### चरण 5: संशोधित प्रेज़ेंटेशन सहेजें और संसाधन रिलीज़ करें
फ़ाइल हैंडल और मेमोरी बफ़र्स को मुक्त करने के लिए हमेशा `Watermarker` को बंद करें।

```java
PresentationWatermarkSlideOptions options = new PresentationWatermarkSlideOptions();
options.setEffects(effects);

watermarker.add(watermark, options);
```

## सामान्य समस्याएँ और ट्रबलशूटिंग
- **गलत फ़ाइल पाथ** – `System.getProperty("user.dir")` के विरुद्ध एब्सोल्यूट पाथ या रिलेटिव पाथ को रिजॉल्व करें।  
- **असमर्थित इमेज फ़ॉर्मेट** – सुनिश्चित करें कि इमेज PNG, JPEG, BMP, या कोई अन्य समर्थित प्रकार है।  
- **लाइसेंस लोड नहीं हुआ** – लाइसेंस फ़ाइल को क्लासपाथ में रखें और किसी भी API कॉल से पहले इनिशियलाइज़ करें।  
- **बड़ी प्रेज़ेंटेशन** – मेमोरी उपयोग कम रखने के लिए स्ट्रीमिंग मोड (`Watermarker.setStreaming(true)`) सक्षम करें।

## व्यावहारिक अनुप्रयोग
1. **ब्रांड सुरक्षा** – कस्टम ब्राइटनेस के साथ अर्द्ध‑पारदर्शी कॉर्पोरेट लोगो एम्बेड करें जिससे कॉपी करना अप्रिय हो।  
2. **शैक्षिक सामग्री** – लेक्चर स्लाइड्स पर विश्वविद्यालय सील वॉटरमार्क लगाएँ जो क्रोमा‑की इफ़ेक्ट का उपयोग करके स्लाइड बैकग्राउंड के साथ मिश्रित हो।  
3. **कॉरपोरेट रिपोर्टिंग** – गोपनीय वित्तीय डेक्स में बॉर्डर वाला वॉटरमार्क जोड़ें, जिससे बॉर्डर रंग कॉरपोरेट ब्रांडिंग गाइडलाइन से मेल खाता हो।

## प्रदर्शन टिप्स
- थ्रेड‑पूल एक्ज़ीक्यूटर का उपयोग करके बैच में प्रेज़ेंटेशन प्रोसेस करें ताकि CPU उपयोग अधिकतम हो।  
- जब संभव हो तो कई फ़ाइलों के लिए वही `Watermarker` इंस्टेंस पुनः उपयोग करें; केवल तब वॉटरमार्क ऑब्जेक्ट को री‑इनिशियलाइज़ करें जब विज़ुअल स्टाइल बदलता हो।  
- VisualVM जैसे टूल्स से JVM हीप मॉनिटर करें ताकि किसी भी अनपेक्षित मेमोरी स्पाइक का पता चल सके।

## अक्सर पूछे जाने वाले प्रश्न

**प्र: इमेज वॉटरमार्क की ट्रांसपेरेंसी कैसे समायोजित करूँ?**  
उ: `PresentationImageEffects` ऑब्जेक्ट पर `setOpacity(double opacity)` कॉल करें; मान 0.0 (पूरी तरह से पारदर्शी) से 1.0 (पूरी तरह से अपारदर्शी) तक होते हैं।

**प्र: क्या मैं केवल विशिष्ट स्लाइड्स पर वॉटरमार्क लागू कर सकता हूँ?**  
उ: हाँ। व्यक्तिगत स्लाइड नंबरों को लक्षित करने के लिए `PresentationWatermarkOptions.setSlideIndices(int... indices)` का उपयोग करें।

**प्र: वॉटरमार्किंग के लिए कौन से इमेज फ़ॉर्मेट समर्थित हैं?**  
उ: PNG, JPEG, BMP, GIF, TIFF, और WebP सभी समर्थित हैं, जिससे आपको लोगो और ग्राफ़िक्स के लिए लचीलापन मिलता है।

**प्र: वॉटरमार्क प्रोसेसिंग के दौरान त्रुटियों को कैसे संभालूँ?**  
उ: वर्कफ़्लो को try‑catch ब्लॉक में रैप करें और विस्तृत त्रुटि कोड और संदेश प्राप्त करने के लिए `WatermarkException` को कैच करें।

**प्र: कई प्रेज़ेंटेशन की बैच प्रोसेसिंग संभव है?**  
उ: बिल्कुल। फ़ाइल पाथ्स के संग्रह पर इटरेट करें, प्रत्येक के लिए `Watermarker` इंस्टैंसिएट करें, और समान वॉटरमार्क कॉन्फ़िगरेशन लागू करें।

## अतिरिक्त संसाधन
- [डॉक्यूमेंटेशन](https://docs.groupdocs.com/watermark/java/)  
- [API रेफ़रेंस](https://reference.groupdocs.com/watermark/java)  
- [GroupDocs.Watermark for Java डाउनलोड करें](https://releases.groupdocs.com/watermark/java/)  
- [GitHub रिपॉज़िटरी](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)  
- [फ़्री सपोर्ट फ़ोरम](https://forum.groupdocs.com/c/watermark/10)  
- [अस्थायी लाइसेंस का अनुरोध करें](https://purchase.groupdocs.com/temporary-license/)

**अंतिम अपडेट:** 2026-08-04  
**परीक्षण किया गया:** GroupDocs.Watermark 24.11 for Java  
**लेखक:** GroupDocs

```java
watermarker.save("YOUR_OUTPUT_DIRECTORY/out_presentation.pptx");
watermarker.close();
```

## संबंधित ट्यूटोरियल

- [GroupDocs.Watermark का उपयोग करके जावा में पावरपॉइंट प्रेज़ेंटेशन के लिए आकार वॉटरमार्क कैसे जोड़ें](/watermark/java/presentation-document-watermarking/groupdocs-watermark-java-add-shape-watermark-ppt/)
- [GroupDocs.Watermark और जावा का उपयोग करके पावरपॉइंट में लाइन इफ़ेक्ट्स वॉटरमार्क कैसे जोड़ें](/watermark/java/presentation-document-watermarking/add-line-effects-watermarks-powerpoint-java-groupdocs/)
- [GroupDocs.Watermark for Java का उपयोग करके पावरपॉइंट प्रेज़ेंटेशन में वॉटरमार्क कैसे जोड़ें](/watermark/java/presentation-document-watermarking/groupdocs-watermark-java-add-powerpoint-watermarks/)