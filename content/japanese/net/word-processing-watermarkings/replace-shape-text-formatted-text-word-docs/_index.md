---
title: Word ドキュメントの図形テキストを書式設定されたテキストに置き換える
linktitle: Word ドキュメントの図形テキストを書式設定されたテキストに置き換える
second_title: GroupDocs.Watermark .NET API
description: GroupDocs.Watermark for .NET を使用して Word 文書内の図形テキストを書式設定されたテキストに置き換える方法を学びます。ドキュメント編集機能を簡単に。
type: docs
weight: 34
url: /ja/net/word-processing-watermarkings/replace-shape-text-formatted-text-word-docs/
---
## 導入
このチュートリアルでは、GroupDocs.Watermark for .NET を使用して、Word 文書内の図形テキストを書式設定されたテキストに置き換えるプロセスを説明します。このライブラリは、図形内のテキストの置換など、透かしを操作するための強力な機能を提供します。
## 前提条件
始める前に、次の前提条件を満たしていることを確認してください。
1.  GroupDocs.Watermark for .NET: GroupDocs.Watermark for .NET がインストールされ、セットアップされていることを確認してください。からダウンロードできます[ここ](https://releases.groupdocs.com/Watermark/net/).
2. ドキュメント パス: テキストを置換する Word ドキュメントへのパスが必要です。

## 名前空間のインポート
コードを記述する前に、必要な名前空間をインポートします。
```csharp
using GroupDocs.Watermark.Contents.WordProcessing;
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## ステップ 1: ドキュメントをロードする
を使用して Word 文書をロードします。`Watermarker`クラス：
```csharp
string documentPath = "Your Document Path";
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    //コードはここに続きます...
}
```
## ステップ 2: コンテンツを取得してテキストを置換する
ドキュメントが読み込まれたら、コンテンツを取得し、図形内のテキストを置き換えます。
```csharp
WordProcessingContent content = watermarker.GetContent<WordProcessingContent>();
foreach (WordProcessingShape shape in content.Sections[0].Shapes)
{
    if (shape.Text.Contains("Some text"))
    {
        shape.FormattedTextFragments.Clear();
        shape.FormattedTextFragments.Add("Another text", new Font("Calibri", 19, FontStyle.Bold), Color.Red, Color.Aqua);
    }
}
```
## ステップ 3: ドキュメントを保存する
テキストを置換した後、変更したドキュメントを保存します。
```csharp
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
watermarker.Save(outputFileName);
```

## 結論
GroupDocs for .NET を使用すると、Word ドキュメント内の図形テキストを書式設定されたテキストに置き換えることが簡単になります。このチュートリアルで概説されている手順に従うことで、ドキュメント内のテキストを効率的に管理および操作できます。

## よくある質問
### GroupDocs.Watermark for .NET を使用して、他の種類のドキュメントのテキストを置き換えることはできますか?
はい、GroupDocs は PDF、Excel、PowerPoint などのさまざまなドキュメント形式をサポートしています。
### GroupDocs.Watermark は .NET Core と互換性がありますか?
はい、GroupDocs.Watermark は .NET Framework と .NET Core の両方をサポートしています。
### GroupDocs.Watermark は画像をウォーターマークとして追加するサポートを提供しますか?
確かに、GroupDocs.Watermark を使用すると、テキストと画像の両方の透かしを文書に追加できます。
### GroupDocs.Watermark を使用して追加されたウォーターマークの外観をカスタマイズできますか?
はい、透かしの外観、位置、その他のプロパティを完全に制御できます。
### GroupDocs.Watermark for .NET の試用版はありますか?
はい、以下から無料試用版をダウンロードできます。[ここ](https://releases.groupdocs.com/).