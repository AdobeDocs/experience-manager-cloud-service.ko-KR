---
title: 제출 후 감사 페이지 또는 리디렉션 양식 구성
description: 사용자 경험을 최적화하고 사용자 여정을 간소화하기 위해 감사 페이지 및 Forms 블록의 리디렉션을 구성하는 방법에 대해 알아봅니다.
feature: Edge Delivery Services
hide: true
hidefromtoc: true
exl-id: e6c66b22-dc52-49e3-a920-059adb5be22f
source-git-commit: 53a66eac5ca49183221a1d61b825401d4645859e
workflow-type: tm+mt
source-wordcount: '608'
ht-degree: 6%

---

# 제출 후 감사 페이지 또는 리디렉션 양식 표시

사용자가 양식을 제출한 후 감사 페이지나 리디렉션을 통해 원활한 경험을 제공하는 것이 중요합니다. 이러한 요소는 성공적인 제출을 확인할 뿐만 아니라 사용자 만족도를 높이고 여정에서 이를 더욱 안내합니다.

* **감사 인사 페이지**: 감사 페이지는 사용자 경험의 초석으로, 브랜드 정체성을 강화하면서 안심을 제공하고 중요한 정보를 전달합니다. 사용자의 행동을 직접 인정하는 역할을 하여 완결성과 만족감을 키운다.

* **리디렉션**: 리디렉션은 사용자를 관련 대상으로 안내하고, 참여를 최적화하고, 궁극적으로 전환율을 높이는 데 중추적 역할을 합니다. 리디렉션을 통해 여정의 다음 단계로 원활하게 안내함으로써 원활한 탐색 경험을 보장합니다. 예를 들어 초기 세부 정보를 수집한 후 사용자를 결제 페이지로 리디렉션합니다.

적응형 Forms 블록에서 기본 동작은 감사 페이지를 표시하는 것입니다. 그러나 특정 요구 사항에 맞게 이 환경을 조정할 수 있는 유연성을 가지게 됩니다. 옵션은 다음과 같습니다.

* [브랜드 및 커뮤니케이션 목표에 맞게 감사 페이지 및 메시지 구성](#configuring-the-thank-you-page-and-message)
* [추가 작업을 위해 사용자를 다른 페이지 사후 제출로 리디렉션합니다.](#redirect-users-to-another-page-post-submission)

## 감사 페이지 및 메시지 구성

적응형 Forms 블록의 기본 동작은 제출 시 &quot;감사합니다&quot; 페이지를 표시하는 것입니다. 다음 단계에 따라 적응형 Forms 블록에 대한 &quot;감사합니다&quot; 페이지를 구성하십시오.

1. Microsoft SharePoint 또는 Google Workspace에서 AEM Edge 게재 프로젝트 폴더에 액세스합니다.
1. 프로젝트 디렉터리 내에 &quot;감사합니다&quot;라는 Microsoft Word 또는 Google 문서 파일을 만듭니다.
1. 감사 메시지를 &quot;감사합니다&quot; 파일에 추가합니다. </br>

   ![감사 인사 페이지 예](/help/edge/assets/sample-thankyou-page.png)

1. AEM Sidekick을 사용하여 &quot;감사합니다&quot; 파일을 미리 보고 게시합니다.

적응형 Forms 블록은 양식 제출 시 &quot;감사합니다&quot; 페이지를 표시합니다.

## 사용자를 다른 페이지 사후 제출로 리디렉션

기본적으로 적응형 Forms 블록은 사용자를 &quot;감사합니다&quot; 페이지로 리디렉션합니다. 사용자를 기본 &quot;감사합니다&quot; 페이지가 아닌 다른 페이지로 리디렉션하려면 다음 두 가지 옵션이 있습니다.

* [&quot;감사합니다&quot; 페이지를 다른 페이지로 바꿉니다.](#replace-the-existing-thankyou-page)
* [&quot;감사합니다&quot; 페이지 리디렉션에 웹 사이트 리디렉션 사용](#use-website-redirects-for-thankyou-page-redirection)

### &quot;감사합니다&quot; 페이지 바꾸기

1. 를 엽니다.[EDS 프로젝트]편집할 /blocks/form/form.js&quot; 파일입니다.
1. 변경 `thankyou` 다음 행에서 선택한 페이지로 이동합니다.

   ```JavaScript
   window.location.href = form.dataset?.redirect || 'thankyou';
   ```

   예:

   ```JavaScript
   window.location.href = form.dataset?.redirect || 'payment';
   ```

   >[!NOTE]
   >
   > Microsoft SharePoint 또는 Google Workspace의 Edge Delivery Services 프로젝트 폴더에 이름이 동일한 페이지가 있는지 확인합니다. 페이지가 존재하지 않는 경우 계속해서 페이지를 만들고 게시합니다.

1. 업데이트된 &#39;form.js&#39; 폴더 및 그 기본 파일을 GitHub의 Edge Delivery Services 프로젝트에 체크 인합니다. 이 업데이트를 통해 양식이 지정된 업데이트된 페이지로 리디렉션됩니다.

1. 페이지가 EDS 프로젝트 폴더에 있는지 확인하고 게시합니다.


### &quot;감사합니다&quot; 페이지 리디렉션에 웹 사이트 리디렉션 사용

양식 제출 후 사용자를 다른 페이지로 리디렉션하면 관련 정보를 제공하고, 작업을 확인하고, 사용자에게 원하는 결과를 안내하여 사용자 경험을 향상시킬 수 있습니다. 예:

* 사용자가 구매 양식을 완료한 후 결제 페이지로 리디렉션되어 안전하게 트랜잭션을 완료할 수 있습니다.
* 이벤트 또는 웨비나에 대한 등록 양식을 제출하면 사용자는 날짜, 시간 및 위치와 같은 이벤트 세부 사항을 표시하는 확인 페이지로 리디렉션됩니다.

&quot;감사합니다&quot; 페이지를 다른 페이지로 리디렉션하려면 [웹 사이트 리디렉션](https://www.aem.live/docs/redirects) 스프레드시트입니다.


## 더 보기

* [양식 구성 요소](/help/edge/docs/forms/form-components.md)
* [양식 필드 속성](/help/edge/docs/forms/eds-form-field-properties)
* [양식 만들기 및 미리 보기](/help/edge/docs/forms/create-forms.md)
* [양식을 활성화하여 데이터 전송](/help/edge/docs/forms/submit-forms.md)
* [사이트 페이지에 양식 게시](/help/edge/docs/forms/publish-forms.md)
* [양식 필드에 유효성 검사 추가](/help/edge/docs/forms/validate-forms.md)
* [양식의 테마 및 스타일 변경](/help/edge/docs/forms/style-theme-forms.md)
