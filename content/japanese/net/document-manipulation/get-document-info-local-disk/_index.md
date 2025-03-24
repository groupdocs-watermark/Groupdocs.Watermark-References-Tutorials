---
title: ローカルディスクからドキュメント情報を取得
linktitle: ローカルディスクからドキュメント情報を取得
second_title: GroupDocs.Watermark .NET API
description: この包括的なステップバイステップ ガイドでは、GroupDocs for .NET のウォーターマークを使用してドキュメントにウォーターマークを追加、削除、抽出する方法を学びます。
weight: 11
url: /ja/net/document-manipulation/get-document-info-local-disk/
---
## 導入
GroupDocs.Watermark for .NET の使用に関する究極のガイドへようこそ!経験豊富な開発者であっても、初心者であっても、この記事では、この強力なツールを使用してドキュメントに透かしを入れるための基本事項を説明します。最終的には、文書に透かしを埋め込み、文書が確実に保護され、仕様に合わせてブランド化されるプロになれるでしょう。
## 前提条件
ステップバイステップ ガイドに進む前に、満たす必要がある前提条件がいくつかあります。
1.  .NET Framework: システムに .NET Framework がインストールされていることを確認してください。 GroupDocs.Watermark for .NET は、.NET Framework のさまざまなバージョンと互換性があるため、[ドキュメンテーション](https://tutorials.groupdocs.com/Watermark/net/)互換性の詳細については。
2.  GroupDocs.Watermark for .NET ライブラリ: 最新バージョンを次の場所からダウンロードしてインストールします。[ダウンロードページ](https://releases.groupdocs.com/Watermark/net/).
3. 開発環境: 開発環境をセットアップする必要があります。 Visual Studio は、.NET 開発によく選ばれています。
4. C# の基本知識: C# プログラミングの基本を理解すると、例を理解するのに役立ちます。
## 名前空間のインポート
GroupDocs.Watermark for .NET を使用する前に、必要な名前空間をプロジェクトにインポートする必要があります。これは簡単なプロセスであり、ライブラリの機能にアクセスするために不可欠です。
```csharp
using System;
using GroupDocs.Watermark.Common;
```
文書に透かしを入れるプロセスを、明確で管理しやすい手順に分けてみましょう。各ステップは、機能を簡単に理解して実装できるように設計されています。
## ステップ 1: ドキュメントをロードする
最初のステップは、透かしを入れたいドキュメントをロードすることです。これは、`Watermarker`このクラスを使用すると、ドキュメントにアクセスして操作できるようになります。
```csharp
using (Watermarker watermarker = new Watermarker("Your Document Path"))
{
    //ドキュメントがロードされ、透かしを入れる準備ができました
}
```
このステップでは、次のように置き換えます。`"Your Document Path"`ドキュメントへの実際のパスを含めます。これにより、`Watermarker`オブジェクトを使用すると、さまざまな透かし機能にアクセスできるようになります。
## ステップ 2: ドキュメント情報を取得する
透かしを追加する前に、ドキュメントに関する情報を収集することができます。これは、ドキュメントのプロパティに基づいてウォーターマークをカスタマイズする場合に役立ちます。

```csharp
using (Watermarker watermarker = new Watermarker("Your Document Path"))
{
    IDocumentInfo info = watermarker.GetDocumentInfo();
    Console.WriteLine("File type: {0}", info.FileType);
    Console.WriteLine("Number of pages: {0}", info.PageCount);
    Console.WriteLine("Document size: {0} bytes", info.Size);
}
```
このステップでは、`GetDocumentInfo`このメソッドは、ファイル タイプ、ページ数、ドキュメント サイズなどの詳細を取得します。この情報はコンソールに出力されますが、必要に応じてアプリケーションで使用できます。
## ステップ 3: テキストの透かしを追加する
ドキュメントがロードされ、その情報が手元にあるので、次は透かしを追加します。シンプルなテキストの透かしから始めます。

```csharp
using (Watermarker watermarker = new Watermarker("Your Document Path"))
{
    TextWatermark textWatermark = new TextWatermark("Confidential", new Font("Arial", 36));
    textWatermark.ForegroundColor = Color.Red;
    textWatermark.BackgroundColor = Color.Yellow;
    textWatermark.Opacity = 0.5;
    textWatermark.RotateAngle = 45;
    watermarker.Add(textWatermark);
    watermarker.Save("Watermarked Document Path");
}
```
ここで、`TextWatermark`オブジェクトに希望のテキスト、フォント、スタイルを追加します。ニーズに合わせて、色、不透明度、回転角度などのプロパティを調整します。最後に、ウォーターマークがドキュメントに追加され、指定されたパスに保存されます。
## ステップ 4: 画像の透かしを追加する
テキストの透かしは素晴らしいですが、ロゴや別の画像を追加したい場合はどうすればよいでしょうか?この手順では、画像の透かしを追加する方法について説明します。

```csharp
using (Watermarker watermarker = new Watermarker("Your Document Path"))
{
    using (ImageWatermark imageWatermark = new ImageWatermark("Path to Your Image"))
    {
        imageWatermark.Opacity = 0.5;
        imageWatermark.RotateAngle = 30;
        watermarker.Add(imageWatermark);
        watermarker.Save("Watermarked Document Path");
    }
}
```
交換する`"Path to Your Image"`透かし画像へのパスを付けます。不透明度や回転角度などのプロパティを設定して、画像の透かしの外観をカスタマイズします。ウォーターマークを追加して保存するプロセスは、テキスト ウォーターマークのプロセスと似ています。
## ステップ 5: 既存のウォーターマークを削除する
場合によっては、ドキュメントから既存の透かしを削除する必要があるかもしれません。これは、`Remove`によって提供されるメソッド`Watermarker`クラス。

```csharp
using (Watermarker watermarker = new Watermarker("Your Document Path"))
{
    watermarker.Remove(WatermarkType.Text);
    watermarker.Save("Cleaned Document Path");
}
```
ここで、`Remove`メソッドは、ドキュメントからテキストの透かしを削除するために使用されます。ニーズに応じて、画像やテキストなど、削除するさまざまなタイプの透かしを指定できます。変更を確認するには、ドキュメントを新しいパスに保存します。
## ステップ 6: 透かしを抽出する
ドキュメントからウォーターマークを抽出して検査する必要がある場合、GroupDocs.Watermark for .NET を使用するとこれが簡単に可能になります。

```csharp
using (Watermarker watermarker = new Watermarker("Your Document Path"))
{
    IEnumerable<Watermark> watermarks = watermarker.GetWatermarks();
    foreach (Watermark watermark in watermarks)
    {
        Console.WriteLine("Watermark type: {0}", watermark.GetType().Name);
        //各ウォーターマークの追加のプロパティとロジック
    }
}
```
このステップでは、`GetWatermarks`ドキュメント内のすべてのウォーターマークを取得するメソッド。その後、ウォーターマークのリストを繰り返し処理して、そのプロパティを検査したり、必要に応じて追加のアクションを実行したりできます。
## 結論
おめでとう！ GroupDocs.Watermark for .NET を使用して、ドキュメントにウォーターマークを追加、削除、抽出する方法を学習しました。これらのスキルがあれば、ドキュメントを効果的に保護し、ブランド化することができます。覚えておいてください、[ドキュメンテーション](https://tutorials.groupdocs.com/Watermark/net/)より詳細な情報や高度な機能が必要な場合には、いつでも利用できます。
## よくある質問
### GroupDocs.Watermark for .NET はどの .NET バージョンでも使用できますか?
はい、GroupDocs.Watermark for .NET はさまざまな .NET Framework バージョンと互換性があります。チェックしてください[ドキュメンテーション](https://tutorials.groupdocs.com/Watermark/net/)具体的には。
### .NET 用の GroupDocs.Watermark はどこでダウンロードできますか?
最新バージョンはからダウンロードできます。[ダウンロードページ](https://releases.groupdocs.com/Watermark/net/).
### 仮免許はどうやって取得するのですか？
一時ライセンスは以下から取得できます。[一時ライセンスのページ](https://purchase.groupdocs.com/temporary-license/).
### 無料トライアルはありますか?
はい、にアクセスして無料トライアルを開始できます。[無料お試しページ](https://releases.groupdocs.com/).
### 問題が発生した場合はどこでサポートを受けられますか?
サポートは次のサイトで利用できます。[GroupDocs ウォーターマーク フォーラム](https://forum.groupdocs.com/c/watermark/19).