---
title: 'Adobe Analytics와 통합 '
description: 'Adobe Analytics와 통합 '
source-git-commit: 856266faf4cb99056b1763383d611e9b2c3c13ea
workflow-type: ht
source-wordcount: '545'
ht-degree: 100%

---


# Adobe Analytics와 통합{#integrating-with-adobe-analytics}

Adobe Analytics와 AEM as a Cloud Service를 통합하여 웹 페이지 활동을 추적할 수 있습니다.

* Adobe Analytics 구성을 사용하면 AEM에서 Adobe Analytics를 인증할 수 있습니다.
* 프레임워크는 Adobe Analytics 보고서 세트로 전송되는 데이터를 식별합니다.

이 데이터에는 다음과 같은 페이지 및 사용자 데이터가 포함됩니다.

* AEM 구성 요소가 수집하는 데이터
* 링크 클릭
* 비디오 사용 정보
* Adobe Analytics에서의 페이지 방문 횟수

아래 나열된 페이지는 통합을 구성하는 데 도움이 됩니다. Adobe에서 제공하는 Launch는 Analytics 기능(JS 라이브러리)을 갖춘 AEM 사이트를 측정하기 위한 실질적인 도구입니다. 따라서 AEM as a Cloud Service와 Launch 및 Adobe Analytics와의 통합은 밀접하게 연결되어 있습니다.

* [Adobe Analytics 연결 및 프레임워크 만들기](https://experienceleague.adobe.com/docs/experience-manager-65/administering/integration/adobeanalytics-connect.html) - “Analytics 프레임워크”는 AEM의 레거시이며, 이를 만들려면 클래식 UI가 필요하므로 AEM as a Cloud Service에서 만들 수 없습니다. 변수를 매핑하고 JS 라이브러리를 페이지에 배포하려면 Adobe에서 제공하는 Launch를 대신 사용해야 합니다.
* [Adobe에서 제공하는 Launch 통합](https://experienceleague.adobe.com/docs/experience-manager-learn/sites/integrations/adobe-launch-integration-tutorial-understand.html)
* [Adobe I/O를 통해 AEM을 Adobe Launch와 통합](https://helpx.adobe.com/experience-manager/using/aem_launch_adobeio_integration.html)
* [Adobe에서 제공하는 Launch, Analytics 및 Target과의 AEM 통합 이해](https://helpx.adobe.com/experience-manager/kt/integration/using/aem-launch-integration-tutorial-understand.html)
* [Adobe Analytics를 위한 링크 추적 구성](https://experienceleague.adobe.com/docs/experience-manager-65/administering/integration/adobeanalytics-link.html)
* [Adobe Analytics 속성을 사용하여 구성 요소 데이터 매핑](https://experienceleague.adobe.com/docs/experience-manager-65/administering/integration/adobeanalytics-mapping.html)
* [Adobe Analytics를 위한 비디오 추적 구성](https://experienceleague.adobe.com/docs/experience-manager-65/administering/integration/adobeanalytics-video.html)
* [Adobe 분류](https://experienceleague.adobe.com/docs/experience-manager-65/administering/integration/adobeanalytics-classifications.html)

>[!CAUTION]
>
>기존 Analytics 계정이 없는 Adobe Experience Manager as a Cloud Service 고객은 Experience Cloud의 Analytics Foundation Pack에 대한 액세스 권한을 요청할 수 있습니다. 이 Foundation Pack은 제한된 볼륨의 Analytics를 사용할 수 있도록 제공합니다.

>[!NOTE]
>
>Adobe에서 제공하는 Launch용 IMS 구성(기술 계정)은 AEM as a Cloud Service에 사전 구성되어 있습니다. 사용자는 이 구성을 만들 필요가 없습니다.

## 추가 정보 {#further-information}

다음을 참조하십시오.

* [Adobe Analytics 통합 확장](https://experienceleague.adobe.com/docs/experience-manager-65/developing/extending-aem/extending-analytics/extending-analytics.html)을 참조하여 사용자 데이터를 수집하는 구성 요소 개발 및 Adobe Analytics 프레임워크 맞춤화에 대한 자세한 내용을 알아보십시오. “Analytics 프레임워크”는 AEM의 레거시이며, 이를 만들려면 클래식 UI가 필요하므로 AEM as a Cloud Service에서 만들 수 없습니다. 변수를 매핑하고 JS 라이브러리를 페이지에 배포하려면 Adobe에서 제공하는 Launch를 대신 사용해야 합니다.
* 지식 기반 문서인 [Adobe Analytics 통합 - 문제 해결](https://helpx.adobe.com/kr/experience-manager/kb/sitecatalystintegrationtroubleshooting.html)을 참조하여 Adobe Analytics 통합 관련 문제를 해결하는 방법에 대해 알아보십시오.

>[!NOTE]
>
>If you are using Adobe Analytics with a custom proxy configuration, you need to [configure two OSGi bundles](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/configuring/configuring-osgi.html) (for example, with the Web console) required for the **Apache HTTP Client** proxy configurations. Both are required as some functionalities of AEM use the 3.x APIs, while others use the 4.x APIs. 다음을 구성하십시오.
>
>* 3.x API 구성을 위한 **Day Commons HTTP 클라이언트 3.1**
   >  (예: [https://localhost:4502/system/console/configMgr/com.day.commons.httpclient](https://localhost:4502/system/console/configMgr/com.day.commons.httpclient))
>
>* 4.x API 구성을 위한 **Apache HTTP 구성 요소 프록시 구성**
   >  (예: [https://localhost:4502/system/console/configMgr/org.apache.http.proxyconfigurator](https://localhost:4502/system/console/configMgr/org.apache.http.proxyconfigurator))
>

