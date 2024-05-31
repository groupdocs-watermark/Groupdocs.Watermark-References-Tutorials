---
title: वर्ड डॉक्स में विशिष्ट आकार के लिए टेक्स्ट बदलें
linktitle: वर्ड डॉक्स में विशिष्ट आकार के लिए टेक्स्ट बदलें
second_title: GroupDocs.Watermark .NET API
description: .NET के लिए GroupDocs.Watermark का उपयोग करके Word दस्तावेज़ों में विशिष्ट आकृतियों के लिए टेक्स्ट को बदलने का तरीका जानें। हमारे चरण-दर-चरण ट्यूटोरियल का अनुसरण करें।
type: docs
weight: 35
url: /hi/net/word-processing-watermarkings/replace-text-specific-shape-word-docs/
---
## परिचय
इस ट्यूटोरियल में, हम यह पता लगाएंगे कि Word दस्तावेज़ों में किसी विशिष्ट आकार के लिए टेक्स्ट को बदलने के लिए .NET के लिए GroupDocs.Watermark का उपयोग कैसे करें। .NET के लिए GroupDocs.Watermark एक शक्तिशाली लाइब्रेरी है जो Word दस्तावेज़ों सहित विभिन्न दस्तावेज़ स्वरूपों में वॉटरमार्क के साथ काम करने के लिए सुविधाओं की एक विस्तृत श्रृंखला प्रदान करती है।
## आवश्यक शर्तें
शुरू करने से पहले, सुनिश्चित करें कि आपके पास निम्नलिखित आवश्यक शर्तें हैं:
1.  .NET के लिए GroupDocs.Watermark: सुनिश्चित करें कि आपने .NET के लिए GroupDocs.Watermark डाउनलोड और इंस्टॉल कर लिया है। आप इसे यहां से डाउनलोड कर सकते हैं[यहाँ](https://releases.groupdocs.com/Watermark/net/).
2. दस्तावेज़: वर्ड दस्तावेज़ तैयार करें जिसमें आप टेक्स्ट को एक विशिष्ट आकार के लिए बदलना चाहते हैं।
3. विकास परिवेश: आवश्यक उपकरणों और निर्भरताओं के साथ अपना विकास परिवेश स्थापित करें।

## नामस्थान आयात करें
सबसे पहले, आइए .NET के लिए GroupDocs.Watermark के साथ काम करने के लिए आवश्यक नामस्थान आयात करें:
```csharp
using GroupDocs.Watermark.Contents.WordProcessing;
using GroupDocs.Watermark.Options.WordProcessing;
using System.IO;
using System;
```
## चरण 1: दस्तावेज़ लोड करें
```csharp
string documentPath = "Your Document Path";
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // आपका कोड यहां जाता है
}
```
 इस चरण में, हम Word दस्तावेज़ के लिए पथ निर्दिष्ट करते हैं और उसका एक उदाहरण बनाते हैं`WordProcessingLoadOptions` दस्तावेज़ लोड करने के लिए.
## चरण 2: दस्तावेज़ सामग्री प्राप्त करें
```csharp
WordProcessingContent content = watermarker.GetContent<WordProcessingContent>();
```
 यहां, हम इसका उपयोग करके वर्ड दस्तावेज़ की सामग्री को पुनः प्राप्त करते हैं`GetContent<T>()` की विधि`Watermarker`वर्ग, प्रकार को इस प्रकार निर्दिष्ट करता है`WordProcessingContent`.
## चरण 3: विशिष्ट आकार के लिए टेक्स्ट बदलें
```csharp
foreach (WordProcessingShape shape in content.Sections[0].Shapes)
{
    if (shape.Text.Contains("Some text"))
    {
        shape.Text = "Another text";
    }
}
```
इस चरण में, हम दस्तावेज़ में प्रत्येक आकृति को दोहराते हैं। यदि आकृति में निर्दिष्ट पाठ (इस उदाहरण में "कुछ पाठ") शामिल है, तो हम इसे वांछित पाठ ("अन्य पाठ") से बदल देते हैं।
## चरण 4: दस्तावेज़ सहेजें
```csharp
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
watermarker.Save(outputFileName);
```
अंत में, हम संशोधित दस्तावेज़ को निर्दिष्ट निर्देशिका में सहेजते हैं।

## निष्कर्ष
.NET के लिए GroupDocs.Watermark Word दस्तावेज़ों में वॉटरमार्क में हेरफेर करने का एक सुविधाजनक और कुशल तरीका प्रदान करता है। इस ट्यूटोरियल में बताए गए चरणों का पालन करके, आप अपने दस्तावेज़ प्रसंस्करण आवश्यकताओं के लिए लचीलापन और अनुकूलन विकल्प प्रदान करते हुए, विशिष्ट आकृतियों के लिए टेक्स्ट को आसानी से बदल सकते हैं।
## अक्सर पूछे जाने वाले प्रश्न
### क्या मैं वर्ड के अलावा अन्य दस्तावेज़ प्रारूपों में आकृतियों के लिए टेक्स्ट को बदल सकता हूँ?
.NET के लिए GroupDocs.Watermark पीडीएफ, एक्सेल, पॉवरपॉइंट और अन्य सहित विभिन्न दस्तावेज़ प्रारूपों का समर्थन करता है। आप समान विधियों का उपयोग करके विभिन्न प्रारूपों में आकृतियों के लिए पाठ को प्रतिस्थापित कर सकते हैं।
### क्या .NET के लिए GroupDocs.Watermark का कोई परीक्षण संस्करण उपलब्ध है?
 हां, आप यहां से नि:शुल्क परीक्षण संस्करण डाउनलोड कर सकते हैं[यहाँ](https://releases.groupdocs.com/).
### मैं .NET के लिए GroupDocs.Watermark के लिए तकनीकी सहायता कैसे प्राप्त कर सकता हूँ?
आप GroupDocs फोरम पर जाकर तकनीकी सहायता प्राप्त कर सकते हैं[यहाँ](https://forum.groupdocs.com/c/watermark/19).
### क्या मुझे .NET के लिए GroupDocs.Watermark का उपयोग करने के लिए अस्थायी लाइसेंस की आवश्यकता है?
 यदि आपको अतिरिक्त सुविधाओं या विस्तारित उपयोग की आवश्यकता है, तो आप अस्थायी लाइसेंस प्राप्त कर सकते हैं[यहाँ](https://purchase.groupdocs.com/temporary-license/).
### मैं .NET के लिए GroupDocs.Watermark का पूर्ण लाइसेंस कहां से खरीद सकता हूं?
 आप GroupDocs वेबसाइट से पूर्ण लाइसेंस खरीद सकते हैं[यहाँ](https://purchase.groupdocs.com/buy).