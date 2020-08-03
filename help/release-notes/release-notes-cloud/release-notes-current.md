---
title: Cloud Service의 2020.7.0 릴리스 [!DNL Adobe Experience Manager] 에 대한 릴리스 노트입니다.
description: '[!DNL Adobe Experience Manager]을(를) Cloud Service 릴리스 노트로(2020.7.0).'
translation-type: tm+mt
source-git-commit: a454bcce2d4db89c0ac8dc27fd187a822bacf7e6
workflow-type: tm+mt
source-wordcount: '968'
ht-degree: 38%

---


# Release Notes for [!DNL Adobe Experience Manager] as a Cloud Service 2020.7.0 {#release-notes}

다음 섹션에서는 클라우드 서비스 2020.7.0으로서의 Experience Manager에 대한 일반 릴리스 노트를 간략하게 설명합니다.

## 릴리스 날짜 {#release-date}

The release date for [!DNL Experience Manager] as a Cloud Service 2020.7.0 is July 30, 2020.

## Cloud Service의 Adobe Experience Manager Sites {#cloud-services-sites}

### 새로운 기능 {#what-is-new-sites}

[!DNL Experience Manager] 를 Cloud Service 커넥터 [!DNL Adobe Target] 로 사용할 수 있으며 다음과 같은 [!DNL Adobe Analytics] 방법으로 개선됩니다.

* 새 사용자 인터페이스 구현은 클래식 UI에 따른 구현을 대체합니다.

* 사용자 인터페이스 대화 상자가 간소화되면서 변수 매핑 및 기타 구성을 위한 프레임워크 생성이 종료됩니다 [!DNL Adobe Launch]. Adobe Analytics [통합](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/sites/integrations/integrating-adobe-analytics.html) 및 Adobe Target [통합을 참조하십시오](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/sites/integrations/integrating-adobe-target.html).

* 이제 구성은 Experience Manager 저장소가 `/conf` 아닌 `/etc/cloudsettings` 에 저장됩니다.

## 클라우드 서비스로서의 Adobe Experience Manager Assets {#assets}

>[!NOTE]
>AEM Assets은 향후 며칠 안에 Cloud Service 기능으로 롤아웃됩니다.

### 새로운 기능 {#what-is-new-assets}

* [!DNL Asset Compute Service] 은 자산을 처리할 수 있는 확장 가능한 서비스입니다. 관리자는 Experience Manager을 구성하여 JavaScript를 사용하여 만든 사용자 지정 작업자를 불러올 수 있습니다 [!DNL Asset Compute Service]. 개발자는 이 서비스를 사용하여 복잡한 사용 사례에 맞는 전문 맞춤형 작업자를 만들 수 있습니다. 이 웹 서비스는 다양한 파일 유형에 대한 축소판, Adobe 파일 포맷의 고품질 이미지 렌더링, 비디오 인코딩(미래), 메타데이터 추출, 색인화를 위한 사전 설정으로 전체 텍스트 추출, 사용 가능한 모든 Sensei 서비스를 통해 자산 실행 등의 작업을 수행할 수 있습니다. 자산 [마이크로서비스 및 처리 프로필 사용을 참조하십시오](/help/assets/asset-microservices-configure-and-use.md).

* Cloud Service [!DNL Dynamic Media] 로 [!DNL Experience Manager] 의 초기 구성이 더욱 강력하도록 개선되었습니다. 이제 관리자에게 프로세스 진행 상황을 제공합니다.

* 에셋 마이크로서비스를 사용하여 전체 에셋 처리 파이프라인의 필수 요소로 에셋 게시를 [!DNL Dynamic Media] 간소화하고 더욱 강력해졌습니다. 또한 일괄 게시 백엔드를 향상시켜 줍니다.

* Cloud Service 배포과 호환되지 않는 워크플로우 단계가 이제 [!UICONTROL 워크플로우 모델] 편집기에 경고로 표시됩니다. 또한 Cloud Service 환경에서 기존 워크플로우를 실행할 때 호환되지 않는 워크플로우 단계를 건너뜁니다.

* Cloud Manager의 환경과 연관된 Git 프로젝트 `/conf/global` 에 배포되는 고객이 생성한 워크플로우 모델은 자동으로 Experience Manager에 배포되어 `/var` 사용할 수 있습니다. 고객이 변경한 제품 워크플로우 모델 `/libs` 은 자동으로 배포되지 않습니다 `/var`.

## 코어 구성 요소 {#core-components}

### 새로운 기능 {#what-is-new-core-components}

Release 2.11.0 of the [AEM Core Components](https://docs.adobe.com/content/help/ko-KR/experience-manager-core-components/using/introduction.html) is now available as part of AEM Sites including:

* 새로운 [PDF 뷰어 구성 요소](https://aemcomponents.dev/content/core-components-examples/library/page-authoring/pdf-viewer.html)소개

* 이제 핵심 구성 요소에 대한 AMP(가속 모바일 페이지) 지원을 사용할 수 있습니다. Google 모바일 검색 결과에서 사이트 방문 시 즉시 페이지를 전환하여 사용자 참여도와 SEO를 향상시킴으로써 고객 경험을 신속하게 제작할 수 있습니다.
자세한 내용은 [핵심 구성 요소에 대한](https://docs.adobe.com/content/help/en/experience-manager-core-components/using/developing/amp.html) AMP 지원을 참조하십시오.

* Adobe 클라이언트 데이터 레이어의 버전 1.0.2와의 [호환성](https://docs.adobe.com/content/help/en/experience-manager-core-components/using/developing/data-layer/overview.html).

* 버그 수정 및 코드 품질 개선

## Cloud Manager {#cloud-manager}

### 릴리스 날짜 {#release-date-cm}

[!UICONTROL Cloud Manager] 버전 2020.7.0의 릴리스 날짜는 2020년 7월 9일입니다.

### 새로운 기능 {#what-is-new-cloud-manager}

* 환경 페이지가 다시 디자인되었습니다.

* 최대 절전 모드인 환경에서 이제 최대 절전 모드일 경우 Cloud Manager에서 개별 상태를 볼 수 있습니다.

* 환경당 환경 변수의 수가 200개로 증가했습니다.

* 이제 Cloud Manager 파이프라인이 고객 설정 변수 및 기밀을 지원합니다.

   자세한 내용은 [파이프라인 변수](/help/onboarding/getting-access-to-aem-in-cloud/creating-aem-application-project.md#pipeline-variables)를 참조하십시오.

### 버그 수정 {#bug-fixes-cm}

* 환경이 완전히 만들어지기 전에 Cloud Manager에서 개발자 콘솔로의 링크가 잘못 활성화되었습니다.

* Cloud Manager에서 직접 개발자 콘솔로 연결되는 링크에는 샌드박스 프로그램 환경의 최대 절전 모드 해제/최대 절전 모드 해제 옵션이 표시되지 않습니다.

* 비프로덕션 파이프라인 편집 페이지의 **취소** 및 **저장** 옵션이 항상 표시되는 것은 아닙니다.

* 코드 품질 프로세스의 일부 오류로 인해 로그 파일이 올바로 생성되지 않을 수 있습니다.

* 새 프로그램을 만들 때 제안된 이름은 기존 프로그램 이름의 복제본을 반환하는 경우가 있습니다.

* 일부 큰 파이프라인 단계 로그를 사용자 인터페이스를 통해 일관되게 다운로드할 수 없습니다.

* 환경 이름의 유효성 검사에 오류가 발생했습니다.

* 환경 페이지는 존재하지 않을 때 게시 및 발송자 세그먼트를 표시하는 경우가 있습니다.

### 알려진 문제 {#known-issues}

* 코드 검사 계산 방식의 변경으로 인해 Jacoco 플러그인의 *최소* 버전은 이제 0.7.5.201505241946(2015년 5월 릴리스)입니다. 이전 버전을 명시적으로 참조하는 고객은 코드 품질 프로세스에서 오류 메시지가 표시됩니다.


## Adobe Experience Manager as a Cloud Service Foundation {#cloud-foundation}

### 새로운 기능 {#what-is-new-foundations}

* [Splunk 계정에](/help/implementing/developing/introduction/logging.md#splunk-logs)로그를 전달할 수 있으므로 기업은 Splunk 투자를 활용할 수 있습니다.

* [정적 전용 송신 IP 주소는](/help/implementing/developing/introduction/development-guidelines.md#dedicated-egress-ip-address) Java 코드로 프로그래밍된 아웃바운드 트래픽에 할당될 수 있으며, 일부 통합에 유용합니다.

* AEM Analytics 클라우드 서비스 UI를 클래식 UI에서 새 AEM UI로 포팅했습니다. 또한 AEM 저장소의 Analytics 클라우드 서비스 위치를 다른 AEM cloud services `/etc` 에 맞게 `/conf`이동했습니다.

* 클래식 UI에서 새 AEM UI로 AEM Target 클라우드 서비스 UI를 포팅했습니다. 또한 AEM 저장소의 Target 클라우드 서비스 위치를 다른 AEM cloud services `/etc` 에 맞게 `/conf`이동했습니다.

## 클라우드 준비 분석기 {#cloud-readiness-analyzer}

이 섹션을 통해 Cloud Readiness Analyzer 릴리스 버전 1.0.2에 대한 새로운 기능 및 업데이트를 알아보십시오.

### 버그 수정 {#cra-bug-fixes}

* AEM(Adobe Experience Manager) 6.1에서 이전 버전의 CRA를 실행할 수 없습니다. 관리자 그룹의 사용자를 허용하는 명시적 지원이 추가되었습니다.

   자세한 내용은 [AEM 6.1에 CRA 설치](https://docs.adobe.com/content/help/ko-KR/experience-manager-cloud-service/moving/cloud-migration/cloud-readiness-analyzer/using-cloud-readiness-analyzer.html#installing-on-aem61)를 참조하십시오.

* 요약 보고서에 표시되는 만료 타임스탬프가 잘못되었습니다.

* CRA가 중복된 사용자 지정 구성 요소를 감지하고 있습니다.

* AEM 6.1에서 전체 검사를 완료하기 전에 컨텐츠 검사를 종료했습니다. 전체 검사가 완료될 때까지 검사자가 건너뛸 수 있도록 예외 처리가 추가되었습니다.
