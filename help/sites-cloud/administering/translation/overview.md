---
title: 다국어 사이트의 컨텐츠 번역
description: 다국어 사이트의 콘텐츠를 번역하는 방법에 대한 개요를 살펴보십시오.
translation-type: tm+mt
source-git-commit: 4fc4dbe2386d571fa39fd6d10e432bb2fc060da1
workflow-type: tm+mt
source-wordcount: '254'
ht-degree: 0%

---


# 다국어 사이트 {#translating-content-for-multilingual-sites} 컨텐츠 번역

페이지 컨텐츠와 에셋 번역 작업을 자동화하여 다국어 웹 사이트를 제작 및 유지 관리할 수 있습니다. 번역 워크플로우를 자동화하기 위해 번역 서비스 제공업체를 AEM과 통합하고 컨텐츠를 여러 언어로 번역할 수 있는 프로젝트를 제작할 수 있습니다. AEM은 인간 및 기계 번역 워크플로우를 지원합니다.

* **인간 번역:** 컨텐츠가 번역 공급자에게 전송되고 전문 번역가가 번역합니다. 완료되면 번역된 컨텐츠가 반환되고 AEM으로 가져오게 됩니다. 번역 공급자가 AEM과 통합되면 AEM과 번역 공급자 사이에 컨텐츠가 자동으로 전송됩니다.
* **기계 번역:** 기계 번역 서비스는 컨텐츠를 즉시 변환합니다.

컨텐츠를 번역하려면 다음 단계가 포함됩니다.

1. [번역 서비스 제공업체와 AEM을 ](integration-framework.md#connecting-to-a-translation-service-provider) 연결하고 번역 통합  [프레임워크 구성을 만듭니다](integration-framework.md).
1. [언어 마스터 페이지를 번역 서비스 및 ](integration-framework.md#configuring-pages-for-translation) 프레임워크 구성과 연결합니다.
1. [변환할 컨텐트의 유형을 ](rules.md) 확인합니다.
1. [언어 마스터를 ](preparation.md) 작성하고 언어 사본의 루트 페이지를 만들어 변환할 컨텐츠를 준비합니다.
1. [번역 프로젝트](managing-projects.md) 를 만들어 변환할 컨텐츠를 수집하고 번역 프로세스를 준비할 수 있습니다.
1. 번역 프로젝트를 사용하여 [콘텐츠 번역 프로세스](managing-projects.md)를 관리합니다.

번역 서비스 공급자가 AEM과 통합할 커넥터를 제공하지 않는 경우 AEM은 XML 형식으로 변환 내용을 수동으로 추출하고 다시 삽입할 수 있도록 지원합니다.

>[!NOTE]
>
>언어 복사 기능을 사용하려면 사용자가 `project-administrators` 그룹의 구성원이어야 합니다.

## 우수 사례 {#best-practices}

[번역 우수 사례](best-practices.md) 페이지에는 구현과 관련된 중요한 정보가 들어 있습니다.
