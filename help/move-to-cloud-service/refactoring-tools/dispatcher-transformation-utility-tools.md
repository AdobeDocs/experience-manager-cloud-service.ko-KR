---
title: AEM Dispatcher Converter 도구
description: AEM Dispatcher Converter 도구
translation-type: tm+mt
source-git-commit: 3478827949356c4a4f5133b54c6cf809f416efef
workflow-type: tm+mt
source-wordcount: '348'
ht-degree: 15%

---


# AEM Dispatcher Converter {#introduction}

Adobe Experience Manager Dispatcher Converter는 기존 AMS Dispatcher 구성을 클라우드 서비스 디스패처 구성으로 AEM으로 변환합니다.

## Dispatcher 소개 {#introduction-dispatcher}

Dispatcher는 Adobe Experience Manager의 캐싱 및/또는 로드 밸런싱 도구입니다. AEM의 Dispatcher를 사용하면 AEM 서버를 공격으로부터 보호할 수 있습니다. 따라서 Dispatcher를 엔터프라이즈급 웹 서버와 함께 사용하여 AEM 인스턴스의 보안을 강화할 수 있습니다.

>[!NOTE]
>The most common use of Dispatcher is to cache responses from an **AEM publish instance**, to increase the responsiveness and security of your externally facing published website.

디스패처 [개요](https://docs.adobe.com/content/help/ko-KR/experience-manager-dispatcher/using/dispatcher.html) (Dispatcher Overview)를 참조하여 디스패처가 캐싱을 수행하고 문서를 반환하며 부하 분산을 수행하는 방법을 알아보십시오.

### Apache 및 Dispatcher 구성 및 테스트 {#dispatcher-configurations-cloud}

Cloud 환경에 배포하기 전에 AEM을 클라우드 서비스 Apache 및 Dispatcher 구성으로 구성하는 방법과 로컬로 유효성을 확인하고 실행하는 방법을 배워야 합니다.

자세한 내용은 [Cloud의](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/implementing/dispatcher/overview.html) Dispatcher를 참조하십시오.

## AEM Dispatcher Converter {#aem-dispatcher-converter}

AEM Dispatcher Converter는 기존 AMS Dispatcher 구성을 클라우드 서비스 발송자 구성으로 AEM으로 변환하는 유틸리티입니다. 이 유틸리티는 AMS 인스턴스용입니다.

구현된 변환기는 **변형 지침을** 따르는 AEMDispatcherConfigConverter입니다.

AMS를 Adobe Experience Manager [로 클라우드 서비스 디스패처 구성으로](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/implementing/dispatcher/overview.html#how-to-convert-an-ams-to-an-aem-as-a-cloud-service-dispatcher-configuration) 변환하기 위해 AMS를 Adobe Experience Manager로 변환을 참조하십시오.

## AEM Dispatcher Converter 사용 {#using-dispatcher-converter}

다음 섹션에서는 AEM Dispatcher Converter 도구를 사용하는 데 필요한 리소스 및 정보에 대해 설명합니다.

Git 리소스 **[를 참조하십시오. AEM Cloud Service Dispatcher Converter](https://github.com/adobe/aem-cloud-service-dispatcher-converter)**에서 이 도구의 사용, 제한 및 문제 해결에 대해 알아보십시오.

>[!IMPORTANT]
>AEM Dispatcher Converter는 Python 3.7.3을 사용하여 개발되었습니다. Python 3.5 이상을 설치하는 것이 좋습니다.

## 제한 사항 {#limitations}

AEM Dispatcher Converter는 제공된 디스패처 구성 폴더의 구조가 Cloud Manager 디스패처 구성에 설명된 구조와 유사하다고 가정하여 작동합니다.


