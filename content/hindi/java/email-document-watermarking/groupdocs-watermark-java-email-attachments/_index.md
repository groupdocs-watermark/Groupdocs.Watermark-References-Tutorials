---
date: '2025-12-29'
description: GroupDocs.Watermark for Java का उपयोग करके ईमेल अटैचमेंट्स में वॉटरमार्क
  कैसे जोड़ें, सीखें। यह गाइड चरण‑दर‑चरण निर्देश और सर्वोत्तम प्रथाएँ प्रदान करता
  है।
keywords:
- GroupDocs Watermark Java
- Java email attachment watermarking
- watermarking with GroupDocs
title: GroupDocs.Watermark for Java के साथ ईमेल अटैचमेंट्स में वॉटरमार्क जोड़ें
type: docs
url: /hi/java/email-document-watermarking/groupdocs-watermark-java-email-attachments/
weight: 1
---

# GroupDocs.Watermark for Java के साथ ईमेल अटैचमेंट्स में वॉटरमार्क जोड़ें

आज के डिजिटल परिदृश्य में, संवेदनशील जानकारी की सुरक्षा अत्यंत महत्वपूर्ण है—विशेषकर जब आप अपने इनबॉक्स से बाहर जाने से पहले **ईमेल अटैचमेंट्स में वॉटरमार्क जोड़ते** हैं। चाहे आप एक डेवलपर हों जो दस्तावेज़ सुरक्षा को कड़ा करना चाहते हैं या कोई व्यवसाय जो प्रत्येक आउटगोइंग फ़ाइल को ब्रांड करना चाहता है, यह ट्यूटोरियल आपको दिखाता है कि GroupDocs.Watermark for Java का उपयोग करके ईमेल संदेश के भीतर सभी समर्थित अटैचमेंट्स पर टेक्स्ट वॉटरमार्क कैसे लागू किया जाए।

## Quick Answers
- **“add watermark to email” क्या हासिल करता है?** यह प्रत्येक समर्थित अटैचमेंट में एक दृश्यमान या अर्ध‑पारदर्शी लेबल (जैसे, “Confidential”) एम्बेड करता है, जिससे अनधिकृत वितरण को हतोत्साहित किया जाता है।  
- **कौन सी लाइब्रेरी आवश्यक है?** GroupDocs.Watermark for Java (नवीनतम रिलीज)।  
- **क्या मुझे लाइसेंस चाहिए?** विकास के लिए ट्रायल लाइसेंस काम करता है; उत्पादन के लिए व्यावसायिक लाइसेंस आवश्यक है।  
- **क्या मैं एक साथ कई ईमेल प्रोसेस कर सकता हूँ?** हाँ—*.msg* फ़ाइलों के फ़ोल्डर पर लूप लगाकर चरणों को दोहराएँ।  
- **कौन से फ़ाइल प्रकार समर्थित हैं?** PDFs, Word, Excel, PowerPoint, इमेजेज और कई अन्य (आधिकारिक दस्तावेज़ देखें)।

## “add watermark to email” क्या है?
ईमेल में वॉटरमार्क जोड़ना मतलब है प्रोग्रामेटिक रूप से ईमेल फ़ाइल खोलना, प्रत्येक अटैचमेंट निकालना, और उन दस्तावेज़ों पर कस्टम टेक्स्ट (या इमेज) स्टैम्प करना, इससे पहले कि ईमेल भेजा या संग्रहीत किया जाए। यह सुनिश्चित करता है कि वॉटरमार्क फ़ाइल के साथ ही यात्रा करे, गोपनीयता और ब्रांड पहचान को मजबूत करता है।

## क्यों उपयोग करें GroupDocs.Watermark for Java?
- **विस्तृत फ़ॉर्मेट सपोर्ट** – PDFs, Office फ़ाइलें, इमेजेज और अधिक के साथ काम करता है।  
- **सरल API** – कुछ ही लाइनों के कोड से आप वॉटरमार्क बना, लागू और सेव कर सकते हैं।  
- **परफ़ॉर्मेंस‑फ़ोकस्ड** – कम मेमोरी फ़ुटप्रिंट, सर्वर‑साइड प्रोसेसिंग के लिए आदर्श।  
- **एंटरप्राइज़‑रेडी लाइसेंसिंग** – मूल्यांकन के लिए ट्रायल, उत्पादन के लिए पेड लाइसेंस।

## Prerequisites
- Java Development Kit (JDK) स्थापित हो।  
- IntelliJ IDEA या Eclipse जैसा IDE।  
- GroupDocs.Watermark for Java को अपने प्रोजेक्ट में जोड़ें (नीचे सेटअप चरण देखें)।  

## Setting Up GroupDocs.Watermark for Java

### Maven Setup
यदि आप Maven उपयोग करते हैं, तो अपने `pom.xml` में रिपॉज़िटरी और डिपेंडेंसी जोड़ें:

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

### Direct Download
वैकल्पिक रूप से, नवीनतम संस्करण डाउनलोड करें: [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/)।

#### License Acquisition
- फ्री ट्रायल के लिए, GroupDocs वेबसाइट पर रजिस्टर करें और एक टेम्पररी लाइसेंस अनुरोध करें।  
- व्यावसायिक उपयोग के लिए, पूर्ण लाइसेंस खरीदें। अधिक जानकारी के लिए [purchase page](https://purchase.groupdocs.com/temporary-license/) देखें।

### Basic Initialization
आपको जिन कोर क्लासेस की आवश्यकता होगी, उन्हें इम्पोर्ट करें:

```java
import com.groupdocs.watermark.Watermarker;
// Other imports as needed...
```

## How to add watermark to email attachments – Step‑by‑Step Guide

### Step 1: Create a Text Watermark
पहले, वॉटरमार्क टेक्स्ट और उसकी दिखावट निर्धारित करें।

```java
import com.groupdocs.watermark.watermarks.Font;
import com.groupdocs.watermark.watermarks.TextWatermark;

// Step 1: Create a text watermark.
TextWatermark watermark = new TextWatermark("Confidential", new Font("Arial", 19));
```

### Step 2: Set Up Email Load Options
लोडर को कॉन्फ़िगर करें ताकि GroupDocs *.msg* फ़ाइल पढ़ सके।

```java
import com.groupdocs.watermark.options.EmailLoadOptions;

// Step 2: Setup the email load options.
EmailLoadOptions loadOptions = new EmailLoadOptions();
```

### Step 3: Initialize Watermarker for Your Email File
`Watermarker` को उस ईमेल फ़ाइल की ओर इंगित करें जिसे आप प्रोसेस करना चाहते हैं।

```java
import com.groupdocs.watermark.Watermarker;

// Step 3: Initialize the watermarker with your email file.
String emailFilePath = "YOUR_DOCUMENT_DIRECTORY/email_file.msg";
Watermarker watermarker = new Watermarker(emailFilePath, loadOptions);
```

### Step 4: Retrieve Email Content
ईमेल की आंतरिक संरचना प्राप्त करें ताकि आप उसके अटैचमेंट्स के साथ काम कर सकें।

```java
import com.groupdocs.watermark.contents.EmailContent;

// Step 4: Retrieve the email content.
EmailContent content = watermarker.getContent(EmailContent.class);
```

### Step 5: Iterate Over Attachments
प्रत्येक अटैचमेंट पर लूप लगाएँ और जाँचें कि क्या उसे वॉटरमार्क किया जा सकता है।

```java
import com.groupdocs.watermark.common.FileType;
import com.groupdocs.watermark.contents.EmailAttachment;
import com.groupdocs.watermark.common.IDocumentInfo;

// Step 5: Process each attachment.
for (EmailAttachment attachment : content.getAttachments()) {
    IDocumentInfo info = attachment.getDocumentInfo();
    
    // Check if file type is supported and not encrypted
    if (info.getFileType() != FileType.Unknown && !info.isEncrypted()) {
        // Proceed with watermarking...
    }
}
```

### Step 6‑9: Add Watermark to Supported Attachments
हर योग्य फ़ाइल को नए `Watermarker` से खोलें, वॉटरमार्क लागू करें, और परिवर्तन को ईमेल में वापस लिखें।

```java
// Step 6: Create a watermarker for the attached document.
Watermarker attachedWatermarker = attachment.createWatermarker();

// Step 7: Apply the text watermark.
attachedWatermarker.add(watermark);

// Step 8: Update with the new content.
attachment.updateContent(attachedWatermarker);

// Step 9: Close the attached watermarker.
attachedWatermarker.close();
```

### Step 10: Save the Watermarked Email
परिवर्तित ईमेल को नई फ़ाइल में लिखें ताकि मूल फ़ाइल अपरिवर्तित रहे।

```java
// Step 10: Save the modified email.
String outputFilePath = "YOUR_OUTPUT_DIRECTORY/watermarked_email_file.msg";
watermarker.save(outputFilePath);
```

### Step 11: Clean Up
मुख्य `Watermarker` को बंद करके संसाधनों को रिलीज़ करें।

```java
// Step 11: Close the watermarker for cleanup.
watermarker.close();
```

## Practical Applications
1. **आंतरिक दस्तावेज़ साझाकरण** – कंपनी का ब्रांडिंग या गोपनीयता नोटिस हर अटैचमेंट में एम्बेड करें, इससे पहले कि वह आंतरिक रूप से वितरित हो।  
2. **क्लाइंट संचार** – कॉन्ट्रैक्ट, प्रस्ताव और वित्तीय स्टेटमेंट्स को स्पष्ट “Confidential” लेबल के साथ सुरक्षित रखें।  
3. **ईमेल मार्केटिंग कैंपेन** – प्रोमोशनल ईमेल में संलग्न PDFs या इमेजेज पर सूक्ष्म ब्रांडिंग वॉटरमार्क जोड़ें, जिससे ब्रांड रीकॉल बढ़े।

## Performance Considerations
- **Memory Management** – एक समय में एक अटैचमेंट प्रोसेस करें और प्रत्येक `Watermarker` को तुरंत बंद करें।  
- **Attachment Size** – बड़े फ़ाइलों से प्रोसेसिंग समय बढ़ता है; वॉटरमार्किंग से पहले संपीड़न या आकार सीमा पर विचार करें।  
- **Batch Processing** – कई *.msg* फ़ाइलों के डायरेक्टरी पर लूप लगाकर ओवरहेड को कम करें जब बड़ी संख्या में ईमेल हैंडल कर रहे हों।

## Frequently Asked Questions

**Q: क्या मैं एन्क्रिप्टेड फ़ाइलों में वॉटरमार्क जोड़ सकता हूँ?**  
A: नहीं। सुरक्षा कारणों से GroupDocs.Watermark एन्क्रिप्टेड दस्तावेज़ों में वॉटरमार्किंग का समर्थन नहीं करता।

**Q: वॉटरमार्किंग के लिए कौन से फ़ाइल प्रकार समर्थित हैं?**  
A: PDFs, Word, Excel, PowerPoint, इमेजेज (PNG, JPEG, BMP) और कई अन्य सामान्य फ़ॉर्मेट। पूर्ण सूची के लिए आधिकारिक दस्तावेज़ देखें।

**Q: मैं अपने वॉटरमार्क की दिखावट कैसे कस्टमाइज़ करूँ?**  
A: आप `TextWatermark` कंस्ट्रक्टर और उसकी प्रॉपर्टीज़ के माध्यम से फ़ॉन्ट फ़ैमिली, साइज, रंग, अपारदर्शिता, रोटेशन और पोज़िशन बदल सकते हैं।

**Q: क्या कई ईमेल का बैच प्रोसेसिंग संभव है?**  
A: हाँ। एक `for` लूप में चरणों को रखकर *.msg* फ़ाइलों के फ़ोल्डर पर इटरेट करें और प्रत्येक पर समान लॉजिक लागू करें।

**Q: मेरा वॉटरमार्क दिखाई नहीं दे रहा है—मैं क्या जांचूँ?**  
A: सुनिश्चित करें कि अटैचमेंट का फ़ाइल टाइप समर्थित है, वॉटरमार्क का आकार पेज डाइमेंशन में फिट हो, और दस्तावेज़ पासवर्ड‑प्रोटेक्टेड न हो।

## Resources
- [Documentation](https://docs.groupdocs.com/watermark/java/)  
- [API Reference](https://reference.groupdocs.com/watermark/java)  
- [Download GroupDocs.Watermark for Java](https://releases.groupdocs.com/watermark/java/)

---

**Last Updated:** 2025-12-29  
**Tested With:** GroupDocs.Watermark 24.11 for Java  
**Author:** GroupDocs