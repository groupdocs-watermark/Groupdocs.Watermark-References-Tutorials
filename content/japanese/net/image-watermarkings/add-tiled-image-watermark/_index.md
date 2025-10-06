---
title: 並べて表示された画像の透かしを追加する
linktitle: 並べて表示された画像の透かしを追加する
second_title: GroupDocs.Watermark .NET API
description: GroupDocs.Watermark for .NET を使用して、タイル画像のウォーターマークをドキュメントに追加する方法を学びます。簡単、効率的、カスタマイズ可能。
weight: 10
url: /ja/net/image-watermarkings/add-tiled-image-watermark/
type: docs
---
# 並べて表示された画像の透かしを追加する

## 導入
GroupDocs.Watermark for .NET は、開発者がさまざまなドキュメント形式のウォーターマークをプログラムで追加、削除、検索できる強力な API です。このチュートリアルでは、GroupDocs.Watermark for .NET を使用して、タイル画像ウォーターマークをドキュメントに追加するプロセスを説明します。
## 前提条件
始める前に、次のものが揃っていることを確認してください。
- C# プログラミング言語の基本的な知識。
- Visual Studio がシステムにインストールされている。
- .NET ライブラリの GroupDocs.Watermark がプロジェクトに追加されました。からダウンロードできます[ここ](https://releases.groupdocs.com/Watermark/net/).

## 名前空間のインポート
必要な名前空間を C# ファイルの先頭にインポートしてください。
```csharp
using GroupDocs.Watermark.Watermarks;
using System;
using System.IO;
```
## ステップ 1: ドキュメントのパスと出力ディレクトリを設定する
入力ドキュメントのパスと出力ドキュメントを保存するディレクトリを定義します。
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
交換する`"Your Document Path"`入力ドキュメントへの絶対パスまたは相対パスを使用します。
## ステップ 2: ウォーターマーカー オブジェクトを初期化する
入力ドキュメント パスを使用してウォーターマーカー オブジェクトを作成します。
```csharp
using (Watermarker watermarker = new Watermarker(documentPath))
{
    //ここに透かしを追加します
}
```
## ステップ 3: タイル画像透かしを追加する
ウォーターマークとして使用する画像ファイルへのパスを使用して、ImageWatermark オブジェクトをインスタンス化します。
```csharp
using (ImageWatermark watermark = new ImageWatermark("Path to Your Image"))
{
    //タイルオプションを構成する
    watermark.TileOptions = new TileOptions()
    {
        TileType = TileType.Offset,
        LineSpacing = new MeasureValue()
        {
            MeasureType = TileMeasureType.Percent,
            Value = 12
        },
        WatermarkSpacing = new MeasureValue()
        {
            MeasureType = TileMeasureType.Percent,
            Value = 10
        },
    };
    watermark.RotateAngle = -30;
    //文書に透かしを追加する
    watermarker.Add(watermark);
    //変更したドキュメントを保存する
    watermarker.Save(outputFileName);
}
```
交換する`"Path to Your Image"`ウォーターマーク画像ファイルへの実際のパスを含めます。

## 結論
次の手順に従うと、GroupDocs.Watermark for .NET を使用して、タイル画像のウォーターマークをドキュメントに簡単に追加できます。望ましい結果を得るために、さまざまなオプションと構成を試してください。
## よくある質問
### つのドキュメントに複数の透かしを追加できますか?
はい、GroupDocs.Watermark for .NET を使用して、さまざまなタイプの複数のウォーターマークをドキュメントに追加できます。
### GroupDocs.Watermark はすべてのドキュメント形式をサポートしていますか?
GroupDocs.Watermark は、PDF、Word、Excel、PowerPoint などを含む幅広いドキュメント形式をサポートしています。
### GroupDocs.Watermark の試用版はありますか?
はい、無料試用版を次からダウンロードできます。[ここ](https://releases.groupdocs.com/).
### 透かしの外観をカスタマイズできますか?
はい、位置、サイズ、回転、透明度など、ウォーターマークのさまざまな側面をカスタマイズできます。
### GroupDocs.Watermark は技術サポートを提供していますか?
はい、GroupDocs.Watermark フォーラムから技術サポートを受けることができます。[ここ](https://forum.groupdocs.com/c/watermark/19).