---
title: Word ドキュメントのすべてのページにロックされた透かしを追加する
linktitle: Word ドキュメントのすべてのページにロックされた透かしを追加する
second_title: GroupDocs.Watermark .NET API
description: Groupdocs.Watermark for .NET を使用してロックされたウォーターマークを追加し、ドキュメントを保護します。簡単に実装するには、ステップバイステップのガイドに従ってください。
weight: 11
url: /ja/net/word-processing-watermarkings/add-locked-watermark-all-pages-word-docs/
---

# Word ドキュメントのすべてのページにロックされた透かしを追加する

## 導入
ドキュメントに透かしを追加することは、コンテンツを保護しブランド化する上で重要なステップです。不正使用を防止する場合でも、単にプロフェッショナルな雰囲気を加える場合でも、ウォーターマークはさまざまな目的に役立ちます。このチュートリアルでは、Groupdocs.Watermark for .NET を使用して、ロックされたウォーターマークを Word 文書のすべてのページに追加するプロセスを説明します。
## 前提条件
ステップバイステップのガイドに入る前に、必要なものがすべて揃っていることを確認してください。
1. Groupdocs.Watermark for .NET: 最新バージョンを次からダウンロードします。[ここ](https://releases.groupdocs.com/Watermark/net/).
2. .NET Framework: マシンに .NET Framework がインストールされていることを確認します。
3. 開発環境: Visual Studio などの開発環境。
4. ライセンス: を選択できます。[無料トライアル](https://releases.groupdocs.com/)または購入する[仮免許証](https://purchase.groupdocs.com/temporary-license/).
## 名前空間のインポート
まず最初に、必要な名前空間をプロジェクトにインポートする必要があります。これらは、Groupdocs.Watermark によって提供されるクラスとメソッドにアクセスするために不可欠です。
```csharp
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## ステップ 1: プロジェクトをセットアップする

開発環境を開き、新しい .NET プロジェクトを作成します。これは、コンソール アプリケーションでも、ニーズに合ったその他の種類でもかまいません。

Groupdocs.Watermark パッケージをプロジェクトに追加する必要があります。これは、NuGet パッケージ マネージャーを介して実行できます。 NuGet パッケージ マネージャー コンソールで次のコマンドを実行します。
```sh
Install-Package GroupDocs.Watermark
```
## ステップ 2: Word 文書をロードする
### ドキュメントパスを定義する
Word 文書へのパスを指定します。これが透かしを追加するドキュメントになります。
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
```
### ロードオプションの設定
のインスタンスを作成します`WordProcessingLoadOptions`特定のオプションを使用して Word 文書をロードします。
```csharp
var loadOptions = new WordProcessingLoadOptions();
```
## ステップ 3: ウォーターマークを作成する
### ウォーターマーカーの初期化
を使用して、`Watermarker`クラスで、指定されたロード オプションを使用してドキュメントをロードします。
```csharp
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    //さらなるステップはこの using ブロック内で行われます
}
```
### ウォーターマークのプロパティを定義する
を作成します`TextWatermark`希望のテキスト、フォント、色のインスタンスを作成します。
```csharp
TextWatermark watermark = new TextWatermark("Watermark text", new Font("Arial", 19));
watermark.ForegroundColor = Color.Red;
```
## ステップ 4: すべてのページにウォーターマークを適用する
### 透かしオプションの設定
定義する`WordProcessingWatermarkPagesOptions`そして、`IsLocked`ウォーターマークをロックするには、プロパティを true に設定します。これにより、透かしが簡単に削除されなくなります。
```csharp
WordProcessingWatermarkPagesOptions options = new WordProcessingWatermarkPagesOptions();
options.IsLocked = true;
options.LockType = WordProcessingLockType.AllowOnlyFormFields;
```
### オプション: パスワード保護の追加
セキュリティをさらに強化したい場合は、ウォーターマークにパスワードを設定できます。
```csharp
//パスワードで保護するには
//options.Password = "7654321";
```
### 透かしを追加する
使用`Add`の方法`Watermarker`クラスを使用して、指定されたオプションを使用してドキュメントにウォーターマークを追加します。
```csharp
watermarker.Add(watermark, options);
```
## ステップ 5: ドキュメントを保存する
最後に、変更したドキュメントを指定した出力ファイルに保存します。
```csharp
watermarker.Save(outputFileName);
```

## 結論
次の手順に従うと、Groupdocs.Watermark for .NET を使用して Word 文書のすべてのページにロックされたウォーターマークを簡単に追加できます。これは、ドキュメントを不正使用から保護するだけでなく、コンテンツにプロフェッショナルな雰囲気を加えることができます。 Groupdocs.Watermark は、透かしのニーズに対応する包括的なソリューションを提供し、文書の安全性とブランド性を確保します。
## よくある質問
### テキストの代わりに画像を透かしとして使用できますか?
はい、Groupdocs のウォーターマークはテキストと画像の両方のウォーターマークをサポートしています。交換できます`TextWatermark`と`ImageWatermark`そして画像を指定します。
### 透かしの位置をカスタマイズすることはできますか?
絶対に！次のようなプロパティを使用して透かしの位置を設定できます。`HorizontalAlignment`そして`VerticalAlignment`.
### ドキュメントの異なるページに異なる透かしを適用できますか?
はい、次を使用して特定のページのウォーターマークをカスタマイズできます。`PageIndex`のプロパティ`WordProcessingWatermarkPagesOptions`.
### Groupdocs.Watermark は Word 以外の文書形式をサポートしていますか?
はい、Groupdocs は PDF、Excel、PowerPoint などのさまざまな形式をサポートしています。
### Groupdocs.Watermark を使用するためのシステム要件は何ですか?
.NET Framework がインストールされたシステムと Visual Studio などの開発環境が必要です。