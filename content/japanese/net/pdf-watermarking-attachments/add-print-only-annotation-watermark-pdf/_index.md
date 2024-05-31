---
title: 印刷専用の注釈ウォーターマークを PDF に追加
linktitle: 印刷専用の注釈ウォーターマークを PDF に追加
second_title: GroupDocs.Watermark .NET API
description: GroupDocs.Watermark for .NET を使用して、印刷専用の注釈ウォーターマークを PDF に追加する方法を学びます。ドキュメントのセキュリティとブランディングを簡単に強化します。
type: docs
weight: 13
url: /ja/net/pdf-watermarking-attachments/add-print-only-annotation-watermark-pdf/
---
## 導入
このチュートリアルでは、GroupDocs.Watermark for .NET を使用して印刷専用の注釈ウォーターマークを PDF に追加するプロセスを詳しく説明します。ドキュメントに透かしを入れることは、ドキュメントのセキュリティとブランド化の重要な側面であり、GroupDocs.Watermark は、これを実現するためのシームレスなソリューションを .NET 開発者に提供します。
## 前提条件
始める前に、次の前提条件を満たしていることを確認してください。
- C# プログラミング言語の基本的な理解。
- Visual Studio がマシンにインストールされていること。
- プロジェクトにインストールされている .NET ライブラリの GroupDocs.Watermark。

## 名前空間のインポート
まず、必要な名前空間をインポートしていることを確認してください。
```csharp
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## ステップ 1: ドキュメントをロードする
まず、透かしを入れたい PDF ドキュメントをロードする必要があります。交換する`"Your Document Path"`PDF ファイルへのパスと`"Your Document Directory"`出力ファイルを保存するディレクトリを指定します。
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    //透かしコードがここに追加されます
}
```
## ステップ 2: 透かしを追加する
次に、目的のテキストとフォントを使用してテキスト透かしオブジェクトを作成します。セット`isPrintOnly`に`true`透かしが表示モードではなく、ドキュメントの印刷時にのみ表示されるようにします。
```csharp
TextWatermark textWatermark = new TextWatermark("This is a print only test watermark. It won't appear in view mode.", new Font("Arial", 8));
bool isPrintOnly = true;
```
## ステップ 3: ウォーターマーク オプションを構成する
ウォーターマークを追加するページ インデックスや印刷専用の注釈として指定するなど、ウォーターマークのオプションを定義します。
```csharp
PdfAnnotationWatermarkOptions options = new PdfAnnotationWatermarkOptions();
options.PageIndex = 0;
options.PrintOnly = isPrintOnly;
```
## ステップ 4: ウォーターマークを適用する
指定したオプションを使用してドキュメントにウォーターマークを追加し、出力ファイルを保存します。
```csharp
watermarker.Add(textWatermark, options);
watermarker.Save(outputFileName);
```

## 結論
このチュートリアルでは、GroupDocs.Watermark for .NET を使用して PDF ドキュメントに印刷専用の注釈ウォーターマークを追加する方法を学びました。これにより、開発者はドキュメントのセキュリティとブランド化を簡単に強化できます。
## よくある質問
### GroupDocs.Watermark は PDF 以外のドキュメント形式と互換性がありますか?
はい、GroupDocs は Word、Excel、PowerPoint、画像などのさまざまなドキュメント形式をサポートしています。
### 透かしの外観をカスタマイズできますか?
確かに、GroupDocs.Watermark は、透かしのテキスト、フォント、色、サイズ、位置をカスタマイズするための広範なオプションを提供します。
### GroupDocs.Watermark はバッチ処理機能を提供しますか?
もちろん、開発者はバッチ処理機能を使用して複数のドキュメントに同時に透かしを入れることができます。
### GroupDocs.Watermark の試用版はありますか?
はい、提供されたリンクから GroupDocs.Watermark の無料試用版にアクセスできます。
### GroupDocs.Watermark のテクニカル サポートを受けるにはどうすればよいですか?
提供されているサポート リンクにある GroupDocs.Watermark フォーラムから技術サポートを求めることができます。