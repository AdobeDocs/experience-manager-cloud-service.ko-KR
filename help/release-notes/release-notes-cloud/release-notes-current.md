---
title: ' [!DNL Adobe Experience Manager] as a Cloud Service 최신 릴리스 정보'
description: ' [!DNL Adobe Experience Manager] as a Cloud Service 최신 릴리스 정보'
mini-toc-levels: 1
exl-id: a2d56721-502c-4f4e-9b72-5ca790df75c5
feature: Release Information
role: Admin
source-git-commit: 0c2d61f05d8a6adea1116406b18aa1245ff701d1
workflow-type: tm+mt
source-wordcount: '2156'
ht-degree: 28%

---

# [!DNL Adobe Experience Manager] as a Cloud Service 최신 릴리스 정보 {#release-notes}

다음 섹션에서는 [!DNL Experience Manager] as a Cloud Service의 최신 기능 릴리스 정보에 대해 간략히 소개합니다.

>[!NOTE]
>
>여기에서 2023년 또는 2024년과 같은 이전 버전의 릴리스 정보로 이동할 수 있습니다.
>
>[!DNL Experience Manager] as a Cloud Service의 향후 기능 활성화에 대해 알아보려면 [Experience Manager 릴리스 로드맵](https://experienceleague.adobe.com/ko/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap)을 살펴보십시오.

>[!NOTE]
>
>Experience Cloud 릴리스 정보의 업데이트에 대한 월별 이메일 알림을 받아 보려면 [Adobe 우선순위 제품 업데이트](https://www.adobe.com/kr/subscription/priority-product-update.html)를 구독하십시오.

## 릴리스 일자 {#release-date}

[!DNL Adobe Experience Manager] as a [!DNL Cloud Service]의 현재 기능 릴리스(2026.3.0) 일자는 2026년 3월 26일 금요일입니다. 다음 기능 릴리스(2026.4.0)는 2026년 4월 30일에 예정되어 있습니다.

## 유지 관리 릴리스 정보 {#maintenance}

[여기](/help/release-notes/maintenance/latest.md)에서 최신 유지 관리 릴리스 정보를 확인할 수 있습니다.

<!--  ## Release Video {#release-video}

Have a look at the March 2026 Release Overview video for a summary of the features added in the 2026.3.0 release:

>[!VIDEO](https://video.tv.adobe.com/v/3480399/?quality=12)

-->

## AEM Beta 프로그램 {#aem-beta-programs}

Adobe Experience Manager(AEM) 베타 프로그램은 고객이 프리릴리스 기능과 코드에 액세스하고, 피드백을 제공하고, AEM의 미래를 안내할 수 있는 방법입니다.

>[!IMPORTANT]
>
>Beta 릴리스에는 결함이 포함될 수 있으며 어떠한 종류의 보증도 없이 &quot;있는 그대로&quot; 제공됩니다. Adobe은 베타 릴리스를 유지, 수정, 업데이트, 변경, 수정 또는 기타 지원(Adobe 지원 서비스 또는 기타 방식으로)할 의무가 없습니다. Adobe은 고객에게 베타 릴리스의 올바른 기능이나 성능 또는 관련 설명서나 자료에 의존하지 말고 주의할 것을 권장합니다. Beta의 기능 및 API는 예고 없이 변경될 수 있습니다. 따라서 Beta 릴리스를 사용하는 것은 전적으로 고객 자신의 책임입니다.

**참여의 이점**

Adobe이 개발 중인 기능에 일찍 액세스하면 고객과 파트너가 피드백을 제공하고 제품 개발을 구체화할 수 있습니다. 또한 GA 전에 새로운 기능을 채택할 준비를 하는 데 도움이 됩니다.

**현재 베타 프로그램**

다음 섹션에는 활성 Beta 프로그램이 나와 있습니다.

### AEM의 에이전트 {#agents-in-aem}

프로덕션, 거버넌스, 최적화, 검색 및 개발 전반에 걸쳐 강력하고 새로운 AEM 에이전트 기능을 살펴보려면 [여기에서 액세스하는 방법에 대해 알아보십시오.](/help/ai-in-aem/agents/overview.md)

<!--
### Agents in AEM (Explorer program) {#agents-in-aem-beta-program}

Gain early access to powerful, new AEM agentic capabilities across production, governance, optimization, discovery, and development. Your feedback directly shapes Adobe's roadmap and final features. See [Overview of Agents in AEM](/help/ai-in-aem/agents/overview.md) to learn more.

This program typically lasts 4-6 weeks, but can be tailored to be flexible around your ability to actively participate. 

To opt in to participate in this program, email [aemagentsteam@adobe.com](mailto:aemagentsteam@adobe.com) and include the following details to the extent possible:

* Names and Adobe ID's of team members who will actively use agents.
* List Specific agents that you or your team will want to use. Or simply say "All Agents."

Customers selected for participation will be notified directly by Adobe. Participation is subject to eligibility considerations, including customer licensing and limited program capacity. While not all requests can be accommodated initially, additional customers may be considered in future beta waves.
-->

### AEM Foundation(Beta 프로그램) {#aem-foundation-beta-programs}

[AEM Foundation Beta 프로그램](#foundation-early-adopter)을 참조하세요.

### Cloud Manager (Beta 프로그램) {#cloud-manager-beta-programs}

[Cloud Manager 베타 프로그램](/help/implementing/cloud-manager/release-notes/current.md)을 참조하세요.

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### 컨텐츠 조각 체크아웃/ {#cf-checkout-in}

AEM Touch UI와의 패리티를 개선하기 위해 이제 콘텐츠 조각을 새 콘텐츠 조각 관리 UI를 사용하여 체크아웃하고 다시 체크인할 수 있습니다. 체크아웃 기능은 변경되지 않으므로 체크아웃 콘텐츠 조각을 효과적으로 잠가서 다른 사용자가 콘텐츠 조각 편집기에서 편집할 수 없습니다. 콘텐츠 조각을 소유한 사용자와 관리자는 조각을 체크아웃한 후 다시 로그인할 수 있습니다. 조각을 확인해도 참조된 하위 조각 또는 자산에는 영향을 주지 않습니다.

### 컨텐츠 조각 실행 작업 패널 {#cf-launches-jobs}

이제 콘텐츠 조각 시작에 대한 비동기 작업을 콘텐츠 조각 시작 관리자 UI의 속성 패널에서 보고 상태를 확인할 수 있습니다(작업이 아직 실행 중이거나, 완료되었거나, 중단되었을 경우). 작업에 대한 관련 세부 정보 또한 함께 표시됩니다.

### 콘텐츠 조각 편집기의 RTE 업데이트 {#cf-rte-update}

콘텐츠 조각 편집기의 리치 텍스트 편집기(RTE)가 TinyMCE에서 TipTap으로 마이그레이션되었습니다. 이러한 변화는 많은 이점을 가져다 줍니다.

* 이제 범용 편집기 와 콘텐츠 조각 편집기 는 동일한 RTE 기술 스택을 사용합니다.
   * 즉, 이제 두 편집기에서 동일한 HTML을 생성합니다.
   * 이제 확장을 재사용할 수 있습니다.
   * 이제 두 편집기를 모두 사용하여 동일한 기능과 메서드를 사용할 수 있습니다(Headless 사용 사례).
   * 궁극적인 목표는 한 구성이 두 편집기에서 통합된 경험을 제공하는 것입니다.
* 이제 콘텐츠 편집기에는 스펙트럼 2 스타일의 새로운 모양과 느낌이 있습니다.
* 콘텐츠 조각 편집기에서 찾기 및 바꾸기, 콘텐츠 관리자 지원 등 새로운 기능을 사용할 수 있습니다.

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

**AEM Sites의 콘텐츠 관리자**

이제 AEM Sites에서 Content Advisor를 사용할 수 있으며, AEM Assets에서 바로 지능형 에셋 검색을 도입할 수 있습니다. 이를 통해 사용자는 워크플로우 내에서 가장 관련성이 높은 에셋을 손쉽게 검색, 탐색 및 재사용할 수 있으므로 컨텍스트를 전환할 필요가 없습니다.

Content Advisor는 캠페인 개요 기반 제안, 상황별 제안, Dynamic Media 렌디션에 대한 액세스 권한 및 세부 에셋 메타데이터와 같은 에셋에 대한 지능형 기능을 제공합니다.

준비 중 - 콘텐츠 조각 검색 기능을 포함하여 Adobe Workfront 및 AJO B2C 애플리케이션에 대한 콘텐츠 관리자 지원

### Dynamic Media의 새로운 기능 {#dynamic-media-new-features}

#### Dynamic Media 템플릿 편집기 업데이트 {#dynamic-media-template-editor-updates}

**레이어 관리 개선 사항**

* 드래그 앤 드롭 레이어 재정렬: 이제 드래그하여 [레이어] 패널에서 직접 레이어를 재정리할 수 있으므로 보다 빠르고 직관적으로 기존의 앞으로 가져오기 또는 뒤로 보내기 작업 이상으로 레이어 겹침 순서를 구성할 수 있습니다.
* 복사, 붙여넣기 및 복제: 다중 레이어 선택 기능을 지원하고 키보드 단축키(Cmd/Ctrl+C, V, D) 또는 컨텍스트 메뉴를 사용하여 레이어를 복사, 붙여넣기 및 복제하는 모든 기능을 지원합니다.
* 별도의 레이어 속성 단추: 레이어 설정을 쉽게 탐색할 수 있도록 전용 레이어 속성 단추를 추가했습니다. 또한 빠른 액세스를 위해 레이어를 두 번 클릭할 수 있도록 지원합니다.

**텍스트 서식 기능**

* 선 간격 제어: 새로운 선 간격 슬라이더를 사용하면 실행 취소/다시 실행 및 템플릿 저장/로드를 비롯한 전체 지원을 통해 텍스트 레이어의 선 높이를 정확하게 제어할 수 있습니다.
* 모든 대문자 서식: 이제 텍스트 레이어에서 굵게, 기울임꼴 및 밑줄과 함께 글꼴 스타일 도구 모음의 모든 대문자 서식 옵션을 지원합니다.
* 수직 정렬 옵션: 텍스트 레이어에 대한 수직 정렬 컨트롤을 추가하여 텍스트 상자 내에 더 정밀한 텍스트 위치를 제공합니다.

**크기 및 Dimension 컨트롤**

* 종횡비 잠금 해제: 사용자는 이제 크기 속성을 조정할 때 종횡비의 잠금을 해제할 수 있으므로 폭 및 높이를 독립적으로 조정하여 보다 유연한 레이어 크기 조정을 가능하게 합니다.
* 자동 맞춤 줄 구성: 텍스트 자동 맞춤 속성에 `copyfitlines` 및 `copyfitmaxlines` 설정에 대한 지원을 추가하여 텍스트 맞춤 동작을 보다 세밀하게 제어할 수 있습니다.

**비주얼 폴란드어**

* 개선된 스펙트럼 2(S2) 디자인 시스템 아이콘으로 타이머 및 모양 레이어의 아이콘을 업데이트했습니다.

## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### AEM Forms의 얼리 액세스 기능 {#forms-early-access-features}

**제출 PDF에서 다중 선택 드롭다운에 대한 레이블 표시**
이제 적응형 Forms의 다중 선택 드롭다운 구성 요소가 [생성된 제출 PDF](/help/forms/generate-document-of-record-core-components.md)에서 선택한 표시 레이블을 렌더링하여 문서가 양식에 표시되는 내용을 정확하게 반영하도록 합니다.

**확인란, 라디오 단추 및 패널 구성 요소에 대한 액세스 가능성 향상**
적응형 Forms 핵심 구성 요소에는 [확인란 그룹(v2)](https://experienceleague.adobe.com/ko/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/checkbox-group), [라디오 단추 그룹(v2)](https://experienceleague.adobe.com/ko/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/radio-button) 및 [패널 구성 요소](https://experienceleague.adobe.com/ko/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/panel)에 대한 WCAG 2.2 호환 의미 체계 마크업이 도입됩니다. 이러한 구성 요소는 `<fieldset>` 및 `<legend>` HTML 요소를 활용하여 그룹 레이블과 해당 옵션 간에 의미 있는 관계를 설정하므로 화면 판독기와 기타 보조 기술이 정확하게 해석할 수 있습니다.

**Forms Manager에서 버전 관리 지원**
이제 Forms Manager [적응형 Forms(핵심 구성 요소 및 기초 구성 요소)](/help/forms/manage-form-versions-forms-manager.md), 양식 단편, 테마, XDP 템플릿 및 이진 자산에 대한 버전 관리를 지원합니다. Forms 및 문서 콘솔에서 직접 버전을 만들고, 전체 버전 기록을 보고, 양식 에셋의 이전 상태를 복원할 수 있습니다.

## [!DNL Experience Manager] as a [!DNL Cloud Service] Foundation {#foundation}

### [!DNL Experience Manager] as a [!DNL Cloud Service] Foundation 새 기능 {#foundation-new}

#### 간소화된 색인 관리 {#simplified-index-management}

[간소화된 색인 관리](https://oak-indexing.github.io/oakTools/simplified.html)에서는 전체 정의를 복사하거나 버전을 수동으로 관리하지 않고도 하나의 JSON 파일을 사용하여 사용자 지정 색인을 정의하고 기본 제공(OOTB) 색인을 사용자 지정하는 간단한 방법을 제공합니다. 맞춤화는 최신 OOTB 인덱스와 병합되며 필요한 경우 새 인덱스 버전이 만들어집니다.

#### Cloud Manager 서버 {#cm-mcp-server}

>[!VIDEO](https://video.tv.adobe.com/v/3480340/?quality=12)

최신 IDE는 MCP(Model Context Protocol)를 사용하여 대형 언어 모델(LLM)이 MCP 서버에 의해 노출된 도구를 호출할 수 있도록 합니다. 개발자는 낮은 수준의 API 사양과 직접 통합하는 대신 단순히 의도를 자연어로 설명할 수 있습니다.

Cloud Manager MCP 서버를 사용하면 프롬프트를 사용하여 IDE에서 직접 Cloud Manager API와 상호 작용할 수 있습니다. 지원되는 시나리오에는 파이프라인 실행, 환경 상태 확인 등이 포함됩니다.

[AEM MCP 서버](/help/ai-in-aem/mcp-support/using-mcp-with-aem-as-a-cloud-service.md)에 대해 자세히 알아보세요.

### [!DNL Experience Manager] Foundation 중요 알림으로서의 [!DNL Cloud Service] {#foundation-notices}

#### Java API 사용 중단 {#java-api-deprecation}

2026/2/26/2026 제거를 대상으로 하는 더 이상 사용되지 않는 API는 코드에서 더 이상 사용되지 않아야 합니다. 배포 차단을 방지하려면 **2026년 3월 30일** 전에 API 사용을 제거하십시오. 중요 날짜:

* **2026년 1월 26일부터**: 작업 센터 알림 전자 메일이 이러한 API 사용을 제거하기 위한 미리 알림으로 전송됩니다.
* **2026년 2월 26일**: 이러한 API를 사용하는 코드가 포함된 Cloud Manager 파이프라인은 **코드 품질** 단계 동안 **일시 중지**&#x200B;됩니다. 배포 관리자, 프로젝트 관리자 또는 비즈니스 소유자는 파이프라인을 진행할 수 있도록 문제를 재정의할 수 있습니다. *이로 인해 코드 변경 내용의 유효성을 검사하고 해제하는 기능이 느려질 수 있습니다.*
* **2026년 3월 30일**: 이러한 API를 사용하는 코드가 포함된 Cloud Manager 파이프라인은 **코드 품질** 단계 동안 **실패**&#x200B;됩니다. 더 이상 사용되지 않는 API 사용이 제거될 때까지 배포가 차단됩니다. *시간이 중요한 업데이트를 릴리스할 수 없으며 비즈니스 운영에 영향을 줄 수 있습니다.*
* **2026년 5월 4일**: 더 이상 사용되지 않는 API를 사용하는 환경은 중요한 Adobe 릴리스 업데이트를 받지 않습니다&#x200B;**. 따라서 성능 및 가용성에 대한 Adobe의 표준 약정이 적용되지 않습니다.** 그 결과, 새로운 기능이나 버그 수정을 받지 않고, 애플리케이션 안정성과 가동 시간에 부정적인 영향을 미치고, 보안 위험 노출이 더 증가할 수 있습니다.

[사용 중단 문서](/help/release-notes/deprecated-removed-features.md#aem-apis)에서 자세한 내용을 확인할 수 있으며, 편의를 위해 아래에 해당 API 목록을 제공합니다.

+++ 확장하여 사용 중단 Java API 보기

* `org.apache.sling.commons.auth`
* `org.apache.felix.webconsole`
* `org.eclipse.jetty`
* `com.mongodb`
* `org.apache.abdera`
* `org.apache.felix.http.whiteboard`
* `org.apache.cocoon.xml`
* `ch.qos.logback`
* `org.slf4j.spi`
* `org.slf4j.event`
* `org.apache.log4j`
* `com.google.common`
* `com.drew`
* `org.apache.jackrabbit.oak.plugins.memory`

+++

### [!DNL Experience Manager] as a [!DNL Cloud Service] Foundation 얼리 어답터 기능 {#foundation-early-adopter}

#### AEM Java 및 Dispatcher 개발을 위한 IDE AI 도구(공개 Beta 프로그램) {#ai-dev-beta}

Java 스택 팀은 기능 전달 속도를 높이고 코드 품질을 개선하기 위해 Cursor, Claude Code, Visual Studio 및 IntelliJ와 같은 도구에서 AI 지원 개발을 점점 더 많이 사용하고 있습니다.

공개 Beta에 참여하여(가입이 필요하지 않음) 코딩 에이전트가 AEM 코드 및 Dispatcher 구성을 생성 및 디버깅하는 데 사용할 수 있는 IDE 도구를 사용해 보십시오.

자세한 내용은 [AI 도구를 사용한 로컬 개발](/help/ai-in-aem/local-development-with-ai-tools.md) 베타 설명서 및 질문 또는 피드백이 포함된 이메일 [aemcs-ai-ide-tools-feedback@adobe.com](mailto:aemcs-ai-ide-tools-feedback@adobe.com)을 참조하세요.

#### AEM Edge 기능(Beta 프로그램) {#edge-functions}

AEM Edge 함수를 사용하면 CDN 계층에서 JavaScript을 실행할 수 있으므로 데이터 처리가 최종 사용자에게 더 가까워집니다. 이렇게 하면 지연 시간이 줄어들고 에지에서 반응성이 뛰어나고 역동적인 경험을 할 수 있습니다.

일반적인 사용 사례는 다음과 같습니다.

* 지리적 위치, 디바이스 유형 또는 사용자 속성에 따라 콘텐츠 개인화
* CDN과 원본 사이의 미들웨어 역할
* 브라우저에 제공하기 전에 서드파티 API의 응답(및 여러 API 응답 집계)을 다시 포맷
* 다양한 백엔드에서 결합된 콘텐츠를 사용하여 에지에서 서버 렌더링 HTML을 구성하고 제공
* ChatGPT 및 Claude와 같은 LLM을 위한 MCP 서버를 사용자 정의 도구에 액세스하도록 노출

라이브 프로덕션 사이트를 위한 AEM Publish Delivery 또는 Edge Delivery Services 프로젝트에 사용할 수 있는 기회는 제한적입니다. 참여에 관심이 있거나 보다 자세히 알아보려면 사용 사례에 대한 간략한 설명과 함께 [aemcs-edgecompute-feedback@adobe.com](mailto:aemcs-edgecompute-feedback@adobe.com)으로 이메일을 보내 주시기 바랍니다.

#### 개발 에이전트를 사용한 웹 계층 구성 파이프라인 문제 해결(Beta 프로그램) {#devagent-webtier}

개발 에이전트의 [파이프라인 문제 해결](/help/ai-in-aem/agents/brand-experience/development/development.md) 기능을 사용하면 개발자가 AEM as a Cloud Service 배포에서 문제를 효율적으로 진단하고 해결할 수 있습니다. 개발 에이전트는 이제 전체 스택 파이프라인(배포 및 코드 품질)을 지원하는 것 외에도 Beta 프로그램의 일부로 **웹 계층 구성 파이프라인**&#x200B;에 대한 문제 해결을 지원합니다.

Beta에 대한 액세스를 요청하려면 [aem-devagent@adobe.com](mailto:aem-devagent@adobe.com)에 전자 메일을 보내십시오. AEM의 에이전트에 대한 기존 액세스 권한이 필요합니다.

#### AEM 6.5에서 AEM Cloud Service로 마이그레이션하기 위한 IDE AI 도구(Alpha 프로그램) {#cm-ide-migration}

IDE AI 도구를 사용하여 [모범 사례 분석기 보고서](/help/journey-migration/best-practices-analyzer/overview-best-practices-analyzer.md)의 권장 사항에 따라 활동하여 AEM 6.5에서 AEM as a Cloud Service(Java 스택)으로 마이그레이션을 가속화하십시오.

자세한 내용은 [aemcs-ai-ide-tools-feedback@adobe.com](mailto:aemcs-ai-ide-tools-feedback@adobe.com)(으)로 전자 메일을 보내십시오.

#### Edge Delivery Services에 대한 Edge 인증(Beta 프로그램) {#edge-authentication}

Edge 인증을 사용하면 ID 공급자(IdP)로 인증된 사용자만 Edge Delivery Services 페이지에 액세스하도록 제한할 수 있습니다. 이 작업은 OpenID Connect(OIDC) 구성 YAML 파일을 배포하는 방법으로 수행됩니다.

원하는 경우 사용 사례에 대한 간단한 설명과 질문을 담은 이메일을 [aemcs-edgecompute-feedback@adobe.com](mailto:aemcs-edgecompute-feedback@adobe.com)에 보내십시오.

#### 라이브 트래픽을 수락하기 전에 코드 테스트를 위한 카나리아 프로덕션 배포(Beta 프로그램) {#canary-beta}

최종 사용자에게 노출하기 전에 내부용 테스트 트래픽으로 프로덕션 빌드의 유효성을 검사합니다. 프로덕션으로 배송하고, 카나리아 트래픽만 라우팅하고(특수 헤더 사용), 동작을 모니터링한 다음 라이브 트래픽으로 승격하거나 고객에게 영향을 주지 않고 롤백합니다.

코드 릴리스를 프로덕션에 배포하되, 라이브 트래픽을 수락할지 아니면 롤백할지 여부를 결정하기 전에 내부 테스트 트래픽으로만 이를 제한합니다.

액세스를 요청하고 피드백을 공유하려면 [aemcs-canary-deployments-beta@adobe.com](mailto:aemcs-canary-deployments-beta@adobe.com)에 이메일을 보내십시오.

#### RDE용 스냅샷(Beta 프로그램) {#rde-snapshot-program}

Beta에서 RDE(빠른 개발 환경)는 이제 코드 및 컨텐츠의 현재 상태에 대한 스냅샷을 생성하는 기능을 지원하며 나중에 복원할 수 있습니다. 이것은 반환이 필요할 수 있는 코드를 동기화하거나, 서로 다른 기능의 개발을 전환할 때 유용할 수 있습니다. 테스트를 위한 알려진 시작점으로 변경 가능한 콘텐츠만 복원하는 것도 가능합니다.

이 기능에 대한 사용 및 피드백 제공에 관심이 있는 경우 [aemcs-rde-support@adobe.com](mailto:aemcs-rde-support@adobe.com)에 전자 메일을 보내십시오.

#### 애플리케이션 성능 모니터링(APM) 기능 확장(Alpha 프로그램) {#apm-alpha}

AEM Cloud Service는 가시성 확보를 위해 현재 Adobe에서 제공하는 [New Relic One](https://experienceleague.adobe.com/ko/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/user-access-new-relic) 및 고객이 관리하는 [Dynatrace](https://experienceleague.adobe.com/ko/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/dynatrace)를 지원합니다. 추가 APM 옵션에 대한 지원을 살펴볼 때 사용 사례와 함께 선호하는 공급업체 또는 기술을 명시한 이메일을 [aemcs-apm-beta@adobe.com](mailto:aemcs-apm-beta@adobe.com)에 보내십시오.

## [!DNL Experience Manager] 안내서 {#guides}

[여기](https://experienceleague.adobe.com/ko/docs/experience-manager-guides/using/release-info/aem-guides-releases-roadmap)에서 Adobe Experience Manager Guides 최신 릴리스의 새로운 기능과 향상된 기능의 전체 목록을 찾을 수 있습니다.

## Cloud Manager {#cloud-manager}

[여기](/help/implementing/cloud-manager/release-notes/current.md)에서 Cloud Manager 월별 릴리스의 전체 목록을 찾을 수 있습니다.

## 마이그레이션 도구 {#migration-tools}

[여기](/help/journey-migration/release-notes/release-notes-migration-tools-current.md)에서 마이그레이션 도구의 전체 목록을 찾을 수 있습니다.

## 범용 편집기 {#universal-editor}

[여기](/help/release-notes/universal-editor/current.md)에서 범용 편집기의 전체 목록을 찾을 수 있습니다.

## 변형 생성 {#generate-variations}

[여기](/help/generative-ai/release-notes-generate-variations.md)에서 변형 생성의 전체 목록을 찾을 수 있습니다.

## Experience Cloud 릴리스 정보 {#experience-cloud}

기타 Experience Cloud 애플리케이션 릴리스에 대한 정보는 [여기](https://experienceleague.adobe.com/ko/docs/release-notes/experience-cloud/current)에서 확인할 수 있습니다.
