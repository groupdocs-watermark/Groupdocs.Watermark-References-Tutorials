---
title: पीडीएफ में छवि कलाकृतियों में वॉटरमार्क जोड़ें
linktitle: पीडीएफ में छवि कलाकृतियों में वॉटरमार्क जोड़ें
second_title: GroupDocs.Watermark .NET API
description: .NET के लिए GroupDocs.Watermark का उपयोग करके अपनी पीडीएफ फाइलों को वैयक्तिकृत वॉटरमार्क से सुरक्षित रखें। पीडीएफ दस्तावेज़ों में छवि कलाकृतियों में आसानी से टेक्स्ट या छवि वॉटरमार्क जोड़ें।
weight: 18
url: /hi/net/pdf-watermarking-attachments/add-watermark-image-artifacts-pdf/
---

# पीडीएफ में छवि कलाकृतियों में वॉटरमार्क जोड़ें

## परिचय
इस ट्यूटोरियल में, हम .NET के लिए GroupDocs.Watermark का उपयोग करके एक पीडीएफ दस्तावेज़ में छवि कलाकृतियों में वॉटरमार्क जोड़ने की प्रक्रिया में आपका मार्गदर्शन करेंगे। इन चरणों का पालन करके, आप वैयक्तिकृत वॉटरमार्क के साथ अपनी पीडीएफ फाइलों को कुशलतापूर्वक सुरक्षित कर सकते हैं।
## आवश्यक शर्तें
शुरू करने से पहले, सुनिश्चित करें कि आपके पास निम्नलिखित आवश्यकताएँ हैं:
1.  .NET के लिए GroupDocs.Watermark: .NET लाइब्रेरी के लिए GroupDocs.Watermark को डाउनलोड और इंस्टॉल करें[यहाँ](https://releases.groupdocs.com/Watermark/net/).
2. दस्तावेज़ पथ: पीडीएफ दस्तावेज़ का पथ रखें जहां आप वॉटरमार्क जोड़ना चाहते हैं।
3. आउटपुट निर्देशिका: एक निर्देशिका बनाएं जहां वॉटरमार्क दस्तावेज़ सहेजा जाएगा।

## नामस्थान आयात करें
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## चरण 1: दस्तावेज़ लोड करें और वॉटरमार्कर प्रारंभ करें
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
```
## चरण 2: पीडीएफ सामग्री प्राप्त करें और वॉटरमार्क जोड़ें
```csharp
	PdfContent pdfContent = watermarker.GetContent<PdfContent>();
	// छवि या टेक्स्ट वॉटरमार्क प्रारंभ करें
	TextWatermark watermark = new TextWatermark("Protected image", new Font("Arial", 8));
	watermark.HorizontalAlignment = HorizontalAlignment.Center;
	watermark.VerticalAlignment = VerticalAlignment.Center;
	watermark.RotateAngle = 45;
	watermark.SizingType = SizingType.ScaleToParentDimensions;
	watermark.ScaleFactor = 1;
	foreach (PdfPage page in pdfContent.Pages)
	{
		foreach (PdfArtifact artifact in page.Artifacts)
		{
			if (artifact.Image != null)
			{
				// छवि में वॉटरमार्क जोड़ें
				artifact.Image.Add(watermark);
			}
		}
	}
```
## चरण 3: वॉटरमार्क दस्तावेज़ सहेजें
```csharp
	watermarker.Save(outputFileName);
}
```

## निष्कर्ष
.NET के लिए GroupDocs.Watermark के साथ, PDF दस्तावेज़ों में छवि कलाकृतियों में वॉटरमार्क जोड़ना एक सहज प्रक्रिया बन जाती है। इस ट्यूटोरियल का अनुसरण करके, आप अपनी पीडीएफ फाइलों को अनुकूलित वॉटरमार्क के साथ कुशलतापूर्वक संरक्षित कर सकते हैं, उनकी सुरक्षा और प्रामाणिकता सुनिश्चित कर सकते हैं।
## अक्सर पूछे जाने वाले प्रश्न
### क्या मैं अपने पीडीएफ दस्तावेज़ में छवि और टेक्स्ट वॉटरमार्क दोनों जोड़ सकता हूँ?
हाँ, .NET के लिए GroupDocs.Watermark छवि और टेक्स्ट वॉटरमार्क दोनों को एक साथ जोड़ने का समर्थन करता है।
### क्या किसी दस्तावेज़ में मेरे द्वारा जोड़े जा सकने वाले वॉटरमार्क की संख्या पर कोई सीमा है?
नहीं, आप बिना किसी सीमा के किसी दस्तावेज़ में एकाधिक वॉटरमार्क जोड़ सकते हैं।
### क्या मैं वॉटरमार्क की उपस्थिति और स्थिति को अनुकूलित कर सकता हूँ?
बिल्कुल, वॉटरमार्क की उपस्थिति, स्थिति और गुणों पर आपका पूरा नियंत्रण है।
### क्या .NET के लिए GroupDocs.Watermark PDF के अलावा अन्य दस्तावेज़ प्रारूपों का समर्थन करता है?
हां, यह वर्ड, एक्सेल, पॉवरपॉइंट और अन्य सहित विभिन्न दस्तावेज़ प्रारूपों का समर्थन करता है।
### क्या किसी दस्तावेज़ से वॉटरमार्क हटाने का कोई तरीका है?
हां, .NET के लिए GroupDocs.Watermark जरूरत पड़ने पर दस्तावेज़ों से वॉटरमार्क हटाने के तरीके प्रदान करता है।