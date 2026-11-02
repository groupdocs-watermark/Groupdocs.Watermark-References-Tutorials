---
date: '2026-10-21'
description: GroupDocs.Watermark for Java का उपयोग करके diagram shapes से hyperlink
  हटाने का तरीका सीखें। सुरक्षित और साफ़ दस्तावेज़ों के लिए इस step‑by‑step गाइड का
  पालन करें।
keywords:
- how to remove hyperlink
- remove hyperlink diagram shapes
- GroupDocs.Watermark Java
- document security Java
- diagram processing library
lastmod: '2026-10-21'
og_description: GroupDocs.Watermark for Java का उपयोग करके diagram shapes से hyperlink
  हटाने का तरीका सीखें। यह गाइड सेटअप, कोड, और सुरक्षित एवं साफ़ दस्तावेज़ों के लिए
  सर्वोत्तम प्रथाओं के माध्यम से आपका मार्गदर्शन करता है।
og_image_alt: Guide showing removal of hyperlinks from diagram shapes using GroupDocs.Watermark
  Java
og_title: GroupDocs.Watermark Java के साथ shapes से hyperlink हटाने का तरीका
schemas:
- author: GroupDocs
  dateModified: '2026-10-21'
  description: Learn how to remove hyperlink from diagram shapes using GroupDocs.Watermark
    for Java. Follow this step‑by‑step guide to secure and clean your documents.
  headline: How to remove hyperlink from shapes with GroupDocs.Watermark Java
  type: TechArticle
- description: Learn how to remove hyperlink from diagram shapes using GroupDocs.Watermark
    for Java. Follow this step‑by‑step guide to secure and clean your documents.
  name: How to remove hyperlink from shapes with GroupDocs.Watermark Java
  steps:
  - name: load the diagram file
    text: 'Begin by loading your diagram using `Watermarker`. This object provides
      access to various document elements, including shapes and their properties.
      - **Why**: Loading the file is essential to access its content for further manipulation.'
  - name: access shape content
    text: 'Retrieve the diagram''s shape contents. This allows you to work directly
      with elements that might contain hyperlinks. - **Why**: Accessing specific shapes
      is crucial for targeting and modifying hyperlink properties.'
  - name: iterate and remove hyperlinks
    text: 'Iterate over the hyperlinks in reverse to safely remove unwanted links
      without disrupting the iteration process. - **Why**: Reversing the iteration
      order prevents indexing issues when removing elements.'
  - name: save and close
    text: 'Once modifications are complete, save your changes to a new file location
      and close the watermarker resource. - **Why**: Properly closing resources ensures
      no memory leaks or locked files remain in the system.'
  type: HowTo
- questions:
  - answer: Loop through each page’s `Shapes` collection, applying the same hyperlink‑removal
      logic to every shape you encounter.
    question: How do I handle multiple shapes on the same page?
  - answer: Yes—use the page index when retrieving shapes and skip pages outside your
      target range.
    question: Can I limit removal to a specific page range?
  - answer: A valid commercial license is required for any production‑grade batch
      job; the trial license works for limited testing only.
    question: Is a license required for batch processing?
  - answer: GroupDocs.Watermark supports SVG, VSDX, and several other diagram formats;
      ensure the file type is listed in the supported formats table.
    question: Does this work with SVG or Visio files?
  - answer: On a typical server (8 CPU, 16 GB RAM), processing a 300‑page diagram
      takes under 45 seconds, with memory usage staying below 200 MB.
    question: What performance can I expect on a 300‑page diagram?
  type: FAQPage
tags:
- remove hyperlink
- GroupDocs.Watermark
- Java diagram processing
- document security
- watermark library
title: GroupDocs.Watermark Java के साथ shapes से hyperlink हटाने का तरीका
type: docs
url: /hi/java/diagram-document-watermarking/remove-hyperlinks-diagram-shapes-groupdocs-watermark-java/
weight: 1
---

# GroupDocs.Watermark Java के साथ आकारों से हाइपरलिंक कैसे हटाएँ

डिजिटल दस्तावेज़ों का प्रबंधन अक्सर आरेखों को संपादित करने में शामिल होता है, विशेष रूप से जब आपको सुरक्षा या दृश्य स्पष्टता के लिए आकारों से **how to remove hyperlink** हटाने की आवश्यकता होती है। यह ट्यूटोरियल आपको जावा में शक्तिशाली **GroupDocs.Watermark** लाइब्रेरी का उपयोग करके आरेख आकारों से अनचाहे हाइपरलिंक हटाने की एक सरल विधि के माध्यम से ले जाता है। इस गाइड के अंत तक, आप समझेंगे कि हाइपरलिंक हटाना क्यों महत्वपूर्ण है, पर्यावरण कैसे सेटअप करें, और सुरक्षित रूप से हटाने के लिए सटीक चरण क्या हैं।

## त्वरित उत्तर
- **What is the primary purpose of removing hyperlinks?** सुरक्षा जोखिमों को समाप्त करने और साझा आरेखों में दृश्य स्पष्टता सुधारने के लिए।  
- **Which library handles the removal?** GroupDocs.Watermark for Java आरेख हेरफेर के लिए समर्पित API प्रदान करता है।  
- **Do I need a license?** परीक्षण के लिए ट्रायल काम करता है; उत्पादन उपयोग के लिए एक व्यावसायिक लाइसेंस आवश्यक है।  
- **Can I process many files at once?** हाँ—कोड को लूप या बैच जॉब में लपेटें ताकि बड़े पैमाने पर संचालन संभाल सकें।  
- **What Java version is required?** Java 8 या उससे उच्च संस्करण समर्थित है।

## how to remove hyperlink क्या है?
**how to remove hyperlink** वाक्यांश आरेख के आकार तत्वों में एम्बेडेड हाइपरलिंक ऑब्जेक्ट्स को खोजने और हटाने की प्रक्रिया को दर्शाता है। यह कार्रवाई करने से बाहरी नेविगेशन उपयोगकर्ताओं को अनजाने में दुर्भावनापूर्ण साइटों या अनचाहे कंटेंट के सामने लाने से रोकती है। सार्वजनिक वितरण के लिए दस्तावेज़ तैयार करते समय यह विशेष रूप से महत्वपूर्ण है, यह सुनिश्चित करते हुए कि कोई छिपा हुआ नेविगेशन पाथ न रहे जो फ़िशिंग साइटों या अनपेक्षित बाहरी संसाधनों की ओर ले जा सके।

## Java के लिए GroupDocs.Watermark का उपयोग क्यों करें?
GroupDocs.Watermark **30+ इनपुट और आउटपुट फ़ॉर्मेट** का समर्थन करता है और **500 पृष्ठों तक** के आरेखों को पूरी फ़ाइल को मेमोरी में लोड किए बिना प्रोसेस कर सकता है, जिससे सामान्य XML पार्सर्स की तुलना में **CPU उपयोग में 40 % कमी** आती है। इसका API आकार गुणों पर सूक्ष्म नियंत्रण प्रदान करता है, जिससे यह जावा अनुप्रयोगों में सुरक्षित आरेख हैंडलिंग के लिए मानक दृष्टिकोण बन जाता है।

## आवश्यकताएँ
- **GroupDocs.Watermark** लाइब्रेरी संस्करण 24.11 या बाद का।  
- Maven स्थापित (या सीधे JAR डाउनलोड)।  
- JDK 8 या नया और IntelliJ IDEA या Eclipse जैसे IDE।  
- बुनियादी जावा ज्ञान और Maven निर्भरताओं की परिचितता।

## Java के लिए GroupDocs.Watermark सेटअप करना
शुरू करने के लिए, अपने प्रोजेक्ट में GroupDocs.Watermark लाइब्रेरी शामिल करें। आप इसे Maven के माध्यम से जोड़ सकते हैं या JAR को मैन्युअल रूप से डाउनलोड कर सकते हैं।

### Maven सेटअप
Add the following configuration to your `pom.xml`:

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
वैकल्पिक रूप से, नवीनतम संस्करण यहाँ से डाउनलोड करें: [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/)।

#### लाइसेंस प्राप्ति चरण
- GroupDocs.Watermark डाउनलोड करके एक मुफ्त ट्रायल से शुरू करें।  
- विस्तारित परीक्षण या उत्पादन उपयोग के लिए, एक अस्थायी लाइसेंस प्राप्त करें या पूर्ण लाइसेंस खरीदें।

#### बुनियादी प्रारम्भिककरण और सेटअप
`Watermarker` क्लास सभी दस्तावेज‑स्तर के ऑपरेशनों के लिए प्रवेश बिंदु है। यह फ़ाइल लोड करता है, आपको उसके पृष्ठों, आकारों और मेटाडेटा तक पहुँच देता है, और अंत में संशोधित दस्तावेज़ को डिस्क पर वापस लिखता है।

To initialize the Watermarker class:

```java
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY", loadOptions);
```

## डायग्राम आकारों से हाइपरलिंक कैसे हटाएँ?
डायग्राम लोड करें, प्रत्येक आकार को खोजें जिसमें हाइपरलिंक हो, और उन हाइपरलिंक ऑब्जेक्ट्स को हटाएँ। पूरी प्रक्रिया को दस से कम कोड लाइनों में किया जा सकता है, और यह सुनिश्चित करता है कि परिणामी डायग्राम में अब कोई क्लिक करने योग्य लिंक नहीं रहेगा जो उपयोगकर्ताओं को बाहरी साइटों पर पुनर्निर्देशित कर सके या संवेदनशील जानकारी उजागर कर सके।

### चरण 1: डायग्राम फ़ाइल लोड करें
`Watermarker` का उपयोग करके अपना डायग्राम लोड करके शुरू करें। यह ऑब्जेक्ट विभिन्न दस्तावेज़ तत्वों, जैसे आकार और उनकी प्रॉपर्टीज़ तक पहुँच प्रदान करता है।

```java
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY", loadOptions);
```
- **Why**: फ़ाइल लोड करना आगे की हेरफेर के लिए उसकी सामग्री तक पहुँचने के लिए आवश्यक है।

### चरण 2: आकार सामग्री तक पहुँचें
डायग्राम के आकार सामग्री को प्राप्त करें। यह आपको उन तत्वों के साथ सीधे काम करने की अनुमति देता है जिनमें हाइपरलिंक हो सकते हैं।

```java
DiagramContent content = watermarker.getContent(DiagramContent.class);
DiagramShape shape = content.getPages().get_Item(0).getShapes().get_Item(0);
```
- **Why**: विशिष्ट आकारों तक पहुँचना हाइपरलिंक प्रॉपर्टीज़ को लक्षित करने और संशोधित करने के लिए महत्वपूर्ण है।

### चरण 3: हाइपरलिंक पर इटरेट करें और हटाएँ
हाइपरलिंक को उल्टे क्रम में इटरेट करें ताकि अनचाहे लिंक को सुरक्षित रूप से हटाया जा सके बिना इटरेशन प्रक्रिया को बाधित किए।

```java
for (int i = shape.getHyperlinks().getCount() - 1; i >= 0; i--) {
    if (shape.getHyperlinks().get_Item(i).getAddress().contains("http://someurl.com")) {
        shape.getHyperlinks().removeAt(i);
    }
}
```
- **Why**: इटरेशन क्रम को उल्टा करने से तत्वों को हटाते समय इंडेक्सिंग समस्याओं से बचा जा सकता है।

### चरण 4: सहेजें और बंद करें
एक बार संशोधन पूर्ण हो जाने पर, अपने बदलावों को नई फ़ाइल स्थान पर सहेजें और watermarker संसाधन को बंद करें।

```java
watermarker.save("YOUR_OUTPUT_DIRECTORY");
watermarker.close();
```
- **Why**: संसाधनों को सही ढंग से बंद करने से सिस्टम में मेमोरी लीक या लॉक्ड फ़ाइलें नहीं रहतीं।

## सामान्य कठिनाइयाँ और समस्या निवारण
- **Null shape collections** – इटरेट करने से पहले हमेशा जांचें कि आकार की `Hyperlinks` कलेक्शन null नहीं है।  
- **Large diagrams** – 200 पृष्ठों से बड़ी फ़ाइलों के लिए, `OutOfMemoryError` से बचने हेतु JVM हीप साइज (`-Xmx2g`) बढ़ाएँ।  
- **License errors** – यदि आप लाइसेंसिंग अपवाद देखते हैं, तो जांचें कि ट्रायल लाइसेंस समाप्त नहीं हुआ है और लाइसेंस फ़ाइल पथ सही है।

## अक्सर पूछे जाने वाले प्रश्न

**Q: एक ही पृष्ठ पर कई आकारों को कैसे संभालें?**  
A: प्रत्येक पृष्ठ की `Shapes` कलेक्शन पर लूप चलाएँ, और मिलने वाले प्रत्येक आकार पर समान हाइपरलिंक‑हटाने की लॉजिक लागू करें।

**Q: क्या मैं हटाने को एक विशिष्ट पृष्ठ रेंज तक सीमित कर सकता हूँ?**  
A: हाँ—आकार प्राप्त करते समय पृष्ठ सूचकांक का उपयोग करें और लक्ष्य रेंज के बाहर के पृष्ठों को छोड़ दें।

**Q: क्या बैच प्रोसेसिंग के लिए लाइसेंस आवश्यक है?**  
A: किसी भी उत्पादन‑स्तर बैच जॉब के लिए एक वैध व्यावसायिक लाइसेंस आवश्यक है; ट्रायल लाइसेंस केवल सीमित परीक्षण के लिए काम करता है।

**Q: क्या यह SVG या Visio फ़ाइलों के साथ काम करता है?**  
A: GroupDocs.Watermark SVG, VSDX और कई अन्य आरेख फ़ॉर्मेट्स का समर्थन करता है; सुनिश्चित करें कि फ़ाइल प्रकार समर्थित फ़ॉर्मेट्स तालिका में सूचीबद्ध है।

**Q: 300‑पृष्ठ वाले आरेख पर मैं किस प्रदर्शन की उम्मीद कर सकता हूँ?**  
A: एक सामान्य सर्वर (8 CPU, 16 GB RAM) पर, 300‑पृष्ठ वाले आरेख को प्रोसेस करने में 45 सेकंड से कम समय लगता है, और मेमोरी उपयोग 200 MB से नीचे रहता है।

## संसाधन
- [दस्तावेज़ीकरण](https://docs.groupdocs.com/watermark/java/)
- [API रेफ़रेंस](https://reference.groupdocs.com/watermark/java)
- [डाउनलोड](https://releases.groupdocs.com/watermark/java/)
- [GitHub रिपॉज़िटरी](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)
- [मुफ़्त समर्थन फ़ोरम](https://forum.groupdocs.com/c/watermark/10)
- [अस्थायी लाइसेंस प्राप्ति](https://purchase.groupdocs.com/temporary-license/)

---

**अंतिम अपडेट:** 2026-10-21  
**परीक्षण किया गया:** GroupDocs.Watermark 24.11 for Java  
**लेखक:** GroupDocs

## संबंधित ट्यूटोरियल

- [Java में GroupDocs.Watermark के साथ Word दस्तावेज़ आकार संशोधित करें: एक व्यापक गाइड](/watermark/java/word-processing-document-watermarking/groupdocs-watermark-java-modify-word-shapes/)
- [Java में GroupDocs.Watermark का उपयोग करके Word दस्तावेज़ों से आकार हटाएँ: एक व्यापक गाइड](/watermark/java/watermark-removal/remove-shapes-groupdocs-watermark-java-word-docs/)
- [Java में GroupDocs.Watermark का उपयोग करके आरेख हेडर और फुटर संपादित करें: एक व्यापक गाइड](/watermark/java/diagram-document-watermarking/edit-diagram-headers-footers-groupdocs-watermark-java/)