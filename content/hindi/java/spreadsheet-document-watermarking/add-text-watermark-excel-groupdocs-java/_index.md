---
date: '2026-03-20'
description: GroupDocs.Watermark for Java का उपयोग करके Excel स्प्रेडशीट में वॉटरमार्क
  कैसे जोड़ें, सीखें, जिसमें Excel में टेक्स्ट वॉटरमार्क जोड़ना और Java से Excel में
  वॉटरमार्क जोड़ने की तकनीकें शामिल हैं।
keywords:
- text watermark excel
- groupdocs watermark java
- excel spreadsheet security
- watermark excel header footer
- custom font text watermark excel
title: GroupDocs.Watermark Java के साथ Excel में वॉटरमार्क कैसे जोड़ें
type: docs
url: /hi/java/spreadsheet-document-watermarking/add-text-watermark-excel-groupdocs-java/
weight: 1
---

# Excel स्प्रेडशीट में Watermark जोड़ने के लिए GroupDocs.Watermark for Java का उपयोग कैसे करें

Adding a **how to add watermark** capability to your Excel files is a practical way to protect sensitive data and assert ownership. In this step‑by‑step guide you’ll learn how to add watermark to an Excel spreadsheet, customize its appearance, and place it in headers or footers—all with GroupDocs.Watermark for Java.

## त्वरित उत्तर
- **What library is required?** GroupDocs.Watermark for Java (24.11 या नया)।  
- **Can I customize font and color?** हाँ, `Font` और `Color` क्लासों का उपयोग करके।  
- **Where does the watermark appear?** चयनित वर्कशीट के हेडर या फुटर में।  
- **Is a license needed for production?** गैर‑ट्रायल उपयोग के लिए एक वैध GroupDocs लाइसेंस आवश्यक है।  
- **Will this work with large workbooks?** हाँ, लेकिन संसाधन मुक्त करने के लिए `Watermarker` ऑब्जेक्ट को बंद करें।

## परिचय

क्या आप अपने Excel स्प्रेडशीट की सुरक्षा को टेक्स्ट Watermark जोड़कर बढ़ाना चाहते हैं? चाहे वह गोपनीय डेटा की सुरक्षा हो या स्वामित्व स्थापित करना, आपके स्प्रेडशीट के हेडर या फुटर में Watermark एम्बेड करना अत्यंत उपयोगी हो सकता है। इस ट्यूटोरियल में, हम आपको GroupDocs.Watermark for Java का उपयोग करके इस फीचर को लागू करने के चरण बताएँगे।

**आप क्या सीखेंगे**  
- Excel स्प्रेडशीट में टेक्स्ट Watermark कैसे जोड़ें  
- कस्टम फ़ॉन्ट और रंगों के साथ Watermark कॉन्फ़िगर करना  
- आपके दस्तावेज़ों में हेडर/फुटर संरेखण सेट करना  

इन कौशलों के साथ, आप अपने स्प्रेडशीट को प्रभावी रूप से सुरक्षित करने के लिए पूरी तरह तैयार होंगे। अब, चलिए शुरू करने के लिए आवश्यक पूर्वशर्तों में डुबकी लगाते हैं।

## Excel में “how to add watermark” क्या है?

Watermark एक हल्का, अर्ध‑पारदर्शी टेक्स्ट या इमेज होता है जो मुख्य सामग्री के पीछे (या सामने) दिखाई देता है। Excel में, Watermark आमतौर पर हेडर या फुटर क्षेत्र में रखा जाता है ताकि वह प्रत्येक प्रिंटेड पृष्ठ पर दिखाई दे और सेल डेटा में बाधा न डाले।

## Java के लिए GroupDocs.Watermark क्यों उपयोग करें?

- **Cross‑platform**: वह किसी भी OS पर काम करता है जो Java को सपोर्ट करता है।  
- **Full control**: फ़ॉन्ट, आकार, रंग और संरेखण को कस्टमाइज़ करें।  
- **Performance‑focused**: बड़े वर्कबुक को कुशलता से संभालता है।

## पूर्वशर्तें
- **GroupDocs.Watermark for Java** (24.11 या बाद का)  
- **Java Development Kit (JDK)** स्थापित और कॉन्फ़िगर किया हुआ  
- IntelliJ IDEA या Eclipse जैसे IDE  
- Maven (यदि आप निर्भरता प्रबंधन पसंद करते हैं)

### आवश्यक लाइब्रेरीज़
- **GroupDocs.Watermark for Java** – Watermarking API प्रदान करता है।

### ज्ञान पूर्वशर्तें
- बेसिक Java प्रोग्रामिंग  
- Maven या मैन्युअल JAR हैंडलिंग की परिचितता  

## Java के लिए GroupDocs.Watermark सेटअप करना

आप लाइब्रेरी को Maven के माध्यम से या सीधे JAR डाउनलोड करके स्थापित कर सकते हैं।

**Maven इंस्टॉलेशन**

अपने `pom.xml` में निम्नलिखित कॉन्फ़िगरेशन जोड़ें:

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

**सीधे डाउनलोड**  
वैकल्पिक रूप से, आप नवीनतम संस्करण [GroupDocs.Watermark for Java रिलीज़](https://releases.groupdocs.com/watermark/java/) से डाउनलोड कर सकते हैं।

### लाइसेंस प्राप्ति
- **Free Trial** – बिना लागत के API का अन्वेषण करें।  
- **Temporary License** – विस्तारित मूल्यांकन अवधि।  
- **Purchase** – पूर्ण‑फ़ीचर, असीमित उपयोग।

GroupDocs.Watermark को इनिशियलाइज़ करने के लिए, इम्पोर्ट स्टेटमेंट शामिल करें:

```java
import com.groupdocs.watermark.Watermarker;
```

## Excel स्प्रेडशीट में Watermark कैसे जोड़ें

नीचे पूर्ण, चलाने योग्य कोड स्पष्ट चरणों में विभाजित है। प्रत्येक चरण में कोड ब्लॉक से पहले एक संक्षिप्त व्याख्या शामिल है, ताकि आप बिना संदर्भ के कोई स्निपेट न देखें।

### चरण 1: स्प्रेडशीट लोड करें

पहले, उपयुक्त लोड विकल्पों के साथ वर्कबुक लोड करें।

```java
import com.groupdocs.watermark.common.HorizontalAlignment;
import com.groupdocs.watermark.common.VerticalAlignment;
import com.groupdocs.watermark.options.SpreadsheetLoadOptions;
import com.groupdocs.watermark.watermarks.Color;
import com.groupdocs.watermark.watermarks.Font;
import com.groupdocs.watermark.watermarks.FontStyle;
import com.groupdocs.watermark.watermarks.TextWatermark;

// Step 1: Load the spreadsheet using specific load options.
SpreadsheetLoadOptions loadOptions = new SpreadsheetLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/spreadsheet.xlsx", loadOptions);
```

**व्याख्या**: यह आपके Excel फ़ाइल से जुड़ा एक `Watermarker` इंस्टेंस बनाता है, जो Watermark संचालन के लिए तैयार है।

### चरण 2: टेक्स्ट Watermark बनाएं

Watermark की दृश्य उपस्थिति को कॉन्फ़िगर करें।

```java
// Step 2: Create a text watermark.
TextWatermark watermark = new TextWatermark("Test watermark", new Font("Segoe UI", 19, FontStyle.Bold));
watermark.setForegroundColor(Color.getRed());
watermark.setBackgroundColor(Color.getAqua());
watermark.setVerticalAlignment(VerticalAlignment.Top);
watermark.setHorizontalAlignment(HorizontalAlignment.Center);
```

**व्याख्या**: हम Watermark टेक्स्ट सेट करते हैं, बोल्ड **Segoe UI** फ़ॉन्ट चुनते हैं, और विपरीत फ़ोरग्राउंड व बैकग्राउंड रंग लागू करते हैं।

### चरण 3: Watermark प्लेसमेंट कॉन्फ़िगर करें

निर्धारित करें कि कौन सा वर्कशीट और पृष्ठ का कौन सा भाग (हेडर/फुटर) Watermark प्राप्त करेगा।

```java
import com.groupdocs.watermark.options.SpreadsheetWatermarkHeaderFooterOptions;

// Step 3: Configure options for adding a watermark to header or footer.
SpreadsheetWatermarkHeaderFooterOptions options = new SpreadsheetWatermarkHeaderFooterOptions();
options.setWorksheetIndex(0); // Target the first worksheet (index 0)
```

**व्याख्या**: `SpreadsheetWatermarkHeaderFooterOptions` ऑब्जेक्ट API को बताता है कि Watermark पहले शीट के हेडर/फुटर पर लागू किया जाए।

### चरण 4: Watermark जोड़ें और सहेजें

Watermark लागू करें और परिणाम को नई फ़ाइल में लिखें।

```java
// Step 4: Add the watermark with specified options.
watermarker.add(watermark, options);
watermarker.save("YOUR_OUTPUT_DIRECTORY/watermarked_spreadsheet.xlsx");
watermarker.close(); // Release any locks on the original document
```

**व्याख्या**: `add` मेथड Watermark डालता है, `save` संशोधित वर्कबुक को लिखता है, और `close` संसाधनों को मुक्त करता है।

## Excel में टेक्स्ट Watermark – उन्नत टिप्स
- **Multiple Worksheets**: प्रत्येक वर्कशीट इंडेक्स पर लूप करें और प्रत्येक के लिए `options.setWorksheetIndex(i)` कॉल करें।  
- **Dynamic Text**: डेटाबेस या कॉन्फ़िगरेशन फ़ाइल से Watermark टेक्स्ट प्राप्त करके प्रत्येक दस्तावेज़ को व्यक्तिगत बनाएं।  
- **Opacity Control**: `watermark.setOpacity(0.5)` का उपयोग करके Watermark को अधिक सूक्ष्म बनाएं।

## सामान्य समस्याएँ और समाधान

| समस्या | समाधान |
|-------|----------|
| **File Not Found** | पाथ स्ट्रिंग (`YOUR_DOCUMENT_DIRECTORY/...`) सही हैं यह सत्यापित करें और परीक्षण के दौरान पूर्ण पाथ का उपयोग करें। |
| **License Not Found** | `GroupDocs.Watermark.lic` फ़ाइल को प्रोजेक्ट रूट में रखें या प्रोग्रामेटिकली लाइसेंस सेट करें: `License license = new License(); license.setLicense("path/to/license.lic");`। |
| **Unsupported Format** | सुनिश्चित करें कि वर्कबुक `.xlsx` या `.xls` के रूप में सहेजा गया है। पुराने फॉर्मेट को पहले रूपांतरित करने की आवश्यकता हो सकती है। |
| **Performance Lag on Large Files** | एक समय में एक वर्कशीट प्रोसेस करें और प्रत्येक फ़ाइल समाप्त होते ही `watermarker.close()` कॉल करें। |

## व्यावहारिक अनुप्रयोग
1. **Confidential Data Protection** – प्रत्येक प्रिंटेड पृष्ठ पर स्पष्ट रूप से चिह्नित करके अनधिकृत कॉपी को रोकें।  
2. **Ownership Assertion** – कंपनी का नाम या लोगो को Watermark के रूप में एम्बेड करके दस्तावेज़ की उत्पत्ति सिद्ध करें।  
3. **Document Tracking** – Watermark में अद्वितीय पहचानकर्ता शामिल करके वितरण पथ को ट्रैक करें।

## प्रदर्शन संबंधी विचार
- एक सत्र में Watermark की संख्या कम रखें।  
- फ़ाइल हैंडल्स मुक्त करने के लिए `Watermarker` ऑब्जेक्ट को तुरंत बंद करें।  
- बहुत बड़े वर्कबुक के लिए, JVM हीप साइज (`-Xmx2g`) बढ़ाने पर विचार करें।

## अक्सर पूछे जाने वाले प्रश्न

**Q: क्या मैं अपने Watermark की फ़ॉन्ट शैली बदल सकता हूँ?**  
A: हाँ, किसी भी स्थापित फ़ॉन्ट फ़ैमिली, आकार, और `FontStyle` (Bold, Italic, आदि) के साथ `Font` ऑब्जेक्ट को कस्टमाइज़ करें।

**Q: क्या कई शीट्स में Watermark जोड़ना संभव है?**  
A: बिल्कुल। प्रत्येक शीट के इंडेक्स पर लूप करें और प्रत्येक शीट के लिए समान `SpreadsheetWatermarkHeaderFooterOptions` लागू करें।

**Q: Excel फ़ाइलों के लिए GroupDocs.Watermark कौन‑से फ़ाइल फ़ॉर्मेट सपोर्ट करता है?**  
A: XLS, XLSX, और अन्य Office Open XML स्प्रेडशीट फ़ॉर्मेट पूरी तरह सपोर्टेड हैं।

**Q: बहुत बड़े दस्तावेज़ों को कुशलता से कैसे संभालूँ?**  
A: एक समय में एक वर्कबुक प्रोसेस करें, सहेजने के बाद `Watermarker` को बंद करें, और JVM मेमोरी उपयोग की निगरानी करें।

**Q: क्या आवश्यकता पड़ने पर Watermark को बाद में हटाया जा सकता है?**  
A: सीधे हटाने की सुविधा नहीं है, लेकिन आप Watermark लागू किए बिना मूल फ़ाइल को पुनः जनरेट कर सकते हैं या भविष्य के उपयोग के लिए अनवॉटरमार्क्ड कॉपी रख सकते हैं।

## संसाधन
- [GroupDocs.Watermark दस्तावेज़ीकरण](https://docs.groupdocs.com/watermark/java/)  
- [API रेफ़रेंस](https://reference.groupdocs.com/watermark/java)  
- [GroupDocs.Watermark for Java डाउनलोड करें](https://releases.groupdocs.com/watermark/java/)  
- [GitHub रिपॉज़िटरी](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)  
- [नि:शुल्क सपोर्ट फ़ोरम](https://forum.groupdocs.com/c/watermark/10)  
- [अस्थायी लाइसेंस जानकारी](https://purchase.groupdocs.com/temporary-license/)  

---

**अंतिम अपडेट:** 2026-03-20  
**परीक्षण किया गया:** GroupDocs.Watermark 24.11 for Java  
**लेखक:** GroupDocs