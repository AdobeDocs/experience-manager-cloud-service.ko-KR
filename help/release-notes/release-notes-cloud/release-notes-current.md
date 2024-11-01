---
title: ' [!DNL Adobe Experience Manager] as a Cloud Service 최신 릴리스 정보'
description: ' [!DNL Adobe Experience Manager] as a Cloud Service 최신 릴리스 정보'
mini-toc-levels: 1
exl-id: a2d56721-502c-4f4e-9b72-5ca790df75c5
feature: Release Information
role: Admin
source-git-commit: d98aa9d206486022d465ca19c8888088562d56c3
workflow-type: tm+mt
source-wordcount: '1395'
ht-degree: 61%

---

# [!DNL Adobe Experience Manager] as a Cloud Service 최신 릴리스 정보 {#release-notes}

다음 섹션에서는 [!DNL Experience Manager] as a Cloud Service의 최신 버전 기능 릴리스 정보에 대해 간략히 소개합니다.

>[!NOTE]
>
>여기에서 2022년 또는 2023년과 같은 이전 버전의 릴리스 정보로 이동할 수 있습니다.
>
>[!DNL Experience Manager] as a Cloud Service의 향후 기능 활성화에 대해 알아보려면 [Experience Manager 릴리스 로드맵](https://experienceleague.adobe.com/ko/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap)을 살펴보십시오.

>[!NOTE]
>
>Experience Cloud 릴리스 정보의 업데이트에 대한 월별 이메일 알림을 받아 보려면 [Adobe 우선 순위 제품 업데이트](https://www.adobe.com/kr/subscription/priority-product-update.html)를 구독하십시오.

## 릴리스 일자 {#release-date}

[!DNL Cloud Service] 현재 기능 릴리스(2024.10.0)인 [!DNL Adobe Experience Manager]의 릴리스 날짜는 2024년 10월 31일입니다. 다음 기능 릴리스(2024.11.0)는 2024년 11월 21일에 예정되어 있습니다.

## 유지 관리 릴리스 정보 {#maintenance}

[ 여기](/help/release-notes/maintenance/latest.md)에서 최신 유지 관리 릴리스 정보를 확인할 수 있습니다.

<!-- ## Release Video {#release-video}

Have a look at the October 2024 Release Overview video for a summary of the features added in the 2024.10.0 release:

>[!VIDEO](https://video.tv.adobe.com/v/3434847?quality=12)

-->

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

**현대화 페이지 이벤트**

이제 다음 AEM Sites 페이지 이벤트를 AEM as a Cloud Service 이벤트 플랫폼을 기반으로 하는 외부에서 사용할 수 있는 이벤트로 사용할 수 있습니다. 이벤트들은 외부 프로세스들과 상호작용하기 위해 Adobe I/O을 통해 처리될 수 있다.
* 페이지 게시됨
* 페이지 게시 취소됨
* 페이지 삭제됨

### 얼리 어답터 프로그램 {#sites-early-adopter}

**변형 생성**

이제 Cloud Service에서 액세스 가능한 AEM의 새로운 기능인 [변형 생성](/help/generative-ai/generate-variations.md)을 통해 GenAI를 활용할 수 있습니다. 변형 생성은 생성형 AI를 사용하여 콘텐츠 제작을 생성하고 확장하는 데 도움이 됩니다. 프로그램 참여를 고려한다면 Adobe 계정 팀에 문의하십시오.

**콘텐츠 조각 배달을 위한 AEM REST OpenAPI**

[콘텐츠 조각 배달용 AEM REST OpenAPI](/help/headless/aem-rest-openapi-content-fragment-delivery.md)를 이제 AEM as a Cloud Service에서 사용할 수 있습니다.

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### Dynamic Media의 얼리 액세스 기능 {#dm-early-access}

**AI 생성 비디오 캡션**

Adobe Dynamic Media의 AI 생성 비디오 캡션은 인공 지능을 통해 비디오 콘텐츠에 대한 캡션을 자동으로 생성합니다. 이 기능은 정확한 실시간 캡션을 제공하여 접근성을 개선하고 사용자 경험을 향상시킬 수 있도록 설계되었습니다. AI는 비디오의 오디오 트랙을 분석하여 음성을 기록하고 캡션을 생성하며, 해당 캡션은 정확성이나 사용자 정의를 위해 편집할 수 있습니다. 이러한 캡션은 접근성 요구 사항을 충족하며, 텍스트 기반 비디오 지원에 의존하거나 이를 선호하는 대상자의 비디오 참여를 개선하는 데 도움이 됩니다.

Dynamic Media 계정에서 AI 생성 캡션 지원에 얼리 액세스하려면 [Adobe 고객 지원 사례를 작성하고 제출](/help/assets/dynamic-media/video.md##enable-dash)하십시오.

### Assets 보기의 새로운 기능 {#assets-view-new-features}

**예약된 보고서**

이제 Assets 보기에서 반복 일정 또는 미래 날짜에 보고서를 자동으로 생성할 수 있으므로 데이터 기반 인사이트를 발견하는 수고를 줄일 수 있습니다.

![예약된 보고서-](/help/assets/assets/scheduled-reports-tab.png)

### Content Hub의 새로운 기능 {#content-hub-new-features}

**사용 허가된 자산에 대한 디지털 권한 관리**

이제 조직은 Content Hub의 사용자에게 라이선스가 부여된 자산에 대한 DRM을 활용하여 라이선스 준수를 높이고, 라이선스 약관이 있는 자산을 공유할 위험을 최소화할 수 있으므로, 라이선스 자산을 다운로드하기 전에 사용자가 라이선스 약관을 검토하고 동의해야 합니다.

![download-multiple-license](/help/assets/assets/download-multiple-license.png)

**자산 카드 메타데이터 구성**

이제 Content Hub을 사용하여 에셋 카드에 표시해야 하는 주요 메타데이터 필드를 최대 6개까지 구성할 수 있습니다.

자산 카드의 ![키 메타데이터](/help/assets/assets/asset-card-key-metadata.png)

**만료된 에셋의 표시 여부 및 다운로드 구성**

이제 관리자는 만료된 자산을 Content Hub에 표시할지 여부를 제어할 수 있습니다. 만료된 자산이 표시되면 사용자가 해당 자산을 다운로드할 수 있는지 여부도 정의할 수 있습니다.

![Content Hub의 만료된 자산](/help/assets/assets/expired-assets-content-hub.png)

## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### AEM Forms의 새로운 프리릴리스 기능 {#forms-new-prerelease-features}

#### 핵심 구성 요소 기반 적응형 양식의 초안 자동 저장

이제 사용자는 부분적으로 완료된 양식을 초안으로 자동 저장하는 자동 저장 기능을 활용할 수 있습니다. 나중에 돌아와 동일한 디바이스 또는 다른 디바이스에서 작성을 마칠 수 있습니다. 이 기능을 통해 사용자가 처음부터 양식을 작성할 필요가 없으므로 양식 폐기를 방지하여 전환율을 높일 수 있습니다.

### AEM Forms의 얼리 액세스 기능 {#forms-new-early-access-features}

AEM Forms 얼리 액세스 프로그램은 최첨단 혁신에 독점적으로 액세스할 수 있는 특별한 기회를 제공하며, 혁신의 발전을 구체화하는 데 도움을 줍니다.

이 릴리스 정보에는 현재 릴리스에서 제공되는 혁신 사항이 나열되어 있습니다. 얼리 액세스 프로그램에서 사용할 수 있는 전체 혁신 목록은 [AEM Forms 얼리 액세스 프로그램 설명서](/help/forms/early-access-ea-features.md)를 참조하십시오.

#### AEM Forms AI 어시스턴트

적응형 양식에 생성형 AI를 사용하면 양식 개발 프로세스에 새로운 수준의 기능과 편의성이 구현됩니다. 그 어느 때보다 빠르게 효율적인 양식을 빌드할 수 있습니다.

![생성형 AI 어시스턴트, 적응형 양식](/help/forms/assets/generative-ai-assistant.png)

제공되는 생성형 AI 기능은 다음과 같습니다.

* **제품 쿼리용 AI 어시스턴트**: AEM 양식 관련 질문에 대한 즉각적인 답변을 얻습니다. AI 어시스턴트는 사용자 개인의 기술 자료로서 플랫폼에서 직접 통찰력 있는 지침 및 권장 사항을 제공합니다.

* **적응형 양식 생성**: 생성형 AI 프롬프트를 사용하여 완전한 양식을 손쉽게 만듭니다. Adobe의 생성형 AI는 드롭오프를 줄이고 경험을 개인화하는 사용자 친화적인 양식을 자동으로 생성합니다.

* **양식용 패널 생성**: 특정 데이터 수집 요구에 맞춰 양식 섹션을 생성합니다. 예를 들어 결제 정보, 고객 선호도, 여행 세부 정보를 수집하는 섹션을 생성합니다.

* **양식 레이아웃 변경**: 생성형 AI 프롬프트를 사용하여 다양한 레이아웃과 디자인을 실험합니다. 마법사 또는 탭 보기 등 다양한 레이아웃을 사용하여 양식에 가장 잘 맞는 디자인을 찾아보십시오. 생성형 AI 프롬프트를 사용하여 모바일 응답성을 위해 양식을 최적화하고 사용자의 마음에 드는 시각적으로 매력적인 양식을 만듭니다.

* **제출 액션 구성**: 생성형 AI 프롬프트를 사용하여 양식의 제출 액션을 간편하게 구성합니다. 사전 빌드된 제출 액션 라이브러리에서 선택하거나, 자체 개발 팀에서 만들고 배포한 사용자 정의 제출 액션에서 선택합니다.

>[!IMPORTANT]
>
> Forms 혁신을 위한 얼리 액세스 프로그램에 참여하는 데 관심이 있으십니까? 공식 주소에서 [aem-forms-ea@adobe.com](mailto:aem-forms-ea@adobe.com)로 관심 있는 기능 목록을 포함하여 이메일을 보내 주십시오.

## CIF 추가 기능 {#cloud-services-cif}

### 버그 수정 {#bug-fixes-cif}

* 핵심 CIF 구성 요소에서 UI 테스트가 제대로 작동하지 않는 문제가 해결되었습니다.
* 카테고리 URL 형식이 클라우드 인스턴스에서 예상대로 작동하지 않는 문제를 해결했습니다.

## [!DNL Experience Manager] as a [!DNL Cloud Service] Foundation {#foundation}

### 고급 네트워킹 옵션을 사용한 셀프서비스 로그 전달 {#log-forwarding}

AEM(Apache/Dispatcher 포함) 및 CDN 로그는 Cloud Manager에서 다운로드할 수 있지만, 많은 조직에서는 이러한 로그를 기본 로깅 대상으로 스트리밍하는 것이 유용할 것으로 생각합니다. AEM은 이제 Azure Blob Storage, Datadog, HTTPS, Elasticsearch(및 OpenSearch) 및 Splunk에 대한 [로그 전달](/help/implementing/developing/introduction/log-forwarding.md)을 지원합니다. AEM 로그는 전용 IP 주소 사용과 같은 고급 네트워킹 구성을 통해 선택적으로 전달할 수 있습니다.

이 기능은 사용자가 셀프서비스 방식으로 구성하고 [구성 파이프라인](/help/operations/config-pipeline.md)을(를) 사용하여 배포합니다.

### 비즈니스 사용자를 위한 파이프라인 없는 URL 리디렉션 {#pipeline-free-redirects}

브라우저 측 리디렉션은 웹 페이지가 다운되었거나 이동된 경우 또는 기타 시나리오에서 유용합니다. [파이프라인 없는 URL 리디렉션](/help/implementing/dispatcher/pipeline-free-url-redirects.md)을 사용하면 Apache 재작성 맵 파일을 AEM 게시 위치에 배치할 수 있습니다. 이 위치에서 파일은 자동으로 로드되므로 소스 제어에 커밋하거나 Cloud Manager 파이프라인을 시작할 필요가 없습니다.

재작성 파일을 게시하는 옵션에는 자산으로 업로드, ACS Commons 재작성 맵 관리자 사용 또는 사용자 지정 사용자 인터페이스와의 상호 작용이 포함됩니다.

### RDE에 대한 파이프라인 구성 {#config-pipeline-rdes}

신속한 개발 환경은 클라우드 환경에서 코드 및 구성을 신속하게 배포하고 테스트하는 강력한 도구입니다. 이제 RDE는 트래픽 필터 규칙 및 요청/응답 변환과 같은 CDN 설정과 로그 전달 및 기타 구성 옵션을 포함하여 [구성 YAML-파일의 동기화](/help/implementing/developing/introduction/rapid-development-environments.md#deploy-config-pipeline)를 지원합니다. 자세한 내용은 지원되는 구성 옵션의 전체 목록을 [참조하십시오](/help/operations/config-pipeline.md).

### 새 제품 프로필 {#new-product-profiles}

새 AEM 환경이 생성되면 제품 프로필이 자동으로 Adobe Admin Console에 표시되므로 관리자는 라이선스가 부여된 솔루션 및 기능에 대한 액세스 권한을 할당할 수 있습니다.

이제 새 환경에는 업데이트된 제품 프로필 세트가 포함되어 있어 Adobe Developer Console에서 API 자격 증명 생성을 포함하여 향후 기능과 호환될 수 있습니다. 기존 환경은 향후 릴리스에서 제품 프로필을 업데이트할 수 있습니다. [자세히 알아보기](/help/onboarding/aem-cs-team-product-profiles.md).

### 새로운 AEM Developer Console (공개 Beta) {#aem-developer-console-beta}

클라우드 환경에서 코드 디버깅을 위한 보다 인터랙티브한 경험을 제공하는 개선된 [AEM Developer Console](/help/implementing/developing/introduction/aem-developer-console.md)을 사용해 보십시오.

현재 AEM Developer Console에서 *새 콘솔 사용 가능* 버튼을 클릭하여 누구나 공개 Beta에 액세스할 수 있습니다. Adobe에서는 피드백을 환영합니다. 피드백은 **<aemcs-new-devconsole-ui-beta@adobe.com>**&#x200B;으로 이메일을 보내주십시오.

![AEM Developer Console의 OSGi 번들 화면](/help/implementing/developing/introduction/assets/osgi-bundles.png)

## [!DNL Experience Manager] 안내서 {#guides}

[여기](https://experienceleague.adobe.com/ko/docs/experience-manager-guides/using/release-info/release-notes/cloud-release-notes/2024-releases/2406-release/whats-new-2024-06-0)에서 Adobe Experience Manager Guides 최신 릴리스의 새로운 기능과 향상된 기능의 전체 목록을 찾을 수 있습니다.

## Cloud Manager {#cloud-manager}

[여기](/help/implementing/cloud-manager/release-notes/current.md)에서 Cloud Manager 월별 릴리스의 전체 목록을 찾을 수 있습니다.

## 마이그레이션 도구 {#migration-tools}

[여기](/help/journey-migration/release-notes/release-notes-migration-tools-current.md)에서 마이그레이션 도구의 전체 목록을 찾을 수 있습니다.

## 범용 편집기 {#universal-editor}

[여기](/help/release-notes/universal-editor/current.md)에서 범용 편집기의 전체 목록을 찾을 수 있습니다.

## 변형 생성 {#generate-variations}

[여기](/help/generative-ai/release-notes-generate-variations.md)에서 변형 생성의 전체 목록을 찾을 수 있습니다.

## Experience Cloud 릴리스 정보 {#experience-cloud}

다른 Experience Cloud 애플리케이션 릴리스에 대한 정보는 [여기](https://experienceleague.adobe.com/ko/docs/release-notes/experience-cloud/current)에서 확인할 수 있습니다.
