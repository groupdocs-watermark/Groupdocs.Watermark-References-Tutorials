---
title: PDF の寸法を取得する
linktitle: PDF の寸法を取得する
second_title: GroupDocs.Watermark .NET API
description: Groupdocs.Watermark for .NET を使用してドキュメントを簡単に保護します。透かし、スタンプ、注釈を簡単に追加できます。
weight: 26
url: /ja/net/pdf-watermarking-attachments/get-pdf-dimensions/
type: docs
---
# PDF の寸法を取得する

## 導入
今日のデジタル時代では、ドキュメントを保護することが最も重要です。ビジネスの専門家、法律の専門家、またはクリエイティブなアーティストであっても、知的財産を保護することは不可欠です。 Groupdocs.Watermark for .NET は、ドキュメントにウォーターマーク、スタンプ、注釈を追加し、ドキュメントのセキュリティと信頼性を確保するための堅牢なソリューションを提供します。
## 前提条件
Groupdocs.Watermark for .NET の世界に入る前に、次の前提条件が満たされていることを確認してください。
1.  Groupdocs.Watermark for .NET のインストール: Groupdocs.Watermark for .NET を次の場所からダウンロードしてインストールします。[ダウンロードリンク](https://releases.groupdocs.com/Watermark/net/).
2. ライセンス キー (オプション): Groupdocs.Watermark for .NET は無料試用版を提供していますが、一時ライセンスを選択することも、完全ライセンスを購入することもできます。[ここ](https://purchase.groupdocs.com/buy)拡張機能用。
3. C# に精通していること: 提供される例を理解して実装するには、C# プログラミング言語の基本的な知識があることが推奨されます。
4. 保護するドキュメント: 実験用にサンプル ドキュメント (PDF、Word、Excel など) をローカル マシン上に用意します。

## 名前空間のインポート
Groupdocs.Watermark for .NET の使用を開始するには、必要な名前空間を C# プロジェクトにインポートする必要があります。
```csharp
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using System;
using System.IO;
```
### ステップ 1: 変数を宣言する
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
### ステップ 2: ドキュメントをロードする
```csharp
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
```
### ステップ 3: PDF コンテンツを取得する
```csharp
PdfContent pdfContent = watermarker.GetContent<PdfContent>();
```
### ステップ 4: 寸法の取得
```csharp
Console.WriteLine(pdfContent.Pages[0].Width);
Console.WriteLine(pdfContent.Pages[0].Height);
```

## 結論
結論として、Groupdocs.Watermark for .NET は、ドキュメントを不正な使用や配布から保護するための包括的なソリューションを提供します。上記の手順に従い、Groupdocs.Watermark for .NET の機能を活用することで、貴重なデジタル資産のセキュリティと整合性を確保できます。
## よくある質問
### Groupdocs.Watermark for .NET を無料で使用できますか?
はい、Groupdocs.Watermark for .NET は評価目的で無料の試用版を提供しています。ただし、拡張機能が必要な場合は、完全なライセンスの購入を検討してください。
### Groupdocs.Watermark は複数のドキュメント形式をサポートしていますか?
はい、Groupdocs は PDF、Word、Excel、PowerPoint などの幅広いドキュメント形式をサポートしています。
### Groupdocs.Watermark を使用してウォーターマークとスタンプをカスタマイズできますか?
絶対に！ Groupdocs.Watermark は、特定の要件に合わせて、透かし、スタンプ、注釈の広範なカスタマイズ オプションを提供します。
### Groupdocs.Watermark ユーザーはテクニカル サポートを利用できますか?
はい、技術サポートを受けたり、Groupdocs コミュニティに参加したりできます。[サポートフォーラム](https://forum.groupdocs.com/c/watermark/19).
### Groupdocs.Watermark の一時ライセンスを取得するにはどうすればよいですか?
 Groupdocs.Watermark の一時ライセンスは、以下から取得できます。[ここ](https://purchase.groupdocs.com/temporary-license/).