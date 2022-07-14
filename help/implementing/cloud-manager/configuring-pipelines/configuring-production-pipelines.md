---
title: 프로덕션 파이프라인 구성
description: 코드를 프로덕션 환경에 빌드 및 배포하도록 프로덕션 파이프라인을 구성하는 방법을 알아봅니다.
index: true
exl-id: 67edca16-159e-469f-815e-d55cf9063aa4
source-git-commit: 13cb8ae059f0a77e517d2e64eae96a08f88ac075
workflow-type: tm+mt
source-wordcount: '1462'
ht-degree: 0%

---

# 프로덕션 파이프라인 구성 {#configure-production-pipeline}

코드를 프로덕션 환경에 빌드 및 배포하도록 프로덕션 파이프라인을 구성하는 방법을 알아봅니다. 프로덕션 파이프라인은 코드를 먼저 스테이지 환경에 배포하며, 승인 시 프로덕션 환경에 동일한 코드를 배포합니다.

사용자에게 **[배포 관리자](/help/onboarding/cloud-manager-introduction.md#role-based-permissions)** 프로덕션 파이프라인을 구성하는 역할입니다.

>[!NOTE]
>
>프로그램 만들기가 완료되고, Git 리포지토리에 하나 이상의 분기가 있으며, 프로덕션 및 스테이징 환경 세트가 작성될 때까지 프로덕션 파이프라인을 설정할 수 없습니다.

코드를 배포하기 전에 [!UICONTROL Cloud Manager].

>[!NOTE]
>
>다음을 수행할 수 있습니다 [파이프라인 설정 편집](managing-pipelines.md) 초기 설정 후.

## 새 프로덕션 파이프라인 추가 {#adding-production-pipeline}

프로그램을 설정하고 을(를) 사용하여 하나 이상의 환경을 만들면 [!UICONTROL Cloud Manager] UI에서 다음 단계를 수행하여 프로덕션 파이프라인을 추가할 준비가 되었습니다.

>[!TIP]
>
>프런트엔드 파이프라인을 구성하기 전에 [AEM 빠른 사이트 만들기 여정](/help/journey-sites/quick-site/overview.md) 사용하기 쉬운 AEM 빠른 사이트 작성 도구를 통해 종단 간 안내서용. 이 여정을 사용하면 AEM Site의 프런트 엔드 개발을 간소화할 수 있으므로 AEM 백 엔드 지식 없이 사이트를 신속하게 사용자 정의할 수 있습니다.

1. Cloud Manager에 로그인 위치 [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) 적절한 조직과 프로그램을 선택합니다.

1. 로 이동합니다 **파이프라인** 카드로부터 **프로그램 개요** 페이지를 클릭하고 **추가** 을(를) 선택합니다. **프로덕션 파이프라인 추가**.

   ![프로그램 관리자 개요의 파이프라인 카드](/help/implementing/cloud-manager/assets/configure-pipeline/add-prod-1.png)

1. 다음 **프로덕션 파이프라인 추가** 대화 상자가 표시됩니다. 다음을 제공합니다. **파이프라인 이름** 를 클릭하여 다음 옵션과 함께 파이프라인을 식별합니다. 클릭 **계속**.

   **배포 트리거** - 파이프라인을 시작할 배포 트리거를 정의할 때 다음 옵션이 있습니다.

   * **수동** - 이 옵션을 사용하여 파이프라인을 수동으로 시작합니다.
   * **Git 변경 시** - 이 옵션은 구성된 git 분기에 커밋이 추가될 때마다 CI/CD 파이프라인을 시작합니다. 이 옵션을 사용하면 필요에 따라 파이프라인을 수동으로 시작할 수 있습니다.

   **중요한 지표 실패 동작** - 파이프라인을 설정하거나 편집하는 동안 **배포 관리자** 는 품질 게이트에서 중요한 오류가 발생할 때 파이프라인의 동작을 정의할 수 있는 옵션을 제공합니다. 사용 가능한 옵션은 다음과 같습니다.

   * **매번 질문하기** - 기본 설정이며 중요한 오류에 대해 수동으로 개입해야 합니다.
   * **즉시 실패** - 이 옵션을 선택하면 중요한 오류가 발생할 때마다 파이프라인이 취소됩니다. 이것은 기본적으로 사용자가 각 실패를 수동으로 거부하는 것을 에뮬레이션합니다.
   * **즉시 계속** - 이 옵션을 선택하면 중요한 오류가 발생할 때마다 파이프라인이 자동으로 진행됩니다. 이것은 기본적으로 사용자가 각 실패를 수동으로 승인하는 것입니다.

   ![프로덕션 파이프라인 구성](/help/implementing/cloud-manager/assets/configure-pipeline/production-pipeline-configuration.png)

1. 설정 **소스 코드** 탭에서 파이프라인이 해당 코드를 검색해야 하는 위치와 파이프라인의 코드 유형을 정의해야 합니다.

   * **[프런트 엔드 코드](#front-end-code)**
   * **[전체 스택 코드](#full-stack-code)**
   * **[웹 계층 구성](#web-tier-config)**

프로덕션 파이프라인 생성을 완료하는 단계는 의 옵션에 따라 달라집니다 **소스 코드** 선택하셨습니다. 위의 링크를 따라 이 문서의 다음 섹션으로 이동하여 파이프라인 구성을 완료합니다.

### 프런트 엔드 코드 {#front-end-code}

프런트 엔드 코드 파이프라인은 하나 이상의 클라이언트측 UI 애플리케이션을 포함하는 프런트 엔드 코드 빌드를 배포합니다. 문서를 참조하십시오 [CI/CD 파이프라인](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md#front-end) 를 참조하십시오.

프런트 엔드 코드 프로덕션 파이프라인의 구성을 완료하려면 다음 단계를 따르십시오.

1. 설정 **소스 코드** 탭에서 다음 옵션을 정의해야 합니다.

   * **저장소** - 이 옵션은 파이프라인에서 코드를 검색해야 하는 Git 리포지토리를 정의합니다.
   >[!TIP]
   > 
   >문서를 참조하십시오 [저장소 추가 및 관리](/help/implementing/cloud-manager/managing-code/cloud-manager-repositories.md) cloud Manager에서 저장소를 추가하고 관리하는 방법을 알아봅니다.

   * **Git 분기** - 이 옵션은 선택한 파이프라인의 어느 분기에서 코드를 검색해야 하는지를 정의합니다.
      * 분기 이름의 처음 몇 문자를 입력하고 이 필드의 자동 완성 기능이 선택한 데 도움이 되는 일치하는 분기를 찾습니다.
   * **코드 위치** - 이 옵션은 파이프라인이 코드를 검색해야 하는 선택한 리포지토리의 분기에서 경로를 정의합니다.
   * **프로덕션에 배포하기 전에 일시 정지** - 이 옵션은 프로덕션에 배포하기 전에 파이프라인을 일시 중지합니다.

   ![프런트 엔드 코드](/help/implementing/cloud-manager/assets/configure-pipeline/production-pipeline-frontend.png)

1. 클릭 **저장** 를 클릭하여 파이프라인을 저장합니다.

파이프라인이 저장되므로 이제 다음을 수행할 수 있습니다 [파이프라인 관리](managing-pipelines.md) on **파이프라인** 카드 **프로그램 개요** 페이지.

### 전체 스택 코드 {#full-stack-code}

전체 스택 코드 파이프라인은 HTTPD/Dispatcher 구성과 함께 하나 이상의 AEM 서버 애플리케이션을 포함하는 백 엔드 및 프런트 엔드 코드 빌드를 동시에 배포합니다. 문서를 참조하십시오 [CI/CD 파이프라인](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md#full-stack-pipeline) 를 참조하십시오.

>[!NOTE]
>
>선택한 환경에 대해 전체 스택 코드 파이프라인이 이미 존재하는 경우 이 선택이 비활성화됩니다.

전체 스택 코드 프로덕션 파이프라인의 구성을 완료하려면 다음 단계를 따르십시오.

1. 설정 **소스 코드** 탭에서 다음 옵션을 정의해야 합니다.

   * **저장소** - 이 옵션은 파이프라인에서 코드를 검색해야 하는 Git 리포지토리를 정의합니다.
   >[!TIP]
   > 
   >문서를 참조하십시오 [저장소 추가 및 관리](/help/implementing/cloud-manager/managing-code/cloud-manager-repositories.md) cloud Manager에서 저장소를 추가하고 관리하는 방법을 알아봅니다.

   * **Git 분기** - 이 옵션은 선택한 파이프라인의 어느 분기에서 코드를 검색해야 하는지를 정의합니다.
      * 분기 이름의 처음 몇 문자를 입력하고 이 필드의 자동 완성 기능이 선택한 데 도움이 되는 일치하는 분기를 찾습니다.
   * **코드 위치** - 이 옵션은 파이프라인이 코드를 검색해야 하는 선택한 리포지토리의 분기에서 경로를 정의합니다.
   * **프로덕션에 배포하기 전에 일시 정지** - 이 옵션은 프로덕션에 배포하기 전에 파이프라인을 일시 중지합니다.
   * **예약됨** - 이 옵션을 사용하면 예약된 프로덕션 배포를 활성화할 수 있습니다.

   ![전체 스택 코드](/help/implementing/cloud-manager/assets/configure-pipeline/production-pipeline-fullstack.png)

1. 클릭 **계속** 앞으로 나아가다 **경험 감사** 탭에서 경험 감사에 항상 포함해야 하는 경로를 정의할 수 있습니다.

   ![경험 감사 추가](/help/implementing/cloud-manager/assets/configure-pipeline/add-prod-audit.png)

1. 경험 감사에 포함할 경로를 제공합니다.

   * 페이지 경로는 `/`.
   * 예를 들어 다음을 포함하려는 경우 `https://wknd.site/us/en/about-us.html` 경험 감사에서 경로를 입력합니다 `/us/en/about-us.html`.

   ![경험 감사 경로 정의](/help/implementing/cloud-manager/assets/configure-pipeline/add-prod-audit3.png)

1. 클릭 **페이지 추가** 및 경로는 환경의 주소로 자동으로 완료되고 경로 표에 추가됩니다.

   ![테이블에 경로 저장](/help/implementing/cloud-manager/assets/configure-pipeline/add-prod-audit4.png)

1. 이전 두 단계를 반복하여 필요한 경로를 계속 추가합니다.

   * 최대 25개의 경로를 추가할 수 있습니다.
   * 경로를 정의하지 않으면 기본적으로 사이트의 홈 페이지가 경험 감사에 포함됩니다.

1. 클릭 **저장** 를 클릭하여 파이프라인을 저장합니다.

경험 감사를 위해 구성된 경로는 서비스에 제출되고 파이프라인이 실행될 때 성능, 액세스 가능성, SEO(검색 엔진 최적화), 모범 사례 및 PWA(점진적 웹 앱) 테스트에 따라 평가됩니다. 을(를) 참조하십시오. [경험 감사 결과 이해](/help/implementing/cloud-manager/experience-audit-testing.md) 자세한 내용

파이프라인이 저장되므로 이제 다음을 수행할 수 있습니다 [파이프라인 관리](managing-pipelines.md) on **파이프라인** 카드 **프로그램 개요** 페이지.

### 웹 계층 구성 {#web-tier-config}

웹 계층 구성 파이프라인이 HTTPD/Dispatcher 구성을 배포합니다. 문서를 참조하십시오 [CI/CD 파이프라인](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md#web-tier-config-pipeline) 를 참조하십시오.

전체 스택 코드 프로덕션 파이프라인의 구성을 완료하려면 다음 단계를 따르십시오.

1. 설정 **소스 코드** 탭에서 다음 옵션을 정의해야 합니다.

   * **저장소** - 이 옵션은 파이프라인에서 코드를 검색해야 하는 Git 리포지토리를 정의합니다.
   >[!TIP]
   > 
   >문서를 참조하십시오 [저장소 추가 및 관리](/help/implementing/cloud-manager/managing-code/cloud-manager-repositories.md) cloud Manager에서 저장소를 추가하고 관리하는 방법을 알아봅니다.

   * **Git 분기** - 이 옵션은 선택한 파이프라인의 어느 분기에서 코드를 검색해야 하는지를 정의합니다.
      * 분기 이름의 처음 몇 문자를 입력하고 이 필드의 자동 완성 기능이 선택한 데 도움이 되는 일치하는 분기를 찾습니다.
   * **코드 위치** - 이 옵션은 파이프라인이 코드를 검색해야 하는 선택한 리포지토리의 분기에서 경로를 정의합니다.
      * 웹 계층 구성 파이프라인의 경우 일반적으로 다음을 포함하는 경로입니다 `conf.d`, `conf.dispatcher.d`, 및 `opt-in` 디렉토리.
      * 예를 들어, 프로젝트 구조가 [AEM 프로젝트 원형,](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html?lang=en) 경로는 다음과 같습니다. `/dispatcher/src`.
   * **프로덕션에 배포하기 전에 일시 정지** - 이 옵션은 프로덕션에 배포하기 전에 파이프라인을 일시 중지합니다.
   * **예약됨** - 이 옵션을 사용하면 예약된 프로덕션 배포를 활성화할 수 있습니다.

   ![웹 계층 코드](/help/implementing/cloud-manager/assets/configure-pipeline/production-pipeline-webtier.png)

1. 클릭 **저장** 를 클릭하여 파이프라인을 저장합니다.

>[!NOTE]
>
>환경에 기존 전체 스택 파이프라인을 배포하는 경우 동일한 환경에 대해 웹 계층 구성 파이프라인을 생성하면 전체 스택 파이프라인의 기존 웹 계층 구성이 무시됩니다.

파이프라인이 저장되므로 이제 다음을 수행할 수 있습니다 [파이프라인 관리](managing-pipelines.md) on **파이프라인** 카드 **프로그램 개요** 페이지.

## 디스패처 패키지 건너뛰기 {#skip-dispatcher-packages}

디스패처 패키지를 파이프라인의 일부로 작성했지만 빌드 저장소에 게시하지 않으려는 경우 게시를 비활성화할 수 있으므로 파이프라인 실행 시간이 줄어들 수 있습니다.

프로젝트를 통해 게시 디스패처 패키지를 비활성화하려면 다음 구성을 추가해야 합니다 `pom.xml` 파일. 환경 변수를 기반으로 합니다. 이 변수는 Cloud Manager 빌드 컨테이너에서 설정할 수 있는 플래그 역할을 하여 디스패처 패키지를 무시해야 하는 시기를 정의합니다.

```xml
<profile>
  <id>only-include-dispatcher-when-it-isnt-ignored</id>
  <activation>
    <property>
      <name>env.IGNORE_DISPATCHER_PACKAGES</name>
      <value>!true</value>
    </property>
  </activation>
  <modules>
    <module>dispatcher</module>
  </modules>
</profile>
```
