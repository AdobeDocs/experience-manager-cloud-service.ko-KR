---
title: AEM Cloud Service의 AEM Sites 주목할 만한 변경 사항
description: 'AEM Cloud Service의 AEM Sites 주목할 만한 변경 사항 '
translation-type: tm+mt
source-git-commit: 16725342c1a14231025bbc1bafb4c97f0d7cfce8

---


# 클라우드 서비스로 AEM Sites에 대한 주목할 만한 변경 사항 {#notable-changes}

클라우드 서비스로 AEM Sites는 클라우드 기본 AEM의 일부로서 클라우드 서비스 플랫폼으로서 경험 관리 기능을 제공합니다. 클라우드 기본 확장성, 가동 시간, 항상 최신 상태로 유지되는 것과 같은 클라우드 서비스로서 AEM의 주요 이점뿐만 아니라, 클라우드 서비스로서 AEM Sites는 다양한 사이트 특정 변경 사항 및 추가 사항을 제공합니다.

>[!NOTE]
>이 문서에서는 AEM Sites의 주목할 만한 변경 사항을 강조 표시합니다. Cloud에서 AEM에 대한 일반적인 변경 사항은 다음을 참조하십시오.
>
>* [클라우드 서비스로 Adobe Experience Manager(AEM)의 주목할 만한 변경 사항](/help/release-notes/aem-cloud-changes.md)


클라우드 서비스로 AEM Sites에서 변경한 내용 및 추가 사항은 다음과 같습니다.

* [비동기 페이지 작업](#asynchronous-page-operations)
* [새 참조 사이트 및 자습서](#new-reference-site-and-tutorial)

## 비동기 페이지 작업 {#asynchronous-page-operations}

AEM Cloud 서비스에서 일반적으로 UI를 차단하는 작업은 백그라운드에서 실행되는 작은 작업으로 분류되었습니다.

* 페이지 이동
* 롤아웃 페이지

이러한 작업의 개시자는 의 새 UI에서 자신의 상태를 확인할 수 `/mnt/overlay/dam/gui/content/asyncjobs.html`있습니다.

>[!NOTE]
>
>이 새로운 기능을 사용하려면 시스템 사용자가 변경할 필요가 없습니다. 여기서는 AEM의 이전 온-프레미스 버전에서의 비헤이비어의 변경으로 알려져 있습니다.

## 새 참조 사이트 및 자습서 {#new-reference-site-and-tutorial}

[새 AEM](https://wknd.site/)참조 사이트, WKND는 AEM을 사용하여 웹 사이트를 구축하는 모범 사례와 AEM에서 사용할 수 있는 포괄적인 기능, 구성 요소 및 배포 모델 세트를 반영하도록 업데이트 및 게시되었습니다. 새로운 참조 사이트 및 [관련 자습서에서는](https://docs.adobe.com/content/help/en/experience-manager-learn/getting-started-wknd-tutorial-develop/overview.html) 프로젝트 설정, 핵심 구성 요소, 편집 가능한 템플릿, 클라이언트 라이브러리 및 Adobe Experience Manager Sites를 사용한 구성 요소 개발과 같은 기본 주제를 다룹니다.

이전에는 We.Retail이 기본적으로 AEM과 함께 설치되었습니다(프로덕션 모드에서 시작한 경우 제외).  이제 기본적으로 참조 사이트가 설치되지 않습니다.  대신 [업데이트된 WKND 참조 사이트 코드와 함께 Git](https://github.com/adobe/aem-guides-wknd/) 보고서 [및](https://docs.adobe.com/content/help/en/experience-manager-learn/getting-started-wknd-tutorial-develop/overview.html) 함께 제공되는 자습서가제공됩니다.

## Runtime에서 사용할 수 없는 기능 {#capabilities-not-available-at-runtime}

클라우드 서비스로서의 AEM은 항상 최신 상태로 유지됩니다. 이를 위해서는 변경 불가능하고 변경 가능한 컨텐츠로 AEM 저장소를 분리하고 런타임 시 변경 불가능한 컨텐츠에 대한 액세스를 금지해야 합니다. 변경 가능한 컨텐츠와 변경 불가능한 컨텐츠에 대한 자세한 내용은 [저장소의 변경 가능한 영역과 불변경 영역을 참조하십시오](/help/implementing/developing/introduction/aem-project-content-package-structure.md#mutable-vs-immutable).

런타임 시 변경할 수 없는 컨텐츠에 액세스할 수 없기 때문에 다음과 같은 AEM Sites 작업은 실행 시 사용할 수 없습니다.

* i18n 사전 번역
* AEM Sites 페이지 편집기의 개발자 모드

이러한 기능은 AEM의 독립 실행형 로컬 개발자 인스턴스를 클라우드 서비스로 통해 AEM의 컨텐츠 및 코드를 클라우드 서비스 GIT 리포지토리로 업데이트하는 데 사용할 수 있지만 호스팅된 런타임 인스턴스는 사용할 수 없습니다.
