---
title: पीडीएफ से एक्सऑब्जेक्ट जानकारी निकालें
linktitle: पीडीएफ से एक्सऑब्जेक्ट जानकारी निकालें
second_title: GroupDocs.Watermark .NET API
description: .NET के लिए GroupDocs.Watermark के साथ दस्तावेज़ वॉटरमार्किंग की शक्ति को अनलॉक करें। पीडीएफ़, वर्ड दस्तावेज़ों और छवियों में वॉटरमार्क को निर्बाध रूप से प्रबंधित करें।
weight: 25
url: /hi/net/pdf-watermarking-attachments/extract-xobject-information-pdf/
---
## परिचय
.NET के लिए GroupDocs.Watermark एक शक्तिशाली दस्तावेज़ वॉटरमार्किंग एपीआई है जिसे पीडीएफ, वर्ड, एक्सेल, पावरपॉइंट और छवियों जैसे विभिन्न दस्तावेज़ प्रारूपों में वॉटरमार्क में हेरफेर करने के लिए डिज़ाइन किया गया है। यह डेवलपर्स को दस्तावेज़ों में प्रोग्रामेटिक रूप से वॉटरमार्क जोड़ने, हटाने, खोजने और बदलने के लिए एक सीधा दृष्टिकोण प्रदान करता है। चाहे आपको अपने दस्तावेज़ों में कंपनी का लोगो, कॉपीराइट नोटिस, या गोपनीय मोहर जोड़ने की आवश्यकता हो, GroupDocs.Watermark अपने सहज एपीआई के साथ प्रक्रिया को सरल बनाता है।
## आवश्यक शर्तें
.NET के लिए GroupDocs.Watermark में गोता लगाने से पहले, सुनिश्चित करें कि आपके पास निम्नलिखित आवश्यक शर्तें हैं:
1. इंस्टालेशन: .NET के लिए GroupDocs.Watermark को डाउनलोड और इंस्टाल करें[डाउनलोड पेज](https://releases.groupdocs.com/Watermark/net/).
2. विकास परिवेश: अपने सिस्टम पर विज़ुअल स्टूडियो या कोई अन्य .NET IDE स्थापित करें।
3. .NET फ्रेमवर्क: सुनिश्चित करें कि आपके पास अपनी विकास मशीन पर आवश्यक .NET फ्रेमवर्क स्थापित है।

## नामस्थान आयात करना
अपने प्रोजेक्ट में .NET के लिए GroupDocs.Watermark का उपयोग शुरू करने के लिए, आपको आवश्यक नेमस्पेस आयात करने की आवश्यकता है।
अपने .NET प्रोजेक्ट में, GroupDocs.Watermark.dll का संदर्भ जोड़ें।
```csharp
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using System;
using System.IO;
```
## चरण 1: दस्तावेज़ लोड करें
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
```
## चरण 2: पीडीएफ सामग्री तक पहुंचें
```csharp
PdfContent pdfContent = watermarker.GetContent<PdfContent>();
```
## चरण 3: पृष्ठों के माध्यम से पुनरावृति करें
```csharp
foreach (PdfPage page in pdfContent.Pages)
```
## चरण 4: XObjects तक पहुंचें
```csharp
foreach (PdfXObject xObject in page.XObjects)
```
## चरण 5: जानकारी निकालें
```csharp
if (xObject.Image != null)
{
    Console.WriteLine(xObject.Image.Width);
    Console.WriteLine(xObject.Image.Height);
    Console.WriteLine(xObject.Image.GetBytes().Length);
}
Console.WriteLine(xObject.Text);
Console.WriteLine(xObject.X);
Console.WriteLine(xObject.Y);
Console.WriteLine(xObject.Width);
Console.WriteLine(xObject.Height);
Console.WriteLine(xObject.RotateAngle);
```

## निष्कर्ष
.NET के लिए GroupDocs.Watermark डेवलपर्स को उनके .NET अनुप्रयोगों में दस्तावेज़ वॉटरमार्क को निर्बाध रूप से प्रबंधित करने का अधिकार देता है। अपनी सहज एपीआई और मजबूत सुविधाओं के साथ, यह किसी भी वॉटरमार्किंग आवश्यकता के लिए सबसे उपयुक्त समाधान है। इस गाइड में उल्लिखित चरणों का पालन करके, आप ग्रुपडॉक्स की पूरी क्षमता का उपयोग कर सकते हैं और अपने दस्तावेज़ प्रबंधन वर्कफ़्लो को बढ़ा सकते हैं।
## अक्सर पूछे जाने वाले प्रश्न
### क्या GroupDocs.Watermark सभी .NET फ्रेमवर्क के साथ संगत है?
हां, GroupDocs.Watermark .NET कोर और .NET फ्रेमवर्क सहित .NET फ्रेमवर्क की एक विस्तृत श्रृंखला का समर्थन करता है।
### क्या मैं GroupDocs.Watermark का उपयोग करके एक ही दस्तावेज़ पर एकाधिक वॉटरमार्क लागू कर सकता हूँ?
बिल्कुल! GroupDocs.Watermark आपको एक ही दस्तावेज़ में विभिन्न प्रकार के कई वॉटरमार्क जोड़ने की अनुमति देता है।
### क्या GroupDocs.Watermark दस्तावेज़ एन्क्रिप्शन के लिए समर्थन प्रदान करता है?
हां, GroupDocs.Watermark आपके दस्तावेज़ों को अनधिकृत पहुंच से सुरक्षित करने के लिए एन्क्रिप्शन क्षमताएं प्रदान करता है।
### क्या GroupDocs.Watermark के लिए कोई परीक्षण संस्करण उपलब्ध है?
 हां, आप GroupDocs.Watermark के निःशुल्क परीक्षण संस्करण तक पहुंच सकते हैं[डाउनलोड पेज](https://releases.groupdocs.com/).
### मुझे GroupDocs.Watermark के लिए अतिरिक्त समर्थन और संसाधन कहां मिल सकते हैं?
आप GroupDocs.Watermark दस्तावेज़ का अन्वेषण कर सकते हैं, सामुदायिक फ़ोरम में शामिल हो सकते हैं, या सहायता के लिए सहायता टीम तक पहुँच सकते हैं।