---
title: Vanilla JS를 사용한 콘텐츠 조각 선택기 통합
description: 컨텐츠 조각 선택기를 다양한 Adobe, 비 Adobe 및 타사 애플리케이션과 통합합니다.
role: Admin, User, Developer
source-git-commit: 592e443928f2c9c18ac281027026132b1c877ce3
workflow-type: tm+mt
source-wordcount: '135'
ht-degree: 2%

---

# Vanilla JS를 사용한 콘텐츠 조각 선택기 통합 {#integrate-content-fragment-selector-using-vanilla-js}

Adobe 또는 Adobe이 아닌 애플리케이션을 Adobe Experience Manager(AEM) as a Cloud Repository와 통합하고 해당 애플리케이션 내에서 컨텐츠 조각을 선택할 수 있습니다.

통합은 콘텐츠 조각 선택기 패키지를 가져와서 바닐라 JavaScript 라이브러리를 사용하여 AEM as a Cloud Service에 연결함으로써 수행됩니다. `index.html` 또는 응용 프로그램 내의 적절한 파일을 편집하여 다음 작업을 수행합니다.

* 인증 세부 정보 정의
* AEM as a Cloud Service 저장소 액세스
* 콘텐츠 조각 선택기 표시 속성 구성

다음과 같은 경우 IMS 속성 중 일부를 정의하지 않고 인증을 수행할 수 있습니다.

* [통합 셸](https://experienceleague.adobe.com/ko/docs/experience-manager-cloud-service/content/overview/aem-cloud-service-on-unified-shell)에서 Adobe 응용 프로그램을 통합 중입니다.
* 이미 인증을 위해 생성된 IMS 토큰이 있습니다.
