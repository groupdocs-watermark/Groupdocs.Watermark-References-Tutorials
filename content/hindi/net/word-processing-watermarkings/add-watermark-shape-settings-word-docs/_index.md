---
title: वर्ड डॉक्स में शेप सेटिंग्स के साथ वॉटरमार्क जोड़ें
linktitle: वर्ड डॉक्स में शेप सेटिंग्स के साथ वॉटरमार्क जोड़ें
second_title: GroupDocs.Watermark .NET API
description: जानें कि .NET के लिए वॉटरमार्क का उपयोग करके Word दस्तावेज़ों में आकार सेटिंग्स के साथ वॉटरमार्क कैसे जोड़ें। अपने दस्तावेज़ों को प्रभावी ढंग से सुरक्षित रखें.
weight: 20
url: /hi/net/word-processing-watermarkings/add-watermark-shape-settings-word-docs/
---
## परिचय
इस ट्यूटोरियल में, हम .NET के लिए GroupDocs.Watermark का उपयोग करके Word दस्तावेज़ों में आकार सेटिंग्स के साथ वॉटरमार्क जोड़ने की प्रक्रिया के बारे में जानेंगे।
## आवश्यक शर्तें
शुरू करने से पहले, सुनिश्चित करें कि आपके पास निम्नलिखित हैं:
1.  .NET के लिए GroupDocs.Watermark स्थापित। आप इसे यहां से डाउनलोड कर सकते हैं[यहाँ](https://releases.groupdocs.com/Watermark/net/).
2. सी# प्रोग्रामिंग का बुनियादी ज्ञान।
3. वर्ड दस्तावेज़ प्रसंस्करण की समझ।

## नामस्थान आयात करें
सबसे पहले, आपको आवश्यक कक्षाओं और विधियों तक पहुँचने के लिए आवश्यक नामस्थान आयात करने की आवश्यकता है।
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## चरण 1: दस्तावेज़ लोड करें
उस Word दस्तावेज़ को लोड करें जहाँ आप वॉटरमार्क जोड़ना चाहते हैं।
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // वॉटरमार्क जोड़ने का कोड यहां जाता है
}
```
## चरण 2: वॉटरमार्क जोड़ें
 त्वरित करें ए`TextWatermark` ऑब्जेक्ट बनाएं और उस टेक्स्ट को निर्दिष्ट करें जिसे आप वॉटरमार्क के रूप में उपयोग करना चाहते हैं।
```csharp
TextWatermark watermark = new TextWatermark("Test watermark", new Font("Arial", 19));
```
## चरण 3: वॉटरमार्क सेटिंग्स अनुकूलित करें
वॉटरमार्क के लिए विभिन्न सेटिंग्स सेट करें, जैसे संरेखण, रोटेशन कोण, रंग और अस्पष्टता।
```csharp
watermark.VerticalAlignment = VerticalAlignment.Center;
watermark.HorizontalAlignment = HorizontalAlignment.Center;
watermark.RotateAngle = 25.0;
watermark.ForegroundColor = Color.Red;
watermark.Opacity = 1.0;
```
## चरण 4: वॉटरमार्क अनुभाग विकल्पों को परिभाषित करें
वॉटरमार्क अनुभाग के लिए विकल्प परिभाषित करें, जैसे आकृति का नाम और वैकल्पिक पाठ।
```csharp
WordProcessingWatermarkSectionOptions options = new WordProcessingWatermarkSectionOptions();
options.Name = "Shape 1";
options.AlternativeText = "Test watermark";
```
## चरण 5: दस्तावेज़ में वॉटरमार्क जोड़ें
निर्दिष्ट विकल्पों के साथ दस्तावेज़ में वॉटरमार्क जोड़ें।
```csharp
watermarker.Add(watermark, options);
```
## चरण 6: दस्तावेज़ सहेजें
दस्तावेज़ को जोड़े गए वॉटरमार्क के साथ सहेजें।
```csharp
watermarker.Save(outputFileName);
```

## निष्कर्ष
.NET के लिए वॉटरमार्क का उपयोग करके Word दस्तावेज़ों में आकार सेटिंग्स के साथ वॉटरमार्क जोड़ना एक सीधी प्रक्रिया है। इस ट्यूटोरियल में बताए गए चरणों का पालन करके, आप अनुकूलित वॉटरमार्क के साथ अपने दस्तावेज़ों को प्रभावी ढंग से सुरक्षित कर सकते हैं।
## अक्सर पूछे जाने वाले प्रश्न
### क्या मैं एक ही दस्तावेज़ में एकाधिक वॉटरमार्क जोड़ सकता हूँ?
हां, आप एक ही दस्तावेज़ में विभिन्न सेटिंग्स के साथ एकाधिक वॉटरमार्क जोड़ सकते हैं।
### क्या GroupDocs.Watermark Word के अलावा अन्य दस्तावेज़ प्रारूपों का समर्थन करता है?
हाँ, GroupDocs.Watermark Excel, PowerPoint, PDF और अन्य सहित विभिन्न दस्तावेज़ स्वरूपों का समर्थन करता है।
### क्या मैं वॉटरमार्क के स्वरूप को और अधिक अनुकूलित कर सकता हूँ?
बिल्कुल, आप अपनी आवश्यकताओं के अनुरूप फ़ॉन्ट आकार, शैली, रंग और स्थिति जैसे विभिन्न मापदंडों को समायोजित कर सकते हैं।
### क्या .NET के लिए GroupDocs.Watermark का कोई परीक्षण संस्करण उपलब्ध है?
 हाँ, आप नि:शुल्क परीक्षण प्राप्त कर सकते हैं[यहाँ](https://releases.groupdocs.com/).
### मुझे GroupDocs.Watermark के लिए समर्थन कहां मिल सकता है?
 आप GroupDocs फ़ोरम पर सहायता पा सकते हैं और प्रश्न पूछ सकते हैं[यहाँ](https://forum.groupdocs.com/c/watermark/19).