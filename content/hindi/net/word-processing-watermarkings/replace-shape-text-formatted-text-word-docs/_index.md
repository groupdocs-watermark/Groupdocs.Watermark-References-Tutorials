---
title: वर्ड डॉक्स में शेप टेक्स्ट को फ़ॉर्मेटेड टेक्स्ट से बदलें
linktitle: वर्ड डॉक्स में शेप टेक्स्ट को फ़ॉर्मेटेड टेक्स्ट से बदलें
second_title: GroupDocs.Watermark .NET API
description: .NET के लिए GroupDocs.Watermark का उपयोग करके Word दस्तावेज़ों में आकार टेक्स्ट को स्वरूपित टेक्स्ट से बदलने का तरीका जानें। आपकी दस्तावेज़ संपादन क्षमताएँ सहजता से।
type: docs
weight: 34
url: /hi/net/word-processing-watermarkings/replace-shape-text-formatted-text-word-docs/
---
## परिचय
इस ट्यूटोरियल में, हम .NET के लिए GroupDocs.Watermark का उपयोग करके Word दस्तावेज़ों में आकार टेक्स्ट को स्वरूपित टेक्स्ट से बदलने की प्रक्रिया में आपका मार्गदर्शन करेंगे। यह लाइब्रेरी वॉटरमार्क के साथ काम करने के लिए शक्तिशाली सुविधाएँ प्रदान करती है, जिसमें आकृतियों के भीतर पाठ को बदलना भी शामिल है।
## आवश्यक शर्तें
शुरू करने से पहले, सुनिश्चित करें कि आपके पास निम्नलिखित आवश्यकताएँ हैं:
1.  .NET के लिए GroupDocs.Watermark: सुनिश्चित करें कि आपने .NET के लिए GroupDocs.Watermark इंस्टॉल और सेटअप कर लिया है। आप इसे यहां से डाउनलोड कर सकते हैं[यहाँ](https://releases.groupdocs.com/Watermark/net/).
2. दस्तावेज़ पथ: आपके पास Word दस्तावेज़ का पथ होना चाहिए जहाँ आप टेक्स्ट को बदलना चाहते हैं।

## नामस्थान आयात करें
कोड लिखने से पहले, आवश्यक नामस्थान आयात करें:
```csharp
using GroupDocs.Watermark.Contents.WordProcessing;
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## चरण 1: दस्तावेज़ लोड करें
 का उपयोग करके Word दस्तावेज़ लोड करें`Watermarker` कक्षा:
```csharp
string documentPath = "Your Document Path";
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // आपका कोड यहां जारी है...
}
```
## चरण 2: सामग्री प्राप्त करें और टेक्स्ट बदलें
एक बार दस्तावेज़ लोड हो जाने पर, सामग्री प्राप्त करें और टेक्स्ट को आकृतियों में बदलें:
```csharp
WordProcessingContent content = watermarker.GetContent<WordProcessingContent>();
foreach (WordProcessingShape shape in content.Sections[0].Shapes)
{
    if (shape.Text.Contains("Some text"))
    {
        shape.FormattedTextFragments.Clear();
        shape.FormattedTextFragments.Add("Another text", new Font("Calibri", 19, FontStyle.Bold), Color.Red, Color.Aqua);
    }
}
```
## चरण 3: दस्तावेज़ सहेजें
टेक्स्ट को बदलने के बाद, संशोधित दस्तावेज़ को सहेजें:
```csharp
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
watermarker.Save(outputFileName);
```

## निष्कर्ष
.NET के लिए वॉटरमार्क के साथ Word दस्तावेज़ों में आकार टेक्स्ट को स्वरूपित टेक्स्ट से बदलना आसान हो गया है। इस ट्यूटोरियल में बताए गए चरणों का पालन करके, आप अपने दस्तावेज़ों में टेक्स्ट को कुशलतापूर्वक प्रबंधित और हेरफेर कर सकते हैं।

## अक्सर पूछे जाने वाले प्रश्न
### क्या मैं .NET के लिए GroupDocs.Watermark का उपयोग करके अन्य प्रकार के दस्तावेज़ों में टेक्स्ट को बदल सकता हूँ?
हां, ग्रुपडॉक्स विभिन्न दस्तावेज़ प्रारूपों जैसे पीडीएफ, एक्सेल, पावरपॉइंट और अन्य का समर्थन करता है।
### क्या GroupDocs.Watermark .NET कोर के साथ संगत है?
हाँ, GroupDocs.Watermark .NET Framework और .NET Core दोनों का समर्थन करता है।
### क्या GroupDocs.Watermark छवियों को वॉटरमार्क के रूप में जोड़ने के लिए सहायता प्रदान करता है?
बिल्कुल, GroupDocs.Watermark आपको अपने दस्तावेज़ों में टेक्स्ट और छवि वॉटरमार्क दोनों जोड़ने की अनुमति देता है।
### क्या मैं GroupDocs.Watermark का उपयोग करके जोड़े गए वॉटरमार्क के स्वरूप को अनुकूलित कर सकता हूँ?
हां, वॉटरमार्क की उपस्थिति, स्थिति और अन्य गुणों पर आपका पूर्ण नियंत्रण है।
### क्या .NET के लिए GroupDocs.Watermark का कोई परीक्षण संस्करण उपलब्ध है?
 हाँ, आप नि:शुल्क परीक्षण डाउनलोड कर सकते हैं[यहाँ](https://releases.groupdocs.com/).