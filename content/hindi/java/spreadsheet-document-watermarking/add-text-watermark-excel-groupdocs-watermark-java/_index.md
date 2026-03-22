---
date: '2026-03-22'
description: GroupDocs.Watermark for Java का उपयोग करके टेक्स्ट वॉटरमार्क जोड़कर Excel
  फ़ाइलों पर वॉटरमार्क कैसे लगाएँ, सीखें। अपने स्प्रेडशीट को सुरक्षित रखें और ब्रांडिंग
  को मजबूत करें।
keywords:
- text watermark Excel
- GroupDocs.Watermark Java
- Excel document security
title: GroupDocs.Watermark for Java का उपयोग करके टेक्स्ट के साथ Excel शीट्स पर वॉटरमार्क
  कैसे लगाएँ
type: docs
url: /hi/java/spreadsheet-document-watermarking/add-text-watermark-excel-groupdocs-watermark-java/
weight: 1
---

# ग्रुपडॉक्स.Watermark for Java का उपयोग करके एक्सेल शीट्स पर टेक्स्ट वॉटरमार्क कैसे लगाएँ

जब आपको **how to watermark Excel** वर्कबुक्स की आवश्यकता होती है—विशेषकर उन वर्कबुक्स की जिनमें संवेदनशील डेटा होता है—एक स्पष्ट, पेशेवर टेक्स्ट वॉटरमार्क जोड़ना आपके कंटेंट की सुरक्षा और ब्रांड पहचान को मजबूत करने के सबसे प्रभावी तरीकों में से एक है। इस ट्यूटोरियल में हम **add text watermark Excel** फ़ाइलों को GroupDocs.Watermark लाइब्रेरी फॉर जावा का उपयोग करके जोड़ने के सटीक चरणों को दिखाएंगे, जिसमें प्रोजेक्ट सेटअप से लेकर अंतिम, सुरक्षित वर्कबुक को सेव करने तक सब कुछ शामिल है।

## त्वरित उत्तर
- **What library should I use?** GroupDocs.Watermark for Java.  
- **Can I add a text watermark to every sheet?** Yes – iterate over each worksheet and apply the same watermark.  
- **Do I need a license?** A free trial works for evaluation; a permanent license is required for production.  
- **Which Java version is supported?** JDK 8 or later.  
- **Will the watermark affect cell data?** No, it only overlays images within the worksheet.

## एक्सेल में वॉटरमार्किंग क्या है?
वॉटरमार्किंग एक्सेल का अर्थ है एक दृश्यमान मार्कर—टेक्स्ट या इमेज—को सीधे वर्कशीट के विज़ुअल एलिमेंट्स (जैसे इमेजेज़) पर एम्बेड करना, ताकि फ़ाइल खोलने वाला कोई भी मालिकाना हक़ या गोपनीयता नोटिस देख सके। यह तकनीक अनधिकृत वितरण को रोकने में मदद करती है और आपके रिपोर्ट्स को पेशेवर लुक देती है।

## जावा का उपयोग करके एक्सेल में टेक्स्ट वॉटरमार्क क्यों जोड़ें?
- **Security** – स्पष्ट रूप से गोपनीय या स्वामित्व वाली जानकारी दर्शाता है।  
- **Brand consistency** – सभी साझा किए गए स्प्रेडशीट्स में कॉर्पोरेट ब्रांडिंग को सुदृढ़ करता है।  
- **Automation** – जावा आपको प्रोग्रामेटिक रूप से वॉटरमार्क एम्बेड करने की सुविधा देता है, जिससे मैन्युअल एडिट्स में समय बचता है।  
- **Cross‑format support** – `.xlsx` और लेगेसी `.xls` दोनों फ़ाइलों के साथ काम करता है।

## पूर्वापेक्षाएँ
- **Java Development Kit (JDK)** 8 या उससे नया।  
- **Maven** डिपेंडेंसी मैनेजमेंट के लिए।  
- जावा सिंटैक्स और ऑब्जेक्ट‑ओरिएंटेड कॉन्सेप्ट्स की बुनियादी समझ।

## GroupDocs.Watermark for Java सेटअप करना
शुरू करने के लिए, अपने Maven प्रोजेक्ट में GroupDocs.Watermark डिपेंडेंसी जोड़ें।

### Maven का उपयोग करके
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
वैकल्पिक रूप से, नवीनतम JAR को [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/) से डाउनलोड करें।

**लाइसेंस प्राप्ति**
- **Free Trial** – सभी फीचर्स को बिना लागत के एक्सप्लोर करें।  
- **Temporary License** – अल्पकालिक टेस्टिंग के लिए उपयोग करें।  
- **Purchase** – प्रोडक्शन क्षमताओं को अनलॉक करें।

### बेसिक इनिशियलाइज़ेशन
```java
import com.groupdocs.watermark.Watermarker;
// Initialize watermarker instance for your document
Watermarker watermarker = new Watermarker("path/to/your/spreadsheet.xlsx");
```

## इम्प्लीमेंटेशन गाइड

### फीचर 1: टेक्स्ट वॉटरमार्क बनाना और उसकी प्रॉपर्टीज़ कॉन्फ़िगर करना
वॉटरमार्क बनाना और कस्टमाइज़ करना टेक्स्ट, फ़ॉन्ट, अलाइनमेंट, रोटेशन एंगल और स्केलिंग सेट करने में शामिल है।  

#### चरण‑दर‑चरण अवलोकन
**Define Your Watermark**
```java
import com.groupdocs.watermark.common.HorizontalAlignment;
import com.groupdocs.watermark.common.VerticalAlignment;
import com.groupdocs.watermark.options.SpreadsheetLoadOptions;
import com.groupdocs.watermark.watermarks.Font;
import com.groupdocs.watermark.watermarks.SizingType;
import com.groupdocs.watermark.watermarks.TextWatermark;

// Create a new TextWatermark object
text watermark = new TextWatermark("Protected image", new Font("Arial", 8));

// Configure the watermark properties
text watermark.setHorizontalAlignment(HorizontalAlignment.Center);
text watermark.setVerticalAlignment(VerticalAlignment.Center);
text watermark.setRotateAngle(45); // Set rotation angle
text watermark.setSizingType(SizingType.ScaleToParentDimensions);
text watermark.setScaleFactor(1); // Maintain original size scale factor
```
- **Text and Font** – एक स्पष्ट संदेश और पढ़ने योग्य फ़ॉन्ट चुनें।  
- **Alignment** – अधिकांश इमेजेज़ के लिए सेंटरिंग उपयुक्त रहती है।  
- **Rotation & Scaling** – 45° का टिल्ट वॉटरमार्क को दिखने योग्य बनाता है बिना इमेज को ढँकते हुए।

### फीचर 2: वॉटरमार्किंग के लिए स्प्रेडशीट डॉक्यूमेंट लोड करना
वर्कबुक को उचित विकल्पों के साथ लोड करें ताकि GroupDocs उसके आंतरिक इमेजेज़ तक पहुँच सके।

```java
import com.groupdocs.watermark.options.SpreadsheetLoadOptions;
// Load your Excel spreadsheet
documentLoadOptions = new SpreadsheetLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/spreadsheet.xlsx", documentLoadOptions);
```

### फीचर 3: वर्कशीट में इमेजेज़ पर टेक्स्ट वॉटरमार्क जोड़ना
पहली वर्कशीट की इमेजेज़ पर इटररेट करें और कॉन्फ़िगर किया गया वॉटरमार्क लागू करें।

```java
import com.groupdocs.watermark.contents.SpreadsheetContent;
import com.groupdocs.watermark.contents.WatermarkableImageCollection;

// Access content from your loaded document
SpreadsheetContent content = watermarker.getContent(SpreadsheetContent.class);
WatermarkableImageCollection images = content.getWorksheets().get_Item(0).findImages();

for (com.groupdocs.watermark.contents.WatermarkableImage image : images) {
    // Add the configured watermark to each image in the worksheet
    image.add(watermark);
}
```

### फीचर 4: वॉटरमार्क्ड स्प्रेडशीट डॉक्यूमेंट को सेव और क्लोज करना
परिवर्तनों को नई फ़ाइल में सेव करें और रिसोर्सेज़ को क्लीन अप करें।

```java
// Save the changes to a new file
watermarker.save("YOUR_OUTPUT_DIRECTORY/spreadsheet-out.xlsx");
// Close the watermarker instance to free resources
watermarker.close();
```

## व्यावहारिक उपयोग
- **Document Security** – गोपनीय वित्तीय मॉडल या HR डेटा की रक्षा करें।  
- **Branding** – सभी साझा किए गए रिपोर्ट्स में कंपनी स्लोगन या लीगल नोटिस डालें।  
- **Copyright Protection** – प्रत्येक एक्सपोर्टेड इमेज को मार्क करके प्लेज़रिज़्म को रोकें।

## प्रदर्शन संबंधी विचार
- नवीनतम प्रदर्शन सुधारों के लिए GroupDocs.Watermark को अप‑टू‑डेट रखें।  
- `Watermarker` इंस्टेंस को तुरंत (`close()`) रिलीज़ करें ताकि मेमोरी मुक्त हो सके।  
- बहुत बड़े वर्कबुक्स के लिए, मेमोरी ओवरहेड कम करने हेतु वर्कशीट्स को बैच में प्रोसेस करें।

## सामान्य समस्याएँ और समाधान
| Issue | Solution |
|-------|----------|
| Watermark not visible | Verify that the worksheet actually contains images; the API only watermarks images, not cells. |
| Misaligned watermark | Adjust `HorizontalAlignment` / `VerticalAlignment` or change `RotateAngle`. |
| Out‑of‑memory errors on big files | Increase JVM heap (`-Xmx`) or process each worksheet separately. |
| License errors | Ensure the trial or permanent license file is correctly referenced in your project. |

## अक्सर पूछे जाने वाले प्रश्न

**Q: क्या मैं इसे सभी Excel संस्करणों पर उपयोग कर सकता हूँ?**  
A: हाँ, GroupDocs दोनों `.xlsx` और `.xls` फ़ॉर्मैट्स को सपोर्ट करता है।

**Q: अगर मेरा वॉटरमार्क सही से नहीं दिख रहा है तो क्या करें?**  
A: अलाइनमेंट सेटिंग्स को दोबारा चेक करें और सुनिश्चित करें कि इमेज डाइमेंशन चुने हुए स्केल फैक्टर के लिए उपयुक्त हैं।

**Q: फ़ॉन्ट स्टाइल को और कैसे कस्टमाइज़ कर सकता हूँ?**  
A: `Font` क्लास का उपयोग करके बोल्ड, इटैलिक, रंग या अन्य टाइपोग्राफ़िक एट्रिब्यूट्स सेट करें।

**Q: क्या वर्कबुक की सभी शीट्स में वॉटरमार्क जोड़ना संभव है?**  
A: बिल्कुल—`content.getWorksheets()` पर लूप करें और प्रत्येक शीट के लिए वही `image.add(watermark)` लॉजिक लागू करें।

**Q: बड़े Excel फ़ाइलों को कुशलता से कैसे हैंडल करूँ?**  
A: वर्कशीट्स को क्रमिक रूप से प्रोसेस करें, प्रत्येक `Watermarker` को सेव करने के बाद क्लोज करें, और JVM हीप साइज बढ़ाने पर विचार करें।

## संसाधन
- [GroupDocs.Watermark Documentation](https://docs.groupdocs.com/watermark/java/)  
- [API Reference](https://reference.groupdocs.com/watermark/java)  
- [Download GroupDocs.Watermark for Java](https://releases.groupdocs.com/watermark/java/)  
- [GitHub Repository](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)  
- [Free Support Forum](https://forum.groupdocs.com/c/watermark/10)  
- [Temporary License Application](httpshttps://purchase.groupdocs.com/temporary-license/) 

इन चरणों को अपने जावा प्रोजेक्ट्स में इंटीग्रेट करके आप **java add watermark excel** फ़ाइलों को जल्दी से बना सकते हैं, जिससे सुरक्षा और ब्रांड कंसिस्टेंसी दोनों सुनिश्चित होती हैं।

---

**Last Updated:** 2026-03-22  
**Tested With:** GroupDocs.Watermark 24.11 for Java  
**Author:** GroupDocs