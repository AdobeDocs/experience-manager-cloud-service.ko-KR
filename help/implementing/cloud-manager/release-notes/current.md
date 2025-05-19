---
title: Cloud Manager 2025.5.0 릴리스 정보
description: Adobe Experience Manager as a Cloud Service의 Cloud Manager 2025.5.0 릴리스에 대해 알아봅니다.
feature: Release Information
role: Admin
exl-id: 24d9fc6f-462d-417b-a728-c18157b23bbe
source-git-commit: 8696cf8a7e7cfc439450b34fa6fda10b38cd415e
workflow-type: tm+mt
source-wordcount: '640'
ht-degree: 24%

---

# Adobe Experience Manager as a Cloud Service의 Cloud Manager 2025.5.0 릴리스 정보 {#release-notes}

<!-- https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+2025.03.0+Release -->

AEM (Adobe Experience Manager) as a Cloud Service의 Cloud Manager 2025.5.0 릴리스에 대해 알아봅니다.

또한 [최신 Adobe Experience Manager as a Cloud Service 릴리스 정보](/help/release-notes/release-notes-cloud/release-notes-current.md)도 살펴보십시오.

## 릴리스 일자 {#release-date}

AEM as a Cloud Service의 Cloud Manager 2025.5.0 릴리스 일자는 2025년 5월 8일 금요일입니다.

다음 릴리스는 2025년 6월 5일 금요일에 예정되어 있습니다.

## 새로운 기능 {#what-is-new}

### Edge Delivery Services에 대해 한 번의 클릭으로 컨텐츠 소스 구성

Adobe Experience Manager(AEM) Edge Delivery Services을 사용하면 빠르고 전역적으로 분산된 에지 네트워크를 사용하여 Google 드라이브, SharePoint 또는 AEM 자체와 같은 여러 소스에서 콘텐츠를 전달할 수 있습니다.

콘텐츠 소스 구성은 Helix 4와 Helix 5에서 다릅니다. 차이점에 대해 알아보고 두 버전에 대한 포괄적인 구성 단계, 예제 및 유효성 검사 지침을 따르십시오.

[콘텐츠 원본 구성](/help/implementing/cloud-manager/edge-delivery/configure-content-source.md)을 참조하세요.


## 얼리 어답터 프로그램 {#early-adoption}

Cloud Manager의 얼리 어답터 프로그램(Early Adopter Program)에 참여하여 일반 릴리스 전에 예정된 기능에 독점적으로 액세스할 수 있습니다.

현재 다음 얼리어답터 기회를 사용할 수 있습니다.

### Edge Delivery 구성 파이프라인 추가 {#add-eds-pipeline}

이제 구성 파이프라인이 Edge Delivery Services으로 빌드된 사이트에 대해 지원되므로 이 기능은 Cloud Service 환경뿐만 아니라 확장됩니다. 해당되는 경우 **파이프라인 구성**&#x200B;을 사용하여 트래픽 필터링 규칙 및 웹 응용 프로그램 방화벽(WAF) 구성과 같은 설정을 관리할 수 있습니다. [지원되는 구성](/help/operations/config-pipeline.md#configurations)을 참조하십시오.

![파이프라인 추가 드롭다운 목록에 Edge Delivery 파이프라인 추가](/help/implementing/cloud-manager/release-notes/assets/add-edge-delivery-pipeline.png)

이 새로운 기능을 테스트하고 피드백을 공유하려면 Adobe ID과 연결된 전자 메일 주소에서 [grp-aemeds-config-pipeline-adopter@adobe.com](mailto:grp-aemeds-config-pipeline-adopter@adobe.com)(으)로 전자 메일을 보내세요.

### Azure DevOps에 대한 지원을 통해 나만의 Git 가져오기 {#gitlab-bitbucket-azure-vsts}

<!-- BOTH CS & AMS -->

이제 고객은 최신 Azure DevOps 및 레거시 VSTS(Visual Studio Team Services) 저장소를 모두 지원하여 Azure DevOps Git 저장소를 Cloud Manager에 온보딩할 수 있습니다.

* Edge Delivery Services 사용자의 경우 온보딩된 리포지토리를 사용하여 사이트 코드를 동기화하고 배포할 수 있습니다.
* AEM as a Cloud Service 및 Adobe Managed Services(AMS) 사용자의 경우 저장소를 전체 스택 및 프론트엔드 파이프라인 모두에 연결할 수 있습니다.

추가 파이프라인 유형에 대한 지원과 코드 품질 파이프라인을 통한 가져오기 요청 유효성 검사가 곧 제공될 예정입니다.

[Cloud Manager에서 외부 저장소 추가](/help/implementing/cloud-manager/managing-code/external-repositories.md)를 참조하십시오.

![저장소 추가 대화 상자](/help/implementing/cloud-manager/release-notes/assets/azure-repo.png)

이 새로운 기능을 테스트하고 피드백을 공유하는 데 관심이 있으시면 Adobe ID와 연결된 이메일 주소로 [Grp-CloudManager_BYOG@adobe.com](mailto:grp-cloudmanager_byog@adobe.com)에 이메일을 보내 주십시오. 사용하려는 Git 플랫폼과 비공개/공개 또는 기업 저장소 구조인지 여부를 반드시 포함해야 합니다.

#### 나만의 Git 가져오기 와 관련하여 자주 묻는 질문

| 질문 | 답변 |
|---|---|
| *필요한 경우 프로젝트가 Adobe 관리 Git 저장소로 다시 전환되는 방법은 무엇입니까?* | 다시 전환하는 것은 간단합니다. [파이프라인을 업데이트](/help/implementing/cloud-manager/configuring-pipelines/managing-pipelines.md)하여 Adobe 저장소를 가리키도록 하고 더 이상 필요하지 않은 경우 외부 저장소를 제거합니다. |
| *다른 환경(예: 비프로덕션 대 프로덕션)에 대해 다른 저장소를 구성하여 비프로덕션에서 먼저 테스트할 수 있습니까?* | 예. 별도의 환경에 대해 서로 다른 저장소를 구성할 수 있습니다. 예를 들어 프로덕션 파이프라인이 Adobe 저장소에 연결된 상태를 유지하는 동안 개발 또는 코드 품질 파이프라인이 외부 저장소를 가리킬 수 있습니다. 이 구성 중에 두 저장소 간의 동기화 작업이 활성 상태로 유지되는지 확인하십시오. |
| *IP 허용 목록과 같은 기존 설정이 계속 작동합니까?* | 예. 기존 IP 허용 목록은 평소대로 계속 작동합니다. 그러나 외부 Git 저장소가 방화벽으로 보호되어 있는 경우 필요한 [Adobe IP 주소를 허용 목록](/help/implementing/cloud-manager/ip-allow-lists/introduction.md)에 추가해야 합니다. |
| *모든 GitLab 저장소 URL이 작동합니까? 사용 중인 저장소 URL은 `https://gitlab_dedicated_url.com/path/repo-name.git` 형식을 따르며, 이는 설명서의 예제와 다릅니다.* | 예. [Cloud Manager에서 외부 저장소 추가](/help/implementing/cloud-manager/managing-code/external-repositories.md)(`https://git-vendor-name.com/org-name/repo-name.git`)에 설명된 것과 같은 자체 호스팅 GitLab URL을 포함하여 API V3 또는 V4를 지원하는 모든 GitLab 저장소가 지원됩니다. |


<!--
## Bug fixes

* Issue

* Issue

* Issue
-->

<!-- ## Known issues {#known-issues} -->

