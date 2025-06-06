---
title: Cloud Manager 2025.6.0 릴리스 정보
description: Adobe Experience Manager as a Cloud Service의 Cloud Manager 2025.6.0 릴리스에 대해 알아봅니다.
feature: Release Information
role: Admin
exl-id: 24d9fc6f-462d-417b-a728-c18157b23bbe
source-git-commit: 52c8745d3a3cc4bc41003a258a85a817e7ccb48b
workflow-type: tm+mt
source-wordcount: '954'
ht-degree: 57%

---

# Adobe Experience Manager as a Cloud Service의 Cloud Manager 2025.6.0 릴리스 정보 {#release-notes}

<!-- https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+2025.03.0+Release -->

AEM (Adobe Experience Manager) as a Cloud Service의 Cloud Manager 2025.6.0 릴리스에 대해 알아봅니다.

또한 [최신 Adobe Experience Manager as a Cloud Service 릴리스 정보](/help/release-notes/release-notes-cloud/release-notes-current.md)도 살펴보십시오.

## 릴리스 일자 {#release-date}

AEM as a Cloud Service의 Cloud Manager 2025.6.0 릴리스 일자는 2025년 6월 5일 금요일입니다.

다음 릴리스는 2025년 7월 10일 금요일에 예정되어 있습니다.

## 새로운 기능 {#what-is-new}

* **라이선스 대시보드에 Edge Delivery Services 라이선스가 포함됨**

  이제 Edge Delivery Services 라이선스 사용량이 라이선스 대시보드에 표시되므로 자격 및 상태를 보다 명확하게 확인할 수 있습니다. <!-- CMGR-67686 -->

  ![라이선스 대시보드](/help/implementing/cloud-manager/assets/license-dashboard.png)

  [라이선스 대시보드](/help/implementing/cloud-manager/license-dashboard.md)를 참조하세요.

* **Edge Delivery 사이트 구성 업데이트됨**

  **리포지토리 URL** 대신 **Edge Delivery 원본**&#x200B;을 요청하여 Edge Delivery 사이트를 추가하는 흐름을 단순화하여 온보딩을 수행하고 보다 직관적이고 빠르게 설정합니다. <!-- CMGR-67686 -->

  ![Edge Delivery 사이트 추가 대화 상자](/help/implementing/cloud-manager/release-notes/assets/add-edge-delivery-site.png)

  [Edge Delivery 사이트 추가](/help/implementing/cloud-manager/edge-delivery/add-edge-delivery-site.md)를 참조하십시오.

* **파이프라인 즐겨찾기**

  이번 릴리스에서는 Cloud Manager에서 즐겨찾는 파이프라인을 고정할 수 있는 기능을 도입하여 특정 파이프라인을 즐겨찾기로 표시하여 **파이프라인** 페이지의 목록 맨 위에 나타나도록 할 수 있습니다. 이 향상된 기능을 통해 자주 액세스하는 파이프라인을 더 쉽게 찾고 실행할 수 있습니다. <!-- CMGR-68293 -->

  ![즐겨찾기로 표시된 파이프라인](/help/implementing/cloud-manager/release-notes/assets/pipeline-favorites.png) *즐겨찾기로 표시된 파이프라인 두 개.*

  [파이프라인 즐겨찾기 표시](/help/implementing/cloud-manager/configuring-pipelines/managing-pipelines.md#pipeline-favorites)를 참조하십시오.


## 얼리 어답터 프로그램 {#early-adoption}

Cloud Manager의 얼리 어답터 프로그램에 참여하면 정식 출시 전에 새로운 기능에 대한 전용 액세스 권한을 얻을 수 있습니다.

현재 제공되는 얼리 어답터 기회는 다음과 같습니다.


### 전문화된 테스트 환경 {#specialized-test-environment}

이제 Cloud Manager에서 **전문 테스트 환경**&#x200B;이라는 새 환경 형식을 추가할 수 있습니다. 환경은 팀이 라이브로 전환하기 전에 프로덕션에 가까운 조건에서 기능을 확인할 수 있도록 설계되었습니다. 이 환경 유형은 *프로덕션 + 단계*, *개발* 또는 *신속한 개발* 환경과 다르며 고급 유효성 검사 시나리오를 실행하기 위한 집중 공간을 제공합니다.

[특수 테스트 환경 추가](/help/implementing/cloud-manager/specialized-test-environment.md)를 참조하십시오.

![특수 테스트 환경 라디오 단추가 선택된 환경 추가 대화 상자](/help/implementing/cloud-manager/release-notes/assets/specialized-test-environment.png)

이 새로운 기능을 테스트하고 피드백을 공유하려면 Adobe ID과 연결된 전자 메일 주소에서 [grp-earlyadopter_cs_advtestenvironment@adobe.com](mailto:grp-earlyadopter_cs_advtestenvironment@adobe.com)(으)로 전자 메일을 보내세요.


### 이제 Azure DevOps에 대한 지원을 통해 나만의 Git(BYOG) 가져오기 {#gitlab-bitbucket-azure-vsts}

<!-- BOTH CS & AMS -->

이제 고객은 Azure DevOps Git 저장소를 Cloud Manager에 온보딩할 수 있으며, 최신 Azure DevOps와 이전 VSTS(Visual Studio Team Services) 저장소가 모두 지원됩니다.

* Edge Delivery Services 사용자의 경우 온보딩된 저장소를 사용하여 사이트 코드를 동기화하고 배포할 수 있습니다.
* AEM as a Cloud Service와 Adobe Managed Services(AMS) 사용자의 경우 저장소를 전체 스택 파이프라인과 프론트엔드 파이프라인 모두에 연결할 수 있습니다.

추가 파이프라인 유형과 코드 품질 파이프라인을 통한 가져오기 요청 유효성 검사도 곧 지원할 예정입니다.

[Cloud Manager에서 외부 저장소 추가](/help/implementing/cloud-manager/managing-code/external-repositories.md)를 참조하십시오.

![저장소 추가 대화 상자](/help/implementing/cloud-manager/release-notes/assets/azure-repo.png)

이 새로운 기능을 테스트하고 피드백을 공유하는 데 관심이 있으시면 Adobe ID와 연결된 이메일 주소로 [Grp-CloudManager_BYOG@adobe.com](mailto:grp-cloudmanager_byog@adobe.com)에 이메일을 보내 주십시오. 사용하려는 Git 플랫폼과 비공개/공개 또는 기업 저장소 구조인지 여부를 반드시 포함해야 합니다.


**BYOG에 대해 자주 묻는 질문**

| 질문 | 답변 |
|---|---|
| *필요한 경우 프로젝트를 Adobe 관리 Git 저장소로 다시 전환하려면 어떻게 해야 합니까?* | 다시 전환하는 것은 간단합니다. [파이프라인을 업데이트](/help/implementing/cloud-manager/configuring-pipelines/managing-pipelines.md)하여 Adobe 저장소를 가리키도록 설정하고 외부 저장소가 더 이상 필요하지 않으면 이를 제거합니다. |
| *다양한 환경(예: 비프로덕션 환경과 프로덕션 환경)에 대해 서로 다른 저장소를 구성한 후 먼저 비프로덕션 환경에서 테스트할 수 있습니까?* | 예, 각기 다른 환경에 맞게 서로 다른 저장소를 구성할 수 있습니다. 예를 들어 개발 또는 코드 품질 파이프라인은 외부 저장소를 가리킬 수 있지만, 프로덕션 파이프라인은 Adobe 저장소에 연결된 상태를 유지합니다. 이 구성 중에는 두 저장소 간의 동기화 작업이 활성 상태로 유지되는지 확인하십시오. |
| *IP 허용 목록과 같은 기존 설정은 계속 작동합니까?* | 예, 기존 IP 허용 목록은 평소처럼 계속 작동합니다. 그러나 외부 Git 저장소가 방화벽으로 보호되는 경우 필요한 [Adobe IP 주소를 허용 목록에 추가해야 합니다](/help/implementing/cloud-manager/ip-allow-lists/introduction.md). |
| *모든 GitLab 저장소 URL이 작동합니까? 사용 중인 저장소 URL이 `https://gitlab_dedicated_url.com/path/repo-name.git` 형식을 따릅니다. 이 형식은 설명서에 나와 있는 예시와 다릅니다.* | 예, API V3 또는 V4를 지원하는 모든 GitLab 저장소가 지원되며, 여기에는 [Cloud Manager에서 외부 저장소 추가](/help/implementing/cloud-manager/managing-code/external-repositories.md)에 설명된 것과 같은 자체 호스팅 GitLab URL(`https://git-vendor-name.com/org-name/repo-name.git`)이 포함됩니다. |


#### Access 토큰 관리{#manage-access-tokens}

Cloud Manager에서 **액세스 토큰 관리**&#x200B;를 사용하여 GitHub Enterprise, GitLab, Bitbucket 및 Azure DevOps와 같은 외부 BYOG 저장소와 연결된 액세스 토큰을 보고, 이름을 바꾸고, 삭제합니다.

[액세스 토큰 관리](/help/implementing/cloud-manager/managing-code/manage-access-tokens.md)를 참조하세요.

이 새로운 기능을 테스트하고 피드백을 공유하려면 Adobe ID과 연결된 전자 메일 주소에서 [Grp-CloudManager_BYOG@adobe.com](mailto:grp-cloudmanager_byog@adobe.com)(으)로 전자 메일을 보내세요.


### Edge Delivery 구성 파이프라인 추가 {#add-eds-pipeline}

이제 Edge Delivery Services를 사용하여 구축한 사이트에서도 구성 파이프라인이 지원되며 Cloud Service 환경 그 이상으로 기능이 확장되었습니다. 해당되는 경우 **구성 파이프라인**&#x200B;을 사용하여 트래픽 필터링 규칙 및 웹 애플리케이션 방화벽(WAF) 구성과 같은 설정을 관리할 수 있습니다. [지원되는 구성](/help/operations/config-pipeline.md#configurations)을 참조하십시오.

![파이프라인 추가 드롭다운 목록에 Edge Delivery 파이프라인 추가](/help/implementing/cloud-manager/release-notes/assets/edge-delivery-pipeline-add.png) *프로그램 개요&#x200B;**페이지,**파이프라인&#x200B;**카드에서 Edge Delivery 파이프라인을 추가***

![Edge Delivery 파이프라인 추가 대화 상자](/help/implementing/cloud-manager/release-notes/assets/edge-delivery-pipeline-add-dialogbox.png) *Edge Delivery 파이프라인 추가 대화 상자*

이 새로운 기능을 테스트하고 피드백을 공유하는 데 관심이 있으시면 Adobe ID와 연결된 이메일 주소로 [grp-aemeds-config-pipeline-adopter@adobe.com](mailto:grp-aemeds-config-pipeline-adopter@adobe.com)에 이메일을 보내주십시오.


## 버그 수정

* 이전에 `HIBERNATED`(으)로 표시된 샌드박스 환경은 더 이상 해당 상태로 유지되지 않으므로 파이프라인 실행 또는 배포가 예상대로 진행될 수 있습니다. <!-- CMGR-67705 -->
* 이제 AEM Cloud Manager은 고객 아티팩트를 가져올 때 409 오류(충돌)로 인해 발생한 Maven 빌드 오류를 고객 실패 로 올바르게 매핑합니다. 이 변경 사항은 내부 오류와 고객 환경 설정과 관련된 문제를 구분하여 오류 메시지를 개선합니다. <!-- CMGR-66673 -->


<!-- ## Known issues {#known-issues} -->

