---
title: PDF から注釈情報を抽出する
linktitle: PDF から注釈情報を抽出する
second_title: GroupDocs.Watermark .NET API
description: この詳細なステップバイステップ ガイドでは、GroupDocs.Watermark for .NET を使用して PDF ドキュメントから注釈情報を抽出する方法を学びます。
weight: 23
url: /ja/net/pdf-watermarking-attachments/extract-annotation-information-pdf/
---
## 導入
PDF ドキュメントから詳細な注釈情報を抽出する必要があることがよくありますか?ドキュメント管理システムに取り組んでいる開発者であっても、多数の PDF を扱うビジネスプロフェッショナルであっても、注釈を効率的に抽出して処理することは非常に重要です。 GroupDocs.Watermark for .NET を使用すると、このタスクを簡単かつ効率的に行うための強力なツールキットを自由に使用できます。
## 前提条件
コードに入る前に、開始するために必要なものがすべて揃っていることを確認してください。
1. Visual Studio: Visual Studio がインストールされていることを確認してください。これは、コードを作成して実行するための IDE になります。
2.  GroupDocs.Watermark for .NET: GroupDocs.Watermark for .NET ライブラリが必要です。あなたはできる[ここからダウンロードしてください](https://releases.groupdocs.com/Watermark/net/).
3. C# の基本知識: 例に従うには、C# プログラミングに精通している必要があります。
## 名前空間のインポート
まず、必要な名前空間をプロジェクトにインポートする必要があります。これらの名前空間には、PDF ファイルを操作して注釈を抽出するために必要なクラスとメソッドが含まれています。
```csharp
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using System;
using System.IO;
```
## ステップ 1: プロジェクトをセットアップする
まず、Visual Studio でプロジェクトを設定しましょう。新しいコンソール アプリ (.NET Core) プロジェクトを作成します。プロジェクトが作成されたら、GroupDocs.Watermark for .NET ライブラリへの参照を追加する必要があります。
1. NuGet パッケージ マネージャーを開きます。
2. 検索する`GroupDocs.Watermark`.
3. をインストールします`GroupDocs.Watermark`パッケージ。
## ステップ 2: ドキュメント パスを定義する
次に、入力 PDF ドキュメントのパスと、抽出された情報が保存される出力ディレクトリを指定する必要があります。これにより、アプリケーションは PDF ファイルの場所と結果の保存場所を認識できるようになります。
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
## ステップ 3: PDF ドキュメントをロードする
 PDF ドキュメントを操作するには、次を使用して PDF ドキュメントをロードする必要があります。`PdfLoadOptions`。このクラスは、読み込みプロセスを構成するオプションを提供します。
```csharp
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    //注釈を抽出するコードはここに記述されます
}
```
## ステップ 4: PDF コンテンツにアクセスする
ドキュメントがロードされると、そのコンテンツにアクセスできるようになります。具体的には、ページと注釈を反復処理できるように PDF コンテンツを取得したいと考えています。
```csharp
PdfContent pdfContent = watermarker.GetContent<PdfContent>();
```
## ステップ 5: ページと注釈を反復処理する
PDF コンテンツを手に入れて、各ページをループしてから、それらのページ上の各注釈をループできます。これにより、必要な情報を抽出できるようになります。
```csharp
foreach (PdfPage page in pdfContent.Pages)
{
    foreach (PdfAnnotation annotation in page.Annotations)
    {
        //ここで注釈の詳細を抽出します
    }
}
```
## ステップ 6: 注釈の詳細を抽出する
ネストされたループ内で、各注釈に関するさまざまな詳細を抽出します。これには、注釈の種類、関連する画像、テキスト、位置データが含まれます。
```csharp
Console.WriteLine(annotation.AnnotationType);
if (annotation.Image != null)
{
    Console.WriteLine(annotation.Image.Width);
    Console.WriteLine(annotation.Image.Height);
    Console.WriteLine(annotation.Image.GetBytes().Length);
}
Console.WriteLine(annotation.Text);
Console.WriteLine(annotation.X);
Console.WriteLine(annotation.Y);
Console.WriteLine(annotation.Width);
Console.WriteLine(annotation.Height);
Console.WriteLine(annotation.RotateAngle);
```
## ステップ 7: 抽出されたデータの保存または処理
最後に、抽出したアノテーション情報をどのように処理するかを決定します。必要に応じて、コンソールに出力したり、ファイルに保存したり、データベースに保存したりすることもできます。
```csharp
//抽出したデータをファイルに保存する例
using (StreamWriter writer = new StreamWriter(outputFileName))
{
    foreach (PdfPage page in pdfContent.Pages)
    {
        foreach (PdfAnnotation annotation in page.Annotations)
        {
            writer.WriteLine($"Annotation Type: {annotation.AnnotationType}");
            if (annotation.Image != null)
            {
                writer.WriteLine($"Image Width: {annotation.Image.Width}");
                writer.WriteLine($"Image Height: {annotation.Image.Height}");
                writer.WriteLine($"Image Bytes: {annotation.Image.GetBytes().Length}");
            }
            writer.WriteLine($"Text: {annotation.Text}");
            writer.WriteLine($"Position: ({annotation.X}, {annotation.Y})");
            writer.WriteLine($"Size: {annotation.Width}x{annotation.Height}");
            writer.WriteLine($"Rotate Angle: {annotation.RotateAngle}");
        }
    }
}
```
## 結論
GroupDocs.Watermark for .NET を使用して PDF ドキュメントから注釈情報を抽出するのは簡単なプロセスであり、時間と労力を大幅に節約できます。このガイドで概説されている手順に従うことで、この機能をプロジェクトに簡単に統合し、貴重な注釈データの抽出を自動化できます。
大量の PDF を管理している場合でも、単に特定の情報を抽出する必要がある場合でも、GroupDocs.Watermark for .NET は信頼性が高く効率的なソリューションを提供します。忘れずにチェックしてください[ドキュメンテーション](https://tutorials.groupdocs.com/Watermark/net/)より高度な機能とカスタマイズ オプションについては、
## よくある質問
### .NET 用の GroupDocs.Watermark とは何ですか?
GroupDocs.Watermark for .NET は、開発者が PDF、Word ドキュメント、画像などのさまざまなドキュメント形式からウォーターマークを追加、検索、削除できるようにする包括的なライブラリです。
### GroupDocs.Watermark を無料で試すことはできますか?
はい、入手できます[無料トライアル](https://releases.groupdocs.com/)購入する前にライブラリの機能をテストします。
### 問題が発生した場合はどうすればサポートを受けられますか?
 GroupDocs チームにアクセスすると、サポートを受けることができます。[サポートフォーラム](https://forum.groupdocs.com/c/watermark/19).
### テスト用の一時ライセンスを取得することはできますか?
はい、リクエストできます[仮免許証](https://purchase.groupdocs.com/temporary-license/)テスト目的のため。
### GroupDocs.Watermark for .NET のフルバージョンはどこで購入できますか?
フルバージョンは以下から購入できます。[GroupDocs Web サイト](https://purchase.groupdocs.com/buy).