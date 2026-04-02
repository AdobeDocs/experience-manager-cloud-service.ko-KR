---
title: 프로덕션 파이프라인 추가
description: 프로덕션 파이프라인을 추가하여 코드를 빌드하고 프로덕션 환경에 배포하는 방법을 알아봅니다.
index: true
exl-id: 67edca16-159e-469f-815e-d55cf9063aa4
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Developer
source-git-commit: fc9f7f10d1797bda5f31d82005b0afbb6ea1e644
workflow-type: tm+mt
source-wordcount: '1903'
ht-degree: 27%

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

프로그램을 설정하고 [!UICONTROL Cloud Manager] UI를 사용하는 환경이 하나 이상 있는 경우 다음 단계에 따라 프로덕션 파이프라인을 추가할 준비가 된 것입니다.

>[!TIP]
>
>프론트엔드 파이프라인을 구성하기 전에 [AEM 빠른 사이트 생성 여정](/help/journey-sites/quick-site/overview.md)에서 사용하기 쉬운 AEM 빠른 사이트 생성 도구에 대한 전체 안내서를 참조하십시오. 이 여정을 사용하면 AEM 사이트의 프론트엔드 개발을 간소화하여 AEM 백엔드 지식 없이 사이트를 빠르게 사용자 정의할 수 있습니다.

1. [experience.adobe.com](https://experience.adobe.com)에서 Cloud Manager에 로그인합니다.
1. **바로 가기** 섹션에서 **Experience Manager**&#x200B;를 클릭합니다.
1. 왼쪽 사이드 패널에서 **Cloud Manager**&#x200B;를 클릭합니다.
1. 원하는 조직을 선택합니다.
1. **내 프로그램** 콘솔에서 프로그램을 클릭합니다.

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

   * **[전체 스택 코드를 사용하고 있습니다](#full-stack-code)**
   * **[타깃팅된 배포 파이프라인 구성](#targeted-deployment)**

파이프라인 유형에 대한 자세한 내용은 [CI/CD 파이프라인](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md)을 참조하십시오.

프로덕션 파이프라인 생성을 완료하는 단계는 선택한 소스 코드 유형에 따라 다릅니다. 파이프라인 구성을 완료할 수 있도록 위의 링크를 따라 이 문서의 다음 섹션으로 이동합니다.

### 전체 스택 코드를 사용하고 있습니다. {#full-stack-code}

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

   * **Git 분기** - 드롭다운 목록에서 선택한 저장소에서 파이프라인을 빌드할 분기를 선택합니다. 기본값은 `main`입니다. 파이프라인은 선택한 분기를 빌드 및 배포의 소스로 사용합니다. 필요한 경우 **새로 고침**&#x200B;을 클릭하여 선택한 저장소에 대해 사용 가능한 분기 목록을 업데이트합니다. 최근에 만든 분기가 목록에 표시되지 않는 경우 이 옵션을 사용합니다.
   * **전략 작성**
      * **전체 빌드** - 매번 저장소의 모든 모듈을 빌드합니다.
      * BETA **스마트 빌드** - 마지막 커밋 이후 변경된 모듈만 빌드합니다.<br>비프로덕션 파이프라인에서 [스마트 빌드를 사용하는 방법에 대해 자세히 알아보세요](#about-smart-build-non-production-pipeline).

        >[!IMPORTANT]
        >
        >스마트 빌드는 코드 품질 파이프라인 및 개발 전체 스택 코드 배포 파이프라인에만 사용할 수 있습니다.
   * **웹 계층 구성 무시** - 이 옵션을 선택하면 파이프라인이 웹 계층 구성을 배포하지 않습니다.
   * **프로덕션에 배포하기 전에 일시 중지** - 프로덕션에 배포하기 전에 파이프라인을 일시 중지합니다.
   * **예약됨** - 사용자가 예약된 프로덕션 배포를 사용하도록 설정할 수 있습니다.

   ![전체 스택 코드](/help/implementing/cloud-manager/assets/configure-pipeline/production-pipeline-fullstack.png)

1. **계속**&#x200B;을 클릭하여 경험 감사에 항상 포함되어야 하는 경로를 정의할 수 있는 **경험 감사** 탭으로 이동합니다.

   ![경험 감사 추가](/help/implementing/cloud-manager/assets/configure-pipeline/add-prod-audit.png)

1. 경험 감사에 포함될 경로를 제공합니다.

   * 자세한 내용은 [경험 감사 테스트](/help/implementing/cloud-manager/reports/report-experience-audit.md#configuration)를 참조하십시오.

1. 파이프라인을 저장하려면 **저장**&#x200B;을 클릭합니다.

파이프라인이 실행되면 경험 감사를 위해 구성된 경로가 성능, 접근성, SEO, 모범 사례 및 PWA 테스트를 기반으로 제출되고 평가됩니다. 자세한 내용은 [경험 감사 결과 이해](/help/implementing/cloud-manager/reports/report-experience-audit.md)를 참조하십시오.

파이프라인이 저장되고 이제 **프로그램 개요** 페이지의 **파이프라인** 카드에서 [파이프라인을 관리](managing-pipelines.md)할 수 있습니다.

### 타깃팅된 배포를 사용 중입니다. {#targeted-deployment}

타깃팅된 배포는 AEM 애플리케이션의 선택한 부분에 대해서만 코드를 배포합니다. 이러한 배포에서는 다음 코드 유형 중 하나를 **포함**&#x200B;하도록 선택할 수 있습니다.

* **구성** - AEM 환경의 다양한 기능에 대한 설정을 구성합니다.
   * 로그 전달, 제거 관련 유지 관리 작업 및 다양한 CDN 구성을 포함하여 지원되는 구성 목록을 보고 올바르게 배포되도록 저장소에서 관리하려면 [구성 파이프라인 사용](/help/operations/config-pipeline.md)을 참조하십시오.
   * 타깃팅된 배포 파이프라인을 실행할 때 구성이 파이프라인에 정의된 환경, 저장소 및 분기에 저장되면 배포됩니다.
   * 언제든지 환경당 하나의 구성 파이프라인만 있을 수 있습니다.
* **Edge Delivery Services 구성 파이프라인 구성** - Edge Delivery 구성 파이프라인에는 별도의 개발, 스테이징 및 프로덕션 환경이 없습니다. AEM as a Cloud Service에서 변경 사항은 개발, 단계 및 프로덕션 계층을 통해 이동됩니다. 반면 Edge Delivery 구성 파이프라인은 Cloud Manager에 등록된 모든 Edge Delivery Sites 도메인에 해당 구성을 직접 적용합니다. 자세한 내용은 [Edge Delivery 파이프라인 추가](/help/implementing/cloud-manager/configuring-pipelines/configuring-edge-delivery-pipeline.md)를 참조하세요.
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

## BETA: 프로덕션 파이프라인에서의 Smart Build 사용 정보{#about-smart-build-production-pipeline}

Cloud Manager의 **스마트 빌드**&#x200B;는 프로덕션 파이프라인에 최적화된 빌드 전략입니다. 스마트 빌드는 모듈을 캐시하고 마지막으로 성공한 실행 이후 변경된 모듈만 다시 빌드하여 빌드 시간을 줄입니다. 변경되지 않은 모듈은 캐시에서 재사용되는 반면 수정된 모듈 및 그 의존성만 재구축되므로 반복적인 개발 워크플로의 효율성을 향상시킵니다.

>[!NOTE]
>
>이 베타에 관심이 있으세요? Adobe OrgID 및 프로그램 ID를 첨부한 이메일을 [beta_quickbuild_cmpipelines@adobe.com](mailto:beta_quickbuild_cmpipelines@adobe.com)으로 보내 주시기 바랍니다.

>[!IMPORTANT]
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

일반적으로 많은 독립 모듈이 있는 프로젝트는 가장 큰 개선 효과를 볼 수 있습니다.

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
* 프로덕션 파이프라인을 편집하여 언제든지 **전체 빌드**(으)로 다시 전환할 수 있습니다.

예기치 않은 빌드 동작이 발생하면 특정 모듈에 대해 캐싱을 사용하지 않도록 설정하거나 빌드 전략을 **전체 빌드**(으)로 일시적으로 전환해 보십시오.

### 스마트 빌드 문제 해결{#smart-build-troubleshoot}

| 문제 | 제안된 해결 방법 |
| --- | --- |
| 빌드 결과가 일관되지 않음 | · 영향을 받는 모듈에 대한 캐싱을 비활성화합니다.<br>· 플러그 인 동작(특히 `exec`/`antrun` 플러그 인)을 확인합니다. |
| 성능 향상 없음 | · 여러 번의 실행이 발생했는지 확인합니다(캐시 준비).<br>· 대부분의 모듈이 자주 변경되는지 확인합니다. |
| 예기치 않은 아티팩트 또는 누락된 변경 사항 | · 변경 사항이 Maven 종속성 추적을 벗어나는지 여부를 검토합니다.<br>· 확인에 **전체 빌드**&#x200B;를 사용합니다. |

스마트 빌드를 사용하려면 [프로덕션 파이프라인 추가](#adding-production-pipeline)를 참조하십시오.

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
