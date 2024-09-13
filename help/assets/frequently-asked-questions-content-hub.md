---
title: Content Hub 자주 묻는 질문(FAQ)
description: Content Hub에 대해 가장 자주 묻는 질문(FAQ) 중 일부에 대한 응답을 얻을 수 있습니다.
source-git-commit: 1d51a1e0858e975bc354ffd9c4b32c26aa1604af
workflow-type: tm+mt
source-wordcount: '1082'
ht-degree: 0%

---

# Content Hub 자주 묻는 질문 {#content-hub-frequently-asked-questions}

![Content Hub 자주 묻는 질문](assets/content-hub-faqs.png)

## Content Hub란? {#what-is-content-hub}

Content Hub은 Adobe Experience Manager Assetsas a Cloud Service 의 기능입니다.

Content Hub을 사용하면 보다 광범위한 팀이 직관적인 포털을 통해 연관성 있고 승인된 자산을 쉽게 검색하고 필요에 맞게 신속하게 조정할 수 있습니다.  또한 Content Hub은 이러한 사용자가 자산을 DAM에 업로드할 때 손쉽게 셀프서비스를 수행할 수 있는 수집 메커니즘을 제공합니다. 따라서 브랜드 일관성과 적절한 보호 조치를 준수하면서 컨텐츠 제작 속도를 향상시켜야 하는 기업의 요구를 직접 충족할 수 있습니다.

## Cloud Manager 프로그램/환경에서 Content Hub을 활성화할 수 없는 이유는 무엇입니까? {#cannot-enable-content-hub}

현재 Content Hub은 Assets 라이선스가 포함된 AEM Cloud Manager 프로덕션 프로그램에서만 사용할 수 있습니다. 활성화하기 위해 [Content Hub](/help/assets/deploy-content-hub.md#enable-content-hub)을(를) 클릭하면 배포되고 해당 프로그램에서 AEM의 작성자 프로덕션 환경과 연결됩니다. 자세한 내용 및 필수 구성 요소는 [Content Hub 배포](/help/assets/deploy-content-hub.md)를 참조하세요.

샌드박스 프로그램/작성자 프로덕션 환경에 대한 Content Hub의 조기 액세스 프로그램이 있습니다. 자세한 내용은 [샌드박스 프로그램 소개](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/introduction-sandbox-programs.md)를 참조하십시오. 조기 액세스 프로그램에 대한 자세한 내용은 Adobe 계정 팀에 문의하십시오.

Content Hub은 이 단계에서 비프로덕션 환경(단계, 개발 등)에 사용할 수 없습니다.

## 프로덕션 프로그램/환경에서 Content Hub을 활성화했는데 비활성화할 수 있습니까? {#can-i-disable-content-hub}

프로덕션 프로그램에서 Content Hub을 활성화하면 프로덕션 인프라의 일부로 배포됩니다. AEM Cloud Manager에서는 사용자 실수로 인한 프로덕션 사용의 위험을 최소화하기 위해 프로덕션 인프라를 제거하거나 비활성화할 수 없습니다.

Content Hub이 배포된 후 사용자에게 제공하지 않으려면 Admin Console의 Content Hub 제품 프로필에 사용자를 할당하지 마십시오. 자세한 내용은 [Content Hub 배포](/help/assets/deploy-content-hub.md#content-hub-instance-product-profile)를 참조하십시오.

## 프로덕션 프로그램/프로덕션 작성 환경에만 사용할 수 있는 경우 조직에서 Content Hub을 어떻게 평가할 수 있습니까? {#how-can-i-evaluate-content-hub}

Content Hub은 Adobe이 제공하고 유지 관리하는 기능이며 개발/스테이지/프로덕션을 통해 일반적인 유효성 검사가 필요한 사용자 지정 코드가 없습니다. 또한 사용자의 기능에 대한 액세스는 관리자가 완전히 제어하므로 모든 사용자에게 노출하지 않고도 평가할 수 있습니다.

AEM as a Cloud Service Assets에서 관리하는 사용자/프로덕션 컨텐츠에 영향을 주지 않고 Content Hub을 평가할 수 있습니다. 평가 절차는 다음과 같습니다.

* 프로덕션 환경(Cloud Manager 프로그램)에서 [Content Hub 사용](/help/assets/deploy-content-hub.md#enable-content-hub)
* [프로덕션 작성자의 AEM 관리자 사용자를 Content Hub 제품 프로필에 추가](/help/assets/deploy-content-hub.md#onboard-content-hub-administrator)합니다.
* AEM 관리자 [Content Hub 구성](/help/assets/configure-content-hub-ui-options.md)
* AEM 관리자 또는 AEM 프로덕션 작성자의 AEM 사용자 [Content Hub에 대한 많은 에셋을 승인](/help/assets/approve-assets-content-hub.md)합니다. DAM에서 프로덕션 콘텐츠를 변경하지 않으려면 AEM 작성자 인스턴스에 별도의 평가 폴더를 만들고 DAM의 일부 에셋을 업로드/태깅하거나 여기에 복사할 수 있습니다.
* Admin Console 관리자가 평가를 시작할 수 있도록 [선택한 사용자 몇 명](/help/assets/deploy-content-hub.md#onboard-content-hub-users)을(를) Content Hub 제품 프로필에 추가합니다.
* 평가가 완료되면 작성자 인스턴스의 AEM 사용자는 테스트 자산에서 승인을 제거하고 Content Hub에 대한 프로덕션 자산을 승인할 수 있습니다. 그런 다음 Admin Console 관리자는 Content Hub 및 승인된 콘텐츠에 액세스해야 하는 모든 사용자를 추가할 수 있습니다. 축하합니다. Content Hub이 지금 생방송입니다.

Adobe은 또한 스테이징 환경에서 Content Hub에 대한 조기 액세스 프로그램을 제공합니다. [내 Cloud Manager 프로그램/환경에서 Content Hub을 활성화할 수 없는 이유는 무엇입니까?자세한 내용은 ](#cannot-enable-content-hub)을(를) 참조하세요.

## Content Hub에 로그온하면 자산이 표시되지 않는 이유는 무엇입니까? {#no-assets-in-content-hub}

Assetsas a Cloud Service 에서 승인된 것으로 표시된 자산은 Content Hub에서 자동으로 사용할 수 있습니다. Content Hub에 로그온한 후 에셋을 볼 수 없는 경우 AEM as a Cloud Service 작성 환경을 사용하여 에셋을 승인하여 Content Hub에서 사용할 수 있도록 합니다. 자세한 내용은 [Content Hub에 대한 자산 승인](/help/assets/approve-assets-content-hub.md)을 참조하세요.

## Content Hub을 사용하여 직접 업로드하거나 Content Hub을 사용하여 Dropbox 또는 OneDrive 계정에서 가져온 자산이 표시되지 않는 이유는 무엇입니까? {#no-assets-uploaded-from-content-hub}

Content Hub을 사용하여 업로드한 에셋의 표시는 구성 사용자 인터페이스에서 사용할 수 있는 [자동 승인](/help/assets/configure-content-hub-ui-options.md#configure-import-options-content-hub) 토글을 활성화했는지 여부에 따라 달라집니다.

* **자동 승인** 전환이 활성화된 경우 Content Hub을 사용하여 업로드하는 에셋을 자동으로 사용할 수 있습니다.

* **자동 승인** 전환이 비활성화된 경우 Content Hub을 사용하여 업로드한 자산이 자동으로 표시되지 않습니다. 자산은 Assets as a Cloud Service 환경의 `hydrated-assets` 폴더에서 사용할 수 있습니다. 폴더로 이동한 다음 해당 에셋의 상태를 [일괄 편집](/help/assets/approve-assets-content-hub.md)하여 해당 에셋을 Content Hub에 표시할 수 있도록 `Approved`합니다.

## AEM as a Cloud Service 환경에서 Content Hub을 사용하여 업로드한 에셋을 빠르게 찾는 방법 {#find-uploaded-assets-on-aem-cloud}

AEM as a Cloud Service 환경에서 Content Hub을 사용하여 업로드한 에셋을 다음 방법으로 빠르게 찾을 수 있습니다.

1. `hydrated-assets` 폴더로 이동 중입니다.

1. **[!UICONTROL 자산 상태]** 필드에서 **[!UICONTROL 필터]**&#x200B;를 클릭하고 **[!UICONTROL 상태 없음]**&#x200B;을 설정하는 중입니다.

1. **[!UICONTROL 수정된 날짜]** 필드를 사용하여 자산을 정렬하는 중입니다.

## 에셋을 다시 혼합하여 새 변형을 만들 수 있도록 에셋 카드에서 Adobe Express을 사용하여 편집 옵션을 보는 것은 어떻습니까? {#edit-using-express-not-available}

에셋 카드에서 Adobe Express을 사용하여 편집 옵션을 보려면 에셋을 새 변형에 리믹스할 수 있는 권한이 있는 [Content Hub 사용자에 대한 권한과 함께 Adobe Express 권한이 있어야 합니다](#onboard-content-hub-users-add-assets). Adobe Express은 Adobe Experience Manager이 배포된 Adobe 관리 콘솔의 동일한 조직에 배포되어야 합니다.

## 조직의 브랜드 가이드라인이 홈 페이지에 링크로 표시되도록 Content Hub을 설정할 수 있습니까? {#content-hub-setup-brand-guidelines}

Content Hub 홈 페이지에서 표준 모든 Assets, 컬렉션 및 인사이트 탭 외에 사용자 지정 링크를 별도의 탭으로 추가할 수 있습니다. 설정 방법에 대한 자세한 내용은 [사용자 지정 링크](/help/assets/configure-content-hub-ui-options.md#configure-custom-links-content-hub)를 참조하세요.

## 기존 Brand Portal 고객을 Content Hub으로 마이그레이션할 계획이 있습니까? {#migration-brand-portal}

Adobe은 Adobe 지원 티켓을 생성하여 사용할 수 있는 Brand Portal에서 Content Hub으로의 마이그레이션 지원을 제공합니다.

## Content Hub에서 제품 설정/구성 옵션이 표시되지 않는 이유는 무엇입니까? {#ui-configuration-option-missing}

[구성 사용자 인터페이스](/help/assets/configure-content-hub-ui-options.md)에 액세스하려면 [Content Hub 관리자](/help/assets/deploy-content-hub.md##onboard-content-hub-administrator)여야 합니다. Adobe Admin Console의 프로덕션 작성자 인스턴스에서 AEM 관리자 제품 프로필에 할당되어 구성 옵션이 표시되지 않는 경우 AEM 관리자 제품 프로필의 이름이 바뀌지 않았는지 확인하십시오. 자세한 내용은 [AEM as a Cloud Service 팀 및 제품 프로필](/help/onboarding/aem-cs-team-product-profiles.md)을 참조하세요.


