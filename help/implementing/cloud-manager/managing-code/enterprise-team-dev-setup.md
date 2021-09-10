---
title: 엔터프라이즈 팀 개발 설정 - Cloud Services
description: 엔터프라이즈 팀 개발 설정에 대한 자세한 내용을 보려면 이 페이지를 따르십시오
exl-id: 85f8779b-12cb-441b-a34d-04641184497a
source-git-commit: 3cdee254eebcf45762feff8fe081b006a803ef1b
workflow-type: tm+mt
source-wordcount: '1525'
ht-degree: 0%

---

# AEM as a Cloud Service에 대한 Enterprise Team Development 설정 {#enterprise-setup}

## 소개 {#introduction}

AEM as a service를 제공하는 클라우드 기반의 서비스인 AEM as a Cloud Service은 10년 이상 엔터프라이즈 소프트웨어를 특정 요구 사항을 갖춘 엔터프라이즈 팀에 제공하는 이점을 누릴 수 있도록 설계되었습니다. AEM은 항상 켜져 있고 항상 최신 상태이며 항상 안전하며 항상 규모에 맞게 새로운 가치를 구현하여 클라우드 기반의 세계로를 투과시키는 반면 AEM은 고객에게 맞춤형 플랫폼으로 제공하고 엔터프라이즈급 팀이 개발 및 전달 절차에 통합할 수 있도록 하는 주요 가치 제안을 보유하고 있습니다.

Adobe 고객을 엔터프라이즈 개발 설정으로 지원하기 위해 AEM as a Cloud Service은 Cloud Manager 및 엔터프라이즈급 개발 및 배포를 통해 여러 해 경험에서 얻은 우수 사례와 지식을 갖추고 있으며 철저한 테스트와 최상의 코드 품질을 보장하여 탁월한 경험을 제공할 수 있도록 특별히 설계된 CI/CD 파이프라인과 완벽하게 통합됩니다.

## 엔터프라이즈 팀 개발 설정에서 Cloud Manager의 지원 {#cloud-manager}

고객을 위한 빠른 온보딩을 위해 Cloud Manager는 Cloud Manager에서 구축, 확인 및 배포하는 사용자 지정을 저장하는 git 저장소를 포함하여 경험 개발을 바로 시작하는 데 필요한 모든 것을 제공합니다.
개발 팀은 Cloud Manager를 사용하여 Adobe 직원에 의존하지 않고 자주 변경 사항을 커밋하는 작업을 수행할 수 있습니다.

Cloud Manager에서는 다음 세 가지 환경 유형을 사용할 수 있습니다.

* 개발
* 단계
* 프로덕션

비프로덕션 파이프라인을 사용하여 코드를 개발 환경에 배포할 수 있습니다. 프로덕션 배포 전에 항상 함께 실행되어 유효성 검사를 확인하는 스테이지 및 프로덕션의 경우, 프로덕션 파이프라인은 품질 게이트를 사용하여 애플리케이션 코드와 구성 변경 사항을 확인합니다.

프로덕션 파이프라인은 코드 및 구성을 스테이징 환경에 먼저 배포하고 애플리케이션을 테스트한 다음 최종적으로 프로덕션에 배포합니다.
항상 최신 Cloud Service 개선 사항으로 업데이트된 Cloud Service SDK를 사용하면 개발자의 로컬 하드웨어를 직접 활용하여 로컬 개발을 수행할 수 있습니다. 이것은 매우 적은 회전시간으로 빠른 발전을 가능하게 한다. 따라서 개발자는 친숙한 로컬 환경에서 머물면서 다양한 개발 도구 중에서 선택하고 적합한 개발 환경이나 프로덕션에 푸시할 수 있습니다.

Cloud Manager는 기업의 요구 사항에 맞게 조정할 수 있는 유연한 다중 팀 설정을 지원합니다. 이는 AMS뿐만 아니라 Cloud Service에도 적용됩니다. 여러 팀이 있는 안정적인 배포를 보장하고 모든 팀의 프로덕션에 영향을 주는 한 팀을 방지하기 위해 Cloud Manager는 관점으로 지정한 파이프라인이 항상 모든 팀의 코드를 함께 확인하고 테스트합니다.


## 실제 사례 {#real-world-example}

각 기업에는 서로 다른 팀 설정, 프로세스 및 개발 워크플로우를 비롯한 다양한 요구 사항이 있습니다. 아래 설명된 설정은 AEM 맨 위에 Cloud Service으로 경험을 제공하는 여러 프로젝트에 대해 Adobe에서 사용됩니다.

예를 들어 Adobe Photoshop 또는 Adobe Illustrator과 같은 Adobe Creative Cloud 애플리케이션에는 최종 사용자가 사용할 수 있는 자습서, 샘플 및 안내서와 같은 컨텐츠 리소스가 포함되어 있습니다. 이 컨텐츠는 AEM 클라우드 게시 계층에 API를 호출하여 구조화된 컨텐츠를 JSON 스트림으로 검색하며 AEM의 [CDN(Content Delivery Network)을 Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/content-delivery/cdn.html?lang=en#content-delivery)으로 활용하여 구조화된 컨텐츠와 구조화되지 않은 컨텐츠를 모두 최적의 성능으로 제공하는 방식으로 *헤드리스* 방식으로 Cloud Service을 사용하는 클라이언트 애플리케이션에서 사용합니다.

이 프로젝트에 참여하는 팀은 향후 설명된 프로세스를 따릅니다.

>[!NOTE]
>설정에 대한 자세한 내용은 [여러 소스 Git 저장소 작업](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/managing-code/working-with-multiple-source-git-repos.html#managing-code) 을 참조하십시오.

각 팀은 자체 개발 워크플로우를 사용하고 있으며 별도의 git 리포지토리를 가지고 있습니다. 추가적인 공유 Git 리포지토리는 프로젝트 온보딩에 사용됩니다. 이 Git 리포지토리에는 공유 Dispatcher 구성을 포함하여 Cloud Manager의 Git 리포지토리의 루트 구조가 포함되어 있습니다. 새 프로젝트를 온보딩하려면 공유 git 저장소의 루트에 있는 Reactor Maven 프로젝트 파일에 나열해야 합니다. Dispatcher 구성의 경우 Dispatcher 프로젝트 내에 새 구성 파일이 만들어집니다. 이 파일은 기본 Dispatcher 구성에 의해 포함됩니다. 각 팀은 자체 디스패처 구성 파일을 담당합니다. 공유 Git 리포지토리에 대한 변경 사항은 드물며, 일반적으로 새 프로젝트를 온보딩할 때만 필요합니다. 기본 작업은 고유한 Git 리포지토리 내에서 각 프로젝트 팀이 수행합니다.

![](/help/implementing/cloud-manager/assets/team-setup1.png)

각 팀의 git 리포지토리는 AEM Maven 원형 을 사용하여 설정되었으므로 AEM 프로젝트 설정에 대한 모범 사례를 따릅니다. 유일한 예외는 위에서 설명한 대로 공유 Git 리포지토리에서 수행되는 Dispatcher 구성을 처리하는 것입니다.
각 팀은 Git 흐름 모델에 따라 두 개의 + N 분기가 있는 간소화된 Git 워크플로우를 사용합니다.

* 안정적인 릴리스 분기는 프로덕션 코드를 포함한다

* 개발 분기에는 최신 개발이 포함되어 있습니다

* 각 기능에 대해 새 분기가 생성됩니다


개발은 기능이 완료될 때 피쳐 분기에서 수행되며 개발 분기로 병합됩니다. 완료되고 검증된 기능은 개발 분기에서 선택되고 안정적인 분기로 병합됩니다. 모든 변경 사항은 PR(가져오기 요청)을 통해 수행됩니다. 각 PR은 품질 게이트에 의해 자동으로 검증됩니다. Sonar는 코드 품질 확인에 사용되며 테스트 세트 세트를 실행하여 새 코드가 회귀를 도입하지 않는지 확인합니다.

Cloud Manager의 git 리포지토리에 있는 설정에는 두 개의 분기가 있습니다.

* 모든 팀의 프로덕션 코드를 포함하는 *안정적인 릴리스 분기*
* 모든 팀의 개발 코드가 포함된 *개발 분기*

개발 또는 안정적인 분기에서 팀의 Git 리포지토리에 대한 모든 푸시는 [github 작업](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/managing-code/working-with-multiple-source-git-repos.html?lang=en#managing-code)을 트리거합니다. 모든 프로젝트는 안정적인 분기에 대해 동일한 설정을 따릅니다. 프로젝트의 안정적인 분기에 대한 푸시가 Cloud Manager의 git 리포지토리에서 안정적인 분기로 자동으로 푸시됩니다. Cloud Manager의 프로덕션 파이프라인은 안정적인 분기로의 푸시에 의해 트리거되도록 구성됩니다. 따라서 프로덕션 파이프라인은 모든 팀의 각 푸시에 의해 안정적인 분기에 실행되며, 모든 품질 게이트가 전달되는 경우 프로덕션 배포가 업데이트됩니다.

![](/help/implementing/cloud-manager/assets/team-setup2.png)

개발 분기 푸시는 다르게 처리됩니다. 팀의 Git 리포지토리에서 개발자 분기에 대한 푸시가 github 작업을 트리거하고 코드가 Cloud Manager의 Git 리포지토리에서 개발 분기로 자동으로 푸시되는 동안 비프로덕션 파이프라인은 코드 푸시에 의해 자동으로 트리거되지 않습니다. Cloud Manager의 api 호출에 의해 트리거됩니다.
프로덕션 파이프라인 실행에는 제공된 품질 게이트를 통해 모든 팀의 코드를 확인하는 작업이 포함됩니다. 코드가 스테이지에 배포되면 테스트 및 감사가 실행되어 모든 것이 예상대로 작동하는지 확인합니다. 모든 게이트가 전달되면 중단 또는 다운타임 없이 변경 사항이 프로덕션에 롤아웃됩니다.
로컬 개발 시 Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/aem-as-a-cloud-service-sdk.html?lang=en#developing)로서 AEM용 [SDK가 사용됩니다. SDK를 사용하면 로컬 작성자, 게시 및 디스패처를 설정할 수 있습니다. 이를 통해 오프라인 개발 및 빠른 전환 시간이 가능합니다. 때로는 작성자만 개발에 사용되지만, 빠르게 디스패처 및 게시를 설정하면 Git 리포지토리로 푸시하기 전에 로컬로 모든 것을 테스트할 수 있습니다. 각 팀의 구성원은 일반적으로 고유한 프로젝트 코드뿐만 아니라 용으로 공유 git에서 코드를 체크아웃합니다. 프로젝트가 독립적이므로 다른 프로젝트를 체크아웃할 필요가 없습니다.

![](/help/implementing/cloud-manager/assets/team-setup3.png)

이러한 실제 설정은 블루프린트로 사용한 다음 기업의 요구 사항에 맞게 사용자 지정할 수 있습니다. 유연한 Git 분기 및 병합 개념을 사용하면 모든 팀의 요구 사항에 맞게 사용자 지정된 위의 워크플로우를 변형할 수 있습니다. AEM as a Cloud Service은 해당 Cloud Manager 파이프라인의 핵심 값을 그대로 유지하면서 이러한 모든 변형을 지원합니다.

### 다중 팀 설정에 대한 고려 사항 {#considerations}

>[!NOTE]
>여러 팀 설정의 경우 모든 팀이 따라야 하는 거버넌스 모델과 표준 세트를 정의하는 것이 중요합니다. 위에 요약된 다중 팀 설정에 대한 블루프린트를 사용하면 더 많은 팀에서 크기 조정을 수행할 수 있으며 이 블루프린트를 시작 지점으로 사용할 수 있습니다.

Cloud Manager의 Git 리포지토리 및 프로덕션 파이프라인을 사용하면 항상 모든 품질 게이트를 통해 전체 프로덕션 코드가 실행되어 하나의 배포 단위로 처리됩니다. 이렇게 하면 중단 또는 다운타임 없이 프로덕션 시스템이 *항상*에 있게 됩니다.
반면, 각 팀이 별도로 배포할 수 있으므로 이러한 시스템이 없으면 단일 팀으로부터 업데이트하면 프로덕션 안정성 문제가 발생할 수 있습니다. 또한 업데이트를 롤아웃하려면 조정과 계획된 다운타임이 필요합니다. 많은 팀들이 투입되면 조정 작업이 훨씬 더 복잡해지고 빠르게 관리할 수 없게 됩니다.

품질 게이트에서 문제가 감지되면 프로덕션에 영향을 주지 않으며, Adobe 직원이 개입하지 않고도 문제를 탐지하고 해결할 수 있습니다. Cloud Service을 사용하지 않고 전체 배포를 항상 테스트하지 않으면 부분 배포가 중단되므로 롤백 요청이나 백업에서 전체 복구가 필요할 수 있습니다. 부분 테스트는 Adobe 직원의 조정 및 지원이 필요한 사실을 다시 확인한 후 수정해야 하는 다른 문제를 초래할 수도 있습니다.
