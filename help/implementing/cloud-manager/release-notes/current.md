---
title: Cloud Manager 2026.4.0 릴리스 정보
description: Adobe Experience Manager as a Cloud Service의 Cloud Manager 2026.4.0 릴리스에 대해 알아봅니다.
feature: Release Information
role: Admin
exl-id: 24d9fc6f-462d-417b-a728-c18157b23bbe
source-git-commit: aa8aba7f798e251c8a25ee247402e23517707e88
workflow-type: tm+mt
source-wordcount: '634'
ht-degree: 23%

---

# Adobe Experience Manager as a Cloud Service의 Cloud Manager 2026.4.0 릴리스 정보 {#release-notes}

<!-- https://wiki.corp.adobe.com/display/DMSArchitecture/%5BKT%5D+Cloud+Manager+2025.08.0+Release -->

AEM (Adobe Experience Manager) as a Cloud Service의 Cloud Manager 2026.4.0 릴리스에 대해 알아봅니다.

또한 [최신 Adobe Experience Manager as a Cloud Service 릴리스 정보](/help/release-notes/release-notes-cloud/release-notes-current.md)도 살펴보십시오.

## 릴리스 일자 {#release-date}

AEM as a Cloud Service의 Cloud Manager 2026.4.0 릴리스 일자는 2026년 4월 2일 금요일입니다.

다음 릴리스는 2026년 5월 7일 금요일에 예정되어 있습니다.


## 새로운 기능 - Cloud Manager {#cloud-manager-whats-new}

* **AI 기반 IDE용 Cloud Manager MCP 서버**

  이제 Cloud Manager 공개 API를 AI 지원 IDE(예: 커서)의 도구로 표시하는 MCP(Model Context Protocol) 서버를 사용할 수 있습니다. 연결한 후 대화 프롬프트를 사용하여 프로그램, 파이프라인, 환경 및 저장소를 나열하고 관리할 수 있으므로 편집기를 종료하지 않고도 더 빠르게 이동할 수 있습니다.

  [AEM as a Cloud Service과 MCP 사용](/help/ai-in-aem/mcp-support/using-mcp-with-aem-as-a-cloud-service.md) 설명서를 참조하세요.

  자습서 [Cloud Manager MCP 서버](https://experienceleague.adobe.com/en/docs/experience-manager-learn/cloud-service/ai/mcp-servers/cloud-manager#)를 참조하십시오.

* **모듈 캐싱을 사용하여 더 빠른 빌드**

  새 빌드 모델은 모듈 수준 캐싱을 사용하여 전체 저장소가 아닌 변경된 모듈만 컴파일함으로써 빌드 시간을 단축합니다. 코드 품질 비프로덕션 파이프라인 및 개발 전체 스택 비프로덕션 파이프라인에 적용됩니다.

  [비프로덕션 파이프라인에서 스마트 빌드 사용 정보](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md#about-smart-build) 및 [비프로덕션 파이프라인 추가](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md#full-stack-code)를 참조하십시오.

* **셀프 서비스 호스트 연결 확인**

  이제 Cloud Manager을 사용하여 환경에서 셀프서비스 검사를 실행할 수 있습니다. 이러한 검사는 호스트 및 포트에 연결할 수 있는지 확인하고 이그레스를 포함하여 구성된 프로그램의 네트워크 경로를 사용하여 DNS 확인을 확인합니다. 이 기능을 사용하면 지원 사례를 열거나 Pod에 액세스하지 않고도 고급 네트워킹을 검증하고 통합 문제를 보다 빠르게 해결할 수 있습니다. <!-- SKYOPS-23640 -->

  [네트워크 연결 테스트](/help/security/network-connectivity-test.md)를 참조하세요.

* **안정성, 성능 및 안정성 향상**

  이 릴리스에는 Cloud Manager의 안정성, 성능 및 안정성을 개선한 최적화 및 유지 관리 업데이트가 포함됩니다.


## Beta 프로그램 {#private-beta-program}

Cloud Manager의 Beta 프로그램에 참여하면 정식 출시 전에 새로운 기능에 대한 전용 액세스 권한을 얻을 수 있습니다.

>[!IMPORTANT]
>
>Beta 릴리스에는 결함이 포함될 수 있으며 어떠한 종류의 보증도 없이 &quot;있는 그대로&quot; 제공됩니다. Adobe은 베타 릴리스를 유지, 수정, 업데이트, 변경, 수정 또는 기타 지원(Adobe 지원 서비스 또는 기타 방식으로)할 의무가 없습니다. Adobe은 고객에게 베타 릴리스의 올바른 기능이나 성능 또는 관련 설명서나 자료에 의존하지 말고 주의할 것을 권장합니다. Beta의 기능 및 API는 예고 없이 변경될 수 있습니다. 따라서 Beta 릴리스를 사용하는 것은 전적으로 고객 자신의 책임입니다.

[AEM Beta 프로그램](/help/release-notes/release-notes-cloud/release-notes-current.md#aem-beta-programs)도 참조하세요.

현재 제공되는 기회는 다음과 같습니다.

### AEM 작성 및 유연한 게시 계층 구성을 통한 Edge Delivery Services {#eds-with-aem-authoring}

Cloud Manager은 최신 게재 아키텍처를 지원하도록 설계된 두 가지 기능을 도입했습니다.

* **AEM 작성 중인 Edge Delivery Services**
이제 Edge Delivery Services 작성 모드에서 콘텐츠를 계속 작성하면서 AEM을 사용하여 사이트를 제공할 수 있습니다. 워크플로우 환경 설정에 따라 다음 작성 방법 중에서 선택할 수 있습니다.

   * 문서 기반 작성
   * AEM 작성자 기반 작성

자세한 내용은 [Cloud Manager에서 Edge Delivery 사이트 만들기](/help/implementing/cloud-manager/edge-delivery/create-edge-delivery-site.md#one-click-edge-delivery-site)를 참조하십시오.

* **유연한 게시 계층 구성**

이제 Cloud Manager을 사용하여 프로그램에 게시 계층이 필요한지 여부를 구성할 수 있습니다. 이러한 유연성을 통해 선택한 게재 아키텍처에 더 잘 맞는 환경을 설정할 수 있습니다.

자세한 내용은 [유연한 게시 계층(Beta)](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md#flexible-publish-tier)을 참조하십시오.

Beta에 가입하려면 Adobe 조직 ID와 프로그램 ID로 [grp-beta_xwalk-publish_config@adobe.com](mailto:grp-beta_xwalk-publish_config@adobe.com)에 전자 메일을 보내십시오.

### 모듈 캐싱을 통한 빌드 속도 향상 {#quick-build-cm-pipelines}

새 빌드 모델은 모듈 수준 캐싱을 사용하여 전체 저장소가 아닌 변경된 모듈만 컴파일하여 빌드 시간을 단축합니다. 프로덕션 파이프라인에 적용됩니다. **스마트 빌드**&#x200B;를 사용하는 프로덕션 파이프라인을 제어합니다.

자세한 내용은 다음을 참조하십시오.

* [프로덕션 파이프라인에서 Smart Build 사용](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md#about-smart-build).
* [프로덕션 파이프라인을 추가](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md#full-stack-code)합니다.

Beta에 참여하려면 Adobe OrgID와 프로그램 ID로 [beta_quickbuild_cmpipelines@adobe.com](mailto:beta_quickbuild_cmpipelines@adobe.com)에 전자 메일을 보내십시오.

<!-- 
OLD
### Experience Hub Extensibility and Customization {#exp-hub-extensibility}

[Experience Hub](/help/experience-hub.md) serves as your entry point to AEM, customized for your organization's needs. Tell Adobe about your existing AEM UI Extensions so they can help you enable them in Experience Hub with minimal effort.

![Diagram of Experience Hub extensibility and customization workflow](/help/implementing/cloud-manager/release-notes/assets/experience-hub-extensibility-customization.png)

Embed custom experiences in Experience Hub to extend and personalize your organization's dashboard. In addition to Adobe's built-in widgets, add your own using the [UI Extensibility](https://developer.adobe.com/uix/docs/) framework. Build JavaScript-based UI apps and surface them to your users to meet business-specific requirements and workflows. 

Interested in the beta? Email [beta_exphubextensibility@adobe.com](mailto:beta_exphubextensibility@adobe.com) with your Adobe OrgID and a short description of the customization you intend to create.
-->

<!-- 
OLD
### Support for Custom Author Domains in Cloud Service

AEM Cloud Service is going to soon support one custom domain per Author environment.
-->



## 버그 수정 {#bug-fixes}

2026년 4월 Cloud Manager 릴리스에는 중요한 버그 수정이 없습니다.

<!-- ## Known issues {#known-issues} -->

