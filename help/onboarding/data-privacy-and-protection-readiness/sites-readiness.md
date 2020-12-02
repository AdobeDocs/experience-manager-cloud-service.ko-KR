---
title: 데이터 보호 및 데이터 개인 정보 보호 규정 - Cloud Service 사이트 준비 규정
description: '다양한 데이터 보호 및 데이터 개인 정보 보호 규정에 대한 Cloud Service 사이트 지원으로서 Adobe Experience Manager에 대해 알아보십시오.여기에는 EU 개인 정보 보호 규정(GDPR), 캘리포니아 개인 정보 보호 법(California Consumer Privacy Act) 및 새로운 AEM을 Cloud Service 프로젝트로 구현할 때 준수하는 방법이 포함됩니다. '
translation-type: tm+mt
source-git-commit: 7b5a427853075054d56bc7ea6569d5d839e282a1
workflow-type: tm+mt
source-wordcount: '1036'
ht-degree: 48%

---


# Adobe Experience Manager, 데이터 보호 및 데이터 개인 정보 보호 규정에 대한 Cloud Service 사이트 준비{#aem-sites-readiness-for-data-protection-and-data-privacy-regulations}

>[!WARNING]
>
>이 문서의 내용은 법률적 조언을 의미하지 않으며 법적 조언을 대체하기 위한 것이 아니다.
>
>데이터 보호 및 데이터 개인 정보 보호 규정에 대한 조언을 얻으려면 회사의 법무팀에 문의하십시오.

>[!NOTE]
>
>개인정보 보호 문제에 대한 Adobe의 응답과 Adobe 고객으로서 귀하에게 어떤 의미를 갖는지에 대한 자세한 내용은 [Adobe 개인 정보 보호 센터](https://www.adobe.com/privacy.html)를 참조하십시오.

Adobe Experience Manager Cloud Service 사이트는 고객의 데이터 개인 정보 보호 및 보호 규정 준수 의무를 지원할 준비가 되어 있습니다. 이 페이지에서는 고객이 AEM Sites에서 이러한 요청을 처리할 수 있는 절차를 안내합니다. 저장된 개인 데이터의 위치와 수동으로 또는 코드로 해당 데이터를 제거하는 방법에 대해서도 설명합니다.

자세한 내용은 [Adobe 개인 정보 보호 센터](https://www.adobe.com/privacy.html)를 참조하십시오.

>[!NOTE]
>
>자세한 내용은 [Adobe Experience Manager을 데이터 보호를 위한 Cloud Service 준비 및 데이터 개인 정보 보호 규정](/help/onboarding/data-privacy-and-protection-readiness/aem-readiness.md)으로 참조하십시오.

## AEM 작성 계층 {#aem-author-tier}

작성자 서버의 사용자 계정 및 UGC 컨텐츠는 [AEM Foundation documentation](/help/onboarding/data-privacy-and-protection-readiness/aem-readiness.md)에서 다룹니다.

## AEM 게시 계층 {#aem-publish-tier}

사이트에서 방문자를 인증하는 데 사용되는 사용자 계정과 게시 서버의 UGC 컨텐츠는 [AEM Foundation documentation](/help/onboarding/data-privacy-and-protection-readiness/aem-readiness.md)에서 다룹니다.

기본적으로 AEM Sites 구성 요소는 게시 서버에서 방문자가 입력한 양식 데이터를 저장하지 않습니다. 추가적인 처리가 필요하면 데이터를 타사 시스템 또는 Adobe Campaign에 전달하는 것이 좋습니다.

## 옵트인/옵트아웃 {#opt-in-opt-out}

<!--
AEM has a [cookie opt-out service](/help/sites-developing/cookie-optout.md ) that can be used for managing the opt-in/opt-out for users.
-->

Adobe Experience Manager은 사용자에 대한 옵트인/옵트아웃을 관리하는 데 사용되는 쿠키 옵트아웃 서비스의 적용을 받습니다.

옵트아웃하려면:

1. 다음으로 이동:
   [Adobe 개인 정보 보호 센터 - 옵트아웃](https://www.adobe.com/privacy/opt-out.html)

1. **서비스** - **Experience Cloud 서비스 사용 데이터**&#x200B;로 스크롤합니다.

1. 참조된 링크를 선택합니다.현재 제목이 **여기**&#x200B;입니다.

1. 옵트아웃 또는 옵트아웃할 수 있는 옵션과 함께 다음과 같은 세부 사항이 표시됩니다.

   * 이 사이트 방문에 대한 데이터 집계 및 분석을 옵트아웃하려면 브라우저에 쿠키를 설치해야 합니다. 이 쿠키는 사용자가 옵트아웃했음을 나타냅니다.

      옵트아웃 쿠키를 삭제하거나 컴퓨터 또는 웹 브라우저를 변경하는 경우 다시 옵트아웃해야 합니다.

      옵트아웃 - 방문자 세션 집계 및 분석에서 나를 제외합니다(`amcglobal.sc.omtrdc.net` 옵트아웃 쿠키 설치) - 여기를 클릭하십시오.

      옵트인 - 방문자 세션 집계 및 분석에 나를 포함합니다(`amcglobal.sc.omtrdc.net` 옵트아웃 쿠키 설치 안 함) - 여기를 클릭하십시오.
   위 단계에 따라 실제 링크에 액세스합니다.

   >[!NOTE]
   >
   > **2에 대한 추가 설명이 있습니다. 개인 정보.** 섹션 [ ](https://www.adobe.com/legal/terms.html).

## Analytics Foundation {#analytics-foundation}

AEM Sites에는 Adobe Analytics 온디맨드 서비스 내에서 기능을 사용하는 Analytics Foundation과의 선택 사항 통합이 포함되어 있습니다.

Adobe Analytics과 관련된 데이터 주체 요청 관리에 대한 자세한 내용은 [Adobe Analytics 및 데이터 개인 정보](https://docs.adobe.com/content/help/en/analytics/admin/data-governance/gdpr-view-settings.html)를 참조하십시오.

## 개인화 기반 Target {#personalization-foundation-by-target}

AEM Sites에는 Adobe Target 온디맨드 서비스 내에서 기능을 사용하는 Target의 개인화 기반과의 선택적인 통합이 포함되어 있습니다.

Adobe Target과 관련된 데이터 주체 요청 관리에 대한 자세한 내용은 [Adobe Target - 개인 정보 보호 및 일반 데이터 보호 규정](https://docs.adobe.com/content/help/ko-KR/target/using/implement-target/before-implement/privacy/cmp-privacy-and-general-data-protection-regulation.html)을 참조하십시오.

## ContextHub {#contexthub}

<!--
AEM provides an optional data layer with [ContextHub](/help/sites-developing/contexthub.md).
-->

AEM에서는 ContextHub와 관련하여 선택적 데이터 계층을 제공합니다. 이렇게 하면 규칙 기반 개인화에 사용할 방문자별 데이터가 브라우저에 유지됩니다.

기본적으로 이 방문자 데이터는 AEM에 저장되지 않습니다. AEM은 브라우저에서 규칙을 데이터 계층에 보내 개인화를 결정합니다.

### 옵트인/옵트아웃 구현 {#implementing-opt-in-opt-out}

사이트 소유자는 다음 지침에 따라 옵트아웃 구성 요소를 구현해야 합니다.

이 지침은 기본적으로 옵트인을 구현합니다. 따라서 웹 사이트 방문자는 개인 데이터가 브라우저의 (클라이언트측) 지속성 내에 저장되기 전에 분명히 동의해야 합니다.

* 옵트아웃 구성 요소는 ContextHub 구성 요소가 포함될 때마다 포함되어야 합니다.
* 웹 사이트에 대한 데이터 보호 및 개인 정보와 관련된 사용 약관은 웹 사이트 방문자에게 표시되어야 하며 이를 통해 다음과 같은 작업을 수행할 수 있습니다.

   * 동의
   * 거부
   * 이전 선택 사항 변경

* 사이트 방문자가 사이트의 약관에 동의하면 ContextHub 옵트아웃 쿠키가 제거됩니다.

   ```
   ContextHub.Utils.Cookie.removeItem('cq-opt-out');
   ```

* 사이트 방문자가 사이트의 약관에 동의하지 않으면 ContextHub 옵트아웃 쿠키가 설정됩니다.

   ```
   ContextHub.Utils.Cookie.setItem('cq-opt-out', 1);
   ```

* ContextHub가 옵트아웃 모드에서 실행되고 있는지 확인하려면 브라우저의 콘솔에서 다음 호출을 수행해야 합니다.

   ```
   var isOptedOut = ContextHub.isOptedOut(true) === true;
   // if isOptedOut is true, ContextHub is running in opt-out mode
   ```

### ContextHub의 지속성 미리 보기 {#previewing-persistence-of-contexthub}

ContextHub에서 사용한 지속성을 미리 보려면 다음 작업을 수행할 수 있습니다.

* 브라우저의 콘솔 사용. 예를 들어

   * Chrome:

      * Developer Tools > Application > Storage를 엽니다.

         * Local Storage > (웹 사이트) > ContextHubPersistence
         * Session Storage > (웹 사이트) > ContextHubPersistence
         * Cookies > (웹 사이트) > SessionPersistence
   * Firefox:

      * Developer Tools > Storage를 엽니다.

         * Local Storage > (웹 사이트) > ContextHubPersistence
         * Session Storage > (웹 사이트) > ContextHubPersistence
         * Cookies > (웹 사이트) > SessionPersistence
   * Safari:

      * 메뉴 막대에서 Preferences > Advanced > Show Develop 메뉴를 엽니다.
      * Develop > Show JavaScript Console을 엽니다.

         * Console > Storage > Local Storage > (웹 사이트) > ContextHubPersistence
         * Console > Storage > Session Storage > (웹 사이트) > ContextHubPersistence
         * Console > Storage > Cookies > (웹 사이트) > ContextHubPersistence
   * Internet Explorer:

      * 개발자 도구 > 콘솔을 엽니다.

         * `localStorage.getItem('ContextHubPersistence')`
         * `sessionStorage.getItem('ContextHubPersistence')`
         * `document.cookie`




* 브라우저 콘솔에서 ContextHub API 사용.

   * ContextHub에서는 다음 데이터 지속성 계층을 제공합니다.

      * `ContextHub.Utils.Persistence.Modes.LOCAL` (기본값)
      * `ContextHub.Utils.Persistence.Modes.SESSION`
      * `ContextHub.Utils.Persistence.Modes.COOKIE`
      * `ContextHub.Utils.Persistence.Modes.WINDOW`

      ContextHub 저장소는 사용할 지속성 계층을 정의하므로 현재 지속성 상태를 보려면 모든 계층을 검사해야 합니다.


예를 들어 localStorage에 저장된 데이터를 보려는 경우

ContextHub에서 사용한 지속성을 미리 보려면 다음 작업을 수행할 수 있습니다.

* 브라우저의 콘솔 사용:

   * Chrome - Developer Tools > Application > Storage 열기:

      * Local Storage > (웹 사이트) > ContextHubPersistence
      * Session Storage > (웹 사이트) > ContextHubPersistence
      * Cookies > (웹 사이트) > SessionPersistence
   * Firefox - Developer Tools > Storage 열기:

      * Local Storage > (웹 사이트) > ContextHubPersistence
      * Session Storage > (웹 사이트) > ContextHubPersistence
      * Cookies > (웹 사이트) > SessionPersistence


* 브라우저 콘솔에서 ContextHub API 사용.

   * ContextHub에서는 다음 데이터 지속성 계층을 제공합니다.

      * `ContextHub.Utils.Persistence.Modes.LOCAL` (기본값)
      * `ContextHub.Utils.Persistence.Modes.SESSION`
      * `ContextHub.Utils.Persistence.Modes.COOKIE`
      * `ContextHub.Utils.Persistence.Modes.WINDOW`

      ContextHub 저장소는 사용할 지속성 계층을 정의하므로 현재 지속성 상태를 보려면 모든 계층을 검사해야 합니다.


예를 들어 localStorage에 저장된 데이터를 보려는 경우

```
var storage = new ContextHub.Utils.Persistence({ mode: ContextHub.Utils.Persistence.Modes.LOCAL });
console.log(storage.getTree());
```

### ContextHub의 지속성 지우기 {#clearing-persistence-of-contexthub}

ContextHub 지속성 지우기:

* 현재 로드된 저장소의 지속성을 지우려면

   ```
   // in order to be able to fully access persistence layer, Opt-Out must be turned off
   ContextHub.Utils.Cookie.removeItem('cq-opt-out');
   
   // following call asks all currently loaded stores to clear their data
   ContextHub.cleanAllStores();
   
   // following call asks all currently loaded stores to set back default values (provided in their configs)
   ContextHub.resetAllStores();
   ```

* 특정 지속성 계층을 지우려면(예: sessionStorage):

   ```
   var storage = new ContextHub.Utils.Persistence({ mode: ContextHub.Utils.Persistence.Modes.SESSION });
   storage.setItem('/store', null);
   storage.setItem('/_', null);
   
   // to confirm that nothing is stored:
   console.log(storage.getTree());
   ```

* 모든 ContextHub 지속성 계층을 지우려면 모든 레이어에 대해 적절한 코드를 호출해야 합니다.

   * `ContextHub.Utils.Persistence.Modes.LOCAL` (기본값)
   * `ContextHub.Utils.Persistence.Modes.SESSION`
   * `ContextHub.Utils.Persistence.Modes.COOKIE`
   * `ContextHub.Utils.Persistence.Modes.WINDOW`
