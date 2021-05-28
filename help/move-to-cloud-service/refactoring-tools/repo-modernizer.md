---
title: Repository Modernizer
description: Repository Modernizer
exl-id: b89156a8-3d7d-4d36-89a2-beeda35bbc01
source-git-commit: 856266faf4cb99056b1763383d611e9b2c3c13ea
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 1%

---

# Repository Modernizer {#repo-modernizer}

Repository Modernizer는 Adobe Experience Manager에 대해 정의된 Cloud Service 구조와 호환될 수 있도록 컨텐츠와 코드를 개별 패키지로 분리하여 기존 프로젝트 패키지를 재구성할 수 있도록 개발된 유틸리티입니다.

## 소개 {#introduction}

Adobe Experience Manager as a Cloud Service은 AEM 프로젝트에 많은 새로운 기능과 가능성을 제공합니다. 그러나 AEM Cloud Service과 호환되도록 Adobe Experience Manager Maven 프로젝트에 필요한 몇 가지 변경 사항이 있습니다. 높은 수준에서 AEM은 가변 콘텐츠와 변경할 수 없는 컨텐츠 간의 분할을 준수하기 위해 **content** 및 **code**&#x200B;을 별도의 하위 패키지로 분리해야 합니다. Cloud Service에 대한 새 AEM 프로젝트 구조에 대한 자세한 내용은 [AEM 프로젝트 구조](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/aem-project-content-package-structure.html)를 참조하십시오.

Repository Modernizer는 다음 배포 구조를 만들어 호환되는 AEM Cloud Service 프로젝트 구조를 만듭니다.

* `ui.apps` 패키지가 에 배포되고  `/apps` 모든 코드를 포함합니다.

* `ui.content` 패키지는 런타임 쓰기 가능 영역에 배포됩니다(예: `/content`,  `/conf`,  `/home`또는 와 관련되지 않은 모든  `/apps`)이며 모든 컨텐츠 및 구성을 포함합니다.

* `all` 패키지는 하위 패키지  `ui.apps` 및  `ui.content`를 포함하는 컨테이너 패키지입니다.

>[!NOTE]
>프로젝트 구조는 패키지 및 `pom.xml/filter.xml files`에 대한 *Archetype 24*&#x200B;을 기반으로 합니다. 자세한 내용은 [Archetype 24](https://github.com/adobe/aem-project-archetype)을 참조하십시오.

## Repository Modernizer {#using-repo-modernizer} 사용

>[!VIDEO](https://video.tv.adobe.com/v/333057/?quality=12&learn=on)

* Adobe I/O CLI 를 통해 :`aio-cli-plugin-aem-cloud-service-migration`(AEM을 Adobe I/O CLI용 Cloud Service 코드 리팩터링 플러그인으로 사용)을 통해 Repository Modernizer를 사용하는 것이 좋습니다.

   **[Git 리소스 를 참조하십시오.aio-cli-plugin-aem-cloud-service-migration](https://github.com/adobe/aio-cli-plugin-aem-cloud-service-migration#introduction)** 플러그인을 설치하고 사용하는 방법을 알아봅니다.

* 독립형 유틸리티 :Repository Modernizer를 독립형 유틸리티로도 실행할 수 있습니다.

   **[Git 리소스 를 참조하십시오.Repository Modernizer](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/repository-modernizer)** 를 사용하여 이 도구를 사용하는 방법을 알아봅니다.

   >[!NOTE]
   >
   >Repository Modernizer는 NodeJS를 사용하여 개발됩니다. NodeJS 10.0 이상을 설치하는 것이 좋습니다.
