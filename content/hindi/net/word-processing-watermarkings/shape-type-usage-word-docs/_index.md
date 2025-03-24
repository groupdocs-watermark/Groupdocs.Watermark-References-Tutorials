---
title: वर्ड डॉक्स में आकार प्रकार का उपयोग
linktitle: वर्ड डॉक्स में आकार प्रकार का उपयोग
second_title: GroupDocs.Watermark .NET API
description: .NET के लिए GroupDocs.Watermark का उपयोग करके Word दस्तावेज़ों में आकृतियों में हेरफेर करना सीखें। यह ट्यूटोरियल कुशल दस्तावेज़ प्रसंस्करण के लिए मार्गदर्शन प्रदान करता है।
weight: 37
url: /hi/net/word-processing-watermarkings/shape-type-usage-word-docs/
---
## परिचय
इस ट्यूटोरियल में, हम यह पता लगाएंगे कि .NET के लिए GroupDocs.Watermark का उपयोग करके Word दस्तावेज़ों में आकार प्रकारों का उपयोग कैसे करें। Word दस्तावेज़ों में आकार अलग-अलग हो सकते हैं, और विभिन्न दस्तावेज़ प्रसंस्करण कार्यों के लिए यह समझना महत्वपूर्ण हो सकता है कि उनमें हेरफेर कैसे किया जाए।
## आवश्यक शर्तें
शुरू करने से पहले, सुनिश्चित करें कि आपके पास निम्नलिखित आवश्यक शर्तें हैं:
1.  .NET लाइब्रेरी के लिए GroupDocs.Watermark: .NET लाइब्रेरी के लिए GroupDocs.Watermark को डाउनलोड और इंस्टॉल करें।[लिंक को डाउनलोड करें](https://releases.groupdocs.com/Watermark/net/).
2. दस्तावेज़ पथ: प्रसंस्करण के लिए एक Word दस्तावेज़ तैयार रखें।
3. विकास वातावरण: .NET फ्रेमवर्क समर्थन के साथ एक उपयुक्त विकास वातावरण स्थापित करें।

## नामस्थान आयात करें
आरंभ करने के लिए, आपको अपने प्रोजेक्ट में आवश्यक नामस्थान आयात करने की आवश्यकता है। ये नामस्थान Word दस्तावेज़ों के साथ काम करने के लिए आवश्यक कक्षाओं और विधियों तक पहुंच प्रदान करेंगे।
```csharp
using GroupDocs.Watermark.Contents.WordProcessing;
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System;
using System.IO;
```
## चरण 1: दस्तावेज़ लोड करें
वर्ड दस्तावेज़ को वॉटरमार्कर ऑब्जेक्ट में लोड करके प्रारंभ करें। लोडिंग प्रक्रिया के दौरान दस्तावेज़ पथ और आवश्यक किसी भी अतिरिक्त विकल्प को निर्दिष्ट करना सुनिश्चित करें।
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // दस्तावेज़ प्रसंस्करण कोड यहां जाता है
}
```
## चरण 2: दस्तावेज़ सामग्री तक पहुँचें
 का उपयोग करके लोड किए गए Word दस्तावेज़ की सामग्री तक पहुंचें`GetContent<WordProcessingContent>()` तरीका। यह दस्तावेज़ में मौजूद अनुभागों, पैराग्राफों और आकृतियों तक पहुंच प्रदान करेगा।
```csharp
WordProcessingContent content = watermarker.GetContent<WordProcessingContent>();
```
## चरण 3: अनुभागों और आकृतियों के माध्यम से पुनरावृति करें
आवश्यकतानुसार निरीक्षण करने और उनमें हेरफेर करने के लिए दस्तावेज़ के भीतर प्रत्येक अनुभाग और आकार को दोहराएँ।
```csharp
foreach (WordProcessingSection section in content.Sections)
{
    foreach (WordProcessingShape shape in section.Shapes)
    {
        // आकृति हेरफेर कोड यहां जाता है
    }
}
```
## चरण 4: आकार प्रकार की जाँच करें
लूप के भीतर, का उपयोग करके विशिष्ट आकार प्रकारों की जांच करें`ShapeType` संपत्ति। यह उदाहरण विकर्ण कोनों, गोल आकृतियों की पहचान और प्रबंधन को दर्शाता है।
```csharp
if (shape.ShapeType == WordProcessingShapeType.DiagonalCornersRounded)
{
    // आकार-विशिष्ट हेरफेर कोड यहां जाता है
}
```
## चरण 5: आकृतियों में हेरफेर करें
टेक्स्ट जोड़ने, फ़ॉर्मेटिंग को संशोधित करने, या पहचानी गई आकृतियों में दृश्य परिवर्तन लागू करने जैसी क्रियाएं करें।
```csharp
shape.FormattedTextFragments.Add("I am Diagonal Corner Rounded", new Font("Calibri", 8, FontStyle.Bold), Color.Red, Color.Aqua);
```
## चरण 6: दस्तावेज़ सहेजें
एक बार सभी आवश्यक संशोधन हो जाने के बाद, दस्तावेज़ को निर्दिष्ट आउटपुट फ़ाइल में लागू परिवर्तनों के साथ सहेजें।
```csharp
watermarker.Save(outputFileName);
```

## निष्कर्ष
विभिन्न दस्तावेज़ प्रसंस्करण कार्यों के लिए Word दस्तावेज़ों में आकृतियों में हेरफेर करना आवश्यक हो सकता है। .NET के लिए GroupDocs.Watermark के साथ, आप अपनी आवश्यकताओं को कुशलतापूर्वक पूरा करने के लिए आकृतियों को आसानी से पहचान सकते हैं, संशोधित कर सकते हैं और हेरफेर कर सकते हैं।
## अक्सर पूछे जाने वाले प्रश्न
### क्या .NET के लिए GroupDocs.Watermark Word के अलावा अन्य दस्तावेज़ प्रारूपों को संभाल सकता है?
हाँ, .NET के लिए GroupDocs.Watermark PDF, Excel, PowerPoint और अन्य सहित दस्तावेज़ स्वरूपों की एक विस्तृत श्रृंखला का समर्थन करता है।
### क्या .NET के लिए GroupDocs.Watermark का निःशुल्क परीक्षण उपलब्ध है?
 हां, आप नि:शुल्क परीक्षण संस्करण तक पहुंच सकते हैं[पृष्ठ जारी करता है](https://releases.groupdocs.com/).
### क्या .NET के लिए GroupDocs.Watermark तकनीकी सहायता प्रदान करता है?
 हां, आप सहायता मांग सकते हैं और इसके माध्यम से समुदाय से जुड़ सकते हैं[सहयता मंच](https://forum.groupdocs.com/c/watermark/19).
### क्या मैं विशिष्ट दस्तावेज़ आवश्यकताओं के लिए वॉटरमार्किंग प्रक्रिया को अनुकूलित कर सकता हूँ?
बिल्कुल, .NET के लिए GroupDocs.Watermark आपकी आवश्यकताओं के अनुसार वॉटरमार्किंग प्रक्रिया को तैयार करने के लिए व्यापक अनुकूलन विकल्प प्रदान करता है।
### मैं .NET के लिए GroupDocs.Watermark के लिए अस्थायी लाइसेंस कैसे प्राप्त कर सकता हूँ?
 आप से अस्थायी लाइसेंस प्राप्त कर सकते हैं[अस्थायी लाइसेंस खरीद पृष्ठ](https://purchase.groupdocs.com/temporary-license/) परीक्षण और मूल्यांकन उद्देश्यों के लिए।