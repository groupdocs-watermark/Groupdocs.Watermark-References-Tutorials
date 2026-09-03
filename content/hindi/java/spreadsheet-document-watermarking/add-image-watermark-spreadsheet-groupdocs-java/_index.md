---
date: '2026-03-20'
description: GroupDocs.Watermark Java SDK का उपयोग करके Excel स्प्रेडशीट में इमेज
  वॉटरमार्क जोड़ना सीखें, जो ब्रांडिंग और दस्तावेज़ सुरक्षा के लिए उपयुक्त है।
keywords:
- GroupDocs.Watermark Java
- add image watermark Excel
- Java SDK spreadsheet watermark
title: 'वॉटरमार्क कैसे जोड़ें: GroupDocs.Watermark Java SDK का उपयोग करके एक्सेल स्प्रेडशीट
  में इमेज वॉटरमार्क'
type: docs
url: /hi/java/spreadsheet-document-watermarking/add-image-watermark-spreadsheet-groupdocs-java/
weight: 1
---

# Excel स्प्रेडशीट में Watermark जोड़ने का तरीका GroupDocs.Watermark Java SDK का उपयोग करके

अपने Excel फ़ाइलों को अनधिकृत वितरण से बचाने या सिर्फ़ ब्रांड पहचान को मजबूत करने के लिए एक दृश्य चिह्न जोड़ना आवश्यक है जो फ़ाइल को किसी भी तरह से देखा जाए, हमेशा दिखाई दे। इस ट्यूटोरियल में आप **वॉटरमार्क कैसे जोड़ें** — विशेष रूप से एक image watermark — को Excel स्प्रेडशीट के हेडर या फुटर में **GroupDocs.Watermark Java SDK** के साथ जोड़ना सीखेंगे। गाइड के अंत तक आप अपने वर्कबुक में सीधे एक लोगो, एक गोपनीयता बैज, या कोई भी कस्टम इमेज एम्बेड कर सकेंगे बिना सेल डेटा बदले।

## त्वरित उत्तर
- **“how to add watermark” क्या दर्शाता है?** एक इमेज (या टेक्स्ट) ओवरले जोड़ना जो हर प्रिंटेड पेज पर या हेडर/फुटर जैसे विशिष्ट सेक्शन में दिखाई देता है।  
- **Java में इसे कौन सी लाइब्रेरी सपोर्ट करती है?** `GroupDocs.Watermark` Java SDK (latest release).  
- **क्या मुझे लाइसेंस चाहिए?** विकास के लिए एक फ्री ट्रायल काम करता है; प्रोडक्शन के लिए एक कमर्शियल लाइसेंस आवश्यक है।  
- **क्या मैं हेडर में लोगो जोड़ सकता हूँ?** हाँ – इमेज वॉटरमार्क का उपयोग करें और हेडर विकल्प सेट करें (`add logo to header`).  
- **क्या एक साथ कई शीट्स प्रोसेस करना संभव है?** वर्कशीट इंडेक्सेज़ पर लूप करें और प्रत्येक शीट पर वही वॉटरमार्क लागू करें।

## पूर्वापेक्षाएँ

इस ट्यूटोरियल को फॉलो करने के लिए, सुनिश्चित करें कि आपके पास है:

- **GroupDocs.Watermark for Java SDK** (version 24.11 या नया)।  
- **Java Development Kit (JDK)** 8 या उससे ऊपर।  
- Java और Excel फ़ाइल संरचनाओं की बुनियादी जानकारी।

## GroupDocs.Watermark for Java SDK सेटअप करना

सबसे पहले, आवश्यक Maven डिपेंडेंसीज़ जोड़ें ताकि SDK आपके क्लासपाथ पर उपलब्ध हो।

### Maven कॉन्फ़िगरेशन

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

यदि आप Maven का उपयोग नहीं करना चाहते हैं, तो आधिकारिक रिलीज़ पेज से नवीनतम JAR डाउनलोड करें: [GroupDocs releases](https://releases.groupdocs.com/watermark/java/).

**License Acquisition**  
- सभी फीचर्स का मूल्यांकन करने के लिए एक फ्री ट्रायल या टेम्पररी लाइसेंस की प्राप्त करें।  
- कमर्शियल डिप्लॉयमेंट्स के लिए पूर्ण लाइसेंस खरीदें।

### इनिशियलाइज़ेशन और सेटअप

`Watermarker` इंस्टेंस बनाएं जो Excel फ़ाइल को लोड करेगा और सभी वॉटरमार्क ऑपरेशन्स के लिए एंट्री पॉइंट के रूप में काम करेगा।

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.SpreadsheetLoadOptions;

// Initialize Load Options
SpreadsheetLoadOptions loadOptions = new SpreadsheetLoadOptions();

// Create Watermarker instance with your spreadsheet file path
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/spreadsheet.xlsx", loadOptions);
```

## स्प्रेडशीट हेडर/फुटर में Watermark कैसे जोड़ें

नीचे चरण‑दर‑चरण प्रक्रिया दी गई है जो **java add image watermark** फ़ंक्शनैलिटी को दर्शाती है और यह भी दिखाती है कि आप **add logo to header** कैसे कर सकते हैं।

### चरण 1: लोडिंग विकल्प कॉन्फ़िगर करें

हम लोड विकल्प परिभाषित करके और `Watermarker` को पुनः‑इंस्टैंटिएट करके शुरू करते हैं। यह सुनिश्चित करता है कि SDK वर्कबुक को सही ढंग से पढ़े।

```java
import com.groupdocs.watermark.common.HorizontalAlignment;
import com.groupdocs.watermark.common.VerticalAlignment;
import com.groupdocs.watermark.options.SpreadsheetLoadOptions;

// Load the document with specified load options
SpreadsheetLoadOptions loadOptions = new SpreadsheetLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/spreadsheet.xlsx", loadOptions);
```

### चरण 2: Image Watermark बनाएं और कॉन्फ़िगर करें

`ImageWatermark` ऑब्जेक्ट बनाएं जो उस इमेज की ओर इशारा करता है जिसे आप एम्बेड करना चाहते हैं (जैसे, लोगो या “CONFIDENTIAL” बैज)। उसकी अलाइनमेंट और स्केलिंग को इस तरह समायोजित करें कि वह हेडर/फुटर क्षेत्र में अच्छी तरह फिट हो।

```java
import com.groupdocs.watermark.watermarks.ImageWatermark;
import com.groupdocs.watermark.watermarks.SizingType;

// Initialize the image watermark with your logo or desired image
ImageWatermark watermark = new ImageWatermark("YOUR_DOCUMENT_DIRECTORY/logo.png");

// Set alignment and scaling for a proper fit within the header/footer
watermark.setVerticalAlignment(VerticalAlignment.Top);
watermark.setHorizontalAlignment(HorizontalAlignment.Center);
watermark.setSizingType(SizingType.ScaleToParentDimensions); // Scales with parent dimensions
watermark.setScaleFactor(1); // Adjust scale factor as needed
```

### चरण 3: Header/Footer विकल्प कॉन्फ़िगर करें

SDK को बताएं कि कौन सी वर्कशीट और कौन सा भाग (हेडर या फुटर) वॉटरमार्क प्राप्त करेगा। यहाँ आप **add logo to header** कर सकते हैं या इसके बजाय फुटर चुन सकते हैं।

```java
import com.groupdocs.watermark.options.SpreadsheetWatermarkHeaderFooterOptions;

// Set options for applying the watermark
SpreadsheetWatermarkHeaderFooterOptions headerFooterOptions = new SpreadsheetWatermarkHeaderFooterOptions();
headerFooterOptions.setWorksheetIndex(0); // Apply to first worksheet (index 0)
```

### चरण 4: Watermark जोड़ें

अब तैयार किए गए इमेज वॉटरमार्क को चयनित हेडर/फुटर स्थान पर संलग्न करें।

```java
// Add the configured watermark
watermarker.add(watermark, headerFooterOptions);
```

### चरण 5: सेव और क्लोज करें

परिवर्तनों को नई फ़ाइल में सेव करें ताकि मूल वर्कबुक अपरिवर्तित रहे, फिर रिसोर्सेज़ रिलीज़ करें।

```java
// Save the watermarked document
watermarker.save("YOUR_OUTPUT_DIRECTORY/out_spreadsheet.xlsx");

// Release resources by closing the Watermarker instance
watermarker.close();
```

#### ट्रबलशूटिंग टिप्स

- इमेज पाथ को दोबारा जांचें; गलत पाथ `FileNotFoundException` फेंकेगा।  
- वर्कशीट इंडेक्स 0 से शुरू होते हैं; सुनिश्चित करें कि आपने जो इंडेक्स सेट किया है वह वास्तव में मौजूद है।  
- यदि वॉटरमार्क विकृत दिखे, तो `setScaleFactor` को समायोजित करें या `SizingType` को `StretchToParentDimensions` में बदलें।

## GroupDocs.Watermark Java SDK क्यों उपयोग करें?

- **क्रॉस‑फ़ॉर्मेट सपोर्ट** – Excel, Word, PowerPoint, PDFs, और इमेजेज़ के साथ काम करता है।  
- **नो‑लॉस एडिटिंग** – मूल सेल डेटा अपरिवर्तित रहता है।  
- **परफॉर्मेंस‑ऑप्टिमाइज़्ड** – बड़े वर्कबुक और बैच प्रोसेसिंग के लिए उपयुक्त।

## व्यावहारिक उपयोग केस

| Scenario | How the watermark helps |
|----------|------------------------|
| **गोपनीय रिपोर्ट्स** | हर प्रिंटेड पेज पर “CONFIDENTIAL” इमेज जोड़ें। |
| **ब्रांड सुदृढ़ीकरण** | इनवॉइस के हेडर में अपनी कंपनी का लोगो रखें। |
| **वर्ज़न ट्रैकिंग** | एक वर्ज़न‑नंबर बैज एम्बेड करें जो स्वचालित रूप से अपडेट होता है। |
| **कानूनी अनुपालन** | नियंत्रित स्प्रेडशीट्स को एक अनुपालन सील से चिह्नित करें। |

## प्रदर्शन संबंधी विचार

- **मेमोरी उपयोग** – बहुत बड़े स्प्रेडशीट प्रोसेस करते समय JVM हीप की निगरानी करें।  
- **बैच प्रोसेसिंग** – फ़ाइलों को समूहों में प्रोसेस करें ताकि मेमोरी फुटप्रिंट कम रहे।  
- **ऑब्जेक्ट्स का पुनः उपयोग** – कई फ़ाइलों के लिए एक ही `Watermarker` इंस्टेंस को पुनः‑उपयोग करने से ओवरहेड कम होता है।

## अक्सर पूछे जाने वाले प्रश्न

**Q: क्या मैं एक ही दस्तावेज़ में कई वॉटरमार्क जोड़ सकता हूँ?**  
A: हाँ, अतिरिक्त `ImageWatermark` इंस्टेंस बनाकर और प्रत्येक को `watermarker.add()` कॉल करने से पहले कॉन्फ़िगर करके।

**Q: स्प्रेडशीट से मौजूदा वॉटरमार्क कैसे हटाएँ?**  
A: वर्तमान में, GroupDocs.Watermark वॉटरमार्क जोड़ने पर केंद्रित है। हटाने के लिए, आपको वॉटरमार्क के बिना वर्कबुक को पुनः बनाना होगा या ऐसा टूल उपयोग करना होगा जो वॉटरमार्क एक्सट्रैक्शन सपोर्ट करता हो।

**Q: वॉटरमार्क के लिए कौन से इमेज फ़ॉर्मेट सपोर्टेड हैं?**  
A: PNG और JPEG जैसे सामान्य फ़ॉर्मेट सपोर्टेड हैं, लेकिन पूरी सूची के लिए [GroupDocs documentation](https://docs.groupdocs.com/watermark/java/) देखें।

**Q: पासवर्ड‑प्रोटेक्टेड स्प्रेडशीट को वॉटरमार्क करना संभव है?**  
A: हाँ, जब फ़ाइल खोलें तो आवश्यक पासवर्ड प्रदान करें।

**Q: दस्तावेज़ की सभी वर्कशीट्स पर वॉटरमार्क कैसे लागू करें?**  
A: प्रत्येक वर्कशीट इंडेक्स पर लूप करें और वॉटरमार्किंग स्टेप्स दोहराएँ, प्रत्येक इटरेशन के लिए `headerFooterOptions.setWorksheetIndex(i)` सेट करें।

## निष्कर्ष

अब आपके पास **java add excel watermark** के लिए एक पूर्ण, प्रोडक्शन‑रेडी तरीका है — विशेष रूप से इमेज वॉटरमार्क — **GroupDocs.Watermark Java SDK** का उपयोग करके। यह तरीका आपके Excel फ़ाइलों के हेडर या फुटर में सीधे ब्रांडिंग, गोपनीयता नोटिस या कोई भी विज़ुअल क्यू जोड़ता है जबकि मूल डेटा अपरिवर्तित रहता है। अन्य वॉटरमार्क प्रकार (टेक्स्ट, शेप) को एक्सप्लोर करने और उन्हें मिलाकर अधिक समृद्ध दस्तावेज़ सुरक्षा बनाने में संकोच न करें।

---

**अंतिम अपडेट:** 2026-03-20  
**परीक्षित संस्करण:** GroupDocs.Watermark 24.11 for Java  
**लेखक:** GroupDocs