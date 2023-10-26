---
title: ' [!DNL Adobe Experience Manager] as a Cloud Service의 2023.9.0 릴리스 정보입니다.'
description: ' [!DNL Adobe Experience Manager] as a Cloud Service의 2023.9.0 릴리스 정보입니다.'
source-git-commit: 8f6611bdee755e0aa6f59c8f322a26cd1a071f23
workflow-type: tm+mt
source-wordcount: '1443'
ht-degree: 98%

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
>릴리스와 직접적으로 관련되지 않는 설명서 업데이트의 세부 정보는 [설명서 업데이트](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html)를 참조하십시오.

## 릴리스 일자 {#release-date}

[!DNL Adobe Experience Manager]인 [!DNL Cloud Service]의 현재 기능 릴리스(2023.9.0)의 날짜는 2023년 9월 28일입니다. 다음 기능 릴리스(2023.10.0)는 2023년 10월 26일에 예정되어 있습니다.

## 유지 관리 릴리스 정보 {#maintenance}

[ 여기](/help/release-notes/maintenance/latest.md)에서 최신 유지 관리 릴리스 정보를 확인할 수 있습니다.

## 릴리스 비디오 {#release-video}

2023년 9월 릴리스 개요 비디오를 통해 2023.9.0 릴리스에 추가된 기능에 대한 간단한 요약을 살펴보십시오.

>[!VIDEO](https://video.tv.adobe.com/v/3424826/?quality=12)

## AEM Edge Delivery Services {#edge-delivery}

Edge Delivery는 고객 상호 작용 시점에서 측정 가능한 비즈니스 결과를 도출하기 위해 콘텐츠가 미치는 영향을 극대화하는 데 역점을 둔 구성 가능한 새로운 서비스 세트입니다.

[여기](/help/edge/overview.md)에 있는 문서에서 Edge Delivery Services에 대해 자세히 알아보십시오.

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### Assets 보기의 새로운 기능 {#assets-view-features}

**폴더에 메타데이터 양식 할당**

이제 배포 내의 특정 폴더에 메타데이터 양식을 할당할 수 있습니다. 하위 폴더의 자산을 포함한 폴더의 모든 자산에는 할당된 메타데이터 양식에 정의된 속성이 표시됩니다.

![폴더에 메타데이터 양식 할당](/help/release-notes/assets/assign-to-folder.png)

### 관리자 보기의 새로운 기능 {#admin-view-features}

* **AEM Assets as a Cloud Service를 Edge Delivery Services용 문서 기반 작성과의 통합**: AEM Assets를 Edge Delivery Services용 문서 기반 작성과 통합하면 웹 사이트 작성자가 [Microsoft Word 또는 Google Docs에서 문서를 작성하는 동안 AEM Assets 저장소에서 사용 가능한 이미지를 사용할 수 있습니다](/help/edge/using.md#integrate-assets-edge).

* **ZIP 아카이브 추출**: Experience Manager에서 관리하는 ZIP 아카이브를 선택하고, 다운로드하지 않고도 [Experience Manager로 직접 파일을 추출하는](/help/assets/manage-digital-assets.md#extract-zip-archives) 기능.

  ![그룹에 맞는 항목 고정](/help/release-notes/assets/extract-archive.png)

### [!DNL Experience Manager Assets]에서 사용할 수 있는 프리릴리스 기능 {#prerelease-features-assets}

* **Dynamic Media**: [Dynamic Media로 비디오의 다중 자막 및 다중 오디오 트랙 지원](/help/assets/dynamic-media/video.md#about-msma) —이제 기본 비디오에 여러 개의 자막과 오디오 트랙을 손쉽게 추가할 수 있습니다. 즉, 이러한 기능을 통해 글로벌 대상자는 비디오에 액세스할 수 있습니다. 여러 언어로 글로벌 대상자에게 게시된 하나의 기본 비디오를 사용자 정의하고 지역별 액세스 가능성 가이드라인을 준수할 수 있습니다. 작성자는 사용자 인터페이스의 단일 탭에서 자막 및 오디오 트랙을 관리할 수도 있습니다.

  ![선택한 비디오 자산의 속성 페이지에 있는 자막 및 오디오 트랙 탭입니다.](/help/release-notes/assets/msma-aem-cs.png)*선택한 비디오 자산의 속성 페이지에 있는 자막 및 오디오 트랙 탭입니다.*

## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### [!DNL Experience Manager Forms]의 새로운 기능 {#forms-features}

* [**Google reCAPTCHA 엔터프라이즈 지원**](/help/forms/captcha-adaptive-forms-core-components.md): 적응형 양식에서 Google reCAPTCHA Enterprise를 사용해 사기 행위 및 스팸 방지 기능을 강화하여 보다 안전한 사용자 환경을 제공합니다. 고급 위험 분석 및 원활한 통합을 통해 실제 사용자가 양식을 쉽게 제출할 수 있는 동시에 봇이 효과적으로 차단됩니다.

* [**양식용 Experience Cloud 설정 자동화를 사용하는 Adobe Analytics**](/help/forms/enable-adobe-analytics-adaptive-form-using-experience-cloud-setup-automation.md): 이제 버튼 클릭 몇 번이면 Experience Cloud 설정 자동화를 사용하여 Adobe Analytics를 활성화할 수 있습니다. 이를 통해 AEM Forms as a Cloud Service를 Experience Platform 태그 및 Adobe Analytics와 연결하여 게시된 양식에 대한 성능 지표를 캡처하고 추적할 수 있습니다.

  >[!VIDEO](https://video.tv.adobe.com/v/3424577/enable-adobe-analytics/?quality=12&learn=on)

* [**적응형 양식용 Adobe Analytics 보고서 템플릿**](/help/forms/view-understand-aem-forms-analytics-reports.md): 이제 Forms as a Cloud Service는 Adobe Analytics 보고서 OOTB를 제공합니다. 이렇게 하면 양식의 성능을 손쉽게 이해할 수 있습니다. 양식 수준 지표를 통해 렌디션, 방문자, 제출, 평균 채우기 시간 등 여러 주요 성과 지표(KPI)에서 양식이 어떻게 수행되는지에 대한 인사이트를 얻습니다. 사용자 행동 및 피드백을 추적하여 혼동을 주는 양식의 영역을 식별하고 양식의 디자인 및 기능을 개선할 수 있습니다.

  ![적응형 사용자 참여 Adobe Analytics 보고서](/help/forms/assets/forms-analytics-report.png)

* **[핵심 구성 요소 기반 적응형 양식의 양식 조각](/help/forms/adaptive-form-fragments-core-components.md)**: 양식 조각으로 양식 작성 경험을 높이면서 중복을 제거하고, 디지털 인벤토리를 최적화하고, 공동 작업을 개선합니다. 이러한 재사용 가능한 구성 요소는 여러 양식에 원활하게 통합되어 일관성 있게 전문가 수준의 양식 작성을 간소화합니다. 양식 조각의 “한번 변경하여 전체 반영” 기능을 통해 재사용성, 표준화와 브랜드 일관성을 보장합니다. 한 위치에서의 업데이트가 이러한 조각을 활용하는 모든 양식에 자동으로 전파되므로 유지 관리 가능성과 효율성이 개선됩니다.

* **[개선된 Adobe Sign 워크플로 단계](/help/forms/aem-forms-workflow-step-reference.md#sign-document-step-sign-document-step)**: Adobe Sign 워크플로 단계는 다음을 포함하도록 개선되었습니다.
   * **Adobe Sign의 정부 ID 기반 인증**: Adobe Acrobat Sign의 정부 ID 기반 인증은 사용자가 정부에서 발급한 ID(운전면허증, 주민등록증, 여권)를 사용하여 자신의 ID를 인증할 수 있도록 추가 확인 계층을 제공합니다. 신뢰할 수 있는 식별 문서를 활용하여 이 개선된 기능은 서명 프로세스에 신뢰도를 추가하여 보안, 규정 준수 및 사용자 유효성 검사 강화에 필요한 시나리오에 적합합니다.

   * **Adobe Sign 문서의 감사 추적**: 감사 추적 기능을 사용하여 Adobe Sign 문서의 수명 주기에 대한 세부 인사이트를 얻을 수 있습니다. 감사 추적을 사용하여 이제 문서와 관련된 모든 작업과 상호 작용에 대한 포괄적인 기록을 유지 관리할 수 있습니다. 여기에는 각 이벤트의 타임스탬프와 함께 문서를 조회하고, 편집하거나 서명한 사람 등과 같은 세부 정보가 포함됩니다. 이러한 개선된 기능은 규정 준수를 유지하고, 분쟁을 해결하고, 디지털 계약의 무결성을 보장하는 데 중요합니다.

   * **계약 수신자의 새 역할이 서명자 이상으로 확장**: Adobe Acrobat Sign은 계약 수신자의 역할을 서명자 이상으로 확장하여 워크플로 요구 사항에 보다 잘 부합하도록 할 수 있습니다. 활성화되면 계약의 각 수신자는 자신의 역할을 개별 구성할 수 있으며 서명자는 기본 역할입니다.

* **커뮤니케이션 API의 페이지 카운트 지원**: 이제 커뮤니케이션 API를 통해 문서를 검색하는 동시에 문서 내 포함된 페이지의 수에 대한 중요한 정보를 받을 수도 있습니다.

* **[규칙 편집기의 사용자 정의 오류 핸들러로 오류 처리](/help/forms/add-custom-error-handler-adaptive-forms-core-components.md)**: 이제 외부 서비스에서 반환되는 오류에 따라 사용자 정의 함수를 호출하여 맞춤형 응답을 최종 사용자에게 제공할 수 있습니다. 예를 들어 특정 오류 코드의 백엔드에서 사용자 정의 워크플로를 호출하거나 서비스가 중단되었음을 고객에게 알려 줄 수 있습니다.

* **[64비트 버전의 AEM Forms Designer](/help/forms/installing-configuring-designer.md)**: 64비트 버전의 AEM Forms Designer는 향상된 성능, 확장성과 메모리 관리 기능을 통해 양식 생성 경험을 지원합니다. 64비트 아키텍처를 사용하면 더 크고 복잡한 프로젝트를 간단하게 처리하여 원활한 워크플로 디자인과 최적화된 효율성을 보장할 수 있습니다. 이 혁신적인 릴리스를 통해 양식 디자인 기능을 개선하고 AEM Forms Designer를 진전시킬 수 있습니다.

### 얼리 어답터 프로그램 {#forms-early-adopter}

* **[DocAssurance API(Communication API의 일부)로 문서 보호](/help/forms/aem-forms-cloud-service-communications-introduction.md#document-assurance-doc-assurance)**: DocAssurance API를 사용하여 문서에 서명하고 암호화하여 민감한 정보를 보호할 수 있습니다. 문서의 콘텐츠는 암호화를 통해 읽을 수 없는 포맷으로 변환되어 권한이 있는 사용자만 액세스할 수 있습니다. 이 보호 계층이 강화되면 중요 데이터를 승인되지 않은 사용자로부터 보호할 뿐만 아니라 고객들이 안심할 수 있습니다. 서명 API를 통해 조직에서 배포하고 수신하는 Adobe PDF 문서의 보안 및 개인정보를 보호할 수 있습니다. 이 서비스는 의도한 수신자만 문서를 변경할 수 있도록 디지털 서명과 인증을 사용합니다.

  공식 이메일 ID에서 “`aem-forms-early-adopter-program@adobe.com`”으로 이메일을 보내 얼리 어답터 프로그램에 참여하여 기능에 대한 액세스 권한을 요청할 수 있습니다.

* **[Headless 적응형 양식](https://experienceleague.adobe.com/docs/experience-manager-headless-adaptive-forms/using/overview.html)**: Headless 적응형 양식을 사용하여 개발자가 기존의 그래픽 사용자 인터페이스가 아닌 API를 통해 액세스하고 상호 작용할 수 있는 대화형 양식을 만들고, 게시하고, 관리할 수 있습니다. Headless 적응형 양식은 다음에 도움이 됩니다.

   * 선택한 프로그래밍 언어로 고품질 다중 채널 양식 작성
   * 양식을 데스크탑 및 모바일 앱, 웹 사이트 및 채팅 애플리케이션에 기본적으로 통합
   * 양식 애플리케이션과 함께 독점 UI 구성 요소 재사용
   * Adobe Experience Manager Forms의 기능 사용

  공식 이메일 ID에서 `aem-forms-headless@adobe.com`으로 이메일을 보내 얼리 어답터 프로그램에 참여할 수 있습니다.

## [!DNL Experience Manager] as a [!DNL Cloud Service] Foundation {#foundation}

### 캠페인 관련 URL 매개변수에 대한 새로운 CDN 캐싱 비헤이비어 {#cache-url-params}

기본적으로 새 환경에서 CDN은 마케팅 관련 쿼리 매개변수를 제거하여 마케팅 캠페인 성과와 캐시 적중률을 높입니다. 기존 환경은 영향을 받지 않습니다. [자세히 알아보기.](/help/implementing/dispatcher/caching.md#marketing-parameters)

### 트래픽 필터 규칙(WAF 규칙 포함) 얼리 어답터 프로그램 {#waf-early-adopter}

다음을 기준으로 CDN에서 트래픽을 필터링할 수 있습니다.
* 요청 헤더 및 속성(예: IP 주소)
* 악성 트래픽과 관련된 것으로 알려진 트래픽 패턴

기능을 사용해 보고 피드백을 공유하고 싶으십니까? 공식 이메일 ID로 **aemcs-waf-adopter@adobe.com**&#x200B;에 이메일을 보내 얼리 어답터 프로그램에 대해 자세히 알아보십시오. 인원이 한정되어 있습니다.

[여기](/help/security/traffic-filter-rules-including-waf.md)에 있는 문서에서 기능에 대해 자세히 알아보십시오.

## Cloud Manager {#cloud-manager}

[여기](/help/implementing/cloud-manager/release-notes/current.md)에서 Cloud Manager 월별 릴리스의 전체 목록을 찾을 수 있습니다.

## 마이그레이션 도구 {#migration-tools}

[여기](/help/journey-migration/release-notes/release-notes-migration-tools-current.md)에서 마이그레이션 도구의 전체 목록을 찾을 수 있습니다.
