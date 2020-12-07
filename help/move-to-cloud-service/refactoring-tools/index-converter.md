---
title: 색인 변환기
description: 색인 변환기
translation-type: tm+mt
source-git-commit: fecbd0b4d5cfd8aa970c235c79158bea44403c09
workflow-type: tm+mt
source-wordcount: '169'
ht-degree: 0%

---


# 인덱스 변환기 {#index-converter}

Index Converter는 AEM으로 Cloud Service으로 이동할 준비를 하면서 고객의 인덱스 정의를 마이그레이션하기 위해 개발된 유틸리티입니다.

## 소개 {#introduction}

색인 변환기를 사용하면 AEM 개발자는 기존 사용자 정의 Oak 색인 정의를 Cloud Service 호환 Custom Oak 색인 정의로 AEM으로 마이그레이션할 수 있습니다.

>[!NOTE]
>색인 변환기는 `/apps` 또는 `/oak:index` 아래에 있는 *lucene* 형식의 사용자 지정 Oak 색인 정의만 변환합니다. `nt:base`에 대해 만들어진 *lucene* 유형 색인은 변환하지 않습니다.

사용자 지정 Oak 색인 정의를 만드는 두 가지 방법이 있습니다.

* `under /apps` (사용자 지정 컨텐츠 패키지를 통해)
* `/oak:index` 경로 아래의

>[!NOTE]
>Oak 정의를 정의하고 만드는 방법을 알아보려면 [Oak 색인](https://adobe-consulting-services.github.io/acs-aem-commons/features/ensure-oak-index/index.html)을 참조하십시오.

## 색인 변환기 사용 {#using-index-converter}

>[!NOTE]
>소스 마이그레이션](https://github.com/adobe/aio-cli-plugin-aem-cloud-service-migration)에 대해 [AIO CLI 플러그인을 통해 Index Converter 도구를 사용하는 것이 좋지만, 독립적으로 실행될 수도 있습니다.

**[Git 리소스를 참조하십시오.aem-cs-source-migration-index-converter](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/index-converter)** 플러그인을 설치하고 사용하는 방법에 대해 학습합니다.

