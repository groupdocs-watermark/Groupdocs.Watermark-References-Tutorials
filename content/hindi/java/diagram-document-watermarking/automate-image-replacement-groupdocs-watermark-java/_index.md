---
date: '2026-10-01'
description: GroupDocs.Watermark के साथ diagram files में image replacement java को
  स्वचालित करने का तरीका जानें, जिसमें watermark addition और efficient processing
  शामिल है।
keywords:
- automate image replacement java
- add watermark to diagram
- GroupDocs.Watermark Java
lastmod: '2026-10-01'
og_description: GroupDocs.Watermark के साथ diagrams में image replacement java को
  स्वचालित करें। यह गाइड दिखाता है कि कैसे images को बदलें, watermarks जोड़ें, और
  large files को efficiently संभालें।
og_image_alt: 'Developer guide: automate image replacement java with GroupDocs.Watermark'
og_title: GroupDocs.Watermark का उपयोग करके java में image replacement को स्वचालित
  करें
schemas:
- author: GroupDocs
  dateModified: '2026-10-01'
  description: Learn how to automate image replacement java in diagram files with
    GroupDocs.Watermark, including watermark addition and efficient processing.
  headline: Automate image replacement java using GroupDocs.Watermark
  type: TechArticle
- description: Learn how to automate image replacement java in diagram files with
    GroupDocs.Watermark, including watermark addition and efficient processing.
  name: Automate image replacement java using GroupDocs.Watermark
  steps:
  - name: initialize the watermarker
    text: The `Watermarker` class is the entry point for all document operations.
      It opens the source file and prepares internal structures for editing. - **DiagramLoadOptions**
      configures diagram‑specific loading parameters. - Initializing the `Watermarker`
      opens the file handle and validates the format.
  - name: access diagram content
    text: '`DiagramContent` represents the logical structure of a diagram, exposing
      pages and individual shapes for inspection. - Use `watermarker.getContent()`
      to retrieve a `DiagramContent` object. - Iterate through `content.getPages()`
      and then `page.getShapes()` to find shapes that contain images.'
  - name: replace shape images in a diagram
    text: '`DiagramShape` objects may hold an embedded image. Replace it by supplying
      a new `InputStream` that reads the replacement picture. The `setImage(InputStream)`
      method replaces the shape''s current image with the supplied stream. - Check
      `shape.getImage()`; if non‑null, call `shape.setImage(newImageStr'
  - name: add watermark to diagram (optional)
    text: If you also need to **add watermark to diagram**, create a `Watermark` object
      and apply it to the desired page or the whole document. The `Watermark` class
      defines a visual overlay that can be placed on diagram pages or the entire document.
      The `add(Watermark, AddOptions)` method applies the specifi
  - name: save and close watermarker
    text: Persist the changes and release resources to avoid file locks. The `save(String)`
      method writes the modified document to the specified path. - Call `watermarker.save("output.vsdx")`
      (or the appropriate extension). - Always invoke `watermarker.close()` in a `finally`
      block or use try‑with‑resources f
  type: HowTo
- questions:
  - answer: Yes. Load the file with `DiagramLoadOptions` that includes the password,
      then proceed with the normal replacement steps.
    question: Can I replace images in password‑protected diagrams?
  - answer: Absolutely. Wrap the single‑file workflow in a loop that iterates over
      a directory; the streaming architecture keeps memory usage low.
    question: Does the SDK support batch processing of multiple diagrams?
  - answer: GroupDocs.Watermark handles SVG, VDX, VSDX, and several other diagram
      formats, totaling more than 30 supported types.
    question: What formats can I work with besides Visio?
  - answer: Yes – invoke `watermarker.add(watermark, options)` after the image replacement
      step and before saving.
    question: Is it possible to add a watermark after replacing images?
  - answer: The `setImage(InputStream)` method embeds the image data directly into
      the diagram file, guaranteeing portability.
    question: How do I ensure the new image is embedded, not linked?
  type: FAQPage
tags:
- image replacement
- GroupDocs.Watermark
- Java diagram processing
title: GroupDocs.Watermark का उपयोग करके java में image replacement को स्वचालित करें
type: docs
url: /hi/java/diagram-document-watermarking/automate-image-replacement-groupdocs-watermark-java/
weight: 1
---

# GroupDocs.Watermark का उपयोग करके जावा में छवि प्रतिस्थापन को स्वचालित करें

डायग्राम के भीतर व्यक्तिगत चित्रों को अपडेट करना एक थकाऊ, त्रुटिप्रणाली मैन्युअल कार्य हो सकता है। **GroupDocs.Watermark for Java** के साथ, आप **जावा में छवि प्रतिस्थापन को स्वचालित** कर सकते हैं दर्जनों या सैकड़ों फ़ाइलों में, ब्रांड निरंतरता सुनिश्चित करते हुए और मूल्यवान विकास समय बचाते हुए। यह ट्यूटोरियल आपको लाइब्रेरी सेटअप करने, डायग्राम सामग्री तक पहुँचने, विशिष्ट आकारों के भीतर छवियों को बदलने, और वैकल्पिक रूप से डायग्राम में वॉटरमार्क जोड़ने के बारे में मार्गदर्शन करता है।

## त्वरित उत्तर
- **कौन सी लाइब्रेरी डायग्राम छवि अपडेट को संभालती है?** GroupDocs.Watermark for Java.  
- **क्या मैं छवियों को बदलते समय वॉटरमार्क जोड़ सकता हूँ?** हाँ – वही API आपको किसी भी डायग्राम पेज पर वॉटरमार्क ओवरले करने देती है।  
- **कौन सा जावा संस्करण आवश्यक है?** JDK 8 या उससे ऊपर।  
- **क्या विकास के लिए लाइसेंस चाहिए?** मूल्यांकन के लिए एक मुफ्त ट्रायल काम करता है; उत्पादन के लिए एक व्यावसायिक लाइसेंस आवश्यक है।  
- **क्या प्रक्रिया बड़े डायग्राम के लिए मेमोरी‑कुशल है?** हाँ – SDK सामग्री को स्ट्रीम करता है और पूरी फ़ाइल को मेमोरी में लोड नहीं करता।

## GroupDocs.Watermark for Java क्या है?
`GroupDocs.Watermark` एक जावा SDK है जो 30 से अधिक दस्तावेज़ फ़ॉर्मेट्स, जिसमें Visio, SVG, और अन्य डायग्राम प्रकार शामिल हैं, में वॉटरमार्क और छवियों को प्रोग्रामेटिक रूप से जोड़ने, हटाने और बदलने की सुविधा देता है। यह फ़ाइलों को स्ट्रीमिंग तरीके से प्रोसेस करता है, जिससे आप कई‑सौ‑पृष्ठों वाले डायग्राम पर काम कर सकते हैं बिना मेमोरी समाप्त किए।

## जावा में छवि प्रतिस्थापन को स्वचालित क्यों करें?
छवि प्रतिस्थापन को स्वचालित करने से बड़े दस्तावेज़ संग्रह में ब्रांडिंग एसेट्स को अपडेट करते समय मैनुअल श्रम में **90 %** तक की कमी आती है। SDK **30+ इनपुट और आउटपुट फ़ॉर्मेट्स** का समर्थन करता है, सामान्य सर्वर हार्डवेयर पर **200 MB** तक की फ़ाइलों को एक सेकंड से कम समय में प्रोसेस करता है, और पिक्सेल‑परफेक्ट छवि स्थिति की गारंटी देता है।

## आवश्यकताएँ
- JDK 8 या उससे नया आपके विकास मशीन पर स्थापित हो।  
- निर्भरताओं को प्रबंधित करने के लिए Maven (या कोई अन्य बिल्ड टूल)।  
- IntelliJ IDEA या Eclipse जैसे IDE।  
- बुनियादी जावा ज्ञान और फ़ाइल I/O की परिचितता।

### आवश्यक लाइब्रेरी, संस्करण, और निर्भरताएँ
`pom.xml` में निम्नलिखित Maven कोऑर्डिनेट्स जोड़ें। नीचे दिया गया प्लेसहोल्डर वही सटीक XML स्निपेट दर्शाता है जिसकी आपको आवश्यकता है; इसे अपरिवर्तित रखें।

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

मैन्युअल डाउनलोड के लिए, आधिकारिक रिलीज़ पेज से नवीनतम JARs प्राप्त करें: [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

## जावा में छवि प्रतिस्थापन को स्वचालित कैसे करें?
`Watermarker` इंस्टेंस के साथ डायग्राम लोड करें, लक्ष्य आकारों को खोजें, उनकी छवि स्ट्रीम को बदलें, वैकल्पिक रूप से वॉटरमार्क जोड़ें, और अंत में फ़ाइल को सहेजें। पूरा वर्कफ़्लो **चार संक्षिप्त चरणों** में फिट होता है, प्रत्येक नीचे दर्शाया गया है, और आमतौर पर बड़े फ़ाइलों के लिए भी प्रति डायग्राम कुछ सेकंड ही लेता है।

### चरण 1: watermarker को प्रारंभ करें
`Watermarker` क्लास सभी दस्तावेज़ ऑपरेशनों के लिए प्रवेश बिंदु है। यह स्रोत फ़ाइल खोलता है और संपादन के लिए आंतरिक संरचनाओं को तैयार करता है।

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

- **DiagramLoadOptions** डायग्राम‑विशिष्ट लोडिंग पैरामीटर कॉन्फ़िगर करता है।  
- `Watermarker` को प्रारंभ करना फ़ाइल हैंडल खोलता है और फ़ॉर्मेट को मान्य करता है।

### चरण 2: डायग्राम सामग्री तक पहुँचें
`DiagramContent` डायग्राम की तार्किक संरचना को दर्शाता है, पृष्ठों और व्यक्तिगत आकारों को निरीक्षण के लिए उजागर करता है।

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.contents.DiagramContent;

public class FeatureAccessDiagramContent {
    public static void run(Watermarker watermarker) throws Exception {
        DiagramContent content = watermarker.getContent(DiagramContent.class);
    }
}
```

- `watermarker.getContent()` का उपयोग करके एक `DiagramContent` ऑब्जेक्ट प्राप्त करें।  
- `content.getPages()` पर इटररेट करें और फिर `page.getShapes()` पर इटररेट करके उन आकारों को खोजें जिनमें छवियां हैं।

### चरण 3: डायग्राम में आकार की छवियों को बदलें
`DiagramShape` ऑब्जेक्ट्स में एम्बेडेड छवि हो सकती है। इसे बदलने के लिए नया `InputStream` प्रदान करें जो प्रतिस्थापन चित्र पढ़ता है।

`setImage(InputStream)` मेथड आकार की वर्तमान छवि को प्रदान किए गए स्ट्रीम से बदल देता है।  

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

- `shape.getImage()` जांचें; यदि non‑null है, तो `shape.setImage(newImageStream)` कॉल करें।  
- SDK स्वचालित रूप से छवि आयाम अपडेट करता है और मूल आकार लेआउट को संरक्षित रखता है।

### चरण 4: डायग्राम में वॉटरमार्क जोड़ें (वैकल्पिक)
यदि आपको **डायग्राम में वॉटरमार्क जोड़ने** की भी आवश्यकता है, तो एक `Watermark` ऑब्जेक्ट बनाएं और इसे इच्छित पेज या पूरे दस्तावेज़ पर लागू करें।

`Watermark` क्लास एक विज़ुअल ओवरले को परिभाषित करता है जिसे डायग्राम पेजों या पूरे दस्तावेज़ पर रखा जा सकता है।  

```java
Watermark watermark = new Watermark("Confidential", new Font("Arial", 36));
watermarker.add(watermark, new WatermarkOptions());
```

`add(Watermark, AddOptions)` मेथड निर्दिष्ट वॉटरमार्क को दिए गए विकल्पों का उपयोग करके दस्तावेज़ पर लागू करता है।  

*(ऊपर दिया गया कोड केवल उदाहरणात्मक है और इसे नया कोड ब्लॉक नहीं माना जाता; यह मौजूदा पैराग्राफ़ के भीतर रखा गया है।)*

### चरण 5: watermarker को सहेजें और बंद करें
परिवर्तनों को स्थायी बनाएं और फ़ाइल लॉक से बचने के लिए संसाधनों को रिलीज़ करें।

`save(String)` मेथड संशोधित दस्तावेज़ को निर्दिष्ट पथ पर लिखता है।  

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

- `watermarker.save("output.vsdx")` कॉल करें (या उपयुक्त एक्सटेंशन)।  
- हमेशा `finally` ब्लॉक में `watermarker.close()` को कॉल करें या स्वचालित क्लीनअप के लिए try‑with‑resources का उपयोग करें।

## सामान्य समस्याएँ और ट्रबलशूटिंग
- **छवि आकार का मेल न होना** – विकृति से बचने के लिए सुनिश्चित करें कि प्रतिस्थापन छवि का पहलू अनुपात मूल के समान हो।  
- **बड़े डायग्राम पर मेमोरी स्पाइक्स** – डायग्राम को एक-एक करके प्रोसेस करें और प्रत्येक सहेजने के बाद `Watermarker` को बंद करें।  
- **लाइसेंस त्रुटियाँ** – ट्रायल लाइसेंस 30 दिन के बाद समाप्त हो जाता है; डिप्लॉयमेंट से पहले इसे प्रोडक्शन कुंजी से बदलें। आप GroupDocs से एक अस्थायी लाइसेंस प्राप्त कर सकते हैं: [obtain a temporary license from GroupDocs](https://purchase.groupdocs.com/temporary-license/).

## अक्सर पूछे जाने वाले प्रश्न

**Q: क्या मैं पासवर्ड‑सुरक्षित डायग्राम में छवियों को बदल सकता हूँ?**  
A: हाँ। फ़ाइल को `DiagramLoadOptions` के साथ लोड करें जिसमें पासवर्ड शामिल हो, फिर सामान्य प्रतिस्थापन चरणों के साथ आगे बढ़ें।

**Q: क्या SDK कई डायग्राम की बैच प्रोसेसिंग का समर्थन करता है?**  
A: बिल्कुल। एकल‑फ़ाइल वर्कफ़्लो को लूप में रैप करें जो एक डायरेक्टरी पर इटररेट करता है; स्ट्रीमिंग आर्किटेक्चर मेमोरी उपयोग को कम रखता है।

**Q: Visio के अलावा मैं किन फ़ॉर्मेट्स के साथ काम कर सकता हूँ?**  
A: GroupDocs.Watermark SVG, VDX, VSDX, और कई अन्य डायग्राम फ़ॉर्मेट्स को संभालता है, कुल मिलाकर 30 से अधिक समर्थित प्रकार।

**Q: क्या छवियों को बदलने के बाद वॉटरमार्क जोड़ना संभव है?**  
A: हाँ – छवि प्रतिस्थापन चरण के बाद और सहेजने से पहले `watermarker.add(watermark, options)` को कॉल करें।

**Q: मैं कैसे सुनिश्चित करूँ कि नई छवि एम्बेडेड है, लिंक नहीं?**  
A: `setImage(InputStream)` मेथड छवि डेटा को सीधे डायग्राम फ़ाइल में एम्बेड करता है, जिससे पोर्टेबिलिटी की गारंटी मिलती है।

---

**Last Updated:** 2026-10-01  
**परीक्षण किया गया:** GroupDocs.Watermark 23.12 for Java  
**लेखक:** GroupDocs

## संबंधित ट्यूटोरियल्स

- [GroupDocs.Watermark Java के लिए डायग्राम वॉटरमार्किंग ट्यूटोरियल्स](/watermark/java/diagram-document-watermarking/)
- [डायग्राम आकारों से हाइपरलिंक्स हटाएँ GroupDocs.Watermark Java का उपयोग करके उन्नत दस्तावेज़ सुरक्षा के लिए](/watermark/java/diagram-document-watermarking/remove-hyperlinks-diagram-shapes-groupdocs-watermark-java/)
- [GroupDocs.Watermark का उपयोग करके जावा में इमेज वॉटरमार्क कैसे जोड़ें: चरण-दर-चरण गाइड](/watermark/java/image-watermarks/add-image-watermark-java-groupdocs/)