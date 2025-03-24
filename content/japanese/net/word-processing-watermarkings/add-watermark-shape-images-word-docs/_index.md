---
title: Word ドキュメントの図形画像に透かしを追加する
linktitle: Word ドキュメントの図形画像に透かしを追加する
second_title: GroupDocs.Watermark .NET API
description: GroupDocs.Watermark for .NET を使用して、Word 文書内の画像に透かしを追加して画像を整形する方法を学びます。このチュートリアルでドキュメントのセキュリティを強化します。
weight: 17
url: /ja/net/word-processing-watermarkings/add-watermark-shape-images-word-docs/
---

# Word ドキュメントの図形画像に透かしを追加する

## 導入
このチュートリアルでは、GroupDocs.Watermark for .NET を使用して、Word ドキュメント内の画像にウォーターマークを追加して整形する方法を説明します。透かしは、特に機密情報や機密情報を扱う場合、文書保護の重要な側面です。画像の形状に透かしを追加することで、ドキュメントの完全性とセキュリティを確保できます。
## 前提条件
始める前に、以下のものがあることを確認してください。
1.  GroupDocs.Watermark for .NET: 次の場所から GroupDocs.Watermark ライブラリをダウンロードしてインストールします。[ダウンロードページ](https://releases.groupdocs.com/Watermark/net/).
2. 文書: 透かしを追加する Word 文書を準備します。
3. 開発環境: 好みの .NET 開発環境をセットアップします。
## 名前空間のインポート
コードを記述する前に、必要な名前空間を必ずインポートしてください。
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.WordProcessing;
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## ステップ 1: ドキュメントをロードする
まず、ドキュメントへのパスを定義し、出力ファイル名を指定します。
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
```
## ステップ 2: ウォーターマーカーを初期化する
インスタンス化する`Watermarker`ドキュメント パスとオプションの読み込みオプションを指定してオブジェクトを作成します。
```csharp
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    //ここに透かしロジックを追加します
}
```
## ステップ 3: テキストの透かしを作成する
テキスト、フォント、配置、回転、サイズ変更などの必要なプロパティを使用してテキストの透かしを定義します。
```csharp
TextWatermark watermark = new TextWatermark("Protected image", new Font("Arial", 8));
watermark.HorizontalAlignment = HorizontalAlignment.Center;
watermark.VerticalAlignment = VerticalAlignment.Center;
watermark.RotateAngle = 45;
watermark.SizingType = SizingType.ScaleToParentDimensions;
watermark.ScaleFactor = 1;
```
## ステップ 4: 画像の形状に透かしを適用する
ドキュメントのセクションと図形を繰り返し処理して、図形画像を特定し、透かしを追加します。
```csharp
WordProcessingContent content = watermarker.GetContent<WordProcessingContent>();
foreach (WordProcessingSection section in content.Sections)
{
    foreach (WordProcessingShape shape in section.Shapes)
    {
        if (shape.HeaderFooter == null && shape.Image != null)
        {
            shape.Image.Add(watermark);
        }
    }
}
```
## ステップ 5: ドキュメントを保存する
ウォーターマークを追加したドキュメントを指定した出力ファイルに保存します。
```csharp
watermarker.Save(outputFileName);
```

## 結論
このチュートリアルでは、GroupDocs.Watermark for .NET を使用して、Word 文書の画像に透かしを追加する方法を学習しました。ステップバイステップのガイドに従い、GroupDocs.Watermark の強力な機能を活用することで、ドキュメントのセキュリティと保護を効果的に強化できます。
## よくある質問
### 透かしテキストの外観をカスタマイズできますか?
はい、フォント、サイズ、色、回転角度、配置などのさまざまなプロパティを調整して、好みに応じてウォーターマークをカスタマイズできます。
### GroupDocs.Watermark は Word 以外のドキュメント形式をサポートしていますか?
はい。GroupDocs.Watermark は、PDF、Excel、PowerPoint などを含む幅広いドキュメント形式をサポートしています。
### 1 つのドキュメントに複数の透かしを追加することはできますか?
もちろん、同じドキュメント内に、コンテンツ、スタイル、位置が異なる複数の透かしを追加できます。
### GroupDocs.Watermark を使用してドキュメントからウォーターマークを削除できますか?
はい。GroupDocs.Watermark は、ドキュメントからウォーターマークを効率的に検出して削除する機能を提供します。
### GroupDocs.Watermark はクロスプラットフォーム互換性を提供しますか?
はい。GroupDocs.Watermark は .NET Framework、.NET Core、および .NET Standard と互換性があり、さまざまなプラットフォーム間でのシームレスな統合を保証します。