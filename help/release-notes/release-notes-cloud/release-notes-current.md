---
title: ' [!DNL Adobe Experience Manager] as a Cloud Service 최신 릴리스 정보'
description: ' [!DNL Adobe Experience Manager] as a Cloud Service 최신 릴리스 정보'
mini-toc-levels: 1
exl-id: a2d56721-502c-4f4e-9b72-5ca790df75c5
feature: Release Information
role: Admin
source-git-commit: b4aec70b13575366c1d40ccf935481580a1fb6d8
workflow-type: tm+mt
source-wordcount: '1810'
ht-degree: 100%

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

[!DNL Adobe Experience Manager] as a [!DNL Cloud Service]의 현재 기능 릴리스(2025.6.0) 일자는 2025년 6월 26일입니다. 다음 기능 릴리스(2025.7.0)는 2025년 8월 7일에 예정되어 있습니다.

## 유지 관리 릴리스 정보 {#maintenance}

[여기](/help/release-notes/maintenance/latest.md)에서 최신 유지 관리 릴리스 정보를 확인할 수 있습니다.

<!-- 

## Release Video {#release-video}

Have a look at the February 2025 Release Overview video for a summary of the features added in the 2025.2.0 release:

>[!VIDEO](https://video.tv.adobe.com/v/3440927?quality=12&captions=kor)

-->

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

**자산 보기에서 향상된 메타데이터 양식 관리**

이제 관리자 보기에서 자산 보기로 메타데이터 양식을 직접 가져올 수 있습니다. 자산 보기에서 이러한 양식을 업데이트하면 해당 내용이 관리자 보기에 자동으로 반영되어 두 환경 모두에서 일관성이 유지됩니다. 이 기능을 통해 기존 메타데이터 구성의 연속성을 유지하면서 새로운 자산 보기로 원활하게 전환할 수 있습니다.

![AI 생성 메타데이터](/help/assets/assets/import-metadata-forms-page.png)

### Content Hub의 새로운 기능 {#new-features-content-hub}

**컬렉션 거버넌스**

이제 Content Hub를 사용하면 [컬렉션을 생성하는 동안 컬렉션에 대한 액세스를 제어할 수 있으므로 권한이 있는 사용자만 그룹화된 자산을 보거나 관리](/help/assets/collections-content-hub.md##create-collections)할 수 있습니다. 이를 통해 보안이 강화되고, 협업이 원활해지며, 자산 관리가 체계화되고, 거버넌스가 간소화됩니다.

>[!VIDEO](https://video.tv.adobe.com/v/3463336)


## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}



### 프리릴리스 기능

* [적응형 양식 및 양식 조각을 위한 Universal Editor](/help/edge/docs/forms/universal-editor/overview-universal-editor-for-edge-delivery-services-for-forms.md): Universal Editor는 이제 적응형 양식과 재사용 가능한 양식 조각을 모두 만들 수 있도록 지원합니다. 작성자는 간소화된 WYSIWYG 작성 환경에서 시각적으로 양식을 작성하고, 제출 작업을 구성하고, reCAPTCHA 유효성 검사를 추가할 수 있습니다. 이 기능을 사용하면 양식 생성 속도가 빨라지고, 일관성이 향상되고, 스팸 및 자동화된 남용에 대한 보호 기능이 향상됩니다.

* [적응형 양식에서 AFP 렌디션 생성 및 동기화](/help/forms/document-generation-afp-api.md): AFP 출력 동기화 API를 사용하면 관리자와 사용자가 적응형 양식에서 AFP(고급 기능 프레젠테이션) 출력을 생성하고 해당 출력을 외부 시스템이나 저장 위치와 동기화할 수 있습니다. AFP는 인쇄에 최적화된 고성능 문서 형식으로, 대규모 기업 환경에서 자주 사용됩니다.

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

* [AEM Forms와 Adobe Experience Platform 통합](/help/forms/aem-forms-aep-connector.md): AEM Forms와 Adobe Experience Platform 커넥터를 사용하면 적응형 양식과 Adobe Experience Platform을 원활하게 통합할 수 있습니다. 이 기능을 사용하면 양식 데이터를 XDM 스키마에 매핑하여 실시간으로 AEP에 직접 제출할 수 있습니다. Adobe Experience Cloud 솔루션 전반에서 개인화 및 활성화 사용 사례에 대한 데이터 캡처를 간소화합니다.

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

**8월 말**&#x200B;부터 지원되지 않는 사용자 정의 로깅 재정의는 무시됩니다. 분석에 따르면 대부분의 고객은 영향을 받지 않으며 현재 구성에 영향을 받을 수 있는 고객에게는 Adobe에서 개별적으로 안내를 드렸습니다.

사용자 정의 로깅 동작에 의존하는 모든 다운스트림 프로세스를 검토하고 업데이트해 주시기 바랍니다. 예:

* 로그 전달 시스템이 사용자 정의 로그 형식을 기대하는 경우, 수집 규칙을 조정해야 할 수도 있습니다.
* 이전에 로그 수준을 변경하여 로그의 세부 정보를 줄인 적이 있는 경우 기본 수준으로 되돌리면 로그 볼륨이 증가할 수 있습니다.

### 이전 버전 및 감사 로그의 기본 삭제 {#mt-defaults}

현재 콘텐츠 버전과 감사 로그는 기본적으로 해당 *삭제 유지 관리 작업*&#x200B;이 비활성화되어 있으므로 명시적으로 구성하지 않는 한 데이터가 제거되지 않습니다.

그러나 저장소 성능을 최적화하기 위해 **2025년 7월 초**&#x200B;부터 다음 지침에 따라 삭제가 기본적으로 활성화됩니다.

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
* 브라우저에 제공하기 전에 서드파티 API의 응답(및 여러 API 응답 집계)을 다시 포맷
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

[여기](https://experienceleague.adobe.com/ko/docs/experience-manager-guides/using/release-info/aem-guides-releases-roadmap)에서 Adobe Experience Manager Guides 최신 릴리스의 새로운 기능과 향상된 기능의 전체 목록을 찾을 수 있습니다.

## Cloud Manager {#cloud-manager}

[여기](/help/implementing/cloud-manager/release-notes/current.md)에서 Cloud Manager 월별 릴리스의 전체 목록을 찾을 수 있습니다.

## 마이그레이션 도구 {#migration-tools}

[여기](/help/journey-migration/release-notes/release-notes-migration-tools-current.md)에서 마이그레이션 도구의 전체 목록을 찾을 수 있습니다.

## Universal Editor {#universal-editor}

[여기](/help/release-notes/universal-editor/current.md)에서 Universal Editor의 전체 목록을 찾을 수 있습니다.

## 변형 생성 {#generate-variations}

[여기](/help/generative-ai/release-notes-generate-variations.md)에서 변형 생성의 전체 목록을 찾을 수 있습니다.

## Experience Cloud 릴리스 정보 {#experience-cloud}

기타 Experience Cloud 애플리케이션 릴리스에 대한 정보는 [여기](https://experienceleague.adobe.com/ko/docs/release-notes/experience-cloud/current)에서 확인할 수 있습니다.
