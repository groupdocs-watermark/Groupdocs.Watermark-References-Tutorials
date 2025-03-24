---
title: वर्ड डॉक्स में अलग-अलग प्रथम पृष्ठ शीर्षलेख/पादलेख सेट करें
linktitle: वर्ड डॉक्स में अलग-अलग प्रथम पृष्ठ शीर्षलेख/पादलेख सेट करें
second_title: GroupDocs.Watermark .NET API
description: .NET के लिए GroupDocs.Watermark का उपयोग करके Word दस्तावेज़ों के पहले पृष्ठ पर विभिन्न शीर्षलेख और पादलेख सेट करना सीखें।
weight: 36
url: /hi/net/word-processing-watermarkings/set-different-first-page-header-footer-word-docs/
---

# वर्ड डॉक्स में अलग-अलग प्रथम पृष्ठ शीर्षलेख/पादलेख सेट करें

## परिचय
दस्तावेज़ प्रबंधन और हेरफेर के क्षेत्र में, .NET के लिए GroupDocs.Watermark एक शक्तिशाली उपकरण के रूप में उभरता है, जो वॉटरमार्किंग दस्तावेज़ों के लिए निर्बाध एकीकरण और मजबूत कार्यक्षमता प्रदान करता है। दस्तावेज़ प्रसंस्करण में सामान्य आवश्यकताओं में से एक Word दस्तावेज़ों के पहले पृष्ठ पर अलग-अलग शीर्षलेख और पादलेख सेट करना है। यह ट्यूटोरियल .NET के लिए GroupDocs.Watermark का उपयोग करके इस कार्य को प्राप्त करने की प्रक्रिया को स्पष्ट करेगा, प्रत्येक चरण को आसानी से समझने योग्य खंडों में विभाजित करेगा।
## आवश्यक शर्तें
कार्यान्वयन में उतरने से पहले, सुनिश्चित करें कि निम्नलिखित शर्तें पूरी हो गई हैं:
1.  .NET के लिए GroupDocs.Watermark की स्थापना: .NET के लिए GroupDocs.Watermark को डाउनलोड और इंस्टॉल करें।[लिंक को डाउनलोड करें](https://releases.groupdocs.com/Watermark/net/).
2. दस्तावेज़ तैयार करना: एक वर्ड दस्तावेज़ तैयार रखें जिसके पहले पृष्ठ पर विभिन्न शीर्षलेख और पादलेख की सेटिंग की आवश्यकता होती है।

## नामस्थान आयात करें
आरंभ करने के लिए, .NET कार्यात्मकताओं के लिए GroupDocs.Watermark का उपयोग करने के लिए आवश्यक आवश्यक नामस्थान आयात करें:
```csharp
using GroupDocs.Watermark.Contents.WordProcessing;
using GroupDocs.Watermark.Options.WordProcessing;
using System.IO;
using System;
```
## चरण 1: दस्तावेज़ लोड करें
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
```
इस चरण में, हम उस दस्तावेज़ के पथ को परिभाषित करते हैं जिसे संसाधित करने की आवश्यकता है और आउटपुट फ़ाइल नाम और निर्देशिका निर्दिष्ट करते हैं। इसके अतिरिक्त, हम a आरंभ करते हैं`Watermarker` दस्तावेज़ पथ और लोड विकल्पों के साथ ऑब्जेक्ट।
## चरण 2: दस्तावेज़ सामग्री तक पहुँचें
```csharp
WordProcessingContent content = watermarker.GetContent<WordProcessingContent>();
```
 यहां, हम इसका उपयोग करके वर्ड दस्तावेज़ की सामग्री को पुनः प्राप्त करते हैं`GetContent<T>()` की विधि`Watermarker` ऑब्जेक्ट, सामग्री के प्रकार को निर्दिष्ट करता है`WordProcessingContent`.
## चरण 3: पेज सेटअप कॉन्फ़िगर करें
```csharp
content.Sections[0].PageSetup.DifferentFirstPageHeaderFooter = true;
content.Sections[0].PageSetup.OddAndEvenPagesHeaderFooter = true;
```
इस चरण में, हम पहले पृष्ठ के लिए अलग-अलग शीर्षलेख और पादलेख सक्षम करने के लिए पृष्ठ सेटअप विकल्पों को कॉन्फ़िगर करते हैं (`DifferentFirstPageHeaderFooter`) साथ ही विषम और सम पृष्ठों के लिए (`OddAndEvenPagesHeaderFooter`).
## चरण 4: परिवर्तन सहेजें
```csharp
watermarker.Save(outputFileName);
```
 अंत में, हम दस्तावेज़ में किए गए संशोधनों को कॉल करके सहेजते हैं`Save()` की विधि`Watermarker` ऑब्जेक्ट, आउटपुट फ़ाइल नाम पास करना।

## निष्कर्ष
.NET के लिए GroupDocs.Watermark Word दस्तावेज़ों के पहले पृष्ठ पर विभिन्न शीर्षलेख और पादलेख सेट करने के लिए एक सीधा समाधान प्रदान करता है। इस ट्यूटोरियल में बताए गए चरणों का पालन करके, उपयोगकर्ता अपनी आवश्यकताओं के अनुसार दस्तावेज़ सामग्री में आसानी से हेरफेर कर सकते हैं।
## अक्सर पूछे जाने वाले प्रश्न
### क्या .NET के लिए GroupDocs.Watermark Word के अलावा अन्य दस्तावेज़ प्रारूपों को संभाल सकता है?
हाँ, .NET के लिए GroupDocs.Watermark PDF, Excel, PowerPoint और अन्य सहित दस्तावेज़ स्वरूपों की एक विस्तृत श्रृंखला का समर्थन करता है।
### क्या परीक्षण प्रयोजनों के लिए कोई परीक्षण संस्करण उपलब्ध है?
हाँ, उपयोगकर्ता .NET के लिए GroupDocs.Watermark का निःशुल्क परीक्षण प्राप्त कर सकते हैं[पृष्ठ जारी करता है](https://releases.groupdocs.com/).
### क्या .NET के लिए GroupDocs.Watermark तकनीकी सहायता प्रदान करता है?
 हाँ, .NET के लिए GroupDocs के लिए तकनीकी सहायता उपलब्ध है[सहयता मंच](https://forum.groupdocs.com/c/watermark/19).
### क्या मैं अल्पकालिक उपयोग के लिए अस्थायी लाइसेंस खरीद सकता हूँ?
 हाँ, .NET के लिए GroupDocs के लिए अस्थायी लाइसेंस प्राप्त किया जा सकता है[अस्थायी लाइसेंस खरीद पृष्ठ](https://purchase.groupdocs.com/temporary-license/).
### मुझे .NET के लिए GroupDocs.Watermark के लिए व्यापक दस्तावेज़ कहाँ मिल सकते हैं?
 .NET के लिए GroupDocs.Watermark का विस्तृत दस्तावेज़ यहां उपलब्ध है[संदर्भ पृष्ठ](https://tutorials.groupdocs.com/Watermark/net/).