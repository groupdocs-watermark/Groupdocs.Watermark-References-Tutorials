---
title: 비밀번호로 보호된 문서 로드
linktitle: 비밀번호로 보호된 문서 로드
second_title: GroupDocs.Watermark .NET API
description: 단계별 가이드를 통해 Groupdocs for .NET을 사용하여 비밀번호로 보호된 문서에 워터마크를 추가하는 방법을 알아보세요. 파일을 쉽게 보호하고 브랜드화하세요.
weight: 13
url: /ko/net/document-loadings/load-password-protected-document/
---

# 비밀번호로 보호된 문서 로드

## 소개
문서가 비밀번호로 보호되어 있더라도 워터마크를 추가하여 문서를 보호하고 싶으십니까? .NET용 Groupdocs.Watermark는 바로 이러한 작업을 수행할 수 있는 강력한 도구입니다. 이 튜토리얼에서는 비밀번호로 보호된 문서를 로드하고 .NET용 Groupdocs.Watermark를 사용하여 워터마크를 추가하는 과정을 안내합니다. 뛰어들어보자!
## 전제조건
시작하기 전에 다음 사항이 있는지 확인하세요.
1. Visual Studio: 컴퓨터에 설치된 모든 버전의 Visual Studio입니다.
2. .NET Framework: .NET Framework 4.6.1 이상이 있는지 확인하십시오.
3. .NET용 Groupdocs.Watermark: 다음에서 .NET용 Groupdocs.Watermark 라이브러리를 다운로드하고 설치합니다.[다운로드 링크](https://releases.groupdocs.com/Watermark/net/).
## 네임스페이스 가져오기
먼저, 필요한 네임스페이스를 프로젝트로 가져와야 합니다. 이를 통해 .NET용 Groupdocs.Watermark에서 제공하는 모든 메서드와 속성에 액세스할 수 있습니다.
```csharp
using GroupDocs.Watermark.Options;
using GroupDocs.Watermark.Watermarks;
using System;
using System.IO;
```
이제 프로세스를 간단하고 따르기 쉬운 단계로 나누어 보겠습니다.
## 1단계: 프로젝트 설정
시작하려면 Visual Studio에서 새 C# 콘솔 애플리케이션을 만듭니다. 프로젝트가 설정되면 NuGet 패키지 관리자를 통해 .NET 라이브러리용 Groupdocs.Watermark를 설치합니다.
1. Visual Studio를 열고 새 콘솔 앱(.NET Framework)을 만듭니다.
2.  이동`Tools` >`NuGet Package Manager` >`Manage NuGet Packages for Solution`.
3.  검색`GroupDocs.Watermark` 그리고 패키지를 설치합니다.
## 2단계: 문서 경로 정의
다음으로, 비밀번호로 보호된 문서의 경로와 워터마크가 있는 문서가 저장될 출력 파일 경로를 정의해야 합니다.
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
```
 바꾸다`"Your Document Path"` 그리고`"Your Document Directory"` 컴퓨터의 실제 경로와 함께.
## 3단계: 비밀번호로 로드 옵션 설정
비밀번호로 보호된 문서를 열려면 로드 옵션에 비밀번호를 제공해야 합니다.
```csharp
LoadOptions loadOptions = new LoadOptions();
loadOptions.Password = "P@$w0rd";
```
 바꾸다`"P@$w0rd"` 문서의 실제 비밀번호로.
## 4단계: 문서 로드
 이제 다음을 사용하여 문서를 로드해 보겠습니다.`Watermarker` 수업.
```csharp
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // 워터마크를 추가하는 코드가 여기에 표시됩니다.
}
```
## 5단계: 워터마크 만들기
문서에 추가할 수 있는 텍스트 워터마크를 만들어 보겠습니다. 필요에 따라 텍스트, 글꼴, 크기 및 기타 속성을 사용자 정의할 수 있습니다.
```csharp
TextWatermark watermark = new TextWatermark("Test watermark", new Font("Arial", 12));
```
 자유롭게 변경하세요.`"Test watermark"`, `"Arial"` , 그리고`12` 원하는 텍스트, 글꼴, 크기로 변경하세요.
## 6단계: 워터마크 추가
 다음을 사용하여 문서에 워터마크를 추가합니다.`Add` 의 방법`Watermarker` 수업.
```csharp
watermarker.Add(watermark);
```
## 7단계: 워터마크가 있는 문서 저장
마지막으로 워터마크가 있는 문서를 지정된 출력 파일 경로에 저장합니다.
```csharp
watermarker.Save(outputFileName);
```
## 결론
비밀번호로 보호된 문서에 워터마크를 추가하는 것은 Watermark for .NET을 사용하는 간단한 과정입니다. 이러한 간단한 단계를 따르면 귀하의 요구 사항에 따라 문서가 보호되고 브랜드화되도록 할 수 있습니다. 보안, 브랜딩, 규정 준수 등을 위해 문서에 워터마킹을 하는 것이 그 어느 때보다 쉬워졌습니다.
## FAQ
### .NET용 Groupdocs.Watermark를 사용하여 이미지 워터마크를 추가할 수 있습니까?
 예, 텍스트와 이미지 워터마크를 모두 추가할 수 있습니다. 간단히`ImageWatermark` 대신 수업`TextWatermark`.
### 문서에서 워터마크를 제거할 수 있나요?
예, .NET용 Groupdocs.Watermark는 워터마크를 검색하고 제거하는 방법을 제공합니다.
### .NET용 Groupdocs.Watermark는 PDF 외에 다른 문서 형식을 지원합니까?
예, Word, Excel, PowerPoint 등을 포함한 다양한 형식을 지원합니다.
### 워터마크의 모양을 사용자 정의할 수 있나요?
전적으로! 글꼴, 크기, 색상, 불투명도 등을 사용자 정의할 수 있습니다.
### 문제가 발생하면 어디서 지원을 받을 수 있나요?
 당신은 방문 할 수 있습니다[Groupdocs 지원 포럼](https://forum.groupdocs.com/c/watermark/19) 도움과 안내를 위해.