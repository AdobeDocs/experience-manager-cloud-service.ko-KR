---
title: 데모 사이트 관리
description: 데모 사이트를 관리하는 데 도움이 되는 도구 및 데모 사이트를 제거하는 방법에 대해 알아봅니다.
source-git-commit: df9b777e24e56ed0329895f833f50b45ecf2defa
workflow-type: tm+mt
source-wordcount: '947'
ht-degree: 0%

---


# 데모 사이트 관리 {#manage-demo-sites}

데모 사이트를 관리하는 데 도움이 되는 도구 및 데모 사이트를 제거하는 방법에 대해 알아봅니다.

## 지금까지 그 이야기 {#story-so-far}

AEM 참조 데모 추가 기능 여정의 이전 문서에서 [사이트 만들기,](create-site.md) 참조 데모 추가 기능의 템플릿을 기반으로 새 데모 사이트를 만들었습니다. 이제 다음을 수행해야 합니다.

* AEM 작성 환경에 액세스하는 방법을 이해합니다.
* 템플릿을 기반으로 사이트를 만드는 방법을 알아봅니다.
* 사이트 구조를 탐색하고 페이지를 편집하는 기본 사항을 이해합니다.

또한 [데모 사이트용 AEM Screens 활성화,](screens.md) 다음 작업도 수행해야 합니다.

* AEM Screens의 기본 사항을 알고 있습니다.
* We.Cafe 데모 콘텐츠를 이해합니다.
* We.Cafe용 AEM Screens 구성 방법을 알아봅니다.

탐색할 데모 사이트가 있으므로 이 문서에서는 데모 사이트를 관리하는 데 도움이 되는 도구 및 데모 사이트를 제거하는 방법에 대해 설명합니다.

## 목표 {#objective}

이 문서는 생성한 데모 사이트를 관리하는 방법을 이해하는 데 도움이 됩니다. 읽은 후에는 다음을 수행해야 합니다.

* 셀프 서비스 데모 유틸리티에 액세스하는 방법을 이해합니다.
* 사용 가능한 유틸리티를 확인합니다.
* 기존 데모 사이트 또는 템플릿을 삭제하는 방법

## 셀프 서비스 데모 유틸리티 액세스 {#accessing-utilities}

데모 사이트가 자체 있으므로 이를 관리하는 방법을 알고 싶을 수 있습니다. 파이프라인은 데모 사이트 컨텐츠를 제공하기 위해 사이트 템플릿을 배포할 뿐만 아니라 이러한 사이트를 관리하기 위해 일련의 유틸리티 세트를 배포했습니다.

1. AEM 전역 탐색 모음에서 를 선택합니다 **도구** -> **참조 데모** -> **참조 데모 유틸리티**.

   ![셀프 서비스 데모 유틸리티](assets/demo-utilities.png)

1. 참조 데모 유틸리티는 Adobe Experience Manager 환경을 설정하고 모니터링하는 데 도움이 되는 유용한 기능의 모음입니다. 초기 보기는 입니다. **대시보드**: 환경 및 데모 기능의 상태 확인 역할을 합니다.

   ![대시보드](assets/dashboard.png)

셀프 서비스 데모 유틸리티는 많은 도구를 제공합니다.

* **사이트 삭제** - 이 Adobe Experience Manager 인스턴스에서 삭제할 사이트를 선택합니다. 이 작업은 파괴적인 작업이므로 일단 시작해도 취소할 수 없습니다.
* **사이트 템플릿 삭제** - 이 Adobe Experience Manager 인스턴스에서 삭제할 사이트 템플릿을 선택합니다. 사이트 템플릿을 삭제하기 전에 템플릿을 참조하는 모든 사이트도 삭제되었는지 확인합니다. 이 작업은 파괴적인 작업이므로 일단 시작해도 취소할 수 없습니다.
* **Prime 작성자 캐시** - Adobe Experience Manager 인스턴스 내에서 여러 리소스를 가져와 가져오기 시간을 단축합니다. 몇 초 정도 걸릴 수 있습니다.
* **Android 앱** - 데모 Android 앱 설치 및 실행 도구. 를 기반으로 사이트 만들기 **WKND 단일 페이지 앱** 을 눌러 이 페이지를 채웁니다. Android 장치, 에뮬레이터 또는 Bluestack에서 사용합니다.
* **사용자 환경 설정** - 자습서 팝업 대화 상자를 끕니다.
* **GraphQL 설정** - 글로벌 GraphQL 엔드포인트를 빠르게 설정합니다.

## 데모 사이트 및 템플릿 삭제 {#deleting}

AEM 기능 세트를 테스트한 후에는 더 이상 데모 사이트 또는 데모 사이트가 기반으로 하는 템플릿도 필요하지 않을 수 있습니다. 데모 사이트와 사이트 템플릿을 모두 삭제하기가 쉽습니다.

1. 액세스 권한 **참조 데모 유틸리티** 탭하거나 클릭합니다. **사이트 삭제**.

   ![사이트 삭제](assets/delete-sites.png)

1. 사용 가능한 사이트는 목록에 표시됩니다. 삭제할 사이트 또는 사이트를 확인한 다음 탭하거나 클릭합니다 **삭제**.

   >[!CAUTION]
   >
   >사이트 및 템플릿 삭제는 파괴적인 작업이며, 한 번 시작하면 취소할 수 없습니다.

1. 대화 상자에서 사이트 삭제를 확인합니다.

   ![사이트 삭제 확인](assets/confirm-site-delete.png)

1. AEM은 선택한 사이트나 사이트를 삭제하고 진행 상황을 **삭제** 이전 단추였습니다.

   ![진행률 삭제](assets/delete-progress.png)

이제 사이트가 삭제됩니다.

제목 아래에서 같은 방식으로 템플릿을 삭제할 수 있습니다 **사이트 템플릿 삭제** 에서 **참조 데모 유틸리티**.

>[!CAUTION]
>
>사이트 템플릿을 삭제하기 전에 템플릿을 참조하는 모든 사이트도 삭제되었는지 확인합니다.

## 여정 종료? {#end-of-journey}

축하합니다! AEM 참조 데모 추가 기능 여정을 완료했습니다! 이제 다음을 수행해야 합니다.

* Cloud Manager에 대한 기본 이해를 제공하고 파이프라인이 컨텐츠 및 구성을 AEM에 전달하는 방법을 이해합니다.
* Cloud Manager를 사용하여 새 프로그램을 만드는 방법을 이해합니다.
* 새로운 프로그램에 대한 참조 데모 추가 기능을 활성화하고 파이프라인을 실행하여 추가 기능 컨텐츠를 배포하는 방법을 알아봅니다.
* 템플릿을 기반으로 사이트를 만들기 위해 AEM 작성 환경에 액세스하는 방법을 이해합니다.
* 셀프 서비스 데모 유틸리티에 액세스하는 방법을 이해합니다.
* 기존 데모 사이트 또는 템플릿을 삭제하는 방법을 알아봅니다.

이제 고유한 데모 사이트를 사용하여 AEM의 기능을 탐색할 수 있습니다. 그러나 AEM은 강력한 도구이며 다양한 추가 옵션을 사용할 수 있습니다. 에서 사용할 수 있는 추가 리소스 중 일부를 확인하십시오 [추가 리소스 섹션](#additional-resources) 추가 정보를 확인하십시오.

## 추가 리소스 {#additional-resources}

* [Cloud Manager 설명서](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/onboarding-concepts/cloud-manager-introduction.html) - Cloud Manager의 기능에 대한 자세한 내용은 세부 기술 문서를 직접 참조하십시오.
* [사이트 만들기](/help/sites-cloud/administering/site-creation/create-site.md) - AEM을 사용하여 사이트 템플릿을 사용하여 사이트를 만들고 사이트의 스타일 및 구조를 정의하는 방법을 알아봅니다.
* [AEM 페이지 이름 지정 규칙.](/help/sites-cloud/authoring/fundamentals/organizing-pages.md#page-name-restrictions-and-best-practices) - AEM 페이지 구성에 대한 규칙을 이해하려면 이 페이지를 참조하십시오.
* [AEM 기본 처리](/help/sites-cloud/authoring/getting-started/basic-handling.md) - 탐색 및 콘솔 구성과 같은 기본 개념을 이해하기 위해 AEM을 처음 사용하는 경우 이 문서를 살펴보십시오.
* [AEM as a Cloud Service 기술 설명서](https://experienceleague.adobe.com/docs/experience-manager-cloud-service.html) - 이미 AEM에 대한 확고한 이해가 있는 경우 심층적인 기술 문서를 직접 참조할 수 있습니다.
* [사이트 템플릿](/help/sites-cloud/administering/site-creation/site-templates.md) - 사이트 템플릿의 구조와 사이트 작성에 사용되는 방법에 대해 자세히 알아보려면 이 문서를 참조하십시오.
