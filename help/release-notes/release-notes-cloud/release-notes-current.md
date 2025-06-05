---
title: ' [!DNL Adobe Experience Manager] as a Cloud Service 최신 릴리스 정보'
description: ' [!DNL Adobe Experience Manager] as a Cloud Service 최신 릴리스 정보'
mini-toc-levels: 1
exl-id: a2d56721-502c-4f4e-9b72-5ca790df75c5
feature: Release Information
role: Admin
source-git-commit: 949a3956a88ae8075e1c518e50400f81b603924d
workflow-type: tm+mt
source-wordcount: '2067'
ht-degree: 31%

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


[!DNL Adobe Experience Manager] as a [!DNL Cloud Service]의 현재 기능 릴리스(2025.5.0) 일자는 2025년 6월 5일 금요일입니다. 다음 기능 릴리스(2025.6.0)는 2025년 6월 26일에 예정되어 있습니다.

## 유지 관리 릴리스 정보 {#maintenance}

[ 여기](/help/release-notes/maintenance/latest.md)에서 최신 유지 관리 릴리스 정보를 확인할 수 있습니다.

<!-- 

## Release Video {#release-video}

Have a look at the February 2025 Release Overview video for a summary of the features added in the 2025.2.0 release:

>[!VIDEO](https://video.tv.adobe.com/v/3440927?quality=12&captions=kor)

-->

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

**AI 생성 메타데이터**

이제 AEM Assets은 [AI를 사용하여 제목, 설명 및 키워드를 포함한 메타데이터를 자동으로 생성합니다](/help/assets/metadata-assets-view.md#ai-smart-tags). 이러한 AI 생성 필드는 메타데이터 정확도를 향상시켜 에셋을 보다 쉽게 검색, 분류 및 추천할 수 있도록 합니다. 이러한 접근 방식은 수동 태깅을 제거함으로써 효율성을 향상시킬 뿐만 아니라 대량의 디지털 컨텐츠 전반에 걸쳐 일관성과 확장성을 보장합니다.

![AI 생성 메타데이터](/help/assets/assets/enhanced-smart-tags.png)

**Figma와 통합**

AEM Assets은 기본적으로 Figma와 통합되어 설계자가 Figma 사용자 인터페이스 내에서 AEM Assets에 저장된 자산에 직접 액세스할 수 있습니다. AEM Assets에서 관리하는 컨텐츠를 그림 캔버스에 배치한 다음 AEM Assets 저장소에 새 컨텐츠 또는 편집된 컨텐츠를 저장할 수 있습니다.

![Figma와 통합](/help/assets/assets/figma-integration.png)


### Content Hub의 새로운 기능 {#new-features-content-hub}

**특성 기반 액세스 제어(ABAC)**

이제 Content Hub을 사용하여 에셋에 액세스하는 데 규칙 기반 제한을 적용할 수 있습니다. 에셋 권한은 거버넌스를 보장하며 사용자가 관련 에셋만 액세스할 수 있도록 합니다.

에셋 제한 규칙은 메타데이터를 기반으로 하며, 규칙에 정의된 조건이 에셋 메타데이터와 일치하는 경우 에셋이 사용자 그룹에 표시됩니다.

속성 기반 액세스 제어의 몇 가지 주요 이점은 다음과 같습니다.

* 사용 권한에 대한 폴더 구조에 대한 종속성 제거

* 관리자가 에셋을 업로드하고 권한 구조를 소급하여 결정할 수 있습니다.

* 중복 횟수가 줄어들어 자산 무결성이 향상됩니다. 동일한 에셋을 다른 그룹과 공유할 때 폴더 기반 권한에서 중복이 필요합니다.

**UI 브랜딩**

이제 Content Hub을 통해 관리자는 배너 이미지, 배너 제목, 본문 텍스트와 기본 및 2차 색상을 비롯한 브랜드별 요소로 사용자 인터페이스를 사용자 정의할 수 있습니다. 이러한 개선 사항은 브랜드 일관성을 보장하고, 사용자 온보딩을 간소화하며, 신뢰를 구축하는 데 도움이 됩니다.

![UI 브랜딩](/help/assets/assets/content-hub-ui-branding.png)

**공개 링크 공유**

Content Hub은 이제 공유 가능한 링크 생성을 지원하여 애플리케이션 액세스 없이 외부 사용자가 에셋 메타데이터를 보거나 에셋을 다운로드할 수 있도록 합니다.

![UI 브랜딩](/help/assets/assets/public-and-private-link.png)

**컬렉션 거버넌스**

이제 Content Hub을 사용하여 생성 중에 컬렉션에 대한 액세스를 제어할 수 있으므로 권한이 있는 사용자만 그룹화된 에셋을 보거나 관리할 수 있습니다. 이를 통해 보안 향상, 협업 개선, 체계적인 에셋 관리, 간소화된 거버넌스 등의 효과를 얻을 수 있습니다.

![컬렉션 거버넌스](/help/assets/assets/collection-permissions.png)

>[!NOTE]
>
>컬렉션 거버넌스는 제한된 가용성 기능입니다. 지원 티켓을 생성하여 활성화할 수 있습니다.

**여러 자산을 ZIP으로 다운로드**

이제 Content Hub을 사용하여 선택한 에셋과 해당 렌디션을 별도의 파일이 아닌 ZIP 파일로 다운로드함으로써 파일 관리를 간소화할 수 있습니다.

Content Hub의 **Dynamic Media 렌디션**

Content Hub 사용자 인터페이스 내에서 직접 모든 Dynamic Media 사전 설정 렌디션 및 스마트 자르기에 액세스하여 다운로드할 수 있습니다.

{&#x200B;0}Dynamic Media 렌디션![&#128279;](/help/assets/assets/dm-renditions-content-hub.png)

### Dynamic Media의 새로운 기능 {#new-features-dynamic-media}

**AJO B2C와 Dynamic Media 기본 통합&#x200B;**

Experience Manager(AEM) Dynamic Media와 Journey Optimizer(AJO) B2C의 기본 통합을 통해 마케터는 AEM Dynamic Media 에셋(렌디션 및 DM 템플릿)을 AJO 콘텐츠에 손쉽게 임베드하고 채널 간에 실시간 업데이트 및 초 개인화된 경험을 제공할 수 있습니다.

{&#x200B;0}Dynamic Media 렌디션![&#128279;](/help/assets/assets/dm-ajo-integration.png)

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

### 사용 중단 프로세스 업데이트됨 {#updated-deprecation-process}

Adobe은 기능, 라이브러리, API 및 구성을 정기적으로 검토하여 성능, 보안 및 가치에 대한 표준을 충족하는지 확인합니다. 기능이 더 이상 이러한 표준을 충족하지 않으면 사용 중지로 표시되며 지정된 제거 날짜까지 사용을 중지해야 합니다. 이 날짜까지 Adobe은 새 빌드를 진행하거나 배포하기 전에 고객에게 이메일 알림과 Cloud Manager에서 수행해야 하는 작업을 알려줍니다. 필요한 조치를 취하지 않으면 AEM의 새 버전으로 업그레이드할 수 없기 때문에 보안, 성능, 안정성 및 가용성에 대한 잠재적인 영향을 받을 수 있습니다.

자세한 내용은 [사용 중단 문서](/help/release-notes/deprecated-removed-features.md)를 참조하세요.

#### 제거 날짜에 즈음하여 더 이상 사용되지 않는 Java API 및 OSGi 구성 {#deprecated-near-removals}

더 이상 사용하지 않아야 하는 더 이상 사용되지 않는 API 및 OSGi 구성을 보려면 아래 목록을 확장하십시오. 제거 타임라인 등 자세한 내용은 사용 중단 문서를 참조하십시오.

<details>
  <summary>를 확장하여 사용 중단 확인</summary>

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

* `org.apache.sling.commons.log.LogManager`(모든 속성)
* `org.apache.sling.commons.log.LogManager.factory.config`(`org.apache.sling.commons.log.file`, `org.apache.sling.commons.log.pattern`)

</details>

### Java 11 런타임 사용 중단 {#java11-runtime-deprecation}

**Java 11 런타임**&#x200B;은(는) 이제 더 이상 사용되지 않으며 대부분의 환경은 이미 성능이 더 뛰어난 **Java 21 런타임**(으)로 업그레이드되었습니다.

지원되지 않는 종속성([Java 21 런타임 요구 사항](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/build-environment-details.md#runtime-requirements) 참조)으로 인해 환경을 업그레이드할 수 없는 경우 Adobe에서 특정 다음 단계에 대한 전자 메일을 받았어야 합니다. **2025년 8월 28일**&#x200B;까지 모든 필수 업데이트가 완료되어 중단 없이 환경을 업그레이드할 수 있는지 확인하십시오.

참고: 런타임 버전은 코드의 빌드 버전과 별도입니다. Java 21을 사용하여 빌드하는 것이 좋지만 현재로서는 Java 11 빌드가 계속 지원됩니다. 향후 Java 11 빌드에 대한 별도의 사용 중단 알림이 공유될 예정입니다.

### AEM Java 로그 구성 정책 시행 {#logconfig-policy}

4월 릴리스 정보에서 언급한 바와 같이 AEM Java 로그는 모든 고객 환경에서 신뢰할 수 있는 모니터링을 보장하기 위해 표준 형식을 따라야 합니다. 로그 형식, 출력 파일 또는 기본 로그 수준에 대한 변경 사항과 같은 사용자 지정 로그 구성은 더 이상 지원되지 않습니다. 로그는 기본 파일로 계속 이동해야 하며 AEM 제품 코드에 대한 기본 로그 수준은 유지되어야 합니다. [로깅 문서](/help/implementing/developing/introduction/logging.md#configuration-loggers)에서 자세한 내용을 확인하세요.

**늦은 8월**&#x200B;부터 지원되지 않는 사용자 지정 로깅 무시가 무시됩니다. 분석에 따르면 대부분의 고객은 영향을 받지 않으며 Adobe은 현재 구성이 영향을 받을 수 있는 모든 고객에게 직접 연락합니다.

사용자 지정 로깅 동작을 사용하는 다운스트림 프로세스를 검토하고 업데이트하십시오. 예:

* 로그 전달 시스템에서 사용자 지정 로그 형식이 필요한 경우 수집 규칙을 조정해야 할 수 있습니다.
* 이전에 로그 수준을 변경하여 로그 심각도를 줄인 경우 기본 수준으로 되돌리면 로그 볼륨이 늘어날 수 있습니다.

### 이전 버전 및 감사 로그 기본 제거 {#mt-defaults}

현재 콘텐츠 버전 및 감사 로그의 관련 *유지 관리 작업 제거*&#x200B;가 기본적으로 비활성화되어 있으므로 해당 OSGi 속성을 통해 명시적으로 구성되지 않은 한 데이터가 제거되지 않습니다.

그러나 저장소 성능을 최적화하기 위해 **2025년 6월 말**&#x200B;부터 다음 지침에 따라 기본적으로 제거가 활성화됩니다.

#### 컨텐츠 버전 {#mt-content}

* **새 환경**(예정된 날짜 이후에 생성됨(나중에 통신됨)
   * **30일**&#x200B;보다 오래된 버전은 정기적으로 삭제됩니다.
   * 지난 30일 내에 가장 최근 5개 버전이 나이에 관계없이 가장 최근 버전 및 현재 버전과 함께 유지됩니다.

* **기존 환경**(예정된 날짜 이전에 생성됨):
   * **7년** 이전 버전은 정기적으로 삭제됩니다.
   * 지난 7년 내의 모든 버전은 유지됩니다.
   * 이 높은 기본 임계값은 의도하지 않은 최근 데이터 제거를 방지합니다. 하지만 저장소 성능을 최적화하기 위해 더 낮은 값을 구성하는 것이 좋습니다.

* OSGi 구성 대체를 통해 이러한 기본값을 수정할 수 있습니다.

#### 감사 로그 {#mt-auditlogs}

* **새 환경**(별도로 전달되는 예정된 날짜 이후에 생성됨):
   * **7일**&#x200B;보다 오래된 복제, DAM 및 페이지 감사 로그는 정기적으로 삭제됩니다.
   * 모든 이벤트는 기본적으로 기록됩니다.

* **기존 환경**(예정된 날짜 이전에 생성됨):
   * **7년**&#x200B;보다 오래된 복제, DAM 및 페이지 감사 로그는 정기적으로 삭제됩니다.
   * 모든 이벤트는 기본적으로 기록됩니다.
   * 이 높은 기본 임계값은 의도하지 않은 최근 데이터 제거를 방지합니다. 하지만 저장소 성능을 최적화하기 위해 더 낮은 값을 구성하는 것이 좋습니다.

* OSGi 구성 대체를 통해 이러한 기본값을 수정할 수 있습니다.

자세한 내용은 [유지 관리 작업 문서](/help/operations/maintenance.md#default)를 참조하십시오.

### Edge 컴퓨팅(Alpha 프로그램) {#edge-computing}

Edge 컴퓨팅을 사용하면 CDN 계층에서 JavaScript을 실행할 수 있으므로 데이터 처리가 최종 사용자에게 더 가까워집니다. 그러면 지연이 줄어들고 에지에서 응답형의 동적 경험이 활성화됩니다.

일반적인 사용 사례는 다음과 같습니다.

* 콘텐츠에 대한 액세스 권한을 부여하기 전에 ID 공급자로 사용자 인증
* 지리적 위치, 장치 유형 또는 사용자 특성을 기반으로 콘텐츠 개인화
* CDN과 원본 간의 미들웨어 역할
* 서드파티 API의 응답을 브라우저에 전달하기 전에 다시 서식 지정(및 여러 API 응답 집계)
* 다양한 백엔드에서 결합된 콘텐츠를 사용하여 에지에서 서버 렌더링 HTML 작성 및 서비스

라이브 프로덕션 사이트를 위한 AEM Publish 게재 또는 Edge Delivery Services 프로젝트에 사용할 수 있는 기회의 수가 제한되어 있습니다. 참여에 관심이 있거나 더 자세히 알아보려면 사용 사례에 대한 간단한 설명을 [aemcs-edgecompute-feedback@adobe.com](mailto:aemcs-edgecompute-feedback@adobe.com)에 전자 메일을 보내십시오.

### Edge Delivery Services(Beta 프로그램)에 대한 CDN 구성 {#cdn-eds-beta}

Adobe 관리 CDN은 [Config Pipeline 문서](/help/operations/config-pipeline.md#configurations)에 설명된 대로 유연한 구성 옵션을 제공합니다.

이제 베타 버전에서 CDN 원본 선택기, 응답 및 요청 변환 등을 포함하는 기능에 대한 구성 파이프라인을 배포합니다. 사용 사례에 대한 자세한 내용을 확인하려면 [aemcs-cdn-config-adopter@adobe.com](mailto:aemcs-cdn-config-adopter@adobe.com)에 문의하세요.

### 더 많은 대상으로 AEM 로그 전달(Beta 프로그램) {#log-forwarding-beta}

로그는 Cloud Manager에서 다운로드할 수 있지만 많은 조직에서 이러한 로그를 선호하는 로깅 대상으로 스트리밍하는 것이 유용하다고 생각합니다. AEM은 이미 Azure Blob Storage, Datadog, HTTPS, Elasticsearch(및 OpenSearch) 및 Splunk로의 AEM 및 CDN 로그 전달을 지원합니다. 이 기능은 셀프서비스 방식으로 구성하고 구성 파이프라인을 사용하여 배포합니다.

이제 Beta에서는 AEM 로그를 Amazon S3, Sumo Logic 및 고유한 New Relic 계정(Adobe 제공 계정이 아님)에 전달할 수 있습니다. 이러한 로깅 대상에 대해 AEM 로그(Apache/Dispatcher 포함)가 지원되지만 CDN 로그는 지원되지 않습니다. 액세스하려면 이메일 [aemcs-logforwarding-beta@adobe.com](mailto:aemcs-logforwarding-beta@adobe.com)으로 문의하십시오.

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
