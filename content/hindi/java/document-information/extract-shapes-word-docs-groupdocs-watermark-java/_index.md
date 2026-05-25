---
date: '2026-02-05'
description: GroupDocs.Watermark for Java का उपयोग करके Word दस्तावेज़ों से आकार निकालना
  सीखें, जिसमें Java में Word दस्तावेज़ लोड करना और आकार डेटा को संशोधित करना शामिल
  है।
keywords:
- GroupDocs.Watermark
- extract shapes from Word documents
- Java document manipulation
title: GroupDocs.Watermark Java का उपयोग करके Word दस्तावेज़ों से आकृतियों को निकालने
  का तरीका
type: docs
url: /hi/java/document-information/extract-shapes-word-docs-groupdocs-watermark-java/
weight: 1
---

# Java में GroupDocs.Watermark का उपयोग करके Word दस्तावेज़ों से आकृतियों को निकालना

इस ट्यूटोरियल में आप GroupDocs.Watermark Java लाइब्रेरी का उपयोग करके Word दस्तावेज़ों से **आकृतियों को निकालने** के बारे में जानेंगे। चाहे आपको आरेखों का विश्लेषण करना हो, एम्बेडेड इमेज निकालनी हों, या रिपोर्ट जनरेशन को स्वचालित करना हो, आकृति मेटाडाटा निकालने से आप अधिक स्मार्ट दस्तावेज़‑प्रोसेसिंग पाइपलाइन बना सकते हैं। हम लाइब्रेरी सेटअप करने, Word दस्तावेज़ लोड करने, और विस्तृत आकृति जानकारी प्राप्त करने की प्रक्रिया को स्पष्ट, चरण‑दर‑चरण Java कोड के साथ दिखाएंगे।

## त्वरित उत्तर
- **“आकृतियों को निकालना” का क्या अर्थ है?** Word फ़ाइल में प्रत्येक ड्राइंग ऑब्जेक्ट के लिए मेटाडाटा (प्रकार, आकार, स्थिति, टेक्स्ट, इमेज) प्राप्त करना।  
- **यह कौन सी लाइब्रेरी संभालती है?** GroupDocs.Watermark for Java।  
- **क्या मुझे लाइसेंस चाहिए?** विकास के लिए ट्रायल काम करता है; पूर्ण लाइसेंस उपयोग सीमाओं को हटाता है।  
- **क्या मैं आकृतियों से इमेज भी प्राप्त कर सकता हूँ?** हाँ – API चित्र आकृतियों के इमेज बाइट्स प्रदान करता है।  
- **कौन सा Java संस्करण आवश्यक है?** JDK 8 या नया।

## Word दस्तावेज़ों के संदर्भ में “आकृतियों को निकालना” क्या है?
आकृतियों को निकालना मतलब प्रोग्रामेटिक रूप से प्रत्येक ड्राइंग एलिमेंट—चित्र, WordArt, ऑटो‑शेप्स, चार्ट, और हेडर या फुटर में एम्बेडेड आकृतियों—तक पहुंचना है। इस जानकारी का उपयोग वैधता, माइग्रेशन, या कंटेंट‑ड्रिवेन एनालिटिक्स के लिए किया जा सकता है।

## Java के लिए GroupDocs.Watermark क्यों उपयोग करें?
GroupDocs.Watermark एक उच्च‑स्तरीय, मेमोरी‑कुशल API प्रदान करता है जो अंतर्निहित Office Open XML फ़ॉर्मेट की जटिलता को सारांशित करता है। यह आपको सक्षम बनाता है:
- दस्तावेज़ों को तेज़ी से लोड करना (`WordProcessingLoadOptions`)।  
- सेक्शन और आकृतियों के माध्यम से इटररेट करना बिना लो‑लेवल XML से निपटे।  
- एक ही कॉल में इमेज डेटा, टेक्स्ट, अलाइनमेंट, और रोटेशन प्राप्त करना।  
- मौजूदा Java सेवाओं या माइक्रो‑सेवाओं में सहजता से एकीकृत करना।

## पूर्वापेक्षाएँ
- **Java Development Kit (JDK)** 8 या उससे ऊपर।  
- **IDE** जैसे IntelliJ IDEA या Eclipse।  
- बेसिक Java I/O ज्ञान।  
- **GroupDocs.Watermark for Java** लाइसेंस या ट्रायल तक पहुंच।

## Java के लिए GroupDocs.Watermark सेटअप करना
लाइब्रेरी को Maven या सीधे डाउनलोड के माध्यम से इंटीग्रेट करें।

### Maven का उपयोग करके
`pom.xml` में रिपॉजिटरी और डिपेंडेंसी जोड़ें:

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
वैकल्पिक रूप से, नवीनतम JAR को [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/) से डाउनलोड करें।

### लाइसेंस प्राप्त करना
टेस्टिंग के लिए एक मुफ्त ट्रायल पर्याप्त है। प्रोडक्शन के लिए, सभी फीचर अनलॉक करने हेतु स्थायी लाइसेंस का अनुरोध करें।

## कार्यान्वयन गाइड
हम कार्यान्वयन को दो स्पष्ट चरणों में विभाजित करेंगे: **Word दस्तावेज़ लोड करना** और **आकृति जानकारी निकालना**।

### चरण 1: Word दस्तावेज़ लोड करें (load word document java)
पहले, लोड विकल्प कॉन्फ़िगर करें और एक `Watermarker` इंस्टेंस बनाएं। यह दस्तावेज़ को आगे निरीक्षण के लिए तैयार करता है।

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.WordProcessingLoadOptions;

public void loadDocument() {
    // Configure load options for loading a Word document
    WordProcessingLoadOptions loadOptions = new WordProcessingLoadOptions();
    
    // Create an instance of Watermarker with the specified document and load options
    Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/document.docx", loadOptions);
    
    // Close the watermarker to release resources
    watermarker.close();
}
```

> **प्रो टिप:** `Watermarker` इंस्टेंस को यथासंभव सीमित रखें; इसे तुरंत बंद करने से नेटिव रिसोर्सेज़ मुक्त होते हैं और मेमोरी लीक से बचते हैं।

### चरण 2: आकृति जानकारी निकालें (extract images from shapes)
अब हम प्रत्येक आकृति के विवरण निकालेंगे, जिसमें एम्बेडेड इमेज भी शामिल हैं। कोड प्रत्येक सेक्शन और प्रत्येक आकृति के माध्यम से इटररेट करता है, उपयोगी मेटाडाटा प्रिंट करता है।

```java
import com.groupdocs.watermark.contents.WordProcessingContent;

public void extractShapeInformation() {
    // Load the Word document as configured previously
    WordProcessingLoadOptions loadOptions = new WordProcessingLoadOptions();
    Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/document.docx", loadOptions);

    // Obtain WordProcessingContent from the watermarker
    WordProcessingContent content = watermarker.getContent(WordProcessingContent.class);

    // Iterate over each section in the document's content
    for (var section : content.getSections()) {
        // Iterate over each shape within the current section
        for (var shape : section.getShapes()) {
            // Check if the shape is part of a header or footer
            if (shape.getHeaderFooter() != null) {
                System.out.println("In header/footer");
            }
            
            // Output details about each shape, such as type and dimensions
            System.out.println(shape.getShapeType());
            System.out.println(shape.getWidth());
            System.out.println(shape.getHeight());
            System.out.println(shape.isWordArt());
            System.out.println(shape.getRotateAngle());
            System.out.println(shape.getAlternativeText());
            System.out.println(shape.getName());
            System.out.println(shape.getX());
            System.out.println(shape.getY());
            System.out.println(shape.getText());

            // If the shape contains an image, output its details
            if (shape.getImage() != null) {
                System.out.println(shape.getImage().getWidth());
                System.out.println(shape.getImage().getHeight());
                System.out.println(shape.getImage().getBytes().length);
            }
            
            // Output alignment information of the shape
            System.out.println(shape.getHorizontalAlignment());
            System.out.println(shape.getVerticalAlignment());
            System.out.println(shape.getRelativeHorizontalPosition());
            System.out.println(shape.getRelativeVerticalPosition());
        }
    }

    // Close the watermarker to release resources
    watermarker.close();
}
```

**यह कोड क्या करता है:**  
- प्रत्येक आकृति का **प्रकार** (जैसे, picture, WordArt) प्राप्त करता है।  
- **आकार**, **स्थिति**, और **रोटेशन** मान प्रिंट करता है।  
- **वैकल्पिक टेक्स्ट** और **नाम** दिखाता है, जो एक्सेसिबिलिटी चेक के लिए उपयोगी हैं।  
- यदि आकृति में इमेज है, तो इमेज के **पिक्सेल आयाम** और **बाइट आकार** प्रिंट करता है—आकृतियों से इमेज निकालने के लिए उपयुक्त।

### सामान्य समस्याएँ और समाधान
| Issue | Cause | Solution |
|-------|-------|----------|
| `FileNotFoundException` | गलत फ़ाइल पथ या अनुमति नहीं होना | एब्सोल्यूट/रिलेटिव पाथ की जाँच करें और सुनिश्चित करें कि फ़ाइल पढ़ी जा सकती है। |
| Null `shape.getImage()` | आकृति चित्र नहीं है (जैसे, ऑटो‑शेप) | `if (shape.getImage() != null)` के साथ गार्ड करें जैसा दिखाया गया है। |
| High memory usage on large docs | सभी दस्तावेज़ को एक साथ लोड करना | सेक्शन को एक-एक करके प्रोसेस करें या JVM हीप बढ़ाएँ (`-Xmx`)। |
| Missing header/footer shapes | `shape.getHeaderFooter()` की जाँच न करना | सैंपल पहले ही लॉग करता है जब आकृति हेडर/फ़ूटर से संबंधित होती है। |

## व्यावहारिक अनुप्रयोग
1. **स्वचालित रिपोर्ट जनरेशन** – चार्ट और आरेख निकालें और डाउनस्ट्रीम PDFs में एम्बेड करें।  
2. **अनुपालन ऑडिटिंग** – सत्यापित करें कि सभी आकृतियों में एक्सेसिबिलिटी के लिए उपयुक्त वैकल्पिक टेक्स्ट हो।  
3. **कंटेंट माइग्रेशन** – लेगेसी Word फ़ाइलों से एम्बेडेड इमेज को डिजिटल एसेट मैनेजमेंट सिस्टम में एक्सपोर्ट करें।  

## प्रदर्शन विचार
- **रिसोर्सेज़ रिलीज़ करें**: हमेशा `watermarker.close()` को `finally` ब्लॉक में कॉल करें या यदि आप API को रैप करते हैं तो try‑with‑resources का उपयोग करें।  
- **चंक प्रोसेसिंग**: 50 MB से बड़े दस्तावेज़ों के लिए, मेमोरी फ़ुटप्रिंट कम रखने हेतु प्रत्येक सेक्शन को अलग‑अलग प्रोसेस करने पर विचार करें।  
- **थ्रेड सुरक्षा**: `Watermarker` इंस्टेंस थ्रेड‑सेफ़ नहीं हैं; प्रत्येक थ्रेड के लिए नया इंस्टेंस बनाएं।  

## निष्कर्ष
अब आप जानते हैं कि GroupDocs.Watermark for Java का उपयोग करके Word दस्तावेज़ों से **आकृतियों को कैसे निकालें**, फ़ाइल लोड करने से लेकर प्रत्येक आकृति के मेटाडाटा और एम्बेडेड इमेज डेटा पढ़ने तक। यह क्षमता उन्नत दस्तावेज़ एनालिटिक्स, स्वचालित कंटेंट पाइपलाइन, और एक्सेसिबिलिटी वैलिडेशन के द्वार खोलती है।

### अगले कदम
- आकृति गुणों (जैसे, रिसाइज़िंग या रीपोजिशनिंग) को बदलने के साथ प्रयोग करें।  
- इस दृष्टिकोण को **GroupDocs.Parser** के साथ मिलाकर आसपास का टेक्स्ट निकालें।  
- एक्सट्रैक्शन लॉजिक को REST सर्विस में इंटीग्रेट करें ताकि ऑन‑डिमांड प्रोसेसिंग हो सके।

## अक्सर पूछे जाने वाले प्रश्न
**प्रश्न: GroupDocs.Watermark for Java क्या है?**  
**उत्तर:** यह एक व्यापक लाइब्रेरी है जो विभिन्न फ़ॉर्मेट में वॉटरमार्क और दस्तावेज़ कंटेंट को मैनेज करने के लिए डिज़ाइन की गई है, जिससे आकृति निष्कर्षण, इमेज रिट्रीवल, और टेक्स्ट मैनिपुलेशन जैसे कार्य संभव होते हैं।

**प्रश्न: क्या मैं लाइसेंस के बिना आकृतियों से इमेज निकाल सकता हूँ?**  
**उत्तर:** ट्रायल संस्करण निष्कर्षण की अनुमति देता है, लेकिन पूर्ण लाइसेंस उपयोग सीमाओं को हटाता है और वाणिज्यिक डिप्लॉयमेंट को सक्षम करता है।

**प्रश्न: क्या यह `.doc` (बाइनरी) फ़ाइलों के साथ काम करता है?**  
**उत्तर:** हाँ, API दोनों `.docx` और लेगेसी `.doc` फ़ॉर्मेट को सपोर्ट करता है।

**प्रश्न: पासवर्ड‑प्रोटेक्टेड दस्तावेज़ों को कैसे हैंडल करें?**  
**उत्तर:** `Watermarker` बनाने से पहले `WordProcessingLoadOptions.setPassword("yourPassword")` के माध्यम से पासवर्ड प्रदान करें।

**प्रश्न: क्या निकाली गई आकृति डेटा को JSON में एक्सपोर्ट करने का कोई तरीका है?**  
**उत्तर:** आप प्रिंट किए गए मानों को POJO में मैप कर सकते हैं और किसी भी JSON लाइब्रेरी (जैसे, Jackson) का उपयोग करके कलेक्शन को सीरियलाइज़ कर सकते हैं।

---

**अंतिम अपडेट:** 2026-02-05  
**परीक्षित संस्करण:** GroupDocs.Watermark 24.11 for Java  
**लेखक:** GroupDocs