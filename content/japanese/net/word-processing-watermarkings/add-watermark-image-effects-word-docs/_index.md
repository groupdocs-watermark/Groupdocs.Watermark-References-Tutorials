---
title: Word ドキュメントに画像効果を使用して透かしを追加する
linktitle: Word ドキュメントに画像効果を使用して透かしを追加する
second_title: GroupDocs.Watermark .NET API
description: GroupDocs.Watermark for .NET を使用して、画像効果のあるウォーターマークを Word 文書に追加する方法を学びます。素晴らしい結果を得るには、ステップバイステップのガイドに従ってください。
weight: 19
url: /ja/net/word-processing-watermarkings/add-watermark-image-effects-word-docs/
type: docs
---
# Word ドキュメントに画像効果を使用して透かしを追加する

## 導入
目を引く透かしを使用して、Word 文書に華やかさを加えたいと考えていますか? GroupDocs.Watermark for .NET があなたをサポートします。この包括的なガイドでは、GroupDocs for .NET を使用して、素晴らしい画像効果を持つウォーターマークを Word 文書に追加するプロセスについて説明します。経験豊富な開発者でも初心者でも、このステップバイステップのチュートリアルを読むと、プロセスが簡単になります。
## 前提条件
チュートリアルに進む前に、次の前提条件を満たしていることを確認してください。
- C# プログラミングの基本知識: .NET を使用するため、C# に精通していることが不可欠です。
- Visual Studio: .NET 開発用にインストールおよびセットアップされています。
-  GroupDocs.Watermark for .NET: 次からダウンロードしてインストールします。[ここ](https://releases.groupdocs.com/Watermark/net/).
- 透かしを入れるドキュメント: 透かしを適用する Word ドキュメント。
- ウォーターマーク用の画像: ウォーターマークとして使用する画像ファイル。
前提条件を整理したので、チュートリアルに進みましょう。
## 名前空間のインポート
まず、GroupDocs.Watermark for .NET の使用を開始するために必要な名前空間をインポートしましょう。
```csharp
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
これらの名前空間は、透かしを追加し、画像効果を適用するために必要なクラスとメソッドを提供します。
## ステップ 1: プロジェクトをセットアップする
まず、Visual Studio で新しいプロジェクトを作成します。これを行うには、Visual Studio を開いて [新しいプロジェクトの作成] を選択し、C# コンソール アプリ (.NET Core または .NET Framework) を選択します。プロジェクトに名前を付けて、「作成」をクリックします。
## ステップ 2: GroupDocs.Watermark for .NET をインストールする
GroupDocs.Watermark をインストールするには、NuGet パッケージ マネージャーを使用できます。ソリューション エクスプローラーでプロジェクトを右クリックし、[NuGet パッケージの管理] を選択し、「GroupDocs.Watermark」を検索してインストールします。
あるいは、次のコマンドを使用して、パッケージ マネージャー コンソール経由でインストールすることもできます。
```powershell
Install-Package GroupDocs.Watermark
```
## ステップ 3: Word 文書をロードする
次に、透かしを入れたい Word 文書をロードしましょう。我々は使用するだろう`WordProcessingLoadOptions`Word 文書を操作していることを指定します。
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    //さらなる手順はここに進みます
}
```
## ステップ 4: 画像のウォーターマークを作成および構成する
次に、`ImageWatermark`物体。このオブジェクトには、透かしとして使用する画像が保持されます。
```csharp
using (ImageWatermark watermark = new ImageWatermark("Path to Your Image"))
{
    //画像効果の設定はここにあります
}
```
## ステップ 5: 画像効果を適用する
透かしを目立たせるために、さまざまな画像効果を適用できます。ここでは、明るさとコントラストを調整し、クロマキーを設定し、枠線を追加します。
```csharp
WordProcessingImageEffects effects = new WordProcessingImageEffects
{
    Brightness = 0.7,
    Contrast = 0.6,
    ChromaKey = Color.Red,
    BorderLineFormat = new BorderLineFormat
    {
        Enabled = true,
        Weight = 1
    }
};
```
## ステップ 6: 透かしオプションを設定する
次に、透かしオプションを設定し、構成したばかりの効果を適用する必要があります。
```csharp
WordProcessingWatermarkSectionOptions options = new WordProcessingWatermarkSectionOptions
{
    Effects = effects
};
```
## ステップ 7: 文書に透かしを追加する
透かしと効果を設定したら、文書に透かしを追加できるようになります。
```csharp
watermarker.Add(watermark, options);
```
## ステップ 8: 透かし入りのドキュメントを保存する
最後に、ウォーターマークを適用したドキュメントを保存します。 
```csharp
watermarker.Save(outputFileName);
```
## 結論
Word 文書に透かしを追加すると、文書の専門性が高まり、コンテンツが保護されます。 GroupDocs.Watermark for .NET を使用すると、このプロセスは簡単でカスタマイズ可能です。このステップバイステップのガイドに従うことで、さまざまな画像効果を備えた透かしを簡単に追加して、文書を目立たせることができます。 
ドキュメントを保護する場合でも、ちょっとしたセンスを追加する場合でも、GroupDocs.Watermark for .NET はすべての透かしのニーズに対応する堅牢なソリューションを提供することを忘れないでください。 
## よくある質問
### 透かしに他の画像形式を使用できますか?
はい、GroupDocs は JPEG、PNG、BMP、GIF などのさまざまな画像形式をサポートしています。
### 透かしの透明度を調整することはできますか?
絶対に！を設定することで透明度を調整できます。`Opacity`の財産`ImageWatermark`物体。
### つのドキュメントに複数の透かしを追加できますか?
はい、呼び出して複数の透かしを追加できます。`Add`メソッドを異なる透かしオブジェクトで複数回実行します。
### 文書から透かしを削除するにはどうすればよいですか?
ウォーターマークを削除するには、`Remove`によって提供されるメソッド`Watermarker`クラス。
### 文書を保存する前に透かしをプレビューする方法はありますか?
現在、GroupDocs.Watermark には直接プレビュー機能はありません。ただし、文書を一時ファイルとして保存して、透かしを確認することができます。