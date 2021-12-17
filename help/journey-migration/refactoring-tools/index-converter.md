---
title: 인덱스 변환기
description: 인덱스 변환기
source-git-commit: a6d225943c5d23ebd960fda0b0912a81f1f80014
workflow-type: tm+mt
source-wordcount: '279'
ht-degree: 0%

---

# 인덱스 변환기 {#index-converter}

Index Converter는 AEM as a Cloud Service으로 이동할 준비를 위해 고객의 색인 정의를 마이그레이션하기 위해 개발된 유틸리티입니다.

## 소개 {#introduction}

Index Converter를 사용하면 AEM 개발자가 기존 사용자 지정 Oak 색인 정의를 AEM as a Cloud Service 호환 사용자 지정 Oak 색인 정의로 마이그레이션할 수 있습니다.

>[!NOTE]
>인덱스 변환기만 변환 *루센* 아래에 있는 사용자 지정 Oak 색인 정의 유형 `/apps` 또는 `/oak:index`. 변환되지 않습니다 *루센* 다음에 대해 생성되는 유형 인덱스 `nt:base`.

사용자 지정 Oak 색인 정의를 만드는 방법에는 두 가지가 있습니다.

* `under /apps` (사용자 지정 컨텐츠 패키지 사용)
* 직접 `/oak:index` 경로

If [Oak 색인 확인](https://adobe-consulting-services.github.io/acs-aem-commons/features/ensure-oak-index/index.html) 이(가) 사용되었으므로 AEM as a Cloud Service에서 정의가 지원되지 않으므로 먼저 Oak 색인 정의로 변환한 다음 아래 지침에 따라 AEM as a Cloud Service과 호환되는 사용자 지정 Oak 색인 정의로 마이그레이션해야 합니다.

* 속성 ignore가 `true`, 정의 확인 을 무시하거나 건너뜁니다.
* 업데이트 `jcr:primaryType` to `oak:QueryIndexDefinition`
* OSGi 구성에서 언급한 대로 무시되는 속성을 제거합니다
* 하위 트리 제거 `/facets/jcr:content` 정의 확인

## Index Converter 사용 {#using-index-converter}

* Adobe I/O CLI 를 통해 : 를 통해 Index Converter를 사용하는 것이 좋습니다 `aio-cli-plugin-aem-cloud-service-migration` (AEM as a Cloud Service 코드 리팩터링 플러그인(Adobe I/O CLI용).

   을(를) 참조하십시오. **[Git 리소스: aio-cli-plugin-aem-cloud-service-migration](https://github.com/adobe/aio-cli-plugin-aem-cloud-service-migration#introduction)** 플러그인을 설치하고 사용하는 방법을 알아봅니다.

* 독립형 유틸리티 : Index Converter는 독립형 유틸리티로도 실행할 수 있습니다.

   을(를) 참조하십시오. **[Git 리소스: aem-cs-source-migration-index-converter](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/index-converter)** 이 도구를 사용하는 방법을 알아봅니다.
