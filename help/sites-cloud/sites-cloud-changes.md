---
title: AEM Cloud Service의 AEM Sites에 대한 주요 변경 내용
description: AEM Cloud Service의 AEM Sites에 대한 주요 변경 내용
exl-id: 60b1aec4-75a0-459f-bf77-8d8c1af757ce
source-git-commit: ab81bca96bcf06b06357f900464e999163bb1bb2
workflow-type: tm+mt
source-wordcount: '532'
ht-degree: 100%

---

# AEM Sites as a Cloud Service의 주요 변경 내용 {#notable-changes}

AEM Sites as a Cloud Service는 클라우드 기반 AEM as a Cloud Service 플랫폼의 일부로 경험 관리 기능을 제공합니다. 클라우드 기반 확장성, 가동 시간 및 최신 상태 유지와 같은 AEM as a Cloud Service의 핵심적인 이점 이외에도, AEM Sites as a Cloud Service는 다양한 사이트별 변경 내용 및 추가 사항을 제공합니다.

>[!NOTE]
>이 문서에서는 AEM Sites에 대한 주요 변경 내용을 조명합니다. AEM as a Cloud Service 및 기타 모듈에 대한 일반적인 변경 내용은 다음을 참조하십시오.
>
>* [Adobe Experience Manager as a Cloud Service 소개](/help/overview/introduction.md)
>* [AEM as a Cloud Service 개요 - 새로운 기능 및 차이점](/help/overview/what-is-new-and-different.md)
>* Adobe Experience Manager as a Cloud Service [아키텍처](/help/overview/architecture.md)
>* [AEM as a Cloud Service에 대한 주목할 만한 변경 사항 (릴리스 정보)](/help/release-notes/aem-cloud-changes.md)
>* [AEM Assets as a Cloud Service에 대한 주요 변경 내용](/help/assets/assets-cloud-changes.md)
>* [AEM Assets as a Cloud Service 소개](/help/assets/overview.md)
>* [Adobe Experience Manager as a Cloud Service 튜토리얼](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/overview.html)


AEM Sites as a Cloud Service에 대한 변경 내용 및 추가 사항은 다음과 같습니다.

* [비동기 페이지 작업](#asynchronous-page-operations)
* [새로운 참조 사이트 및 튜토리얼](#new-reference-site-and-tutorial)

## 비동기 페이지 작업 {#asynchronous-page-operations}

AEM Cloud service에서는 전통적으로 UI를 차단하는 작업이 백그라운드에서 실행되는 더 작은 작업으로 분류되었습니다.

* 페이지 이동
* 페이지 롤아웃

이러한 작업의 개시자는 `/mnt/overlay/dam/gui/content/asyncjobs.html`의 새로운 UI에서 이들의 상태를 확인할 수 있습니다.

>[!NOTE]
>
>시스템 사용자는 이 새로운 기능을 사용하기 위해 변경 작업을 수행할 필요가 없습니다. 이는 AEM의 이전 온프레미스 버전의 비헤이비어에 대한 변경 내용으로 기재되어 있습니다.

## 새로운 참조 사이트 및 튜토리얼 {#new-reference-site-and-tutorial}

새로운 AEM 참조 사이트인 [WKND](https://wknd.site/)는 AEM을 통해 웹 사이트를 구축하기 위한 모범 사례와 AEM에서 사용할 수 있는 포괄적인 기능, 구성 요소 및 배포 모델의 세트를 반영하도록 업데이트 및 게시되었습니다. 새로운 참조 사이트 및 [함께 제공되는 튜토리얼](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/overview.html)은 Adobe Experience Manager Sites를 통한 사용한 프로젝트 설정, 핵심 구성 요소, 편집 가능한 템플릿, 클라이언트 라이브러리 및 구성 요소 개발 등의 기본 주제를 다룹니다.

이전에는 We.Retail이 기본적으로 AEM을 통해 설치되었습니다(프로덕션 모드로 시작하는 경우 제외). 이제는 참조 사이트가 기본적으로 설치되지 않습니다. 대신 [git 저장소](https://github.com/adobe/aem-guides-wknd/) 및 [함께 제공되는 튜토리얼](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/overview.html)이 업데이트된 WKND 참조 사이트 코드와 함께 제공됩니다.

## 런타임 시 사용할 수 없는 기능 {#capabilities-not-available-at-runtime}

AEM as a Cloud Service는 항상 활성화되어 있으며 최신 상태로 유지됩니다. 이를 위해서는 AEM 저장소를 변경 불가능한 콘텐츠와 변경 가능한 콘텐츠로 분리하고 런타임 시 변경 불가능한 콘텐츠에 대한 액세스를 금지해야 합니다. 변경 가능한 콘텐츠 및 변경 불가능한 콘텐츠에 대한 자세한 내용은 [저장소의 변경 가능한 영역 및 변경 불가능한 영역](/help/implementing/developing/introduction/aem-project-content-package-structure.md#mutable-vs-immutable)을 참조하십시오.

런타임 시 변경 불가능한 콘텐츠에 액세스할 수 없으므로, 다음 AEM Sites 작업도 런타임 시 사용할 수 없게 됩니다.

* i18n 사전 번역
* AEM Sites 페이지 편집기의 개발자 모드

이들 기능은 AEM as a Cloud Service 독립형 로컬 개발자 인스턴스를 통해 사용하여 AEM as a Cloud Service GIT 저장소의 콘텐츠 및 코드를 업데이트할 수 있지만, 호스팅된 런타임 인스턴스에서는 사용할 수 없습니다.
