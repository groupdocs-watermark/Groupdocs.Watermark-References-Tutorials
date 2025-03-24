---
title: 画像の透かしを追加する
linktitle: 画像の透かしを追加する
second_title: GroupDocs.Watermark .NET API
description: 詳細なステップバイステップのチュートリアルで、GroupDocs.Watermark for .NET を使用してドキュメントに画像ウォーターマークを追加する方法を学びます。
weight: 11
url: /ja/net/image-watermarkings/add-image-watermark/
---
## 導入
GroupDocs.Watermark for .NET を使用して画像ウォーターマークを追加するためのこの包括的なガイドへようこそ。透かしは、文書や画像を不正使用から保護する強力な方法であり、知的財産の安全性を確保します。このチュートリアルでは、環境のセットアップからドキュメントへのウォーターマークの適用までのプロセス全体を説明します。経験豊富な開発者であっても、初心者であっても、このガイドは役に立ち、理解しやすいものであることがわかります。
## 前提条件
チュートリアルに入る前に、必要なものがすべて揃っていることを確認してください。
- 開発環境: Visual Studio または任意の .NET 互換 IDE
- .NET Framework: .NET Framework 4.0以降
- GroupDocs.Watermark for .NET: 次の場所からダウンロードできます。[GroupDocs Web サイト](https://releases.groupdocs.com/Watermark/net/)
- 画像ファイル: 透かしとして使用する画像ファイル (例:`watermark.jpg`)
- ドキュメント ファイル: ウォーターマークを追加するドキュメント (例:`presentation.pptx`)
## 名前空間のインポート
まず、必要な名前空間をプロジェクトにインポートする必要があります。これは、GroupDocs の機能にアクセスするために不可欠です。
```csharp
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
このセクションでは、画像透かしを追加するプロセスを明確で管理しやすい手順に分けて説明します。各手順を慎重に実行して、文書に透かしを正常に挿入します。
## ステップ 1: 環境をセットアップする
まず、開発環境が適切に設定されていることを確認します。 GroupDocs.Watermark ライブラリを次の場所からダウンロードしてインストールします。[GroupDocs Web サイト](https://releases.groupdocs.com/Watermark/net/).
1. Visual Studio でプロジェクトを開きます。
2. ソリューション エクスプローラーでプロジェクトを右クリックします。
3. 「NuGet パッケージの管理...」を選択します。
4. 検索する`GroupDocs.Watermark`そしてそれをインストールします。
## ステップ 2: ファイル パスを定義する
次に、入力ドキュメントと出力ディレクトリのパスを定義する必要があります。これは、プログラムが操作する必要のあるファイルを見つけるのに役立ちます。
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
交換する`"Your Document Path"`そして`"Your Document Directory"`ドキュメントへの実際のパスと目的の出力ディレクトリを指定します。
## ステップ 3: ウォーターマーカーを初期化する
ここで、初期化します`Watermarker`クラスをドキュメントへのパスに置き換えます。このクラスは、透かしプロセスの管理を担当します。
```csharp
using (Watermarker watermarker = new Watermarker(documentPath))
{
    //この using ブロック内の次のステップに進みます。
}
```
## ステップ 4: 画像透かしを作成する
以内`Watermarker`ブロック、のインスタンスを作成します。`ImageWatermark`ウォーターマーク画像へのパスを使用するクラス。このクラスは、透かしとして使用する画像を表します。
```csharp
using (ImageWatermark watermark = new ImageWatermark("path/to/your/watermark.jpg"))
{
    //この using ブロック内の次のステップに進みます。
}
```
## ステップ 5: 文書に透かしを追加する
とともに`ImageWatermark`インスタンスの準備ができたら、それを使用してドキュメントに追加します`Add`の方法`Watermarker`クラス。
```csharp
watermarker.Add(watermark);
```
## ステップ 6: ドキュメントを保存する
最後に、透かしを入れたドキュメントを指定した出力ディレクトリに保存します。この手順により、変更が新しいファイルに確実に書き込まれます。
```csharp
watermarker.Save(outputFileName);
```
## 結論
おめでとう！ GroupDocs.Watermark for .NET を使用して、ドキュメントに画像ウォーターマークを正常に追加しました。このステップバイステップのガイドに従うことで、カスタム透かしを使用してドキュメントを簡単に保護できます。ウォーターマークは、デジタル資産を不正使用から守るための重要なステップであることを忘れないでください。

## よくある質問
### GroupDocs.Watermark ではどのようなファイル形式がサポートされていますか?
GroupDocs.Watermark は、PDF、DOCX、PPTX、XLSX、JPEG や PNG などの画像ファイルなど、幅広いファイル形式をサポートしています。
### GroupDocs.Watermark を .NET Core で使用できますか?
はい、GroupDocs.Watermark は .NET Framework と .NET Core の両方と互換性があります。
### GroupDocs.Watermark の一時ライセンスを取得するにはどうすればよいですか?
一時ライセンスは以下から取得できます。[GroupDocs Web サイト](https://purchase.groupdocs.com/temporary-license/).
### 1 つのドキュメントに複数の透かしを追加することはできますか?
絶対に！を呼び出すことで、複数のウォーターマークを追加できます。`Add`メソッドを異なるウォーターマーク インスタンスで複数回実行します。
### 他の例やドキュメントはどこで入手できますか?
その他の例と詳細なドキュメントについては、次のサイトを参照してください。[GroupDocs.Watermark ドキュメント](https://tutorials.groupdocs.com/Watermark/net/).