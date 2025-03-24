---
title: Word ドキュメントの特定のページに透かしを追加する
linktitle: Word ドキュメントの特定のページに透かしを追加する
second_title: GroupDocs.Watermark .NET API
description: GroupDocs for .NET を使用して Word 文書の特定のページにウォーターマークを追加する方法を説明します。コンテンツを簡単に保護します。
weight: 14
url: /ja/net/word-processing-watermarkings/add-watermark-specific-page-word-docs/
---
## 導入
文書に透かしを入れることは、文書のセキュリティとブランド化の重要な側面です。このチュートリアルでは、GroupDocs.Watermark for .NET を使用して Word 文書の特定のページにウォーターマークを追加する方法を説明します。
## 前提条件
始める前に、次の前提条件を満たしていることを確認してください。
- C# プログラミングの基本的な知識。
- Visual Studio IDE がインストールされている。
- GroupDocs.Watermark for .NET がプロジェクトにインストールされています。

## 名前空間のインポート
コードに入る前に、必要な名前空間をインポートしていることを確認してください。
```csharp
using GroupDocs.Watermark.Contents.WordProcessing;
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## ステップ 1: ドキュメントをロードする
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    //コードはここに入力されます
}
```
## ステップ 2: 透かしを追加する
```csharp
//透かしのテキストとスタイルを定義する
TextWatermark textWatermark = new TextWatermark("DRAFT", new Font("Arial", 42));
//最後のページに透かしを追加する
WordProcessingContent content = watermarker.GetContent<WordProcessingContent>();
WordProcessingWatermarkPagesOptions options = new WordProcessingWatermarkPagesOptions();
options.PageNumbers = new int[] {content.PageCount};
watermarker.Add(textWatermark, options);
```
## ステップ 3: ドキュメントを保存する
```csharp
//透かしを入れて文書を保存する
watermarker.Save(outputFileName);
```

## 結論
このチュートリアルでは、GroupDocs.Watermark for .NET を使用して Word 文書の特定のページにウォーターマークを追加する方法を学習しました。これらの手順に従うことで、ドキュメントを効果的に保護し、必要に応じてブランド要素を追加できます。
## よくある質問
### 透かしのテキストとスタイルをカスタマイズできますか?
はい、要件に応じて透かしのテキスト、フォント、サイズ、色、位置をカスタマイズできます。
### GroupDocs.Watermark for .NET は他のドキュメント形式と互換性がありますか?
はい。GroupDocs.Watermark は、Word、Excel、PowerPoint、PDF などを含むさまざまなドキュメント形式をサポートしています。
### つのドキュメントに複数の透かしを追加できますか?
もちろん、異なるコンテンツやスタイルを持つ複数の透かしを同じドキュメントに追加することもできます。
### GroupDocs.Watermark for .NET に利用できる無料試用版はありますか?
はい、無料トライアルで GroupDocs.Watermark の機能を探索できます。提供されたリンクにアクセスするだけで開始できます[ここ](https://releases.groupdocs.com/).
### GroupDocs.Watermark のテクニカル サポートはどこで受けられますか?
役立つリソースを見つけたり、技術サポートを受けたりできます。[ここ](https://forum.groupdocs.com/c/watermark/19)GroupDocs.Watermark フォーラム。コミュニティに参加するには、提供されたリンクにアクセスしてください。