---
title: 제출 후 감사 페이지 또는 리디렉션 양식 구성
description: 양식 블록에 대한 감사 페이지와 리디렉션을 구성하여 사용자 경험을 최적화하고 사용자 여정을 간소화하는 방법에 대해 알아봅니다.
feature: Edge Delivery Services
hide: true
hidefromtoc: true
exl-id: e6c66b22-dc52-49e3-a920-059adb5be22f
source-git-commit: 4144f9704aaf17ea684be147395adc3aa31641f2
workflow-type: tm+mt
source-wordcount: '576'
ht-degree: 80%

---

# 제출 후 감사 페이지 또는 리디렉션 양식 표시

사용자가 양식을 제출한 후에는 감사 페이지 또는 리디렉션을 통해 원활한 경험을 제공하는 것이 중요합니다. 이러한 요소로 양식을 성공적으로 제출할 뿐만 아니라 사용자 만족도를 높이고 더 나은 여정을 안내합니다.

* **감사 페이지**: 감사 페이지는 브랜드 아이덴티티를 강화하는 동시에 안심을 주고 중요한 정보를 제공하는 사용자 경험의 기초입니다. 이는 작업 완성도와 사용자의 만족도를 높이면서 사용자의 작업을 직접적으로 승인합니다.

* **리디렉션**: 리디렉션은 사용자를 관련 대상으로 유도한 다음 사용자 참여도를 최적화하여 최종적으로 전환율을 높이는 데 핵심적인 역할을 합니다. 리디렉션은 사용자에게 고객 여정의 다음 단계를 원활하게 안내함으로써 원활한 탐색 경험을 제공할 수 있습니다. 예를 들어 초기 세부 정보가 수집되면 사용자는 결제 페이지로 리디렉션됩니다.

적응형 Forms 블록에서 기본 동작은 감사 페이지를 표시하는 것입니다. 단, 특정 요구 사항에 따라 이 환경을 유연하게 조정할 수 있습니다. 옵션은 다음과 같습니다.

* [브랜드 및 커뮤니케이션 목표에 부합하는 감사 페이지 및 메시지 구성](#configuring-the-thank-you-page-and-message)
* [추가 작업을 위해 양식 제출 후 사용자를 다른 페이지로 리디렉션](#redirect-users-to-another-page-post-submission)

## 감사 페이지 및 메시지 구성

적응형 Forms 블록의 기본 동작은 제출 시 &quot;감사합니다&quot; 페이지를 표시하는 것입니다. 다음 단계에 따라 적응형 Forms 블록에 대한 &quot;감사합니다&quot; 페이지를 구성하십시오.

1. Microsoft SharePoint 또는 Google Workspace에서 AEM Edge Delivery 프로젝트 폴더에 액세스합니다.
1. 프로젝트 디렉터리 내에서 “감사”라는 이름의 Microsoft Word 또는 Google Docs 파일을 만듭니다.
1. 감사 메시지를 “감사” 파일에 추가합니다. </br>

   ![샘플 감사 인사 페이지](/help/edge/assets/sample-thankyou-page.png)

1. AEM Sidekick을 사용하여 “감사 파일”을 미리 보고 게시합니다.

적응형 Forms 블록은 양식 제출 시 &quot;감사합니다&quot; 페이지를 표시합니다.

## 양식 제출 후 사용자를 다른 페이지로 리디렉션

기본적으로 적응형 Forms 블록은 사용자를 &quot;감사합니다&quot; 페이지로 리디렉션합니다. 사용자를 기본 “감사” 페이지가 아닌 다른 페이지로 리디렉션하려면 다음 두 가지 옵션을 사용할 수 있습니다.

* [“감사” 페이지를 다른 페이지로 바꾸기](#replace-the-existing-thankyou-page)
* [“감사” 페이지 리디렉션에 웹 사이트 리디렉션 사용](#use-website-redirects-for-thankyou-page-redirection)

### “감사” 페이지 바꾸기

1. “[EDS Project]/blocks/form/form.js” 파일을 열어 편집합니다.
1. 다음 줄의 `thankyou` 페이지를 원하는 페이지로 변경합니다.

   ```JavaScript
   window.location.href = form.dataset?.redirect || 'thankyou';
   ```

   예:

   ```JavaScript
   window.location.href = form.dataset?.redirect || 'payment';
   ```

   >[!NOTE]
   >
   > Microsoft SharePoint 또는 Google Workspace의 Edge Delivery Services 프로젝트 폴더에 이름이 동일한 페이지가 있는지 확인합니다. 페이지가 없으면 계속해서 페이지를 만들고 게시합니다.

1. 업데이트된 &#39;form.js&#39; 폴더 및 그 기본 파일을 GitHub의 Edge Delivery Services 프로젝트에 체크 인합니다. 이 업데이트를 통해 이제 양식이 지정된 대로 업데이트된 페이지로 리디렉션됩니다.

1. 페이지가 EDS 프로젝트 폴더에 있는지 확인하고 게시합니다.


### “감사” 페이지 리디렉션에 웹 사이트 리디렉션 사용

양식 제출 후 사용자를 다른 페이지로 리디렉션하면 관련 정보를 제공하고, 작업을 확인하고, 사용자가 원하는 결과를 얻도록 유도함으로써 사용자 경험을 향상시킬 수 있습니다. 예:

* 사용자가 구매 양식을 작성하면 사용자는 결제 페이지로 리디렉션되어 거래를 안전하게 완료할 수 있습니다.
* 이벤트나 웨비나용 등록 양식 제출 시 사용자는 날짜, 시간, 위치 등 이벤트 세부 정보를 표시하는 확인 페이지로 리디렉션됩니다.

“감사” 페이지를 다른 페이지로 리디렉션하려면 [웹 사이트 리디렉션](https://www.aem.live/docs/redirects) 스프레드시트를 사용할 수 있습니다.


## 참고 항목

{{see-more-forms-eds}}