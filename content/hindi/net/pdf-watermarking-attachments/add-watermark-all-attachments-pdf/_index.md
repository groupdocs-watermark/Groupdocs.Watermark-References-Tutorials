---
title: पीडीएफ में सभी अनुलग्नकों में वॉटरमार्क जोड़ें
linktitle: पीडीएफ में सभी अनुलग्नकों में वॉटरमार्क जोड़ें
second_title: GroupDocs.Watermark .NET API
description: .NET के लिए GroupDocs.Watermark का उपयोग करके PDF अनुलग्नकों में वॉटरमार्क जोड़ने का तरीका जानें। अपने दस्तावेज़ों को कस्टम वॉटरमार्क से आसानी से सुरक्षित करें।
weight: 16
url: /hi/net/pdf-watermarking-attachments/add-watermark-all-attachments-pdf/
---
## परिचय
पीडीएफ अनुलग्नकों में वॉटरमार्क जोड़ना दस्तावेज़ प्रबंधन में एक महत्वपूर्ण कदम हो सकता है, खासकर सुरक्षा या ब्रांडिंग सुनिश्चित करते समय। .NET के लिए GroupDocs.Watermark पीडीएफ फाइलों में वॉटरमार्क को निर्बाध रूप से एम्बेड करने के लिए एक व्यापक समाधान प्रदान करता है। इस ट्यूटोरियल में, हम .NET के लिए GroupDocs.Watermark का उपयोग करके एक पीडीएफ दस्तावेज़ के भीतर सभी अनुलग्नकों में वॉटरमार्क जोड़ने की प्रक्रिया में आपका मार्गदर्शन करेंगे।
## आवश्यक शर्तें
शुरू करने से पहले, सुनिश्चित करें कि आपके पास निम्नलिखित हैं:
1.  .NET के लिए GroupDocs.Watermark: यदि आपने पहले से नहीं किया है, तो .NET के लिए GroupDocs.Watermark को डाउनलोड और इंस्टॉल करें।[वेबसाइट](https://releases.groupdocs.com/Watermark/net/).
2. विकास वातावरण: विजुअल स्टूडियो या किसी अन्य .NET-संगत आईडीई के साथ एक उपयुक्त विकास वातावरण स्थापित करें।
3. पीडीएफ दस्तावेज़: पीडीएफ दस्तावेज़ तैयार करें जिसमें आप वॉटरमार्क जोड़ना चाहते हैं, साथ ही उन अनुलग्नकों के साथ जिन्हें आप वॉटरमार्क करना चाहते हैं।

## नामस्थान आयात करना
कोड में गोता लगाने से पहले, .NET कार्यात्मकताओं के लिए GroupDocs.Watermark तक पहुँचने के लिए आवश्यक नामस्थान आयात करना सुनिश्चित करें:
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## चरण 1: दस्तावेज़ पथ और आउटपुट निर्देशिका को परिभाषित करें
सबसे पहले, अपने इनपुट पीडीएफ दस्तावेज़ का पथ और उस निर्देशिका को परिभाषित करें जहां वॉटरमार्क दस्तावेज़ सहेजा जाएगा:
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
## चरण 2: लोड विकल्प और वॉटरमार्क प्रारंभ करें
इसके बाद, पीडीएफ दस्तावेज़ के लिए लोड विकल्प आरंभ करें और एक टेक्स्ट वॉटरमार्क बनाएं:
```csharp
var loadOptions = new PdfLoadOptions();
TextWatermark watermark = new TextWatermark("This is WaterMark on Attachment", new Font("Arial", 19));
```
## चरण 3: दस्तावेज़ और अनुलग्नक लोड करें
पीडीएफ दस्तावेज़ को लोड करें और उसके अनुलग्नकों के माध्यम से पुनरावृत्त करें:
```csharp
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    PdfContent pdfContent = watermarker.GetContent<PdfContent>();
    foreach (PdfAttachment attachment in pdfContent.Attachments)
    {
```
## चरण 4: अनुलग्नक समर्थन की जाँच करें
जांचें कि क्या संलग्न फ़ाइल GroupDocs.Watermark द्वारा समर्थित है:
```csharp
        IDocumentInfo info = attachment.GetDocumentInfo();
        if (info.FileType != FileType.Unknown && !info.IsEncrypted)
        {
```
## चरण 5: अनुलग्नकों में वॉटरमार्क जोड़ें
संलग्न दस्तावेज़ लोड करें और वॉटरमार्क जोड़ें:
```csharp
            using (Watermarker attachedWatermarker = attachment.CreateWatermarker())
            {
                attachedWatermarker.Add(watermark);
                attachedWatermarker.Save();
            }
        }
    }
```
## चरण 6: परिवर्तन सहेजें
अंत में, वॉटरमार्क वाले पीडीएफ दस्तावेज़ में परिवर्तन सहेजें:
```csharp
    watermarker.Save(outputFileName);
}
```

## निष्कर्ष
इस ट्यूटोरियल में, हमने पता लगाया है कि .NET के लिए GroupDocs.Watermark का उपयोग करके पीडीएफ दस्तावेज़ के सभी अनुलग्नकों में वॉटरमार्क कैसे जोड़ें। चरण-दर-चरण मार्गदर्शिका का पालन करके, आप दस्तावेज़ सुरक्षा और ब्रांडिंग सुनिश्चित करते हुए वॉटरमार्क को अपनी पीडीएफ फाइलों में सहजता से एकीकृत कर सकते हैं।
## अक्सर पूछे जाने वाले प्रश्न
### क्या मैं वॉटरमार्क के स्वरूप को अनुकूलित कर सकता हूँ?
हां, आप अपनी आवश्यकताओं के अनुसार टेक्स्ट, फ़ॉन्ट, आकार, रंग और वॉटरमार्क की स्थिति जैसे विभिन्न पहलुओं को अनुकूलित कर सकते हैं।
### क्या GroupDocs.Watermark पीडीएफ के अलावा अन्य दस्तावेज़ प्रारूपों का समर्थन करता है?
हाँ, GroupDocs.Watermark Microsoft Word, Excel, PowerPoint, Visio, Outlook और Images सहित दस्तावेज़ स्वरूपों की एक विस्तृत श्रृंखला का समर्थन करता है।
### क्या GroupDocs.Watermark के लिए कोई परीक्षण संस्करण उपलब्ध है?
हां, आप वेबसाइट से निःशुल्क परीक्षण संस्करण डाउनलोड करके GroupDocs.Watermark की सुविधाओं का पता लगा सकते हैं।
### क्या मैं एक ही दस्तावेज़ में एकाधिक वॉटरमार्क जोड़ सकता हूँ?
बिल्कुल, GroupDocs.Watermark आपको दस्तावेज़ सुरक्षा और ब्रांडिंग को बढ़ाने के लिए एक साथ टेक्स्ट, छवि और एनोटेशन सहित कई वॉटरमार्क जोड़ने की अनुमति देता है।
### क्या GroupDocs.Watermark उपयोगकर्ताओं के लिए तकनीकी सहायता उपलब्ध है?
हां, ग्रुपडॉक्स उपयोगकर्ताओं को उनके सामने आने वाले किसी भी प्रश्न या समस्या में सहायता करने के लिए मंचों और समर्पित समर्थन चैनलों के माध्यम से व्यापक तकनीकी सहायता प्रदान करता है।