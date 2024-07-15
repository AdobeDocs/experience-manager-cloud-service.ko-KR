---
title: ' [!DNL Adobe Experience Manager] as a Cloud Service의 2024.3.0 릴리스 정보입니다.'
description: ' [!DNL Adobe Experience Manager] as a Cloud Service의 2024.3.0 릴리스 정보입니다.'
exl-id: b3816929-2c0a-4d6a-b583-c928d2182ecd
feature: Release Information
role: Admin
source-git-commit: 8d5d8910a906e2adf17fa9c75f17634602c2e0b9
workflow-type: tm+mt
source-wordcount: '2292'
ht-degree: 94%

---

# [!DNL Adobe Experience Manager] as a Cloud Service 2024.3.0 릴리스 정보 {#release-notes}

다음 섹션에서는 [!DNL Experience Manager] as a Cloud Service의 2024.3.0 버전 기능 릴리스 정보에 대해 간략히 소개합니다.

>[!NOTE]
>
>여기에서 2021년 또는 2022년과 같은 이전 버전의 릴리스 정보로 이동할 수 있습니다.
>
>[!DNL Experience Manager] as a Cloud Service의 향후 기능 활성화에 대해 알아보려면 [Experience Manager 릴리스 로드맵](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html)을 살펴보십시오.

>[!NOTE]
>
>릴리스와 직접적으로 관련되지 않는 설명서 업데이트의 세부 정보는 [최신 설명서 업데이트](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html)를 참조하십시오.

## 릴리스 일자 {#release-date}

[!DNL Adobe Experience Manager] as a [!DNL Cloud Service] 현재 기능 릴리스(2024.3.0)의 릴리스 일자는 2024년 4월 11일입니다. 다음 기능 릴리스(2024.4.0)는 2024년 4월 25일에 예정되어 있습니다.

## 유지 관리 릴리스 정보 {#maintenance}

[ 여기](/help/release-notes/maintenance/latest.md)에서 최신 유지 관리 릴리스 정보를 확인할 수 있습니다.

## 릴리스 비디오 {#release-video}

2024년 3월 릴리스 개요 비디오를 통해 2024.3.0 릴리스에 추가된 기능에 대한 간단한 요약을 살펴보십시오.

>[!VIDEO](https://video.tv.adobe.com/v/3428342?quality=12)

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### [!DNL Experience Manager Sites]의 새로운 기능 {#sites-features}

**Edge Delivery Services를 위한 AEM 작성**

이제 AEM Sites를 Edge Delivery Services의 콘텐츠 소스로 사용할 수 있습니다. 작성자는 새로운 Universal Editor 내 컨텍스트 wysiwyg 작성을 사용하여 AEM에서 웹 사이트를 관리합니다. 이를 통해 기업은 AEM의 강력한 콘텐츠 관리 기능을 활용하면서 Edge Delivery Services를 통해 빠른 고성능 웹 페이지를 빌드할 수 있습니다.

![AEM 작성](/help/edge/assets/universal_editor_edge_delivery_services.png)

자세한 내용은 [설명서](/help/edge/overview.md)를 참조하고 [AEM Gems - AEM Authoring 및 Edge Delivery Services 시작하기](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-manager/aem-gems-getting-started-with-aem-authoring-and-edge-delivery/m-p/652694#M43905)를 시청하십시오.

**Headless 구현을 위한 Universal Editor**

Universal Editor를 사용하면 분리된 웹 애플리케이션을 통해 이전에 기존 사이트에서만 가능했던 직관적인 컨텍스트 내 WYSIWYG 작성을 동일하게 활용할 수 있습니다. 이제 콘텐츠 작성자는 페이지 내의 구성 요소와 마찬가지로 쉽게 콘텐츠 조각을 사용하여 레이아웃을 시각적으로 구성할 수 있습니다.

Universal Editor를 차별화하는 점은 서버측 렌더링과 클라이언트측 렌더링을 모두 수용하고, 프레임워크에 구애받지 않으며, AEM 호스팅의 필요성을 없애는 등 다양한 웹 아키텍처에 대한 적응성입니다. 콘텐츠 편집을 위해 기존 웹 애플리케이션을 Universal Editor와 통합하는 것은 간단하며, 주로 개발자가 특정 데이터 속성을 마크업에 통합해야 합니다.

이를 통해 Universal Editor는 콘텐츠 구조나 기본 기술 스택에 관계없이 일관된 편집 경험을 보장합니다. 자세한 내용은 [Universal Editor 소개](/help/implementing/universal-editor/introduction.md)를 참조하십시오.

**콘텐츠 조각 및 모델을 위한 콘텐츠 관리 OpenAPI**

이제 개발자는 콘텐츠 조각 및 콘텐츠 조각 모델과 프로그래밍 방식으로 상호 작용하고 콘텐츠 관리 OpenAPI를 사용하여 CruD 작업을 수행할 수 있습니다. 자세한 내용은 [API 설명서](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/stable/sites/)를 참조하십시오.

**경험 조각에 대한 다중 사이트 관리 지원**

경험 조각을 저장하는 폴더 구조에 대한 다중 사이트 관리 지원이 확장되어 사용자가 경험 조각으로 전체 콘텐츠 구조를 롤아웃할 수 있습니다.

**콘텐츠 조각 버전 비교**

이제 새로운 콘텐츠 조각 편집기를 사용하면 콘텐츠 작성자가 콘텐츠 조각의 현재 버전과 이전 버전 간의 차이점을 비교하고 볼 수 있습니다.

### 얼리 어답터 프로그램 {#sites-early-adopter}

**변형 생성**

이제 클라우드 서비스에서 액세스 가능한 AEM의 새로운 기능인 [변형 생성](/help/generative-ai/generate-variations.md)을 통해 GenAI를 활용할 수 있습니다. 변형 생성은 생성형 AI를 사용하여 콘텐츠 제작을 생성하고 확장하는 데 도움이 됩니다. 프로그램 참여를 고려한다면 Adobe 계정 팀에 문의하십시오.

**콘텐츠 조각 콘솔에서 자산 찾아보기**

이제 콘텐츠 작성자는 콘텐츠 조각 콘솔을 종료하지 않고도 이미지 및 기타 자산을 찾아보고, 보고, 작업을 수행할 수 있습니다.

![자산 찾아보기](/help/sites-cloud/administering/content-fragments/assets/cf-console-assets-browse.png)

기능을 사용해 보고 피드백을 공유하고 싶으십니까? 공식 이메일 ID로 aemcs-headless-adopter@adobe.com에 이메일을 보내 얼리 어답터 프로그램에 대해 자세히 알아보십시오.

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### 관리자 보기의 새로운 기능 {#admin-view}

**Adobe Express와의 네이티브 통합**

AEM Assets는 Adobe Express에 기본적으로 통합되므로 Adobe Express 사용자 인터페이스 내에서 AEM Assets에 저장된 자산에 직접 액세스할 수 있습니다. AEM Assets에서 관리되는 콘텐츠를 Express 캔버스에 배치한 다음 AEM Assets 저장소에 새 콘텐츠 또는 편집된 콘텐츠를 저장할 수 있습니다.

![Assets 추가 기능에서 자산 포함](/help/assets/assets/adobe-express-native-integration.png)

**지원되는 모든 비디오 유형에 대한 미리보기 렌디션**

Experience Manager Assets는 이제 처리 프로필 구성 없이 기본적으로 지원되는 모든 비디오 유형의 미리보기 렌디션을 생성합니다.

### Assets 보기의 새로운 기능 {#assets-view}

**컬렉션에 대한 권한 관리**

Assets Essentials에서 관리자는 저장소에서 사용할 수 있는 비공개 컬렉션에 대한 액세스 수준을 관리할 수 있습니다. 관리자는 사용자 그룹을 만든 다음 해당 그룹에 액세스 수준을 관리하도록 권한을 할당할 수 있습니다. 또한 사용자 그룹에 권한 관리 권한을 위임할 수도 있습니다.


## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

<!-- 

* **Configure a shard for Adobe Sign for AEM Forms**: Adobe distributes Acrobat Sign API around the globe in many deployment units called "shards." Each shard serves a customer's account, such as NA1, NA2, NA3, EU1, JP1, AU1, IN1, and others. The shard names correspond to geographic locations. You can now use more than one shard while using Adobe Sign integration with AEM Forms. 

-->

### AEM Forms의 새로운 기능 {#forms-new-features}

* **[Adobe Experience Manager Forms Edge Delivery Services](/help/edge/docs/forms/overview.md)**: AEM Forms Edge Delivery Services는 새 양식을 빠르게 업데이트, 게시 및 시작할 수 있는 신속한 개발 환경을 지원하는 구성 가능한 서비스 세트입니다. 이러한 서비스는 참여와 전환을 촉진하는 탁월하고 영향력 있는 양식 경험을 선사합니다. 이러한 양식 환경은 쉽게 작성하고 개발할 수 있습니다.

  ![EDS 양식 기능](/help/edge/assets/eds-forms-features.png)

이러한 서비스를 통해 다음이 가능합니다.

* 동일한 양식 사이트에서 여러 콘텐츠 소스로 작업하고 Microsoft Excel, Google Sheets 또는 적응형 양식 편집기 등 선호하는 작성 도구를 사용합니다.
* RUM(실시간 사용 모니터링)을 통해 양식 성능을 빠르고 지속적으로 모니터링하는 로드 및 렌더링의 디지털 등록 경험을 제공합니다.
* 일반 HTML, 최신 CSS 및 바닐라 JavaScript를 사용하여 특정 프레임워크의 가파른 학습 곡선을 방지하면서 뛰어난 경험을 창출합니다.


### AEM Forms 프리릴리스의 새로운 기능 {#forms-pre-release}

* **핵심 구성 요소 기반 적응형 양식을 위한 향상된 시각적 규칙 편집기**: 이 릴리스에서는 핵심 구성 요소 기반 적응형 양식을 위한 시각적 규칙 편집기가 대폭 업그레이드되었습니다. 이 릴리스에서는 핵심 구성 요소 기반 적응형 양식을 위한 시각적 규칙 편집기가 대폭 업그레이드되었습니다. 이 업데이트는 사용자 정의 함수와의 상호 작용을 간소화하여 더욱 강력하고 효율적인 양식을 빌드할 수 있도록 하는 데 중점을 둡니다.

  이제 다음을 통해 사용자 정의 함수 상호 작용을 간소화할 수 있습니다.

   * 새 주석을 활용하여 더 명확한 함수 정의를 제공합니다.
   * 사용자 지정 함수에 캐싱 메커니즘을 사용하여 양식 성능 향상
   * 사용자 지정 함수 내에서 전역 개체와 원활하게 작업할 수 있습니다.
   * 사용자 지정 함수 내에서 선택적 매개 변수를 정의하고 활용합니다.

  이 업데이트는 또한 규칙 편집기 기능에 다음과 같은 향상된 기능을 제공합니다. 다음과 같은 작업을 수행할 수 있습니다.

   * 조건부 실행에 강력한 &quot;when-then-else&quot; 논리를 구현합니다.
   * let 및 arrow 함수(ES10 지원)와 같은 최신 JavaScript 기능을 활용합니다.
   * 필드뿐만 아니라 전체 패널과 양식도 검증하거나 재설정하여 사용자 상호 작용에 대한 제어를 확장합니다.

  이러한 개선 사항은 시각적 규칙 편집기 내에서 규칙 및 사용자 정의 함수를 작성하는 데 더욱 직관적이고 강력한 경험을 제공합니다.

* **다양한 버전의 적응형 양식 만들기**: 이제 기존 양식의 변형을 쉽게 관리할 수 있습니다. 이에 따라 간소화된 단일 워크플로 내에서 버전 제어가 단순화되고, 양식 최적화를 위한 비교가 용이해집니다.

* **적응형 양식 비교**: 이제 두 양식을 쉽게 비교하여 두 양식 간의 차이점을 확인할 수 있습니다. 팀원이 수정본을 비교하고 변경 사항을 효율적으로 논의할 수 있도록 하여 원활한 공동 작업을 촉진합니다.

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

* **Reader 확장 서비스**: AEM Forms 커뮤니케이션 API는 일반 PDF에 양식 채우기 및 주석 달기와 같은 기능을 추가하여, 무료 Adobe Reader를 사용하는 사용자가 대화형으로 이용할 수 있는 Reader 확장 서비스를 제공합니다.

* [오른쪽에서 왼쪽 방향 언어 지원](/help/forms/supporting-new-language-localization-core-components.md): 이제 핵심 구성 요소를 기반으로 빌드된 적응형 양식을 아랍어, 페르시아어, 우르두어와 같은 오른쪽에서 왼쪽 방향(RTL) 언어로 표시할 수 있습니다. RTL 언어의 사용자는 전 세계적으로 20억 명이 넘습니다. RTL 언어로 된 양식을 사용하면 적응형 양식의 범위를 확장하여 더 다양성 높게 대상자를 수용하고 RTL 시장을 선택할 수 있습니다. 특정 지역에서는 현지 언어로 양식을 제공하는 것이 법적 의무이기도 합니다. 현지 언어를 수용함으로써 더 많은 대상자에게 접근할 수 있을 뿐만 아니라 관련 법률 및 규정을 준수할 수 있습니다.

* **[DocAssurance API(Communication API의 일부)로 문서 보호](/help/forms/aem-forms-cloud-service-communications-introduction.md#document-assurance-doc-assurance)**: DocAssurance API를 사용하여 문서에 서명하고 암호화하여 민감한 정보를 보호할 수 있습니다. 문서의 콘텐츠는 암호화를 통해 읽을 수 없는 포맷으로 변환되어 권한이 있는 사용자만 액세스할 수 있습니다. 이 보호 계층이 강화되면 중요 데이터를 승인되지 않은 사용자로부터 보호할 뿐만 아니라 고객들이 안심할 수 있습니다. 서명 API를 통해 조직에서 배포하고 수신하는 Adobe PDF 문서의 보안 및 개인정보를 보호할 수 있습니다. 이 서비스는 의도한 수신자만 문서를 변경할 수 있도록 디지털 서명과 인증을 사용합니다.

  공식 이메일 ID에서 “`aem-forms-ea@adobe.com`”으로 이메일을 보내 얼리 어답터 프로그램에 참여하여 기능에 대한 액세스 권한을 요청할 수 있습니다.

* **[RUM(Real Use Monitoring) 데이터 서비스](/help/implementing/cloud-manager/content-requests.md#real-user-monitoring-for-aem-as-a-cloud-service)**를 활용하여 AEM as a Cloud Service에 대해 클라이언트측 수집을 사용하도록 설정할 수 있습니다.
RUM(Real Use Monitoring) 데이터 서비스는 사용자 상호 작용을 보다 정확하게 반영하여 웹 사이트 참여를 안정적으로 측정합니다. 이를 통해 페이지 성능에 대한 고급 인사이트를 얻을 수 있습니다. 이는 Adobe가 관리하는 CDN 또는 Adobe가 관리하지 않는 CDN을 사용하는 고객 모두에게 유용합니다. 또한 Adobe가 관리하지 않는 CDN을 사용하는 고객의 경우 이제 자동화된 트래픽 보고를 활성화할 수 있으므로 트래픽 보고서를 Adobe와 공유할 필요가 없습니다.

  이 새로운 기능을 테스트하고 피드백을 공유하는 데 관심이 있으시면 Adobe ID와 연결된 이메일 주소를 통해 RUM을 활성화하고자 하는 각 환경에 대한 도메인 이름과 함께 `aemcs-rum-adopter@adobe.com`으로 이메일을 보내 주십시오. 그런 다음 Adobe의 제품 팀이 RUM(Real Use Monitoring) 데이터 서비스를 활성화합니다.

## [!DNL Experience Manager] as a [!DNL Cloud Service] Foundation {#foundation}

### 얼리 어답터 프로그램 {#foundation-early-adopter}

#### 트래픽 필터 규칙 경고(얼리 어답터 프로그램) {#traffic-filter-rules-alerts-early-adopter}

선택적으로 라이선스를 부여할 수 있는 WAF(웹 애플리케이션 방화벽) 규칙을 포함하는 최근 릴리스된 [트래픽 필터 규칙](/help/security/traffic-filter-rules-including-waf.md)을 통해 허용하거나 거부해야 하는 트래픽을 구성할 수 있습니다.

지금 **<aemcs-cdn-config-adopter@adobe.com>**&#x200B;으로 이메일을 보내 얼리 어답터 프로그램에 참여하면 트래픽 필터 규칙이 실행될 때마다 알림을 받을 수 있습니다. 액션 센터 이메일 알림은 특정 트래픽 상황이 발생할 때 적절한 조치를 취할 수 있도록 지속적으로 정보를 제공해 줍니다.

#### CDN 구성(얼리 어답터 프로그램) {#cdn-config-early-adopter}

선택적으로 라이선스를 부여할 수 있는 WAF(웹 애플리케이션 방화벽) 규칙을 포함하는 최근 릴리스된 [트래픽 필터 규칙](/help/security/traffic-filter-rules-including-waf.md) 외에도 구성 파이프라인을 사용하여 다른 유형의 CDN 구성을 선언하고 배포할 수 있습니다. [자세히 알아보고](/help/implementing/dispatcher/cdn-configuring-traffic.md) **<aemcs-cdn-config-adopter@adobe.com>**&#x200B;으로 이메일을 보내 얼리 어답터 프로그램에 참여하십시오. 다음에 대한 액세스 권한을 받을 수 있습니다.

* 301/302 클라이언트측 리디렉션
* 에지의 요청을 임의 출처(예: AEM이 아닌 애플리케이션)로 프록시 처리
* URL 변환
* 요청 또는 응답 헤더 설정 또는 수정
* CDN이 AEM에 연결할 수 없는 경우의 사용자 정의 오류 페이지

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

## Cloud Manager {#cloud-manager}

[여기](/help/implementing/cloud-manager/release-notes/current.md)에서 Cloud Manager 월별 릴리스의 전체 목록을 찾을 수 있습니다.

## 마이그레이션 도구 {#migration-tools}

[여기](/help/journey-migration/release-notes/release-notes-migration-tools-current.md)에서 마이그레이션 도구의 전체 목록을 찾을 수 있습니다.
