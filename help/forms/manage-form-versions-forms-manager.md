---
title: Forms Manager에서 양식 버전 관리
description: Forms Manager UI에서 적응형 Forms, 양식 단편, 테마 및 기타 에셋의 버전을 만들고 관리하는 방법을 알아봅니다.
feature: Adaptive Forms, Core Components, Foundation Components
role: User, Developer, Admin
badgeSaas: label="AEM Forms" type="Positive" tooltip="AEM Forms에 적용됩니다)."
exl-id: cd2c6e15-99a6-4b4e-bfd1-8291a2001ebe
source-git-commit: 89b0f2a8ca9d2f60365a5c3962b0b4e826f79b3e
workflow-type: tm+mt
source-wordcount: '433'
ht-degree: 5%

---

# Forms Manager UI에서 양식 Assets 버전 관리

<span class="preview"> 이 기능은 조기 액세스 프로그램을 통해 사용할 수 있습니다. 액세스를 요청하려면 공식 주소에서 [aem-forms-ea@adobe.com](mailto:aem-forms-ea@adobe.com)(으)로 이메일을 보내십시오. </span>

Forms Manager는 이제 양식 에셋에 대한 버전 관리를 지원합니다. Forms Manager UI에서 버전을 만들고, 버전 기록을 보고, 이전 버전의 에셋을 복원할 수 있습니다.

## 지원되는 에셋 유형 {#supported-asset-types}

다음 자산 유형에 대한 버전을 만들고 관리할 수 있습니다.

| 에셋 유형 | 설명 |
|---|---|
| 적응형 Forms(핵심 구성 요소) | 핵심 구성 요소를 사용하여 빌드된 적응형 Forms |
| 적응형 Forms(Foundation 구성 요소) | 기초 구성 요소를 사용하여 빌드된 적응형 Forms |
| 양식 조각 | 여러 양식에서 공유된 재사용 가능한 양식 섹션 |
| 테마 | 적응형 Forms에 적용된 시각적 스타일 정의 |
| XDP 템플릿 | XFA 기반 양식 템플릿 |
| 이진 자산 | 양식 DAM 저장소에 저장된 기타 파일 |

## 버전 만들기 {#create-version-forms-manager}

양식 에셋의 버전을 생성하려면 다음을 수행합니다.

1. **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL 양식]** > **[!UICONTROL 양식 및 문서]**&#x200B;로 이동합니다.
1. 양식 또는 자산을 선택합니다.
1. 왼쪽 패널에서 **[!UICONTROL 타임라인]**&#x200B;을 선택합니다.
1. 타임라인 도구 모음에서 **[!UICONTROL 다른 버전으로 저장]**을 클릭합니다.
   ![다른 버전으로 저장](/help/forms/assets/create-version.png)
1. **[!UICONTROL 레이블]**&#x200B;과(와) 선택적 **[!UICONTROL 댓글]**&#x200B;을 입력하여 변경 내용을 설명합니다.
1. **[!UICONTROL 만들기]**를 클릭합니다.
   ![다른 버전으로 저장2](/help/forms/assets/create-version1.png)

버전은 레이블, 주석 및 타임스탬프와 함께 [타임라인] 패널에 표시됩니다.

## 업로드 중 에셋 버전 지정 {#version-on-upload}

기존 에셋과 동일한 이름의 에셋을 업로드할 때 Forms Manager는 업데이트할 에셋을 나열하는 **파일 업로드** 대화 상자를 표시합니다. 대화 상자에 자산 이름, 섹션 및 경로가 표시됩니다.

이름이 같은 에셋이 이미 있으면 업로드가 기존 에셋을 대체하고 새 버전을 자동으로 만듭니다. 타임라인에서 생성된 버전을 볼 수 있습니다.

![버전 업로드를 표시하는 파일 업로드 대화 상자](/help/forms/assets/version-upload.png)

## 버전 내역 보기 {#view-version-history}

에셋의 버전 내역을 보려면 다음과 같이 하십시오.

1. Forms Manager에서 자산을 선택합니다.
1. 왼쪽 패널에서 **[!UICONTROL 타임라인]**을 선택합니다.
   ![버전 기록](/help/forms/assets/version-history.png)

타임라인에는 모든 버전 항목이 활동 이벤트와 함께 표시됩니다. 각 항목에는 레이블, 댓글, 작성자 및 타임스탬프가 표시됩니다.

## 이전 버전 복원 {#restore-version}

자산을 이전 버전으로 복원하려면 다음 작업을 수행하십시오.

1. Forms Manager에서 자산을 선택합니다.
1. 왼쪽 패널에서 **[!UICONTROL 타임라인]**&#x200B;을 선택합니다.
1. 복원할 버전을 선택합니다.
1. **[!UICONTROL 이 버전으로 되돌리기]**를 클릭합니다.
   ![버전 되돌리기](/help/forms/assets/revert-version.png)

>[!NOTE]
>
>이미지를 이전 버전으로 되돌릴 수 없습니다. 적응형 Forms, 양식 단편, 테마 및 XDP 템플릿을 포함한 다른 모든 에셋 유형은 버전 복원을 지원합니다.

## 추가 참조 {#see-also}

* [적응형 양식에 대한 버전 관리, 검토 및 주석 달기](/help/forms/add-comments-annotations-versioning-adaptive-form-core-components.md)
* [양식 및 관련 에셋 가져오기 및 내보내기](/help/forms/import-export-forms-templates.md)
* [양식 게시 및 게시 취소](/help/forms/publishing-unpublishing-forms.md)
