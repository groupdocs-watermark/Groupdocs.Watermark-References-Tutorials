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

# GroupDocs.Watermark for Java के साथ ईमेल अटैचमेंट में वॉटरमार्क जोड़ें

आज के डिजिटल लैंडस्केप में, संवेदनशील जानकारी की सुरक्षा बहुत ज़रूरी है— स्वैच्छिक जब आप अपने इनबॉक्स से बाहर जाने से पहले **ईमेल अटैचमेंट में वॉटरमार्क जोड़ते हैं**। चाहे आप एक डेवलपर हों जो डॉक्यूमेंट सुरक्षा को मुश्किल करना चाहते हैं या कोई व्यवसाय जो हर आउटगोइंग फ़ाइल को ब्रांड करना चाहता है, यह ट्यूटोरियल आपको दिखाता है कि GroupDocs.Watermark for Java का इस्तेमाल करके ईमेल मैसेज के अंदर सभी सपोर्टेड अटैचमेंट पर टेक्स्ट वॉटरमार्क कैसे लागू किया जाए।

## क्विक आंसर
- **“add watermark to email” क्या हासिल करता है?** यह हर सपोर्टेड अटैचमेंट में एक असरदार या अर्ध-पारदर्शी लेबल (जैसे, “Confidential”) एम्बेड करता है, जिससे गोपनीय डिस्ट्रीब्यूशन को नुकसान होता है।

- **कौन सी लाइब्रेरी ज़रूरी है?** GroupDocs.Watermark for Java (नवीनतम रिलीज़)।
- **क्या मुझे लाइसेंस चाहिए?** विकास के लिए ट्रायल लाइसेंस काम करता है; प्रोडक्शन के लिए प्रोफेशनल लाइसेंस ज़रूरी है।

- **क्या मैं एक साथ कई ईमेल प्रोसेस कर सकता हूँ?** हाँ—*.msg* वर्जन के फ़ोल्डर पर लूप लगाकर स्टेप्स को दोहराएँ।

- **कौन से फ़ाइल प्रकार सपोर्टेड हैं?** PDFs, Word, Excel, PowerPoint, इमेजेज और कई अन्य (अधिकारी डॉक्यूमेंट देखें)।

## “add watermark to email” क्या है?

ईमेल में वॉटरमार्क जोड़ना मतलब है प्रोग्रामेटिक रूप से ईमेल फ़ाइल खोलना, हर अटैचमेंट निकालना, और उन डॉक्यूमेंट्स पर कस्टम टेक्स्ट (या इमेज) स्टैम्प करना, इससे पहले कि ईमेल भेजा या भेजा जाए। यह सुनिश्चित करता है कि वॉटरमार्क फ़ाइल के साथ ही यात्रा करे, डिस्क्रिप्शन और ब्रांड आइडेंटिटी को मज़बूत करता है।

## Java के लिए GroupDocs.Watermark का इस्तेमाल क्यों करें?

- **विस्तृत फ़ॉर्मेट सपोर्ट** – PDFs, Office फ़ाइलें, इमेजेज और ज़्यादा के साथ काम करता है।
- **सरल API** – कुछ ही आईएसओ के कोड से आप वॉटरमार्क बना सकते हैं, लागू कर सकते हैं और सेव कर सकते हैं।
- **परफ़ॉर्मेंस‑फ़ोकस्ड** – कम मेमोरी फ़ुटप्रिंट, सर्वर‑साइड प्रोडक्ट के लिए आदर्श।
- **एंटरप्राइज़‑रेडी लाइसेंसिंग** – वैल्यूएशन के लिए ट्रायल, प्रोडक्शन के लिए पेड लाइसेंस।

## ज़रूरी शर्तें
- Java डेवलपमेंट किट (JDK) इंस्टॉल हो।
- IntelliJ IDEA या Eclipse जैसा IDE।
- GroupDocs.Watermark for Java को अपने प्रोजेक्ट में जोड़ें (नीचे सेटअप स्टेप देखें)।

## GroupDocs.Watermark for Java सेट अप करना

### Maven सेटअप
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

### डायरेक्ट डाउनलोड
वैकल्पिक रूप से, नवीनतम संस्करण डाउनलोड करें: [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/)।

#### लाइसेंस लेना
- फ्री ट्रायल के लिए, GroupDocs वेबसाइट पर रजिस्टर करें और एक टेम्पररी लाइसेंस अनुरोध करें।  
- व्यावसायिक उपयोग के लिए, पूर्ण लाइसेंस खरीदें। अधिक जानकारी के लिए [purchase page](https://purchase.groupdocs.com/temporary-license/) देखें।

### बेसिक इनिशियलाइज़ेशन
आपको जिन कोर क्लासेस की आवश्यकता होगी, उन्हें इम्पोर्ट करें:

```java
import com.groupdocs.watermark.Watermarker;
// Other imports as needed...
```
## ईमेल अटैचमेंट में वॉटरमार्क कैसे जोड़ें – स्टेप-बाय-स्टेप गाइड

### स्टेप 1: टेक्स्ट वॉटरमार्क बनाएं
पहले, वॉटरमार्क टेक्स्ट और उसकी दिखावट निर्धारित करें।

```java
import com.groupdocs.watermark.watermarks.Font;
import com.groupdocs.watermark.watermarks.TextWatermark;

// Step 1: Create a text watermark.
TextWatermark watermark = new TextWatermark("Confidential", new Font("Arial", 19));
```

### स्टेप 2: ईमेल लोड ऑप्शन सेट अप करें
लोडर को कॉन्फ़िगर करें ताकि GroupDocs *.msg* फ़ाइल पढ़ सके।

```java
import com.groupdocs.watermark.options.EmailLoadOptions;

// Step 2: Setup the email load options.
EmailLoadOptions loadOptions = new EmailLoadOptions();
```

### स्टेप 3: अपनी ईमेल फ़ाइल के लिए वॉटरमार्कर इनिशियलाइज़ करें
`Watermarker` को उस ईमेल फ़ाइल की ओर इंगित करें जिसे आप प्रोसेस करना चाहते हैं।

```java
import com.groupdocs.watermark.Watermarker;

// Step 3: Initialize the watermarker with your email file.
String emailFilePath = "YOUR_DOCUMENT_DIRECTORY/email_file.msg";
Watermarker watermarker = new Watermarker(emailFilePath, loadOptions);
```

### स्टेप 4: ईमेल कंटेंट पाएं
ईमेल की आंतरिक संरचना प्राप्त करें ताकि आप उसके अटैचमेंट्स के साथ काम कर सकें।

```java
import com.groupdocs.watermark.contents.EmailContent;

// Step 4: Retrieve the email content.
EmailContent content = watermarker.getContent(EmailContent.class);
```

### स्टेप 5: अटैचमेंट पर दोबारा जाएं
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

### स्टेप 6-9: सपोर्टेड अटैचमेंट में वॉटरमार्क जोड़ें
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

### स्टेप 10: वॉटरमार्क वाला ईमेल सेव करें
परिवर्तित ईमेल को नई फ़ाइल में लिखें ताकि मूल फ़ाइल अपरिवर्तित रहे।

```java
// Step 10: Save the modified email.
String outputFilePath = "YOUR_OUTPUT_DIRECTORY/watermarked_email_file.msg";
watermarker.save(outputFilePath);
```

### स्टेप 11: क्लीन अप करें
मुख्य `Watermarker` को बंद करके संसाधनों को रिलीज़ करें।

```java
// Step 11: Close the watermarker for cleanup.
watermarker.close();
```

## प्रैक्टिकल एप्लीकेशन
1. **आंतरिक दस्तावेज़ साझाकरण** – कंपनी का ब्रांडिंग या गोपनीयता नोटिस हर अटैचमेंट में एम्बेड करें, इससे पहले कि वह आंतरिक रूप से वितरित हो।  
2. **क्लाइंट संचार** – कॉन्ट्रैक्ट, प्रस्ताव और वित्तीय स्टेटमेंट्स को स्पष्ट “Confidential” लेबल के साथ सुरक्षित रखें।  
3. **ईमेल मार्केटिंग कैंपेन** – प्रोमोशनल ईमेल में संलग्न PDFs या इमेजेज पर सूक्ष्म ब्रांडिंग वॉटरमार्क जोड़ें, जिससे ब्रांड रीकॉल बढ़े।

## परफॉर्मेंस से जुड़ी बातें
- **Memory Management** – एक समय में एक अटैचमेंट प्रोसेस करें और प्रत्येक `Watermarker` को तुरंत बंद करें।  
- **Attachment Size** – बड़े फ़ाइलों से प्रोसेसिंग समय बढ़ता है; वॉटरमार्किंग से पहले संपीड़न या आकार सीमा पर विचार करें।  
- **Batch Processing** – कई *.msg* फ़ाइलों के डायरेक्टरी पर लूप लगाकर ओवरहेड को कम करें जब बड़ी संख्या में ईमेल हैंडल कर रहे हों।

## अक्सर पूछे जाने वाले सवाल

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

## रिसोर्स
- [Documentation](https://docs.groupdocs.com/watermark/java/)  
- [API Reference](https://reference.groupdocs.com/watermark/java)  
- [Download GroupDocs.Watermark for Java](https://releases.groupdocs.com/watermark/java/)

---

**Last Updated:** 2025-12-29  
**Tested With:** GroupDocs.Watermark 24.11 for Java  
**Author:** GroupDocs