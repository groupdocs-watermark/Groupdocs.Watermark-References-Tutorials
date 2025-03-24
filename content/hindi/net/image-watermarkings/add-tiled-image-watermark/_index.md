---
title: टाइलयुक्त छवि वॉटरमार्क जोड़ें
linktitle: टाइलयुक्त छवि वॉटरमार्क जोड़ें
second_title: GroupDocs.Watermark .NET API
description: जानें कि .NET के लिए GroupDocs.Watermark का उपयोग करके अपने दस्तावेज़ों में टाइलयुक्त छवि वॉटरमार्क कैसे जोड़ें। आसान, कुशल और अनुकूलन योग्य।
weight: 10
url: /hi/net/image-watermarkings/add-tiled-image-watermark/
---
## परिचय
.NET के लिए GroupDocs.Watermark एक शक्तिशाली एपीआई है जो डेवलपर्स को प्रोग्रामेटिक रूप से विभिन्न दस्तावेज़ प्रारूपों में वॉटरमार्क जोड़ने, हटाने और खोजने की अनुमति देता है। इस ट्यूटोरियल में, हम .NET के लिए GroupDocs.Watermark का उपयोग करके आपके दस्तावेज़ों में एक टाइल वाली छवि वॉटरमार्क जोड़ने की प्रक्रिया में आपका मार्गदर्शन करेंगे।
## आवश्यक शर्तें
शुरू करने से पहले, सुनिश्चित करें कि आपके पास निम्नलिखित हैं:
- C# प्रोग्रामिंग भाषा का बुनियादी ज्ञान।
- आपके सिस्टम पर विज़ुअल स्टूडियो स्थापित है।
- .NET लाइब्रेरी के लिए GroupDocs.Watermark आपके प्रोजेक्ट में जोड़ा गया। आप इसे यहां से डाउनलोड कर सकते हैं[यहाँ](https://releases.groupdocs.com/Watermark/net/).

## नामस्थान आयात करें
अपनी C# फ़ाइल की शुरुआत में आवश्यक नामस्थान आयात करना सुनिश्चित करें:
```csharp
using GroupDocs.Watermark.Watermarks;
using System;
using System.IO;
```
## चरण 1: दस्तावेज़ पथ और आउटपुट निर्देशिका सेट करें
अपने इनपुट दस्तावेज़ का पथ और उस निर्देशिका को परिभाषित करें जहाँ आप आउटपुट दस्तावेज़ को सहेजना चाहते हैं:
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
 प्रतिस्थापित करें`"Your Document Path"` आपके इनपुट दस्तावेज़ के पूर्ण या सापेक्ष पथ के साथ।
## चरण 2: वॉटरमार्कर ऑब्जेक्ट को आरंभ करें
इनपुट दस्तावेज़ पथ का उपयोग करके वॉटरमार्कर ऑब्जेक्ट बनाएं:
```csharp
using (Watermarker watermarker = new Watermarker(documentPath))
{
    // यहां वॉटरमार्क जोड़ें
}
```
## चरण 3: टाइल वाली छवि वॉटरमार्क जोड़ें
जिस छवि फ़ाइल को आप वॉटरमार्क के रूप में उपयोग करना चाहते हैं, उसके पथ के साथ एक ImageWatermark ऑब्जेक्ट को इंस्टेंट करें:
```csharp
using (ImageWatermark watermark = new ImageWatermark("Path to Your Image"))
{
    // टाइल विकल्प कॉन्फ़िगर करें
    watermark.TileOptions = new TileOptions()
    {
        TileType = TileType.Offset,
        LineSpacing = new MeasureValue()
        {
            MeasureType = TileMeasureType.Percent,
            Value = 12
        },
        WatermarkSpacing = new MeasureValue()
        {
            MeasureType = TileMeasureType.Percent,
            Value = 10
        },
    };
    watermark.RotateAngle = -30;
    // दस्तावेज़ में वॉटरमार्क जोड़ें
    watermarker.Add(watermark);
    // संशोधित दस्तावेज़ सहेजें
    watermarker.Save(outputFileName);
}
```
 प्रतिस्थापित करें`"Path to Your Image"` आपकी वॉटरमार्क छवि फ़ाइल के वास्तविक पथ के साथ।

## निष्कर्ष
इन चरणों का पालन करके, आप .NET के लिए GroupDocs.Watermark का उपयोग करके आसानी से अपने दस्तावेज़ों में एक टाइलयुक्त छवि वॉटरमार्क जोड़ सकते हैं। वांछित परिणाम प्राप्त करने के लिए विभिन्न विकल्पों और कॉन्फ़िगरेशन के साथ प्रयोग करें।
## अक्सर पूछे जाने वाले प्रश्न
### क्या मैं एक ही दस्तावेज़ में एकाधिक वॉटरमार्क जोड़ सकता हूँ?
हाँ, आप .NET के लिए GroupDocs.Watermark का उपयोग करके किसी दस्तावेज़ में विभिन्न प्रकार के एकाधिक वॉटरमार्क जोड़ सकते हैं।
### क्या GroupDocs.Watermark सभी दस्तावेज़ प्रारूपों का समर्थन करता है?
GroupDocs.Watermark पीडीएफ, वर्ड, एक्सेल, पॉवरपॉइंट और कई अन्य सहित दस्तावेज़ प्रारूपों की एक विस्तृत श्रृंखला का समर्थन करता है।
### क्या GroupDocs.Watermark के लिए कोई परीक्षण संस्करण उपलब्ध है?
 हां, आप यहां से नि:शुल्क परीक्षण संस्करण डाउनलोड कर सकते हैं[यहाँ](https://releases.groupdocs.com/).
### क्या मैं वॉटरमार्क के स्वरूप को अनुकूलित कर सकता हूँ?
हां, आप वॉटरमार्क के विभिन्न पहलुओं को अनुकूलित कर सकते हैं, जैसे स्थिति, आकार, रोटेशन, पारदर्शिता, आदि।
### क्या GroupDocs.Watermark तकनीकी सहायता प्रदान करता है?
 हां, आप GroupDocs.Watermark फोरम से तकनीकी सहायता प्राप्त कर सकते हैं[यहाँ](https://forum.groupdocs.com/c/watermark/19).