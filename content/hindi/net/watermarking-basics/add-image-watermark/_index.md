---
title: छवि वॉटरमार्क जोड़ें
linktitle: छवि वॉटरमार्क जोड़ें
second_title: GroupDocs.Watermark .NET API
description: .NET के लिए GroupDocs.Watermark का उपयोग करके अपने दस्तावेज़ों में आसानी से छवि वॉटरमार्क जोड़ें। अपनी बौद्धिक संपदा को आसानी से सुरक्षित रखें।
weight: 10
url: /hi/net/watermarking-basics/add-image-watermark/
type: docs
---
# छवि वॉटरमार्क जोड़ें

## परिचय
इस ट्यूटोरियल में, हम .NET के लिए GroupDocs.Watermark का उपयोग करके आपके दस्तावेज़ों में एक छवि वॉटरमार्क जोड़ने की प्रक्रिया के बारे में विस्तार से जानेंगे। बौद्धिक संपदा और ब्रांडिंग की सुरक्षा के लिए वॉटरमार्किंग दस्तावेज़ आवश्यक हैं। .NET के लिए GroupDocs.Watermark के साथ, आप वॉटरमार्क को Word, Excel, PowerPoint, PDF और कई अन्य दस्तावेज़ स्वरूपों में सहजता से एकीकृत कर सकते हैं।
## आवश्यक शर्तें
शुरू करने से पहले, सुनिश्चित करें कि आपके पास निम्नलिखित आवश्यक शर्तें हैं:
1.  .NET लाइब्रेरी के लिए GroupDocs.Watermark: .NET लाइब्रेरी के लिए GroupDocs.Watermark को डाउनलोड और इंस्टॉल करें।[वेबसाइट](https://releases.groupdocs.com/Watermark/net/).
2. दस्तावेज़: वह दस्तावेज़ तैयार रखें जिसमें आप वॉटरमार्क जोड़ना चाहते हैं।
3. वॉटरमार्क के लिए छवि: वह छवि फ़ाइल तैयार करें जिसे आप वॉटरमार्क के रूप में उपयोग करना चाहते हैं।

## नामस्थान आयात करें
```csharp
using System;
using System.IO;
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Options.Spreadsheet;
using GroupDocs.Watermark.Watermarks;
```
## चरण 1: दस्तावेज़ पथ और आउटपुट निर्देशिका प्रारंभ करें
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
 प्रतिस्थापित करें`"Your Document Path"`आपके दस्तावेज़ के पूर्ण या सापेक्ष पथ के साथ और`"Your Document Directory"` उस निर्देशिका के साथ जहां आप वॉटरमार्क दस्तावेज़ को सहेजना चाहते हैं।
## चरण 2: दस्तावेज़ स्ट्रीम खोलें और वॉटरमार्कर प्रारंभ करें
```csharp
using (FileStream stream = File.Open(documentPath, FileMode.Open, FileAccess.ReadWrite))
{
    using (Watermarker watermarker = new Watermarker(stream))
    {
        // यहां वॉटरमार्किंग की प्रक्रिया चलेगी
    }
}
```
 का उपयोग करके दस्तावेज़ स्ट्रीम खोलें`FileStream` और आरंभ करें`Watermarker` वस्तु।
## चरण 3: छवि वॉटरमार्क जोड़ें
```csharp
using (ImageWatermark watermark = new ImageWatermark(Constants.LogoPng))
{
    watermark.HorizontalAlignment = HorizontalAlignment.Center;
    watermark.VerticalAlignment = VerticalAlignment.Center;
    watermarker.Add(watermark);
}
```
 एक बनाएं`ImageWatermark` उस छवि फ़ाइल के पथ के साथ ऑब्जेक्ट करें जिसे आप वॉटरमार्क के रूप में उपयोग करना चाहते हैं। वॉटरमार्क का क्षैतिज और ऊर्ध्वाधर संरेखण सेट करें।
## चरण 4: वॉटरमार्क दस्तावेज़ सहेजें
```csharp
watermarker.Save(outputFileName);
```
वॉटरमार्क वाले दस्तावेज़ को वांछित फ़ाइल नाम के साथ निर्दिष्ट आउटपुट निर्देशिका में सहेजें।

## निष्कर्ष
अंत में, .NET के लिए GroupDocs.Watermark विभिन्न दस्तावेज़ प्रारूपों में आसानी से वॉटरमार्क जोड़ने के लिए एक व्यापक समाधान प्रदान करता है। इस ट्यूटोरियल में बताए गए चरणों का पालन करके, आप कुशलतापूर्वक अपने दस्तावेज़ों में छवि वॉटरमार्क जोड़ सकते हैं और अपनी बौद्धिक संपदा की रक्षा कर सकते हैं।
## अक्सर पूछे जाने वाले प्रश्न
### क्या मैं .NET के लिए GroupDocs.Watermark का उपयोग करके टेक्स्ट वॉटरमार्क जोड़ सकता हूँ?
हाँ, .NET के लिए GroupDocs.Watermark दस्तावेज़ों में छवि और टेक्स्ट वॉटरमार्क दोनों जोड़ने का समर्थन करता है।
### क्या .NET के लिए GroupDocs.Watermark विभिन्न दस्तावेज़ प्रारूपों के साथ संगत है?
बिल्कुल, .NET के लिए GroupDocs.Watermark Word, Excel, PowerPoint, PDF और अन्य सहित दस्तावेज़ स्वरूपों की एक विस्तृत श्रृंखला का समर्थन करता है।
### क्या .NET के लिए GroupDocs.Watermark वॉटरमार्क के लिए अनुकूलन विकल्प प्रदान करता है?
हां, आप वॉटरमार्क के विभिन्न पहलुओं जैसे स्थिति, आकार, अस्पष्टता और रोटेशन को अनुकूलित कर सकते हैं।
### क्या मैं .NET के लिए GroupDocs.Watermark का उपयोग करके दस्तावेज़ों से वॉटरमार्क हटा सकता हूँ?
हाँ, .NET के लिए GroupDocs.Watermark दस्तावेजों से वॉटरमार्क का पता लगाने और हटाने की कार्यक्षमता प्रदान करता है।
### क्या .NET के लिए GroupDocs.Watermark का कोई परीक्षण संस्करण उपलब्ध है?
 हाँ, आप खरीदने से पहले सुविधाओं का पता लगाने के लिए वेबसाइट से निःशुल्क परीक्षण संस्करण का लाभ उठा सकते हैं[यहाँ](https://releases.groupdocs.com/).