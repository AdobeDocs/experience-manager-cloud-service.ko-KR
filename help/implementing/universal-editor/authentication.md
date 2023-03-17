---
title: 범용 편집기 인증
description: 유니버설 편집기가 인증되는 방법을 알아봅니다.
source-git-commit: f454475b65da8f410812bbbe30ca5fc393be410a
workflow-type: tm+mt
source-wordcount: '339'
ht-degree: 0%

---


# 범용 편집기 인증 {#authentication}

유니버설 편집기가 인증되는 방법을 알아봅니다.

## 옵션 {#options}

범용 편집기는 통합 셸을 통해 제공되는 Adobe의 Identity Management 시스템(IMS) 인증을 사용합니다.

모든 애플리케이션/원격 페이지는 필수 백엔드 시스템에 대한 인증을 담당합니다. CRUD 작업은 독립형 서비스이므로 유니버설 편집기 서비스에는 백엔드 시스템에 이 인증이 필요합니다.

범용 편집기를 사용하는 방식에 따라 다양한 구현 옵션이 있습니다.

* [표준 흐름](#standard-flow) - IMS를 사용하는 AEM as a Cloud Service 또는 AMS의 경우
* [타사 흐름](#third-party-flow) - AEM 온-프레미스 또는 IMS가 없는 AMS의 경우

## 표준 흐름 {#standard-flow}

IMS를 사용하여 범용 편집기를 사용하는 AEM as a Cloud Service 및 AMS를 위한 솔루션입니다.

범용 편집기를 사용하려면 사용자가 IMS에 대해 인증을 받는 통합 셸에 로그인해야 합니다. 제공된 IMS 토큰은 사용자 세션 저장소에 저장됩니다.

사용자가 CRUD 작업을 수행할 때마다 HTTP 헤더에서 IMS 베어러 토큰을 사용하여 유니버설 편집기 서비스로 호출이 전송됩니다. 그런 다음 범용 편집기 서비스는 베어러 토큰을 사용하여 AEM 백엔드 시스템에 대한 요청을 인증하여 사용자 이름에 있는 작업을 실행합니다.

![표준 인증 흐름](assets/standard-flow.png)

## 추가 리소스 {#additional-resources}

범용 편집기에 대한 자세한 내용은 다음 문서를 참조하십시오.

* [범용 편집기 소개](introduction.md) - 범용 편집기를 사용하면 모든 구현에서 컨텐츠의 모든 측면을 편집할 수 있어 뛰어난 경험을 제공하고 컨텐츠 속도를 높이며 최신 개발자 경험을 제공할 수 있습니다.
* [범용 편집기를 사용하여 컨텐츠 작성](authoring.md) - 컨텐츠 작성자가 범용 편집기를 사용하여 컨텐츠를 만드는 것이 얼마나 쉽고 직관적인지를 알아봅니다.
* [AEM에서 범용 편집기 시작하기](getting-started.md) - 범용 편집기에 액세스하는 방법과 첫 번째 AEM 앱 계측을 시작하여 이를 사용하는 방법을 알아봅니다.
* [범용 편집기 아키텍처](architecture.md) - 범용 편집기의 아키텍처와 서비스 및 레이어 간에 데이터가 어떻게 이동되는지 알아봅니다.
* [속성 및 유형](attributes-types.md) - 범용 편집기에 필요한 데이터 속성 및 유형에 대해 알아봅니다.
