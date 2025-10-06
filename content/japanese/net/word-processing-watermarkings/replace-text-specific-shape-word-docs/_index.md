---
title: Word ドキュメントの特定の図形のテキストを置換する
linktitle: Word ドキュメントの特定の図形のテキストを置換する
second_title: GroupDocs.Watermark .NET API
description: GroupDocs.Watermark for .NET を使用して、Word 文書内の特定の図形のテキストを置換する方法を学びます。ステップバイステップのチュートリアルに従ってください。
weight: 35
url: /ja/net/word-processing-watermarkings/replace-text-specific-shape-word-docs/
type: docs
---
# Word ドキュメントの特定の図形のテキストを置換する

## 導入
このチュートリアルでは、GroupDocs.Watermark for .NET を使用して Word 文書内の特定の図形のテキストを置き換える方法を説明します。 GroupDocs.Watermark for .NET は、Word ドキュメントを含むさまざまなドキュメント形式のウォーターマークを操作するための幅広い機能を提供する強力なライブラリです。
## 前提条件
始める前に、次の前提条件が満たされていることを確認してください。
1.  GroupDocs.Watermark for .NET: GroupDocs.Watermark for .NET をダウンロードしてインストールしていることを確認してください。からダウンロードできます[ここ](https://releases.groupdocs.com/Watermark/net/).
2. ドキュメント: 特定の図形のテキストを置換する Word ドキュメントを準備します。
3. 開発環境: 必要なツールと依存関係を備えた開発環境をセットアップします。

## 名前空間のインポート
まず、GroupDocs.Watermark for .NET を操作するために必要な名前空間をインポートしましょう。
```csharp
using GroupDocs.Watermark.Contents.WordProcessing;
using GroupDocs.Watermark.Options.WordProcessing;
using System.IO;
using System;
```
## ステップ 1: ドキュメントをロードする
```csharp
string documentPath = "Your Document Path";
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    //コードはここに入力します
}
```
このステップでは、Word 文書へのパスを指定し、`WordProcessingLoadOptions`ドキュメントをロードします。
## ステップ 2: ドキュメントのコンテンツを取得する
```csharp
WordProcessingContent content = watermarker.GetContent<WordProcessingContent>();
```
ここでは、`GetContent<T>()`の方法`Watermarker`クラス、タイプを次のように指定します`WordProcessingContent`.
## ステップ 3: 特定の形状のテキストを置換する
```csharp
foreach (WordProcessingShape shape in content.Sections[0].Shapes)
{
    if (shape.Text.Contains("Some text"))
    {
        shape.Text = "Another text";
    }
}
```
このステップでは、ドキュメント内の各図形を繰り返し処理します。図形に指定されたテキスト (この例では「一部のテキスト」) が含まれている場合、それを目的のテキスト (「別のテキスト」) に置き換えます。
## ステップ 4: ドキュメントを保存する
```csharp
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
watermarker.Save(outputFileName);
```
最後に、変更したドキュメントを指定したディレクトリに保存します。

## 結論
GroupDocs.Watermark for .NET は、Word 文書内のウォーターマークを操作する便利で効率的な方法を提供します。このチュートリアルで概説されている手順に従うことで、特定の図形のテキストを簡単に置き換えることができ、ドキュメント処理のニーズに合わせた柔軟性とカスタマイズ オプションが提供されます。
## よくある質問
### Word 以外の文書形式の図形のテキストを置き換えることはできますか?
GroupDocs.Watermark for .NET は、PDF、Excel、PowerPoint などを含むさまざまなドキュメント形式をサポートしています。同様の方法を使用して、さまざまな形式の図形のテキストを置き換えることができます。
### GroupDocs.Watermark for .NET の試用版はありますか?
はい、無料試用版を次からダウンロードできます。[ここ](https://releases.groupdocs.com/).
### GroupDocs.Watermark for .NET のテクニカル サポートを受けるにはどうすればよいですか?
GroupDocs フォーラムにアクセスすると、技術サポートを受けることができます。[ここ](https://forum.groupdocs.com/c/watermark/19).
### GroupDocs.Watermark for .NET を使用するには一時ライセンスが必要ですか?
追加機能や拡張使用が必要な場合は、次のサイトから一時ライセンスを取得できます。[ここ](https://purchase.groupdocs.com/temporary-license/).
### GroupDocs.Watermark for .NET のフル ライセンスはどこで購入できますか?
 GroupDocs Web サイトから完全なライセンスを購入できます。[ここ](https://purchase.groupdocs.com/buy).