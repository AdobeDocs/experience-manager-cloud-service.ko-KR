---
title: AEM 커넥터 구현
description: AEM 커넥터 구현
exl-id: 70024424-8c52-493e-bbc9-03d238b8a5f5
source-git-commit: 90de3cf9bf1c949667f4de109d0b517c6be22184
workflow-type: tm+mt
source-wordcount: '968'
ht-degree: 10%

---

AEM 커넥터 구현
=============================

Provided below are useful references for building [AEM Connectors](https://www.adobe.io/apis/experiencecloud/aem/aemconnectors.html) and should be read in conjunction with guidance on [submitting](submit.md) and [maintaining](maintain.md) connectors.

AEM용 개발자 라이센스는 [Adobe 교환 프로그램](https://partners.adobe.com/exchangeprogram/experiencecloud).

공통 통합 패턴
---------------------------

AEM은 첨단 웹 경험 관리 솔루션이며, 통합의 잠재적인 많은 영역을 제공합니다. 일반적인 통합 패턴에는 다음이 포함됩니다.

* 외부 시스템의 데이터를 AEM으로 가져오는 중입니다. 예를 들어, CRM에서 연락처 정보를 내보내어 AEM 기반 웹 사이트를 방문하는 더 많은 사용자가 사용할 수 있도록 합니다.  구현에서는 Sling의 을 사용해야 합니다 [예약된 작업](https://sling.apache.org/documentation/bundles/apache-sling-eventing-and-job-handling.html#scheduled-jobs): 컨테이너가 작동 중단되더라도 작업이 실행되도록 보장합니다. 작업이 두 번 이상 트리거될 수 있다고 가정하기 위해 코드를 설계해야 합니다.
* AEM에서 외부 시스템으로 데이터 내보내기. 예를 들어, AEM 기반 웹 사이트에서 CRM에 제출된 뉴스레터 구독 설정이 여기에 해당합니다.
* AEM에서 자산 검색. 예를 들어, AEM Assets에 저장된 자산을 참조하는 외부 CMS(콘텐츠 관리 시스템)가 있습니다. 또는 다른 예로 AEM Assets의 이미지에 연결된 PIM 시스템이 있습니다.
* AEM 인프라에 자산 저장. 예를 들어 AEM Assets에 승인된 자산을 저장하는 MRM(마케팅 리소스 관리) 시스템입니다.
* 사용자 지정 UI 구성 요소 구성 및 렌더링. 예를 들어, 작성자가 비디오 구성 요소를 드래그 앤 드롭하고 라이브 사이트에서 재생할 특정 비디오를 구성할 수 있도록 허용합니다.
* 파트너 서비스를 사용하여 자산에 대해 작업. 예를 들어 페이지가 게시될 때 비디오 플랫폼으로 자산 전송
* AEM Admin Console에서 사이트, 페이지 또는 자산 분석. 예를 들어, 기존 또는 게시 취소된 페이지에 대해 SEO 추천을 할 수 있습니다.
* 외부 서비스에서 유지 관리하는 사용자 데이터에 대한 페이지 수준 액세스. 예를 들어 인구 통계 정보를 활용하여 사이트 경험을 개인화합니다. 컨텍스트 데이터를 저장, 조작 및 제공하기 위한 프레임워크인 ContextHub에 대해 알아보십시오.
* 사이트 복사 또는 자산 메타데이터 번역 자세한 내용은 [AEM 번역 프레임워크 Bootstrap 커넥터](https://github.com/Adobe-Marketing-Cloud/aem-translation-framework-bootstrap-connector) 변환 커넥터의 기본 구현인 AEM Translation Framework를 사용한 샘플 코드의 경우.


유용한 설명서
--------------------

as a Cloud Service Experience Manager [설명서](../overview/introduction.md) AEM에서 개발에 대한 중요한 통찰력을 제공합니다. 다음은 AEM 커넥터를 구현하는 동안 유용할 수 있는 몇 가지 특정 기술 항목 및 참조입니다.

* ACS(Adobe 컨설팅 서비스) [AEM 샘플](http://adobe-consulting-services.github.io/acs-aem-samples/) AEM 개발자를 교육하는 데 도움이 되는 잘 알려진 코드
* 이 문서의 공통 통합 패턴 섹션의 다양한 설명서 링크

커뮤니티 리소스
--------------------

위의 정적 설명서 외에도 Adobe 및 AEM 커뮤니티에서 커넥터를 출시하는 데 도움이 되는 리소스를 제공합니다.

* Adobe 커뮤니티 [AEM 포럼](http://help-forums.adobe.com/content/adobeforums/kr/experience-manager-forum/adobe-experience-manager.html) 는 동료가 질문하고 응답하는 활성 사이트입니다
* 추가 Adobe 기술 리소스는 특정 파트너 수준에서 사용할 수 있습니다. 추가 정보 [Adobe 교환 프로그램](https://partners.adobe.com/exchangeprogram/experiencecloud).
* If your organization would like implementation help, consider Adobe&#39;s [Professional Services](http://www.adobe.com/marketing-cloud/service-support/professional-consulting-training.html) team or see the [Solution Partner Finder](https://solutionpartners.adobe.com/home/partnerFinder.html) for a list of Adobe&#39;s partners across the globe

패키지 구조 규칙
-----------------------

롤링 배포를 지원하기 위해 AEM as a Cloud Service 패키지의 예로는 &quot;변경할 수 없는&quot; 컨텐츠와 &quot;변경할 수 없는&quot; 컨텐츠 간에 엄격한 구분이 있습니다. 패키지는 다음과 같은 패키지와 완전히 분리되어야 합니다.

* `/apps`
* `/content` 및 `/conf`

커넥터는 다음과 같이 설명된 이러한 패키지 지침을 따라야 합니다 [이 문서](/help/implementing/developing/introduction/aem-project-content-package-structure.md). 기존 커넥터도 준수하도록 리팩터링해야 합니다.

또한 Adobe만 코드를 `/libs`, 고객 및 파트너가 `/apps`.

기존 커넥터를 리팩터링하여 한 번 배치되었을 수 있는 구성을 이동해야 할 수도 있습니다 `/etc` 다른 최상위 폴더(예: `/conf`. 이 재구성은 AEM 6.5의 일부로 수행되었으며, [AEM 6.5 설명서](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/restructuring/repository-restructuring.html).

대부분의 커넥터 코드는 아래에 배치하는 것이 좋습니다 `/apps/connectors/<vendor>` 커넥터를 여러 개 사용하는 고객에 대해 깨끗한 저장소 구조를 프로모션하기 위해.

Cloud Services 구성
-----------------------------

커넥터 구현의 한 측면은 커넥터의 구성을 지원하는 코드입니다. 이 코드를 사용하면 커넥터 이름이 있는 카드가 도구 > 작업 > Cloud Services 아래에 나타납니다. 클릭하면 [구성 브라우저](/help/implementing/developing/introduction/configurations.md#using-configuration-browser) 고객이 커넥터 구성을 포함할 상위 폴더를 선택하는 위치를 표시합니다. 커넥터의 코드는 구성해야 하는 모든 속성이 있는 양식을 생성하여 최종적으로 아래의 구성 폴더에 값을 저장해야 합니다 `/conf`. 이 폴더는 나중에 사이트 속성 탭 또는 자산 속성 탭에서 선택할 수 있습니다.


텍스트 인식 구성
-----------------------------

[컨텍스트 인식 구성](https://sling.apache.org/documentation/bundles/context-aware-configuration/context-aware-configuration.html) 다음을 포함하여 서로 다른 폴더에 계층 구성을 허용합니다. `/libs`, `/apps`, `/conf` 하위 폴더 `/conf`. 고객이 각 마이크로사이트에 대해 특정 변경을 수행하는 동안 글로벌 구성을 구성할 수 있도록 상속을 지원합니다. Cloud Services 구성에 대해 이 기능을 활용할 수 있으므로 커넥터 코드는 특정 구성 노드를 참조하는 대신 컨텍스트 인식 구성 API를 사용하여 구성을 참조해야 합니다.

커넥터에서 수정된 구성을 사용하는 경우 커넥터를 설계하여 향후 업데이트를 고객 구성과 함께 Connector에서 제공하는 기본 구성으로 처리/병합합니다. 고객 경고 및 동의 없이 사용자 지정된(고객이 변경한 경우) 컨텐츠 또는 구성을 변경하면 해당 커넥터로 중단되거나(또는 예기치 않은 동작을 생성)될 수 있습니다.

코딩 우수 사례
----------------------

AEM as a Cloud Service은 클라우드 기반의 솔루션이므로 커넥터의 코드 전략에 영향을 줄 수 있는 몇 가지 지침이 있습니다. 자세한 내용은 [AEM as a Cloud Service 개발 지침](/help/implementing/developing/introduction/development-guidelines.md) 자세한 내용

AEM 커넥터 테스트
-------------------------

로컬 환경 개발 기술을 사용하여 새 커넥터를 만들거나 기존 커넥터를 수정해야 합니다. Partner Team은 ISV 파트너에게 AEM Connector를 vanilla 애플리케이션에 배포하여 작동 여부를 확인할 수 있는 샌드박스 환경을 제공합니다.
