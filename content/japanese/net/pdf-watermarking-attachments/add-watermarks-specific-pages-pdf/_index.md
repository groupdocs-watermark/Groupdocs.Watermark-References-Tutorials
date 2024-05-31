---
title: PDF の特定のページにウォーターマークを追加する
linktitle: PDF の特定のページにウォーターマークを追加する
second_title: GroupDocs.Watermark .NET API
description: Groupdocs for .NET を使用して、PDF の特定のページにテキストと画像のウォーターマークを追加する方法を学びます。詳細なガイドに従って書類を保護してください。
type: docs
weight: 15
url: /ja/net/pdf-watermarking-attachments/add-watermarks-specific-pages-pdf/
---
## 導入
PDF ドキュメントに透かしを追加することは、コンテンツを保護し、所有権を主張するための重要なステップです。下書きにマークを付ける場合でも、機密情報を保護する場合でも、単にブランドを追加する場合でも、透かしは効果的なツールです。このチュートリアルでは、Groupdocs.Watermark for .NET を使用して、PDF ファイルの特定のページにテキストと画像の両方の透かしを追加する方法を説明します。プロセスを管理しやすいステップに分割して、確実にプロジェクトに沿ってこれらの機能を実装できるようにします。
## 前提条件
実装に入る前に、次の前提条件が満たされていることを確認してください。
- Visual Studio がインストールされている: .NET コードを作成して実行するには、Visual Studio などの IDE が必要です。
- .NET Framework: .NET Framework がマシンにインストールされていることを確認します。
-  Groupdocs.Watermark for .NET: Groupdocs.Watermark for .NET をダウンロードしてインストールします。がんばって[ここ](https://releases.groupdocs.com/Watermark/net/).
- C# の基礎知識: C# プログラミング言語に精通していると役立ちます。
- PDF ドキュメント: 透かしの追加をテストするために使用できる PDF ファイルを用意します。
## 名前空間のインポート
まず、必要な名前空間をプロジェクトにインポートする必要があります。この手順は、Groupdocs のクラスとメソッドにアクセスできるようにするために重要です。
```csharp
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## ステップ 1: プロジェクトのセットアップ
### 新しいプロジェクトを作成する
まず、Visual Studio を開き、新しい C# プロジェクトを作成します。簡単にするためにコンソール アプリケーションを選択できます。
```plaintext
File -> New -> Project -> Console App (.NET Core)
```
### Groupdocs.Watermark をインストールする
次に、NuGet パッケージ マネージャーを介して Groupdocs.Watermark ライブラリをインストールします。
```plaintext
Tools -> NuGet Package Manager -> Manage NuGet Packages for Solution
```
「Groupdocs.Watermark」を検索してインストールします。
## ステップ 2: PDF ドキュメントをロードする
### ドキュメントパスの定義
PDF ドキュメントへのパスと、透かし入り PDF が保存される出力ディレクトリを指定します。
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
### PDF ドキュメントをロードする
使用`PdfLoadOptions`PDF ドキュメントをロードするクラス。
```csharp
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    //透かしを追加するコードはここに記述されます
}
```
## ステップ 3: 奇数ページにテキストの透かしを追加する
### テキストの透かしを作成する
を作成します`TextWatermark`オブジェクトに希望のテキストとフォント設定を加えます。
```csharp
TextWatermark textWatermark = new TextWatermark("This is a test watermark", new Font("Arial", 8));
textWatermark.PagesSetup = new PagesSetup
{
    OddPages = true
};
```
### テキスト透かしオプションを適用する
使用`PdfArtifactWatermarkOptions`ウォーターマークを適用する方法を指定します。
```csharp
PdfArtifactWatermarkOptions textWatermarkOptions = new PdfArtifactWatermarkOptions();
watermarker.Add(textWatermark, textWatermarkOptions);
```
## ステップ 4: 最初のページに画像の透かしを追加する
透かしとして使用する画像を読み込みます。画像パスが正しいことを確認してください。
```csharp
using (ImageWatermark imageWatermark = new ImageWatermark("Path to Your Image"))
{
    imageWatermark.PagesSetup = new PagesSetup
    {
        FirstPage = true
    };
    
    PdfArtifactWatermarkOptions imageWatermarkOptions = new PdfArtifactWatermarkOptions();
    watermarker.Add(imageWatermark, imageWatermarkOptions);
}
```
## ステップ 5: 透かし入り PDF を保存する
最後に、透かしを入れた PDF を指定した出力ディレクトリに保存します。
```csharp
watermarker.Save(outputFileName);
```
## 結論
Groupdocs for .NET を使用して PDF にウォーターマークを追加するのは簡単なプロセスです。これらの手順に従うことで、PDF ドキュメントの特定のページにテキストと画像の透かしを効率的に追加できます。これは書類を保護するだけでなく、プロフェッショナルな外観を維持するのにも役立ちます。試してみて、透かしをユニークで効果的なものにするために利用できるさまざまなカスタマイズ オプションを調べてください。
## よくある質問
### .NET 用の Groupdocs.Watermark とは何ですか?
Groupdocs.Watermark for .NET は、PDF、Word、Excel などのさまざまなドキュメント形式でウォーターマークを追加、検索、削除できるライブラリです。
### 透かしの外観をカスタマイズできますか?
はい、テキストのウォーターマークのテキストのフォント、サイズ、色、位置をカスタマイズでき、画像のウォーターマークのサイズ、不透明度、位置を調整できます。
### 特定のページにのみウォーターマークを追加することはできますか?
絶対に。 Groupdocs.Watermark for .NET は、特定のページ、奇数ページまたは偶数ページ、またはページ範囲にウォーターマークを追加するオプションを提供します。
### Groupdocs.Watermark の無料トライアルを取得するにはどうすればよいですか?
無料トライアル版は次からダウンロードできます。[グループドキュメント Web サイト](https://releases.groupdocs.com/).
### より詳細なドキュメントはどこで入手できますか?
さらに詳しい情報については、以下を参照してください。[ドキュメンテーション](https://reference.groupdocs.com/Watermark/net/).