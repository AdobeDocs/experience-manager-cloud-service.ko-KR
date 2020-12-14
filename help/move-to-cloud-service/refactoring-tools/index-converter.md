---
title: 색인 변환기
description: 색인 변환기
translation-type: tm+mt
source-git-commit: 3fe19282f9e96d503f4e8be05553c6f48a6f19b6
workflow-type: tm+mt
source-wordcount: '279'
ht-degree: 0%

---


# 색인 변환기 {#index-converter}

Index Converter는 AEM으로 Cloud Service으로 이동할 준비를 위해 고객의 색인 정의를 마이그레이션하기 위해 개발된 유틸리티입니다.

## 소개 {#introduction}

색인 변환기를 사용하면 AEM 개발자는 기존 사용자 정의 Oak 색인 정의를 Cloud Service 호환 Custom Oak 색인 정의로 AEM에 마이그레이션할 수 있습니다.

>[!NOTE]
>색인 변환기는 `/apps` 또는 `/oak:index` 아래에 있는 *lucene* 유형의 사용자 지정 Oak 색인 정의만 변환합니다. `nt:base`에 대해 만들어진 *lucene* 유형 색인은 변환하지 않습니다.

사용자 지정 Oak 색인 정의를 만드는 방법에는 두 가지가 있습니다.

* `under /apps` (사용자 정의 컨텐츠 패키지를 통해)
* `/oak:index` 경로 아래에

[Oak 색인](https://adobe-consulting-services.github.io/acs-aem-commons/features/ensure-oak-index/index.html)이 사용되었는지 확인하십시오. AEM에서는 정의가 Cloud Service으로 지원되지 않으므로, 먼저 Oak 색인 정의로 변환한 다음 아래 지침에 따라 AEM과 호환 가능한 사용자 정의 Oak 색인 정의로 마이그레이션해야 합니다.

* 속성 ignore가 `true`으로 설정된 경우 정의 확인
* `jcr:primaryType`을(를) `oak:QueryIndexDefinition`(으)로 업데이트
* OSGi 구성에 언급된 대로 무시될 속성을 제거합니다.
* 정의 확인에서 하위 트리 `/facets/jcr:content` 제거

## 인덱스 변환기 사용 {#using-index-converter}

* Adobe I/O CLI 사용:Index Converter를 `aio-cli-plugin-aem-cloud-service-migration`(Adobe I/O CLI용 Cloud Service 코드 리팩토링 플러그인으로 AEM)을 통해 사용하는 것이 좋습니다.

   **[Git 리소스를 참조하십시오.aio-cli-plugin-aem-cloud-service-migration](https://github.com/adobe/aio-cli-plugin-aem-cloud-service-migration#introduction)** 플러그인을 설치하고 사용하는 방법에 대해 학습합니다.

* 독립 실행형 유틸리티로:색인 변환기는 독립 실행형 유틸리티로 실행할 수도 있습니다.

   **[Git 리소스를 참조하십시오.이 도구를 사용하는 방법에 대해 알아보려면 aem-cs-source-migration-index-converter](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/index-converter)**.



