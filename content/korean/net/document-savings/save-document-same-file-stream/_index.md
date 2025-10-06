---
title: 동일한 파일 또는 스트림에 문서 저장
linktitle: 동일한 파일 또는 스트림에 문서 저장
second_title: GroupDocs.Watermark .NET API
description: .NET용 Groupdocs.Watermark를 사용하여 문서에 워터마크를 추가하는 방법을 알아보세요. 이 가이드는 문서 보호 및 무결성을 보장하기 위한 지침을 제공합니다.
weight: 10
url: /ko/net/document-savings/save-document-same-file-stream/
type: docs
---
# 동일한 파일 또는 스트림에 문서 저장

## 소개
오늘날 디지털 시대에 문서에 워터마크를 추가하는 것은 지적 재산을 보호하고 브랜드 무결성을 보장하는 데 필수적입니다. .NET용 Groupdocs.Watermark는 워터마크를 문서에 원활하게 포함시키려는 개발자를 위한 강력한 솔루션을 제공합니다. 이 포괄적인 가이드는 .NET용 Groupdocs.Watermark를 사용하여 워터마크가 있는 문서를 동일한 파일이나 스트림에 저장하는 단계를 안내합니다.
## 전제조건
튜토리얼을 시작하기 전에 다음 사항을 확인하세요.
1. 개발 환경: 컴퓨터에 Visual Studio가 설치되어 있습니다.
2. .NET Framework: .NET Framework 4.0 이상이 있는지 확인하세요.
3.  .NET용 Groupdocs.Watermark: 다음에서 최신 버전을 다운로드하여 설치하세요.[대지](https://releases.groupdocs.com/Watermark/net/).
4.  라이센스: 임시 또는 영구 라이센스를 얻습니다.[여기](https://purchase.groupdocs.com/temporary-license/).
## 네임스페이스 가져오기
.NET 프로젝트에서 Groupdocs.Watermark 사용을 시작하려면 필요한 네임스페이스를 가져와야 합니다.
```csharp
using System;
using System.IO;
using GroupDocs.Watermark.Watermarks;
```
## 1단계: 프로젝트 설정
문서에 워터마크를 추가하기 전에 .NET 프로젝트를 설정해야 합니다. 방법은 다음과 같습니다.
1. 새 프로젝트 만들기: Visual Studio를 열고 새 콘솔 애플리케이션을 만듭니다.
2. Groupdocs.Watermark 참조 추가: 솔루션 탐색기에서 프로젝트를 마우스 오른쪽 단추로 클릭하고 "NuGet 패키지 관리"를 선택한 다음 Groupdocs.Watermark 패키지를 설치합니다.
## 2단계: 문서를 새 위치에 복사
원본 문서를 직접 변경하지 않으려면 먼저 새 위치에 복사하는 것이 좋습니다. 방법은 다음과 같습니다.
```csharp
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName("Your Document Path"));
File.Copy("Your Document Path", outputFileName);
```
## 3단계: 워터마커 초기화
이제 문서가 복사되었으므로 Watermarker 클래스를 초기화하여 워터마크를 추가할 수 있습니다.
```csharp
using (Watermarker watermarker = new Watermarker(outputFileName))
{
    // 워터마킹이 여기에 표시됩니다.
}
```
## 4단계: 텍스트 워터마크 생성 및 추가
다음으로 텍스트 워터마크를 만들어 문서에 추가합니다.
```csharp
TextWatermark watermark = new TextWatermark("Test watermark", new Font("Arial", 12));
watermarker.Add(watermark);
```
## 5단계: 문서 저장
마지막으로 워터마크가 적용된 문서를 저장합니다.
```csharp
watermarker.Save();
```
## 결론
Groupdocs for .NET을 사용하여 문서에 워터마크를 추가하는 것은 간단하고 효율적입니다. 위에 설명된 단계를 따르면 문서를 보호하고 손쉽게 무결성을 유지할 수 있습니다. 자세한 내용은 다음을 참조하세요.[선적 서류 비치](https://tutorials.groupdocs.com/Watermark/net/).
## FAQ
### 텍스트 대신 이미지를 워터마크로 사용할 수 있나요?
예, Groupdocs.Watermark를 사용하면 이미지, 모양 및 텍스트를 워터마크로 사용할 수 있습니다.
### 문서에서 워터마크를 어떻게 제거하나요?
 문서의 워터마크 컬렉션에 접근하고 다음을 사용하여 워터마크를 제거할 수 있습니다.`Remove` 방법.
### 워터마크의 모양을 사용자 정의할 수 있습니까?
전적으로. 워터마크의 글꼴, 크기, 색상, 위치를 사용자 정의할 수 있습니다.
### 단일 문서에 여러 워터마크를 적용할 수 있나요?
 예, 다음을 호출하여 여러 워터마크를 추가할 수 있습니다.`Add` 다른 워터마크 개체를 사용하여 메서드를 여러 번 사용하세요.
### Groupdocs.Watermark는 모든 문서 형식과 호환됩니까?
Groupdocs.Watermark는 PDF, DOCX, PPTX 등 다양한 문서 형식을 지원합니다.