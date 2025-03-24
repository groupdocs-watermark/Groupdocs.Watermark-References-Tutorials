---
title: パスワードで保護されたドキュメントをロードする
linktitle: パスワードで保護されたドキュメントをロードする
second_title: GroupDocs.Watermark .NET API
description: Groupdocs for .NET を使用してパスワードで保護されたドキュメントにウォーターマークを追加する方法については、ステップバイステップのガイドを参照してください。ファイルを簡単に保護し、ブランド化します。
weight: 13
url: /ja/net/document-loadings/load-password-protected-document/
---

# パスワードで保護されたドキュメントをロードする

## 導入
パスワードで保護されている場合でも、透かしを追加してドキュメントを保護したいと考えていますか? Groupdocs.Watermark for .NET は、まさにそれを可能にする強力なツールです。このチュートリアルでは、パスワードで保護されたドキュメントをロードし、Groupdocs.Watermark for .NET を使用してそれにウォーターマークを追加するプロセスを説明します。飛び込んでみましょう！
## 前提条件
始める前に、以下のものがあることを確認してください。
1. Visual Studio: マシンにインストールされている Visual Studio の任意のバージョン。
2. .NET Framework: .NET Framework 4.6.1 以降があることを確認してください。
3. Groupdocs.Watermark for .NET: Groupdocs.Watermark for .NET ライブラリを次の場所からダウンロードしてインストールします。[ダウンロードリンク](https://releases.groupdocs.com/Watermark/net/).
## 名前空間のインポート
まず、必要な名前空間をプロジェクトにインポートする必要があります。これにより、Groupdocs.Watermark for .NET によって提供されるすべてのメソッドとプロパティに確実にアクセスできるようになります。
```csharp
using GroupDocs.Watermark.Options;
using GroupDocs.Watermark.Watermarks;
using System;
using System.IO;
```
ここで、プロセスをシンプルでわかりやすい手順に分割してみましょう。
## ステップ 1: プロジェクトをセットアップする
まず、Visual Studio で新しい C# コンソール アプリケーションを作成します。プロジェクトがセットアップされたら、NuGet パッケージ マネージャーを介して .NET ライブラリ用の Groupdocs.Watermark をインストールします。
1. Visual Studio を開き、新しいコンソール アプリ (.NET Framework) を作成します。
2. に行く`Tools`>`NuGet Package Manager`>`Manage NuGet Packages for Solution`.
3. 検索する`GroupDocs.Watermark`そしてパッケージをインストールします。
## ステップ 2: ドキュメント パスを定義する
次に、パスワードで保護されたドキュメントへのパスと、透かし入りのドキュメントが保存される出力ファイルのパスを定義する必要があります。
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
```
交換する`"Your Document Path"`そして`"Your Document Directory"`マシン上の実際のパスを使用します。
## ステップ 3: パスワードを使用してロード オプションを設定する
パスワードで保護されたドキュメントを開くには、ロード オプションでパスワードを指定する必要があります。
```csharp
LoadOptions loadOptions = new LoadOptions();
loadOptions.Password = "P@$w0rd";
```
交換する`"P@$w0rd"`文書の実際のパスワードを使用してください。
## ステップ 4: ドキュメントをロードする
次に、次のコマンドを使用してドキュメントをロードしましょう`Watermarker`クラス。
```csharp
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    //ウォーターマークを追加するコードはここにあります
}
```
## ステップ 5: 透かしを作成する
ドキュメントに追加できるテキストの透かしを作成します。必要に応じて、テキスト、フォント、サイズ、その他のプロパティをカスタマイズできます。
```csharp
TextWatermark watermark = new TextWatermark("Test watermark", new Font("Arial", 12));
```
自由に変更してください`"Test watermark"`, `"Arial"`、 そして`12`好みのテキスト、フォント、サイズに変更します。
## ステップ 6: 透かしを追加する
を使用して文書に透かしを追加します。`Add`の方法`Watermarker`クラス。
```csharp
watermarker.Add(watermark);
```
## ステップ 7: 透かし入りのドキュメントを保存する
最後に、透かし入りのドキュメントを指定した出力ファイル パスに保存します。
```csharp
watermarker.Save(outputFileName);
```
## 結論
パスワードで保護されたドキュメントにウォーターマークを追加するのは、Groupdocs for .NET を使用する簡単なプロセスです。これらの簡単な手順に従うことで、要件に従ってドキュメントが保護され、ブランド化されることを確認できます。セキュリティ、ブランディング、コンプライアンスのいずれの目的であっても、文書に透かしを入れるのがかつてないほど簡単になります。
## よくある質問
### Groupdocs.Watermark for .NET を使用して画像のウォーターマークを追加できますか?
はい、テキストと画像の両方の透かしを追加できます。単純に使用してください`ImageWatermark`の代わりにクラス`TextWatermark`.
### 文書から透かしを削除することはできますか?
はい。Groupdocs.Watermark for .NET は、ウォーターマークを検索および削除するメソッドを提供します。
### Groupdocs.Watermark for .NET は PDF 以外のドキュメント形式をサポートしていますか?
はい、Word、Excel、PowerPoint などを含む幅広い形式をサポートしています。
### 透かしの外観をカスタマイズできますか?
絶対に！フォント、サイズ、色、不透明度などをカスタマイズできます。
### 問題が発生した場合はどこでサポートを受けられますか?
を訪問できます。[Groupdocs サポート フォーラム](https://forum.groupdocs.com/c/watermark/19)助けと導きのために。