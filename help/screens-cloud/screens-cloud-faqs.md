---
title: Screens as a Cloud Service FAQ
description: 이 페이지에서는 Screens as a Cloud Service FAQ에 대해 설명합니다.
exl-id: 93f2144c-0e64-4012-88c6-86972d8cad9f
source-git-commit: bc3c054e781789aa2a2b94f77b0616caec15e2ff
workflow-type: tm+mt
source-wordcount: '454'
ht-degree: 2%

---

# Screens as a Cloud Service FAQ {#screens-cloud-faqs}

다음 섹션에서는 Screens as a Cloud Service 프로젝트와 관련된 FAQ에 대한 답변을 제공합니다.

## Screens as a Cloud Service을 가리키는 AEM Screens Player에서 /etc.clientlibs/xxx/clientlibs/clientlib-site.lc-813643788974b0f89d686d9591526d63-lc.min.css 포맷이 있는 사용자 지정 clientlibs를 선택하지 않는 경우 어떻게 해야 합니까?

AEM as a Cloud Service은 모든 배포에서 긴 캐시 키를 변경합니다. AEM Screens은 Cloud Manager가 배포를 실행할 때가 아니라 콘텐츠가 수정될 때 오프라인 캐시를 생성합니다. 매니페스트의 이러한 긴 캐시 키가 잘못되었으므로 플레이어에서 *clientlibs*.

사용 `longCacheKey="none"` (으)로 `clientlib` 폴더는 의 긴 캐시 키를 모두 제거합니다. *clientlibs*.


## 오프라인 매니페스트에 의도한 대로 모든 리소스가 포함되지 않은 경우 어떻게 해야 합니까? {#offline-manifest}

오프라인 캐시는 다음을 사용하여 생성됩니다 **bulk-offline-update-screens-service** 서비스 사용자. 특정 경로를에서 액세스할 수 없음 `bulk-offline-update-screens-service`: 오프라인 매니페스트에서 컨텐츠가 누락됩니다.

코드에서, 즉 `ui.config or ui.apps`, 다음 컨텐츠로 구성 폴더에 OSGi 구성을 만들고 파일 이름을 로 지정합니다. `org.apache.sling.jcr.repoinit.RepositoryInitializer-serviceusersandacls-content.config`

```
scripts=[
        "
        set principal ACL for bulk-offline-update-screens-service
                allow jcr:read on /content/mysite
                allow jcr:read on /apps/my-resources
        end
        "] 
```

## AEM Screens as a Cloud Service 채널에서 원활한 이미지 렌디션에 어떤 이미지 형식을 권장합니까?{#screens-cloud-image-format}

Adobe은 형식의 이미지를 사용할 것을 권장합니다 `.png` 및 `.jpeg` 최고의 디지털 사이니지 경험을 위해 AEM Screens as a Cloud Service 채널에서.
형식의 이미지 `*.tif` (태그 이미지 파일 형식)은 AEM Screens as a Cloud Service에서 지원되지 않습니다. 채널에 이 이미지 형식이 있으면 플레이어 측에서 이미지가 렌더링되지 않습니다.

## 개발자 모드(온라인)의 채널이 AEM Screens Player에서 렌더링되지 않는 경우 어떻게 해야 합니까?{#screens-cloud-online-channel-blank-iframe}

Adobe은 AEM Screens 캐싱 기능을 사용할 것을 권장합니다. 그러나 개발자 모드에서 채널을 실행해야 하고 AEM Screens Player에 빈 화면이 표시되는 경우 플레이어의 개발자 도구를 확인하고 다음을 찾습니다 `X-Frame-Options` 또는 `frame-ancestors` 오류. 해결 방법은 iFrame에서 실행되는 콘텐츠를 허용하도록 Dispatcher를 구성하는 것입니다. 일반적으로 다음 구성이 작동합니다.

```
Header set Content-Security-Policy "frame-ancestors 'self' file: localhost:*;"
```

## 등록 코드 제한의 용도는 무엇입니까?

가장 좋은 방법은 등록 코드 사용을 제한하는 것입니다. 등록 코드가 손상되었지만 등록 수가 100개로 제한되어 있는 경우 공격자는 해당 숫자까지만 등록할 수 있지만 그 이상은 등록할 수 없습니다. 등록 코드가 생성되고 고객의 플레이어가 이미 등록된 후 언제든지 사용 제한을 업데이트할 수 있습니다. 고객이 특정 등록 코드에 대해 비정상적인 등록 활동을 관찰하면 조사하는 동안 실시간으로 한도를 낮출 수 있다. 이미 등록된 플레이어에게 영향을 주지 않고 잘못된 알람인 경우 숫자를 다시 늘릴 수 있습니다.
