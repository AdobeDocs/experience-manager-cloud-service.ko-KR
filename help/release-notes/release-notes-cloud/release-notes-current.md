---
title: 릴리스 2020.4.0 릴리스 노트
description: 릴리스 2020.4.0 릴리스 노트
translation-type: tm+mt
source-git-commit: 77163877bea36f854ac8ea6fbc78cbcf4d58ccc0

---


# 클라우드 서비스 2020.4.0으로서의 AEM 릴리스 노트 {#release-notes}

다음 섹션에서는 클라우드 서비스 2020.4.0으로서의 Experience Manager에 대한 일반 릴리스 노트를 간략하게 설명합니다.

## 자산 {#assets}

클라우드 서비스 릴리스 2020.4.0으로서 AEM의 Experience Manager 자산 및 Dynamic Media에 대한 새로운 기능과 업데이트를 살펴보려면 이 섹션을 따르십시오.

### 새로운 기능 {#assets-what-is-new}

* [AEM에서](https://docs.adobe.com/content/help/en/experience-manager-brand-portal/using/home.html) 클라우드 서비스 자산으로 브랜드 포털을 사용할 수 있으며 자산 배포 사용 사례를 지원합니다. Brand Portal은 승인된 브랜드 및 제품 자산을 외부 에이전시, 파트너, 내부 팀 및 리셀러에 안전하게 배포하여 조직의 마케팅 요구 사항을 충족할 수 있도록 지원합니다.
   * 브랜드 포털 구성은 Adobe I/O 콘솔을 통해 수행됩니다.
   * 브랜드 포털의 자산 소싱은 아직 클라우드 서비스로 AEM에서 지원되지 않습니다.
* Adobe Asset Link [2.0의](https://helpx.adobe.com/kr/enterprise/using/adobe-asset-link.html) 새로운 릴리스는 AEM에서 클라우드 서비스로 지원됩니다. Adobe Asset Link를 사용하면 앱 내 에셋 링크 패널을 통해 AEM Assets와 Photoshop, Illustrator 및 InDesign의 Creative Cloud 데스크탑 앱을 연결하여 콘텐츠 제작 과정에서 크리에이티브 전문가와 마케터 간의 공동 작업을 간소화할 수 있습니다.
   * 클라우드 서비스로 AEM이 Adobe Asset Link에 대해 미리 구성되어 있으므로 구성이 [간소화됩니다](https://helpx.adobe.com/enterprise/using/configure-aem-assets-for-asset-link.html).
   * 자산 링크는 이제 AEM [환경 전환기를](https://helpx.adobe.com/enterprise/using/manage-assets-using-adobe-asset-link.html#UseAdobeAssetLink)지원하여 크리에이티브 사용자가 다른 AEM 환경에 보다 쉽게 연결할 수 있도록 합니다(예: AEM 자산으로 여러 클라이언트와 일하는 에이전시 디자이너의 경우).
* 폴더 속성 UI에서 특정 폴더 계층에 대한 [사후 처리](/help/assets/asset-microservices-configure-and-use.md#post-processing-workflows) 작업 자동 시작을 구성할 수 있습니다.
   * 메타데이터 프로필, 처리 프로필 및 새로운 자동 시작 워크플로우 구성이 포함된 새로운 자산 처리 탭을 사용하여 폴더 속성 UI가 간소화되었습니다.
* 자산 재처리 대화 상자에서는 특정 처리 프로필을 선택하고 하위 폴더에서 다시 처리할 수 있습니다
* 다이내믹 미디어:선택적 게시 구성을 추가했습니다. 즉, 자산은 보안 미리 보기만을 위해 자동으로 게시되며, 공개 도메인에서 배달을 위해 DMS7에 게시하지 않고도 AEM에 명시적으로 게시할 수 있습니다.

### 버그 수정  {#assets-bug-fixes}

* 자산 처리 수정
* Dynamic Media 구성 및 Dynamic Media 배달 서비스에 자산 게시 수정
