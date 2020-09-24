---
title: Repository Modernizer
description: Repository Modernizer
translation-type: tm+mt
source-git-commit: 5d2b14c827603297a59cba7180fc1a68de0c841a
workflow-type: tm+mt
source-wordcount: '301'
ht-degree: 4%

---


# Repository Modernizer {#repo-modernizer}

Repository Modernizer는 Adobe Experience Manager에 대해 Cloud Service으로 정의된 프로젝트 구조와 호환되도록 컨텐츠와 코드를 개별 패키지로 구분하여 기존 프로젝트 패키지를 재구성하는 데 사용되는 유틸리티입니다.

## 소개 {#introduction}

Cloud Service으로 자리매김한 Adobe Experience Manager은 AEM 프로젝트에 많은 새로운 기능과 가능성을 제공합니다. 하지만 Adobe Experience Manager 매번즈 프로젝트에 AEM Cloud Service과 호환되도록 몇 가지 변경이 필요합니다. 고품질의 AEM에서는 변경할 수 있는 컨텐츠와 변경할 수 없는 컨텐츠 간의 분할을 준수하기 위해 **컨텐츠** 및 **코드를 개별 하위 패키지로** 분리해야 합니다. Cloud Service의 새로운 AEM 프로젝트 구조에 대한 자세한 내용은 [AEM 프로젝트](https://docs.adobe.com/content/help/ko-KR/experience-manager-cloud-service/implementing/developing/aem-project-content-package-structure.html) 구조를 참조하십시오.

Repository Modernizer는 다음 배포 구조를 생성하여 호환되는 AEM Cloud Service 프로젝트 구조를 생성합니다.

* `ui.apps` 패키지 배포 후 모든 코드 `/apps` 를 포함

* `ui.content` 패키지 배포를 런타임 쓰기 가능 영역(예: `/content`, `/conf``/home`, or anything not `/apps`) and contains all the content and configuration.

* `all` 패키지 `ui.apps` `ui.content`는 하위 패키지 및

>[!NOTE]
>프로젝트 구조는 *Tranype 24* 패키지 및 패키지를 기반으로 `pom.xml/filter.xml files`합니다. 자세한 내용은 [원형 24를](https://github.com/adobe/aem-project-archetype) 참조하십시오.

## 저장소 현대화 사용 {#using-repo-modernizer}

* Adobe I/O CLI 사용:Adobe I/O CLI용 Cloud Service 코드 리팩토링 플러그인으로 `aio-cli-plugin-aem-cloud-service-migration` (AEM)을 통해 Repository Modernizer를 사용하는 것이 좋습니다.

   Git 리소스 **[를 참조하십시오.aio-cli-plugin-aem-cloud-service-migration](https://github.com/adobe/aio-cli-plugin-aem-cloud-service-migration#introduction)** to learn how to install and use the plugin.

* 독립형 유틸리티로,Repository Modernizer를 독립형 유틸리티로 실행할 수도 있습니다.

   Git 리소스 **[를 참조하십시오.Repository Modernizer](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/repository-modernizer)** 를 사용하여 이 도구를 사용하는 방법을 알아봅니다.

   >[!NOTE]
   >Repository Modernizer는 NodeJS를 사용하여 개발되었습니다. NodeJS 10.0+을 설치하는 것이 좋습니다.