---
title: 컨텐츠 서비스용 JSON 익스포터
description: AEM Content Services는 웹 페이지에 초점을 두지 않고 AEM에서 컨텐츠 설명 및 게재를 일반화하기 위해 디자인되었습니다. 모든 클라이언트가 사용할 수 있는 표준화된 방법을 사용하여 기존 AEM 웹 페이지가 아닌 채널에 컨텐츠를 게재할 수 있습니다.
translation-type: tm+mt
source-git-commit: 0799a817095558edd49b53ddc915c9474181fef7
workflow-type: tm+mt
source-wordcount: '413'
ht-degree: 30%

---


# 컨텐츠 서비스용 JSON 익스포터 {#json-exporter-for-content-services}

AEM Content Services는 웹 페이지 이외의 AEM에서 컨텐츠의 설명과 전달을 일반화하기 위해 고안되었습니다.

모든 클라이언트가 사용할 수 있는 표준화된 방법을 사용하여 기존 AEM 웹 페이지가 아닌 채널에 컨텐츠를 게재할 수 있습니다. 이러한 채널에는 다음과 같은 것들이 포함될 수 있습니다.

* SPA(Single Page Applications)
* 기본 모바일 애플리케이션
* AEM 외부 채널 및 터치 포인트

구조화된 컨텐츠를 사용하는 컨텐츠 조각을 사용하면 JSON 내보내기 도구를 사용하여 (y) AEM 페이지의 컨텐츠를 JSON 데이터 모델 형식으로 전달하여 컨텐츠 서비스를 제공할 수 있습니다. 그런 다음 사용자 자신의 응용 프로그램에서 사용할 수 있습니다.

## 컨텐츠 조각 핵심 구성 요소를 포함하는 JSON 내보내기 {#json-exporter-with-content-fragment-core-components}

AEM JSON 내보내기 도구를 사용하여 (y) AEM 페이지의 콘텐츠를 JSON 데이터 모델 형식으로 제공할 수 있습니다. 그런 다음 사용자 자신의 응용 프로그램에서 사용할 수 있습니다.

AEM 내에서 선택기 `model` 및 `.json` 확장을 사용하여 배달을 수행합니다.

`.model.json`

1. 예를 들어 다음과 같은 URL입니다.

   ```shell
   http://localhost:4502/content/wknd/language-masters/en/magazine/guide-la-skateparks.model.json
   ```

1. 다음과 같은 컨텐츠를 제공합니다.

   ![WKND 컨텐츠의 JSON 모델](assets/json-model-wknd.png)

구조화된 컨텐츠 조각을 구체적으로 타깃팅하여 컨텐츠를 전달할 수도 있습니다.

이 작업은 조각(를 통해)의 전체 경로를 사용하여 `jcr:content`수행됩니다.예를 들어

`.../jcr:content/root/container/container/contentfragment.model.json`

페이지에는 단일 컨텐츠 조각 또는 다양한 유형의 여러 구성 요소가 포함될 수 있습니다. 목록 구성 요소와 같은 메커니즘을 사용하여 관련 컨텐츠를 자동으로 검색할 수도 있습니다.

* 예를 들어 다음과 같은 URL입니다.

   ```shell
   http://localhost:4502/content/wknd/language-masters/en/magazine/guide-la-skateparks/jcr:content/root/container/container/contentfragment.model.json
   ```

* 다음과 같은 컨텐츠를 제공합니다.

   ![WKND 컨텐츠 조각 JSON 모델](assets/json-model-wknd-content-fragment.png)

   >[!NOTE]
   >
   >자신의 구성 요소를 [조정하여](enabling-json-exporter.md) 이 데이터에 액세스하고 사용할 수 있습니다.

   >[!NOTE]
   >
   >표준 구현은 아니지만 [여러 개의 선택기가 지원되지만](enabling-json-exporter.md#multiple-selectors) 첫 번째 `model` 선택기가 되어야 합니다.

### 추가 정보 {#further-information}

참고 항목:

* 자산 HTTP API
   * [자산 HTTP API](/help/assets/developer-reference-material-apis.md)
* Sling Models:
   * [Sling Models - 130부터 리소스 유형과 모델 클래스 연결](https://sling.apache.org/documentation/bundles/models.html#associating-a-model-class-with-a-resource-type-since-130)
* AEM(JSON 포함):
   * [구성 요소에 대해 JSON 내보내기 활성화](enabling-json-exporter.md)

## 관련 설명서 {#related-documentation}

자세한 내용은 다음을 참조하십시오.

* [자산 사용 안내서의 컨텐츠 조각](/help/assets/content-fragments/content-fragments.md)
* [콘텐츠 조각 모델](/help/assets/content-fragments/content-fragments-models.md)
* [컨텐츠 조각으로 작성](/help/sites-cloud/authoring/fundamentals/content-fragments.md)
* [핵심 구성 요소](https://docs.adobe.com/content/help/ko-KR/experience-manager-core-components/using/introduction.html) 및 [컨텐츠 조각 구성 요소](https://docs.adobe.com/content/help/kr/experience-manager-core-components/using/components/content-fragment-component.html)
