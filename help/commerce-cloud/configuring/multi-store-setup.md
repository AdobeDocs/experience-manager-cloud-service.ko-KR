---
title: 다중 스토어 설정
description: 다중 스토어 설정
translation-type: tm+mt
source-git-commit: 94c6abef36b6add300ba3b24855ebf3edf10e1ed
workflow-type: tm+mt
source-wordcount: '335'
ht-degree: 0%

---


# 다중 스토어 설정 {#multi-store}

AEM CIF 핵심 구성 요소는 여러 AEM 사이트 구조에서 사용할 수 있으며 기본 GraphQL 클라이언트 구현은 서로 다른 Magento 스토어/스토어 뷰에 연결할 수 있습니다. 이를 통해 복잡한 다중 저장소/다중 사이트 설정을 구현할 수 있습니다.

여러 Magento 스토어 보기를 Adobe Experience Manager Sites과 통합하는 옵션을 자세히 설명하는 비디오 연습입니다.

>[!VIDEO](https://video.tv.adobe.com/v/28952/?quality=12)

AEM Live Copy 및 언어 카피의 다중 사이트 관리 기능은 Commerce Integration Framework와 함께 사용하여 지역 및 로케일 간에 사이트를 전역적으로 관리합니다.

AEM 사이트와 Magento 스토어 보기 간에 1:1 관계를 사용하는 것이 좋습니다.

AEM 사이트 및 AEM CIF 핵심 구성 요소를 전용 스토어 보기에 연결하려면 아래 단계를 따르십시오.

## 구성 {#configuration}

1. Magento 웹 사이트, 스토어 및 보기에 설명된 패턴에 따라 여러 스토어 및 [스토어 보기 구성](https://docs.magento.com/m2/ce/user_guide/stores/websites-stores-views.html)

2. AEM과 Magento 간의 연결이 작동하는지 확인합니다.

3. 다음 단계에 따라 CIF Cloud Service 구성의 하위 구성을 만듭니다.

   * AEM에서 도구 -> 일반 -> 구성 브라우저로 이동
   * 만든 기본 구성 선택
   * 위의 2단계에서 설명한 단계를 사용하여 새 구성 만들기

   이 새 구성은 기본 구성의 하위 구성으로 생성됩니다. 이제 도구 -> 일반 -> 구성 브라우저로 이동하여 구성 설정을 만들 수 있습니다.

4. AEM 사이트에 하위 구성 할당

   * AEM Sites 콘솔으로 이동
   * 사이트 구조의 지역 또는 언어 루트로 이동합니다(예: /content/venia/us _or_ /content/venia/us/en for Venia 샘플 페이지
   * 페이지 선택 및 페이지 속성 열기
   * 고급 탭 선택
   * 섹션에서 `Configuration` 단계에서 생성한 구성을 선택합니다

## 추가 리소스

* [Magento 웹 사이트, 스토어 및 보기](https://docs.magento.com/m2/ce/user_guide/stores/websites-stores-views.html)
* [AEM CIF 핵심 구성 요소 - 멀티 스토어/사이트 구성](https://github.com/adobe/aem-core-cif-components/wiki/configuration#multi-store--site-configuration)
* [다중 사이트 관리자 사용](https://docs.adobe.com/content/help/en/experience-manager-learn/sites/translation/multi-site-manager-feature-video-use.html)
* [컨텐츠 재활용: 다중 사이트 관리자 및 Live Copy](https://helpx.adobe.com/experience-manager/6-5/sites/administering/using/msm.html)
