---
title: 인덱스 변환기
description: 인덱스 변환기
exl-id: e6a3ec6d-cc02-4f5b-8b1d-ea481d6884ca
source-git-commit: 90de3cf9bf1c949667f4de109d0b517c6be22184
workflow-type: tm+mt
source-wordcount: '279'
ht-degree: 0%

---

# 인덱스 변환기 {#index-converter}

Index Converter는 AEM으로 Cloud Service으로 이동할 준비를 위해 고객의 색인 정의를 마이그레이션하기 위해 개발된 유틸리티입니다.

## 소개 {#introduction}

Index Converter를 사용하면 AEM 개발자가 기존 사용자 지정 Oak 색인 정의를 Cloud Service 호환 사용자 지정 Oak 색인 정의로 AEM에 마이그레이션할 수 있습니다.

>[!NOTE]
>Index Converter는 *lucene* 유형인 `/apps` 또는 `/oak:index` 아래에 있는 사용자 지정 Oak 색인 정의만 변환합니다. *lucene* 유형 인덱스가 변환되지 않고 `nt:base`에 대해 만들어집니다.

사용자 지정 Oak 색인 정의를 만드는 방법에는 두 가지가 있습니다.

* `under /apps` (사용자 지정 컨텐츠 패키지 사용)
* `/oak:index` 경로 바로 아래

[Oak 색인](https://adobe-consulting-services.github.io/acs-aem-commons/features/ensure-oak-index/index.html)을 사용한 경우, 정의가 AEM에서 Cloud Service으로 지원되지 않으므로 먼저 Oak 색인 정의로 변환한 다음 아래 지침에 따라 AEM과 Cloud Service으로 호환되는 사용자 지정 Oak 색인 정의로 마이그레이션해야 합니다.

* 속성 ignore가 `true`로 설정된 경우 정의 확인 을 무시하거나 건너뜁니다
* `jcr:primaryType`을 `oak:QueryIndexDefinition`(으)로 업데이트
* OSGi 구성에서 언급한 대로 무시되는 속성을 제거합니다
* 정의에서 하위 트리 `/facets/jcr:content` 제거

## Index Converter {#using-index-converter} 사용

* Adobe I/O CLI 를 통해 :`aio-cli-plugin-aem-cloud-service-migration`(AEM을 Adobe I/O CLI용 Cloud Service 코드 리팩터링 플러그인으로 사용)을 통해 Index Converter를 사용하는 것이 좋습니다.

   **[Git 리소스 를 참조하십시오.aio-cli-plugin-aem-cloud-service-migration](https://github.com/adobe/aio-cli-plugin-aem-cloud-service-migration#introduction)** 플러그인을 설치하고 사용하는 방법을 알아봅니다.

* 독립형 유틸리티 :Index Converter는 독립형 유틸리티로도 실행할 수 있습니다.

   **[Git 리소스 를 참조하십시오.aem-cs-source-migration-index-converter](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/index-converter)** 에서 이 도구를 사용하는 방법을 알아보십시오.
