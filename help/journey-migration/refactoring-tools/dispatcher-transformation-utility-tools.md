---
title: AEM Dispatcher 변환기 도구
description: AEM Dispatcher의 기존 구성을 AEM as a Cloud Service Dispatcher의 구성으로 변환하는 방법에 대해 알아봅니다.
exl-id: 2e95ff7b-cc94-477d-99ab-816a58998287
source-git-commit: f7ffe727ecc7f1331c1c72229a5d7f940070c011
workflow-type: tm+mt
source-wordcount: '330'
ht-degree: 28%

---

# AEM Dispatcher 변환기 {#introduction}

>[!CONTEXTUALHELP]
>id="aemcloud_nonbpa_dispconverter"
>title="AEM Dispatcher 변환기"
>abstract="Adobe Experience Manager Dispatcher 변환기는 기존 AEM Dispatcher의 구성을 AEM as a Cloud Service Dispatcher로 변환해 줍니다."

Adobe Experience Manager Dispatcher 변환기는 기존 AEM Dispatcher의 구성을 AEM as a Cloud Service Dispatcher로 변환해 줍니다.

## Dispatcher 소개 {#introduction-dispatcher}

Dispatcher는 Adobe Experience Manager의 캐싱, 또는 로드 밸런싱 또는 둘 다입니다. AEM의 Dispatcher를 사용하면 AEM 서버를 공격으로부터 보호할 수 있습니다. 따라서 Dispatcher를 엔터프라이즈급 웹 서버와 함께 사용하여 AEM 인스턴스의 보안을 강화할 수 있습니다.

>[!NOTE]
>Dispatcher의 가장 일반적인 사용은 **AEM 게시 인스턴스**&#x200B;의 응답을 캐시하여 외부에서 게시되는 웹 사이트의 응답성과 보안을 향상시키는 것입니다.

다음을 참조하십시오 [Dispatcher 개요](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/dispatcher.html) dispatcher가 캐싱을 수행하는 방법을 알아보려면 문서를 반환하고 로드 밸런싱을 수행합니다.

### Apache 및 Dispatcher 구성과 테스트 {#dispatcher-configurations-cloud}

클라우드 환경에 배포하기 전에 AEM as a Cloud Service Apache 및 Dispatcher 구성을 구성하는 방법과 이를 로컬에서 확인하고 실행하는 방법을 알아봅니다.

다음을 참조하십시오 [클라우드의 디스패처](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/content-delivery/disp-overview.html) 추가 정보.

## AEM Dispatcher 변환기 {#aem-dispatcher-converter}

AEM Dispatcher Converter 는 기존 온-프레미스 또는 Adobe Managed Services AEM Dispatcher 구성을 as a Cloud Service 호환 Dispatcher 구성으로 리팩터링하는 기능을 제공합니다.

## AEM Dispatcher 변환기 사용 {#using-dispatcher-converter}

* Adobe Developer CLI 의 방법 : Adobe은 의 방법으로 AEM Dispatcher Converter 를 사용할 것을 권장합니다. `aio-cli-plugin-aem-cloud-service-migration` (Adobe Developer CLI용 AEM as a Cloud Service 코드 리팩터링 플러그인).

  다음을 참조하십시오 **[Git 리소스: aio-cli-plugin-aem-cloud-service-migration](https://github.com/adobe/aio-cli-plugin-aem-cloud-service-migration#introduction)** 따라서 플러그인을 설치하고 사용하는 방법을 배울 수 있습니다.

* 독립형 유틸리티로 : AEM Dispatcher 변환기 도구를 독립형 유틸리티로 실행할 수도 있습니다.

  다음을 참조하십시오 **[Git 리소스: AEM Cloud Service Dispatcher 변환기](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/dispatcher-converter)** 따라서 이 도구의 사용 및 문제 해결에 대해 알아볼 수 있습니다.

>[!IMPORTANT]
>AEM Dispatcher 변환기는 NodeJS를 사용하여 개발되었습니다. Adobe은 NodeJS 10.0+를 설치하도록 권장합니다.
