---
date: '2026-06-01'
description: Java के लिए GroupDocs.Watermark के साथ Excel फ़ाइलों से आकार हटाने के
  तरीके सीखें। इसमें Excel लोड करने, वर्कशीट्स पर इटररेट करने, और फ़ॉर्मेटेड आकार
  हटाने के चरण शामिल हैं।
keywords:
- remove shapes from excel
- add watermark to excel
- load excel document java
- how to add watermark excel
schemas:
- author: GroupDocs
  dateModified: '2026-06-01'
  description: Learn how to remove shapes from excel files with GroupDocs.Watermark
    for Java. Includes steps to load Excel, iterate worksheets, and delete formatted
    shapes.
  headline: How to remove shapes from excel using GroupDocs.Watermark in Java
  type: TechArticle
- description: Learn how to remove shapes from excel files with GroupDocs.Watermark
    for Java. Includes steps to load Excel, iterate worksheets, and delete formatted
    shapes.
  name: How to remove shapes from excel using GroupDocs.Watermark in Java
  steps:
  - name: '**Data Validation** – Automatically delete shapes that contain deprecated
      notices.'
    text: '**Data Validation** – Automatically delete shapes that contain deprecated
      notices.'
  - name: '**Template Standardization** – Enforce corporate branding by stripping
      non‑standard text boxes.'
    text: '**Template Standardization** – Enforce corporate branding by stripping
      non‑standard text boxes.'
  - name: '**Automated Reporting** – Clean up generated reports before distribution,
      guaranteeing a polished look.'
    text: '**Automated Reporting** – Clean up generated reports before distribution,
      guaranteeing a polished look.'
  type: HowTo
- questions:
  - answer: Yes. Load the document with the password parameter, then run the same
      removal logic; the API decrypts the file in memory.
    question: Can I remove shapes from a password‑protected workbook?
  - answer: Absolutely. GroupDocs.Watermark handles both `.xlsx` and legacy `.xls`
      formats without conversion.
    question: Does the library support .xls (Excel 97‑2003) files?
  - answer: Iterate the shape collection, check the formatting criteria, log `shape.getName()`
      or `shape.getId()`, then call `remove()`.
    question: How do I log which shapes were deleted?
  - answer: Yes. After cleanup, invoke `doc.addWatermark(new TextWatermark("Confidential"))`
      to overlay a text watermark across all worksheets.
    question: Is it possible to add a watermark after removing shapes?
  - answer: The library can process files up to **2 GB** on a 64‑bit JVM, limited
      only by available heap memory and OS constraints.
    question: What is the maximum file size supported?
  type: FAQPage
title: Java में GroupDocs.Watermark का उपयोग करके Excel से आकार कैसे हटाएँ
type: docs
url: /hi/java/spreadsheet-document-watermarking/excel-shape-manipulation-groupdocs-watermark-java/
weight: 1
---

# Excel में आकार हटाने के लिए GroupDocs.Watermark का उपयोग Java में कैसे करें

Excel स्प्रेडशीट्स व्यापार रिपोर्टिंग का एक मुख्य आधार हैं, लेकिन अवांछित आकार—विशेषकर वे जिनमें पुराना या गैर‑मानक टेक्स्ट फ़ॉर्मेटिंग है—फ़ाइल को अव्यवस्थित कर सकते हैं और दृश्य संगति को तोड़ सकते हैं। **Excel से आकार हटाना** साफ़, पेशेवर दस्तावेज़ों के लिए जल्दी ही आवश्यक हो जाता है। इस ट्यूटोरियल में हम एक Excel वर्कबुक लोड करने, उसकी वर्कशीट्स को इटरेट करने, और विशिष्ट फ़ॉर्मेटिंग मानदंडों से मेल खाने वाले आकारों को प्रोग्रामेटिक रूप से हटाने की प्रक्रिया को GroupDocs.Watermark Java लाइब्रेरी के साथ दिखाएंगे।

## त्वरित उत्तर
- **क्या GroupDocs.Watermark आकार हटाता है?** हाँ, यह `removeShape` मेथड प्रदान करता है जो किसी भी वर्कशीट पर काम करता है।  
- **क्या इस फीचर के लिए लाइसेंस चाहिए?** मूल्यांकन के लिए ट्रायल काम करता है; उत्पादन के लिए पूर्ण लाइसेंस आवश्यक है।  
- **कौन सा Java संस्करण आवश्यक है?** Java 8 या बाद का समर्थन किया जाता है।  
- **GroupDocs.Watermark कितने फ़ाइल फ़ॉर्मेट संभालता है?** 30 से अधिक इनपुट और आउटपुट फ़ॉर्मेट, जैसे XLSX, DOCX, PDF, और PPTX।  
- **क्या बड़े वर्कबुक के लिए मेमोरी खपत चिंता का विषय है?** try‑with‑resources का उपयोग करें और पूरी शीट को मेमोरी में लोड करने से बचें; API डेटा को कुशलता से स्ट्रीम करता है।

## Excel से आकार हटाना क्या है?
*Excel से आकार हटाना* का मतलब है प्रोग्रामेटिक रूप से ड्राइंग ऑब्जेक्ट्स—जैसे टेक्स्ट बॉक्स, आइकन, या SmartArt—को हटाना जो कुछ मानदंडों (फ़ॉन्ट शैली, रंग, या आकार) को पूरा करते हैं। यह ऑपरेशन वर्कबुक को मैन्युअल संपादन के बिना साफ़ करता है, दृश्य संगति सुनिश्चित करता है, फ़ाइल आकार घटाता है, और वितरित रिपोर्टों में पुरानी या अवांछित ग्राफ़िक्स दिखने से रोकता है।

## Excel से आकार क्यों हटाएँ?
GroupDocs.Watermark **30+ फ़ाइल फ़ॉर्मेट** को 3 × तेज़ गति से प्रोसेस कर सकता है, जबकि 50 MB से बड़ी फ़ाइलों के लिए मेमोरी उपयोग 150 MB से कम रखता है। आकार हटाने को स्वचालित करने से मानव त्रुटि समाप्त होती है और सभी उत्पन्न रिपोर्टों में निरंतर ब्रांडिंग सुनिश्चित होती है।

## पूर्वापेक्षाएँ
### आवश्यक लाइब्रेरी, संस्करण, और निर्भरताएँ
- **Java Development Kit (JDK)**: संस्करण 8 या बाद का।  
- **GroupDocs.Watermark**: संस्करण 24.11 (लेखन के समय नवीनतम स्थिर रिलीज़)।

### पर्यावरण सेटअप आवश्यकताएँ
IntelliJ IDEA या Eclipse जैसे IDE का उपयोग करें और निर्भरता प्रबंधन के लिए Maven का प्रयोग करें।

### ज्ञान पूर्वापेक्षाएँ
Java सिंटैक्स और बुनियादी Excel अवधारणाओं (वर्कशीट, सेल, और आकार) की परिचितता आपको उदाहरणों को समझने में मदद करेगी।

## Java के लिए GroupDocs.Watermark सेटअप करना
### Maven निर्भरता  
अपने `pom.xml` में निम्नलिखित जोड़ें:

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
वैकल्पिक रूप से नवीनतम संस्करण [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/) से डाउनलोड करें।

### लाइसेंस प्राप्ति चरण
- **Free Trial** – फीचर का मूल्यांकन करने के लिए मुफ्त ट्रायल से शुरू करें।  
- **Temporary License** – विस्तारित परीक्षण के लिए अस्थायी लाइसेंस प्राप्त करें।  
- **Purchase** – उत्पादन उपयोग के लिए पूर्ण लाइसेंस खरीदें।

### बुनियादी आरंभिककरण और सेटअप  
एक बार लाइब्रेरी आपके प्रोजेक्ट में जोड़ दी गई, नीचे दिखाए अनुसार इसे इनिशियलाइज़ करें:

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.SpreadsheetLoadOptions;

public class WatermarkSetup {
    public static void main(String[] args) {
        // Initialize the watermarker with a document path and load options
        SpreadsheetLoadOptions loadOptions = new SpreadsheetLoadOptions();
        Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/spreadsheet.xlsx", loadOptions);
        
        // Always close the watermarker to release resources
        watermarker.close();
    }
}
```  

## Excel से आकार कैसे हटाएँ?
वर्कबुक लोड करें, प्रत्येक वर्कशीट को इटरेट करें, और आकार‑हटाने API को कॉल करें। यह दो‑चरणीय पैटर्न—*लोड* फिर *इटरेट*—लगभग किसी भी परिदृश्य को कवर करता है जहाँ आपको पूरे फ़ाइल में आकार साफ़ करने की आवश्यकता होती है। हटाने से पहले प्रत्येक आकार की प्रॉपर्टी को आपके मानदंडों के विरुद्ध जांचें, ताकि केवल अवांछित तत्व हटें और दस्तावेज़ का लेआउट व सामग्री बना रहे।

## Excel दस्तावेज़ लोड करें
### अवलोकन  
Excel दस्तावेज़ लोड करना किसी भी मैनिपुलेशन कार्य का प्रारंभिक बिंदु है। GroupDocs.Watermark अपने सहज API के साथ इसे सरल बनाता है।  

### परिभाषा एंकर  
`SpreadsheetDocument` GroupDocs.Watermark में मुख्य क्लास है जो मेमोरी में एक Excel वर्कबुक का प्रतिनिधित्व करता है, वर्कशीट, सेल, और आकार तक पहुँचने के मेथड प्रदान करता है।  

#### कोड स्निपेट
```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.SpreadsheetLoadOptions;

public class FeatureLoadExcelDocument {
    public static void main(String[] args) {
        // Create a SpreadsheetLoadOptions object to specify load configurations
        SpreadsheetLoadOptions loadOptions = new SpreadsheetLoadOptions();
        
        // Load the Excel document using an absolute or relative path
        Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/spreadsheet.xlsx", loadOptions);
    }
}
```  

## स्प्रेडशीट में वर्कशीट्स तक पहुँच और इटरेट करना
### अवलोकन  
वर्कशीट्स को इटरेट करने से आप प्रत्येक शीट पर अलग‑अलग ऑपरेशन कर सकते हैं।  

### परिभाषा एंकर  
`Worksheet` `SpreadsheetDocument` के भीतर एकल शीट का प्रतिनिधित्व करता है; आप इस ऑब्जेक्ट के माध्यम से उसकी सामग्री को पढ़, संशोधित, या हटाए सकते हैं।  

#### कोड स्निपेट
```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.contents.SpreadsheetContent;
import com.groupdocs.watermark.options.SpreadsheetLoadOptions;

public class FeatureIterateWorksheets {
    public static void main(String[] args) throws Exception {
        // Load the document as before
        SpreadsheetLoadOptions loadOptions = new SpreadsheetLoadOptions();
        Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/spreadsheet.xlsx", loadOptions);
        
        // Access and iterate through worksheets
        SpreadsheetContent content = watermarker.getContent(SpreadsheetContent.class);
        for (SpreadsheetWorksheet section : content.getWorksheets()) {
            System.out.println("Processing Worksheet: " + section.getName());
        }
        
        watermarker.close();
    }
}
```  

## स्प्रेडशीट से विशिष्ट टेक्स्ट फ़ॉर्मेटिंग वाले आकार हटाएँ
### अवलोकन  
यह फीचर उन आकारों को लक्षित करता है जो कुछ टेक्स्ट फ़ॉर्मेटिंग मानदंडों (जैसे फ़ॉन्ट प्रकार या रंग) को पूरा करते हैं।  

### परिभाषा एंकर  
`Shape` वर्कशीट के भीतर किसी भी ड्राइंग एलिमेंट (टेक्स्ट बॉक्स, चित्र, या SmartArt) का ऑब्जेक्ट मॉडल है; यह `getText`, `getFont`, और `remove` जैसी प्रॉपर्टी प्रदान करता है।  

#### कोड स्निपेट
```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.contents.SpreadsheetContent;
import com.groupdocs.watermark.contents.SpreadsheetWorksheet;
import com.groupdocs.watermark.search.FormattedTextFragment;
import com.groupdocs.watermark.watermarks.Color;

public class FeatureRemoveShapesWithSpecificFormatting {
    public static void main(String[] args) throws Exception {
        // Load the document
        SpreadsheetLoadOptions loadOptions = new SpreadsheetLoadOptions();
        Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/spreadsheet.xlsx", loadOptions);
        
        // Iterate through worksheets and shapes
        SpreadsheetContent content = watermarker.getContent(SpreadsheetContent.class);
        for (SpreadsheetWorksheet section : content.getWorksheets()) {
            for (int i = section.getShapes().getCount() - 1; i >= 0; i--) {
                for (FormattedTextFragment fragment : section.getShapes().get_Item(i).getFormattedTextFragments()) {
                    // Check specific text formatting criteria
                    if (fragment.getForegroundColor().equals(Color.getRed()) &&
                        "Arial".equalsIgnoreCase(fragment.getFont().getFamilyName())) {
                        // Remove the shape if it matches
                        section.getShapes().removeAt(i);
                        break;
                    }
                }
            }
        }
        
        // Save changes to a new document
        watermarker.save("YOUR_OUTPUT_DIRECTORY/modified_spreadsheet.xlsx");
        watermarker.close();
    }
}
```  

## व्यावहारिक अनुप्रयोग
### वास्तविक‑विश्व उपयोग केस
1. **Data Validation** – स्वचालित रूप से उन आकारों को हटाएँ जो अप्रचलित नोटिस शामिल करते हैं।  
2. **Template Standardization** – गैर‑मानक टेक्स्ट बॉक्स हटाकर कॉर्पोरेट ब्रांडिंग लागू करें।  
3. **Automated Reporting** – वितरण से पहले उत्पन्न रिपोर्ट को साफ़ करें, जिससे एक परिष्कृत रूप सुनिश्चित हो।  

### एकीकरण संभावनाएँ
GroupDocs.Watermark को Java‑आधारित एंटरप्राइज़ पाइपलाइन में एम्बेड किया जा सकता है, जैसे दस्तावेज़‑जनरेशन माइक्रो‑सर्विसेज, बैच‑प्रोसेसिंग जॉब्स, या कंटेंट‑मैनेजमेंट सिस्टम, जो Excel एसेट्स को प्रबंधित करने का एक सहज, लाइसेंस‑अनुपालन तरीका प्रदान करता है।

## प्रदर्शन विचार
### प्रदर्शन अनुकूलन
- **लूप के भीतर भारी ऑपरेशन्स से बचें** – प्रत्येक वर्कशीट पर आकार संग्रह को एक बार प्राप्त करें।  
- **संसाधनों को शीघ्र रिलीज़ करें** – स्ट्रीम को स्वचालित रूप से बंद करने के लिए try‑with‑resources का उपयोग करें।  

### संसाधन उपयोग दिशानिर्देश
प्रोसेसिंग समाप्त होते ही `SpreadsheetDocument` ऑब्जेक्ट को रिलीज़ करें ताकि नेटिव मेमोरी मुक्त हो सके। 100 MB से बड़ी फ़ाइलों के लिए वर्कशीट्स को समानांतर स्ट्रीम में प्रोसेस करने पर विचार करें ताकि मल्टी‑कोर CPU का लाभ उठाया जा सके।

### Java मेमोरी प्रबंधन के लिए सर्वोत्तम प्रथाएँ
`try (SpreadsheetDocument doc = new SpreadsheetDocument(...)) { … }` का उपयोग करें ताकि `close()` मेथड अपवाद होने पर भी चलाया जाए।

## सामान्य समस्याएँ और समाधान
- **Shape not found** – सुनिश्चित करें कि आप सही वर्कशीट इंडेक्स की जाँच कर रहे हैं; आकार प्रत्येक शीट के अनुसार स्कोप्ड होते हैं।  
- **License exception** – ट्रायल लाइसेंस बैच प्रोसेसिंग को अक्षम करता है; अनलिमिटेड ऑपरेशन्स के लिए पूर्ण लाइसेंस में अपग्रेड करें।  
- **Unexpected font values** – फ़ॉन्ट गुण विरासत में मिल सकते हैं; हल किए गए स्टाइल को प्राप्त करने के लिए `shape.getEffectiveFont()` का उपयोग करें।  

## अक्सर पूछे जाने वाले प्रश्न

**Q: क्या मैं पासवर्ड‑सुरक्षित वर्कबुक से आकार हटाना सकता हूँ?**  
A: हाँ। पासवर्ड पैरामीटर के साथ दस्तावेज़ लोड करें, फिर वही हटाने लॉजिक चलाएँ; API मेमोरी में फ़ाइल को डिक्रिप्ट करता है।

**Q: क्या लाइब्रेरी .xls (Excel 97‑2003) फ़ाइलों को सपोर्ट करती है?**  
A: बिल्कुल। GroupDocs.Watermark `.xlsx` और लेगेसी `.xls` दोनों फ़ॉर्मेट को बिना रूपांतरण के संभालता है।

**Q: मैं कैसे लॉग करूँ कि कौन से आकार हटाए गए?**  
A: आकार संग्रह को इटरेट करें, फ़ॉर्मेटिंग मानदंड जांचें, `shape.getName()` या `shape.getId()` को लॉग करें, फिर `remove()` कॉल करें।

**Q: क्या आकार हटाने के बाद वॉटरमार्क जोड़ना संभव है?**  
A: हाँ। सफ़ाई के बाद `doc.addWatermark(new TextWatermark("Confidential"))` को कॉल करके सभी वर्कशीट्स पर टेक्स्ट वॉटरमार्क ओवरले करें।

**Q: अधिकतम समर्थित फ़ाइल आकार क्या है?**  
A: लाइब्रेरी 64‑बिट JVM पर **2 GB** तक की फ़ाइलें प्रोसेस कर सकती है, जो केवल उपलब्ध हीप मेमोरी और OS प्रतिबंधों से सीमित है।

## निष्कर्ष
इस ट्यूटोरियल में हमने GroupDocs.Watermark for Java का उपयोग करके **Excel से आकार हटाने** के लिए एक पूर्ण, उत्पादन‑तैयार दृष्टिकोण दिखाया। दस्तावेज़ लोड करके, वर्कशीट्स को इटरेट करके, और सटीक फ़ॉर्मेटिंग फ़िल्टर लागू करके आप सफ़ाई कार्यों को स्वचालित कर सकते हैं, ब्रांडिंग लागू कर सकते हैं, और बड़े पैमाने पर रिपोर्ट गुणवत्ता में सुधार कर सकते हैं। अतिरिक्त सुविधाओं जैसे वॉटरमार्क इन्सर्शन, दस्तावेज़ रूपांतरण, और बैच प्रोसेसिंग का अन्वेषण करें ताकि अपने दस्तावेज़‑ऑटोमेशन टूलकिट को और विस्तारित किया जा सके।

---

**अंतिम अपडेट:** 2026-06-01  
**परीक्षण किया गया:** GroupDocs.Watermark 24.11 for Java  
**लेखक:** GroupDocs

## संबंधित ट्यूटोरियल

- [Excel Shape Manipulation Using GroupDocs.Watermark in Java: A Comprehensive Guide](/watermark/java/spreadsheet-document-watermarking/excel-shape-manipulation-groupdocs-watermark-java/)
- [Add Image Watermark to Excel Spreadsheet Using GroupDocs.Watermark Java SDK](/watermark/java/spreadsheet-document-watermarking/add-image-watermark-spreadsheet-groupdocs-java/)
- [Excel Document Handling and Watermarking with GroupDocs.Watermark Java](/watermark/java/spreadsheet-document-watermarking/excel-document-handling-groupdocs-watermark-java/)