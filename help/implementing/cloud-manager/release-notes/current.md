---
title: Cloud Manager 2025.7.0 릴리스 정보
description: Adobe Experience Manager as a Cloud Service의 Cloud Manager 2025.7.0 릴리스에 대해 알아봅니다.
feature: Release Information
role: Admin
exl-id: 24d9fc6f-462d-417b-a728-c18157b23bbe
source-git-commit: 26fbc60b1348e8c5f42adc8fd0e596b639fe9b44
workflow-type: tm+mt
source-wordcount: '920'
ht-degree: 66%

---

# Adobe Experience Manager as a Cloud Service의 Cloud Manager 2025.7.0 릴리스 정보 {#release-notes}

<!-- https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+2025.03.0+Release -->

AEM (Adobe Experience Manager) as a Cloud Service의 Cloud Manager 2025.7.0 릴리스에 대해 알아봅니다.

또한 [최신 Adobe Experience Manager as a Cloud Service 릴리스 정보](/help/release-notes/release-notes-cloud/release-notes-current.md)도 살펴보십시오.

## 릴리스 일자 {#release-date}

AEM as a Cloud Service의 Cloud Manager 2025.7.0 릴리스 일자는 2025년 7월 10일 금요일입니다.

다음 릴리스는 2025년 8월 7일 금요일에 예정되어 있습니다.

## 새로운 기능 {#what-is-new}

* **Cloud Manager에서 ECDSA(Elliptic Curve Digital Signature Algorithm) SSL 인증서 지원 추가**

  이제 Cloud Manager에서 ECDSA 인증서를 지원합니다. 이 기능은 더 작은 키 크기로 강력한 보안을 제공하여 고객이 CDN 구성에 최신 초경량 암호화를 적용할 수 있도록 합니다. <!-- https://jira.corp.adobe.com/browse/CMGR-62399 -->

* **사이트 라이선스 사용량 보고서 다운로드**

  **사이트 사용 세부 정보** 페이지(Cloud Manager에서 **라이선스**&#x200B;를 클릭합니다. Solutions 테이블의 **Sites** 행에서 **사용 세부 정보 보기**&#x200B;를 클릭합니다. 이제 고객은 **보고서 다운로드**&#x200B;를 클릭하여 데이터를 CSV 파일로 내보낼 수 있습니다. 이 다운로드를 통해 사용 트렌드를 간편하게 분석하고 공유할 수 있습니다. <!-- https://jira.corp.adobe.com/browse/CMGR-42274 -->

  ![사이트 사용 세부 정보 페이지](/help/implementing/cloud-manager/release-notes/assets/sites-license-usage-page.png)

## 얼리 어답터 프로그램 {#private-beta-program}

Cloud Manager의 알파 및 베타 프로그램에 참여하여 일반 릴리스 전에 예정된 기능에 독점적으로 일찍 액세스하십시오.

현재 사용할 수 있는 영업 기회는 다음과 같습니다.


### 파이프라인 배포를 위한 원클릭 롤백 {#one-click-rollback}

최신 코드가 예상대로 작동하지 않는 경우 이전 배포로 빠르게 되돌립니다. 전체 파이프라인을 다시 실행하거나 커밋을 수동으로 되돌릴 필요가 없습니다.<!--https://jira.corp.adobe.com/browse/CMGR-69556 -->

<!-- Add link to topic within the affected article ==>


### Specialized Testing Environment {#specialized-test-environment}

Cloud Manager now supports the addition of a new environment type called **Specialized Testing Environment**. The environment is designed to help teams validate features under near-production conditions before going live. This environment type is distinct from *Production + Stage*, *Development*, or *Rapid Development* environments and offers a focused space for running advanced validation scenarios.

Recent enhancement: You can now configure specialized testing environments on a non-production pipeline through a simpler, more intuitive workflow. The streamlined setup speeds completion and reduces configuration errors.

See [Add a Specialized Testing Environment](/help/implementing/cloud-manager/specialized-test-environment.md).

![Add environment dialog box with Specialized Testing Environment radio button selected](/help/implementing/cloud-manager/release-notes/assets/specialized-test-environment.png)

If you are interested in testing this new feature and sharing your feedback, send an email to [grp-earlyadopter_cs_advtestenvironment@adobe.com](mailto:grp-earlyadopter_cs_advtestenvironment@adobe.com) from your email address associated with your Adobe ID.


### Bring Your Own Git (BYOG) - now with support for Azure DevOps {#gitlab-bitbucket-azure-vsts}

<!-- BOTH CS & AMS -->

이제 고객은 Azure DevOps Git 저장소를 Cloud Manager에 온보딩할 수 있으며, 최신 Azure DevOps와 이전 VSTS(Visual Studio Team Services) 저장소가 모두 지원됩니다.

* Edge Delivery Services 사용자의 경우 온보딩된 저장소를 사용하여 사이트 코드를 동기화하고 배포할 수 있습니다.
* AEM as a Cloud Service와 Adobe Managed Services(AMS) 사용자의 경우 저장소를 전체 스택 파이프라인과 프론트엔드 파이프라인 모두에 연결할 수 있습니다.

추가 파이프라인 유형과 코드 품질 파이프라인을 통한 가져오기 요청 유효성 검사도 곧 지원할 예정입니다.

[Cloud Manager에서 외부 저장소 추가](/help/implementing/cloud-manager/managing-code/external-repositories.md)를 참조하십시오.

![저장소 추가 대화 상자](/help/implementing/cloud-manager/release-notes/assets/azure-repo.png)

이 새로운 기능을 테스트하고 피드백을 공유하는 데 관심이 있으시면 Adobe ID와 연결된 이메일 주소로 [Grp-CloudManager_BYOG@adobe.com](mailto:grp-cloudmanager_byog@adobe.com)에 이메일을 보내 주십시오. 사용하려는 Git 플랫폼과 비공개/공개 또는 기업 저장소 구조인지 여부를 반드시 포함해야 합니다.


**BYOG에 대한 FAQ**

| 질문 | 답변 |
|---|---|
| *필요한 경우 프로젝트를 Adobe 관리 Git 저장소로 다시 전환하려면 어떻게 해야 합니까?* | 다시 전환하는 것은 간단합니다. [파이프라인을 업데이트](/help/implementing/cloud-manager/configuring-pipelines/managing-pipelines.md)하여 Adobe 저장소를 가리키도록 설정하고 외부 저장소가 더 이상 필요하지 않으면 이를 제거합니다. |
| *다양한 환경(예: 비프로덕션 환경과 프로덕션 환경)에 대해 서로 다른 저장소를 구성한 후 먼저 비프로덕션 환경에서 테스트할 수 있습니까?* | 예, 각기 다른 환경에 맞게 서로 다른 저장소를 구성할 수 있습니다. 예를 들어 개발 또는 코드 품질 파이프라인은 외부 저장소를 가리킬 수 있지만 프로덕션 파이프라인은 Adobe 저장소에 연결된 상태를 유지합니다. 이 구성 중에는 두 저장소 간의 동기화 작업이 활성 상태로 유지되는지 확인하십시오. |
| *IP 허용 목록과 같은 기존 설정은 계속 작동합니까?* | 예, 기존 IP 허용 목록은 평소처럼 계속 작동합니다. 그러나 외부 Git 저장소가 방화벽으로 보호되는 경우 필요한 [Adobe IP 주소를 허용 목록에 추가해야 합니다](/help/implementing/cloud-manager/ip-allow-lists/introduction.md). |
| *모든 GitLab 저장소 URL이 작동합니까? 사용 중인 저장소 URL이 `https://gitlab_dedicated_url.com/path/repo-name.git` 형식을 따릅니다. 이 형식은 설명서에 나와 있는 예시와 다릅니다.* | 예, API V3 또는 V4를 지원하는 모든 GitLab 저장소가 지원되며, 여기에는 [Cloud Manager에서 외부 저장소 추가](/help/implementing/cloud-manager/managing-code/external-repositories.md)에 설명된 것과 같은 자체 호스팅 GitLab URL(`https://git-vendor-name.com/org-name/repo-name.git`)이 포함됩니다. |


#### 액세스 토큰 관리{#manage-access-tokens}

Cloud Manager에서 **액세스 토큰 관리**&#x200B;를 사용하여 GitHub Enterprise, GitLab, Bitbucket, Azure DevOps와 같은 외부 BYOG 저장소와 관련된 액세스 토큰을 보고, 이름을 변경하고, 삭제할 수 있습니다.

[액세스 토큰 관리](/help/implementing/cloud-manager/managing-code/manage-access-tokens.md)를 참조하십시오.

이 새로운 기능을 테스트하고 피드백을 공유하는 데 관심이 있으시면 Adobe ID와 연결된 이메일 주소로 [Grp-CloudManager_BYOG@adobe.com](mailto:grp-cloudmanager_byog@adobe.com)에 이메일을 보내 주십시오.


### Edge Delivery 구성 파이프라인 추가 {#add-eds-pipeline}

이제 Edge Delivery Services를 사용하여 구축한 사이트에서도 구성 파이프라인이 지원되며 Cloud Service 환경 그 이상으로 기능이 확장되었습니다. 해당되는 경우 **구성 파이프라인**&#x200B;을 사용하여 트래픽 필터링 규칙 및 웹 애플리케이션 방화벽(WAF) 구성과 같은 설정을 관리할 수 있습니다. [지원되는 구성](/help/operations/config-pipeline.md#configurations)을 참조하십시오.

![](/help/implementing/cloud-manager/release-notes/assets/edge-delivery-pipeline-add.png)***프로그램 개요**&#x200B;페이지,**파이프라인**&#x200B;카드에서 Edge Delivery 파이프라인 추가 드롭다운 목록에 Edge Delivery 파이프라인 추가.*

![Edge Delivery 파이프라인 추가 대화 상자](/help/implementing/cloud-manager/release-notes/assets/edge-delivery-pipeline-add-dialogbox.png) *Edge Delivery 파이프라인 추가 대화 상자.*

이 새로운 기능을 테스트하고 피드백을 공유하는 데 관심이 있으시면 Adobe ID와 연결된 이메일 주소로 [grp-aemeds-config-pipeline-adopter@adobe.com](mailto:grp-aemeds-config-pipeline-adopter@adobe.com)에 이메일을 보내 주십시오.


## 버그 수정

* 이제 Cloud Manager은 환경 업그레이드 중에 모든 파이프라인에 대한 릴리스 버전을 업데이트하여 모든 파이프라인 유형에서 일관된 버전 추적을 보장합니다. <!-- CMGR-69043 -->
* 이제 DV(도메인 유효성 검사) SSL 인증서가 실패하면 UI에 상태 및 자세한 오류 메시지가 표시되므로 인증서 문제를 이해하고 해결하는 데 도움이 됩니다. <!-- CMGR-68872 -->
* 도메인 매핑을 편집하는 동안 UI는 이제 선택한 도메인과 일치하지 않는 SSL 인증서를 선택할 수 없도록 하여 잘못된 구성을 줄이고 설정 중 안정성을 향상시킵니다. <!-- CMGR-64307 -->
* 인증서가 제대로 삭제되지 않아 도메인이 여전히 활성 상태인 경우가 있습니다. <!-- CMGR-69867 -->
* 경우에 따라 *Adobe Assets*&#x200B;에서 *Adobe Assets Ultimate*(으)로 업그레이드를 차단할 수 있는 문제를 해결했습니다. 이제 전환이 더 매끄럽고 안정적입니다. <!-- CMGR-69506 -->
* 다운스트림 서비스 및 배포를 원활하게 지원하기 위해 다중 지역 환경을 만들 때 주요 지역 필드가 자동으로 설정되는 문제를 해결했습니다. <!-- CMGR-69471 -->
* 실행 후 일부 구성 파이프라인이 제대로 중지되지 않던 문제를 해결했습니다. 이제 파이프라인이 정상적으로 완료되고 예상대로 닫혀 안정성이 향상됩니다. <!-- CMGR-69344 -->


<!-- ## Known issues {#known-issues} -->

