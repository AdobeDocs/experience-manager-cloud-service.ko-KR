---
title: Adobe Analytics와 통합
description: 'Adobe Analytics와 통합 '
translation-type: tm+mt
source-git-commit: 6754693da488b0bc44a71aa9f0402fc1308b703a
workflow-type: tm+mt
source-wordcount: '561'
ht-degree: 4%

---


# Adobe Analytics와 통합{#integrating-with-adobe-analytics}

Adobe Analytics 및 AEM을 클라우드 서비스로 통합하면 웹 페이지 활동을 추적할 수 있습니다.

* Adobe Analytics 구성을 통해 AEM이 Adobe Analytics에 인증할 수 있습니다.
* 프레임워크는 Adobe Analytics 보고서 세트로 전송된 데이터를 식별합니다.

데이터에는 페이지 및 사용자 데이터가 포함됩니다. 예:

* AEM 구성 요소가 수집하는 데이터
* 링크 클릭 수
* 비디오 사용 정보
* Adobe Analytics에서 페이지 방문 횟수

아래 나열된 페이지에서는 통합을 구성하는 데 도움이 될 수 있습니다. Launch by Adobe는 Analytics 기능(JS 라이브러리)을 사용하여 AEM 사이트를 구현하기 위한 사실상의 툴입니다. 따라서 Launch와 클라우드 서비스로 AEM을 통합하면 Adobe Analytics가 함께 제공됩니다.

* [Adobe Analytics에 연결 및 프레임워크](https://docs.adobe.com/content/help/en/experience-manager-65/administering/integration/adobeanalytics-connect.html) 만들기 - &quot;Analytics 프레임워크&quot;는 AEM에서 이전 버전이며, 클래식 UI가 필요하기 때문에 AEM에서 이러한 프레임워크를 만든 것은 클라우드 서비스로 작동하지 않습니다. 대신 Launch by Adobe를 사용하여 변수 매핑과 JS 라이브러리를 페이지에 배포해야 합니다.
* [Adobe Launch 통합](https://docs.adobe.com/content/help/en/experience-manager-learn/sites/integrations/adobe-launch-integration-tutorial-understand.html)
* [Adobe I/O를 통해 AEM과 Adobe Launch 통합](https://helpx.adobe.com/experience-manager/using/aem_launch_adobeio_integration.html)
* [Adobe, Analytics 및 Target에서 Launch와 AEM 통합 이해](https://helpx.adobe.com/experience-manager/kt/integration/using/aem-launch-integration-tutorial-understand.html)
* [Adobe Analytics에 대한 링크 추적 구성](https://docs.adobe.com/content/help/en/experience-manager-65/administering/integration/adobeanalytics-link.html)
* [Adobe Analytics 속성을 사용하여 구성 요소 데이터 매핑](https://docs.adobe.com/content/help/en/experience-manager-65/administering/integration/adobeanalytics-mapping.html)
* [Adobe Analytics에 대한 비디오 추적 구성](https://docs.adobe.com/content/help/en/experience-manager-65/administering/integration/adobeanalytics-video.html)
* [Adobe 분류](https://docs.adobe.com/content/help/en/experience-manager-65/administering/integration/adobeanalytics-classifications.html)

>[!CAUTION]
>
>Adobe Experience Manager를 기존 Analytics 계정이 없는 클라우드 서비스 고객은 Experience Cloud용 Analytics Foundation Pack에 대한 액세스를 요청할 수 있습니다.  이 Foundation Pack은 Analytics의 볼륨 사용을 제한합니다.

>[!NOTE]
>
>Launch by Adobe의 IMS 구성(기술 계정)은 AEM에서 클라우드 서비스로 미리 구성되어 있습니다. 사용자는 이 구성을 만들 필요가 없습니다.

## 추가 정보 {#further-information}

다음을 참조하십시오.

* [Adobe Analytics 통합](https://docs.adobe.com/content/help/en/experience-manager-65/developing/extending-aem/extending-analytics/extending-analytics.html) 확장을 참조하십시오. &quot;Analytics 프레임워크&quot;는 AEM에서 이전 버전이며, 이러한 프레임워크는 클래식 UI가 필요하므로 AEM에서 클라우드 서비스로 작동하지 않습니다. 대신 Launch by Adobe를 사용하여 변수 매핑과 JS 라이브러리를 페이지에 배포해야 합니다.
* Adobe Analytics 통합 문제 해결에 대한 자세한 내용은 기술 자료 문서 [Adobe Analytics 통합 - 문제](https://helpx.adobe.com/experience-manager/kb/sitecatalystintegrationtroubleshooting.html)해결 관련 문서를 참조하십시오.

>[!NOTE]
>
>사용자 지정 프록시 구성과 함께 Adobe Analytics를 사용하는 경우 [Apache HTTP 클라이언트](https://docs.adobe.com/content/help/en/experience-manager-65/deploying/configuring/configuring-osgi.html) 프록시 구성에 필요한 두 개의 OSGi 번들 **** (예: 웹 콘솔 포함)을 구성해야 합니다. AEM의 일부 기능에서 3.x API를 사용하는 반면 다른 기능에서는 4.x API를 모두 사용해야 합니다. 구성:
>
>* **3.x API를 구성하는 Day Commons HTTP Client 3.1** ;
   >  예: [https://localhost:4502/system/console/configMgr/com.day.commons.httpclient](https://localhost:4502/system/console/configMgr/com.day.commons.httpclient)
   >
   >
* **4.x API를** 구성하기 위한 Apache HTTP Components Proxy Configuration;
   >  예: [https://localhost:4502/system/console/configMgr/org.apache.http.proxyconfigurator](https://localhost:4502/system/console/configMgr/org.apache.http.proxyconfigurator)

>


