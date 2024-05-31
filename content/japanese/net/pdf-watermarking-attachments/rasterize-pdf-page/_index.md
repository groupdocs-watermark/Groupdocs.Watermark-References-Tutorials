---
title: PDF ページをラスタライズする
linktitle: PDF ページをラスタライズする
second_title: GroupDocs.Watermark .NET API
description: GroupDocs for .NET でドキュメントのセキュリティを強化します。 PDF やその他の形式にウォーターマークをシームレスに追加します。
type: docs
weight: 28
url: /ja/net/pdf-watermarking-attachments/rasterize-pdf-page/
---
## 導入
GroupDocs.Watermark for .NET は、開発者が PDF、Word、Excel、PowerPoint などのさまざまなドキュメント形式にウォーターマークをシームレスに追加できる強力な API です。 GroupDocs.Watermark は、直感的なインターフェイスと広範な機能により、文書にテキストまたは画像の透かしを追加するプロセスを簡素化し、ユーザーが知的財産を保護し、文書のセキュリティを簡単に強化できるようにします。
## 前提条件
GroupDocs.Watermark for .NET の使用に入る前に、次の前提条件が満たされていることを確認してください。
1. インストール: GroupDocs.Watermark for .NET を次の場所からダウンロードしてインストールします。[ダウンロードページ](https://releases.groupdocs.com/Watermark/net/).
2. ライセンス: GroupDocs.Watermark for .NET のライセンスを取得します。評価目的の一時ライセンスは、次から取得できます。[ここ](https://purchase.groupdocs.com/temporary-license/) 、またはから完全なライセンスを購入します。[購入ページ](https://purchase.groupdocs.com/buy).
3. .NET Framework: .NET Framework が開発マシンにインストールされていることを確認してください。
4. ドキュメント: ウォーターマークを追加するドキュメントを準備します。

## 名前空間のインポート
GroupDocs.Watermark for .NET の使用を開始するには、必要な名前空間をプロジェクトにインポートします。
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## ステップ 1: ドキュメントをロードする
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    //コードはここに入力します
}
```
## ステップ 2: ウォーターマークを初期化する
```csharp
TextWatermark watermark = new TextWatermark("Do not copy", new Font("Arial", 8));
watermark.HorizontalAlignment = HorizontalAlignment.Center;
watermark.VerticalAlignment = VerticalAlignment.Center;
watermark.RotateAngle = 45;
watermark.SizingType = SizingType.ScaleToParentDimensions;
watermark.ScaleFactor = 1;
watermark.Opacity = 0.5;
```
## ステップ 3: 透かしを追加する
```csharp
PdfArtifactWatermarkOptions options = new PdfArtifactWatermarkOptions();
options.PageIndex = 0;
watermarker.Add(watermark, options);
```
## ステップ 4: ページをラスタライズする
```csharp
PdfContent pdfContent = watermarker.GetContent<PdfContent>();
pdfContent.Pages[0].Rasterize(100, 100, PdfImageConversionFormat.Png);
```
## ステップ 5: ドキュメントを保存する
```csharp
watermarker.Save(outputFileName);
```

## 結論
結論として、GroupDocs.Watermark for .NET は、PDF やその他のドキュメント形式にウォーターマークを追加するためのシームレスなソリューションを提供します。上記で概説したステップバイステップのガイドに従うことで、開発者は PDF ページを効率的にラスタライズし、ドキュメントのセキュリティを簡単に強化できます。
## よくある質問
### GroupDocs.Watermark は PDF 以外のドキュメント形式と互換性がありますか?
はい。GroupDocs.Watermark は、Word、Excel、PowerPoint、Visio などを含む幅広いドキュメント形式をサポートしています。
### ドキュメントに追加される透かしの外観をカスタマイズできますか?
絶対に！ GroupDocs.Watermark は、テキストと画像の透かしの広範なカスタマイズ オプションを提供し、ユーザーが好みに応じてフォント、サイズ、色、不透明度、位置を調整できるようにします。
### GroupDocs.Watermark は個人使用と商用使用の両方に適していますか?
はい、GroupDocs.Watermark は個人と企業の両方のニーズに応える柔軟なライセンス オプションを提供しており、個人のプロジェクトだけでなく大規模な商用アプリケーションにも適しています。
### GroupDocs.Watermark は開発者に技術サポートを提供しますか?
はい、開発者は GroupDocs.Watermark フォーラムを通じて包括的な技術サポートにアクセスでき、支援を求めたり、経験を共有したり、他の開発者と交流したりすることができます。
### 購入する前に GroupDocs.Watermark を試してみることはできますか?
確かに！ GroupDocs.Watermark の無料試用版は、[リリースページ](https://releases.groupdocs.com/)を購入する前に、その特徴や機能を調べることができます。