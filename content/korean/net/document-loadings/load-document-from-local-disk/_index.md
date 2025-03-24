---
title: 로컬 디스크에서 문서 로드
linktitle: 로컬 디스크에서 문서 로드
second_title: GroupDocs.Watermark .NET API
description: Groupdocs for .NET으로 문서를 보호하고 관리하세요. 워터마크를 원활하게 추가하려면 자세한 가이드를 따르세요.
weight: 10
url: /ko/net/document-loadings/load-document-from-local-disk/
---

# 로컬 디스크에서 문서 로드

## 소개
워터마킹 문서는 오늘날의 디지털 시대에 콘텐츠 보호, 소유권 주장 및 기밀성을 보장하는 데 필수적입니다. .NET용 Groupdocs.Watermark는 개발자가 다양한 문서 형식의 워터마크를 추가, 검색 및 관리할 수 있는 강력한 라이브러리입니다. 이 자습서에서는 자세한 단계별 지침을 통해 .NET용 Groupdocs.Watermark를 사용하여 문서에 워터마크를 추가하는 과정을 안내합니다.
## 전제조건
구현을 시작하기 전에 다음 사항을 확인하세요.
1. Visual Studio 설치: Visual Studio 또는 다른 호환 가능한 .NET IDE가 필요합니다.
2.  .NET용 Groupdocs.Watermark: 다음에서 라이브러리를 다운로드하세요.[다운로드 링크](https://releases.groupdocs.com/Watermark/net/).
3. .NET Framework: .NET Framework 4.6.1 이상이 설치되어 있는지 확인하세요.
4. 샘플 문서: 워터마킹 프로세스를 테스트하기 위해 샘플 문서를 준비합니다.
## 네임스페이스 가져오기
시작하려면 프로젝트에서 필요한 네임스페이스를 가져와야 합니다. 이는 워터마킹에 필요한 클래스와 메서드에 액세스하는 데 필수적입니다.
```csharp
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## 1단계: 로컬 디스크에서 문서 로드
먼저 로컬 디스크에서 문서를 로드해야 합니다. 이 문서는 워터마크를 추가할 문서입니다.
워터마크를 추가할 문서의 경로를 정의하세요.
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
```
## 2단계: 로드 옵션 초기화
 다음으로 로드 옵션을 초기화합니다. 예를 들어, Word 문서로 작업하는 경우 다음을 사용합니다.`WordProcessingLoadOptions`.
```csharp
var loadOptions = new WordProcessingLoadOptions();
```
## 3단계: 워터마커 생성 및 구성
 이제`Watermarker` 수업. 이 인스턴스는 문서에 워터마크를 관리하고 적용하는 데 사용됩니다.
```csharp
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // 이 블록에는 워터마크를 추가하고 저장하는 추가 단계가 포함됩니다.
}
```
## 4단계: 워터마크 만들기
텍스트 워터마크를 만듭니다. 이 워터마크에는 귀하가 선택한 모든 텍스트가 포함될 수 있습니다. 여기서는 "테스트 워터마크"를 사용하겠습니다.
```csharp
TextWatermark watermark = new TextWatermark("Test watermark", new Font("Arial", 12));
```
## 5단계: 문서에 워터마크 추가
생성된 워터마크를 다음을 사용하여 문서에 추가합니다.`Add` 의 방법`Watermarker` 수업.
```csharp
watermarker.Add(watermark);
```
## 6단계: 워터마크가 있는 문서 저장
마지막으로 워터마크가 있는 문서를 지정된 경로에 저장합니다.
```csharp
watermarker.Save(outputFileName);
```

## 결론
Groupdocs for .NET을 사용하여 문서에 워터마크를 추가하는 것은 간단하고 효율적입니다. 이 가이드는 환경 설정부터 워터마크가 있는 문서 저장까지 전체 과정을 안내했습니다. 이 강력한 도구를 사용하면 문서를 보호하고 지적 재산을 안전하게 보호할 수 있습니다. 
 자세한 내용은[선적 서류 비치](https://tutorials.groupdocs.com/Watermark/net/) , 문제가 발생하면[지원 포럼](https://forum.groupdocs.com/c/watermark/19) 도움을 받을 수 있는 훌륭한 장소입니다. 
## FAQ
### 워터마크에 사용자 정의 글꼴을 사용할 수 있습니까?
예, Groupdocs는 사용자 정의 글꼴을 지원합니다. 시스템에 설치된 글꼴을 지정할 수 있습니다.
### 어떤 유형의 문서가 지원되나요?
Groupdocs.Watermark는 Word, Excel, PDF, PowerPoint 등을 포함한 광범위한 문서 형식을 지원합니다.
### 문서에서 워터마크를 제거하려면 어떻게 해야 합니까?
 당신은 사용할 수 있습니다`Remove` 에서 제공하는 방법`Watermarker` 워터마크를 제거하는 클래스입니다.
### 이미지 워터마크를 추가할 수 있나요?
 예, 다음을 사용하여 이미지 워터마크를 추가할 수 있습니다.`ImageWatermark` 수업.
### Groupdocs.Watermark를 무료로 사용해 볼 수 있나요?
 물론, 당신은 다운로드할 수 있습니다[무료 시험판](https://releases.groupdocs.com/) 구매하기 전에 라이브러리를 평가하십시오.