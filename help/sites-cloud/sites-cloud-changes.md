---
title: AEM 클라우드 서비스의 AEM 사이트에 대한 주요 변경 사항
description: AEM 클라우드 서비스의 AEM 사이트에 대한 주요 변경 사항
exl-id: 60b1aec4-75a0-459f-bf77-8d8c1af757ce
source-git-commit: 90de3cf9bf1c949667f4de109d0b517c6be22184
workflow-type: tm+mt
source-wordcount: '538'
ht-degree: 21%

---

# AEM Sites as a Cloud Service에 대한 주요 변경 사항 {#notable-changes}

AEM Sites as a Cloud Service은 클라우드 기반의 AEM as a Cloud Service 플랫폼의 일부로서 경험 관리 기능을 제공합니다. AEM as a Cloud Service은 클라우드 기반의 확장성, 가동 시간, 항상 최신 상태로 유지하는 등 Cloud Service의 핵심 이점 외에도 많은 사이트 관련 변경 사항 및 추가 사항을 제공합니다.

>[!NOTE]
>이 문서에서는 AEM Sites의 주요 변경 사항을 조명합니다. AEM as a Cloud Service 및 기타 모듈에 대한 일반적인 변경 사항에 대해서는 다음을 참조하십시오.
>
>* [Adobe Experience Manager as a Cloud Service 소개](/help/overview/introduction.md)
* [AEM as a Cloud Service에 대한 개요 - 새로운 기능 및 다른 기능](/help/overview/what-is-new-and-different.md)
* Adobe Experience Manager as a Cloud Service [아키텍처](/help/core-concepts/architecture.md)
* [AEM as a Cloud Service에 대한 주목할 만한 변경 사항(릴리스 노트)](/help/release-notes/aem-cloud-changes.md)
* [AEM Assets as a Cloud Service에 대한 주요 변경 사항](/help/assets/assets-cloud-changes.md)
* [AEM Assets as a Cloud Service 소개](/help/assets/overview.md)
* [Adobe Experience Manager as a Cloud Service 자습서](https://docs.adobe.com/content/help/ko-KR/experience-manager-learn/cloud-service/overview.html)


Cloud Service 로서 AEM Sites의 변경 사항 및 추가 사항은 다음과 같습니다.

* [비동기 페이지 작업](#asynchronous-page-operations)
* [새 참조 사이트 및 자습서](#new-reference-site-and-tutorial)

## 비동기 페이지 작업 {#asynchronous-page-operations}

AEM 클라우드 서비스에서는 일반적으로 UI를 차단한 작업이 백그라운드에서 실행되는 작은 작업으로 구분되었습니다.

* 페이지 이동
* 페이지 롤아웃

이러한 작업의 개시자는 새 UI에서 `/mnt/overlay/dam/gui/content/asyncjobs.html`의 상태를 확인할 수 있습니다.

>[!NOTE]
이 새 기능을 사용하기 위해 시스템 사용자가 변경할 필요가 없습니다. 여기서는 AEM의 이전 온-프레미스 버전에서의 동작 변화만 간단히 설명합니다.

## 새 참조 사이트 및 자습서 {#new-reference-site-and-tutorial}

[새 AEM 참조 사이트인](https://wknd.site/) WKND가 AEM으로 웹 사이트를 구축하는 모범 사례와 AEM에서 사용할 수 있는 포괄적인 기능, 구성 요소 및 배포 모델 세트를 반영하도록 업데이트 및 게시되었습니다. 새 참조 사이트 및 [추가 자습서](https://docs.adobe.com/content/help/en/experience-manager-learn/getting-started-wknd-tutorial-develop/overview.html)에서는 프로젝트 설정, 핵심 구성 요소, 편집 가능한 템플릿, 클라이언트 라이브러리 및 Adobe Experience Manager Sites을 사용한 구성 요소 개발과 같은 기본 주제를 다룹니다.

이전에는 AEM에서 기본적으로 We.Retail을 설치했지만(프로덕션 모드에서 시작하는 경우 제외)  이제 참조 사이트는 기본적으로 앞으로 설치되지 않습니다.  대신 업데이트된 WKND 참조 사이트 코드와 함께 [git repo](https://github.com/adobe/aem-guides-wknd/) 및 [함께 자습서](https://docs.adobe.com/content/help/en/experience-manager-learn/getting-started-wknd-tutorial-develop/overview.html)가 제공됩니다.

## 런타임 {#capabilities-not-available-at-runtime}에서 기능을 사용할 수 없습니다.

AEM as a Cloud Service은 항상 켜져 있으며 항상 최신 상태입니다. 이를 위해서는 변경할 수 없는 컨텐츠와 변경할 수 없는 컨텐츠로 AEM 리포지토리를 분리해야 하며 런타임 시 변경할 수 없는 컨텐츠에 대한 액세스를 금지해야 합니다. 변경할 수 있는 컨텐츠와 변경할 수 없는 컨텐츠에 대한 자세한 내용은 [변경할 수 있는 영역과 저장소의 변경할 수 없는 영역을 참조하십시오](/help/implementing/developing/introduction/aem-project-content-package-structure.md#mutable-vs-immutable).

런타임 시 변경할 수 없는 컨텐츠에 액세스할 수 없기 때문에 런타임 시 다음 AEM Sites 작업을 사용할 수 없습니다.

* i18n 사전 번역
* AEM Sites 페이지 편집기의 개발자 모드

이러한 기능은 AEM as a Cloud Service의 로컬 독립 실행형 개발자 인스턴스를 통해 AEM에서 Cloud Service GIT 리포지토리로서 컨텐츠 및 코드를 업데이트하기 위해 사용할 수 있지만 호스팅된 런타임 인스턴스에는 사용할 수 없습니다.
