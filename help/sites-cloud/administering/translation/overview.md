---
title: 다국어 사이트를 위한 콘텐츠 번역
description: 다국어 사이트를 위한 콘텐츠를 번역하는 방법에 대한 개요를 살펴봅니다.
feature: Language Copy
role: Admin
exl-id: c3e89719-4d08-401b-b9dd-19d1db03d72c
source-git-commit: 04054e04d24b5dde093ed3f14ca5987aa11f5b0e
workflow-type: tm+mt
source-wordcount: '292'
ht-degree: 100%

---

# 다국어 사이트를 위한 콘텐츠 번역 {#translating-content-for-multilingual-sites}

페이지 콘텐츠 및 에셋의 번역을 자동화하여 다국어 웹 사이트를 만들고 관리할 수 있습니다. 번역 워크플로를 자동화하려면 번역 서비스 공급업체를 AEM과 통합하고 콘텐츠를 다국어로 번역하는 프로젝트를 제작해야 합니다. AEM은 사람 번역 및 기계 번역 워크플로를 지원합니다.

* **사람 번역:** 콘텐츠를 전문 번역사가 번역할 수 있도록 번역 공급업체로 보냅니다. 번역이 완료되면 번역된 콘텐츠는 반환되어 AEM으로 가져와집니다. 번역 공급업체를 AEM과 통합하면 콘텐츠는 자동으로 AEM과 번역 공급업체 간 전송됩니다.
* **기계 번역:** 콘텐츠가 기계 번역 서비스를 통해 즉시 번역됩니다.

>[!TIP]
>
>콘텐츠 번역이 처음이라면 AEM의 강력한 번역 도구를 사용한 AEM Sites 콘텐츠 번역을 안내하며 AEM이 없거나 번역 경험이 없는 사용자에게 최적화된 [사이트 번역 여정](/help/journey-sites/translation/overview.md)을 참조하십시오.

콘텐츠 번역의 단계는 다음과 같습니다.

1. [AEM과 번역 서비스 공급업체를 연결](integration-framework.md#connecting-to-a-translation-service-provider)한 다음 [번역 통합 프레임워크 구성을 만듭니다](integration-framework.md).
1. 번역 서비스 및 프레임워크 구성과 [언어 마스터의 페이지를 연결](integration-framework.md#configuring-pages-for-translation)합니다.
1. 번역할 [콘텐츠의 유형을 식별](rules.md)합니다.
1. 언어 마스터를 작성하고 언어 사본의 루트 페이지를 만들어 [번역할 콘텐츠를 준비](preparation.md)합니다.
1. [번역 프로젝트를 제작하여](managing-projects.md) 번역할 콘텐츠를 수집하고 번역 프로세스를 준비합니다.
1. 번역 프로젝트를 사용하여 [콘텐츠 번역 프로세스를 관리](managing-projects.md)합니다.

번역 서비스 공급업체에서 AEM과의 통합을 위한 커넥터를 제공하지 않을 경우, AEM은 XML 형식의 번역 콘텐츠에 대한 수동 추출 및 재삽입을 지원합니다.

>[!NOTE]
>
>언어 복사 기능을 사용하려면 사용자는 `project-administrators` 그룹의 멤버여야 합니다.

## 모범 사례 {#best-practices}

[번역 모범 사례](best-practices.md) 페이지에는 구현과 관련된 중요한 정보가 포함되어 있습니다.
