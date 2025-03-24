---
title: ストリームからドキュメントをロード
linktitle: ストリームからドキュメントをロード
second_title: GroupDocs.Watermark .NET API
description: このガイドでは、GroupDocs.Watermark for .NET を使用してドキュメントにウォーターマークを追加する方法を学習します。ドキュメントのセキュリティを強化したい開発者に最適です。
weight: 11
url: /ja/net/document-loadings/load-document-from-stream/
---

# ストリームからドキュメントをロード

## 導入
.NET を使用してドキュメントにウォーターマークをシームレスに追加したいと考えていますか?これ以上探さない！ GroupDocs.Watermark for .NET は、さまざまなドキュメント形式のウォーターマークを管理できる強力で使いやすいライブラリです。 PDF、Word 文書、画像のいずれを扱う場合でも、このツールが役に立ちます。このチュートリアルでは、ストリームからドキュメントを読み込み、ウォーターマークを追加するプロセスを段階的に説明します。それでは、早速入っていきましょう！
## 前提条件
始める前に、次の設定がされていることを確認してください。
1. Visual Studio: Visual Studio の最新バージョンはどれも正常に動作します。
2. .NET Framework: .NET Framework 4.0 以降がインストールされていることを確認してください。
3.  GroupDocs.Watermark for .NET: 次からダウンロードできます。[ここ](https://releases.groupdocs.com/Watermark/net/).
4. C# の基礎知識: C# とオブジェクト指向プログラミングの概念に精通していると役立ちます。

## 名前空間のインポート
プロジェクトで GroupDocs.Watermark を使用するには、必要な名前空間をインポートする必要があります。これにより、ライブラリの機能に問題なくアクセスできるようになります。
```csharp
using System;
using System.IO;
using GroupDocs.Watermark.Watermarks;
```
## ステップ 1: プロジェクトのセットアップ
まず最初に、Visual Studio でプロジェクトを設定する必要があります。その方法は次のとおりです。
1. 新しいプロジェクトを作成する: Visual Studio を開き、新しい C# コンソール アプリケーション プロジェクトを作成します。
2.  GroupDocs.Watermark をインストールする: NuGet パッケージ マネージャーを介して GroupDocs.Watermark ライブラリをインストールします。単純に検索してください`GroupDocs.Watermark`そしてそれをインストールします。
## ステップ 2: ドキュメント パスを定義する
次に、ドキュメントのパスと、透かし入りドキュメントが保存される出力ファイルのパスを定義する必要があります。
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
```
交換する`"Your Document Path"`透かしを入れたいドキュメントの実際のパスと`"Your Document Directory"`を、透かし入りのドキュメントを保存するディレクトリに置き換えます。
## ステップ 3: ストリームからドキュメントをロードする
次に、ストリームからドキュメントをロードしましょう。これには、ドキュメントをストリームとして開き、`Watermarker` GroupDocs.Watermark ライブラリのクラスを使用して管理します。
```csharp
using (Stream document = File.OpenRead(documentPath))
using (Watermarker watermarker = new Watermarker(document))
{
    //ウォーターマークを管理するコードはここに記述されます
}
```
このコード スニペットにより、ドキュメントがストリームとして開かれ、`Watermarker`クラスはこのストリームで初期化されます。の`using`ステートメントにより、リソースが使用後に適切に処分されることが保証されます。
## ステップ 4: ウォーターマークを作成して追加する
GroupDocs.Watermark を使用すると、ウォーターマークの作成が簡単になります。この例では、単純なテキストの透かしを作成します。
```csharp
TextWatermark watermark = new TextWatermark("Test watermark", new Font("Arial", 12));
watermarker.Add(watermark);
```
ここでは、`TextWatermark` 「テストウォーターマーク」というテキストを含むオブジェクトを作成し、フォントの詳細を指定します。次に、この透かしをドキュメントに追加します。`Add`の方法`Watermarker`クラス。
## ステップ 5: 透かし入りのドキュメントを保存する
最後に、透かしを入れたドキュメントを指定した出力パスに保存します。
```csharp
watermarker.Save(outputFileName);
```
このコードは、新しく追加された透かしを含むドキュメントを保存します。`outputFileName`前に定義したパス。

## 結論
おめでとう！ GroupDocs.Watermark for .NET を使用してドキュメントにウォーターマークを追加することに成功しました。このライブラリを使用すると、さまざまなドキュメント形式にわたるウォーターマークの管理が驚くほど簡単になります。テキスト、画像、その他の種類のウォーターマークを追加する必要がある場合でも、GroupDocs.Watermark には必要なツールが揃っています。忘れずにチェックしてください[ドキュメンテーション](https://tutorials.groupdocs.com/Watermark/net/)より高度な機能とカスタマイズ オプションについては、
## よくある質問
### GroupDocs.Watermark for .NET を使用して追加できるウォーターマークの種類は何ですか?
テキストの透かし、画像の透かし、さらには複雑な形状やロゴを追加できます。このライブラリは、幅広いカスタマイズ オプションをサポートしています。
### GroupDocs.Watermark を使用してドキュメントからウォーターマークを削除できますか?
はい、GroupDocs.Watermark を使用すると、ドキュメントから既存のウォーターマークを削除することもできます。
### GroupDocs.Watermark に利用できる無料トライアルはありますか?
はい、以下から無料試用版をダウンロードできます。[ここ](https://releases.groupdocs.com/).
### GroupDocs.Watermark のライセンスを購入するにはどうすればよいですか?
ライセンスは次から直接購入できます。[GroupDocs Web サイト](https://purchase.groupdocs.com/buy).
### 問題が発生した場合はどこでサポートを受けられますか?
サポートが必要な場合は、次のサイトにアクセスしてください。[GroupDocs.Watermark サポート フォーラム](https://forum.groupdocs.com/c/watermark/19).