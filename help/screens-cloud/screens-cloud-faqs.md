---
title: 화면 as a Cloud Service FAQ
description: 이 페이지에서는 Screens as a Cloud Service FAQ에 대해 설명합니다.
exl-id: 93f2144c-0e64-4012-88c6-86972d8cad9f
source-git-commit: cf091056bdb96917a6d22bf1197d9b34ebbf9610
workflow-type: tm+mt
source-wordcount: '275'
ht-degree: 0%

---

# 화면 as a Cloud Service FAQ {#screens-cloud-faqs}

다음 섹션에서는 Screens as a Cloud Service 프로젝트와 관련된 FAQ(자주 묻는 질문)에 대한 답변을 제공합니다.

## Screens as a Cloud Service을 가리키는 AEM Screens 플레이어가 /etc.clientlibs/xxx/clientlibs/clientlib-site.lc-813643788974b0f89d686d9591526d63-lc.min.css 포맷의 사용자 지정 clientlibs를 선택하지 않으면 어떻게 해야 합니까?

AEM as a Cloud Service은 모든 배포에 있는 긴 캐시 키를 변경합니다. AEM Screens은 Cloud Manager가 배포를 실행하는 경우가 아니라 컨텐츠가 수정될 때 오프라인 캐시를 생성합니다. 매니페스트에 있는 이러한 긴 캐시 키가 잘못되었으므로 플레이어가 이러한 *clientlibs*&#x200B;를 다운로드하지 못했습니다.

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

## AEM Screens as a Cloud Service 채널에서 이미지의 원활한 렌디션을 위해 권장되는 이미지 형식은 무엇입니까?{#screens-cloud-image-format}

최상의 디지털 사이니지 경험을 위해 AEM Screens as a Cloud Service 채널에서 `.png` 및 `.jpeg` 형식의 이미지를 사용하는 것이 좋습니다.
`*.tif` 형식의 이미지(태그 이미지 파일 형식)는 AEM Screens as a Cloud Service에서 지원되지 않습니다. 채널에 이 이미지 형식이 있으면 플레이어 측에서 이미지가 렌더링되지 않습니다.