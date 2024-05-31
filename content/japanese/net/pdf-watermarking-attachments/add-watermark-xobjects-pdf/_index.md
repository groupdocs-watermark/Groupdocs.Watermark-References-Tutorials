---
title: PDF の XObject にウォーターマークを追加する
linktitle: PDF の XObject にウォーターマークを追加する
second_title: GroupDocs.Watermark .NET API
description: Groupdocs.Watermark for .NET を使用して PDF の XObject にウォーターマークを追加する方法を学びます。簡単に実装するには、ステップバイステップのガイドに従ってください。
type: docs
weight: 20
url: /ja/net/pdf-watermarking-attachments/add-watermark-xobjects-pdf/
---
## 導入
PDF に透かしを入れることは、ドキュメントを不正使用から確実に保護するための重要な手順です。 Groupdocs.Watermark for .NET を使用すると、PDF 内の XObject にウォーターマークを追加することがこれまでになく簡単になります。このチュートリアルでは、プロセスを段階的に説明し、PDF ドキュメントに自信を持って透かしを適用できるようにします。始めましょう！
## 前提条件
チュートリアルに入る前に、スムーズに進めるために必要なものがすべて揃っていることを確認してください。
-  Groupdocs.Watermark for .NET: 最新バージョンを次からダウンロードしてインストールします。[ここ](https://releases.groupdocs.com/Watermark/net/).
- .NET Framework: 開発マシンに .NET Framework がインストールされていることを確認してください。
- 開発環境: Visual Studio または .NET 開発をサポートするその他の IDE を使用します。
- 一時ライセンス: を取得します。[仮免許証](https://purchase.groupdocs.com/temporary-license/)製品を評価している場合。
これらの前提条件を満たしたら、PDF に透かしを入れる準備が整います。
## 名前空間のインポート
まず、必要な名前空間をプロジェクトにインポートする必要があります。 C# プロジェクトを開き、次の using ディレクティブを追加します。
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## ステップ 1: ドキュメント パスを設定する
最初のステップでは、ドキュメントのパスを設定します。 PDF が存在する場所と、透かし入りの PDF を保存する場所のパスを定義します。
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
交換する`"Your Document Path"`そして`"Your Document Directory"`マシン上の実際のパスを使用します。
## ステップ 2: PDF ロード オプションを初期化する
次に、PDF 読み込みオプションを初期化する必要があります。これは、PDF コンテンツを正しくロードするために重要です。
```csharp
var loadOptions = new PdfLoadOptions();
```
## ステップ 3: PDF ドキュメントをロードする
ロード オプションを使用して、PDF ドキュメントをロードします。`Watermarker`クラス。
```csharp
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    PdfContent pdfContent = watermarker.GetContent<PdfContent>();
```
## ステップ 4: ウォーターマークを作成する
ここで、PDF に追加されるウォーターマークを作成する必要があります。このチュートリアルでは、テキストの透かしを作成します。
```csharp
TextWatermark watermark = new TextWatermark("Protected image", new Font("Arial", 8))
{
    HorizontalAlignment = HorizontalAlignment.Center,
    VerticalAlignment = VerticalAlignment.Center,
    RotateAngle = 45,
    SizingType = SizingType.ScaleToParentDimensions,
    ScaleFactor = 1
};
```
## ステップ 5: XObject にウォーターマークを追加する
PDF 内の各ページと各 XObject を繰り返し処理して、ウォーターマークを適用します。
```csharp
foreach (PdfPage page in pdfContent.Pages)
{
    foreach (PdfXObject xObject in page.XObjects)
    {
        if (xObject.Image != null)
        {
            //画像に透かしを追加する
            xObject.Image.Add(watermark);
        }
    }
}
```
## ステップ 6: 透かし入り PDF を保存する
最後に、透かしを入れた PDF を指定した出力ファイルに保存します。
```csharp
    watermarker.Save(outputFileName);
}
```
そして、それができました！ PDF のすべての XObject に透かしが含まれるようになりました。
## 結論
 Groupdocs for .NET を使用して PDF ドキュメントにウォーターマークを追加することは、追加のセキュリティ層を提供する簡単なプロセスです。このチュートリアルで概説されている手順に従うことで、ドキュメントを不正使用から確実に保護できます。いつでも参照できることを覚えておいてください。[ドキュメンテーション](https://reference.groupdocs.com/Watermark/net/)より詳細な情報と高度な機能については、
## よくある質問
### テキストの代わりに画像を透かしとして使用できますか?
はい、Groupdocs.Watermark for .NET はテキストと画像の両方のウォーターマークをサポートしています。
### Groupdocs.Watermark を購入せずにテストするにはどうすればよいですか?
を使用できます[仮免許証](https://purchase.groupdocs.com/temporary-license/)製品を評価するため。
### 透かしの外観をカスタマイズすることはできますか?
絶対に！フォント、サイズ、回転角度などをカスタマイズできます。
### Groupdocs.Watermark は他のドキュメント形式をサポートしていますか?
はい、Word、Excel、PowerPoint などのさまざまな形式をサポートしています。
### 問題が発生した場合はどこでサポートを受けられますか?
からサポートを受けることができます。[グループドキュメントフォーラム](https://forum.groupdocs.com/c/watermark/19).