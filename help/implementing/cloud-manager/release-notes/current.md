---
title: Cloud Manager 2025.10.0 릴리스 정보
description: Adobe Experience Manager as a Cloud Service의 Cloud Manager 2025.10.0 릴리스에 대해 알아봅니다.
feature: Release Information
role: Admin
exl-id: 24d9fc6f-462d-417b-a728-c18157b23bbe
source-git-commit: 85784a9611bc6f83a1d70b66ff7087117aa7ec0b
workflow-type: tm+mt
source-wordcount: '1428'
ht-degree: 89%

---

# Adobe Experience Manager as a Cloud Service의 Cloud Manager 2025.10.0 릴리스 정보 {#release-notes}

<!-- https://wiki.corp.adobe.com/display/DMSArchitecture/%5BKT%5D+Cloud+Manager+2025.08.0+Release -->

AEM (Adobe Experience Manager) as a Cloud Service의 Cloud Manager 2025.10.0 릴리스에 대해 알아봅니다.

또한 [최신 Adobe Experience Manager as a Cloud Service 릴리스 정보](/help/release-notes/release-notes-cloud/release-notes-current.md)도 살펴보십시오.

## 릴리스 일자 {#release-date}

AEM as a Cloud Service의 Cloud Manager 2025.10.0 릴리스 일자는 2025년 10월 2일 목요일입니다.

다음 릴리스는 2025년 11월 6일 목요일에 예정되어 있습니다.

## 새로운 기능 {#what-is-new}

* **전용 단계 전용 및 프로덕션 전용 배포 파이프라인**

  이제 Cloud Manager은 전용 스테이지 전용 및 프로덕션 전용 배포 파이프라인을 제공하여 스테이징 및 프로덕션 환경에 대한 배포를 독립적으로 관리할 수 있는 보다 큰 유연성을 제공합니다. [스테이지 전용 및 프로덕션 전용 파이프라인 분할](/help/implementing/cloud-manager/configuring-pipelines/stage-prod-only.md)을 참조하십시오.

* **AEM 클라우드 상태 평가 서비스**

  Adobe은 AEM as a Cloud Service 환경을 최적화하고 안전하며 모범 사례에 맞도록 유지하는 자동화된 비침습적 검사 도구인 AEM 클라우드 상태 평가 서비스를 제공합니다.

  이 서비스는 다음을 수행합니다.

   * 환경을 스캔하여 성능 병목 현상, 비효율성 및 잠재적 위험을 표시합니다.
   * 콘텐츠 구조(블루프린트, Live Copy) 및 사용자 정의 구성을 분석합니다.
   * 오래된 종속성(AEM SDK, 서드파티 라이브러리)을 식별합니다.
   * 코드 품질 문제에 플래그를 지정합니다(잘못된 주석, 비효율적인 패턴).
   * **액션 센터**&#x200B;와 같은 대시보드를 통해 실행 가능한 지침을 제공합니다.
   * 초기 문제 탐지 및 해결을 통해 사전 최적화를 지원합니다.

  팀은 보다 원활한 성능, 더 강력한 보안 및 장기 유지 가능성을 위해 AEM 환경을 지속적으로 모니터링하고 개선할 수 있습니다.

  [프로덕션 및 스테이징 환경에 대한 상태 평가](/help/implementing/cloud-manager/reports/report-health-assessment.md)를 참조하십시오.

* **구성 파이프라인 지원**

  이제 Edge Delivery Services를 사용하여 빌드한 사이트에서도 구성 파이프라인이 지원되며 Cloud Service 환경 그 이상으로 기능이 확장되었습니다. **구성 파이프라인**&#x200B;을 사용하여 트래픽 필터 규칙 및 원본 선택기를 포함한 CDN 구성 등의 설정을 관리할 수 있습니다. [지원되는 구성](/help/operations/config-pipeline.md#configurations)을 참조하십시오.

  Edge Delivery 구성 파이프라인은 Cloud Manager 파이프라인 변수를 통해 비밀 또한 지원합니다.

  [Edge Delivery 파이프라인 추가](/help/implementing/cloud-manager/configuring-pipelines/configuring-edge-delivery-pipeline.md)를 참조하십시오.

* **도메인을 CDN에 매핑 설정 대화 상자 간소화**

  Cloud Manager는 혼동을 줄이고 구성 속도를 높이기 위해 **도메인을 CDN에 매핑** 흐름을 간소화했습니다. 이제 대화 상자에서 **Adobe 관리형 CDN**(&#39;권장&#39; 배지 포함)을 강조 표시합니다.

  ![Adobe 관리형 CDN 라디오 버튼이 선택된 상태의 도메인을 CDN에 매핑 대화 상자입니다](/help/implementing/cloud-manager/assets/cdn/map-domain-to-cdn-dialog-box-adobe-managed-cdn.png).

  [도메인 매핑 추가](/help/implementing/cloud-manager/domain-mappings/add-domain-mapping.md)를 참조하십시오.

  대화 상자에는 다음과 같은 지침 콘텐츠에 중점을 둔 **기타 CDN 공급자** 카드에 대한 간결한 단일 체크리스트도 표시됩니다.

   * CDN 원본을 `publish-p<PROGRAM_ID>-e<ENV_ID>.adobeaemcloud.com`으로 지정합니다.
   * 원래 호스트를 전달하려면 **호스트/SNI**&#x200B;를 설정합니다.
   * `X-AEM-Edge-Key`를 추가합니다(Cloud Manager에서 키를 배포한 후).
   * `X-Forwarded-Host`를 고객용 도메인으로 설정합니다.
   * AEM에 도달하기 전에 다른 `X-Forwarded-*` 헤더를 지웁니다.

  ![기타 CDN 공급자 라디오 버튼이 선택된 상태의 도메인을 CDN에 매핑 대화 상자](/help/implementing/cloud-manager/assets/cdn/map-domain-to-cdn-dialog-box-other-cdn-provider.png)

  <!-- (no redundant `Origin` field or "Learn more" clutter) -->함께 제공되는 바닥글에는 주요 CDN에 대한 샘플 구성 및 전체 설명서에 대한 링크 등 두 개의 유용한 링크가 있습니다. 단일 확인 버튼 - 내 CDN을 구성했습니다. 흐름이 완료됩니다.

  [AEM as a Cloud Service의 CDN](/help/implementing/dispatcher/cdn.md#point-to-point-CDN)을 참조하십시오.

<!--
### Staging-Only and Production-Only Pipelines {#staging-production-only-pipelines}

Support for [staging-only and production-only pipelines](/help/implementing/cloud-manager/configuring-pipelines/stage-prod-only.md) has been introduced, enabling you to split full-stack production deployment pipelines into smaller, specialized deployments.

If you are interested in testing this new feature and sharing your feedback, send an email to  `Grp-cloudmanager_splitpipelines@adobe.com` from your email address associated with your Adobe ID. -->


## Beta 프로그램 {#private-beta-program}

Cloud Manager의 Beta 프로그램에 참여하면 정식 출시 전에 새로운 기능에 대한 전용 액세스 권한을 얻을 수 있습니다.

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

**최근 개선 사항**

* 이제 더 간단하고 직관적인 워크플로를 통해 비프로덕션 파이프라인에서 특수 테스트 환경을 구성할 수 있습니다. 간소화된 설정으로 완료 속도가 빨라지고 구성 오류가 줄어듭니다.
* **콘텐츠 복사**&#x200B;가 이제 특수 테스트 환경에서 지원됩니다. 이제 프로덕션을 미러링하는 독립적인 테스트 환경에서 **콘텐츠 복사**&#x200B;를 안전하게 실행할 수 있습니다.<!-- (CMGR‑68900) -->

[전문화된 테스트 환경 추가](/help/implementing/cloud-manager/specialized-test-environment.md)를 참조하십시오.

![전문화된 테스트 환경 라디오 버튼이 선택된 환경 추가 대화 상자](/help/implementing/cloud-manager/release-notes/assets/specialized-test-environment.png)

>[!NOTE]
>
>Adobe는 충분한 수의 참가자가 확보되어 전문화된 테스트 환경에 대한 Beta 액세스 요청을 종료했습니다. 해당 기능은 이제 일반 공급을 위해 준비 중입니다.

<!--
If you are interested in testing this new feature and sharing your feedback, send an email to [grp-earlyadopter_cs_advtestenvironment@adobe.com](mailto:grp-earlyadopter_cs_advtestenvironment@adobe.com) from your email address associated with your Adobe ID. -->


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

10월 Cloud Manager 릴리스에는 중요한 버그 수정 사항이 없습니다.


<!-- ## Known issues {#known-issues} -->

