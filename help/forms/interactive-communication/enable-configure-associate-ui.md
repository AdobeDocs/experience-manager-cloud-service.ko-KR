---
title: 대화형 커뮤니케이션용 연결 UI 활성화 및 구성
description: 연결된 사용자가 연결 UI를 사용할 수 있도록 대화형 통신 설정에서 업데이트에 대한 보기 연결 및 워크플로 구성을 활성화하는 방법에 대해 알아봅니다.
products: SG_EXPERIENCEMANAGER/Cloud Service/FORMS
feature: Interactive Communication
role: User, Developer, Admin
exl-id: 7c3e8a2b-5f21-4a1e-9e2d-8a4b6c7d8e9f
source-git-commit: a41459520feb03594212b91e68cfd8e2b1e610c4
workflow-type: tm+mt
source-wordcount: '764'
ht-degree: 1%

---

# 대화형 커뮤니케이션용 연결 UI 활성화 및 구성

>[!NOTE]
>
> 대화형 통신 기능은 얼리어답터 프로그램에서 사용할 수 있습니다. 액세스 권한을 요청하려면 회사 이메일 주소를 통해 `aem-forms-ea@adobe.com`으로 이메일을 보내시기 바랍니다.

이 문서에서는 대화형 통신(IC)에 대한 연결 UI를 활성화하고 필요한 경우 제출을 위해 AEM 워크플로를 구성하는 방법에 대해 설명합니다. 작성자는 **대화형 통신 설정**&#x200B;에서 다음 단계를 수행합니다.

UI 및 사용자 역할 연결에 대한 개요는 [대화형 통신 편집기에서 UI 연결](/help/forms/interactive-communication/associate-ui-in-interactive-communication-editor.md)을 참조하십시오.

## 사전 요구 사항

Associate UI를 활성화하고 구성하기 전에 다음을 확인하십시오.

- 대화형 통신 편집기에 대한 **작성자 액세스**.
- 필요한 레이아웃 및 데이터 바인딩을 사용하여 만든 **대화형 통신**.
- **사용자 연결**&#x200B;이(가) **forms-associates** 그룹에 추가되었습니다(동료가 연결 UI에 액세스하는 데 필요).
- **작성자**&#x200B;이(가) **forms-associates** 그룹에 추가되었습니다(작성자가 UI 연결에 액세스하는 데 필요).

연결 UI를 애플리케이션과 통합하고 게시 인스턴스에서 호출할 준비가 되면 팝업 지원이 활성화되고 IC가 게시된 브라우저도 필요합니다. 전체 통합 필수 조건은 [응용 프로그램에서 연결 UI 통합](/help/forms/interactive-communication/invoke-associate-ui.md)을 참조하십시오.

## 보기 연결 활성화(UI 연결)

동료가 대화형 커뮤니케이션을 사용할 수 있도록 문서 수준에서 연결 UI를 활성화합니다.

1. 편집기에서 대화형 통신을 엽니다.
1. 상단 작업 모음 또는 문서 옵션에서 **대화형 통신 설정**(또는 **설정**)을 엽니다.

   ![대화형 통신 설정 - 보기 편집 연결을 사용하여 속성 연결](/help/forms/assets/associate-ui-settings.png)

1. 왼쪽 패널에서 **속성 연결**&#x200B;이 선택되어 있는지 확인합니다.
1. 오른쪽에서 **보기 편집 연결 사용**&#x200B;을 확인하세요.
1. **변경 내용 적용**&#x200B;을 클릭한 다음 문서를 저장합니다.

   ![대화형 통신 설정 - 보기 편집 연결을 사용하여 속성 연결](/help/forms/assets/associate-ui-enable-view.png)

보기 연결을 활성화하려면 변경 사항을 적용하고 문서를 저장하라는 메시지가 표시될 수 있습니다. 저장한 후 IC를 연결-방식(associate-driven)으로 사용할 수 있습니다.

### 구성 요소별 연결 UI 편집 허용

IC에 대해 [연결 보기]를 사용하도록 설정한 후에는 연결할 수 있는 각 구성 요소에 대해 **연결을 통한 편집 허용**&#x200B;을 켜야 합니다. 이 설정이 켜지지 않은 구성 요소는 연결 UI에서 읽기 전용으로 유지됩니다.

1. IC 편집기의 캔버스 또는 구성 요소 계층 구조에서 구성 요소(예: 텍스트 필드)를 선택합니다.
1. 오른쪽 **속성** 패널에서 **속성 연결**&#x200B;을 확장합니다.
1. 해당 구성 요소에 대해 **동료의 편집 허용** **켜기**&#x200B;을(를) 켭니다.
1. 연결하는 모든 구성 요소에 대해 이 작업을 반복하여 편집한 다음 문서를 저장합니다.

![구성 요소 속성에서 연결을 통한 편집 허용](/help/forms/assets/associate-ui-allow-editing-by-associate.png)

>[!NOTE]
>
> **속성 연결**&#x200B;에는 **타이포그래피**(연결 UI의 필드에 대한 글꼴, 크기 및 스타일 지정), **도구 설명** 및 **패턴**(유효성 검사)과 같은 옵션도 포함됩니다. 이러한 매개 변수를 사용하여 연결 프로그램에서 편집할 때 구성 요소의 모양과 동작을 제어합니다. 예를 들어 연결 프로그램에서 데이터를 필수 형식으로 입력할 수 있도록 유효성 검사 패턴을 설정합니다.

## 연결 UI에 대한 워크플로 구성

사용자가 연결 UI에서 데이터를 제출하거나 업데이트할 때 AEM 워크플로우를 실행하려면 다음을 구성합니다.

1. **대화형 통신 설정**&#x200B;의 왼쪽 패널([속성 연결] 아래)에서 **워크플로**&#x200B;를 선택합니다.
1. **업데이트할 워크플로를 구성** **설정**&#x200B;합니다.
1. **워크플로 모델 선택**&#x200B;에서 실행할 AEM 워크플로 모델(예: `conversionWorkflow` 또는 `/var/workflow/models/submit-workflow-1` 등 경로)을 선택합니다.
1. 선택적으로 **워크플로 성공 메시지**&#x200B;를 설정합니다(워크플로가 완료된 후 사용자에게 표시됨).
1. 필요한 경우 **리디렉션 URL**&#x200B;을 설정하여 제출 후 사용자를 특정 페이지로 보냅니다.
1. **변경 내용 적용**&#x200B;을 클릭하고 문서를 저장합니다.

   ![대화형 통신 설정 - 연결 UI에 대한 워크플로 구성](/help/forms/assets/associate-ui-configure-workflow.png)

워크플로우를 활성화하면 사용자가 연결 UI에서 제출할 때마다 실행됩니다. 제출 및 워크플로 작동 방식(실행 위치, 사용 인스턴스 및 주요 고려 사항)은 [연결 UI를 위한 제출 워크플로](/help/forms/interactive-communication/submission-workflow-associate-ui-ic-pdf.md#submission-and-workflow-behavior)를 참조하십시오. 이 문서에는 IC 제출에서 PDF을 생성하는 워크플로우의 예도 포함되어 있습니다.

## UI 연결 설정 완료

뷰 연결을 활성화하고 필요한 경우 워크플로우를 구성한 후:

1. **편집 가능한 필드 사용:** IC의 필수 섹션에서 연결할 수 있는 필드를 사용하도록 설정합니다. 필요에 따라 유효성 검사 및 필수/읽기 전용 동작을 설정합니다.
1. **IC를 게시**&#x200B;하여 동료의 게시 인스턴스에서 사용할 수 있도록 합니다.
1. 게시된 IC 링크를 동료와 공유합니다. 인증하고(예: [Microsoft Entra ID](https://www.microsoft.com/en-us/security/business/identity-access/microsoft-entra-id)를 통해) 연결 UI를 열고, 고객 데이터를 입력하거나 확인하고, 최종 통신을 생성합니다. 워크플로우를 구성한 경우 제출 시 실행됩니다. 제출 및 워크플로 작동 방식은 [연결 UI에 대한 제출 워크플로](/help/forms/interactive-communication/submission-workflow-associate-ui-ic-pdf.md#submission-and-workflow-behavior)를 참조하십시오.

## 추가 참조

- [대화형 통신 편집기에서 UI 연결](/help/forms/interactive-communication/associate-ui-in-interactive-communication-editor.md)
- [애플리케이션에 UI 연결 통합](/help/forms/interactive-communication/invoke-associate-ui.md)
- [UI 연결을 위한 제출 워크플로 — IC PDF 출력 생성](/help/forms/interactive-communication/submission-workflow-associate-ui-ic-pdf.md) — 제출 및 워크플로 작동 방식, IC 제출에서 PDF을 생성하는 예제 워크플로.
