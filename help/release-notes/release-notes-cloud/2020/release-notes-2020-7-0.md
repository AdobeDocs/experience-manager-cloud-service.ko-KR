---
title: ' [!DNL Adobe Experience Manager] as a Cloud Service 2020.7.0 릴리스의 릴리스 노트'
description: "[!DNL Adobe Experience Manager] as a Cloud Service 릴리스 노트(220.0)"
exl-id: 75d354a3-6987-4de0-aec8-24043461c516
feature: Release Information
role: Admin
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '1012'
ht-degree: 73%

---

# as a Cloud Service [!DNL Adobe Experience Manager] 2.020.0 릴리스 정보 {#release-notes}

다음 섹션에서는 Experience Manager as a Cloud Service 2020.7.0 일반 릴리스 노트를 간략하게 설명합니다.

## 릴리스 일자 {#release-date}

[!DNL Experience Manager] as a Cloud Service 2020.7.0 릴리스 날짜는 2020년 7월 30일입니다.

## Adobe Experience Manager Sites as a Cloud Service {#cloud-services-sites}

### 새로운 기능 {#what-is-new-sites}

[!DNL Adobe Target] 및 [!DNL Adobe Analytics]의 [!DNL Experience Manager] as a Cloud Service 커넥터로서 다음과 같이 개선되었습니다.

* 새 사용자 인터페이스 구현으로 클래식 UI 기반의 구현을 대체합니다.

* 변수 매핑과 기타 구성을 위한 프레임워크 생성 작업을 [!DNL Adobe Launch]로 넘기면서 사용자 인터페이스 대화 상자가 간단해졌습니다. [Adobe Analytics 통합](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/sites/integrations/integrating-adobe-analytics.html) 및 [Adobe Target 통합](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/sites/integrations/integrating-adobe-target.html)을 참조하십시오.

* 이제 구성이 Experience Manager 저장소의 `/etc/cloudsettings`가 아닌 `/conf`에 저장됩니다.

## as a Cloud Service [!DNL Adobe Experience Manager Assets] {#assets}

### [!DNL Assets]의 새로운 기능 {#what-is-new-assets}

* [!DNL Asset Compute Service]는 자산을 처리하는 확장 가능한 서비스입니다. 관리자는 [!DNL Asset Compute Service]을(를) 사용하여 만든 사용자 지정 응용 프로그램을 호출하도록 [!DNL Experience Manager]을(를) 구성할 수 있습니다. 개발자는 이 서비스를 사용하여 복잡한 사용 사례에 맞는 전문 사용자 정의 애플리케이션을 만들 수 있습니다. 이 웹 서비스는 다양한 파일 유형에 대한 썸네일 생성, Adobe 파일 형식의 고품질 이미지 렌더링, 비디오 인코딩(미래), 메타데이터 추출, 색인을 생성하기 위한 사전 설정으로 전체 텍스트 추출, 사용 가능한 모든 [!DNL Sensei] 서비스를 통한 자산 실행 등의 작업을 수행할 수 있습니다. [자산 마이크로서비스 및 처리 프로필 사용](/help/assets/asset-microservices-configure-and-use.md)을 참조하세요.

* [!DNL Experience Manager] as a Cloud Service에서 [!DNL Dynamic Media]의 초기 구성이 더욱 강력하게 개선되었습니다. 이제 관리자에게 프로세스 진행 상황을 제공합니다.

* 자산 마이크로서비스를 사용하고 일괄 게시 벡엔드를 향상하여 자산 게시를 전체 자산 처리 파이프라인에 필수 요소로 통합함으로서 [!DNL Dynamic Media]의 자산 게시가 더 단순화되고 더 강력해졌습니다.

* 클라우드 서비스 배포와 호환되지 않는 워크플로우 단계에는 이제 [!UICONTROL 워크플로우 모델] 편집기에서 경고가 표시됩니다. 또한 Cloud Service 환경에서 기존 워크플로우를 실행할 때 호환되지 않는 워크플로우 단계를 건너뜁니다.

* 고객이 만든 워크플로 모델 중 [!DNL Cloud Manager]의 환경과 연결된 Git 프로젝트의 `/conf/global`에 배포되는 모델은 `/var`에 자동으로 배포되어 [!DNL Experience Manager]에서 사용할 수 있습니다. 고객이 변경한 `/libs`의 제품 워크플로우 모델은 자동으로 `/var`에 배포되지 않습니다.

### 수정된 버그 {#assets-bugs-fixed}

* 에셋 이동 마법사가 컬렉션에 포함된 에셋에 대해 예상대로 로드되지 않습니다. (CQ-4296756)
* `dam:size` 및 `dam:sha1`의 값이 XMP 원본에 쓰지 않습니다. (CQ-4237355)
* 자산을 일괄적으로 게시 취소할 때 [!DNL Brand Portal]에서 요청 URI가 너무 길다는 오류가 발생합니다. (CQ-4299474)

## Adobe Experience Manager Commerce as a Cloud Service {#cloud-services-commerce}

### 새로운 기능 {#what-is-new-commerce}

이제 Cloud Service에서 AEM Commerce을 사용할 수 있습니다.

자세한 내용은 [AEM Commerce as a Cloud Service 시작하기](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/commerce/getting-started.html)를 참조하십시오.

## 핵심 구성 요소 {#core-components}

### 새로운 기능 {#what-is-new-core-components}

[AEM 코어 구성 요소](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=ko-KR)의 릴리스 2.11.0은 이제 다음을 포함하여 AEM Sites의 일부로 사용할 수 있습니다.

* 새로운 [PDF 뷰어 구성 요소](https://www.aemcomponents.dev/content/core-components-examples/library/core-content/pdf-viewer.html) 소개

* 이제 코어 구성 요소에 대한 AMP(Accelerated Mobile Page) 지원을 사용할 수 있습니다. Google 모바일 검색 결과에서 사이트 방문 시 즉시 페이지를 전환하여 더 빠른 고객 경험을 제공하고 사용자 참여도와 SEO를 향상합니다.
자세한 내용은 [핵심 구성 요소에 대한 AMP 지원](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/amp.html)을 참조하십시오.

* [Adobe 클라이언트 데이터 레이어](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/data-layer/overview.html) 버전 1.0.2와의 호환성.

* 버그 수정 및 코드 품질 개선

## Cloud Manager {#cloud-manager}

### 릴리스 날짜 {#release-date-cm}

[!UICONTROL Cloud Manager] 버전 2020.7.0의 릴리스 날짜는 2020년 7월 9일입니다.

### 새로운 기능 {#what-is-new-cloud-manager}

* 환경 페이지가 다시 디자인되었습니다.

* 최대 절전 모드인 환경에서 이제 최대 절전 모드일 경우 Cloud Manager에서 개별 상태를 볼 수 있습니다.

* 환경당 환경 변수의 수가 200개로 증가했습니다.

* 이제 Cloud Manager 파이프라인이 고객 설정 변수 및 암호를 지원합니다.

  자세한 내용은 파이프라인 변수를 참조하십시오.

* 이제 인증 바인딩된 비공개 Maven 저장소가 지원됩니다.

* 이제 Cloud Manager 빌드 컨테이너가 Java 8과 Java 11을 모두 지원합니다.
자세한 내용은 Java 11 지원 사용을 참조하십시오.

### 버그 수정 {#bug-fixes-cm}

* 환경이 완전히 만들어지기 전에 Cloud Manager에서 개발자 콘솔로의 링크가 잘못 활성화되었습니다.

* Cloud Manager에서 직접 개발자 콘솔로 연결되는 링크에는 샌드박스 프로그램 환경의 최대 절전 모드 해제/최대 절전 모드 해제 옵션이 표시되지 않습니다.

* 비프로덕션 파이프라인 편집 페이지의 **취소** 및 **저장** 옵션이 항상 표시되는 것은 아닙니다.

* 코드 품질 프로세스의 일부 오류로 인해 로그 파일이 올바로 생성되지 않을 수 있습니다.

* 프로그램을 만들 때 제안된 이름은 기존 프로그램 이름의 복제본을 반환하는 경우가 있습니다.

* 일부 큰 파이프라인 단계 로그를 사용자 인터페이스를 통해 일관되게 다운로드할 수 없습니다.

* 환경 이름의 유효성 검사에 오류가 발생했습니다.

* 환경 페이지는 존재하지 않을 때 게시 및 발송자 세그먼트를 표시하는 경우가 있습니다.

### 알려진 문제 {#known-issues}

* 코드 검사 계산 방식의 변경으로 인해 Jacoco 플러그인의 *최소* 버전은 이제 0.7.5.201505241946(2015년 5월 릴리스)입니다. 이전 버전을 명시적으로 참조하는 고객은 코드 품질 프로세스에서 오류 메시지를 받게 됩니다.

## Adobe Experience Manager as a Cloud Service Foundation {#cloud-foundation}

### 새로운 기능 {#what-is-new-foundations}

* [로그를 Splunk 계정에 전달](/help/implementing/developing/introduction/logging.md#splunk-logs)할 수 있으며, 이를 통해 조직에서 해당 Splunk 투자를 사용할 수 있습니다.

* [정적 전용 송신 IP 주소](/help/implementing/developing/introduction/development-guidelines.md#dedicated-egress-ip-address)를 Java 코드로 프로그래밍된 아웃바운드 트래픽에 할당할 수 있으며 이는 일부 통합에 유용합니다.

* AEM Analytics 클라우드 서비스 UI를 클래식 UI에서 새 AEM UI로 포팅했습니다. 또한 다른 AEM 클라우드 서비스와 맞추기 위해 AEM 저장소의 Analytics 클라우드 서비스 위치를 `/etc`에서 `/conf`로 이동했습니다.

* AEM Target 클라우드 서비스 UI를 클래식 UI에서 새 AEM UI로 포팅했습니다. 다른 AEM 클라우드 서비스와 맞추기 위해 AEM 저장소의 Target 클라우드 서비스 위치도 `/etc`에서 `/conf`로 이동했습니다.

## 클라우드 준비 분석기 {#cloud-readiness-analyzer}

이 섹션을 통해 Cloud Readiness Analyzer 릴리스 버전 1.0.2에 대한 새로운 기능 및 업데이트를 알아보십시오.

### 버그 수정 {#cra-bug-fixes}

* AEM(Adobe Experience Manager) 6.1에서 이전 버전의 CRA를 실행할 수 없습니다. 관리자 그룹의 사용자를 허용하는 명시적 지원이 추가되었습니다.

  자세한 내용은 [AEM 6.1에 CRA 설치](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/cloud-readiness-analyzer/using-cloud-readiness-analyzer.html#installing-on-aem61)를 참조하십시오.

* 요약 보고서에 표시되는 만료 타임스탬프가 잘못되었습니다.

* CRA가 중복된 사용자 지정 구성 요소를 감지하고 있습니다.

* AEM 6.1에서 전체 검사를 완료하기 전에 컨텐츠 검사를 종료했습니다. 전체 검사가 완료될 때까지 검사자가 건너뛸 수 있도록 예외 처리가 추가되었습니다.
