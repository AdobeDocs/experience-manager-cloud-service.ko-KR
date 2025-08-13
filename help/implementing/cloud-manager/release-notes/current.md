---
title: Cloud Manager 2025.8.0 릴리스 정보
description: Adobe Experience Manager as a Cloud Service의 Cloud Manager 2025.8.0 릴리스에 대해 알아봅니다.
feature: Release Information
role: Admin
exl-id: 24d9fc6f-462d-417b-a728-c18157b23bbe
source-git-commit: c6493d05c60c01b4840c8f12d06aa4508bdbb534
workflow-type: tm+mt
source-wordcount: '1403'
ht-degree: 55%

---

# Adobe Experience Manager as a Cloud Service의 Cloud Manager 2025.8.0 릴리스 정보 {#release-notes}

<!-- https://wiki.corp.adobe.com/display/DMSArchitecture/%5BKT%5D+Cloud+Manager+2025.08.0+Release -->

AEM (Adobe Experience Manager) as a Cloud Service의 Cloud Manager 2025.8.0 릴리스에 대해 알아봅니다.

또한 [최신 Adobe Experience Manager as a Cloud Service 릴리스 정보](/help/release-notes/release-notes-cloud/release-notes-current.md)도 살펴보십시오.

## 릴리스 일자 {#release-date}

AEM as a Cloud Service의 Cloud Manager 2025.8.0 릴리스 일자는 2025년 8월 7일 금요일입니다.

다음 릴리스는 2025년 9월 4일 금요일에 예정되어 있습니다.

## 새로운 기능 {#what-is-new}

* **Adobe Experience Hub 준비 중**

  2025년 8월 19일부터 Adobe은 모든 Adobe Experience Manager 사용자에게 새 Experience Hub의 단계적 롤아웃을 시작합니다.

  Experience Hub은 사용자가 목표를 더 빨리 달성할 수 있도록 개인화된 컨텍스트 기반의 경험을 제공하는 통합 시작점입니다. 롤아웃은 2025년 8월 26일까지 완료되어 모든 사용자가 사용할 수 있습니다. 새 Experience Hub은 [experience.adobe.com](https://experience.adobe.com/)에서 바로 액세스할 수 있습니다. 자세한 내용은 [Adobe Experience Hub](/help/implementing/cloud-manager/aem-home.md)를 참조하세요.

* **Edge Delivery Services 라이선스는 셀프 서비스 방식으로 HIPAA 프로그램에 포함될 수 있습니다**

  의료 또는 민감한 데이터 요구 사항이 있는 조직은 이제 셀프서비스 방식으로 Edge Delivery Services을 사용할 수 있으므로 HIPAA 규정을 준수하여 엄격한 규제 표준을 충족할 수 있습니다. <!-- CMGR-70016 -->

* 이제 Edge Delivery Services에서 **BYOG를 사용할 수 있습니다**

  이제 Cloud Manager을 사용하여 외부 Git 저장소를 구성할 수 있으므로 유연한 코드 관리 워크플로를 가능하게 합니다. <!--(CMGR‑69010, CMGR‑70988) --> 또한 선택한 분기에서 Cloud Manager UI로 직접 코드를 가져올 수 있으므로 수동 저장소 작업이 줄어듭니다. [외부 Git 저장소를 사용하도록 Edge Delivery 사이트 구성](/help/implementing/cloud-manager/edge-delivery/config-edge-delivery-site-with-byog.md) <!-- (CMGR‑68085)(CMGR-69015) -->을 참조하십시오. <!-- KT: https://wiki.corp.adobe.com/display/DMSArchitecture/%5B2025%5D+Cloud+Manager+-+Bring+Your+Own+Git+with+EDS -->

* **새 Forms 추가 기능에 대한 자동 프로비저닝**

  사이트 전용 고객은 마케팅 양식을 간소화하고 저렴하게 구축할 수 있는 방법이 필요한 경우가 많습니다. 새로운 AEM Forms 사이트 추가 기능은 Sites 프로그램에 제한된 Forms 기능을 추가하여 필요한 사항을 충족합니다. 또한 전체 AEM Forms 제품에 대한 명확한 업그레이드 경로를 만듭니다. <!-- (CMGR-64301) --> <!-- KT: CMGR Provisioning Support for AEM Forms Sites Add-On SKU https://wiki.corp.adobe.com/pages/viewpage.action?pageId=3578379797 -->

  추가 기능:
   * 별도의 Forms 프로그램이나 권한 없이 Sites 프로그램에 연결하여 함께 배포합니다.
   * 간단한 마케팅 양식 사용 사례를 타깃팅합니다.
   * IMS 조직이 사용 가능한 Forms 추가 기능 라이선스를 보유하고 있는 경우에만 프로덕션 프로그램을 만들거나 프로덕션 프로그램을 편집하는 동안 **솔루션 및 추가 기능** 목록에 표시됩니다.

     ![Forms 추가 기능](/help/implementing/cloud-manager/release-notes/assets/forms-add-on.png) *IMS 조직에서 Forms 추가 기능 라이선스를 사용할 수 있는 경우에만 프로그램에 Forms 추가 기능을 추가할 수 있습니다.*

     ![프로덕션 프로그램을 만들 때 솔루션 및 추가 기능의 Forms 추가 기능](/help/implementing/cloud-manager/release-notes/assets/forms-add-on-creating-production-program.png) *프로그램을 만드는 동안 Sites 솔루션에서 Forms 추가 기능을 선택할 수 있습니다.*

     ![프로덕션 프로그램을 편집할 때 Forms 추가 기능](/help/implementing/cloud-manager/release-notes/assets/forms-add-on-editing-production-program.png) ***프로그램 편집**&#x200B;에서 Sites 프로그램에 대한 Forms 추가 기능을 선택한 다음 파이프라인을 실행하여 환경에서 활성화하십시오.*

     자세한 내용은 [프로덕션 프로그램 만들기](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md)를 참조하십시오.

## Beta 프로그램 {#private-beta-program}

Cloud Manager의 베타 프로그램에 참여하여 일반 릴리스 전에 예정된 기능에 독점적으로 액세스할 수 있습니다.

현재 제공되는 기회는 다음과 같습니다.

### 파이프라인 배포를 위한 원클릭 롤백 {#one-click-rollback}

최신 고객 소스 코드가 예상대로 작동하지 않는 경우 전체 파이프라인을 다시 실행하거나 커밋을 수동으로 되돌릴 필요 없이 이전 배포로 빠르게 되돌릴 수 있습니다.<!--https://jira.corp.adobe.com/browse/CMGR-69556 -->

![환경 카드에서 고객 소스 코드 복원](/help/implementing/cloud-manager/release-notes/assets/restore-previous-code-deployed.png) *위의 환경 카드는 선택한 환경에 대한&#x200B;**복원**>**이전에 배포된 코드**&#x200B;옵션을 보여 줍니다.*

![이전에 배포된 코드 복원 대화 상자](/help/implementing/cloud-manager/release-notes/assets/restore-previous-code-deployed-dialogbox.png)
***이전에 배포된 코드 복원**&#x200B;대화 상자에서 현재 배포된 버전과 복원하려는 버전을 검토한 다음&#x200B;**확인***을 클릭합니다.

![활성화 복원](/help/implementing/cloud-manager/release-notes/assets/restoring-previous-code-deployed-restoring.png)
*Cloud Manager는 환경을 이전 빌드로 롤백하고 콘텐츠와 구성을 그대로 유지하며 배포가 완료될 때까지 환경&#x200B;**복원**&#x200B;을 표시합니다.*

![사용 중인 소스 코드 버전](/help/implementing/cloud-manager/release-notes/assets/environments-view-details-sourcecodeversion.png) *위에서 볼 수 있는 환경 세부 정보 보기에는 이제 사용 중인 활성 소스 코드 버전도 표시됩니다.*

이 새로운 기능을 테스트하고 피드백을 공유하는 데 관심이 있으시면 Adobe ID와 연결된 이메일 주소로 [restorecode@adobe.com](mailto:restorecode@adobe.com)에 이메일을 보내 주십시오.

[AEM as a Cloud Service에서 배포된 이전 코드 복원](/help/operations/restore-previous-code-deployed.md)을 참조하십시오.

[AEM as a Cloud Service 콘텐츠 복원](/help/operations/restore.md).

### 전문화된 테스트 환경 {#specialized-test-environment}

이제 Cloud Manager는 **전문화된 테스트 환경**&#x200B;이라는 새로운 환경 유형의 추가를 지원합니다. 이 환경은 팀이 라이브로 전환하기 전에 거의 프로덕션 환경에서 기능을 검증할 수 있도록 설계되었습니다. 이 환경 유형은 *프로덕션 + 스테이징*, *개발* 또는 *신속한 개발* 환경과는 다르며 고급 검증 시나리오를 실행할 수 있는 집중 공간을 제공합니다.

**최근 개선 사항**

* 이제 더 간단하고 직관적인 워크플로우를 통해 비프로덕션 파이프라인에서 전문 테스트 환경을 구성할 수 있습니다. 간소화된 설정으로 완료 속도가 빨라지고 구성 오류가 줄어듭니다.
* **콘텐츠 복사**&#x200B;는 전문 테스트 환경에서 지원됩니다. 이제 프로덕션을 미러링하는 격리된 테스트 환경에서 **콘텐츠 복사**&#x200B;를 안전하게 실행할 수 있습니다. <!-- (CMGR‑68900) -->

[전문화된 테스트 환경 추가](/help/implementing/cloud-manager/specialized-test-environment.md)를 참조하십시오.

![전문화된 테스트 환경 라디오 버튼이 선택된 환경 추가 대화 상자](/help/implementing/cloud-manager/release-notes/assets/specialized-test-environment.png)

>[!NOTE]
>
>Adobe은 충분한 수의 참가자에 도달하여 전문 테스트 환경에 대한 베타 액세스 요청을 마감했습니다. 이 기능은 현재 일반 공급 준비 중입니다.

<!--
If you are interested in testing this new feature and sharing your feedback, send an email to [grp-earlyadopter_cs_advtestenvironment@adobe.com](mailto:grp-earlyadopter_cs_advtestenvironment@adobe.com) from your email address associated with your Adobe ID. -->


### Bring Your Own Git (BYOG) {#gitlab-bitbucket-azure-vsts}

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
| *`IP Allow` 목록과 같은 기존 설정이 계속 작동합니까?* | 예, 기존 `IP Allow` 목록은 평소와 같이 계속 작동합니다. 그러나 외부 Git 저장소가 방화벽으로 보호되는 경우 필요한 [Adobe IP 주소를 허용 목록에 추가해야 합니다](/help/implementing/cloud-manager/ip-allow-lists/introduction.md). |
| *모든 GitLab 저장소 URL이 작동합니까? 사용 중인 저장소 URL이 `https://gitlab_dedicated_url.com/path/repo-name.git` 형식을 따릅니다. 이 형식은 설명서에 나와 있는 예시와 다릅니다.* | 예, API V3 또는 V4를 지원하는 모든 GitLab 저장소가 지원되며, 여기에는 [Cloud Manager에서 외부 저장소 추가](/help/implementing/cloud-manager/managing-code/external-repositories.md)에 설명된 것과 같은 자체 호스팅 GitLab URL(`https://git-vendor-name.com/org-name/repo-name.git`)이 포함됩니다. |


#### 액세스 토큰 관리{#manage-access-tokens}

Cloud Manager에서 **액세스 토큰 관리**&#x200B;를 사용하여 GitHub Enterprise, GitLab, Bitbucket, Azure DevOps와 같은 외부 BYOG 저장소와 관련된 액세스 토큰을 보고, 이름을 변경하고, 삭제할 수 있습니다.

[액세스 토큰 관리](/help/implementing/cloud-manager/managing-code/manage-access-tokens.md)를 참조하십시오.

<!-- If you are interested in testing this new feature and sharing your feedback, send an email to [Grp-CloudManager_BYOG@adobe.com](mailto:grp-cloudmanager_byog@adobe.com) from your email address associated with your Adobe ID. -->


### Edge Delivery 구성 파이프라인 추가 {#add-eds-pipeline}

이제 Edge Delivery Services를 사용하여 빌드한 사이트에서도 구성 파이프라인이 지원되며 Cloud Service 환경 그 이상으로 기능이 확장되었습니다. 해당되는 경우 **구성 파이프라인**&#x200B;을 사용하여 트래픽 필터링 규칙 및 웹 애플리케이션 방화벽(WAF) 구성과 같은 설정을 관리할 수 있습니다. [지원되는 구성](/help/operations/config-pipeline.md#configurations)을 참조하십시오.

**최근 개선 사항**

* 이제 Edge Delivery Services 파이프라인에 **배포된 코드** 열에 **구성**&#x200B;이 표시되어 구성 전용 배포를 즉시 식별할 수 있습니다. <!-- CMGR‑69681 -->
* 프로그램에 하나 이상의 Edge Delivery Services 사이트 및 매핑된 도메인이 포함되면 Cloud Manager에서 **Edge Delivery 파이프라인 추가**&#x200B;를 표시합니다. 그렇지 않으면 옵션이 비활성화되어 표시되고 툴팁에 누락된 요구 사항이 설명되어 있습니다. <!-- CMGR‑69680 -->
* **Edge Delivery** 탭에는 각 파이프라인의 이름, 상태, 저장소 및 분기를 나열하는 새 **Edge Delivery 파이프라인** 위젯이 표시됩니다. <!-- (CMGR-69052) -->

  ![파이프라인 이름, 상태, 저장소 및 분기를 표시하는 Edge Delivery 파이프라인 위젯](/help/implementing/cloud-manager/release-notes/assets/edge-delivery-pipeline-widget.png)

* **필터** 패널에 **배달 유형** 섹션이 추가됩니다. **Edge 배달** 및 **배달 게시** 확인란이 포함됩니다. <!-- (CMGR-69682) -->

  ![Edge 게재 및 게시 게재의 새 게재 유형을 표시하는 필터 패널](/help/implementing/cloud-manager/release-notes/assets/filter-delivery-type.png)

![](/help/implementing/cloud-manager/release-notes/assets/edge-delivery-pipeline-add.png)***프로그램 개요**&#x200B;페이지,**파이프라인**&#x200B;카드에서 Edge Delivery 파이프라인 추가 드롭다운 목록에 Edge Delivery 파이프라인 추가.*

![Edge Delivery 파이프라인 추가 대화 상자](/help/implementing/cloud-manager/release-notes/assets/edge-delivery-pipeline-add-dialogbox.png) *Edge Delivery 파이프라인 추가 대화 상자.*

[Edge Delivery 파이프라인 추가](/help/implementing/cloud-manager/configuring-pipelines/configuring-edge-delivery-pipeline.md)를 참조하십시오.

이 새로운 기능을 테스트하고 피드백을 공유하는 데 관심이 있으시면 Adobe ID와 연결된 이메일 주소로 [grp-aemeds-config-pipeline-adopter@adobe.com](mailto:grp-aemeds-config-pipeline-adopter@adobe.com)에 이메일을 보내 주십시오.


## 버그 수정

* 이제 파이프라인은 활성 Edge Delivery Services 도메인 구성에만 변수를 전달하여 파이프라인 재생성 중 제거된 구성을 건너뜁니다. <!-- (CMGR‑70039) -->
* 이제 파이프라인 실행이 안정적으로 시작됩니다. 내부 리소스 처리 오류로 인해 일부 파이프라인이 시작되지 못하는 문제가 해결되었습니다. <!-- (CMGR‑58167) -->
* 컨텐츠 복사는 Cloud Manager 권한 및 배포 관리자 또는 관리자 권한이 없는 사용자의 시작을 확인합니다. <!-- (CMGR‑62097) -->


<!-- ## Known issues {#known-issues} -->

