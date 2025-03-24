---
title: PDF のすべての添付ファイルに透かしを追加する
linktitle: PDF のすべての添付ファイルに透かしを追加する
second_title: GroupDocs.Watermark .NET API
description: GroupDocs.Watermark for .NET を使用して PDF 添付ファイルにウォーターマークを追加する方法を学びます。カスタム透かしを使用してドキュメントを簡単に保護します。
weight: 16
url: /ja/net/pdf-watermarking-attachments/add-watermark-all-attachments-pdf/
---
## 導入
PDF 添付ファイルに透かしを追加することは、ドキュメント管理において、特にセキュリティやブランド化を確保する場合に重要なステップとなります。 GroupDocs.Watermark for .NET は、PDF ファイルにウォーターマークをシームレスに埋め込むための包括的なソリューションを提供します。このチュートリアルでは、GroupDocs.Watermark for .NET を使用して、PDF ドキュメント内のすべての添付ファイルにウォーターマークを追加するプロセスを説明します。
## 前提条件
始める前に、以下のものがあることを確認してください。
1.  GroupDocs.Watermark for .NET: まだダウンロードしていない場合は、.NET 用 GroupDocs.Watermark をダウンロードしてインストールします。[Webサイト](https://releases.groupdocs.com/Watermark/net/).
2. 開発環境: Visual Studio またはその他の .NET 互換 IDE を使用して、適切な開発環境をセットアップします。
3. PDF ドキュメント: ウォーターマークを追加する PDF ドキュメントと、ウォーターマークを追加する添付ファイルを準備します。

## 名前空間のインポート
コードに入る前に、GroupDocs.Watermark for .NET 機能にアクセスするために必要な名前空間をインポートしてください。
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## ステップ 1: ドキュメントのパスと出力ディレクトリを定義する
まず、入力 PDF ドキュメントへのパスと、透かし入りドキュメントを保存するディレクトリを定義します。
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
## ステップ 2: ロード オプションとウォーターマークを初期化する
次に、PDF ドキュメントの読み込みオプションを初期化し、テキストの透かしを作成します。
```csharp
var loadOptions = new PdfLoadOptions();
TextWatermark watermark = new TextWatermark("This is WaterMark on Attachment", new Font("Arial", 19));
```
## ステップ 3: ドキュメントと添付ファイルをロードする
PDF ドキュメントをロードし、その添付ファイルを繰り返し処理します。
```csharp
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    PdfContent pdfContent = watermarker.GetContent<PdfContent>();
    foreach (PdfAttachment attachment in pdfContent.Attachments)
    {
```
## ステップ 4: 添付ファイルのサポートを確認する
添付ファイルが GroupDocs.Watermark でサポートされているかどうかを確認します。
```csharp
        IDocumentInfo info = attachment.GetDocumentInfo();
        if (info.FileType != FileType.Unknown && !info.IsEncrypted)
        {
```
## ステップ 5: 添付ファイルに透かしを追加する
添付されたドキュメントをロードし、透かしを追加します。
```csharp
            using (Watermarker attachedWatermarker = attachment.CreateWatermarker())
            {
                attachedWatermarker.Add(watermark);
                attachedWatermarker.Save();
            }
        }
    }
```
## ステップ 6: 変更を保存する
最後に、透かし入りの PDF ドキュメントへの変更を保存します。
```csharp
    watermarker.Save(outputFileName);
}
```

## 結論
このチュートリアルでは、GroupDocs.Watermark for .NET を使用して PDF ドキュメント内のすべての添付ファイルにウォーターマークを追加する方法を説明しました。ステップバイステップのガイドに従うことで、透かしを PDF ファイルにシームレスに統合し、ドキュメントのセキュリティとブランド化を確保できます。
## よくある質問
### 透かしの外観をカスタマイズできますか?
はい、要件に応じて、ウォーターマークのテキスト、フォント、サイズ、色、位置などのさまざまな側面をカスタマイズできます。
### GroupDocs.Watermark は PDF 以外のドキュメント形式をサポートしていますか?
はい。GroupDocs.Watermark は、Microsoft Word、Excel、PowerPoint、Visio、Outlook、画像などの幅広いドキュメント形式をサポートしています。
### GroupDocs.Watermark の試用版はありますか?
はい、Web サイトから無料試用版をダウンロードすることで、GroupDocs.Watermark の機能を探索できます。
### つのドキュメントに複数の透かしを追加できますか?
確かに、GroupDocs.Watermark を使用すると、テキスト、画像、注釈を含む複数のウォーターマークを同時に追加して、ドキュメントのセキュリティとブランド化を強化できます。
### GroupDocs.Watermark ユーザーはテクニカル サポートを利用できますか?
はい、GroupDocs はフォーラムや専用のサポート チャネルを通じて包括的な技術サポートを提供し、ユーザーが遭遇する可能性のある質問や問題を支援します。