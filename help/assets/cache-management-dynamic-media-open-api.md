---
title: Open API를 사용한 Dynamic Media의 캐시 관리
description: Open API를 사용한 Dynamic Media의 캐시 관리
role: User
badgeSaas: label="AEM Assets" type="Positive" tooltip="AEM Assets에 적용됩니다)."
exl-id: 203a5291-edb5-4900-8b0a-32e1ebae5395
source-git-commit: a641933d1049cd07ee8935672c8ef357a5bbf18c
workflow-type: tm+mt
source-wordcount: '598'
ht-degree: 1%

---

# Open API를 사용한 Dynamic Media의 캐시 관리 {#cache-management-dynamic-media-open-apis}

효과적인 캐시 관리는 고성능, 확장성 및 최신 디지털 자산을 제공하는 데 필수적입니다. Open API가 있는 Dynamic Media에서 캐시 관리는 게재 파이프라인의 다양한 계층에서 콘텐츠가 저장되고, 새로 고쳐지고, 전달되는 방법을 정의합니다. 에셋 게재 응답은 최적의 성능과 빠른 콘텐츠 전달을 위해 여러 계층에서 캐시됩니다.

Open API를 사용하는 Dynamic Media의 장기 캐싱은 [CDN 계층 캐싱](#cdn-layer-caching) 및 [외부 캐시 제어(BYOCDN 및 브라우저 캐싱)](#byocdn-browser-caching)로 구성됩니다.

## CDN 레이어 캐싱 {#cdn-layer-caching}

자산 게재 응답은 성능을 극대화하고 원본에 대한 로드를 최소화하기 위해 확장된 기간 동안 [Adobe Managed CDN](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/implementing/content-delivery/cdn#aem-managed-cdn)에서 캐시됩니다. 이 캐싱은 Adobe에서 완전히 관리되므로 최종 사용자가 고품질의 경험을 일관되게 유지할 수 있습니다. 캐시 지속 시간은 의도적으로 성능을 위해 최적화되었기 때문에 사용자가 모든 고객에게 안정성과 효율적인 컨텐츠 전달을 유지하도록 사용자 지정할 수 없습니다.

모든 게재 URL은 최적의 성능을 보장하기 위해 연장된 기간 동안 에지(Fastly)에 캐시됩니다. 캐시된 게재 객체에는 정적 렌디션, 비디오, 원본 이미지 바이너리 및 URL 매개 변수를 통해 생성된 크기 조정되거나 형식이 변경된 에셋과 같이 동적으로 변환된 이미지가 포함됩니다. <!--The CDN is designed to serve these assets directly from the cache without revalidating them, unless an explicit purge is performed.-->

## 외부 캐시 제어(BYOCDN 및 브라우저 캐싱) {#byocdn-browser-caching}

자산 게재 응답에는 다운스트림 캐싱 계층에 대해 `Cache-Control`10분`max-age`의 기본 **을(를) 사용하는** 헤더가 포함됩니다. 이는 사용자 지정 *BYOCDN(Bring-Your-Own-CDN) 구성*, *최종 사용자 브라우저* 및 *중간 캐싱 프록시*&#x200B;에 적용되므로 전체 게재 경로에서 일관된 캐시 제어를 보장합니다.

### 캐시 제어 헤더 사용자 정의 {#customizing-cache-control-headers}

캐시 TTL(Time to Live) 값을 기본 구성 이상으로 늘리면 오래된 콘텐츠를 제공할 가능성이 높아져 최종 사용자 경험에서 콘텐츠 업데이트의 가시성이 지연될 수 있습니다. 특정 사용 사례에 대한 캐시 제어 동작을 수정해야 하는 경우 사용자 지정 CDN 규칙을 구성하여 응답 헤더를 조정할 수 있습니다. 요구 사항에 따라 서로 다른 캐시 지속 시간을 설정할 수 있습니다. 응답 헤더에 대한 [AEM 사용자 지정 CDN 규칙](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/implementing/content-delivery/cdn-configuring-traffic)을 참조하세요.

```
responseTransformations:
    rules:
      - name: cache-asset-delivery
        when:
          allOf:
            - reqProperty: path
              like: '/adobe/assets/urn:aaid:aem:*'
            - reqProperty: tier
              equals: delivery
        actions:
          - type: set
            respHeader: Cache-Control
            value: max-age=300
```

캐시 관리에 대한 추가 지원 또는 질문이 있으면 [Adobe 지원](https://helpx.adobe.com/in/contact.html)에 문의하십시오.

## 활성 캐시 무효화 {#active-cache-invalidation}

에셋이 업데이트, 삭제 또는 수정될 때마다(메타데이터 변경 시) Open API가 있는 Dynamic Media는 Adobe Managed CDN에서 연결된 모든 게재 URL을 자동으로 무효화합니다. 이것은 너비, 형식 또는 품질과 같은 변형 매개 변수를 포함하는 URL과 함께 별칭 ID 또는 별칭을 사용하는 URL에 적용됩니다. 이 이벤트 기반 무효화를 통해 사용자는 수동 개입 없이 항상 최신 버전의 자산을 받을 수 있습니다.

### 수동 캐시 삭제 {#manual-cache-purging}

캐시된 콘텐츠를 수동으로 제거해야 하는 경우 AEM의 캐시 무효화 기능을 사용하여 이 작업을 수행할 수 있습니다. 특정 캐시 URL을 제거하는 방법에 대한 자세한 지침은 [AEM CDN 캐시 무효화](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/implementing/content-delivery/cdn-cache-purge#single-purge)를 참조하십시오.

## 자주 묻는 질문{#faq-cache-management}

+++**캐시 관리가 기존 통합에 어떤 영향을 줍니까?**

에셋 URL은 변경되지 않으며, Adobe Managed CDN에서 브라우저(및 기타 다운스트림 중개인)로 전송된 캐시 제어 헤더는 [`stale-while-revalidate directive`](https://web.dev/articles/stale-while-revalidate#whats_it_mean)에서 10분이 되므로 다운스트림 시스템이 캐시를 최적으로 계속 활용하도록 합니다.

+++

+++**캐시 제거를 트리거하는 것은 무엇입니까?**

에셋이 업데이트, 수정, 보관 또는 삭제되면 캐시 제거가 자동으로 트리거됩니다.

<!--The cache purge triggers automatically in the following circumstances:
 
 - when an asset is updated, modified, or archived.
 - when an asset reaches `ready_for_delivery` state after approval.-->

+++

<!--
+++ **How long does it take for the cache to refresh after updating an asset?**

Any time the asset changes, the cache refreshes usually in *less than 60 seconds*.

+++

<!--
+++ **What happens if the cache purge system fails?**
The following mechanisms can be followed:
 
 - **Automatic retries:** 3 retry attempts with exponential backoff
 - **Monitoring:** Sev-2 alert fires if staleness exceeds 10 minutes
 - **Natural expiry:** Even without purge, cache expires after 10 hours maximum
 - **Manual override:** Engineers can manually purge via CLI tool

+++
-->

+++ **장기 캐싱에 대해 지원되는 모든 자산 유형은 무엇입니까?**

이벤트 기반 활성 캐시 무효화를 사용한 장기 캐싱은 자산 유형 또는 형식에 관계없이 Open API를 사용하는 Dynamic Media의 모든 유형의 자산에 적용할 수 있습니다.

+++

+++ **저장소에 대한 장기 캐싱을 옵트아웃할 수 있습니까?**

확장 캐싱을 옵트아웃하려면 [Adobe 지원](https://helpx.adobe.com/in/contact.html)에 연락하여 요청의 이유를 제공하십시오.

+++


>[!MORELIKETHIS]
>
>- [자산 선택기와 다양한 애플리케이션 통합](/help/assets/integrate-asset-selector.md)
>- [가상 URL](/help/assets/vanity-urls.md)
