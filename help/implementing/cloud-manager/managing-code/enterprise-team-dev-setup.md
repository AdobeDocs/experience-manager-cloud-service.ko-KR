---
title: 엔터프라이즈 개발 팀 설정
description: 기업 개발 팀을 설정 및 확장하는 방법과 AEM as a Cloud Service를 통해 개발 프로세스를 지원하는 방법을 알아봅니다.
exl-id: 85f8779b-12cb-441b-a34d-04641184497a
source-git-commit: bc3c054e781789aa2a2b94f77b0616caec15e2ff
workflow-type: tm+mt
source-wordcount: '1437'
ht-degree: 95%

---

# AEM as a Cloud Service에 대한 엔터프라이즈 개발 팀 설정 {#enterprise-setup}

기업 개발 팀을 설정 및 확장하는 방법과 AEM as a Cloud Service를 통해 개발 프로세스를 지원하는 방법을 알아봅니다.

## 소개 {#introduction}

기업 개발 설정을 사용하는 고객을 지원하기 위해 AEM as a Cloud Service는 Cloud Manager 및 해당 목적에 맞게 빌드된 [독자적인 CI/CD 파이프라인과 완전히 통합됩니다](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md). 이러한 파이프라인과 서비스는 모범 사례를 기반으로 구축되어 철저한 [테스트와 최고의 코드 품질](/help/implementing/cloud-manager/code-quality-testing.md)을 보장합니다.

## 기업 팀 개발 설정에서 Cloud Manager 지원 {#cloud-manager}

Cloud Manager는 신속한 온보딩을 보장하기 위해 사용자 정의 내용을 저장한 다음 Cloud Manager에서 빌드, 확인 및 배포하는 git 저장소를 포함하여 디지털 경험 개발을 즉시 시작하는 데 필요한 모든 기능을 제공합니다.

개발 팀은 Cloud Manager를 사용하여 Adobe 직원에게 의존하지 않고 자주 변경 사항을 적용할 수 있습니다.

Cloud Manager에서는 세 가지 유형의 환경을 사용할 수 있습니다.

* 개발
* 스테이지
* 프로덕션

코드는 비프로덕션 파이프라인을 사용하여 개발 환경에 배포할 수 있습니다. 항상 함께 구성되는 스테이지 및 프로덕션 환경의 경우 모범 사례로서 프로덕션 배포 전 유효성 검사를 보장하기 위해 프로덕션 파이프라인은 [품질 게이트](/help/implementing/cloud-manager/custom-code-quality-rules.md)를 사용하여 애플리케이션 코드 및 구성 변경의 유효성을 검사합니다.

프로덕션 파이프라인은 먼저 코드와 구성을 스테이징 환경에 배포하고 애플리케이션을 테스트한 다음 마지막으로 프로덕션에 배포합니다.

항상 최신 AEM as a Cloud Service 개선 사항으로 업데이트되는 Cloud Service SDK를 통해 개발자의 로컬 하드웨어를 직접 활용하여 로컬 개발을 수행할 수 있습니다. 이를 통해 매우 짧은 처리 시간으로 신속한 개발이 가능합니다. 따라서 개발자는 익숙한 로컬 환경을 사용하고 다양한 개발 도구 중에서 선택할 수 있으며 적합하다고 판단되면 개발 환경이나 프로덕션으로 푸시할 수 있습니다.

Cloud Manager는 기업의 요구 사항에 맞게 조정할 수 있는 유연한 다중 팀 설정을 지원합니다. 한 팀이 모든 팀의 프로덕션에 영향을 미치는 상황을 피하면서 여러 팀과 함께 안정적인 배포를 보장하기 위해 Cloud Manager의 독자적인 파이프라인은 항상 모든 팀의 코드를 함께 검증하고 테스트합니다.

## 실제 사례 {#real-world-example}

기업마다 팀 설정, 프로세스 및 개발 워크플로 등의 요구 사항이 다릅니다. 아래에 설명된 설정은 Adobe에서 AEM as a Cloud Service를 기반으로 경험을 제공하는 여러 프로젝트에 사용됩니다.

예를 들어 Adobe Photoshop 또는 Adobe Illustrator와 같은 Adobe Creative Cloud 애플리케이션에는 최종 사용자가 사용할 수 있는 튜토리얼, 샘플 및 안내서와 같은 콘텐츠 리소스가 포함되어 있습니다. 이 콘텐츠는 AEM Cloud 게시 계층에 API를 호출하여 구조화된 콘텐츠를 JSON 스트림으로 검색하고 를 사용하여 Headless 방식으로 AEM as a Cloud Service을 사용하는 클라이언트 애플리케이션에서 사용됩니다. [AEM as a Cloud Service의 CDN(Content Delivery Network)](/help/implementing/dispatcher/cdn.md#content-delivery) 정형 및 비정형 컨텐츠를 최적의 성능으로 제공할 수 있습니다.

이 프로젝트에 기여하는 팀은 다음 프로세스를 따릅니다.

각 팀은 자체 개발 워크플로를 사용하며 별도의 git 저장소가 있습니다. 추가 공유 git 저장소는 프로젝트 온보딩에 사용됩니다. 이 git 저장소에는 공유 Dispatcher 구성을 포함하는 Cloud Manager git 저장소의 루트 구조가 포함되어 있습니다.

새 프로젝트를 온보딩하려면 공유 git 저장소의 루트에 있는 Reactor Maven 프로젝트 파일에 나열되어야 합니다. Dispatcher 구성의 경우 Dispatcher 프로젝트 내부에 새 구성 파일이 생성됩니다. 그런 다음 이 파일이 기본 Dispatcher 구성에 포함됩니다. 각 팀은 자체 Dispatcher 구성 파일을 담당합니다. 공유 git 저장소에 대한 변경은 드물며 일반적으로 새 프로젝트가 온보딩될 때만 필요합니다. 주요 작업은 각 프로젝트 팀이 자체 git 저장소 내에서 수행합니다.

![워크플로 다이어그램](/help/implementing/cloud-manager/assets/team-setup1.png)

각각에 대한 git 저장소는 [AEM Project Archetype](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html)을 사용하여 설정되므로 AEM 프로젝트 설정을 위한 모범 사례를 따릅니다. 유일한 예외는 위에 설명된 대로 공유 git 저장소에서 수행되는 Dispatcher 구성입니다.

각 팀은 git 흐름 모델에 따라 2개의 +N 분기가 있는 단순화된 git 워크플로를 사용합니다.

* 안정적인 릴리스 분기에는 프로덕션 코드가 포함됩니다.

* 개발 분기에는 최신 개발이 포함됩니다.

* 각 기능에 대해 새 분기가 생성됩니다.

개발은 기능 분기에서 수행됩니다. 기능이 완성되면 개발 분기에 병합됩니다. 완성되고 검증된 기능은 개발 분기에서 선택되어 안정적인 분기에 병합됩니다.

모든 변경은 풀 요청(PR)을 통해 수행됩니다. 각 PR의 유효성은 품질 게이트에서 자동으로 검사됩니다. 코드의 품질을 확인하는 데는 Sonar가 사용되며 새 코드에 회귀가 발생하지 않는지 확인하기 위해 일련의 테스트 모음이 실행됩니다.

Cloud Manager의 git 저장소 설정에는 두 개의 분기가 있습니다.

* 안정적인 릴리스 분기에는 모든 팀의 프로덕션 코드가 포함됩니다.
* 개발 분기에는 모든 팀의 개발 코드가 포함됩니다.

개발 또는 안정적인 분기에서 팀의 git 저장소로 푸시할 때마다 [GitHub 작업](/help/implementing/cloud-manager/managing-code/working-with-multiple-source-git-repositories.md#managing-code)이 트리거됩니다.

모든 프로젝트는 안정적인 분기에 대해 동일한 설정을 따릅니다. 프로젝트의 안정적인 분기로 푸시하면 Cloud Manager의 git 저장소에 있는 안정적인 분기로 자동 푸시됩니다. Cloud Manager의 프로덕션 파이프라인은 안정적인 분기로 푸시하여 트리거되도록 구성됩니다. 따라서 프로덕션 파이프라인은 팀이 안정적인 분기로 푸시할 때마다 실행되며 모든 품질 게이트가 통과하면 프로덕션 배포가 업데이트됩니다.

![푸시 다이어그램](/help/implementing/cloud-manager/assets/team-setup2.png)

개발 분기에 대한 푸시는 처리 방법이 다릅니다. 팀의 git 저장소에 있는 개발자 분기로 푸시하면 GitHub 작업도 트리거되고 코드가 Cloud Manager의 git 저장소에 있는 개발 분기에 자동으로 푸시되지만, 비프로덕션 파이프라인은 코드 푸시에 의해 자동으로 트리거되지 않습니다. Cloud Manager의 API 호출에 의해 트리거됩니다.

프로덕션 파이프라인 실행에는 제공된 품질 게이트를 통해 모든 팀의 코드를 확인하는 작업이 포함됩니다. 코드가 스테이지에 배포되면 모든 것이 예상대로 작동하는지 확인하기 위해 테스트와 감사가 실행됩니다. 모든 게이트가 통과되면 가동 중단 없이 변경 사항이 프로덕션으로 롤아웃됩니다.

로컬 개발의 경우 [AEM as a Cloud Service용 SDK](/help/implementing/developing/introduction/aem-as-a-cloud-service-sdk.md#developing)가 사용됩니다. SDK를 사용하면 로컬 작성자, 게시 및 Dispatcher를 설정할 수 있습니다. 이를 통해 오프라인 개발 및 빠른 처리 시간이 가능합니다. 때로는 작성자 환경만 개발에 사용되지만 Dispatcher 및 게시 환경을 빠르게 설정하면 git 저장소로 푸시하기 전에 모든 것을 로컬에서 테스트할 수 있습니다.

각 팀의 멤버는 일반적으로 공유 git의 코드 및 자체 프로젝트 코드를 체크아웃합니다. 프로젝트가 독립적이므로 다른 프로젝트를 체크아웃할 필요가 없습니다.

![로컬 체크아웃 및 SDK](/help/implementing/cloud-manager/assets/team-setup3.png)

이 실제 설정을 청사진으로 사용한 다음 기업의 요구 사항에 맞게 사용자 정의할 수 있습니다. git의 유연한 분기 및 병합 개념은 모든 팀의 요구 사항에 맞게 위의 워크플로를 사용자 정의할 수 있습니다. AEM as a Cloud Service는 독창적인 Cloud Manager 파이프라인의 핵심 가치를 그대로 유지하면서 이러한 모든 변형을 지원합니다.

>[!TIP]
>
>이 설정에 대한 자세한 내용은 [다중 소스 Git 저장소를 사용하여 작업](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/managing-code/working-with-multiple-source-git-repos.html#managing-code) 문서를 참조하십시오.

### 다중 팀 설정에 대한 고려 사항 {#considerations}

Cloud Manager의 git 저장소와 프로덕션 파이프라인을 사용하면 전체 프로덕션 코드가 항상 모든 품질 게이트를 통해 실행되어 하나의 배포 단위로 처리됩니다. 이러한 방식으로 프로덕션 시스템은 중단 없이 항상 가동됩니다.

반면에 이러한 시스템이 없으면 각 팀이 개별적으로 배포할 수 있기 때문에 각 팀의 업데이트로 인해 프로덕션 안정성 문제가 발생할 위험이 있습니다. 또한 업데이트를 롤아웃하려면 조정과 계획된 가동 중지 시간이 필요합니다. 팀의 수가 증가함에 따라 조정 작업은 훨씬 더 복잡해지고 관리하는 데 시간이 오래 걸립니다.

품질 게이트에서 문제가 감지되면 생산에 영향을 미치지 않으며 Adobe 직원이 개입할 필요 없이 문제를 감지하고 해결할 수 있습니다. Cloud Service를 사용하지 않고 전체 배포를 항상 테스트하지 않으면 부분 배포로 인해 롤백 요청이 필요하거나 백업에서 전체 복원을 수행해야 하는 운영 중단이 발생할 수 있습니다. 부분 테스트로 인해 다른 문제가 발생하여 Adobe 직원의 조정 및 지원을 통해 해결해야 할 수도 있습니다.

>[!TIP]
>
>다중 팀 설정의 경우 모든 팀이 따라야 하는 거버넌스 모델과 일련의 표준을 정의하는 것이 중요합니다. 다중 팀 설정에 대한 이전 청사진을 시작점으로 사용하여 더 많은 팀으로 확장할 수 있습니다.
