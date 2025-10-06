---
title: ストリームから画像透かしを追加
linktitle: ストリームから画像透かしを追加
second_title: GroupDocs.Watermark .NET API
description: GroupDocs.Watermark for .NET を使用してドキュメントに画像のウォーターマークを追加する方法を学びます。ウォーターマークをシームレスに統合するには、ステップバイステップのガイドに従ってください。
weight: 12
url: /ja/net/image-watermarkings/add-image-watermark-from-stream/
type: docs
---
# ストリームから画像透かしを追加

## 導入
文書管理とセキュリティの分野では、ファイルに透かしを組み込むことが最も重要です。ブランド化、著作権保護、文書の完全性の維持など、透かしは重要な役割を果たします。幸いなことに、GroupDocs.Watermark for .NET は、さまざまなドキュメント形式でウォーターマークを追加、削除、検索するための堅牢なソリューションを提供します。
## 前提条件
GroupDocs.Watermark for .NET を使用したウォーターマークの実装に入る前に、次の前提条件が満たされていることを確認してください。
1.  GroupDocs.Watermark for .NET をインストールする: GroupDocs.Watermark for .NET ライブラリを次の場所からダウンロードしてインストールします。[ダウンロードリンク](https://releases.groupdocs.com/Watermark/net/).
2. ドキュメントへのアクセス: 透かしを追加または削除するドキュメントにアクセスできます。
3. C# の基本知識: 提供されたコード スニペットを理解して実装するには、C# プログラミング言語に精通している必要があります。

## 名前空間のインポート
ストリームから画像のウォーターマークを追加する前に、必要な名前空間をインポートします。
```csharp
using GroupDocs.Watermark.Watermarks;
using System;
using System.IO;
```

## ステップ 1: ドキュメントのパスと出力ディレクトリを定義する
まず、ウォーターマークを追加するドキュメントのパスを定義し、処理されたドキュメントの出力ディレクトリを指定します。
```csharp
string documentPath = Constants.WatermarkJpg;
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
## ステップ 2: ウォーターマーク ストリームを開く
ウォーターマーク画像ファイルをストリームとして開きます。`File.OpenRead`方法。
```csharp
using (Stream watermarkStream = File.OpenRead(documentPath))
{
    //透かし処理ロジックがここに入ります
}
```
## ステップ 3: 文書に透かしを追加する
を初期化します`Watermarker`オブジェクトをドキュメント パスに置き換えてから、`ImageWatermark`ステップ 2 で取得したウォーターマーク ストリームをオブジェクトに追加します。`Add`の方法`Watermarker`物体。
```csharp
using (Watermarker watermarker = new Watermarker("Your Document Path"))
{
    using (ImageWatermark watermark = new ImageWatermark(watermarkStream))
    {
        //文書に透かしを追加する
        watermarker.Add(watermark);
        //文書を透かし付きで保存する
        watermarker.Save(outputFileName);
    }
}
```

## 結論
GroupDocs.Watermark for .NET は、ドキュメントにウォーターマークを追加し、ブランド アイデンティティ、著作権保護、ドキュメントの整合性を確保するためのシームレスなソリューションを提供します。概要を示した手順に従い、提供されたコード スニペットを利用することで、ユーザーはドキュメントに透かしを簡単に組み込むことができます。
## よくある質問
### GroupDocs.Watermark はさまざまなドキュメント形式と互換性がありますか?
はい。GroupDocs.Watermark は、Word ドキュメント、Excel スプレッドシート、PowerPoint プレゼンテーション、PDF などを含む幅広いドキュメント形式をサポートしています。
### 透かしの外観と位置をカスタマイズできますか?
確かに、GroupDocs.Watermark は、特定の要件に合わせてウォーターマークの外観、位置、透明度、回転などをカスタマイズするための広範なオプションを提供します。
### GroupDocs.Watermark は既存のウォーターマークを削除するための API を提供しますか?
はい、GroupDocs.Watermark を使用すると、ユーザーはウォーターマークを追加するだけでなく、ドキュメントから既存のウォーターマークを簡単に削除することもできます。
### GroupDocs.Watermark ユーザーはテクニカル サポートを利用できますか?
はい、ユーザーは専用のサポートを通じてテクニカル サポートと支援を利用できます。[GroupDocs.Watermark フォーラム](https://forum.groupdocs.com/c/watermark/19).
### 購入する前に GroupDocs.Watermark を評価できますか?
確かに、ユーザーは、購入を決定する前に、GroupDocs.Watermark の無料トライアルを選択して、その機能を調べることができます。