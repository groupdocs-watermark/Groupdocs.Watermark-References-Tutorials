---
title: PDF にページ余白タイプのウォーターマークを追加する
linktitle: PDF にページ余白タイプのウォーターマークを追加する
second_title: GroupDocs.Watermark .NET API
description: Groupdocs for .NET を使用して、PDF にページ余白タイプのウォーターマークを追加する方法を説明します。書類を簡単に保護します。
type: docs
weight: 21
url: /ja/net/pdf-watermarking-attachments/add-watermark-page-margin-type-pdf/
---
## 導入
今日のデジタル時代では、文書の安全性がこれまで以上に重要になっています。ドキュメントの完全性と信頼性を保証する 1 つの方法は、透かしを追加することです。 Groupdocs.Watermark for .NET は、このプロセスを簡単にするために設計された優れたツールです。このチュートリアルでは、Groupdocs.Watermark for .NET を使用して PDF にページ余白タイプのウォーターマークを追加する手順を説明します。
## 前提条件
チュートリアルに入る前に、次の前提条件が満たされていることを確認してください。
-  Groupdocs.Watermark for .NET: ダウンロードしてインストールします。[最新バージョン](https://releases.groupdocs.com/Watermark/net/).NET 用の Groupdocs.Watermark の。
- 開発環境: Visual Studio のような .NET 開発環境。
- C# の基本的な知識: C# プログラミング言語に精通していること。
- PDF ドキュメント: 透かしを追加する PDF ドキュメント。
## 名前空間のインポート
まず、必要な名前空間を C# プロジェクトにインポートする必要があります。これらの名前空間は、Groupdocs 機能へのアクセスを提供します。
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
次に、プロセスを管理可能なステップに分割してみましょう。各手順を慎重に実行して、PDF ドキュメントに透かしを追加します。
## ステップ 1: ドキュメントのパスと出力ディレクトリを設定する
まず、ドキュメントへのパスと、透かし入り PDF が保存される出力ディレクトリを指定する必要があります。
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
## ステップ 2: PDF ドキュメントをロードする
次に、次のコマンドを使用して PDF ドキュメントを読み込みます。`PdfLoadOptions`クラス。このクラスを使用すると、PDF のロードに必要なオプションを指定できます。
```csharp
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
```
## ステップ 3: テキストの透かしを作成する
次に、ウォーターマークを作成します。この例では、フォント、サイズ、配置などの特定のプロパティを使用してテキスト透かしを作成します。
```csharp
TextWatermark watermark = new TextWatermark("Test watermark", new Font("Arial", 42));
watermark.HorizontalAlignment = HorizontalAlignment.Right;
watermark.VerticalAlignment = VerticalAlignment.Top;
watermark.SizingType = SizingType.ScaleToParentDimensions;
watermark.ScaleFactor = 1;
```
## ステップ 4: ページ余白のタイプを設定する
ウォーターマークを適切に配置するには、ページ余白のタイプを設定する必要があります。ここでは、ページマージンのタイプを次のように設定します。`BleedBox`.
```csharp
PdfContent pdfContent = watermarker.GetContent<PdfContent>();
pdfContent.PageMarginType = PdfPageMarginType.BleedBox;
watermark.ConsiderParentMargins = true;
```
## ステップ 5: ウォーターマークを追加して保存する
最後に、文書に透かしを追加し、変更した PDF を指定した出力ディレクトリに保存します。
```csharp
watermarker.Add(watermark);
watermarker.Save(outputFileName);
}
```
## 結論
そして、それができました！これらの手順に従うと、Groupdocs.Watermark for .NET を使用して、特定のページ余白タイプのウォーターマークを PDF ドキュメントに簡単に追加できます。これは、文書を保護するだけでなく、文書の信頼性を保証するのにも役立ちます。機密報告書、法的文書、またはクリエイティブな作品を扱う場合でも、透かしはコンテンツを保護するためのシンプルかつ効果的な方法です。
## よくある質問
### .NET 用の Groupdocs.Watermark とは何ですか?
Groupdocs.Watermark for .NET は、プログラムによってさまざまなドキュメント形式にウォーターマークを追加するための強力なライブラリです。画像やテキストなどをサポートしており、広範なカスタマイズが可能です。
### この方法を使用して他の種類のドキュメントに透かしを入れることはできますか?
はい。Groupdocs.Watermark for .NET は、Word、Excel、PowerPoint、画像などの幅広いドキュメント形式をサポートしています。プロセスは似ていますが、異なるオプションやクラスが含まれる場合があります。
### Groupdocs.Watermark for .NET の無料トライアルを入手するにはどうすればよいですか?
あなたはできる[無料トライアルをダウンロードする](https://releases.groupdocs.com/)Groupdocs Web サイトからアクセスして、ライブラリの特徴と機能を調べてください。
### 透かしの外観をカスタマイズすることはできますか?
絶対に！ニーズに合わせて、ウォーターマークのフォント、サイズ、色、不透明度、配置、その他のプロパティをカスタマイズできます。
### Groupdocs.Watermark for .NET のサポートはどこで入手できますか?
サポートが必要な場合は、次のサイトにアクセスしてください。[Groupdocs ウォーターマーク サポート フォーラム](https://forum.groupdocs.com/c/watermark/19)ここでは、質問したり、コミュニティや Groupdocs チームから支援を受けることができます。