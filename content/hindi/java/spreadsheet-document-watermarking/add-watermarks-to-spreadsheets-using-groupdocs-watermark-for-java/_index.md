---
date: '2026-03-30'
description: GroupDocs.Watermark for Java का उपयोग करके स्प्रेडशीट में वॉटरमार्क जोड़ना
  सीखें, जिसमें टेक्स्ट और इमेज वॉटरमार्क जोड़ने की जावा तकनीकों को चरण‑दर‑चरण मार्गदर्शिका
  में कवर किया गया है।
keywords:
- GroupDocs Watermark Java
- add watermarks to spreadsheets
- Java watermarking guide
title: GroupDocs.Watermark for Java का उपयोग करके स्प्रेडशीट में वॉटरमार्क जोड़ें
type: docs
url: /hi/java/spreadsheet-document-watermarking/add-watermarks-to-spreadsheets-using-groupdocs-watermark-for-java/
weight: 1
---

# स्प्रेडशीट में वॉटरमार्क जोड़ें GroupDocs.Watermark for Java का उपयोग करके: एक व्यापक गाइड

आज के डेटा‑चालित वातावरण में, **स्प्रेडशीट में वॉटरमार्क जोड़ना** संवेदनशील जानकारी को अनधिकृत उपयोग या छेड़छाड़ से बचाने के सबसे प्रभावी तरीकों में से एक है। चाहे आप गोपनीय व्यावसायिक रिपोर्ट, वित्तीय विवरण, या व्यक्तिगत डेटा संभाल रहे हों, एक ठीक‑से रखा गया वॉटरमार्क स्वामित्व दर्शाता है और दुरुपयोग को रोकता है। यह ट्यूटोरियल आपको GroupDocs.Watermark for Java के साथ Excel फ़ाइलों में टेक्स्ट और इमेज वॉटरमार्क जोड़ने के लिए आवश्यक सभी चरणों से गुजराता है।

## त्वरित उत्तर
- **मुझे कौन सी लाइब्रेरी चाहिए?** GroupDocs.Watermark for Java (v24.11 या नया)।  
- **क्या मैं टेक्स्ट और इमेज दोनों वॉटरमार्क जोड़ सकता हूँ?** हाँ – API दोनों प्रकार का समर्थन करता है।  
- **क्या उत्पादन के लिए लाइसेंस आवश्यक है?** एक वैध GroupDocs लाइसेंस आवश्यक है; एक मुफ्त ट्रायल उपलब्ध है।  
- **कौन सा Java संस्करण समर्थित है?** कोई भी JDK 8+ रनटाइम लाइब्रेरी के साथ काम करता है।  
- **बाद में वॉटरमार्क कैसे हटाऊँ?** API की रिमूवल मेथड्स का उपयोग करें – “स्प्रेडशीट से वॉटरमार्क हटाएँ” सेक्शन देखें।

## स्प्रेडशीट में वॉटरमार्क जोड़ना क्या है?
वॉटरमार्क एक अर्ध‑पारदर्शी ओवरले (टेक्स्ट या इमेज) है जो स्प्रेडशीट की सामग्री के पीछे दिखाई देता है। यह फ़ाइल को Excel या अन्य व्यूअर्स में खोलने पर भी दिखाई देता है, और दस्तावेज़ के गोपनीय या स्वामित्व वाले होने का दृश्य संकेत देता है।

## GroupDocs.Watermark for Java का उपयोग क्यों करें?
GroupDocs.Watermark एक सरल, उच्च‑प्रदर्शन API प्रदान करता है जो सभी प्रमुख स्प्रेडशीट फ़ॉर्मेट (XLS, XLSX, ODS) के साथ काम करता है। यह बड़े फ़ाइलों को संभालता है, बैच प्रोसेसिंग का समर्थन करता है, और पोजिशनिंग, अपारदर्शिता, तथा रोटेशन पर सूक्ष्म नियंत्रण देता है—सर्वर पर Microsoft Office की आवश्यकता के बिना।

## पूर्वापेक्षाएँ
शुरू करने से पहले सुनिश्चित करें कि आपके पास हैं:

1. **GroupDocs.Watermark लाइब्रेरी** – संस्करण 24.11 या बाद का।  
2. **Java Development Kit (JDK)** – JDK 8 या नया स्थापित हो।  
3. **Maven** (या कोई अन्य बिल्ड टूल) ताकि डिपेंडेंसीज़ मैनेज की जा सकें।  
4. **बेसिक Java ज्ञान** – आपको क्लासेज़ बनाना और एक्सेप्शन हैंडल करना आता हो।

## GroupDocs.Watermark for Java सेटअप करना
आप लाइब्रेरी को Maven के माध्यम से या सीधे JAR डाउनलोड करके अपने प्रोजेक्ट में जोड़ सकते हैं।

### Maven का उपयोग करना
अपने `pom.xml` फ़ाइल में रिपॉज़िटरी और डिपेंडेंसी जोड़ें:

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
वैकल्पिक रूप से, आधिकारिक रिलीज़ पेज से नवीनतम JAR डाउनलोड करें: [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/)।

#### लाइसेंस प्राप्ति
- **Free Trial** – बिना लागत के सभी फीचर्स टेस्ट करें।  
- **Temporary License** – विस्तारित मूल्यांकन के लिए शॉर्ट‑टर्म लाइसेंस अनुरोध करें।  
- **Full License** – अनलिमिटेड प्रोडक्शन उपयोग के लिए खरीदें।

## बुनियादी इनिशियलाइज़ेशन और सेटअप
अपने Java सोर्स फ़ाइल में आवश्यक क्लासेज़ इम्पोर्ट करें और आगे बढ़ने से पहले लाइब्रेरी को क्लासपाथ में सुनिश्चित करें।

## कार्यान्वयन गाइड
नीचे एक स्टेप‑बाय‑स्टेप walkthrough दिया गया है जो स्प्रेडशीट लोड करने, टेक्स्ट और इमेज दोनों वॉटरमार्क जोड़ने, और अंत में संरक्षित फ़ाइल को सेव करने को कवर करता है।

### स्प्रेडशीट दस्तावेज़ लोड करना
**Overview:** वह Excel फ़ाइल खोलें जिसे आप सुरक्षित करना चाहते हैं।

#### चरण 1: फ़ाइल पथ निर्धारित करें
```java
String filePath = "YOUR_DOCUMENT_DIRECTORY/spreadsheet.xlsx";
```

#### चरण 2: स्प्रेडशीट के लिए लोड विकल्प बनाएं
```java
SpreadsheetLoadOptions loadOptions = new SpreadsheetLoadOptions();
```

#### चरण 3: Watermarker इंस्टेंस इनिशियलाइज़ करें
```java
Watermarker watermarker = new Watermarker(filePath, loadOptions);
```

### टेक्स्ट वॉटरमार्क जोड़ना
**Overview:** “Confidential” जैसे पढ़ने योग्य टेक्स्ट वॉटरमार्क डालें।

#### चरण 1: वॉटरमार्क टेक्स्ट और शैली निर्धारित करें
```java
TextWatermark watermark = new TextWatermark("Confidential", new Font("Arial", 12));
```

#### चरण 2: प्रत्येक शीट पर टेक्स्ट वॉटरमार्क लागू करें
```java
watermarker.add(watermark);
```

### इमेज वॉटरमार्क जोड़ना
**Overview:** मजबूत विज़ुअल प्रोटेक्शन के लिए इमेज (लोगो, सील आदि) का उपयोग करें।

#### चरण 1: इमेज वॉटरमार्क ऑब्जेक्ट निर्धारित करें
```java
ImageWatermark imageWatermark = new ImageWatermark("path/to/image.png");
```

#### चरण 2: दस्तावेज़ पर इमेज वॉटरमार्क लागू करें
```java
watermarker.add(imageWatermark);
```

### वॉटरमार्क किए गए दस्तावेज़ को सहेजना और बंद करना
**Overview:** बदलावों को स्थायी बनाएं और संसाधनों को मुक्त करें।

#### चरण 1: आउटपुट फ़ाइल पथ निर्दिष्ट करें
```java
String outputPath = "YOUR_OUTPUT_DIRECTORY/spreadsheet-out.xlsx";
```

#### चरण 2: वॉटरमार्क किया गया स्प्रेडशीट सहेजें
```java
watermarker.save(outputPath);
```

#### चरण 3: मेमोरी मुक्त करने के लिए Watermarker बंद करें
```java
watermarker.close();
```

## स्प्रेडशीट से वॉटरमार्क कैसे हटाएँ
यदि आपको बाद में वॉटरमार्क हटाना पड़े (उदाहरण के लिए, दस्तावेज़ की गोपनीयता अवधि समाप्त होने के बाद), तो GroupDocs.Watermark एक `remove()` मेथड प्रदान करता है। आप दस्तावेज़ को उसी तरह लोड करेंगे, प्रत्येक वॉटरमार्क को हटाने के लिए `watermarker.remove(watermark)` कॉल करेंगे, और फिर फ़ाइल को फिर से सहेजेंगे। विस्तृत API उपयोग आधिकारिक दस्तावेज़ीकरण में पाया जा सकता है।

## सामान्य समस्याएँ और समाधान
| समस्या | संभावित कारण | समाधान |
|---------|--------------|-----|
| **`FileNotFoundException`** | गलत फ़ाइल पथ | पूर्ण/सापेक्ष पथ की जाँच करें और सुनिश्चित करें कि फ़ाइल मौजूद है। |
| **OutOfMemoryError on large files** | Watermarker इंस्टेंस बंद नहीं करना | हमेशा `watermarker.close()` को `finally` ब्लॉक में कॉल करें या try‑with‑resources का उपयोग करें। |
| **Watermark not visible** | अपारदर्शिता बहुत कम सेट है या सेल्स के पीछे रखा गया है | अपारदर्शिता समायोजित करें या इसे प्रमुख बनाने के लिए `watermark.setRotationAngle(45)` का उपयोग करें। |
| **License errors** | लाइसेंस फ़ाइल गायब या समाप्त हो गई है | वैध `license.lic` फ़ाइल को क्लासपाथ में रखें या प्रोग्रामेटिक रूप से लाइसेंस सेट करें। |

## व्यावहारिक अनुप्रयोग
1. **कॉरपोरेट दस्तावेज़ प्रबंधन** – वितरण से पहले आंतरिक वित्तीय रिपोर्ट को सुरक्षित करें।  
2. **कानूनी फर्में** – लीक को रोकने के लिए केस फ़ाइलों पर “प्रिविलेज्ड” वॉटरमार्क लगाएँ।  
3. **शैक्षणिक संस्थान** – प्लेज़रिज़्म रोकने के लिए छात्र सबमिशन पर स्कूल लोगो लगाएँ।  

## प्रदर्शन संबंधी विचार
- **संसाधन प्रबंधन:** हमेशा `Watermarker` ऑब्जेक्ट्स को बंद करें ताकि नेटिव संसाधन मुक्त हों।  
- **बैच प्रोसेसिंग:** कई फ़ाइलों पर वॉटरमार्किंग को समानांतर करने के लिए Java के `ExecutorService` का उपयोग करें।  
- **मेमोरी मॉनिटरिंग:** 100 MB से बड़ी फ़ाइलों के लिए, स्ट्रीमिंग API या JVM हीप साइज बढ़ाने पर विचार करें।  

## अक्सर पूछे जाने वाले प्रश्न

**Q: क्या मैं GroupDocs.Watermark for Java का उपयोग करके इमेज वॉटरमार्क जोड़ सकता हूँ?**  
A: बिल्कुल। “इमेज वॉटरमार्क जोड़ना” सेक्शन में दिखाए अनुसार `ImageWatermark` क्लास का उपयोग करें।

**Q: स्प्रेडशीट से वॉटरमार्क कैसे हटाऊँ?**  
A: दस्तावेज़ लोड करें, `watermarker.remove(existingWatermark)` कॉल करें, फिर फ़ाइल सहेजें। सटीक ओवरलोड्स के लिए API डॉक्यूमेंट देखें।

**Q: क्या लाइब्रेरी XLSX के अलावा अन्य फ़ॉर्मेट का समर्थन करती है?**  
A: हाँ – यह XLS, ODS, और OpenXML मानक द्वारा समर्थित अन्य स्प्रेडशीट फ़ॉर्मेट के साथ काम करती है।

**Q: वॉटरमार्किंग के दौरान त्रुटियों का सामना करने पर मुझे क्या करना चाहिए?**  
A: फ़ाइल पथ दोबारा जाँचें, सुनिश्चित करें कि लाइसेंस सही ढंग से लोड हुआ है, और गायब डिपेंडेंसीज़ के लिए स्टैक ट्रेस देखें।

**Q: क्या मैं वॉटरमार्क की पोजिशन और रोटेशन को कस्टमाइज़ कर सकता हूँ?**  
A: API `setHorizontalAlignment()`, `setVerticalAlignment()`, और `setRotationAngle()` जैसे मेथड्स प्रदान करता है जिससे आप सटीक प्लेसमेंट कर सकते हैं।

## संसाधन
- **दस्तावेज़ीकरण:** [GroupDocs Watermark Java Documentation](https://docs.groupdocs.com/watermark/java/)  
- **API संदर्भ:** [GroupDocs Watermark API Reference](https://reference.groupdocs.com/watermark/java)  
- **डाउनलोड:** [GroupDocs Downloads](https://releases.groupdocs.com/watermark/java/)  
- **GitHub रिपॉजिटरी:** [GroupDocs.Watermark for Java on GitHub](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)  
- **नि:शुल्क समर्थन फ़ोरम:** [GroupDocs Forum](https://forum.groupdocs.com/c/watermark/10)  
- **अस्थायी लाइसेंस:** [Apply for a Temporary License](https://purchase.groupdocs.com/temporary-license/)

---

**अंतिम अपडेट:** 2026-03-30  
**परीक्षित संस्करण:** GroupDocs.Watermark 24.11 for Java  
**लेखक:** GroupDocs