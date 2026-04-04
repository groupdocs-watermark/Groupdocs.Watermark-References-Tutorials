---
date: '2026-04-04'
description: GroupDocs.Watermark for Java का उपयोग करके Excel अटैचमेंट्स को निकालना
  और एम्बेडेड ऑब्जेक्ट्स को निकालना सीखें। अपने दस्तावेज़ प्रबंधन को कुशलतापूर्वक
  सुव्यवस्थित करें।
keywords:
- how to extract excel
- extract embedded objects
- java attachment extraction
title: GroupDocs Watermark Java के साथ Excel अटैचमेंट्स निकालने का तरीका
type: docs
url: /hi/java/email-document-watermarking/extract-attachments-excel-groupdocs-watermark-java/
weight: 1
---

# GroupDocs.Watermark Java के साथ Excel अटैचमेंट निकालने का तरीका

Excel वर्कबुक से एम्बेडेड फ़ाइलों को निकालना डेटा पाइपलाइन को ऑटोमेट करने या आर्काइविंग समाधान बनाने पर एक वास्तविक बाधा बन सकता है। इस ट्यूटोरियल में आप GroupDocs.Watermark लाइब्रेरी for Java का उपयोग करके **Excel निकालने का तरीका** अटैचमेंट्स को जल्दी और भरोसेमंद तरीके से निकालना सीखेंगे। हम पर्यावरण सेटअप, कोड walkthrough, और व्यावहारिक टिप्स को कवर करेंगे ताकि आप इस क्षमता को तुरंत अपने अनुप्रयोगों में एकीकृत कर सकें।

## त्वरित उत्तर
- **Excel अटैचमेंट्स को संभालने वाली लाइब्रेरी कौन सी है?** GroupDocs.Watermark for Java  
- **प्रमुख उपयोग किया गया मेथड?** `Watermarker` with `SpreadsheetLoadOptions`  
- **क्या मुझे लाइसेंस चाहिए?** विकास के लिए एक फ्री ट्रायल काम करता है; उत्पादन के लिए पूर्ण लाइसेंस आवश्यक है  
- **समर्थित Java संस्करण?** Java 8 या उससे ऊपर  
- **क्या मैं प्रीव्यू इमेज निकाल सकता हूँ?** हाँ, `getPreviewImageContent()` के माध्यम से  

## दस्तावेज़ ऑटोमेशन के संदर्भ में “how to extract excel” क्या है?
जब हम *how to extract excel* कहते हैं, तो हम प्रोग्रामेटिक रूप से किसी भी एम्बेडेड ऑब्जेक्ट—जैसे PDFs, इमेजेज, या अन्य स्प्रेडशीट्स—को `.xlsx` फ़ाइल के भीतर से निकालने की बात कर रहे होते हैं। यह डेटा विश्लेषण, अनुपालन आर्काइविंग, या डायनेमिक रिपोर्ट जनरेशन जैसी डाउनस्ट्रीम प्रक्रियाओं को बिना मैन्युअल उपयोगकर्ता इंटरैक्शन के सक्षम बनाता है।

## Java के लिए GroupDocs.Watermark क्यों उपयोग करें?
GroupDocs.Watermark एक हाई‑लेवल API प्रदान करता है जो लो‑लेवल OpenXML हैंडलिंग को एब्स्ट्रैक्ट करता है, जिससे आपको मिलता है:
- **सरल ऑब्जेक्ट मॉडल** worksheets, attachments, और metadata के लिए  
- **इनबिल्ट प्रीव्यू एक्सट्रैक्शन** तेज़ विज़ुअल चेक्स के लिए  
- **मजबूत लाइसेंसिंग** जो ट्रायल से एंटरप्राइज़ तक स्केल करती है  

## आवश्यकताएँ
- **Java Development Kit (JDK) 8+** – स्थापित और आपके `PATH` में जोड़ा गया  
- **IDE** – IntelliJ IDEA, Eclipse, या कोई भी एडिटर जो आप पसंद करते हैं  
- **Maven** – डिपेंडेंसी मैनेजमेंट के लिए (वैकल्पिक रूप से आप JAR डाउनलोड कर सकते हैं)  

### आवश्यक लाइब्रेरी और डिपेंडेंसीज़
आपको GroupDocs.Watermark for Java लाइब्रेरी की आवश्यकता होगी। इस ट्यूटोरियल में संस्करण 24.11 उपयोग किया गया है, जिसे आप Maven Central या आधिकारिक GroupDocs रिपॉज़िटरी से प्राप्त कर सकते हैं।

### प्रत्यक्ष डाउनलोड लिंक (असंशोधित)
वैकल्पिक रूप से, नवीनतम संस्करण को यहाँ से डाउनलोड करें: [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

## Java के लिए GroupDocs.Watermark सेटअप करना
### Maven सेटअप
अपने `pom.xml` फ़ाइल में निम्न कॉन्फ़िगरेशन जोड़ें:

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

### लाइसेंस प्राप्त करने के चरण
- **फ्री ट्रायल:** लाइब्रेरी की क्षमताओं को एक्सप्लोर करने के लिए फ्री ट्रायल से शुरू करें।  
- **अस्थायी लाइसेंस:** विस्तारित विकास उपयोग के लिए एक अस्थायी लाइसेंस प्राप्त करें।  
- **खरीदें:** उत्पादन डिप्लॉयमेंट के लिए पूर्ण लाइसेंस में अपग्रेड करें।  

### बुनियादी इनिशियलाइज़ेशन और सेटअप
```java
import com.groupdocs.watermark.Watermarker;

public class DocumentSetup {
    public static void main(String[] args) {
        String filePath = "YOUR_DOCUMENT_DIRECTORY/spreadsheet.xlsx";
        Watermarker watermarker = new Watermarker(filePath);
        
        // Your code to manipulate the document goes here
        
        watermarker.close();
    }
}
```

## GroupDocs.Watermark का उपयोग करके Excel अटैचमेंट्स निकालना
### स्प्रेडशीट लोड और तैयार करना
**अवलोकन:** मेमोरी उपयोग और लोडिंग व्यवहार को नियंत्रित करने के लिए `SpreadsheetLoadOptions` के साथ अपना वर्कबुक लोड करें।

```java
import com.groupdocs.watermark.options.SpreadsheetLoadOptions;
import com.groupdocs.watermark.Watermarker;

public class ExtractAttachments {
    public static void extract() {
        SpreadsheetLoadOptions loadOptions = new SpreadsheetLoadOptions();
        String filePath = "YOUR_DOCUMENT_DIRECTORY/spreadsheet.xlsx";
        
        Watermarker watermarker = new Watermarker(filePath, loadOptions);
```

### स्प्रेडशीट कंटेंट तक पहुंच
**अवलोकन:** हाई‑लेवल कंटेंट मॉडल प्राप्त करें जो आपको worksheets और एम्बेडेड ऑब्जेक्ट्स तक पहुंच देता है।

```java
import com.groupdocs.watermark.contents.SpreadsheetContent;

// Get the content of the spreadsheet.
SpreadsheetContent content = watermarker.getContent(SpreadsheetContent.class);
```

### worksheets के माध्यम से इटररेट करना
**अवलोकन:** प्रत्येक worksheet और फिर प्रत्येक अटैचमेंट पर लूप करें ताकि उन्हें व्यक्तिगत रूप से प्रोसेस किया जा सके।

```java
import com.groupdocs.watermark.contents.SpreadsheetWorksheet;

for (SpreadsheetWorksheet worksheet : content.getWorksheets()) {
    for (SpreadsheetAttachment attachment : worksheet.getAttachments()) {
```

### अटैचमेंट विवरण निकालना
**अवलोकन:** प्रत्येक अटैचमेंट के लिए उपयोगी मेटाडाटा जैसे वैकल्पिक टेक्स्ट, पोजीशन, साइज, और वास्तविक फ़ाइल बाइट्स निकालें।

```java
import com.groupdocs.watermark.contents.SpreadsheetAttachment;

// Display alternative text and frame details of each attachment.
System.out.println("Alternative text: " + attachment.getAlternativeText());
System.out.println("Attachment frame x-coordinate: " + attachment.getX());
System.out.println("Attachment frame y-coordinate: " + attachment.getY());
System.out.println("Attachment frame width: " + attachment.getWidth());
System.out.println("Attachment frame height: " + attachment.getHeight());

// Check if a preview image is available and display its size.
int imageSize = (attachment.getPreviewImageContent() != null) ? attachment.getPreviewImageContent().length : 0;
System.out.println("Preview image size: " + imageSize);

if (attachment.isLink()) {
    System.out.println("Full path to the attached file: " + attachment.getSourceFullName());
} else {
    System.out.println("File type: " + attachment.getDocumentInfo().getFileType());
    System.out.println("Name of the source file: " + attachment.getSourceFullName());
    System.out.println("File size: " + attachment.getContent().length);
}
```

### रिसोर्सेज बंद करना
**अवलोकन:** हमेशा `Watermarker` इंस्टेंस को बंद करें ताकि नेटिव रिसोर्सेज मुक्त हों और मेमोरी लीक्स से बचा जा सके।

```java
// Close the Watermarker to release resources.
watermarker.close();
```

## व्यावहारिक अनुप्रयोग (यह क्यों महत्वपूर्ण है)
1. **ऑटोमेटेड डेटा कंसॉलिडेशन** – रिपोर्टों के बैच से प्रत्येक अटैच्ड PDF या इमेज को एकल एनालिटिक्स रन के लिए निकालें।  
2. **अनुपालन आर्काइविंग** – ऑडिट आवश्यकताओं को पूरा करने के लिए निकाली गई फ़ाइलों को मूल वर्कबुक के साथ संग्रहीत करें।  
3. **डायनेमिक रिपोर्ट जनरेशन** – एम्बेडेड चार्ट्स या दस्तावेज़ों को कस्टम रिपोर्टिंग इंजन में अलग एसेट्स के रूप में पुनः उपयोग करें।  

## प्रदर्शन संबंधी विचार
- **मेमोरी मैनेजमेंट:** प्रत्येक फ़ाइल प्रोसेसिंग समाप्त होते ही `Watermarker` को बंद करें।  
- **बैच प्रोसेसिंग:** CPU उपयोग को स्थिर रखने के लिए वर्कबुक को चंक्स में प्रोसेस करें (उदा., प्रति थ्रेड 10‑20 फ़ाइलें)।  
- **लोड ऑप्शन्स ट्यूनिंग:** जब आपको केवल अटैचमेंट्स चाहिए हों, तो लोड किए जाने वाले पंक्तियों/कॉलमों की संख्या को सीमित करने के लिए `SpreadsheetLoadOptions` का उपयोग करें।  

## सामान्य समस्याएँ और समाधान
| समस्या | समाधान |
|-------|----------|
| **`getPreviewImageContent()` पर `NullPointerException`** | सुनिश्चित करें कि अटैचमेंट में वास्तव में प्रीव्यू मौजूद है; सभी फ़ाइल प्रकार प्रीव्यू नहीं बनाते। |
| **बड़ी Excel फ़ाइलें OutOfMemoryError का कारण बनती हैं** | JVM हीप साइज बढ़ाएँ (`-Xmx2g`) या प्रत्येक फ़ाइल के बाद स्पष्ट `close()` के साथ क्रमिक रूप से प्रोसेस करें। |
| **प्रोडक्शन में LicenseException** | सुनिश्चित करें कि आपने `License.setLicense("path/to/license.json")` के माध्यम से वैध पूर्ण‑लाइसेंस फ़ाइल लागू की है। |

## अक्सर पूछे जाने वाले प्रश्न
**Q:** क्या मैं पासवर्ड‑प्रोटेक्टेड Excel फ़ाइलों से अटैचमेंट्स निकाल सकता हूँ?  
**A:** हाँ। पासवर्ड सहित `SpreadsheetLoadOptions` के साथ वर्कबुक लोड करें, फिर दिखाए अनुसार आगे बढ़ें।

**Q:** क्या API एम्बेडेड चार्ट्स को इमेजेज़ के रूप में निकालने का समर्थन करता है?  
**A:** चार्ट्स को अलग ऑब्जेक्ट्स के रूप में माना जाता है; आप उनके प्रीव्यू इमेज को `getPreviewImageContent()` के माध्यम से प्राप्त कर सकते हैं।

**Q:** किन फ़ाइल फ़ॉर्मैट्स को अटैचमेंट्स के रूप में निकाला जा सकता है?  
**A:** वर्कबुक में एम्बेडेड कोई भी फ़ाइल प्रकार—PDF, DOCX, PNG, JPG, आदि—`SpreadsheetAttachment` API के माध्यम से एक्सेस किया जा सकता है।

**Q:** क्या निकाली गई फ़ाइलों को स्वचालित रूप से सहेजने का कोई तरीका है?  
**A:** आप `attachment.getContent()` को अपनी पसंद के `FileOutputStream` में लिख सकते हैं। ट्यूटोरियल मेटाडाटा प्रिंट करने पर केंद्रित है, लेकिन वही बाइट एरे को सहेजा जा सकता है।

**Q:** क्या अटैचमेंट्स निकालते समय मुझे Excel फ़ॉर्मूले संभालने की जरूरत है?  
**A:** नहीं। अटैचमेंट्स सेल फ़ॉर्मूलों से स्वतंत्र होते हैं; वे वर्कबुक के भीतर OLE ऑब्जेक्ट्स के रूप में संग्रहीत होते हैं।

## निष्कर्ष
अब आपके पास GroupDocs.Watermark for Java का उपयोग करके **Excel अटैचमेंट्स निकालने** के लिए एक पूर्ण, प्रोडक्शन‑रेडी गाइड है। इन चरणों को अपने ऑटोमेशन पाइपलाइन में एकीकृत करके आप डेटा संग्रह को सुव्यवस्थित कर सकते हैं, अनुपालन में सुधार कर सकते हैं, और नई रिपोर्टिंग संभावनाओं को खोल सकते हैं। लाइब्रेरी की अन्य सुविधाओं—जैसे वाटरमार्किंग या रिडैक्शन—का अन्वेषण करें ताकि अपने दस्तावेज़ प्रोसेसिंग वर्कफ़्लो को और बेहतर बना सकें।

---

**Last Updated:** 2026-04-04  
**Tested With:** GroupDocs.Watermark 24.11 for Java  
**Author:** GroupDocs  

---