---
title: ドキュメントを指定した場所に保存
linktitle: ドキュメントを指定した場所に保存
second_title: GroupDocs.Watermark .NET API
description: このステップバイステップのガイドでは、GroupDocs.Watermark for .NET を使用してドキュメントにウォーターマークを簡単に追加する方法を学びます。ドキュメントのセキュリティを強化します。
type: docs
weight: 11
url: /ja/net/document-savings/save-document-specified-location/
---
## 導入
デジタル時代において、文書の安全性はこれまで以上に重要になっています。透かしは、ドキュメントを不正使用から保護する効果的な方法です。 GroupDocs.Watermark for .NET は、ドキュメントにウォーターマークを追加するための堅牢なソリューションを提供します。アプリケーションに透かしを統合しようとしている開発者であっても、ドキュメントの保護に興味がある開発者であっても、このチュートリアルではそのプロセスを段階的に説明します。
## 前提条件
チュートリアルに入る前に、次の前提条件が満たされていることを確認してください。
- .NET 開発環境: Visual Studio またはその他の .NET 開発環境がインストールされていることを確認します。
-  GroupDocs.Watermark for .NET Library: ライブラリをダウンロードしてプロジェクト内で参照します。[.NET 用の GroupDocs.Watermark をダウンロード](https://releases.groupdocs.com/Watermark/net/)
- C# プログラミングの基礎知識: 基本的な C# プログラミングの概念を理解すると役立ちます。
- ドキュメントにウォーターマークを適用: ウォーターマークを適用するサンプルドキュメントを用意します。
## 名前空間のインポート
例を始める前に、必要な名前空間をインポートする必要があります。コード ファイルの先頭に次の using ステートメントを追加します。
```csharp
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
GroupDocs.Watermark for .NET を使用してドキュメントにウォーターマークを追加するプロセスを管理可能な手順に分割してみましょう。ウォーターマークを正常に適用し、ドキュメントを指定した場所に保存するには、次の手順に従います。
## ステップ 1: プロジェクトをセットアップする
まず、Visual Studio で新しい .NET プロジェクトを作成します。簡単にするためにコンソール アプリを選択できます。
1. Visual Studio を開きます。
2. 選択する`File`>`New`>`Project`.
3. 選ぶ`Console App (.NET Core)`または`Console App (.NET Framework)`.
4. プロジェクトに名前を付けてクリックします`Create`.

## ステップ 2: 文書と透かしテキストを準備する
### ドキュメントパスの指定
透かしを入れるドキュメントのパスを定義します。この例では、プレースホルダー パスを使用してみましょう。
```csharp
string documentPath = "Your Document Path";
```
### 出力パスの定義
透かし入りのドキュメントを保存する出力パスを設定します。
```csharp
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
```
## ステップ 3: ドキュメントをロードする
使用`Watermarker`ドキュメントをロードするクラス。このクラスは、ウォーターマークを追加、削除、編集するためのメソッドを提供します。
```csharp
using (Watermarker watermarker = new Watermarker(documentPath))
{
    //ここに透かしロジックを追加します
}
```
## ステップ 4: ウォーターマークを作成して追加する

### テキスト透かしの作成
インスタンス化する`TextWatermark`必要なテキストとフォントのプロパティを含むオブジェクトを作成します。
```csharp
TextWatermark watermark = new TextWatermark("Test watermark", new Font("Arial", 12));
```
### 文書に透かしを追加する
作成したウォーターマークをドキュメントに追加するには、`Add`の方法`Watermarker`クラス。
```csharp
watermarker.Add(watermark);
```
## ステップ 5: ドキュメントを保存する
最後に、ウォーターマークを含むドキュメントを指定した場所に保存します。
```csharp
watermarker.Save(outputFileName);
```
## 結論
GroupDocs Watermark for .NET を使用してドキュメントにウォーターマークを付けることは、ドキュメントのセキュリティを大幅に強化できる簡単なプロセスです。このステップバイステップのガイドに従うことで、ドキュメントに透かしを簡単に追加し、目的の場所に保存できます。知的財産の保護、ドキュメントの信頼性の確保、または単にプロフェッショナルなタッチの追加を行う場合でも、GroupDocs.Watermark for .NET は必要なツールを提供します。
## よくある質問
### GroupDocs.Watermark for .NET で画像をウォーターマークとして使用できますか?
はい、GroupDocs for .NET ではテキストと画像の両方のウォーターマークを使用できます。このライブラリは、ニーズに合わせてさまざまなタイプのウォーターマークをサポートしています。
### GroupDocs.Watermark for .NET に利用できる無料試用版はありますか?
はい、次のサイトから無料試用版をダウンロードできます。[Webサイト](https://releases.groupdocs.com/).
### GroupDocs.Watermark for .NET のライセンスを購入するにはどうすればよいですか?
からライセンスを購入できます。[購入ページ](https://purchase.groupdocs.com/buy).
### GroupDocs.Watermark for .NET はバッチ透かしをサポートしていますか?
はい、ドキュメントのリストを繰り返し処理してウォーターマークを適用することで、バッチ プロセスで複数のドキュメントにウォーターマークを付けることができます。
### GroupDocs.Watermark for .NET のサポートはどこで受けられますか?
サポートは次のサイトで利用できます。[GroupDocs フォーラム](https://forum.groupdocs.com/c/watermark/19).