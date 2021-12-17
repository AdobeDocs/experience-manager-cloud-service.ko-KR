---
title: Cloud Manager 및 빠른 사이트 생성 워크플로우를 이해합니다
description: Cloud Manager와 새로운 빠른 사이트 생성 프로세스를 함께 연결하는 방법에 대해 알아봅니다.
source-git-commit: 5e1a89743c5ac36635a139ada690849507813c30
workflow-type: tm+mt
source-wordcount: '1102'
ht-degree: 0%

---


# Cloud Manager 및 빠른 사이트 생성 워크플로우를 이해합니다 {#understand-cloud-manager}

Cloud Manager와 새로운 빠른 사이트 생성 프로세스를 함께 연결하는 방법에 대해 알아봅니다.

>[!TIP]
>
>프런트 엔드 개발만 수행하는 역할인 경우 문서를 건너뛸 수 있습니다 [Git 리포지토리 액세스 정보 검색](retrieve-access.md) 여정에서 확인하십시오.
>
>AEM 관리자인 Cloud Manager 관리자가 프런트 엔드 개발 및 관리자 작업을 모두 담당하거나, 프런트 엔드 개발을 위해 AEM의 엔드 투 엔드 프로세스를 이해하려면 현재 문서를 계속 읽고 이 여정을 계속 진행합니다.

## 목표 {#objective}

이 문서는 AEM 빠른 사이트 만들기 도구가 작동하는 방식을 이해하고 종단 간 흐름에 대한 개요를 제공합니다. 읽은 후에는 다음을 수행해야 합니다.

* 프런트 엔드 개발을 지원하기 위해 AEM Sites과 Cloud Manager가 함께 작동하는 방식을 이해합니다
* 프런트엔드 사용자 지정 단계가 AEM에서 완전히 분리되고 AEM 지식이 필요하지 않은 방법을 참조하십시오.

이 문서는 구성을 시작하는 여정의 다음 단계로 이동하기 전에 빠른 사이트 작성 솔루션의 이러한 기본 사항을 이해하는 데 중점을 둡니다.

이 여정을 단계별로 진행하는 것이 좋지만 AEM Sites 및 Cloud Manager가 함께 작동하는 것을 이미 알고 있고 구성을 바로 시작하려면 다음을 수행할 수 있습니다 [여정의 다음 단계로 이동합니다.](create-site.md)

## 책임 역할 {#responsible-role}

이 여정 부분은 AEM 관리자와 Cloud Manager 관리자 모두에 적용됩니다.

## 요구 사항 및 사전 요구 사항 {#requirements-prerequisites}

빠른 사이트 만들기 도구를 사용하여 사이트를 만들고 사용자 지정하기 전에 몇 가지 요구 사항이 있습니다.

이 여정은 프런트엔드 개발자, 관리자 및 모든 역할의 조합을 위한 것이므로 두 가지 요구 사항이 여기에 나열되어 있습니다.

프런트 엔드 개발자의 경우 AEM 액세스 또는 지식이 필요하지 않음을 이해하는 것이 중요합니다.

### 지식 {#knowledge}

| 지식 | 역할 |
|---|---|
| 프런트 엔드 개발을 위한 표준 툴 및 프로세스 이해 | 프런트엔드 개발자 |
| AEM에서 사이트를 만들고 관리하는 방법에 대한 기본 지식입니다 | AEM 관리자 |
| Cloud Manager에 대한 기본 지식 | Cloud Manager 관리자 |

프런트 엔드 개발자의 경우 AEM 지식이 필요하지 않습니다.

### 도구 {#tools}

| 도구 | 역할 |
|---|---|
| 선호하는 프런트엔드 개발 환경 | 프런트엔드 개발자 |
| npm | 프런트엔드 개발자 |
| 웹 팩 | 프런트엔드 개발자 |
| Cloud Manager 액세스 | Cloud Manager 관리자 |
| 다음 항목의 구성원이어야 합니다. **비즈니스 소유자** Cloud Manager의 역할 | Cloud Manager 관리자 |
| Cloud Manager에서 Sys 관리자 되기 | Cloud Manager 관리자 |
| Admin Console 액세스 | Cloud Manager 관리자 |
| 의 구성원이어야 합니다 **배포 관리자** Cloud Manager의 역할 | Cloud Manager 관리자 |
| 의 구성원이어야 합니다 **배포 관리자** Cloud Manager의 역할 | 프런트엔드 개발자 |

프런트 엔드 개발자의 경우 AEM을 사용할 필요가 없습니다.

>[!TIP]
>
>Cloud Manager 역할 및 역할 관리에 익숙하지 않은 경우 의 역할 기반 권한 문서를 참조하십시오. [추가 리소스](#additional-resources) 섹션을 참조하십시오.

## Cloud Manager {#cloud-manager}

Cloud Manager는 AEM as a Cloud Service의 필수 구성 요소이며 플랫폼의 단일 시작 지점으로 사용됩니다.

AEM as a Cloud Service은 엔터프라이즈 개발 설정을 통해 고객을 지원하기 위해 Cloud Manager 및 특별히 제작된 CI/CD 파이프라인과 완벽하게 통합됩니다. Quick Site Creation 도구는 이러한 기능을 확장하여 전용 프런트 엔드 개발 파이프라인을 지원합니다.

이 여정을 위해 Cloud Manager에 대한 완전한 이해는 필요하지 않습니다. 높은 수준에서 Cloud Manager는 몇 가지 구조의 단계로 구성됩니다.

![Cloud Manager 구조](assets/cloud-manager-structure.png)

* **테넌트** - 모든 고객에게 테넌트가 제공됩니다. **WKND Travel and Adventure Enterprises** 임차인일 수 있습니다.
* **프로그램.** - 각 임차인에게 하나 이상의 프로그램이 있습니다. 다음 **WKND Travel and Adventure Enterprises** 임차인이 **WKND 밤문화** 그리고 **WKND 오후 프로젝트** 프로그램.
* **환경** - 각 프로그램에는 라이브 컨텐츠를 위한 프로덕션, 개발을 위한 스테이징 및 개발 등의 여러 환경이 있습니다. **WKND 밤문화** 및 **WKND 오후 프로젝트** 프로그램에는 개발, 스테이지 및 프로덕션 환경이 모두 있습니다.
* **저장소** - 환경에는 애플리케이션과 프런트 엔드 코드가 유지되는 Git 리포지토리가 있습니다.
* **도구 및 워크플로우** - 파이프라인은 저장소에서 환경으로의 코드 배포를 관리합니다.

## 빠른 사이트 생성 프런트 엔드 개발 흐름 {#flow}

Cloud Manager에 대한 경험이 아직 광범위하지 않더라도 전체 흐름은 간단하고 직관적입니다.

1. AEM 관리자는 AEM 환경에 로그인하고 사이트 템플릿을 사용하여 새 사이트를 만듭니다.
1. Cloud Manager 관리자는 Cloud Manager에서 프런트엔드 파이프라인을 생성합니다. 파이프라인은 Git 리포지토리에서 AEM 환경으로 코드 배포를 오케스트레이션합니다.
1. AEM 관리자는 프로그램의 AEM 인스턴스에서 사이트 테마를 내보내고 프런트 엔드 개발자에게 제공합니다.
1. Cloud Manager 관리자는 사용자 지정을 커밋할 수 있는 AEM Git 리포지토리에 대한 프런트 엔드 개발자 액세스 권한을 부여합니다.
1. 프런트 엔드 개발자는 액세스 자격 증명을 검색하여 git 및 파이프라인에 액세스합니다.
1. 프런트 엔드 개발자는 테마를 사용자 지정하고 프록시를 사용하여 사이트의 실제 콘텐츠를 사용하여 테스트한 다음 git 리포지토리에 변경 사항을 커밋합니다.
1. 프런트 엔드 개발자는 파이프라인을 실행하여 테마 사용자 지정을 프로그램의 프로덕션 환경에 배포합니다.

![빠른 사이트 만들기 흐름](assets/qsc-flow.png)

빠른 사이트 작성 도구를 사용할 때의 주요 이점은 순수 프런트 엔드 개발자는 실제 사용자 지정 작업만 책임진다는 것입니다. 프런트 엔드 개발자는 AEM과 상호 작용하지 않거나 AEM에 대한 지식이 필요합니다.

## 다음은 무엇입니까? {#what-is-next}

이제 AEM 빠른 사이트 만들기 여정의 이 부분을 완료했으므로 다음을 수행해야 합니다.

* 프런트 엔드 개발을 지원하기 위해 AEM Sites과 Cloud Manager가 함께 작동하는 방식을 이해합니다
* 프런트엔드 사용자 지정 단계가 AEM에서 완전히 분리되고 AEM 지식이 필요하지 않은 방법을 참조하십시오.

이 지식을 바탕으로 작성하고 다음 문서를 검토하여 AEM 빠른 사이트 만들기 여정을 계속 진행합니다 [템플릿에서 사이트 만들기,](create-site.md) 여기서 템플릿을 사용하여 새 AEM 사이트를 빠르게 만드는 방법을 알아봅니다.

## 추가 리소스 {#additional-resources}

문서를 검토하여 빠른 사이트 만들기 여정의 다음 부분으로 이동하는 것이 좋습니다 [템플릿에서 사이트 만들기,](create-site.md) 다음은 이 문서에서 언급된 일부 개념을 자세히 설명하는 몇 가지 추가 선택적 리소스입니다. 여정을 계속 진행할 필요는 없습니다.

* [Cloud Manager 설명서](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/onboarding-concepts/cloud-manager-introduction.html) - Cloud Manager의 기능에 대한 자세한 내용은 세부 기술 문서를 직접 참조하십시오.
* [역할 기반 권한](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/requirements/role-based-permissions.html) - Cloud Manager에는 적절한 권한이 있는 미리 구성된 역할이 있습니다. 이러한 역할에 대한 자세한 내용 및 관리 방법은 이 문서를 참조하십시오.
* [npm](https://www.npmjs.com) - 사이트를 빠르게 구축하는 데 사용되는 AEM 테마는 npm을 기반으로 합니다.
* [웹 팩](https://webpack.js.org) - 사이트를 빠르게 구축하는 데 사용되는 AEM 테마는 웹 팩을 사용합니다.
