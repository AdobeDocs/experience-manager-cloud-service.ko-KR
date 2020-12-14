---
title: 저장소 현대화 프로그램
description: 저장소 현대화 프로그램
translation-type: tm+mt
source-git-commit: 5da0d4cc8c6d8781dd7cce8bbbde207568a6d10b
workflow-type: tm+mt
source-wordcount: '301'
ht-degree: 4%

---


# 저장소 현대화 프로그램 {#repo-modernizer}

Repository Modernizer는 Adobe Experience Manager에 대해 Cloud Service으로 정의된 프로젝트 구조와 호환되도록 컨텐츠와 코드를 개별 패키지로 구분하여 기존 프로젝트 패키지를 재구성할 수 있도록 개발된 유틸리티입니다.

## 소개 {#introduction}

Adobe Experience Manager은 Cloud Service으로 AEM 프로젝트에 다양한 새로운 기능과 가능성을 제공합니다. 그러나 AEM Cloud Service과 호환되도록 Adobe Experience Manager Maven 프로젝트에 몇 가지 변경이 필요합니다. 높은 수준의 AEM에서는 변경할 수 없는 컨텐츠와 변경할 수 없는 컨텐츠 간의 분할을 준수하기 위해 **content** 및 **code**&#x200B;를 개별 하위 패키지로 구분해야 합니다. Cloud Service에 대한 새 AEM 프로젝트 구조에 대한 자세한 내용은 [AEM 프로젝트 구조](https://docs.adobe.com/content/help/ko-KR/experience-manager-cloud-service/implementing/developing/aem-project-content-package-structure.html)를 참조하십시오.

Repository Modernizer는 다음 배포 구조를 생성하여 호환되는 AEM Cloud Service 프로젝트 구조를 생성합니다.

* `ui.apps` 패키지 배포  `/apps` 및 모든 코드 포함

* `ui.content` 런타임 쓰기 가능 영역에 패키지 배포(예: `/content`,  `/conf`또는  `/home`  `/apps`기타)를 포함하고 모든 컨텐트 및 구성을 포함합니다.

* `all` package는 하위 패키지 `ui.apps` 와 `ui.content`를 포함하는 컨테이너 패키지입니다.

>[!NOTE]
>프로젝트 구조는 패키지 및 `pom.xml/filter.xml files`에 대한 *Receype 24*&#x200B;을 기반으로 합니다. 자세한 내용은 [원형 24](https://github.com/adobe/aem-project-archetype)을 참조하십시오.

## 저장소 현대화 사용 {#using-repo-modernizer}

* Adobe I/O CLI 사용:Repository Modernizer를 `aio-cli-plugin-aem-cloud-service-migration`(Adobe I/O CLI용 Cloud Service 코드 리팩토링 플러그인으로 AEM)을 통해 사용하는 것이 좋습니다.

   **[Git 리소스를 참조하십시오.aio-cli-plugin-aem-cloud-service-migration](https://github.com/adobe/aio-cli-plugin-aem-cloud-service-migration#introduction)** 플러그인을 설치하고 사용하는 방법에 대해 학습합니다.

* 독립 실행형 유틸리티로:Repository Modernizer를 독립형 유틸리티로 실행할 수도 있습니다.

   **[Git 리소스를 참조하십시오.저장소 현대화 프로그램](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/repository-modernizer)**&#x200B;에서 이 도구를 사용하는 방법을 알아보십시오.

   >[!NOTE]
   >
   >Repository Modernizer는 NodeJS를 사용하여 개발되었습니다. NodeJS 10.0+를 설치하는 것이 좋습니다.
