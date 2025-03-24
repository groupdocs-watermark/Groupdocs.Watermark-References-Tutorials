---
title: Word ドキュメントの特定のページにロックされた透かしを追加する
linktitle: Word ドキュメントの特定のページにロックされた透かしを追加する
second_title: GroupDocs.Watermark .NET API
description: 簡単なステップバイステップ ガイドで、GroupDocs.Watermark for .NET を使用して Word 文書の特定のページにロックされたウォーターマークを追加する方法を学びます。
weight: 12
url: /ja/net/word-processing-watermarkings/add-locked-watermark-specific-pages-word-docs/
---

# Word ドキュメントの特定のページにロックされた透かしを追加する

## 導入
Word 文書の特定のページに透かしを追加したいと考えていますが、簡単に削除または編集できないようにロックしたいと考えていますか?あなたは正しい場所にいます！このチュートリアルでは、GroupDocs.Watermark for .NET を使用して、Word 文書の特定のページにロックされたウォーターマークを追加するプロセスを説明します。この強力なライブラリを使用すると、さまざまな種類のドキュメントに透かしを簡単に適用、管理、カスタマイズできます。あなたが開発者であっても、ドキュメントを保護する必要があるだけの人であっても、このガイドでは各ステップをわかりやすく説明します。
## 前提条件
チュートリアルに入る前に、必要なものがすべて揃っていることを確認してください。
1.  .NET 用の GroupDocs.Watermark: できること[ダウンロード](https://releases.groupdocs.com/Watermark/net/)最新バージョン。
2. 開発環境: Visual Studio のような IDE。
3. C# の基本知識: C# プログラミングに精通していると役立ちます。
4. ウォーターマークを追加する文書: ウォーターマークを追加する Word 文書 (.docx または .doc)。
## 名前空間のインポート
まず、必要な名前空間を C# プロジェクトにインポートする必要があります。これらの名前空間は、GroupDocs.Watermark を操作するために必要なクラスとメソッドへのアクセスを提供します。
```csharp
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
前提条件を満たし、必要な名前空間をインポートしたので、プロセスをステップごとに詳しく見てみましょう。
## ステップ 1: Word 文書をロードする
まず、透かしを追加する Word 文書をロードする必要があります。これは、`Watermarker`一緒にクラス`WordProcessingLoadOptions`.
```csharp
string documentPath = "Your Document Path";
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    //次のステップに進みます
}
```
## ステップ 2: テキストの透かしを作成する
次に、テキストの透かしを作成します。要件に応じて、テキスト、フォント、色、その他のプロパティをカスタマイズできます。
```csharp
TextWatermark watermark = new TextWatermark("Watermark text", new Font("Arial", 19));
watermark.ForegroundColor = Color.Red;
```
## ステップ 3: ウォーターマーク オプションを構成する
特定のページにウォーターマークを適用してロックするには、`WordProcessingWatermarkPagesOptions`。ここでは、透かしを表示するページ番号を指定し、ロック オプションを設定します。
```csharp
WordProcessingWatermarkPagesOptions options = new WordProcessingWatermarkPagesOptions();
options.PageNumbers = new int[] { 1, 3 }; //ページを指定する
options.IsLocked = true; //透かしをロックする
options.LockType = WordProcessingLockType.AllowOnlyComments; //ロックタイプの設定
//パスワードで保護するには
//options.Password = "7654321";
```
## ステップ 4: 文書に透かしを追加する
ウォーターマークとオプションを設定したら、ドキュメントにウォーターマークを追加できるようになります。
```csharp
watermarker.Add(watermark, options);
```
## ステップ 5: ドキュメントを保存する
最後に、ウォーターマークを適用したドキュメントを保存します。適切な出力パスを選択し、ファイルを保存します。
```csharp
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
watermarker.Save(outputFileName);
```
## 結論
おめでとう！ GroupDocs.Watermark for .NET を使用して、ロックされたウォーターマークを Word 文書の特定のページに追加することに成功しました。このチュートリアルでは、ドキュメントの読み込みから透かし入りファイルの保存までの重要な手順をすべて説明しました。これらの手順に従うことで、ドキュメントに安全に透かしを入れて、コンテンツを不正な編集や使用から保護することができます。
詳細については、以下を参照してください。[GroupDocs.Watermark ドキュメント](https://tutorials.groupdocs.com/Watermark/net/) 。ご質問がある場合、またはさらにサポートが必要な場合は、お気軽に次のサイトにアクセスしてください。[サポートフォーラム](https://forum.groupdocs.com/c/watermark/19).
## よくある質問
### .NET 用の GroupDocs.Watermark とは何ですか?
GroupDocs.Watermark for .NET は、開発者が Word、PDF、Excel などのさまざまな種類のドキュメントにウォーターマークを追加できる強力なライブラリです。
### 文書内の複数のページに透かしを適用できますか?
はい、複数のページ番号を指定できます。`PageNumbers`複数のページにウォーターマークを適用する配列。
### ウォーターマークをパスワードで保護するにはどうすればよいですか?
ウォーターマークをパスワードで保護するには、`Password`のプロパティ`WordProcessingWatermarkPagesOptions`.
### 透かしの外観をカスタマイズすることはできますか?
絶対に！ニーズに合わせて、ウォーターマークのテキスト、フォント、色、サイズ、その他のプロパティをカスタマイズできます。
### GroupDocs.Watermark の一時ライセンスはどこで入手できますか?
一時ライセンスは次から取得できます。[ここ](https://purchase.groupdocs.com/temporary-license/).