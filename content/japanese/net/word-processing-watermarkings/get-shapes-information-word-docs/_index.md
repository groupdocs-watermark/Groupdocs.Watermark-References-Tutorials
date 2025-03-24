---
title: Word ドキュメントで図形情報を取得する
linktitle: Word ドキュメントで図形情報を取得する
second_title: GroupDocs.Watermark .NET API
description: GroupDocs for .NET を使用すると、Word ドキュメントから貴重な洞察を簡単に得ることができます。形状情報をシームレスに抽出してデータ分析を強化します。
weight: 24
url: /ja/net/word-processing-watermarkings/get-shapes-information-word-docs/
---

# Word ドキュメントで図形情報を取得する

## 導入
データが重要なデジタル環境では、ドキュメントから有意義な洞察を抽出することが最も重要です。 GroupDocs.Watermark for .NET を使用すると、開発者はドキュメント構造を詳しく調べて、貴重な情報を簡単に抽出できます。このチュートリアルでは、この強力なツールを活用して Word 文書から形状情報を取得する方法を段階的に説明します。
## 前提条件
チュートリアルに入る前に、次の前提条件が満たされていることを確認してください。
1.  GroupDocs.Watermark for .NET: からライブラリをダウンロードしてインストールします。[Webサイト](https://releases.groupdocs.com/Watermark/net/).
2. 開発環境: Visual Studio または任意のテキスト エディターを含む .NET 開発環境をセットアップします。
3. Word ドキュメントへのアクセス: 形状情報を抽出する Word ドキュメントにアクセスできます。

## 必要な名前空間のインポート
コードに進む前に、必要な名前空間をインポートすることが重要です。
```csharp
using System;
using System.IO;
using GroupDocs.Watermark.Contents.WordProcessing;
using GroupDocs.Watermark.Options.WordProcessing;
```
## ステップ 1: ドキュメントをロードする
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
```
必ず交換してください`"Your Document Path"` Word 文書への実際のパスを含めます。
## ステップ 2: 形状情報を抽出する
```csharp
	WordProcessingContent content = watermarker.GetContent<WordProcessingContent>();
	foreach (WordProcessingSection section in content.Sections)
	{
		foreach (WordProcessingShape shape in section.Shapes)
		{
```
このスニペットは Word 文書のコンテンツを取得し、その中の各セクションと図形を反復処理します。
## ステップ 3: 形状属性を分析する
```csharp
			if (shape.HeaderFooter != null)
			{
				Console.WriteLine("In header/footer");
			}
			Console.WriteLine(shape.ShapeType);
			Console.WriteLine(shape.Width);
			Console.WriteLine(shape.Height);
			Console.WriteLine(shape.IsWordArt);
			Console.WriteLine(shape.RotateAngle);
			Console.WriteLine(shape.AlternativeText);
			Console.WriteLine(shape.Name);
			Console.WriteLine(shape.X);
			Console.WriteLine(shape.Y);
			Console.WriteLine(shape.Text);
			if (shape.Image != null)
			{
				Console.WriteLine(shape.Image.Width);
				Console.WriteLine(shape.Image.Height);
				Console.WriteLine(shape.Image.GetBytes().Length);
			}
			Console.WriteLine(shape.HorizontalAlignment);
			Console.WriteLine(shape.VerticalAlignment);
			Console.WriteLine(shape.RelativeHorizontalPosition);
			Console.WriteLine(shape.RelativeVerticalPosition);
		}
	}
}
```
コード スニペットのこの部分では、各図形のタイプ、寸法、位置、テキストなどのさまざまな属性を取得します。

## 結論
GroupDocs.Watermark for .NET は、Word 文書からの図形情報の抽出を簡素化し、文書構造を簡単に調査できるシームレスなソリューションを開発者に提供します。このチュートリアルで概説されている手順に従うことで、ドキュメントから貴重な洞察を引き出し、データ分析機能を強化することができます。
## よくある質問
### GroupDocs.Watermark は他のドキュメント形式と互換性がありますか?
はい、GroupDocs は PDF、Excel、PowerPoint などのさまざまなドキュメント形式をサポートしています。
### GroupDocs.Watermark を使用してドキュメントにウォーターマークを適用できますか?
確かに、GroupDocs.Watermark を使用すると、プログラムで簡単にドキュメントにウォーターマークを追加できます。
### GroupDocs.Watermark はカスタム ドキュメント解析のサポートを提供しますか?
実際、GroupDocs.Watermark は、さまざまなユースケースに合わせてカスタム ドキュメントを解析するための柔軟なオプションを提供します。
### GroupDocs.Watermark はエンタープライズ レベルのドキュメント処理に適していますか?
はい、GroupDocs.Watermark はエンタープライズ レベルのドキュメント処理のニーズを満たすように設計されており、堅牢な機能と拡張性を提供します。
### GroupDocs.Watermark を既存の .NET プロジェクトに統合できますか?
確かに、GroupDocs.Watermark は .NET プロジェクトにシームレスに統合され、ドキュメント操作のための包括的なソリューションを提供します。