---
title: Word ドキュメントで図形設定を使用して透かしを追加する
linktitle: Word ドキュメントで図形設定を使用して透かしを追加する
second_title: GroupDocs.Watermark .NET API
description: GroupDocs for .NET を使用して、形状設定を含むウォーターマークを Word 文書に追加する方法を説明します。文書を効果的に保護します。
weight: 20
url: /ja/net/word-processing-watermarkings/add-watermark-shape-settings-word-docs/
---

# Word ドキュメントで図形設定を使用して透かしを追加する

## 導入
このチュートリアルでは、GroupDocs.Watermark for .NET を使用して、形状設定を含むウォーターマークを Word 文書に追加するプロセスを説明します。
## 前提条件
始める前に、以下のものがあることを確認してください。
1.  .NET 用の GroupDocs.Watermark がインストールされています。からダウンロードできます[ここ](https://releases.groupdocs.com/Watermark/net/).
2. C# プログラミングの基本的な知識。
3. Word 文書処理についての理解。

## 名前空間のインポート
まず、必要なクラスとメソッドにアクセスするために必要な名前空間をインポートする必要があります。
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## ステップ 1: ドキュメントをロードする
透かしを追加する Word 文書を読み込みます。
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    //ウォーターマーク追加コードはここにあります
}
```
## ステップ 2: 透かしを追加する
インスタンス化する`TextWatermark`オブジェクトを選択し、透かしとして使用するテキストを指定します。
```csharp
TextWatermark watermark = new TextWatermark("Test watermark", new Font("Arial", 19));
```
## ステップ 3: ウォーターマーク設定をカスタマイズする
ウォーターマークの配置、回転角度、色、不透明度などのさまざまな設定を行います。
```csharp
watermark.VerticalAlignment = VerticalAlignment.Center;
watermark.HorizontalAlignment = HorizontalAlignment.Center;
watermark.RotateAngle = 25.0;
watermark.ForegroundColor = Color.Red;
watermark.Opacity = 1.0;
```
## ステップ 4: ウォーターマーク セクションのオプションを定義する
図形名や代替テキストなど、透かしセクションのオプションを定義します。
```csharp
WordProcessingWatermarkSectionOptions options = new WordProcessingWatermarkSectionOptions();
options.Name = "Shape 1";
options.AlternativeText = "Test watermark";
```
## ステップ 5: 文書に透かしを追加する
指定したオプションを使用してドキュメントにウォーターマークを追加します。
```csharp
watermarker.Add(watermark, options);
```
## ステップ 6: ドキュメントを保存する
ウォーターマークを追加して文書を保存します。
```csharp
watermarker.Save(outputFileName);
```

## 結論
GroupDocs for .NET を使用して、形状設定を含むウォーターマークを Word 文書に追加するのは簡単なプロセスです。このチュートリアルで概説されている手順に従うことで、カスタマイズされた透かしを使用してドキュメントを効果的に保護できます。
## よくある質問
### 同じ文書に複数の透かしを追加できますか?
はい、同じドキュメントに異なる設定の複数の透かしを追加できます。
### GroupDocs.Watermark は Word 以外のドキュメント形式をサポートしていますか?
はい。GroupDocs.Watermark は、Excel、PowerPoint、PDF などを含むさまざまなドキュメント形式をサポートしています。
### 透かしの外観をさらにカスタマイズできますか?
もちろん、ニーズに合わせてフォントのサイズ、スタイル、色、位置などのさまざまなパラメータを調整できます。
### GroupDocs.Watermark for .NET の試用版はありますか?
はい、次のサイトから無料トライアルを利用できます。[ここ](https://releases.groupdocs.com/).
### GroupDocs.Watermark のサポートはどこで見つけられますか?
 GroupDocs フォーラムでサポートを見つけたり、質問したりできます[ここ](https://forum.groupdocs.com/c/watermark/19).