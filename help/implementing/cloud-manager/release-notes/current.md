---
title: Cloud Manager 2025.7.0 릴리스 정보
description: Adobe Experience Manager as a Cloud Service의 Cloud Manager 2025.7.0 릴리스에 대해 알아봅니다.
feature: Release Information
role: Admin
exl-id: 24d9fc6f-462d-417b-a728-c18157b23bbe
source-git-commit: f3e31d1f17283086cd6fe9e73d67feac938d6567
workflow-type: ht
source-wordcount: '1209'
ht-degree: 100%

---

# Adobe Experience Manager as a Cloud Service의 Cloud Manager 2025.7.0 릴리스 정보 {#release-notes}

<!-- https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+2025.03.0+Release -->

AEM (Adobe Experience Manager) as a Cloud Service의 Cloud Manager 2025.7.0 릴리스에 대해 알아봅니다.

또한 [최신 Adobe Experience Manager as a Cloud Service 릴리스 정보](/help/release-notes/release-notes-cloud/release-notes-current.md)도 살펴보십시오.

## 릴리스 일자 {#release-date}

AEM as a Cloud Service의 Cloud Manager 2025.7.0 릴리스 일자는 2025년 7월 10일 목요일입니다.

다음 릴리스는 2025년 8월 7일 목요일에 예정되어 있습니다.

## 새로운 기능 {#what-is-new}

* **Cloud Manager에 ECDSA(Elliptic Curve Digital Signature Algorithm) SSL 인증서 지원**

  Cloud Manager는 이제 ECDSA 인증서를 지원합니다. 이 기능은 더 작은 키 크기로 강력한 보안을 제공하므로 고객은 CDN 구성에 가볍고 현대적인 암호화를 적용할 수 있습니다. <!-- https://jira.corp.adobe.com/browse/CMGR-62399 -->

* **사이트 라이선스 사용 보고서 다운로드**

  **사이트 사용 세부 정보** 페이지에서(Cloud Manager에서) **라이선스**&#x200B;를 클릭합니다. 솔루션 테이블의 **사이트** 행에서 **사용 세부 정보 보기**&#x200B;를 클릭하면 이제 고객이 **보고서 다운로드**&#x200B;를 클릭하여 데이터를 CSV 파일로 내보낼 수 있습니다. 이 다운로드를 통해 사용 추세를 분석하고 공유하는 작업이 간소화됩니다. <!-- https://jira.corp.adobe.com/browse/CMGR-42274 -->

  ![Sites 사용 세부 페이지](/help/implementing/cloud-manager/release-notes/assets/sites-license-usage-page.png)

  [라이선스 대시보드](/help/implementing/cloud-manager/license-dashboard.md)를 참조하십시오.

## Alpha/Beta 프로그램 {#private-beta-program}

Cloud Manager의 Alpha 및 Beta 프로그램에 참여하면 정식 출시 전에 새로운 기능에 대한 전용 액세스 권한을 얻을 수 있습니다.

현재 제공되는 기회는 다음과 같습니다.

### 파이프라인 배포를 위한 원클릭 롤백 {#one-click-rollback}

최신 고객 소스 코드가 예상대로 작동하지 않는 경우 전체 파이프라인을 다시 실행하거나 커밋을 수동으로 되돌릴 필요 없이 이전 배포로 빠르게 되돌릴 수 있습니다.<!--https://jira.corp.adobe.com/browse/CMGR-69556 -->

![환경 카드에서 고객 소스 코드 복원](/help/implementing/cloud-manager/release-notes/assets/restore-previous-code-deployed.png) *위의 환경 카드는 선택한 환경에 대한&#x200B;**복원**>**이전에 배포된 코드**옵션을 보여 줍니다.*


![이전에 배포된 코드 복원 대화 상자](/help/implementing/cloud-manager/release-notes/assets/restore-previous-code-deployed-dialogbox.png)
***이전에 배포된 코드 복원**대화 상자에서 현재 배포된 버전과 복원하려는 버전을 검토한 다음&#x200B;**확인***을 클릭합니다.


![활성화 복원](/help/implementing/cloud-manager/release-notes/assets/restoring-previous-code-deployed-restoring.png)
*Cloud Manager는 환경을 이전 빌드로 롤백하고 콘텐츠와 구성을 그대로 유지하며 배포가 완료될 때까지 환경&#x200B;**복원**을 표시합니다.*


![사용 중인 소스 코드 버전](/help/implementing/cloud-manager/release-notes/assets/environments-view-details-sourcecodeversion.png) *위에서 볼 수 있는 환경 세부 정보 보기에는 이제 사용 중인 활성 소스 코드 버전도 표시됩니다.*

이 새로운 기능을 테스트하고 피드백을 공유하는 데 관심이 있으시면 Adobe ID와 연결된 이메일 주소로 [restorecode@adobe.com](mailto:restorecode@adobe.com)에 이메일을 보내 주십시오.

[AEM as a Cloud Service에서 배포된 이전 코드 복원](/help/operations/restore-previous-code-deployed.md)을 참조하십시오.

[AEM as a Cloud Service 콘텐츠 복원](/help/operations/restore.md).


### 전문화된 테스트 환경 {#specialized-test-environment}

이제 Cloud Manager는 **전문화된 테스트 환경**&#x200B;이라는 새로운 환경 유형의 추가를 지원합니다. 이 환경은 팀이 라이브로 전환하기 전에 거의 프로덕션 환경에서 기능을 검증할 수 있도록 설계되었습니다. 이 환경 유형은 *프로덕션 + 스테이징*, *개발* 또는 *신속한 개발* 환경과는 다르며 고급 검증 시나리오를 실행할 수 있는 집중 공간을 제공합니다.

최근 개선 사항: 이제 더 간단하고 직관적인 워크플로를 통해 비프로덕션 파이프라인에서 특수 테스트 환경을 구성할 수 있습니다. 간소화된 설정으로 완료 속도가 빨라지고 구성 오류가 줄어듭니다.

[전문화된 테스트 환경 추가](/help/implementing/cloud-manager/specialized-test-environment.md)를 참조하십시오.

![전문화된 테스트 환경 라디오 버튼이 선택된 환경 추가 대화 상자](/help/implementing/cloud-manager/release-notes/assets/specialized-test-environment.png)

이 새로운 기능을 테스트하고 피드백을 공유하는 데 관심이 있으시면 Adobe ID와 연결된 이메일 주소로 [grp-earlyadopter_cs_advtestenvironment@adobe.com](mailto:grp-earlyadopter_cs_advtestenvironment@adobe.com)에 이메일을 보내 주십시오.


### 자체 Git 가져오기(BYOG) - Azure DevOps 지원 포함 {#gitlab-bitbucket-azure-vsts}

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

이제 Edge Delivery Services를 사용하여 빌드한 사이트에서도 구성 파이프라인이 지원되며 Cloud Service 환경 그 이상으로 기능이 확장되었습니다. 해당되는 경우 **구성 파이프라인**&#x200B;을 사용하여 트래픽 필터링 규칙 및 웹 애플리케이션 방화벽(WAF) 구성과 같은 설정을 관리할 수 있습니다. [지원되는 구성](/help/operations/config-pipeline.md#configurations)을 참조하십시오.

![](/help/implementing/cloud-manager/release-notes/assets/edge-delivery-pipeline-add.png)***프로그램 개요**페이지,**파이프라인**카드에서 Edge Delivery 파이프라인 추가 드롭다운 목록에 Edge Delivery 파이프라인 추가.*

![Edge Delivery 파이프라인 추가 대화 상자](/help/implementing/cloud-manager/release-notes/assets/edge-delivery-pipeline-add-dialogbox.png) *Edge Delivery 파이프라인 추가 대화 상자.*

이 새로운 기능을 테스트하고 피드백을 공유하는 데 관심이 있으시면 Adobe ID와 연결된 이메일 주소로 [grp-aemeds-config-pipeline-adopter@adobe.com](mailto:grp-aemeds-config-pipeline-adopter@adobe.com)에 이메일을 보내 주십시오.


## 버그 수정

* 이제 Cloud Manager는 환경 업그레이드 중에 모든 파이프라인의 릴리스 버전을 업데이트하여 모든 파이프라인 유형에서 일관된 버전 추적을 보장합니다. <!-- CMGR-69043 -->
* 이제 도메인 검증(DV) SSL 인증서가 실패하면 UI에 상태와 자세한 오류 메시지가 표시되어 인증서 문제를 이해하고 해결하는 데 도움이 됩니다. <!-- CMGR-68872 -->
* 도메인 매핑을 편집하는 동안 UI에서 선택한 도메인과 일치하지 않는 SSL 인증서를 선택하지 못하도록 방지하여 구성 오류를 줄이고 설정 중 안정성을 향상시켰습니다. <!-- CMGR-64307 -->
* 어떤 상황에서는 인증서가 제대로 삭제되지 않았지만 도메인은 여전히 활성 상태로 유지됩니다. <!-- CMGR-69867 -->
* 특정한 경우 *Adobe Assets*&#x200B;에서 *Adobe Assets Ultimate*&#x200B;로의 업그레이드를 차단할 수 있는 문제를 해결했습니다. 이제 전환이 더욱 원활하고 안정적입니다. <!-- CMGR-69506 -->
* 다운스트림 서비스와 배포를 원활하게 지원하기 위해 다중 지역 환경을 생성할 때 주요 지역 필드가 자동으로 설정되는 문제를 해결했습니다. <!-- CMGR-69471 -->
* 일부 구성 파이프라인이 실행 후 제대로 중지되지 않는 문제가 해결되었습니다. 이제 파이프라인이 예상대로 정상적으로 완료되고 닫히므로 신뢰성이 향상되었습니다. <!-- CMGR-69344 -->


<!-- ## Known issues {#known-issues} -->

