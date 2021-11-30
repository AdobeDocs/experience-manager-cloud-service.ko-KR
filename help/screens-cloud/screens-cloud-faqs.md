---
title: 화면 as a Cloud Service FAQ
description: 이 페이지에서는 Screens as a Cloud Service FAQ에 대해 설명합니다.
exl-id: 93f2144c-0e64-4012-88c6-86972d8cad9f
source-git-commit: 489cc9963910ba9f94d30906127beb75f9ad37df
workflow-type: tm+mt
source-wordcount: '458'
ht-degree: 0%

---

# 화면 as a Cloud Service FAQ {#screens-cloud-faqs}

다음 섹션에서는 Screens as a Cloud Service 프로젝트와 관련된 FAQ(자주 묻는 질문)에 대한 답변을 제공합니다.

## Screens as a Cloud Service을 가리키는 AEM Screens Player가 /etc.clientlibs/xxx/clientlibs/clientlib-site.lc-813643788974b0f89d686d9591526d63-lc.min.css 포맷의 사용자 지정 clientlibs를 선택하지 않으면 어떻게 해야 합니까?

AEM as a Cloud Service은 모든 배포에 있는 긴 캐시 키를 변경합니다. AEM Screens은 Cloud Manager가 배포를 실행하는 경우가 아니라 컨텐츠가 수정될 때 오프라인 캐시를 생성합니다. 매니페스트에 있는 이러한 긴 캐시 키가 잘못되어 플레이어가 이 키를 다운로드하지 못합니다 *clientlibs*.

사용 `longCacheKey="none"` 다음 위치에서 `clientlib` 폴더가 이러한 폴더에 대한 긴 캐시 키를 모두 제거합니다. *clientlibs*.


## 오프라인 매니페스트에 모든 리소스가 의도한 대로 포함되지 않는 경우 어떻게 해야 합니까? {#offline-manifest}

오프라인 캐시는 **bulk-offline-update-screens-service** 서비스 사용자. 특정 경로로서 액세스할 수 없음 `bulk-offline-update-screens-service`를 입력하면 오프라인 매니페스트에 콘텐츠가 누락됩니다.

코드에서는, `ui.config or ui.apps`를 채울 때는 구성 폴더에 다음 컨텐츠를 사용하여 OSGi 구성을 만들고 파일 이름을 로 지정합니다. `org.apache.sling.jcr.repoinit.RepositoryInitializer-serviceusersandacls-content.config`

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

형식으로 이미지를 사용하는 것이 좋습니다 `.png` 및 `.jpeg` AEM Screens as a Cloud Service 채널에서 최고의 디지털 간판 경험을 확인하십시오.
형식의 이미지 `*.tif` (태그 이미지 파일 형식)은 AEM Screens as a Cloud Service에서 지원되지 않습니다. 채널에 이 이미지 형식이 있으면 플레이어 측에서 이미지가 렌더링되지 않습니다.

## 개발자 모드(온라인)의 채널이 AEM Screens 플레이어에서 렌더링되지 않는 경우 어떻게 해야 합니까?{#screens-cloud-online-channel-blank-iframe}

AEM Screens 캐싱 기능을 활용하는 것이 좋지만 개발자 모드에서 채널을 실행해야 하며 AEM Screens 플레이어에 빈 화면이 표시되는 경우 플레이어의 개발자 도구를 확인하고 를 찾습니다 `X-Frame-Options` 또는 `frame-ancestors` 오류가 발생합니다. 해결 방법은 iFrame에서 컨텐츠를 실행할 수 있도록 디스패처를 구성하는 것입니다. 일반적으로 다음 구성이 작동합니다.

```
Header set Content-Security-Policy "frame-ancestors ‘self’ file: localhost:*;"
```

## 등록 코드 한도의 사용은 무엇입니까?

가장 좋은 방법은 등록 코드 사용을 제한할 수 있습니다. 등록 코드가 손상되었지만 100개의 등록 제한이 있는 경우 공격자는 해당 번호까지만 등록할 수 있지만 더 이상 등록할 수 없습니다. 등록 코드가 생성되고 일부 고객의 플레이어가 이미 등록된 후에는 항상 사용 제한을 업데이트할 수 있습니다. 고객이 특정 등록 코드에 대한 비정상적인 등록 활동을 관찰하면 실시간으로 제한 사항을 낮출 수 있고, 잘못된 경보였다면 등록된 플레이어에게 영향을 주지 않고 숫자를 다시 늘릴 수 있습니다.