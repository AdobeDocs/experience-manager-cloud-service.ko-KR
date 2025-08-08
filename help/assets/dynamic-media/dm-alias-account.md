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
source-git-commit: bc422429d4a57bbbf89b7af2283b537a1f516ab5
workflow-type: tm+mt
source-wordcount: '671'
ht-degree: 0%

---

# Dynamic Media 회사 별칭 계정 구성 정보 {#about-dm-alias-acct}

<!-- hide: yes
hidefromtoc: yes 
-->

<!-- 
>[!NOTE]
>
>This feature to create a Dynamic Media company alias account is in the Prerelease Channel for January 2022. See [Prerelease Channel documentation](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/release-notes/prerelease.html?lang=en#enable-prerelease) for information on how to enable the feature for your environment. The feature is generally available in the February 2022 release. 
-->

Dynamic Media URL 및 뷰어 포함 코드에는 회사 계정 이름이 포함되어 있습니다. 이 계정 이름은 Dynamic Media 프로비저닝 시 만들어졌습니다. 비즈니스가 인수 또는 리브랜딩을 거치거나 더 기억에 남는 이름을 사용하려는 경우가 있을 수 있습니다. 이러한 시나리오에서는 기본 제공되는 모든 URL 및 뷰어 포함 코드에서 회사 계정 이름을 수동으로 업데이트하는 것이 쉽지 않습니다. 또한 기존 Dynamic Media 저장소에 영향을 주거나 라이브 컨텐츠에 영향을 줄 수 있습니다. 이 문제를 해결하려면 Dynamic Media 회사 별칭 계정을 구성할 수 있습니다.

Dynamic Media 회사 별칭 계정은 사용자 인터페이스의 모든 기본 Dynamic Media URL 및 뷰어 포함 코드가 리브랜딩과 같은 비즈니스 컨텍스트에 대한 모든 업데이트를 반영하도록 합니다. Dynamic Media URL 및 뷰어 포함 코드는 새 회사 계정 이름을 반영하므로 별칭 계정 은 SEO(검색 엔진 최적화)에도 긍정적인 영향을 줍니다.

Dynamic Media 회사 별칭 계정을 구성할 때는 다음 사항에 유의하십시오.

* *live* 디지털 속성의 기존 Dynamic Media URL 또는 뷰어 포함 코드를 수동으로 업데이트하여 새 별칭 이름을 반영해야 합니다. 그러나 원래 Dynamic Media 회사 이름이 있는 모든 URL 또는 뷰어 포함 코드는 기존 또는 새 에셋에 대해 계속 작동합니다.
* Dynamic Media 회사 별칭 계정 기능은 Experience Manager Assets 작성 모드 및 제공으로 제한됩니다. 회사 별칭 이름은 Experience Manager Sites에서 작동하지 않습니다. WCM(웹 콘텐츠 관리) 구성 요소는 이 변경에 대해 업데이트되지 않습니다. 이러한 구성 요소는 Dynamic Media 에셋을 가져오기 위해 원래 Dynamic Media 회사 이름으로 계속 작동합니다.
* **[!UICONTROL Dynamic Media 구성 편집]** 페이지에서 회사 별칭 계정을 하나만 설정할 수 있습니다. 그러나 지원 사례를 통해 회사 별칭 계정을 최대한 많이 만들 수 있으며 필요한 별칭 이름을 Dynamic Media URL 또는 뷰어 포함 코드에 수동으로 반영할 수 있습니다.
* Dynamic Media의 기본 [캐시 무효화](/help/assets/dynamic-media/invalidate-cdn-cache-dynamic-media.md) 기능은 클라우드 서비스의 Dynamic Media 구성 페이지에 구성된 회사 및 회사 별칭 계정이 모두 있는 URL을 무효화합니다.
* **[!UICONTROL Dynamic Media 구성 편집]** 페이지에서 회사 별칭 계정을 구성할 때 캐시 무효화에 성공하려면 *Company* 계정과 **[!UICONTROL Company 별칭]** 계정의 **[!UICONTROL 모두]**&#x200B;에 대한 URL을 동시에 무효화해야 합니다.

[클라우드 서비스에서 Dynamic Media 구성 만들기](/help/assets/dynamic-media/config-dm.md#configuring-dynamic-media-cloud-services)도 참조하세요.

## Dynamic Media 회사 별칭 계정 구성 {#configure-dm-alias-account}

먼저 지원 사례를 제출하여 Dynamic Media 회사 별칭 계정 구성을 시작합니다. 이 단계는 필수입니다.

1. [Admin Console을 사용하여 지원 사례를 만듭니다](https://helpx.adobe.com/kr/enterprise/using/support-for-experience-cloud.html).
1. 지원 사례에 다음 정보를 제공하십시오.

   * 사용할 Dynamic Media 회사 별칭 이름입니다. 이름에는 *문자*&#x200B;개(대/소문자를 혼용할 수 있음), 숫자, 하이픈 및 밑줄을 포함해야 합니다.
   * 내 지역.
   * 대체 Dynamic Media 회사 계정 이름을 통해 Dynamic Media 콘텐츠 제공을 위해 이전에 [규칙 세트](/help/assets/dynamic-media/using-rulesets-to-transform-urls.md)을(를) 사용하고 있는지 여부.

1. 지원에 의해 Dynamic Media 별칭 계정이 생성되면 Experience Manager as a Cloud Service 작성자 인스턴스에서 Experience Manager as a Cloud Service 로고를 선택하여 전역 탐색 콘솔에 액세스합니다.
1. 콘솔 왼쪽에서 도구 아이콘을 선택한 다음 **[!UICONTROL 클라우드 서비스 > Dynamic Media 구성]**(으)로 이동합니다.
1. Dynamic Media 구성 브라우저 페이지의 왼쪽 창에서 **[!UICONTROL 전역]**&#x200B;을(를) 선택합니다(**[!UICONTROL 전역]** 왼쪽에 있는 폴더 아이콘을 선택하지 마십시오). **[!UICONTROL 편집]**&#x200B;을 선택합니다.

   ![Dynamic Media 회사 별칭 텍스트 필드](/help/assets/assets-dm/dm-company-alias.png)

1. **[!UICONTROL Dynamic Media 구성 편집]** 페이지의 **[!UICONTROL 회사 별칭]** 텍스트 필드에 이전에 지원 사례에서 지정한 Dynamic Media 별칭 계정 이름을 입력하십시오.
1. 페이지의 오른쪽 상단에서 **[!UICONTROL 저장]**을 선택합니다.
이제 Dynamic Media 회사 별칭 계정이 저장되고 활성화되었습니다. 기존 및 새 자산에 대한 모든 URL 및 뷰어 포함 코드가 이제 새 회사 별칭 이름을 반영합니다.