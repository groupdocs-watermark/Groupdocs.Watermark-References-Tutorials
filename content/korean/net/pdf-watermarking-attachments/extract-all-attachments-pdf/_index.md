---
title: PDF에서 모든 첨부 파일 추출
linktitle: PDF에서 모든 첨부 파일 추출
second_title: GroupDocs.Watermark .NET API
description: .NET용 Groupdocs.Watermark를 사용하여 PDF에서 모든 첨부 파일을 추출하는 방법을 알아보세요. 원활한 추출 과정을 위해 단계별 가이드를 따르세요.
weight: 22
url: /ko/net/pdf-watermarking-attachments/extract-all-attachments-pdf/
---

# PDF에서 모든 첨부 파일 추출

## 소개
PDF 문서에서 첨부 파일을 손쉽게 추출하고 싶으십니까? 글쎄, 당신은 바로 이곳에 있어요! 이 포괄적인 튜토리얼에서는 .NET용 Groupdocs.Watermark를 사용하여 PDF에서 모든 첨부 파일을 추출하는 과정을 안내합니다. 이 강력한 라이브러리를 통해 개발자는 다양한 문서 형식의 워터마크를 관리할 수 있을 뿐만 아니라 포함된 파일을 추출하는 강력한 기능도 포함하고 있습니다. 숙련된 개발자이든 이제 막 시작하는 개발자이든 이 단계별 가이드를 통해 프로세스를 쉽게 수행할 수 있습니다.
## 전제조건
코드를 살펴보기 전에 시작하는 데 필요한 기본 사항을 살펴보겠습니다. 준비가 되었는지 확인하기 위한 간단한 체크리스트는 다음과 같습니다.
1. .NET 환경: .NET 개발 환경이 설정되어 있는지 확인하세요. Visual Studio 또는 원하는 다른 .NET IDE를 사용할 수 있습니다.
2.  .NET용 Groupdocs.Watermark: 다음에서 최신 버전의 .NET용 Groupdocs.Watermark를 다운로드하여 설치하세요.[여기](https://releases.groupdocs.com/Watermark/net/).
3. 개발 기술: C# 프로그래밍에 대한 기본적인 이해 및 .NET 라이브러리에 대한 지식.
4. 샘플 PDF 문서: 테스트에 사용할 수 있는 첨부 파일이 포함된 샘플 PDF 문서를 준비하세요.
## 네임스페이스 가져오기
코딩을 시작하기 전에 필요한 네임스페이스를 가져와야 합니다. 이를 통해 코드를 구성하고 사용할 클래스와 메서드에 액세스할 수 있습니다.
```csharp
using System;
using System.IO;
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
```
## 1단계: 프로젝트 설정
먼저, 프로젝트를 설정해 보겠습니다. .NET 개발 환경을 열고 새 콘솔 애플리케이션을 만듭니다.
### 새 프로젝트 만들기
1. 비주얼 스튜디오를 엽니다.
2. "새 프로젝트 만들기"를 선택하세요.
3. 기본 설정에 따라 "콘솔 앱(.NET Core)" 또는 ".NET Framework"를 선택합니다.
4. 프로젝트 이름을 지정하고 "만들기"를 클릭하세요.
### .NET용 Groupdocs.Watermark 추가
1. 솔루션 탐색기에서 프로젝트를 마우스 오른쪽 버튼으로 클릭합니다.
2. "NuGet 패키지 관리"를 선택하십시오.
3. "Groupdocs.Watermark"를 검색하여 최신 버전을 설치하세요.
## 2단계: 경로 정의
다음으로 문서 및 출력 디렉터리의 경로를 정의해야 합니다. 여기에 PDF와 추출된 첨부 파일이 저장됩니다.

 당신의`Program.cs` 파일에 다음 코드를 추가하여 경로를 정의합니다.
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
 바꾸다`"Your Document Path"` 그리고`"Your Document Directory"` 시스템의 실제 경로와 함께.
## 3단계: PDF 문서 로드
 이제 Groupdocs.Watermark를 사용하여 PDF 문서를 로드해 보겠습니다. 이 단계에는 로드 옵션을 생성하고`Watermarker` 수업.
### 로드 옵션 생성
 먼저 인스턴스를 생성합니다.`PdfLoadOptions`:
```csharp
var loadOptions = new PdfLoadOptions();
```
### 워터마커 초기화
 다음으로`Watermarker` 문서를 로드하는 클래스:
```csharp
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // 귀하의 코드는 여기에 저장됩니다
}
```
## 4단계: 첨부파일 추출
문서가 로드되었으면 이제 첨부 파일을 추출할 차례입니다. 당신은`PdfContent` 클래스를 사용하여 첨부 파일에 액세스한 다음 지정된 출력 디렉터리에 저장합니다.
### PDF 콘텐츠 가져오기
 내부`using` 차단하고 PDF 콘텐츠를 가져옵니다.
```csharp
PdfContent pdfContent = watermarker.GetContent<PdfContent>();
```
### 첨부 파일을 통한 루프
PDF의 각 첨부 파일을 반복합니다.
```csharp
foreach (PdfAttachment attachment in pdfContent.Attachments)
{
    Console.WriteLine("Name: {0}", attachment.Name);
    Console.WriteLine("Description: {0}", attachment.Description);
    Console.WriteLine("File type: {0}", attachment.GetDocumentInfo().FileType);
    // 첨부파일을 디스크에 저장
    File.WriteAllBytes(Path.Combine(outputDirectory, attachment.Name), attachment.Content);
}
```
이 코드는 각 첨부 파일을 추출하여 출력 디렉터리에 저장합니다. 또한 각 연결에 대한 몇 가지 기본 정보를 콘솔에 인쇄합니다.
## 결론
그리고 거기에 있습니다! .NET용 Groupdocs.Watermark를 사용하여 PDF에서 첨부 파일을 성공적으로 추출했습니다. 이 튜토리얼에서는 프로젝트 설정, 문서 로드 및 첨부 파일 추출 과정을 단계별로 안내했습니다. 이러한 기술을 사용하면 이제 .NET 애플리케이션에서 PDF 첨부 파일을 쉽게 관리하고 조작할 수 있습니다.
## FAQ
### .NET용 Groupdocs.Watermark란 무엇입니까?
.NET용 Groupdocs.Watermark는 PDF를 포함한 다양한 문서 형식의 워터마크를 추가, 제거 및 관리하기 위한 포괄적인 라이브러리입니다. 또한 내장된 파일을 추출하는 기능도 제공합니다.
### PDF에 포함된 다른 유형의 파일을 추출할 수 있습니까?
예, .NET용 Groupdocs.Watermark를 사용하면 첨부 파일뿐만 아니라 PDF에 포함된 모든 유형의 파일을 추출할 수 있습니다.
### 무료 평가판이 제공되나요?
 예, 다음에서 .NET용 Groupdocs.Watermark 무료 평가판을 다운로드할 수 있습니다.[여기](https://releases.groupdocs.com/).
### 문제가 발생하면 어떻게 지원을 받을 수 있나요?
 방문하시면 지원을 받으실 수 있습니다.[Groupdocs.Watermark 지원 포럼](https://forum.groupdocs.com/c/watermark/19).
### .NET용 Groupdocs.Watermark를 사용하려면 라이센스가 필요합니까?
 예, 프로덕션 환경에서 라이브러리를 사용하려면 라이선스가 필요합니다. 라이센스를 구매하실 수 있습니다[여기](https://purchase.groupdocs.com/buy) 아니면 임시면허를 취득하세요.[여기](https://purchase.groupdocs.com/temporary-license/).