---
title: 프로덕션 파이프라인 추가
description: 프로덕션 파이프라인을 추가하여 코드를 빌드하고 프로덕션 환경에 배포하는 방법을 알아봅니다.
index: true
exl-id: 67edca16-159e-469f-815e-d55cf9063aa4
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 9cde6e63ec452161dbeb1e1bfb10c75f89e2692c
workflow-type: tm+mt
source-wordcount: '1314'
ht-degree: 39%

---


# 프로덕션 파이프라인 추가 {#configure-production-pipeline}

코드를 빌드하고 프로덕션 환경에 배포하기 위해 프로덕션 파이프라인을 구성하는 방법을 알아봅니다. 프로덕션 파이프라인은 먼저 코드를 스테이징 환경에 배포합니다. 승인 시 프로덕션 환경에 동일한 코드를 배포합니다.

프로덕션 파이프라인을 구성하려면 사용자에게 **[배포 관리자](/help/onboarding/cloud-manager-introduction.md#role-based-permissions)** 역할이 있어야 합니다.

>[!NOTE]
>
>다음과 같은 상황이 발생할 때까지 프로덕션 파이프라인을 설정할 수 없습니다.
>
>* 프로그램이 생성됩니다.
>* Git 저장소에는 분기가 하나 이상 있습니다.
>* 프로덕션 및 스테이징 환경이 생성됩니다.

코드 배포를 시작하기 전에 [!UICONTROL Cloud Manager]에서 파이프라인 설정을 구성하십시오.

>[!NOTE]
>
>초기 설정 후에 [파이프라인 설정을 편집](managing-pipelines.md)할 수 있습니다.

## 새 프로덕션 파이프라인 추가 {#adding-production-pipeline}

프로그램을 설정하고 [!UICONTROL Cloud Manager] UI를 사용하는 환경이 하나 이상 있는 경우 다음 단계에 따라 비프로덕션 파이프라인을 추가할 준비가 된 것입니다.

>[!TIP]
>
>프론트엔드 파이프라인을 구성하기 전에 [AEM 빠른 사이트 생성 여정](/help/journey-sites/quick-site/overview.md)에서 사용하기 쉬운 AEM 빠른 사이트 생성 도구에 대한 전체 안내서를 참조하십시오. 이 여정을 사용하면 AEM Site의 프론트엔드 개발을 간소화하여 백엔드 AEM에 대한 백엔드 지식 없이 사이트를 빠르게 사용자 정의할 수 있습니다.

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)에서 Cloud Manager에 로그인한 다음 적절한 조직 선택

1. **[내 프로그램](/help/implementing/cloud-manager/navigation.md#my-programs)** 콘솔에서 프로그램을 선택합니다.

1. **프로그램 개요** 페이지에서 **파이프라인** 카드로 이동한 다음 **추가**&#x200B;를 클릭하여 **프로덕션 파이프라인 추가**&#x200B;를 선택합니다.

   ![프로그램 관리자의 파이프라인 카드 개요](/help/implementing/cloud-manager/assets/configure-pipeline/add-prod-1.png)

1. **프로덕션 파이프라인 추가** 대화 상자가 표시됩니다. 파이프라인을 식별할 수 있도록 다음 옵션과 함께 **파이프라인 이름**&#x200B;을 입력합니다. **계속**&#x200B;을 클릭합니다.

   **배포 트리거** - 다음과 같은 옵션을 사용하여 배포 트리거를 정의하여 파이프라인을 시작할 수 있습니다.

   * **수동** - 파이프라인을 수동으로 시작합니다.
   * **Git 변경 시** - 구성된 Git 분기에 커밋이 추가될 때마다 CI/CD 파이프라인을 시작합니다. 이 옵션을 사용하면 필요에 따라 파이프라인을 수동으로 시작할 수 있습니다.

   **중요한 지표 장애 비헤이비어** - 파이프라인 설정 또는 편집 중에 **배포 관리자**&#x200B;는 품질 게이트에서 중요한 장애가 발생했을 때 파이프라인의 비헤이비어를 정의할 수 있는 옵션을 제공합니다. 사용 가능한 옵션은 다음과 같습니다.

   * **매번 묻기** - 기본 설정입니다. 중요한 장애가 발생하면 수동으로 개입해야 합니다.
   * **즉시 실패** - 이 옵션을 선택하면 중요한 오류가 발생할 때마다 파이프라인이 취소됩니다. 이 프로세스는 본질적으로 각 실패를 수동으로 거부하는 사용자를 에뮬레이션하는 것입니다.
   * **즉시 계속** - 이 옵션을 선택하면 중요한 오류가 발생할 때마다 파이프라인이 자동으로 진행됩니다. 이 프로세스는 본질적으로 각 실패를 수동으로 승인하는 사용자를 에뮬레이션하는 것입니다.

   ![프로덕션 파이프라인 구성](/help/implementing/cloud-manager/assets/configure-pipeline/production-pipeline-configuration.png)

1. **Source 코드** 탭에서 파이프라인이 처리해야 하는 코드 유형을 선택합니다.

   * **[전체 스택 코드 파이프라인 구성](#full-stack-code)**
   * **[타깃팅된 배포 파이프라인 구성](#targeted-deployment)**

파이프라인 유형에 대한 자세한 내용은 [CI/CD 파이프라인](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md)을 참조하십시오.

프로덕션 파이프라인 생성을 완료하는 단계는 선택한 소스 코드 유형에 따라 다릅니다. 파이프라인 구성을 완료할 수 있도록 위의 링크를 따라 이 문서의 다음 섹션으로 이동합니다.

### 전체 스택 코드 파이프라인 구성 {#full-stack-code}

전체 스택 코드 파이프라인은 HTTPD/Dispatcher 구성과 함께 하나 이상의 AEM 서버 애플리케이션을 포함하는 백엔드 및 프론트엔드 코드 빌드를 동시에 배포합니다.

>[!NOTE]
>
>선택한 환경에 대한 전체 스택 코드 파이프라인이 이미 있는 경우, 이 선택이 비활성화됩니다.

**전체 스택 코드 파이프라인을 구성하려면:**

1. **Source 코드** 탭에서 다음 옵션을 정의합니다.

   * **저장소** - 파이프라인에서 코드를 검색해야 하는 Git 저장소를 정의합니다.

   >[!TIP]
   > 
   >Cloud Manager에서 저장소를 추가하고 관리하는 방법은 [저장소 추가 및 관리](/help/implementing/cloud-manager/managing-code/managing-repositories.md)를 참조하십시오.

   * **Git 분기** - 선택한 파이프라인에서 코드를 검색해야 하는 분기를 정의합니다.
분기 이름의 처음 몇 문자를 입력하면 이 필드의 자동 완성 기능이 일치하는 분기를 찾아 선택하는 데 도움이 됩니다.
   * **웹 계층 구성 무시** - 이 옵션을 선택하면 파이프라인이 웹 계층 구성을 배포하지 않습니다.
   * **프로덕션에 배포하기 전에 일시 중지** - 프로덕션에 배포하기 전에 파이프라인을 일시 중지합니다.
   * **예약됨** - 사용자가 예약된 프로덕션 배포를 사용하도록 설정할 수 있습니다.

   ![전체 스택 코드](/help/implementing/cloud-manager/assets/configure-pipeline/production-pipeline-fullstack.png)

1. **계속**&#x200B;을 클릭하여 경험 감사에 항상 포함되어야 하는 경로를 정의할 수 있는 **경험 감사** 탭으로 이동합니다.

   ![경험 감사 추가](/help/implementing/cloud-manager/assets/configure-pipeline/add-prod-audit.png)

1. 경험 감사에 포함될 경로를 제공합니다.

   * 자세한 내용은 [경험 감사 테스트](/help/implementing/cloud-manager/experience-audit-dashboard.md#configuration)를 참조하십시오.

1. 파이프라인을 저장하려면 **저장**&#x200B;을 클릭합니다.

파이프라인이 실행되면 경험 감사를 위해 구성된 경로가 성능, 접근성, SEO, 모범 사례 및 PWA 테스트를 기반으로 제출되고 평가됩니다. 자세한 내용은 [경험 감사 결과 이해](/help/implementing/cloud-manager/experience-audit-dashboard.md)를 참조하십시오.

파이프라인이 저장되고 이제 **프로그램 개요** 페이지의 **파이프라인** 카드에서 [파이프라인을 관리](managing-pipelines.md)할 수 있습니다.

### 타깃팅된 배포 파이프라인 구성 {#targeted-deployment}

타깃팅된 배포는 AEM 애플리케이션의 선택한 부분에 대해서만 코드를 배포합니다. 이러한 배포에서는 다음 코드 유형 중 하나를 **포함**&#x200B;하도록 선택할 수 있습니다.

* **구성** - AEM 환경의 다양한 기능에 대한 설정을 구성합니다.
   * 로그 전달, 제거 관련 유지 관리 작업 및 다양한 CDN 구성을 포함하여 지원되는 구성 목록을 보고 올바르게 배포되도록 저장소에서 관리하려면 [구성 파이프라인 사용](/help/operations/config-pipeline.md)을 참조하십시오.
   * 타깃팅된 배포 파이프라인을 실행할 때 파이프라인에 정의된 환경, 저장소 및 분기에 저장된 경우 구성이 배포됩니다.
   * 언제든지 환경당 하나의 구성 파이프라인만 있을 수 있습니다.
* **프론트엔드 코드** - AEM 애플리케이션의 프론트엔드에 맞게 JavaScript 및 CSS를 구성합니다.
   * 프론트엔드 파이프라인을 사용하면 프론트엔드 개발자에게 더 많은 독립성을 부여하고 개발 프로세스를 가속화할 수 있습니다.
   * 이 프로세스의 잠재력을 최대한 활용하기 위해 알아야 할 몇 가지 고려 사항 및 이 프로세스가 작동하는 방식에 대한 자세한 내용은 [프론트엔드 파이프라인으로 Sites 개발](/help/implementing/developing/introduction/developing-with-front-end-pipelines.md) 문서를 참조하십시오.
* **웹 계층 구성** - 웹 페이지를 저장하고 처리하고 클라이언트에 전달하도록 Dispatcher 속성을 구성합니다.
   * 자세한 내용은 [CI/CD 파이프라인](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md#web-tier-config-pipelines) 문서를 참조하십시오.
   * 선택한 환경에 대한 웹 계층 코드 파이프라인이 있는 경우, 이 선택이 비활성화됩니다.
   * 기존 전체 스택 파이프라인이 있는 환경에 대한 웹 계층 구성 파이프라인을 만드는 경우 전체 스택 파이프라인의 웹 계층 구성이 무시됩니다. 이 변경 사항은 해당 환경의 웹 계층 구성에만 영향을 줍니다.

>[!NOTE]
>
>웹 계층 및 구성 파이프라인은 비공개 저장소에서 지원되지 않습니다. 제한 사항에 대한 자세한 내용 및 전체 목록은 [Cloud Manager에 개인 저장소 추가](/help/implementing/cloud-manager/managing-code/private-repositories.md)를 참조하십시오.

**대상 배포 파이프라인을 구성하려면:**

1. 필요한 배포 유형을 선택합니다.

![타깃팅된 배포 옵션](/help/implementing/cloud-manager/assets/configure-pipeline/prod-pipeline-targeted-deployment.png)

1. **적합한 배포 환경**&#x200B;을(를) 정의합니다.

   * 파이프라인이 배포 파이프라인인 경우 배포할 환경을 선택해야 합니다.

1. **Source 코드**&#x200B;에서 다음 옵션을 정의합니다.

   * **저장소** - 이 옵션은 파이프라인에서 코드를 검색해야 하는 git 저장소를 정의합니다.

   >[!TIP]
   > 
   >Cloud Manager에서 저장소를 추가하고 관리하는 방법은 [저장소 추가 및 관리](/help/implementing/cloud-manager/managing-code/managing-repositories.md)를 참조하십시오.

   * **Git 분기** - 이 옵션은 선택한 파이프라인에서 코드를 검색해야 하는 분기를 정의합니다.
      * 분기 이름의 처음 몇 글자와 이 필드의 자동 완성 기능을 입력합니다. 선택할 수 있는 일치하는 분기를 찾습니다.
   * **코드 위치** - 이 옵션은 파이프라인이 코드를 검색해야 하는 선택한 저장소 분기의 경로를 정의합니다.
   * **프로덕션에 배포 전 일시 중지** - 이 옵션은 프로덕션에 배포하기 전에 파이프라인을 일시 중지합니다.
   * **예약됨** - 사용자가 예약된 프로덕션 배포를 사용하도록 설정할 수 있습니다. 웹 계층 대상 배포에만 사용할 수 있습니다.

   ![파이프라인 구성](/help/implementing/cloud-manager/assets/configure-pipeline/prod-pipeline-config-deployment.png)

1. **저장**&#x200B;을 클릭합니다.

파이프라인이 저장되고 이제 **프로그램 개요** 페이지의 **파이프라인** 카드에서 [파이프라인을 관리](managing-pipelines.md)할 수 있습니다.

## Dispatcher 패키지 건너뛰기 {#skip-dispatcher-packages}

스토리지를 빌드하는 데 Dispatcher 패키지를 게시하지 않고 파이프라인에서 빌드하려면 게시 옵션을 비활성화하면 됩니다. 이렇게 하면 파이프라인의 실행 시간을 줄이는 데 도움이 될 수 있습니다.

Dispatcher 패키지 게시를 비활성화하려면 프로젝트 `pom.xml` 파일을 통해 다음 구성을 추가해야 합니다. 환경 변수는 Cloud Manager 빌드 컨테이너에서 설정하는 플래그 역할을 하여 Dispatcher 패키지를 무시할 시기를 결정합니다.

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
