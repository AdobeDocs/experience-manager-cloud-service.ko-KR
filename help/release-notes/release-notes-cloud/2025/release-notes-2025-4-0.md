---
title: ' [!DNL Adobe Experience Manager] as a Cloud Service의 2025.4.0 릴리스 정보입니다.'
description: ' [!DNL Adobe Experience Manager] as a Cloud Service의 2025.4.0 릴리스 정보입니다.'
feature: Release Information
role: Admin
exl-id: 48e09824-5c67-49d8-8896-358d679649fc
source-git-commit: c8391e09b7e2888423187f48360423c52b18fe0a
workflow-type: tm+mt
source-wordcount: '1828'
ht-degree: 89%

---

# [!DNL Adobe Experience Manager] as a Cloud Service 2025.4.0 릴리스 정보 {#release-notes}

다음 섹션에서는 [!DNL Experience Manager] as a Cloud Service의 2025.4.0 버전 기능 릴리스 정보에 대해 간략히 소개합니다.

>[!NOTE]
>
>여기에서 2023년 또는 2024년과 같은 이전 버전의 릴리스 정보로 이동할 수 있습니다.
>
>[!DNL Experience Manager] as a Cloud Service의 향후 기능 활성화에 대해 알아보려면 [Experience Manager 릴리스 로드맵](https://experienceleague.adobe.com/ko/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap)을 살펴보십시오.

>[!NOTE]
>
>Experience Cloud 릴리스 정보의 업데이트에 대한 월별 이메일 알림을 받아 보려면 [Adobe 우선순위 제품 업데이트](https://www.adobe.com/kr/subscription/priority-product-update.html)를 구독하십시오.

## 릴리스 일자 {#release-date}

[!DNL Adobe Experience Manager] as a [!DNL Cloud Service] 현재 기능 릴리스(2025.4.0)의 릴리스 일자는 2025년 4월 24일입니다. 다음 기능 릴리스(2025.5.0)는 2025년 6월 5일에 예정되어 있습니다.

## 유지 관리 릴리스 정보 {#maintenance}

[ 여기](/help/release-notes/maintenance/latest.md)에서 최신 유지 관리 릴리스 정보를 확인할 수 있습니다.

## 릴리스 비디오 {#release-video}

2025년 4월 릴리스 개요 비디오를 통해 2025.4.0 릴리스에 추가된 기능에 대한 간단한 요약을 살펴보십시오.

>[!VIDEO](https://video.tv.adobe.com/v/3463991?quality=12)

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### Experience Manager Sites의 새로운 기능 {#enhancements-sites}

**새로운 콘텐츠 조각 모델 관리 UI**

AEM 콘텐츠 조각을 사용하여 작업할 때 사용할 수 있는 새로운 클라이언트측 사용자 인터페이스 목록이 더욱 확장되고 완성되었으며, 이제 콘텐츠 조각 모델에 대해 새로운 관리 UI를 사용할 수 있습니다. 새로운 UI는 필터를 사용하여 모델을 검색할 수 있는 깔끔하고 현대적인 목록 보기를 제공하며, 이를 통해 모델 태그와 특정 모델을 기반으로 하는 콘텐츠 조각이 표시됩니다. 설명서는 [여기](/help/sites-cloud/administering/content-fragments/managing-content-fragment-models.md)에서 확인할 수 있습니다.

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### Dynamic Media (Scene7) {#dynamic-media-scene7}

**개선된 보안 환경에서 Dynamic Media(Scene7)가 지원되지 않음**

AEM as a Cloud Service의 Dynamic Media(Scene7)는 HIPAA를 지원하지 않으며 개선된 보안이 활성화된 AEM 환경에서 사용할 수 없습니다.

2025년 4월 AEM as a Cloud Service 릴리스부터 기술 제한 사항으로 인해 보안이 강화된 환경에서는 Dynamic Media(Scene7)를 구성할 수 없습니다. 결과적으로, **도구** > **클라우드 서비스** 아래의 **Dynamic Media 구성** 카드는 이러한 환경에서 더 이상 표시되지 않습니다.

또한 AEM 6.5를 사용하는 고객은 Dynamic Media (Scene7) 스택이 HIPAA를 지원하지 않는다는 점을 인지하고 있어야 합니다.

### Dynamic Media Classic {#dynamic-media-classic}

**보고**

Dynamic Media Classic 보고 대시보드의 대역폭 탭은 2025년 4월부터 더 이상 지원되지 않습니다.

[대역폭 및 스토리지, 보고서 유형](https://experienceleague.adobe.com/ko/docs/dynamic-media-classic/using/setup/administration-setup#types-of-reports)을 참조하십시오.

## 자산 보기의 새로운 기능 {#new-features-assets-view}

**자산 관계**

이제 자산 보기의 간소화된 자산 세부 정보 패널에서 자산 관계를 보고 편집할 수 있습니다. 소스 및 파생과 같은 관계를 콘텐츠에 간편하게 추가하여 사용자가 관련성 있는 히어로 콘텐츠를 보다 효과적으로 찾을 수 있도록 하십시오.

![자산 관계 예시](/help/assets/assets/asset-relations-example.png)

**자산 버전 비교**

이제 자산 보기를 사용하여 원하는 버전의 자산을 빠르게 선택하고 최신 버전과 비교할 수 있습니다.

![자산 버전 비교](/help/assets/assets/version-compare2.png)


## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### 프리릴리스 기능

* [적응형 Forms 및 양식 단편을 위한 범용 편집기](/help/edge/docs/forms/universal-editor/overview-universal-editor-for-edge-delivery-services-for-forms.md): 이제 범용 편집기는 적응형 Forms 및 재사용 가능한 양식 단편을 모두 만들 수 있습니다. 작성자는 간소화된 WYSIWYG 작성 환경에서 양식을 시각적으로 작성하고, 제출 작업을 구성하고, reCAPTCHA 유효성 검사를 추가할 수 있습니다. 이 기능은 양식 생성을 가속화하고 일관성을 향상시키며 스팸 및 자동 남용에 대한 보호 기능을 향상시킵니다.

* [SharePoint 문서 라이브러리 - 원본 파일 이름으로 첨부 파일 저장](/help/forms/connect-forms-to-sharepoint-document-library.md#connect-an-adaptive-form-to-microsoft-sharepoint-document-library): 이제 SharePoint 문서 라이브러리에 양식 첨부 파일을 저장할 때 원본 파일 이름을 사용하여 저장할 수 있는 옵션이 추가되었습니다. 이 향상된 기능은 업로드된 파일의 식별과 관리를 간소화해 줍니다.

* **규칙 편집기**:
   * [“When” 절에 클릭 이벤트가 포함된 바이너리 조건](/help/forms/rule-editor-core-components-events-operators.md#available-operator-types-and-events-in-rule-editor): 이제 규칙 편집기에서 버튼 클릭 이벤트(_클릭됨_)를 “When” 절 내의 다른 조건과 결합할 수 있습니다. 이를 통해 사용자 상호 작용 및 기타 요소를 기반으로 규칙 실행을 보다 정밀하게 제어할 수 있습니다. 참고: 여러 조건을 사용하는 경우에는 클릭 이벤트가 가장 먼저 나열된 조건이어야 합니다.
   * [필드 및 패널에 대한 유효성 검사 조건](/help/forms/rule-editor-core-components-usecases.md): 이제 규칙 편집기에 _IsValid_ 및 _IsNotValid_ 조건이 포함됩니다. 이를 통해 특정 필드나 전체 패널(가로 탭, 세로 탭, 아코디언, 마법사 등의 레이아웃 포함)의 유효성 검사 상태를 확인할 수 있으며, 유효성 검사 결과에 따라 양식 탐색과 사용자 경험이 향상됩니다.
* [SharePoint 목록에 대한 범위 관리 개선](/help/forms/connect-forms-to-sharepoint-list.md): 이제 SharePoint 사이트가 /sites 및 /teams와 같은 모든 관리 경로를 지원합니다. 이 향상된 기능은 다양한 SharePoint 사이트 구조에서 보다 광범위한 통합을 가능하게 해 주므로 조직 콘텐츠에 연결하는 데 더 큰 유연성이 제공됩니다.
* [SharePoint 목록에 기록 문서 저장 지원](/help/forms/generate-document-of-record-core-components.md#bind-adaptive-form-components-with-template-fields): 이제 SharePoint 목록 기반 양식 데이터 모델(FDM)을 사용하여 생성된 양식이 기록 문서 바인드 참조 필드 속성을 구성하여 기록 문서(DoR)를 SharePoint 목록에 저장할 수 있습니다. 이 개선된 기능을 통해 지원되는 양식 데이터와 문서를 SharePoint 스토리지와 원활하게 통합할 수 있습니다.
* [적응형 양식 조각에 대한 자동 매핑 지원](/help/forms/adaptive-form-fragments-core-components.md#auto-mapping-support-for-fragments-in-an-adaptive-form): 이제 적응형 Forms은 스키마 개체가 정의된 조각 구조와 일치할 때 일치하는 조각의 자동 삽입을 지원하여 양식 만들기를 간소화하고 재사용을 촉진합니다.

### AEM Forms의 얼리 액세스 기능 {#forms-new-early-access-features}

AEM Forms 얼리 액세스 프로그램은 최첨단 혁신에 독점적으로 액세스할 수 있는 특별한 기회를 제공하며, 혁신의 발전을 구체화하는 데 도움을 줍니다.

이 릴리스 정보에는 현재 릴리스에서 제공되는 혁신 사항이 나열되어 있습니다. 얼리 액세스 프로그램에서 사용할 수 있는 전체 혁신 목록은 [AEM Forms 얼리 액세스 프로그램 설명서](/help/forms/early-access-ea-features.md)를 참조하십시오.

#### Adobe Experience Platform(AEP)과 Forms 통합

* [Adobe Experience Platform과 AEM Forms 통합](/help/forms/aem-forms-aep-connector.md): AEM Forms-Adobe Experience Platform 커넥터를 사용하면 적응형 Forms과 Adobe Experience Platform 간의 원활한 통합을 수행할 수 있습니다. 이 기능을 사용하면 양식 데이터를 XDM 스키마에 매핑하고 실시간으로 AEP에 직접 제출할 수 있습니다. Adobe Experience Cloud 솔루션에서 개인화 및 활성화 사용 사례에 대한 데이터 캡처를 간소화합니다.

## CIF 추가 기능 {#cloud-services-cif}

### 개선 사항 {#enhancements-cif}

* CIF 제품 참조 데이터 유형에 대한 제품 변형 선택 기능 추가
* **실험**: PDP의 CIF 핵심 구성 요소에서 [JSON+LD](/help/commerce-cloud/customizing/json-ld.md)
* **실험**: [캐시를 지우는 CIF 기능](/help/commerce-cloud/configuring/clear-cache.md)

### 버그 수정 {#bug-fixes-cif}

* 제품 필드의 검색 문제 해결
* #variant_sku에 대한 제품 URL 형식이 제대로 작동하지 않음
* 제품 목록 구성 요소에 20개가 넘는 SKU를 추가할 수 없음

## [!DNL Experience Manager] as a [!DNL Cloud Service] Foundation {#foundation}

### OpenAPI 기반 API {#open-apis}

개발자는 AEM as Cloud Service 기능을 자신의 애플리케이션과 도구에 긴밀하게 통합할 수 있습니다. 새 AEM as a Cloud Service API는 OpenAPI 사양을 따르며, 일관되고 문서화가 잘 되며 사용자 친화적인 것을 목표로 합니다. 인증이 필요한 엔드포인트에 대한 자격 증명은 Adobe Developer Console 프로젝트를 만들어 생성되며 OAuth 서버 간, 웹 앱 및 단일 페이지 앱(SPA)을 지원합니다.

OpenAPI 기반 AEM API의 [전체 목록](https://developer.adobe.com/experience-cloud/experience-manager-apis/#openapi-based-apis)을 확인하고, [자세히 알아보고](/help/implementing/developing/open-api-based-apis.md), 구성 및 사용 방법을 안내하는 [전체 튜토리얼](https://experienceleague.adobe.com/ko/docs/experience-manager-learn/cloud-service/aem-apis/openapis/invoke-api-using-oauth-s2s)을 살펴보십시오.

나중에 사용할 수 있도록 인증된 API를 구성하는 방법을 알아보려면 이 비디오를 시청하십시오.

>[!VIDEO](https://video.tv.adobe.com/v/3457510?quality=12&learn=on)

### CDN 구성 관련 개선 사항 {#cdn-enhancements}

Adobe 관리 CDN은 [구성 파이프라인 문서](/help/operations/config-pipeline.md#configurations)에 설명된 대로 유연한 구성 옵션을 제공합니다. 최근 추가된 몇 가지 기능은 다음과 같습니다.

#### CDN 로그에 추가 속성 포함 {#props-in-cdnlogs}

디버깅 및 데이터 분석을 포함한 시나리오에 유용하며, [요청 및 응답 변환](/help/implementing/dispatcher/cdn-configuring-traffic.md#request-transformations)에서 `logProperty` 액션을 설정하여 기본 속성 외에도 CDN 로그에 더 많은 정보를 포함할 수 있습니다.

#### 지역, 대륙 및 조직 속성을 일치 조건으로 사용 {#matching-conditions}

이제 CDN 규칙을 트래픽 차단 및 리디렉션을 포함한 사용 사례에 대해 지역, 대륙 및 조직을 기준으로 매칭할 수 있습니다. `clientRegion` 및 `clientContinent`는 이미 지원되는 `clientCountry`를 보강하여 지리적 위치를 기반으로 매칭하는 반면, `clientAsName` 및 `clientAsNumber`는 자율 시스템을 매칭하여 대규모 ISP, 회사 또는 클라우드 공급업체를 식별합니다. [새로 공개된 요청 속성](/help/security/traffic-filter-rules-including-waf.md#condition-structure)에 대해 자세히 알아보십시오.

#### 쿠키 값 설정 {#cookie-attributes}

[응답 변환](/help/implementing/dispatcher/cdn-configuring-traffic.md#response-transformations)에서 쿠키 속성을 설정할 수 있습니다.

### Java 21 지원 {#java21}

1월 릴리스부터 Java 21 및 Java 17을 사용하여 코드를 작성할 수 있습니다. 패턴 매칭, 봉인된 클래스 및 다양한 성능 개선과 같은 새로운 기능을 사용할 수 있습니다. Maven 프로젝트 및 라이브러리 버전 업데이트를 포함한 구성 단계는 [빌드 환경](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/build-environment-details.md#using-java-support) 문서를 참조하십시오.

Java 17 또는 21 빌드가 감지되면 성능이 더 뛰어난 Java 21 **런타임**&#x200B;이 자동으로 배포됩니다. 그러나 Java 11로 빌드된 환경에서는 Java 21 런타임을 선택하는 것도 좋습니다. 이를 위해서는 [aemcs-java-adopter@adobe.com](mailto:aemcs-java-adopter@adobe.com)로 이메일을 보내 문의하시기 바랍니다. [Java 21 런타임 요구 사항](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/build-environment-details.md#runtime-requirements)에 대해 알아보십시오.

>[!IMPORTANT]
>
> Java 21 **런타임**&#x200B;은 2월에 개발/RDE 환경에 배포되었으며, **4월 28일과 29일**&#x200B;에 스테이징/프로덕션 환경에 적용될 예정입니다. Java 21(또는 Java 17)을 사용한 **코드 작성**&#x200B;은 Java 21 런타임과 독립적입니다. Java 21(또는 Java 17)을 사용하여 코드를 작성하기 위한 단계를 명시적으로 수행해야 합니다.

### AEM 로깅 구성 시행 {#logconfig-policy}

고객 환경을 효과적으로 모니터링하려면 AEM Java 로그가 일관된 형식을 유지해야 하며 사용자 정의 구성으로 재정의되어서는 안 됩니다. 로그 출력은 기본 파일로 계속 전달되어야 합니다. AEM 제품 코드의 경우 기본 로그 수준을 유지해야 합니다. 단, 고객이 개발한 코드에 대한 로그 수준을 조정하는 것은 허용됩니다.

이를 위해 다음 OSGi 속성을 변경해서는 안 됩니다.
* **Apache Sling 로그 구성** (PID: `org.apache.sling.commons.log.LogManager`) — *모든 속성*
* **Apache Sling 로깅 로거 구성** (공장 PID: `org.apache.sling.commons.log.LogManager.factory.config`):
   * `org.apache.sling.commons.log.file`
   * `org.apache.sling.commons.log.pattern`

5월 중순부터 AEM에서는 이러한 속성에 대한 사용자 정의 수정 사항이 무시되는 정책을 시행할 예정입니다. 다운스트림 프로세스를 검토하고 그에 따라 조정하십시오. 예를 들어 로그 전달 기능을 사용하는 경우:
* 로깅 대상이 사용자 정의(기본이 아닌) 로그 형식을 기대하는 경우 수집 규칙을 업데이트해야 할 수 있습니다.
* 로그 수준을 변경하여 로그의 자세한 정보가 줄어든 경우, 기본 로그 수준을 적용하면 로그 볼륨이 상당히 증가할 수 있다는 점을 알아 두십시오.

### 더 많은 대상으로 AEM 로그 전달 - Beta 프로그램 {#log-forwarding-earlyadopter}

현재 Beta 버전에서는 AEM 로그를 New Relic(HTTPS 사용), Amazon S3, Sumo Logic으로 전달할 수 있습니다. AEM 로그(Apache/Dispatcher 포함)는 지원되지만 CDN 로그는 지원되지 않습니다. 액세스하려면 이메일 [aemcs-logforwarding-beta@adobe.com](mailto:aemcs-logforwarding-beta@adobe.com)으로 문의하십시오.

로그는 Cloud Manager에서 다운로드할 수 있지만 많은 조직에서 이러한 로그를 선호하는 로깅 대상으로 스트리밍하는 것이 유용하다고 생각합니다. AEM은 이미 Azure Blob Storage, Datadog, HTTPS, Elasticsearch(및 OpenSearch), Splunk로의 (GA) AEM 및 CDN 로그 전달을 지원합니다. 이 기능은 셀프서비스 방식으로 구성하고 구성 파이프라인을 사용하여 배포합니다.

자세한 내용은 [로그 전달 설명서](/help/implementing/developing/introduction/log-forwarding.md)에서 확인하십시오.

### 에지 컴퓨팅 - 피드백 요청 {#edge-computing-feedback}

에지 컴퓨팅은 데이터 처리를 브라우저에 더 가까운 위치에서 수행하여, 지연 시간 감소와 같은 이점을 제공합니다. Adobe는 이 기술이 AEM 게시 게재 및 Edge Delivery Services 프로젝트에 유용할 것이라고 생각하는지에 대한 귀하의 의견을 듣고자 합니다. 또한 제품 로드맵에 반영할 수 있도록 이 기술을 어떻게 활용할 계획인지 알려 주십시오.

가능한 일부 사용 사례는 다음과 같습니다.

* 콘텐츠에 대한 액세스를 제어하기 위해 IdP를 통한 인증
* 지리적 위치, 디바이스 유형, 사용자 속성 등을 기반으로 다이내믹 콘텐츠를 랜더링하여 개인화
* 고급 이미지 조작
* CDN과 원본 간 미들웨어
* 브라우저와 서드파티 API 사이의 레이어, API 응답을 다시 포맷하기 위한 목적
* 여러 출처로부터 데이터를 집계하여 클라이언트 브라우저가 데이터를 보다 쉽게 렌더링할 수 있도록 함

질문과 의견을 이메일([aemcs-edgecompute-feedback@adobe.com](mailto:aemcs-edgecompute-feedback@adobe.com))로 보내 주십시오.

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
