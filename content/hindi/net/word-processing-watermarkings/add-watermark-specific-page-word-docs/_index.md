---
title: वर्ड डॉक्स में विशिष्ट पेज पर वॉटरमार्क जोड़ें
linktitle: वर्ड डॉक्स में विशिष्ट पेज पर वॉटरमार्क जोड़ें
second_title: GroupDocs.Watermark .NET API
description: जानें कि .NET के लिए वॉटरमार्क का उपयोग करके Word दस्तावेज़ों में विशिष्ट पृष्ठों पर वॉटरमार्क कैसे जोड़ें। अपनी सामग्री को सहजता से सुरक्षित रखें।
weight: 14
url: /hi/net/word-processing-watermarkings/add-watermark-specific-page-word-docs/
type: docs
---
# वर्ड डॉक्स में विशिष्ट पेज पर वॉटरमार्क जोड़ें

## परिचय
वॉटरमार्किंग दस्तावेज़ दस्तावेज़ सुरक्षा और ब्रांडिंग का एक महत्वपूर्ण पहलू है। इस ट्यूटोरियल में, हम जानेंगे कि .NET के लिए GroupDocs.Watermark का उपयोग करके Word दस्तावेज़ों में किसी विशिष्ट पृष्ठ पर वॉटरमार्क कैसे जोड़ा जाए।
## आवश्यक शर्तें
शुरू करने से पहले, सुनिश्चित करें कि आपके पास निम्नलिखित आवश्यकताएँ हैं:
- सी# प्रोग्रामिंग का बुनियादी ज्ञान।
- विज़ुअल स्टूडियो आईडीई स्थापित किया गया।
- आपके प्रोजेक्ट में .NET के लिए GroupDocs.Watermark स्थापित है।

## नामस्थान आयात करना
कोड में गोता लगाने से पहले, सुनिश्चित करें कि आप आवश्यक नामस्थान आयात कर लें:
```csharp
using GroupDocs.Watermark.Contents.WordProcessing;
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## चरण 1: दस्तावेज़ लोड करें
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // आपका कोड यहां जाएगा
}
```
## चरण 2: वॉटरमार्क जोड़ें
```csharp
// वॉटरमार्क टेक्स्ट और शैली को परिभाषित करें
TextWatermark textWatermark = new TextWatermark("DRAFT", new Font("Arial", 42));
// अंतिम पृष्ठ पर वॉटरमार्क जोड़ें
WordProcessingContent content = watermarker.GetContent<WordProcessingContent>();
WordProcessingWatermarkPagesOptions options = new WordProcessingWatermarkPagesOptions();
options.PageNumbers = new int[] {content.PageCount};
watermarker.Add(textWatermark, options);
```
## चरण 3: दस्तावेज़ सहेजें
```csharp
// दस्तावेज़ को वॉटरमार्क के साथ सहेजें
watermarker.Save(outputFileName);
```

## निष्कर्ष
इस ट्यूटोरियल में, हमने सीखा कि .NET के लिए GroupDocs.Watermark का उपयोग करके Word दस्तावेज़ों में किसी विशिष्ट पृष्ठ पर वॉटरमार्क कैसे जोड़ा जाए। इन चरणों का पालन करके, आप अपने दस्तावेज़ों को प्रभावी ढंग से सुरक्षित कर सकते हैं और आवश्यकतानुसार ब्रांडिंग तत्व जोड़ सकते हैं।
## अक्सर पूछे जाने वाले प्रश्न
### क्या मैं वॉटरमार्क टेक्स्ट और शैली को अनुकूलित कर सकता हूँ?
हां, आप अपनी आवश्यकताओं के अनुसार टेक्स्ट, फ़ॉन्ट, आकार, रंग और वॉटरमार्क की स्थिति को अनुकूलित कर सकते हैं।
### क्या .NET के लिए GroupDocs.Watermark अन्य दस्तावेज़ प्रारूपों के साथ संगत है?
हाँ, GroupDocs.Watermark Word, Excel, PowerPoint, PDF और अन्य सहित विभिन्न दस्तावेज़ स्वरूपों का समर्थन करता है।
### क्या मैं एक ही दस्तावेज़ में एकाधिक वॉटरमार्क जोड़ सकता हूँ?
बिल्कुल, आप एक ही दस्तावेज़ में विभिन्न सामग्री और शैलियों के साथ एकाधिक वॉटरमार्क जोड़ सकते हैं।
### क्या .NET के लिए GroupDocs.Watermark का निःशुल्क परीक्षण उपलब्ध है?
 हाँ, आप नि:शुल्क परीक्षण के साथ GroupDocs.Watermark की सुविधाओं का पता लगा सकते हैं। आरंभ करने के लिए बस दिए गए लिंक पर जाएं[यहाँ](https://releases.groupdocs.com/).
### मुझे GroupDocs.Watermark के लिए तकनीकी सहायता कहां मिल सकती है?
 आप सहायक संसाधन पा सकते हैं और तकनीकी सहायता प्राप्त कर सकते हैं[यहाँ](https://forum.groupdocs.com/c/watermark/19)GroupDocs.Watermark फोरम। समुदाय में शामिल होने के लिए दिए गए लिंक पर जाएँ।