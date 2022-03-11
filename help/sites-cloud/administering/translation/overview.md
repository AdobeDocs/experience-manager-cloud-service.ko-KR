---
title: 다국어 사이트를 위한 콘텐츠 번역
description: 다국어 사이트의 콘텐츠를 변환하는 방법에 대한 개요를 살펴보십시오.
feature: Language Copy
role: Admin
exl-id: c3e89719-4d08-401b-b9dd-19d1db03d72c
source-git-commit: 04054e04d24b5dde093ed3f14ca5987aa11f5b0e
workflow-type: tm+mt
source-wordcount: '292'
ht-degree: 4%

---

# 다국어 사이트를 위한 콘텐츠 번역 {#translating-content-for-multilingual-sites}

페이지 컨텐츠 및 자산 번역을 자동화하여 다국어 웹 사이트를 제작 및 유지 관리할 수 있습니다. 번역 워크플로우를 자동화하기 위해 번역 서비스 공급자를 AEM과 통합하고 컨텐츠를 여러 언어로 번역할 프로젝트를 만듭니다. AEM은 사람 및 기계 번역 워크플로우를 지원합니다.

* **인간 번역:** 컨텐츠는 번역 공급자에게 전송되고 전문 번역가가 번역합니다. 완료되면 번역된 컨텐츠가 반환되고 AEM으로 가져옵니다. 번역 공급자가 AEM과 통합되면 AEM과 번역 공급자 간에 콘텐츠가 자동으로 전송됩니다.
* **기계 번역:** 기계 번역 서비스는 콘텐츠를 즉시 번역합니다.

>[!TIP]
>
>콘텐츠를 번역할 신규 분은 [사이트 번역 여정,](/help/journey-sites/translation/overview.md) AEM 또는 번역 경험이 없는 사용자에게 이상적인 AEM의 강력한 번역 도구를 사용하여 AEM Sites 컨텐츠를 번역하는 안내식 경로입니다.

컨텐츠를 번역하려면 다음 단계가 포함됩니다.

1. [번역 서비스 공급자와 AEM 연결](integration-framework.md#connecting-to-a-translation-service-provider) 및 [번역 통합 프레임워크 구성 만들기](integration-framework.md).
1. [언어 마스터의 페이지를 연결합니다](integration-framework.md#configuring-pages-for-translation) 변환 서비스 및 프레임워크 구성 사용.
1. [컨텐츠 유형 식별](rules.md) 변환
1. [컨텐츠 번역 준비](preparation.md) 언어 마스터를 작성하고 언어 사본의 루트 페이지를 만들어 봅니다.
1. [번역 프로젝트 만들기](managing-projects.md) 번역할 컨텐츠를 수집하고 번역 프로세스를 준비합니다.
1. 번역 프로젝트를 사용하여 다음 작업을 수행할 수 있습니다 [컨텐츠 번역 프로세스 관리](managing-projects.md).

번역 서비스 공급자가 AEM과의 통합에 커넥터를 제공하지 않는 경우 AEM에서는 XML 형식으로 번역 컨텐츠를 수동으로 추출하고 다시 삽입할 수 있습니다.

>[!NOTE]
>
>사용자는 `project-administrators` 그룹에 언어 복사 기능을 사용할 수 없습니다.

## 우수 사례 {#best-practices}

다음 [번역 우수 사례](best-practices.md) 페이지에는 구현과 관련된 중요한 정보가 포함되어 있습니다.
