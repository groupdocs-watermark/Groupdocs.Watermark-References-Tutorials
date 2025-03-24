---
title: पीडीएफ आयाम प्राप्त करें
linktitle: पीडीएफ आयाम प्राप्त करें
second_title: GroupDocs.Watermark .NET API
description: .NET के लिए Groupdocs.Watermark का उपयोग करके अपने दस्तावेज़ों को आसानी से सुरक्षित रखें। वॉटरमार्क, स्टैम्प और एनोटेशन आसानी से जोड़ें।
weight: 26
url: /hi/net/pdf-watermarking-attachments/get-pdf-dimensions/
---
## परिचय
आज के डिजिटल युग में, अपने दस्तावेज़ों की सुरक्षा करना सर्वोपरि है। चाहे आप व्यावसायिक पेशेवर हों, कानूनी विशेषज्ञ हों, या रचनात्मक कलाकार हों, अपनी बौद्धिक संपदा की रक्षा करना आवश्यक है। .NET के लिए Groupdocs.Watermark आपके दस्तावेज़ों में वॉटरमार्क, स्टैम्प और एनोटेशन जोड़ने, उनकी सुरक्षा और प्रामाणिकता सुनिश्चित करने के लिए एक मजबूत समाधान प्रदान करता है।
## आवश्यक शर्तें
.NET के लिए Groupdocs.Watermark की दुनिया में उतरने से पहले, सुनिश्चित करें कि आपके पास निम्नलिखित आवश्यक शर्तें हैं:
1.  .NET के लिए Groupdocs.Watermark की स्थापना: .NET के लिए Groupdocs.Watermark को डाउनलोड और इंस्टॉल करें।[लिंक को डाउनलोड करें](https://releases.groupdocs.com/Watermark/net/).
2.  लाइसेंस कुंजी (वैकल्पिक): जबकि .NET के लिए Groupdocs.Watermark एक निःशुल्क परीक्षण प्रदान करता है, आप अस्थायी लाइसेंस का विकल्प चुन सकते हैं या पूर्ण लाइसेंस खरीद सकते हैं[यहाँ](https://purchase.groupdocs.com/buy) विस्तारित कार्यक्षमता के लिए.
3. सी# से परिचित: दिए गए उदाहरणों को समझने और लागू करने के लिए सी# प्रोग्रामिंग भाषा का बुनियादी ज्ञान अनुशंसित है।
4. सुरक्षित रखने के लिए दस्तावेज़: प्रयोग करने के लिए अपनी स्थानीय मशीन पर एक नमूना दस्तावेज़ (उदाहरण के लिए, पीडीएफ, वर्ड, एक्सेल) तैयार रखें।

## नामस्थान आयात करें
.NET के लिए Groupdocs.Watermark के साथ काम करना शुरू करने के लिए, आपको अपने C# प्रोजेक्ट में आवश्यक नेमस्पेस आयात करना होगा।
```csharp
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using System;
using System.IO;
```
### चरण 1: चर घोषित करें
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
### चरण 2: दस्तावेज़ लोड करें
```csharp
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
```
### चरण 3: पीडीएफ सामग्री प्राप्त करें
```csharp
PdfContent pdfContent = watermarker.GetContent<PdfContent>();
```
### चरण 4: आयाम पुनः प्राप्त करें
```csharp
Console.WriteLine(pdfContent.Pages[0].Width);
Console.WriteLine(pdfContent.Pages[0].Height);
```

## निष्कर्ष
अंत में, .NET के लिए Groupdocs.Watermark आपके दस्तावेज़ों को अनधिकृत उपयोग और वितरण से बचाने के लिए एक व्यापक समाधान प्रदान करता है। ऊपर बताए गए चरणों का पालन करके और .NET के लिए Groupdocs.Watermark की शक्ति का लाभ उठाकर, आप अपनी मूल्यवान डिजिटल संपत्तियों की सुरक्षा और अखंडता सुनिश्चित कर सकते हैं।
## अक्सर पूछे जाने वाले प्रश्न
### क्या मैं .NET के लिए Groupdocs.Watermark का निःशुल्क उपयोग कर सकता हूँ?
हाँ, .NET के लिए Groupdocs.Watermark मूल्यांकन उद्देश्यों के लिए एक निःशुल्क परीक्षण संस्करण प्रदान करता है। हालाँकि, विस्तारित कार्यक्षमता के लिए, आप पूर्ण लाइसेंस खरीदने पर विचार कर सकते हैं।
### क्या Groupdocs.Watermark एकाधिक दस्तावेज़ प्रारूपों का समर्थन करता है?
हां, ग्रुपडॉक्स पीडीएफ, वर्ड, एक्सेल, पावरपॉइंट और अन्य सहित दस्तावेज़ प्रारूपों की एक विस्तृत श्रृंखला का समर्थन करता है।
### क्या मैं Groupdocs.Watermark के साथ वॉटरमार्क और स्टैम्प को अनुकूलित कर सकता हूँ?
बिल्कुल! Groupdocs.Watermark आपकी विशिष्ट आवश्यकताओं के अनुरूप वॉटरमार्क, स्टैम्प और एनोटेशन के लिए व्यापक अनुकूलन विकल्प प्रदान करता है।
### क्या Groupdocs.Watermark उपयोगकर्ताओं के लिए तकनीकी सहायता उपलब्ध है?
 हां, आप तकनीकी सहायता प्राप्त कर सकते हैं और ग्रुपडॉक्स समुदाय के साथ जुड़ सकते हैं[सहयता मंच](https://forum.groupdocs.com/c/watermark/19).
### मैं Groupdocs.Watermark के लिए अस्थायी लाइसेंस कैसे प्राप्त कर सकता हूं?
 आप Groupdocs.Watermark के लिए एक अस्थायी लाइसेंस प्राप्त कर सकते हैं[यहाँ](https://purchase.groupdocs.com/temporary-license/).