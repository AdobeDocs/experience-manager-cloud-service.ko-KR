---
title: 저장소 현대화 도구
description: 저장소 현대화 도구
exl-id: cd9d212e-e720-4209-8b5a-659883cc1d95
source-git-commit: 92c123817a654d0103d0f7b8e457489d9e82c2ce
workflow-type: tm+mt
source-wordcount: '303'
ht-degree: 6%

---

# 저장소 현대화 도구 {#repo-modernizer}

Repository Modernizer 는 Adobe Experience Manager as a Cloud Service에 대해 정의된 프로젝트 구조와 호환될 수 있도록 콘텐츠와 코드를 개별 패키지로 분리하여 기존 프로젝트 패키지를 재구성하도록 개발된 유틸리티입니다.

## 소개 {#introduction}

Adobe Experience Manager as a Cloud Service은 AEM 프로젝트에 많은 새로운 기능과 가능성을 제공합니다. 그러나 Adobe Experience Manager Maven 프로젝트가 AEM Cloud Service과 호환되도록 하려면 몇 가지 변경이 필요합니다. 높은 수준에서 AEM은 **콘텐츠** 및 **코드** 변경할 수 있는 컨텐츠와 변경할 수 없는 컨텐츠 간의 분할을 준수하도록 개별 하위 패키지로 변환합니다. 다음을 참조하십시오 [AEM 프로젝트 구조](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/aem-project-content-package-structure.html) 를 참조하십시오. Cloud Service을 위한 새 AEM 프로젝트 구조.

Repository Modernizer는 다음과 같은 배포 구조를 생성하여 호환되는 AEM Cloud Service 프로젝트 구조를 만듭니다.

* `ui.apps` 패키지 배포 위치 `/apps` 모든 코드를 포함

* `ui.content` 런타임 쓰기 가능 영역에 패키지 배포(예: `/content`, `/conf`, `/home`또는 기타 `/apps`) 모든 컨텐츠 및 구성을 포함합니다.

* `all` 패키지는 하위 패키지가 포함된 컨테이너 패키지입니다 `ui.apps` 및 `ui.content`.

>[!NOTE]
>프로젝트 구조는 다음을 기반으로 합니다 *Archetype 24* 패키지 및 해당 `pom.xml/filter.xml files`. 을(를) 참조하십시오 [Archetype 24](https://github.com/adobe/aem-project-archetype) 을 참조하십시오.

## Repository Modernizer 사용 {#using-repo-modernizer}

>[!VIDEO](https://video.tv.adobe.com/v/333057/?quality=12&learn=on)

* Adobe I/O CLI 를 통해 : 다음을 통해 Repository Modernizer를 사용하는 것이 좋습니다. `aio-cli-plugin-aem-cloud-service-migration` (Adobe I/O CLI용 AEM as a Cloud Service 코드 리팩터링 플러그인).

  다음을 참조하십시오 **[Git 리소스: aio-cli-plugin-aem-cloud-service-migration](https://github.com/adobe/aio-cli-plugin-aem-cloud-service-migration#introduction)** 따라서 플러그인을 설치하고 사용하는 방법을 배울 수 있습니다.

* 독립형 유틸리티로서 : Repository Modernizer를 독립형 유틸리티로 실행할 수도 있습니다.

  다음을 참조하십시오 **[Git 리소스: Repository Modernizer](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/repository-modernizer)** 이 도구를 사용하는 방법을 배울 수 있습니다.

  >[!NOTE]
  >
  >Repository Modernizer 는 NodeJS 를 사용하여 개발되었습니다. NodeJS 10.0+를 설치하는 것이 좋습니다.
