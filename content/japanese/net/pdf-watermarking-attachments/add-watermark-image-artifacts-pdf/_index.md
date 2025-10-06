---
title: PDF の画像アーティファクトに透かしを追加する
linktitle: PDF の画像アーティファクトに透かしを追加する
second_title: GroupDocs.Watermark .NET API
description: GroupDocs.Watermark for .NET を使用して、PDF ファイルをパーソナライズされたウォーターマークで保護します。 PDF ドキュメント内の画像アーティファクトにテキストまたは画像の透かしを簡単に追加します。
weight: 18
url: /ja/net/pdf-watermarking-attachments/add-watermark-image-artifacts-pdf/
type: docs
---
# PDF の画像アーティファクトに透かしを追加する

## 導入
このチュートリアルでは、GroupDocs.Watermark for .NET を使用して、PDF ドキュメント内の画像アーティファクトにウォーターマークを追加するプロセスを説明します。これらの手順に従うことで、パーソナライズされた透かしを使用して PDF ファイルを効率的に保護できます。
## 前提条件
始める前に、次の前提条件を満たしていることを確認してください。
1.  GroupDocs.Watermark for .NET: GroupDocs.Watermark for .NET ライブラリを次からダウンロードしてインストールします。[ここ](https://releases.groupdocs.com/Watermark/net/).
2. ドキュメント パス: 透かしを追加する PDF ドキュメントへのパスを指定します。
3. 出力ディレクトリ: 透かし入りのドキュメントを保存するディレクトリを作成します。

## 名前空間のインポート
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## ステップ 1: ドキュメントをロードしてウォーターマーカーを初期化する
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
```
## ステップ 2: PDF コンテンツを取得してウォーターマークを追加する
```csharp
	PdfContent pdfContent = watermarker.GetContent<PdfContent>();
	//画像またはテキストの透かしを初期化する
	TextWatermark watermark = new TextWatermark("Protected image", new Font("Arial", 8));
	watermark.HorizontalAlignment = HorizontalAlignment.Center;
	watermark.VerticalAlignment = VerticalAlignment.Center;
	watermark.RotateAngle = 45;
	watermark.SizingType = SizingType.ScaleToParentDimensions;
	watermark.ScaleFactor = 1;
	foreach (PdfPage page in pdfContent.Pages)
	{
		foreach (PdfArtifact artifact in page.Artifacts)
		{
			if (artifact.Image != null)
			{
				//画像に透かしを追加する
				artifact.Image.Add(watermark);
			}
		}
	}
```
## ステップ 3: 透かし入りのドキュメントを保存する
```csharp
	watermarker.Save(outputFileName);
}
```

## 結論
GroupDocs.Watermark for .NET を使用すると、PDF ドキュメント内の画像アーティファクトにウォーターマークを追加することがシームレスなプロセスになります。このチュートリアルに従うことで、カスタマイズされた透かしを使用して PDF ファイルを効率的に保護し、そのセキュリティと信頼性を確保できます。
## よくある質問
### 画像とテキストの両方の透かしを PDF 文書に追加できますか?
はい、GroupDocs.Watermark for .NET は、画像とテキストのウォーターマークの両方の同時追加をサポートしています。
### ドキュメントに追加できるウォーターマークの数に制限はありますか?
いいえ、ドキュメントに複数の透かしを制限なく追加できます。
### 透かしの外観と位置をカスタマイズできますか?
もちろん、透かしの外観、位置、プロパティを完全に制御できます。
### GroupDocs.Watermark for .NET は PDF 以外のドキュメント形式をサポートしていますか?
はい、Word、Excel、PowerPoint などを含むさまざまなドキュメント形式をサポートしています。
### 文書から透かしを削除する方法はありますか?
はい、GroupDocs.Watermark for .NET は、必要に応じてドキュメントからウォーターマークを削除するメソッドを提供します。