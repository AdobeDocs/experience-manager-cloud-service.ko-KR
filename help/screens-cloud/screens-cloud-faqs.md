---
title: Screens as a Cloud Service FAQ
description: 이 페이지에서는 Screens as a Cloud Service에 대해 자주 묻는 질문을 설명합니다.
exl-id: 93f2144c-0e64-4012-88c6-86972d8cad9f
source-git-commit: bc3c054e781789aa2a2b94f77b0616caec15e2ff
workflow-type: ht
source-wordcount: '454'
ht-degree: 100%

---

# Screens as a Cloud Service FAQ {#screens-cloud-faqs}

다음 섹션에서는 Screens as a Cloud Service 프로젝트와 관련된 자주 묻는 질문(FAQ)에 대한 답변을 제공합니다.

## Screens as a Cloud Service를 가리키는 AEM Screens 플레이어가 /etc.clientlibs/xxx/clientlibs/clientlib-site.lc-813643788974b0f89d686d9591526d63-lc.min.css 형식의 사용자 정의 clientlibs를 선택하지 않는 경우 어떻게 해야 합니까?

AEM as a Cloud Service는 배포 시마다 긴 캐시 키를 변경합니다. AEM Screens는 Cloud Manager가 배포를 실행할 때가 아니라 콘텐츠가 수정될 때 오프라인 캐시를 생성합니다. 매니페스트에 있는 이러한 긴 캐시 키는 유효하지 않으므로 플레이어에서 *clientlibs*&#x200B;를 다운로드하지 못합니다.

`clientlib` 폴더에서 `longCacheKey="none"`을 사용하면 *clientlibs*&#x200B;의 긴 캐시 키가 모두 제거됩니다.


## 오프라인 매니페스트에 의도한 대로 모든 리소스가 포함되지 않으면 어떻게 해야 합니까? {#offline-manifest}

오프라인 캐시는 **bulk-offline-update-screens-service** 서비스 사용자를 사용하여 생성됩니다. `bulk-offline-update-screens-service`에서 특정 경로에 액세스하지 못하면 오프라인 매니페스트에서 내용이 누락될 수 있습니다.

코드, 즉 `ui.config or ui.apps`에서 다음 내용으로 구성 폴더에 OSGi 구성을 만들고 파일 이름을 `org.apache.sling.jcr.repoinit.RepositoryInitializer-serviceusersandacls-content.config`로 지정하십시오.

```
scripts=[
        "
        set principal ACL for bulk-offline-update-screens-service
                allow jcr:read on /content/mysite
                allow jcr:read on /apps/my-resources
        end
        "] 
```

## AEM Screens as a Cloud Service 채널에서 이미지를 원활하게 렌디션하려면 어떤 이미지 형식이 권장됩니까?{#screens-cloud-image-format}

Adobe에서는 AEM Screens as a Cloud Service 채널에서 최고의 디지털 사이니지 경험을 위해 `.png` 및 `.jpeg` 형식의 이미지를 사용할 것을 권장합니다.
`*.tif` 형식(Tag Image File 형식)의 이미지는 AEM Screens as a Cloud Service에서 지원되지 않습니다. 채널에 이 이미지 형식이 있으면 플레이어 측에서 이미지가 렌더링되지 않습니다.

## 개발자 모드(온라인)의 채널이 AEM Screens 플레이어에서 렌더링되지 않는 경우 어떻게 해야 합니까?{#screens-cloud-online-channel-blank-iframe}

Adobe에서는 AEM Screens 캐싱 기능을 사용할 것을 권장합니다. 그러나 개발자 모드에서 채널을 실행해야 하고 AEM Screens 플레이어에 빈 화면이 표시되는 경우 플레이어의 개발자 도구를 확인하여 `X-Frame-Options` 또는 `frame-ancestors` 오류를 찾으십시오. 해결 방법은 iFrame에서 콘텐츠가 실행될 수 있도록 Dispatcher를 구성하는 것입니다. 일반적으로 다음 구성이 작동합니다.

```
Header set Content-Security-Policy "frame-ancestors 'self' file: localhost:*;"
```

## 등록 코드 제한의 용도는 무엇입니까?

모범 사례로서 등록 코드 사용을 제한할 수 있습니다. 등록 코드가 침해되더라도 등록이 100개로 제한되어 있는 경우 공격자는 해당 수까지만 등록할 수 있고 이를 초과해서는 등록할 수 없습니다. 등록 코드가 생성되고 고객의 플레이어 중 일부가 이미 등록된 후 언제든지 사용 제한을 업데이트할 수 있습니다. 고객이 특정 등록 코드의 비정상적인 등록 활동을 확인하는 경우 조사하는 동안 실시간으로 제한을 낮출 수 있습니다. 실제 문제가 아닌 경우에는 이미 등록된 플레이어에 영향을 주지 않고 숫자를 다시 늘릴 수 있습니다.
