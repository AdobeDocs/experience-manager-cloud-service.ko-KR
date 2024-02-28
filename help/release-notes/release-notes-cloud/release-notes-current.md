---
title: ' [!DNL Adobe Experience Manager] as a Cloud Service 최신 릴리스 정보'
description: ' [!DNL Adobe Experience Manager] as a Cloud Service 최신 릴리스 정보'
mini-toc-levels: 1
exl-id: a2d56721-502c-4f4e-9b72-5ca790df75c5
source-git-commit: 3a86639d9203fff3c72e63baa8d1499b18a4539f
workflow-type: ht
source-wordcount: '937'
ht-degree: 100%

---

# [!DNL Adobe Experience Manager] as a Cloud Service 최신 릴리스 정보 {#release-notes}

다음 섹션에서는 [!DNL Experience Manager] as a Cloud Service의 최신 버전 기능 릴리스 정보에 대해 간략히 소개합니다.

>[!NOTE]
>
>여기에서 2021년 또는 2022년과 같은 이전 버전의 릴리스 정보로 이동할 수 있습니다.
>
>[!DNL Experience Manager] as a Cloud Service의 향후 기능 활성화에 대해 알아보려면 [Experience Manager 릴리스 로드맵](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html)을 살펴보십시오.

>[!NOTE]
>
>릴리스와 직접적으로 관련되지 않는 설명서 업데이트의 세부 정보는 [최신 설명서 업데이트](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html)를 참조하십시오.

## 릴리스 일자 {#release-date}

[!DNL Adobe Experience Manager] as a [!DNL Cloud Service] 현재 기능 릴리스(2024.1.0)의 릴리스 일자는 2024년 1월 25일입니다. 다음 기능 릴리스(2024.3.0)는 2024년 4월 4일에 예정되어 있습니다.

## 유지 관리 릴리스 정보 {#maintenance}

[ 여기](/help/release-notes/maintenance/latest.md)에서 최신 유지 관리 릴리스 정보를 확인할 수 있습니다.

## 릴리스 비디오 {#release-video}

2024년 1월 릴리스 개요 비디오를 통해 2024.1.0 릴리스에 추가된 기능에 대한 간단한 요약을 살펴보십시오.

>[!VIDEO](https://video.tv.adobe.com/v/3427041?quality=12)

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### AEM Sites의 Extension Manager {#sites-extension-manager}

UI 확장 기능을 구성하여 AEM 설정을 개인화하려면 **[AEM Sites의 새로운 Extension Manager](https://developer.adobe.com/uix/docs/extension-manager/)**&#x200B;를 살펴보십시오.

![AEM Sites의 Extension Manager](/help/assets/sites/extension-manager/homepage.png)

AEM Sites의 Extension Manager를 사용하면 개발자와 실무자가 AEM Sites의 기능을 향상시키기 위해 [Adobe App Builder](https://developer.adobe.com/app-builder/)로 빌드된 [UI 확장 기능](https://developer.adobe.com/uix/docs/)에 액세스하고, 관리하고, 사용자 정의할 수 있습니다.
Extension Manager를 사용하면 다음과 같은 작업을 수행할 수 있습니다.

* 각 인스턴스별로 확장 기능을 활성화하거나 비활성화합니다.
* 확장 기능 매개변수를 구성합니다.
* 확장 기능을 미리 보고 공유 가능한 미리보기 링크를 생성합니다.
* 대화형 데모를 통해 UI 확장 기능을 탐색합니다.
* 자사 확장 기능을 통해 Adobe의 실험 기능에 액세스합니다.

당사는 UI 확장 기능에 대한 피드백과 새로운 사용 사례를 적극적으로 찾고 있습니다. 연결을 원하시면 `uix@adobe.com`으로 이메일을 보내 주십시오.

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### 관리자 보기 프리릴리스 기능 {#admin-view-prerelease}

**지원되는 모든 비디오 유형에 대한 미리보기 렌디션**

Experience Manager Assets는 이제 처리 프로필 구성 없이 기본적으로 지원되는 모든 비디오 유형의 미리보기 렌디션을 생성합니다.

### 자산 보기 {#assets-view-features}

**스마트 태그 차단 목록**

이제 Assets Essentials를 사용하면 자산을 저장소에 업로드할 때 자산에 스마트 태그로 추가하면 안 되는 단어로 구성된 차단 목록을 정의할 수 있습니다. 이 기능은 브랜드 규정 준수를 유지하는 데 도움이 되며 스마트 태그를 조정해야 하는 번거로움을 제거해 줍니다.

![스마트 태그 차단 목록](/help/assets/assets/block-tags.png)


## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

<!-- 

* **Configure a shard for Adobe Sign for AEM Forms**: Adobe distributes Acrobat Sign API around the globe in many deployment units called "shards." Each shard serves a customer's account, such as NA1, NA2, NA3, EU1, JP1, AU1, IN1, and others. The shard names correspond to geographic locations. You can now use more than one shard while using Adobe Sign integration with AEM Forms. 

-->

### 얼리 어답터 프로그램 {#forms-early-adopter}

* **[Adobe Workfront Fusion 시나리오에 적응형 양식 제출](/help/forms/submit-adaptive-form-to-workfront-fusion.md)**: Forms as a Cloud Service는 적응형 양식을 Adobe Workfront와 쉽게 연결할 수 있는 기본 옵션을 제공합니다. 이를 통해 적응형 양식을 Adobe Workfront 시나리오에 제출하는 프로세스가 단순화되며 적응형 양식 제출 시 Workfront Fusion 시나리오를 트리거할 수 있습니다.

* **[오른쪽에서 왼쪽 방향 언어 지원](/help/forms/supporting-new-language-localization-core-components.md)**: 이제 핵심 구성 요소를 기반으로 구축된 적응형 양식을 아랍어, 페르시아어, 우르두어와 같은 오른쪽에서 왼쪽 방향(RTL) 언어로 표시할 수 있습니다. RTL 언어의 사용자는 전 세계적으로 20억 명이 넘습니다. RTL 언어로 된 양식을 사용하면 적응형 양식의 범위를 확장하여 더 다양성 높게 대상자를 수용하고 RTL 시장을 선택할 수 있습니다. 특정 지역에서는 현지 언어로 양식을 제공하는 것이 법적 의무이기도 합니다. 현지 언어를 수용함으로써 더 많은 대상자에게 접근할 수 있을 뿐만 아니라 관련 법률 및 규정을 준수할 수 있습니다.

  ![오른쪽에서 왼쪽 방향 언어 지원](/help/forms/assets/right-to-left-language-support.png)

* **[DocAssurance API(Communication API의 일부)로 문서 보호](/help/forms/aem-forms-cloud-service-communications-introduction.md#document-assurance-doc-assurance)**: DocAssurance API를 사용하여 문서에 서명하고 암호화하여 민감한 정보를 보호할 수 있습니다. 문서의 콘텐츠는 암호화를 통해 읽을 수 없는 포맷으로 변환되어 권한이 있는 사용자만 액세스할 수 있습니다. 이 보호 계층이 강화되면 중요 데이터를 승인되지 않은 사용자로부터 보호할 뿐만 아니라 고객들이 안심할 수 있습니다. 서명 API를 통해 조직에서 배포하고 수신하는 Adobe PDF 문서의 보안 및 개인정보를 보호할 수 있습니다. 이 서비스는 의도한 수신자만 문서를 변경할 수 있도록 디지털 서명과 인증을 사용합니다.

  공식 이메일 ID에서 “`aem-forms-early-adopter-program@adobe.com`”으로 이메일을 보내 얼리 어답터 프로그램에 참여하여 기능에 대한 액세스 권한을 요청할 수 있습니다.

* **[실제 사용자 모니터링(RUM) 데이터 서비스](/help/implementing/cloud-manager/content-requests.md#real-user-monitoring-for-aem-as-a-cloud-service)**를 활용하여 AEM as a Cloud Service에 대한 클라이언트측 컬렉션을 활성화할 수 있습니다.
실제 사용자 모니터링(RUM) 데이터 서비스는 사용자 상호 작용을 보다 정확하게 반영하여 웹 사이트 참여에 대한 안정적인 측정을 보장합니다. 이를 통해 페이지 성능에 대한 고급 인사이트를 얻을 수 있습니다. 이는 Adobe가 관리하는 CDN 또는 Adobe가 관리하지 않는 CDN을 사용하는 고객 모두에게 유용합니다. 또한 Adobe가 관리하지 않는 CDN을 사용하는 고객의 경우 이제 자동화된 트래픽 보고를 활성화할 수 있으므로 트래픽 보고서를 Adobe와 공유할 필요가 없습니다.

  이 새로운 기능을 테스트하고 피드백을 공유하는 데 관심이 있으시면 Adobe ID와 연결된 이메일 주소를 통해 RUM을 활성화하고자 하는 각 환경에 대한 도메인 이름과 함께 `aemcs-rum-adopter@adobe.com`으로 이메일을 보내 주십시오. 그러면 Adobe 제품 팀에서 실제 사용자 모니터링(RUM) 데이터 서비스를 활성화합니다.

## [!DNL Experience Manager] as a [!DNL Cloud Service] Foundation {#foundation}

### Dynatrace에 대한 지원 {#dynatrace}

Dynatrace 고객은 자신의 AEM 사용 현황을 모니터링할 수 있습니다. [애플리케이션 성능 모니터링을 위해 Dynatrace 환경과의 연결을 요청하는 방법](/help/implementing/cloud-manager/dynatrace.md)을 읽어보십시오. 모든 고객이 사용할 수 있는 New Relic APM은 Dynatrace가 활성화되면 데이터 수집을 중단합니다.

### 사이트 테마 및 사이트 템플릿을 사용하는 프론트 엔드 코드에 대한 RDE 지원: 얼리 어답터 프로그램 {#rde-frontend-early-adopter}

[신속한 개발 환경(RDE)](/help/implementing/developing/introduction/rapid-development-environments.md)은 이제 얼리 어답터에 대해 [사이트 테마](/help/sites-cloud/administering/site-creation/site-themes.md) 및 [사이트 템플릿](/help/sites-cloud/administering/site-creation/site-templates.md)을 기반으로 하는 프론트 엔드 코드를 지원합니다. RDE를 사용하면 [프론트 엔드 파이프라인](/help/sites-cloud/administering/site-creation/enable-front-end-pipeline.md)이 아닌 명령줄 지시문을 사용하여 이 작업이 수행됩니다. 사용 후 피드백을 제공하려면 **aemcs-rde-support@adobe.com**&#x200B;으로 연락해 주십시오.

## Cloud Manager {#cloud-manager}

[여기](/help/implementing/cloud-manager/release-notes/current.md)에서 Cloud Manager 월별 릴리스의 전체 목록을 찾을 수 있습니다.

## 마이그레이션 도구 {#migration-tools}

[여기](/help/journey-migration/release-notes/release-notes-migration-tools-current.md)에서 마이그레이션 도구의 전체 목록을 찾을 수 있습니다.

