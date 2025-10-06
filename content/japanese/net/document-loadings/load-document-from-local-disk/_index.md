---
title: ローカルディスクからドキュメントをロード
linktitle: ローカルディスクからドキュメントをロード
second_title: GroupDocs.Watermark .NET API
description: Groupdocs for .NET を使用してドキュメントを保護および管理します。ウォーターマークをシームレスに追加するには、詳細なガイドに従ってください。
weight: 10
url: /ja/net/document-loadings/load-document-from-local-disk/
type: docs
---
# ローカルディスクからドキュメントをロード

## 導入
今日のデジタル時代において、ドキュメントの透かしは、コンテンツの保護、所有権の主張、機密性を確保するために不可欠です。 Groupdocs.Watermark for .NET は、開発者がさまざまなドキュメント形式でウォーターマークを追加、検索、管理できる強力なライブラリです。このチュートリアルでは、Groupdocs.Watermark for .NET を使用してドキュメントにウォーターマークを追加するプロセスを、詳細なステップバイステップの手順とともに説明します。
## 前提条件
実装に入る前に、次のものが揃っていることを確認してください。
1. Visual Studio がインストールされている: Visual Studio または別の互換性のある .NET IDE が必要です。
2.  Groupdocs.Watermark for .NET: からライブラリをダウンロードします。[ダウンロードリンク](https://releases.groupdocs.com/Watermark/net/).
3. .NET Framework: .NET Framework 4.6.1 以降がインストールされていることを確認してください。
4. サンプル ドキュメント: 透かし入れプロセスをテストするためのサンプル ドキュメントを準備します。
## 名前空間のインポート
まず、必要な名前空間をプロジェクトにインポートする必要があります。これらは、透かし入れに必要なクラスとメソッドにアクセスするために不可欠です。
```csharp
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## ステップ 1: ローカル ディスクからドキュメントをロードする
まず、ローカル ディスクからドキュメントをロードする必要があります。この文書に透かしを追加します。
透かしを入れるドキュメントのパスを定義します。
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
```
## ステップ 2: ロード オプションを初期化する
次に、ロード オプションを初期化します。たとえば、Word 文書を使用している場合は、次のようにします。`WordProcessingLoadOptions`.
```csharp
var loadOptions = new WordProcessingLoadOptions();
```
## ステップ 3: ウォーターマーカーの作成と構成
ここで、のインスタンスを作成します。`Watermarker`クラス。このインスタンスは、ウォーターマークを管理し、ドキュメントに適用するために使用されます。
```csharp
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    //このブロックには、ウォーターマークを追加して保存するためのさらなる手順が含まれます
}
```
## ステップ 4: 透かしを作成する
テキストの透かしを作成します。この透かしには、選択した任意のテキストを含めることができます。ここでは「テストウォーターマーク」を使用します。
```csharp
TextWatermark watermark = new TextWatermark("Test watermark", new Font("Arial", 12));
```
## ステップ 5: 文書に透かしを追加する
作成したウォーターマークをドキュメントに追加するには、`Add`の方法`Watermarker`クラス。
```csharp
watermarker.Add(watermark);
```
## ステップ 6: 透かし入りのドキュメントを保存する
最後に、透かしを入れたドキュメントを指定したパスに保存します。
```csharp
watermarker.Save(outputFileName);
```

## 結論
Groupdocs for .NET を使用してドキュメントにウォーターマークを追加するのは簡単かつ効率的です。このガイドでは、環境のセットアップから透かし入りのドキュメントの保存までのプロセス全体を説明します。この強力なツールを使用すると、ドキュメントが保護され、知的財産が安全であることを確認できます。 
詳細については、[ドキュメンテーション](https://tutorials.groupdocs.com/Watermark/net/)問題が発生した場合は、[サポートフォーラム](https://forum.groupdocs.com/c/watermark/19)助けを求めるのに最適な場所です。 
## よくある質問
### 透かしにカスタム フォントを使用できますか?
はい、Groupdocs はカスタム フォントをサポートしています。システムにインストールされている任意のフォントを指定できます。
### どのような種類のドキュメントがサポートされていますか?
Groupdocs.Watermark は、Word、Excel、PDF、PowerPoint などを含む幅広いドキュメント形式をサポートしています。
### 文書から透かしを削除するにはどうすればよいですか?
使用できます`Remove`によって提供されるメソッド`Watermarker`ウォーターマークを削除するクラス。
### 画像に透かしを追加することは可能ですか?
はい、画像の透かしを追加するには、`ImageWatermark`クラス。
### Groupdocs.Watermark を無料で試すことはできますか?
もちろん、ダウンロードできます[無料トライアル](https://releases.groupdocs.com/)購入前にライブラリを評価してください。