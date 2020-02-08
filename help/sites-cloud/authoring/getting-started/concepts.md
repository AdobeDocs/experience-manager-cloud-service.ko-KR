---
title: 작성 개념
description: AEM에서 작성의 개념
translation-type: tm+mt
source-git-commit: 16725342c1a14231025bbc1bafb4c97f0d7cfce8

---


# 작성 개념 {#authoring-concepts}

AEM 설치는 일반적으로 두 개 이상의 환경으로 구성됩니다.

* 작성
* 게시

이러한 상호 작용을 통해 방문자가 액세스할 수 있도록 웹 사이트에서 컨텐츠를 사용할 수 있도록 만들 수 있습니다.

작성 환경에서는 컨텐츠를 실제로 게시하기 전에 컨텐츠를 만들고, 업데이트하고, 검토할 수 있는 메커니즘을 제공합니다.

* 작성자는 컨텐츠를 만들고 검토합니다. 컨텐츠는 페이지, 자산, 발행물 등과 같은 다양한 유형일 수 있습니다.
* 이 컨텐츠는 어느 시점에 웹 사이트에 게시됩니다.

![작성자, 게시자 및 디스패처 다이어그램](/help/sites-cloud/authoring/assets/author-publish.png)

작성 환경에서는 AEM의 작성 UI를 통해 AEM의 기능을 사용할 수 있습니다. 게시 환경의 경우 사용자가 사용할 수 있도록 만들어진 인터페이스의 전체 모양 및 느낌을 디자인합니다.

>[!NOTE]
>
>AEM 자체는 AEM 설명서를 게시하는 데 사용됩니다.

## 작성 환경 {#author-environment}

작성자는 **작성 환경으로**&#x200B;알려진 곳에서 작업합니다.이를 통해 컨텐츠 작성을 위한 편리한 인터페이스(그래픽 사용자 인터페이스(GUI 또는 UI)를 제공합니다. 적절한 액세스 권한이 할당된 계정을 사용하여 작성자가 로그인해야 합니다.

>[!NOTE]
>
>컨텐츠를 만들거나 편집하거나 게시하려면 계정에 적절한 액세스 권한이 있어야 합니다.

작성자의 인스턴스와 개인의 액세스 권한이 어떻게 구성되었는지에 따라 컨텐츠에서 다음을 비롯한 다양한 작업을 수행할 수 있습니다.

* 페이지에서 새 컨텐츠 생성 또는 기존 컨텐츠 편집
* 사전 정의된 템플릿을 사용하여 새 컨텐츠 페이지 만들기
* 자산 및 컬렉션 만들기, 편집 및 관리
* 컨텐츠 페이지, 자산 등의 이동, 복사 및 삭제
* 페이지, 자산 등의 게시(또는 게시 취소)

컨텐츠를 관리하는 데 도움이 되는 관리 작업들도 있습니다.

* 게시 전에 검토 실행과 같이 변경 사항을 관리하는 방법을 제어하는 워크플로우
* 개별 작업을 조정하는 프로젝트

>[!NOTE]
>
>AEM은 작성 환경에서도 관리됩니다.

## 게시 환경 {#publish-environment}

When ready, your site&#39;s content is published to the **publish environment**. 이 환경에서는 의도했던 대상이 디자인된 인터페이스의 모양 및 느낌에 따라 웹 사이트의 페이지를 사용할 수 있게 되어 있습니다.

페이지 게시 및 게시 취소에 대한 자세한 내용은 페이지 게시 [문서를 참조하십시오.](/help/sites-cloud/authoring/fundamentals/publishing-pages.md)

## Dispatcher {#dispatcher}

To optimize performance for visitors to your website, the **[dispatcher](/help/implementing/dispatcher/overview.md)**implements load balancing and caching.
