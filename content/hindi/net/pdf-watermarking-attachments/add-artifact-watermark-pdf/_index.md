---
title: पीडीएफ में आर्टिफैक्ट वॉटरमार्क जोड़ें
linktitle: पीडीएफ में आर्टिफैक्ट वॉटरमार्क जोड़ें
second_title: GroupDocs.Watermark .NET API
description: .NET के लिए Groupdocs.Watermark का उपयोग करके आसानी से PDF फ़ाइलों में आर्टिफैक्ट वॉटरमार्क जोड़ने का तरीका जानें। अपने दस्तावेज़ों को आसानी से सुरक्षित रखें।
weight: 11
url: /hi/net/pdf-watermarking-attachments/add-artifact-watermark-pdf/
---

# पीडीएफ में आर्टिफैक्ट वॉटरमार्क जोड़ें

## परिचय
पीडीएफ फाइलों में वॉटरमार्क जोड़ना दस्तावेज़ प्रबंधन का एक महत्वपूर्ण पहलू है, खासकर जब बौद्धिक संपदा या ब्रांडिंग दस्तावेज़ों की सुरक्षा की बात आती है। .NET के लिए Groupdocs.Watermark पीडीएफ फाइलों में आसानी से वॉटरमार्क जोड़ने के लिए एक मजबूत समाधान प्रदान करता है। इस ट्यूटोरियल में, हम चरण दर चरण पीडीएफ फाइलों में एक आर्टिफैक्ट वॉटरमार्क जोड़ने की प्रक्रिया के बारे में जानेंगे।
## आवश्यक शर्तें
शुरू करने से पहले, सुनिश्चित करें कि आपके पास निम्नलिखित आवश्यकताएँ हैं:
1.  .NET के लिए Groupdocs.Watermark: .NET के लिए Groupdocs.Watermark को डाउनलोड और इंस्टॉल करें[यहाँ](https://releases.groupdocs.com/Watermark/net/).
2. विकास परिवेश: एक .NET विकास परिवेश स्थापित करें।
3. पीडीएफ दस्तावेज़: पीडीएफ दस्तावेज़ तैयार करें जिसमें आप वॉटरमार्क जोड़ना चाहते हैं।
4. आउटपुट निर्देशिका: वॉटरमार्क वाली पीडीएफ फाइल को सहेजने के लिए एक निर्देशिका बनाएं।

## नामस्थान आयात करना
आरंभ करने के लिए, अपने C# प्रोजेक्ट में आवश्यक नामस्थान आयात करें:
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## चरण 1: पीडीएफ दस्तावेज़ लोड करें
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
```
## चरण 2: वॉटरमार्क विकल्पों को परिभाषित करें
```csharp
PdfArtifactWatermarkOptions options = new PdfArtifactWatermarkOptions();
```
## चरण 3: टेक्स्ट वॉटरमार्क जोड़ें
```csharp
TextWatermark textWatermark = new TextWatermark("This is an artifact watermark", new Font("Arial", 8));
textWatermark.HorizontalAlignment = HorizontalAlignment.Right;
watermarker.Add(textWatermark, options);
```
## चरण 4: छवि वॉटरमार्क जोड़ें
```csharp
using (ImageWatermark imageWatermark = new ImageWatermark(Constants.LogoBmp))
{
    watermarker.Add(imageWatermark, options);
}
```
## चरण 5: वॉटरमार्क वाली पीडीएफ को सेव करें
```csharp
watermarker.Save(outputFileName);
```

## निष्कर्ष
इस ट्यूटोरियल में, हमने सीखा कि .NET के लिए Groupdocs.Watermark का उपयोग करके PDF फ़ाइलों में आर्टिफैक्ट वॉटरमार्क कैसे जोड़ें। इन चरणों का पालन करके, आप अपने दस्तावेज़ों की सुरक्षा और अखंडता सुनिश्चित करते हुए, अपने .NET अनुप्रयोगों में वॉटरमार्किंग कार्यक्षमता को निर्बाध रूप से एकीकृत कर सकते हैं।
## अक्सर पूछे जाने वाले प्रश्न
### क्या मैं टेक्स्ट वॉटरमार्क के स्वरूप को अनुकूलित कर सकता हूँ?
हां, आप अपनी पसंद के अनुसार फ़ॉन्ट, आकार, रंग और टेक्स्ट वॉटरमार्क के संरेखण जैसे विभिन्न पहलुओं को अनुकूलित कर सकते हैं।
### क्या Groupdocs.Watermark अन्य दस्तावेज़ प्रारूपों में वॉटरमार्क जोड़ने का समर्थन करता है?
हाँ, Groupdocs.Watermark Word, Excel, PowerPoint और अन्य दस्तावेज़ स्वरूपों की एक विस्तृत श्रृंखला में वॉटरमार्क जोड़ने का समर्थन करता है।
### क्या .NET के लिए Groupdocs.Watermark का कोई परीक्षण संस्करण उपलब्ध है?
 हां, आप यहां से नि:शुल्क परीक्षण संस्करण डाउनलोड कर सकते हैं[यहाँ](https://releases.groupdocs.com/).
### मैं Groupdocs.Watermark से संबंधित किसी भी मुद्दे या प्रश्न के लिए समर्थन कैसे प्राप्त कर सकता हूं?
 आप ग्रुपडॉक्स सामुदायिक मंच से सहायता प्राप्त कर सकते हैं[यहाँ](https://forum.groupdocs.com/c/watermark/19).
### क्या मैं व्यावसायिक उद्देश्यों के लिए Groupdocs.Watermark का उपयोग कर सकता हूँ?
हाँ, आप व्यावसायिक उपयोग के लिए लाइसेंस खरीद सकते हैं[यहाँ](https://purchase.groupdocs.com/buy).