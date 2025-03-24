---
title: टेक्स्ट वॉटरमार्क जोड़ें
linktitle: टेक्स्ट वॉटरमार्क जोड़ें
second_title: GroupDocs.Watermark .NET API
description: इस चरण-दर-चरण मार्गदर्शिका से जानें कि .NET के लिए Groupdocs का उपयोग करके अपने दस्तावेज़ों में टेक्स्ट वॉटरमार्क कैसे जोड़ें।
weight: 11
url: /hi/net/watermarking-basics/add-text-watermark/
---

# टेक्स्ट वॉटरमार्क जोड़ें

## परिचय
.NET के लिए GroupDocs.Watermark एक शक्तिशाली लाइब्रेरी है जो डेवलपर्स को .NET अनुप्रयोगों में विभिन्न दस्तावेज़ प्रारूपों से वॉटरमार्क जोड़ने, खोजने और हटाने की अनुमति देती है। इस ट्यूटोरियल में, हम GroupDocs.Watermark का उपयोग करके दस्तावेज़ में टेक्स्ट वॉटरमार्क जोड़ने पर ध्यान केंद्रित करेंगे।
## आवश्यक शर्तें
शुरू करने से पहले, सुनिश्चित करें कि आपके पास निम्नलिखित शर्तें हैं:
1. C# प्रोग्रामिंग भाषा का बुनियादी ज्ञान।
2. आपके सिस्टम पर विज़ुअल स्टूडियो स्थापित है।
3.  .NET लाइब्रेरी के लिए GroupDocs.Watermark स्थापित। आप इसे यहां से डाउनलोड कर सकते हैं[यहाँ](https://releases.groupdocs.com/Watermark/net/).

## नामस्थान आयात करें
सबसे पहले, आपको अपने C# प्रोजेक्ट में आवश्यक नेमस्पेस आयात करना होगा।
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Watermarks;
using System;
using System.IO;
```
## चरण 1: दस्तावेज़ पथ और आउटपुट निर्देशिका को परिभाषित करें
अपने इनपुट दस्तावेज़ और आउटपुट निर्देशिका का पथ परिभाषित करें जहां वॉटरमार्क दस्तावेज़ सहेजा जाएगा।
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
 प्रतिस्थापित करें`"Your Document Path"` उदाहरण के लिए, आपके इनपुट दस्तावेज़ के पूर्ण या सापेक्ष पथ के साथ:`@"C:\Docs\document.pdf"`. साथ ही, वह निर्देशिका निर्दिष्ट करें जहां आप वॉटरमार्क दस्तावेज़ को सहेजना चाहते हैं।
## चरण 2: टेक्स्ट वॉटरमार्क जोड़ें
 त्वरित करें`Watermarker` इनपुट दस्तावेज़ पथ के साथ वर्ग। फिर, एक बनाएं`TextWatermark` वांछित पाठ और फ़ॉन्ट सेटिंग्स के साथ ऑब्जेक्ट।
```csharp
using (Watermarker watermarker = new Watermarker(documentPath))
{
    TextWatermark watermark = new TextWatermark("top secret", new Font("Arial", 36));
    watermark.ForegroundColor = Color.Red;
    watermark.HorizontalAlignment = HorizontalAlignment.Center;
    watermark.VerticalAlignment = VerticalAlignment.Center;
    watermarker.Add(watermark);
    watermarker.Save(outputFileName);
}
```

## निष्कर्ष
इस ट्यूटोरियल में, हमने सीखा कि .NET के लिए GroupDocs.Watermark का उपयोग करके किसी दस्तावेज़ में टेक्स्ट वॉटरमार्क कैसे जोड़ा जाए। अपने सहज ज्ञान युक्त एपीआई के साथ, डेवलपर्स विभिन्न दस्तावेज़ प्रारूपों में वॉटरमार्क में आसानी से हेरफेर कर सकते हैं।
## अक्सर पूछे जाने वाले प्रश्न
### क्या .NET के लिए GroupDocs.Watermark सभी दस्तावेज़ प्रारूपों के साथ संगत है?
GroupDocs.Watermark पीडीएफ, माइक्रोसॉफ्ट वर्ड, एक्सेल, पॉवरपॉइंट और कई अन्य सहित दस्तावेज़ प्रारूपों की एक विस्तृत श्रृंखला का समर्थन करता है।
### क्या मैं टेक्स्ट वॉटरमार्क के स्वरूप को अनुकूलित कर सकता हूँ?
हां, आप टेक्स्ट वॉटरमार्क के फ़ॉन्ट, रंग, संरेखण और अस्पष्टता जैसे विभिन्न गुणों को अनुकूलित कर सकते हैं।
### क्या GroupDocs.Watermark दस्तावेज़ों से वॉटरमार्क हटाने के लिए सहायता प्रदान करता है?
हाँ, GroupDocs.Watermark दस्तावेज़ों से वॉटरमार्क खोजने और हटाने की कार्यक्षमता प्रदान करता है।
### क्या मैं खरीदने से पहले .NET के लिए GroupDocs.Watermark आज़मा सकता हूँ?
 हां, आप यहां से नि:शुल्क परीक्षण संस्करण डाउनलोड कर सकते हैं[यहाँ](https://releases.groupdocs.com/).
### मैं GroupDocs.Watermark के लिए तकनीकी सहायता कैसे प्राप्त कर सकता हूँ?
 पर जाकर तकनीकी सहायता प्राप्त कर सकते हैं[GroupDocs.वॉटरमार्क फ़ोरम](https://forum.groupdocs.com/c/watermark/19).