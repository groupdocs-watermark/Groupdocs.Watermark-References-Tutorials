---
title: PDF から透かしを削除する
linktitle: PDF から透かしを削除する
second_title: GroupDocs.Watermark .NET API
description: GroupDocs.Watermark for .NET を使用して PDF ファイルからウォーターマークを削除する方法を学びます。プロフェッショナルなドキュメント編集のための簡単な手順。
weight: 34
url: /ja/net/pdf-watermarking-attachments/remove-watermark-pdf/
---
## 導入
今日のデジタル時代では、機密文書を透かしで保護するのが一般的です。ただし、さまざまな理由により、PDF ファイルからウォーターマークを削除する必要がある場合があります。ドキュメントを編集している場合でも、単にプレゼンテーション用にクリーンなバージョンが必要な場合でも、GroupDocs.Watermark for .NET は PDF ファイルからウォーターマークを削除するためのシームレスなソリューションを提供します。
## 前提条件
GroupDocs.Watermark for .NET を使用して PDF ファイルからウォーターマークを削除する前に、次の前提条件を満たしていることを確認してください。
1.  GroupDocs.Watermark for .NET ライブラリ: からライブラリをダウンロードしてインストールします。[ここ](https://releases.groupdocs.com/Watermark/net/).
2. 開発環境: Visual Studio または互換性のある IDE がシステムにインストールされています。
3. 透かしのある文書: 削除したい透かしを含む PDF 文書を準備します。

## 名前空間のインポート
C# プロジェクトで、必要な名前空間をインポートすることから始めます。
```csharp
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Search;
using GroupDocs.Watermark.Search.SearchCriteria;
using System.IO;
using System;
```
## ステップ 1: PDF ドキュメントをロードする
```csharp
string documentPath = "YourDocumentPath.pdf";
string outputDirectory = "YourOutputDirectory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
var loadOptions = new PdfLoadOptions();
```
このステップでは、PDF ドキュメントへのパスと出力ファイルを保存するディレクトリを指定します。
## ステップ 2: ウォーターマーカーと検索基準を初期化する
```csharp
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    ImageSearchCriteria imageSearchCriteria = new ImageDctHashSearchCriteria(Constants.LogoPng);
    TextSearchCriteria textSearchCriteria = new TextSearchCriteria("Company Name");
```
PDF ドキュメントのパスとロード オプションを使用してウォーターマーカー オブジェクトを初期化します。次に、削除するウォーターマークの検索条件を定義します。画像またはテキストに基づいてウォーターマークを検索できます。
## ステップ 3: ウォーターマークを検索して削除する
```csharp
    PdfContent pdfContent = watermarker.GetContent<PdfContent>();
    PossibleWatermarkCollection possibleWatermarks = pdfContent.Pages[0].Search(imageSearchCriteria.Or(textSearchCriteria));
    //見つかったすべてのウォーターマークを削除します
    for (int i = possibleWatermarks.Count - 1; i >= 0; i--)
    {
        possibleWatermarks.RemoveAt(i);
    }
    watermarker.Save(outputFileName);
}
```
定義された検索基準に基づいて、PDF ドキュメントの最初のページで透かしの可能性があるものを検索します。次に、考えられるウォーターマークのコレクションを繰り返し処理し、それらを 1 つずつ削除します。最後に、変更した PDF ドキュメントを透かしなしで保存します。

## 結論
PDF ファイルからウォーターマークを削除することは、文書編集からプレゼンテーションの準備まで、さまざまなシナリオにおいて重要な作業です。 GroupDocs.Watermark for .NET を使用すると、簡単な C# コードを使用して PDF ファイルからウォーターマークを簡単に削除でき、ドキュメントをクリーンでプロフェッショナルなものにすることができます。
## よくある質問
### GroupDocs.Watermark for .NET は Visual Studio のすべてのバージョンと互換性がありますか?
はい。GroupDocs.Watermark for .NET は、Visual Studio 2019 および Visual Studio 2022 を含む、Visual Studio のすべてのバージョンと互換性があります。
### GroupDocs.Watermark for .NET を使用して、単一の PDF ドキュメントから複数のウォーターマークを削除できますか?
はい、適切な検索条件を指定することで、1 つの PDF ドキュメントから複数のウォーターマークを検索して削除できます。
### GroupDocs.Watermark for .NET は PDF 以外のドキュメント形式をサポートしていますか?
はい、GroupDocs.Watermark for .NET は、Word ドキュメント、Excel スプレッドシート、PowerPoint プレゼンテーションなどを含む幅広いドキュメント形式をサポートしています。
### GroupDocs.Watermark for .NET の試用版はありますか?
はい、GroupDocs.Watermark for .NET の無料試用版を次のサイトからダウンロードできます。[ここ](https://releases.groupdocs.com/).
### GroupDocs.Watermark for .NET の追加のサポートと支援はどこで入手できますか?
追加のサポートが必要な場合は、GroupDocs.Watermark フォーラムにアクセスしてください。[ここ](https://forum.groupdocs.com/c/watermark/19).