---
title: AEM 클라우드 서비스의 AEM 사이트에 대한 주요 변경 사항
description: 'AEM 클라우드 서비스의 AEM 사이트에 대한 주요 변경 사항 '
translation-type: tm+mt
source-git-commit: e381807d7c199113689304e9481dfe2022ee5f93
workflow-type: tm+mt
source-wordcount: '538'
ht-degree: 21%

---


# AEM Sites as a Cloud Service에 대한 주요 변경 사항 {#notable-changes}

Cloud Service의 AEM Sites은 Cloud Service 플랫폼으로서 클라우드 기반의 AEM에 포함된 경험 관리 기능을 제공합니다. 클라우드 기본 확장성, 가동 시간, 항상 최신 상태로 유지 등 Cloud Service로서 AEM의 주요 이점뿐만 아니라 Cloud Service의 AEM Sites은 다양한 사이트 관련 변경 사항 및 추가 사항을 제공합니다.

>[!NOTE]
>이 문서에서는 AEM Sites의 주목할 만한 변경 사항을 집중적으로 설명합니다. Cloud Service 및 기타 모듈로서 AEM에 대한 일반적인 변경 사항은 다음을 참조하십시오.
>
>* [Adobe Experience Manager as a Cloud Service 소개](/help/overview/introduction.md)
>* [AEM as a Cloud Service에 대한 개요 - 새로운 기능 및 다른 기능](/help/overview/what-is-new-and-different.md)
>* Adobe Experience Manager as a Cloud Service [아키텍처](/help/core-concepts/architecture.md)
>* [AEM as a Cloud Service에 대한 주목할 만한 변경 사항(릴리스 노트)](/help/release-notes/aem-cloud-changes.md)
>* [AEM Assets as a Cloud Service에 대한 주요 변경 사항](/help/assets/assets-cloud-changes.md)
>* [Cloud Service으로 AEM Assets 소개](/help/assets/overview.md)
>* [Adobe Experience Manager as a Cloud Service 자습서](https://docs.adobe.com/content/help/ko-KR/experience-manager-learn/cloud-service/overview.html)


Cloud Service의 변경 사항 및 추가 사항은 다음과 같습니다.

* [비동기 페이지 작업](#asynchronous-page-operations)
* [새로운 참조 사이트 및 자습서](#new-reference-site-and-tutorial)

## 비동기 페이지 작업 {#asynchronous-page-operations}

AEM Cloud 서비스에서 일반적으로 UI를 차단하는 작업은 백그라운드에서 실행되는 작은 작업으로 분류됩니다.

* 페이지 이동
* 롤아웃 페이지

이러한 작업의 개시자는 `/mnt/overlay/dam/gui/content/asyncjobs.html`의 새 UI에서 자신의 상태를 확인할 수 있습니다.

>[!NOTE]
>
>이 새 기능을 사용하기 위해 시스템 사용자가 변경할 필요가 없습니다. 여기에서는 AEM의 이전 온-프레미스 버전과의 비헤이비어의 변화라고 간단히 언급됩니다.

## 새 참조 사이트 및 자습서 {#new-reference-site-and-tutorial}

[새로운 AEM 참조 사이트](https://wknd.site/) WKND는 AEM을 사용하여 웹 사이트를 구축하는 모범 사례와 AEM에서 사용할 수 있는 포괄적인 기능, 구성 요소 및 배포 모델 세트를 반영하도록 업데이트 및 게시되었습니다. 새 참조 사이트 및 [관련 자습서](https://docs.adobe.com/content/help/en/experience-manager-learn/getting-started-wknd-tutorial-develop/overview.html)에서는 Adobe Experience Manager Sites을 사용한 프로젝트 설정, 핵심 구성 요소, 편집 가능한 템플릿, 클라이언트 라이브러리 및 구성 요소 개발과 같은 기본 주제를 다룹니다.

이전에는 We.Retail이 기본적으로 AEM과 함께 설치되었습니다(프로덕션 모드에서 시작한 경우 제외).  이제 앞으로 기본적으로 참조 사이트가 설치되지 않습니다.  대신 업데이트된 WKND 참조 사이트 코드와 함께 [git 보고서](https://github.com/adobe/aem-guides-wknd/) 및 [관련 자습서](https://docs.adobe.com/content/help/en/experience-manager-learn/getting-started-wknd-tutorial-develop/overview.html)가 제공됩니다.

## 런타임 {#capabilities-not-available-at-runtime}에서 기능을 사용할 수 없습니다.

AEM은 항상 켜져 있으며 항상 최신 상태로 유지됩니다. 이를 수행하려면 변경 불가하고 변경 가능한 컨텐츠로 AEM 저장소를 분리해야 하며 런타임 시 변경할 수 없는 컨텐츠에 대한 액세스를 금지해야 합니다. 변경 가능한 컨텐츠와 변경 불가능한 컨텐츠에 대한 자세한 내용은 [변경 가능한 영역과 저장소의 변경 불가능한 영역 비교](/help/implementing/developing/introduction/aem-project-content-package-structure.md#mutable-vs-immutable)를 참조하십시오.

런타임 시 변경할 수 없는 컨텐츠를 액세스할 수 없기 때문에 런타임 시 다음 AEM Sites 작업을 사용할 수 없습니다.

* i18n 사전 번역
* AEM Sites 페이지 편집기의 개발자 모드

이러한 기능은 AEM의 로컬 독립 실행형 개발자 인스턴스를 Cloud Service으로 사용하여 AEM의 컨텐츠 및 코드를 Cloud Service GIT 리포지토리로 업데이트하는 데 사용할 수 있지만 호스팅된 런타임 인스턴스에는 사용할 수 없습니다.
