---
title: AEM AS A CLOUD SERVICE DEVELOPER CONSOLE - BETA
description: AEM as a Cloud Service Developer Console 및 클라우드 환경 디버깅을 위한 읽기 전용 도구 세트에 대해 알아봅니다.
feature: Developing
role: Admin, Developer
exl-id: 4b0fc3e9-b7c4-4c95-bd97-8b24e4d5cb3d
source-git-commit: 51c14ba3c15e0136911003752253d21ed673a0eb
workflow-type: tm+mt
source-wordcount: '1188'
ht-degree: 1%

---


# AEM as a Cloud Service Developer Console (Beta) {#developer-console}

AEM as a Cloud Service Developer Console에는 클라우드 환경을 디버깅하기 위한 읽기 전용 도구 세트가 포함되어 있습니다. Cloud Manager의 환경별 링크를 통해 액세스할 수 있으며 번들, OSGi 설정, 서비스 및 서블릿 등을 볼 수 있는 기능을 제공합니다.

>[!NOTE]
>
>이 문서에서는 현재 베타 버전인 AEM Cloud Service Developer Console에 대해 개선된 환경에 대해 설명합니다.
>
>* 제한된 사용자 세트는 현재 Developer Console 상단에 있는 버튼을 통해 새 콘솔에 액세스할 수 있습니다.
>* Adobe은 `aemcs-new-devconsole-ui-beta@adobe.com`에게 보낼 수 있는 모든 피드백을 환영합니다.
>* 현재 AEM Developer Console에 대한 설명서는 [이 문서를 참조하십시오.](/help/implementing/developing/introduction/development-guidelines.md#crxde-lite-and-developer-console)
>* AEM as a Cloud Service Developer Console을 비슷한 이름의 [*Adobe Developer Console*.](https://developer.adobe.com/developer-console/)과 혼동하면 안 됩니다.

>[!TIP]
>
>Developer Console은 읽기 전용입니다. SDK을 사용하여 로컬 개발 작업을 수행하는 중에 OSGi 설정이나 저장소 콘텐츠를 수정해야 하는 경우 다음을 사용할 수 있습니다.
>
>* [CRXDE Lite](/help/implementing/developing/tools/crxde.md)

<!--
There are multiple ways of accessing it:

1. Launch from Cloud Manager  

1. Type a url that can be determined by adjusting the Author or Publish service urls as follows:
   ```  
   https://dev-console/-<namespace>.<cluster>.dev.adobeaemcloud.com
   ```  

1. As a shortcut, the following Cloud Manager CLI command can be used to launch the AEM as a Cloud Service Developer Console based on an environment parameter described below:    
   ```
   aio cloudmanager:open-developer-console <ENVIRONMENTID> --programId <PROGRAMID>
   ```
-->

## 사전 요구 사항 {#prerequisites}

Developer Console은 특정 프로그램에서 특정 역할을 가진 사용자만 액세스할 수 있습니다.

* 프로덕션 프로그램의 경우 Adobe Admin Console의 &quot;Cloud Manager - 개발자 역할&quot;이 Developer Console에 대한 액세스를 제어합니다.
* 샌드박스 프로그램의 경우 AEM 액세스 권한을 부여하는 제품 프로필을 가진 모든 사용자는 Developer Console을 사용할 수 있습니다.
* 모든 프로그램의 경우 상태 덤프 및 저장소 브라우저 액세스에 &quot;Cloud Manager - 개발자 역할&quot;이 필요합니다.

작성자 및 게시 서비스 모두에서 데이터를 보려면 두 서비스의 &quot;AEM 사용자&quot; 또는 &quot;AEM 관리자 제품 프로필&quot;에도 사용자를 할당해야 합니다.

사용자 권한 설정에 대한 자세한 내용은 [Cloud Manager 설명서를 참조하십시오.](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-manager/content/requirements/users-and-roles)

## OSGi 번들 탭 {#osgi-bundles}

**OSGi 번들** 탭에서는 선택한 환경에 배포되고 전체 텍스트 검색을 제공하는 OSGi 번들에 대한 개요를 제공합니다.

![Developer Console의 새 OSGi 번들 화면](/help/implementing/developing/introduction/assets/osgi-bundles.png)

* 탭에는 내보낸 패키지, 가져온 패키지, 사용된 서비스 등과 같은 환경의 실제 번들 상태에 대한 정보가 제공됩니다.
* 번들이 수행할 것으로 예상되는 작업을 수행하는지 번들의 상태를 확인하는 것이 이상적입니다.

**예제 사용 사례:** 번들에서 종속성에 대한 버전 범위를 지정했다고 가정해 보겠습니다. 그러나 종속성에 문제가 발생하여 번들이 실제로 사용하는 종속성 버전을 확인해야 합니다. 확인하려면 Developer Console을 열고 **OSGi 번들** 탭에서 번들 이름을 클릭하여 번들 세부 정보에 액세스하고 **번들 가져오기** 아코디언을 사용하여 런타임 시 사용 중인 번들 버전 또는 패키지 버전을 확인합니다. 이 정보를 사용하여 Maven 종속성 버전 범위를 조정하거나 코드를 조정할 수 있습니다.

## Java 패키지 탭 {#java-packages}

**Java 패키지** 탭은 환경의 OSGi 시스템에서 활성 상태인 패키지를 검색하는 검색 필드를 제공합니다.

Developer Console UI의 ![Java 패키지 탭](/help/implementing/developing/introduction/assets/java-packages-dev-console-ui.png)

* 패키지를 내보내거나 제공하는 번들과 패키지를 가져오거나 사용하는 번들을 확인할 수 있습니다.
* 중복 패키지(동일한 패키지, 다른 버전)를 확인할 수도 있으므로 경우에 따라 문제가 발생할 수 있습니다.

**예제 사용 사례:** [동적 클래스 로더](https://sling.apache.org/apidocs/sling9/org/apache/sling/commons/classloader/DynamicClassLoaderManager.html)를 사용하는 사용자 지정 서비스가 버전을 지정하지 않고 클래스를 로드한다고 가정해 보겠습니다. 여러 번들이 서로 다른 버전을 내보내므로 구현이 달라져 동작이 변경됩니다. 기능 모델을 분석하지 않고 환경에 있는 패키지를 확인할 수 있습니다. 이 탭을 사용하여 패키지를 검색하고 내보낸 모든 버전을 볼 수 있으며 그런 다음 더 나은 버전 범위를 사용할 수 있습니다.

## 구성 탭 {#configurations}

**구성** 탭은 환경에서 활성화된 구성의 검색 가능한 목록을 제공합니다. 각 구성을 클릭하고 세부 정보 페이지를 보면 각 구성에서 제공하는 속성을 확인할 수 있습니다.

Developer Console UI의 ![구성 탭](/help/implementing/developing/introduction/assets/configurations-dev-console.png)

* **예제 사용 사례:** 지정한 구성이 실제로 환경에 있는지 확인하려고 합니다. 콘솔에서 **구성** 탭을 검색했는데 구성이 누락된 경우 기능 모델, 구성 실행 모드 또는 폴더를 확인할 수 있습니다.

## 서블릿 탭 {#servlets}

**서블릿** 탭에는 선택기를 사용하여 경로를 지정하고 GET 또는 POST를 사용하여 확장을 지정할 수 있는 검색 필드가 있습니다. 그런 다음 Sling에서 요청을 처리하는 기본 설정 순서대로 서블릿 목록을 제공합니다.

Developer Console UI의 ![서블릿 탭](/help/implementing/developing/introduction/assets/servlets-dev-console-ui.png)

**예제 사용 사례:** 요청 시 활성화하고 출력을 응답에 인쇄해야 하는 OSGi 서블릿이 있다고 가정해 보겠습니다. 그러나 예상 출력 대신 빈 응답이 표시됩니다. 더 구체적인 선택기, `resourceType`, 확장 또는 순위로 인해 일부 다른 서블릿이 서블릿보다 우선하는지 확인해야 합니다. 예상 경로를 검색하고 순위가 높은 다른 서블릿이 활성 상태임을 확인합니다. 그런 다음 예를 들어 선택기를 추가하여 서블릿의 등급을 늘릴 수 있는지 여부를 결정할 수 있습니다.

## 서비스 탭 {#services}

**서비스** 탭에서는 선택한 환경에 있는 서비스에 대한 개요를 제공하고 전체 텍스트 검색을 제공합니다.

Developer Console UI의 ![서비스 탭](/help/implementing/developing/introduction/assets/services-dev-console.png)

세부 정보를 보려면 서비스를 클릭하십시오.

## OSGi 구성 요소 탭 {#osgi-components}

**OSGi 구성 요소** 탭에서는 선택한 환경 유형에 있고 전체 텍스트 검색을 제공하는 OSGi 구성 요소에 대한 개요를 제공합니다. 환경에서 OSGi 구성 요소의 라이브 상태 및 이를 충족하는 서비스, 이를 제공하는 번들 및 활성화 유형(즉시 또는 지연)을 볼 수 있습니다.

Developer Console UI의 ![OSGi 구성 요소 탭](/help/implementing/developing/introduction/assets/osgi-components-dev-console.png)

* **사용 사례 1 예:** 예기치 않은 동작이 발생했으므로 구성을 통해 활성화된 구성 요소가 특정 환경에서 활성화되었는지 확인해야 합니다. 검색에서 구성 요소를 조회하고 구성 요소가 활성 상태인지 확인하면 됩니다.
* **사용 사례 2 예:** 환경에서 사용할 수 있는 기본 구성 요소를 확인하고 Adobe Experience Manager as a Cloud Service에 대해 자세히 알아보기 위해 해당 구성 요소가 지원하는 서비스를 식별해 보겠습니다. 구성 요소 목록에서 구성 요소를 확인할 수 있습니다.

## 통합 탭 {#integrations}

**통합** 탭에서 관리자는 서비스 자격 증명과 개발자 토큰을 생성하고 이름을 바꾸고 삭제할 수 있습니다.

Developer Console UI의 ![통합 탭](/help/implementing/developing/introduction/assets/integrations-dev-console-ui.png)

## 저장소 탭 {#repository}

**저장소** 탭에서 [저장소 브라우저](/help/implementing/developing/tools/repository-browser.md)를 엽니다.

## 상태 덤프/쿼리 탭 {#status-dumps-queries}

**상태 덤프/쿼리** 탭에서는 번들, 패키지, 구성, 서비스, 구성 요소, 슬링 작업 또는 Oak 정의의 현재 상태에 대한 전체 텍스트 또는 JSON 덤프를 다운로드할 수 있습니다.

Developer Console UI의 ![상태 덤프/쿼리 탭](/help/implementing/developing/introduction/assets/status-dumps-queries.png)

[쿼리 성능 도구를 열 수도 있습니다.](/help/operations/query-and-indexing-best-practices.md#query-performance-tool)

* **예제 사용 사례:** 이 탭은 예기치 않은 상태가 발생하여 다른 개발자에게 전달하거나 문서화하려는 경우 특히 유용합니다. 덤프를 다운로드하면 나중에 참조할 수 있도록 상태의 스냅샷이 제공됩니다.
