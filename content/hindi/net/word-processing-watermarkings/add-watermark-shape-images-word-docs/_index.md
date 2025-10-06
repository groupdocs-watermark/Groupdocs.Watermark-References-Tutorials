---
title: वर्ड डॉक्स में छवियों को आकार देने के लिए वॉटरमार्क जोड़ें
linktitle: वर्ड डॉक्स में छवियों को आकार देने के लिए वॉटरमार्क जोड़ें
second_title: GroupDocs.Watermark .NET API
description: जानें कि .NET के लिए GroupDocs.Watermark का उपयोग करके Word दस्तावेज़ों में छवियों को आकार देने के लिए वॉटरमार्क कैसे जोड़ें। इस ट्यूटोरियल के साथ दस्तावेज़ सुरक्षा बढ़ाएँ।
weight: 17
url: /hi/net/word-processing-watermarkings/add-watermark-shape-images-word-docs/
type: docs
---
# वर्ड डॉक्स में छवियों को आकार देने के लिए वॉटरमार्क जोड़ें

## परिचय
इस ट्यूटोरियल में, हम जानेंगे कि .NET के लिए GroupDocs.Watermark का उपयोग करके Word दस्तावेज़ों में छवियों को आकार देने के लिए वॉटरमार्क कैसे जोड़ा जाए। वॉटरमार्किंग दस्तावेज़ सुरक्षा का एक महत्वपूर्ण पहलू है, खासकर संवेदनशील या गोपनीय जानकारी से निपटने के दौरान। छवियों को आकार देने के लिए वॉटरमार्क जोड़कर, आप अपने दस्तावेज़ों की अखंडता और सुरक्षा सुनिश्चित कर सकते हैं।
## आवश्यक शर्तें
शुरू करने से पहले, सुनिश्चित करें कि आपके पास निम्नलिखित हैं:
1.  .NET के लिए GroupDocs.Watermark: यहां से GroupDocs.Watermark लाइब्रेरी डाउनलोड और इंस्टॉल करें।[डाउनलोड पेज](https://releases.groupdocs.com/Watermark/net/).
2. दस्तावेज़: वर्ड दस्तावेज़ तैयार करें जहाँ आप वॉटरमार्क जोड़ना चाहते हैं।
3. विकास परिवेश: अपना पसंदीदा .NET विकास परिवेश स्थापित करें।
## नामस्थान आयात करें
कोड लिखने से पहले, आवश्यक नामस्थान आयात करना सुनिश्चित करें:
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.WordProcessing;
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## चरण 1: दस्तावेज़ लोड करें
सबसे पहले, अपने दस्तावेज़ का पथ परिभाषित करें और आउटपुट फ़ाइल नाम निर्दिष्ट करें:
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
```
## चरण 2: वॉटरमार्कर प्रारंभ करें
 त्वरित करें ए`Watermarker` दस्तावेज़ पथ और वैकल्पिक लोड विकल्प प्रदान करके ऑब्जेक्ट करें:
```csharp
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // यहां वॉटरमार्किंग तर्क जोड़ें
}
```
## चरण 3: टेक्स्ट वॉटरमार्क बनाएं
टेक्स्ट वॉटरमार्क को वांछित गुणों जैसे टेक्स्ट, फ़ॉन्ट, संरेखण, रोटेशन, आकार इत्यादि के साथ परिभाषित करें:
```csharp
TextWatermark watermark = new TextWatermark("Protected image", new Font("Arial", 8));
watermark.HorizontalAlignment = HorizontalAlignment.Center;
watermark.VerticalAlignment = VerticalAlignment.Center;
watermark.RotateAngle = 45;
watermark.SizingType = SizingType.ScaleToParentDimensions;
watermark.ScaleFactor = 1;
```
## चरण 4: छवियों को आकार देने के लिए वॉटरमार्क लागू करें
आकृति छवियों की पहचान करने और वॉटरमार्क जोड़ने के लिए दस्तावेज़ अनुभागों और आकृतियों के माध्यम से पुनरावृति करें:
```csharp
WordProcessingContent content = watermarker.GetContent<WordProcessingContent>();
foreach (WordProcessingSection section in content.Sections)
{
    foreach (WordProcessingShape shape in section.Shapes)
    {
        if (shape.HeaderFooter == null && shape.Image != null)
        {
            shape.Image.Add(watermark);
        }
    }
}
```
## चरण 5: दस्तावेज़ सहेजें
दस्तावेज़ को निर्दिष्ट आउटपुट फ़ाइल में जोड़े गए वॉटरमार्क के साथ सहेजें:
```csharp
watermarker.Save(outputFileName);
```

## निष्कर्ष
इस ट्यूटोरियल में, हमने सीखा कि .NET के लिए GroupDocs.Watermark का उपयोग करके Word दस्तावेज़ों में छवियों को आकार देने के लिए वॉटरमार्क कैसे जोड़ें। चरण-दर-चरण मार्गदर्शिका का पालन करके और GroupDocs.Watermark की शक्तिशाली सुविधाओं का लाभ उठाकर, आप अपने दस्तावेज़ों की सुरक्षा और संरक्षण को प्रभावी ढंग से बढ़ा सकते हैं।
## अक्सर पूछे जाने वाले प्रश्न
### क्या मैं वॉटरमार्क टेक्स्ट के स्वरूप को अनुकूलित कर सकता हूँ?
हां, आप अपनी प्राथमिकताओं के अनुसार वॉटरमार्क को अनुकूलित करने के लिए विभिन्न गुणों जैसे फ़ॉन्ट, आकार, रंग, रोटेशन कोण और संरेखण को समायोजित कर सकते हैं।
### क्या GroupDocs.Watermark Word के अलावा अन्य दस्तावेज़ प्रारूपों का समर्थन करता है?
हां, GroupDocs.Watermark पीडीएफ, एक्सेल, पॉवरपॉइंट और अन्य सहित दस्तावेज़ प्रारूपों की एक विस्तृत श्रृंखला के लिए समर्थन प्रदान करता है।
### क्या एक ही दस्तावेज़ में एकाधिक वॉटरमार्क जोड़ना संभव है?
बिल्कुल, आप एक ही दस्तावेज़ में विभिन्न सामग्री, शैलियों और स्थितियों के साथ कई वॉटरमार्क जोड़ सकते हैं।
### क्या मैं GroupDocs.Watermark का उपयोग करके दस्तावेज़ों से वॉटरमार्क हटा सकता हूँ?
हाँ, GroupDocs.Watermark दस्तावेज़ों से वॉटरमार्क का कुशलतापूर्वक पता लगाने और हटाने की सुविधाएँ प्रदान करता है।
### क्या GroupDocs.Watermark क्रॉस-प्लेटफ़ॉर्म अनुकूलता प्रदान करता है?
हां, GroupDocs.Watermark .NET फ्रेमवर्क, .NET कोर और .NET स्टैंडर्ड के साथ संगत है, जो विभिन्न प्लेटफार्मों पर निर्बाध एकीकरण सुनिश्चित करता है।