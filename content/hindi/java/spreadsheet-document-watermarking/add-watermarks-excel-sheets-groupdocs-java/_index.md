---
date: '2026-03-25'
description: GroupDocs.Watermark for Java का उपयोग करके एक्सेल शीट्स में वॉटरमार्क
  कैसे जोड़ें, जिसमें टेक्स्ट वॉटरमार्क और इमेज विकल्प शामिल हैं, ताकि आप अपने दस्तावेज़
  सुरक्षित कर सकें।
keywords:
- add watermark to excel
- remove watermark from excel
- add text watermark excel
- confidential watermark excel
title: Java और GroupDocs.Watermark के साथ Excel शीट्स में वॉटरमार्क जोड़ें
type: docs
url: /hi/java/spreadsheet-document-watermarking/add-watermarks-excel-sheets-groupdocs-java/
weight: 1
---

# Java और GroupDocs.Watermark के साथ Excel शीट्स में वॉटरमार्क जोड़ें

आज के तेज़ गति वाले व्यावसायिक माहौल में, **add watermark to excel** फ़ाइलें संवेदनशील डेटा की सुरक्षा, स्वामित्व का दावा करने और ब्रांडिंग को मजबूत करने का एक सरल yet शक्तिशाली तरीका है। चाहे आपको आंतरिक रिपोर्टों के लिए **confidential watermark excel** चाहिए या क्लाइंट‑फेसिंग वर्कबुक्स के लिए लोगो ओवरले, GroupDocs.Watermark for Java प्रक्रिया को सरल बनाता है। इस गाइड में हम लाइब्रेरी सेटअप, टेक्स्ट और इमेज दोनों वॉटरमार्क जोड़ने, और आवश्यकता पड़ने पर **remove watermark from excel** करने की प्रक्रिया को देखेंगे।

## त्वरित उत्तर
- **Java में Excel वॉटरमार्किंग के लिए सबसे अच्छी लाइब्रेरी कौन सी है?** GroupDocs.Watermark for Java.  
- **क्या मैं “Confidential” कहने वाला टेक्स्ट वॉटरमार्क जोड़ सकता हूँ?** हाँ – बस इच्छित टेक्स्ट के साथ `TextWatermark` बनाएं।  
- **क्या किसी विशिष्ट वर्कशीट पर लोगो लगाना संभव है?** बिल्कुल; `ImageWatermark` का उपयोग करें और वर्कशीट इंडेक्स सेट करें।  
- **क्या उत्पादन उपयोग के लिए लाइसेंस चाहिए?** पूर्ण लाइसेंस सभी फीचर अनलॉक करता है; ट्रायल लाइसेंस मूल्यांकन के लिए काम करता है।  
- **क्या बड़े वर्कबुक्स प्रदर्शन को प्रभावित करेंगे?** इमेज साइज ऑप्टिमाइज़ करें और मेमोरी उपयोग कम रखने के लिए संसाधनों को तुरंत बंद करें।  

## “add watermark to excel” क्या है?
वॉटरमार्क जोड़ने का मतलब है Excel वर्कबुक में एक अर्ध‑पारदर्शी टेक्स्ट या इमेज लेयर एम्बेड करना, जिससे यह प्रत्येक प्रिंटेड पेज या स्क्रीन पर दिखाई देता है। यह दृश्य संकेत अनधिकृत वितरण को रोकने में मदद करता है और दस्तावेज़ की गोपनीयता स्तर को स्पष्ट रूप से दर्शाता है।

## Java के लिए GroupDocs.Watermark क्यों उपयोग करें?
- **Cross‑platform** – वह किसी भी OS पर काम करता है जो Java को सपोर्ट करता है।  
- **Fine‑grained control** – व्यक्तिगत वर्कशीट्स को टार्गेट करें, रोटेशन, अपारदर्शिता, और पोजिशनिंग सेट करें।  
- **High performance** – बड़े स्प्रेडशीट्स के लिए न्यूनतम मेमोरी ओवरहेड के साथ डिज़ाइन किया गया है।  
- **Rich API** – टेक्स्ट, इमेज, और कस्टम शेप वॉटरमार्क को सपोर्ट करता है।

## पूर्वापेक्षाएँ
- **GroupDocs.Watermark for Java** (संस्करण 24.11 या नया)।  
- **Java Development Kit (JDK)** 8 या उससे ऊपर।  
- IntelliJ IDEA या Eclipse जैसे IDE।  
- बेसिक Java प्रोग्रामिंग ज्ञान।

## Java के लिए GroupDocs.Watermark सेटअप करना
अपने Java प्रोजेक्ट में GroupDocs.Watermark शुरू करने के लिए कुछ सरल चरणों की आवश्यकता होती है। यहाँ Maven का उपयोग करके इसे सेटअप करने का तरीका दिया गया है:

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

वैकल्पिक रूप से, आप सीधे [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/) से नवीनतम संस्करण डाउनलोड कर सकते हैं।

### लाइसेंस प्राप्ति
आप एक अस्थायी लाइसेंस डाउनलोड करके मुफ्त ट्रायल से शुरू कर सकते हैं या सभी फीचर अनलॉक करने के लिए पूर्ण लाइसेंस खरीद सकते हैं। लाइसेंस प्राप्त करने के लिए उनकी वेबसाइट पर दी गई निर्देशों का पालन करें।

एक बार सब सेट हो जाने पर, अपने Java प्रोजेक्ट में GroupDocs.Watermark को इनिशियलाइज़ करें:

```java
import com.groupdocs.watermark.Watermarker;

// Initialize Watermarker with your document
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/spreadsheet.xlsx");
```

## Excel वर्कशीट्स में वॉटरमार्क जोड़ने का चरण‑दर‑चरण गाइड

### वर्कशीट में टेक्स्ट वॉटरमार्क जोड़ें
एक **confidential watermark excel** अक्सर “Confidential” या “Do Not Distribute” जैसे बोल्ड टेक्स्ट का उपयोग करता है। नीचे पूरा वर्कफ़्लो दिया गया है।

#### चरण 1: स्प्रेडशीट डॉक्यूमेंट लोड करें
```java
import com.groupdocs.watermark.options.SpreadsheetLoadOptions;

SpreadsheetLoadOptions loadOptions = new SpreadsheetLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/spreadsheet.xlsx", loadOptions);
```

#### चरण 2: टेक्स्ट वॉटरमार्क बनाएं
```java
import com.groupdocs.watermark.watermarks.Font;
import com.groupdocs.watermark.watermarks.TextWatermark;

TextWatermark textWatermark = new TextWatermark("Confidential", new Font("Arial", 12));
textWatermark.setRotateAngle(-45);
```
*Pro tip:* रोटेशन एंगल को समायोजित करें ताकि वॉटरमार्क डेटा को अस्पष्ट किए बिना प्रमुख दिखे।

#### चरण 3: विशिष्ट शीट के लिए वॉटरमार्क कॉन्फ़िगर करें
```java
import com.groupdocs.watermark.options.SpreadsheetWatermarkShapeOptions;

SpreadsheetWatermarkShapeOptions options = new SpreadsheetWatermarkShapeOptions();
options.setWorksheetIndex(0); // Apply to the first worksheet

watermarker.add(textWatermark, options);
```

#### चरण 4: सेव करें और रिसोर्सेज़ रिलीज़ करें
```java
watermarker.save("YOUR_OUTPUT_DIRECTORY/watermarked_spreadsheet.xlsx");
watermarker.close();
textWatermark.close();
```

### वर्कशीट में इमेज वॉटरमार्क जोड़ें
इमेज वॉटरमार्क ब्रांडिंग के लिए बेहतरीन होते हैं—जैसे कंपनी लोगो या सील।

#### चरण 1: स्प्रेडशीट डॉक्यूमेंट लोड करें
(टेक्स्ट‑वॉटरमार्क सेक्शन से `SpreadsheetLoadOptions` को पुनः उपयोग करें।)

#### चरण 2: इमेज वॉटरमार्क बनाएं
```java
import com.groupdocs.watermark.watermarks.ImageWatermark;

ImageWatermark imageWatermark = new ImageWatermark("YOUR_DOCUMENT_DIRECTORY/logo.png");
imageWatermark.setOpacity(0.5);
```
अपारदर्शिता को 0.5 सेट करने से नीचे का डेटा पढ़ने योग्य रहता है।

#### चरण 3: इच्छित शीट के लिए वॉटरमार्क कॉन्फ़िगर करें
```java
SpreadsheetWatermarkShapeOptions options = new SpreadsheetWatermarkShapeOptions();
options.setWorksheetIndex(1); // Apply to the second worksheet

watermarker.add(imageWatermark, options);
```

#### चरण 4: सेव करें और रिसोर्सेज़ रिलीज़ करें
पहले दिखाए गए सेविंग और क्लोजिंग चरणों को पुनः उपयोग करें।

## सामान्य उपयोग केस
- **Confidential reports** – वित्तीय स्टेटमेंट्स में **confidential watermark excel** जोड़ें।  
- **Brand reinforcement** – प्रत्येक क्लाइंट‑फेसिंग वर्कबुक में अपना लोगो एम्बेड करें।  
- **Document tracking** – वितरण को ट्रैक करने के लिए एक यूनिक आइडेंटिफायर वॉटरमार्क शामिल करें।  

## (यदि आवश्यक हो) Excel से वॉटरमार्क हटाने का तरीका
GroupDocs.Watermark एक रिमूवल API भी प्रदान करता है। आप वर्कबुक लोड कर सकते हैं, `watermarker.removeAll()` कॉल करें या विशिष्ट शैप्स को टार्गेट करें, फिर साफ़ फ़ाइल को सेव करें। हटाने से पहले मूल फ़ाइल का बैकअप लेना याद रखें।

## प्रदर्शन टिप्स
- **Optimize image size** – छोटे PNG तेज़ लोड होते हैं।  
- **Close objects promptly** – `watermarker.close()` नेेटिव रिसोर्सेज़ को मुक्त करता है।  
- **Batch processing** – वर्कबुक्स के फ़ोल्डर पर लूप करके बुल्क में वॉटरमार्क लागू करें।

## अक्सर पूछे जाने वाले प्रश्न

**Q: क्या मैं वर्कबुक की सभी वर्कशीट्स में वॉटरमार्क जोड़ सकता हूँ?**  
A: हाँ, प्रत्येक वर्कशीट इंडेक्स पर इटररेट करके लूप में वॉटरमार्क लागू करें।

**Q: क्या वॉटरमार्क की पोजिशन बदलना संभव है?**  
A: बिल्कुल! सटीक प्लेसमेंट के लिए शैप ऑप्शन्स पर `setX` और `setY` जैसे पैरामीटर समायोजित करें।

**Q: बड़े Excel फ़ाइलों को प्रभावी ढंग से कैसे हैंडल करूँ?**  
A: वर्कबुक को छोटे हिस्सों में विभाजित करने या मेमोरी खपत कम करने के लिए लो‑रेज़ोल्यूशन इमेजेज़ उपयोग करने पर विचार करें।

**Q: GroupDocs.Watermark कौन‑से फ़ाइल फ़ॉर्मेट्स को सपोर्ट करता है?**  
A: Excel के अलावा, लाइब्रेरी PDFs, Word डॉक्यूमेंट्स, PowerPoint प्रेज़ेंटेशन, और सामान्य इमेज फ़ॉर्मेट्स को सपोर्ट करती है।

**Q: क्या मैं वॉटरमार्क जोड़ने के बाद उन्हें हटा सकता हूँ?**  
A: हाँ, API में रिमूवल मेथड्स शामिल हैं, लेकिन अनजाने में महत्वपूर्ण कंटेंट डिलीट न हो, इसका ध्यान रखें।

## संसाधन
- **डॉक्यूमेंटेशन**: [GroupDocs.Watermark for Java Documentation](https://docs.groupdocs.com/watermark/java/)
- **API रेफ़रेंस**: [API Reference Guide](https://reference.groupdocs.com/watermark/java)
- **GroupDocs डाउनलोड**: [Download Latest Version](https://releases.groupdocs.com/watermark/java/)
- **GitHub रिपॉजिटरी**: [GroupDocs.Watermark for Java on GitHub](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)
- **सपोर्ट फ़ोरम**: [Free Support Forum](https://forum.groupdocs.com/c/watermark/10)
- **अस्थायी लाइसेंस**: [Acquire a Temporary License](https://purchase.groupdocs.com/temporary-license/)

इस गाइड का पालन करके, अब आपके पास **add watermark to excel** फ़ाइलों को जोड़ने, संवेदनशील डेटा की सुरक्षा करने, और अपने ब्रांड को मजबूत करने की ठोस नींव है—सिर्फ कुछ Java कोड लाइनों से। हैप्पी वॉटरमार्किंग!

---

**अंतिम अपडेट:** 2026-03-25  
**परीक्षित संस्करण:** GroupDocs.Watermark 24.11 for Java  
**लेखक:** GroupDocs