---
title: CDN 구성 관리
description: Cloud Manager을 사용하여 Edge Delivery 사이트 또는 Cloud Manager 환경에 대한 CDN 구성을 편집 및 업데이트하거나 삭제하는 방법에 대해 알아봅니다.
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: ff8c7fb21b4d8bcf395d28c194a7351281eef45b
workflow-type: tm+mt
source-wordcount: '477'
ht-degree: 7%

---


# CDN(Content Delivery Network) 구성 관리 {#manage-cdn-configurations}

Cloud Manager을 사용하여 Edge Delivery 사이트 또는 Cloud Manager 환경에 대한 CDN 구성을 편집 및 업데이트하거나 삭제하는 방법에 대해 알아봅니다.

## CDN 구성 편집 {#edit-cdn}

Cloud Manager Adobe에서 몇 가지 이유로 환경 계층(Publish 또는 미리보기)과 SSL 인증서를 포함한 CDN 구성을 편집할 수 있습니다.

* **환경 변경**: 계층을 조정하면 라이브 프로덕션(Publish) 또는 테스트(미리보기) 여부에 관계없이 CDN 설정을 올바른 환경과 일치시킵니다.
* **보안 개선 사항**: 인증서를 업데이트하거나 규정 준수 및 보안 요구 사항을 해결할 때 다른 SSL 인증서를 선택해야 합니다.
* **성능 최적화**: 구성을 편집하면 변화하는 운영 요구 사항에 따라 콘텐츠를 게재하기 위한 올바른 CDN 설정이 보장됩니다.

기존 구성을 완전히 제거하지 않고 구성을 편집할 수 있습니다. 변경 사항은 선택한 환경(예: 스테이징 또는 프로덕션)에 적용되며, 콘텐츠 전달 및 보안 방식에 영향을 줄 수 있습니다.

이 작업을 완료하려면 사용자가 **비즈니스 소유자** 또는 **배포 관리자** 역할의 멤버여야 합니다.

**CDN 구성을 편집하려면:**

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)에서 Cloud Manager에 로그인한 다음 적절한 조직과 프로그램을 선택합니다.
1. 사이드 패널의 **서비스**&#x200B;에서 ![소셜 네트워크 아이콘](https://spectrum.adobe.com/static/icons/workflow_18/Smock_SocialNetwork_18_N.svg) **CDN 구성**&#x200B;을 클릭합니다.
1. **CDN 구성** 테이블에서 업데이트하려는 CDN 구성이 있는 행 끝에 있는 ![추가 아이콘](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg)을 클릭합니다.

   ![CDN 구성 편집](/help/implementing/cloud-manager/assets/cdn-config-edit.png)

1. 드롭다운 메뉴에서 **편집**&#x200B;을 클릭합니다.
1. **CDN 구성 편집** 대화 상자에서 각 드롭다운 목록에 있는 옵션을 하나 이상 설정합니다.

   대화 상자에 표시되는 옵션은 Adobe 관리 CDN 또는 고객 관리 CDN을 사용 하는지에 따라 달라질 수 있습니다.

1. **업데이트**&#x200B;를 클릭합니다.

   편집된 CDN의 상태가 변경 사항을 반영하도록 **CDN 구성** 표에 업데이트됩니다.

<!-- ## ALTERNATE METHOD FOR EDITING A CDN CONFIGURATION from the Environments page
    
    The steps for adding a custom domain name from the **Environments** page are the same as when [adding a custom domain name from the Domain Settings page](#adding-cdn-settings), but the entry point differs. Follow these steps to add a custom domain name from the **Environments** page.
    
    1. Log into Cloud Manager at [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) and select the appropriate organization and program.
    
    1. Navigate to the **Environments Detail** detail page for the environment of interest.
    
       ![Entering domain name on the Environment Details page](/help/implementing/cloud-manager/assets/cdn/environments-cdn-config.png)
    
    1. Use the **Domain Names** table to submit the custom domain name.
    
       1. Enter the custom domain name.
       1. Select the SSL certificate associated with this name from the drop-down list.
       1. Click ![Add icon](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Add_18_N.svg) **Add**.
    
       ![Add a custom domain name](/help/implementing/cloud-manager/assets/cdn/cdn-create3.png)
    
    1. The **Add domain name** dialog box opens to the **Domain Name** tab. Continue as you would for [adding a custom domain name from the Domain Settings page](#adding-cdn-settings). -->

## CDN 구성 삭제 {#delete-cdn}

Adobe Cloud Manager에서 Adobe 관리 또는 고객 관리 CDN 구성을 삭제하면 연결된 도메인의 라우팅 및 SSL 인증서 설정이 제거됩니다. 도메인은 트래픽 전달에 더 이상 CDN을 사용하지 않으며, CDN에서 제공하는 보안 또는 성능 개선 사항은 손실됩니다. 삭제된 CDN을 다시 추가하든 아니면 새 CDN을 추가하든 새 구성이 설정될 때까지 서비스가 중단될 수 있습니다.

이 작업을 완료하려면 사용자가 **비즈니스 소유자** 또는 **배포 관리자** 역할의 멤버여야 합니다.

**CDN 구성을 삭제하려면:**

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)에서 Cloud Manager에 로그인한 다음 적절한 조직과 프로그램을 선택합니다.

1. 왼쪽 탐색 패널의 **서비스**&#x200B;에서 **CDN 구성**&#x200B;을 클릭합니다.

1. CDN 구성 테이블에서 제거할 CDN이 있는 행의 끝에 있는 생략 부호를 클릭합니다.

   ![CDN 구성 삭제](/help/implementing/cloud-manager/assets/cdn-config-delete.png)

1. **삭제**&#x200B;를 클릭합니다.
1. 사이트의 CDN 제거를 확인하려면 **삭제**&#x200B;를 다시 클릭합니다.


