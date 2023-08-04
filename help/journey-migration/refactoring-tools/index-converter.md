---
title: 인덱스 변환기
description: AEM as a Cloud Service으로 이동할 준비를 위해 색인 정의를 마이그레이션하는 방법에 대해 알아봅니다.
exl-id: ac02ca41-eb35-4f24-bf17-d00ce318423d
source-git-commit: 8c73805b6ed1b7a03c65b4d21a4252c1412a5742
workflow-type: tm+mt
source-wordcount: '290'
ht-degree: 1%

---

# 인덱스 변환기 {#index-converter}

AEM Index Converter는 as a Cloud Service으로 이전할 때를 대비하여 고객의 Index Definitions를 마이그레이션하기 위해 개발된 유틸리티입니다.

## 소개 {#introduction}

인덱스 변환기 를 사용하면 AEM 개발자가 기존 사용자 지정 Oak 색인 정의를 AEM as a Cloud Service 호환 사용자 지정 Oak 색인 정의로 마이그레이션할 수 있습니다.

>[!NOTE]
>인덱스 변환기만 변환 *lucene* 아래에 있는 사용자 정의 Oak 색인 정의를 입력합니다. `/apps` 또는 `/oak:index`. 변형되지 않습니다 *lucene* 다음에 대해 생성된 인덱스 입력 `nt:base`.

사용자 정의 Oak 색인 정의를 생성하는 방법에는 두 가지가 있습니다.

* `under /apps` (모든 사용자 지정 콘텐츠 패키지를 통해)
* 의 바로 아래에 `/oak:index` 경로

If [Oak 색인 확인](https://adobe-consulting-services.github.io/acs-aem-commons/features/ensure-oak-index/index.html) 이(가) 사용되었습니다. 정의가 AEM as a Cloud Service에서 지원되지 않는지 확인하십시오. 따라서 이러한 OAK 색인 정의는 먼저 Oak 색인 정의로 변환한 다음 아래 지침에 따라 AEM as a Cloud Service과 호환되는 사용자 정의 Oak 색인 정의로 마이그레이션해야 합니다.

* Ignore 속성이 로 설정된 경우 `true`, 정의 확인 무시 또는 건너뛰기
* 업데이트 `jcr:primaryType` 끝 `oak:QueryIndexDefinition`
* OSGi 구성에 언급된 대로 무시할 속성을 제거합니다.
* 하위 트리 제거 `/facets/jcr:content` 시작 정의

## Index Converter 사용 {#using-index-converter}

* Adobe I/O CLI 의 방법 : 의 방법으로 인덱스 변환기 를 사용하는 것이 좋습니다. `aio-cli-plugin-aem-cloud-service-migration` (Adobe I/O CLI용 AEM as a Cloud Service 코드 리팩터링 플러그인).

  다음을 참조하십시오 **[Git 리소스: aio-cli-plugin-aem-cloud-service-migration](https://github.com/adobe/aio-cli-plugin-aem-cloud-service-migration#introduction)** 을(를) 사용하여 플러그인을 설치하고 사용하는 방법을 알아봅니다.

* 독립형 유틸리티로서 : 인덱스 변환기를 독립형 유틸리티로 실행할 수도 있습니다.

  다음을 참조하십시오 **[Git 리소스: aem-cs-source-migration-index-converter](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/index-converter)** 을(를) 사용하여 이 도구를 사용하는 방법을 알아봅니다.
