---
title: Dynamic Media 회사 별칭 계정 구성
description: Dynamic Media에서 회사 별칭 계정을 구성하는 방법에 대해 알아봅니다.
contentOwner: Rick Brough
topic-tags: administering
content-type: reference
feature: Image Profiles
role: User,Admin
mini-toc-levels: 4
exl-id: 886063d4-71dd-48c8-a342-884ad2c111ca
source-git-commit: f7525b6b37e486a53791c2331dc6000e5248f8af
workflow-type: tm+mt
source-wordcount: '675'
ht-degree: 0%

---

# Dynamic Media 회사 별칭 계정 구성 정보 {#about-dm-alias-acct}

<!-- hide: yes
hidefromtoc: yes -->

<!-- >[!NOTE]
>
>This feature to create a Dynamic Media company alias account is in the Prerelease Channel for January 2022. See [Prerelease Channel documentation](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/release-notes/prerelease.html?lang=en#enable-prerelease) for information on how to enable the feature for your environment. The feature is generally available in the February 2022 release. -->

Dynamic Media URL 및 뷰어 포함 코드에는 회사 계정 이름이 포함되어 있습니다. 이 계정 이름은 Dynamic Media 프로비저닝 시 만들어졌습니다. 비즈니스가 인수 또는 리브랜딩을 거치거나 더 기억에 남는 이름을 사용하려는 경우가 있을 수 있습니다. 이러한 시나리오에서는 기본 제공되는 모든 URL 및 뷰어 포함 코드에서 회사 계정 이름을 수동으로 업데이트하는 것이 쉽지 않습니다. 또한 기존 Dynamic Media 저장소에 영향을 주거나 라이브 컨텐츠에 영향을 줄 수 있습니다. 이 문제를 해결하려면 Dynamic Media 회사 별칭 계정을 구성할 수 있습니다.

Dynamic Media 회사 별칭 계정은 사용자 인터페이스의 모든 기본 Dynamic Media URL 및 뷰어 포함 코드가 리브랜딩과 같은 비즈니스 컨텍스트에 대한 모든 업데이트를 반영하도록 합니다. Dynamic Media URL 및 뷰어 포함 코드는 새 회사 계정 이름을 반영하므로 별칭 계정은 SEO(검색 엔진 최적화)에도 긍정적인 영향을 줍니다.

Dynamic Media 회사 별칭 계정을 구성할 때에는 다음 사항에 유의하십시오.

* 의 기존 Dynamic Media URL 또는 뷰어 포함 코드 *live* 디지털 속성은 새 별칭 이름을 반영하도록 수동으로 업데이트해야 합니다. 그러나 원래 Dynamic Media 회사 이름이 있는 모든 URL 또는 뷰어 포함 코드는 기존 또는 새 에셋에서 계속 작동합니다.
* Dynamic Media 회사 별칭 계정 기능은 Experience Manager Assets 작성 모드 및 전달로 제한됩니다. 회사 별칭 이름은 Experience Manager Sites에서 작동하지 않습니다. WCM(웹 콘텐츠 관리) 구성 요소는 이 변경에 대해 업데이트되지 않습니다. 이러한 구성 요소는 Dynamic Media 에셋을 가져오기 위해 원래 Dynamic Media 회사 이름으로 계속 작동합니다.
* 에서 하나의 회사 별칭 계정만 설정할 수 있습니다. **[!UICONTROL Dynamic Media 구성 편집]** 페이지를 가리키도록 업데이트하는 중입니다. 그러나 지원 사례를 통해 회사 별칭 계정을 최대한 많이 만들 수 있으며 필요한 별칭 이름을 Dynamic Media URL 또는 뷰어 포함 코드에 수동으로 반영할 수 있습니다.
* 기본 제공 [캐시 무효화](/help/assets/dynamic-media/invalidate-cdn-cache-dynamic-media.md) Dynamic Media의 기능은 Cloud Services의 Dynamic Media 구성 페이지에 구성된 회사 및 회사 별칭 계정이 모두 있는 URL을 무효화합니다.
* 에서 회사 별칭 계정을 구성할 때 **[!UICONTROL Dynamic Media 구성 편집]** 페이지, 캐시 무효화에 성공하려면 의 URL을 무효화해야 합니다. *모두* 다음 **[!UICONTROL 회사]** 계정 및 **[!UICONTROL 회사 별칭]** 동시에 계정을 만드십시오.

참조: [Cloud Services에서 Dynamic Media 구성 만들기](/help/assets/dynamic-media/config-dm.md#configuring-dynamic-media-cloud-services)

## Dynamic Media 회사 별칭 계정 구성 {#configure-dm-alias-account}

먼저 지원 사례를 제출하여 Dynamic Media 회사 별칭 계정 구성을 시작합니다. 이 단계는 필수입니다.

1. [Admin Console을 사용하여 지원 사례 만들기](https://helpx.adobe.com/kr/enterprise/using/support-for-experience-cloud.html).
1. 지원 사례에 다음 정보를 입력합니다.

   * 사용할 Dynamic Media 회사 별칭 이름입니다. 이름에는 다음이 포함되어야 합니다. *전용* 문자(대소문자를 혼용할 수 있음), 숫자, 하이픈 및 밑줄.
   * 내 지역.
   * 유무 [규칙 세트](/help/assets/dynamic-media/using-rulesets-to-transform-urls.md) 는 대체 Dynamic Media 회사 계정 이름을 통해 Dynamic Media 콘텐츠를 제공하는 데 이전에 사용됩니다.

1. 지원에서 Dynamic Media 별칭 계정을 만든 후 Experience Manager as a Cloud Service 작성자 인스턴스에서 Experience Manager as a Cloud Service 로고를 선택하여 전역 탐색 콘솔에 액세스합니다.
1. 콘솔의 왼쪽에서 도구 아이콘을 선택한 다음 로 이동합니다. **[!UICONTROL Cloud Services > Dynamic Media 구성]**.
1. Dynamic Media 구성 브라우저 페이지의 왼쪽 창에서 을(를) 선택합니다 **[!UICONTROL 글로벌]** ( 왼쪽에 있는 폴더 아이콘을 선택하지 마십시오. **[!UICONTROL 글로벌]**). 그런 다음 을 선택합니다 **[!UICONTROL 편집]**.

   ![Dynamic Media 회사 별칭 텍스트 필드](/help/assets/assets-dm/dm-company-alias.png)

1. 다음에서 **[!UICONTROL Dynamic Media 구성 편집]** 페이지, **[!UICONTROL 회사 별칭]** 텍스트 필드에 이전에 지원 사례에서 지정한 Dynamic Media 별칭 계정 이름을 입력합니다.
1. 페이지의 오른쪽 상단에서 을 선택합니다. **[!UICONTROL 저장]**.
이제 Dynamic Media 회사 별칭 계정이 저장되고 활성화됩니다. 기존 및 새 에셋에 대한 모든 URL 및 뷰어 포함 코드는 이제 새 회사 별칭 이름을 반영합니다.