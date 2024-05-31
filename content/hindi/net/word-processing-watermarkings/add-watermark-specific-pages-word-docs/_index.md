---
title: वर्ड डॉक्स में विशिष्ट पेजों पर वॉटरमार्क जोड़ें
linktitle: वर्ड डॉक्स में विशिष्ट पेजों पर वॉटरमार्क जोड़ें
second_title: GroupDocs.Watermark .NET API
description: .NET के लिए वॉटरमार्क का उपयोग करके आसानी से Word दस्तावेज़ों में विशिष्ट पृष्ठों पर वॉटरमार्क जोड़ने का तरीका जानें। दस्तावेज़ सुरक्षा और ब्रांडिंग बढ़ाएँ।
type: docs
weight: 18
url: /hi/net/word-processing-watermarkings/add-watermark-specific-pages-word-docs/
---
## परिचय
इस ट्यूटोरियल में, हम .NET के लिए Groupdocs.Watermark का उपयोग करके Word दस्तावेज़ों में विशिष्ट पृष्ठों पर वॉटरमार्क जोड़ने की प्रक्रिया के बारे में जानेंगे। वॉटरमार्किंग दस्तावेज़ प्रबंधन का एक महत्वपूर्ण पहलू है, जो आपके दस्तावेज़ों को सुरक्षा और ब्रांडिंग प्रदान करता है। .NET के लिए Groupdocs.Watermark के साथ, आप सटीकता और दक्षता के साथ आसानी से अपने Word दस्तावेज़ों में टेक्स्ट या छवि वॉटरमार्क जोड़ सकते हैं।
## आवश्यक शर्तें
शुरू करने से पहले, सुनिश्चित करें कि आपके पास निम्नलिखित आवश्यकताएँ हैं:
1.  .NET के लिए Groupdocs.Watermark: .NET के लिए Groupdocs.Watermark को डाउनलोड और इंस्टॉल करें[यहाँ](https://releases.groupdocs.com/Watermark/net/).
2. दस्तावेज़: वह Word दस्तावेज़ तैयार रखें जिसे आप वॉटरमार्क करना चाहते हैं।
3. विकास परिवेश: विजुअल स्टूडियो या किसी अन्य .NET विकास उपकरण के साथ अपना विकास परिवेश स्थापित करें।

## नामस्थान आयात करें
कोड में गोता लगाने से पहले, आइए आवश्यक नामस्थान आयात करें:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
```
## चरण 1: दस्तावेज़ लोड करें
सबसे पहले, हमें Word दस्तावेज़ को वॉटरमार्कर ऑब्जेक्ट में लोड करना होगा।
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // वॉटरमार्किंग कोड जोड़ें यहां जाएगा
}
```
## चरण 2: वॉटरमार्क जोड़ें
अब, दस्तावेज़ के विशिष्ट पृष्ठों पर एक टेक्स्ट वॉटरमार्क जोड़ें।
```csharp
TextWatermark textWatermark = new TextWatermark("DRAFT", new Font("Arial", 42));
textWatermark.PagesSetup = new PagesSetup
{
    Pages = new List<int> { 2, 3 } // वॉटरमार्क जोड़ने के लिए पृष्ठ निर्दिष्ट करें
};
watermarker.Add(textWatermark);
```
## चरण 3: दस्तावेज़ सहेजें
अंत में, वॉटरमार्क वाले दस्तावेज़ को वांछित स्थान पर सहेजें।
```csharp
watermarker.Save(outputFileName);
```

## निष्कर्ष
इस ट्यूटोरियल में, हमने सीखा कि .NET के लिए Groupdocs.Watermark का उपयोग करके Word दस्तावेज़ों में विशिष्ट पृष्ठों पर वॉटरमार्क कैसे जोड़ें। कोड की केवल कुछ पंक्तियों के साथ, आप आसानी से अपने दस्तावेज़ों की सुरक्षा और ब्रांडिंग बढ़ा सकते हैं।
## अक्सर पूछे जाने वाले प्रश्न
### क्या मैं एक ही दस्तावेज़ में एकाधिक वॉटरमार्क जोड़ सकता हूँ?
हां, आप प्रत्येक वॉटरमार्क के लिए वॉटरमार्क जोड़ने की प्रक्रिया को दोहराकर कई वॉटरमार्क जोड़ सकते हैं।
### क्या Groupdocs.Watermark Word के अलावा अन्य दस्तावेज़ प्रारूपों का समर्थन करता है?
हां, ग्रुपडॉक्स पीडीएफ, एक्सेल, पावरपॉइंट और अन्य सहित दस्तावेज़ प्रारूपों की एक विस्तृत श्रृंखला का समर्थन करता है।
### क्या कोई परीक्षण संस्करण उपलब्ध है?
 हां, आप यहां से नि:शुल्क परीक्षण संस्करण डाउनलोड कर सकते हैं[यहाँ](https://releases.groupdocs.com/).
### क्या मैं वॉटरमार्क के स्वरूप को अनुकूलित कर सकता हूँ?
बिल्कुल, आप वॉटरमार्क के विभिन्न पहलुओं जैसे फ़ॉन्ट, आकार, रंग और अस्पष्टता को अनुकूलित कर सकते हैं।
### क्या तकनीकी सहायता उपलब्ध है?
 हां, आप ग्रुपडॉक्स फोरम पर तकनीकी सहायता और संसाधन पा सकते हैं[यहाँ](https://forum.groupdocs.com/c/watermark/19).