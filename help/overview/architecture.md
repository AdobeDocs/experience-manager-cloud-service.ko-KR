---
title: Adobe Experience Manager as a Cloud Service 아키텍처 소개
description: Adobe Experience Manager as a Cloud Service 아키텍처 소개.
exl-id: 3fe856b7-a0fc-48fd-9c03-d64c31a51c5d
source-git-commit: 25af074bcb32e47732b27bacf10c8d3435299440
workflow-type: tm+mt
source-wordcount: '2713'
ht-degree: 100%

---

# Adobe Experience Manager as a Cloud Service 아키텍처 소개 {#an-introduction-to-the-architecture-adobe-experience-manager-as-a-cloud-service}

>[!CONTEXTUALHELP]
>id="intro_aem_cloudservice_architecture"
>title="AEM as a Cloud Service 아키텍처 소개"
>abstract="이 탭에서는 AEM as a Cloud Service의 새 아키텍처를 확인하고 변경 내용을 알아볼 수 있습니다. AEM에서 다양한 수의 이미지를 가진 동적 아키텍처를 구축했으므로 클라우드 아키텍처를 이해하는 시간을 가져 보십시오."
>additional-url="https://video.tv.adobe.com/v/330542/" text="아키텍처 개요"

Adobe Experience Manager(AEM) as a Cloud Service는 영향력이 큰 경험을 만들고 관리할 수 있는 구성 가능한 서비스 세트를 제공합니다.

이 페이지에서는 AEM as a Cloud Service에 대한 논리적 아키텍처, 서비스 아키텍처, 시스템 아키텍처 및 개발 아키텍처를 소개합니다.

## 논리적 아키텍처 {#logical-architecture}

AEM as a Cloud Service는 AEM Sites, AEM Assets 및 AEM Forms와 같은 고급 솔루션으로 구성됩니다. 이러한 서비스는 개별적으로 라이선스가 부여되지만 공동으로 사용할 수 있습니다. 각 솔루션은 해당 사용 사례에 따라 AEM as a Cloud Service에서 제공하는 구성 가능한 서비스 조합을 사용합니다.

### 프로그램 {#programs}

AEM 애플리케이션은 사용자가 라이선스 권한에 따라 Cloud Manager 애플리케이션에서 만드는 [프로그램](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/program-types.md)의 형태로 구체화됩니다. 이러한 프로그램을 사용하면 특정 프로젝트의 컨텍스트에서 연결된 AEM 애플리케이션의 이름을 지정하고 구성하는 방법과 권한을 할당하는 방법을 완벽하게 제어할 수 있습니다.

고객으로서 귀하는 일반적으로 Adobe에서 **테넌트**(*IMS 조직*(Identity Management System)이라고도 함)로 식별됩니다. 테넌트는 필요한 만큼 많은 프로그램을 보유하고 라이선스를 취득할 수 있습니다. 예를 들어 AEM Assets에 대한 중앙 프로그램을 보는 것은 매우 일반적인 반면, AEM Sites는 여러 온라인 경험에 해당하는 여러 프로그램에서 사용될 수 있습니다.

>[!NOTE]
>
>AEM Edge Delivery Services는 Cloud Manager에서 최상위 솔루션으로 노출되는 동시에, 라이선스 관점에서 보면 다른 주요 솔루션의 일부이기도 합니다. 예를 들어 Edge Delivery Services가 포함된 AEM Sites가 있습니다.

프로그램은 고급 솔루션의 조합으로 구성할 수 있으며 각 솔루션은 일대다 추가 기능을 지원할 수 있습니다. 예를 들어 AEM Sites용 Commerce 또는 Screens, AEM Assets용 Dynamic Media 또는 Brand Portal이 있습니다.

![AEM as a Cloud Service - 프로그램](assets/architecture-aem-edge-programs.png "AEM as a Cloud Service - 배포 아키텍처")

### 환경 {#environments}

AEM Sites, AEM Assets 또는 AEM Forms 솔루션을 사용하여 프로그램을 만들면 연결된 AEM 인스턴스가 이 프로그램에서 AEM 환경의 형태로 표시됩니다.

AEM as a Cloud Service에 사용할 수 있는 [환경](/help/implementing/cloud-manager/manage-environments.md)에는 다음 네 가지 유형이 있습니다.

* 프로덕션 환경:

   * 프로덕션 환경은 비즈니스 실무자를 위한 애플리케이션을 호스팅하고 라이브 경험을 실행합니다.

* 스테이징 환경:

   * 스테이징 환경은 일반적으로 1:1 관계에서 프로덕션 환경에 연결됩니다.
   * 스테이징 환경은 주로 애플리케이션 변경 사항이 프로덕션 환경에 푸시되기 전에 자동화된 테스트용으로 설계됩니다.
      * 이는 유지 관리 업데이트의 일부로 Adobe에서 시작하거나 코드 배포에 의해 시작되는 변경 사항과는 별개입니다.
      * 코드 배포의 경우 수동 테스트를 수행할 수도 있습니다.
   * 스테이징 환경의 콘텐츠는 일반적으로 셀프서비스 콘텐츠 복사 기능을 사용하여 프로덕션 콘텐츠와 동기화된 상태로 유지됩니다.
   * 스테이징 환경에서 성능 및 보안 테스트를 수행합니다. 이는 프로덕션 크기와 동일합니다.
* 개발 환경:
   * 개발 환경은 개발자가 스테이징 및 프로덕션 환경과 동일한 런타임 조건으로 AEM 애플리케이션을 구현하고 테스트할 수 있도록 해 줍니다.
   * 변경 사항은 프로덕션 배포 파이프라인과 동일한 코드 품질 및 보안 게이트를 허용하는 배포 파이프라인을 거칩니다.
   * 개발 환경은 스테이징 및 프로덕션과 크기가 동일하지 않으며 성능 및 보안 테스트를 수행하는 데 사용해서는 안 됩니다.
* 신속한 개발 환경(RDE):
   * RDE 환경에서는 일반 개발 환경에서 볼 수 있는 공식적인 배포 파이프라인을 거치지 않고도 새 코드나 기존 코드를 RDE 인스턴스에 배포할 때 신속한 개발 반복이 가능합니다.

### Edge Delivery Services {#logical-architecture-edge-delivery-services}

AEM 프로그램은 [Edge Delivery Services](/help/edge/overview.md)를 사용하여 구성할 수도 있습니다.

일단 구성되면 AEM은 Edge Delivery Services로 경험을 구축하는 데 사용되는 GitHub 코드 저장소를 참조할 수 있습니다. 결과적으로 연결된 경험에 대해 새로운 구성 옵션을 사용할 수 있게 됩니다. 여기에는 Adobe 관리 CDN 설정, 라이선스 지표 또는 SLA 보고서 액세스가 포함됩니다.

## 서비스 아키텍처 {#service-architecture}

AEM as a Cloud Service의 상위 수준 구성 가능 서비스 목록은 콘텐츠 관리와 경험 게재라는 두 가지 세그먼트로 표시될 수 있습니다.

![AEM as a Cloud Service 개요 - Edge Delivery Services 포함](assets/architecture-aem-edge.png "AEM as a Cloud Service 개요 - Edge Delivery Services 포함")

콘텐츠 관리에는 콘텐츠 작성을 위한 두 가지 주요 서비스 세트가 있으며, 둘 다 *콘텐츠 소스*&#x200B;로 표시됩니다.

* AEM 작성 계층:
웹 콘텐츠 관리를 위한 웹 기반 인터페이스(연결된 API 포함)를 제공합니다. 이는 다음과 같은 두 가지 접근 방식 모두에 적용됩니다.
   * Headful - 페이지 편집기 및 Universal Editor를 통해
   * Headless - 콘텐츠 조각 편집기를 통해
* 문서 기반 작성 계층:
다음과 같은 표준 애플리케이션을 사용하여 콘텐츠를 작성할 수 있습니다.
   * Microsoft Word 및 Excel - SharePoint를 통해
   * Google Docs 및 Sheets - Google Drive를 통해

경험 게재의 경우 AEM Sites 또는 AEM Forms를 사용할 때, 상호 배타적이지 않고 공유 Adobe 관리 CDN(Content Delivery Network)에서 서로 다른 출처로 작동하는 두 가지 기본 서비스 세트도 있습니다.

* AEM 게시 계층:
   * 표준 AEM 게시자 및 Dispatcher 팜을 실행하여 게시된 콘텐츠와 결합된 웹 페이지 및 API 콘텐츠(예: GraphQL)의 동적 렌더링을 허용합니다.
   * 주로 서버측 애플리케이션 논리를 기반으로 합니다.
* Edge Delivery 게시 계층:
   * AEM 작성 계층 또는 문서 기반 작성 계층과 같은 다양한 콘텐츠 소스의 웹 페이지 및 API 콘텐츠를 동적으로 렌더링할 수 있습니다.
   * 클라이언트측 애플리케이션 논리를 기반으로 하며 최대 성능을 위해 설계됩니다.

다음과 같은 주요 인접 서비스도 있습니다.

* Edge Delivery 자산 계층:
   * AEM Assets에서 승인되고 게시된 미디어 항목을 게재할 수 있습니다. 예를 들어 이미지, 비디오 등이 있습니다.
   * 미디어 항목은 일반적으로 AEM 게시 계층, Edge Delivery 게시 계층 또는 AEM Assets와 통합된 다른 Adobe Experience Cloud 애플리케이션에서 실행되는 경험에서 참조됩니다.
* AEM 미리보기 계층 및 Edge Delivery Services 미리보기 계층:
   * AEM 게시 계층 또는 Edge Delivery 게시 계층을 사용하여 구축된 경험에도 사용할 수 있습니다.
   * 콘텐츠 작성자는 게시 작업 전에 콘텐츠를 컨텍스트에서 미리 볼 수 있습니다.

>[!NOTE]
>
>기본적으로 자산 전용 프로그램에는 게시 계층이나 미리보기 계층이 없습니다.

다음과 같은 다른 인접 서비스도 있습니다.

* 복제 서비스:
   * 콘텐츠 관리 계층과 경험 게재 계층 사이에 위치합니다.
   * 콘텐츠 작성자가 발행한 *게시* 작업을 처리한 다음 게시된 콘텐츠를 게시 계층(AEM 또는 Edge Delivery)에 제공하는 역할을 담당합니다.

  >[!NOTE]
  >이전 버전 AEM의 복제 프레임워크가 더 이상 콘텐츠 게시에 사용되지 않으므로 복제 서비스는 AEM 6.x 버전과 비교하여 완전히 재설계되었습니다.
  >
  >최신 아키텍처는 클라우드 기반 콘텐츠 대기열을 활용하는 *게시 및 구독* 접근 방식을 기반으로 합니다. AEM 게시 계층은 다양한 수의 게시자가 게시 콘텐츠를 구독할 수 있도록 하며, AEM as a Cloud Service에 대한 정확하고 빠른 자동 크기 조정을 달성하는 데 필수적인 부분입니다.

* 콘텐츠 저장소 서비스:
   * AEM 작성 계층에서 사용됩니다.
   * Apache Oak 기술로 구현된 JCR 호환 콘텐츠 저장소의 클라우드 기반 인스턴스입니다.
   * 콘텐츠의 지속성은 주로 Blob 기반 클라우드 스토리지를 기반으로 합니다.
* CI/CD 서비스:
   * AEM 환경에 대한 배포 파이프라인 관리를 전담하는 Cloud Manager 기능의 하위 세트를 나타냅니다.
* 테스트 서비스:
   * 다음과 같은 작업을 실행하는 데 사용되는 기본 인프라를 나타냅니다.
      * 기능 테스트
      * UI 테스트: 예를 들어 Selenium 또는 Cypress 스크립트를 기반으로 함
      * 감사 테스트 경험: 예를 들어 Lighthouse 점수

     AEM 환경에 대한 배포 파이프라인의 일부이거나 Edge Delivery 코드 저장소에 대한 GitHub 가져오기 요청의 일부입니다.
* 데이터 서비스:
   * 라이선스 지표(예: 콘텐츠 요청, 스토리지, 사용자) 또는 사용 보고서(예: 업로드, 다운로드 수)와 같은 고객 데이터를 노출하는 일을 담당합니다.
   * 고객 데이터는 API를 통해, 그리고 제품 사용자 인터페이스(예: Cloud Manager) 내에서 노출될 수 있습니다.
* 실제 사용자 지표(RUM) 서비스:
   * 고객 경험(예: 페이지 조회수, 핵심 웹 바이탈 및 전환 이벤트)에서 주요 지표를 수집하고 관련 쿼리(예: 지난 7일 동안 특정 도메인에 대한 상위 페이지 조회수)에 응답하는 일을 담당합니다.
* 자산 컴퓨팅 서비스:
   * 업로드된 이미지, 비디오, 문서(예: PDF 및 Adobe Photoshop 파일) 처리를 담당합니다. 처리에서는 Adobe Sensei를 사용하여 이미지 및 비디오 메타데이터(예: 설명 태그 또는 주 색상 톤)를 추출한 다음 Adobe Photoshop 및 Adobe Lightroom API와 같은 API에 액세스하여 렌디션(예: 다양한 크기 또는 형식)을 생성할 수 있습니다.
* Identity Management Service(IMS):
   * 특정 Adobe Experience Cloud 애플리케이션(예: Cloud Manager 또는 AEM 작성 계층)에 대한 사용자 및 사용자 그룹을 관리하고 인증하는 역할을 담당하는 중앙 위치입니다.
   * Adobe Admin Console을 통해 액세스됩니다.

## 시스템 구조 {#system-architecture}

### AEM 작성, 미리보기 및 게시 계층 {#aem-author-preview-publish-tiers}

AEM 작성 및 게시 계층은 표준 컨테이너 오케스트레이션 서비스에서 운영되는 Docker 컨테이너 세트로 구현됩니다. 결과에 해당하는 컨테이너화된 아키텍처는 실제 활동(콘텐츠 관리용) 및 실제 트래픽(경험 게재용)에 따라 다양한 수의 포드를 갖춘 완전히 동적 시스템을 의미합니다. 이는 트래픽 패턴이 변화할 때 AEM as a Cloud Service가 트래픽 패턴을 수용할 수 있도록 해 줍니다.

AEM 작성 계층은 단일 콘텐츠 저장소를 공유하는 AEM 작성자 포드의 클러스터로 운영됩니다. 유지 관리 작업이 실행 중이거나 배포 프로세스가 진행되는 동안 최소 두 개의 포드로 비즈니스 연속성을 확보합니다.

AEM 게시 계층은 각각 게시된 콘텐츠의 자체 콘텐츠 저장소가 있는 AEM 게시 인스턴스의 팜으로 운영됩니다. 각 게시자는 콘텐츠의 구체화된 보기를 위해 AEM Dispatcher 모듈이 장착된 단일 Apache 인스턴스에 연결되어 Adobe 관리 CDN의 원본 역할을 합니다. 최소 두 개의 포드를 사용하면 비즈니스 연속성 또한 확보할 수 있지만, 트래픽이 많은 기간에는 이 숫자가 흔히 늘어납니다.

AEM 미리보기 계층은 단일 AEM 노드로 구성되어 있습니다. 게시 계층에 게시하기 전 콘텐츠의 품질 보증에 사용됩니다. 특히 배포 중에 가끔 가동 중지 시간이 미리보기 계층에서 발생할 수 있습니다.

### Edge Delivery Services {#system-architecture-edge-delivery-services}

Edge Delivery Services는 가장 효율적인 방식으로 페이지를 어셈블하기 위해 CDN 및 서버리스 인프라를 기반으로 운영됩니다. 리소스가 요청되면 서버리스 인프라는 게시된 콘텐츠를 유의미한 HTML로 변환하고 CDN의 원본 역할을 합니다.

유의미한 HTML로 전환하는 작업은 AEM 작성 계층 또는 문서 기반 작성 환경에서 제공되는 게시된 콘텐츠에서 발생합니다.

다음 다이어그램은 Microsoft Word(문서 기반 작성)에서 Sites 콘텐츠를 편집하고 Edge Delivery에 게시하는 방법을 보여 줍니다. 또한 다양한 편집기를 사용하는 기존 AEM 게시 방법을 보여 줍니다.

![AEM Sites as a Cloud Service - Edge Delivery Services 포함](assets/architecture-aem-edge-author-publish.png "AEM Sites as a Cloud Service - Edge Delivery Services 포함")

Edge Delivery Services는 Adobe Experience Manager의 일부이므로 Edge Delivery, AEM Sites 밍 AEM Assets는 동일한 도메인에서 함께 존재할 수 있습니다. 이는 대규모 웹 사이트의 일반적인 사용 사례입니다. 예를 들어 고객은 트래픽이 많은 특정 페이지를 Edge Delivery Services로 마이그레이션하고 다른 모든 페이지는 AEM 게시 계층에 남겨 두고자 할 수 있습니다.

## 개발 아키텍처 {#development-architecture}

### 코드 저장소 {#code-repositories}

AEM 프로젝트의 코드 및 구성은 변경 사항이 있을 때 배포 파이프라인이 실행되는 코드 저장소에 저장됩니다. 코드 저장소에는 다음과 같이 다양한 유형이 있습니다.

* AEM 전체 스택:
   * AEM 작성 및 게시 계층에 대한 서버측 Java 코드 및 OSGI 구성을 저장합니다.
* AEM 프론트엔드:
   * AEM 작성 및 게시 계층에 대한 클라이언트측 JS, CSS 및 HTML 코드를 저장합니다.
clientlibs에 대한 자세한 내용은 [AEM as a Cloud Service에서 클라이언트측 라이브러리 사용](/help/implementing/developing/introduction/clientlibs.md)을 참조하십시오.
* AEM 웹 계층:
   * AEM 게시 계층에 대한 Dispatcher 구성 파일을 저장합니다.
* AEM 구성:
   * AEM 게시 계층 및 Edge Delivery Services 게시 계층에 대한 다양한 구성 옵션(예: CDN 설정 또는 유지 관리 작업 설정)을 저장할 수 있습니다.
* AEM Edge Delivery:
   * Edge Delivery Services로 구축된 사이트의 클라이언트측 JS, CSS 및 HTML 코드를 저장하는 용도입니다.

### 배포 파이프라인 {#deployment-pipelines}

개발자 및 관리자는 Cloud Manager를 통해 제공되는 CI/CD(Continuous Integration/Continuous Delivery) 서비스를 사용하여 AEM as a Cloud Service 애플리케이션을 관리합니다. Cloud Manager는 또한 모니터링, 유지 관리, 문제 해결(예: 로그 파일 액세스) 및 라이선스와 관련된 모든 사항을 표시합니다.

![AEM as a Cloud Service - 배포 아키텍처](assets/architecture-aem-edge-deployment-pipelines.png "AEM as a Cloud Service - 배포 아키텍처")

Cloud Manager는 AEM as a Cloud Service 인스턴스에 대한 모든 업데이트를 관리합니다. 이는 작성, 미리보기 및 게시 계층에 고객 애플리케이션을 구축하고, 테스트하고, 배포할 수 있는 유일한 방법이므로 필수적인 작업입니다. 이러한 업데이트는 새로운 버전의 AEM Cloud Service가 준비되었을 때 Adobe가 또는 새로운 버전의 애플리케이션이 준비되었을 때 고객이 직접 트리거할 수 있습니다.

이는 프로그램 내의 각 환경과 결합된 배포 파이프라인에 의해 구현됩니다. Cloud Manager 파이프라인이 실행되면 작성 계층과 게시 계층 모두에 대해 고객 애플리케이션의 새 버전이 만들어집니다. 이 작업은 최신 고객 패키지를 최신 기준 Adobe 이미지와 결합함으로써 수행됩니다.

고객이 코드를 변경하거나 Adobe가 새로운 유지 관리 릴리스를 배포할 때 배포 파이프라인이 트리거됩니다.

두 경우 모두 동일한 자동화된 테스트 세트가 실행됩니다. 이는 다음과 같은 테스트로 구성됩니다.

* 제품 무결성을 보장하기 위해 Adobe에서 기여한 테스트
* 고객이 기여한 테스트
   * 기능 테스트: AEM 작성 또는 게시 계층에 대한 http 요청을 통한 테스트
   * UI 테스트: Selenium 또는 Cypress 기술 기반

이와 같은 자동화된 테스트는 스테이징 환경에서 실행됩니다. 따라서 스테이징 환경 콘텐츠를 프로덕션 인스턴스의 콘텐츠와 최대한 가깝게 유지하는 것이 중요합니다.

모든 테스트가 성공적으로 통과되면 새 코드가 프로덕션 환경에 배포됩니다.

### 롤링 업데이트 {#rolling-updates}

Cloud Manager는 롤링 업데이트 패턴을 사용해 모든 서비스 노드를 업데이트하여 최신 버전의 AEM 애플리케이션으로 전환하는 작업을 완전히 자동화합니다. 따라서 작성 또는 게시 서비스에 대한 **가동 중지 시간**&#x200B;이 발생하지 않습니다.

## AEM 6.x 이후의 주요 혁신 사항 {#major-innovations-since-aem-6x}

AEM as a Cloud Service를 위한 최신 아키텍처에서는 이전 세대(AEM 6.x 및 이전)와 비교하여 몇 가지 근본적인 변경 사항과 획기적인 기능을 제공합니다.

* 모든 파일은 클라우드 데이터 저장소에서 바로 업로드되고 제공됩니다. 연관된 비트 스트림은 AEM 작성 및 게시 서비스의 JVM을 거치지 않습니다. 그 결과, AEM 작성 및 게시 서비스의 노드는 크기가 더 작아질 수 있고 따라서 빠른 자동 크기 조절에 대한 기대를 더 잘 충족합니다. 비즈니스 전문가의 경우 이에 따라 이미지, 비디오 및 다른 작업을 더 빨리 업로드하고 다운로드할 수 있습니다.

* 이제 콘텐츠 게시로 구성된 모든 작업에 구독 패턴을 따르는 파이프라인이 포함됩니다. 게시된 콘텐츠는 파이프라인의 다양한 큐에 푸시되어 게시 서비스의 모든 노드가 이 콘텐츠를 구독합니다. 따라서 작성 계층은 게시 서비스의 노드 수를 인식할 필요가 없으며, 따라서 게시 계층의 자동 크기 조절 기능이 빨라집니다.

* 아키텍처는 애플리케이션 코드와 구성에서 애플리케이션 콘텐츠를 완전히 분리합니다. 모든 코드와 구성은 사실상 변경할 수 없으며 작성 및 게시 서비스의 다양한 노드를 만드는 데 사용되는 기준 이미지에 결합됩니다. 그 결과, 각 노드는 같아지고, 코드 및 구성의 변경은 Cloud Manager 파이프라인을 실행해야만 전역적으로 수행할 수 있습니다.

* 아키텍처에는 서버리스 기술, 특히 Adobe I/O 런타임을 기반으로 구축된 여러 마이크로 서비스가 포함되어 있습니다.

## 추가 정보 {#further-information}

* 프로그램 설정
   * [온보딩 여정](/help/journey-onboarding/overview.md)
   * [프로그램 및 프로그램 유형](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/program-types.md)
* 개발 아키텍처
   * [Cloud Manager 저장소](/help/implementing/cloud-manager/managing-code/cloud-manager-repositories.md)
   * [CI/CD 파이프라인](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md)
   * [코드 품질 테스트](/help/implementing/cloud-manager/code-quality-testing.md)
* Edge Delivery Services:
   * [AEM as a Cloud Service 개요 - Edge Delivery Services 포함](/help/edge/overview.md)
   * [Edge Delivery Services 사용](/help/edge/using.md)
   * [Edge Delivery Services를 사용하여 AEM as a Cloud Service의 기본 아키텍처와 중요한 부분을 살펴보기](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/introduction/architecture.html)
