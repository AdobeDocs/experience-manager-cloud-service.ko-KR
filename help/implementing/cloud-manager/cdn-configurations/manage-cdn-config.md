---
title: 도메인 매핑 관리
description: Cloud Manager을 사용하여 Edge Delivery 사이트 또는 Cloud Manager 환경에 대한 CDN 구성을 편집 및 업데이트하거나 삭제하는 방법에 대해 알아봅니다.
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
exl-id: 2ec16c91-0195-4732-a26d-ac223e10afb9
source-git-commit: 41155a724f48ad28a12aac615a3e9a13bb3afa26
workflow-type: tm+mt
source-wordcount: '783'
ht-degree: 8%

---

# 도메인 매핑 관리 {#manage-cdn-configurations}

Cloud Manager을 사용하여 Edge Delivery 사이트 또는 Cloud Manager 환경에 대한 CDN 구성을 편집하거나 삭제하는 방법에 대해 알아봅니다.

## 도메인 매핑 페이지에서 CDN 구성 편집 {#edit-cdn}

Adobe Cloud Manager에서는 몇 가지 이유로 환경 계층(게시 또는 미리보기)과 SSL 인증서를 비롯한 CDN(Content Delivery Network) 구성을 편집할 수 있습니다.

* **환경 변경**: 계층을 조정하면 라이브 프로덕션(게시) 또는 테스트(미리보기) 여부에 관계없이 CDN 설정을 올바른 환경과 일치시킬 수 있습니다.
* **보안 개선 사항**: 인증서를 업데이트하거나 규정 준수 및 보안 요구 사항을 해결할 때 다른 SSL 인증서를 선택해야 합니다.
* **성능 최적화**: 구성을 편집하면 변화하는 운영 요구 사항에 따라 콘텐츠를 게재하기 위한 올바른 CDN 설정이 보장됩니다.

기존 구성을 완전히 제거하지 않고 구성을 편집할 수 있습니다. 변경 사항은 선택한 환경(예: 스테이징 또는 프로덕션)에 적용되며, 콘텐츠 전달 및 보안 방식에 영향을 줄 수 있습니다.

이 작업을 완료하려면 사용자가 **비즈니스 소유자** 또는 **배포 관리자** 역할의 멤버여야 합니다.

**도메인 매핑 페이지에서 CDN 구성을 편집하려면:**

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)에서 Cloud Manager에 로그인한 다음 적절한 조직과 프로그램을 선택합니다.
1. 왼쪽 메뉴에서 **서비스** 아래의 ![소셜 네트워크 아이콘](https://spectrum.adobe.com/static/icons/workflow_18/Smock_SocialNetwork_18_N.svg) **도메인 매핑**&#x200B;을 클릭합니다.
1. **도메인 매핑** 테이블에서 업데이트하려는 CDN 구성이 있는 행 끝에 있는 ![추가 아이콘](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg)을 클릭합니다.

1. 드롭다운 메뉴에서 **편집**&#x200B;을 클릭합니다.

1. **CDN 구성 편집** 대화 상자에서 각 드롭다운 목록에 있는 옵션을 하나 이상 설정합니다.

   대화 상자에 표시되는 옵션은 **Adobe 관리 CDN**&#x200B;을 사용하는지 또는 **기타 CDN 공급자**(고객 관리 CDN)를 사용하는지에 따라 다릅니다.

1. **업데이트**&#x200B;를 클릭합니다.

   편집된 CDN의 상태가 변경 사항을 반영하도록 **도메인 매핑** 테이블에서 업데이트됩니다.


## 환경 페이지에서 CDN 구성 편집

**환경** 페이지에서 CDN 구성을 편집하는 단계는 [도메인 매핑 페이지에서 CDN 구성을 편집](#edit-cdn)하는 단계와 거의 동일하지만 시작 지점이 다릅니다.

**환경 페이지에서 CDN 구성을 편집하려면:**

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)에서 Cloud Manager에 로그인한 다음 적절한 조직과 프로그램을 선택합니다.

1. 왼쪽 메뉴에서 ![데이터 아이콘](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Data_18_N.svg) **환경**&#x200B;을 클릭합니다.

1. **환경** 페이지에서 원하는 환경을 선택하십시오.

1. 환경 세부 정보 페이지의 도메인 매핑 그룹에서 편집할 CDN 구성에 해당하는 ![추가 아이콘](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg)을 클릭합니다.

1. 팝업 메뉴에서 **편집**&#x200B;을 클릭합니다.

1. **CDN 구성 편집** 대화 상자에서 각 드롭다운 목록에 있는 옵션을 하나 이상 설정합니다.

   대화 상자에 표시되는 옵션은 **Adobe 관리 CDN**&#x200B;을 사용하는지 또는 **기타 CDN 공급자**(고객 관리 CDN)를 사용하는지에 따라 다릅니다.

1. **업데이트**&#x200B;를 클릭합니다.

<!-- 
## Go live readiness: Configure DNS settings for a custom domain {#go-live-readiness} 

Before a custom domain can serve traffic in Adobe Cloud Manager, you must complete DNS configuration with your DNS provider. After deploying a domain mapping and clicking **Go live**, Cloud Manager displays a dialog box that guides you through the DNS record setup process. You have the option to go live by adding either a CNAME record type or an A record type representing Fastly's IPs, simplifying domain routing. This ability eliminates the restriction of relying solely on CNAME records for domain setup with Fastly.

MAYBE There is support for A record types to improve Go Live readiness for domains using CDN configurations in AEM Cloud Manager. MAYBE

See also [APEX record](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md#adobe-managed-cert-cname-record#adobe-managed-cert-apex-record) and [CNAME record](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md#adobe-managed-cert-cname-record).

**To configure Go live readiness:**

1. Log into Cloud Manager at [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) and select the appropriate organization and program.

1. In the left side menu, under **Services**, click ![Social network icon](https://spectrum.adobe.com/static/icons/workflow_18/Smock_SocialNetwork_18_N.svg) **Domain Mappings**.

1. In the Domain Mappings table, click **Go live** near the end of a row that corresponds to a CDN whose Go Live readiness you want to configure. 

1. In the Go live readiness dialog box, do one of the following:

    | Configure  | Steps |
    | --- | --- |
    | A RECORD | Recommended for root domains like `example.com`<br><ol><li>Log in to your DNS service provider's portal.<li>Go to the DNS Records section.<li>Create an A record to point to all the listed IP addresses.<li>In the Go live readiness dialog box, click **OK**.<li>In the Domain Mappings table, under the **Status** column, click ![Refresh icon](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Refresh_18_N.svg).<br>The status is updated to **Verified** when the resolution is complete.</li></ol> |
    | CNAME | Recommended for custom domains like `www.example.com`<br><ol><li>Log in to your DMS service provider's portal.<li>Go to the DNS Records section.<li>Map [cdn.adobeaemcloud.com](http://cdn.adobeaemcloud.com/) (CNAME record) in the DNS record of the DNS service provider (your custom domain). This mapping ensures that requests received at the custom domain are redirected to Adobe's CDN.<li>In the **Go live readiness** dialog box, click **OK** to save the record.<br>Wait for DNS propogation (may take several minutes to a few hours). When the **[!UICONTROL Status]** column in the Domamin Mappings table updates to **[!UICONTROL Verified]**, the custom domain is ready to use. You may need to click ![Refresh icon](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Refresh_18_N.svg) to refresh the status.</li></ol> | 
    
-->

## CDN 구성 삭제 {#delete-cdn}

Cloud Manager에서 Adobe 관리 또는 고객 관리 CDN 구성을 삭제하면 연결된 도메인의 라우팅 및 SSL 인증서 설정이 제거됩니다. 도메인은 트래픽 전달에 더 이상 CDN을 사용하지 않으며, CDN에서 제공하는 보안 또는 성능 개선 사항은 손실됩니다. 삭제된 CDN을 다시 추가하든 아니면 새 CDN을 추가하든 새 구성이 설정될 때까지 서비스가 중단될 수 있습니다.

이 작업을 완료하려면 사용자가 **비즈니스 소유자** 또는 **배포 관리자** 역할의 멤버여야 합니다.

**CDN 구성을 삭제하려면:**

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)에서 Cloud Manager에 로그인한 다음 적절한 조직과 프로그램을 선택합니다.

1. 왼쪽 메뉴에서 **서비스** 아래의 ![소셜 네트워크 아이콘](https://spectrum.adobe.com/static/icons/workflow_18/Smock_SocialNetwork_18_N.svg) **도메인 매핑**&#x200B;을 클릭합니다.

1. 도메인 매핑 테이블에서 제거할 CDN에 해당하는 행 끝에 있는 ![추가 아이콘](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg)을 클릭한 다음 **삭제**&#x200B;를 클릭합니다.

1. **CDN 구성 삭제** 대화 상자에서 **삭제**&#x200B;를 클릭합니다.

1. 사이트의 CDN 제거를 확인하려면 **삭제**&#x200B;를 다시 클릭합니다.


## 환경 페이지에서 CDN 구성 삭제

**환경** 페이지에서 CDN 구성을 삭제하는 단계는 [도메인 매핑 페이지](#edit-cdn)에서 CDN 구성을 삭제하는 단계와 거의 동일하지만 시작 지점이 다릅니다.

**환경 페이지에서 CDN 구성을 삭제하려면:**

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)에서 Cloud Manager에 로그인한 다음 적절한 조직과 프로그램을 선택합니다.

1. 왼쪽 메뉴에서 ![데이터 아이콘](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Data_18_N.svg) **환경**&#x200B;을 클릭합니다.

1. **환경** 페이지에서 원하는 환경을 선택하십시오.

1. 환경 세부 정보 페이지의 **도메인 매핑** 그룹화에서 제거할 CDN 구성에 해당하는 ![추가 아이콘](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg)을 클릭한 다음 **삭제**&#x200B;를 클릭합니다.

1. **CDN 구성 삭제** 대화 상자에서 **삭제**&#x200B;를 클릭합니다.

1. 사이트의 CDN 제거를 확인하려면 **삭제**&#x200B;를 다시 클릭합니다.
