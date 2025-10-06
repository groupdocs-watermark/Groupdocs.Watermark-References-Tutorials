---
title: वर्ड डॉक्स में सेक्शन इमेज में वॉटरमार्क जोड़ें
linktitle: वर्ड डॉक्स में सेक्शन इमेज में वॉटरमार्क जोड़ें
second_title: GroupDocs.Watermark .NET API
description: जानें कि .NET के लिए वॉटरमार्क का उपयोग करके Word दस्तावेज़ों में छवियों में वॉटरमार्क कैसे जोड़ें। सुरक्षित और पेशेवर दस्तावेज़ सुरक्षा के लिए हमारी मार्गदर्शिका का पालन करें।
weight: 16
url: /hi/net/word-processing-watermarkings/add-watermark-section-images-word-docs/
type: docs
---
# वर्ड डॉक्स में सेक्शन इमेज में वॉटरमार्क जोड़ें

## परिचय
आज की डिजिटल दुनिया में, अपने दस्तावेज़ों की सुरक्षा करना आवश्यक है। अपने Word दस्तावेज़ों में वॉटरमार्क जोड़ना आपकी सामग्री को सुरक्षित करने का एक सरल लेकिन प्रभावी तरीका है। यह ट्यूटोरियल आपको .NET के लिए Groupdocs.Watermark का उपयोग करके Word दस्तावेज़ों में अनुभाग छवियों में वॉटरमार्क जोड़ने की प्रक्रिया में मार्गदर्शन करेगा। चाहे आप एक डेवलपर हों और इस सुविधा को अपने एप्लिकेशन में एकीकृत करना चाहते हों या बस अपने दस्तावेज़ों की सुरक्षा करना चाहते हों, यह मार्गदर्शिका आपके लिए है।
## आवश्यक शर्तें
इससे पहले कि हम विवरण में उतरें, सुनिश्चित करें कि आपके पास निम्नलिखित हैं:
1.  .NET के लिए Groupdocs.Watermark: इसे डाउनलोड करें[यहाँ](https://releases.groupdocs.com/Watermark/net/).
2. .NET फ्रेमवर्क: सुनिश्चित करें कि आपकी मशीन पर .NET फ्रेमवर्क स्थापित है।
3. एक वर्ड दस्तावेज़: एक वर्ड दस्तावेज़ तैयार रखें जिसमें आप वॉटरमार्क जोड़ना चाहते हैं।
4. विकास परिवेश: विज़ुअल स्टूडियो या कोई अन्य .NET संगत IDE।
5.  अस्थायी लाइसेंस: प्राप्त करें[अस्थायी लाइसेंस](https://purchase.groupdocs.com/temporary-license/) Groupdocs.वॉटरमार्क के लिए।
## नामस्थान आयात करें
आरंभ करने के लिए, अपने प्रोजेक्ट में आवश्यक नामस्थान आयात करें। यह सुनिश्चित करने के लिए एक महत्वपूर्ण कदम है कि Groupdocs.Watermark की सभी कार्यक्षमताएँ उपलब्ध हैं।
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.Image;
using GroupDocs.Watermark.Contents.WordProcessing;
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
अब, आइए इस प्रक्रिया को प्रबंधनीय चरणों में विभाजित करें।
## चरण 1: अपना प्रोजेक्ट स्थापित करना
सबसे पहले, अपने प्रोजेक्ट को अपनी पसंदीदा IDE में सेट करें। एक नया .NET प्रोजेक्ट बनाएं और Groupdocs.Watermark लाइब्रेरी स्थापित करें।
```bash
dotnet add package GroupDocs.Watermark
```
## चरण 2: वर्ड दस्तावेज़ लोड करें
वह Word दस्तावेज़ लोड करें जिसे आप वॉटरमार्क करना चाहते हैं। सुनिश्चित करें कि आपके दस्तावेज़ का पथ सही है।
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // आपका कोड यहां जाएगा
}
```
## चरण 3: वॉटरमार्क बनाएं
एक टेक्स्ट वॉटरमार्क बनाएं जिसे आप Word दस्तावेज़ में छवियों पर लागू करेंगे। अपनी आवश्यकताओं के अनुरूप टेक्स्ट, फ़ॉन्ट, आकार और संरेखण को अनुकूलित करें।
```csharp
TextWatermark watermark = new TextWatermark("Protected image", new Font("Arial", 8));
watermark.HorizontalAlignment = HorizontalAlignment.Center;
watermark.VerticalAlignment = VerticalAlignment.Center;
watermark.RotateAngle = 45;
watermark.SizingType = SizingType.ScaleToParentDimensions;
watermark.ScaleFactor = 1;
```
## चरण 4: पहले खंड से छवियाँ पुनर्प्राप्त करें
Word दस्तावेज़ की सामग्री तक पहुंचें और पहले अनुभाग में सभी छवियां ढूंढें। यह चरण महत्वपूर्ण है क्योंकि यह उन छवियों की पहचान करता है जिन पर वॉटरमार्क लागू किया जाएगा।
```csharp
WordProcessingContent content = watermarker.GetContent<WordProcessingContent>();
WatermarkableImageCollection images = content.Sections[0].FindImages();
```
## चरण 5: छवियों पर वॉटरमार्क लागू करें
पहले अनुभाग में प्रत्येक छवि के माध्यम से लूप करें और बनाए गए वॉटरमार्क को लागू करें। यह सुनिश्चित करता है कि अनुभाग की सभी छवियाँ सुरक्षित हैं।
```csharp
foreach (WatermarkableImage image in images)
{
    image.Add(watermark);
}
```
## चरण 6: दस्तावेज़ सहेजें
अंत में, वॉटरमार्क वाले दस्तावेज़ को निर्दिष्ट पथ पर सहेजें। यह किसी Word दस्तावेज़ में अनुभाग छवियों में वॉटरमार्क जोड़ने की प्रक्रिया पूरी करता है।
```csharp
watermarker.Save(outputFileName);
```
## निष्कर्ष
अपने Word दस्तावेज़ों में छवियों में वॉटरमार्क जोड़ना आपकी सामग्री को सुरक्षित रखने का एक शक्तिशाली तरीका है। .NET के लिए Groupdocs.Watermark के साथ, यह प्रक्रिया सीधी और कुशल है। यह सुनिश्चित करने के लिए कि आपके दस्तावेज़ सुरक्षित और अच्छी तरह से संरक्षित हैं, इस ट्यूटोरियल में बताए गए चरणों का पालन करें।
 अधिक विस्तृत दस्तावेज़ीकरण के लिए, पर जाएँ[प्रलेखन](https://tutorials.groupdocs.com/Watermark/net/) . यदि आपके कोई प्रश्न हैं या अतिरिक्त सहायता की आवश्यकता है, तो देखें[सहयता मंच](https://forum.groupdocs.com/c/watermark/19).
## अक्सर पूछे जाने वाले प्रश्न
### क्या मैं वॉटरमार्क टेक्स्ट को कस्टमाइज़ कर सकता हूँ?
हां, आप अपनी आवश्यकताओं के अनुरूप वॉटरमार्क टेक्स्ट, फ़ॉन्ट, आकार, संरेखण और रोटेशन को अनुकूलित कर सकते हैं।
### क्या एकाधिक अनुभागों में वॉटरमार्क जोड़ना संभव है?
हाँ, आप प्रत्येक अनुभाग में लूप कर सकते हैं और सभी अनुभागों में छवियों पर वॉटरमार्क लागू कर सकते हैं।
### क्या मैं इस पद्धति का उपयोग अन्य दस्तावेज़ प्रारूपों के लिए कर सकता हूँ?
 ग्रुपडॉक्स। वॉटरमार्क विभिन्न दस्तावेज़ प्रारूपों का समर्थन करता है। जाँचें[प्रलेखन](https://tutorials.groupdocs.com/Watermark/net/) अधिक जानकारी के लिए।
### मैं अस्थायी लाइसेंस कैसे प्राप्त कर सकता हूँ?
 आप अस्थायी लाइसेंस प्राप्त कर सकते हैं[यहाँ](https://purchase.groupdocs.com/temporary-license/).
### यदि Groupdocs.Watermark का उपयोग करते समय मुझे समस्याएं आती हैं तो क्या होगा?
 दौरा करना[सहयता मंच](https://forum.groupdocs.com/c/watermark/19)आपके सामने आने वाली किसी भी समस्या में सहायता के लिए।