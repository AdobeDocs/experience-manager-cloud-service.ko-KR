---
title: 적응형 Forms에 대해 자동 생성된 기록 문서 템플릿을 사용자 지정하는 방법
description: Adobe Forms Designer을 사용하여 적응형 Forms용 자동 생성된 기록 문서(DoR) 템플릿을 다운로드하고, 사용자 지정하고, 다시 업로드하는 방법에 대해 알아봅니다.
feature: Adaptive Forms, Core Components, Foundation Components
role: User, Developer
badgeSaas: label="AEM Forms" type="Positive" tooltip="AEM Forms에 적용됩니다)."
exl-id: 2416add3-0b9d-4a8d-a84d-d65c0762d8e8
source-git-commit: 89b0f2a8ca9d2f60365a5c3962b0b4e826f79b3e
workflow-type: tm+mt
source-wordcount: '852'
ht-degree: 1%

---

# 자동 생성된 기록 문서 템플릿 사용자 지정

<span class="preview"> 이 문서는 적응형 Forms 기반의 **핵심 구성 요소** 및 **기초 구성 요소**&#x200B;에 모두 적용됩니다.</span>

적응형 양식에 대해 기록 문서(DoR)를 자동으로 생성하면 AEM Forms에서 양식 구조를 기반으로 기본 템플릿을 만듭니다. 조직의 브랜딩 및 레이아웃 요구 사항과 일치하도록 이 자동 생성된 템플릿을 사용자 지정할 수 있습니다.

사용자 지정 워크플로에는 다음 세 단계가 포함됩니다.

1. Forms Manager에서 자동 생성된 DoR 템플릿을 다운로드합니다.
1. Adobe Forms Designer을 사용하여 템플릿을 수정합니다.
1. 사용자 지정된 템플릿을 AEM Forms에 다시 업로드하고 사용자 지정 템플릿으로 구성합니다.

## 사전 요구 사항 {#prerequisites}

시작하기 전에 다음을 확인하십시오.

* 템플릿을 다운로드하고 업로드할 수 있는 권한이 있는 AEM Forms Manager에 액세스합니다.
* Adobe Forms Designer이 로컬 컴퓨터에 설치되었습니다.
* **[!UICONTROL 기록 문서 생성]**&#x200B;이 활성화된 적응형 양식입니다.

## 1단계: 자동 생성된 DoR 템플릿 다운로드 {#download-auto-generated-dor-template}

적응형 양식용 자동 생성된 DoR 템플릿(XDP 파일)을 다운로드하려면:

1. AEM Forms 작성자 인스턴스에 로그인합니다.
1. **[!UICONTROL Forms]** > **[!UICONTROL Forms 및 문서]**&#x200B;로 이동합니다.
1. DoR 템플릿을 다운로드할 적응형 양식을 선택하십시오.
1. 선택한 적응형 양식의 속성을 엽니다.
1. 속성 패널에서 **[!UICONTROL 기록 문서 다운로드]** 옵션을 선택하여 자동 생성된 DoR 템플릿(XDP 파일)을 다운로드합니다.
1. 다운로드한 XDP 파일을 로컬 시스템에 저장합니다.


## 2단계: Adobe Forms Designer을 사용하여 템플릿 사용자 지정 {#customize-template-using-designer}

Adobe Forms Designer에서 다운로드한 XDP 템플릿을 열고 조직의 요구 사항에 맞게 수정합니다.

1. 다운로드한 XDP 파일을 **Adobe Forms Designer**&#x200B;에서 엽니다.
1. 필요에 따라 템플릿을 사용자 정의합니다. 맞춤화의 예는 다음과 같습니다.

   * **여러 마스터 페이지**: 기록 문서의 특정 페이지에 대해 다른 레이아웃을 정의할 마스터 페이지를 추가합니다. 예를 들어 회사 머리글이 있는 별도의 첫 번째 페이지와 더 간단한 레이아웃이 있는 후속 페이지를 사용합니다.
   * **글꼴 색상 및 글꼴 패밀리**: 회사 브랜드 지침에 맞게 글꼴 색상, 크기 및 패밀리를 변경합니다.
   * **사용자 지정 요소**: 회사 로고, 머리글, 바닥글 및 면책조항 텍스트와 같은 요소를 추가하여 일관된 브랜드 정체성을 설정합니다.
   * **페이지 레이아웃 및 스타일 지정**: 여백, 간격 및 전체 페이지 구조를 조정하여 가독성을 향상시킵니다.
   * **필드 스타일 및 위치 지정**: 기본 레이아웃과 일치하도록 양식 필드의 모양과 위치를 수정합니다.

1. 사용자 지정된 XDP 템플릿을 저장합니다.

>[!NOTE]
>
> 템플릿에 있는 스크립트를 제거하거나 수정하지 마십시오. 스크립트를 수정하면 데이터 바인딩 및 기록 문서 생성에 영향을 줄 수 있습니다.

## 3단계: 사용자 지정된 템플릿을 AEM에 다시 업로드 {#reupload-customized-template}

템플릿을 사용자 지정한 후 AEM Forms에 업로드하고 이를 사용하도록 적응형 양식을 구성하십시오.

1. 사용자 지정된 XDP 템플릿을 AEM Forms 인스턴스에 업로드합니다.
   * **[!UICONTROL Forms]** > **[!UICONTROL Forms 및 문서]**&#x200B;로 이동합니다.
   * **[!UICONTROL 만들기]** > **[!UICONTROL 파일 업로드]**&#x200B;를 선택하고 사용자 지정된 XDP 파일을 업로드하십시오.

그런 다음 사용자 지정 템플릿을 사용하도록 양식을 구성합니다. 양식이 핵심 구성 요소를 기반으로 하는지 또는 기초 구성 요소를 기반으로 하는지에 따라 단계가 달라집니다.

>[!BEGINTABS]

>[!TAB 핵심 구성 요소]

핵심 구성 요소 기반 적응형 Forms의 경우:

1. 사용자 지정 템플릿을 적용할 편집기에서 적응형 양식을 엽니다.
1. 콘텐츠 트리에서 **[!UICONTROL 안내 컨테이너]**(루트 패널)를 선택하십시오.
1. **[!UICONTROL 속성]**&#x200B;을 열고 **[!UICONTROL 기록 문서]**(DoR) 아이콘을 클릭하여 기록 문서 속성을 엽니다.
1. **[!UICONTROL 기본]** 탭에서 **[!UICONTROL 템플릿]** 드롭다운을 열고 **[!UICONTROL 사용자 지정]**&#x200B;을 선택합니다.
1. 업로드한 사용자 지정 XDP 템플릿을 찾아 선택합니다.
1. 저장할 확인 표시를 선택합니다.

   ![기록 문서 속성 - 사용자 지정(핵심 구성 요소)으로 설정된 템플릿](/help/forms/assets/submission-pdf-dor-custom-template.png)

>[!TAB 기초 구성 요소]

기초 구성 요소 기반 적응형 Forms의 경우:

1. 사용자 지정 템플릿을 적용할 편집기에서 적응형 양식을 엽니다.
1. 루트 패널(양식 컨테이너)을 선택합니다.
1. 속성 패널 또는 DoR 탭에서 **[!UICONTROL 기록 속성 문서]**&#x200B;를 엽니다.
1. **[!UICONTROL 기본]** 탭에서 **[!UICONTROL 템플릿]** 드롭다운을 열고 **[!UICONTROL 사용자 지정]**&#x200B;을 선택합니다.
1. 업로드한 사용자 지정 XDP 템플릿을 찾아 선택합니다.
1. **[!UICONTROL 완료]**&#x200B;를 선택하여 저장합니다.

   ![기록 문서 속성 - 사용자 지정(Foundation 구성 요소)으로 설정된 템플릿](/help/forms/assets/dor-custom-template-foundation-components.png)

>[!ENDTABS]

이제 기록 문서를 생성할 때 적응형 양식에서 사용자 지정된 템플릿을 사용합니다.

## 사용자 지정된 템플릿 확인 {#verify-customized-template}

사용자 정의된 템플릿이 올바르게 적용되었는지 확인하려면 다음을 수행합니다.

1. 적응형 양식에 대한 테스트 항목을 제출합니다.
1. 기록 문서를 생성합니다.
1. 생성된 PDF에 로고, 글꼴, 레이아웃 변경 및 기타 브랜딩 요소를 비롯한 사용자 지정 사항이 반영되었는지 확인합니다.

## 문제 해결 {#troubleshooting}

| 문제 | 해결 방법 |
|---|---|
| 사용자 지정된 템플릿이 업로드되지 않습니다. | XDP 파일이 유효하고 손상되지 않았는지 확인하십시오. AEM Forms에 파일을 업로드하는 데 필요한 권한이 있는지 확인합니다. |
| 생성된 기록 문서에는 사용자 정의가 표시되지 않습니다. | 양식 속성의 **[!UICONTROL 기록 문서 템플릿 구성]** 섹션에서 올바른 사용자 지정 템플릿을 선택했는지 확인하십시오. |
| 생성된 PDF의 레이아웃 또는 서식 문제. | Adobe Forms Designer의 사용자 지정이 [기본 템플릿 규칙](/help/forms/generate-document-of-record-core-components.md#base-template-conventions)을 따르는지 확인하십시오. 모든 요소가 템플릿 구조 내에 제대로 배치되었는지 확인합니다. |

## 추가 참조 {#see-also}

* [적응형 Forms(핵심 구성 요소)를 위한 기록 문서 생성](/help/forms/generate-document-of-record-core-components.md)
* [적응형 Forms(Foundation 구성 요소)에 대한 기록 문서 생성](/help/forms/generate-document-of-record-for-non-xfa-based-adaptive-forms.md)
* [기록 문서의 기본 템플릿](/help/forms/generate-document-of-record-core-components.md#base-template-of-a-document-of-record)
* [기록 문서의 브랜딩 정보 사용자 정의](/help/forms/generate-document-of-record-core-components.md#customize-the-branding-information-in-document-of-record)
