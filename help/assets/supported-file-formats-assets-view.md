---
title: 지원되는 파일 형식
description: ' [!DNL Assets view]의 다양한 사용 사례에 대해 지원되는 파일 형식'
role: User, Leader, Admin, Architect, Developer
contentOwner: AG
exl-id: 5936ace2-318e-4888-9ad4-23e6f6bfb857
feature: Asset Management, Publishing, Collaboration, Asset Processing
source-git-commit: 7c8f54d7c1139485717cc42dafbc87be74fd5883
workflow-type: tm+mt
source-wordcount: '527'
ht-degree: 94%

---

# [!DNL Assets view]에서 지원되는 파일 형식 {#file-format-support}

[!DNL Assets view]는 다양한 파일 형식을 지원하며 각 기능 또한 다양한 파일 형식을 지원합니다.

* ![image file type icon](assets/image-icon.svg) 이미지: JPG, PNG, GIF, TIFF 등
* ![creative cloudtype icon](assets/creative-cloud-files.svg) Creative Cloud 파일: PSD, PSB, AI 및 INDD
* ![camera type icon](assets/camera-icon.svg) Camera RAW 파일: CR2/CR3, NEF, SRW/SRF 및 기타
* ![document file type icon](assets/document-icon.svg) 문서: DOCX, PDF, PPTX 및 XLSX
* ![video file type icon](assets/video-icon.svg) 비디오: MP4

[!DNL Assets view]는 스토리지, 업로드, 복사, 이동, 삭제 및 메타데이터 추가와 같은 기본 서비스가 포함된 모든 바이너리 파일 유형을 지원합니다.

[!DNL Assets view]는 또한 Adobe Camera Raw에서 제공되는 Canon(CR2/CR3), Nikon(NEF), Sony(SRW/SRF), Fujifilm(RAW), Olympus(ORF) 등 다양한 주요 카메라 제조업체의 Camera RAW 파일을 지원합니다.

아래에 설명된 바와 같이 파일 유형에 따라 사용 사례 및 기능에 대한 지원 수준이 다릅니다. 범례를 사용하여 지원 수준을 이해할 수 있습니다.

| 지원 수준 | 설명 |
|-------------------|-------------------------|
| ✓ | 지원됨 |
| ✓ ‡ | 조건부로 지원됨 |
| − | 해당되지 않음 |

## 에셋 추가, 업로드 및 보기 {#support-to-upload-view}

<!-- TBD: For AEM, AI files require the PDF option to be selected when saving the AI file.
-->

| 에셋 유형 | [찾아보기](/help/assets/navigate-assets-view.md) | 복사 | [업로드](/help/assets/add-delete-assets-view.md) | 만들기 | [삭제](/help/assets/add-delete-assets-view.md#delete-assets) | 세부 사항 | 이미지 확대/축소 | [최근에 본 항목](/help/assets/navigate-assets-view.md) |
|-------------------|----------|----------|----------|----------|----------|-------------------|------------|-----------------|
| 래스터 이미지 | ✓ | ✓ | ✓ | − | ✓ | ✓ | ✓ | ✓ |
| RAW 파일 | ✓ | ✓ | ✓ | − | ✓ | ✓ | ✓ | ✓ |
| 폴더 | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | − | − |
| MP4 비디오 | ✓ | ✓ | ✓ | − | ✓ | ✓ ‡ | − | ✓ |
| PDF | ✓ | ✓ | ✓ | − | ✓ | ✓ | − | ✓ |
| PSD, PSB, AI 및 INDD | ✓ | ✓ | ✓ | − | ✓ | ✓ ‡ | − | ✓ |
| 기타 바이너리 파일 | ✓ | ✓ | ✓ | − | ✓ | ✓ | − | ✓ |

<!-- Hiding CC Libraries (considered beta) as per PM feedback.
| CC Libraries  | &#10003; | &minus;  | &#10003; | &#10003; | &#10003; | &#10003; | &minus;    | &minus;         |
-->

## 에셋 검색, 사용 및 편집 {#support-to-search-use-edit}

| 에셋 유형 | [다운로드](/help/assets/manage-organize-assets-view.md#download) | 드래그 앤 드롭 | [이미지 편집기](/help/assets/edit-images-assets-view.md) | [검색](/help/assets/search-assets-view.md) | [스마트 태그](/help/assets/metadata-assets-view.md#tags) | [이름 변경](/help/assets/manage-organize-assets-view.md) | [버전](/help/assets/manage-organize-assets-view.md#versions-of-assets) |
|---------------|----------|---------------|--------------|----------|------------|----------|----------|
| 래스터 이미지 | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| RAW 파일 | ✓ | ✓ | − | ✓ | ✓ | ✓ | ✓ | ✓ |
| 폴더 | ✓ | ✓ | − | ✓ | − | ✓ | ✓ |
| 비디오 | ✓ | ✓ | − | ✓ | ✓ | ✓ | ✓ |
| CC Libraries | − | − | − | − | − | ✓ | ✓ |
| PDF | ✓ | ✓ | − | ✓ | ✓ | ✓ | ✓ |
| PSD 및 PSB | ✓ | ✓ | − | ✓ | ✓ | ✓ | ✓ |
| AI 및 INDD | ✓ | ✓ | − | ✓ | − | ✓ | ✓ |
| 기타 바이너리 파일 | ✓ | ✓ | − | ✓ | − | ✓ | ✓ |


## 에셋 검토 및 공동 작업 {#support-to-review-collaborate}

| 에셋 유형 | 주석 | 댓글 | 작업 생성 및 검토 |
|---------------|----------|----------|-------------------------|
| 래스터 이미지 | ✓ | ✓ | ✓ |
| RAW 파일 | ✓ | ✓ | ✓ |
| 폴더 | − | − | − |
| 비디오 | − | ✓ | ✓ |
| CC Libraries | − | − | − |
| PDF | − | ✓ | ✓ |
| PSD, PSB, AI 및 INDD | − | ✓ | ✓ |
| 기타 바이너리 파일 | − | ✓ | ✓ |
| DOC | − | ✓ | ✓ |
| DOCX | − | ✓ | ✓ |
| PPT | − | ✓ | ✓ |
| PPTX | − | ✓ | ✓ |
| XLS | − | ✓ | ✓ |
| XLSX | − | ✓ | ✓ |
| TXT | − | ✓ | ✓ |
| RTF | − | ✓ | ✓ |

## 기타 에셋 관리 작업 {#support-to-manage-assets}

| 에셋 유형 | [메타데이터](/help/assets/metadata-assets-view.md) | [표현물](/help/assets/add-delete-assets-view.md#renditions) | [휴지통](/help/assets/add-delete-assets-view.md#delete-assets) | 복사 | 이동 |
|---------------|-------------------|------------|----------|----------|----------|
| 래스터 이미지 | ✓ | ✓ | ✓ | ✓ | ✓ |
| RAW 파일 | ✓ | ✓ | ✓ | ✓ | ✓ |
| 폴더 | ✓ | − | ✓ | ✓ | ✓ |
| 비디오 | ✓ | − | ✓ | ✓ | ✓ |
| CC Libraries | ✓ | − | − | − | − |
| PDF | ✓ | − | ✓ | ✓ | ✓ |
| AI 및 INDD | ✓ | − | ✓ | ✓ | ✓ |
| PSD 및 PSB | ✓ | ✓ | ✓ | ✓ | ✓ |
| 기타 바이너리 파일 | ✓ | − | ✓ | ✓ | ✓ |

[!DNL Adobe Asset Link] 사용자는 지원되는 [!DNL Adobe Creative Cloud] 데스크탑 애플리케이션에서 [!DNL Assets view] 저장소에 파일을 업로드하고 체크인(새 버전 업로드)할 수 있습니다.

<!-- TBD: Saving the template table separately for later use.
| Asset type    | Features |
|---------------|----------|
| Raster images |          |
| Folders       |          |
| Videos        |          |
| CC Libraries  |          |
| PDF files     |          |
| PSD, PSB           |          |
| AI            |          |
| INDD          |          |

>[!MORELIKETHIS]
>
>* []()
-->

## 다음 단계 {#next-steps}

* Assets 보기 사용자 인터페이스에서 사용 가능한 [!UICONTROL 피드백] 옵션을 사용하여 제품 피드백 제공

* 오른쪽 사이드바에서 사용 가능한 [!UICONTROL 이 페이지 편집], ![페이지 편집](assets/do-not-localize/edit-page.png), [!UICONTROL 문제 기록] 또는 ![GitHub 문제 생성](assets/do-not-localize/github-issue.png)을 사용하여 설명서 피드백 제공

* [고객 지원 센터](https://experienceleague.adobe.com/?support-solution=General#support) 문의
