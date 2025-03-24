---
title: पीडीएफ में केवल प्रिंट एनोटेशन वॉटरमार्क जोड़ें
linktitle: पीडीएफ में केवल प्रिंट एनोटेशन वॉटरमार्क जोड़ें
second_title: GroupDocs.Watermark .NET API
description: .NET के लिए GroupDocs.Watermark का उपयोग करके PDF में केवल-प्रिंट एनोटेशन वॉटरमार्क जोड़ने का तरीका जानें। दस्तावेज़ सुरक्षा और ब्रांडिंग को सहजता से बढ़ाएँ।
weight: 13
url: /hi/net/pdf-watermarking-attachments/add-print-only-annotation-watermark-pdf/
---

# पीडीएफ में केवल प्रिंट एनोटेशन वॉटरमार्क जोड़ें

## परिचय
इस ट्यूटोरियल में, हम .NET के लिए GroupDocs.Watermark का उपयोग करके एक पीडीएफ में केवल-प्रिंट एनोटेशन वॉटरमार्क जोड़ने की प्रक्रिया के बारे में विस्तार से जानेंगे। वॉटरमार्किंग दस्तावेज़ दस्तावेज़ सुरक्षा और ब्रांडिंग का एक महत्वपूर्ण पहलू है, और GroupDocs.Watermark इसे प्राप्त करने के लिए .NET डेवलपर्स के लिए एक सहज समाधान प्रदान करता है।
## आवश्यक शर्तें
आरंभ करने से पहले, सुनिश्चित करें कि आपके पास निम्नलिखित आवश्यकताएँ हैं:
- C# प्रोग्रामिंग भाषा की बुनियादी समझ।
- आपकी मशीन पर विज़ुअल स्टूडियो स्थापित है।
- आपके प्रोजेक्ट में .NET लाइब्रेरी के लिए GroupDocs.Watermark स्थापित है।

## नामस्थान आयात करें
आरंभ करने के लिए, सुनिश्चित करें कि आप आवश्यक नामस्थान आयात करें:
```csharp
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## चरण 1: दस्तावेज़ लोड करें
 सबसे पहले, आपको वह पीडीएफ दस्तावेज़ लोड करना होगा जिसे आप वॉटरमार्क करना चाहते हैं। प्रतिस्थापित करें`"Your Document Path"` आपकी पीडीएफ फ़ाइल के पथ के साथ और`"Your Document Directory"` उस निर्देशिका के साथ जहां आप आउटपुट फ़ाइल को सहेजना चाहते हैं।
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // यहां वॉटरमार्किंग कोड जोड़ा जाएगा
}
```
## चरण 2: वॉटरमार्क जोड़ें
इसके बाद, वांछित टेक्स्ट और फ़ॉन्ट के साथ एक टेक्स्ट वॉटरमार्क ऑब्जेक्ट बनाएं। तय करना`isPrintOnly` को`true` यह सुनिश्चित करने के लिए कि वॉटरमार्क केवल तभी दिखाई दे जब दस्तावेज़ मुद्रित हो, दृश्य मोड में नहीं।
```csharp
TextWatermark textWatermark = new TextWatermark("This is a print only test watermark. It won't appear in view mode.", new Font("Arial", 8));
bool isPrintOnly = true;
```
## चरण 3: वॉटरमार्क विकल्प कॉन्फ़िगर करें
वॉटरमार्क के लिए विकल्पों को परिभाषित करें, जैसे पेज इंडेक्स जहां वॉटरमार्क जोड़ा जाना चाहिए और इसे केवल प्रिंट एनोटेशन के रूप में निर्दिष्ट करना।
```csharp
PdfAnnotationWatermarkOptions options = new PdfAnnotationWatermarkOptions();
options.PageIndex = 0;
options.PrintOnly = isPrintOnly;
```
## चरण 4: वॉटरमार्क लागू करें
निर्दिष्ट विकल्पों का उपयोग करके दस्तावेज़ में वॉटरमार्क जोड़ें और आउटपुट फ़ाइल को सहेजें।
```csharp
watermarker.Add(textWatermark, options);
watermarker.Save(outputFileName);
```

## निष्कर्ष
इस ट्यूटोरियल में, हमने सीखा कि .NET के लिए GroupDocs.Watermark का उपयोग करके PDF दस्तावेज़ में केवल-प्रिंट एनोटेशन वॉटरमार्क कैसे जोड़ा जाए। यह डेवलपर्स को दस्तावेज़ सुरक्षा और ब्रांडिंग को आसानी से बढ़ाने में सक्षम बनाता है।
## अक्सर पूछे जाने वाले प्रश्न
### क्या GroupDocs.Watermark पीडीएफ के अलावा अन्य दस्तावेज़ प्रारूपों के साथ संगत है?
हाँ, GroupDocs वर्ड, एक्सेल, पॉवरपॉइंट और छवियों जैसे विभिन्न दस्तावेज़ प्रारूपों का समर्थन करता है।
### क्या मैं वॉटरमार्क के स्वरूप को अनुकूलित कर सकता हूँ?
निश्चित रूप से, GroupDocs.Watermark वॉटरमार्क टेक्स्ट, फ़ॉन्ट, रंग, आकार और स्थिति को अनुकूलित करने के लिए व्यापक विकल्प प्रदान करता है।
### क्या GroupDocs.Watermark बैच प्रोसेसिंग क्षमताएं प्रदान करता है?
बिल्कुल, डेवलपर्स बैच प्रोसेसिंग सुविधाओं का उपयोग करके एक साथ कई दस्तावेज़ों को वॉटरमार्क कर सकते हैं।
### क्या GroupDocs.Watermark के लिए कोई परीक्षण संस्करण उपलब्ध है?
हां, आप दिए गए लिंक से GroupDocs.Watermark के निःशुल्क परीक्षण संस्करण तक पहुंच सकते हैं।
### मैं GroupDocs.Watermark के लिए तकनीकी सहायता कैसे प्राप्त कर सकता हूँ?
आप दिए गए सहायता लिंक पर उपलब्ध GroupDocs.Watermark फोरम से तकनीकी सहायता प्राप्त कर सकते हैं।