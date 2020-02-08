---
title: 데이터 보호 및 데이터 개인 정보 보호 규정 - 클라우드 서비스 사이트로서의 Adobe Experience Manager 준비
description: '다양한 데이터 보호 및 데이터 개인 정보 보호 규정에 대한 클라우드 서비스 사이트 지원으로서 Adobe Experience Manager에 대해 알아봅니다.여기에는 EU GDPR(General Data Protection Regulation), California Consumer Privacy Act 및 새로운 AEM을 클라우드 서비스 프로젝트로 구현할 때 준수하는 방법이 포함됩니다. '
translation-type: tm+mt
source-git-commit: 1130e8a07bc3826380483a7560ebda7e8a17e238

---


# Adobe Experience Manager를 클라우드 서비스 사이트로서 데이터 보호 및 데이터 개인 정보 보호 규정 준비 {#aem-sites-readiness-for-data-protection-and-data-privacy-regulations}

>[!WARNING]
>
>이 문서의 내용은 법률적 조언을 구성하지 않으며 법적 자문을 대체하기 위한 것이 아닙니다.
>
>데이터 보호 및 데이터 개인 정보 보호 규정에 대한 자세한 내용은 회사의 법무팀에 문의하십시오.

>[!NOTE]
>
>개인정보 보호 문제에 대한 Adobe의 응답 및 Adobe 고객으로서 귀하에게 의미하는 사항에 대한 자세한 내용은 Adobe [의 개인정보 보호 센터를 참조하십시오](https://www.adobe.com/privacy.html).

Adobe Experience Manager as a Cloud Service Sites는 고객의 데이터 개인 정보 보호 및 보호 규정 준수 의무를 지원할 준비가 되었습니다. 이 페이지는 고객에게 AEM Sites에서 이러한 요청을 처리하는 절차를 안내합니다. 저장된 개인 데이터의 위치 및 수동으로 또는 코드를 사용하여 데이터를 제거하는 방법에 대해 설명합니다.

자세한 내용은 Adobe 개인정보 [보호 센터를 참조하십시오](https://www.adobe.com/privacy.html).

>[!NOTE]
>
>자세한 [내용은 Adobe Experience Manager를 데이터 보호 및 데이터 개인 정보 보호 규정에](/help/onboarding/data-privacy-and-protection-readiness/aem-readiness.md) 대한 클라우드 서비스 준비로 참조하십시오.

## AEM 작성자 계층 {#aem-author-tier}

작성자 서버의 사용자 계정 및 UGC 컨텐츠는 AEM Foundation [설명서에서](/help/onboarding/data-privacy-and-protection-readiness/aem-readiness.md)다룹니다.

## AEM 게시 계층 {#aem-publish-tier}

사이트에서 방문자를 인증하는 데 사용되는 사용자 계정 및 게시 서버의 UGC 컨텐츠는 AEM Foundation [설명서에서](/help/onboarding/data-privacy-and-protection-readiness/aem-readiness.md)다룹니다.

기본적으로 AEM Sites 구성 요소는 방문자가 입력한 양식 데이터를 게시 서버에 저장하지 않습니다. 추가 처리를 위해 데이터를 타사 시스템 또는 Adobe Campaign에 전달하는 것이 좋습니다.

## 옵트인/옵트아웃 {#opt-in-opt-out}

<!--
AEM has a [cookie opt-out service](/help/sites-developing/cookie-optout.md ) that can be used for managing the opt-in/opt-out for users.
-->

Adobe Experience Manager는 사용자를 위한 옵트인/옵트아웃을 관리하는 데 사용되는 쿠키 옵트아웃 서비스를 받습니다.

옵트아웃하려면:

1. 다음으로 이동:
   [Adobe 개인 정보 보호 센터 - 옵트아웃](https://www.adobe.com/privacy/opt-out.html)

1. 아래로 스크롤하여 **서비스** - **Experience Cloud 서비스 사용 데이터로**&#x200B;이동합니다.

1. 참조된 링크를 선택합니다.현재 제목이 **여기에**&#x200B;있습니다.

1. 그만두거나 들어올 수 있는 옵션과 함께 다음 세부 사항이 표시됩니다.

   * 이 사이트 방문에 대한 데이터 집계 및 분석을 옵트아웃하려면 브라우저에 쿠키를 설치해야 합니다. 이 쿠키는 사용자가 옵트아웃했음을 나타냅니다.

      옵트아웃 쿠키를 삭제하거나 컴퓨터 또는 웹 브라우저를 변경하는 경우 다시 옵트아웃해야 합니다.

      옵트아웃 - 방문자 세션 집계 및 분석에서 나를 제외합니다( `amcglobal.sc.omtrdc.net` 옵트아웃 쿠키 설치) - 여기를 클릭하십시오.

      옵트인 - 방문자 세션 집계 및 분석에 나를 포함시킵니다( `amcglobal.sc.omtrdc.net` 옵트아웃 쿠키 설치 안 함) - 여기를 클릭합니다.
   위의 단계에 따라 실제 링크에 액세스합니다.

   >[!NOTE]
   >
   > 사용 약관의 개인정보 보호 정책 **섹션에** 대한 [추가 설명이 있습니다](https://marketing.adobe.com/resources/help/en_US/terms.html).

## Analytics Foundation {#analytics-foundation}

AEM Sites에는 Adobe Analytics 온디맨드 서비스 내에서 기능을 사용하는 Analytics Foundation과의 선택적 통합이 포함되어 있습니다.

Adobe Analytics와 관련된 데이터 주체의 요청 관리에 대한 자세한 내용은 Adobe Analytics [및 데이터 개인 정보를 참조하십시오](https://docs.adobe.com/content/help/en/analytics/admin/data-governance/gdpr-view-settings.html).

## Target별 개인화 기반 {#personalization-foundation-by-target}

AEM Sites에는 Adobe Target 온디맨드 서비스 내에서 기능을 사용하는 Personalization Foundation by Target과의 선택적 통합이 포함되어 있습니다.

Adobe Target과 관련된 데이터 주체의 요청 관리에 대한 자세한 내용은 Adobe Target - 개인 [정보 보호 및 일반 데이터 보호 규정을 참조하십시오](https://marketing.adobe.com/resources/help/en_US/target/target/privacy-and-general-data-protection-regulation.html).

## ContextHub {#contexthub}

<!--
AEM provides an optional data layer with [ContextHub](/help/sites-developing/contexthub.md).
-->

AEM 파섹 이렇게 하면 방문자별 데이터가 브라우저에 보관되어 규칙 기반 개인화에 사용됩니다.

기본적으로 이 방문자 데이터는 AEM에 저장되지 않습니다.AEM은 브라우저에서 개인화 결정을 내리기 위해 규칙을 데이터 레이어로 보냅니다.

### 옵트인/옵트아웃 구현 {#implementing-opt-in-opt-out}

사이트 소유자는 다음 지침에 따라 옵트아웃 구성 요소를 구현해야 합니다.

이러한 지침은 기본적으로 옵트인을 구현합니다. 따라서 웹 사이트 방문자는 개인 데이터가 브라우저의 (클라이언트측) 지속성에 저장되기 전에 분명히 동의해야 합니다.

* 옵트아웃 구성 요소는 ContextHub 구성 요소가 포함될 때마다 포함되어야 합니다.
* 웹 사이트의 데이터 보호 및 개인 정보와 관련된 약관을 웹 사이트 방문자에게 표시해야 합니다. 이렇게 하려면 웹 사이트 방문자에게 다음을 허용해야 합니다.

   * accept
   * 거부
   * 이전 선택 변경

* 사이트 방문자가 사이트의 약관에 동의하는 경우 ContextHub 옵트아웃 쿠키는 제거해야 합니다.

   ```
   ContextHub.Utils.Cookie.removeItem('cq-opt-out');
   ```

* 사이트 방문자가 사이트의 약관에 동의하지 않으면 ContextHub 옵트아웃 쿠키를 설정해야 합니다.

   ```
   ContextHub.Utils.Cookie.setItem('cq-opt-out', 1);
   ```

* ContextHub이 옵트아웃 모드에서 실행되고 있는지 확인하려면 브라우저 콘솔에서 다음 호출을 수행해야 합니다.

   ```
   var isOptedOut = ContextHub.isOptedOut(true) === true;
   // if isOptedOut is true, ContextHub is running in opt-out mode
   ```

### ContextHub 지속성 미리 보기 {#previewing-persistence-of-contexthub}

사용자는 사용된 ContextHub을 미리 보려면 다음을 수행할 수 있습니다.

* 브라우저 콘솔 사용;예를 들면 다음과 같습니다.

   * Chrome:

      * 개발자 도구 > 애플리케이션 > 스토리지를 엽니다.

         * 로컬 저장소 > (웹 사이트) > ContextHubPersistence
         * 세션 저장소 > (웹 사이트) > ContextHubPersistence
         * 쿠키 > (웹 사이트) > 세션 지속성
   * Firefox:

      * 개발자 도구 > 스토리지 열기:

         * 로컬 저장소 > (웹 사이트) > ContextHubPersistence
         * 세션 저장소 > (웹 사이트) > ContextHubPersistence
         * 쿠키 > (웹 사이트) > 세션 지속성
   * Safari:

      * 메뉴 모음에서 환경 설정 > 고급 > 현상 메뉴 표시를 엽니다.
      * 현상 > JavaScript 콘솔 표시 열기

         * 콘솔 > 스토리지 > 로컬 스토리지 > (웹 사이트) > ContextHubPersistence
         * 콘솔 > 스토리지 > 세션 스토리지 > (웹 사이트) > ContextHubPersistence
         * 콘솔 > 스토리지 > 쿠키 > (웹 사이트) > ContextHubPersistence
   * Internet Explorer:

      * 개발자 도구 열기 > 콘솔

         * `localStorage.getItem('ContextHubPersistence')`
         * `sessionStorage.getItem('ContextHubPersistence')`
         * `document.cookie`




* 브라우저 콘솔에서 ContextHub API를 사용합니다.

   * ContextHub에서는 다음과 같은 데이터 지속성 레이어를 제공합니다.

      * `ContextHub.Utils.Persistence.Modes.LOCAL` (기본값)
      * `ContextHub.Utils.Persistence.Modes.SESSION`
      * `ContextHub.Utils.Persistence.Modes.COOKIE`
      * `ContextHub.Utils.Persistence.Modes.WINDOW`
      ContextHub 저장소는 사용할 지속성 레이어를 정의하므로 모든 레이어를 확인해야 하는 지속성 상태를 확인할 수 있습니다.


예를 들어 localStorage에 저장된 데이터를 보려면 다음을 수행합니다.

사용자는 사용된 ContextHub을 미리 보려면 다음을 수행할 수 있습니다.

* 브라우저 콘솔을 사용합니다.

   * Chrome - [개발자 도구] > [응용 프로그램] > [저장소]를 엽니다.

      * 로컬 저장소 > (웹 사이트) > ContextHubPersistence
      * 세션 저장소 > (웹 사이트) > ContextHubPersistence
      * 쿠키 > (웹 사이트) > 세션 지속성
   * Firefox - 개발자 도구 > 스토리지 열기:

      * 로컬 저장소 > (웹 사이트) > ContextHubPersistence
      * 세션 저장소 > (웹 사이트) > ContextHubPersistence
      * 쿠키 > (웹 사이트) > 세션 지속성


* 브라우저 콘솔에서 ContextHub API를 사용합니다.

   * ContextHub에서는 다음과 같은 데이터 지속성 레이어를 제공합니다.

      * `ContextHub.Utils.Persistence.Modes.LOCAL` (기본값)
      * `ContextHub.Utils.Persistence.Modes.SESSION`
      * `ContextHub.Utils.Persistence.Modes.COOKIE`
      * `ContextHub.Utils.Persistence.Modes.WINDOW`
      ContextHub 저장소는 사용할 지속성 레이어를 정의하므로 모든 레이어를 확인해야 하는 지속성 상태를 확인할 수 있습니다.


예를 들어 localStorage에 저장된 데이터를 보려면 다음을 수행합니다.

```
var storage = new ContextHub.Utils.Persistence({ mode: ContextHub.Utils.Persistence.Modes.LOCAL });
console.log(storage.getTree());
```

### ContextHub 지속성 지우기 {#clearing-persistence-of-contexthub}

ContextHub 지속성을 지우려면:

* 현재 로드된 스토어의 지속성을 지우려면:

   ```
   // in order to be able to fully access persistence layer, Opt-Out must be turned off
   ContextHub.Utils.Cookie.removeItem('cq-opt-out');
   
   // following call asks all currently loaded stores to clear their data
   ContextHub.cleanAllStores();
   
   // following call asks all currently loaded stores to set back default values (provided in their configs)
   ContextHub.resetAllStores();
   ```

* 특정 지속성 레이어를 지우려면예: sessionStorage:

   ```
   var storage = new ContextHub.Utils.Persistence({ mode: ContextHub.Utils.Persistence.Modes.SESSION });
   storage.setItem('/store', null);
   storage.setItem('/_', null);
   
   // to confirm that nothing is stored:
   console.log(storage.getTree());
   ```

* 모든 ContextHub 지속성 레이어를 지우려면 모든 레이어에 대해 적절한 코드를 호출해야 합니다.

   * `ContextHub.Utils.Persistence.Modes.LOCAL` (기본값)
   * `ContextHub.Utils.Persistence.Modes.SESSION`
   * `ContextHub.Utils.Persistence.Modes.COOKIE`
   * `ContextHub.Utils.Persistence.Modes.WINDOW`
