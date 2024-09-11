---
title: AEM as a Cloud Service Developer Console(Beta)
description: CRX/DE Lite 및 AEM as a Cloud Service Developer Console에 대해 알아보기
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 16379d9cb7cdf876502205c12a233a95b410a67a
workflow-type: tm+mt
source-wordcount: '1202'
ht-degree: 0%

---


# AEM as a Cloud Service Developer Console(Beta) {#developer-console}

>[!NOTE]
>
>이 문서에서는 현재 베타 버전이며 일부 고객이 클래식 UI 상단에 있는 버튼을 클릭하여 사용할 수 있는 AEM Cloud Service Developer Console에 대해 개선된 환경에 대해 설명합니다. `aemcs-new-devconsole-ui-beta@adobe.com`님에게 보낼 수 있는 피드백에 감사드립니다. 클래식 AEM Developer Console에 대한 자세한 내용은 [이 문서](/help/implementing/developing/introduction/development-guidelines.md#crxde-lite-and-developer-console)를 참조하십시오.

## AEM as a Cloud Service 개발 도구 {#aem-as-a-cloud-service-development-tools}

>[!NOTE]
>AEM as a Cloud Service Developer Console을 비슷한 이름의 [*Adobe Developer Console*](https://developer.adobe.com/developer-console/)와 혼동하면 안 됩니다.
>

고객은 작성 계층의 개발 환경에서 CRXDE lite에 액세스할 수 있지만, 스테이지나 프로덕션 환경에서는 액세스할 수 없습니다. 변경할 수 없는 저장소(`/libs`, `/apps`)를 런타임에 쓸 수 없으므로 이 작업을 시도하면 오류가 발생합니다.

대신 AEM as a Cloud Service Developer Console에서 저장소 브라우저를 시작하여 작성자, 게시 및 미리보기 계층의 모든 환경에 대해 저장소에 대한 읽기 전용 보기를 제공할 수 있습니다. 자세한 내용은 [저장소 브라우저](/help/implementing/developing/tools/repository-browser.md)를 참조하세요.

AEM as a Cloud Service 개발자 환경을 디버깅하기 위한 도구 세트는 RDE, 개발, 스테이지 및 프로덕션 환경용 AEM as a Cloud Service Developer Console에서 사용할 수 있습니다. URL은 다음과 같이 작성자 또는 Publish 서비스 URL을 조정하여 결정할 수 있습니다.

`https://dev-console/-<namespace>.<cluster>.dev.adobeaemcloud.com`

바로 가기로는 다음 Cloud Manager CLI 명령을 사용하여 아래에 설명된 환경 매개 변수를 기반으로 AEM as a Cloud Service Developer Console을 시작할 수 있습니다.

`aio cloudmanager:open-developer-console <ENVIRONMENTID> --programId <PROGRAMID>`

자세한 내용은 [릴리스 정보](/help/release-notes/home.md)를 참조하세요.

개발자는 상태 정보를 생성하고 다양한 리소스를 해결할 수 있다.

사용 가능한 상태 정보에는 아래에서 보듯이 번들, 구성 요소, OSGI 구성, oak 색인, OSGI 서비스 및 Sling 작업의 상태가 포함됩니다.

### OSGi 번들 {#osgi-bundles}

![개발 콘솔의 새 OSGi 번들 화면](/help/implementing/developing/introduction/assets/osgi-bundles.png)

* 이렇게 하면 선택한 환경 유형에 배포되는 OSGI 번들에 대한 개요가 생성됩니다. 전체 텍스트 검색이 가능합니다.
* 환경의 실제 번들 상태 정보를 가져오는 것이 유용합니다. 내보낸 패키지, 가져온 패키지, 사용된 서비스 등과 같은 정보를 가져올 수 있습니다.
* 개발자는 실제 환경에서 번들이 예상대로 작동하는지 확인하려고 합니다.
* **예제 사용 사례:** 종속 항목의 버전 범위가 번들에 지정되어 있습니다. 종속성에서 문제가 발생합니다. 번들에 연결할 종속 항목의 버전을 확인하려고 합니다. 이를 확인하려면 번들 세부 정보로 이동한 다음 번들/패키지 가져오기를 사용하여 런타임 시 어떤 번들 버전 또는 패키지 버전이 사용되고 있는지 확인합니다. 이 정보를 사용하여 Maven 종속성 버전 범위를 조정하거나 코드를 조정할 수 있습니다.

### Java 패키지 {#java-packages}

![개발 콘솔 UI의 Java 패키지 탭](/help/implementing/developing/introduction/assets/java-packages-dev-console-ui.png)

* 환경의 OSGI 시스템에서 활성 상태인 패키지를 검색하는 데 사용할 수 있는 검색 프롬프트를 제공합니다. 이 위치에서 패키지를 내보내거나 제공하는 번들과 패키지를 가져오거나 사용하는 번들을 확인할 수 있습니다. 중복 패키지(동일한 패키지, 다른 버전)를 확인할 수도 있으므로 경우에 따라 문제가 발생할 수 있습니다.
* **예제 사용 사례:** [동적 클래스 로더](https://sling.apache.org/apidocs/sling9/org/apache/sling/commons/classloader/DynamicClassLoaderManager.html)을(를) 사용하는 사용자 지정 서비스에서 버전을 지정하지 않고 클래스를 로드하고 있습니다. 다른 버전을 가진 여러 번들이 이 클래스를 내보내 구현이 달라지고 동작이 변경됩니다. 개발자는 기능 모델을 분석하지 않고 환경에 있는 패키지를 확인하려고 하므로 이 패키지를 검색하고 내보내는 모든 버전을 확인합니다. 이렇게 하면 더 나은 버전 범위를 입력하라는 정보가 제공됩니다.

### 서블릿 {#servlets}

![개발 콘솔 UI의 서블릿 탭](/help/implementing/developing/introduction/assets/servlets-dev-console-ui.png)

* 선택기를 사용하여 경로를 지정하고 GET 또는 POST을 사용하여 확장을 지정할 수 있는 검색 프롬프트를 제공합니다. 그런 다음 Sling에서 요청을 처리할 기본 설정 순서로 서블릿의 결과를 제공합니다.
* **예제 사용 사례:** 요청 시 활성화하고 응답에 인쇄해야 하는 OSGI 서블릿이 있지만 대신 빈 응답이 반환됩니다. 더 구체적인 선택기, `resourceType`, 확장 또는 순위로 인해 일부 다른 서블릿이 서블릿보다 우선하는지 확인해야 합니다. 예상 경로를 검색하고 순위가 높은 다른 서블릿이 활성 상태인지 확인합니다. 그런 다음, 예를 들어 선택기를 추가하여 위 서블릿을 순위로 가져올 수 있는지 여부를 결정합니다.

### 서비스 {#services}

![개발 콘솔 UI의 서비스 탭](/help/implementing/developing/introduction/assets/services-dev-console.png)

* OSGI 구성 요소 보기와 유사하지만 서비스를 기반으로 합니다. 특정 속성과 함께 제공되는 서비스를 빠르게 검색할 수 있습니다.

### OSGi 구성 요소 {#osgi-components}

개발 콘솔 UI의 ![OSGi 구성 요소 탭](/help/implementing/developing/introduction/assets/osgi-components-dev-console.png)

* 이렇게 하면 선택한 환경 유형에 있는 OSGI 구성 요소에 대한 개요가 생성됩니다. 전체 텍스트 검색이 가능합니다.
* 환경에서 OSGI 구성 요소의 라이브 상태를 가져올 수 있습니다. 어떤 서비스를 만족하는지, 해당 서비스를 제공하는 번들과 활성화 유형(즉시 또는 지연)을 확인할 수 있습니다.
* **예제 사용 사례 1:** 개발자는 예상한 동작을 얻지 못하기 때문에 구성으로 활성화된 구성 요소가 특정 환경에서 활성 상태인지 여부를 확인하려고 합니다. 검색에서 구성 요소를 조회하고 구성 요소가 활성 상태인지 확인하기만 하면 됩니다.
* **예제 사용 사례 2:** 환경에 있는 기본 구성 요소와 해당 구성 요소가 충족하는 서비스를 확인하고 Adobe Experience Manager as a Cloud Service에 대해 자세히 알아보십시오. 구성 요소 목록에서 체크 아웃할 수 있습니다.

### 통합 {#integrations}

![개발 콘솔 UI의 통합 탭](/help/implementing/developing/introduction/assets/integrations-dev-console-ui.png)

* 관리자에게 서비스 자격 증명 및 개발자 토큰을 생성하고, 이름을 바꾸고, 삭제할 수 있는 기능을 제공합니다.

### 저장소 {#repository}

* [저장소 브라우저](/help/implementing/developing/tools/repository-browser.md)를 엽니다.

### 상태 덤프/쿼리 {#status-dumps-queries}

![개발 콘솔 UI의 상태 덤프/쿼리 탭](/help/implementing/developing/introduction/assets/status-dumps-queries.png)

* 번들, 패키지, 구성, 서비스, 구성 요소, 슬링 작업 또는 oak 정의의 현재 상태에 대한 전체 텍스트 또는 JSON 덤프를 제공합니다.
* 이 기능은 특히 개발자가 예기치 않은 상태를 발견하여 다른 개발자에게 전달하거나 문서화하려는 경우에 유용합니다. 덤프를 다운로드하면 나중에 참조할 수 있도록 상태의 스냅샷이 제공됩니다.

### 구성 {#configurations}

![개발 콘솔 UI의 구성 탭](/help/implementing/developing/introduction/assets/configurations-dev-console.png)

* 이렇게 하면 환경에서 활성화된 구성의 검색 가능한 목록을 제공합니다. 세부 정보 페이지를 확인하여 구성에서 제공하는 속성을 확인할 수 있습니다.
* **예제 사용 사례:** 개발자가 지정한 구성이 실제로 환경에 있는지 확인하려고 합니다. 구성이 부족한 경우 피쳐 모델이나 구성 실행 모드 또는 폴더를 확인할 수 있습니다.

프로덕션 프로그램의 경우 AEM as a Cloud Service Developer Console에 대한 액세스는 Adobe Admin Console의 &quot;Cloud Manager - 개발자 역할&quot;에 의해 정의되지만, 샌드박스 프로그램의 경우 AEM as a Cloud Service Developer ConsoleAEM as a Cloud Service 에 대한 액세스 권한을 제공하는 제품 프로필이 있는 모든 사용자가 사용할 수 있습니다. 모든 프로그램의 경우, &quot;Cloud Manager - 개발자 역할&quot;이 상태 덤프에 필요하며, 작성자와 게시 서비스 모두에서 데이터를 보려면 저장소 브라우저와 사용자가 AEM 사용자 또는 AEM 관리자 제품 프로필에도 정의되어야 합니다. 사용자 권한 설정에 대한 자세한 내용은 [Cloud Manager 설명서](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/requirements/setting-up-users-and-roles.html)를 참조하세요.