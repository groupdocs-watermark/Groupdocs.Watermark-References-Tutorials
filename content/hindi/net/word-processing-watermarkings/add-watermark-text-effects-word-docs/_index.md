---
title: वर्ड डॉक्स में टेक्स्ट इफेक्ट्स के साथ वॉटरमार्क जोड़ें
linktitle: वर्ड डॉक्स में टेक्स्ट इफेक्ट्स के साथ वॉटरमार्क जोड़ें
second_title: GroupDocs.Watermark .NET API
description: .NET के लिए GroupDocs.Watermark का उपयोग करके Word दस्तावेज़ों में टेक्स्ट इफ़ेक्ट के साथ कस्टम वॉटरमार्क जोड़ने का तरीका जानें। दस्तावेज़ सुरक्षा और दृश्य अपील सहजता से।
weight: 21
url: /hi/net/word-processing-watermarkings/add-watermark-text-effects-word-docs/
---
## परिचय
इस ट्यूटोरियल में, हम जानेंगे कि .NET के लिए GroupDocs.Watermark का उपयोग करके Word दस्तावेज़ों में टेक्स्ट इफ़ेक्ट के साथ वॉटरमार्क कैसे जोड़ा जाए। इन चरण-दर-चरण निर्देशों का पालन करके, आप अपने दस्तावेज़ों को अनुकूलित वॉटरमार्क के साथ बढ़ाने में सक्षम होंगे जिसमें विभिन्न पाठ प्रभाव शामिल हैं।
## आवश्यक शर्तें
आरंभ करने से पहले, सुनिश्चित करें कि आपके पास निम्नलिखित हैं:
1.  .NET के लिए GroupDocs.Watermark: लाइब्रेरी को डाउनलोड और इंस्टॉल करें[वेबसाइट](https://releases.groupdocs.com/Watermark/net/).
2. दस्तावेज़ पथ: उस Word दस्तावेज़ का पथ जानें जिसमें आप वॉटरमार्क जोड़ना चाहते हैं।
3. आउटपुट निर्देशिका: एक निर्देशिका रखें जहाँ आप संशोधित दस्तावेज़ को सहेजना चाहते हैं।

## नामस्थान आयात करें
आवश्यक कक्षाओं और विधियों तक पहुँचने के लिए आवश्यक नामस्थान आयात करना सुनिश्चित करें:
```csharp
using GroupDocs.Watermark.Contents;
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## चरण 1: दस्तावेज़ लोड करें
उस Word दस्तावेज़ को लोड करें जिस पर आप वॉटरमार्क जोड़ना चाहते हैं।
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // वॉटरमार्क जोड़ने के लिए कोड यहां दिया गया है
}
```
## चरण 2: टेक्स्ट इफ़ेक्ट के साथ वॉटरमार्क जोड़ें
वांछित टेक्स्ट और फ़ॉन्ट के साथ एक टेक्स्ट वॉटरमार्क बनाएं, फिर लाइन प्रारूप जैसे टेक्स्ट प्रभावों को परिभाषित करें।
```csharp
TextWatermark watermark = new TextWatermark("Test watermark", new Font("Arial", 19));
WordProcessingTextEffects effects = new WordProcessingTextEffects();
effects.LineFormat.Enabled = true;
effects.LineFormat.Color = Color.Red;
effects.LineFormat.DashStyle = OfficeDashStyle.DashDotDot;
effects.LineFormat.LineStyle = OfficeLineStyle.Triple;
effects.LineFormat.Weight = 1;
```
## चरण 3: वॉटरमार्क विकल्प अनुकूलित करें
वॉटरमार्क अनुभाग विकल्पों को परिभाषित करें, जैसे पाठ प्रभाव, और उन्हें वॉटरमार्क पर निर्दिष्ट करें।
```csharp
WordProcessingWatermarkSectionOptions options = new WordProcessingWatermarkSectionOptions();
options.Effects = effects;
watermarker.Add(watermark, options);
```
## चरण 4: दस्तावेज़ सहेजें
संशोधित दस्तावेज़ को जोड़े गए वॉटरमार्क के साथ सहेजें।
```csharp
watermarker.Save(outputFileName);
```

## निष्कर्ष
Word दस्तावेज़ों में टेक्स्ट इफ़ेक्ट के साथ वॉटरमार्क जोड़ने से उनकी दृश्य अपील और सुरक्षा में उल्लेखनीय वृद्धि हो सकती है। .NET के लिए GroupDocs.Watermark के साथ, यह प्रक्रिया सुव्यवस्थित और अनुकूलन योग्य हो जाती है, जिससे आप पेशेवर दिखने वाले दस्तावेज़ कुशलतापूर्वक बना सकते हैं।
## अक्सर पूछे जाने वाले प्रश्न
### क्या मैं वॉटरमार्क टेक्स्ट के फ़ॉन्ट और आकार को अनुकूलित कर सकता हूँ?
हां, आप टेक्स्टवॉटरमार्क ऑब्जेक्ट बनाते समय फ़ॉन्ट और आकार निर्दिष्ट कर सकते हैं।
### क्या एक ही दस्तावेज़ में एकाधिक वॉटरमार्क जोड़ना संभव है?
बिल्कुल, .NET के लिए GroupDocs.Watermark एक ही दस्तावेज़ में विभिन्न सेटिंग्स के साथ कई वॉटरमार्क जोड़ने का समर्थन करता है।
### क्या GroupDocs.Watermark Word के अलावा अन्य दस्तावेज़ प्रारूपों का समर्थन करता है?
हां, यह पीडीएफ, एक्सेल, पावरपॉइंट और अन्य सहित दस्तावेज़ प्रारूपों की एक विस्तृत श्रृंखला का समर्थन करता है।
### क्या मैं दस्तावेज़ में वॉटरमार्क जोड़ने के बाद उसे हटा सकता हूँ?
हाँ, लाइब्रेरी दस्तावेज़ों से वॉटरमार्क आसानी से हटाने के तरीके प्रदान करती है।
### क्या परीक्षण प्रयोजनों के लिए कोई परीक्षण संस्करण उपलब्ध है?
 हां, आप यहां से नि:शुल्क परीक्षण संस्करण डाउनलोड कर सकते हैं[यहाँ](https://releases.groupdocs.com/).