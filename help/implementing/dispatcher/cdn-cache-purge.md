---
title: CDN 캐시 삭제
description: API 호출에 사용할 수 있는 제거 API 토큰을 구성하여 Adobe CDN 캐시에서 캐시된 개체를 제거하는 방법을 알아봅니다.
feature: Dispatcher
source-git-commit: 7224db99c29c90fb5e93ac07d7d501e2e9aaf74e
workflow-type: tm+mt
source-wordcount: '443'
ht-degree: 1%

---

# CDN 캐시 삭제 {#cdn-purge-cache}

>[!NOTE]
>이 기능은 아직 일반적으로 사용할 수 없습니다. 얼리어답터 프로그램에 참여하려면 다음 이메일을 보내십시오. `aemcs-cdn-config-adopter@adobe.com`.

지우기는 Adobe CDN 캐시에서 개체를 제거하여 향후 요청이 캐시에서 처리되지 않고 캐시 누락으로 원점으로 진행됩니다.
AEM as a Cloud Service을 사용하면 제거 API 토큰을 구성할 수 있으며, 이 토큰을 API 호출에 사용할 수 있습니다. 읽기 <!--[Configuring CDN Credentials and Authentication article](/help/implementing/dispatcher/cdn-credentials-authentication.md#purge-API-token)--> cloud Manager 구성 파이프라인 인증 지침을 사용하여 이 토큰을 구성하는 방법을 알아봅니다.

세 가지 지원되는 삭제 변형이 있습니다.

* [단일 URL 삭제](#single-purge) - 한 번에 하나의 리소스를 제거합니다.
* [대리 키로 제거](#surrogate-key-purge) - 여러 리소스를 한 번에 제거합니다.
* [전체 제거](#full-purge) - 모든 리소스를 제거합니다.

모든 제거 변형은 다음을 공유합니다.

* HTTP 메서드를 로 설정해야 합니다. `PURGE`.
* URL은 제거 요청이 의도된 AEM 서비스와 연관된 모든 도메인일 수 있습니다.
* 다음 `X-AEM-Purge-Key` 은(는) HTTP 헤더에 제공해야 합니다.

>[!CAUTION]
>특히 하드 플래그를 사용하여 CDN 캐시를 지우면 원본의 트래픽이 증가하며 제대로 실행되지 않을 경우 중단이 발생할 수 있습니다.

## 단일 URL 삭제 {#single-purge}

다음과 같이 한 번에 하나의 리소스를 제거할 수 있습니다.

```
curl
-X PURGE "https://publish-p1234-e5467.adobeaemcloud.com/resource-path" \
-H 'X-AEM-Purge-Key: <my_purge_key>' \
-H 'X-AEM-Purge: soft'
```

위의 예에서 보듯이 **선택적으로** cdn이 다음을 수행할지 여부를 지정합니다. **단단하** 제거(기본값) 또는 **소프트** 캐시된 객체를 제거합니다.

기본 하드 제거를 사용하면 콘텐츠를 원본에서 검색할 때까지 새로운 요청에 즉시 액세스할 수 없게 됩니다. 소프트 지우기는 콘텐츠를 부실 상태로 표시하지만 여전히 클라이언트에 제공하므로 콘텐츠를 원점에서 검색할 때까지 기다릴 필요가 없습니다.

## 대리 키 제거 {#surrogate-key-purge}

서로게이트 키는 콘텐츠 세트를 제거하는 데 사용하는 고유한 식별자입니다. 을 추가하여 콘텐츠에 적용합니다. `Surrogate-Key` 응답에 대한 헤더입니다. 제거 API 호출에서 하나 이상의 대리 키를 참조할 수 있습니다.

```
curl
-X PURGE "https://publish-p1234-e5467.adobeaemcloud.com" \
-H 'X-AEM-Purge-Key: <my_purge_key>' \
-H "Surrogate-Key: my-surrogate-key"
-H "X-AEM-Purge: soft" #optional
```

다음 `Surrogate-Key`(s)는 공백으로 구분됩니다. 단일 URL 제거와 마찬가지로 하드 또는 소프트 제거를 구성할 수 있습니다.

## 전체 제거 {#full-purge}

다음과 같이 캐시된 모든 리소스를 완전히 제거할 수 있습니다.

```
curl
-X PURGE "https://publish-p1234-e5467.adobeaemcloud.com" \
-H 'X-AEM-Purge-Key: <my_purge_key>' \
-H "X-AEM-Purge: all"
```

다음 사항에 주의하십시오. `X-AEM-Purge` 헤더에는 &#39;all&#39; 값이 포함되어야 합니다.

## Apache/Dispatcher 계층과의 상호 작용 {#apache-layer}

에 설명된 대로 [컨텐츠 전달 흐름 문서](/help/implementing/dispatcher/overview.md), CDN은 캐시가 만료된 경우 Apache/Dispatcher 레이어에서 콘텐츠를 검색합니다. 이는 CDN에서 리소스를 제거하기 전에 Dispatcher에서도 새로운 버전의 콘텐츠를 사용할 수 있는지 확인해야 함을 의미합니다. 자세한 내용은 다음을 참조하십시오. [디스패처 캐시 무효화](/help/implementing/dispatcher/caching.md#disp).
