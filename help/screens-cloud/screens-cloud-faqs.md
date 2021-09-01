---
title: 스크린으로 Cloud Service FAQ
description: 이 페이지에서는 Screens를 Cloud Service FAQ로 설명합니다.
source-git-commit: 7a26bb50a8b95a2358912249e21daeb9c5e9c1a3
workflow-type: tm+mt
source-wordcount: '191'
ht-degree: 0%

---


# 스크린으로 Cloud Service FAQ {#screens-cloud-faqs}

다음 섹션에서는 Cloud Service 프로젝트로서 Screens와 관련된 FAQ(자주 묻는 질문)에 대한 답변을 제공합니다.

## AEM Screens 플레이어가 Cloud Service으로 Screens를 가리키는 경우 /etc.clientlibs/xxx/clientlibs/clientlib-site.lc-813643788974b0f89d686d9591526d63-lc.min.css 포맷의 사용자 지정 clientlibs를 선택하지 않으면 어떻게 해야 합니까?

AEM as a Cloud Service은 모든 배포에서 긴 캐시 키를 변경합니다. AEM Screens은 Cloud Manager가 배포를 실행하는 경우가 아니라 컨텐츠가 수정될 때 오프라인 캐시를 생성합니다. 매니페스트에 있는 이러한 긴 캐시 키가 잘못되었으므로 플레이어가 이러한 *clientlibs*&#x200B;를 다운로드하지 못했습니다.

`clientlib` 폴더에서 `longCacheKey="none"`을 사용하면 이러한 *clientlibs*&#x200B;에 대한 긴 캐시 키가 모두 제거됩니다.


## 오프라인 매니페스트에 모든 리소스가 의도한 대로 포함되지 않는 경우 어떻게 해야 합니까? {#offline-manifest}

오프라인 캐시는 **대량 오프라인-update-screens-service** 서비스 사용자를 사용하여 생성됩니다. `bulk-offline-update-screens-service`에서 액세스할 수 없는 특정 경로에서는 오프라인 매니페스트에 콘텐츠가 누락됩니다.

코드에서 `ui.config or ui.apps`, 다음 컨텐츠로 구성 폴더에 OSGi 구성을 만들고 파일 이름을 `org.apache.sling.jcr.repoinit.RepositoryInitializer-serviceusersandacls-content.config`로 지정합니다.

```
scripts=[
        "
        set principal ACL for bulk-offline-update-screens-service
                allow jcr:read on /content/mysite
                allow jcr:read on /apps/my-resources
        end
        "] 
```
