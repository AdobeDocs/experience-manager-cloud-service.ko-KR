---
title: AEM Connector 구현
description: AEM Connector 구현
translation-type: tm+mt
source-git-commit: 629de3a9f55d2e4c52ef91c9e0bb5d439aebe84f

---


AEM Connector 구현
=============================

아래에 제공된 참조는 AEM [커넥터를](https://www.adobe.io/apis/experiencecloud/aem/aemconnectors.html) 빌드하는 데 유용하며 [커넥터](submit.md) 제출 [및](maintain.md) 유지 관리에대한 지침과 함께 읽어야 합니다.

AEM에 대한 개발자 라이선스는 Adobe Exchange 프로그램을 통해 얻을 수 [있습니다](https://marketing.adobe.com/resources/content/resources/exchange-partner-program.html).

공통 통합 패턴
---------------------------

AEM 파섹 일반적인 통합 패턴은 다음과 같습니다.

* 외부 시스템에서 AEM으로 데이터 가져오기 예를 들어 CRM에서 연락처 정보를 내보내 AEM 기반 웹 사이트를 방문하는 더 많은 사용자가 사용할 수 있도록 합니다.  구현은 Sling의 예약된 [작업을](https://sling.apache.org/documentation/bundles/apache-sling-eventing-and-job-handling.html#scheduled-jobs)사용해야 하며, 이 작업은 컨테이너가 작동 중지되어도 실행됩니다. 작업은 여러 번 트리거될 수 있다고 가정하도록 코드를 디자인해야 합니다.
* AEM에서 외부 시스템으로 데이터 내보내기 예를 들어, AEM 기반 웹 사이트에서 CRM에 제출된 뉴스레터 구독 설정을 예로 들 수 있습니다.
* AEM에서 자산 검색. 예를 들어 AEM 자산에 저장된 자산을 참조하는 외부 CMS(콘텐츠 관리 시스템)가 있습니다. 또는 다른 예로 AEM Assets의 이미지에 대한 PIM 시스템이 연결되어 있습니다.
* AEM 인프라에 자산 저장 예를 들어 AEM 자산에 승인된 자산을 저장하는 MRM(마케팅 리소스 관리) 시스템입니다.
* 사용자 정의 UI 구성 요소 구성 및 렌더링. 예를 들어, 작성자가 비디오 구성 요소를 드래그 앤 드롭하고 라이브 사이트에서 재생할 특정 비디오를 구성할 수 있도록 허용합니다.
* 파트너 서비스를 통해 자산 관리 예를 들어, 페이지가 게시될 때 자산을 비디오 플랫폼으로 보냅니다.
* AEM 관리 콘솔에서 사이트, 페이지 또는 자산 분석 예를 들어 기존 또는 게시 취소된 페이지에 대해 SEO 권장 사항을 만듭니다.
* 외부 서비스에서 유지 관리하는 사용자 데이터에 대한 페이지 수준 액세스 예를 들어 인구 통계 정보를 활용하여 사이트 경험을 개인화합니다. 컨텍스트 데이터를 저장, 조작 및 표시하기 위한 프레임워크인 ContextHub에 대해 알아보십시오.
* 사이트 복사 또는 자산 메타데이터 번역 번역 [커넥터의 기본 구현인](https://github.com/Adobe-Marketing-Cloud/aem-translation-framework-bootstrap-connector) AEM Translation Framework를 사용하는 샘플 코드는 AEM Translation Framework Bootstrap 커넥터를 참조하십시오.


유용한 설명서
--------------------

Adobe Experience Manager as a Cloud Service [설명서는](../overview/introduction.md) AEM에서 개발하는 데 유용한 인사이트를 제공합니다. 다음은 AEM 커넥터를 구현할 때 유용하다고 판단되는 몇 가지 특정 기술 항목 및 참조입니다.

* AEM 개발자를 교육하는 [데 도움이 되는 잘](http://adobe-consulting-services.github.io/acs-aem-samples/) 추가된 코드에 대한 Adobe 컨설팅 서비스(ACS) AEM 샘플
* 이 문서의 공통 통합 패턴 섹션에 있는 다양한 설명서 링크

커뮤니티 리소스
--------------------

위의 정적 설명서 외에도 Adobe 및 AEM 커뮤니티는 커넥터를 시장에 출시하는 데 도움이 되는 리소스를 제공합니다.

* Adobe Community의 [AEM](http://help-forums.adobe.com/content/adobeforums/en/experience-manager-forum/adobe-experience-manager.html) 포럼은 동료가 질문과 답변을 제공하는 활성 사이트입니다
* 특정 파트너 수준에서 추가 Adobe 기술 리소스를 이용할 수 있습니다. Adobe Exchange 프로그램에 대한 자세한 [내용을 살펴보십시오](https://marketing.adobe.com/resources/content/resources/exchange-partner-program.html).
* 조직에서 구현 지원을 받으려면 Adobe의 전문 [서비스](http://www.adobe.com/marketing-cloud/service-support/professional-consulting-training.html) 팀을 고려하거나 솔루션 파트너 파인더를 [](https://solutionpartners.adobe.com/home/partnerFinder.html) 통해 전 세계 Adobe의 파트너 목록을 확인하십시오.

패키지 구조 규칙
-----------------------

롤링 배포를 지원하기 위해 AEM을 클라우드 서비스 패키지로 사용할 수 있으며, 이러한 커넥터의 예로는 &quot;변경할 수 없음&quot;과 &quot;변경 가능&quot; 컨텐츠가 구분됩니다. 패키지는 다음과 같은 패키지 간에 깔끔하게 분리되어야 합니다.

* `/apps`
* `/content` 및 `/conf`

커넥터는 [이 문서에](/help/implementing/developing/introduction/aem-project-content-package-structure.md)설명된 이러한 패키징 지침을 따라야 합니다. 기존 커넥터도 일치되도록 다시 팩토링해야 합니다.

또한 Adobe만이 코드를 작성하고 고객 및 파트너가 `/libs`이에 서명해야 `/apps`합니다.

또한 기존 커넥터를 리팩토링하여 한 때 다른 최상위 폴더(예: `/etc` 예: `/conf`)로 배치했을 수 있는 모든 구성을 이동할 수도 있습니다. 이 내용은 AEM [설명서에](https://helpx.adobe.com/experience-manager/6-5/sites/deploying/using/repository-restructuring.html)설명되어 있습니다.

커넥터 코드가 여러 개 있는 고객을 위해 깨끗한 저장소 구조를 홍보하려면 대부분의 커넥터 코드를 `/apps/connectors/<vendor>` 아래에서 배치하는 것이 좋습니다.

클라우드 서비스 구성
-----------------------------

커넥터 구현의 한 가지 이점은 커넥터 구성을 지원하는 코드입니다. 이 코드는 커넥터 이름이 있는 카드를 도구 > 작업 > 클라우드 서비스 아래에 표시합니다. 클릭하면 고객이 커넥터 구성을 포함할 상위 폴더를 선택하는 구성 브라우저가 표시됩니다. 커넥터의 코드는 구성해야 하는 모든 속성이 있는 양식으로 생성되어야 하며, 궁극적으로 이 값은 구성 폴더에 `/conf`저장됩니다. 나중에 사이트 속성 탭 또는 자산 속성 탭에서 이 폴더를 선택할 수 있습니다.


컨텍스트 인식 구성
-----------------------------

[컨텍스트 인식 구성을](https://sling.apache.org/documentation/bundles/context-aware-configuration/context-aware-configuration.html) 사용하면 아래 `/libs`, `/apps`및 하위 폴더를 비롯한 다양한 폴더에 레이어 구성을 만들 수 `/conf` `/conf`있습니다. 이 플러그인은 상속을 지원하므로 고객은 각 마이크로 사이트에 대해 특정 변경 사항을 적용하면서 글로벌 구성을 구성할 수 있습니다. 클라우드 서비스 구성에 대해 이 기능을 활용할 수 있으므로 커넥터 코드는 특정 구성 노드를 참조하는 대신 컨텍스트 인식 구성 API를 사용하여 구성을 참조해야 합니다.

커넥터에서 수정된 구성을 사용하는 경우 커넥터를 설계하여 Connector에서 제공한 기본 구성에 대한 향후 업데이트를 고객 구성과 포함/병합합니다. 고객 경고 및 동의 없이 사용자 지정된 컨텐츠 또는 구성을 변경(고객이 변경한 상태)하면 해당 커넥터로 인해 중단되거나 예기치 않은 동작이 발생할 수 있습니다.

코딩 우수 사례
----------------------

클라우드 서비스로서의 AEM은 클라우드 기반 솔루션이므로 커넥터의 코드 전략에 영향을 줄 수 있는 몇 가지 지침이 있습니다. 자세한 [내용은 AEM을 클라우드 서비스](/help/implementing/developing/introduction/development-guidelines.md) 개발 가이드라인으로 참조하십시오.

AEM Connector 테스트
-------------------------

로컬 환경 개발 기술을 사용하여 새 커넥터를 만들거나 기존 커넥터를 수정해야 합니다. 파트너 팀은 ISV 파트너에게 AEM Connector를 vanilla 애플리케이션에 배포하여 제대로 작동하는지 확인할 수 있는 샌드박스 환경을 제공합니다.
