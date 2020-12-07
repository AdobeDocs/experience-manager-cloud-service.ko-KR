---
title: 색인 변환기
description: 색인 변환기
translation-type: tm+mt
source-git-commit: 21bd9392d913369a5e8e0ebd9badbbe30fd4bba3
workflow-type: tm+mt
source-wordcount: '102'
ht-degree: 0%

---


# 인덱스 변환기 {#index-converter}

Index Converter는 AEM으로 Cloud Service으로 이동할 준비를 하면서 고객의 인덱스 정의를 마이그레이션하기 위해 개발된 유틸리티입니다.

## 소개 {#introduction}

색인 변환기를 사용하면 AEM 개발자는 기존 사용자 정의 Oak 색인 정의를 Cloud Service 호환 Custom Oak 색인 정의로 AEM으로 마이그레이션할 수 있습니다.

>[!NOTE]
>색인 변환기는 *lucene* 유형인 `/apps` 또는 `/oak:index` 아래에 있는 사용자 지정 Oak 색인 정의만 변형합니다. `nt:base`에 대해 만들어진 *lucene* 유형 색인은 변환하지 않습니다.

## 색인 변환기 사용 {#using-index-converter}

**[Git 리소스를 참조하십시오.aem-cs-source-migration-index-converter](https://github.com/adobe/aio-cli-plugin-aem-cloud-service-migration#introduction)** 플러그인을 설치하고 사용하는 방법에 대해 학습합니다.

