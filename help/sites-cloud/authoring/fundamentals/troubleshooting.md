---
title: 작성 시의 AEM 문제 해결
description: AEM을 사용할 때 발생할 수 있는 몇 가지 문제
translation-type: tm+mt
source-git-commit: 16725342c1a14231025bbc1bafb4c97f0d7cfce8

---


# 작성 시의 AEM 문제 해결 {#troubleshooting-aem-when-authoring}

다음 섹션에서는 AEM 사용 시 발생할 수 있는 문제들과 이러한 문제의 해결 방법에 대한 제안 사항을 다룹니다.

## 게시된 사이트에 이전 페이지 버전이 여전히 있음 {#old-page-version-still-on-published-site}

* **문제**:
   * You have made changes to a page and published the page to the publish site, but the *old* version of the page is still being shown on the publish site.
* **이유**:
   * 이것은 때로 복제 큐 문제일 수 있지만 몇 가지 원인이 있을 수 있고 대개는 캐시 문제일 수 있습니다(로컬 브라우저나 디스패처 중 하나).
* **솔루션**:
   * 다음과 같이 다양한 가능성이 있습니다.
   * 페이지가 올바로 복제되었는지 확인합니다. 페이지 상태를 확인하고, 필요할 경우 복제 큐의 상태도 확인합니다.
   * 로컬 브라우저의 캐시를 지우고 다시 페이지에 액세스합니다.
   * Add `?` to the end of the page URL. For example:
      * `http://<host>:<port>/sites.html/content?`
      * 이렇게 하면 페이지가 AEM에서 바로 요청되고 디스패처가 무시됩니다. 업데이트된 페이지가 표시되면, 이것은 디스패처 캐시를 지우라는 의미입니다.
   * 복제 큐 문제가 있을 경우 시스템 관리자에게 문의하십시오.

## 구성 요소 작업이 도구 모음에 표시되지 않음 {#component-actions-not-visible-on-toolbar}

* **문제**:
   * 적용 가능한 구성 요소 작업의 전체 범위는 작성 환경에서 컨텐츠 페이지를 편집할 때 표시되지 않습니다.
* **이유**:
   * 드문 경우이지만 이전 작업이 도구 모음에 영향을 줄 수 있습니다.
* **솔루션**:
   * 페이지를 새로 고칩니다.
