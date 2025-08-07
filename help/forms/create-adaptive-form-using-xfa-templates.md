---
title: XFA 양식 템플릿을 사용하여 핵심 구성 요소를 기반으로 하는 적응형 양식을 만드는 방법
description: ' [!DNL Experience Manager Forms] XFA 양식 템플릿 또는 XDP 파일을 사용하여 적응형 양식을 만드는 방법을 알아봅니다.'
feature: Adaptive Forms, Core Components
role: User, Developer
level: Beginner
exl-id: f3c9b798-8b20-4674-9b96-a3a0b143d947
source-git-commit: 2e2a0bdb7604168f0e3eb1672af4c2bc9b12d652
workflow-type: tm+mt
source-wordcount: '711'
ht-degree: 16%

---

# XFA Forms 템플릿 기반 적응형 양식(핵심 구성 요소) 만들기

<span class="preview"> 이 기능은 얼리어답터 프로그램에서 사용할 수 있습니다. 공식 이메일 ID를 사용하여 aem-forms-ea@adobe.com으로 이메일을 보내 얼리 어답터 프로그램에 참여하고 기능에 대한 액세스 권한을 요청할 수 있습니다. </span>

AEM as a Cloud Service에서는 XFA(XML Forms 아키텍처) 양식 템플릿 또는 `*.XDP`(XML 데이터 패키지) 파일을 사용하여 핵심 구성 요소를 기반으로 적응형 Forms을 만들 수 있는 옵션을 제공합니다. 이 기능을 사용하면 XFA 양식 템플릿 또는 XDP 파일 파일의 필드를 적응형 Forms으로 직접 마이그레이션하여 시간을 절약할 수 있습니다.

XFA 양식 템플릿 또는 XDP 파일 양식 템플릿의 용도를 다시 지정하여 핵심 구성 요소 기반의 적응형 Forms을 만들 수 있습니다. XFA 양식 템플릿 또는 XDP 파일을 다시 사용하려면 업로드하고 적응형 양식에 연결하십시오. XFA 양식 템플릿 또는 XDP 파일의 요소는 적응형 양식 작성 중 콘텐츠 파인더에서 사용할 수 있습니다. 콘텐츠 파인더에서 양식 템플릿 요소를 양식으로 드래그하여 놓을 수 있습니다.

## XFA 양식 템플릿 또는 XDP 파일을 기반으로 양식을 만들 수 있는 이점

XFA 양식 템플릿 또는 XDP 파일을 기반으로 양식을 만들 때 얻을 수 있는 이점 중 일부는 다음과 같습니다.

* **시간 절약**: 양식 구조를 다시 만들 필요 없이 기존 XFA 양식 템플릿(XDP 파일)을 빠르게 재사용할 수 있으므로 작성 프로세스 동안 시간과 노력을 절약할 수 있습니다.
* **간편한 마이그레이션**: 이미 사용 중인 XFA 양식 템플릿이 있는 경우 이 옵션을 사용하면 적응형 Forms으로 쉽게 마이그레이션할 수 있으므로 기존 양식 데이터 및 논리를 손실하지 않고 최신 AEM 핵심 구성 요소의 이점을 이용할 수 있습니다.
* **향상된 사용자 환경**: 적응형 Forms은 XFA 양식보다 더 반응적이고 사용자 정의가 가능합니다. 적응형 Forms으로 전환하면 다양한 디바이스와 화면 크기에서 보다 사용자 친화적인 경험을 할 수 있습니다.
* **향상된 통합**: 적응형 Forms은 워크플로우, 데이터 바인딩 및 양식 제출과 같은 다른 기능과 더 잘 통합되므로 더 원활한 워크플로우와 더 나은 전체 양식 관리를 가능하게 합니다.

## 사전 요구 사항

XFA 양식 템플릿 또는 XDP 파일을 사용하여 핵심 구성 요소를 기반으로 하는 적응형 양식을 만들려면 다음 항목이 필요합니다.

* [환경에 맞는 적응형 Forms 핵심 구성 요소를 사용하도록 설정](enable-adaptive-forms-core-components.md).
* 다음 영역에 익숙해지는 것이 좋습니다.
   * 적응형 양식 만들기
   * XFA(XML Forms 아키텍처)

## XFA 양식 템플릿 또는 XDP 파일을 사용하여 적응형 양식을 만드는 방법

XFA 또는 XDP 양식 템플릿을 사용하여 적응형 양식을 만들려면 다음 단계를 수행하십시오.

1. [!DNL Experience Manager Forms] 작성자 인스턴스에 로그인합니다.
1. Experience Manager 로그인 페이지에서 자격 증명을 입력합니다. 로그인한 후 왼쪽 상단에서 **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL 양식]** > **[!UICONTROL 양식 및 문서]**&#x200B;를 선택합니다.

   ![Forms 및 문서](/help/forms/assets/create-fdm.png)

1. **[!UICONTROL 만들기]** > **[!UICONTROL 적응형 Forms]**&#x200B;을(를) 선택합니다.

   ![적응형 양식 만들기](/help/forms/assets/create-af.png)

   양식 만들기 마법사가 열립니다.
1. **Source** 탭에서 핵심 구성 요소를 기반으로 템플릿을 선택합니다.

   ![템플릿 선택](/help/forms/assets/select-template.png)

   템플릿을 선택하면 템플릿에 지정된 테마 및 제출 액션이 자동으로 선택되고 **[!UICONTROL 만들기]** 단추가 활성화됩니다.

   ![테마 선택](/help/forms/assets/select-form-theme.png)

1. **[!UICONTROL 만들기]**&#x200B;를 선택합니다. 적응형 양식을 저장할 제목, 이름 및 위치를 지정하는 대화 상자가 나타납니다.
1. 제목, 이름 및 위치를 지정합니다.
1. **[!UICONTROL 만들기]**&#x200B;를 선택합니다.
   ![이름 및 제목 제공](/help/forms/assets/create-form.png)

   적응형 양식을 만들고 적응형 양식 편집기에서 엽니다. 템플릿에서 사용할 수 있는 콘텐츠가 편집기에 표시됩니다.
1. ![페이지 정보](/help/forms/assets/Smock_Properties_18_N.svg) > **[!UICONTROL 속성 열기]**&#x200B;를 선택합니다.

   ![속성 열기](/help/forms/assets/form-properties.png)

   양식 속성 페이지가 열립니다.
1. **[!UICONTROL 양식 모델]** 탭으로 이동하여 **양식 서식 파일**&#x200B;을 선택하세요.
1. 드롭다운 목록에서 .xdp 파일을 선택합니다.

   ![XDP 파일 선택](/help/forms/assets/select-xdp-file.png)

   화면에 경고 대화 상자가 나타납니다. 계속 진행하려면 **확인**&#x200B;을 클릭하세요.

   ![경고 대화 상자](/help/forms/assets/fdm-warning.png)

1. 속성을 저장하려면 **[!UICONTROL 저장 및 닫기]**&#x200B;를 선택하십시오.

   >[!NOTE]
   >
   > 양식 **모델** 탭에서 **양식 서식 파일**&#x200B;을(를) 선택한 후에는 변경할 수 없습니다.


적응형 양식을 만들고 적응형 양식 편집기에서 엽니다. 편집기에 템플릿에서 사용 가능한 콘텐츠가 표시됩니다.  적응형 양식 유형에 따라 연결된 XFA 양식 템플릿에 있는 양식 요소가 사이드바의 **[!UICONTROL 콘텐츠 브라우저]**&#x200B;에 있는 **[!UICONTROL 데이터 모델 개체]** 탭에 표시됩니다. 이러한 요소를 드래그 앤 드롭하여 적응형 양식을 작성할 수도 있습니다.

>[!NOTE]
>
> 추가된 필드의 패널 도구 모음을 사용하여 XDP 양식 필드에 대한 스크립트를 비활성화할 수 있습니다. [시각적 규칙 편집기](/help/forms/rule-editor-core-components.md)를 사용하여 추가된 필드에 대한 논리를 만듭니다.

