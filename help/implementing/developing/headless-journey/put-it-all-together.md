---
title: 모든 것을 하나로 통합하는 방법 - AEM 헤드리스에서 앱과 콘텐츠를
description: AEM 헤드리스 개발자 여정의 이 부분에서 컨텐츠 조각, GraphQL 호출, REST API 호출 및 애플리케이션을 비롯한 AEM 프로젝트를 가져와 라이브할 수 있도록 준비하는 방법을 살펴봅니다.
hide: true
hidefromtoc: true
index: false
exl-id: 254fb9dd-36c8-43ce-aaea-ceb4d079503d
source-git-commit: 0960c354eb9a5156d9200b2c6f54761f1a8383a2
workflow-type: tm+mt
source-wordcount: '308'
ht-degree: 0%

---

# 모든 것을 통합하는 방법 - AEM 헤드리스 {#put-it-all-together}에서 앱과 콘텐츠를

>[!CAUTION]
>
>진행 중인 작업 - 이 문서의 작성은 진행 중이며 완전한 또는 최종적인 것으로 해석되거나 제작 목적으로 사용되어서는 안 됩니다.

[AEM 헤드리스 개발자 여정의 이 부분에서는 ](overview.md) 컨텐츠 조각, GraphQL 호출, REST API 호출 및 애플리케이션을 포함하여 AEM 프로젝트를 가져와 라이브되도록 준비하는 방법을 알아봅니다.

## 지금까지 스토리 {#story-so-far}

AEM 헤드리스 여정의 이전 문서에서, [AEM Assets API를 통해 컨텐츠를 업데이트하는 방법](update-your-content.md) API를 통해 AEM에서 기존 헤드리스 컨텐츠를 업데이트하는 방법을 학습했고 이제 다음을 수행해야 합니다.

* AEM Assets HTTP API를 이해합니다.

이 문서는 이러한 기본 사항을 바탕으로 작성되므로 AEM 헤드리스 프로젝트를 라이브할 수 있도록 준비하는 방법을 이해할 수 있습니다.

## 목표 {#objective}

* AEM의 로컬 개발 워크플로우란 무엇입니까?
* AEM SDK를 설치하여 컨텐츠를 테스트하는 데 사용할 수 있는 로컬 개발 런타임을
* 로컬 개발 런타임 외에 작업하는 데 필요한 개발 툴에 대해 알아봅니다.

## 다음 {#what-is-next} 소개

AEM 헤드리스 프로젝트를 라이브로 촬영하는 [헤드리스 응용 프로그램을 사용하여 라이브하는 방법](go-live.md) 문서를 다시 검토하여 AEM 헤드리스 여정을 계속 진행해야 합니다!

## 추가 리소스 {#additional-resources}

* [로컬 개발 환경 설정](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/overview.html?lang=en#local-dispatcher-runtime)  - AEM용 개발을 시작하는 데 필요한 도구를 설치하는 방법을 알아봅니다.
* [AEM을 Cloud Service SDK로](/help/implementing/developing/introduction/aem-as-a-cloud-service-sdk.md)  사용 - AEM SDK에 대해 자세히 살펴보십시오