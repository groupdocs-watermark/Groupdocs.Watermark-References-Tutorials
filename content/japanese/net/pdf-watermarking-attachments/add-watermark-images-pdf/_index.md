---
title: PDF の画像に透かしを追加する
linktitle: PDF の画像に透かしを追加する
second_title: GroupDocs.Watermark .NET API
description: 詳細なステップバイステップのチュートリアルで、GroupDocs.Watermark for .NET を使用して PDF ドキュメント内の画像にウォーターマークを追加する方法を学びます。 PDF を簡単に保護します。
type: docs
weight: 19
url: /ja/net/pdf-watermarking-attachments/add-watermark-images-pdf/
---
## 導入
PDF ドキュメント内の画像に透かしを追加することは、知的財産を保護したり、ドキュメントの信頼性を確保したりするために不可欠です。 GroupDocs.Watermark for .NET を使用すると、このタスクを効率的かつ簡単に実行できます。このチュートリアルでは、環境のセットアップからウォーターマークの追加、最終ドキュメントの保存まで、プロセスの各ステップを説明します。飛び込んでみましょう！
## 前提条件
始める前に、以下のものがあることを確認してください。
1. Visual Studio: .NET アプリケーション用の統合開発環境 (IDE) である Visual Studio をインストールします。
2.  GroupDocs.Watermark for .NET: GroupDocs.Watermark for .NET ライブラリを次の場所からダウンロードしてインストールします。[リリースページ](https://releases.groupdocs.com/Watermark/net/).
3. PDF ドキュメント: 透かし機能をテストできるように、画像を含む PDF ドキュメントを用意します。
4. 一時ライセンス: を取得します。[仮免許証](https://purchase.groupdocs.com/temporary-license/)製品を評価している場合。
## 名前空間のインポート
まず、必要な名前空間がプロジェクトにインポートされていることを確認します。これには、PDF ドキュメントとウォーターマークを操作するために必要なコアの名前空間が含まれます。
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.Image;
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## ステップ 1: ドキュメントのパスと出力ディレクトリを設定する
まず、入力ドキュメントのパスと、透かし入りドキュメントが保存される出力ディレクトリを定義します。このステップは、プログラムがソース文書の場所と処理されたファイルの保存場所を確実に認識するために重要です。
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
## ステップ 2: PDF ドキュメントをロードする
次に、次を使用して PDF ドキュメントをロードする必要があります。`PdfLoadOptions`。このクラスを使用すると、必要に応じてパスワード保護など、PDF をロードするためのオプションを指定できます。
```csharp
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    //透かしのコードはここに入力されます
}
```
## ステップ 3: ウォーターマークを作成する
次に、ウォーターマークを初期化します。この例では、「保護された画像」というテキストの透かしを作成しています。ニーズに応じてフォント、配置、回転、拡大縮小をカスタマイズします。
```csharp
TextWatermark watermark = new TextWatermark("Protected image", new Font("Arial", 8));
watermark.HorizontalAlignment = HorizontalAlignment.Center;
watermark.VerticalAlignment = VerticalAlignment.Center;
watermark.RotateAngle = 45;
watermark.SizingType = SizingType.ScaleToParentDimensions;
watermark.ScaleFactor = 1;
```
## ステップ 4: PDF コンテンツにアクセスする
PDF ドキュメントのコンテンツを取得します。具体的には、PDF 内の画像にアクセスする必要があります。ここでは最初のページに焦点を当てていますが、必要に応じてこれを他のページに拡張できます。
```csharp
PdfContent pdfContent = watermarker.GetContent<PdfContent>();
//最初のページからすべての画像を取得します
WatermarkableImageCollection images = pdfContent.Pages[0].FindImages();
```
## ステップ 5: 画像に透かしを適用する
最初のページで見つかった各画像をループし、透かしを適用します。これにより、指定したページ上のすべての画像にウォーターマークが適用されます。
```csharp
//見つかったすべての画像に透かしを追加します
foreach (WatermarkableImage image in images)
{
    image.Add(watermark);
}
```
## ステップ 6: 透かし入りのドキュメントを保存する
最後に、透かし入りの PDF を指定した出力ディレクトリに保存します。このステップでは、変更を新しいファイルに書き込むことでプロセスを終了します。
```csharp
watermarker.Save(outputFileName);
```
## 結論
そして、それができました！ GroupDocs Watermark for .NET を使用して PDF 内の画像にウォーターマークを追加することは、ドキュメントのセキュリティと信頼性を大幅に強化できる簡単なプロセスです。これらの手順に従うことで、知的財産が保護され、ドキュメントが安全であることを確認できます。
## よくある質問
### .NET 用の GroupDocs.Watermark とは何ですか?
GroupDocs.Watermark for .NET は、開発者が PDF を含むさまざまなドキュメント形式でウォーターマークを追加、検索、削除できるようにする包括的なライブラリです。
### GroupDocs.Watermark を使用してテキストと画像の両方の透かしを追加できますか?
はい、GroupDocs.Watermark はテキストと画像の両方の透かしをサポートしており、さまざまな種類の透かしニーズに柔軟に対応できます。
### PDF 内の複数のページに透かしを入れることはできますか?
絶対に！ PDF の各ページをループして、各ページの画像に透かしを適用できます。
### GroupDocs.Watermark for .NET を使用するにはライセンスが必要ですか?
はい、ライセンスが必要です。を取得できます。[仮免許証](https://purchase.groupdocs.com/temporary-license/)評価目的のため。
### GroupDocs.Watermark for .NET に関するその他のドキュメントはどこで見つけられますか?
包括的なドキュメントは、[GroupDocs.Watermark ドキュメント ページ](https://reference.groupdocs.com/Watermark/net/).