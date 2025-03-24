---
title: पीडीएफ से एनोटेशन जानकारी निकालें
linktitle: पीडीएफ से एनोटेशन जानकारी निकालें
second_title: GroupDocs.Watermark .NET API
description: इस विस्तृत, चरण-दर-चरण मार्गदर्शिका में .NET के लिए GroupDocs.Watermark का उपयोग करके PDF दस्तावेज़ों से एनोटेशन जानकारी निकालने का तरीका जानें।
weight: 23
url: /hi/net/pdf-watermarking-attachments/extract-annotation-information-pdf/
---
## परिचय
क्या आपको अक्सर अपने पीडीएफ दस्तावेज़ों से विस्तृत एनोटेशन जानकारी निकालने की आवश्यकता महसूस होती है? चाहे आप दस्तावेज़ प्रबंधन प्रणालियों पर काम करने वाले डेवलपर हों या कई पीडीएफ को संभालने वाले व्यावसायिक पेशेवर हों, एनोटेशन को कुशलतापूर्वक निकालना और संसाधित करना महत्वपूर्ण हो सकता है। .NET के लिए GroupDocs.Watermark के साथ, आपके पास इस कार्य को सीधा और कुशल बनाने के लिए एक शक्तिशाली टूलकिट है।
## आवश्यक शर्तें
इससे पहले कि हम कोड में उतरें, आइए सुनिश्चित करें कि आरंभ करने के लिए आपके पास वह सब कुछ है जो आपको चाहिए:
1. विजुअल स्टूडियो: सुनिश्चित करें कि आपके पास विजुअल स्टूडियो स्थापित है। कोड लिखने और चलाने के लिए यह हमारी आईडीई होगी।
2.  .NET के लिए GroupDocs.Watermark: .NET लाइब्रेरी के लिए आपके पास GroupDocs.Watermark होना चाहिए। तुम कर सकते हो[यहाँ पर डाउनलोड करो](https://releases.groupdocs.com/Watermark/net/).
3. C# का बुनियादी ज्ञान: उदाहरणों के साथ C# प्रोग्रामिंग से परिचित होना आवश्यक है।
## नामस्थान आयात करें
आरंभ करने के लिए, आपको अपने प्रोजेक्ट में आवश्यक नामस्थान आयात करना होगा। इन नामस्थानों में पीडीएफ फाइलों के साथ काम करने और एनोटेशन निकालने के लिए आवश्यक कक्षाएं और विधियां शामिल हैं।
```csharp
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using System;
using System.IO;
```
## चरण 1: अपना प्रोजेक्ट सेट करें
सबसे पहले, आइए विजुअल स्टूडियो में अपना प्रोजेक्ट स्थापित करें। एक नया कंसोल ऐप (.NET कोर) प्रोजेक्ट बनाएं। एक बार आपका प्रोजेक्ट बन जाने के बाद, आपको .NET लाइब्रेरी के लिए GroupDocs.Watermark में एक संदर्भ जोड़ना होगा।
1. NuGet पैकेज मैनेजर खोलें।
2.  निम्न को खोजें`GroupDocs.Watermark`.
3.  स्थापित करें`GroupDocs.Watermark` पैकेट।
## चरण 2: दस्तावेज़ पथ परिभाषित करें
इसके बाद, आपको अपने इनपुट पीडीएफ दस्तावेज़ और आउटपुट निर्देशिका के लिए पथ निर्दिष्ट करने की आवश्यकता होगी जहां निकाली गई जानकारी सहेजी जाएगी। यह सुनिश्चित करता है कि आपका एप्लिकेशन जानता है कि पीडीएफ फाइल कहां ढूंढनी है और परिणाम कहां संग्रहीत करना है।
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
## चरण 3: पीडीएफ दस्तावेज़ लोड करें
 पीडीएफ दस्तावेज़ के साथ काम करने के लिए, हमें इसका उपयोग करके लोड करना होगा`PdfLoadOptions`. यह वर्ग लोडिंग प्रक्रिया को कॉन्फ़िगर करने के लिए विकल्प प्रदान करता है।
```csharp
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // एनोटेशन निकालने के लिए कोड यहां जाएगा
}
```
## चरण 4: पीडीएफ सामग्री तक पहुंचें
एक बार दस्तावेज़ लोड हो जाने पर, हम उसकी सामग्री तक पहुंच सकते हैं। विशेष रूप से, हम पीडीएफ सामग्री प्राप्त करना चाहते हैं ताकि हम पृष्ठों और एनोटेशन के माध्यम से पुनरावृति कर सकें।
```csharp
PdfContent pdfContent = watermarker.GetContent<PdfContent>();
```
## चरण 5: पृष्ठों और टिप्पणियों के माध्यम से पुनरावृति करें
हाथ में पीडीएफ सामग्री के साथ, हम प्रत्येक पृष्ठ के माध्यम से और फिर उन पृष्ठों पर प्रत्येक एनोटेशन के माध्यम से लूप कर सकते हैं। इससे हमें आवश्यक जानकारी निकालने में मदद मिलती है।
```csharp
foreach (PdfPage page in pdfContent.Pages)
{
    foreach (PdfAnnotation annotation in page.Annotations)
    {
        // एनोटेशन विवरण यहां निकालें
    }
}
```
## चरण 6: एनोटेशन विवरण निकालें
नेस्टेड लूप्स के भीतर, हम प्रत्येक एनोटेशन के बारे में विभिन्न विवरण निकालते हैं। इसमें एनोटेशन का प्रकार, कोई भी संबद्ध छवियाँ, पाठ और स्थिति संबंधी डेटा शामिल हैं।
```csharp
Console.WriteLine(annotation.AnnotationType);
if (annotation.Image != null)
{
    Console.WriteLine(annotation.Image.Width);
    Console.WriteLine(annotation.Image.Height);
    Console.WriteLine(annotation.Image.GetBytes().Length);
}
Console.WriteLine(annotation.Text);
Console.WriteLine(annotation.X);
Console.WriteLine(annotation.Y);
Console.WriteLine(annotation.Width);
Console.WriteLine(annotation.Height);
Console.WriteLine(annotation.RotateAngle);
```
## चरण 7: निकाले गए डेटा को सहेजें या संसाधित करें
अंत में, तय करें कि आप निकाली गई एनोटेशन जानकारी के साथ क्या करना चाहते हैं। आप अपनी आवश्यकताओं के आधार पर इसे कंसोल पर प्रिंट कर सकते हैं, फ़ाइल में सहेज सकते हैं, या डेटाबेस में भी संग्रहीत कर सकते हैं।
```csharp
// निकाले गए डेटा को फ़ाइल में सहेजने का उदाहरण
using (StreamWriter writer = new StreamWriter(outputFileName))
{
    foreach (PdfPage page in pdfContent.Pages)
    {
        foreach (PdfAnnotation annotation in page.Annotations)
        {
            writer.WriteLine($"Annotation Type: {annotation.AnnotationType}");
            if (annotation.Image != null)
            {
                writer.WriteLine($"Image Width: {annotation.Image.Width}");
                writer.WriteLine($"Image Height: {annotation.Image.Height}");
                writer.WriteLine($"Image Bytes: {annotation.Image.GetBytes().Length}");
            }
            writer.WriteLine($"Text: {annotation.Text}");
            writer.WriteLine($"Position: ({annotation.X}, {annotation.Y})");
            writer.WriteLine($"Size: {annotation.Width}x{annotation.Height}");
            writer.WriteLine($"Rotate Angle: {annotation.RotateAngle}");
        }
    }
}
```
## निष्कर्ष
.NET के लिए GroupDocs.Watermark का उपयोग करके पीडीएफ दस्तावेज़ों से एनोटेशन जानकारी निकालना एक सीधी प्रक्रिया है जो आपका बहुत सारा समय और प्रयास बचा सकती है। इस गाइड में उल्लिखित चरणों का पालन करके, आप इस कार्यक्षमता को आसानी से अपनी परियोजनाओं में एकीकृत कर सकते हैं और मूल्यवान एनोटेशन डेटा के निष्कर्षण को स्वचालित कर सकते हैं।
 चाहे आप बड़ी मात्रा में पीडीएफ का प्रबंधन कर रहे हों या बस विशिष्ट जानकारी निकालने की आवश्यकता हो, .NET के लिए GroupDocs.Watermark एक विश्वसनीय और कुशल समाधान प्रदान करता है। को जांचना न भूलें[प्रलेखन](https://tutorials.groupdocs.com/Watermark/net/) अधिक उन्नत सुविधाओं और अनुकूलन विकल्पों के लिए।
## अक्सर पूछे जाने वाले प्रश्न
### .NET के लिए GroupDocs.Watermark क्या है?
.NET के लिए GroupDocs.Watermark एक व्यापक लाइब्रेरी है जो डेवलपर्स को PDF, Word दस्तावेज़ और छवियों सहित विभिन्न दस्तावेज़ प्रारूपों से वॉटरमार्क जोड़ने, खोजने और हटाने की अनुमति देती है।
### क्या मैं GroupDocs.Watermark निःशुल्क आज़मा सकता हूँ?
 हाँ, आप पा सकते हैं[मुफ्त परीक्षण](https://releases.groupdocs.com/) खरीदारी करने से पहले लाइब्रेरी की सुविधाओं का परीक्षण करना।
### यदि मुझे कोई समस्या आती है तो मुझे सहायता कैसे मिलेगी?
 आप GroupDocs टीम पर जाकर उनसे सहायता प्राप्त कर सकते हैं[सहयता मंच](https://forum.groupdocs.com/c/watermark/19).
### क्या परीक्षण के लिए अस्थायी लाइसेंस प्राप्त करना संभव है?
 हाँ, आप अनुरोध कर सकते हैं[अस्थायी लाइसेंस](https://purchase.groupdocs.com/temporary-license/)परीक्षण प्रयोजनों के लिए.
### मैं .NET के लिए GroupDocs.Watermark का पूर्ण संस्करण कहां से खरीद सकता हूं?
 आप पूर्ण संस्करण यहां से खरीद सकते हैं[ग्रुपडॉक्स वेबसाइट](https://purchase.groupdocs.com/buy).