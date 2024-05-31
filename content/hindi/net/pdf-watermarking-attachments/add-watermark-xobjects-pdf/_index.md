---
title: पीडीएफ में XObjects में वॉटरमार्क जोड़ें
linktitle: पीडीएफ में XObjects में वॉटरमार्क जोड़ें
second_title: GroupDocs.Watermark .NET API
description: .NET के लिए Groupdocs.Watermark का उपयोग करके PDF में XObjects में वॉटरमार्क जोड़ने का तरीका जानें। आसान कार्यान्वयन के लिए हमारी चरण-दर-चरण मार्गदर्शिका का पालन करें।
type: docs
weight: 20
url: /hi/net/pdf-watermarking-attachments/add-watermark-xobjects-pdf/
---
## परिचय
यह सुनिश्चित करने के लिए कि आपके दस्तावेज़ अनधिकृत उपयोग से सुरक्षित हैं, पीडीएफ़ को वॉटरमार्क करना एक महत्वपूर्ण कदम है। .NET के लिए Groupdocs.Watermark के साथ, आपके PDF में XObjects में वॉटरमार्क जोड़ना इतना आसान कभी नहीं रहा। इस ट्यूटोरियल में, हम आपको चरण-दर-चरण प्रक्रिया के बारे में बताएंगे, यह सुनिश्चित करते हुए कि आप आत्मविश्वास से अपने पीडीएफ दस्तावेज़ों पर वॉटरमार्क लागू कर सकते हैं। आएँ शुरू करें!
## आवश्यक शर्तें
ट्यूटोरियल में जाने से पहले, आइए सुनिश्चित करें कि आपके पास निर्बाध रूप से पालन करने के लिए आवश्यक सभी चीजें हैं:
-  .NET के लिए Groupdocs.Watermark: यहां से नवीनतम संस्करण डाउनलोड और इंस्टॉल करें[यहाँ](https://releases.groupdocs.com/Watermark/net/).
- .NET फ्रेमवर्क: सुनिश्चित करें कि आपकी डेवलपमेंट मशीन पर .NET फ्रेमवर्क स्थापित है।
- विकास परिवेश: विज़ुअल स्टूडियो या किसी अन्य IDE का उपयोग करें जो .NET विकास का समर्थन करता है।
-  अस्थायी लाइसेंस: प्राप्त करें[अस्थायी लाइसेंस](https://purchase.groupdocs.com/temporary-license/) यदि आप उत्पाद का मूल्यांकन कर रहे हैं।
एक बार जब आपके पास ये पूर्वापेक्षाएँ हों, तो आप अपनी पीडीएफ़ को वॉटरमार्क करना शुरू करने के लिए तैयार हैं।
## नामस्थान आयात करें
सबसे पहले, आपको अपने प्रोजेक्ट में आवश्यक नामस्थान आयात करने की आवश्यकता होगी। अपना C# प्रोजेक्ट खोलें और निर्देशों का उपयोग करके निम्नलिखित जोड़ें:
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## चरण 1: अपना दस्तावेज़ पथ सेट करें
पहले चरण में आपके दस्तावेज़ के लिए पथ सेट करना शामिल है। उस पथ को परिभाषित करें जहां आपका पीडीएफ स्थित है और जहां आप वॉटरमार्क वाली पीडीएफ को सहेजना चाहते हैं।
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
 प्रतिस्थापित करें`"Your Document Path"` और`"Your Document Directory"` आपकी मशीन पर वास्तविक पथों के साथ।
## चरण 2: पीडीएफ लोड विकल्प प्रारंभ करें
इसके बाद, आपको पीडीएफ लोड विकल्पों को आरंभ करने की आवश्यकता होगी। पीडीएफ सामग्री को सही ढंग से लोड करने के लिए यह महत्वपूर्ण है।
```csharp
var loadOptions = new PdfLoadOptions();
```
## चरण 3: पीडीएफ दस्तावेज़ लोड करें
लोड विकल्पों का उपयोग करके, पीडीएफ दस्तावेज़ को इसके साथ लोड करें`Watermarker` कक्षा।
```csharp
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    PdfContent pdfContent = watermarker.GetContent<PdfContent>();
```
## चरण 4: वॉटरमार्क बनाएं
अब, आपको वॉटरमार्क बनाना होगा जो पीडीएफ में जोड़ा जाएगा। इस ट्यूटोरियल के लिए, हम एक टेक्स्ट वॉटरमार्क बनाएंगे।
```csharp
TextWatermark watermark = new TextWatermark("Protected image", new Font("Arial", 8))
{
    HorizontalAlignment = HorizontalAlignment.Center,
    VerticalAlignment = VerticalAlignment.Center,
    RotateAngle = 45,
    SizingType = SizingType.ScaleToParentDimensions,
    ScaleFactor = 1
};
```
## चरण 5: XObjects में वॉटरमार्क जोड़ें
वॉटरमार्क लागू करने के लिए पीडीएफ के भीतर प्रत्येक पृष्ठ और प्रत्येक XObject को दोहराएँ।
```csharp
foreach (PdfPage page in pdfContent.Pages)
{
    foreach (PdfXObject xObject in page.XObjects)
    {
        if (xObject.Image != null)
        {
            // छवि में वॉटरमार्क जोड़ें
            xObject.Image.Add(watermark);
        }
    }
}
```
## चरण 6: वॉटरमार्क वाली पीडीएफ को सेव करें
अंत में, वॉटरमार्क वाली पीडीएफ को निर्दिष्ट आउटपुट फ़ाइल में सहेजें।
```csharp
    watermarker.Save(outputFileName);
}
```
आखिर तुमने इसे हासिल कर ही लिया है! आपके पीडीएफ में अब सभी XObjects पर वॉटरमार्क शामिल हैं।
## निष्कर्ष
 .NET के लिए Groupdocs का उपयोग करके अपने PDF दस्तावेज़ों में वॉटरमार्क जोड़ना एक सीधी प्रक्रिया है जो सुरक्षा की एक अतिरिक्त परत प्रदान करती है। इस ट्यूटोरियल में बताए गए चरणों का पालन करके, आप यह सुनिश्चित कर सकते हैं कि आपके दस्तावेज़ अनधिकृत उपयोग से सुरक्षित हैं। याद रखें, आप हमेशा इसका संदर्भ ले सकते हैं[प्रलेखन](https://reference.groupdocs.com/Watermark/net/) अधिक विस्तृत जानकारी और उन्नत सुविधाओं के लिए।
## अक्सर पूछे जाने वाले प्रश्न
### क्या मैं टेक्स्ट के बजाय किसी छवि को वॉटरमार्क के रूप में उपयोग कर सकता हूँ?
हाँ, .NET के लिए Groupdocs.Watermark टेक्स्ट और छवि वॉटरमार्क दोनों का समर्थन करता है।
### मैं Groupdocs.Watermark को खरीदे बिना उसका परीक्षण कैसे कर सकता हूँ?
 आप एक का उपयोग कर सकते हैं[अस्थायी लाइसेंस](https://purchase.groupdocs.com/temporary-license/) उत्पाद का मूल्यांकन करने के लिए.
### क्या वॉटरमार्क के स्वरूप को अनुकूलित करना संभव है?
बिल्कुल! आप फ़ॉन्ट, आकार, घूर्णन कोण और बहुत कुछ अनुकूलित कर सकते हैं।
### क्या Groupdocs.Watermark अन्य दस्तावेज़ प्रारूपों का समर्थन करता है?
हाँ, यह Word, Excel और PowerPoint सहित विभिन्न स्वरूपों का समर्थन करता है।
### यदि मुझे कोई समस्या आती है तो मुझे सहायता कहाँ से मिल सकती है?
 से आपको सहयोग मिल सकता है[ग्रुपडॉक्स फोरम](https://forum.groupdocs.com/c/watermark/19).