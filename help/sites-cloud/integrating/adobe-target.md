---
title: Adobe Target과 통합
description: Adobe Target과 통합
exl-id: 2b4cf35e-2b75-4303-8d09-f6644ad99274
source-git-commit: f40a2db6616aeaaf13f8ae19ab429a7301e6c05a
workflow-type: tm+mt
source-wordcount: '727'
ht-degree: 100%

---

# Adobe Target과 통합{#integrating-with-adobe-target}

Adobe Marketing Cloud의 일부인 [Adobe Target](https://www.adobe.com/kr/solutions/testing-targeting/testandtarget.html)을 사용하여 모든 채널에 걸친 타겟팅 및 측정을 통해 콘텐츠 관련성을 높일 수 있습니다. 마케터는 Adobe Target을 사용하여 온라인 테스트를 디자인 및 실행하고, 즉석으로 대상자 세그먼트를 만들고(행동 기반), 콘텐츠 및 온라인 경험의 타겟팅을 자동화합니다. AEM as a Cloud Service는 Adobe Target Standard에서 사용하는 타겟팅 워크플로를 채택했습니다. Target을 사용하면 AEM as a Cloud Service의 편집 환경 타겟팅에 잘 알게 될 수 있습니다.

AEM 사이트와 Adobe Target을 통합함으로써 페이지의 콘텐츠를 개인화하여 다음과 같은 작업을 수행할 수 있습니다.

* 콘텐츠 타겟팅 구현
* Target 대상자를 사용하여 개인화된 경험 만들기
* 방문자가 페이지와 상호 작용할 때 컨텍스트 데이터를 Target에 제출
* 전환율 추적

>[!NOTE]
>
>기존 Target 계정이 없는 Adobe Experience Manager as a Cloud Service 고객은 Experience Cloud의 Target Foundation Pack에 대한 액세스 권한을 요청할 수 있습니다.  Foundation Pack은 제한된 볼륨의 Target을 사용할 수 있도록 제공합니다.


Target과 통합하려면 다음과 같은 작업을 수행해야 합니다.

* [사전 요구 사항 작업 수행](https://experienceleague.adobe.com/docs/experience-manager-65/administering/integration/target-requirements.html): Adobe Target으로 등록하여 AEM 작성자 인스턴스의 특정 측면을 구성합니다. Adobe Target 계정은 최소한 **승인자** 수준 권한을 보유해야 합니다. 또한 사용자가 액세스할 수 없도록 게시 노드의 활동 설정을 보호해야 합니다.

* Adobe에서 제공하는 Launch는 Target 기능(JS 라이브러리)을 갖춘 AEM 사이트를 측정하기 위한 실질적인 도구입니다. 따라서 AEM as a Cloud Service와 Launch 및 Adobe Target과의 통합은 밀접하게 연결되어 있습니다(아래 링크 참조).

   * [Adobe I/O를 사용하여 Adobe Target과 통합](https://experienceleague.adobe.com/docs/experience-manager-65/administering/integration/integration-target-ims-adobe-io.html)
   * [Adobe에서 제공하는 Launch 통합](https://experienceleague.adobe.com/docs/experience-manager-learn/sites/integrations/experience-platform-launch/overview.html)
   * [Adobe I/O를 통해 AEM을 Adobe Launch와 통합](https://docs.adobe.com/content/help/ko/experience-manager-learn/sites/integrations/experience-platform-launch/overview.html)
   * [Adobe에서 제공하는 Launch, Analytics 및 Target과의 AEM 통합 이해](https://experienceleague.adobe.com/docs/experience-manager-learn/sites/integrations/experience-platform-launch/overview.html)

>[!NOTE]
>
>Adobe에서 제공하는 Launch용 IMS 구성(기술 계정)은 AEM as a Cloud Service에 사전 구성되어 있습니다. 사용자는 이 구성을 만들 필요가 없습니다.

1. [활동 구성](https://experienceleague.adobe.com/docs/experience-manager-65/authoring/personalization/activitylib.html): 활동을 Target 클라우드 구성과 연결합니다.

>[!CAUTION]
>
>AEM as a Cloud Service에서는 AEM에서 Adobe Target으로 오퍼 및 활동을 동기화하는 복제 에이전트가 기본적으로 비활성화되어 있습니다. 복제 에이전트를 다시 활성화해야 하는 경우 [Adobe 지원](https://experienceleague.adobe.com/?support-solution=General#support) 팀에 문의하십시오.

>[!NOTE]
>
>사용자 정의 프록시 구성을 통해 Target을 사용 중인 경우, AEM의 일부 기능은 3.x API를 사용하고 다른 일부 기능은 4.x API를 사용하므로 HTTP 클라이언트 프록시 구성을 모두 구성해야 합니다.
>
>* 3.x은(는) [http://localhost:4502/system/console/configMgr/com.day.commons.httpclient](http://localhost:4502/system/console/configMgr/com.day.commons.httpclient)로 구성됩니다.
>* 4.x은(는) [http://localhost:4502/system/console/configMgr/org.apache.http.proxyconfigurator](http://localhost:4502/system/console/configMgr/org.apache.http.proxyconfigurator)로 구성됩니다.
>


>[!CAUTION]
>
>일반 사용자가 액세스할 수 없도록 게시 인스턴스에서 활동 설정 노드 **cq:ActivitySettings**&#x200B;를 보호해야 합니다. 활동 설정 노드는 Adobe Target에 대한 활동 동기화를 처리하는 서비스에만 액세스할 수 있어야 합니다.
>
>자세한 내용은 [Adobe Target과 통합하기 위한 전제 조건](https://experienceleague.adobe.com/docs/experience-manager-65/administering/integration/target-requirements.html#securing-the-activity-settings-node)을 참조하십시오.

통합이 완료되면 Adobe Target에 방문자 데이터를 전송하는 [타겟팅된 콘텐츠를 작성](https://experienceleague.adobe.com/docs/experience-manager-65/authoring/personalization/content-targeting-touch.html)할 수 있습니다. 콘텐츠 타겟팅을 활성화하려면 페이지 구성 요소에 특정 코드가 필요합니다. [타겟팅된 콘텐츠용 개발](https://experienceleague.adobe.com/docs/experience-manager-65/developing/personlization/target.html)을 참조하십시오.

>[!NOTE]
>
>AEM 작성자의 구성 요소를 타겟팅하면 해당 구성 요소는 Adobe Target에 대한 일련의 서버측 호출을 만들어 캠페인을 등록하고, 오퍼를 설정하고, Adobe Target 세그먼트를 검색합니다(구성된 경우). AEM 게시에서 Adobe Target으로는 서버측 호출을 만들 수 없습니다.

## 배경 정보 소스 {#background-information-sources}

AEM as a Cloud Service와 Adobe Target을 통합하려면 Adobe Target, AEM 활동 관리 및 AEM 대상자 관리에 대한 지식이 필요합니다. 다음과 같은 정보를 숙지해야 합니다.

* Adobe Target ([Adobe Target 설명서](https://experienceleague.adobe.com/docs/target/using/target-home.html) 참조)
* AEM 활동 콘솔([활동 관리](https://experienceleague.adobe.com/docs/experience-manager-65/authoring/personalization/activitylib.html) 참조)
* AEM 대상자([대상자 관리](https://experienceleague.adobe.com/docs/experience-manager-65/authoring/personalization/managing-audiences.html) 참조)

>[!NOTE]
>
>Adobe Target을 사용하여 작업 시 캠페인 내에서 허용되는 최대 아티팩트의 수는 다음과 같습니다.
>
>* 50개 위치
>* 2,000개 경험
>* 50개 지표
>* 50개 보고 세그먼트

