---
title: ドキュメントプレビューの生成
linktitle: ドキュメントプレビューの生成
second_title: GroupDocs.Watermark .NET API
description: このガイドでは、GroupDocs.Watermark for .NET を使用してドキュメント プレビューを生成する方法を学習します。ドキュメントのセキュリティと管理を簡単に強化します。
type: docs
weight: 10
url: /ja/net/document-manipulation/generate-document-preview/
---
## 導入
デジタル文書管理の世界では、透かしは文書のセキュリティと信頼性を確保する上で重要な役割を果たします。 GroupDocs.Watermark for .NET は、開発者がドキュメントにウォーターマークを簡単に追加できる強力なツールです。このチュートリアルでは、GroupDocs.Watermark for .NET を使用してドキュメント プレビューを生成するプロセスについて説明します。経験豊富な開発者であっても、初心者であっても、このガイドは目標を達成するための包括的な段階的なプロセスを提供します。
## 前提条件
実装に入る前に、開始するために必要なものがすべて揃っていることを確認してください。
- C# と .NET Framework の基本的な理解。
- Visual Studio がマシンにインストールされていること。
- .NET ライブラリの GroupDocs.Watermark。あなたはできる[ここからダウンロードしてください](https://releases.groupdocs.com/Watermark/net/).
- GroupDocs.Watermark の有効なライセンス。どちらでも購入できます[ここ](https://purchase.groupdocs.com/buy)または、[仮免許証](https://purchase.groupdocs.com/temporary-license/)評価目的のため。
## 名前空間のインポート
プロジェクトで GroupDocs.Watermark の使用を開始するには、必要な名前空間をインポートする必要があります。これを行うには、次の using ディレクティブをコードに追加します。
```csharp
using System;
using System.IO;
using GroupDocs.Watermark.Options;
```
これらの名前空間は、透かしの挿入とドキュメント プレビューの生成に必要なクラスとメソッドへのアクセスを提供します。

ドキュメント プレビューを生成するプロセスを、シンプルでわかりやすい手順に分割してみましょう。
## ステップ 1: プロジェクトをセットアップする
まず最初に、Visual Studio で .NET プロジェクトを設定します。プロジェクトがまだない場合は、次の手順に従って新しいプロジェクトを作成します。
1. Visual Studio を開きます。
2. 「新しいプロジェクトの作成」をクリックします。
3. 「コンソール アプリ (.NET Core)」を選択し、「次へ」をクリックします。
4. プロジェクトに名前を付け、保存する場所を選択して、[作成] をクリックします。
## ステップ 2: GroupDocs.Watermark for .NET をインストールする
プロジェクトで GroupDocs.Watermark を使用するには、ライブラリをインストールする必要があります。これは、NuGet パッケージ マネージャーを使用して実行できます。
1. ソリューション エクスプローラーでプロジェクトを右クリックします。
2. 「NuGet パッケージの管理」を選択します。
3. [参照] タブで「GroupDocs.Watermark」を検索します。
4. 「インストール」をクリックしてライブラリをプロジェクトに追加します。
あるいは、パッケージ マネージャー コンソール経由でインストールすることもできます。
```powershell
Install-Package GroupDocs.Watermark
```
## ステップ 3: ドキュメントのパスと出力ディレクトリを定義する
プレビューを生成する前に、プレビューするドキュメントのパスとプレビュー画像が保存されるディレクトリを指定する必要があります。
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
```
「Your Document Path」をドキュメントへのパスに置き換え、「Your Document Directory」をプレビュー イメージを保存するディレクトリに置き換えます。
## ステップ 4: ウォーターマーカー オブジェクトを初期化する
のインスタンスを作成します。`Watermarker`ドキュメントのパスをそのコンストラクターに渡すことによって、クラスを作成します。このオブジェクトは、すべての透かし処理を実行するために使用されます。
```csharp
using (Watermarker watermarker = new Watermarker(documentPath))
{
    //コードはここにあります
}
```
## ステップ 5: ストリーム処理用のデリゲート メソッドを作成する
プレビューを生成するには、ストリームを作成および解放するためのデリゲート メソッドを定義する必要があります。これらのメソッドは、ドキュメントの各ページのストリームの作成と解放を処理します。
```csharp
CreatePageStream createPageStreamDelegate = delegate(int number)
{
    string previewImageFileName = Path.Combine(outputDirectory, string.Format("page{0}.png", number));
    return File.OpenWrite(previewImageFileName);
};
ReleasePageStream releasePageStreamDelegate = delegate(int number, Stream stream)
{
    stream.Close();
};
```
の`createPageStreamDelegate`メソッドはドキュメントの各ページにストリームを作成しますが、`releasePageStreamDelegate`このメソッドは、プレビューの生成後にストリームを閉じます。
## ステップ 6: プレビュー オプションを構成する
次に、のインスタンスを作成してプレビュー オプションを構成します。`PreviewOptions`クラス。デリゲート メソッドを指定し、プレビュー形式を PNG に設定します。プレビューに含めるページを指定することもできます。
```csharp
PreviewOptions previewOptions = new PreviewOptions(createPageStreamDelegate, releasePageStreamDelegate)
{
    PreviewFormat = PreviewOptions.PreviewFormats.PNG,
    PageNumbers = new[] { 1, 2 }
};
```
この例では、ドキュメントの最初の 2 ページのプレビューを生成しています。
## ステップ 7: ドキュメントのプレビューを生成する
最後に、`GeneratePreview`のメソッド`Watermarker`オブジェクト、構成されたものを渡します`PreviewOptions`。これにより、プレビュー イメージが生成され、指定されたディレクトリに保存されます。
```csharp
watermarker.GeneratePreview(previewOptions);
```
## 結論
GroupDocs.Watermark for .NET を使用したドキュメント プレビューの生成は、わずか数行のコードで実行できる簡単なプロセスです。このガイドで概説されている手順に従うことで、プロジェクトを簡単にセットアップし、必要なオプションを構成し、ドキュメントのプレビューを生成できます。この強力なライブラリは、透かしプロセスを簡素化するだけでなく、透かしを管理および操作するための堅牢な機能も提供します。
ご質問がある場合、またはさらにサポートが必要な場合は、お気軽に次のサイトにアクセスしてください。[GroupDocs.Watermark サポート フォーラム](https://forum.groupdocs.com/c/watermark/19)または、を参照してください。[ドキュメンテーション](https://reference.groupdocs.com/Watermark/net/).
## よくある質問
### GroupDocs.Watermark for .NET ではどのようなファイル形式がサポートされていますか?
 GroupDocs.Watermark for .NET は、PDF、DOCX、PPTX、XLSX などを含む幅広いファイル形式をサポートしています。サポートされている形式の完全なリストについては、を参照してください。[ドキュメンテーション](https://reference.groupdocs.com/Watermark/net/).
### 透かしの外観をカスタマイズできますか?
はい、GroupDocs.Watermark を使用すると、テキスト、画像、図形の透かしなどの透かしの外観を完全にカスタマイズできます。フォント、色、サイズ、透明度などのプロパティを調整できます。
### 試用版はありますか?
はい、入手できます[無料トライアル](https://releases.groupdocs.com/)購入前に GroupDocs.Watermark for .NET の機能を評価してください。
### GroupDocs.Watermark のライセンスを購入するにはどうすればよいですか?
 GroupDocs.Watermark のライセンスを購入できます。[ここ](https://purchase.groupdocs.com/buy)。さまざまなニーズに合わせてさまざまなライセンス オプションを利用できます。
### GroupDocs.Watermark を商用プロジェクトで使用できますか?
はい、有効なライセンスがあれば、商用プロジェクトで GroupDocs.Watermark を使用できます。ライセンス契約条件を必ず確認してください。[購入ページ](https://purchase.groupdocs.com/buy).