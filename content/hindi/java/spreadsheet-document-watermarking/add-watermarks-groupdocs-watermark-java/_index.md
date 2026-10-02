---
date: '2026-03-27'
description: GroupDocs.Watermark for Java का उपयोग करके एक्सेल फ़ाइलों में वॉटरमार्क
  कैसे जोड़ें, सीखें। यह गाइड सेटअप, कोड और स्प्रेडशीट्स में वॉटरमार्क लगाने के सर्वोत्तम
  अभ्यासों को समझाता है।
keywords:
- GroupDocs.Watermark
- Java
- Document Processing
title: GroupDocs.Watermark Java का उपयोग करके एक्सेल में वॉटरमार्क जोड़ें
type: docs
url: /hi/java/spreadsheet-document-watermarking/add-watermarks-groupdocs-watermark-java/
weight: 1
---

# GroupDocs.Watermark Java का उपयोग करके Excel में वॉटरमार्क जोड़ें

Excel फ़ाइलों में वॉटरमार्क जोड़ना एक बड़ा बदलाव हो सकता है—चाहे आपको संवेदनशील डेटा की सुरक्षा करनी हो, रिपोर्ट्स पर ब्रांडिंग करनी हो, या सिर्फ़ एक पेशेवर लुक देना हो। इस ट्यूटोरियल में आप **Excel में वॉटरमार्क कैसे जोड़ें** सीखेंगे, GroupDocs.Watermark for Java का उपयोग करके, स्पष्ट व्याख्याओं, वास्तविक उपयोग मामलों, और सामान्य समस्याओं से बचने के टिप्स के साथ।

## त्वरित उत्तर
- **मुझे कौन सी लाइब्रेरी चाहिए?** GroupDocs.Watermark for Java (नवीनतम संस्करण)।  
- **कौन से Excel फ़ॉर्मेट समर्थित हैं?** .xlsx और .xls फ़ाइलें (बिना एन्क्रिप्शन के)।  
- **क्या मैं इमेज वॉटरमार्क जोड़ सकता हूँ?** हाँ – SDK टेक्स्ट और इमेज दोनों वॉटरमार्क को सपोर्ट करता है।  
- **प्रोडक्शन के लिए लाइसेंस चाहिए?** गैर‑ट्रायल डिप्लॉयमेंट के लिए एक कॉमर्शियल लाइसेंस आवश्यक है।  
- **इम्प्लीमेंटेशन में कितना समय लगेगा?** बेसिक टेक्स्ट वॉटरमार्क के लिए लगभग 10‑15 मिनट।

## **Excel में वॉटरमार्क जोड़ना** क्या है?
Excel वर्कबुक में वॉटरमार्क जोड़ना मतलब हर वर्कशीट या एम्बेडेड डॉक्यूमेंट पर एक दिखाई देने वाला (या अर्ध‑पारदर्शी) टेक्स्ट या इमेज स्टैम्प लगाना। यह आपको स्वामित्व स्थापित करने, गोपनीयता दर्शाने, या पूरे फ़ाइल में ब्रांडिंग को मजबूत करने में मदद करता है।

## GroupDocs.Watermark for Java क्यों उपयोग करें?
GroupDocs.Watermark एक हाई‑लेवल API प्रदान करता है जो Office Open XML स्ट्रक्चर की जटिलताओं को एब्स्ट्रैक्ट करता है। यह आपको सक्षम बनाता है:

- एक ही कॉल में कई वर्कशीट्स पर वॉटरमार्क लागू करना।  
- एम्बेडेड अटैचमेंट्स (जैसे एम्बेडेड PDFs) को स्वचालित रूप से हैंडल करना।  
- मूल फ़ॉर्मेटिंग और फ़ॉर्मूलाज़ को संरक्षित रखना।  
- टेक्स्ट और इमेज दोनों वॉटरमार्क के साथ काम करना (जैसे **add image watermark java**)।

## पूर्वापेक्षाएँ

- **Java Development Environment** – Java 8 या उससे ऊपर (JDK)।  
- **GroupDocs.Watermark for Java SDK** – नवीनतम रिलीज़ [यहाँ](https://releases.groupdocs.com/watermark/java/) से डाउनलोड करें।  
- **IDE** – IntelliJ IDEA, Eclipse, या कोई भी Java‑संगत एडिटर।  
- **सैंपल स्प्रेडशीट** – एक .xlsx फ़ाइल जिसे आप प्रोटेक्ट करना चाहते हैं।

आप Maven, Gradle, या JAR फ़ाइलों को क्लासपाथ में मैन्युअली जोड़कर SDK को अपने प्रोजेक्ट में शामिल कर सकते हैं।

## पैकेज इम्पोर्ट करें

इन इम्पोर्ट्स से आपको कोर वॉटरमार्किंग क्लासेज़, स्प्रेडशीट हैंडलिंग, और फ़ॉन्ट यूटिलिटीज़ तक पहुँच मिलती है।

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.examples.Constants;
import com.groupdocs.watermark.domain.DocumentInfo;
import com.groupdocs.watermark.domain.FileType;
import com.groupdocs.watermark.domain.content.SpreadsheetContent;
import com.groupdocs.watermark.domain.content.SpreadsheetWorksheet;
import com.groupdocs.watermark.domain.content.SpreadsheetAttachment;
import com.groupdocs.watermark.domain.document.IDocumentInfo;
import com.groupdocs.watermark.domain.loadoptions.SpreadsheetLoadOptions;
import com.groupdocs.watermark.domain.wrappers.TextWatermark;
import java.awt.Font;
```

## **स्प्रेडशीट में वॉटरमार्क** कैसे जोड़ें – चरण‑दर‑चरण गाइड

नीचे एक व्यावहारिक, क्रमांकित walkthrough दिया गया है जो दिखाता है **स्प्रेडशीट में वॉटरमार्क** फ़ाइलों को Java से कैसे जोड़ें। प्रत्येक चरण में एक छोटा स्पष्टीकरण और मूल कोड ब्लॉक (अपरिवर्तित) शामिल है।

### चरण 1: अपना Watermark ऑब्जेक्ट सेट अप करें  
**क्यों?** यह ऑब्जेक्ट उस स्टैम्प की विज़ुअल अपीयरेंस को परिभाषित करता है जिसे आप लागू करेंगे।

```java
TextWatermark watermark = new TextWatermark("Confidential", new Font("Arial", 19));
```

### चरण 2: स्प्रेडशीट लोड करें  
**क्यों?** वर्कबुक खोलने से SDK को एडिट करने के लिए एक हैंडल मिल जाता है।

```java
SpreadsheetLoadOptions loadOptions = new SpreadsheetLoadOptions();
Watermarker watermarker = new Watermarker("your-file-path.xlsx", loadOptions);
```

### चरण 3: स्प्रेडशीट कंटेंट और वर्कशीट्स तक पहुँचें  
**क्यों?** Excel फ़ाइलों में कई शीट्स हो सकती हैं; आपको प्रत्येक पर इटररेट करना होगा।

```java
SpreadsheetContent content = watermarker.getContent(SpreadsheetContent.class);
for (SpreadsheetWorksheet worksheet : content.getWorksheets()) {
    // Process each worksheet
}
```

### चरण 4: प्रत्येक वर्कशीट में अटैचमेंट्स पर लूप करें  
**क्यों?** कुछ वर्कशीट्स अन्य डॉक्यूमेंट्स (जैसे PDFs) एम्बेड करती हैं। इन्हें हैंडल करने से पूरे फ़ाइल में समान वॉटरमार्क सुनिश्चित होता है।

```java
for (SpreadsheetAttachment attachment : worksheet.getAttachments()) {
    IDocumentInfo info = attachment.getDocumentInfo();
    if (info.getFileType() != FileType.Unknown && !info.isEncrypted()) {
        // Process the supported attachment
    }
}
```

### चरण 5: प्रत्येक एम्बेडेड डॉक्यूमेंट पर वॉटरमार्क लगाएँ  
**क्यों?** आप हर एम्बेडेड फ़ाइल पर वही “Confidential” स्टैम्प चाहते हैं।

```java
Watermarker attachedWatermarker = attachment.createWatermarker();
attachedWatermarker.add(watermark);
attachment.updateContent(attachedWatermarker);
attachedWatermarker.close();
```

### चरण 6: सभी बदलाव सेव करें  
**क्यों?** संशोधनों को नई वर्कबुक में परसिस्ट करें।

```java
watermarker.save("your-output-file.xlsx");
```

### चरण 7: रिसोर्सेज़ को बंद करें  
**क्यों?** रिसोर्सेज़ को फ्री करने से मेमोरी लीक्स रोकते हैं, विशेषकर बड़े वर्कबुक प्रोसेस करते समय।

```java
watermarker.close();
```

## सब कुछ एक साथ: पूर्ण उदाहरण

निम्नलिखित क्लास सभी चरणों को एक ही रनएबल प्रोग्राम में जोड़ता है। **कोड ब्लॉक को संशोधित न करें** – यह मूल उदाहरण के समान है।

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.domain.DocumentInfo;
import com.groupdocs.watermark.domain.FileType;
import com.groupdocs.watermark.domain.content.SpreadsheetContent;
import com.groupdocs.watermark.domain.content.SpreadsheetWorksheet;
import com.groupdocs.watermark.domain.content.SpreadsheetAttachment;
import com.groupdocs.watermark.domain.loadoptions.SpreadsheetLoadOptions;
import com.groupdocs.watermark.domain.wrappers.TextWatermark;
import java.awt.Font;

public class WatermarkSpreadsheet {
    public static void main(String[] args) {
        try {
            // Step 1: Create watermark
            TextWatermark watermark = new TextWatermark("Confidential", new Font("Arial", 19));
            
            // Step 2: Load spreadsheet
            SpreadsheetLoadOptions loadOptions = new SpreadsheetLoadOptions();
            Watermarker watermarker = new Watermarker("path/to/your/spreadsheet.xlsx", loadOptions);
            
            // Step 3: Access content and worksheets
            SpreadsheetContent content = watermarker.getContent(SpreadsheetContent.class);
            for (SpreadsheetWorksheet worksheet : content.getWorksheets()) {
                
                // Step 4: Loop attachments
                for (SpreadsheetAttachment attachment : worksheet.getAttachments()) {
                    DocumentInfo info = attachment.getDocumentInfo();
                    if (info.getFileType() != FileType.Unknown && !info.isEncrypted()) {
                        
                        // Step 5: Watermark attached documents
                        Watermarker attachedWatermarker = attachment.createWatermarker();
                        attachedWatermarker.add(watermark);
                        attachment.updateContent(attachedWatermarker);
                        attachedWatermarker.close(); // Clean up
                    }
                }
            }
            // Step 6: Save modifications
            watermarker.save("path/to/output/spreadsheet_watermarked.xlsx");
        } catch (Exception e) {
            e.printStackTrace();
        } finally {
            // Step 7: Close resources
            // (Ensure resources are closed)
        }
    }
}
```

## सामान्य समस्याएँ और समाधान

| समस्या | क्यों होता है | समाधान |
|-------|----------------|-----|
| **Encrypted workbook is skipped** | SDK पासवर्ड के बिना एन्क्रिप्टेड फ़ाइलें नहीं पढ़ सकता। | फ़ाइल को पहले डिक्रिप्ट करें या `SpreadsheetLoadOptions.setPassword("pwd")` के माध्यम से पासवर्ड प्रदान करें। |
| **Watermark not visible on some sheets** | शीट में कस्टम व्यू या प्रोटेक्शन हो सकता है जो ड्रॉइंग ऑब्जेक्ट्स को छुपाता है। | वॉटरमार्क जोड़ने से पहले शीट प्रोटेक्शन डिसेबल करें, फिर आवश्यकता पड़ने पर पुनः लागू करें। |
| **Performance slowdown on large files** | पूरी वर्कबुक को मेमोरी में लोड करना भारी हो सकता है। | वर्कशीट्स को बैच में प्रोसेस करें या JVM हीप साइज बढ़ाएँ (`-Xmx2g`)। |
| **Image watermark appears distorted** | स्केलिंग सेटिंग्स गलत हैं। | `ImageWatermark` को स्पष्ट width/height पैरामीटर्स के साथ उपयोग करें ताकि aspect ratio बना रहे। |

## अक्सर पूछे जाने वाले प्रश्न

**प्रश्न: क्या मैं टेक्स्ट के बजाय इमेज वॉटरमार्क जोड़ सकता हूँ?**  
**उत्तर:** हाँ। SDK से `ImageWatermark` का उपयोग करें और एक `java.awt.Image` इंस्टेंस पास करें। यह **add image watermark java** परिदृश्य को कवर करता है।

**प्रश्न: मैं वॉटरमार्क की पोज़िशन कैसे नियंत्रित करूँ?**  
**उत्तर:** `TextWatermark` (या `ImageWatermark`) क्लास में `setHorizontalAlignment`, `setVerticalAlignment`, और `setOpacity` जैसी प्रॉपर्टीज़ होती हैं जो प्लेसमेंट और ट्रांसपेरेंसी को फाइन‑ट्यून करती हैं।

**प्रश्न: क्या एक ही रन में कई Excel फ़ाइलों पर वॉटरमार्क लगाया जा सकता है?**  
**उत्तर:** बिल्कुल। फ़ाइलों की डायरेक्टरी पर इटररेट करने के लिए एक `for` लूप रखें, और वही `TextWatermark` इंस्टेंस पुनः उपयोग करें।

**प्रश्न: अगर स्प्रेडशीट में चार्ट्स हैं तो क्या होगा?**  
**उत्तर:** चार्ट्स को अलग ड्रॉइंग ऑब्जेक्ट माना जाता है; वॉटरमार्क वर्कशीट कैनवास पर लागू होता है, इसलिए चार्ट्स अप्रभावित रहते हैं लेकिन पारदर्शी स्टैम्प से कवर हो जाते हैं।

**प्रश्न: क्या मैं पहले जोड़ा गया वॉटरमार्क हटाकर सकता हूँ?**  
**उत्तर:** SDK में `watermarker.remove(watermark)` मेथड उपलब्ध है, लेकिन आपको मूल वॉटरमार्क ऑब्जेक्ट का रेफ़रेंस रखना होगा या टेक्स्ट/कंटेंट के आधार पर उसे खोज कर पहचानना होगा।

---

**अंतिम अपडेट:** 2026-03-27  
**टेस्टेड विथ:** GroupDocs.Watermark 23.12 (Java)  
**लेखक:** GroupDocs