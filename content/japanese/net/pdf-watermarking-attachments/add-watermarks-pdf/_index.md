---
title: PDF に透かしを追加する
linktitle: PDF に透かしを追加する
second_title: GroupDocs.Watermark .NET API
description: 包括的なステップバイステップ ガイドで、GroupDocs.Watermark for .NET を使用して PDF にテキストと画像の透かしを追加する方法を学びます。
weight: 14
url: /ja/net/pdf-watermarking-attachments/add-watermarks-pdf/
type: docs
---
# PDF に透かしを追加する

## 導入
PDF に透かしを追加して文書を保護したり、ロゴをブランド化したいと考えていますか?これ以上探さない！このチュートリアルでは、GroupDocs.Watermark for .NET を使用してテキストと画像の両方のウォーターマークを PDF ファイルに追加するプロセスについて詳しく説明します。経験豊富な開発者でも、初心者でも、このガイドでは各ステップを順を追って説明し、ウォーターマークを簡単かつ正確に適用できるようにします。
## 前提条件
始める前に、このチュートリアルに従うために必要なものがすべて揃っていることを確認してください。
-  GroupDocs.Watermark for .NET: 最新バージョンがインストールされていることを確認してください。あなたはできる[ここからダウンロードしてください](https://releases.groupdocs.com/Watermark/net/).
- .NET 開発環境: Visual Studio または .NET をサポートするその他の IDE。
- C# の基本知識: C# プログラミングの基本を理解すると、手順を簡単に進めることができます。
- PDF ドキュメント: 透かしを入れるためのサンプル PDF ドキュメントを用意します。
- ウォーターマーク用の画像: 画像のウォーターマークを追加する場合は、画像ファイルを用意してください。
## 名前空間のインポート
まず、必要な名前空間を C# プロジェクトにインポートする必要があります。これにより、GroupDocs.Watermark 機能にアクセスできるようになります。
```csharp
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
次に、プロセスを管理可能なステップに分割してみましょう。
## ステップ 1: PDF ドキュメントをロードする
最初のステップは、PDF ドキュメントをウォーターマーカーにロードすることです。その方法は次のとおりです。
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    //ここにさらに手順が追加されます
}
```
## ステップ 2: 最初のページにテキストの透かしを追加する
次に、PDF の最初のページにテキストの透かしを追加します。次の指示に従ってください。
```csharp
//最初のページにテキストの透かしを追加する
TextWatermark textWatermark = new TextWatermark("This is a test watermark", new Font("Arial", 8));
PdfArtifactWatermarkOptions textWatermarkOptions = new PdfArtifactWatermarkOptions();
textWatermarkOptions.PageIndex = 0;
watermarker.Add(textWatermark, textWatermarkOptions);
```

テキストの透かしを追加すると、ドキュメントを不正使用から保護したり、単にブランド化したりするのに役立ちます。本物であることを証明する目に見えないシールを書類に押すことを想像してみてください。
## ステップ 3: 2 ページ目に画像の透かしを追加する
次に、2 ページ目に画像の透かしを追加してみましょう。これは、ロゴやグラフィック透かしに特に役立ちます。
```csharp
// 2 ページ目に画像の透かしを追加する
using (ImageWatermark imageWatermark = new ImageWatermark("Your Image Path"))
{
    PdfArtifactWatermarkOptions imageWatermarkOptions = new PdfArtifactWatermarkOptions();
    imageWatermarkOptions.PageIndex = 1;
    watermarker.Add(imageWatermark, imageWatermarkOptions);
}
```

画像の透かしを使用すると、ドキュメントがプロフェッショナルに見えるようになり、ブランドが常に目立つようになります。すべてのページに署名を追加するようなものです。
## ステップ 4: 透かし入り PDF を保存する
透かしを追加した後の最後のステップは、透かしを入れた PDF を目的の場所に保存することです。
```csharp
watermarker.Save(outputFileName);
```
ドキュメントを保存すると、加えたすべての変更が確定します。これは、あなたの努力が目に見える結果として固まり、すぐに使用または配布できる瞬間です。
## 結論
おめでとう！ GroupDocs.Watermark for .NET を使用して、テキストと画像の両方のウォーターマークを PDF に追加することができました。このプロセスは簡単なだけでなく、特定のニーズに合わせて高度にカスタマイズ可能です。文書を保護する場合でも、文書にブランドを付ける場合でも、透かしは自由に使える強力なツールです。
## よくある質問
### 同じページに複数のウォーターマークを追加できますか?
はい、同じページに複数のウォーターマークを追加できます。`Add`メソッドを異なる透かしオブジェクトで複数回実行します。
### テキストの透かしの外観をカスタマイズするにはどうすればよいですか?
テキストの透かしをカスタマイズするには、フォント、サイズ、色、不透明度などのプロパティを調整します。`TextWatermark`物体。
### PDF の特定のページにのみ透かしを入れることはできますか?
はい、設定することでどのページに透かしを入れるかを指定できます。`PageIndex`のプロパティ`PdfArtifactWatermarkOptions`.
### PDF から透かしを削除できますか?
はい。GroupDocs.Watermark は、PDF ドキュメントからウォーターマークを検索して削除する機能を提供します。
### GroupDocs.Watermark の一時ライセンスを取得するにはどうすればよいですか?
にアクセスして一時ライセンスを取得できます。[一時ライセンスのページ](https://purchase.groupdocs.com/temporary-license/).