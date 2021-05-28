---
title: 'Adobe Analytics와 통합 '
description: 'Adobe Analytics와 통합 '
source-git-commit: 856266faf4cb99056b1763383d611e9b2c3c13ea
workflow-type: tm+mt
source-wordcount: '545'
ht-degree: 2%

---


# Adobe Analytics와 통합{#integrating-with-adobe-analytics}

Adobe Analytics과 AEM as a Cloud Service을 통합하여 웹 페이지 활동을 추적할 수 있습니다.

* Adobe Analytics 구성을 사용하면 AEM에서 Adobe Analytics을 인증할 수 있습니다.
* 프레임워크는 Adobe Analytics 보고서 세트로 전송되는 데이터를 식별합니다.

데이터에는 페이지 및 사용자 데이터가 포함됩니다(예: ).

* AEM 구성 요소가 수집하는 데이터
* 링크 클릭 수
* 비디오 사용 정보
* Adobe Analytics에서 페이지 방문 횟수

아래 나열된 페이지를 통해 통합을 구성할 수 있습니다. Launch by Adobe은 Analytics 기능(JS 라이브러리)을 사용하여 AEM 사이트를 계측하는 사실상의 도구입니다. 따라서 AEM as a Cloud Service과 Launch 및 Adobe Analytics을 통합하면 즉시 사용이 가능합니다.

* [Adobe Analytics에 연결 및 프레임워크 생성](https://experienceleague.adobe.com/docs/experience-manager-65/administering/integration/adobeanalytics-connect.html)  - &quot;Analytics 프레임워크&quot;는 AEM에서 오래되며, 클래식 UI가 필요하므로 AEM에서 작성이 Cloud Service으로 작동하지 않습니다. Launch by Adobe은 변수 매핑과 JS 라이브러리를 페이지에 배포하는 데 모두 대신 사용해야 합니다.
* [Launch by Adobe 통합](https://experienceleague.adobe.com/docs/experience-manager-learn/sites/integrations/adobe-launch-integration-tutorial-understand.html)
* [Adobe I/O을 통해 AEM과 Adobe Launch 통합](https://helpx.adobe.com/experience-manager/using/aem_launch_adobeio_integration.html)
* [Launch by Adobe, Analytics 및 Target과 AEM 통합 이해](https://helpx.adobe.com/experience-manager/kt/integration/using/aem-launch-integration-tutorial-understand.html)
* [Adobe Analytics에 대한 링크 추적 구성](https://experienceleague.adobe.com/docs/experience-manager-65/administering/integration/adobeanalytics-link.html)
* [구성 요소 데이터를 Adobe Analytics 속성과 매핑](https://experienceleague.adobe.com/docs/experience-manager-65/administering/integration/adobeanalytics-mapping.html)
* [Adobe Analytics에 대한 비디오 추적 구성](https://experienceleague.adobe.com/docs/experience-manager-65/administering/integration/adobeanalytics-video.html)
* [Adobe 분류](https://experienceleague.adobe.com/docs/experience-manager-65/administering/integration/adobeanalytics-classifications.html)

>[!CAUTION]
>
>기존 Analytics 계정이 없는 Cloud Service 고객인 Adobe Experience Manager은 Experience Cloud을 위한 Analytics Foundation Pack 액세스 권한을 요청할 수 있습니다.  이 기초 팩은 Analytics의 볼륨 제한을 제공합니다.

>[!NOTE]
>
>Launch by Adobe에 대한 IMS 구성(기술 계정)은 AEM에서 Cloud Service으로 미리 구성되어 있습니다. 사용자는 이 구성을 만들 필요가 없습니다.

## 추가 정보 {#further-information}

다음을 참조하십시오.

* [Adobe Analytics ](https://experienceleague.adobe.com/docs/experience-manager-65/developing/extending-aem/extending-analytics/extending-analytics.html) 통합 확장 을 참조하십시오. Analytics 프레임워크&quot;는 AEM에서 레거시 이며, 클래식 UI가 필요하므로 AEM에서는 작성이 Cloud Service으로 작동하지 않습니다. Launch by Adobe은 변수 매핑과 JS 라이브러리를 페이지에 배포하는 데 모두 대신 사용해야 합니다.
* Adobe Analytics 통합 문제 해결에 대한 자세한 내용은 기술 자료 문서 [Adobe Analytics 통합 - 문제 해결](https://helpx.adobe.com/experience-manager/kb/sitecatalystintegrationtroubleshooting.html) 을 참조하십시오.

>[!NOTE]
>
>사용자 지정 프록시 구성과 함께 Adobe Analytics을 사용하는 경우 [Apache HTTP Client **프록시 구성에 필요한 두 개의 OSGi 번들](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/configuring/configuring-osgi.html)(예: 웹 콘솔 사용)을 구성해야 합니다.** AEM의 일부 기능에서는 3.x API를 사용하는 반면, 다른 기능에서는 4.x API를 사용하기 때문에 두 가지 모두 필요합니다. 구성:
>
>* **3.x API를 구성하기 위한 Day Commons HTTP Client 3.1** 
   >  예: [https://localhost:4502/system/console/configMgr/com.day.commons.httpclient](https://localhost:4502/system/console/configMgr/com.day.commons.httpclient)
   >
   >
* **4.x API를** 구성하기 위한 Apache HTTP 구성 요소 프록시 구성
   >  예: [https://localhost:4502/system/console/configMgr/org.apache.http.proxyconfigurator](https://localhost:4502/system/console/configMgr/org.apache.http.proxyconfigurator)

>


