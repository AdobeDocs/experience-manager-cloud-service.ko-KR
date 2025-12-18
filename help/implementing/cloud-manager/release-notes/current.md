---
title: Cloud Manager 2025.12.0 릴리스 정보
description: Adobe Experience Manager as a Cloud Service의 Cloud Manager 2025.12.0 릴리스에 대해 알아봅니다.
feature: Release Information
role: Admin
exl-id: 24d9fc6f-462d-417b-a728-c18157b23bbe
source-git-commit: 7c1f1f1022fd63c190a493d312ab1f355859d15a
workflow-type: tm+mt
source-wordcount: '1149'
ht-degree: 61%

---

# Adobe Experience Manager as a Cloud Service의 Cloud Manager 2025.12.0 릴리스 정보 {#release-notes}

<!-- https://wiki.corp.adobe.com/display/DMSArchitecture/%5BKT%5D+Cloud+Manager+2025.08.0+Release -->

AEM (Adobe Experience Manager) as a Cloud Service의 Cloud Manager 2025.12.0 릴리스에 대해 알아봅니다.

또한 [최신 Adobe Experience Manager as a Cloud Service 릴리스 정보](/help/release-notes/release-notes-cloud/release-notes-current.md)도 살펴보십시오.

## 릴리스 일자 {#release-date}

AEM as a Cloud Service의 Cloud Manager 2025.12.0 릴리스 일자는 2025년 12월 4일 금요일입니다.

다음 릴리스는 2026년 1월 22일 금요일에 예정되어 있습니다.

## 새로운 기능 - Experience Hub {#experience-hub-whats-new}

* **Experience Hub에 대한 간소화된 액세스**

  사용자 역할 선택이 제거되었으며 **사전 설정** 선택(콘텐츠 작성자, 자산 라이브러리 관리자, 관리자 및 IT)에 대한 안내서가 추가되었습니다.

* **공지** 및 **제품 업데이트**

  사용 가능한 공지를 전환하고 반복할 수 있지만 취소할 수도 있습니다.

* **최근 항목**

  페이지 편집기, 자산, 프로그램 및 파이프라인 실행 세부 사항, 보안 페이지를 포함한 추가 페이지 및 리소스에 대한 지원을 추가했습니다.

* **프로그램 목록**

  Cloud Manager 세부 사항 페이지에 빠르게 액세스하여 조직의 AEM Cloud Manager 프로그램 표시.

* **AEM Guides**

  AEM Guides 추가 기능이 활성화된 작성 환경에 대한 빠른 작업 및 바로 가기

## 새로운 기능 - Cloud Manager {#cloud-manager-whats-new}

* **안정성, 성능 및 안정성 향상**

  이 릴리스에는 Cloud Manager의 안정성, 성능 및 안정성을 개선한 최적화 및 유지 관리 업데이트가 포함됩니다.

* **특수 테스트 환경**

  >[!NOTE]
  >
  >이제 전문 테스트 환경을 구입할 수 있습니다. 주문하려면 Adobe 담당자에게 문의하십시오.

  이제 Cloud Manager는 **전문화된 테스트 환경**&#x200B;이라는 새로운 환경 유형의 추가를 지원합니다. 이 환경은 팀이 라이브로 전환하기 전에 거의 프로덕션 환경에서 기능을 검증할 수 있도록 설계되었습니다. 이 환경 유형은 *프로덕션 + 스테이징*, *개발* 또는 *신속한 개발* 환경과는 다르며 고급 검증 시나리오를 실행할 수 있는 집중 공간을 제공합니다.

  [전문화된 테스트 환경 추가](/help/implementing/cloud-manager/specialized-test-environment.md)를 참조하십시오.

  ![전문화된 테스트 환경 라디오 버튼이 선택된 환경 추가 대화 상자](/help/implementing/cloud-manager/release-notes/assets/specialized-test-environment.png)

<!--
>[!NOTE]
>
>Adobe has closed beta access requests for Specialized Testing Environments, having reached a sufficient number of participants. The feature is now in preparation for general availability.

If you are interested in testing this new feature and sharing your feedback, send an email to [grp-earlyadopter_cs_advtestenvironment@adobe.com](mailto:grp-earlyadopter_cs_advtestenvironment@adobe.com) from your email address associated with your Adobe ID. -->


* **파이프라인 배포에 대한 원클릭 롤백**

  최신 고객 소스 코드가 예상대로 작동하지 않는 경우 이전 배포로 빠르게 돌아갑니다. 전체 파이프라인을 다시 실행하거나 커밋을 수동으로 되돌릴 필요가 없습니다. <!--https://jira.corp.adobe.com/browse/CMGR-69556 -->

  [AEM as a Cloud Service에서 배포된 이전 코드 복원](/help/operations/restore-previous-code-deployed.md)을 참조하십시오.

  [AEM as a Cloud Service 콘텐츠 복원](/help/operations/restore.md).

* **Edge Delivery Services용 셀프 서비스 WAF 설정**

  Cloud Manager에서 Edge Delivery Services 프로그램을 만들 때 웹 애플리케이션 방화벽(WAF)을 활성화할 수 있습니다. 이 설정은 악성 트래픽 및 DDoS 공격으로부터 사이트를 즉시 보호하여 수동 설정 작업을 줄입니다.

  [한 번의 클릭으로 첫 번째 Edge Delivery 사이트 만들기](/help/implementing/cloud-manager/edge-delivery/create-edge-delivery-site.md)를 참조하십시오.


## Beta 프로그램 {#private-beta-program}

Cloud Manager의 Beta 프로그램에 참여하면 정식 출시 전에 새로운 기능에 대한 전용 액세스 권한을 얻을 수 있습니다.

>[!IMPORTANT]
>
>Beta 릴리스에는 결함이 포함될 수 있으며 어떠한 종류의 보증도 없이 &quot;있는 그대로&quot; 제공됩니다. Adobe은 베타 릴리스를 유지, 수정, 업데이트, 변경, 수정 또는 기타 지원(Adobe 지원 서비스 또는 기타 방식으로)할 의무가 없습니다. Adobe은 고객에게 베타 릴리스의 올바른 기능이나 성능 또는 관련 설명서나 자료에 의존하지 말고 주의할 것을 권장합니다. Beta의 기능 및 API는 예고 없이 변경될 수 있습니다. 따라서 Beta 릴리스를 사용하는 것은 전적으로 고객 자신의 책임입니다.

[AEM Beta 프로그램](/help/release-notes/release-notes-cloud/release-notes-current.md#aem-beta-programs)도 참조하세요.

현재 제공되는 기회는 다음과 같습니다.
<!--
### Support for Custom Author Domains in Cloud Service

AEM Cloud Service is going to soon support one custom domain per Author environment.-->

### Experience Hub 확장성 및 사용자 정의 {#exp-hub-extensibility}

[Experience Hub](/help/experience-hub.md)는 조직의 요구 사항에 맞게 사용자 정의된 AEM에 대한 진입점 역할을 합니다. Experience Hub에서 손쉽게 활성화할 수 있도록 기존 AEM UI 확장 기능에 대해 Adobe에 알려 주십시오.

![Experience Hub 확장성 및 사용자 정의 워크플로의 다이어그램](/help/implementing/cloud-manager/release-notes/assets/experience-hub-extensibility-customization.png)

조직의 대시보드를 확장하고 개인화할 수 있도록 Experience Hub에 사용자 정의 경험을 임베드합니다. Adobe의 기본 제공 위젯 외에 [UI 확장성](https://developer.adobe.com/uix/docs/) 프레임워크를 사용하여 나만의 위젯을 추가합니다. JavaScript 기반 UI 앱을 빌드하고 이를 사용자에게 제공하여 비즈니스별 요구 사항 및 워크플로를 충족합니다.

Beta에 관심이 있으신가요? Adobe OrgID 및 만들고자 하는 사용자 정의에 대한 간단한 설명을 첨부한 이메일을 [beta_exphubextensibility@adobe.com](mailto:beta_exphubextensibility@adobe.com)으로 보내 주시기 바랍니다.

### 모듈 캐싱을 통한 빌드 속도 향상 {#quick-build-cm-pipelines}

새 빌드 모델은 모듈 수준 캐싱을 사용하여 전체 저장소가 아닌 변경된 모듈만 컴파일함으로써 빌드 시간을 단축합니다. 코드 품질, 전체 스택 및 스테이지 전용 파이프라인에 적용됩니다.

![두 가지 빌드 전략 옵션(전체 빌드 및 스마트 빌드)을 표시하는 비프로덕션 파이프라인 편집 대화 상자](/help/implementing/cloud-manager/release-notes/assets/non-production-pipeline-edit.png)
*두 가지 빌드 전략 옵션(전체 빌드 및 스마트 빌드)을 표시하는 비프로덕션 파이프라인 편집 대화 상자*

**파이프라인 추가/편집** 대화 상자의 **Source 코드** 탭에서 새 **빌드 전략** 섹션을 통해 다음 빌드 옵션 중 하나를 선택할 수 있습니다.

* **전체 빌드** — 실행할 때마다 저장소의 모든 모듈을 빌드합니다.
* **스마트 빌드** — 마지막 커밋 이후에 변경된 모듈만 빌드하므로 전체 빌드 시간이 단축됩니다.

**스마트 빌드**&#x200B;를 사용하는 파이프라인을 제어합니다. Beta를 실행하는 동안 이 옵션은 **코드 품질** 및 **개발 배포** 파이프라인에만 나타납니다.

관심이 있으신가요? Adobe OrgID 및 프로그램 ID를 첨부한 이메일을 [beta_quickbuild_cmpipelines@adobe.com](mailto:beta_quickbuild_cmpipelines@adobe.com)으로 보내 주시기 바랍니다.

<!-- You can deactivate incremental builds at the pipeline level by setting the property `CM_BUILD_DISABLE_MODULE_CACHING` to `true` (effective during the `BUILD` step). For how to add pipeline variables, see [Pipeline Variables in Cloud Manager](/help/implementing/cloud-manager/configuring-pipelines/pipeline-variables.md).-->

### Git(BYOG) 가져오기 {#gitlab-bitbucket-azure-vsts}

<!-- BOTH CS & AMS -->

이제 고객은 Azure DevOps Git 저장소를 Cloud Manager에 온보딩할 수 있으며, 최신 Azure DevOps와 이전 VSTS(Visual Studio Team Services) 저장소가 모두 지원됩니다.

* Edge Delivery Services 사용자의 경우 온보딩된 저장소를 사용하여 사이트 코드를 동기화하고 배포할 수 있습니다.
* AEM as a Cloud Service와 Adobe Managed Services(AMS) 사용자의 경우 저장소를 전체 스택 파이프라인과 프론트엔드 파이프라인 모두에 연결할 수 있습니다.

추가 파이프라인 유형과 코드 품질 파이프라인을 통한 가져오기 요청 유효성 검사도 곧 지원할 예정입니다.

[Cloud Manager에서 외부 저장소 추가](/help/implementing/cloud-manager/managing-code/external-repositories.md)를 참조하십시오.

![저장소 추가 대화 상자](/help/implementing/cloud-manager/release-notes/assets/azure-repo.png)

<!-- If you are interested in testing this new feature and sharing your feedback, send an email to [Grp-CloudManager_BYOG@adobe.com](mailto:grp-cloudmanager_byog@adobe.com) from your email address associated with your Adobe ID. Be sure to include which Git platform you want to use and whether you are on a private/public or enterprise repository structure. -->

**BYOG에 대한 FAQ**

| 질문 | 답변 |
|---|---|
| *필요한 경우 프로젝트를 Adobe 관리 Git 저장소로 다시 전환하려면 어떻게 해야 합니까?* | 다시 전환하는 것은 간단합니다. [파이프라인을 업데이트](/help/implementing/cloud-manager/configuring-pipelines/managing-pipelines.md)하여 Adobe 저장소를 가리키도록 설정하고 외부 저장소가 더 이상 필요하지 않으면 이를 제거합니다. |
| *다양한 환경(예: 비프로덕션 환경과 프로덕션 환경)에 대해 서로 다른 저장소를 구성한 후 먼저 비프로덕션 환경에서 테스트할 수 있습니까?* | 예, 각기 다른 환경에 맞게 서로 다른 저장소를 구성할 수 있습니다. 예를 들어 개발 또는 코드 품질 파이프라인은 외부 저장소를 가리킬 수 있지만 프로덕션 파이프라인은 Adobe 저장소에 연결된 상태를 유지합니다. 이 구성 중에는 두 저장소 간의 동기화 작업이 활성 상태로 유지되는지 확인하십시오. |
| *목록`IP Allow`과 같은 기존 설정이 계속 작동합니까?* | 예, 기존 `IP Allow`목록은 평소처럼 계속 작동합니다. 그러나 외부 Git 저장소가 방화벽으로 보호되는 경우 필요한 [Adobe IP 주소를 허용 목록에 추가해야 합니다](/help/implementing/cloud-manager/ip-allow-lists/introduction.md). |
| *모든 GitLab 저장소 URL이 작동합니까? 사용 중인 저장소 URL이 `https://gitlab_dedicated_url.com/path/repo-name.git` 형식을 따릅니다. 이 형식은 설명서에 나와 있는 예시와 다릅니다.* | 예, API V3 또는 V4를 지원하는 모든 GitLab 저장소가 지원되며, 여기에는 [Cloud Manager에서 외부 저장소 추가](/help/implementing/cloud-manager/managing-code/external-repositories.md)에 설명된 것과 같은 자체 호스팅 GitLab URL(`https://git-vendor-name.com/org-name/repo-name.git`)이 포함됩니다. |


#### 액세스 토큰 관리{#manage-access-tokens}

Cloud Manager에서 **액세스 토큰 관리**&#x200B;를 사용하여 GitHub Enterprise, GitLab, Bitbucket, Azure DevOps와 같은 외부 BYOG 저장소와 관련된 액세스 토큰을 보고, 이름을 변경하고, 삭제할 수 있습니다.

[액세스 토큰 관리](/help/implementing/cloud-manager/managing-code/manage-access-tokens.md)를 참조하십시오.

<!-- If you are interested in testing this new feature and sharing your feedback, send an email to [Grp-CloudManager_BYOG@adobe.com](mailto:grp-cloudmanager_byog@adobe.com) from your email address associated with your Adobe ID. -->


## 버그 수정 {#bug-fixes}

2025년 12월 Cloud Manager 릴리스에는 중요한 버그 수정이 없습니다.


<!-- ## Known issues {#known-issues} -->

