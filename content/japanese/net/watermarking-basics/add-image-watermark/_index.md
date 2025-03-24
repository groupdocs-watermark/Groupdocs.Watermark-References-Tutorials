---
title: 画像の透かしを追加する
linktitle: 画像の透かしを追加する
second_title: GroupDocs.Watermark .NET API
description: GroupDocs.Watermark for .NET を使用すると、画像のウォーターマークをドキュメントに簡単に追加できます。知的財産を簡単に保護します。
weight: 10
url: /ja/net/watermarking-basics/add-image-watermark/
---
## 導入
このチュートリアルでは、GroupDocs.Watermark for .NET を使用してドキュメントに画像ウォーターマークを追加するプロセスを詳しく説明します。文書に透かしを入れることは、知的財産とブランドを保護するために不可欠です。 GroupDocs.Watermark for .NET を使用すると、Word、Excel、PowerPoint、PDF などのさまざまなドキュメント形式にウォーターマークをシームレスに統合できます。
## 前提条件
始める前に、次の前提条件が満たされていることを確認してください。
1.  GroupDocs.Watermark for .NET ライブラリ: GroupDocs.Watermark for .NET ライブラリを次の場所からダウンロードしてインストールします。[Webサイト](https://releases.groupdocs.com/Watermark/net/).
2. ドキュメント: 透かしを追加するドキュメントを準備します。
3. ウォーターマーク用画像：ウォーターマークとして使用する画像ファイルを用意します。

## 名前空間のインポート
```csharp
using System;
using System.IO;
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Options.Spreadsheet;
using GroupDocs.Watermark.Watermarks;
```
## ステップ 1: ドキュメント パスと出力ディレクトリを初期化する
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
交換する`"Your Document Path"`ドキュメントへの絶対パスまたは相対パスを使用して、`"Your Document Directory"`を、透かし入りのドキュメントを保存するディレクトリに置き換えます。
## ステップ 2: ドキュメント ストリームを開き、ウォーターマーカーを初期化する
```csharp
using (FileStream stream = File.Open(documentPath, FileMode.Open, FileAccess.ReadWrite))
{
    using (Watermarker watermarker = new Watermarker(stream))
    {
        //透かし処理はここに進みます
    }
}
```
次を使用してドキュメント ストリームを開きます`FileStream`そして初期化します`Watermarker`物体。
## ステップ 3: 画像透かしを追加する
```csharp
using (ImageWatermark watermark = new ImageWatermark(Constants.LogoPng))
{
    watermark.HorizontalAlignment = HorizontalAlignment.Center;
    watermark.VerticalAlignment = VerticalAlignment.Center;
    watermarker.Add(watermark);
}
```
を作成します`ImageWatermark`オブジェクトに、透かしとして使用する画像ファイルへのパスを指定します。ウォーターマークの水平方向と垂直方向の配置を設定します。
## ステップ 4: 透かし入りのドキュメントを保存する
```csharp
watermarker.Save(outputFileName);
```
透かし入りのドキュメントを、希望のファイル名で指定された出力ディレクトリに保存します。

## 結論
結論として、GroupDocs.Watermark for .NET は、さまざまなドキュメント形式にウォーターマークを簡単に追加するための包括的なソリューションを提供します。このチュートリアルで概説されている手順に従うことで、文書に画像の透かしを効率的に追加し、知的財産を保護できます。
## よくある質問
### GroupDocs.Watermark for .NET を使用してテキスト透かしを追加できますか?
はい。GroupDocs.Watermark for .NET は、画像とテキストの両方のウォーターマークのドキュメントへの追加をサポートしています。
### GroupDocs.Watermark for .NET はさまざまなドキュメント形式と互換性がありますか?
確かに、GroupDocs.Watermark for .NET は、Word、Excel、PowerPoint、PDF などを含む幅広いドキュメント形式をサポートしています。
### GroupDocs.Watermark for .NET はウォーターマークのカスタマイズ オプションを提供しますか?
はい、位置、サイズ、不透明度、回転など、ウォーターマークのさまざまな側面をカスタマイズできます。
### GroupDocs.Watermark for .NET を使用してドキュメントからウォーターマークを削除できますか?
はい。GroupDocs.Watermark for .NET は、ドキュメントからウォーターマークを検出して削除する機能を提供します。
### GroupDocs.Watermark for .NET の試用版はありますか?
はい、Web サイトから無料試用版を利用して、購入前に機能を試すことができます。[ここ](https://releases.groupdocs.com/).