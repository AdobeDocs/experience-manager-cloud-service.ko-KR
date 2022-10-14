---
title: 비프로덕션 파이프라인 구성
description: 프로덕션 환경에 배포하기 전에 비프로덕션 파이프라인을 구성하여 코드 품질을 테스트하는 방법을 알아봅니다.
index: true
exl-id: eba608eb-a19e-4bff-82ff-05860ceabe6e
source-git-commit: 9804d9b71f082c3d4788667fdc3993af3b673588
workflow-type: tm+mt
source-wordcount: '1119'
ht-degree: 100%

---

# 비프로덕션 파이프라인 구성 {#configuring-non-production-pipelines}

프로덕션 환경에 배포하기 전에 비프로덕션 파이프라인을 구성하여 코드 품질을 테스트하는 방법을 알아봅니다.

## 비프로덕션 파이프라인 {#non-production-pipelines}

스테이징 및 프로덕션 환경에 배포하는 [프로덕션 파이프라인](#configuring-production-pipelines.md) 외에 비프로덕션 파이프라인을 설정하여 코드를 검증할 수도 있습니다.

비프로덕션 파이프라인에는 두 가지 유형이 있습니다.

* **코드 품질 파이프라인** - git 분기의 코드에 대해 코드 품질 스캔을 실행하고 빌드 및 코드 품질 단계를 실행합니다.
* **배포 파이프라인** - 이러한 파이프라인은 코드 품질 파이프라인과 같은 빌드 및 코드 품질 단계를 실행하는 것 외에도 코드를 비프로덕션 환경에 배포합니다.

>[!NOTE]
>
>초기 설정 후에 [파이프라인 설정을 편집](managing-pipelines.md)할 수 있습니다.

## 새 비프로덕션 파이프라인 추가 {#adding-non-production-pipeline}

프로그램을 설정하고 Cloud Manager UI를 사용하는 환경이 하나 이상 있는 경우 다음 단계에 따라 비프로덕션 파이프라인을 추가할 준비가 된 것입니다.

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)에서 Cloud Manager에 로그인한 다음 적절한 조직과 프로그램을 선택합니다.

1. Cloud Manager 홈 화면에서 **파이프라인** 카드에 액세스합니다. **+추가**&#x200B;를 클릭하고 **비프로덕션 파이프라인 추가**&#x200B;를 선택합니다.

   ![비프로덕션 파이프라인 추가](/help/implementing/cloud-manager/assets/configure-pipeline/nonprod-pipeline-add1.png)

1. **비프로덕션 파이프라인 추가** 대화 상자의 **구성** 탭에서 추가할 비프로덕션 파이프라인 유형(**코드 품질 파이프라인** 또는 **배포 파이프라인**)을 선택합니다.

   ![비프로덕션 파이프라인 추가 대화 상자](/help/implementing/cloud-manager/assets/configure-pipeline/non-prod-pipeline-config.png)

1. 파이프라인을 식별할 수 있도록 다음 추가 정보와 함께 **비프로덕션 파이프라인 이름**&#x200B;을 입력합니다.

   * **배포 트리거** - 다음과 같은 옵션을 사용하여 배포 트리거를 정의하여 파이프라인을 시작할 수 있습니다.

      * **수동** - 파이프라인을 수동으로 시작하려면 이 옵션을 사용합니다.
      * **Git 변경 시** - 이 옵션은 구성된 git 분기에 커밋이 추가될 때마다 CI/CD 파이프라인을 시작합니다. 이 옵션을 사용하면 필요에 따라 파이프라인을 수동으로 시작할 수 있습니다.

1. **계속**&#x200B;을 클릭합니다.

1. **비프로덕션 파이프라인 추가** 대화 상자의 **소스 코드** 탭에서 파이프라인이 처리해야 하는 코드 유형을 선택해야 합니다.

   * **[프론트엔드 코드](#front-end-code)**
   * **[전체 스택 코드](#full-stack-code)**
   * **[웹 계층 구성](#web-tier-config)**

비프로덕션 파이프라인 생성을 완료하는 단계는 선택한 **소스 코드** 옵션에 따라 다릅니다. 위의 링크를 따라 이 문서의 다음 섹션으로 이동하여 파이프라인 구성을 완료합니다.

### 프론트엔드 코드 {#front-end-code}

프론트엔드 코드 파이프라인은 하나 이상의 클라이언트측 UI 애플리케이션을 포함하는 프론트엔드 코드 빌드를 배포합니다. 이 파이프라인 유형에 대한 자세한 내용은 [CI/CD 파이프라인](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md#front-end) 문서를 참조하십시오.

프론트엔드 코드 비프로덕션 파이프라인의 구성을 완료하려면 다음 단계를 따릅니다.

1. **소스 코드** 탭에서 다음 옵션을 정의해야 합니다.

   * **적합한 배포 환경** - 파이프라인이 배포 파이프라인인 경우 배포할 환경을 선택해야 합니다.
   * **저장소** - 이 옵션은 파이프라인에서 코드를 검색해야 하는 git 저장소를 정의합니다.

   >[!TIP]
   > 
   >Cloud Manager에서 저장소를 추가하고 관리하는 방법은 [저장소 추가 및 관리](/help/implementing/cloud-manager/managing-code/cloud-manager-repositories.md) 문서를 참조하십시오.

   * **Git 분기** - 이 옵션은 선택한 파이프라인에서 코드를 검색해야 하는 분기를 정의합니다.
      * 분기 이름의 처음 몇 글자를 입력하면 이 필드의 자동 완성 기능이 일치하는 분기를 찾아 선택하는 데 도움이 됩니다.
   * **코드 위치** - 이 옵션은 파이프라인이 코드를 검색해야 하는 선택한 저장소 분기의 경로를 정의합니다.

   ![프론트엔드 파이프라인](/help/implementing/cloud-manager/assets/configure-pipeline/non-prod-pipeline-front-end.png)

1. **저장**&#x200B;을 클릭합니다.

파이프라인이 저장되고 이제 **프로그램 개요** 페이지의 **파이프라인** 카드에서 [파이프라인을 관리](managing-pipelines.md)할 수 있습니다.

### 전체 스택 코드 {#full-stack-code}

전체 스택 코드 파이프라인은 HTTPD/Dispatcher 구성과 함께 하나 이상의 AEM 서버 애플리케이션을 포함하는 백엔드 및 프론트엔드 코드 빌드를 동시에 배포합니다. 이 파이프라인 유형에 대한 자세한 내용은 [CI/CD 파이프라인](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md#full-stack-pipeline) 문서를 참조하십시오.

>[!NOTE]
>
>선택한 환경에 대한 전체 스택 코드 파이프라인이 이미 있는 경우 이 선택이 비활성화됩니다.

전체 스택 코드 비프로덕션 파이프라인의 구성을 완료하려면 다음 단계를 따릅니다.

1. **소스 코드** 탭에서 다음 옵션을 정의해야 합니다.

   * **적합한 배포 환경** - 파이프라인이 배포 파이프라인인 경우 배포할 환경을 선택해야 합니다.
   * **저장소** - 이 옵션은 파이프라인에서 코드를 검색해야 하는 git 저장소를 정의합니다.

   >[!TIP]
   > 
   >Cloud Manager에서 저장소를 추가하고 관리하는 방법은 [저장소 추가 및 관리](/help/implementing/cloud-manager/managing-code/cloud-manager-repositories.md) 문서를 참조하십시오.

   * **Git 분기** - 이 옵션은 선택한 파이프라인에서 코드를 검색해야 하는 분기를 정의합니다.
      * 분기 이름의 처음 몇 글자를 입력하면 이 필드의 자동 완성 기능이 일치하는 분기를 찾아 선택하는 데 도움이 됩니다.
   * **웹 계층 구성 무시** - 이 옵션을 선택하면 파이프라인이 웹 계층 구성을 배포하지 않습니다.

   ![전체 스택 파이프라인](/help/implementing/cloud-manager/assets/configure-pipeline/non-prod-pipeline-full-stack.png)

1. **저장**&#x200B;을 클릭합니다.

파이프라인이 저장되고 이제 **프로그램 개요** 페이지의 **파이프라인** 카드에서 [파이프라인을 관리](managing-pipelines.md)할 수 있습니다.

### 웹 계층 구성 {#web-tier-config}

웹 계층 구성 파이프라인 HTTPD/Dispatcher 구성을 배포합니다. 이 파이프라인 유형에 대한 자세한 내용은 [CI/CD 파이프라인](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md#web-tier-config-pipeline) 문서를 참조하십시오.

>[!NOTE]
>
>선택한 환경에 대한 웹 계층 코드 파이프라인이 이미 있는 경우 이 선택이 비활성화됩니다.

웹 계층 코드 비프로덕션 파이프라인의 구성을 완료하려면 다음 단계를 따릅니다.

1. **소스 코드** 탭에서 다음 옵션을 정의해야 합니다.

   * **적합한 배포 환경** - 파이프라인이 배포 파이프라인인 경우 배포할 환경을 선택해야 합니다.
   * **저장소** - 이 옵션은 파이프라인에서 코드를 검색해야 하는 git 저장소를 정의합니다.

   >[!TIP]
   > 
   >Cloud Manager에서 저장소를 추가하고 관리하는 방법은 [저장소 추가 및 관리](/help/implementing/cloud-manager/managing-code/cloud-manager-repositories.md) 문서를 참조하십시오.

   * **Git 분기** - 이 옵션은 선택한 파이프라인에서 코드를 검색해야 하는 분기를 정의합니다.
   * **코드 위치** - 이 옵션은 파이프라인이 코드를 검색해야 하는 선택한 저장소 분기의 경로를 정의합니다.
      * 웹 계층 구성 파이프라인의 경우 일반적으로 `conf.d`, `conf.dispatcher.d` 및 `opt-in` 디렉터리가 포함된 경로입니다.
      * 예를 들어 프로젝트 구조가 [AEM Project Archetype](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html?lang=ko)에서 생성된 경우 경로는 `/dispatcher/src`입니다.

   ![웹 계층 파이프라인](/help/implementing/cloud-manager/assets/configure-pipeline/non-prod-pipeline-web-tier.png)

1. **저장**&#x200B;을 클릭합니다.

>[!NOTE]
>
>기존 전체 스택 파이프라인이 환경에 배포되어 있는 경우 동일한 환경에 대한 웹 계층 구성 파이프라인을 생성하면 전체 스택 파이프라인의 기존 웹 계층 구성이 무시됩니다.

파이프라인이 저장되고 이제 **프로그램 개요** 페이지의 **파이프라인** 카드에서 [파이프라인을 관리](managing-pipelines.md)할 수 있습니다.

## Dispatcher 패키지 건너뛰기 {#skip-dispatcher-packages}

Dispatcher 패키지를 파이프라인의 일부로 빌드하고 싶지만 스토리지를 빌드하기 위해 게시하지 않으려는 경우 게시를 비활성화하면 파이프라인 실행 기간이 단축될 수 있습니다.

Dispatcher 패키지 게시를 비활성화하려면 프로젝트 `pom.xml` 파일을 통해 다음 구성을 추가해야 합니다. 이는 환경 변수를 기반으로 하며, Cloud Manager 빌드 컨테이너에서 디스패처 패키지를 무시해야 하는 시기를 정의할 때 설정할 수 있는 플래그 역할을 합니다.

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
