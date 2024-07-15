---
title: 저장소 현대화 도구
description: 기존 프로젝트 패키지를 재구성하고 Adobe Experience Manager as a Cloud Service에 대해 정의된 프로젝트 구조와 호환되도록 하는 방법에 대해 알아봅니다.
exl-id: cd9d212e-e720-4209-8b5a-659883cc1d95
feature: Migration
role: Admin
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '304'
ht-degree: 2%

---

# 저장소 현대화 도구 {#repo-modernizer}

Repository Modernizer 는 Adobe Experience Manager as a Cloud Service에 대해 정의된 프로젝트 구조와 호환될 수 있도록 콘텐츠와 코드를 개별 패키지로 분리하여 기존 프로젝트 패키지를 재구성하도록 개발된 유틸리티입니다.

## 소개 {#introduction}

Adobe Experience Manager as a Cloud Service은 AEM 프로젝트에 많은 새로운 기능과 가능성을 제공합니다. 그러나 Adobe Experience Manager Maven 프로젝트가 AEM Cloud Service과 호환되도록 하려면 몇 가지 변경이 필요합니다. 높은 수준에서 AEM은 변경 가능한 콘텐츠와 변경 불가능한 콘텐츠 사이의 분할을 준수하도록 **콘텐츠**&#x200B;와(과) **코드**&#x200B;을(를) 개별 하위 패키지로 분리해야 합니다. Cloud Service을 위한 새 AEM 프로젝트 구조에 대한 자세한 내용은 [AEM 프로젝트 구조](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/aem-project-content-package-structure.html)를 참조하십시오.

Repository Modernizer는 다음과 같은 배포 구조를 생성하여 호환되는 AEM Cloud Service 프로젝트 구조를 만듭니다.

* `ui.apps` 패키지가 `/apps`에 배포되고 모든 코드를 포함합니다.

* `ui.content` 패키지가 런타임 쓰기 가능 영역(예: `/content`, `/conf`, `/home` 또는 `/apps`이(가) 아닌 모든 영역)에 배포되며 모든 콘텐츠 및 구성을 포함합니다.

* `all` 패키지는 하위 패키지 `ui.apps` 및 `ui.content`이(가) 포함된 컨테이너 패키지입니다.

>[!NOTE]
>프로젝트 구조는 패키지 및 해당 `pom.xml/filter.xml files`의 *Archetype 24*&#x200B;을(를) 기반으로 합니다. 자세한 내용은 [Archetype 24](https://github.com/adobe/aem-project-archetype)을(를) 참조하십시오.

## Repository Modernizer 사용 {#using-repo-modernizer}

>[!VIDEO](https://video.tv.adobe.com/v/333057/?quality=12&learn=on)

* Adobe I/O CLI 방법 : Adobe은 `aio-cli-plugin-aem-cloud-service-migration`을(를) 통해 Repository Modernizer 사용(Adobe I/O CLI의 경우 AEM as a Cloud Service 코드 리팩터링 플러그인)을 권장합니다.

  플러그인을 설치하고 사용하는 방법을 배울 수 있도록 **[Git 리소스: aio-cli-plugin-aem-cloud-service-migration](https://github.com/adobe/aio-cli-plugin-aem-cloud-service-migration#introduction)**&#x200B;을(를) 참조하십시오.

* 독립형 유틸리티로서 : Repository Modernizer를 독립형 유틸리티로 실행할 수도 있습니다.

  이 도구의 사용 방법을 배울 수 있도록 **[Git 리소스: Repository Modernizer](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/repository-modernizer)**&#x200B;를 참조하십시오.

  >[!NOTE]
  >
  >Repository Modernizer 는 NodeJS 를 사용하여 개발되었습니다. NodeJS 10.0+를 설치하는 것이 좋습니다.
