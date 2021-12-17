---
title: 참조 데모 추가 기능 설치 이해
description: Cloud Manager와 추가 기능을 설치하는 데 사용하는 방법에 대해 알아봅니다.
source-git-commit: 52d65251744ce0ae5cf7a7e0a45b39d8fe78f13a
workflow-type: tm+mt
source-wordcount: '983'
ht-degree: 0%

---


# 참조 데모 추가 기능 설치 이해 {#understand-installation}

Cloud Manager와 추가 기능을 설치하는 데 사용하는 방법에 대해 알아봅니다.

>[!TIP]
>
>이미 Cloud Manager에 경험이 있거나 추가 기능의 구성 및 사용으로 바로 이동하려는 경우 로 건너뛸 수 있습니다. [프로그램 및 파이프라인 만들기](create-program.md)
>
>Cloud Manager와 AEM을 함께 사용하여 데모 환경을 만들고 고유한 데모 환경을 설정하고 사용하는 방법을 알아보려면 현재 문서를 계속 읽으십시오.

## 목표 {#objective}

이 문서는 참조 데모 추가 기능의 설치 프로세스가 작동하는 방식을 이해하는 데 도움이 되며 다양한 조각을 함께 작동하는 방식을 보여 줍니다. 읽은 후에는 다음을 수행해야 합니다.

* Cloud Manager에 대한 기본 이해를 얻으십시오.
* 파이프라인이 컨텐츠 및 구성을 AEM에 전달하는 방법을 이해합니다.
* 몇 번의 클릭만으로 데모 컨텐츠가 미리 채워진 새 사이트를 템플릿을 통해 만들 수 있는 방법을 살펴볼 수 있습니다.

이 문서에서는 설치를 시작하는 여정의 다음 단계로 이동하기 전에 AEM 참조 데모 추가 기능의 이러한 기본 부분을 이해하는 데 중점을 둡니다.

이 여정 단계별 프로세스를 수행하는 것이 좋지만 이미 Cloud Manager에 경험이 있거나 추가 기능의 구성 및 사용으로 바로 이동하려는 경우 로 건너뛸 수 있습니다. [프로그램 및 파이프라인 만들기](create-program.md)

## 책임 역할 {#responsible-role}

이 여정은 **비즈니스 소유자** 조직의 Cloud Manager 역할입니다.

## 요구 사항 및 사전 요구 사항 {#requirements-prerequisites}

참조 데모 추가 기능을 학습하고 사용하기 시작하는 데 필요한 최소 요구 사항이 있습니다.

### 지식 {#knowledge}

* Cloud Manager에 대한 기본 지식

### 도구 {#tools}

* 다음 항목의 구성원이어야 합니다. **비즈니스 소유자** 조직에 대한 Cloud Manager의 역할

## Cloud Manager 이해 {#cloud-manager}

Cloud Manager는 AEM as a Cloud Service의 필수 구성 요소이며 플랫폼의 단일 시작 지점으로 사용됩니다.

Cloud Manager는 필요한 환경 및 도구를 포함하여 AEM 프로젝트를 지원하는 클라우드 리소스를 관리하는 데 사용됩니다. 이 여정을 위해 Cloud Manager에 대한 완전한 이해는 필요하지 않습니다. 그러나 몇 가지 기본 개념을 숙지해야 합니다.

>[!TIP]
>
>Cloud Manager에 대해 자세히 알아보려면 [추가 리소스](#additional-resources) 이 문서의 섹션을 참조하십시오.

### 프로그램 {#programs}

Cloud Manager에 로그인하면 하나 이상에 액세스할 수 있습니다 **프로그램**. 프로그램은 여러 가지 방법으로 정의할 수 있지만, 한 가지 브랜드 이미지와 연관된 사이트 및 경험과 연관된 것으로 생각하는 것이 더 쉽습니다.

을 나타내는 Cloud Manager에 로그인하는 경우 **WKND Travel and Adventure Enterprises**&#x200B;로 지정하는 경우 **WKND 밤문화** 프로그램 및 **WKND 뒤뜰 프로젝트** 프로그램. 이 두 프로그램 모두 관련 사이트를 관리하기 위한 AEM 환경이 있을 것입니다.

### 샌드박스 {#sandboxes}

프로그램은 프로덕션 프로그램 또는 샌드박스 프로그램 중 하나일 수 있습니다.

* **프로덕션 프로그램** 프로그램이 라이브로 전환될 준비가 되면 결국 라이브 트래픽을 허용하도록 만들어집니다.
* **샌드박스 프로그램** 교육, 실행 데모, 사용, POC 등을 위해 작성됩니다. 및 는 라이브 트래픽을 위한 것이 아닙니다.

AEM 참조 데모 추가 기능을 설치하려면 새 샌드박스 프로그램을 만들어야 합니다.

>[!NOTE]
>
>AEM 참조 데모 추가 기능은 샌드박스 프로그램에서만 사용할 수 있습니다.

## 설치 및 사용 흐름 {#installation-flow}

Cloud Manager의 몇 가지 기본 개념을 이해했으므로 AEM 참조 데모 추가 기능 설치는 개념적으로 간단합니다.

1. Cloud Manager에 로그인합니다.
1. 프로그램의 옵션으로 AEM 참조 데모 추가 기능을 활성화하여 새 샌드박스 AEM 프로그램을 만듭니다.
1. 데모 컨텐츠 및 구성이 프로그램에 배포됩니다. 데모 콘텐츠에는 다음이 포함되어 있습니다.
   * 우수 사례 예제로 사전에 채워진 AEM 기능을 사용하여 다양한 AEM 사이트를 만드는 데 사용되는 사이트 템플릿입니다.
   * 데모 컨텐츠를 관리하는 구성 도구.
1. 새 샌드박스 프로그램에서 AEM에 로그인하고 빠른 사이트 만들기 도구를 사용하고 템플릿을 기반으로 데모 사이트를 만듭니다.
1. 구성 도구를 사용하여 더 이상 필요하지 않은 데모 사이트 및 템플릿을 삭제하는 것을 포함하여 해당 데모 사이트 및 템플릿을 관리합니다.

## AEM 사이트 템플릿 {#site-templates}

AEM 사이트 템플릿은 사이트에 대해 사전 정의된 컨텐츠 및 구조를 포함하는 패키지입니다. AEM 관리자가 새 사이트를 만들 때 비즈니스 사례에 적용되는 템플릿 중에서 선택할 수 있도록 특정 프로젝트의 요구 사항에 맞게 사이트 템플릿을 사용자 지정할 수 있습니다.

AEM 참조 데모 추가 기능에는 다양한 테스트 및 데모 요구 사항을 위한 여러 템플릿이 포함되어 있습니다. 프로그램을 만들고 파이프라인을 배포하여 추가 기능을 설치하면 AEM에 로그인하고 많은 데모 템플릿을 기반으로 사이트를 만들 수 있습니다

## 다음은 무엇입니까? {#what-is-next}

AEM 참조 데모 추가 기능 여정의 이 부분을 완료했으므로 다음을 수행해야 합니다.

* Cloud Manager에 대한 기본 이해를 얻으십시오.
* 파이프라인이 컨텐츠 및 구성을 AEM에 전달하는 방법을 이해합니다.
* 몇 번의 클릭만으로 데모 컨텐츠가 미리 채워진 새 사이트를 템플릿을 통해 만들 수 있는 방법을 살펴볼 수 있습니다.

이 지식을 바탕으로 작성하고 다음 문서를 검토하여 AEM 빠른 사이트 만들기 여정을 계속 진행합니다 [프로그램 및 파이프라인 만들기,](create-program.md) 여기서 추가 기능을 배포할 새 프로그램 및 파이프라인을 설정하는 방법을 배웁니다.

## 추가 리소스 {#additional-resources}

문서를 검토하여 빠른 사이트 만들기 여정의 다음 부분으로 이동하는 것이 좋습니다 [프로그램 및 파이프라인 만들기,](create-program.md) 다음은 이 문서에서 언급된 일부 개념을 자세히 설명하는 몇 가지 추가 선택적 리소스입니다. 여정을 계속 진행할 필요는 없습니다.

* [프로그램 및 프로그램 유형 이해](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/understand-program-types.html) - 라이브 프로그램과 샌드박스 프로그램 간의 차이점을 이해하려면 여기에서 시작하십시오.
* [사이트 템플릿](/help/sites-cloud/administering/site-creation/site-templates.md) - 사이트 템플릿의 구조와 사이트 작성에 사용되는 방법에 대해 자세히 알아보려면 이 문서를 참조하십시오.
* [Cloud Manager 설명서](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/onboarding-concepts/cloud-manager-introduction.html) - Cloud Manager의 기능에 대한 자세한 내용은 세부 기술 문서를 직접 참조하십시오.
