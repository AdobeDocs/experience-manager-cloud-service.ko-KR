---
title: Universal Editor 인증
description: Universal Editor가 인증을 위해 Adobe의 Identity Management System(IMS)을 사용하는 방법에 대해 알아봅니다.
exl-id: fb86c510-3c41-4511-81b7-1bdf2f5e7dd3
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 646ca4f4a441bf1565558002dcd6f96d3e228563
workflow-type: tm+mt
source-wordcount: '178'
ht-degree: 100%

---


# Universal Editor 인증 {#authentication}

Universal Editor의 인증 방법을 알아봅니다.

## 옵션 {#options}

Universal Editor는 통합 셸을 통해 제공되는 Adobe의 Identity Management System(IMS) 인증을 사용합니다.

모든 애플리케이션/원격 페이지는 필수 백엔드 시스템에 대한 인증을 담당합니다. Universal Editor 서비스는 독립 실행형 서비스이므로 CRUD 작업을 수행하려면 백엔드 시스템에 대한 이 인증이 필요합니다.

## 표준 흐름 {#standard-flow}

AEM as a Cloud Service 및 IMS 사용 AMS에서 Universal Editor를 사용하기 위한 솔루션입니다.

Universal Editor를 사용하려면 사용자가 IMS에 대해 인증하는 통합 셸에 로그인해야 합니다. 제공된 IMS 토큰은 사용자 세션 저장소에 저장됩니다.

사용자가 CRUD 작업을 수행할 때마다 HTTP 헤더의 IMS 전달자 토큰과 함께 Universal Editor 서비스로 호출이 전송됩니다. 그런 다음 Universal Editor 서비스는 전달자 토큰을 사용해 AEM 백엔드 시스템에 대한 요청을 인증하여 사용자 이름으로 작업을 실행합니다.

![표준 인증 흐름](assets/standard-flow.png)
