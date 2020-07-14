---
title: AEM Dispatcher 변환기 도구
description: AEM Dispatcher 변환기 도구
translation-type: ht
source-git-commit: 66cf4fc7b5a336968dd3f8757cc56a11d6e4843e
workflow-type: ht
source-wordcount: '348'
ht-degree: 100%

---


# AEM Dispatcher 변환기 {#introduction}

Adobe Experience Manager Dispatcher 변환기는 기존 AMS Dispatcher 구성을 AEM에 클라우드 서비스 Dispatcher 구성으로 변환합니다.

## Dispatcher 소개 {#introduction-dispatcher}

Dispatcher는 Adobe Experience Manager의 캐싱 및/또는 로드 밸런싱 도구입니다. AEM의 Dispatcher를 사용하면 AEM 서버를 공격으로부터 보호할 수 있습니다. 따라서 Dispatcher를 엔터프라이즈급 웹 서버와 함께 사용하여 AEM 인스턴스의 보안을 강화할 수 있습니다.

>[!NOTE]
>Dispatcher의 가장 일반적인 사용은 **AEM 게시 인스턴스**&#x200B;의 응답을 캐시하여 외부에서 게시되는 웹 사이트의 응답성과 보안을 향상시키는 것입니다.

[Dispatcher 개요](https://docs.adobe.com/content/help/ko-KR/experience-manager-dispatcher/using/dispatcher.html)를 참조하여 Dispatcher가 캐싱을 수행하고 문서를 반환하며 부하 분산을 수행하는 방법을 알아보십시오.

### Apache 및 Dispatcher 구성과 테스트 {#dispatcher-configurations-cloud}

클라우드 환경에 배포하기 전에 클라우드 서비스로서의 AEM Apache 및 Dispatcher 구성을 조직하는 방법과 이렇게 구성한 조직을 로컬로 확인하고 실행하는 방법을 알아보아야 합니다.

자세한 내용은 [클라우드의 Dispatcher](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/implementing/content-delivery/disp-overview.html)를 참조하십시오.

## AEM Dispatcher 변환기 {#aem-dispatcher-converter}

AEM Dispatcher 변환기는 기존 AMS Dispatcher 구성을 클라우드 서비스로서의 AEM Dispatcher 구성으로 변환하는 유틸리티입니다. 이 유틸리티는 AMS 인스턴스용입니다.

구현된 변환기는 변환 지침을 따르는 **AEMDispatcherConfigConverter**&#x200B;입니다.

AMS를 클라우드 서비스로서의 Adobe Experience Manager Dispatcher 구성으로 변환하려면 [AMS를 클라우드 서비스로서의 Adobe Experience Manager Dispatcher 구성으로 변환](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/implementing/content-delivery/disp-overview.html#how-to-convert-an-ams-to-an-aem-as-a-cloud-service-dispatcher-configuration)을 참조하십시오.

## AEM Dispatcher 변환기 사용 {#using-dispatcher-converter}

다음 섹션에서는 AEM Dispatcher 변환기 도구를 사용하는 데 필요한 리소스 및 정보에 대해 설명합니다.

**[Git 리소스: AEM 클라우드 서비스 Dispatcher 변환기](https://github.com/adobe/aem-cloud-service-dispatcher-converter)**를 참조하여 이 도구의 사용, 제한 및 문제 해결에 대해 알아보십시오.

>[!IMPORTANT]
>AEM Dispatcher 변환기는 Python 3.7.3을 사용하여 개발되었습니다. Python 3.5 이상을 설치하는 것이 좋습니다.

## 제한 사항 {#limitations}

AEM Dispatcher 변환기는 제공된 디스패처 구성 폴더의 구조가 Cloud Manager 디스패처 구성에 설명된 구조와 유사하다고 가정 하에 작동합니다.


