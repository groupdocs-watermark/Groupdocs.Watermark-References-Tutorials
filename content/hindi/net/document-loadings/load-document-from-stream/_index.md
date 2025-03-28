---
title: स्ट्रीम से दस्तावेज़ लोड करें
linktitle: स्ट्रीम से दस्तावेज़ लोड करें
second_title: GroupDocs.Watermark .NET API
description: इस गाइड से जानें कि .NET के लिए GroupDocs.Watermark का उपयोग करके दस्तावेज़ों में वॉटरमार्क कैसे जोड़ें। दस्तावेज़ सुरक्षा बढ़ाने की चाहत रखने वाले डेवलपर्स के लिए बिल्कुल सही।
weight: 11
url: /hi/net/document-loadings/load-document-from-stream/
---

# स्ट्रीम से दस्तावेज़ लोड करें

## परिचय
क्या आप .NET का उपयोग करके अपने दस्तावेज़ों में वॉटरमार्क जोड़ना चाह रहे हैं? आगे कोई तलाश नहीं करें! .NET के लिए GroupDocs.Watermark एक शक्तिशाली और उपयोग में आसान लाइब्रेरी है जो आपको विभिन्न दस्तावेज़ प्रारूपों में वॉटरमार्क प्रबंधित करने की अनुमति देती है। चाहे आप पीडीएफ, वर्ड दस्तावेज़, या छवियों के साथ काम कर रहे हों, यह टूल आपको कवर कर लेगा। इस ट्यूटोरियल में, हम आपको एक स्ट्रीम से दस्तावेज़ लोड करने और चरण दर चरण वॉटरमार्क जोड़ने की प्रक्रिया के बारे में बताएंगे। तो, आइए सीधे गोता लगाएँ!
## आवश्यक शर्तें
शुरू करने से पहले, सुनिश्चित करें कि आपके पास निम्नलिखित सेटअप है:
1. विजुअल स्टूडियो: विजुअल स्टूडियो का कोई भी हालिया संस्करण ठीक काम करेगा।
2. .NET फ्रेमवर्क: सुनिश्चित करें कि आपके पास .NET फ्रेमवर्क 4.0 या उच्चतर स्थापित है।
3.  .NET के लिए GroupDocs.Watermark: आप इसे यहां से डाउनलोड कर सकते हैं[यहाँ](https://releases.groupdocs.com/Watermark/net/).
4. सी# का बुनियादी ज्ञान: सी# और ऑब्जेक्ट-ओरिएंटेड प्रोग्रामिंग अवधारणाओं से परिचित होना सहायक होगा।

## नामस्थान आयात करें
अपने प्रोजेक्ट में GroupDocs.Watermark का उपयोग करने के लिए, आपको आवश्यक नामस्थान आयात करने की आवश्यकता होगी। यह आपको बिना किसी समस्या के लाइब्रेरी की सुविधाओं तक पहुंचने में सक्षम करेगा।
```csharp
using System;
using System.IO;
using GroupDocs.Watermark.Watermarks;
```
## चरण 1: अपना प्रोजेक्ट स्थापित करना
सबसे पहली बात, आपको अपना प्रोजेक्ट विजुअल स्टूडियो में सेट करना होगा। यहां बताया गया है कि आप इसे कैसे करते हैं:
1. एक नया प्रोजेक्ट बनाएं: विज़ुअल स्टूडियो खोलें और एक नया C# कंसोल एप्लिकेशन प्रोजेक्ट बनाएं।
2.  GroupDocs.Watermark स्थापित करें: NuGet पैकेज मैनेजर के माध्यम से GroupDocs.Watermark लाइब्रेरी स्थापित करें। बस खोजें`GroupDocs.Watermark` और इसे इंस्टॉल करें.
## चरण 2: दस्तावेज़ पथ परिभाषित करें
इसके बाद, आपको अपने दस्तावेज़ और आउटपुट फ़ाइल के लिए पथ परिभाषित करने की आवश्यकता है जहां वॉटरमार्क दस्तावेज़ सहेजा जाएगा।
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
```
 प्रतिस्थापित करें`"Your Document Path"` दस्तावेज़ के वास्तविक पथ के साथ जिसे आप वॉटरमार्क करना चाहते हैं और`"Your Document Directory"` उस निर्देशिका के साथ जहां आप वॉटरमार्क दस्तावेज़ को सहेजना चाहते हैं।
## चरण 3: दस्तावेज़ को स्ट्रीम से लोड करें
अब, दस्तावेज़ को एक स्ट्रीम से लोड करते हैं। इसमें दस्तावेज़ को एक स्ट्रीम के रूप में खोलना और फिर इसका उपयोग करना शामिल है`Watermarker` इसे प्रबंधित करने के लिए GroupDocs.Watermark लाइब्रेरी से कक्षा।
```csharp
using (Stream document = File.OpenRead(documentPath))
using (Watermarker watermarker = new Watermarker(document))
{
    // वॉटरमार्क प्रबंधित करने के लिए आपका कोड यहां जाएगा
}
```
 यह कोड स्निपेट सुनिश्चित करता है कि दस्तावेज़ को एक स्ट्रीम के रूप में खोला गया है`Watermarker` इस स्ट्रीम के साथ कक्षा प्रारंभ की गई है।`using` कथन यह सुनिश्चित करते हैं कि उपयोग के बाद संसाधनों का उचित निपटान किया जाए।
## चरण 4: वॉटरमार्क बनाएं और जोड़ें
GroupDocs.Watermark के साथ वॉटरमार्क बनाना आसान है। इस उदाहरण में, हम एक सरल टेक्स्ट वॉटरमार्क बनाएंगे।
```csharp
TextWatermark watermark = new TextWatermark("Test watermark", new Font("Arial", 12));
watermarker.Add(watermark);
```
 यहां, हम एक बनाते हैं`TextWatermark` "वॉटरमार्क का परीक्षण करें" टेक्स्ट के साथ ऑब्जेक्ट करें और फ़ॉन्ट विवरण निर्दिष्ट करें। फिर, हम इस वॉटरमार्क को का उपयोग करके दस्तावेज़ में जोड़ते हैं`Add` की विधि`Watermarker` कक्षा।
## चरण 5: वॉटरमार्क दस्तावेज़ सहेजें
अंत में, वॉटरमार्क वाले दस्तावेज़ को निर्दिष्ट आउटपुट पथ पर सहेजें।
```csharp
watermarker.Save(outputFileName);
```
 यह कोड दस्तावेज़ को नए जोड़े गए वॉटरमार्क के साथ सहेजता है`outputFileName` पथ जो आपने पहले परिभाषित किया था।

## निष्कर्ष
बधाई हो! आपने .NET के लिए GroupDocs.Watermark का उपयोग करके अपने दस्तावेज़ में सफलतापूर्वक वॉटरमार्क जोड़ लिया है। यह लाइब्रेरी विभिन्न दस्तावेज़ प्रारूपों में वॉटरमार्क प्रबंधित करना अविश्वसनीय रूप से आसान बनाती है। चाहे आपको टेक्स्ट, चित्र, या अन्य प्रकार के वॉटरमार्क जोड़ने की आवश्यकता हो, GroupDocs.Watermark के पास आपके लिए आवश्यक उपकरण हैं। को जांचना न भूलें[प्रलेखन](https://tutorials.groupdocs.com/Watermark/net/) अधिक उन्नत सुविधाओं और अनुकूलन विकल्पों के लिए।
## अक्सर पूछे जाने वाले प्रश्न
### .NET के लिए GroupDocs.Watermark का उपयोग करके मैं किस प्रकार के वॉटरमार्क जोड़ सकता हूँ?
आप टेक्स्ट वॉटरमार्क, छवि वॉटरमार्क और यहां तक कि जटिल आकार और लोगो भी जोड़ सकते हैं। लाइब्रेरी अनुकूलन विकल्पों की एक विस्तृत श्रृंखला का समर्थन करती है।
### क्या मैं GroupDocs.Watermark का उपयोग करके दस्तावेज़ों से वॉटरमार्क हटा सकता हूँ?
हाँ, GroupDocs.Watermark आपको दस्तावेज़ों से मौजूदा वॉटरमार्क हटाने की भी अनुमति देता है।
### क्या GroupDocs.Watermark के लिए कोई निःशुल्क परीक्षण उपलब्ध है?
 हाँ, आप नि:शुल्क परीक्षण डाउनलोड कर सकते हैं[यहाँ](https://releases.groupdocs.com/).
### मैं GroupDocs.Watermark के लिए लाइसेंस कैसे खरीदूं?
आप सीधे यहां से लाइसेंस खरीद सकते हैं[ग्रुपडॉक्स वेबसाइट](https://purchase.groupdocs.com/buy).
### यदि मुझे कोई समस्या आती है तो मुझे सहायता कहाँ से मिल सकती है?
 समर्थन के लिए, आप पर जा सकते हैं[GroupDocs.वॉटरमार्क समर्थन फ़ोरम](https://forum.groupdocs.com/c/watermark/19).