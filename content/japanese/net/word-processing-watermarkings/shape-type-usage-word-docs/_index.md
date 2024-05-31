---
title: Word ドキュメントでの図形タイプの使用法
linktitle: Word ドキュメントでの図形タイプの使用法
second_title: GroupDocs.Watermark .NET API
description: GroupDocs.Watermark for .NET を使用して Word 文書内の図形を操作する方法を学びます。このチュートリアルでは、文書を効率的に処理するためのガイダンスを提供します。
type: docs
weight: 37
url: /ja/net/word-processing-watermarkings/shape-type-usage-word-docs/
---
## 導入
このチュートリアルでは、GroupDocs.Watermark for .NET を使用して Word 文書で図形タイプを利用する方法を検討します。 Word 文書の形状はさまざまであるため、その操作方法を理解することは、さまざまな文書処理タスクにとって重要です。
## 前提条件
始める前に、次の前提条件が満たされていることを確認してください。
1.  GroupDocs.Watermark for .NET ライブラリ: GroupDocs.Watermark for .NET ライブラリを次の場所からダウンロードしてインストールします。[ダウンロードリンク](https://releases.groupdocs.com/Watermark/net/).
2. ドキュメント パス: Word ドキュメントを処理できる状態にします。
3. 開発環境: .NET Framework をサポートする適切な開発環境をセットアップします。

## 名前空間のインポート
開始するには、必要な名前空間をプロジェクトにインポートする必要があります。これらの名前空間は、Word 文書を操作するために必要なクラスとメソッドへのアクセスを提供します。
```csharp
using GroupDocs.Watermark.Contents.WordProcessing;
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System;
using System.IO;
```
## ステップ 1: ドキュメントをロードする
まず、Word 文書をウォーターマーカー オブジェクトにロードします。ドキュメントのパスと、読み込みプロセス中に必要な追加オプションを必ず指定してください。
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    //文書処理コードがここに入ります
}
```
## ステップ 2: ドキュメントのコンテンツにアクセスする
ロードされた Word 文書のコンテンツにアクセスするには、`GetContent<WordProcessingContent>()`方法。これにより、ドキュメント内に存在するセクション、段落、図形にアクセスできるようになります。
```csharp
WordProcessingContent content = watermarker.GetContent<WordProcessingContent>();
```
## ステップ 3: セクションとシェイプを反復処理する
ドキュメント内の各セクションと図形を反復処理して、必要に応じて検査および操作します。
```csharp
foreach (WordProcessingSection section in content.Sections)
{
    foreach (WordProcessingShape shape in section.Shapes)
    {
        //形状操作コードはここにあります
    }
}
```
## ステップ 4: 形状タイプを確認する
ループ内で、`ShapeType`財産。この例では、斜めの角、丸い形状の識別と処理を示します。
```csharp
if (shape.ShapeType == WordProcessingShapeType.DiagonalCornersRounded)
{
    //形状固有の操作コードはここにあります
}
```
## ステップ 5: 形状を操作する
テキストの追加、書式設定の変更、特定された図形への視覚的な変更の適用などのアクションを実行します。
```csharp
shape.FormattedTextFragments.Add("I am Diagonal Corner Rounded", new Font("Calibri", 8, FontStyle.Bold), Color.Red, Color.Aqua);
```
## ステップ 6: ドキュメントを保存する
必要な変更をすべて行ったら、変更を適用したドキュメントを指定した出力ファイルに保存します。
```csharp
watermarker.Save(outputFileName);
```

## 結論
Word 文書内の図形の操作は、さまざまな文書処理タスクに不可欠です。 GroupDocs.Watermark for .NET を使用すると、要件を効率的に満たすために形状を簡単に識別、変更、操作できます。
## よくある質問
### GroupDocs.Watermark for .NET は Word 以外のドキュメント形式を処理できますか?
はい、GroupDocs.Watermark for .NET は、PDF、Excel、PowerPoint などを含む幅広いドキュメント形式をサポートしています。
### GroupDocs.Watermark for .NET に利用できる無料試用版はありますか?
はい、次のサイトから無料試用版にアクセスできます。[リリースページ](https://releases.groupdocs.com/).
### GroupDocs.Watermark for .NET はテクニカル サポートを提供しますか?
はい、サポートを求めたり、コミュニティに参加したりできます。[サポートフォーラム](https://forum.groupdocs.com/c/watermark/19).
### 特定のドキュメント要件に合わせて透かしプロセスをカスタマイズできますか?
確かに、GroupDocs.Watermark for .NET は、ニーズに応じて透かしプロセスを調整するための広範なカスタマイズ オプションを提供します。
### GroupDocs.Watermark for .NET の一時ライセンスを取得するにはどうすればよいですか?
一時ライセンスは以下から取得できます。[一時ライセンス購入ページ](https://purchase.groupdocs.com/temporary-license/)テストと評価の目的で。