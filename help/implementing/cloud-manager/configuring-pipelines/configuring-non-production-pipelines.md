---
title: 비프로덕션 파이프라인 추가
description: 프로덕션 환경에 배포하기 전에 비프로덕션 파이프라인을 추가하여 코드 품질을 테스트하는 방법을 알아봅니다.
index: true
exl-id: eba608eb-a19e-4bff-82ff-05860ceabe6e
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Developer
source-git-commit: 2556f606db8b74bce25cd504a183abdc43e31227
workflow-type: tm+mt
source-wordcount: '1727'
ht-degree: 21%

---


# 비프로덕션 파이프라인 추가 {#configuring-non-production-pipelines}

프로그램을 설정하고 Cloud Manager UI에서 하나 이상의 환경을 만든 후 비프로덕션 파이프라인을 추가할 수 있습니다. 이러한 파이프라인을 사용하면 프로덕션 환경에 배포하기 전에 코드 품질을 테스트할 수 있습니다.

비프로덕션 파이프라인을 구성하려면 사용자에게 **[배포 관리자](/help/onboarding/cloud-manager-introduction.md#role-based-permissions)** 역할이 있어야 합니다.

>[!NOTE]
>
>초기 설정 후에 [파이프라인 설정을 편집](managing-pipelines.md)할 수 있습니다.

## 새 비프로덕션 파이프라인 추가 {#adding-non-production-pipeline}

프로그램을 설정하고 Cloud Manager UI에서 환경을 하나 이상 만든 후 비프로덕션 파이프라인을 추가할 수 있습니다. 프로덕션 환경에 배포하기 전에 이러한 파이프라인을 사용하여 코드 품질을 테스트합니다.

**새 비프로덕션 파이프라인을 추가하려면:**

1. [experiece.adobe.com](https://experience.adobe.com)에서 Cloud Manager에 로그인합니다.
1. **바로 가기** 섹션에서 **Experience Manager**&#x200B;를 클릭합니다.
1. 왼쪽 사이드 패널에서 **Cloud Manager**&#x200B;를 클릭합니다.
1. 원하는 조직을 선택합니다.
1. **내 프로그램** 콘솔에서 프로그램을 클릭합니다.
1. 왼쪽 패널에서 **파이프라인**&#x200B;을 클릭합니다.
1. 오른쪽 상단 모서리의 **파이프라인** 페이지에서 **파이프라인 추가** > **비프로덕션 파이프라인 추가**&#x200B;를 클릭합니다.

   ![비프로덕션 파이프라인 추가](/help/implementing/cloud-manager/assets/configure-pipeline/nonprod-pipeline-add1.png)

1. **비프로덕션 파이프라인 추가** 대화 상자의 **구성** 탭에서 만들 비프로덕션 파이프라인 중 하나를 선택합니다.

   * **코드 품질 파이프라인** - 환경에 배포하지 않고 GIT 분기에 코드를 빌드하고 단위 테스트를 실행하고 코드 품질을 평가하는 파이프라인을 만듭니다.
   * **배포 파이프라인** - 코드를 빌드하고, 단위 테스트를 실행하고, 코드 품질을 평가하고, 비프로덕션 환경에 배포하는 파이프라인을 만듭니다.

   ![비프로덕션 파이프라인 추가 대화 상자](/help/implementing/cloud-manager/assets/configure-pipeline/non-prod-pipeline-config.png)

1. **파이프라인 구성** 섹션의 **비프로덕션 파이프라인 이름** 필드에 비프로덕션 파이프라인에 대한 설명을 입력합니다.
1. **배포 옵션** 섹션에서 사용할 다음 배포 트리거 중 하나를 선택합니다.

   * **수동** - 파이프라인을 수동으로 시작할 수 있습니다.
   * **Git 변경 시** - 구성된 Git 분기에 커밋이 추가될 때 파이프라인을 시작합니다. 이 옵션을 사용하면 필요에 따라 파이프라인을 수동으로 시작할 수 있습니다.

1. 사용하려는 **중요한 지표 오류 동작**&#x200B;을 선택하십시오.

   * **매번 묻기** - 이 비헤이비어는 기본 설정이며 중요한 장애에 대해 수동 개입이 필요합니다.
   * **즉시 실패** - 이 옵션을 선택하면 중요한 오류가 발생할 때마다 파이프라인이 취소됩니다. 각 실패를 수동으로 거부하는 사용자를 에뮬레이션합니다.
   * **즉시 계속** - 이 옵션을 선택하면 중요한 오류가 발생할 때마다 파이프라인이 자동으로 계속됩니다. 기본적으로 각 실패를 수동으로 승인하는 사용자를 에뮬레이션합니다.

1. **계속**&#x200B;을 클릭합니다.

1. 비프로덕션 파이프라인의 구성을 완료하는 데 사용하는 나머지 단계는 사용하려는 소스 코드 유형에 따라 다릅니다.
**비프로덕션 파이프라인 추가** 대화 상자의 **Source 코드** 탭에서 비프로덕션 파이프라인이 처리해야 하는 코드 유형을 선택합니다.

   * **[전체 스택 코드를 사용하고 있습니다](#full-stack-code)**
   * **[타깃팅된 배포를 사용하고 있습니다](#targeted-deployment)**

   파이프라인 유형에 대한 자세한 내용은 [CI/CD 파이프라인](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md)을 참조하십시오.


### 전체 스택 코드를 사용하고 있습니다. {#full-stack-code}

전체 스택 코드 파이프라인은 HTTPD/Dispatcher 구성과 함께 하나 이상의 AEM 서버 애플리케이션을 포함하는 백엔드 및 프론트엔드 코드 빌드를 동시에 배포합니다.

>[!NOTE]
>
>선택한 환경에 대한 전체 스택 코드 파이프라인이 있는 경우, 이 선택이 비활성화됩니다.

전체 스택 코드 비프로덕션 파이프라인의 구성을 완료하려면 다음을 수행합니다.

1. **Source 코드** 섹션에서 다음 옵션을 정의합니다.

   * **적합한 배포 환경** - 비프로덕션 파이프라인을 편집할 때만 사용할 수 있습니다. 파이프라인이 배포 파이프라인인 경우 배포할 환경을 선택해야 합니다.
   * **저장소** - 드롭다운 목록에서 파이프라인이 소스로 사용하는 Git 저장소를 선택합니다. Cloud Manager은 여기에서 선택한 저장소에서 코드를 빌드합니다.

     >[!TIP]
     > 
     >Cloud Manager에서 저장소를 추가하고 관리하는 방법은 [저장소 추가 및 관리](/help/implementing/cloud-manager/managing-code/managing-repositories.md)를 참조하십시오.

   * **Git 분기** - 드롭다운 목록에서 선택한 저장소에서 파이프라인을 빌드할 분기를 선택합니다. 기본값은 `main`입니다. 파이프라인은 선택한 분기를 빌드 및 배포의 소스로 사용합니다. 필요한 경우 **새로 고침**&#x200B;을 클릭하여 선택한 저장소에 대해 사용 가능한 분기 목록을 업데이트합니다. 최근에 만든 분기가 목록에 표시되지 않는 경우 이 옵션을 사용합니다.
   * **전략 작성**
      * **전체 빌드** - 매번 저장소의 모든 모듈을 빌드합니다.
      * BETA **스마트 빌드** - 마지막 커밋 이후 변경된 모듈만 빌드합니다.<br>비프로덕션 파이프라인에서 [스마트 빌드를 사용하는 방법에 대해 자세히 알아보세요](#about-smart-build).

        >[!IMPORTANT]
        >
        >스마트 빌드는 코드 품질 파이프라인 및 개발 전체 스택 코드 배포 파이프라인에만 사용할 수 있습니다.

   * **웹 계층 구성 무시** 확인란 - 이 확인란을 선택하면 파이프라인이 웹 계층 구성을 배포하지 않습니다.

1. **파이프라인** 섹션에서 파이프라인이 배포 파이프라인인 경우 테스트 단계를 실행하도록 선택할 수 있습니다. 이 단계에서 활성화하려는 옵션을 확인합니다. 옵션을 선택하지 않으면 파이프라인 실행 중에 테스트 단계가 표시되지 않습니다.

   * **제품 기능 테스트** - 개발 환경에 대해 [제품 기능 테스트](/help/implementing/cloud-manager/functional-testing.md#product-functional-testing)를 실행합니다.
   * **사용자 지정 기능 테스트** - 개발 환경에 대해 [사용자 지정 기능 테스트](/help/implementing/cloud-manager/functional-testing.md#custom-functional-testing)를 실행합니다.
   * **사용자 지정 UI 테스트** - 사용자 지정 응용 프로그램에 대해 [사용자 지정 UI 테스트](/help/implementing/cloud-manager/ui-testing.md)를 실행합니다.
   * **경험 감사** - [경험 감사 실행](/help/implementing/cloud-manager/reports/report-experience-audit.md)

   ![전체 스택 파이프라인](/help/implementing/cloud-manager/assets/configure-pipeline/non-prod-pipeline-full-stack.png)

1. **저장**&#x200B;을 클릭합니다.

파이프라인이 저장되었으며 이제 [파이프라인을 관리]&#x200B;(managing-pipe)할 수 있습니다.
**프로그램 개요** 페이지의 **파이프라인** 카드의 lines.md).

### 타깃팅된 배포를 사용 중입니다. {#targeted-deployment}

타깃팅된 배포는 AEM 애플리케이션의 선택한 부분에 대해서만 코드를 배포합니다. 이러한 배포에서는 다음 코드 유형 중 하나를 **포함**&#x200B;하도록 선택할 수 있습니다.

![타깃팅된 배포 옵션](/help/implementing/cloud-manager/assets/configure-pipeline/non-prod-pipeline-targeted-deployment1.png)

<!--
* **Config** - Configure settings for various features in your AEM environment.
  * See [Using Config Pipelines](/help/operations/config-pipeline.md) for a list of supported configurations, which include log forwarding, purge-related maintenance tasks, and various CDN configurations, and to manage them in your repository so they are deployed properly.
  * When running a targeted deployment pipeline, configurations are deployed, provided they are saved to the environment, repository, and branch you defined in the pipeline.
  * At any time, there can only be one config pipeline per environment.
* **Configure Edge Delivery Services config pipeline** - Edge Delivery Configuration Pipelines do not have separate development, staging, and production environments. In AEM as a Cloud Service, changes move through development, stage, and production tiers. In contrast, an Edge Delivery Configuration Pipeline applies its configuration directly to all Edge Delivery Sites domains registered in Cloud Manager. To learn more, see [Add an Edge Delivery Pipeline](/help/implementing/cloud-manager/configuring-pipelines/configuring-edge-delivery-pipeline.md).
-->


* **프론트엔드 코드** - AEM 애플리케이션의 프론트엔드에 맞게 JavaScript 및 CSS를 구성합니다.
   * 프론트엔드 파이프라인을 사용하면 프론트엔드 개발자에게 더 많은 독립성을 부여하고 개발 프로세스를 가속화할 수 있습니다.
   * 이 프로세스의 잠재력을 최대한 활용하기 위해 알아야 할 몇 가지 고려 사항 및 이 프로세스가 작동하는 방식에 대한 자세한 내용은 [프론트엔드 파이프라인으로 Sites 개발](/help/implementing/developing/introduction/developing-with-front-end-pipelines.md) 문서를 참조하십시오.
* **웹 계층 구성** - 웹 페이지를 저장하고 처리하고 클라이언트에 전달하도록 Dispatcher 속성을 구성합니다.
   * 자세한 내용은 [CI/CD 파이프라인](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md#web-tier-config-pipelines) 문서를 참조하십시오.
   * 선택한 환경에 대한 웹 계층 코드 파이프라인이 있는 경우, 이 선택이 비활성화됩니다.
   * 전체 스택 파이프라인이 이미 환경에 배포된 경우에도 동일한 환경에 대한 웹 계층 구성 파이프라인을 만들 수 있습니다. 이 경우 Cloud Manager에서는 전체 스택 파이프라인의 웹 계층 구성을 무시합니다.

     >[!NOTE]
     >
     >웹 계층 및 구성 파이프라인은 비공개 저장소에서 지원되지 않습니다. 제한 사항에 대한 자세한 내용 및 전체 목록은 [Cloud Manager에 개인 저장소 추가](/help/implementing/cloud-manager/managing-code/private-repositories.md)를 참조하십시오.

<!--
The steps to complete the creation of your non-production, targeted deployment pipeline are the same once you choose a deployment type.

1. Choose which deployment type you require.

![Targeted deployment options](/help/implementing/cloud-manager/assets/configure-pipeline/non-prod-pipeline-targeted-deployment.png)

1. Define the **Eligible Deployment Environments**.

   * If your pipeline is a deployment pipeline, you must select to which environments it should deploy.
-->

1. **Source 코드** 섹션에서 다음 옵션을 정의합니다.

   * **저장소** - 이 옵션은 비프로덕션 파이프라인이 코드를 검색해야 하는 GIT 저장소를 정의합니다.

     >[!TIP]
     > 
     >Cloud Manager에서 저장소를 추가하고 관리하는 방법은 [저장소 추가 및 관리](/help/implementing/cloud-manager/managing-code/managing-repositories.md)를 참조하십시오.

   * **Git 분기** - 이 옵션은 선택한 파이프라인에서 코드를 검색해야 하는 분기를 정의합니다. 분기 이름의 처음 몇 글자와 이 필드의 자동 완성 기능을 입력합니다. 선택할 수 있는 일치하는 분기를 찾습니다.
   * **코드 위치** - 이 옵션은 파이프라인이 코드를 검색해야 하는 선택한 저장소 분기의 경로를 정의합니다.

<!--
   * **Pipeline** - For front-end non-production pipelines, you have the option to enable **[Experience Audit](/help/implementing/cloud-manager/reports/report-experience-audit.md)**.
   
   ![Config pipeline](/help/implementing/cloud-manager/assets/configure-pipeline/non-prod-pipeline-config-deployment-experience-audit.png)
-->

1. 경험 감사를 활성화한 경우 **계속**&#x200B;을 클릭하여 경험 감사에 항상 포함되어야 하는 경로를 정의할 수 있는 **경험 감사** 탭으로 이동합니다.

   * **경험 감사**&#x200B;를 사용하도록 설정한 경우 구성 방법에 대한 자세한 내용은 [경험 감사](/help/implementing/cloud-manager/reports/report-experience-audit.md) 문서를 참조하십시오.
   * 그렇지 않은 경우 이 단계를 건너뜁니다.

1. **저장**&#x200B;을 클릭하여 파이프라인을 저장합니다.

파이프라인이 저장되고 이제 **프로그램 개요** 페이지의 **파이프라인** 카드에서 [파이프라인을 관리](managing-pipelines.md)할 수 있습니다.


## 비프로덕션 파이프라인에서의 Smart Build 사용 정보{#about-smart-build}

Cloud Manager의 **스마트 빌드**&#x200B;는 비프로덕션 파이프라인에 최적화된 빌드 전략입니다. 스마트 빌드는 모듈을 캐시하고 마지막으로 성공한 실행 이후 변경된 모듈만 다시 빌드하여 빌드 시간을 줄입니다. 변경되지 않은 모듈은 캐시에서 재사용되는 반면 수정된 모듈 및 그 의존성만 재구축되므로 반복적인 개발 워크플로의 효율성을 향상시킵니다.

스마트 빌드는 현재 다음에 대해서만 사용할 수 있습니다.

* 코드 품질 파이프라인.
* 개발 전체 스택 배포 파이프라인.

>[!NOTE]
>
>Smart Build를 활성화한 후 첫 번째 실행은 캐시가 비어 있으므로 전체 빌드와 같이 작동합니다.

다음과 같은 경우에는 스마트 빌드를 사용하는 것이 좋습니다.
* 빈번한 증분 변경을 적극적으로 개발하고 커밋하고 있습니다.
* 프로젝트에 여러 Maven 모듈이 포함되어 있습니다.
* 전체 빌드는 시간이 오래 걸립니다.

다음과 같은 경우에는 스마트 빌드가 항상 이상적이지 않습니다.
* 빌드는 Maven의 종속성 그래프 외부에서 작업을 수행하는 플러그인에 크게 의존합니다.
* 모든 실행 시 전체 재구축 유효성 검사가 필요합니다.

### 빌드 성능 이해{#smart-build-performance}

Smart Build를 사용하여 얻을 수 있는 성능 이익은 다음을 포함한 몇 가지 요인에 따라 달라집니다.

* 프로젝트의 모듈 수입니다.
* 코드 변경 빈도 및 범위입니다.
* 모듈 간 종속성 분포.

일반적으로 많은 독립 모듈이 있는 프로젝트에서는 개선 사항이 가장 많이 이루어집니다.

### 모듈별 캐시 옵트아웃{#smart-build-cache-optout}

Smart Build에서는 특정 모듈에 대한 캐싱을 비활성화할 수 있는 세분화된 제어를 제공합니다. 이 기능은 특정 모듈이 다음과 같은 경우 유용합니다.

* `exec-maven-plugin` 또는 `maven-antrun-plugin`과(와) 같은 플러그인을 사용합니다.
* Maven 종속성으로 추적되지 않는 파일 작업을 수행합니다.
* 캐시된 콘텐츠는 일관되지 않은 결과를 생성합니다.

### 모듈에 대한 캐싱 비활성화{#smart-build-disable-caching}

영향을 받는 모듈의 `pom.xml`에 다음 속성을 추가할 수 있습니다.

```xml
<properties>
  <maven.build.cache.enabled>false</maven.build.cache.enabled>
</properties>
```

이 구문은 모듈이 모든 파이프라인 실행에 대해 다시 빌드되도록 하는 반면 다른 모듈은 캐싱의 이점을 계속 사용합니다.

### Smart Build 사용 시 제한 사항 및 고려 사항{#smart-build-limitations}

Smart Build를 사용할 때는 다음 사항에 유의하십시오.

* Smart Build는 Maven 종속성 분석을 사용합니다.
* 종속성 그래프 외부의 변경 사항은 재빌드를 트리거하지 않을 수 있습니다.
* 일부 플러그인은 캐싱과 완전히 호환되지 않을 수 있습니다.
* 비프로덕션 파이프라인을 편집하여 언제든지 **전체 빌드**(으)로 다시 전환할 수 있습니다.

예기치 않은 빌드 동작이 발생하면 특정 모듈에 대해 캐싱을 사용하지 않도록 설정하거나 빌드 전략을 **전체 빌드**(으)로 일시적으로 전환해 보십시오.

### 스마트 빌드 문제 해결{#smart-build-troubleshoot}

| 문제 | 제안된 해결 방법 |
| --- | --- |
| 빌드 결과가 일관되지 않음 | · 영향을 받는 모듈에 대한 캐싱을 비활성화합니다.<br>· 플러그 인 동작(특히 `exec`/`antrun` 플러그 인)을 확인합니다. |
| 성능 향상 없음 | · 여러 번의 실행이 발생했는지 확인합니다(캐시 준비).<br>· 대부분의 모듈이 자주 변경되는지 확인합니다. |
| 예기치 않은 아티팩트 또는 누락된 변경 사항 | · 변경 사항이 Maven 종속성 추적을 벗어나는지 여부를 검토합니다.<br>· 확인에 **전체 빌드**&#x200B;를 사용합니다. |

스마트 빌드를 사용하려면 [비프로덕션 파이프라인 추가](#adding-non-production-pipeline)를 참조하십시오.











<!--
## Add a non-production pipeline {#adding-non-production-pipeline}

Once you have set up your program and have at least one environment using the Cloud Manager UI, you are ready to add a non-production pipeline by following these steps.

1. Sign into Cloud Manager at [experiece.adobe.com](https://experience.adobe.com).
1. In the **Quick access** section, click **Experience Manager**.
1. In the left side panel, click **Cloud Manager**.
1. Select an organization that you want.
1. On the **My Programs** console, click a program. 

1. Access the **Pipelines** card from the Cloud Manager home screen. Click **+Add** and select **Add Non-Production Pipeline**. 

   ![Add non-production pipeline](/help/implementing/cloud-manager/assets/configure-pipeline/nonprod-pipeline-add1.png)

1. On the **Configuration** tab of the **Add Non-Production Pipeline** dialog, select the type of non-production pipeline you with to add.

   * **Code Quality Pipeline** - Create a pipeline that builds your code, runs unit tests, and evaluates code quality but does NOT deploy.
   * **Deployment Pipeline** - Create a pipeline that builds your code, runs unit tests, evaluates code quality, and deploys to an environment.

   ![Add Non-Production pipeline dialog](/help/implementing/cloud-manager/assets/configure-pipeline/non-prod-pipeline-config.png)

1. Provide a **Non-Production Pipeline Name** to identify your pipeline along with the following additional information.

   * **Deployment Trigger** - You have the following options when defining the deployment triggers to start the pipeline.
   
     * **Manual** - Use this option to start the pipeline manually.
     * **On Git Changes** - This option starts the CI/CD pipeline whenever commits are added to the configured Git branch. With this option, you can still start the pipeline manually as required.

1. If you choose to create a **Deployment Pipeline**, you must also define the **Important Metric Failures Behavior**.

   * **Ask every time** - This behavior is the default setting and requires manual intervention on any important failure.
   * **Fail Immediately** - If selected, the pipeline is canceled whenever an important failure occurs. It is essentially emulating a user manually rejecting each failure.
   * **Continue Immediately** - If selected, the pipeline procedes automatically whenever an important failure occurs. It is essentially emulating a user manually approving each failure.

1. Click **Continue**.

1. On the **Source Code** tab of the **Add Non-Production Pipeline** dialog, you must select which type of code the pipeline should process.

   * **[Full Stack Code](#full-stack-code)**
   * **[Targeted deployment](#targeted-deployment)**

See [CI/CD Pipelines](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md) for more information about the types of pipelines.

The steps to complete the creation of your non-production pipeline vary depending on the type of source code you selected. Follow the links above to jump to the next section of this document so you can complete the configuration of your pipeline.

### Full Stack Code {#full-stack-code}

A full-stack code pipeline simultaneously deploys back-end and front-end code builds containing one or more AEM server applications along with HTTPD/Dispatcher configuration.

>[!NOTE]
>
>If a full-stack code pipeline exists for the selected environment, this selection is disabled.

To finish the configuration of the full-stack code non-production pipeline, follow these steps.

1. On the **Source Code** tab, you must define the following options.

   * **Eligible Deployment Environments** - If your pipeline is a deployment pipeline, you must select to which environments it should deploy.
   * **Repository** - This option defines from which git repo that the pipeline should retrieve the code.

   >[!TIP]
   > 
   >See [Adding and Managing Repositories](/help/implementing/cloud-manager/managing-code/managing-repositories.md) so you can learn how to add and manage repositories in Cloud Manager.

   * **Git Branch** - This option defines from which branch in the selected pipeline should retrieve the code.
     * Enter the first few characters of the branch name and the auto-complete feature of this field. It helps you find the matching branches that you can select.
   * **Ignore Web Tier Configuration** - When checked, the pipeline does not deploy your web tier configuration.
   * **Pipeline** - If your pipeline is a deployment pipeline, you can choose to run a testing phase. Check the options that you want to enable in this phase. If none of the options are selected, the testing phase is not displayed during the pipeline's run.

     * **Product Functional Testing** - Execute [product functional tests](/help/implementing/cloud-manager/functional-testing.md#product-functional-testing) against the development environment.
     * **Custom Functional Testing** - Execute [custom functional tests](/help/implementing/cloud-manager/functional-testing.md#custom-functional-testing) against the development environment.
     * **Custom UI Testing** - Execute [custom UI tests](/help/implementing/cloud-manager/ui-testing.md) for custom applications.
     * **Experience Audit** - Execute [Experience Audit](/help/implementing/cloud-manager/reports/report-experience-audit.md)

   ![Full-stack pipeline](/help/implementing/cloud-manager/assets/configure-pipeline/non-prod-pipeline-full-stack.png)

1. Click **Save**.

The pipeline is saved and you can now [manage your pipelines](managing-pipelines.md) on the **Pipelines** card on the **Program Overview** page.

-->



## Dispatcher 패키지 제외 {#exclude-dispatcher-packages}

Dispatcher 패키지를 파이프라인에서 빌드하고 싶지만 스토리지를 빌드하기 위해 업로드하지 않으려면 게시를 비활성화합니다. 이렇게 하면 파이프라인의 실행 시간을 단축할 수 있습니다.

Dispatcher 패키지 게시를 비활성화하려면 프로젝트 `pom.xml` 파일에 다음 구성을 추가하십시오. Cloud Manager 빌드 컨테이너에서 환경 변수를 설정하여 Dispatcher 패키지를 무시할 때 플래그를 지정합니다. 파이프라인은 이 플래그를 읽고 그에 따라 이를 무시합니다.

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
