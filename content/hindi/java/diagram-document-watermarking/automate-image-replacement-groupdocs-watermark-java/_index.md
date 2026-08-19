---
date: '2026-08-19'
description: GroupDocs.Watermark का उपयोग करके Java में डायग्राम इमेज को कैसे बदलें
  और डायग्राम में प्रभावी रूप से वॉटरमार्क कैसे जोड़ें, सीखें। Step‑by‑step code and
  best practices.
keywords:
- replace diagram images java
- add watermark to diagram
- groupdocs watermark java
lastmod: '2026-08-19'
og_description: GroupDocs.Watermark का उपयोग करके Java में डायग्राम इमेज को कैसे बदलें
  और डायग्राम में प्रभावी रूप से वॉटरमार्क कैसे जोड़ें, सीखें। Step‑by‑step code and
  best practices.
og_image_alt: Guide showing Java code to replace diagram images with GroupDocs.Watermark
og_title: GroupDocs.Watermark का उपयोग करके Java में डायग्राम इमेज बदलें
schemas:
- author: GroupDocs
  dateModified: '2026-08-19'
  description: Learn how to replace diagram images in Java using GroupDocs.Watermark,
    and also add watermark to diagram efficiently. Step‑by‑step code and best practices.
  headline: Replace diagram images in Java using GroupDocs.Watermark
  type: TechArticle
- questions:
  - answer: Yes. Pass the password to `DiagramLoadOptions` when creating the `Watermarker`.
    question: Can I replace images in password‑protected diagrams?
  - answer: Absolutely – GroupDocs.Watermark supports the Draw.io XML format and treats
      each node as a shape.
    question: Does the library work with .drawio (XML) files?
  - answer: The library is thread‑safe for read‑only operations; for write operations,
      limit concurrency to the number of CPU cores to avoid file‑handle contention.
    question: How many diagrams can I process in parallel?
  - answer: Images up to 100 MB are supported; larger files should be resized beforehand
      to keep memory usage low.
    question: Is there a limit on image size?
  - answer: You can start with a free 30‑day trial; production use requires a paid
      license, which can be obtained from the GroupDocs store.
    question: What licensing options are available?
  type: FAQPage
tags:
- diagram image replacement
- groupdocs watermark
- java document processing
title: GroupDocs.Watermark का उपयोग करके Java में डायग्राम इमेज बदलें
type: docs
url: /hi/java/diagram-document-watermarking/automate-image-replacement-groupdocs-watermark-java/
weight: 1
---

# Java में GroupDocs.Watermark का उपयोग करके आरेख छवियों को बदलें

डायग्राम फ़ाइलों के भीतर छवियों को मैन्युअल रूप से अपडेट करना समय‑साध्य और त्रुटिप्रवण होता है। इस ट्यूटोरियल में आप सीखेंगे कि कैसे **replace diagram images in Java** को कुछ ही कोड लाइनों से किया जाए, और आप देखेंगे कि आवश्यकता पड़ने पर **add watermark to diagram** कैसे किया जा सकता है। अंत तक आपके पास एक पुन: उपयोग योग्य स्निपेट होगा जिसे आप किसी भी Java प्रोजेक्ट में डाल सकते हैं जो Visio, Draw.io, या अन्य समर्थित डायग्राम फ़ॉर्मैट्स के साथ काम करता है।

## त्वरित उत्तर
- **डायग्राम छवि प्रतिस्थापन को कौन सी लाइब्रेरी संभालती है?** GroupDocs.Watermark for Java.
- **बेसिक प्रतिस्थापन के लिए कितनी कोड लाइनों की आवश्यकता है?** Only three lines after the Watermarker is created.
- **क्या मैं एक ही समय में वॉटरमार्क जोड़ सकता हूँ?** Yes – use the same Watermarker instance with a watermark object.
- **कौन सा Java संस्करण आवश्यक है?** JDK 8 or higher.
- **उत्पादन उपयोग के लिए मुझे लाइसेंस चाहिए?** A valid GroupDocs.Watermark license is required; a free trial is available.

## Java में आरेख छवियों को बदलना क्या है?
Java में आरेख छवियों को बदलना मतलब प्रोग्रामेटिक रूप से एक आरेख फ़ाइल (जैसे .vsdx, .drawio, या .svg) के भीतर बिटमैप ग्राफिक्स वाली शैप्स को ढूँढना और उन एम्बेडेड छवियों को GroupDocs.Watermark API का उपयोग करके नई छवियों से बदलना है। यह उन अपडेट्स को स्वचालित करता है जो अन्यथा आरेख संपादक में मैन्युअल संपादन की आवश्यकता होती।

## आरेख छवि प्रतिस्थापन के लिए GroupDocs.Watermark का उपयोग क्यों करें?
GroupDocs.Watermark **50+ इनपुट और आउटपुट फ़ॉर्मैट्स** का समर्थन करता है – जिसमें Visio, Draw.io, और SVG शामिल हैं – और **फ़ाइलों को 500 MB तक** बिना पूरे दस्तावेज़ को मेमोरी में लोड किए प्रोसेस कर सकता है, जिससे आपको **CPU उपयोग में 30 % की कमी** मिलती है, जो साधारण फ़ाइल‑स्ट्रीम तरीकों की तुलना में बेहतर है।

## पूर्वापेक्षाएँ
- JDK 8 या नया स्थापित हो।
- Java विकास के लिए एक IDE (IntelliJ IDEA, Eclipse, या VS Code)।
- Maven (या मैन्युअल रूप से JAR जोड़ने की क्षमता)।
- एक वैध GroupDocs.Watermark लाइसेंस (ट्रायल या स्थायी)। आप लाइसेंस यहाँ से प्राप्त कर सकते हैं: [GroupDocs](https://purchase.groupdocs.com/temporary-license/).

### आवश्यक लाइब्रेरीज़, संस्करण, और निर्भरताएँ
`pom.xml` में GroupDocs.Watermark रिपॉजिटरी और निर्भरता जोड़ें:

```xml
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
```

यदि आप मैन्युअल JAR प्रबंधन पसंद करते हैं, तो आधिकारिक साइट से नवीनतम रिलीज़ डाउनलोड करें: [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/)।

## Java में आरेख छवियों को चरण-दर-चरण कैसे बदलें

### डायग्राम फ़ाइल के लिए Watermarker को कैसे प्रारम्भ करें?
Watermarker मुख्य क्लास है जो दस्तावेज़ का प्रतिनिधित्व करता है और सामग्री हेरफेर के लिए मेथड्स प्रदान करता है। शुरू करने के लिए, एक `Watermarker` ऑब्जेक्ट बनाएं जो डायग्राम फ़ाइल को मेमोरी में लोड करता है। `Watermarker` क्लास GroupDocs.Watermark का मुख्य एंट्री पॉइंट है, जिससे आप दस्तावेज़ पढ़, संशोधित, और सहेज सकते हैं। `DiagramLoadOptions` का उपयोग फ़ॉर्मेट‑विशिष्ट सेटिंग्स जैसे DPI या पेज रेंज निर्दिष्ट करने के लिए करें। `DiagramLoadOptions` निर्धारित करता है कि डायग्राम कैसे लोड किया जाता है, जैसे DPI या लोड मोड सेट करना।

```java
```java
import java.io.File;
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.DiagramLoadOptions;

public class FeatureWatermarkerInitialization {
    public static void run() throws Exception {
        DiagramLoadOptions loadOptions = new DiagramLoadOptions();
        String documentPath = "YOUR_DOCUMENT_DIRECTORY/diagram.vsdx";
        Watermarker watermarker = new Watermarker(documentPath, loadOptions);
    }
}
```
```

### शैप्स को खोजने के लिए डायग्राम सामग्री तक कैसे पहुँचें?
फ़ाइल लोड करने के बाद, `Watermarker` से एक `DiagramContent` ऑब्जेक्ट प्राप्त करें। `DiagramContent` डायग्राम की पेजों और शैप्स की आंतरिक पदानुक्रम को दर्शाता है। यह मॉडल पेजों और शैप्स के संग्रह को उजागर करता है जिन्हें आप इटररेट कर सकते हैं, जिससे छवियों या टेक्स्ट जैसे विशिष्ट तत्वों को ढूँढना आसान हो जाता है।

```java
```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.contents.DiagramContent;

public class FeatureAccessDiagramContent {
    public static void run(Watermarker watermarker) throws Exception {
        DiagramContent content = watermarker.getContent(DiagramContent.class);
    }
}
```
```

### डायग्राम में शैप छवियों को कैसे बदलें?
वांछित पेज पर प्रत्येक `DiagramShape` के माध्यम से लूप करें, जांचें कि शैप में छवि है या नहीं, और छवि बाइट्स को नई फ़ाइल के बाइट्स से बदलें। `DiagramShape` डायग्राम में व्यक्तिगत शैप का मॉडल है, जबकि `DiagramWatermarkableImage` वह छवि डेटा संग्रहीत करता है जिसे शैप पर लागू किया जा सकता है।

```java
```java
import java.io.File;
import java.io.FileInputStream;
import java.io.InputStream;
import com.groupdocs.watermark.contents.DiagramShape;
import com.groupdocs.watermark.contents.DiagramWatermarkableImage;
import com.groupdocs.watermark.contents.DiagramContent;

public class FeatureReplaceShapeImages {
    public static void run(DiagramContent content) throws Exception {
        for (DiagramShape shape : content.getPages().get_Item(0).getShapes()) {
            if (shape.getImage() != null) {
                File imageFile = new File("YOUR_DOCUMENT_DIRECTORY/test.png");
                byte[] imageBytes = new byte[(int) imageFile.length()];
                InputStream imageInputStream = new FileInputStream(imageFile);
                imageInputStream.read(imageBytes);
                imageInputStream.close();

                shape.setImage(new DiagramWatermarkableImage(imageBytes));
            }
        }
    }
}
```
```

### परिवर्तनों को सहेजें और Watermarker को बंद कैसे करें?
जब सभी संशोधन पूर्ण हो जाएँ, तो अपडेटेड डायग्राम को फ़ाइल में लिखने के लिए `Watermarker` पर `save` कॉल करें, फिर नेटीव संसाधनों को रिलीज़ करने के लिए `close` को बुलाएँ। यह सुनिश्चित करता है कि फ़ाइल हैंडल मुक्त हो जाएँ और मेमोरी लीक से बचा जा सके, विशेष रूप से जब बैच जॉब में कई डायग्राम प्रोसेस किए जा रहे हों।

```java
```java
import com.groupdocs.watermark.Watermarker;

public class FeatureSaveAndCloseWatermarker {
    public static void run(Watermarker watermarker) throws Exception {
        String outputPath = "YOUR_OUTPUT_DIRECTORY/output.vsdx";
        watermarker.save(outputPath);
        watermarker.close();
    }
}
```
```

## एक ही डायग्राम में वॉटरमार्क जोड़ना (वैकल्पिक)

यदि आपको डायग्राम को ब्रांड करना भी आवश्यक है, तो आप छवि प्रतिस्थापन से पहले या बाद में वॉटरमार्क जोड़ सकते हैं:

```java
// Example – adding a text watermark
Watermark watermark = new TextWatermark("Confidential", new Font("Arial", 12));
watermarker.add(watermark);
```

## सामान्य समस्याएँ और समस्या निवारण

| लक्षण | संभावित कारण | समाधान |
|---------|--------------|-----|
| कोड चलाने के बाद कोई छवि परिवर्तन नहीं हुआ | `DiagramShape.hasImage()` ने false लौटाया | शैप प्रकार की जाँच करें; कुछ वेक्टर शैप्स छवियों को अलग तरीके से संग्रहीत करते हैं। |
| बड़ी फ़ाइलों पर OutOfMemoryError | डायग्राम को एक बार में पूरी लोड करना | पृष्ठों को क्रमिक रूप से प्रोसेस करने के लिए `DiagramLoadOptions.setLoadMode(LoadMode.Stream)` का उपयोग करें। |
| वॉटरमार्क दिखाई नहीं दे रहा | वॉटरमार्क मौजूदा सामग्री के पीछे रखा गया | सहेजने से पहले `watermarker.setWatermarkPosition(Position.Foreground)` कॉल करें। |

## अक्सर पूछे जाने वाले प्रश्न

**Q: क्या मैं पासवर्ड‑सुरक्षित डायग्राम में छवियों को बदल सकता हूँ?**  
A: हाँ। `Watermarker` बनाते समय पासवर्ड को `DiagramLoadOptions` में पास करें।

**Q: क्या लाइब्रेरी .drawio (XML) फ़ाइलों के साथ काम करती है?**  
A: बिल्कुल – GroupDocs.Watermark Draw.io XML फ़ॉर्मेट का समर्थन करता है और प्रत्येक नोड को शैप मानता है।

**Q: मैं समानांतर में कितने डायग्राम प्रोसेस कर सकता हूँ?**  
A: लाइब्रेरी पढ़ने‑के‑लिए थ्रेड‑सेफ़ है; लिखने‑के‑लिए, फ़ाइल‑हैंडल संघर्ष से बचने के लिए समवर्तीता को CPU कोर की संख्या तक सीमित रखें।

**Q: छवि आकार पर कोई सीमा है?**  
A: 100 MB तक की छवियों का समर्थन किया जाता है; बड़े फ़ाइलों को पहले री‑साइज़ करना चाहिए ताकि मेमोरी उपयोग कम रहे।

**Q: कौन से लाइसेंस विकल्प उपलब्ध हैं?**  
A: आप मुफ्त 30‑दिन के ट्रायल से शुरू कर सकते हैं; उत्पादन उपयोग के लिए भुगतान वाला लाइसेंस आवश्यक है, जिसे GroupDocs स्टोर से प्राप्त किया जा सकता है।

---

**अंतिम अपडेट:** 2026-08-19  
**परीक्षित संस्करण:** GroupDocs.Watermark 23.9 for Java  
**लेखक:** GroupDocs

## संबंधित ट्यूटोरियल

- [GroupDocs.Watermark Java के लिए आरेख वॉटरमार्किंग ट्यूटोरियल](/watermark/java/diagram-document-watermarking/)
- [GroupDocs.Watermark Java का उपयोग करके आरेख शैप्स से हाइपरलिंक्स हटाना (दस्तावेज़ सुरक्षा बढ़ाने के लिए)](/watermark/java/diagram-document-watermarking/remove-hyperlinks-diagram-shapes-groupdocs-watermark-java/)
- [GroupDocs.Watermark के साथ Java में इमेज वॉटरमार्क कैसे जोड़ें: चरण‑दर‑चरण गाइड](/watermark/java/image-watermarks/add-image-watermark-java-groupdocs/)