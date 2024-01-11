---
title: AEM 커넥터 구현
description: 커넥터와 그 기능에 대해 자세히 알아보고 Experience Manager에서 이들 유용한 도구를 구현하는 방법에 대해 알아봅니다.
exl-id: 70024424-8c52-493e-bbc9-03d238b8a5f5
source-git-commit: 07db10c4ee9cced7b6a697fe4f41c99eaba6a39f
workflow-type: tm+mt
source-wordcount: '935'
ht-degree: 96%

---


AEM 커넥터 구현
=============================

다음은 [AEM 커넥터](https://www.adobe.io/apis/experiencecloud/aem/aemconnectors.html) 구축에 유용한 참고 자료이며, 커넥터 [제출](submit.md) 및 [유지](maintain.md) 지침과 함께 읽어야 합니다.

AEM에 대한 개발자 라이선스는 [Adobe 교환 프로그램](https://partners.adobe.com/exchangeprogram/experiencecloud).

일반적인 통합 패턴
---------------------------

AEM은 혁신적인 웹 경험 관리 솔루션으로, 다양한 잠재적 통합 영역을 제공합니다. 일반적인 통합 패턴은 다음과 같습니다.

* 외부 시스템에서 AEM으로 데이터 가져오기 예: CRM에서 연락처 정보를 가져와 AEM 기반 웹 사이트를 방문하는 더 많은 대상자가 이를 사용할 수 있도록 지원  구현은 컨테이너가 다운되더라도 작업이 실행될 수 있도록 하는 Sling의 [예정된 작업](https://sling.apache.org/documentation/bundles/apache-sling-eventing-and-job-handling.html#scheduled-jobs)을 사용해야 합니다. 코드는 작업이 잠재적으로 한 번 이상 트리거될 수 있음을 가정하고 설계되어야 합니다.
* AEM에서 외부 시스템으로 데이터 가져오기 예: AEM 기반 웹 사이트에서 CRM으로 제출된 뉴스레터 구독 설정
* AEM에서 자산 검색 예: AEM Assets에 저장된 자산을 참조하는 외부 콘텐츠 관리 시스템 (CMS) 또 다른 예: AEM Assets의 이미지에 연결된 PIM 시스템
* AEM 인프라에 자산 저장 예: AEM Assets에 승인된 자산을 저장하는 마케팅 리소스 관리(MRM) 시스템
* 사용자 정의 UI 구성 요소 구성 및 렌더링 예: 작성자가 비디오 구성 요소를 드래그하여 놓고 특정 비디오를 라이브 사이트에서 재생하도록 구성할 수 있도록 허용
* 파트너 서비스를 통해 자산을 사용하여 작업 예: 페이지가 게시될 때 자산을 비디오 플랫폼에 전송
* AEM 관리 콘솔의 사이트, 페이지 또는 자산 분석 예: 기존 또는 게시되지 않은 페이지에 대한 SEO 권장 사항 작성
* 외부 서비스에 의해 유지되는 사용자 데이터에 대한 페이지 수준 액세스 예: 인구학적 정보를 사용하여 사이트 경험 개인 맞춤화 컨텍스트 데이터를 저장하고, 조정하고, 나타낼 수 있는 프레임워크인 ContextHub에 대해 살펴보십시오.
* 사이트 사본 또는 자산 메타데이터 번역 권장 번역 커넥터 구현인 AEM 번역 프레임워크를 사용하는 샘플 코드에 대해 알아보려면 [AEM 번역 프레임워크 Bootstrap 커넥터](https://github.com/Adobe-Marketing-Cloud/aem-translation-framework-bootstrap-connector)를 참조하십시오.


유용한 설명서
--------------------

Experience Manager as a Cloud Service [설명서](../overview/introduction.md)는 AEM에서의 개발 작업에 관련하여 중요한 통찰력을 제공합니다. 아래는 AEM 커넥터 구현 시 유용하게 사용할 수 있는 몇 가지 특정 기술 주제 및 참고 자료입니다.

* AEM 개발자를 교육할 때 도움이 되도록 작성된 코드에 대한 Adobe 컨설팅 서비스(ACS) [AEM 샘플](https://adobe-consulting-services.github.io/acs-aem-samples/)
* 이 문서의 [일반적인 통합 패턴] 섹션에 있는 다양한 설명서 링크

커뮤니티 리소스
--------------------

위의 정적 설명서 이외에도 Adobe 및 AEM 커뮤니티는 커넥터를 시장에 출시하는 데 도움이 되는 리소스를 제공합니다.

* Adobe 커뮤니티의 [AEM 포럼](https://help-forums.adobe.com/content/adobeforums/en/experience-manager-forum/adobe-experience-manager.html)은 동료들이 질문을 묻고 답하는 활성 사이트입니다.
* 추가적인 Adobe 기술 리소스는 특정 파트너 수준으로 사용할 수 있습니다. [Adobe Exchange 프로그램](https://partners.adobe.com/exchangeprogram/experiencecloud)에 대해 자세히 알아보십시오.
* 구현 관련 도움이 필요한 경우 Adobe의 [전문 서비스](https://www.adobe.com/kr/marketing-cloud/service-support/professional-consulting-training.html) 팀에 문의하거나 [솔루션 파트너 파인더](https://solutionpartners.adobe.com/home/partnerFinder.html)를 참조하여 전 세계의 Adobe 파트너 목록을 확인하십시오.

패키지 구조 규칙
-----------------------

지속적인 배포를 지원하기 위해 AEM as a Cloud Service 패키지(예: 커넥터)는 “변경 불가능한” 콘텐츠와 “변경 가능한” 콘텐츠를 엄격하게 분리하여 사용합니다. 패키지는 다음 항목을 포함하는 패키지와 명확히 구분되어야 합니다.

* `/apps`
* `/content` 및 `/conf`

커넥터는 [이 문서](/help/implementing/developing/introduction/aem-project-content-package-structure.md)에 설명된 패키징 가이드라인을 준수해야 합니다. 기존 커넥터도 이에 부합하도록 리팩터링되어야 합니다.

또한 Adobe만 `/libs`에, 고객 및 파트너는 `/apps`에 코드를 작성해야 합니다.

기존 커넥터는 이전에 한 번 `/etc`로 배치되었을 수 있는 구성을 `/conf`와 같은 상위 수준 폴더로 이동하도록 리팩터링해야 할 수도 있습니다. 이러한 재구성은 AEM 6.5의 일부로 수행되며 이는 [AEM 6.5 설명서](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/restructuring/repository-restructuring.html)에 기재되어 있습니다.

대부분의 커넥터 코드는 아래에 배치하는 것이 좋습니다. `/apps/connectors/<vendor>` 여러 커넥터를 보유하고 있는 고객을 위해 깔끔한 저장소 구조를 홍보합니다.

클라우드 서비스 구성
-----------------------------

커넥터 구현의 한 가지 측면은 커넥터 구성을 지원하는 코드입니다. 이 코드를 사용하면 커넥터의 이름이 포함된 카드가 [도구] > [작업] > [클라우드 서비스] 아래에 표시됩니다. 클릭하면 고객이 커넥터 구성을 포함할 상위 폴더를 선택할 수 있는 [구성 브라우저](/help/implementing/developing/introduction/configurations.md#using-configuration-browser) 팝업이 표시됩니다. 커넥터의 코드는 구성되어야 하는 모든 속성이 포함된 양식을 만들어 궁극적으로 `/conf` 아래의 구성 폴더에 값을 저장해야 합니다. 이 폴더는 나중에 Sites 속성 탭 또는 Assets 속성 탭에서 선택할 수 있습니다.


컨텍스트 인식 구성
-----------------------------

[컨텍스트 인식 구성](https://sling.apache.org/documentation/bundles/context-aware-configuration/context-aware-configuration.html)을 사용하면 `/libs`, `/apps`, `/conf` 및 `/conf` 아래의 하위 폴더 등 서로 다른 폴더 간 구성에 레이어를 적용할 수 있습니다. 상속이 지원되므로 고객은 각 마이크로사이트의 특정 내용을 변경하는 동시에 전역 구성을 구성할 수 있습니다. 클라우드 서비스 구성에 이 기능을 사용할 수 있으므로, 커넥터 코드는 특정 구성 노드를 참조하는 대신 컨텍스트 인식 구성 API를 사용하는 구성을 참조해야 합니다.

수정된 구성을 커넥터에 사용하는 경우 커넥터를 커넥터 제공 기본 구성에 대한 향후 업데이트 및 고객 구성의 포함/병합을 처리할 수 있도록 설계하십시오. 맞춤화된(고객에 의해 변경된) 콘텐츠 또는 구성을 고객 경고 또는 동의 없이 변경하면 커넥터에 오류가 발생하거나 예기치 않은 동작이 발생할 수 있습니다.

코딩 모범 사례
----------------------

AEM as a Cloud Service는 클라우드 기반 솔루션이므로, 커넥터의 코드 전략에 영향을 미칠 수 있는 몇 가지 지침이 있습니다. 자세한 내용은 [AEM as a Cloud Service 개발 지침](/help/implementing/developing/introduction/development-guidelines.md)을 참조하십시오.

AEM 커넥터 테스트
-------------------------

로컬 환경 개발 기법을 사용하여 새 커넥터를 생성(또는 기존 커넥터를 수정)해야 합니다. 파트너 팀은 ISV 파트너에게 AEM 커넥터를 바닐라 애플리케이션에 배포하여 제대로 작동하는지 확인할 수 있는 샌드박스 환경을 제공합니다.
