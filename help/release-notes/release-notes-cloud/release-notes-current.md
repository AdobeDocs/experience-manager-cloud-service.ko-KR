---
title: ' [!DNL Adobe Experience Manager] as a Cloud Service 최신 릴리스 정보'
description: ' [!DNL Adobe Experience Manager] as a Cloud Service 최신 릴리스 정보'
mini-toc-levels: 1
exl-id: a2d56721-502c-4f4e-9b72-5ca790df75c5
source-git-commit: 0ef1e1915f2fdbe44cff209851eb43cc9d69958e
workflow-type: tm+mt
source-wordcount: '2261'
ht-degree: 31%

---

# [!DNL Adobe Experience Manager] as a Cloud Service 최신 릴리스 정보 {#release-notes}

다음 섹션에서는 [!DNL Experience Manager] as a Cloud Service의 최신 버전 기능 릴리스 정보에 대해 간략히 소개합니다.

>[!NOTE]
>
>여기에서 2021년 또는 2022년과 같은 이전 버전의 릴리스 정보로 이동할 수 있습니다.
>
>[!DNL Experience Manager] as a Cloud Service의 향후 기능 활성화에 대해 알아보려면 [Experience Manager 릴리스 로드맵](https://experienceleague.adobe.com/en/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap)을 살펴보십시오.

>[!NOTE]
>
>릴리스와 직접적으로 관련되지 않는 설명서 업데이트의 세부 정보는 [최신 설명서 업데이트](https://experienceleague.adobe.com/en/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates)를 참조하십시오.

## 릴리스 일자 {#release-date}

의 릴리스 날짜 [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] 현재 기능 릴리스(2024.3.0)는 2024년 4월 11일입니다. 다음 기능 릴리스(2024.4.0)는 2024년 4월 25일에 예정되어 있습니다.

## 유지 관리 릴리스 정보 {#maintenance}

[ 여기](/help/release-notes/maintenance/latest.md)에서 최신 유지 관리 릴리스 정보를 확인할 수 있습니다.

<!-- ## Release Video {#release-video}

Have a look at the March 2024 Release Overview video for a summary of the features added in the 2024.3.0 release:

>[!VIDEO](https://video.tv.adobe.com/v/3425864?quality=12)

-->

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### [!DNL Experience Manager Sites]의 새로운 기능 {#sites-features}

**Edge Delivery Services을 위한 AEM 작성**

이제 AEM Sites을 Edge Delivery Services의 컨텐츠 소스로 사용할 수 있습니다. 작성자는 컨텍스트 내 wysiwyg 작성과 함께 새로운 범용 편집기를 사용하여 AEM에서 웹 사이트를 관리합니다. 이를 통해 회사는 Edge Delivery Services을 통해 빠른 고성능 웹 페이지를 구축하는 동시에 AEM의 강력한 컨텐츠 관리 기능을 활용할 수 있습니다.

![AEM 작성](/help/edge/assets/universal_editor_edge_delivery_services.png)

자세한 내용은 [설명서](/help/edge/overview.md) 다음을 확인하십시오 [AEM Gems - AEM 작성 및 Edge Delivery Services 시작하기](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-manager/aem-gems-getting-started-with-aem-authoring-and-edge-delivery/m-p/652694#M43905)

**Headless 구현용 유니버설 편집기**

또한 범용 편집기를 사용하면 분리된 웹 응용 프로그램에서 이전에 기존 사이트에서만 작성되었던 것과 동일한 직관적인 컨텍스트 내 WYSIWYG 작성을 사용할 수 있습니다. 이제 콘텐츠 작성자는 페이지 내의 구성 요소와 동일한 방식으로 콘텐츠 조각을 사용하여 레이아웃을 시각적으로 작성할 수 있습니다.

유니버설 에디터의 차별화 점은 다양한 웹 아키텍처에 대한 적응성, 서버측 및 클라이언트측 렌더링, 프레임워크 독립적인 유지, AEM 호스팅의 필요성 제거 등입니다. 컨텐츠 편집을 위해 기존 웹 애플리케이션을 범용 편집기와 통합하는 것은 간단하며 주로 개발자가 특정 데이터 속성을 마크업에 통합해야 합니다.

이를 통해 범용 편집기는 콘텐츠 구조 또는 기본 기술 스택에 관계없이 일관된 편집 환경을 보장합니다. 자세한 내용은 [유니버설 편집기 소개](/help/implementing/universal-editor/introduction.md).

**콘텐츠 조각 및 모델용 콘텐츠 관리 OpenAPI**

개발자는 이제 프로그래밍 방식으로 콘텐츠 조각 및 콘텐츠 조각 모델과 상호 작용하고 콘텐츠 관리 OpenAPI를 사용하여 해당 모델에 대해 CruD 작업을 수행할 수 있습니다. 자세한 내용은 [API 설명서](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/stable/sites/)

**경험 조각에 대한 다중 사이트 관리 지원**

경험 조각을 저장하는 폴더 구조에 대한 다중 사이트 관리 지원이 확장되어 사용자가 경험 조각이 포함된 전체 콘텐츠 구조를 롤아웃할 수 있습니다.

**콘텐츠 조각 버전 비교**

이제 새로운 콘텐츠 조각 편집기 를 사용하여 콘텐츠 작성자는 현재 버전의 콘텐츠 조각과 이전 버전 간의 차이점을 비교하고 볼 수 있습니다.

### 얼리 어답터 프로그램 {#sites-early-adopter}

**변형 생성**

AEM의 새로운 기능을 통해 GenAI 활용, [변형 생성](/help/generative-ai/generate-variations.md)이제 Cloud Service에서 액세스할 수 있습니다. 변형 생성은 생성 AI를 사용하여 콘텐츠 생성을 생성하고 확장하는 데 도움이 됩니다. 프로그램에서 검토하려면 Adobe 계정 팀에 문의하십시오.

**콘텐츠 조각 콘솔에서 에셋 검색**

이제 콘텐츠 작성자는 콘텐츠 조각 콘솔에서 나가지 않고도 이미지 및 기타 에셋을 찾아보고, 보고, 작업을 수행할 수 있습니다.

![에셋 검색](/help/sites-cloud/administering/content-fragments/assets/cf-console-assets-browse.png)

기능을 사용해 보고 피드백을 공유하고 싶으십니까? 얼리어답터 프로그램에 대한 자세한 내용을 알려면 공식 이메일 ID에서 aemcs-headless-adopter@adobe.com으로 이메일을 보내십시오.

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### 관리자 보기의 새로운 기능 {#admin-view}

**Adobe Express와의 네이티브 통합**

AEM Assets은 기본적으로 Adobe Express과 통합되어 있으므로 Adobe Express 사용자 인터페이스 내에서 AEM Assets에 저장된 에셋에 직접 액세스할 수 있습니다. AEM Assets에서 관리하는 콘텐츠를 빠른 캔버스에 넣은 다음 AEM Assets 저장소에 새 콘텐츠 또는 편집된 콘텐츠를 저장할 수 있습니다.

![Assets 추가 기능에서 자산 포함](/help/assets/assets/adobe-express-native-integration.png)

**지원되는 모든 비디오 유형에 대한 미리보기 렌디션**

이제 Experience Manager Assets은 처리 프로필 구성 없이도 기본적으로 지원되는 모든 비디오 유형의 미리보기 렌디션을 생성합니다.

### Assets 보기의 새로운 기능 {#assets-view}

**컬렉션에 대한 권한 관리**

Assets Essentials을 통해 관리자는 저장소에서 사용할 수 있는 개인 컬렉션에 대한 액세스 수준을 관리할 수 있습니다. 관리자는 사용자 그룹을 만든 다음 해당 그룹에 액세스 수준을 관리하도록 권한을 할당할 수 있습니다. 사용자 그룹에 권한 관리 권한을 위임할 수도 있습니다.


## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

<!-- 

* **Configure a shard for Adobe Sign for AEM Forms**: Adobe distributes Acrobat Sign API around the globe in many deployment units called "shards." Each shard serves a customer's account, such as NA1, NA2, NA3, EU1, JP1, AU1, IN1, and others. The shard names correspond to geographic locations. You can now use more than one shard while using Adobe Sign integration with AEM Forms. 

-->

### AEM Forms의 새로운 기능 {#forms-new-features}

* **[Adobe Experience Manager Forms Edge Delivery Services](/help/edge/docs/forms/overview.md)**: AEM Forms Edge Delivery Services은 작성자가 새로운 양식을 신속하게 업데이트, 게시 및 실행할 수 있는 신속한 개발 환경을 구현하는 구성 가능한 서비스 세트입니다. 이러한 서비스는 참여와 전환을 촉진하는 탁월하고 영향력 있는 양식 경험을 선사합니다. 이러한 양식 환경은 쉽게 작성하고 개발할 수 있습니다.

  ![EDS Forms 기능](/help/edge/assets/eds-forms-features.png)

이러한 서비스를 통해 다음이 가능합니다.

* 동일한 양식 사이트에서 여러 컨텐츠 소스로 작업하고 Microsoft Excel, Google Sheets 또는 적응형 Forms 편집기와 같은 기본 작성 도구를 사용합니다.
* RUM(실시간 사용자 모니터링)을 통해 양식 성능을 빠르고 지속적으로 모니터링하는 로드 및 렌더링의 디지털 등록 경험을 제공합니다.
* 일반 HTML, 최신 CSS 및 바닐라 JavaScript를 사용하여 특정 프레임워크의 가파른 학습 곡선을 피하고 탁월한 경험을 만듭니다.


### AEM Forms용 프리릴리스의 새로운 기능 {#forms-pre-release}

* **핵심 구성 요소 기반 적응형 Forms을 위한 향상된 시각적 규칙 편집기**: 이 릴리스에서는 핵심 구성 요소 기반의 적응형 양식에 대한 시각적 규칙 편집기를 크게 업그레이드합니다. 이 릴리스에서는 핵심 구성 요소 기반의 적응형 양식에 대한 시각적 규칙 편집기를 크게 업그레이드했습니다. 이 업데이트는 사용자 정의 기능과의 상호 작용을 간소화하여 보다 강력하고 효율적인 양식을 구축할 수 있도록 하는 데 중점을 둡니다.

  이제 다음을 수행하여 사용자 정의 기능 상호 작용을 간소화할 수 있습니다.

   * 새 주석을 활용하여 더 명확한 함수 정의를 제공합니다.
   * 사용자 지정 함수에 캐싱 메커니즘을 사용하여 양식 성능 향상
   * 사용자 지정 함수 내에서 전역 개체와 원활하게 작업할 수 있습니다.
   * 사용자 지정 함수 내에서 선택적 매개 변수를 정의하고 활용합니다.

  또한 이 업데이트에서는 규칙 편집기 기능이 다음과 같이 개선되었습니다. 다음과 같은 작업을 수행할 수 있습니다.

   * 조건부 실행에 강력한 &quot;when-then-else&quot; 논리를 구현합니다.
   * let 및 arrow 함수와 같은 최신 JavaScript 기능을 활용할 수 있습니다(ES10 지원).
   * 필드뿐만 아니라 전체 패널 및 양식의 유효성을 검사하거나 재설정하여 사용자 상호 작용에 대한 제어를 확장합니다.

  이러한 향상된 기능은 시각적 규칙 편집기 내에서 규칙 및 사용자 지정 함수를 만드는 데 보다 직관적이고 강력한 경험을 제공합니다.

* **적응형 양식의 여러 버전 만들기**: 이제 기존 양식의 변형을 쉽게 관리할 수 있습니다. 이를 통해 간소화된 단일 워크플로우 내에서 버전 제어를 단순화하고 양식 최적화를 위한 비교를 용이하게 할 수 있습니다.

* **적응형 양식 비교**: 이제 두 양식을 쉽게 비교하여 두 양식 간의 차이점을 식별할 수 있습니다. 팀원이 수정 사항을 비교하고 변경 사항을 효율적으로 논의할 수 있도록 하여 원활한 협업을 촉진합니다.

* **스크리블 서명 구성 요소의 접근성 개선**: 이 업데이트는 스크리블 서명 구성 요소에 상당한 접근성을 개선합니다.

  **향상된 키보드 탐색:**
   * Tab 키를 누르면 사용자가 서명 대화 상자 내의 모든 대화형 요소를 탐색할 수 있습니다.
   * 브러시 또는 키보드로 서명하고 Enter 키를 누르면 대화 상자가 닫힙니다.
   * 서명하고 &quot;확인&quot;을 클릭하면 서명 컨트롤에 포커스가 유지됩니다.

  **서명 지우기 기능:**

   * Tab 키를 통해 서명 삭제를 위한 명확한 교차 아이콘에 액세스할 수 있습니다.
   * &quot;서명 확인 지우기&quot; 대화 상자는 탭 탐색을 통해서도 액세스할 수 있습니다.

  **향상된 레이블 및 컨트롤:**
   * 이제 키보드 서명 버튼의 레이블이 더 명확해졌습니다. 기능을 알리기 위해 &quot;aria-label&quot;(예: &quot;aria-label=&#39;Sign using Keyboard&#39;&quot;)을 사용합니다.
   * 대비가 개선되어 스크리블 서명 내의 모든 컨트롤을 쉽게 구분할 수 있습니다.
   * 이제 확인/확인 표시 단추가 언제 비활성 상태인지를 시각적으로 표시합니다.

  **화면 Reader에 대한 서명 피드백:**
   * 서명을 입력하면 화면 판독기 사용자는 서명을 만드는 데 사용되는 텍스트를 들을 수 있습니다.

이 업데이트는 스크리블 서명 구성 요소에 대한 탐색, 명확성 및 피드백을 개선하여 장애가 있는 사용자에게 보다 포괄적인 경험을 제공합니다.

### 얼리 어답터 프로그램 {#forms-early-adopter}

* **[Adobe Workfront Fusion 시나리오에 적응형 양식 제출](/help/forms/submit-adaptive-form-to-workfront-fusion.md)**: Forms as a Cloud Service에서는 적응형 양식을 Adobe Workfront에 쉽게 연결할 수 있는 획기적인 옵션을 제공합니다. 이를 통해 적응형 양식을 Adobe Workfront 시나리오에 제출하는 프로세스가 단순화되며 적응형 양식 제출 시 Workfront Fusion 시나리오를 트리거할 수 있습니다.

  <br/> ![Adobe Workfront](/help/forms/assets/adobe-workfront.png) <br/> Adobe Workfront Fusion Connector를 사용하면 적응형 양식 제출 시 자동으로 트리거되는 워크플로를 디자인할 수 있습니다. 예를 들어 워크플로우가 시작되어 특정 개인에게 제출된 데이터를 검토하는 작업을 할당하여 적응형 양식을 통해 캡처된 정보를 기반으로 애플리케이션에 대한 승인 또는 거부를 허용하는 시나리오를 구상할 수 있습니다. 이 간소화된 통합은 효율성을 높이고 워크플로우 프로세스에 새로운 수준의 자동화를 제공합니다.|

* **Reader 확장 서비스**: AEM Forms Communication API를 사용하면 Reader 확장 서비스를 통해 일반 PDF에게 양식 채우기 및 댓글 달기와 같은 기능을 추가하여 무료 Adobe Reader을 사용하는 사용자와 상호 작용할 수 있습니다.

* [오른쪽에서 왼쪽 방향 언어 지원](/help/forms/supporting-new-language-localization-core-components.md): 이제 핵심 구성 요소를 기반으로 구축된 적응형 양식을 아랍어, 페르시아어, 우르두어와 같은 오른쪽에서 왼쪽 방향(RTL) 언어로 표시할 수 있습니다. RTL 언어의 사용자는 전 세계적으로 20억 명이 넘습니다. RTL 언어로 된 양식을 사용하면 적응형 양식의 범위를 확장하여 더 다양성 높게 대상자를 수용하고 RTL 시장을 선택할 수 있습니다. 특정 지역에서는 현지 언어로 양식을 제공하는 것이 법적 의무이기도 합니다. 현지 언어를 수용함으로써 더 많은 대상자에게 접근할 수 있을 뿐만 아니라 관련 법률 및 규정을 준수할 수 있습니다.

* **[DocAssurance API(Communication API의 일부)로 문서 보호](/help/forms/aem-forms-cloud-service-communications-introduction.md#document-assurance-doc-assurance)**: DocAssurance API를 사용하여 문서에 서명하고 암호화하여 민감한 정보를 보호할 수 있습니다. 문서의 콘텐츠는 암호화를 통해 읽을 수 없는 포맷으로 변환되어 권한이 있는 사용자만 액세스할 수 있습니다. 이 보호 계층이 강화되면 중요 데이터를 승인되지 않은 사용자로부터 보호할 뿐만 아니라 고객들이 안심할 수 있습니다. 서명 API를 통해 조직에서 배포하고 수신하는 Adobe PDF 문서의 보안 및 개인정보를 보호할 수 있습니다. 이 서비스는 의도한 수신자만 문서를 변경할 수 있도록 디지털 서명과 인증을 사용합니다.

  공식 이메일 ID에서 “`aem-forms-ea@adobe.com`”으로 이메일을 보내 얼리 어답터 프로그램에 참여하여 기능에 대한 액세스 권한을 요청할 수 있습니다.

* **[실제 사용자 모니터링(RUM) 데이터 서비스](/help/implementing/cloud-manager/content-requests.md#real-user-monitoring-for-aem-as-a-cloud-service)**를 활용하여 AEM as a Cloud Service에 대한 클라이언트측 컬렉션을 활성화할 수 있습니다.
실제 사용자 모니터링(RUM) 데이터 서비스는 사용자 상호 작용을 보다 정확하게 반영하여 웹 사이트 참여에 대한 안정적인 측정을 보장합니다. 이를 통해 페이지 성능에 대한 고급 인사이트를 얻을 수 있습니다. 이는 Adobe가 관리하는 CDN 또는 Adobe가 관리하지 않는 CDN을 사용하는 고객 모두에게 유용합니다. 또한 Adobe가 관리하지 않는 CDN을 사용하는 고객의 경우 이제 자동화된 트래픽 보고를 활성화할 수 있으므로 트래픽 보고서를 Adobe와 공유할 필요가 없습니다.

  이 새로운 기능을 테스트하고 피드백을 공유하는 데 관심이 있으시면 Adobe ID와 연결된 이메일 주소를 통해 RUM을 활성화하고자 하는 각 환경에 대한 도메인 이름과 함께 `aemcs-rum-adopter@adobe.com`으로 이메일을 보내 주십시오. 그러면 Adobe 제품 팀에서 실제 사용자 모니터링(RUM) 데이터 서비스를 활성화합니다.

## [!DNL Experience Manager] as a [!DNL Cloud Service] Foundation {#foundation}

### 얼리 어답터 프로그램 {#foundation-early-adopter}

#### 트래픽 필터 규칙 경고(얼리 어답터 프로그램) {#traffic-filter-rules-alerts-early-adopter}

최근에 릴리스된 [트래픽 필터 규칙](/help/security/traffic-filter-rules-including-waf.md)선택적으로 사용 가능한 WAF(Web Application Firewall) 규칙이 포함된 을 사용하면 허용하거나 거부할 트래픽을 구성할 수 있습니다.

이제 이메일을 보낼 수 있습니다. **<aemcs-cdn-config-adopter@adobe.com>** 트래픽 필터 규칙이 트리거될 때마다 알림을 받을 수 있도록 얼리어답터 프로그램에 참여합니다. Actions Center 이메일 알림은 특정 트래픽 상태가 발생할 때 사용자에게 계속 알려주므로 적절한 조치를 취할 수 있습니다.

#### CDN 구성(얼리 어답터 프로그램) {#cdn-config-early-adopter}

최근에 릴리스된 외에도 [트래픽 필터 규칙](/help/security/traffic-filter-rules-including-waf.md)선택적 라이선스 가능한 WAF(Web Application Firewall) 규칙이 포함된 에서는 구성 파이프라인을 사용하여 다른 유형의 CDN 구성을 선언하고 배포할 수 있습니다. [자세히 알아보기](/help/implementing/dispatcher/cdn-configuring-traffic.md) 이메일로 얼리어답터 프로그램에 참여 **<aemcs-cdn-config-adopter@adobe.com>** 액세스 권한을 얻으려면:

* 301/302 클라이언트측 리디렉션
* 에지에서 요청을 임의 원본(예: 비 AEM 애플리케이션)으로 프록시 설정
* URL 변환
* 요청 또는 응답 헤더 설정 또는 수정
* CDN이 AEM에 연결할 수 없는 경우의 사용자 정의 오류 페이지

#### 재작성 맵의 Apache/Dispatcher 런타임 수집(얼리 어답터 프로그램) {#apache-rewritemaps-early-adopter}

AEM 6.5와 마찬가지로 Apache/Dispatcher는 웹 계층 파이프라인 실행 없이도 게시 저장소의 특정 위치에 배치된 재작성 맵을 수집하여 로드합니다. 이렇게 하면 비즈니스 사용자가 ACS Commons 리디렉션 맵 관리자에서 제공하는 UI와 같은 UI를 사용하여 리디렉션을 선언할 수 있습니다. 에게 문의하십시오. **<aemcs-cdn-config-adopter@adobe.com>** 추가 정보.

#### Dynamic Content(Early Adopter 프로그램) 로드를 위한 ESI(Edge Side Includes) {#esi-early-adopter}

이제 Adobe 관리 CDN은 에지 수준의 다이내믹 웹 컨텐츠 어셈블리에 대한 마크업 언어인 ESI(Edge Side Includes)를 지원합니다. ESI 스니펫을 포함하면 더 높은 TTL로 CDN의 전체 HTML 페이지를 캐시하는 동시에 더 높은 케이던스 업데이트(더 낮은 TTL)가 필요한 더 작은 섹션을 원본에서 더 자주 가져올 수 있습니다. 에게 문의하십시오. **<aemcs-cdn-config-adopter@adobe.com>** 추가 정보.

#### 사이트 테마 및 사이트 템플릿을 사용하는 프론트엔드 코드에 대한 RDE 지원(얼리 어답터 프로그램) {#rde-frontend-early-adopter}

[신속한 개발 환경(RDE)](/help/implementing/developing/introduction/rapid-development-environments.md)은 이제 얼리 어답터에 대해 [사이트 테마](/help/sites-cloud/administering/site-creation/site-themes.md) 및 [사이트 템플릿](/help/sites-cloud/administering/site-creation/site-templates.md)을 기반으로 하는 프론트 엔드 코드를 지원합니다. RDE를 사용하면 [프론트 엔드 파이프라인](/help/sites-cloud/administering/site-creation/enable-front-end-pipeline.md)이 아닌 명령줄 지시문을 사용하여 이 작업이 수행됩니다. 에게 문의하십시오. **<aemcs-rde-support@adobe.com>** 사용해 보고 피드백을 제공해 주십시오.

#### RDE에 대한 로깅 개선(얼리 어답터 프로그램) {#rde-logging-early-adopter}

에서 코드를 디버깅하는 동안 [신속한 개발 환경(RDE)](/help/implementing/developing/introduction/rapid-development-environments.md)이제 개발자는 버전 제어에서 OSGI 속성을 수정하지 않고도 명령줄을 사용하여 로그를 보다 효율적으로 구성하고 스트리밍할 수 있습니다. 기능은 다음과 같습니다.

* 패키지 또는 클래스 수준별로 로그 수준 선언
* 로그 출력 형식 사용자 지정
* 여러 로그를 동시에 스트리밍

에게 문의하십시오. **<aemcs-rde-support@adobe.com>** 사용해 보고 피드백을 제공해 주십시오.

## Cloud Manager {#cloud-manager}

[여기](/help/implementing/cloud-manager/release-notes/current.md)에서 Cloud Manager 월별 릴리스의 전체 목록을 찾을 수 있습니다.

## 마이그레이션 도구 {#migration-tools}

[여기](/help/journey-migration/release-notes/release-notes-migration-tools-current.md)에서 마이그레이션 도구의 전체 목록을 찾을 수 있습니다.
