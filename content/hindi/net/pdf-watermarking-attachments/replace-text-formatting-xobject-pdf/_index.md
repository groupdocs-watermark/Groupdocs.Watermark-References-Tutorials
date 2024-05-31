---
title: पीडीएफ में XObject के लिए टेक्स्ट को फ़ॉर्मेटिंग से बदलें
linktitle: पीडीएफ में XObject के लिए टेक्स्ट को फ़ॉर्मेटिंग से बदलें
second_title: GroupDocs.Watermark .NET API
description: .NET के लिए वॉटरमार्क के साथ अपनी .NET दस्तावेज़ हेरफेर क्षमताओं को बढ़ाएं। पीडीएफ़ में टेक्स्ट को फ़ॉर्मेटिंग से आसानी से बदलने का तरीका जानें।
type: docs
weight: 45
url: /hi/net/pdf-watermarking-attachments/replace-text-formatting-xobject-pdf/
---
## परिचय
दस्तावेज़ हेरफेर और प्रबंधन के क्षेत्र में, .NET के लिए GroupDocs.Watermark विभिन्न दस्तावेज़ प्रारूपों के भीतर वॉटरमार्क, पाठ और छवियों में हेरफेर करने की मांग करने वाले .NET डेवलपर्स के लिए एक मजबूत समाधान के रूप में सामने आता है। यह ट्यूटोरियल इसकी शक्तिशाली विशेषताओं में से एक पर प्रकाश डालता है: पीडीएफ में XObject के लिए टेक्स्ट को फ़ॉर्मेटिंग से बदलना। इस गाइड के अंत तक, आप इस कार्यक्षमता को अपने .NET अनुप्रयोगों में निर्बाध रूप से एकीकृत करने में सक्षम होंगे।
## आवश्यक शर्तें
ट्यूटोरियल में जाने से पहले, सुनिश्चित करें कि आपके पास निम्नलिखित शर्तें हैं:
1.  .NET के लिए GroupDocs.Watermark: लाइब्रेरी को डाउनलोड और इंस्टॉल करें[लिंक को डाउनलोड करें](https://releases.groupdocs.com/Watermark/net/).
2. विकास परिवेश: एक उपयुक्त विकास परिवेश स्थापित करें, अधिमानतः विज़ुअल स्टूडियो या कोई .NET-संगत आईडीई।
3. दस्तावेज़: पीडीएफ दस्तावेज़ तैयार करें जहां आप टेक्स्ट को फ़ॉर्मेटिंग से बदलना चाहते हैं।

## नामस्थान आयात करें
अपने .NET प्रोजेक्ट में, सुनिश्चित करें कि आप GroupDocs.Watermark कार्यात्मकताओं का लाभ उठाने के लिए आवश्यक नेमस्पेस आयात करें:
```csharp
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## चरण 1: पीडीएफ दस्तावेज़ लोड करें
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
```
 सुनिश्चित करें कि आप प्रतिस्थापित करें`"Your Document Path"`अपनी पीडीएफ फ़ाइल के पथ के साथ और संशोधित दस्तावेज़ के लिए आउटपुट निर्देशिका निर्दिष्ट करें।
## चरण 2: पीडीएफ सामग्री तक पहुंचें
```csharp
    PdfContent pdfContent = watermarker.GetContent<PdfContent>();
    foreach (PdfXObject xObject in pdfContent.Pages[0].XObjects)
    {
```
 का उपयोग करें`GetContent<PdfContent>()` पीडीएफ दस्तावेज़ की सामग्री तक पहुंचने की विधि। पहले पृष्ठ के XObjects के माध्यम से पुनरावृति करें।
## चरण 3: टेक्स्ट को फ़ॉर्मेटिंग से बदलें
```csharp
        // पाठ बदलें
        if (xObject.Text.Contains("Test"))
        {
            xObject.FormattedTextFragments.Clear();
            xObject.FormattedTextFragments.Add("Passed", new Font("Calibri", 19, FontStyle.Bold), Color.Red, Color.Aqua);
        }
```
जांचें कि क्या XObject में वह टेक्स्ट है जिसे आप बदलना चाहते हैं। यदि पाया जाता है, तो मौजूदा पाठ अंशों को साफ़ करें और नया स्वरूपित पाठ जोड़ें।
## चरण 4: दस्तावेज़ सहेजें
```csharp
    // दस्तावेज़ सहेजें
    watermarker.Save(outputFileName);
}
```
संशोधित दस्तावेज़ को निर्दिष्ट आउटपुट निर्देशिका में सहेजें।

## निष्कर्ष
.NET के लिए GroupDocs.Watermark PDF दस्तावेज़ों में XObject के लिए टेक्स्ट को फ़ॉर्मेटिंग से बदलने का एक सहज तरीका प्रदान करता है। इस ट्यूटोरियल का अनुसरण करके, आपने सीखा है कि इस कार्यक्षमता को अपने .NET अनुप्रयोगों में कैसे एकीकृत किया जाए, जिससे आपकी दस्तावेज़ हेरफेर क्षमताओं में वृद्धि हो।
## अक्सर पूछे जाने वाले प्रश्न
### क्या GroupDocs.Watermark पीडीएफ के अलावा अन्य दस्तावेज़ प्रारूपों को संभाल सकता है?
हां, ग्रुपडॉक्स वर्ड, एक्सेल, पॉवरपॉइंट और अन्य सहित विभिन्न दस्तावेज़ प्रारूपों का समर्थन करता है।
### क्या GroupDocs.Watermark के लिए कोई निःशुल्क परीक्षण उपलब्ध है?
 हाँ, आप नि:शुल्क परीक्षण का उपयोग कर सकते हैं[पृष्ठ जारी करता है](https://releases.groupdocs.com/).
### क्या मैं बदले गए टेक्स्ट की फ़ॉर्मेटिंग को अनुकूलित कर सकता हूँ?
बिल्कुल, फ़ॉन्ट आकार, शैली, रंग और बहुत कुछ सहित फ़ॉर्मेटिंग पर आपका पूर्ण नियंत्रण है।
### क्या GroupDocs.Watermark तकनीकी सहायता प्रदान करता है?
 हाँ, आप तकनीकी सहायता ले सकते हैं[सहयता मंच](https://forum.groupdocs.com/c/watermark/19).
### क्या GroupDocs.Watermark व्यावसायिक उपयोग के लिए उपयुक्त है?
 हां, आप यहां से लाइसेंस खरीद सकते हैं[खरीद पृष्ठ](https://purchase.groupdocs.com/buy) व्यावसायिक उपयोग के लिए.