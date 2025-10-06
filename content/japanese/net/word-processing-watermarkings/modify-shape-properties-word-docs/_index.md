---
title: Word ドキュメントの図形プロパティを変更する
linktitle: Word ドキュメントの図形プロパティを変更する
second_title: GroupDocs.Watermark .NET API
description: GroupDocs for .NET を使用して Word ドキュメントを保護します。形状プロパティを簡単に変更してセキュリティを強化します。
weight: 27
url: /ja/net/word-processing-watermarkings/modify-shape-properties-word-docs/
type: docs
---
# Word ドキュメントの図形プロパティを変更する

## 導入
今日のデジタル時代では、ドキュメントのセキュリティを確保することが最も重要です。ビジネスの専門家、法律の専門家、クリエイティブなライターのいずれであっても、機密情報を保護することは非常に重要です。ここで GroupDocs.Watermark for .NET が活躍し、ドキュメントを不正使用や配布から保護するための包括的なソリューションを提供します。
## 前提条件
チュートリアルに入る前に、次の前提条件が満たされていることを確認してください。
1.  GroupDocs.Watermark for .NET: GroupDocs.Watermark for .NET ライブラリを次の場所からダウンロードしてインストールします。[ダウンロードリンク](https://releases.groupdocs.com/Watermark/net/).
2. ドキュメント: 変更する Word ドキュメントを用意します。
3. C# の基礎知識: C# プログラミング言語に精通していると役立ちます。

## 名前空間のインポート
まず、必要な名前空間を C# コードにインポートします。
```csharp
using GroupDocs.Watermark.Contents.WordProcessing;
using GroupDocs.Watermark.Options.WordProcessing;
using System.IO;
using System;
```
ここで、例を複数のステップに分けてみましょう。
## ステップ 1: ドキュメントをロードする
まず、Word 文書へのパスと出力ファイル名を指定します。必要なロード オプションを必ず含めてください。
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
var loadOptions = new WordProcessingLoadOptions();
```
## ステップ 2: ウォーターマーカーを初期化する
のインスタンスを作成します。`Watermarker`クラスを作成し、指定されたロード オプションを使用してドキュメントをロードします。
```csharp
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    WordProcessingContent content = watermarker.GetContent<WordProcessingContent>();
```
## ステップ 3: 形状プロパティを変更する
ドキュメントのセクション内の図形を繰り返し処理し、必要な変更を適用します。
```csharp
foreach (WordProcessingShape shape in content.Sections[0].Shapes)
{
    if (shape.Text.Contains("Some text"))
    {
        shape.AlternativeText = "watermark";
        shape.RotateAngle = 30;
        shape.X = 200;
        shape.Y = 200;
        shape.Height = 100;
        shape.Width = 400;
        shape.BehindText = false;
    }
}
```
## ステップ 4: ドキュメントを保存する
変更を適用したら、変更を含むドキュメントを保存します。
```csharp
watermarker.Save(outputFileName);
```
## 結論
GroupDocs.Watermark for .NET を使用すると、図形プロパティを簡単に変更することで Word ドキュメントのセキュリティを強化できます。直感的な API と包括的な機能により、機密情報の保護がこれまでになく簡単になりました。

## よくある質問
### GroupDocs.Watermark は他のドキュメント形式と互換性がありますか?
はい。GroupDocs.Watermark は、Word、Excel、PowerPoint、PDF などを含む幅広いドキュメント形式をサポートしています。
### 透かしのテキストと外観をカスタマイズできますか?
絶対に！ GroupDocs.Watermark は、透かしのテキスト、フォント、色、不透明度、位置をカスタマイズするための広範なオプションを提供します。
### GroupDocs.Watermark はバッチ処理機能を提供しますか?
はい、GroupDocs を使用して複数のドキュメントを同時に処理できるため、時間と労力を節約できます。
### GroupDocs.Watermark の試用版はありますか?
はい、次から無料試用版をダウンロードして、GroupDocs.Watermark の機能を探索できます。[ここ](https://releases.groupdocs.com/).
### GroupDocs.Watermark のサポートを受けるにはどうすればよいですか?
問い合わせや支援が必要な場合は、GroupDocs.Watermark フォーラムにアクセスしてください。[ここ](https://forum.groupdocs.com/c/watermark/19).