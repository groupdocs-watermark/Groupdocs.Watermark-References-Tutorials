---
date: '2025-12-26'
description: GroupDocs.Watermark for Java का उपयोग करके Excel फ़ाइलों से अटैचमेंट
  निकालना सीखें। यह गाइड जावा में Excel अटैचमेंट निकालना, जावा में Excel वर्कशीट्स
  को इटरेट करना और Excel अटैचमेंट्स को बैच प्रोसेस करना कवर करता है।
keywords:
- extract attachments from excel
- groupdocs watermark java tutorial
- manage excel document attachments
title: GroupDocs.Watermark Java के साथ Excel से अटैचमेंट्स निकालने का तरीका
type: docs
url: /hi/java/email-document-watermarking/extract-attachments-excel-groupdocs-watermark-java/
weight: 1
---

# GroupDocs.Watermark Java का इस्तेमाल करके Excel से अटैचमेंट निकालना

आज के डेटा‑ड्रिवेन वर्कफ़्लोज़ में, **अटैचमेंट निकालने** की आवश्यकता अक्सर होती है। चाहे आप प्रोजेक्ट संसाधनों को एकत्रित कर रहे हों, अनुपालन दस्तावेज़ों को संग्रहित कर रहे हों, या स्वचालित रिपोर्टिंग पाइपलाइन बना रहे हों, एम्बेडेड फ़ाइलों को निकालना समय बचाता है और मैन्युअल त्रुटियों को समाप्त करता है। इस ट्यूटोरियल में आप देखेंगे कि GroupDocs.Watermark for Java को कैसे सेटअप करें, वह कोड जो **java extract excel attachments** करता है, और **batch process excel attachments** के लिए सर्वोत्तम प्रथाएँ समझेंगे।

## क्विक जवाब
- **Excel अटैचमेंट को संभालने वाली लाइब्रेरी कौन सी है?** GroupDocs.Watermark for Java.  
- **स्प्रेडशीट को लोड करने वाला मेथड कौन सा है?** `new Watermarker(filePath, new SpreadsheetLoadOptions())`.  
- **क्या मैं Java के साथ वर्कशीट्स को इटरेट कर सकता हूँ?** हाँ – `content.getWorksheets()` का उपयोग करें और प्रत्येक `SpreadsheetWorksheet` पर लूप करें।  
- **प्रोडक्शन के लिए लाइसेंस आवश्यक है?** प्रोडक्शन उपयोग के लिए पूर्ण GroupDocs.Watermark लाइसेंस आवश्यक है।  
- **क्या यह बड़े फ़ाइलों पर काम करेगा?** हाँ, जब आप Watermarker को तुरंत बंद करें और उपयुक्त लोड विकल्पों का उपयोग करें।

## Excel के कॉन्टेक्स्ट में “अटैचमेंट कैसे निकालें” क्या है?
अटैचमेंट निकालना मतलब Excel वर्कबुक की वर्कशीट्स में एम्बेडेड किसी भी ऑब्जेक्ट—फ़ाइलें, इमेजेज़, या लिंक—को प्राप्त करना है। इन ऑब्जेक्ट्स को `SpreadsheetAttachment` ऑब्जेक्ट्स के रूप में संग्रहीत किया जाता है और इन्हें प्रोग्रामेटिकली एक्सेस, निरीक्षण और डिस्क पर सहेजा जा सकता है।

## Excel अटैचमेंट निकालने के लिए GroupDocs.Watermark का इस्तेमाल क्यों करें?
GroupDocs.Watermark एक हाई‑लेवल API प्रदान करता है जो लो‑लेवल Office Open XML हैंडलिंग को एब्स्ट्रैक्ट करता है, जिससे आप फ़ाइल फ़ॉर्मेट की जटिलताओं के बजाय बिज़नेस लॉजिक पर ध्यान केंद्रित कर सकते हैं। यह **extract embedded objects excel** को भी सपोर्ट करता है, प्रीव्यू इमेज एक्सट्रैक्शन प्रदान करता है, और Java 8+ पर्यावरण में लगातार काम करता है।

## ज़रूरी शर्तें
- **Java Development Kit (JDK) 8 या उससे ऊपर** – लाइब्रेरी किसी भी आधुनिक JDK पर चलती है।  
- **IDE** – IntelliJ IDEA, Eclipse, या आपका पसंदीदा कोई भी एडिटर।  
- **Maven** – डिपेंडेंसी मैनेजमेंट के लिए (या आप JAR मैन्युअली डाउनलोड कर सकते हैं)।  
- बेसिक Java ज्ञान और Maven कोऑर्डिनेट्स की परिचितता।

## Java के लिए GroupDocs.Watermark सेट अप करना

### Maven सेटअप
अपने `pom.xml` में GroupDocs रिपॉजिटरी और डिपेंडेंसी जोड़ें:

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

### डायरेक्ट डाउनलोड (विकल्प)
अगर आप Maven इस्तेमाल नहीं करना चाहते, तो [GroupDocs.Watermark for Java रिलीज़](https://releases.groupdocs.com/watermark/java/) से लेटेस्ट JAR लें।

### लाइसेंस पाने के स्टेप्स
- **फ़्री ट्रायल:** GroupDocs पोर्टल पर रजिस्टर करके लिमिटेड टाइम के लिए ट्रायल लें।
- **टेम्पररी लाइसेंस:** डेवलपमेंट के दौरान एक टेम्पररी की इस्तेमाल करें।
- **फ़ुल लाइसेंस:** अनलिमिटेड इस्तेमाल के लिए प्रोडक्शन लाइसेंस खरीदें।

### बेसिक इनिशियलाइज़ेशन और सेटअप
एक `Watermarker` इंस्टेंस बनाएं जो आपकी Excel फ़ाइल की ओर पॉइंट करे:

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

## Excel से अटैचमेंट कैसे निकालें – स्टेप-बाय-स्टेप गाइड

### स्प्रेडशीट लोड करें और तैयार करें
सबसे पहले, वर्कबुक को `SpreadsheetLoadOptions` से लोड करें ताकि लाइब्रेरी को पता चले कि वह Excel फ़ाइल के साथ काम कर रही है:

```java
import com.groupdocs.watermark.options.SpreadsheetLoadOptions;
import com.groupdocs.watermark.Watermarker;

public class ExtractAttachments {
    public static void extract() {
        SpreadsheetLoadOptions loadOptions = new SpreadsheetLoadOptions();
        String filePath = "YOUR_DOCUMENT_DIRECTORY/spreadsheet.xlsx";
        
        Watermarker watermarker = new Watermarker(filePath, loadOptions);
```

### स्प्रेडशीट कंटेंट एक्सेस करें
हाई-लेवल कंटेंट ऑब्जेक्ट पाएं जो आपको वर्कशीट और उनके अटैचमेंट का एक्सेस देता है:

```java
import com.groupdocs.watermark.contents.SpreadsheetContent;

// Get the content of the spreadsheet.
SpreadsheetContent content = watermarker.getContent(SpreadsheetContent.class);
```

### वर्कशीट में इटरेट करें (java iterate excel worksheets java)
हर वर्कशीट पर और फिर उस शीट के अंदर हर अटैचमेंट पर लूप करें:

```java
import com.groupdocs.watermark.contents.SpreadsheetWorksheet;

for (SpreadsheetWorksheet worksheet : content.getWorksheets()) {
    for (SpreadsheetAttachment attachment : worksheet.getAttachments()) {
```

### अटैचमेंट डिटेल्स निकालें
हर `SpreadsheetAttachment` के लिए आप उसका मेटाडेटा, प्रीव्यू इमेज और रॉ फ़ाइल बाइट्स पढ़ सकते हैं:

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

### रिसोर्स बंद करें
मेमोरी खाली करने के लिए जब आपका काम हो जाए तो हमेशा `Watermarker` रिलीज़ करें:

```java
// Close the Watermarker to release resources.
watermarker.close();
```

## प्रैक्टिकल एप्लीकेशन
- **ऑटोमेटेड डेटा कंसोलिडेशन:** स्प्रेडशीट के बैच से हर अटैच्ड फ़ाइल को निकालें और डेटा-लेक में फीड करें।

- **डॉक्यूमेंट आर्काइविंग:** ऑडिट के लिए मूल वर्कबुक के साथ निकाले गए अटैचमेंट को स्टोर करें।

- **डायनामिक रिपोर्ट जेनरेशन:** कस्टम रिपोर्टिंग इंजन के इनपुट के रूप में निकाली गई इमेज या PDF का इस्तेमाल करें।

## बैच प्रोसेस एक्सेल अटैचमेंट के लिए परफॉर्मेंस संबंधी बातें

- **मेमोरी मैनेजमेंट:** हर फ़ाइल के बाद `watermarker.close()` कॉल करें; try‑with‑resources प्रोसेसिंग का इस्तेमाल करने पर विचार करें।

- **बैच लूपिंग:** बैच लूप को मैनेज करने वाले ग्रुप (जैसे, 20‑30 एक बार में) में प्रोसेस करें ताकि JVM हीप ओवरलोड न हो।

- **लोड ऑप्शन ट्यूनिंग:** बहुत बड़ी वर्कबुक्स के लाइब्रेरी को तेज़ी से करने के लिए `SpreadsheetLoadOptions` को एडजस्ट करें (जैसे, अनावश्यक फीचर्स को डिसेबल करें)।

## सामान्य मुद्दे और समाधान
| समस्या | कारण | समाधान |
|-------|---------|-----|
| `NullPointerException` on `attachment.getPreviewImageContent()` | अटैचमेंट के लिए कोई प्रीव्यू इमेज मौजूद नहीं है। | कोड में दिखाए अनुसार एक नल चेक जोड़ें। |
| कई बड़ी फाइलों को प्रोसेस करते समय मेमोरी स्पाइक्स | Watermarker को समय पर बंद नहीं किया गया। | `try { … } finally { watermarker.close(); }` ब्लॉक का उपयोग करें। |
| अटैचमेंट सूचीबद्ध नहीं हैं | पूर्ण अटैचमेंट सपोर्ट के बिना पुराने GroupDocs संस्करण का उपयोग किया जा रहा है। | नवीनतम 24.11 जारी (या उससे नया) में अपग्रेड करें। |

## अक्सर पूछे जाने वाले सवाल

**Q: क्या मैं पासवर्ड-प्रोटेक्टेड एक्सेल सेक्शन से अटैचमेंट निकाल सकता हूँ?**
A: हाँ। `Watermarker` इंस्टेंस बनाने के लिए सही समय पर ओवरलोड का इस्तेमाल करके पासवर्ड दें।

**Q: क्या यह `.xls` (BIFF) सेक्शन के साथ-साथ `.xlsx` पर भी काम करता है?**
A: GroupDocs.Watermark दोनों लेगेसी `.xls` और मॉडर्न `.xlsx` फॉर्मेट को सपोर्ट करता है।

**Q: निकाले गए अटैचमेंट को डिस्क पर कैसे डिलीट करें?**
A: `attachment.getContent()` के ज़रिए बाइट लें और उसे `FileOutputStream` में लिखें।

**Q: क्या केवल विशिष्ट अटैचमेंट प्रकार (जैसे PDFs) को निकालने का कोई तरीका है?**
A: प्रोसेस करने से पहले `attachment.getDocumentInfo().getFileType()` द्वारा लोकेशन करें।

**Q: प्रोफेशनल इस्तेमाल के लिए कौन सा लाइसेंस ज़रूरी है?**
A: प्रोडक्शन डिप्लॉयमेंट के लिए पूरा GroupDocs.Watermark लाइसेंस ज़रूरी है।

---

**लास्ट अपडेटेड:** 2025-12-26
**इसके साथ टेस्ट किया गया:** Java के लिए GroupDocs.Watermark 24.11
**लेखक:** GroupDocs