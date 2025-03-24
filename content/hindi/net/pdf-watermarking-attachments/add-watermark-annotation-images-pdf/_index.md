---
title: पीडीएफ में एनोटेशन छवियों में वॉटरमार्क जोड़ें
linktitle: पीडीएफ में एनोटेशन छवियों में वॉटरमार्क जोड़ें
second_title: GroupDocs.Watermark .NET API
description: जानें कि .NET के लिए Groupdocs.Watermark का उपयोग करके एनोटेशन छवियों में वॉटरमार्क जोड़कर अपने PDF दस्तावेज़ों को कैसे सुरक्षित रखें।
weight: 17
url: /hi/net/pdf-watermarking-attachments/add-watermark-annotation-images-pdf/
---
## परिचय
इस ट्यूटोरियल में, हम जानेंगे कि .NET के लिए Groupdocs.Watermark का उपयोग करके PDF दस्तावेज़ों में एनोटेशन छवियों में वॉटरमार्क कैसे जोड़ें। वॉटरमार्किंग आपके दस्तावेज़ों को अनधिकृत उपयोग या वितरण से बचाने के लिए महत्वपूर्ण है। इस चरण-दर-चरण मार्गदर्शिका का पालन करके, आप सीखेंगे कि पीडीएफ में एनोटेशन छवियों पर टेक्स्ट वॉटरमार्क को प्रभावी ढंग से कैसे लागू किया जाए।
## आवश्यक शर्तें
आगे बढ़ने से पहले, सुनिश्चित करें कि आपके पास निम्नलिखित हैं:
1. C# प्रोग्रामिंग भाषा की बुनियादी समझ।
2. .NET लाइब्रेरी के लिए Groupdocs.Watermark स्थापित किया गया।
3. विजुअल स्टूडियो जैसे विकास परिवेश तक पहुंच।
4. वॉटरमार्क के लिए एनोटेशन छवियों वाला एक पीडीएफ दस्तावेज़।

## नामस्थान आयात करना
सबसे पहले, आपको अपने C# कोड में आवश्यक नामस्थान आयात करने होंगे:
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.Pdf;
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
## चरण 2: पीडीएफ सामग्री प्राप्त करें और वॉटरमार्क प्रारंभ करें
```csharp
    PdfContent pdfContent = watermarker.GetContent<PdfContent>();
    // छवि या टेक्स्ट वॉटरमार्क प्रारंभ करें
    TextWatermark watermark = new TextWatermark("Protected image", new Font("Arial", 8));
    watermark.HorizontalAlignment = HorizontalAlignment.Center;
    watermark.VerticalAlignment = VerticalAlignment.Center;
    watermark.RotateAngle = 45;
    watermark.SizingType = SizingType.ScaleToParentDimensions;
    watermark.ScaleFactor = 1;
```
## चरण 3: पीडीएफ पृष्ठों और एनोटेशन छवियों के माध्यम से पुनरावृति करें
```csharp
    foreach (PdfPage page in pdfContent.Pages)
    {
        foreach (PdfAnnotation annotation in page.Annotations)
        {
            if (annotation.Image != null)
            {
                // छवि में वॉटरमार्क जोड़ें
                annotation.Image.Add(watermark);
            }
        }
    }
```
## चरण 4: दस्तावेज़ को वॉटरमार्क के साथ सहेजें
```csharp
    watermarker.Save(outputFileName);
}
```
इन चरणों को निष्पादित करने के बाद, आपके पीडीएफ दस्तावेज़ में एनोटेशन छवियों में निर्दिष्ट वॉटरमार्क जोड़ा जाएगा।

## निष्कर्ष
पीडीएफ में एनोटेशन छवियों में वॉटरमार्क जोड़ना आपके दस्तावेज़ों की अखंडता की रक्षा करने और यह सुनिश्चित करने के लिए आवश्यक है कि उनका दुरुपयोग न हो। .NET के लिए Groupdocs.Watermark के साथ, यह प्रक्रिया सरल और कुशल हो जाती है, जिससे आप अपनी पीडीएफ फाइलों को प्रभावी ढंग से सुरक्षित रख सकते हैं।
## अक्सर पूछे जाने वाले प्रश्न
### क्या मैं एक ही पीडीएफ दस्तावेज़ में एकाधिक वॉटरमार्क जोड़ सकता हूँ?
हाँ, आप .NET के लिए Groupdocs.Watermark का उपयोग करके एक ही PDF दस्तावेज़ में एकाधिक वॉटरमार्क जोड़ सकते हैं।
### क्या Groupdocs.Watermark पीडीएफ के अलावा अन्य दस्तावेज़ प्रारूपों का समर्थन करता है?
हां, ग्रुपडॉक्स वर्ड, एक्सेल, पॉवरपॉइंट और अन्य सहित विभिन्न दस्तावेज़ प्रारूपों का समर्थन करता है।
### क्या वॉटरमार्क के स्वरूप को अनुकूलित करना संभव है?
बिल्कुल, आप अपनी पसंद के अनुसार टेक्स्ट, फ़ॉन्ट, रंग, आकार और वॉटरमार्क की स्थिति को अनुकूलित कर सकते हैं।
### क्या मैं Groupdocs.Watermark का उपयोग करके PDF दस्तावेज़ों से वॉटरमार्क हटा सकता हूँ?
हां, Groupdocs.Watermark पीडीएफ दस्तावेज़ों से वॉटरमार्क को आसानी से हटाने की कार्यक्षमता प्रदान करता है।
### क्या .NET के लिए Groupdocs.Watermark के लिए कोई निःशुल्क परीक्षण उपलब्ध है?
हाँ, आप वेबसाइट से .NET के लिए Groupdocs.Watermark के निःशुल्क परीक्षण का लाभ उठा सकते हैं।