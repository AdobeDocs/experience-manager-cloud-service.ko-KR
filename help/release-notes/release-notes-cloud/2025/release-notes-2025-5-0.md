---
title: ' [!DNL Adobe Experience Manager] as a Cloud Service의 2025.5.0 릴리스 정보입니다.'
description: ' [!DNL Adobe Experience Manager] as a Cloud Service의 2025.5.0 릴리스 정보입니다.'
feature: Release Information
role: Admin
source-git-commit: df16d5c7ee666f563cf4bbc861df4210318f7f36
workflow-type: tm+mt
source-wordcount: '2108'
ht-degree: 97%

---

# [!DNL Adobe Experience Manager] as a Cloud Service 2025.5.0 릴리스 정보 {#release-notes}

다음 섹션에서는 [!DNL Experience Manager] as a Cloud Service의 2025.5.0 버전 기능 릴리스 정보에 대해 간략히 소개합니다.

>[!NOTE]
>
>여기에서 2023년 또는 2024년과 같은 이전 버전의 릴리스 정보로 이동할 수 있습니다.
>
>[!DNL Experience Manager] as a Cloud Service의 향후 기능 활성화에 대해 알아보려면 [Experience Manager 릴리스 로드맵](https://experienceleague.adobe.com/ko/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap)을 살펴보십시오.

>[!NOTE]
>
>Experience Cloud 릴리스 정보의 업데이트에 대한 월별 이메일 알림을 받아 보려면 [Adobe 우선순위 제품 업데이트](https://www.adobe.com/kr/subscription/priority-product-update.html)를 구독하십시오.

## 릴리스 일자 {#release-date}

[!DNL Adobe Experience Manager] as a [!DNL Cloud Service]의 현재 기능 릴리스(2025.5.0) 일자는 2025년 6월 5일입니다. 다음 기능 릴리스(2025.6.0)는 2025년 6월 26일에 예정되어 있습니다.

## 유지 관리 릴리스 정보 {#maintenance}

[ 여기](/help/release-notes/maintenance/latest.md)에서 최신 유지 관리 릴리스 정보를 확인할 수 있습니다.

## 릴리스 비디오 {#release-video}

2025년 5월 릴리스 개요 비디오를 통해 2025.5.0 릴리스에 추가된 기능에 대한 간단한 요약을 살펴보십시오.

>[!VIDEO](https://video.tv.adobe.com/v/3464357?quality=12&captions=kor)

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

**AI 생성 메타데이터**

이제 AEM Assets는 [AI를 사용하여 제목, 설명, 키워드를 포함한 메타데이터를 자동으로 생성합니다](/help/assets/metadata-assets-view.md#ai-smart-tags). 이러한 AI 생성 필드는 메타데이터의 정확도를 높여 자산을 검색, 분류 및 추천하기 쉽게 만듭니다. 이 접근 방식은 수동 태그 지정을 제거하여 효율성을 향상시킬 뿐만 아니라 방대한 양의 디지털 콘텐츠에 대한 일관성과 확장성을 보장합니다.

![AI 생성 메타데이터](/help/assets/assets/enhanced-smart-tags.png)

**Figma와의 통합**

AEM Assets는 Figma에 기본적으로 통합되므로 디자이너는 Figma 사용자 인터페이스 내에서 AEM Assets에 저장된 자산에 직접 액세스할 수 있습니다. AEM Assets에서 관리되는 콘텐츠를 Figma 캔버스에 배치한 다음 AEM Assets 저장소에 새 콘텐츠 또는 편집된 콘텐츠를 저장할 수 있습니다. Figma 커뮤니티 페이지에서 제공되는 AEM Assets Connector에 액세스하려면 [여기](https://www.figma.com/community/plugin/1512561378275712210/adobe-experience-manager-aem-assets-connector)를 클릭하십시오.

>[!VIDEO](https://video.tv.adobe.com/v/3463828)


### Content Hub의 새로운 기능 {#new-features-content-hub}

**속성 기반 액세스 제어(ABAC)**

[이제 Content Hub를 사용하면 자산에 접근하기 위해 규칙 기반 제한을 적용할 수 있습니다](/help/assets/attribute-based-access-control.md). 에셋 권한은 거버넌스를 보장하며 사용자가 관련 에셋만 액세스할 수 있도록 합니다.

자산 제한 규칙은 메타데이터를 기반으로 하며, 규칙에 정의된 조건이 자산 메타데이터와 일치하면 자산이 사용자 그룹에 표시됩니다.

속성 기반 액세스 제어의 주요 이점은 다음과 같습니다.

* 폴더 구조에 대한 권한 종속을 제거합니다.

* 관리자가 자산을 업로드하고 권한 구조를 소급적으로 결정할 수 있도록 합니다.

* 중복 횟수를 줄여 자산 무결성을 향상시킵니다. 폴더 기반 권한에서는 동일한 자산이 다른 그룹과 공유될 때 중복이 필요합니다.

**UI 브랜딩**

이제 Content Hub를 통해 관리자는 배너 이미지, 배너 제목, 본문 텍스트, 기본 및 보조 색상 등 [브랜드별 요소를 사용하여 사용자 인터페이스를 사용자 정의](/help/assets/configure-content-hub-ui-options.md##configure-branding-content-hub)할 수 있습니다. 이러한 개선 사항은 브랜드 일관성을 보장하고 사용자 온보딩을 간소화하며 신뢰를 구축하는 데 도움이 됩니다.

![UI 브랜딩](/help/assets/assets/content-hub-ui-branding.png)

**공개 링크 공유**

이제 Content Hub는 애플리케이션에 액세스하지 않고도 [외부 사용자가 자산 메타데이터를 보거나 자산을 다운로드할 수 있도록 공유 가능한 링크 생성](/help/assets/share-assets-content-hub.md##share-assets)을 지원합니다.

![UI 브랜딩](/help/assets/assets/public-and-private-link.png)

**컬렉션 거버넌스**

이제 Content Hub를 사용하면 [컬렉션을 생성하는 동안 컬렉션에 대한 액세스를 제어할 수 있으므로 권한이 있는 사용자만 그룹화된 자산을 보거나 관리](/help/assets/collections-content-hub.md##create-collections)할 수 있습니다. 이를 통해 보안이 강화되고, 협업이 원활해지며, 자산 관리가 체계화되고, 거버넌스가 간소화됩니다.

>[!VIDEO](https://video.tv.adobe.com/v/3463336)

>[!NOTE]
>
>컬렉션 거버넌스는 제한적으로 제공되는 기능입니다. 지원 티켓을 생성하여 활성화할 수 있습니다.

**여러 자산을 ZIP으로 다운로드**

이제 Content Hub를 사용하면 [선택한 자산과 해당 렌디션을 별도의 파일이 아닌 ZIP 파일로 다운로드](/help/assets/download-assets-content-hub.md#download-asset-renditions)하여 파일 관리를 간소화할 수 있습니다.

**Content Hub의 Dynamic Media 렌디션**

[Content Hub 사용자 인터페이스 내에서 다운로드할 수 있는 모든 Dynamic Media 사전 설정 렌디션과 스마트 자르기](/help/assets/download-assets-content-hub.md#download-asset-renditions)에 직접 액세스할 수 있습니다.

&#x200B;![Dynamic Media 렌디션](/help/assets/assets/dm-renditions-content-hub.png)

### Dynamic Media의 새로운 기능 {#new-features-dynamic-media}

**AJO B2C와의 Dynamic Media 네이티브 통합**

[Experience Manager(AEM) Dynamic Media와 Journey Optimizer(AJO) B2C의 네이티브 통합](https://experienceleague.adobe.com/ko/docs/journey-optimizer/using/content-management/combine/aem-dynamic)을 통해 마케터는 AEM Dynamic Media 자산(렌디션 및 DM 템플릿)을 AJO 콘텐츠에 쉽게 포함하고 여러 채널에서 실시간 업데이트 및 초개인화된 경험을 제공할 수 있습니다.

>[!VIDEO](https://video.tv.adobe.com/v/3463789/?learn=on&enablevpops=&autoplay=true&captions=kor)

## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### 프리릴리스 기능

* [범용 편집기 - 양식 조각](/help/edge/docs/forms/universal-editor/creating-form-fragments.md): 이제 범용 편집기를 사용하여 적응형 양식의 양식 조각을 만들고 재사용할 수 있습니다. 이들 조각은 한 번 빌드하여 여러 양식에 적용할 수 있는 재사용 가능한 양식 섹션(예: 연락처 세부 정보, 동의 필드)입니다. 이 기능을 사용하면 양식 생성이 간소화되고, 일관성이 보장되며, 작성 효율성이 향상됩니다.

* [SharePoint 문서 라이브러리 - 원본 파일 이름으로 첨부 파일 저장](/help/forms/connect-forms-to-sharepoint-document-library.md#connect-an-adaptive-form-to-microsoft-sharepoint-document-library): 이제 SharePoint 문서 라이브러리에 양식 첨부 파일을 저장할 때 원본 파일 이름을 사용하여 저장할 수 있는 옵션이 추가되었습니다. 이 향상된 기능은 업로드된 파일의 식별과 관리를 간소화해 줍니다.

* **규칙 편집기**:
   * [“When” 절에 클릭 이벤트가 포함된 바이너리 조건](/help/forms/rule-editor-core-components-events-operators.md#available-operator-types-and-events-in-rule-editor): 이제 규칙 편집기에서 버튼 클릭 이벤트(_클릭됨_)를 “When” 절 내의 다른 조건과 결합할 수 있습니다. 이를 통해 사용자 상호 작용 및 기타 요소를 기반으로 규칙 실행을 보다 정밀하게 제어할 수 있습니다. 참고: 여러 조건을 사용하는 경우에는 클릭 이벤트가 가장 먼저 나열된 조건이어야 합니다.
   * [필드 및 패널에 대한 유효성 검사 조건](/help/forms/rule-editor-core-components-usecases.md): 이제 규칙 편집기에 _IsValid_ 및 _IsNotValid_ 조건이 포함됩니다. 이를 통해 특정 필드나 전체 패널(가로 탭, 세로 탭, 아코디언, 마법사 등의 레이아웃 포함)의 유효성 검사 상태를 확인할 수 있으며, 유효성 검사 결과에 따라 양식 탐색과 사용자 경험이 향상됩니다.
* [SharePoint 목록에 대한 범위 관리 개선](/help/forms/connect-forms-to-sharepoint-list.md): 이제 SharePoint 사이트가 /sites 및 /teams와 같은 모든 관리 경로를 지원합니다. 이 향상된 기능은 다양한 SharePoint 사이트 구조에서 보다 광범위한 통합을 가능하게 해 주므로 조직 콘텐츠에 연결하는 데 더 큰 유연성이 제공됩니다.
* [SharePoint 목록에 기록 문서 저장 지원](/help/forms/generate-document-of-record-core-components.md#bind-adaptive-form-components-with-template-fields): 이제 SharePoint 목록 기반 양식 데이터 모델(FDM)을 사용하여 생성된 양식이 기록 문서 바인드 참조 필드 속성을 구성하여 기록 문서(DoR)를 SharePoint 목록에 저장할 수 있습니다. 이 개선된 기능을 통해 지원되는 양식 데이터와 문서를 SharePoint 스토리지와 원활하게 통합할 수 있습니다.

### AEM Forms의 얼리 액세스 기능 {#forms-new-early-access-features}

AEM Forms 얼리 액세스 프로그램은 최첨단 혁신에 독점적으로 액세스할 수 있는 특별한 기회를 제공하며, 혁신의 발전을 구체화하는 데 도움을 줍니다.

이 릴리스 정보에는 현재 릴리스에서 제공되는 혁신 사항이 나열되어 있습니다. 얼리 액세스 프로그램에서 사용할 수 있는 전체 혁신 목록은 [AEM Forms 얼리 액세스 프로그램 설명서](/help/forms/early-access-ea-features.md)를 참조하십시오.

#### Adobe Experience Platform(AEP)과 Forms 통합

이제 얼리 어답터를 위해 Forms와 AEP 간 통합 기능이 제공됩니다.

## [!DNL Experience Manager] as a [!DNL Cloud Service] Foundation {#foundation}

### 업데이트된 사용 중단 프로세스 {#updated-deprecation-process}

Adobe는 정기적으로 기능, 라이브러리, API 및 구성을 검토하여 성능, 보안 및 가치에 대한 기준을 충족하는지 확인합니다. 기능이 더 이상 이 기준을 충족하지 못하면 더 이상 사용되지 않으며 지정된 제거 날짜까지 사용을 중단해야 합니다. 이 날짜까지 Adobe는 이메일 알림을 통해 고객에게 알리고, 새 빌드를 진행하거나 배포하기 전에 Cloud Manager에서 수행해야 할 작업을 알려 드립니다. 필요한 조치를 취하지 않으면 AEM의 새 버전으로 업그레이드할 수 없게 되어 보안, 성능, 안정성 및 가용성에 잠재적인 영향을 미칠 수 있습니다.

자세한 내용은 [사용 중단 문서](/help/release-notes/deprecated-removed-features.md)를 참조하십시오.

#### 제거 날짜가 다가옴에 따라 사용 중단된 Java API 및 OSGi 구성 {#deprecated-near-removals}

아래 목록을 확장하여 사용 중단된 API와 OSGi 구성을 확인하십시오. 제거 일정을 포함한 자세한 내용은 사용 중단 문서를 참조하십시오.

<details>
  <summary>사용 중단 항목을 보려면 확장하십시오.</summary>

Java API:
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
* `org.bson`
* `org.apache.jackrabbit.oak.plugins.blob`
* `org.apache.jackrabbit.oak.plugins.memory`

OSGi 속성:

* `org.apache.sling.commons.log.LogManager` (모든 속성)
* `org.apache.sling.commons.log.LogManager.factory.config` (`org.apache.sling.commons.log.file`, `org.apache.sling.commons.log.pattern`)

</details>

### Java 11 런타임 사용 중단 {#java11-runtime-deprecation}

**Java 11 런타임**&#x200B;은 이제 더 이상 사용되지 않으며, 대부분의 환경은 이미 성능이 더 좋은 **Java 21 런타임**&#x200B;으로 업그레이드되었습니다.

지원되지 않는 종속성으로 인해 환경을 업그레이드할 수 없는 경우([Java 21 런타임 요구 사항](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/build-environment-details.md#runtime-requirements) 참조), Adobe로부터 구체적인 다음 단계가 포함된 이메일을 받았을 것입니다. 모든 필수 업데이트가 **2025년 8월 28일**&#x200B;까지 완료되어 중단 없이 환경을 업그레이드할 수 있도록 해 주시기 바랍니다.

참고: 런타임 버전은 코드의 빌드 버전과 별도입니다. Java 21을 사용한 빌드를 권장하지만 현재로서는 Java 11 빌드도 여전히 지원됩니다. Java 11 빌드에 대한 별도의 사용 중단 공지는 앞으로 공유될 예정입니다.

### AEM Java 로그 구성 시행 {#logconfig-policy}

4월 릴리스 정보에서 언급된 대로 AEM Java 로그는 모든 고객 환경에서 안정적인 모니터링을 보장하기 위해 표준 형식을 따라야 합니다. 로그 형식 변경, 출력 파일 또는 기본 로그 수준과 같은 사용자 정의 로그 구성은 더 이상 지원되지 않습니다. 로그는 기본 파일로 전달되어야 하며, AEM 제품 코드의 기본 로그 수준은 유지되어야 합니다. 자세한 내용은 [로깅 문서](/help/implementing/developing/introduction/logging.md#configuration-loggers)를 참조하십시오.

**8월 말**&#x200B;부터 지원되지 않는 사용자 정의 로깅 재정의는 무시됩니다. 분석에 따르면 대부분의 고객은 영향을 받지 않으며 Adobe는 현재 구성에 영향을 받을 수 있는 고객에게 직접 연락할 것입니다.

사용자 정의 로깅 동작에 의존하는 모든 다운스트림 프로세스를 검토하고 업데이트해 주시기 바랍니다. 예:

* 로그 전달 시스템이 사용자 정의 로그 형식을 기대하는 경우, 수집 규칙을 조정해야 할 수도 있습니다.
* 이전에 로그 수준을 변경하여 로그의 세부 정보를 줄인 적이 있는 경우 기본 수준으로 되돌리면 로그 볼륨이 증가할 수 있습니다.

### 이전 버전 및 감사 로그의 기본 삭제 {#mt-defaults}

현재 콘텐츠 버전과 감사 로그는 기본적으로 해당 *삭제 유지 관리 작업*&#x200B;이 비활성화되어 있으므로 명시적으로 구성하지 않는 한 데이터가 제거되지 않습니다.

그러나 저장소 성능을 최적화하기 위해 **2025년 6월 말**&#x200B;부터 다음 지침에 따라 삭제가 기본적으로 활성화됩니다.

#### 콘텐츠 버전 {#mt-content}

* **새로운 환경** (향후 날짜 이후에 생성됨(나중에 전달))
   * **30일** 이전 버전은 주기적으로 삭제됩니다.
   * 지난 30일 이내의 최신 버전 5개는 보관 기간에 관계없이 가장 최신 버전 및 현재 버전도 함께 유지됩니다.

* **기존 환경**(향후 날짜 이전에 생성됨):
   * **7년** 이전 버전은 주기적으로 삭제됩니다.
   * 지난 7년 이내의 모든 버전이 보존됩니다.
   * 이 높은 기본 임계값은 최근 데이터가 의도치 않게 제거되는 것을 방지합니다. 그러나 저장소 성능을 최적화하려면 더 낮은 값을 구성하는 것이 좋습니다.

* 해당 기본값은 구성 파이프라인을 사용해 배포된 YAML 구성으로 수정할 수 있습니다.

#### 감사 로그 {#mt-auditlogs}

* **새로운 환경**(향후 날짜가 정해지면 별도 공지 예정):
   * 복제, DAM 및 페이지 감사 로그는 **7일** 이상 주기적으로 삭제됩니다.
   * 모든 이벤트는 기본적으로 기록됩니다.

* **기존 환경**(향후 날짜 이전에 생성됨):
   * 복제, DAM 및 페이지 감사 로그는 **7년** 이상 주기적으로 삭제됩니다.
   * 모든 이벤트는 기본적으로 기록됩니다.
   * 이 높은 기본 임계값은 최근 데이터가 의도치 않게 제거되는 것을 방지합니다. 그러나 저장소 성능을 최적화하려면 더 낮은 값을 구성하는 것이 좋습니다.

* 해당 기본값은 구성 파이프라인을 사용해 배포된 YAML 구성으로 수정할 수 있습니다.

자세한 내용은[유지 관리 작업 문서](/help/operations/maintenance.md#defaults)를 참조하십시오.

### 에지 컴퓨팅(Alpha 프로그램) {#edge-computing}

에지 컴퓨팅을 사용하면 CDN 계층에서 JavaScript를 실행할 수 있어 데이터 처리가 최종 사용자에게 더 가까워집니다. 이렇게 하면 지연 시간이 줄어들고 에지에서 반응성이 뛰어나고 역동적인 경험을 할 수 있습니다.

일반적인 사용 사례는 다음과 같습니다.

* 콘텐츠 접근 권한을 부여하기 전에 ID 공급자를 통해 사용자 인증
* 지리적 위치, 디바이스 유형 또는 사용자 속성에 따라 콘텐츠 개인화
* CDN과 원본 사이의 미들웨어 역할
* 서드파티 API의 응답을 다시 서식 지정(및 여러 API 응답 집계)한 후 브라우저에 전달
* 다양한 백엔드에서 결합된 콘텐츠를 사용하여 에지에서 서버 렌더링 HTML을 구성하고 제공

라이브 프로덕션 사이트를 위한 AEM Publish Delivery 또는 Edge Delivery Services 프로젝트에 사용할 수 있는 기회는 제한적입니다. 참여에 관심이 있거나 보다 자세히 알아보려면 사용 사례에 대한 간략한 설명과 함께 [aemcs-edgecompute-feedback@adobe.com](mailto:aemcs-edgecompute-feedback@adobe.com)으로 이메일을 보내 주시기 바랍니다.

### Edge Delivery Services를 위한 CDN 구성(Beta 프로그램) {#cdn-eds-beta}

Adobe 관리 CDN은 [구성 파이프라인 문서](/help/operations/config-pipeline.md#configurations)에 설명된 대로 유연한 구성 옵션을 제공합니다.

이제 Beta 버전에서는 CDN 원본 선택기, 응답 및 요청 변환 등을 포함한 기능에 대한 구성 파이프라인을 배포합니다. 사용 사례에 대한 자세한 내용은 [aemcs-cdn-config-adopter@adobe.com](mailto:aemcs-cdn-config-adopter@adobe.com)에 문의해 주십시오.

### 더 많은 대상으로 AEM 로그 전달(Beta 프로그램) {#log-forwarding-beta}

로그는 Cloud Manager에서 다운로드할 수 있지만 많은 조직에서 이러한 로그를 선호하는 로깅 대상으로 스트리밍하는 것이 유용하다고 생각합니다. AEM은 이미 Azure Blob Storage, Datadog, HTTPS, Elasticsearch(및 OpenSearch), Splunk로의 AEM 및 CDN 로그 전달을 지원합니다. 이 기능은 셀프서비스 방식으로 구성하고 구성 파이프라인을 사용하여 배포합니다.

이제 Beta 버전에서는 AEM 로그를 Amazon S3, Sumo Logic 및 사용자의 New Relic 계정(Adobe 제공 계정이 아닌 경우)으로 전달할 수 있습니다. AEM 로그(Apache/Dispatcher 포함)가 이러한 로깅 대상에 대해 지원되지만 CDN 로그는 지원되지 않습니다. 액세스하려면 이메일 [aemcs-logforwarding-beta@adobe.com](mailto:aemcs-logforwarding-beta@adobe.com)으로 문의하십시오.

자세한 내용은 [로그 전달 설명서](/help/implementing/developing/introduction/log-forwarding.md)에서 확인하십시오.

## [!DNL Experience Manager] 안내서 {#guides}

[여기](https://experienceleague.adobe.com/ko/docs/experience-manager-guides/using/release-info/aem-guides-releases-roadmap)서 Adobe Experience Manager Guides 최신 릴리스의 새로운 기능과 향상된 기능의 전체 목록을 찾을 수 있습니다.

## Cloud Manager {#cloud-manager}

[여기](/help/implementing/cloud-manager/release-notes/current.md)서 Cloud Manager 월별 릴리스의 전체 목록을 찾을 수 있습니다.

## 마이그레이션 도구 {#migration-tools}

[여기](/help/journey-migration/release-notes/release-notes-migration-tools-current.md)서 마이그레이션 도구의 전체 목록을 찾을 수 있습니다.

## 범용 편집기 {#universal-editor}

[여기](/help/release-notes/universal-editor/current.md)서 범용 편집기의 전체 목록을 찾을 수 있습니다.

## 변형 생성 {#generate-variations}

[여기](/help/generative-ai/release-notes-generate-variations.md)서 변형 생성의 전체 목록을 찾을 수 있습니다.

## Experience Cloud 릴리스 정보 {#experience-cloud}

다른 Experience Cloud 애플리케이션 릴리스에 대한 정보는 [여기](https://experienceleague.adobe.com/ko/docs/release-notes/experience-cloud/current)서 확인할 수 있습니다.
