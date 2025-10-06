---
title: PDFドキュメントをラスタライズする
linktitle: PDFドキュメントをラスタライズする
second_title: GroupDocs.Watermark .NET API
description: GroupDocs.Watermark for .NET を使用して PDF ドキュメントをラスタライズする方法を学びます。ドキュメントのセキュリティと視覚的な魅力を簡単に強化します。
weight: 27
url: /ja/net/pdf-watermarking-attachments/rasterize-pdf-document/
type: docs
---
# PDFドキュメントをラスタライズする

## 導入
ドキュメントの管理と操作の分野では、GroupDocs.Watermark for .NET は強力なツールとして優れており、さまざまなドキュメント形式でウォーターマークを追加、削除、検索するための堅牢な機能を提供します。著作権表示でドキュメントを保護する場合でも、ブランド化のために企業ロゴを追加する場合でも、単にスタンプでドキュメントに注釈を付ける場合でも、GroupDocs.Watermark は直感的な API と広範な機能セットでプロセスを簡素化します。
## 前提条件
GroupDocs.Watermark for .NET を使用してウォーターマークの世界に飛び込む前に、次の前提条件が満たされていることを確認してください。
### 1..NET Frameworkをインストールする
開発マシンに .NET Framework がインストールされていることを確認してください。 Microsoft Web サイトからダウンロードするか、好みのパッケージ マネージャーを使用できます。
#### ステップ 1: .NET Framework をダウンロードする
Microsoft .NET Framework のダウンロード ページにアクセスします。
#### ステップ 2: .NET Framework をインストールする
ダウンロード ページに記載されているインストール手順に従って、システムに .NET Framework をインストールします。
### 2. GroupDocs.Watermark ライセンスを取得する
GroupDocs.Watermark のすべての機能を利用するには、有効なライセンスが必要です。ライセンスを購入することも、評価目的で一時的なライセンスを取得することもできます。
#### ステップ 1: ライセンスを取得する
GroupDocs.Watermark の購入ページにアクセスしてください。
#### ステップ 2: 一時ライセンスを購入または取得する
ニーズに基づいて適切なライセンス オプションを選択します。継続的に使用するためにライセンスを購入するか、評価目的で一時ライセンスを取得します。

## 名前空間のインポート
ドキュメントにウォーターマークを挿入する前に、GroupDocs の機能にシームレスにアクセスするために必要な名前空間をインポートしてください。
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```

すべての設定が完了したので、GroupDocs.Watermark for .NET を使用して PDF ドキュメントをラスタライズしてみましょう。ラスター化では、PDF ドキュメントの各ページを PNG などのラスター イメージ形式に変換します。
## ステップ 1: 変数を初期化する
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
「ドキュメント パス」と「ドキュメント ディレクトリ」を、それぞれ PDF ドキュメントと目的の出力ディレクトリへの実際のパスに置き換えてください。
## ステップ 2: ドキュメントをロードして透かしを追加する
```csharp
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    //画像またはテキストの透かしを初期化する
    TextWatermark watermark = new TextWatermark("Do not copy", new Font("Arial", 8));
    watermark.HorizontalAlignment = HorizontalAlignment.Center;
    watermark.VerticalAlignment = VerticalAlignment.Center;
    watermark.RotateAngle = 45;
    watermark.SizingType = SizingType.ScaleToParentDimensions;
    watermark.ScaleFactor = 1;
    watermark.Opacity = 0.5;
    //任意のタイプの透かしを最初に追加します
    watermarker.Add(watermark);
    PdfContent pdfContent = watermarker.GetContent<PdfContent>();
    //全ページをラスタライズする
    pdfContent.Rasterize(100, 100, PdfImageConversionFormat.Png);
    //すべてのページのコンテンツがラスター画像に置き換えられます
    watermarker.Save(outputFileName);
}
```
このステップでは、PDF ドキュメントをロードし、テキスト、フォント、配置、回転角度、サイズ変更タイプ、スケール係数、不透明度などの指定されたプロパティを使用してテキスト透かしを初期化します。次に、文書に透かしを追加します。次に、PDF ドキュメントのコンテンツを取得し、すべてのページを解像度 100 DPI の PNG 形式にラスタライズします。最後に、変更したドキュメントをラスタライズされたコンテンツとともに保存します。

## 結論
GroupDocs.Watermark for .NET は、さまざまなドキュメント形式にウォーターマークを簡単に追加するための包括的なソリューションを提供します。このチュートリアルで概説されている手順に従うことで、PDF ドキュメントを効果的にラスタライズし、セキュリティと視覚的な魅力を高めることができます。
## よくある質問
### GroupDocs.Watermark は PDF 以外のドキュメント形式と互換性がありますか?
はい、GroupDocs.Watermark は、Microsoft Word、Excel、PowerPoint、Visio、Outlook などを含む幅広いドキュメント形式をサポートしています。
### GroupDocs.Watermark を使用して追加されたウォーターマークの外観をカスタマイズできますか?
絶対に！ GroupDocs.Watermark は、テキスト、フォント、色、サイズ、不透明度、回転、位置などの透かしプロパティをカスタマイズするための広範なオプションを提供します。
### GroupDocs.Watermark はバッチ処理のサポートを提供しますか?
はい、GroupDocs ウォーターマークを使用すると、複数のドキュメントをバッチ モードで簡単に処理でき、大規模なファイル セットにウォーターマークを付ける時間と労力を節約できます。
### GroupDocs.Watermark の試用版はありますか?
はい、Web サイトから GroupDocs.Watermark の無料試用版をダウンロードして、購入前にその機能を評価できます。
### GroupDocs.Watermark に関して問題が発生したり質問がある場合は、どうすればサポートを受けられますか?
GroupDocs.Watermark フォーラムにアクセスしてコミュニティからのサポートを求めるか、GroupDocs サポート チームに連絡して支援を求めることができます。