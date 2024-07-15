---
title: 인덱스 변환기
description: AEM as a Cloud Service으로 이동할 준비를 위해 색인 정의를 마이그레이션하는 방법에 대해 알아봅니다.
exl-id: ac02ca41-eb35-4f24-bf17-d00ce318423d
feature: Migration
role: Admin
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '272'
ht-degree: 1%

---

# 인덱스 변환기 {#index-converter}

Index Converter는 AEM as a Cloud Service으로 이동할 준비를 하면서 고객의 Index Definitions를 마이그레이션하기 위해 개발된 유틸리티입니다.

## 소개 {#introduction}

인덱스 변환기 를 사용하면 AEM 개발자가 기존 사용자 지정 Oak 인덱스 정의를 호환되는 AEM as a Cloud Service 사용자 지정 Oak 인덱스 정의로 마이그레이션할 수 있습니다.

>[!NOTE]
>인덱스 변환기는 `/apps` 또는 `/oak:index` 아래에 있는 *lucene* 유형의 사용자 지정 Oak 인덱스 정의만 변환합니다. `nt:base`에 대해 만들어진 *lucene* 형식 인덱스를 변환하지 않습니다.

사용자 지정 Oak 색인 정의를 만드는 방법에는 두 가지가 있습니다.

* `under /apps`(모든 사용자 지정 콘텐츠 패키지를 통해)
* `/oak:index` 경로 바로 아래

[Oak 인덱스 확인](https://adobe-consulting-services.github.io/acs-aem-commons/features/ensure-oak-index/index.html)을 사용한 경우 AEM as a Cloud Service에서 정의가 지원되지 않는지 확인하십시오. 따라서 아래 지침에 따라 먼저 Oak 색인 정의로 변환한 다음 AEM as a Cloud Service과 호환되는 사용자 지정 Oak 색인 정의로 마이그레이션해야 합니다.

* Ignore 속성이 `true`(으)로 설정된 경우 정의 확인을 무시하거나 건너뜁니다.
* `jcr:primaryType`을(를) `oak:QueryIndexDefinition`(으)로 업데이트
* OSGi 구성에 언급된 대로 무시할 속성을 제거합니다.
* 확인 정의에서 하위 트리 `/facets/jcr:content` 제거

## Index Converter 사용 {#using-index-converter}

* Adobe I/O CLI 사용 : Adobe은 `aio-cli-plugin-aem-cloud-service-migration`(Adobe I/O CLI의 경우 AEM as a Cloud Service 코드 리팩터링 플러그인)을 통해 인덱스 변환기를 사용할 것을 권장합니다.

  플러그인을 설치하고 사용하는 방법에 대해 알아보려면 **[Git 리소스: aio-cli-plugin-aem-cloud-service-migration](https://github.com/adobe/aio-cli-plugin-aem-cloud-service-migration#introduction)**&#x200B;을(를) 참조하십시오.

* 독립형 유틸리티로서 : 인덱스 변환기를 독립형 유틸리티로 실행할 수도 있습니다.

  이 도구의 사용 방법을 알아보려면 **[Git 리소스: aem-cs-source-migration-index-converter](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/index-converter)**&#x200B;를 참조하십시오.
