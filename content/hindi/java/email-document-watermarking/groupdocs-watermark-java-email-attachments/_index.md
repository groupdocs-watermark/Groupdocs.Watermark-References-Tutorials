---
date: '2026-04-07'
description: GroupDocs.Watermark for Java का उपयोग करके ईमेल अटैचमेंट्स के लिए टेक्स्ट
  वॉटरमार्क बनाना सीखें, ईमेल अटैचमेंट्स को सुरक्षित करें और गोपनीय डेटा की रक्षा
  करें।
keywords:
- create text watermark
- secure email attachments
- groupdocs watermark java
title: GroupDocs Java के साथ ईमेल अटैचमेंट्स के लिए टेक्स्ट वाटरमार्क बनाएं
type: docs
url: /hi/java/email-document-watermarking/groupdocs-watermark-java-email-attachments/
weight: 1
---

# ईमेल अटैचमेंट्स में वॉटरमार्क जोड़ने के लिए GroupDocs.Watermark for Java का उपयोग कैसे करें

इस ट्यूटोरियल में आप **टेक्स्ट वॉटरमार्क** ऑब्जेक्ट बनाएँगे और उन्हें ईमेल संदेश के भीतर प्रत्येक समर्थित अटैचमेंट पर लागू करेंगे। वॉटरमार्क जोड़ना **ईमेल अटैचमेंट्स को सुरक्षित** करने, गोपनीयता संकेत देने, और ब्रांड पहचान को मजबूत करने का एक प्रभावी तरीका है—सिर्फ कुछ ही जावा कोड लाइनों के साथ।

## परिचय

ईमेल के माध्यम से संवेदनशील जानकारी के प्रवाह की सुरक्षा पहले से कहीं अधिक महत्वपूर्ण हो गई है। चाहे आपको आंतरिक रिपोर्टों पर लेबल लगाना हो, कानूनी अनुबंधों को चिह्नित करना हो, या सिर्फ मार्केटिंग एसेट्स पर ब्रांडिंग करना हो, टेक्स्ट वॉटरमार्क आपको एक हल्का, छेड़छाड़‑प्रकट करने वाला सुरक्षा लेयर देता है। यह गाइड आपको **GroupDocs.Watermark for Java** का उपयोग करके Outlook `.msg` फ़ाइल में प्रत्येक अटैचमेंट पर कस्टम वॉटरमार्क जोड़ने की पूरी प्रक्रिया दिखाता है।

### आप क्या सीखेंगे
- कस्टम फ़ॉन्ट और रंगों के साथ **टेक्स्ट वॉटरमार्क** ऑब्जेक्ट कैसे बनाएं।  
- जावा ईमेल‑प्रोसेसिंग वर्कफ़्लो में वॉटरमार्किंग को चरण‑दर‑चरण एकीकृत करना।  
- बड़े अटैचमेंट्स को संभालते समय प्रदर्शन को अनुकूलित करने के टिप्स।  
- वास्तविक‑दुनिया के परिदृश्य जहाँ ईमेल अटैचमेंट्स पर वॉटरमार्किंग मूल्य जोड़ता है।

आइए यह सुनिश्चित करें कि आपके पास सब कुछ है, फिर आगे बढ़ते हैं।

## त्वरित उत्तर
- **“create text watermark” का क्या अर्थ है?** इसका मतलब है एक `TextWatermark` ऑब्जेक्ट बनाना जो दृश्य टेक्स्ट, फ़ॉन्ट, आकार और शैली को परिभाषित करता है जिसे दस्तावेज़ पर ओवरले किया जाएगा।  
- **क्या मैं एन्क्रिप्टेड अटैचमेंट्स पर वॉटरमार्क लगा सकता हूँ?** नहीं – सुरक्षा कारणों से GroupDocs.Watermark एन्क्रिप्टेड फ़ाइलों को सपोर्ट नहीं करता।  
- **कौन‑से फ़ाइल प्रकार समर्थित हैं?** PDFs, Word, Excel, PowerPoint, इमेजेज, और कई अन्य – पूरी सूची के लिए आधिकारिक डॉक्यूमेंट देखें।  
- **क्या मुझे लाइसेंस चाहिए?** विकास के लिए ट्रायल लाइसेंस काम करता है; प्रोडक्शन उपयोग के लिए कमर्शियल लाइसेंस आवश्यक है।  
- **प्रक्रिया कितनी तेज़ है?** सामान्य 2 MB अटैचमेंट को आधुनिक हार्डवेयर पर एक सेकंड से कम समय में वॉटरमार्क किया जा सकता है।

## पूर्वापेक्षाएँ

- **Java Development Kit (JDK)** – संस्करण 8 या नया।  
- IntelliJ IDEA या Eclipse जैसे IDE।  
- **GroupDocs.Watermark for Java** को अपने प्रोजेक्ट में जोड़ें (नीचे सेटअप चरण देखें)।  
- एक ईमेल फ़ाइल (`.msg`, `.eml`, आदि) तक पहुँच जो उन अटैचमेंट्स को रखती हो जिन्हें आप सुरक्षित करना चाहते हैं।

## GroupDocs.Watermark for Java सेटअप

### Maven सेटअप

यदि आप Maven से डिपेंडेंसीज़ मैनेज करते हैं, तो अपने `pom.xml` में रिपॉज़िटरी और डिपेंडेंसी जोड़ें:

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

वैकल्पिक रूप से, आधिकारिक साइट से नवीनतम JAR डाउनलोड करें:  
[GroupDocs.Watermark for Java रिलीज़](https://releases.groupdocs.com/watermark/java/)

#### लाइसेंस प्राप्ति
- **ट्रायल:** GroupDocs वेबसाइट पर रजिस्टर करें और एक अस्थायी लाइसेंस अनुरोध करें।  
- **कमर्शियल:** यहाँ पूर्ण लाइसेंस खरीदें: [purchase page](https://purchase.groupdocs.com/temporary-license/)।

### बेसिक इनिशियलाइज़ेशन

अपने जावा सोर्स फ़ाइल में आवश्यक कोर क्लासेज़ इम्पोर्ट करें:

```java
import com.groupdocs.watermark.Watermarker;
// Other imports as needed...
```

## टेक्स्ट वॉटरमार्क क्या है?

एक **टेक्स्ट वॉटरमार्क** एक अर्ध‑पारदर्शी टेक्स्ट का टुकड़ा है जो दस्तावेज़ के प्रत्येक पृष्ठ के ऊपर रेंडर किया जाता है। GroupDocs.Watermark के साथ आप फ़ॉन्ट, आकार, रंग, रोटेशन, और अपारदर्शिता को नियंत्रित कर सकते हैं, जिससे आप मूल सामग्री के साथ स्वाभाविक रूप से मिश्रित ब्रांडिंग या गोपनीयता नोटिस बना सकते हैं।

## ईमेल अटैचमेंट्स के लिए GroupDocs.Watermark का उपयोग क्यों करें?

- **ईमेल अटैचमेंट्स को सुरक्षित** करें उन्हें स्पष्ट रूप से गोपनीय के रूप में चिह्नित करके।  
- **ब्रांड स्थिरता** बनाए रखें सभी आउटगोइंग दस्तावेज़ों में।  
- **बैच‑प्रोसेस** कई ईमेल को एक लूप से प्रोसेस करें, समय बचाएँ और मैन्युअल त्रुटियों को घटाएँ।  
- **क्रॉस‑फ़ॉर्मेट सपोर्ट** – वही कोड PDFs, Word फ़ाइलों, इमेजेज आदि के लिए काम करता है।

## इम्प्लीमेंटेशन गाइड

हम प्रत्येक चरण को विस्तार से बताएँगे, कोड के पीछे का *क्यों* समझाएँगे ताकि आप इसे अपने प्रोजेक्ट में अनुकूलित कर सकें।

### चरण 1: टेक्स्ट वॉटरमार्क बनाएं

पहले, `TextWatermark` को इच्छित टेक्स्ट और फ़ॉन्ट सेटिंग्स के साथ इंस्टैंशिएट करें।

```java
import com.groupdocs.watermark.watermarks.Font;
import com.groupdocs.watermark.watermarks.TextWatermark;

// Step 1: Create a text watermark.
TextWatermark watermark = new TextWatermark("Confidential", new Font("Arial", 19));
```

> **प्रो टिप:** फ़ॉन्ट आकार या रंग को अपने कॉरपोरेट स्टाइल गाइड के अनुसार समायोजित करें। यदि आपको अधिक सूक्ष्म प्रभाव चाहिए तो `watermark.setOpacity(0.5)` के माध्यम से अपारदर्शिता सेट कर सकते हैं।

### चरण 2: ईमेल लोड विकल्प सेट करें

`EmailLoadOptions` लाइब्रेरी को बताता है कि आने वाली ईमेल फ़ाइल को कैसे इंटरप्रेट किया जाए।

```java
import com.groupdocs.watermark.options.EmailLoadOptions;

// Step 2: Setup the email load options.
EmailLoadOptions loadOptions = new EmailLoadOptions();
```

### चरण 3: अपने ईमेल फ़ाइल के लिए Watermarker इनिशियलाइज़ करें

`Watermarker` कन्स्ट्रक्टर को उस `.msg` (या `.eml`) फ़ाइल की ओर इंगित करें जिसे आप प्रोसेस करना चाहते हैं।

```java
import com.groupdocs.watermark.Watermarker;

// Step 3: Initialize the watermarker with your email file.
String emailFilePath = "YOUR_DOCUMENT_DIRECTORY/email_file.msg";
Watermarker watermarker = new Watermarker(emailFilePath, loadOptions);
```

### चरण 4: ईमेल कंटेंट प्राप्त करें

ईमेल की आंतरिक संरचना निकालें ताकि आप उसके अटैचमेंट्स पर लूप कर सकें।

```java
import com.groupdocs.watermark.contents.EmailContent;

// Step 4: Retrieve the email content.
EmailContent content = watermarker.getContent(EmailContent.class);
```

### चरण 5: अटैचमेंट्स पर इटररेट करें

प्रत्येक अटैचमेंट के लिए, हम जांचते हैं कि फ़ाइल प्रकार समर्थित है और वह एन्क्रिप्टेड नहीं है।

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

### चरण 6‑9: समर्थित अटैचमेंट्स में वॉटरमार्क जोड़ें

शर्तीय ब्लॉक के भीतर, हम अटैचमेंट के लिए एक समर्पित `Watermarker` बनाते हैं, वॉटरमार्क लागू करते हैं, और फिर संशोधित कंटेंट को ईमेल में वापस पुश करते हैं।

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

### चरण 10: वॉटरमार्क्ड ईमेल सहेजें

अपडेटेड ईमेल को एक नई फ़ाइल में लिखें ताकि मूल फ़ाइल अपरिवर्तित रहे।

```java
// Step 10: Save the modified email.
String outputFilePath = "YOUR_OUTPUT_DIRECTORY/watermarked_email_file.msg";
watermarker.save(outputFilePath);
```

### चरण 11: क्लीन अप

संसाधनों को रिलीज़ करना न भूलें ताकि मेमोरी लीक्स न हों।

```java
// Step 11: Close the watermarker for cleanup.
watermarker.close();
```

## सामान्य समस्याएँ और समाधान

| समस्या | कारण | समाधान |
|-------|--------|-----|
| **वॉटरमार्क दिखाई नहीं दे रहा** | अपारदर्शिता बहुत कम सेट है या फ़ॉन्ट रंग पृष्ठभूमि से मेल खाता है। | अपारदर्शिता बढ़ाएँ (`watermark.setOpacity(0.7)`) या कंट्रास्टिंग रंग चुनें। |
| **असमर्थित अटैचमेंट प्रकार** | फ़ाइल फ़ॉर्मेट GroupDocs द्वारा समर्थित सूची में नहीं है। | फ़ाइल को पहले समर्थित फ़ॉर्मेट (जैसे PDF) में बदलें या लॉग संदेश के साथ इसे स्किप करें। |
| **बड़े PDFs पर OutOfMemoryError** | बहुत बड़े अटैचमेंट लोड करने से हीप बहुत अधिक उपयोग हो जाता है। | JVM हीप बढ़ाएँ (`-Xmx2g`) या अटैचमेंट्स को छोटे बैच में प्रोसेस करें। |

## अक्सर पूछे जाने वाले प्रश्न

**Q:** क्या मैं एन्क्रिप्टेड फ़ाइलों पर वॉटरमार्क लगा सकता हूँ?  
**A:** नहीं, GroupDocs.Watermark सुरक्षा प्रतिबंधों के कारण एन्क्रिप्टेड फ़ाइलों पर वॉटरमार्क जोड़ने का समर्थन नहीं करता।

**Q:** वॉटरमार्किंग के लिए कौन‑से फ़ाइल प्रकार समर्थित हैं?  
**A:** समर्थित प्रकारों में PDFs, Word दस्तावेज़, Excel स्प्रेडशीट, PowerPoint प्रेज़ेंटेशन, और सामान्य इमेज फ़ॉर्मेट शामिल हैं। पूरी सूची के लिए आधिकारिक डॉक्यूमेंटेशन देखें।

**Q:** मैं अपने वॉटरमार्क की उपस्थिति कैसे कस्टमाइज़ करूँ?  
**A:** `Font` क्लास का उपयोग करके आकार, शैली और रंग सेट करें, और `TextWatermark` इंस्टेंस पर `setOpacity` तथा `setRotationAngle` जैसे मेथड कॉल करें।

**Q:** क्या कई ईमेल को बैच में प्रोसेस करना संभव है?  
**A:** हाँ। पूरे वर्कफ़्लो को एक लूप में लपेटें जो डायरेक्टरी में फ़ाइलों पर इटररेट करे, और दक्षता के लिए वही `TextWatermark` इंस्टेंस पुनः उपयोग करें।

**Q:** मेरा वॉटरमार्क अंतिम पृष्ठ पर कट रहा है—क्या समस्या है?  
**A:** सुनिश्चित करें कि वॉटरमार्क पेज मार्जिन के भीतर फिट हो। आप उसकी पोज़िशन `watermark.setHorizontalAlignment` और `watermark.setVerticalAlignment` से समायोजित कर सकते हैं।

## व्यावहारिक अनुप्रयोग

1. **आंतरिक दस्तावेज़ शेयरिंग:** रिपोर्ट्स को पूरे संगठन में वितरित करने से पहले कंपनी ब्रांडिंग या गोपनीयता नोटिस एम्बेड करें।  
2. **क्लाइंट कम्युनिकेशन:** अनुबंधों और प्रस्तावों को “Confidential” टैग करके प्राप्तकर्ताओं को डेटा हैंडलिंग नीतियों की याद दिलाएँ।  
3. **ईमेल मार्केटिंग:** न्यूज़लेटर्स में संलग्न प्रोमोशनल PDFs पर सूक्ष्म ब्रांड वॉटरमार्क जोड़ें, जिससे डिज़ाइन बाधित हुए बिना ब्रांड रीकॉल बढ़े।

## प्रदर्शन संबंधी विचार

- **मेमोरी मैनेजमेंट:** प्रत्येक `attachedWatermarker` को तुरंत बंद करें (जैसा कि चरण 9 में दिखाया गया है) ताकि नेटिव रिसोर्सेज़ मुक्त हों।  
- **फ़ाइल साइज लिमिट:** 10 MB से बड़े अटैचमेंट्स के लिए स्ट्रीमिंग या JVM हीप साइज बढ़ाने पर विचार करें।  
- **पैरेलल प्रोसेसिंग:** कई ईमेल को एक साथ वॉटरमार्क करने के लिए Java के `ExecutorService` का उपयोग करें, लेकिन CPU उपयोग को मॉनिटर करें ताकि कंटेंशन न हो।

## निष्कर्ष

अब आपके पास एक पूर्ण, प्रोडक्शन‑रेडी रेसिपी है कि कैसे **टेक्स्ट वॉटरमार्क** ऑब्जेक्ट बनाकर उन्हें जावा के साथ GroupDocs.Watermark का उपयोग करके ईमेल फ़ाइल के प्रत्येक समर्थित अटैचमेंट पर लागू किया जाए। इस वर्कफ़्लो को अपने मौजूदा ईमेल‑हैंडलिंग पाइपलाइन में इंटीग्रेट करके आप दस्तावेज़ सुरक्षा बढ़ा सकते हैं, ब्रांडिंग लागू कर सकते हैं, और न्यूनतम ओवरहेड के साथ अनुपालन बनाए रख सकते हैं।

अगला कदम उठाने के लिए तैयार हैं? कोड को विस्तारित करके `.msg` फ़ाइलों के पूरे फ़ोल्डर को प्रोसेस करने की कोशिश करें, या इमेजेज़ और QR कोड जैसे अतिरिक्त वॉटरमार्क प्रकारों का अन्वेषण करें।

---

**अंतिम अपडेट:** 2026-04-07  
**के साथ परीक्षण किया गया:** GroupDocs.Watermark 24.11 for Java  
**लेखक:** GroupDocs  

**संसाधन**  
- [डॉक्यूमेंटेशन](https://docs.groupdocs.com/watermark/java/)  
- [API रेफ़रेंस](https://reference.groupdocs.com/watermark/java)  
- [GroupDocs.Watermark for Java डाउनलोड करें](https://releases.groupdocs.com/watermark/java/)