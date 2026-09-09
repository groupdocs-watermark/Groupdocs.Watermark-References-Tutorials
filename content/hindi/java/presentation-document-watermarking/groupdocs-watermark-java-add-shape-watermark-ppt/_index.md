---
date: '2026-05-27'
description: GroupDocs का उपयोग करके Java के साथ PPT फ़ाइलों में आकार वॉटरमार्क जोड़ना
  सीखें। चरण-दर-चरण गाइड, कॉन्फ़िगरेशन टिप्स, और प्रदर्शन अंतर्दृष्टि।
keywords:
- how to use groupdocs
- java add watermark ppt
- GroupDocs.Watermark
schemas:
- author: GroupDocs
  dateModified: '2026-05-27'
  description: Learn how to use GroupDocs to add shape watermarks to PPT files with
    Java. Step-by-step guide, configuration tips, and performance insights.
  headline: How to Use GroupDocs to Add Shape Watermarks in Java for PowerPoint Presentations
  type: TechArticle
- description: Learn how to use GroupDocs to add shape watermarks to PPT files with
    Java. Step-by-step guide, configuration tips, and performance insights.
  name: How to Use GroupDocs to Add Shape Watermarks in Java for PowerPoint Presentations
  steps:
  - name: Create a Shape Watermark
    text: '`ShapeWatermarkOptions` defines visual properties of a shape watermark,
      including size, color, opacity, and rotation.'
  - name: Apply the Watermark to All Slides
    text: Iterate through each slide in the presentation and add the shape watermark.
  - name: Save the Watermarked Presentation
    text: Choose the output format (PPTX) and save the file. The SDK preserves original
      slide content and animations.
  type: HowTo
- questions:
  - answer: Yes – call `watermarker.add()` multiple times with different `ShapeWatermarkOptions`
      for each watermark.
    question: Can I add multiple watermarks to the same slide?
  - answer: Absolutely. Provide the password in `PresentationLoadOptions.setPassword("yourPassword")`
      before loading.
    question: Does GroupDocs.Watermark support password‑protected PPTX files?
  - answer: Yes – specify the slide indices in the `add` method instead of iterating
      over all slides.
    question: Is it possible to watermark only selected slides?
  - answer: The SDK works with Java 8 through Java 21, covering both legacy and modern
      environments.
    question: What Java versions are compatible?
  - answer: Shape watermarks are static by design; they do not interfere with existing
      animations on the slide.
    question: How does the library handle animated shapes?
  type: FAQPage
title: GroupDocs का उपयोग करके Java में PowerPoint प्रस्तुतियों के लिए आकार वॉटरमार्क
  कैसे जोड़ें
type: docs
url: /hi/java/presentation-document-watermarking/groupdocs-watermark-java-add-shape-watermark-ppt/
weight: 1
---

# GroupDocs का उपयोग करके जावा में PowerPoint प्रस्तुतियों में आकार वॉटरमार्क जोड़ने का तरीका

अपने PowerPoint डेक को सुरक्षित रखना ब्रांड की निरंतरता और डेटा सुरक्षा के लिए आवश्यक है। इस ट्यूटोरियल में आप **GroupDocs का उपयोग कैसे करें** यह जानेंगे, जिससे आप जावा के साथ PPTX फ़ाइलों में सीधे आकार वॉटरमार्क एम्बेड कर सकते हैं, जो हर स्लाइड को ब्रांड करने का एक विश्वसनीय, प्रोग्रामेटिक तरीका प्रदान करता है।

## त्वरित उत्तर
- **Java में PPTX में वॉटरमार्क जोड़ने वाली लाइब्रेरी कौन सी है?** GroupDocs.Watermark.
- **कौन सा क्लास प्रस्तुति लोड करता है?** `PresentationLoadOptions`.
- **कौन सा क्लास वॉटरमार्क लागू करता है?** `Watermarker`.
- **क्या विकास के लिए लाइसेंस की आवश्यकता है?** परीक्षण के लिए एक मुफ्त ट्रायल काम करता है; उत्पादन के लिए एक भुगतान लाइसेंस आवश्यक है।
- **क्या मैं बड़े फ़ाइलों (>500 MB) पर वॉटरमार्क लगा सकता हूँ?** हाँ – GroupDocs 2 GB तक की फ़ाइलों को पूरी दस्तावेज़ को मेमोरी में लोड किए बिना प्रोसेस करता है।

## GroupDocs.Watermark क्या है?
`GroupDocs.Watermark` एक Java SDK है जो आपको PPT, PPTX, PDF, और DOCX सहित 100 से अधिक दस्तावेज़ फ़ॉर्मैट्स में टेक्स्ट, इमेज, या आकार वॉटरमार्क जोड़ने की सुविधा देता है। यह 2 GB तक की फ़ाइलों को प्रोसेस करता है जबकि मेमोरी उपयोग कम रखता है। लाइब्रेरी अपारदर्शिता, घूर्णन, और स्थिति को अनुकूलित करने के लिए API भी प्रदान करती है, जिससे वॉटरमार्क मौजूदा स्लाइड लेआउट्स के साथ सहजता से एकीकृत हो जाता है।

## PowerPoint प्रस्तुतियों में आकार वॉटरमार्क क्यों जोड़ें?
आकार वॉटरमार्क स्लाइड्स में दृश्य निरंतरता बनाए रखते हैं और वेक्टर निर्देशांक का उपयोग करके सटीक रूप से स्थित किए जा सकते हैं, जिससे आप ब्रांडिंग तत्वों को ठीक वहीँ संरेखित कर सकते हैं जहाँ आवश्यकता हो। वे मूल PowerPoint आकारों के रूप में संपादन योग्य रहते हैं, जिससे प्रस्तुति में बाद के किसी भी संपादन से वॉटरमार्क की उपस्थिति और स्थान बना रहता है। मात्रात्मक लाभ शामिल हैं:
- **50+** वॉटरमार्क शैलियाँ (टेक्स्ट, इमेज, आकार) समर्थित।
- **100 %** लेआउट सटीकता – संपादन के बाद भी आकार संरेखित रहते हैं।
- **2 GB** तक की फ़ाइल आकार संभालना बिना पूरे दस्तावेज़ को लोड किए, जिससे साधारण तरीकों की तुलना में मेमोरी खपत **70 %** तक कम हो जाती है।

## पूर्वापेक्षाएँ
- **Java Development Kit (JDK) 8+** स्थापित है।
- **Maven** निर्भरता प्रबंधन के लिए।
- **IntelliJ IDEA** या **Eclipse** जैसे IDE।
- बुनियादी Java ज्ञान और Maven से परिचितता।
- **GroupDocs.Watermark** लाइसेंस (ट्रायल या व्यावसायिक) तक पहुँच।

### आवश्यक लाइब्रेरी और संस्करण
- **GroupDocs.Watermark for Java** संस्करण **24.11** या बाद का।

### पर्यावरण सेटअप आवश्यकताएँ
- सुनिश्चित करें कि `JAVA_HOME` आपके JDK की ओर इशारा करता है।
- नीचे दिखाए अनुसार अपने प्रोजेक्ट के `pom.xml` को कॉन्फ़िगर करें।

## GroupDocs.Watermark का उपयोग करके जावा में PowerPoint फ़ाइल में आकार वॉटरमार्क कैसे जोड़ें?
`PresentationLoadOptions` PowerPoint फ़ाइलों को लोड करने के विकल्प निर्दिष्ट करता है, जैसे स्लाइड चयन और पासवर्ड हैंडलिंग।  
`Watermarker` वह मुख्य क्लास है जो दस्तावेज़ को लोड करता है और वॉटरमार्क लागू करता है।  

`PresentationLoadOptions` के साथ प्रस्तुति लोड करें, एक `Watermarker` इंस्टेंस बनाएं, एक आकार वॉटरमार्क परिभाषित करें, इसे प्रत्येक स्लाइड पर लागू करें, और अंत में फ़ाइल सहेजें। यह एंड‑टू‑एंड प्रवाह केवल कुछ कोड लाइनों की आवश्यकता रखता है और सामान्य 10‑स्लाइड डेक के लिए एक सेकंड से कम समय में चलता है।

### Maven कॉन्फ़िगरेशन
अपने `pom.xml` फ़ाइल में निम्नलिखित निर्भरता जोड़ें:

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

### प्रत्यक्ष डाउनलोड
वैकल्पिक रूप से, नवीनतम संस्करण यहाँ से डाउनलोड करें: [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/)।

### लाइसेंस प्राप्ति
GroupDocs.Watermark की सभी सुविधाओं को खोजने के लिए एक मुफ्त ट्रायल या अस्थायी लाइसेंस प्राप्त करें। उत्पादन उपयोग के लिए, अपने डिप्लॉयमेंट स्केल के अनुसार लाइसेंस खरीदें।

#### बुनियादी प्रारंभिककरण और सेटअप
`Watermarker` वह मुख्य क्लास है जो दस्तावेज़ को लोड करता है और वॉटरमार्क लागू करता है।  
`PresentationLoadOptions` PowerPoint फ़ाइलों को लोड करने के विकल्प प्रदान करता है, जैसे स्लाइड हैंडलिंग और एनीमेशन संरक्षण।

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.PresentationLoadOptions;

PresentationLoadOptions loadOptions = new PresentationLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/presentation.pptx\
```

#### चरण 1: आकार वॉटरमार्क बनाएं
`ShapeWatermarkOptions` आकार वॉटरमार्क की दृश्य गुणों को परिभाषित करता है, जिसमें आकार, रंग, अपारदर्शिता, और घूर्णन शामिल हैं।

```java
import com.groupdocs.watermark.watermarkoptions.ShapeWatermarkOptions;
import com.groupdocs.watermark.contents.Shape;

// Create a rectangle shape
Shape shape = new Shape(Shape.ShapeType.Rectangle);
shape.setWidth(200);
shape.setHeight(100);
shape.setColor(Color.BLUE);
shape.setOpacity(0.3);

// Configure watermark options
ShapeWatermarkOptions options = new ShapeWatermarkOptions(shape);
options.setHorizontalAlignment(HorizontalAlignment.Center);
options.setVerticalAlignment(VerticalAlignment.Center);
```

#### चरण 2: सभी स्लाइड्स पर वॉटरमार्क लागू करें
प्रस्तुति की प्रत्येक स्लाइड पर इटररेट करें और आकार वॉटरमार्क जोड़ें।

```java
for (int i = 0; i < watermarker.getDocument().getPages().size(); i++) {
    watermarker.add(options, i); // i = slide index
}
```

#### चरण 3: वॉटरमार्क वाली प्रस्तुति सहेजें
आउटपुट फ़ॉर्मेट (PPTX) चुनें और फ़ाइल सहेजें। SDK मूल स्लाइड सामग्री और एनीमेशन को संरक्षित रखता है।

```java
watermarker.save("OUTPUT_DIRECTORY/presentation_watermarked.pptx", SaveFormat.Pptx);
```

### सामान्य समस्याएँ और समाधान
- **लाइसेंस नहीं मिलने की त्रुटि:** सुनिश्चित करें कि लाइसेंस फ़ाइल क्लासपाथ में रखी गई है या `License.setLicense("path/to/license.lic")` के माध्यम से सेट की गई है।  
`License` क्लास GroupDocs लाइसेंस फ़ाइल को लोड और लागू करता है ताकि पूर्ण SDK कार्यक्षमता सक्षम हो सके।
- **आकार दिखाई नहीं दे रहा:** आकार की अपारदर्शिता या रंग कंट्रास्ट बढ़ाएँ; डिफ़ॉल्ट अपारदर्शिता 0.2 है।
- **बड़ी फ़ाइल में धीमी गति:** स्लाइड्स को आवश्यकता अनुसार लोड करने के लिए `PresentationLoadOptions.setLoadAllSlides(false)` का उपयोग करें, जिससे मेमोरी उपयोग कम हो जाता है।

## अक्सर पूछे जाने वाले प्रश्न

**प्रश्न:** क्या मैं एक ही स्लाइड में कई वॉटरमार्क जोड़ सकता हूँ?  
**उत्तर:** हाँ – प्रत्येक वॉटरमार्क के लिए अलग `ShapeWatermarkOptions` के साथ `watermarker.add()` को कई बार कॉल करें।

**प्रश्न:** क्या GroupDocs.Watermark पासवर्ड‑सुरक्षित PPTX फ़ाइलों का समर्थन करता है?  
**उत्तर:** बिल्कुल। लोड करने से पहले `PresentationLoadOptions.setPassword("yourPassword")` में पासवर्ड प्रदान करें।

**प्रश्न:** क्या केवल चयनित स्लाइड्स पर वॉटरमार्क लगाना संभव है?  
**उत्तर:** हाँ – सभी स्लाइड्स पर इटररेट करने के बजाय `add` मेथड में स्लाइड इंडेक्स निर्दिष्ट करें।

**प्रश्न:** कौन से Java संस्करण संगत हैं?  
**उत्तर:** SDK Java 8 से लेकर Java 21 तक काम करता है, जो दोनों लेगेसी और आधुनिक वातावरण को कवर करता है।

**प्रश्न:** लाइब्रेरी एनीमेटेड आकारों को कैसे संभालती है?  
**उत्तर:** आकार वॉटरमार्क डिज़ाइन के अनुसार स्थैतिक होते हैं; वे स्लाइड पर मौजूदा एनीमेशन में हस्तक्षेप नहीं करते।

---

**अंतिम अपडेट:** 2026-05-27  
**परीक्षण किया गया:** GroupDocs.Watermark 24.11 for Java  
**लेखक:** GroupDocs

## संबंधित ट्यूटोरियल

- [GroupDocs.Watermark for Java का उपयोग करके PowerPoint प्रस्तुतियों में वॉटरमार्क जोड़ें](/watermark/java/presentation-document-watermarking/groupdocs-watermark-java-add-powerpoint-watermarks/)
- [GroupDocs.Watermark for Java का उपयोग करके PowerPoint इमेजेज में टेक्स्ट वॉटरमार्क कैसे जोड़ें](/watermark/java/presentation-document-watermarking/add-text-watermarks-presentation-images-groupdocs-watermark-java/)
- [GroupDocs.Watermark और Java का उपयोग करके PowerPoint में लाइन इफ़ेक्ट वॉटरमार्क कैसे जोड़ें](/watermark/java/presentation-document-watermarking/add-line-effects-watermarks-powerpoint-java-groupdocs/)