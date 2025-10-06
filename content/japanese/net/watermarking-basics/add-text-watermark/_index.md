---
title: テキストの透かしを追加する
linktitle: テキストの透かしを追加する
second_title: GroupDocs.Watermark .NET API
description: このステップバイステップ ガイドでは、Groupdocs Watermark for .NET を使用してドキュメントにテキスト ウォーターマークを追加する方法を学習します。
weight: 11
url: /ja/net/watermarking-basics/add-text-watermark/
type: docs
---
# テキストの透かしを追加する

## 導入
GroupDocs.Watermark for .NET は、開発者が .NET アプリケーションのさまざまなドキュメント形式に対してウォーターマークを追加、検索、削除できる強力なライブラリです。このチュートリアルでは、GroupDocs.Watermark を使用してドキュメントにテキスト ウォーターマークを追加することに焦点を当てます。
## 前提条件
始める前に、次の前提条件を満たしていることを確認してください。
1. C# プログラミング言語の基本的な知識。
2. Visual Studio がシステムにインストールされている。
3.  .NET ライブラリ用の GroupDocs.Watermark がインストールされています。からダウンロードできます[ここ](https://releases.groupdocs.com/Watermark/net/).

## 名前空間のインポート
まず、必要な名前空間を C# プロジェクトにインポートする必要があります。
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Watermarks;
using System;
using System.IO;
```
## ステップ 1: ドキュメントのパスと出力ディレクトリを定義する
入力ドキュメントへのパスと、透かし入りドキュメントが保存される出力ディレクトリを定義します。
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
交換する`"Your Document Path"`入力ドキュメントへの絶対パスまたは相対パスを使用します。例:`@"C:\Docs\document.pdf"`。また、透かし入りのドキュメントを保存するディレクトリを指定します。
## ステップ 2: テキストの透かしを追加する
インスタンス化します`Watermarker`入力ドキュメントパスを含むクラス。次に、`TextWatermark`オブジェクトに必要なテキストとフォントの設定を加えます。
```csharp
using (Watermarker watermarker = new Watermarker(documentPath))
{
    TextWatermark watermark = new TextWatermark("top secret", new Font("Arial", 36));
    watermark.ForegroundColor = Color.Red;
    watermark.HorizontalAlignment = HorizontalAlignment.Center;
    watermark.VerticalAlignment = VerticalAlignment.Center;
    watermarker.Add(watermark);
    watermarker.Save(outputFileName);
}
```

## 結論
このチュートリアルでは、GroupDocs.Watermark for .NET を使用してドキュメントにテキスト ウォーターマークを追加する方法を学習しました。直感的な API を使用すると、開発者はさまざまなドキュメント形式のウォーターマークを簡単に操作できます。
## よくある質問
### GroupDocs.Watermark for .NET はすべてのドキュメント形式と互換性がありますか?
GroupDocs.Watermark は、PDF、Microsoft Word、Excel、PowerPoint などを含む幅広いドキュメント形式をサポートしています。
### テキストの透かしの外観をカスタマイズできますか?
はい、テキストの透かしのフォント、色、配置、不透明度などのさまざまなプロパティをカスタマイズできます。
### GroupDocs.Watermark はドキュメントからウォーターマークを削除するサポートを提供しますか?
はい。GroupDocs.Watermark は、ドキュメントからウォーターマークを検索して削除する機能を提供します。
### 購入する前に GroupDocs.Watermark for .NET を試すことはできますか?
はい、無料試用版を次からダウンロードできます。[ここ](https://releases.groupdocs.com/).
### GroupDocs.Watermark のテクニカル サポートを受けるにはどうすればよいですか?
テクニカル サポートを受けるには、次のサイトにアクセスしてください。[GroupDocs.Watermark フォーラム](https://forum.groupdocs.com/c/watermark/19).