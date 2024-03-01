---
title: EDS 양식의 감사 인사 페이지 구성
description: 사용자 경험을 최적화하고 사용자 여정을 간소화하기 위해 EDS Forms에 대한 감사 페이지 및 리디렉션을 구성하는 방법에 대해 알아봅니다.
feature: Edge Delivery Services
hide: true
hidefromtoc: true
source-git-commit: e2970c7a141025222c6b119787142e7c39d453af
workflow-type: tm+mt
source-wordcount: '356'
ht-degree: 2%

---


# 적응형 Forms 블록에서 감사 페이지 및 리디렉션 구성

감사 페이지 및 리디렉션은 사용자에게 양식 제출 후 확인, 명확한 커뮤니케이션 및 원활한 탐색을 제공하는 사용자 경험 향상에 중요한 측면입니다.

## 감사 인사 페이지 구성

감사 페이지는 사용자에게 안심시키는 역할을 하며 조직이 브랜드 정체성을 강화하는 동시에 필수 정보를 전달할 수 있도록 합니다. EDS Forms에 대한 감사 페이지를 구성하려면 다음 단계를 따르십시오.

1. Microsoft SharePoint 또는 Google Workspace에서 AEM Edge 게재 프로젝트 폴더에 액세스합니다.
1. 프로젝트 디렉터리 내에 &quot;감사합니다&quot;라는 Microsoft Word 또는 Google 문서 파일을 만듭니다.
1. 감사 메시지를 &quot;감사합니다&quot; 파일에 추가합니다.
   ![감사 인사 페이지 예](/help/edge/assets/sample-thankyou-page.png)
1. AEM Sidekick을 활용하여 &quot;감사합니다&quot; 파일을 미리 보고 게시합니다.

## 제출 후 사용자 리디렉션

리디렉션을 사용하면 관련 대상으로 사용자를 안내하고, 참여를 최적화하고, 전환율을 높여 원활한 사용자 여정을 수행할 수 있습니다.

기본적으로 적응형 Forms 블록은 사용자를 &quot;감사합니다&quot; 페이지로 리디렉션합니다. 사용자를 기본 &quot;감사합니다&quot; 페이지가 아닌 다른 페이지로 리디렉션하려면 다음 두 가지 옵션이 있습니다.

* 기존의 &quot;감사합니다&quot; 페이지를 다른 페이지로 바꾸거나
* &quot;감사합니다&quot; 페이지를 선택한 다른 페이지로 리디렉션합니다.

### 기존 &quot;감사합니다&quot; 페이지 바꾸기

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
   > Microsoft SharePoint 또는 Google Workspace의 Edge Delivery Service 프로젝트 폴더에 이름이 동일한 페이지가 있는지 확인합니다. 페이지가 존재하지 않는 경우 계속해서 페이지를 만들고 게시합니다.

1. 업데이트된 &#39;form.js&#39; 폴더 및 그 기본 파일을 GitHub의 Edge Delivery Service 프로젝트에 체크 인합니다. 이 업데이트를 통해 양식이 지정된 업데이트된 페이지로 리디렉션됩니다.

1. 페이지가 EDS 프로젝트 폴더에 있는지 확인하고 게시합니다.


### 웹 사이트 리디렉션 사용

웹 사이트 리디렉션을 구성하여 &quot;감사합니다&quot; 페이지를 다른 페이지로 보냅니다. 다음을 참조하십시오. [리디렉션 설명서](https://www.aem.live/docs/redirects) 자세한 지침은 을 참조하십시오.


