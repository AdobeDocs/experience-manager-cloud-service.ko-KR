---
title: AEM 커넥터 구현
description: AEM 커넥터 구현
translation-type: tm+mt
source-git-commit: 69756d6831678151b0e8eb73db81113d49f17447
workflow-type: tm+mt
source-wordcount: '960'
ht-degree: 2%

---


AEM 커넥터 구현
=============================

아래에 제공된 정보는 [AEM 커넥터](https://www.adobe.io/apis/experiencecloud/aem/aemconnectors.html) 구축을 위한 유용한 참조이며 커넥터 [제출](submit.md) 및 [유지 관리에 대한 지침과 함께](maintain.md) 읽어야합니다.

AEM용 개발자 라이선스는 [Adobe Exchange 프로그램을 통해 얻을 수 있습니다](https://partners.adobe.com/exchangeprogram/experiencecloud).

공통 통합 패턴
---------------------------

AEM은 첨단 웹 경험 관리 솔루션으로 다양한 통합 영역을 제공합니다. 일반적인 통합 패턴은 다음과 같습니다.

* 외부 시스템에서 AEM으로 데이터 가져오기 예를 들어 AEM 기반 웹 사이트를 방문하는 더 많은 사용자가 사용할 수 있도록 CRM에서 연락처 정보를 내보냅니다.  구현은 Sling의 [예약된 작업](https://sling.apache.org/documentation/bundles/apache-sling-eventing-and-job-handling.html#scheduled-jobs)을 사용해야 하며, 이 작업은 컨테이너가 내려가도 실행됩니다. 작업은 여러 번 실행될 가능성이 있다고 가정하도록 코드를 설계해야 합니다.
* AEM에서 외부 시스템으로 데이터 내보내기 예를 들어, 뉴스레터 구독 설정이 AEM 기반 웹 사이트에서 CRM에 제출되었습니다.
* AEM에서 에셋을 검색하는 중입니다. 예를 들어 AEM Assets에 저장된 자산을 참조하는 외부 CMS(Content Management System)가 있습니다. 또 다른 예로 AEM Assets의 이미지에 PIM 시스템을 연결합니다.
* AEM 인프라에 자산 저장 예를 들어, 승인된 자산을 AEM Assets에 저장하는 MRM(마케팅 리소스 관리) 시스템입니다.
* 사용자 지정 UI 구성 요소 구성 및 렌더링. 예를 들어, 작성자가 비디오 구성 요소를 드래그 앤 드롭하고 특정 비디오를 라이브 사이트에서 재생하도록 구성할 수 있습니다.
* 파트너 서비스를 통해 자산 사용 예를 들어 페이지가 게시될 때 자산을 비디오 플랫폼으로 보냅니다.
* AEM 관리 콘솔에서 사이트, 페이지 또는 자산 분석 예를 들어, 기존 또는 게시 취소된 페이지에 대해 SEO 추천을 만듭니다.
* 외부 서비스에서 유지 관리하는 사용자 데이터에 대한 페이지 수준 액세스. 예를 들어 인구 통계 정보를 활용하여 사이트 경험을 개인화합니다. 컨텍스트 데이터를 저장, 조작 및 표시하기 위한 프레임워크인 ContextHub에 대해 알아보십시오.
* 사이트 복사 또는 자산 메타데이터 번역 번역 커넥터의 기본 구현인 AEM Translation Framework를 사용하는 샘플 코드는 [AEM Translation Framework Bootstrap 커넥터를](https://github.com/Adobe-Marketing-Cloud/aem-translation-framework-bootstrap-connector) 참조하십시오.


유용한 설명서
--------------------

Cloud Service [문서로서 Experience Manager은 AEM에서](../overview/introduction.md) 개발하는 데 대한 중요한 통찰력을 제공합니다. 다음은 AEM 커넥터를 구현할 때 유용한 몇 가지 특정 기술 주제 및 참조입니다.

* Adobe 컨설팅 서비스(ACS) [AEM](http://adobe-consulting-services.github.io/acs-aem-samples/) AEM 개발자를 교육하는 데 도움이 되는 주석 달기 코드에 대한 샘플
* 이 문서의 공통 통합 패턴 섹션에 있는 다양한 문서 링크

커뮤니티 리소스
--------------------

위의 정적 설명서 외에도 Adobe과 AEM 커뮤니티는 커넥터를 시장에 출시하는 데 도움이 되는 리소스를 제공합니다.

* Adobe 커뮤니티의 [AEM](http://help-forums.adobe.com/content/adobeforums/kr/experience-manager-forum/adobe-experience-manager.html) 포럼은 동료가 질문과 답변을 제공하는 활성 사이트입니다
* 특정 파트너 수준에서 추가 Adobe 기술 리소스를 사용할 수 있습니다. [Adobe Exchange 프로그램에 대한 자세한 내용을 살펴보십시오](https://partners.adobe.com/exchangeprogram/experiencecloud).
* 조직에서 구현 지원을 원하는 경우 Adobe [전문 서비스](http://www.adobe.com/marketing-cloud/service-support/professional-consulting-training.html) 팀을 고려하거나 [솔루션 파트너](https://solutionpartners.adobe.com/home/partnerFinder.html) 파인더를 참조하여 전 세계 Adobe 파트너 목록을 확인하십시오

패키지 구조 규칙
-----------------------

롤링 배포를 지원하기 위해 Cloud Service 패키지로 사용되는 AEM은 &quot;불변량&quot; 컨텐츠와 &quot;mutable&quot; 컨텐츠 간에 엄격하게 구분됩니다. 패키지는 다음과 같은 패키지 간에 깔끔하게 분리되어야 합니다.

* `/apps`
* `/content` 및 `/conf`

커넥터는 [이 문서에 설명된 이러한 패키징 지침을 따라야 합니다](/help/implementing/developing/introduction/aem-project-content-package-structure.md). 기존 커넥터를 다시 팩토링하여 일치시켜야 합니다.

또한 Adobe만이 코드를 작성하고 고객 및 파트너가 서명하는 `/libs`등 `/apps`을 사용해야 합니다.

또한 기존 커넥터를 리팩토링하여 한 때 다른 최상위 폴더 `/etc` 로 배치했을 수 있는 구성을 이동시켜야 할 수도 있습니다(예: `/conf`). 이 내용은 [AEM 설명서에 설명되어 있습니다](https://helpx.adobe.com/experience-manager/6-5/sites/deploying/using/repository-restructuring.html).

커넥터를 여러 개 보유한 고객을 위해 대부분의 커넥터 코드 `/apps/connectors/<vendor>` 를 깔끔한 저장소 구조에 배치하는 것이 좋습니다.

Cloud Services 구성
-----------------------------

커넥터 구현의 한 측면에서는 커넥터의 구성을 지원하는 코드가 있습니다. 이 코드를 사용하면 커넥터 이름이 있는 카드가 도구 > 작업 > Cloud Services 아래에 나타납니다. 클릭하면 고객이 커넥터 구성을 포함할 상위 폴더를 선택하는 [구성 브라우저가](/help/implementing/developing/introduction/configurations.md#using-configuration-browser) 표시됩니다. 커넥터의 코드는 구성해야 하는 모든 속성이 있는 양식으로 생성되어 이 값을 구성 폴더 아래에 저장합니다 `/conf`. 나중에 사이트 속성 탭 또는 자산 속성 탭에서 이 폴더를 선택할 수 있습니다.


컨텍스트 인식 구성
-----------------------------

[컨텍스트 인식 구성을](https://sling.apache.org/documentation/bundles/context-aware-configuration/context-aware-configuration.html) 사용하면 하위 폴더 `/libs`, `/apps`및 하위 폴더를 비롯한 다양한 폴더 `/conf` 에서 레이어 구성을 만들 수 `/conf`있습니다. 또한 상속을 지원하므로 고객은 각 마이크로 사이트에 대해 특정 변경 작업을 수행하는 동안 글로벌 구성을 구성할 수 있습니다. Cloud Services 구성에 대해 이 기능을 활용할 수 있으므로 커넥터 코드는 특정 구성 노드를 참조하는 대신 컨텍스트 인식 구성 API를 사용하여 구성을 참조해야 합니다.

커넥터에서 수정된 구성을 사용하는 경우 커넥터를 설계하여 향후 커넥터로 제공된 기본 구성에 대한 업데이트를 고객 구성과 포함/병합합니다. 고객 경고 및 동의 없이 사용자 지정된 컨텐츠 또는 구성을 변경(고객이 변경한 상태)하면 해당 커넥터로 인해 중단되거나 예기치 않은 동작을 만들 수 있습니다.

코딩 우수 사례
----------------------

AEM은 클라우드 기반 솔루션이므로 커넥터의 코드 전략에 영향을 줄 수 있는 몇 가지 지침이 있습니다. 자세한 내용은 [AEM을 Cloud Service 개발 가이드라인으로](/help/implementing/developing/introduction/development-guidelines.md) 참조하십시오.

AEM 커넥터 테스트
-------------------------

로컬 환경 개발 기술을 사용하여 새 커넥터를 만들거나 기존 커넥터를 수정해야 합니다. 파트너 팀은 ISV 파트너에게 AEM Connector를 바닐라 애플리케이션에 배포하여 제대로 작동하는지 확인할 수 있는 샌드박스 환경을 제공합니다.
