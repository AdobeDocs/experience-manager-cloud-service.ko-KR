---
title: 참조 데모 추가 기능 설치 이해
description: Cloud Manager 및 이를 사용하여 추가 기능을 설치하는 방법에 대해 알아봅니다.
exl-id: 9418aac6-a8c4-43f7-b329-b02149fe2d53
source-git-commit: bc3c054e781789aa2a2b94f77b0616caec15e2ff
workflow-type: tm+mt
source-wordcount: '956'
ht-degree: 97%

---

# 참조 데모 추가 기능 설치 이해 {#understand-installation}

Cloud Manager 및 이를 사용하여 추가 기능을 설치하는 방법에 대해 알아봅니다.

>[!TIP]
>
>숙련된 Cloud Manager 사용자이거나 추가 기능 구성 및 사용으로 바로 이동하고자 하는 경우, [프로그램 및 파이프라인 제작](create-program.md)으로 건너뜁니다.
>
>Cloud Manager와 AEM을 함께 사용하여 데모 환경을 제작하는 방법 및 나만의 데모 환경을 설정하고 사용하는 방법에 대해 자세히 알아보려면 현재 문서를 계속 읽어보십시오.

## 목표 {#objective}

이 문서는 서로 다른 부분이 함께 작동하며, 참조 데모 추가 기능의 설치 프로세스를 이루는 방법을 이해하는 데 도움이 됩니다. 문서를 읽고 나면

* Cloud Manager의 기본 사항에 대해 이해할 수 있습니다.
* 파이프라인이 AEM에 콘텐츠와 구성을 전달하는 방법을 이해할 수 있습니다.
* 몇 번의 클릭만으로 템플릿을 통해 데모 콘텐츠로 미리 채워진 사이트를 제작하는 방법을 파악할 수 있습니다.

이 문서는 설치를 시작하는 여정의 다음 단계로 이동하기 전에 이러한 AEM 참조 데모 추가 기능 기본 사항을 이해하는 데 중점을 둡니다.

이 여정을 진행하는 것이 좋지만, 숙련된 Cloud Manager 사용자이거나 추가 기능 구성 및 사용으로 바로 이동하고자 하는 경우에는 [프로그램 및 파이프라인 제작](create-program.md)으로 건너뜁니다.

## 담당 역할 {#responsible-role}

이 여정은 귀사의 Cloud Manager에서 **사업주** 역할의 멤버인 시스템 관리자에게 적용됩니다.

## 요구 사항 및 사전 요구 사항 {#requirements-prerequisites}

참조 데모 추가 기능에 대해 알아보고 이를 사용하는 데 필요한 최소 요구 사항이 있습니다.

### 지식 {#knowledge}

* Cloud Manager 기본 지식

### 도구 {#tools}

* 귀사의 Cloud Manager에서 **사업주** 역할의 멤버여야 합니다.

## Cloud Manager 이해 {#cloud-manager}

Cloud Manager는 AEM as a Cloud Service의 필수 구성 요소이며 플랫폼의 단일 진입점 역할을 합니다.

Cloud Manager를 사용하여 필요한 환경 및 도구 등 AEM 프로젝트를 지원하는 클라우드 리소스를 관리할 수 있습니다. 이 여정에서는 Cloud Manager를 완전히 이해하지 않아도 됩니다. 단, 몇 가지 기본 개념에 대해 숙지하고 있어야 합니다.

>[!TIP]
>
>Cloud Manager에 대해 자세히 알아보려면 다음을 참조하십시오. [추가 리소스](#additional-resources) 이 문서의 섹션에서 자세한 내용을 확인할 수 있습니다.

### 프로그램 {#programs}

Cloud Manager에 로그인하게 되면 하나 이상의 **프로그램**&#x200B;에 액세스할 수 있습니다. 다양한 방법으로 프로그램을 정의할 수 있지만, 프로그램을 하나의 브랜드 정체성과 관련된 사이트 및 경험과 연결하여 생각하는 것이 가장 쉽습니다.

**WKND Travel 및 Adventure Enterprises**&#x200B;를 나타내는 Cloud Manager에 로그인하면 **WKND Nightlife** 프로그램 및 **WKND Backyard Projects** 프로그램을 만들 수 있습니다. 이들 프로그램은 관련 사이트를 관리하기 위한 AEM 환경을 가질 수 있습니다.

### 샌드박스 {#sandboxes}

프로그램은 프로덕션 프로그램이거나 샌드박스 프로그램일 수 있습니다.

* **프로덕션 프로그램**&#x200B;은 프로그램을 실행할 준비가 되었을 때 라이브 트래픽을 허용하도록 생성됩니다.
* **샌드박스 프로그램**&#x200B;은 교육, 데모 실행, 지원, POC 등을 위해 만들어지며 실시간 트래픽을 위한 것이 아닙니다.

AEM 참조 데모 추가 기능을 설치하려면 샌드박스 프로그램을 만듭니다.

>[!NOTE]
>
>AEM 참조 데모 추가 기능은 샌드박스 프로그램에서만 사용할 수 있습니다.

## 설치 및 사용 흐름 {#installation-flow}

이제 Cloud Manager에 대한 몇 가지 기본 개념에 대해 알아보았으며 AEM 참조 데모 추가 기능 설치는 개념적으로 간단합니다.

1. Cloud Manager에 로그인합니다.
1. 샌드박스 AEM 프로그램을 설치하고 AEM 참조 데모 추가 기능을 해당 프로그램에 대한 옵션으로 활성화합니다.
1. 데모 콘텐츠 및 구성은 프로그램에 배포됩니다. 데모 콘텐츠에는 다음이 포함됩니다.
   * AEM의 기능을 사용하여 다양한 AEM 사이트를 만드는 데 사용되는 사이트 템플릿(모범 사례 예제들로 채워져 있음)
   * 데모 콘텐츠 관리를 위한 구성 도구
1. 새 샌드박스 프로그램에서 AEM에 로그인한 다음 빠른 사이트 생성 도구를 사용하여 템플릿을 기반으로 데모 사이트를 만듭니다.
1. 구성 도구를 사용하여 더 이상 필요하지 않은 경우 삭제하는 등 이들 데모 사이트 및 템플릿을 관리합니다.

## AEM 사이트 템플릿 {#site-templates}

AEM 사이트 템플릿은 사이트에 대해 사전 정의된 콘텐츠 및 구조가 포함된 패키지입니다. AEM 관리자가 사이트를 만들 때 해당 비즈니스 사례에 적용되는 템플릿을 선택할 수 있도록 사이트 템플릿을 특정 프로젝트의 요구 사항에 맞게 맞춤화할 수 있습니다.

AEM 참조 데모 추가 기능에는 다양한 테스트 및 데모 요구 사항을 위한 여러 템플릿이 포함됩니다. 프로그램을 만들고 파이프라인을 배포하여 추가 기능을 설치하고 나면 AEM에 로그인한 다음 다양한 데모 템플릿을 기반으로 사이트를 만들 수 있습니다.

## 다음 단계 {#what-is-next}

AEM 참조 데모 추가 기능 여정의 한 부분을 완료했으므로

* Cloud Manager의 기본 사항에 대해 이해할 수 있습니다.
* 파이프라인이 AEM에 콘텐츠와 구성을 전달하는 방법을 이해할 수 있습니다.
* 몇 번의 클릭만으로 템플릿을 통해 데모 콘텐츠로 미리 채워진 사이트를 제작하는 방법을 파악할 수 있습니다.

이 지식을 기반으로 [프로그램 및 파이프라인 제작](create-program.md)을 검토하여 AEM 빠른 사이트 생성 여정을 계속하십시오. 여기에서는 새 프로그램 및 파이프라인을 설정하여 추가 기능을 배포하는 방법에 대해 알아보게 됩니다.

## 추가 리소스 {#additional-resources}

[프로그램 및 파이프라인 제작](create-program.md)을 검토하여 빠른 사이트 생성 여정의 다음 부분으로 넘어가는 것이 좋으며 다음은 추가적인 일부 옵션 리소스입니다. 이 리소스는 해당 문서에서 언급된 개념에 대해 자세히 알아봅니다. 그러나 여정을 계속하지 않아도 됩니다.

* [프로그램 및 프로그램 유형 이해](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/programs/program-types.html) - 라이브 프로그램과 샌드박스 프로그램 간 차이점에 대해 이해할 수 있습니다.
* [사이트 템플릿](/help/sites-cloud/administering/site-creation/site-templates.md) - 사이트 템플릿 구조 및 이를 사용하여 사이트를 만드는 방법에 대해 자세히 알아보려면 이 문서를 참조하십시오.
* [Cloud Manager 설명서](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/onboarding-concepts/cloud-manager-introduction.html) - Cloud Manager의 기능에 대해 자세히 알아보려면 바로 심화 기술 문서를 참조할 수 있습니다.
