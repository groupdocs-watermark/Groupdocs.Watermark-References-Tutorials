---
date: '2026-04-07'
description: GroupDocs.Watermark का उपयोग करके जावा में ईमेल बॉडी कैसे खोजें, जिसमें
  कई कीवर्ड ईमेल की खोज और ईमेल वॉटरमार्क को कैसे हटाएँ, शामिल है।
keywords:
- search email body java
- search multiple keywords email
- how to remove email watermarks
title: 'GroupDocs.Watermark के साथ जावा में ईमेल बॉडी खोजें: एक व्यापक मार्गदर्शिका'
type: docs
url: /hi/java/email-document-watermarking/master-groupdocs-watermark-java-email-text-search/
weight: 1
---

# GroupDocs.Watermark के साथ ईमेल बॉडी जावा खोजें

यदि आपको **search email body java** जल्दी और विश्वसनीय रूप से करना है, तो आप सही जगह पर आए हैं। इस ट्यूटोरियल में हम देखेंगे कि GroupDocs.Watermark for Java आपको ईमेल विषय, HTML बॉडी और साधारण टेक्स्ट बॉडी में विशिष्ट टेक्स्ट कैसे खोजने देता है, और बाद में अनचाहे वॉटरमार्क को कैसे साफ़ किया जा सकता है। अंत तक, आप एक मजबूत समाधान लागू कर पाएंगे जो एकल या कई कीवर्ड पर काम करता है और आवश्यकता पड़ने पर ईमेल वॉटरमार्क भी हटाता है।

## त्वरित उत्तर
- **What does “search email body java” mean?** यह Java कोड (GroupDocs.Watermark के साथ) का उपयोग करके ईमेल की सामग्री के भीतर टेक्स्ट खोजने को दर्शाता है।  
- **Can I search multiple keywords email at once?** हाँ – अलग-अलग `SearchCriteria` ऑब्जेक्ट बनाकर उन्हें मिलाएँ।  
- **How to remove email watermarks?** खोज के बाद `PossibleWatermarkCollection.clear()` मेथड का उपयोग करके ईमेल वॉटरमार्क हटाएँ।  
- **Do I need a license?** परीक्षण के लिए एक मुफ्त ट्रायल काम करता है; उत्पादन के लिए स्थायी लाइसेंस आवश्यक है।  
- **Which IDE works best?** IntelliJ IDEA या Eclipse दोनों पूरी तरह समर्थित हैं।

## आप क्या सीखेंगे
- GroupDocs.Watermark for Java को स्थापित और कॉन्फ़िगर करना।  
- विषय और बॉडियों में **search email body java** के लिए खोज मानदंड सेट करना।  
- **search multiple keywords email** को एक ही रन में करने की तकनीकें।  
- उन्हें खोजने के बाद **how to remove email watermarks** के सटीक चरण।

## GroupDocs.Watermark के साथ ईमेल बॉडी जावा क्यों खोजें?
GroupDocs.Watermark एक उच्च‑स्तरीय API प्रदान करता है जो .msg फ़ाइलों को पार्स करने, विभिन्न बॉडी फ़ॉर्मेट को संभालने और वॉटरमार्क प्रबंधन की जटिलताओं को सारांशित करता है। यह कस्टम पार्सर बनाने की तुलना में आपका समय बचाता है और बड़े ईमेल बैचों में सुसंगत परिणाम सुनिश्चित करता है।

## आवश्यकताएँ
- Java Development Kit (JDK) 8 या नया।  
- Maven (या मैन्युअली JAR जोड़ने की क्षमता)।  
- Java और ईमेल फ़ाइल फ़ॉर्मेट (.msg, .eml) की बुनियादी जानकारी।  

## GroupDocs.Watermark for Java सेटअप
GroupDocs.Watermark for Java दस्तावेज़ों, जिसमें ईमेल शामिल हैं, में वॉटरमार्किंग और टेक्स्ट खोज को सरल बनाता है। नीचे दो सबसे सामान्य तरीके हैं जिनसे आप लाइब्रेरी को अपने प्रोजेक्ट में जोड़ सकते हैं।

### Maven सेटअप
Include the following in your `pom.xml` file to add GroupDocs.Watermark as a dependency:
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
वैकल्पिक रूप से, आप नवीनतम संस्करण सीधे [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/) से डाउनलोड कर सकते हैं।

### लाइसेंस प्राप्त करने के चरण
- **Free Trial:** बुनियादी कार्यक्षमताओं का परीक्षण करने के लिए एक मुफ्त ट्रायल से शुरू करें।  
- **Temporary License:** विस्तारित एक्सेस और परीक्षण के लिए एक अस्थायी लाइसेंस प्राप्त करें।  
- **Purchase:** यदि GroupDocs.Watermark आपकी जरूरतों को पूरा करता है तो खरीदने पर विचार करें।

#### बेसिक इनिशियलाइज़ेशन
Initialize the `Watermarker` class as shown below:
```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.EmailLoadOptions;

EmailLoadOptions loadOptions = new EmailLoadOptions();
Watermarker watermarker = new Watermarker("input_email.msg", loadOptions);
```

## कार्यान्वयन गाइड

### फीचर 1: ईमेल बॉडी में टेक्स्ट खोजें
यह फीचर ईमेल के विषय और बॉडी में विशिष्ट टेक्स्ट खोजने में सक्षम बनाता है।

#### अवलोकन
हम दिखाएंगे कि Java कोड का उपयोग करके GroupDocs.Watermark को ईमेल संदेश के विभिन्न भागों में खोज करने के लिए कैसे कॉन्फ़िगर किया जाए।

##### चरण 1: दस्तावेज़ पाथ निर्धारित करें
Set up your input and output paths for handling emails:
```java
String inputDocumentPath = "YOUR_DOCUMENT_DIRECTORY/message.msg";
String outputDocumentPath = "YOUR_OUTPUT_DIRECTORY/output_message.msg";
```

##### चरण 2: लोड विकल्प और Watermarker सेट करें
Initialize the `EmailLoadOptions` and `Watermarker` to work with your email document.
```java
EmailLoadOptions loadOptions = new EmailLoadOptions();
Watermarker watermarker = new Watermarker(inputDocumentPath, loadOptions);
```

##### चरण 3: खोज मानदंड बनाएं
Define criteria for searching text. We'll use a case‑insensitive search for the keyword **"test"**:
```java
import com.groupdocs.watermark.search.SearchCriteria;
import com.groupdocs.watermark.search.TextSearchCriteria;

SearchCriteria criteria = new TextSearchCriteria("test", false);
```

##### चरण 4: खोज स्थान निर्दिष्ट करें
Configure the search to cover both the subject and body of emails:
```java
watermarker.getSearchableObjects().setEmailSearchableObjects(
    EmailSearchableObjects.Subject |
    EmailSearchableObjects.HtmlBody | 
    EmailSearchableObjects.PlainTextBody);
```

##### चरण 5: खोज निष्पादित करें और वॉटरमार्क साफ़ करें
Perform the search and remove any found watermarks:
```java
import com.groupdocs.watermark.search.PossibleWatermarkCollection;

PossibleWatermarkCollection watermarks = watermarker.search(criteria);
watermarks.clear();
```

##### चरण 6: परिवर्तन सहेजें
After processing, save your changes to a new document:
```java
watermarker.save(outputDocumentPath);
// Close the Watermarker instance to release resources
watermarker.close();
```

#### समस्या निवारण टिप्स
- **Common Issue:** यदि खोज परिणाम खाली हैं, तो सुनिश्चित करें कि टेक्स्ट ईमेल बॉडी या विषय में मौजूद है।  
- **Performance Tip:** केवल आवश्यक सेक्शन तक खोज को सीमित करके अनुकूलित करें।

### फीचर 2: ईमेल दस्तावेज़ विकल्प लोड करें
यह अनुभाग बताता है कि GroupDocs.Watermark के साथ प्रोसेसिंग के लिए ईमेल दस्तावेज़ लोड करते समय अतिरिक्त विकल्प कैसे सेट किए जा सकते हैं।

#### अवलोकन
लोड विकल्पों को कॉन्फ़िगर करने से दस्तावेज़ों के हैंडलिंग पर अधिक नियंत्रण मिलता है, जैसे पासवर्ड सुरक्षा या एन्कोडिंग सेटिंग्स निर्दिष्ट करना।

##### चरण 1: लोड विकल्प कॉन्फ़िगर करें
Here's a basic setup for `EmailLoadOptions`:
```java
EmailLoadOptions loadOptions = new EmailLoadOptions();
// Additional configurations can be added here.
```

#### मुख्य कॉन्फ़िगरेशन विकल्प
- **Password Protection:** यदि आपके ईमेल एन्क्रिप्टेड हैं तो पासवर्ड निर्दिष्ट करें।  
- **Encoding Settings:** आवश्यकतानुसार विशिष्ट एन्कोडिंग प्रकार निर्धारित करें।

## कई कीवर्ड ईमेल कैसे खोजें
यदि आपको एक ही पास में कई शब्द खोजने हैं, तो कई `SearchCriteria` ऑब्जेक्ट बनाकर उन्हें लॉजिकल **OR** या **AND** ऑपरेटरों से मिलाएँ। API आपको मानदंडों को चेन करने देता है, इसलिए आप “invoice” **or** “receipt” को अलग-अलग लूप चलाए बिना खोज सकते हैं।

## ईमेल वॉटरमार्क कैसे हटाएँ
वॉटरमार्क (या आपके मानदंड से मेल खाने वाले किसी भी टेक्स्ट) खोजने के बाद, `PossibleWatermarkCollection.clear()` मेथड उन्हें ईमेल दस्तावेज़ से हटा देता है। यह वही सटीक चरण है जिसे हमने ऊपर **Step 5** में उपयोग किया था, और यह किसी भी संख्या में मैच के लिए काम करता है।

## व्यावहारिक अनुप्रयोग

### उपयोग केस 1: स्वचालित ईमेल प्रोसेसिंग
विशिष्ट सामग्री को कुशलतापूर्वक खोजने के लिए बड़े पैमाने पर ईमेल डेटा के फ़िल्टरिंग और प्रोसेसिंग को स्वचालित करें।

### उपयोग केस 2: कानूनी अनुपालन जांच
कॉर्पोरेट ईमेल में संवेदनशील जानकारी खोजकर अनुपालन सुनिश्चित करें।

### उपयोग केस 3: ग्राहक समर्थन स्वचालन
ग्राहक पूछताछ में कीवर्ड या वाक्यांश जल्दी खोजकर समर्थन कार्यप्रवाह को सुव्यवस्थित करें।

## प्रदर्शन विचार
GroupDocs.Watermark का उपयोग करते समय, प्रदर्शन को अनुकूलित करने के लिए निम्नलिखित पर विचार करें:
- **Resource Management:** बड़े ईमेल डेटासेट को संभालने के लिए मेमोरी और प्रोसेसिंग पावर को कुशलतापूर्वक प्रबंधित करें।  
- **Java Memory Management Best Practices:** नियमित रूप से संसाधन उपयोग की निगरानी करें और संसाधनों को तुरंत रिलीज़ करें।

## अक्सर पूछे जाने वाले प्रश्न
**Q:** मैं एन्क्रिप्टेड ईमेल को GroupDocs.Watermark के साथ कैसे संभालूँ?  
**A:** `Watermarker` को इनिशियलाइज़ करते समय पासवर्ड निर्दिष्ट करने के लिए `EmailLoadOptions` का उपयोग करें।

**Q:** क्या मैं एक साथ कई कीवर्ड खोज सकता हूँ?  
**A:** हाँ, अलग-अलग `SearchCriteria` इंस्टेंस बनाकर उन्हें लॉजिकल ऑपरेशन्स से मिलाएँ।

**Q:** क्या GroupDocs.Watermark Java मुफ्त में उपयोग किया जा सकता है?  
**A:** एक मुफ्त ट्रायल उपलब्ध है; विस्तारित फीचर्स के लिए लाइसेंस खरीदने पर विचार करें।

**Q:** मैं बड़ी मात्रा में ईमेल को कुशलतापूर्वक कैसे संभालूँ?  
**A:** विशिष्ट ईमेल सेक्शन को लक्षित करके और संसाधनों को प्रभावी ढंग से प्रबंधित करके अपनी खोजों को अनुकूलित करें।

**Q:** अतिरिक्त सहायता या समर्थन कहाँ मिल सकता है?  
**A:** सामुदायिक समर्थन के लिए [GroupDocs forum](https://forum.groupdocs.com/c/watermark/10) पर जाएँ या उनके मुफ्त सपोर्ट चैनल से संपर्क करें।

## संसाधन
- **Documentation:** विस्तृत गाइड के लिए [GroupDocs Documentation](https://docs.groupdocs.com/watermark/java/) देखें।  
- **API Reference:** तकनीकी विवरण के लिए [GroupDocs API](https://apireference.groupdocs.com/watermark/java/) देखें।

---

**अंतिम अपडेट:** 2026-04-07  
**परीक्षित संस्करण:** GroupDocs.Watermark 24.11 for Java  
**लेखक:** GroupDocs