---
title: पीडीएफ पेज को रेखापुंज करें
linktitle: पीडीएफ पेज को रेखापुंज करें
second_title: GroupDocs.Watermark .NET API
description: .NET के लिए GroupDocs के साथ दस्तावेज़ सुरक्षा बढ़ाएँ। पीडीएफ और अन्य प्रारूपों में निर्बाध रूप से वॉटरमार्क जोड़ें।
weight: 28
url: /hi/net/pdf-watermarking-attachments/rasterize-pdf-page/
---

# पीडीएफ पेज को रेखापुंज करें

## परिचय
.NET के लिए GroupDocs.Watermark एक शक्तिशाली एपीआई है जो डेवलपर्स को पीडीएफ, वर्ड, एक्सेल, पावरपॉइंट और अन्य सहित विभिन्न दस्तावेज़ प्रारूपों में वॉटरमार्क जोड़ने की अनुमति देता है। अपने सहज इंटरफ़ेस और व्यापक सुविधाओं के साथ, GroupDocs.Watermark दस्तावेज़ों में टेक्स्ट या छवि वॉटरमार्क जोड़ने की प्रक्रिया को सरल बनाता है, जिससे उपयोगकर्ता अपनी बौद्धिक संपदा की रक्षा कर सकते हैं और दस्तावेज़ सुरक्षा को आसानी से बढ़ा सकते हैं।
## आवश्यक शर्तें
.NET के लिए GroupDocs.Watermark का उपयोग करने से पहले, सुनिश्चित करें कि आपके पास निम्नलिखित शर्तें हैं:
1. इंस्टालेशन: .NET के लिए GroupDocs.Watermark को डाउनलोड और इंस्टाल करें[डाउनलोड पेज](https://releases.groupdocs.com/Watermark/net/).
2.  लाइसेंस: .NET के लिए GroupDocs.Watermark के लिए लाइसेंस प्राप्त करें। आप मूल्यांकन उद्देश्यों के लिए एक अस्थायी लाइसेंस प्राप्त कर सकते हैं[यहाँ](https://purchase.groupdocs.com/temporary-license/) , या से पूर्ण लाइसेंस खरीदें[खरीद पृष्ठ](https://purchase.groupdocs.com/buy).
3. .NET फ्रेमवर्क: सुनिश्चित करें कि आपकी डेवलपमेंट मशीन पर .NET फ्रेमवर्क स्थापित है।
4. दस्तावेज़: वह दस्तावेज़ तैयार करें जिसमें आप वॉटरमार्क जोड़ना चाहते हैं।

## नामस्थान आयात करें
.NET के लिए GroupDocs.Watermark का उपयोग शुरू करने के लिए, अपने प्रोजेक्ट में आवश्यक नेमस्पेस आयात करें:
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## चरण 1: दस्तावेज़ लोड करें
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // आपका कोड यहां जाता है
}
```
## चरण 2: वॉटरमार्क प्रारंभ करें
```csharp
TextWatermark watermark = new TextWatermark("Do not copy", new Font("Arial", 8));
watermark.HorizontalAlignment = HorizontalAlignment.Center;
watermark.VerticalAlignment = VerticalAlignment.Center;
watermark.RotateAngle = 45;
watermark.SizingType = SizingType.ScaleToParentDimensions;
watermark.ScaleFactor = 1;
watermark.Opacity = 0.5;
```
## चरण 3: वॉटरमार्क जोड़ें
```csharp
PdfArtifactWatermarkOptions options = new PdfArtifactWatermarkOptions();
options.PageIndex = 0;
watermarker.Add(watermark, options);
```
## चरण 4: पृष्ठ को व्यवस्थित करें
```csharp
PdfContent pdfContent = watermarker.GetContent<PdfContent>();
pdfContent.Pages[0].Rasterize(100, 100, PdfImageConversionFormat.Png);
```
## चरण 5: दस्तावेज़ सहेजें
```csharp
watermarker.Save(outputFileName);
```

## निष्कर्ष
अंत में, .NET के लिए GroupDocs.Watermark पीडीएफ और अन्य दस्तावेज़ प्रारूपों में वॉटरमार्क जोड़ने के लिए एक सहज समाधान प्रदान करता है। ऊपर उल्लिखित चरण-दर-चरण मार्गदर्शिका का पालन करके, डेवलपर्स पीडीएफ पृष्ठों को कुशलतापूर्वक व्यवस्थित कर सकते हैं और दस्तावेज़ सुरक्षा को आसानी से बढ़ा सकते हैं।
## अक्सर पूछे जाने वाले प्रश्न
### क्या GroupDocs.Watermark पीडीएफ के अलावा अन्य दस्तावेज़ प्रारूपों के साथ संगत है?
हाँ, GroupDocs.Watermark Word, Excel, PowerPoint, Visio और अन्य सहित दस्तावेज़ स्वरूपों की एक विस्तृत श्रृंखला का समर्थन करता है।
### क्या मैं दस्तावेज़ में जोड़े गए वॉटरमार्क के स्वरूप को अनुकूलित कर सकता हूँ?
बिल्कुल! GroupDocs.Watermark टेक्स्ट और छवि वॉटरमार्क के लिए व्यापक अनुकूलन विकल्प प्रदान करता है, जिससे उपयोगकर्ता अपनी प्राथमिकताओं के अनुसार फ़ॉन्ट, आकार, रंग, अस्पष्टता और स्थिति को समायोजित कर सकते हैं।
### क्या GroupDocs.Watermark व्यक्तिगत और व्यावसायिक उपयोग दोनों के लिए उपयुक्त है?
हां, GroupDocs.Watermark व्यक्तिगत और उद्यम दोनों की जरूरतों को पूरा करने के लिए लचीले लाइसेंसिंग विकल्प प्रदान करता है, जो इसे व्यक्तिगत परियोजनाओं के साथ-साथ बड़े पैमाने पर व्यावसायिक अनुप्रयोगों के लिए उपयुक्त बनाता है।
### क्या GroupDocs.Watermark डेवलपर्स के लिए तकनीकी सहायता प्रदान करता है?
हां, डेवलपर्स GroupDocs.Watermark फोरम के माध्यम से व्यापक तकनीकी सहायता प्राप्त कर सकते हैं, जहां वे सहायता मांग सकते हैं, अनुभव साझा कर सकते हैं और साथी डेवलपर्स के साथ जुड़ सकते हैं।
### क्या मैं खरीदारी करने से पहले GroupDocs.Watermark आज़मा सकता हूँ?
निश्चित रूप से! आप GroupDocs.Watermark के निःशुल्क परीक्षण संस्करण का लाभ उठा सकते हैं[पृष्ठ जारी करता है](https://releases.groupdocs.com/), जिससे आप खरीदारी करने से पहले इसकी विशेषताओं और कार्यप्रणाली का पता लगा सकते हैं।