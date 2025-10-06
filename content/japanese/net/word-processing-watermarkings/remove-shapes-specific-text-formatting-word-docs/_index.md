---
title: Word ドキュメントで特定のテキスト書式設定を持つ図形を削除する
linktitle: Word ドキュメントで特定のテキスト書式設定を持つ図形を削除する
second_title: GroupDocs.Watermark .NET API
description: GroupDocs.Watermark for .NET を使用して Word 文書内の特定のテキスト書式を持つ図形を削除する方法を学びます。ウォーターマークを効率的に操作するには、ガイドに従ってください。
weight: 31
url: /ja/net/word-processing-watermarkings/remove-shapes-specific-text-formatting-word-docs/
type: docs
---
# Word ドキュメントで特定のテキスト書式設定を持つ図形を削除する

## 導入
GroupDocs.Watermark for .NET は、開発者がさまざまなドキュメント形式のウォーターマークをプログラムで操作できるようにする強力な API です。このチュートリアルでは、GroupDocs.Watermark for .NET を使用して Word 文書内の特定のテキスト書式を持つ図形を削除することに焦点を当てます。経験豊富な開発者でも、初心者でも、このステップバイステップのガイドは、シェイプを効率的かつ効果的に削除するプロセスを理解するのに役立ちます。
## 前提条件
チュートリアルに入る前に、次の前提条件が満たされていることを確認してください。
1.  GroupDocs.Watermark for .NET: 開発環境に GroupDocs.Watermark for .NET ライブラリがインストールされていることを確認します。からダウンロードできます。[Webサイト](https://releases.groupdocs.com/Watermark/net/).
2. 開発環境: Visual Studio またはその他の .NET IDE がインストールされている適切な開発環境をセットアップします。
3. Word 文書: 削除する特定のテキスト書式を持つ図形を含む Word 文書を準備します。

## 名前空間のインポート
実装を始める前に、必要な名前空間をインポートしましょう。
```csharp
using GroupDocs.Watermark.Contents.WordProcessing;
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Search;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## ステップ 1: ドキュメントをロードする
```csharp
string documentPath = "Your Document Path";
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    //実装はここに進みます
}
```
## ステップ 2: コンテンツを取得してセクションを反復処理する
```csharp
WordProcessingContent content = watermarker.GetContent<WordProcessingContent>();
foreach (WordProcessingSection section in content.Sections)
{
    //実装はここに進みます
}
```
## ステップ 3: 図形を反復処理し、テキストの書式設定に基づいて削除する
```csharp
for (int i = section.Shapes.Count - 1; i >= 0; i--)
{
    foreach (FormattedTextFragment fragment in section.Shapes[i].FormattedTextFragments)
    {
        if (fragment.ForegroundColor.Equals(Color.Red) && fragment.Font.FamilyName == "Arial")
        {
            section.Shapes.RemoveAt(i);
            break;
        }
    }
}
```
## ステップ 4: ドキュメントを保存する
```csharp
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
watermarker.Save(outputFileName);
```

## 結論
このチュートリアルでは、GroupDocs.Watermark for .NET を使用して Word 文書内の特定のテキスト書式を持つ図形を削除する方法を学習しました。ステップバイステップのガイドに従い、提供されたコード例を利用することで、開発者は要件に応じてウォーターマークを簡単に操作できます。
## よくある質問
### GroupDocs.Watermark for .NET は Word 以外のドキュメント形式と互換性がありますか?
はい。GroupDocs.Watermark for .NET は、Excel、PowerPoint、PDF などを含むさまざまなドキュメント形式をサポートしています。
### テキストの書式設定に基づいて図形を削除する基準をカスタマイズできますか?
絶対に！コードを変更して、フォント サイズ、スタイル、色などの特定のテキスト属性をターゲットにすることができます。
### GroupDocs.Watermark for .NET はウォーターマークの追加もサポートしていますか?
はい、削除するだけでなく、GroupDocs.Watermark for .NET を使用してテキストまたは画像のウォーターマークをドキュメントに追加することもできます。
### 購入前にテストできる試用版はありますか?
はい、GroupDocs から無料試用版をダウンロードできます。[Webサイト](https://releases.groupdocs.com/).
### GroupDocs.Watermark for .NET に関するテクニカル サポートや支援を受けるにはどうすればよいですか?
技術的なサポートが必要な場合は、次のサポート フォーラムにアクセスしてください。[GroupDocs.Watermark フォーラム](https://forum.groupdocs.com/c/watermark/19).