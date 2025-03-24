---
title: पीडीएफ में एनोटेशन वॉटरमार्क जोड़ें
linktitle: पीडीएफ में एनोटेशन वॉटरमार्क जोड़ें
second_title: GroupDocs.Watermark .NET API
description: .NET के लिए GroupDocs.Watermark का उपयोग करके आसानी से PDF दस्तावेज़ों में एनोटेशन वॉटरमार्क जोड़ने का तरीका जानें। आसानी से दस्तावेज़ ब्रांडिंग और सुरक्षा बढ़ाएँ।
weight: 10
url: /hi/net/pdf-watermarking-attachments/add-annotation-watermark-pdf/
---
## परिचय
दस्तावेज़ प्रबंधन के क्षेत्र में, पीडीएफ फाइलों में वॉटरमार्क जोड़ना एक महत्वपूर्ण पहलू के रूप में कार्य करता है, विशेष रूप से ब्रांडिंग, सुरक्षा और दस्तावेज़ पहचान उद्देश्यों के लिए। .NET के लिए GroupDocs.Watermark एक शक्तिशाली लाइब्रेरी है जो PDF सहित विभिन्न दस्तावेज़ प्रारूपों में वॉटरमार्क के निर्बाध एकीकरण की सुविधा प्रदान करती है। इस ट्यूटोरियल में, हम .NET के लिए GroupDocs.Watermark द्वारा प्रदान की गई कार्यक्षमताओं का उपयोग करते हुए, चरण दर चरण पीडीएफ दस्तावेज़ों में एनोटेशन वॉटरमार्क जोड़ने की प्रक्रिया के बारे में विस्तार से जानेंगे।
## आवश्यक शर्तें
इससे पहले कि हम ट्यूटोरियल के साथ आगे बढ़ें, सुनिश्चित करें कि आपके पास निम्नलिखित शर्तें मौजूद हैं:
1.  .NET लाइब्रेरी के लिए GroupDocs.Watermark: .NET लाइब्रेरी के लिए GroupDocs.Watermark को डाउनलोड और इंस्टॉल करें।[वेबसाइट](https://releases.groupdocs.com/Watermark/net/).
2. विकास वातावरण: एक उपयुक्त विकास वातावरण स्थापित करें, जैसे विज़ुअल स्टूडियो या कोई अन्य .NET IDE।
3. C# की बुनियादी समझ: C# प्रोग्रामिंग भाषा के बुनियादी सिद्धांतों से परिचित होने की अनुशंसा की जाती है।

## आवश्यक नामस्थान आयात करना
आरंभ करने के लिए, अपने C# प्रोजेक्ट में आवश्यक नामस्थान आयात करें:
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Options.Image;
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
	PdfAnnotationWatermarkOptions options = new PdfAnnotationWatermarkOptions();
```
## चरण 3: टेक्स्ट वॉटरमार्क जोड़ें
```csharp
	TextWatermark textWatermark = new TextWatermark("This is an annotation watermark", new Font("Arial", 8));
	textWatermark.HorizontalAlignment = HorizontalAlignment.Left;
	textWatermark.VerticalAlignment = VerticalAlignment.Top;
	watermarker.Add(textWatermark, options);
```
## चरण 4: छवि वॉटरमार्क जोड़ें
```csharp
	using (ImageWatermark imageWatermark = new ImageWatermark(Constants.ProtectJpg))
	{
		imageWatermark.HorizontalAlignment = HorizontalAlignment.Right;
		imageWatermark.VerticalAlignment = VerticalAlignment.Top;
		watermarker.Add(imageWatermark, options);
	}
```
## चरण 5: दस्तावेज़ को वॉटरमार्क के साथ सहेजें
```csharp
	watermarker.Save(outputFileName);
}
```

## निष्कर्ष
अंत में, .NET के लिए GroupDocs.Watermark प्रोग्रामेटिक रूप से PDF दस्तावेज़ों में एनोटेशन वॉटरमार्क जोड़ने के लिए एक व्यापक समाधान प्रदान करता है। उल्लिखित चरणों का पालन करके, उपयोगकर्ता अपनी पीडीएफ फाइलों में टेक्स्ट और छवि वॉटरमार्क को सहजता से एकीकृत कर सकते हैं, जिससे दस्तावेज़ ब्रांडिंग और सुरक्षा बढ़ सकती है।
## अक्सर पूछे जाने वाले प्रश्न
### क्या GroupDocs.Watermark पीडीएफ के अलावा अन्य दस्तावेज़ प्रारूपों के साथ संगत है?
हाँ, GroupDocs.Watermark Word, Excel, PowerPoint और अन्य सहित दस्तावेज़ स्वरूपों की एक विस्तृत श्रृंखला का समर्थन करता है।
### क्या मैं वॉटरमार्क के स्वरूप को अनुकूलित कर सकता हूँ?
बिल्कुल! GroupDocs.Watermark टेक्स्ट और छवि वॉटरमार्क दोनों के लिए व्यापक अनुकूलन विकल्प प्रदान करता है, जिससे उपयोगकर्ता आकार, स्थिति, अस्पष्टता और अन्य मापदंडों को समायोजित कर सकते हैं।
### क्या GroupDocs.Watermark दस्तावेज़ों की बैच प्रोसेसिंग के लिए उपयुक्त है?
निश्चित रूप से! GroupDocs.Watermark कुशल बैच प्रोसेसिंग क्षमताएं प्रदान करता है, जिससे उपयोगकर्ता एक साथ कई दस्तावेज़ों पर वॉटरमार्क लागू कर सकते हैं।
### क्या GroupDocs.Watermark .NET कोर विकास का समर्थन करता है?
हाँ, GroupDocs.Watermark .NET कोर का समर्थन करता है, जिससे डेवलपर्स को वॉटरमार्किंग कार्यक्षमताओं को क्रॉस-प्लेटफ़ॉर्म अनुप्रयोगों में एकीकृत करने की अनुमति मिलती है।
### क्या GroupDocs.Watermark उपयोगकर्ताओं के लिए तकनीकी सहायता उपलब्ध है?
हाँ, GroupDocs अपने समर्पित मंचों और ग्राहक सेवा चैनलों के माध्यम से व्यापक तकनीकी सहायता प्रदान करता है।