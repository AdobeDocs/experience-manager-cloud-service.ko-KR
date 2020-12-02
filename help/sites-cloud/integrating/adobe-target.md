---
title: Adobe Target과 통합
description: 'Adobe Target과 통합 '
translation-type: tm+mt
source-git-commit: bffc335fdafe6bf12a66bcd2f7aacf029fce567e
workflow-type: tm+mt
source-wordcount: '743'
ht-degree: 8%

---


# Adobe Target과 통합{#integrating-with-adobe-target}

Adobe Marketing Cloud의 일부로, [Adobe Target](http://www.adobe.com/solutions/testing-targeting/testandtarget.html)에서는 모든 채널에서 타깃팅 및 측정을 통해 컨텐츠 관련성을 높일 수 있습니다. Adobe Target은 온라인 테스트를 디자인 및 실행하고, 행동에 따라 고객 세그먼트를 생성하고, 컨텐츠 및 온라인 경험의 타깃팅을 자동화하는 데 사용됩니다. AEM은 Cloud Service로서 Adobe Target 표준에서 사용되는 타깃팅 워크플로우를 채택했습니다. Target을 사용하는 경우 AEM의 타깃팅 편집 환경에 Cloud Service으로 익숙할 것입니다.

AEM 사이트를 Adobe Target과 통합하여 페이지의 컨텐츠를 개인화할 수 있습니다.

* 콘텐츠 타깃팅 구현
* Target 고객을 사용하여 개인화된 경험 제작
* 방문자가 페이지와 상호 작용할 때 컨텍스트 데이터를 Target에 제출합니다.
* 전환율 추적

>[!NOTE]
>
>기존 Target 계정이 없는 Cloud Service 고객인 Adobe Experience Manager은 Experience Cloud용 Target Foundation Pack에 대한 액세스를 요청할 수 있습니다.  Foundation Pack은 Target의 볼륨 사용을 제한합니다.


Target과 통합하려면 다음 작업을 수행하십시오.

* [사전 요구 작업](https://docs.adobe.com/content/help/en/experience-manager-65/administering/integration/target-requirements.html) 수행:Adobe Target에 등록하고 AEM 작성자 인스턴스의 특정 측면을 구성합니다. Adobe Target 계정에는 최소 **승인자** 수준 권한이 있어야 합니다. 또한 사용자가 액세스할 수 없도록 게시 노드에서 활동 설정을 보호해야 합니다.

* Launch by Adobe은 Target 기능(JS 라이브러리)이 있는 AEM 사이트를 구현하기 위한 실질적인 도구입니다. 따라서 AEM을 Launch와 Cloud Service으로 통합하고 Adobe Target이 함께 사용할 수 있습니다(아래 링크 참조).

   * [Adobe I/O을 사용한 Adobe Target 통합](https://docs.adobe.com/content/help/en/experience-manager-65/administering/integration/integration-ims-adobe-io.html)
   * [Launch by Adobe 통합](https://docs.adobe.com/content/help/en/experience-manager-learn/sites/integrations/adobe-launch-integration-tutorial-understand.html)
   * [AEM과 Adobe I/O을 통해 Adobe Launch 통합](https://helpx.adobe.com/experience-manager/using/aem_launch_adobeio_integration.html)
   * [Launch by Adobe, 분석 및 Target과 AEM 통합 이해](https://helpx.adobe.com/experience-manager/kt/integration/using/aem-launch-integration-tutorial-understand.html)

>[!NOTE]
>
>Launch by Adobe에 대한 IMS 구성(기술 계정)은 AEM에서 Cloud Service으로 미리 구성되어 있습니다. 사용자는 이 구성을 만들 필요가 없습니다.

1. [활동 구성](https://docs.adobe.com/content/help/en/experience-manager-65/authoring/personalization/activitylib.html):활동을 Target 클라우드 구성과 연결합니다.

>[!CAUTION]
>
>AEM에서 Cloud Service으로, AEM에서 오퍼와 활동을 Adobe Target에 동기화하는 복제 에이전트는 기본적으로 비활성화됩니다. 복제 에이전트를 다시 활성화해야 하는 경우 [Adobe 지원](https://helpx.adobe.com/contact/enterprise-support.ec.html#experience-manager) 팀에 문의하십시오.

>[!NOTE]
>
>사용자 지정 프록시 구성과 함께 Target을 사용하는 경우, AEM의 일부 기능으로서 두 HTTP 클라이언트 프록시 구성을 모두 구성해야 하며, 나머지 일부 기능에서는 4.x API를 사용하고 있습니다.
>
>* 3.x는 [http://localhost:4502/system/console/configMgr/com.day.commons.httpclient](http://localhost:4502/system/console/configMgr/com.day.commons.httpclient)으로 구성됩니다.
>* 4.x는 [http://localhost:4502/system/console/configMgr/org.apache.http.proxyconfigurator](http://localhost:4502/system/console/configMgr/org.apache.http.proxyconfigurator)으로 구성됩니다.

>



>[!CAUTION]
>
>일반 사용자가 액세스할 수 없도록 게시 인스턴스에서 활동 설정 노드 **cq:ActivitySettings**&#x200B;를 보호해야 합니다. 활동 설정 노드는 Adobe Target에 대한 활동 동기화를 처리하는 서비스만 액세스할 수 있어야 합니다.
>
>자세한 내용은 [Adobe Target과 통합하기 위한 전제 조건](https://docs.adobe.com/content/help/en/experience-manager-65/administering/integration/target-requirements.html#securing-the-activity-settings-node)을 참조하십시오.

통합이 완료되면 방문자 데이터를 Adobe Target으로 보내는 [타깃팅된 컨텐츠](https://docs.adobe.com/content/help/en/experience-manager-65/authoring/personalization/content-targeting-touch.html)를 작성할 수 있습니다. 페이지 구성 요소에는 컨텐츠 타깃팅을 활성화하려면 특정 코드가 필요합니다. ([타깃팅된 컨텐츠 개발](https://docs.adobe.com/content/help/en/experience-manager-65/developing/personlization/target.html)을 참조하십시오.)

>[!NOTE]
>
>AEM 작성자의 구성 요소를 타깃팅하면 구성 요소는 캠페인을 등록하고, 오퍼를 설정하고, Adobe Target 세그먼트를 가져오기 위해 Adobe Target에 일련의 서버측 호출을 만듭니다(구성된 경우). AEM에서 Adobe Target으로 게시한 서버측 호출은 없습니다.

## 배경 정보 소스 {#background-information-sources}

AEM을 Adobe Target과 Cloud Service으로 통합하려면 Adobe Target, AEM 활동 관리 및 AEM 대상 관리에 대한 지식이 필요합니다. 다음 정보에 대해 잘 알고 있어야 합니다.

* Adobe Target([Adobe Target 설명서](https://docs.adobe.com/content/help/en/target/using/target-home.html) 참조).
* AEM 활동 콘솔(활동 관리[을 참조하십시오.](https://docs.adobe.com/content/help/en/experience-manager-65/authoring/personalization/activitylib.html)
* AEM 대상(대상 관리[을 참조하십시오.](https://docs.adobe.com/content/help/en/experience-manager-65/authoring/personalization/managing-audiences.html)

>[!NOTE]
>
>Adobe Target 작업 시 캠페인 내에서 허용되는 최대 객체 수는 다음과 같습니다.
>
>* 50개 위치
>* 2,000개의 경험
>* 50지표
>* 세그먼트 50개 보고

>


