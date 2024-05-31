---
title: पीडीएफ में अनुलग्नक जोड़ें
linktitle: पीडीएफ में अनुलग्नक जोड़ें
second_title: GroupDocs.Watermark .NET API
description: निर्बाध वॉटरमार्किंग और अटैचमेंट हैंडलिंग के लिए GroupDocs.Watermark के साथ अपनी .NET दस्तावेज़ प्रबंधन क्षमताओं को बढ़ाएं।
type: docs
weight: 12
url: /hi/net/pdf-watermarking-attachments/add-attachment-pdf/
---
## परिचय
.NET विकास के क्षेत्र में, GroupDocs.Watermark विभिन्न दस्तावेज़ प्रारूपों में वॉटरमार्क, एनोटेशन और बहुत कुछ प्रबंधित करने के लिए एक शक्तिशाली उपकरण के रूप में सामने आता है। चाहे आप PDF, Word दस्तावेज़, या छवियों के साथ काम कर रहे हों, .NET के लिए GroupDocs.Watermark एक सहज एकीकरण प्रदान करता है जो डेवलपर्स को दस्तावेज़ों में आसानी से हेरफेर करने में सक्षम बनाता है।
## आवश्यक शर्तें
.NET के लिए GroupDocs.Watermark का उपयोग करने की जटिलताओं में गोता लगाने से पहले, सुनिश्चित करें कि आपके पास निम्नलिखित पूर्वापेक्षाएँ हैं:
1.  स्थापना: सुनिश्चित करें कि आपने .NET के लिए GroupDocs.Watermark स्थापित किया है। आप इसे यहां से डाउनलोड कर सकते हैं[रिलीज पेज](https://releases.groupdocs.com/Watermark/net/).
2. दस्तावेज़ तैयार करना: एक दस्तावेज़ तैयार रखें जिस पर आप वॉटरमार्किंग या अन्य कार्य करना चाहते हैं।
3. C# का बुनियादी ज्ञान: C# प्रोग्रामिंग भाषा की बुनियादी बातों से खुद को परिचित करें क्योंकि हम इसका उपयोग GroupDocs.Watermark API के साथ इंटरैक्ट करने के लिए करेंगे।

## नामस्थान आयात करें
कार्यान्वयन शुरू करने से पहले, GroupDocs.Watermark की कार्यक्षमता तक पहुंचने के लिए आवश्यक नामस्थान आयात करना महत्वपूर्ण है। नीचे आवश्यक नामस्थान हैं:
```csharp
using System;
using System.IO;
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
```
## चरण 1: दस्तावेज़ लोड करें
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
```
 इस चरण में, हम उस दस्तावेज़ का पथ निर्दिष्ट करते हैं जिसके साथ हम काम करना चाहते हैं और एक दस्तावेज़ बनाना चाहते हैं`PdfLoadOptions` पीडीएफ दस्तावेज़ लोड करने के लिए ऑब्जेक्ट। फिर, हम a प्रारंभ करते हैं`Watermarker` दस्तावेज़ पथ और लोड विकल्पों के साथ ऑब्जेक्ट।
## चरण 2: पीडीएफ सामग्री प्राप्त करें
```csharp
PdfContent pdfContent = watermarker.GetContent<PdfContent>();
```
 यहां, हम इसका उपयोग करके पीडीएफ दस्तावेज़ की सामग्री प्राप्त करते हैं`GetContent<PdfContent>()` तरीका।
## चरण 3: अनुलग्नक जोड़ें
```csharp
pdfContent.Attachments.Add(File.ReadAllBytes("Your Document Path"), "sample doc", "sample doc as attachment");
```
इस चरण में पीडीएफ दस्तावेज़ में एक अनुलग्नक जोड़ना शामिल है। आपको अनुलग्नक फ़ाइल बाइट्स, नाम और विवरण प्रदान करना होगा।
## चरण 4: परिवर्तन सहेजें
```csharp
watermarker.Save(outputFileName);
```
अंत में, हम दस्तावेज़ में किए गए परिवर्तनों को अतिरिक्त अनुलग्नक के साथ सहेजते हैं।

## निष्कर्ष
.NET के लिए GroupDocs.Watermark दस्तावेज़ वॉटरमार्क और अनुलग्नकों को निर्बाध रूप से प्रबंधित करने के लिए एक मजबूत समाधान प्रदान करता है। ऊपर बताए गए चरणों का पालन करके, आप वॉटरमार्किंग और अटैचमेंट कार्यक्षमताओं को अपने .NET अनुप्रयोगों में आसानी से एकीकृत कर सकते हैं।
## अक्सर पूछे जाने वाले प्रश्न
### क्या GroupDocs.Watermark सभी .NET फ्रेमवर्क के साथ संगत है?
हाँ, GroupDocs.Watermark .NET Framework 2.0 और उच्चतर का समर्थन करता है।
### क्या मैं GroupDocs.Watermark का उपयोग करके जोड़े गए वॉटरमार्क हटा सकता हूँ?
हाँ, GroupDocs.Watermark दस्तावेज़ों से वॉटरमार्क हटाने के तरीके प्रदान करता है।
### क्या GroupDocs.Watermark दस्तावेज़ एन्क्रिप्शन का समर्थन करता है?
हाँ, GroupDocs.Watermark आपको एन्क्रिप्टेड दस्तावेज़ों के साथ काम करने की अनुमति देता है।
### क्या मैं वॉटरमार्क के स्वरूप को अनुकूलित कर सकता हूँ?
बिल्कुल, GroupDocs.Watermark वॉटरमार्क के लिए विभिन्न अनुकूलन विकल्प प्रदान करता है।
### क्या परीक्षण प्रयोजनों के लिए कोई परीक्षण संस्करण उपलब्ध है?
 हां, आप यहां से परीक्षण संस्करण तक पहुंच सकते हैं[पृष्ठ जारी करता है](https://releases.groupdocs.com/).