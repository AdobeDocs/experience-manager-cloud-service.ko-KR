---
title: Cloud Manager 소개
description: Cloud Manager가 프로그램, 환경 및 파이프라인을 통해 AEM 프로젝트를 지원하는 방법에 대해 알아봅니다.
exl-id: b743f126-b34e-4f48-a3f0-5dbd4e1ac34e
source-git-commit: 1994b90e3876f03efa571a9ce65b9fb8b3c90ec4
workflow-type: tm+mt
source-wordcount: '835'
ht-degree: 100%

---

# Cloud Manager 소개 {#intro-cloud-manager}

Cloud Manager는 AEM as a Cloud Service의 필수 구성 요소이며 팀의 단일 진입점 역할을 합니다. 특별히 제작된 CI/CD 파이프라인은 철저한 테스트와 최고의 코드 품질을 보장하여 탁월한 경험을 제공합니다. 고객이 프로젝트를 빠르게 시작할 수 있도록 Cloud Manager는 클라우드 리소스 및 환경을 생성하고 git 저장소에 액세스하는 기능을 포함하여 셀프서비스 방식으로 시작하는 데 필요한 모든 기능을 제공합니다. 이러한 기능은 기업 개발 설정을 지원하므로 팀이 변경 사항을 자주 커밋하고 탁월한 디지털 경험을 신속하게 제공하며 가치 실현 시간을 단축할 수 있습니다.

시스템 관리자는 클라우드 리소스 및 개발자를 생성할 개인을 포함하여 Cloud Manager 팀을 구성할 책임이 있습니다. 기업 개발 팀을 설정하고 확장하는 방법과 AEM as a Cloud Service가 개발 프로세스를 지원하는 방법에 대한 자세한 내용은 [AEM as a Cloud Service에 대한 기업 팀 개발 설정](/help/implementing/cloud-manager/managing-code/enterprise-team-dev-setup.md)을 참조하십시오.

## Cloud Manager의 개요 페이지로 이동 {#navigate-cloud-manager}

다음 단계에 따라 Cloud Manager로 이동합니다.

1. Cloud Manager의 로그인 페이지([`https://my.cloudmanager.adobe.com`.](https://my.cloudmanager.adobe.com/))로 이동합니다.

1. Cloud Manager의 **프로그램 및 제품** 페이지에서 프로그램을 선택하여 **개요** 페이지를 시작합니다.

다음 단계에 따라 Adobe Experience Cloud 홈 페이지에서 Cloud Manager 프로그램 및 제품 페이지로 이동할 수도 있습니다.

1. Adobe Experience Cloud([`https://experience.adobe.com`](https://experience.adobe.com))로 이동한 다음 Adobe ID를 사용하여 로그인합니다.

1. 도구 모음의 오른쪽 상단에 표시된 조직 이름을 참조하여 올바른 조직에 있는지 확인합니다.

1. **Experience Manager**&#x200B;를 선택합니다.

1. **Cloud Manager** 카드에서 **실행**&#x200B;을 클릭합니다.

## Cloud Manager의 역할 기반 권한 {#role-based-permissions}

| 권한 | 설명 | 비즈니스 소유자 | 배포 관리자 | 프로그램 관리자 | 개발자 |
|--- |--- |--- |--- |--- |--- |
| 프로그램 추가<br>프로그램 편집 | 새 프로그램 추가<br>솔루션 또는 추가 기능 추가 또는 제거 | x |  |  |  |
| 환경 만들기 | 프로덕션+스테이징 및 개발 환경 만들기 | x | x |  |  |
| 환경 업데이트 | 프로덕션+스테이징 및 개발 환경 업데이트 | x | x |  |  |
| 개발 환경 삭제 | 개발 환경 삭제 | x | x |  |  |
| 파이프라인 설정 | 파이프라인 설정 및 편집 |  | x |  |  |
| 파이프라인 실행 | 파이프라인 시작 | x | x |  |  |
| 파이프라인 실행 | 중요한 3계층 품질 게이트 실패 거부/승인 | x | x | x |  |
| 파이프라인 실행 | Go-Live 승인 제공 | x | x | x |  |
| 파이프라인 실행 | 프로덕션 배포 예약 | x | x | x |  |
| 파이프라인 삭제 | 파이프라인 삭제 허용 |  | x |  |  |
| 실행 취소 | 현재 실행 취소 |  | x |  |  |
| 개인 액세스 토큰 생성 | git 액세스 |  | x |  | x |
| RDE 만들기 | 신속한 개발 환경 만들기 | x |  |  | x |
| RDE 재설정 | 신속한 개발 환경 재설정 | x |  |  | x |

>[!NOTE]
>
>한 사용자에게 여러 역할을 할당할 수 있습니다. 예를 들어 사용자에게 **비즈니스 소유자** 및 **배포 관리자** 역할을 모두 할당하면 사용자에게 이러한 권한의 합계가 제공됩니다.

## Cloud Manager 프로그램 {#cloud-manager-programs}

Cloud Manager 프로그램은 비즈니스 이니셔티브의 논리적 그룹화를 지원하는 Cloud Manager 환경 세트를 나타냅니다. 이러한 그룹화는 일반적으로 구매한 SLA(서비스 수준 계약)에 해당합니다. 예를 들어 한 프로그램은 조직의 공개 웹 사이트를 지원하기 위한 AEM 리소스를 나타내고 다른 프로그램은 내부 DAM을 나타낼 수 있습니다.


Cloud Manager 프로그램 사용에 대해 자세히 알아보려면 이 [비디오](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-manager/programs.html)를 시청하십시오.

사용자는 **샌드박스** 또는 **프로덕션** 프로그램을 만들 수 있습니다.

* **프로덕션 프로그램**&#x200B;은 미래의 적절한 시간에 라이브 트래픽을 활성화하기 위해 만들어집니다.
   * 자세한 내용은 [프로덕션 프로그램 소개](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/introduction-production-programs.md)를 참조하십시오.

* **샌드박스 프로그램**&#x200B;은 일반적으로 교육, 데모 실행, 활성화, POC 만들기 또는 문서화 목적으로 만들어집니다.
   * 라이브 트래픽을 전달하기 위한 것이 아니며 프로덕션 프로그램에는 없는 제한 사항이 있습니다.
   * 여기에는 Sites 및 Assets가 포함되며 샘플 코드, 개발 환경 및 비프로덕션 파이프라인이 포함된 git 분기가 자동으로 채워져 제공됩니다.
   * 자세한 내용은 [샌드박스 프로그램 소개](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/introduction-sandbox-programs.md)를 참조하십시오.

## Cloud Manager 환경 {#cloud-manager-environments}

클라우드 환경은 Cloud Manager를 통해 생성, 액세스 및 조회됩니다. 이러한 환경은 프로덕션, 스테이징 또는 개발 환경일 수 있습니다. 각 환경은 서로 다른 용도로 사용되며 다른 CI/CD 파이프라인과 함께 사용할 수 있습니다. 환경은 다음과 같은 서비스로 구성됩니다.

* [AEM 제작 서비스](#author-services)
* [AEM 게시 서비스](#publish-services)
* [Dispatcher 서비스](#dispatcher-services)

>[!TIP]
>
> 사용 가능한 환경에 대한 개요는 [Adobe Cloud Manager 환경 사용](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-manager/environments.html) 비디오를 참조하십시오.
>
>사용자가 만들 수 있는 환경 유형과 사용자가 환경을 만드는 방법에 대한 자세한 내용은 [환경 관리](/help/implementing/cloud-manager/manage-environments.md)를 참조하십시오.

### AEM 제작 서비스 {#author-services}

AEM 제작 서비스는 사이트 콘텐츠 및 디지털 자산이 생성, 관리 및 업데이트되는 환경에 포함됩니다. 일반적으로 내부 사용자만 제작 서비스에 액세스할 수 있으며 로그인 화면 뒤에 유지됩니다. 제작 서비스는 제작 및 미리보기 환경 역할을 모두 수행합니다.

### AEM 게시 서비스 {#publish-services}

AEM 게시 서비스는 웹 사이트와 같은 최종 사용자 경험을 호스팅하는 환경에 포함됩니다. 사이트 방문자가 보고 상호 작용하는 서비스입니다. 일반적으로 게시 서비스는 공개적으로 사용할 수 있습니다.

### AEM Dispatcher 서비스 {#dispatcher-services}

Dispatcher는 AEM 게시 서비스 앞의 보안 및 성능 계층을 제공하는 `Apache HTTP Web server` 모듈입니다.
