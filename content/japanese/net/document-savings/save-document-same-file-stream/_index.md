---
title: ドキュメントを同じファイルまたはストリームに保存
linktitle: ドキュメントを同じファイルまたはストリームに保存
second_title: GroupDocs.Watermark .NET API
description: Groupdocs.Watermark for .NET を使用してドキュメントにウォーターマークを追加する方法を学びます。このガイドでは、文書の保護と整合性を確保するための手順を説明します。
weight: 10
url: /ja/net/document-savings/save-document-same-file-stream/
---
## 導入
今日のデジタル時代では、知的財産を保護し、ブランドの完全性を確保するために、文書に透かしを追加することが不可欠になっています。 Groupdocs.Watermark for .NET は、ウォーターマークをドキュメントにシームレスに埋め込みたい開発者に堅牢なソリューションを提供します。この包括的なガイドでは、Groupdocs.Watermark for .NET を使用して、ウォーターマーク付きのドキュメントを同じファイルまたはストリームに保存する手順を説明します。
## 前提条件
チュートリアルに入る前に、次のものが揃っていることを確認してください。
1. 開発環境: Visual Studio がマシンにインストールされています。
2. .NET Framework: .NET Framework 4.0 以降を使用していることを確認してください。
3.  Groupdocs.Watermark for .NET: 最新バージョンを次の場所からダウンロードしてインストールします。[サイト](https://releases.groupdocs.com/Watermark/net/).
4. ライセンス: から一時ライセンスまたは永久ライセンスを取得します。[ここ](https://purchase.groupdocs.com/temporary-license/).
## 名前空間のインポート
.NET プロジェクトで Groupdocs.Watermark の使用を開始するには、必要な名前空間をインポートする必要があります。
```csharp
using System;
using System.IO;
using GroupDocs.Watermark.Watermarks;
```
## ステップ 1: プロジェクトをセットアップする
ドキュメントに透かしを追加する前に、.NET プロジェクトを設定する必要があります。その方法は次のとおりです。
1. 新しいプロジェクトを作成する: Visual Studio を開き、新しいコンソール アプリケーションを作成します。
2. Groupdocs.Watermark 参照の追加: ソリューション エクスプローラーでプロジェクトを右クリックし、[NuGet パッケージの管理] を選択して、Groupdocs.Watermark パッケージをインストールします。
## ステップ 2: ドキュメントを新しい場所にコピーする
元のドキュメントを直接変更しないようにするには、最初にそれを新しい場所にコピーすることをお勧めします。その方法は次のとおりです。
```csharp
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName("Your Document Path"));
File.Copy("Your Document Path", outputFileName);
```
## ステップ 3: ウォーターマーカーを初期化する
ドキュメントがコピーされたので、ウォーターマーク クラスを初期化してウォーターマークを追加できます。
```csharp
using (Watermarker watermarker = new Watermarker(outputFileName))
{
    //ここに透かしが入ります
}
```
## ステップ 4: テキスト透かしを作成して追加する
次に、テキストの透かしを作成し、ドキュメントに追加します。
```csharp
TextWatermark watermark = new TextWatermark("Test watermark", new Font("Arial", 12));
watermarker.Add(watermark);
```
## ステップ 5: ドキュメントを保存する
最後に、ウォーターマークを適用したドキュメントを保存します。
```csharp
watermarker.Save();
```
## 結論
Groupdocs for .NET を使用してドキュメントにウォーターマークを追加するのは簡単かつ効率的です。上記の手順に従うことで、ドキュメントを保護し、その整合性を簡単に維持できます。詳細については、以下を参照してください。[ドキュメンテーション](https://tutorials.groupdocs.com/Watermark/net/).
## よくある質問
### テキストの代わりに画像を透かしとして使用できますか?
はい、Groupdocs.Watermark を使用すると、画像、図形、テキストを透かしとして使用できます。
### 文書から透かしを削除するにはどうすればよいですか?
ウォーターマークを削除するには、ドキュメント内のウォーターマーク コレクションにアクセスし、`Remove`方法。
### 透かしの外観をカスタマイズすることはできますか?
絶対に。ウォーターマークのフォント、サイズ、色、位置をカスタマイズできます。
### 1 つのドキュメントに複数のウォーターマークを適用できますか?
はい、呼び出して複数の透かしを追加できます。`Add`メソッドを異なる透かしオブジェクトで複数回実行します。
### Groupdocs.Watermark はすべてのドキュメント形式と互換性がありますか?
Groupdocs.Watermark は、PDF、DOCX、PPTX などの幅広いドキュメント形式をサポートしています。