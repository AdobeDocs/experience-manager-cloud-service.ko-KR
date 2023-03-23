---
title: AEM Dispatcher 변환기 도구
description: AEM Dispatcher 변환기 도구
exl-id: 2e95ff7b-cc94-477d-99ab-816a58998287
source-git-commit: 940a01cd3b9e4804bfab1a5970699271f624f087
workflow-type: tm+mt
source-wordcount: '337'
ht-degree: 61%

---

# AEM Dispatcher 변환기 {#introduction}

>[!CONTEXTUALHELP]
>id="aemcloud_nonbpa_dispconverter"
>title="AEM Dispatcher 변환기"
>abstract="Adobe Experience Manager Dispatcher 변환기는 기존 AEM Dispatcher 구성을 AEM as a Cloud Service Dispatcher 구성으로 변환합니다."

Adobe Experience Manager Dispatcher 변환기는 기존 AEM Dispatcher 구성을 AEM as a Cloud Service Dispatcher 구성으로 변환합니다.

## Dispatcher 소개 {#introduction-dispatcher}

Dispatcher는 Adobe Experience Manager의 캐싱 및/또는 로드 밸런싱 도구입니다. AEM의 Dispatcher를 사용하면 AEM 서버를 공격으로부터 보호할 수 있습니다. 따라서 Dispatcher를 엔터프라이즈급 웹 서버와 함께 사용하여 AEM 인스턴스의 보안을 강화할 수 있습니다.

>[!NOTE]
>Dispatcher의 가장 일반적인 사용은 **AEM 게시 인스턴스**&#x200B;의 응답을 캐시하여 외부에서 게시되는 웹 사이트의 응답성과 보안을 향상시키는 것입니다.

[Dispatcher 개요](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/dispatcher.html?lang=ko-KR)를 참조하여 Dispatcher가 캐싱을 수행하고 문서를 반환하며 부하 분산을 수행하는 방법을 알아보십시오.

### Apache 및 Dispatcher 구성과 테스트 {#dispatcher-configurations-cloud}

클라우드 환경에 배포하기 전에 AEM as a Cloud Service Apache 및 Dispatcher 구성을 조직하는 방법과 이렇게 구성한 조직을 로컬로 확인하고 실행하는 방법을 알아보아야 합니다.

자세한 내용은 [클라우드의 Dispatcher](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/content-delivery/disp-overview.html)를 참조하십시오.

## AEM Dispatcher 변환기 {#aem-dispatcher-converter}

AEM Dispatcher Converter는 기존 온-프레미스 또는 Adobe Managed Services 디스패처 구성을 AEM as a Cloud Service 호환 디스패처 구성으로 리팩터링하는 기능을 제공합니다.

## AEM Dispatcher 변환기 사용 {#using-dispatcher-converter}

* Adobe I/O CLI 를 통해 : 를 통해 AEM Dispatcher 변환기를 사용하는 것이 좋습니다 `aio-cli-plugin-aem-cloud-service-migration` (AEM as a Cloud Service 코드 리팩터링 플러그인(Adobe I/O CLI용).

   을(를) 참조하십시오. **[Git 리소스: aio-cli-plugin-aem-cloud-service-migration](https://github.com/adobe/aio-cli-plugin-aem-cloud-service-migration#introduction)** 플러그인을 설치하고 사용하는 방법을 알아봅니다.

* 독립형 유틸리티 : AEM Dispatcher 변환기 도구를 독립형 유틸리티로 실행할 수도 있습니다.

   을(를) 참조하십시오. **[Git 리소스: AEM Cloud Service Dispatcher 변환기](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/dispatcher-converter)** 이 도구의 사용 및 문제 해결에 대해 알아봅니다.

>[!IMPORTANT]
>AEM Dispatcher 변환기는 NodeJS를 사용하여 개발됩니다. NodeJS 10.0 이상을 설치하는 것이 좋습니다.
