---
title: PDF の注釈画像に透かしを追加する
linktitle: PDF の注釈画像に透かしを追加する
second_title: GroupDocs.Watermark .NET API
description: Groupdocs.Watermark for .NET を使用して注釈画像にウォーターマークを追加し、PDF ドキュメントを保護する方法を学びます。
weight: 17
url: /ja/net/pdf-watermarking-attachments/add-watermark-annotation-images-pdf/
---
## 導入
このチュートリアルでは、Groupdocs.Watermark for .NET を使用して PDF ドキュメント内の注釈画像にウォーターマークを追加する方法を説明します。透かしは、ドキュメントを不正な使用や配布から保護するために非常に重要です。このステップバイステップのガイドに従うことで、PDF 内の注釈画像にテキストの透かしを効果的に適用する方法を学びます。
## 前提条件
続行する前に、次のものが揃っていることを確認してください。
1. C# プログラミング言語の基本的な理解。
2. .NET ライブラリ用の Groupdocs.Watermark がインストールされました。
3. Visual Studio などの開発環境へのアクセス。
4. 透かしを入れる注釈画像を含む PDF ドキュメント。

## 名前空間のインポート
まず、必要な名前空間を C# コードにインポートする必要があります。
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## ステップ 1: PDF ドキュメントをロードする
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
```
## ステップ 2: PDF コンテンツを取得してウォーターマークを初期化する
```csharp
    PdfContent pdfContent = watermarker.GetContent<PdfContent>();
    //画像またはテキストの透かしを初期化する
    TextWatermark watermark = new TextWatermark("Protected image", new Font("Arial", 8));
    watermark.HorizontalAlignment = HorizontalAlignment.Center;
    watermark.VerticalAlignment = VerticalAlignment.Center;
    watermark.RotateAngle = 45;
    watermark.SizingType = SizingType.ScaleToParentDimensions;
    watermark.ScaleFactor = 1;
```
## ステップ 3: PDF ページと注釈画像を反復処理する
```csharp
    foreach (PdfPage page in pdfContent.Pages)
    {
        foreach (PdfAnnotation annotation in page.Annotations)
        {
            if (annotation.Image != null)
            {
                //画像に透かしを追加する
                annotation.Image.Add(watermark);
            }
        }
    }
```
## ステップ 4: 透かしを入れてドキュメントを保存する
```csharp
    watermarker.Save(outputFileName);
}
```
これらの手順を実行すると、PDF ドキュメントの注釈画像に指定された透かしが追加されます。

## 結論
PDF 内の注釈画像に透かしを追加することは、ドキュメントの完全性を保護し、悪用されないようにするために不可欠です。 Groupdocs.Watermark for .NET を使用すると、このプロセスがシンプルかつ効率的になり、PDF ファイルを効果的に保護できるようになります。
## よくある質問
### 同じ PDF ドキュメントに複数のウォーターマークを追加できますか?
はい、Groupdocs.Watermark for .NET を使用して、同じ PDF ドキュメントに複数のウォーターマークを追加できます。
### Groupdocs.Watermark は PDF 以外のドキュメント形式をサポートしていますか?
はい、Groupdocs は Word、Excel、PowerPoint などのさまざまなドキュメント形式をサポートしています。
### 透かしの外観をカスタマイズすることはできますか?
もちろん、お好みに応じて透かしのテキスト、フォント、色、サイズ、位置をカスタマイズできます。
### Groupdocs.Watermark を使用して PDF ドキュメントからウォーターマークを削除できますか?
はい。Groupdocs.Watermark は、PDF ドキュメントからウォーターマークを簡単に削除する機能を提供します。
### Groupdocs.Watermark for .NET に利用できる無料トライアルはありますか?
はい、Web サイトから Groupdocs.Watermark for .NET の無料トライアルを利用できます。