---
title: 콘텐츠 서비스에 대한 JSON 내보내기
description: AEM Content Services는 웹 페이지에 초점을 두지 않고 AEM에서 콘텐츠 설명 및 게재를 일반화하기 위해 디자인되었습니다. 모든 클라이언트가 사용할 수 있는 표준화된 방법을 사용하여 기존 AEM 웹 페이지가 아닌 채널에 콘텐츠를 게재할 수 있습니다.
exl-id: d3ddffb7-cef9-4c86-aa31-175f13f9b4a5
source-git-commit: 6be7cc7678162c355c39bc3000716fdaf421884d
workflow-type: tm+mt
source-wordcount: '404'
ht-degree: 31%

---

# 콘텐츠 서비스에 대한 JSON 내보내기 {#json-exporter-for-content-services}

AEM Content Services는 웹 페이지의 초점 외에 AEM 내/에서 컨텐츠의 설명 및 전달을 일반화하도록 설계되었습니다.

모든 클라이언트가 사용할 수 있는 표준화된 방법을 사용하여 기존 AEM 웹 페이지가 아닌 채널에 콘텐츠를 게재할 수 있습니다. 이러한 채널에는 다음과 같은 것들이 포함될 수 있습니다.

* SPA (Single Page Applications)
* 기본 모바일 애플리케이션
* AEM 외부의 기타 채널 및 터치 포인트

구조화된 컨텐츠를 사용하는 컨텐츠 조각을 사용하면 JSON 내보내기 도구를 사용하여 (y) AEM 페이지의 컨텐츠를 JSON 데이터 모델 형식으로 전달하여 컨텐츠 서비스를 제공할 수 있습니다. 그런 다음 자체 애플리케이션에서 사용할 수 있습니다.

## 컨텐츠 조각 핵심 구성 요소가 있는 JSON 내보내기 {#json-exporter-with-content-fragment-core-components}

AEM JSON Exporter를 사용하여 (y) AEM 페이지의 컨텐츠를 JSON 데이터 모델 형식으로 제공할 수 있습니다. 그런 다음 자체 애플리케이션에서 사용할 수 있습니다.

AEM 내에서 선택기를 사용하여 게재를 수행합니다 `model` 및 `.json` 확장.

`.model.json`

1. 예를 들어 다음과 같은 URL이 있습니다.

   ```shell
   http://localhost:4502/content/wknd/language-masters/en/magazine/guide-la-skateparks.model.json
   ```

1. 은 다음과 같은 컨텐츠를 제공합니다.

   ![WKND 컨텐츠의 JSON 모델](assets/json-model-wknd.png)

또는 구조화된 컨텐츠 조각의 컨텐츠를 특별히 타깃팅하여 게재할 수 있습니다.

이 작업은 조각에 대한 전체 경로( `jcr:content`); 예를 들어 와 같은 접미사가 있는 경우.

`.../jcr:content/root/container/container/contentfragment.model.json`

페이지에는 단일 컨텐츠 조각 또는 다양한 유형의 여러 구성 요소가 포함될 수 있습니다. 목록 구성 요소와 같은 메커니즘을 사용하여 관련 컨텐츠를 자동으로 검색할 수도 있습니다.

* 예를 들어 다음과 같은 URL이 있습니다.

   ```shell
   http://localhost:4502/content/wknd/language-masters/en/magazine/guide-la-skateparks/jcr:content/root/container/container/contentfragment.model.json
   ```

* 은 다음과 같은 컨텐츠를 제공합니다.

   ![WKND 컨텐츠 조각의 JSON 모델](assets/json-model-wknd-content-fragment.png)

   >[!NOTE]
   >
   >다음을 수행할 수 있습니다 [고유한 구성 요소 조정](enabling-json-exporter.md) 이 데이터에 액세스하여 사용합니다.

   >[!NOTE]
   >
   >표준 구현은 아니지만, [여러 선택기가 지원되고](enabling-json-exporter.md#multiple-selectors) 그러나 `model` 첫 번째여야 합니다.

### 추가 정보 {#further-information}

또한 Headless 개념 및 용어 소개가 포함되어 있는

* Assets HTTP API
   * [자산 HTTP API](/help/assets/developer-reference-material-apis.md)
* Sling 모델:
   * [Sling 모델 - 130 이후 모델 클래스를 리소스 유형과 연결](https://sling.apache.org/documentation/bundles/models.html#associating-a-model-class-with-a-resource-type-since-130)
* JSON이 있는 AEM:
   * [구성 요소에 대해 JSON 내보내기 활성화](enabling-json-exporter.md)

## 관련 설명서 {#related-documentation}

자세한 내용은 다음을 참조하십시오.

* [콘텐츠 조각](/help/sites-cloud/administering/content-fragments/content-fragments.md)
* [콘텐츠 조각 모델](/help/sites-cloud/administering/content-fragments/content-fragments-models.md)
* [컨텐츠 조각으로 작성](/help/sites-cloud/authoring/fundamentals/content-fragments.md)
* [핵심 구성 요소](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html) 그리고 [컨텐츠 조각 구성 요소](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/components/content-fragment-component.html)
