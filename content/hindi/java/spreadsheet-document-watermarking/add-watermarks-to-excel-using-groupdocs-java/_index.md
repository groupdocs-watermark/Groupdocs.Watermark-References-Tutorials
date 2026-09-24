---
date: '2026-03-27'
description: GroupDocs.Watermark for Java के साथ स्प्रेडशीट बैकग्राउंड में वॉटरमार्क
  एक्सेल जोड़ना सीखें, जिससे दस्तावेज़ की सुरक्षा और प्रामाणिकता बढ़ेगी।
keywords:
- GroupDocs.Watermark for Java
- Excel watermarking
- Java spreadsheet security
title: GroupDocs.Watermark for Java का उपयोग करके एक्सेल बैकग्राउंड में वॉटरमार्क
  कैसे जोड़ें
type: docs
url: /hi/java/spreadsheet-document-watermarking/add-watermarks-to-excel-using-groupdocs-java/
weight: 1
---

# GroupDocs.Watermark for Java का उपयोग करके एक्सेल बैकग्राउंड में वॉटरमार्क कैसे जोड़ें

आज के डिजिटल युग में, **Excel में वॉटरमार्क जोड़ना** फ़ाइलों को संवेदनशील डेटा की सुरक्षा करने और स्वामित्व स्थापित करने का सिद्ध तरीका है। चाहे आप एक बिज़नेस एनालिस्ट हों जो गोपनीय वित्तीय मॉडल की सुरक्षा कर रहे हों या व्यक्तिगत रूप से निजी स्प्रेडशीट्स की रक्षा कर रहे हों, **add watermark excel** को अपने वर्कबुक की बैकग्राउंड इमेजेज़ में जोड़ना सीखने से आपको यह भरोसा मिलेगा कि आपके दस्तावेज़ प्रामाणिक और छेड़छाड़‑प्रूफ़ रहते हैं। यह ट्यूटोरियल आपको पूरी प्रक्रिया के माध्यम से स्पष्ट व्याख्याओं और तैयार‑चलाने योग्य जावा कोड के साथ ले जाता है।

## त्वरित उत्तर
- **“add watermark excel” क्या हासिल करता है?** यह कार्यपत्रक की बैकग्राउंड इमेजेज़ में दृश्यमान टेक्स्ट या ब्रांडिंग एम्बेड करता है, जिससे अनधिकृत उपयोग रोका जा सके।  
- **कौन सी लाइब्रेरी की सिफ़ारिश की जाती है?** GroupDocs.Watermark for Java (v24.11 or newer).  
- **क्या मुझे लाइसेंस की आवश्यकता है?** विकास के लिए एक फ्री ट्रायल या टेम्पररी लाइसेंस काम करता है; उत्पादन के लिए पूर्ण लाइसेंस आवश्यक है।  
- **क्या मैं फ़ॉन्ट, रोटेशन या आकार को कस्टमाइज़ कर सकता हूँ?** हाँ – `TextWatermark` क्लास आपको फ़ॉन्ट, अलाइनमेंट, रोटेशन एंगल और स्केलिंग को नियंत्रित करने देती है।  
- **क्या यह बड़े वर्कबुक्स के लिए सुरक्षित है?** वर्कशीट्स को एक‑एक करके प्रोसेस करें और मेमोरी उपयोग कम रखने के लिए `Watermarker` को तुरंत बंद करें।

## “add watermark excel” क्या है?
Excel फ़ाइल में वॉटरमार्क जोड़ना मतलब कार्यपत्रक की बैकग्राउंड पर अर्ध‑पारदर्शी टेक्स्ट या इमेज़ को ओवरले करना है। वॉटरमार्क दृश्य सामग्री का हिस्सा बन जाता है, जिससे स्पष्ट हो जाता है कि फ़ाइल सुरक्षित या ब्रांडेड है।

## GroupDocs.Watermark for Java का उपयोग क्यों करें?
- **व्यापक फ़ॉर्मेट समर्थन** – XLS, XLSX और अन्य स्प्रेडशीट प्रकारों के साथ काम करता है।  
- **सूक्ष्म नियंत्रण** – आप प्रत्येक कार्यपत्रक के लिए फ़ॉन्ट, अलाइनमेंट, रोटेशन और स्केलिंग सेट कर सकते हैं।  
- **प्रदर्शन‑उन्मुख** – बड़े दस्तावेज़ों को अत्यधिक मेमोरी उपयोग के बिना संभालने के लिए डिज़ाइन किया गया है।  
- **आसान इंटीग्रेशन** – सरल Maven डिपेंडेंसी और स्पष्ट API।

## पूर्वापेक्षाएँ

शुरू करने से पहले, सुनिश्चित करें कि आपके पास निम्नलिखित हैं:

### आवश्यक लाइब्रेरी, संस्करण, और डिपेंडेंसियों
आपको GroupDocs.Watermark for Java संस्करण 24.11 या बाद का चाहिए। अपने `pom.xml` में रिपॉजिटरी और डिपेंडेंसी जोड़ें:

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

वैकल्पिक रूप से, लाइब्रेरी को सीधे यहाँ से डाउनलोड करें: [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/)।

### पर्यावरण सेटअप आवश्यकताएँ
- Java Development Kit (JDK) 8 या नया  
- IntelliJ IDEA या Eclipse जैसे IDE  

### ज्ञान पूर्वापेक्षाएँ
बुनियादी जावा कोडिंग कौशल और Maven डिपेंडेंसी प्रबंधन की परिचितता।

## GroupDocs.Watermark for Java सेटअप करना

1. **लाइब्रेरी इंस्टॉल करें** – ऊपर दिया गया Maven स्निपेट उपयोग करें या JAR को अपने प्रोजेक्ट के क्लासपाथ में जोड़ें।  
2. **लाइसेंस प्राप्त करें** – आप फ्री ट्रायल या टेम्पररी लाइसेंस से शुरू कर सकते हैं। यहाँ से प्राप्त करें: [GroupDocs.Watermark Licensing](https://purchase.groupdocs.com/temporary-license/).  
3. **`Watermarker` इंस्टेंस बनाएं** – यह ऑब्जेक्ट आपके Excel फ़ाइल को लोड करेगा और आपको उसकी सामग्री तक पहुँच देगा।

## स्प्रेडशीट बैकग्राउंड इमेजेज़ में watermark excel कैसे जोड़ें

नीचे चरण‑दर‑चरण गाइड दिया गया है। प्रत्येक चरण में एक छोटा विवरण और फिर वह सटीक कोड शामिल है जिसे आपको कॉपी करना है।

### चरण 1: Excel दस्तावेज़ लोड करें

हम `SpreadsheetLoadOptions` का उपयोग करते हैं ताकि लाइब्रेरी को बताया जा सके कि हम एक स्प्रेडशीट के साथ काम कर रहे हैं।

```java
SpreadsheetLoadOptions loadOptions = new SpreadsheetLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/spreadsheet.xlsx", loadOptions);
```

### चरण 2: एक **text watermark excel** ऑब्जेक्ट बनाएं

वॉटरमार्क की उपस्थिति कॉन्फ़िगर करें – फ़ॉन्ट, अलाइनमेंट, रोटेशन, और स्केलिंग।

```java
// Initialize text watermark with specific settings
textWatermark = new TextWatermark("Protected image", new Font("Arial", 8));
textWatermark.setHorizontalAlignment(HorizontalAlignment.Center); // Center horizontally
textWatermark.setVerticalAlignment(VerticalAlignment.Center);    // Center vertically
textWatermark.setRotateAngle(45);                             // Set rotation angle
textWatermark.setSizingType(SizingType.ScaleToParentDimensions); // Scale to parent dimensions
textWatermark.setScaleFactor(1);                              // Set scale factor
```

### चरण 3: प्रत्येक कार्यपत्रक की बैकग्राउंड पर वॉटरमार्क लागू करें (the **excel background watermark**)

लूप यह जांचता है कि क्या कार्यपत्रक में पहले से बैकग्राउंड इमेज है; यदि है, तो वॉटरमार्क जोड़ा जाता है।

```java
SpreadsheetContent content = watermarker.getContent(SpreadsheetContent.class);
for (SpreadsheetWorksheet worksheet : content.getWorksheets()) {
    if (worksheet.getBackgroundImage() != null) {
        // Add watermark to the existing background image
        worksheet.getBackgroundImage().add(watermark);
    }
}
```

### चरण 4: संशोधित वर्कबुक सहेजें

ऐसा आउटपुट पाथ चुनें जो आपकी मूल फ़ाइल को ओवरराइट न करे।

```java
watermarker.save("YOUR_OUTPUT_DIRECTORY/spreadsheet_with_watermark.xlsx");
```

### चरण 5: संसाधनों को रिलीज़ करें

फ़ाइल हैंडल्स और मेमोरी मुक्त करने के लिए हमेशा `Watermarker` को बंद करें।

```java
watermarker.close();
```

## सामान्य समस्याएँ और समाधान (ट्रबलशूटिंग)

| समस्या | क्यों होता है | समाधान |
|---------|----------------|-----|
| कोई वॉटरमार्क नहीं दिखता | कार्यपत्रक में कोई बैकग्राउंड इमेज नहीं है। | पहले एक बैकग्राउंड इमेज जोड़ें या अलग वॉटरमार्किंग तरीका उपयोग करें (जैसे, सेल‑लेवल वॉटरमार्क)। |
| `FileNotFoundException` | गलत फ़ाइल पाथ या पढ़ने/लिखने की अनुमति नहीं है। | पाथ की जाँच करें और सुनिश्चित करें कि एप्लिकेशन को फ़ाइल सिस्टम एक्सेस है। |
| बड़ी फ़ाइलों पर प्रदर्शन में देरी | सभी कार्यपत्रक एक साथ प्रोसेस होते हैं। | वर्कशीट्स को बैच में प्रोसेस करें और आवश्यकता होने पर प्रत्येक बैच के बाद `System.gc()` कॉल करें। |
| लाइसेंस त्रुटि | ट्रायल लाइसेंस की समाप्ति के बाद उपयोग करना। | वैध स्थायी लाइसेंस में अपडेट करें या ट्रायल को नवीनीकृत करें। |

## अक्सर पूछे जाने वाले प्रश्न

**Q: क्या मैं GroupDocs.Watermark का उपयोग करके PDFs में भी वॉटरमार्क जोड़ सकता हूँ?**  
A: हाँ! GroupDocs.Watermark PDFs, Word दस्तावेज़, इमेजेज़ और कई अन्य फ़ॉर्मेट्स को सपोर्ट करता है।

**Q: मैं प्रत्येक कार्यपत्रक के लिए वॉटरमार्क टेक्स्ट को डायनामिकली कैसे बदल सकता हूँ?**  
A: लूप के अंदर एक नया `TextWatermark` बनाएं, वर्कशीट नाम या अन्य मेटाडेटा के आधार पर टेक्स्ट सेट करें, फिर `add(watermark)` कॉल करें।

**Q: अगर मेरी Excel फ़ाइल में कोई बैकग्राउंड इमेज नहीं है तो क्या होगा?**  
A: API उन शीट्स को स्किप कर देगा। आप पहले Excel में या प्रोग्रामेटिकली एक साधारण बैकग्राउंड इमेज सेट कर सकते हैं, फिर वॉटरमार्क लागू करें।

**Q: क्या विभिन्न कार्यपत्रकों के लिए अलग-अलग फ़ॉन्ट उपयोग करना संभव है?**  
A: बिल्कुल। प्रत्येक कार्यपत्रक के लिए अलग `Font` सेटिंग्स के साथ अलग `TextWatermark` ऑब्जेक्ट बनाएं।

**Q: वॉटरमार्किंग प्रक्रिया के दौरान अपवादों को कैसे संभालूँ?**  
A: कोड को `try‑catch` ब्लॉक में रखें, अपवाद को लॉग करें, और हमेशा `finally` क्लॉज़ में `watermarker.close()` कॉल करें।

## Excel बैकग्राउंड वॉटरमार्क के व्यावहारिक उपयोग

- **दस्तावेज़ सुरक्षा:** गोपनीय वित्तीय मॉडलों के अनधिकृत वितरण को रोकें।  
- **ब्रांडिंग:** प्रत्येक शीट पर आपका कंपनी लोगो या स्लोगन दिखाएँ।  
- **कॉपीराइट सुरक्षा:** स्वामित्व डेटा को स्पष्ट “Confidential” लेबल से चिह्नित करें।  
- **ऑडिट ट्रेल्स:** संस्करण नंबर या टाइमस्टैम्प को सीधे विज़ुअल लेआउट में एम्बेड करें।  
- **कस्टम नोटिफिकेशन्स:** आंतरिक रिव्यू चक्रों के लिए रिमाइंडर (जैसे, “Draft – Do Not Distribute”) जोड़ें।

## बड़े स्प्रेडशीट्स के लिए प्रदर्शन टिप्स

- वर्कशीट्स को क्रमिक रूप से प्रोसेस करें बजाय पूरे वर्कबुक को मेमोरी में लोड करने के।  
- `SizingType.ScaleToParentDimensions` का उपयोग करके बड़े रास्टर इमेजेज़ से बचें।  
- जब काम समाप्त हो जाए तो तुरंत `Watermarker` को बंद करें ताकि फ़ाइल हैंडल्स रिलीज़ हो सकें।

## निष्कर्ष

अब आपके पास GroupDocs.Watermark for Java का उपयोग करके **add watermark excel** बैकग्राउंड जोड़ने की एक पूरी, प्रोडक्शन‑रेडी विधि है। यह तरीका न केवल आपके स्प्रेडशीट्स को सुरक्षित करता है बल्कि वॉटरमार्क की लुक और फील पर पूरी नियंत्रण देता है। विभिन्न फ़ॉन्ट, रंग और रोटेशन एंगल्स के साथ प्रयोग करने में संकोच न करें ताकि आपके ब्रांडिंग गाइडलाइन के साथ मेल खाए।

---

**अंतिम अपडेट:** 2026-03-27  
**परीक्षण किया गया:** GroupDocs.Watermark for Java 24.11  
**लेखक:** GroupDocs  

## संसाधन
- **डॉक्यूमेंटेशन:** [GroupDocs.Watermark Java Docs](https://docs.groupdocs.com/watermark/java/)  
- **API रेफ़रेंस:** [Java API Reference](https://reference.groupdocs.com/watermark/java)  
- **डाउनलोड:** [Get the Latest Release](https://releases.groupdocs.com/watermark/java/)  
- **GitHub रिपॉज़िटरी:** [GroupDocs.Watermark for Java](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)  
- **सपोर्ट फ़ोरम:** [Free Support](https://forum.groupdocs.com/c/watermark/10)  
- **टेम्पररी लाइसेंस:** [Get a Temporary License](https://purchase.groupdocs.com/temporary-license/)