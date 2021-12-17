---
title: 데모 사이트 만들기
description: 사전 구성된 템플릿 라이브러리를 기반으로 AEM에서 데모 사이트를 만듭니다.
source-git-commit: 52d65251744ce0ae5cf7a7e0a45b39d8fe78f13a
workflow-type: tm+mt
source-wordcount: '781'
ht-degree: 1%

---


# 데모 사이트 만들기 {#creating-a-site}

사전 구성된 템플릿 라이브러리를 기반으로 AEM에서 데모 사이트를 만듭니다.

## 지금까지 그 이야기 {#story-so-far}

AEM 빠른 사이트 만들기 여정의 이전 문서에서, [프로그램 만들기,](create-program.md) 첫 번째 구성 단계를 수행하여 테스트 목적의 프로그램을 만들고 파이프라인을 사용하여 추가 기능 컨텐츠를 배포했습니다. 이제 다음을 수행해야 합니다.

* Cloud Manager를 사용하여 새 프로그램을 만드는 방법을 이해합니다.
* 새 프로그램에 대한 참조 데모 추가 기능을 활성화하는 방법을 알아봅니다.
* 파이프라인을 실행하여 추가 기능 컨텐츠를 배포할 수 있습니다.

이 문서에서는 참조 데모 추가 기능의 템플릿을 기반으로 AEM에서 새 사이트를 만들어 프로세스의 다음 단계를 설명합니다.

## 목표 {#objective}

이 문서는 참조 데모 추가 기능의 템플릿을 기반으로 새 사이트를 만드는 방법을 이해하는 데 도움이 됩니다. 읽은 후에는 다음을 수행해야 합니다.

* AEM 작성 환경에 액세스하는 방법을 이해합니다.
* 템플릿을 기반으로 사이트를 만드는 방법을 알아봅니다.
* 사이트 구조를 탐색하고 페이지를 편집하는 기본 사항을 이해합니다.

## 데모 사이트 만들기 {#create-site}

파이프라인이 참조 데모 추가 기능을 배포하면 AEM 작성 환경에 액세스하여 추가 기능 컨텐츠를 기반으로 데모 사이트를 만들 수 있습니다.

1. Cloud Manager의 프로그램 개요 페이지에서 AEM 작성 환경에 대한 링크를 탭하거나 클릭합니다.

   ![작성 환경 액세스](assets/access-author.png)

1. AEM의 기본 메뉴에서 을(를) 탭하거나 클릭합니다 **Sites**.

   ![사이트 액세스](assets/access-sites.png)

1. 사이트 콘솔에서 을 탭하거나 클릭합니다 **만들기** 화면 오른쪽 상단에서 을(를) 선택하고 을(를) 선택합니다. **템플릿의 사이트** 을 클릭합니다.

   ![템플릿에서 사이트 만들기](assets/create-site-from-template.png)

1. 사이트 만들기 마법사가 시작됩니다. 왼쪽 열에서 작성 인스턴스에 파이프라인이 배포한 데모 템플릿을 볼 수 있습니다. 하나를 탭하거나 클릭하여 선택하고 오른쪽 열에 세부 사항을 표시합니다. **다음**&#x200B;을 탭하거나 클릭합니다.

   ![사이트 만들기 마법사](assets/site-creation-wizard.png)

1. 다음 화면에서 사이트의 제목을 입력합니다. 사이트 이름을 제공할 수 있거나, 생략하면 제목에서 생성됩니다. **만들기**&#x200B;를 탭하거나 클릭합니다.

   * 사이트 제목은 브라우저 제목 표시줄에 나타납니다.
   * 사이트 이름이 URL의 일부가 됩니다.
   * 사이트 이름은 AEM 페이지 이름 지정 규칙을 준수해야 하며 자세한 내용은 [추가 리소스](#additional-resources) 섹션을 참조하십시오.

   ![사이트 세부 사항](assets/site-details.png)

1. 사이트 만들기가 대화 상자로 확인됩니다. 탭 또는 클릭 **완료**.

   ![사이트 만들기 완료](assets/site-creation-complete.png)

이제 고유한 데모 사이트를 만들었습니다!

## 데모 사이트 사용 {#use-site}

데모 사이트가 만들어지면 이제 AEM의 다른 사이트처럼 해당 사이트를 탐색하고 사용할 수 있습니다.

1. 이제 사이트가 사이트 콘솔에 표시됩니다.

   ![Sites 콘솔의 새로운 데모 사이트](assets/new-demo-site.png)

1. 화면의 오른쪽 상단 모서리에서 콘솔 보기가 로 설정되어 있는지 확인합니다. **열 보기**.

   ![열 보기](assets/column-view.png)

1. 사이트의 구조와 컨텐츠를 탐색하려면 사이트를 탭하거나 클릭합니다. 데모 사이트의 컨텐츠 트리를 탐색할 때 열 보기가 계속 확장됩니다.

   ![사이트 구조](assets/site-structure.png)

1. 페이지를 탭하거나 클릭하여 선택한 다음, 탭하거나 클릭합니다 **편집** 클릭합니다.

   ![페이지 선택](assets/select-page.png)

1. 페이지를 구성 요소 또는 자산 추가 또는 편집과 같은 다른 AEM 컨텐츠 페이지로 편집하고 AEM의 기능을 테스트할 수 있습니다.

   ![페이지 편집](assets/edit-page.png)

축하합니다! 이제 데모 사이트의 콘텐츠를 자세히 살펴보고 참조 데모 추가 기능의 모범 사례 콘텐츠를 통해 AEM에서 제공해야 하는 모든 것을 발견할 수 있습니다.

다른 템플릿을 기반으로 추가 사이트를 만들어 더 많은 AEM 기능을 탐색합니다.

## 다음은 무엇입니까? {#what-is-next}

AEM 참조 데모 추가 기능 여정의 이 부분을 완료했으므로 다음을 수행해야 합니다.

* AEM 작성 환경에 액세스하는 방법을 이해합니다.
* 템플릿을 기반으로 사이트를 만드는 방법을 알아봅니다.
* 사이트 구조를 탐색하고 페이지를 편집하는 기본 사항을 이해합니다.

이제 추가 기능 콘텐츠를 사용하여 AEM의 기능을 테스트할 수 있습니다. 이 데모 컨텐츠를 관리하는 방법을 이해하려면 다음 문서를 검토하여 AEM 참조 데모 추가 기능 여정을 계속 진행합니다 [데모 사이트 관리,](manage.md) 데모 사이트를 관리하는 데 도움이 되는 도구 및 데모 사이트를 제거하는 방법에 대해 알아봅니다.

## 추가 리소스 {#additional-resources}

* [Cloud Manager 설명서](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/onboarding-concepts/cloud-manager-introduction.html) - Cloud Manager의 기능에 대한 자세한 내용은 세부 기술 문서를 직접 참조하십시오.
* [사이트 만들기](/help/sites-cloud/administering/site-creation/create-site.md) - AEM을 사용하여 사이트 템플릿을 사용하여 사이트를 만들고 사이트의 스타일 및 구조를 정의하는 방법을 알아봅니다.
* [AEM 페이지 이름 지정 규칙.](/help/sites-cloud/authoring/fundamentals/organizing-pages.md#page-name-restrictions-and-best-practices) - AEM 페이지 구성에 대한 규칙을 이해하려면 이 페이지를 참조하십시오.
* [AEM 기본 처리](/help/sites-cloud/authoring/getting-started/basic-handling.md) - 탐색 및 콘솔 구성과 같은 기본 개념을 이해하기 위해 AEM을 처음 사용하는 경우 이 문서를 살펴보십시오.