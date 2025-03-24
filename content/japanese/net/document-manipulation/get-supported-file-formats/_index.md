---
title: サポートされているファイル形式を取得する
linktitle: サポートされているファイル形式を取得する
second_title: GroupDocs.Watermark .NET API
description: GroupDocs.Watermark for .NET を使用すると、ドキュメントにウォーターマークを簡単に追加できます。デジタル資産を保護するには、包括的なステップバイステップのガイドに従ってください。
weight: 13
url: /ja/net/document-manipulation/get-supported-file-formats/
---

# サポートされているファイル形式を取得する

## 導入
ドキュメントに透かしを入れることは、デジタル資産を保護するための重要なステップです。知的財産の保護、機密保持の確保、または単にブランド化のいずれであっても、透かしは重要な役割を果たします。ウォーターマーク機能をアプリケーションに統合しようとしている .NET 開発者であれば、GroupDocs.Watermark for .NET は検討すべき強力で多用途のツールです。このチュートリアルでは、インストールから最初のウォーターマークの適用まで、GroupDocs.Watermark の使用の基本を説明し、簡単に理解できるように各ステップに分けて説明します。
## 前提条件
詳細に入る前に、開始するために必要なものがすべて揃っていることを確認してください。
1.  Visual Studio: マシンに Visual Studio がインストールされていることを確認してください。からダウンロードできます。[Visual Studio の Web サイト](https://visualstudio.microsoft.com/).
2. .NET Framework: GroupDocs.Watermark は、.NET Framework のさまざまなバージョンをサポートします。プロジェクトが互換性のあるバージョンをターゲットにしていることを確認してください。
3. GroupDocs.Watermark for .NET: 最新バージョンを次の場所からダウンロードできます。[リリースページ](https://releases.groupdocs.com/Watermark/net/).
4. C# の基本知識: このチュートリアルは、C# と .NET 開発の基本を理解していることを前提としています。
## 名前空間のインポート
まず、プロジェクトに必要な名前空間をインポートしましょう。 C# ファイルを開き、次の using ディレクティブを先頭に追加します。
```csharp
using System;
using System.Collections.Generic;
using GroupDocs.Watermark.Common;
```
これらの名前空間をインポートすると、ドキュメントに透かしを追加できるようになります。

## ステップ 1: ウォーターマーク エンジンを初期化する
最初のステップは、透かし入れエンジンを初期化することです。これには、`Watermarker`透かしを入れたいドキュメントのクラス。
```csharp
string documentPath = "path/to/your/document.pdf";
Watermarker watermarker = new Watermarker(documentPath);
```
このコード スニペットは、`Watermarker`オブジェクト。ドキュメントに透かしを適用するために使用します。
## ステップ 2: テキストの透かしを追加する
次に、単純なテキストの透かしを文書に追加してみましょう。テキストの透かしは、「社外秘」や「下書き」などのラベルを追加するのに最適です。
```csharp
TextWatermark textWatermark = new TextWatermark("Confidential", new Font("Arial", 36));
textWatermark.ForegroundColor = Color.Red;
textWatermark.HorizontalAlignment = HorizontalAlignment.Center;
textWatermark.VerticalAlignment = VerticalAlignment.Center;
watermarker.Add(textWatermark);
```
ここで作成したのは、`TextWatermark`「社外秘」というテキストを含むオブジェクトを選択し、フォントと色を設定して文書の中央に配置します。
## ステップ 3: 画像の透かしを追加する
画像をウォーターマークとして使用したい場合は、GroupDocs.Watermark を使用すると簡単に使用できます。
```csharp
ImageWatermark imageWatermark = new ImageWatermark("path/to/watermark.png");
imageWatermark.Width = 100;
imageWatermark.Height = 100;
imageWatermark.HorizontalAlignment = HorizontalAlignment.Right;
imageWatermark.VerticalAlignment = VerticalAlignment.Top;
watermarker.Add(imageWatermark);
```
この例では、`ImageWatermark`オブジェクトを選択し、その寸法を設定し、ドキュメントの右上隅に位置合わせします。
## ステップ 4: ドキュメントを保存する
必要な透かしを追加した後の最後のステップは、変更したドキュメントを保存することです。
```csharp
watermarker.Save("path/to/output/document.pdf");
watermarker.Dispose();
```
これにより、透かし入りのドキュメントが指定されたパスに保存され、そこで使用されていたリソースが解放されます。`Watermarker`実例。
## ステップ 5: サポートされているファイル形式を取得する
GroupDocs.Watermark でサポートされているファイル形式を確認するには、次のコード スニペットを使用できます。
```csharp
IEnumerable<FileType> supportedFileTypes = FileType.GetSupportedFileTypes();
foreach (FileType fileType in supportedFileTypes)
{
    Console.WriteLine(fileType);
}
```
これにより、GroupDocs.Watermark が処理できるすべてのファイル タイプが出力され、その機能の包括的なビューが得られます。
## 結論
GroupDocs for .NET を使用してドキュメントにウォーターマークを付けるのは簡単かつ効率的です。このチュートリアルに従うことで、透かしエンジンの初期化、テキストと画像の透かしの追加、透かし入りドキュメントの保存、およびサポートされるファイル形式の一覧表示の方法を学習しました。これらのツールを使用すると、自信を持ってドキュメントを保護できます。
ご質問がある場合、またはさらにサポートが必要な場合は、お気軽に次のサイトにアクセスしてください。[GroupDocs.Watermark サポート フォーラム](https://forum.groupdocs.com/c/watermark/19).
## よくある質問
### GroupDocs.Watermark for .NET をインストールするにはどうすればよいですか?
からダウンロードできます。[リリースページ](https://releases.groupdocs.com/Watermark/net/) DLL をプロジェクトに追加します。
### GroupDocs.Watermark を無料で試すことはできますか?
はい、リクエストできます[無料トライアル](https://releases.groupdocs.com/)購入前にソフトウェアを評価するため。
### GroupDocs.Watermark ではどのようなファイル形式がサポートされていますか?
提供されたコード スニペットを使用して、サポートされているすべてのファイル形式を一覧表示できます。
### GroupDocs.Watermark のライセンスを購入するにはどうすればよいですか?
ライセンスは次から直接購入できます。[購入ページ](https://purchase.groupdocs.com/buy).
### GroupDocs.Watermark について利用可能なドキュメントはありますか?
はい、包括的なドキュメントが利用可能です[ここ](https://tutorials.groupdocs.com/Watermark/net/).