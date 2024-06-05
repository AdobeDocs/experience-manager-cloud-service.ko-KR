---
title: ' [!DNL Adobe Experience Manager] as a Cloud Service의 2024.4.0 릴리스 정보입니다.'
description: ' [!DNL Adobe Experience Manager] as a Cloud Service의 2024.4.0 릴리스 정보입니다.'
exl-id: 153a3172-676f-4434-94d4-12fab8e17734
feature: Release Information
role: Admin
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '2727'
ht-degree: 99%

---

# [!DNL Adobe Experience Manager] as a Cloud Service 2024.4.0 릴리스 정보 {#release-notes}

다음 섹션에서는 [!DNL Experience Manager] as a Cloud Service의 2024.4.0 버전 기능 릴리스 정보에 대해 간략히 소개합니다.

>[!NOTE]
>
>여기에서 2021년 또는 2022년과 같은 이전 버전의 릴리스 정보로 이동할 수 있습니다.
>
>[!DNL Experience Manager] as a Cloud Service의 향후 기능 활성화에 대해 알아보려면 [Experience Manager 릴리스 로드맵](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html)을 살펴보십시오.

>[!NOTE]
>
>릴리스와 직접적으로 관련되지 않는 설명서 업데이트의 세부 정보는 [최신 설명서 업데이트](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html)를 참조하십시오.

## 릴리스 일자 {#release-date}

[!DNL Adobe Experience Manager] as a [!DNL Cloud Service] 현재 기능 릴리스(2024.4.0)의 릴리스 일자는 2024년 4월 25일입니다. 다음 기능 릴리스(2024.5.0)는 2024년 5월 30일에 예정되어 있습니다.

## 유지 관리 릴리스 정보 {#maintenance}

[ 여기](/help/release-notes/maintenance/latest.md)에서 최신 유지 관리 릴리스 정보를 확인할 수 있습니다.

## 릴리스 비디오 {#release-video}

2024년 4월 릴리스 개요 비디오를 통해 2024.4.0 릴리스에 추가된 기능에 대한 요약 내용을 살펴보십시오.

>[!VIDEO](https://video.tv.adobe.com/v/3429111?quality=12)

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### 얼리 어답터 프로그램 {#sites-early-adopter}

**변형 생성**

이제 클라우드 서비스에서 액세스 가능한 AEM의 새로운 기능인 [변형 생성](/help/generative-ai/generate-variations.md)을 통해 GenAI를 활용할 수 있습니다. 변형 생성은 생성형 AI를 사용하여 콘텐츠 제작을 생성하고 확장하는 데 도움이 됩니다. 프로그램 참여를 고려한다면 Adobe 계정 팀에 문의하십시오.

**콘텐츠 조각 콘솔에서 자산 찾아보기**

이제 콘텐츠 작성자는 콘텐츠 조각 콘솔을 종료하지 않고도 이미지 및 기타 자산을 찾아보고, 보고, 작업을 수행할 수 있습니다.

![자산 찾아보기](/help/sites-cloud/administering/content-fragments/assets/cf-console-assets-browse.png)

기능을 사용해 보고 피드백을 공유하고 싶으십니까? 공식 이메일 ID로 aemcs-headless-adopter@adobe.com에 이메일을 보내 얼리 어답터 프로그램에 대해 자세히 알아보십시오.

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### Assets 보기의 새로운 기능 {#assets-view-new-features}


**상황별 검색**

이제 [텍스트 프롬프트를 정의하여 저장소에서 사용 가능한 자산을 검색](/help/assets/search-assets-view.md#contextual-search)할 수도 있습니다. Experience Manager Assets는 해당 텍스트 프롬프트를 검색 필터로 자동 변환하고 검색 결과를 표시합니다. 필터 창을 사용하여 자동 필터를 확인하여 수정하고 검색 결과의 범위를 더 좁힐 수 있습니다.

![상황별 검색](/help/assets/assets/contextual-search-text-prompt1.png)

**Express 비디오 빠른 작업**

이제 Experience Manager Assets에는 콘텐츠 재사용률과 콘텐츠 속도를 높이는 [Adobe Express에서 제공하는 쉽고 직관적인 비디오 편집 도구](/help/assets/edit-videos-assets-view.md)가 포함됩니다. 편집 옵션에는 비디오 트리밍, 자르기, 크기 조정 및 MP4를 GIF 파일로 변환 등이 포함됩니다.

![Adobe Express로 비디오 자르기](/help/assets/assets/adobe-express-crop-video.png)

**동적 렌디션**

이제 Experience Manager Assets에서 [동적 렌디션(스마트 자르기 포함)을 보고 다운로드](/help/assets/renditions.md)할 수 있습니다. 동적 렌디션은 디바이스 해상도에 따라 이미지 크기를 조정하거나 다양한 종횡비에 맞게 자르기 등 특정 요구 사항을 충족하기 위해 실시간으로 생성된 이미지 자산의 사용자 정의 버전입니다. 이러한 렌디션을 통해 조직은 다양한 대상자 요구에 맞게 개인화되고 최적화된 경험을 제공할 수 있습니다.

![동적 렌디션](/help/assets/assets/preset_smart_crop.png)

**자산 및 폴더의 바로 이름 바꾸기**

이제 Experience Manager Assets는 [한 번의 클릭으로 자산 또는 폴더의 이름을 바꾸는 기능](/help/assets/manage-organize-assets-view.md)을 제공하여 단순화된 사용자 경험을 제공합니다.

**여러 폴더에 메타데이터 양식 할당 또는 제거**

이제 [여러 폴더에 메타데이터 양식을 할당하거나 제거](/help/assets/metadata-assets-view.md#assign-metadata-form-to-a-folder)할 수 있습니다.

### 관리자 보기의 새로운 기능 {#admin-view-new-features}

**링크 공유 구성**

관리자가 사용자를 위해 이 기능의 기본 동작을 사용자 정의할 수 있는 새로운 구성 집합과 함께 [링크 공유를 만드는](/help/assets/share-assets.md) 향상된 새로운 사용자 환경입니다.

![링크 공유 구성](/help/assets/assets/config-email-service.png)



## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

<!-- 

* **Configure a shard for Adobe Sign for AEM Forms**: Adobe distributes Acrobat Sign API around the globe in many deployment units called "shards." Each shard serves a customer's account, such as NA1, NA2, NA3, EU1, JP1, AU1, IN1, and others. The shard names correspond to geographic locations. You can now use more than one shard while using Adobe Sign integration with AEM Forms. 

-->

### AEM Forms의 새로운 기능 {#forms-new-features}

* **핵심 구성 요소 기반 적응형 양식을 위한 향상된 시각적 규칙 편집기**: 이 릴리스에서는 핵심 구성 요소 기반 적응형 양식을 위한 시각적 규칙 편집기가 대폭 업그레이드되었습니다. 이 릴리스에서는 핵심 구성 요소 기반 적응형 양식을 위한 시각적 규칙 편집기가 대폭 업그레이드되었습니다. 이 업데이트는 사용자 정의 함수와의 상호 작용을 간소화하여 더욱 강력하고 효율적인 양식을 빌드할 수 있도록 하는 데 중점을 둡니다.

  이제 다음을 통해 사용자 정의 함수 상호 작용을 간소화할 수 있습니다.

   * [새로운 주석을 활용하여 더욱 명확한 함수 정의를 제공합니다](/help/forms/create-and-use-custom-functions.md#supported-javascript-annotations-for-custom-function).
   * [사용자 정의 함수에 캐싱 메커니즘을 사용하여 양식 성능 속도를 높입니다](/help/forms/create-and-use-custom-functions.md#caching-support-for-custom-function).
   * [사용자 정의 함수 내에서 전역 오브젝트로 원활하게 작업합니다](/help/forms/create-and-use-custom-functions.md#field-and-global-scope-objects-in-custom-functions).
   * [사용자 정의 함수 내에서 선택적 매개변수를 정의하고 활용합니다](/help/forms/create-and-use-custom-functions.md#parameter).

  이 업데이트는 또한 규칙 편집기 기능에 다음과 같은 향상된 기능을 제공합니다. 다음과 같은 작업을 수행할 수 있습니다.

   * 조건부 실행을 위한 강력한 [“when-then-else”](/help/forms/rule-editor-core-components.md#when) 로직을 구현합니다.
   * let 및 arrow 함수(ES10 지원)와 같은 최신 JavaScript 기능을 활용합니다.
   * 필드뿐만 아니라 전체 패널과 양식도 검증하거나 재설정하여 사용자 상호 작용에 대한 제어를 확장합니다.

  이러한 개선 사항은 시각적 규칙 편집기 내에서 규칙 및 사용자 정의 함수를 작성하는 데 더욱 직관적이고 강력한 경험을 제공합니다.

* **[다양한 버전의 적응형 양식 만들기](/help/forms/add-comments-annotations-versioning-adaptive-form-core-components.md)**: 이제 기존 양식의 변형을 쉽게 관리할 수 있습니다. 이에 따라 간소화된 단일 워크플로 내에서 버전 제어가 단순화되고, 양식 최적화를 위한 비교가 용이해집니다.

* **[적응형 양식 비교](/help/forms/compare-forms.md)**: 이제 두 양식을 쉽게 비교하여 두 양식 간의 차이점을 확인할 수 있습니다. 팀원이 수정본을 비교하고 변경 사항을 효율적으로 논의할 수 있도록 하여 원활한 공동 작업을 촉진합니다.

* **스크리블 서명 구성 요소에 대한 접근성 향상**: 이 업데이트는 스크리블 서명 구성 요소에 대한 접근성을 크게 향상시킵니다.

  **향상된 키보드 탐색:**
   * Tab 키를 누르면 사용자가 서명 대화 상자 내의 모든 대화형 요소를 탐색할 수 있습니다.
   * 브러시나 키보드로 서명하고 Enter 키를 누르면 대화 상자가 닫힙니다.
   * 서명하고 “확인”을 클릭한 후에는 서명 컨트롤에 초점이 유지됩니다.

  **명확한 서명 기능:**

   * Tab 키를 통해 서명을 지우기 위한 명확한 십자 아이콘에 액세스할 수 있습니다.
   * Tab 탐색을 통해서도 “서명 확인 지우기” 대화 상자에 액세스할 수 있습니다.

  **향상된 레이블 및 컨트롤:**
   * 이제 “aria-label”을 사용하여 기능을 알리므로(예: &quot;aria-label=&#39;Sign using Keyboard&#39;&quot;) 키보드 서명 버튼의 레이블이 더욱 명확해졌습니다.
   * 향상된 대비를 통해 스크리블 서명 내의 모든 컨트롤을 쉽게 구별할 수 있습니다.
   * 이제 확인/확인 표시 버튼이 비활성 상태일 때 시각적으로 구분하여 표시됩니다.

  **화면 판독기를 위한 서명 피드백:**
   * 서명을 입력하면 화면 판독기 사용자가 서명을 만드는 데 사용된 텍스트를 들을 수 있습니다.

이 업데이트는 스크리블 서명 구성 요소에 대한 탐색, 명확성 및 피드백을 개선하여 장애인 사용자에게 더욱 포용적인 환경을 보장합니다.

### 얼리 어답터 프로그램 {#forms-early-adopter}

* **[Adobe Workfront Fusion 시나리오에 적응형 양식 제출](/help/forms/submit-adaptive-form-to-workfront-fusion.md)**: Forms as a Cloud Service는 적응형 양식을 Adobe Workfront와 쉽게 연결할 수 있는 기본 옵션을 제공합니다. 이를 통해 적응형 양식을 Adobe Workfront 시나리오에 제출하는 프로세스가 단순화되며 적응형 양식 제출 시 Workfront Fusion 시나리오를 트리거할 수 있습니다.

  <br/> ![Adobe Workfront](/help/forms/assets/adobe-workfront.png) <br/> Adobe Workfront Fusion Connector를 사용하면 적응형 양식 제출 시 자동으로 트리거되는 워크플로를 설계할 수 있습니다. 예를 들어 제출된 데이터를 검토하는 작업을 특정 개인에게 할당하는 워크플로가 시작되어 적응형 양식을 통해 캡처된 정보를 기반으로 신청서를 승인하거나 거부할 수 있는 시나리오를 생각해 볼 수 있습니다. 이처럼 간소화된 통합으로 효율성이 향상되며 워크플로 프로세스에 새로운 수준의 자동화가 구현됩니다.|

* **[Reader 확장 서비스](/help/forms/aem-forms-cloud-service-communications-introduction.md#reader-extension-service)**: AEM Forms 커뮤니케이션 API는 일반 PDF에 양식 채우기 및 주석 달기와 같은 기능을 추가하여, 무료 Adobe Reader를 사용하는 사용자가 대화형으로 이용할 수 있는 Reader 확장 서비스를 제공합니다.

* [오른쪽에서 왼쪽 방향 언어 지원](/help/forms/supporting-new-language-localization-core-components.md): 이제 핵심 구성 요소를 기반으로 빌드된 적응형 양식을 아랍어, 페르시아어, 우르두어와 같은 오른쪽에서 왼쪽 방향(RTL) 언어로 표시할 수 있습니다. RTL 언어의 사용자는 전 세계적으로 20억 명이 넘습니다. RTL 언어로 된 양식을 사용하면 적응형 양식의 범위를 확장하여 더 다양성 높게 대상자를 수용하고 RTL 시장을 선택할 수 있습니다. 특정 지역에서는 현지 언어로 양식을 제공하는 것이 법적 의무이기도 합니다. 현지 언어를 수용함으로써 더 많은 대상자에게 접근할 수 있을 뿐만 아니라 관련 법률 및 규정을 준수할 수 있습니다.

* **[DocAssurance API(Communication API의 일부)로 문서 보호](/help/forms/aem-forms-cloud-service-communications-introduction.md#document-assurance-doc-assurance)**: DocAssurance API를 사용하여 문서에 서명하고 암호화하여 민감한 정보를 보호할 수 있습니다. 문서의 콘텐츠는 암호화를 통해 읽을 수 없는 포맷으로 변환되어 권한이 있는 사용자만 액세스할 수 있습니다. 이 보호 계층이 강화되면 중요 데이터를 승인되지 않은 사용자로부터 보호할 뿐만 아니라 고객들이 안심할 수 있습니다. 서명 API를 통해 조직에서 배포하고 수신하는 Adobe PDF 문서의 보안 및 개인정보를 보호할 수 있습니다. 이 서비스는 의도한 수신자만 문서를 변경할 수 있도록 디지털 서명과 인증을 사용합니다.

  공식 이메일 ID에서 “`aem-forms-ea@adobe.com`”으로 이메일을 보내 얼리 어답터 프로그램에 참여하여 기능에 대한 액세스 권한을 요청할 수 있습니다.

* **[실제 사용자 모니터링(RUM) 데이터 서비스](/help/implementing/cloud-manager/content-requests.md#real-user-monitoring-for-aem-as-a-cloud-service)**를 활용하여 AEM as a Cloud Service에 대한 클라이언트측 컬렉션을 활성화할 수 있습니다.
실제 사용자 모니터링(RUM) 데이터 서비스는 사용자 상호 작용을 보다 정확하게 반영하여 웹 사이트 참여에 대한 안정적인 측정을 보장합니다. 이를 통해 페이지 성능에 대한 고급 인사이트를 얻을 수 있습니다. 이는 Adobe가 관리하는 CDN 또는 Adobe가 관리하지 않는 CDN을 사용하는 고객 모두에게 유용합니다. 또한 Adobe가 관리하지 않는 CDN을 사용하는 고객의 경우 이제 자동화된 트래픽 보고를 활성화할 수 있으므로 트래픽 보고서를 Adobe와 공유할 필요가 없습니다.

  이 새로운 기능을 테스트하고 피드백을 공유하는 데 관심이 있으시면 Adobe ID와 연결된 이메일 주소를 통해 RUM을 활성화하고자 하는 각 환경에 대한 도메인 이름과 함께 `aemcs-rum-adopter@adobe.com`으로 이메일을 보내 주십시오. 그러면 Adobe 제품 팀에서 실제 사용자 모니터링(RUM) 데이터 서비스를 활성화합니다.

## [!DNL Experience Manager] as a [!DNL Cloud Service] Foundation {#foundation}

### CDN 구성 {#cdn-config}

다음과 같은 방법으로 Adobe CDN에서 트래픽을 구성합니다.

* [요청 변환](/help/implementing/dispatcher/cdn-configuring-traffic.md#request-transformations) - AEM으로 라우팅되기 전에 경로, 쿼리 매개변수 및 HTTP 헤더를 포함하여 수신 요청의 측면을 수정합니다.
* [응답 변환](/help/implementing/dispatcher/cdn-configuring-traffic.md#response-transformations) - 발신 응답이 브라우저에 제공되기 전에 HTTP 헤더를 변경합니다.
* [원본 선택기](/help/implementing/dispatcher/cdn-configuring-traffic.md#response-transformations#origin-selectors) - CDN을 통해 트래픽을 AEM 외부 사이트 및 애플리케이션으로 라우팅합니다.

이러한 규칙이 소스 제어(git)에서 선언되면 Cloud Manager 구성 파이프라인을 사용하여 CDN에 배포할 수 있습니다. 아래 얼리 어답터 섹션의 클라이언트측 리디렉션 기능도 참조하십시오.

### 사용자 정의 CDN 오류 페이지 {#cdn-error-pages}

CDN이 트래픽을 AEM 원본으로 라우팅할 수 없는 경우에는 사용자 정의 오류 페이지를 선언하여 일반 버전을 대체할 수 있습니다. 브랜드 오류 페이지를 제공하는 방법에 대해 [자세히 알아보십시오](/help/implementing/dispatcher/cdn-error-pages.md).

### 얼리 어답터 프로그램 {#foundation-early-adopter}

#### 클라이언트측 리디렉션(얼리 어답터 프로그램) {#client-side-redirects-early-adopter}

소스 제어에서 301/302 클라이언트측 리디렉션을 구성하고 CDN에 배포합니다. [자세히 알아보고](/help/implementing/dispatcher/cdn-configuring-traffic.md#client-side-redirectors) **<aemcs-cdn-config-adopter@adobe.com>**&#x200B;으로 이메일을 보내 얼리 어답터 프로그램에 참여하십시오.

#### 트래픽 필터 규칙 경고(얼리 어답터 프로그램) {#traffic-filter-rules-alerts-early-adopter}

선택적으로 라이선스를 부여할 수 있는 WAF(웹 애플리케이션 방화벽) 규칙을 포함하는 최근 릴리스된 [트래픽 필터 규칙](/help/security/traffic-filter-rules-including-waf.md)을 통해 허용하거나 거부해야 하는 트래픽을 구성할 수 있습니다.

지금 **<aemcs-cdn-config-adopter@adobe.com>**&#x200B;으로 이메일을 보내 얼리 어답터 프로그램에 참여하면 트래픽 필터 규칙이 실행될 때마다 알림을 받을 수 있습니다. 액션 센터 이메일 알림은 특정 트래픽 상황이 발생할 때 적절한 조치를 취할 수 있도록 지속적으로 정보를 제공해 줍니다.

#### 재작성 맵의 Apache/Dispatcher 런타임 수집(얼리 어답터 프로그램) {#apache-rewritemaps-early-adopter}

AEM 6.5와 유사하게 Apache/Dispatcher는 게시 저장소의 특정 위치에 배치된 재작성 맵을 수집하고 웹 계층 파이프라인 실행 없이 로드합니다. 이를 통해 비즈니스 사용자가 ACS Commons Redirect Map Manager에서 제공하는 것과 같은 UI를 사용하여 리디렉션을 선언할 수 있습니다. 자세한 내용은 **<aemcs-cdn-config-adopter@adobe.com>**&#x200B;으로 문의하십시오.

#### 동적 콘텐츠 로드를 위한 ESI(에지측 포함)(얼리 어답터 프로그램) {#esi-early-adopter}

이제 Adobe Managed CDN은 에지 수준 동적 웹 콘텐츠 어셈블리를 위한 마크업 언어인 ESI(에지측 포함)를 지원합니다. ESI 스니펫을 포함하면 더 높은 TTL을 사용하여 CDN에서 전체 HTML 페이지를 캐싱하는 동시에 더 높은 케이던스 업데이트(낮은 TTL)가 필요한 작은 섹션을 출처에서 더 자주 가져올 수 있습니다. 자세한 내용은 **<aemcs-cdn-config-adopter@adobe.com>**&#x200B;으로 문의하십시오.

#### 사이트 테마 및 사이트 템플릿을 사용하는 프론트 엔드 코드에 대한 RDE 지원(얼리 어답터 프로그램) {#rde-frontend-early-adopter}

[신속한 개발 환경(RDE)](/help/implementing/developing/introduction/rapid-development-environments.md)은 이제 얼리 어답터에 대해 [사이트 테마](/help/sites-cloud/administering/site-creation/site-themes.md) 및 [사이트 템플릿](/help/sites-cloud/administering/site-creation/site-templates.md)을 기반으로 하는 프론트 엔드 코드를 지원합니다. RDE를 사용하면 [프론트 엔드 파이프라인](/help/sites-cloud/administering/site-creation/enable-front-end-pipeline.md)이 아닌 명령줄 지시문을 사용하여 이 작업이 수행됩니다. 사용해 보고 피드백을 제공하려면 **<aemcs-rde-support@adobe.com>**&#x200B;으로 문의하십시오.

#### RDE에 대한 향상된 로깅(얼리 어답터 프로그램) {#rde-logging-early-adopter}

이제 개발자는 [신속한 개발 환경(RDE)](/help/implementing/developing/introduction/rapid-development-environments.md)에서 코드를 디버깅하는 동안 버전 제어에서 OSGI 속성을 수정하지 않고도 명령줄을 사용하여 로그를 더욱 효율적으로 구성하고 스트리밍할 수 있습니다. 기능은 다음과 같습니다.

* 패키지별 또는 클래스 수준에서 로그 수준 선언
* 로그 출력 형식 사용자 정의
* 여러 로그를 병렬로 스트리밍

사용해 보고 피드백을 제공하려면 **<aemcs-rde-support@adobe.com>**&#x200B;으로 문의하십시오.

## [!DNL Experience Manager] 안내서 {#guides}

### 사전 구성된 언어 그룹을 사용하여 콘텐츠를 여러 언어로 번역하는 기능

이제 Experience Manager Guides를 사용하면 언어 그룹을 만들고 콘텐츠를 여러 언어로 간편하게 번역할 수 있습니다. 이 기능은 조직의 필요에 따라 번역을 구성하고 관리하는 데 도움이 됩니다.

예를 들어 유럽 일부 국가의 콘텐츠를 번역해야 하는 경우 영어(EN), 프랑스어(FR), 독일어(DE), 스페인어(ES), 이탈리아어(IT)와 같은 유럽 언어에 대한 언어 그룹을 만들 수 있습니다.

![번역 패널](/help/release-notes/assets/guides/translation-languages-2404.png)

*문서를 번역하려는 언어 그룹 또는 언어를 선택합니다.*

>[!NOTE]
>
>언어의 대상 폴더가 없거나 대상 언어가 소스와 동일한 경우 회색으로 표시되며 경고 기호가 나타납니다.

관리자는 언어 그룹을 생성하고 이를 여러 폴더 프로필로 구성할 수 있습니다. 작성자는 폴더 프로필에 구성된 언어 그룹을 조회할 수 있습니다.


언어 그룹을 만들면 번역 프로젝트의 전반적인 효율성과 생산성이 향상되어 궁극적으로 여러 언어에 대한 현지화 프로세스가 개선됩니다.


[웹 편집기에서 문서를 번역하는 방법](https://experienceleague.adobe.com/ko/docs/experience-manager-guides/using/user-guide/author-content/create-preview-topics/author-content-aem-guides/work-with-web-editor/translate-documents-web-editor) 알아보기

### 저장소 보기에서 파일을 검색하고 필터링하도록 향상된 환경

이제 파일을 필터링하는 동안 향상된 환경을 경험할 수 있습니다. 향상된 파일 필터링 기능은 파일을 쉽게 검색하고 탐색할 수 있는 향상된 방법을 제공합니다.

![저장소 보기에서 파일 검색](/help/release-notes/assets/guides/repository-filter-search-2404.png)

*텍스트가 포함된 파일 검색`general purpose.`*

관련 파일에 대한 더 빠른 액세스, 더 직관적인 사용자 인터페이스 등의 이점을 활용하여 검색 환경을 더욱 원활하고 효율적으로 만들어 보십시오.

![빠른 검색 필터 ](/help/release-notes/assets/guides/repository-filter-search-quick.png)

*빠른 필터를 사용하여 DITA 및 비 DITA 파일을 검색합니다.*

[왼쪽 패널](https://experienceleague.adobe.com/ko/docs/experience-manager-guides/using/user-guide/author-content/create-preview-topics/author-content-aem-guides/work-with-web-editor/web-editor-features#id2051EA0M0HS) 섹션의 **필터 검색** 기능에 대해 자세히 알아보십시오.

### 데이터 소스 커넥터의 향상된 기능

2024.4.0 릴리스에는 데이터 소스 커넥터에 대한 다음과 같은 개선 사항이 포함됩니다.

#### Salsify, Akeneo 및 Microsoft Azure DevOps Boards (ADO) 데이터 소스에 연결

기존의 기본 제공 커넥터 외에도 Experience Manager Guides는 Salsify, Akeneo 및 Microsoft Azure DevOps Boards (ADO) 데이터 소스에 대한 커넥터를 제공합니다. 관리자는 이러한 커넥터를 다운로드하고 설치할 수 있습니다. 그런 다음 설치된 커넥터를 구성합니다.

#### 샘플 쿼리를 복사하고 붙여넣어 콘텐츠 스니펫 또는 주제 만들기

생성기에서 샘플 데이터 쿼리를 손쉽게 복사하고 붙여넣어 콘텐츠 스니펫이나 주제를 생성할 수 있습니다. 이 기능을 사용하면 구문을 기억하거나 쿼리를 수동으로 만들 필요가 없습니다. 쿼리를 수동으로 입력하는 대신 샘플 쿼리를 복사하여 붙여넣고 편집한 후 요구 사항에 따라 데이터를 가져오는 데 사용할 수 있습니다.

![콘텐츠 스니펫 삽입 대화 상자](/help/release-notes/assets/guides/insert-content-snippet.png)

*샘플 쿼리를 복사하고 편집하여 콘텐츠 스니펫을 만듭니다.*

#### 파일 커넥터를 사용하여 JSON 데이터 파일에 연결


이제 관리자는 JSON 데이터 파일을 데이터 소스로 사용하도록 JSON 파일 커넥터를 구성할 수 있습니다. 커넥터를 사용하여 컴퓨터 또는 Adobe Experience Manager Assets에서 JSON 파일을 가져옵니다. 그런 다음 작성자는 생성기를 사용하여 콘텐츠 조각이나 주제를 만들 수 있습니다.

이 기능을 사용하면 JSON 파일에 저장된 데이터를 사용하고 다양한 스니펫에서 재사용할 수 있습니다. JSON 파일을 업데이트할 때마다 콘텐츠도 동적으로 업데이트됩니다.

#### 콘텐츠 스니펫 또는 주제를 생성하기 위해 커넥터에 대한 여러 리소스 URL 구성

관리자는 일반 REST 클라이언트, Salsify, Akeneo 및 Microsoft Azure DevOps Boards(ADO)와 같은 일부 커넥터에 대해 여러 리소스 URL을 구성할 수 있습니다.
그런 다음 작성자는 데이터 소스에 연결하여 생성기를 사용하여 콘텐츠 스니펫이나 주제를 만듭니다. 이 기능을 사용하면 각 URL에 대한 데이터 소스를 만들 필요가 없기 때문에 유용합니다. 이는 단일 콘텐츠 스니펫 또는 주제의 특정 데이터 소스에 대한 모든 리소스에서 데이터를 빠르게 가져오는 데 도움이 됩니다. 데이터 소스 커넥터에 대한 자세한 내용과 [사용자 인터페이스에서 데이터 소스 커넥터를 구성하는 방법](https://experienceleague.adobe.com/ko/docs/experience-manager-guides/using/install-guide/cs-ig/web-editor-configs-cs/conf-data-source-connector-tools)을 확인하십시오. [데이터 소스의 데이터를 사용하는 방법](https://experienceleague.adobe.com/ko/docs/experience-manager-guides/using/user-guide/author-content/create-preview-topics/author-content-aem-guides/work-with-web-editor/web-editor-content-snippet)에 대해 알아봅니다.

새로운 기능 및 개선 사항에 대한 자세한 내용은 [2024.04.0 릴리스의 새로운 기능](https://experienceleague.adobe.com/ko/docs/experience-manager-guides/using/release-info/release-notes/cloud-release-notes/2024-releases/2404-release/whats-new-2024-04-0)을 참조하십시오.

이 릴리스에서 해결된 문제 목록을 보려면 [2024.4.0 릴리스에서 해결된 문제](https://experienceleague.adobe.com/ko/docs/experience-manager-guides/using/release-info/release-notes/cloud-release-notes/2024-releases/2404-release/fixed-issues-2024-04-0)를 확인하십시오.

## Cloud Manager {#cloud-manager}

[여기](/help/implementing/cloud-manager/release-notes/current.md)에서 Cloud Manager 월별 릴리스의 전체 목록을 찾을 수 있습니다.

## 마이그레이션 도구 {#migration-tools}

[여기](/help/journey-migration/release-notes/release-notes-migration-tools-current.md)에서 마이그레이션 도구의 전체 목록을 찾을 수 있습니다.
