---
title: Content credentials 통합
description: AEM Assets에 통합되고 Assets 보기 내에 포함된 Content credentials은 에셋의 작성 방법 및 작성 참여자 등 에셋 기록에 대한 컨텍스트를 제공할 수 있습니다. 디지털 콘텐츠에 대한 영양 레이블처럼 Content credentials은 투명성을 높이고 대상과 신뢰를 구축하는 데 도움이 될 수 있습니다.
role: User
exl-id: 27c25ae0-4477-40c3-85c8-3e0aa725aba7
source-git-commit: e3fd0fe2ee5bad2863812ede2a294dd63864f3e2
workflow-type: tm+mt
source-wordcount: '480'
ht-degree: 1%

---

# Content Credentials {#content-credentials}

| [모범 사례 검색](/help/assets/search-best-practices.md) | [메타데이터 모범 사례](/help/assets/metadata-best-practices.md) | [Content Hub](/help/assets/product-overview.md) | [OpenAPI 기능이 있는 Dynamic Media](/help/assets/dynamic-media-open-apis-overview.md) | [AEM Assets 개발자 설명서](https://developer.adobe.com/experience-cloud/experience-manager-apis/) |
| ------------- | --------------------------- |---------|----|-----|

브랜드는 콘텐츠 투명성, AI 공시, 자산 변조 방지에 어느 때보다 신경이 쓰인다. Adobe의 CAI(Content Authenticity Initiative)는 [Coalition for Content Provenance and Authenticity](https://c2pa.org/specifications/specifications/1.1/specs/C2PA_Specification.html#_trust_model)(C2PA) 기술 표준을 준수하는 도구를 빌드합니다. Content credentials은 새롭고 암호화된 변조 불가능한 메타데이터로서 시청자가 컨텐츠 계보를 이해하고 브랜드 자산의 무결성을 확인하는 데 도움이 될 수 있습니다. 여기에는 디지털 에셋의 기록에 대한 통찰력을 제공하는 광범위한 조달 데이터가 포함될 수 있습니다.

이 정보는 다음과 같습니다.

* **발급자 또는 서명자:** 인증서를 인증하거나 자산에 서명하기 위해 디지털 서명을 발급한 엔터티 또는 회사에 대한 정보입니다.
* **문제 날짜:** Content Credential이 자산에 적용된 날짜입니다.
* **크레딧 및 사용:** 이름, 소셜 미디어 핸들 또는 기타 ID 관련 정보를 포함하여 에셋 제작자에 대한 정보입니다.
* **프로세스:** 에셋에 대한 편집 또는 수정 사항을 기록합니다.
* **장치 정보:** 자산을 만들거나 편집하는 데 사용되는 앱 또는 장치에 대한 정보입니다.
* **AI 도구 사용됨:** 생성 AI를 사용하여 에셋을 편집하거나 만든 경우 사용된 모델의 이름이 포함될 수 있습니다.
* **기타 관련 정보:** 자산 내역에 대한 추가 컨텍스트를 제공하는 데 도움이 되도록 추가 데이터가 포함될 수도 있습니다.

전체 보기를 위해 [확인](https://contentcredentials.org/verify)을 통해 자산 기록에 대한 보다 포괄적인 통찰력을 제공할 수 있습니다.

Adobe Experience Manager Assets은 이제 Content credentials을 지원하므로 사용자가 AEM의 Assets 보기에서 직접 Content credentials을 볼 수 있습니다. 에셋 세부 사항을 보면 Content credentials이 있는 이미지(예: GenAI 서비스로 만든 이미지)가 전용 패널에 매니페스트 세부 사항을 표시합니다. 에셋이 다운로드, 게시 또는 공유되는 경우 Content credentials은 에셋과 함께 그대로 유지됩니다.

![자산](/help/assets/assets/content-credentials.png)

## 액세스 Content credentials {#access-content-credentials}

1. Assets 보기 UI로 이동한 다음 왼쪽 창에서 **Assets**&#x200B;을(를) 클릭합니다.
1. 폴더로 이동하고 원하는 에셋을 선택합니다.
1. **세부 정보**&#x200B;를 클릭하고 맨 오른쪽 창에서 `Cr pin`을(를) 선택합니다. content credentials 탭에는 에셋에 대한 다음 정보가 표시됩니다.
   1. **생성된 이미지:** Content credentials이 적용된 날짜 및 시간입니다.
   1. **콘텐츠 요약:** 에셋이 AI에 의해 부분적으로 생성되었는지 완전히 생성되었는지 또는 편집된 방법을 나타냅니다.
      ![content credentials](/help/assets/assets/content-credentials1.png)
   1. **프로세스:** 에셋 생성에 사용되는 응용 프로그램, 장치, AI 도구(Adobe Firefly 등)와 이후에 변경한 내용을 자세히 설명합니다.
      ![프로세스](/help/assets/assets/CR-Process.png)
   1. **이 Content credentials 정보:** 발급자의 이름과 발급 날짜 및 시간을 표시합니다.
      ![발급자](/help/assets/assets/CR-issuer.png)
