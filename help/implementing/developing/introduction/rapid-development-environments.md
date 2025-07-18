---
title: 신속한 개발 환경
description: 클라우드 환경에서 신속한 개발 반복을 위해 빠른 개발 환경을 사용하는 방법에 대해 알아봅니다.
exl-id: 1e9824f2-d28a-46de-b7b3-9fe2789d9c68
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 5db419e674ceb3c861f53a19e7b852c89ebd3702
workflow-type: tm+mt
source-wordcount: '5391'
ht-degree: 3%

---

# 신속한 개발 환경 {#rapid-development-environments}

변경 사항을 배포하기 위해 현재 클라우드 개발 환경에서는 CI/CD 파이프라인이라는 광범위한 코드 보안 및 품질 규칙을 사용하는 프로세스를 사용해야 합니다. 빠르고 반복적인 변경이 필요한 상황에 대해 Adobe은 신속한 개발 환경(RDE)을 도입했습니다.

RDE를 사용하면 개발자가 변경 사항을 신속하게 배포하고 검토할 수 있으므로 로컬 개발 환경에서 작동하는 것으로 입증된 기능을 테스트하는 데 필요한 시간을 최소화할 수 있습니다.

RDE에서 변경 사항을 테스트하면 Cloud Manager 파이프라인을 통해 일반 클라우드 개발 환경에 배포할 수 있습니다.

>[!NOTE]
> Adobe의 [디스코드 채널](https://discord.com/channels/1131492224371277874/1245304281184079872)에서 RDE 개발자에게 문의하십시오. RDE 주제에 대해 자유롭게 질문하거나 피드백을 제공해 주십시오.

>[!VIDEO](https://video.tv.adobe.com/v/3415582/?quality=12&learn=on)


RDE를 사용하여 [설정 방법](https://experienceleague.adobe.com/ko/docs/experience-manager-learn/cloud-service/developing/rde/how-to-setup), [사용 방법](https://experienceleague.adobe.com/ko/docs/experience-manager-learn/cloud-service/developing/rde/how-to-use) 및 [개발 수명 주기](https://experienceleague.adobe.com/ko/docs/experience-manager-learn/cloud-service/developing/rde/development-life-cycle)를 보여 주는 추가 비디오를 볼 수 있습니다.

## 소개 {#introduction}

RDE는 코드, 콘텐츠 및 Apache 또는 Dispatcher 구성에 사용할 수 있습니다. 일반 클라우드 개발 환경과 달리 개발자는 로컬 명령줄 도구를 사용하여 로컬로 빌드된 코드를 RDE에 동기화할 수 있습니다.

모든 프로그램은 RDE로 프로비저닝됩니다. Sandbox 계정이 있는 경우 몇 시간 동안 사용하지 않으면 최대 절전 모드로 전환됩니다.

생성 시 RDE는 가장 최근에 사용할 수 있는 Adobe Experience Manager(AEM) 버전으로 설정됩니다. Cloud Manager을 사용하여 수행할 수 있는 RDE 재설정은 RDE를 순환시키고 가장 최근에 사용할 수 있는 AEM 버전으로 설정합니다.

일반적으로 RDE는 특정 기능을 테스트 및 디버깅하기 위해 주어진 시간에 단일 개발자에 의해 사용됩니다. 개발 세션이 완료되면 RDE는 다음 사용을 위해 기본 상태로 재설정될 수 있습니다.

프로덕션(샌드박스가 아닌) 프로그램에 대해 추가 RDE에 라이센스가 부여될 수 있습니다.

## 프로그램에서 RDE 활성화 {#enabling-rde-in-a-program}

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)에서 Cloud Manager에 로그인한 다음 적절한 조직을 선택합니다.

1. RDE를 추가할 프로그램을 클릭하여 세부 정보를 표시합니다.

   * RDE는 [샌드박스 프로그램](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-sandbox-programs.md) 및 [프로덕션 프로그램](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/introduction-production-programs.md)에 모두 추가할 수 있습니다.

1. **프로그램 개요** 페이지의 **환경** 카드에서 **환경 추가**&#x200B;를 클릭합니다.

   ![환경 카드](/help/implementing/cloud-manager/assets/no-environments.png)

   * **환경 추가** 옵션은 **환경** 탭에서도 사용할 수 있습니다.

     ![환경 탭](/help/implementing/cloud-manager/assets/environments-tab.png)

   * 사용 권한이 없거나 사용 허가된 리소스에 따라 **환경 추가** 옵션이 비활성화될 수 있습니다.

1. **환경 추가** 대화 상자에서 다음을 수행합니다.

   * **환경 유형 선택** 제목에서 **신속한 개발**&#x200B;을 선택합니다.
      * 사용 가능한/사용된 환경 수는 환경 유형 뒤의 괄호 안에 표시됩니다.
   * 환경에 **이름**&#x200B;을(를) 제공하십시오.
   * 환경에 대한 선택적 **설명**&#x200B;을(를) 제공합니다.
   * **클라우드 영역**&#x200B;을 선택합니다.

   ![환경 추가 대화 상자](/help/implementing/cloud-manager/assets/add-environment-wizard.png)

1. **저장**&#x200B;을 클릭하여 지정된 환경을 추가합니다.

이제 **개요** 화면에 **환경** 카드에 새 환경이 표시됩니다.

생성 시 RDE는 가장 최근에 사용할 수 있는 AEM 버전으로 설정됩니다. Cloud Manager을 사용하여 수행할 수도 있는 RDE 재설정은 RDE를 순환시키고 가장 최근에 사용할 수 있는 AEM 버전으로 설정합니다.

Cloud Manager을 사용하여 환경을 만들고, 환경에 액세스할 수 있는 사용자를 관리하고, 사용자 지정 도메인을 할당하는 방법에 대한 자세한 내용은 Cloud Manager 설명서의 [프로그램 및 프로그램 유형](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/program-types.md)을 참조하십시오.

## RDE 명령줄 도구 설치 {#installing-the-rde-command-line-tools}

Cloud Manager을 사용하여 프로그램에 대한 RDE를 추가한 후 다음 단계에 설명된 대로 명령줄 도구를 설정하여 상호 작용할 수 있습니다.

>[!IMPORTANT]
>
>Adobe I/O(AIO) CLI 및 관련 플러그인이 제대로 작동하도록 [노드 및 NPM 버전 20이 설치](https://nodejs.org/en/download/)되어 있는지 확인하십시오.


1. 이 [프로시저](https://developer.adobe.com/app-builder/docs/guides/runtime_guides/tools/cli-install)에 따라 AIO CLI 도구를 설치하십시오.
1. AIO CLI 도구 AEM RDE 플러그인 설치:

   ```
   aio plugins:install @adobe/aio-cli-plugin-aem-rde
   aio plugins:update
   ```

1. Adobe I/O(AIO) 클라이언트를 사용하여 로그인합니다.

   ```
   aio login
   ```

   로그인 정보(토큰)는 글로벌 aio 구성에 저장되므로 하나의 로그인 및 조직만 지원합니다. 서로 다른 로그인 또는 조직이 필요한 여러 RDE를 사용하려는 경우 아래 컨텍스트 소개 예를 따르십시오.

   <details><summary>다음 예제에 따라 RDE 로그인 중 하나에 대한 로컬 컨텍스트를 설정합니다</summary>
   로그인 정보를 특정 컨텍스트 내의 현재 디렉토리에 있는 '.aio' 파일에 로컬로 저장하려면 다음 단계를 수행합니다. 컨텍스트는 CI/CD 환경 또는 스크립트를 설정하는 영리한 방법이기도 합니다.  이 기능을 사용하려면 aio-cli 버전 10.3.1 이상을 사용해야 합니다. 'npm install -g @adobe/aio-cli'를 사용하여 업데이트합니다.

   이제 login 명령을 호출하기 전에 auth 플러그인을 사용하여 기본 컨텍스트로 설정한 m`ycontext`이라는 컨텍스트를 만듭니다.

   ```
   aio config set --json -l "ims.contexts.mycontext" "{ cli.bare-output: false }"
   aio auth ctx -s mycontext
   aio login --no-open
   ```

   >[!NOTE]
   > `--no-open` 옵션이 있는 login 명령은 기본 브라우저를 여는 대신 터미널에서 URL을 출력합니다. 브라우저의 **시크릿** 창을 사용하여 복사하고 열 수 있습니다. 이 기능을 사용하면 기본 브라우저 창의 현재 세션에 영향을 주지 않고 작업에 필요한 특정 계정 및 조직에 로그인할 수 있습니다.

   첫 번째 명령은 로컬 `.aio` 구성 파일에 `mycontext`이라는 새 로그인 컨텍스트 구성을 만듭니다(필요한 경우 파일이 만들어집니다). 두 번째 명령은 컨텍스트 `mycontext`을(를) &quot;현재&quot; 컨텍스트(기본값)로 설정합니다.

   이 구성이 적용되면 login 명령은 컨텍스트 `mycontext`에 로그인 토큰을 자동으로 저장하므로 로컬로 유지합니다.

   로컬 구성을 여러 폴더에 보관하여 여러 컨텍스트를 관리할 수 있습니다. 또는 단일 구성 파일 내에 여러 컨텍스트를 설정하고 &quot;현재&quot; 컨텍스트를 변경하여 이들 간에 전환할 수도 있습니다.
   </details>

1. 조직, 프로그램 및 환경을 사용하도록 RDE 플러그인을 구성합니다. 아래 설정 명령은 사용자에게 조직에 있는 프로그램 목록을 대화식으로 제공하고 해당 프로그램에서 선택할 수 있는 RDE 환경을 표시합니다.

   ```
   aio aem:rde:setup
   ```

   스크립팅된 환경을 사용하는 경우 설정 단계를 건너뛸 수 있습니다. 이 경우 각 명령에 직접 조직, 프로그램 및 환경 값을 포함하십시오. [자세한 내용은 아래의 RDE 명령을 참조하십시오](#rde-cli-commands).

### 대화형 설정 {#installing-the-rde-command-line-tools-interactive}

setup 명령은 제공된 구성을 로컬로 저장할지 전역으로 저장할지를 묻습니다.

```
Setup the CLI configuration necessary to use the RDE commands.
? Do you want to store the information you enter in this setup procedure locally? (y/N)
```

`no` 선택

* aio 구성에 조직, 프로그램 및 환경을 전체적으로 저장합니다.
* 단일 RDE로만 작업합니다.

다음을 수행하려면 `yes`을(를) 선택하십시오.

* 조직, 프로그램 및 환경을 현재 디렉터리의 `.aio` 파일에 로컬로 저장합니다. 이 방법은 Git 저장소를 복제하는 다른 사용자가 사용할 수 있도록 파일을 버전 제어에 커밋하려는 경우에 편리합니다.
* 다른 디렉터리로 전환하면 대신 해당 구성이 사용되도록 많은 RDE에서 작업할 수 있습니다.
* 스크립트를 참조할 수 있는 프로그래밍 컨텍스트에서 구성을 사용합니다.


로컬 또는 전역 구성을 선택하면 setup 명령은 현재 로그인에서 조직 ID를 읽은 다음 조직의 프로그램을 읽습니다. 조직을 찾을 수 없는 경우 몇 가지 지침과 함께 수동으로 입력할 수 있습니다.

```
Selected only organization: XYXYXYXYXYXYXYXXYY
retrieving programs of your organization ...
```

프로그램이 검색되면 사용자는 목록에서 선택하고 필터링할 내용을 입력할 수 있습니다. 프로그램을 선택하면 선택할 수 있는 RDE 환경 목록이 나열됩니다. 프로그램이 하나뿐이거나 사용 가능한 RDE 환경이 하나이거나 둘 다인 경우 자동으로 선택됩니다.

현재 환경 컨텍스트를 보려면 다음을 실행합니다.

```aio aem rde setup --show```

명령은 다음과 유사한 결과로 응답합니다.

```Current configuration: cm-p1-e1: programName - environmentName (organization: ...@AdobeOrg)```

### 비대화형 환경에서의 수동 설정 절차 {#manual-setup}

사용자가 대화식으로 설치 명령을 실행할 수 없는 환경(예: CI/CD 또는 스크립트)에서는 수동 구성이 필요합니다. 아래 단계를 사용하여 조직, 프로그램 및 환경 매개 변수를 설정할 수 있습니다.


<details>
  <summary>를 확장하여 수동으로 구성하는 방법에 대한 세부 정보 찾기</summary>

1. 조직 ID를 구성하고 영숫자 문자열을 자체 조직 ID로 바꿉니다.

   `aio config:set cloudmanager_orgid 4E03EQC05D34GL1A0B49421C@AdobeOrg`

   * [조직 ID 보기](https://experienceleague.adobe.com/ko/docs/core-services/interface/administration/organizations#concept_EA8AEE5B02CF46ACBDAD6A8508646255)에 설명된 메서드를 사용하여 자신의 조직 ID를 조회할 수 있습니다.

1. 다음으로 프로그램 ID를 구성합니다.

   `aio config:set cloudmanager_programid 12345`

1. 그런 다음 RDE를 첨부할 환경 ID를 구성합니다.

   `aio config:set cloudmanager_environmentid 123456`

1. 플러그인 구성을 완료한 후 다음을 수행하여 로그인합니다.

   `aio login`

   이 단계를 수행하려면 Cloud Manager **Developer - Cloud Service** 제품 프로필의 멤버여야 합니다. 자세한 내용은 [Cloud Manager 제품 프로필에 팀원 할당 - 개발자 제품 프로필 할당](/help/journey-onboarding/assign-profiles-cloud-manager.md#assign-developer)을 참조하십시오.

자세한 내용과 데모를 보려면 비디오 튜토리얼 [RDE를 설정하는 방법(06:24)](https://experienceleague.adobe.com/ko/docs/experience-manager-learn/cloud-service/developing/rde/how-to-setup)을 시청하십시오.
</details>

## 새 기능을 개발하는 동안 RDE 사용 {#using-rde-while-developing-a-new-feature}

Adobe은 새 기능을 개발하기 위해 다음 워크플로우를 권장합니다.

* AEM as a Cloud Service SDK을 사용하여 중간 이정표에 도달하고 로컬에서 성공적으로 검증되면 코드를 Git 기능 분기에 커밋합니다. git에 커밋은 선택 사항이지만 분기는 아직 주 라인에 포함되지 않아야 합니다. &#39;중간 이정표&#39;를 구성하는 것은 팀 습관에 따라 다르다. 예를 들면 몇 개의 새로운 코드 줄, 반나절 작업 또는 하위 기능 완료가 있습니다.

* 다른 기능에서 RDE를 사용했으며 [기본 상태로 재설정](#reset-rde)하려는 경우 RDE를 재설정하십시오. <!-- Alexandru: hiding for now, do not delete This can be done by way of [Cloud Manager](#reset-the-rde-cloud-manager) or by way of the [command line](#reset-the-rde-command-line). -->다시 설정하는 데 몇 분 정도 소요되며 기존의 모든 콘텐츠와 코드가 삭제됩니다. RDE status 명령을 사용하여 RDE가 준비되었는지 확인할 수 있습니다. RDE는 최신 AEM 릴리스 버전으로 다시 제공됩니다.

  >[!IMPORTANT]
  >
  >스테이징 및 프로덕션 환경이 자동 AEM 릴리스 업데이트를 받지 못하고 최신 버전보다 오래된 경우 RDE에서 다른 버전의 AEM을 실행할 수 있습니다. 따라서 RDE의 코드 동작이 스테이징 및 프로덕션에서 작동하는 방식과 일치하지 않을 수 있습니다. 이 경우 코드를 프로덕션에 배포하기 전에 스테이징에서 철저한 테스트를 수행하는 것이 중요합니다.


* RDE 명령줄 인터페이스를 사용하여 로컬 코드를 RDE에 동기화합니다. 다음을 포함한 다양한 유형의 파일을 설치할 수 있습니다.

   * 컨텐츠 패키지
   * 특정 번들
   * OSGi 구성 파일
   * 컨텐츠 파일
   * Apache/Dispatcher 구성이 포함된 ZIP 파일

  원격 콘텐츠 패키지를 참조할 수도 있습니다. 자세한 내용은 [RDE 명령줄 도구](/help/implementing/developing/introduction/rapid-development-environments.md#rde-cli-commands)를 참조하십시오. status 명령을 사용하여 배포가 성공했는지 확인할 수 있습니다. 필요한 경우 패키지 관리자를 사용하여 콘텐츠 패키지를 설치합니다.

* RDE에서 코드를 테스트합니다. 작성자 및 게시 URL은 Cloud Manager에서 사용할 수 있습니다.

* 코드가 예상대로 작동하지 않으면 표준 디버깅 기술을 사용하여 문제를 이해하고 적절하게 변경합니다. 코드 수정 사항을 Git에 커밋하지 않고(유효성이 검사되지 않았으므로) 로컬 CLI를 사용하여 코드를 RDE에 동기화합니다. 문제가 해결될 때까지 계속 반복하십시오.

* 코드가 예상대로 작동하면 코드를 git 기능 분기에 커밋합니다.

* RDE로 동기화된 코드는 Cloud Manager 파이프라인을 사용하지 않으므로 이제 Cloud Manager 비프로덕션 파이프라인을 사용하여 Git 기능 분기를 클라우드 개발 환경에 배포해야 합니다. 이 프로세스는 코드가 Cloud Manager 품질 게이트를 통과하는지 확인하고 나중에 Cloud Manager 프로덕션 파이프라인을 사용하여 코드가 성공적으로 배포되었는지 확인할 수 있도록 합니다.

* 기능에 대한 모든 코드가 준비되고 RDE 및 클라우드 개발 환경 모두에서 잘 실행될 때까지 각 중간 이정표에 대해 위의 단계를 반복합니다.

* Cloud Manager 프로덕션 파이프라인을 통해 프로덕션에 코드를 배포합니다.

## RDE를 사용하여 기존 기능 디버그 {#use-rde-to-debug-an-existing-feature}

이 워크플로우는 새 기능을 개발하는 것과 유사합니다. 차이점은 RDE에 동기화된 코드가 문제가 발생한 환경에 푸시된 것의 Git 레이블을 반영한다는 것입니다. 이 워크플로우는 문제를 조사하거나 재현할 때 일관성을 유지하는 데 도움이 됩니다. 또한 업스트림 환경과 일치하는 콘텐츠를 배포하는 것이 유용할 수 있습니다. 이 방법은 콘텐츠 패키지를 내보내고 가져와서 수행할 수 있습니다.

## 여러 개발자가 동일한 RDE에서 공동 작업 {#multiple-developers-collaborating-on-the-same-rde}

RDE는 한 번에 하나의 프로젝트를 지원합니다. 코드는 로컬 개발 환경에서 RDE 환경으로 동기화되므로 한 개발자가 주어진 시간에 직접 사용하는 것이 가장 자연스럽습니다.

그러나 신중하게 조정하면 두 명 이상의 개발자가 특정 기능을 검증하거나 특정 문제를 디버깅할 수 있습니다. 핵심은 각 개발자가 로컬 프로젝트를 계속 동기화하여 특정 개발자의 코드 변경 사항을 다른 개발자가 흡수할 수 있도록 하는 것입니다. 그렇지 않으면 한 개발자가 실수로 다른 개발자의 코드를 덮어쓸 수 있습니다. 권장되는 전략은 각 개발자가 RDE로 동기화하기 전에 공유 Git 분기에 변경 사항을 커밋하여 다른 개발자가 직접 변경하기 전에 변경 사항을 가져오는 것입니다.

## RDE 명령줄 도구 명령 {#rde-cli-commands}

### 도움말/일반 정보 {#help}

* 명령 목록을 보려면 다음을 입력합니다.

  `aio aem:rde`

* 명령에 대한 자세한 도움말을 보려면 다음과같이 입력합니다.

  `aio aem rde <command> --help`

### 글로벌 플래그 {#global-flags}

* 덜 자세한 출력의 경우 자동 플래그를 사용합니다.

  `aio aem rde <command> --quiet`

  이 플래그는 스피너 및 진행률 표시줄과 같은 특정 요소를 제거하고 사용자 입력의 필요성을 제한합니다.

* 콘솔 로그 출력 대신 JSON의 경우 json 플래그를 사용합니다.

  `aio aem rde <command> --json`

  이 플래그는 콘솔 출력을 제외하는 동안 유효한 JSON을 반환합니다. 아래 추가 JSON 예 를 참조하십시오.

* setup 명령 또는 aio 구성 생성을 사용하여 RDE 연결 정보를 구성하지 않으려면 조직, 프로그램 및 환경에 대해 세 가지 플래그를 사용합니다.

  `aio aem rde <command> --organizationId=<value> --programId=<value> --environmentId=<value>`

  ```aio login```을(를) 수행해야 합니다.

### RDE에 배포 {#deploying-to-rde}

이 섹션에서는 RDE CLI를 사용하여 다양한 리소스를 배포, 설치 또는 업데이트하는 방법을 설명합니다. 이러한 리소스에는 다음이 포함됩니다.

* 컨텐츠 패키지
* OSGi 구성
* 번들
* 컨텐츠 파일
* Apache 또는 Dispatcher 구성

일반적인 사용 패턴은 `aio aem:rde:install <artifact>`입니다.

다음은 몇 가지 예입니다.

#### 컨텐츠 패키지 배포 {#deploy-content-package}

`aio aem:rde:install sample.demo.ui.apps.all-1.0.0-SNAPSHOT.zip`

성공적인 배포에 대한 응답은 다음과 같습니다.

```
...
#1: deploy completed for content-package sample.demo.ui.apps.all-1.0.0-SNAPSHOT.zip on author,publish - done by 9E072FC75D54FE1A2B49431C@AdobeID at 2022-09-13T11:32:06.229Z
```

필요한 경우 원격 저장소를 참조할 수 있습니다.

`aio aem:rde:install -t content-package "https://repo1.maven.org/maven2/com/adobe/aem/guides/aem-guides-wknd.all/2.1.0/aem-guides-wknd.all-2.1.0.zip"`

기본적으로 아티팩트는 작성자 및 게시 계층 모두에 배포되지만 `-s` 플래그를 사용하여 특정 계층을 타깃팅할 수 있습니다.

코드, 콘텐츠가 포함된 패키지 또는 [컨테이너 패키지](/help/implementing/developing/introduction/aem-project-content-package-structure.md#container-packages)(&quot;모든&quot; 패키지라고도 함)와 같은 모든 AEM 패키지를 배포할 수 있습니다.

>[!IMPORTANT]
>
>위의 콘텐츠 패키지 설치는 WKND 프로젝트에 대한 Dispatcher 구성을 배포하지 않습니다. &quot;Apache/Dispatcher 구성 배포&quot; 단계에 따라 별도로 배포합니다.

#### OSGI 구성 배포 {#deploy-OSGI-config}

`aio aem:rde:install com.adobe.granite.demo.MyServlet.cfg.json`

성공적인 배포에 대한 응답은 다음과 같습니다.

```
...
#2: deploy completed for osgi-config com.adobe.granite.demo.MyServlet.cfg.json on author,publish - done by 9E0725C05D54FE1A0B49431C@AdobeID at 2022-09-13T11:54:36.390Z
```

#### 번들 배포 {#deploy-bundle}

번들을 배포하려면 다음을 사용합니다.

`aio aem:rde:install ~/.m2/repository/org/apache/felix/org.apache.felix.gogo.jline/1.1.8/org.apache.felix.gogo.jline-1.1.8.jar`

성공적인 배포에 대한 응답은 다음과 같습니다.

```
...
#3: deploy staged for osgi-bundle org.apache.felix.gogo.jline-1.1.8.jar on author,publish - done by 9E0725C05D53BE1A0B49431C@AdobeID at 2022-09-14T07:54:28.882Z
```

#### 컨텐츠 파일 배포 {#deploy-content-file}

컨텐츠 파일을 배포하려면 다음을 사용합니다.

`aio aem:rde:install world.txt -p /apps/hello.txt`

성공적인 배포에 대한 응답은 다음과 같습니다.

```
..
#4: deploy completed for content-file world.txt on author,publish - done by 9E0729C05C54FE1A0B49431C@AdobeID at 2022-09-14T07:49:30.644Z
```

#### Apache/Dispatcher 구성 배포 {#deploy-apache-config}

이러한 유형의 구성을 위해서는 전체 폴더 구조가 zip 파일 형식이어야 합니다.

AEM 프로젝트의 `dispatcher` 모듈에서 아래 maven 명령을 실행하여 Dispatcher 구성을 압축할 수 있습니다.

`mvn clean package`

또는 `dispatcher` 모듈의 `src` 디렉터리에서 아래 zip 명령을 사용합니다.

`zip -y -r dispatcher.zip .`

그런 다음 이 명령을 사용하여 구성을 배포합니다.

`aio aem:rde:install target/aem-guides-wknd.dispatcher.cloud-X.X.X-SNAPSHOT.zip`

>[!TIP]
>
>위의 명령은 사용자가 [WKND](https://github.com/adobe/aem-guides-wknd) 프로젝트의 Dispatcher 구성을 배포하고 있다고 가정합니다. 프로젝트의 Dispatcher 구성을 배포할 때 `X.X.X`을(를) 해당 WKND 프로젝트 버전 번호 또는 프로젝트별 버전 번호로 바꾸십시오.

>[!NOTE]
>
>RDE는 &quot;유연한 모드&quot; Dispatcher 구성을 지원하지만 &quot;레거시 모드&quot; Dispatcher 구성은 지원하지 않습니다. 두 모드에 대한 자세한 내용은 [Dispatcher 설명서](/help/implementing/dispatcher/disp-overview.md#validation-debug)를 참조하세요. 아직 수행하지 않았다면 [유연한 모드로 마이그레이션](/help/implementing/dispatcher/validation-debug.md#migrating)에 대한 설명서를 참조할 수도 있습니다.

배포가 성공하면 다음과 유사한 응답이 생성됩니다.

```
..
#5 deploy completed for dispatcher-config dispatcher.zip on author,publish - done by 9E0735C05T54FE1A0B49431C@AdobeID at 2022-10-03T10:26:31.286Z
Logs:
  Cloud manager validator 2.0.49
  2022/10/03 10:26:37 No issues found
  Syntax OK
```

RDE에 배포된 코드는 Cloud Manager 파이프라인 및 관련 품질 게이트를 거치지 않습니다. 그러나 이 코드는 아래 코드 샘플에 표시된 대로 오류를 보고하는 몇 가지 분석을 수행합니다.

```
$ aio aem:rde:install ~/.m2/repository/org/apache/felix/org.apache.felix.gogo.jline/1.1.8/org.apache.felix.gogo.jline-1.1.8.jar
...
#19: deploy staged for osgi-bundle org.apache.felix.gogo.jline-1.1.8.jar on author,publish - done by 9E0725C05D74FR1A0B49431C@AdobeID at 2022-09-14T07:54:28.882Z
Logs:
The analyser found the following errors for author :
[requirements-capabilities] com.adobe.aem.temp:org.apache.felix.gogo.jline:1.1.8: Artifact com.adobe.aem.temp:org.apache.felix.gogo.jline:1.1.8 requires [org.apache.felix.gogo.jline/1.1.8] org.apache.felix.gogo; filter:="(&(org.apache.felix.gogo=command.implementation)(version>=1.0.0)(!(version>=2.0.0)))"; effective:=active in start level 20 but no artifact is providing a matching capability in this start level.
[api-regions-exportsimports] com.adobe.aem.temp:org.apache.felix.gogo.jline:1.1.8: Bundle org.apache.felix.gogo.jline:1.1.8 is importing package(s) [org.jline.builtins, org.jline.utils, org.apache.felix.service.command, org.apache.felix.service.threadio, org.jline.terminal, org.jline.reader, org.apache.felix.gogo.runtime, org.jline.reader.impl] in start level 20 but no bundle is exporting these for that start level.
The analyser found the following errors for publish :
[requirements-capabilities] com.adobe.aem.temp:org.apache.felix.gogo.jline:1.1.8: Artifact com.adobe.aem.temp:org.apache.felix.gogo.jline:1.1.8 requires [org.apache.felix.gogo.jline/1.1.8] org.apache.felix.gogo; filter:="(&(org.apache.felix.gogo=command.implementation)(version>=1.0.0)(!(version>=2.0.0)))"; effective:=active in start level 20 but no artifact is providing a matching capability in this start level.
[api-regions-exportsimports] com.adobe.aem.temp:org.apache.felix.gogo.jline:1.1.8: Bundle org.apache.felix.gogo.jline:1.1.8 is importing package(s) [org.jline.builtins, org.jline.utils, org.apache.felix.service.command, org.apache.felix.service.threadio, org.jline.terminal, org.jline.reader, org.apache.felix.gogo.runtime, org.jline.reader.impl] in start level 20 but no bundle is exporting these for that start level.
```

위의 코드 샘플은 번들이 해결되지 않는 경우의 동작을 보여 줍니다. 이 경우 &quot;스테이징됨&quot;이며 다른 코드 설치를 통해 요구 사항(이 경우 누락된 가져오기)이 충족되는 경우에만 설치됩니다.

#### 구성 파이프라인 관련 구성(yaml 구성) 배포 {#deploy-config-pipeline}

문서 [구성 파이프라인 사용](/help/operations/config-pipeline.md)에 설명된 환경별 구성(1개 이상의 yaml 파일)은 다음과 같이 배포할 수 있습니다.

`aio aem:rde:install -t env-config ./my-config-folder`
여기서 `my-config-folder`은(는) yaml 구성이 포함된 상위 폴더입니다.

또는 구성 폴더 트리가 포함된 zip 파일을 설치할 수도 있습니다.

`aio aem:rde:install -t env-config config.zip`

yaml 파일의 envTypes 배열에는 아래 예와 같이 값 `rde`이(가) 포함되어 있습니다.

```
kind: "CDN"
version: "1"
metadata:
  envTypes: ["rde"]
```

### 사이트 테마 및 사이트 템플릿을 기반으로 프론트엔드 코드 배포 {#deploying-themes-to-rde}

RDE는 [사이트 테마](/help/sites-cloud/administering/site-creation/site-themes.md) 및 [사이트 템플릿](/help/sites-cloud/administering/site-creation/site-templates.md)으로 빌드된 프론트엔드 코드를 지원합니다. RDE는 다른 환경 유형과 같이 Cloud Manager [프론트엔드 파이프라인](/help/sites-cloud/administering/site-creation/enable-front-end-pipeline.md)을(를) 사용하는 대신 명령줄 지시문을 사용하여 프론트엔드 패키지를 배포합니다.

평소대로 npm을 사용하여 프론트엔드 패키지를 빌드합니다.

`npm run build`

프런트 엔드 패키지 폴더에 `package.json` 파일과 `dist` 폴더가 포함되도록 `dist/` 폴더를 생성합니다.

```
ls ./path-to-frontend-pkg-folder/
...
dist
package.json
```

이제 다음과 같은 방식으로 프론트엔드 패키지 폴더를 가리키면 프론트엔드 패키지를 RDE에 배포할 준비가 되었습니다.

```
aio aem:rde:install -t frontend ./path-to-frontend-pkg-folder/
...
#1: deploy completed for frontend frontend-pipeline.zip on author,publish - done by ... at 2024-01-18T15:33:22.898Z
Logs:
> Deployed artifact wknd-1.0.0-1705592008-26e7ec1a
> with workspace hash 692021864642a20d6d298044a927d66c0d9cf2adf42d4cca0c800a378ac3f8d3
```

또는 `package.json` 파일과 `dist` 폴더를 압축하고 해당 zip 파일을 배포할 수 있습니다.

`zip -r frontend-pkg.zip ./path-to-frontend-pkg-folder/dist ./path-to-frontend-pkg-folder/package.json`

```
aio aem:rde:install -t frontend frontend-pkg.zip
...
#1: deploy completed for frontend frontend-pipeline.zip on author,publish - done by ... at 2024-01-18T15:33:22.898Z
Logs:
> Deployed artifact wknd-1.0.0-1705592008-26e7ec1a
> with workspace hash 692021864642a20d6d298044a927d66c0d9cf2adf42d4cca0c800a378ac3f8d3
```

>[!NOTE]
>
>프론트엔드 패키지의 파일 이름은 다음 명명 규칙을 준수해야 합니다.
>
> * `dist` 폴더, npm 빌드 출력 패키지 폴더
> * npm 종속성 패키지에 대한 `package.json` 파일

>[!TIP]
>
>2023년 4월 이전에 RDE를 만든 후 프론트엔드 기능을 처음 사용할 때 `UNEXPECTED_API_ERROR`이(가) 발생하는 경우, 오래된 설정 때문일 수 있습니다. 이 문제를 해결하려면 환경을 삭제하고 새 환경을 만듭니다.

### RDE 상태 확인 {#checking-rde-status}

RDE CLI를 사용하여 RDE 플러그인을 통해 배포된 내용과 같이 환경을 배포할 준비가 되었는지 확인할 수 있습니다.

다음을 실행합니다.

`aio aem:rde:status`

를 반환하며 다음을 포함합니다.

```
Info for cm-p12345-e987654
Environment: Ready
- Bundles Author:
 com.adobe.granite.sample.demo-1.0.0.SNAPSHOT
- Bundles Publish:
 com.adobe.granite.sample.demo-1.0.0.SNAPSHOT
- Configurations Author:
 com.adobe.granite.demo.MyServlet
- Configurations Publish:
 com.adobe.granite.demo.MyServlet
```

인스턴스 배포에 대한 메모를 반환하는 경우 계속해서 다음 업데이트를 수행할 수 있지만 마지막 업데이트가 아직 인스턴스에 표시되지 않을 수 있습니다.

### 배포 내역 표시 {#show-deployment-history}

다음을 실행하여 RDE에 대한 배포 내역을 확인할 수 있습니다.

`aio aem:rde:history`

응답 형식을 반환합니다.

`#1: deploy completed for content-package aem-guides-wknd.all-2.1.0.zip on author,publish - done by 029039A55D4DE16A0A494025@AdobeID at 2022-09-12T14:41:55.393Z`

### RDE에서 삭제 {#deleting-from-rde}

CLI 도구를 사용하여 이전에 RDE에 배포한 구성 및 번들을 삭제할 수 있습니다. 삭제할 수 있는 항목 목록에 `status` 명령을 사용하십시오. 이 목록에는 번들의 경우 `bsn`, delete 명령에서 참조할 구성의 경우 `pid`이(가) 포함됩니다.

예를 들어 `com.adobe.granite.demo.MyServlet.cfg.json`이(가) 설치된 경우 `bsn`은(는) **cfg.json** 접미사가 없는 `com.adobe.granite.demo.MyServlet`입니다.

컨텐츠 패키지 또는 컨텐츠 파일 삭제는 지원되지 않습니다. 이를 제거하려면 RDE를 재설정하여 기본 상태로 되돌립니다.

자세한 내용은 아래 예를 참조하십시오.

```
aio aem:rde:delete com.adobe.granite.csrf.impl.CSRFFilter
#13: delete completed for osgi-config com.adobe.granite.csrf.impl.CSRFFilter on author - done by karl at 2022-09-12T22:01:01.955Z
#14: delete completed for osgi-config com.adobe.granite.csrf.impl.CSRFFilter on publish - done by karl at 2022-09-12T22:01:12.979Z
```

자세한 내용과 데모는 비디오 튜토리얼 [RDE 명령 사용 방법(10:01)](https://experienceleague.adobe.com/ko/docs/experience-manager-learn/cloud-service/developing/rde/how-to-use)을 참조하세요.


## 외부 Git 공급자의 RDE에 배포 {#deploy-to-rde}

>[!NOTE]
>
>이 기능은 Beta 프로그램을 통해 사용할 수 있습니다. 이 새로운 기능을 테스트하고 피드백을 공유하려면 Adobe ID과 연결된 전자 메일 주소에서 [CloudManager_BYOG@adobe.com](mailto:cloudmanager_byog@adobe.com)(으)로 전자 메일을 보내세요. 사용하려는 Git 플랫폼과 비공개/공개 또는 기업 저장소 구조인지 여부를 반드시 포함해야 합니다.

Cloud Manager에서는 [BYOG(Bring Your Own Git) 구성](/help/implementing/cloud-manager/managing-code/external-repositories.md)을 사용할 때 외부 Git 공급자에서 직접 RDE에 코드를 배포할 수 있습니다.

외부 Git 저장소에서 RDE로 배포하려면 다음 조건을 충족해야 합니다.

* Cloud Manager과 통합된 외부 Git 저장소 사용(BYOG 설정).
* 프로젝트에 하나 이상의 RDE 환경이 프로비저닝되어 있어야 합니다.
* `github.com`을(를) 사용하는 경우 업데이트된 GitHub 앱 설치를 검토하고 수락하여 필요한 새 권한을 부여해야 합니다.

**사용 정보**

* RDE에 대한 배포는 현재 AEM 콘텐츠 및 Dispatcher 패키지에 대해서만 지원됩니다.
* 다른 패키지 유형(예: 전체 AEM 애플리케이션 패키지)의 배포는 아직 지원되지 않습니다.
* 현재 주석을 사용하여 RDE 환경을 재설정하는 기능은 지원되지 않습니다. 대신 기존 AIO CLI reset 명령을 사용해야 합니다([여기에 설명](/help/implementing/developing/introduction/rapid-development-environments.md#reset-the-rde-command-line)).

**작동 방식**

1. **코드 품질 유효성 검사 메시지.**

   끌어오기 요청(PR)이 코드 품질 파이프라인 실행을 트리거할 때 유효성 검사 결과는 배포가 RDE 환경으로 진행될 수 있는지 여부를 나타냅니다.

   GitHub Enterprise의 특징:
   ![GitHub Enterprise의 코드 품질 유효성 검사 메시지](/help/implementing/developing/introduction/assets/rde-gitlab-code-quality-validation-message.png)

   GitLab의 특징:
   ![GitLab의 코드 품질 유효성 검사 메시지](/help/implementing/developing/introduction/assets/rde-gitlab-code-quality-validation-message.png)

   Bitbucket의 모양:
   ![Bitbucket의 코드 품질 유효성 검사 메시지](/help/implementing/developing/introduction/assets/rde-bitbucket-code-quality-validation-message.png)

1. **댓글을 사용하여 배포를 트리거합니다.**

   배포를 시작하려면 `deploy on rde-environment-<envName>` 형식으로 PR에 주석을 추가하십시오.

   ![댓글을 사용하여 배포 트리거](/help/implementing/developing/introduction/assets/rde-trigger-deployment-using-comment.png)

   `<envName>`은(는) 기존 RDE 환경의 이름과 일치해야 합니다. 이름을 찾을 수 없으면 환경이 유효하지 않음을 나타내는 주석이 반환됩니다.

   환경 상태가 준비되지 않은 경우 다음과 같은 댓글이 표시됩니다.

   ![환경을 배포할 준비가 되지 않았습니다](/help/implementing/developing/introduction/assets/rde-environment-not-ready.png)

1. **환경 검사 및 아티팩트 배포.**

   RDE가 준비되면 Cloud Manager은 PR에 새 검사를 게시합니다.

   GitHub Enterprise의 특징:

   ![GitHub의 환경 상태](/help/implementing/developing/introduction/assets/rde-github-environment-status-is-ready.png)

   GitLab의 특징:

   ![GitLab의 환경 상태](/help/implementing/developing/introduction/assets/rde-gitlab-deployment-1.png)

   Bitbucket의 모양:

   ![Bitbucket의 환경 상태](/help/implementing/developing/introduction/assets/rde-bitbucket-deployment-1.png)

1. **배포 완료 메시지.**

   배포가 완료되면 Cloud Manager은 대상 환경에 배포된 아티팩트를 요약하는 성공 메시지를 게시합니다.

   GitHub Enterprise의 특징:

   ![GitHub의 환경 배포 상태](/help/implementing/developing/introduction/assets/rde-github-environment-deployed-artifacts.png)

   GitLab의 특징:

   ![GitLab의 환경 배포 상태](/help/implementing/developing/introduction/assets/rde-gitlab-deployment-2.png)

   Bitbucket의 모양:

   ![Bitbucket의 환경 배포 상태](/help/implementing/developing/introduction/assets/rde-bitbucket-deployment-2.png)




## 로그 {#rde-logging}

다른 환경 유형과 유사하게 OSGi 구성을 수정하여 로그 수준을 설정할 수 있지만, 위에서 설명한 대로 RDE에 대한 배포 모델에 Cloud Manager 배포가 아닌 명령줄이 포함됩니다. 로그를 보고 다운로드하고 해석하는 방법에 대한 자세한 내용은 [로깅 설명서](/help/implementing/developing/introduction/logging.md)를 참조하세요.

또한 RDE CLI에는 기록되는 클래스 및 패키지와 로그 수준을 빠르게 구성하는 데 사용되는 자체 log 명령도 있습니다. 이러한 구성은 버전 제어에서 OSGI 속성을 수정하지 않으므로 사용 후 삭제로 볼 수 있습니다. 이 기능은 먼 과거의 로그를 조회하는 것보다 실시간으로 로그를 추적하는 데 중점을 둡니다.

다음 예제에서는 하나의 패키지를 디버그 로그 수준으로 설정하고 두 패키지(공백으로 구분)를 정보 디버그 수준으로 설정하여 작성자 계층을 추적하는 방법을 보여 줍니다. **auth** 패키지가 포함된 출력이 강조 표시됩니다.

`aio aem:rde:logs --target=author --debug=org.apache.sling --info=org.apache.sling.commons.threads.impl org.apache.sling.jcr.resource.internal.helper.jcr -H .auth.`

>[!TIP]
>
>작성자 서비스에 대한 로그 명령을 재생할 때 `RDECLI:UNEXPECTED_API_ERROR` 오류가 표시되면 환경을 재설정하고 다시 시도하십시오. 이 오류는 최근 재설정 작업이 2024년 5월 말 이전인 경우 발생합니다.
>
>```
>aio aem:rde:reset
>```

명령줄 옵션의 전체 집합은 `aio aem:rde:logs --help`을(를) 참조하십시오.

기능에는 다음이 포함됩니다.

* 패키지별 또는 클래스 수준에서 로그 수준 선언
* 로그 출력 형식 사용자 정의
* 각각 자체 터미널에 최대 4개의 현재 로그 구성 추적
* 특정 로그 강조 표시

로그는 RDE의 메모리에 저장되며 이러한 로그는 재활용되므로 꼬리가 붙지 않거나 네트워크가 너무 느리면 삭제됩니다.


## RDE 재설정 {#reset-rde}

RDE를 재설정하면 작성자 및 게시 인스턴스 모두에서 모든 사용자 지정 코드, 구성 및 콘텐츠가 제거됩니다. RDE를 재설정하면 한 기능 테스트를 완료하고 다른 기능을 테스트하기 전에 환경을 기본 상태로 되돌리려는 경우에 유용합니다.

재설정하면 RDE가 가장 최근에 사용할 수 있는 AEM 버전으로 설정됩니다.

[Cloud Manager](#reset-the-rde-cloud-manager) 또는 [명령줄](#reset-the-rde-command-line)을 사용하여 RDE를 다시 설정할 수 있습니다. 재설정하는 데 몇 분이 소요되며 기존 콘텐츠와 코드가 모두 RDE에서 삭제됩니다.

>[!NOTE]
>
>재설정 기능을 사용하기 전에 Cloud Manager 개발자 역할이 할당되었는지 확인하십시오. 그렇지 않으면 오류가 발생하여 재설정 작업이 실패합니다.

### 명령줄을 사용하여 RDE 재설정 {#reset-the-rde-command-line}

다음을 실행하여 RDE를 재설정하고 기본 상태로 되돌릴 수 있습니다.

`aio aem:rde:reset`

이 프로세스는 일반적으로 몇 분 정도 소요되며, 성공할 경우 ```Environment reset.```을(를) 보고하거나, 오류에 대해 ```Failed to reset the environment.```을(를) 보고합니다. 구조화된 출력의 경우 아래 ```--json``` 출력에 대한 장을 참조하십시오.

[status 명령](#checking-rde-status)을(를) 사용하여 환경이 다시 준비되었는지 확인하십시오.

### Cloud Manager에서 RDE 재설정 {#reset-the-rde-cloud-manager}

Cloud Manager을 사용하여 아래 단계를 수행하여 RDE를 재설정할 수 있습니다.

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)에서 Cloud Manager에 로그인한 다음 적절한 조직을 선택합니다.

1. RDE를 재설정할 프로그램을 클릭합니다.

1. **개요** 페이지에서 화면 상단의 **환경** 탭을 클릭합니다.

   ![환경 탭](/help/implementing/cloud-manager/assets/environments-tab2.png)

   * 또는 **환경** 카드에서 **모두 표시** 버튼을 클릭하여 **환경** 탭으로 직접 이동합니다.

     ![모두 표시 옵션](/help/implementing/cloud-manager/assets/environment-showall.png)

1. **환경** 창이 열리고 프로그램에 대한 모든 환경이 나열됩니다.

   ![환경 탭](/help/implementing/cloud-manager/assets/environments-tab-populated.png)

1. 재설정할 RDE의 줄임표 단추를 클릭한 다음 **재설정**&#x200B;을 선택합니다.

   ![환경 세부 정보 보기](/help/implementing/cloud-manager/assets/rde-reset.png)

1. 대화 상자에서 **재설정**&#x200B;을 클릭하여 RDE를 재설정할지 확인하십시오.

   ![재설정 확인](/help/implementing/cloud-manager/assets/rde-reset-confirm.png)

1. Cloud Manager은 배너 알림을 통해 재설정 프로세스가 시작되었음을 확인합니다.

   ![배너 알림 재설정](/help/implementing/cloud-manager/assets/rde-reset-banner.png)

RDE 재설정이 시작되면 일반적으로 환경을 완료하고 기본 상태로 복원하는 데 몇 분이 소요됩니다. **환경** 카드 또는 창의 **상태** 열에서 언제든지 재설정 상태를 볼 수 있습니다.

![RDE 재설정 상태](/help/implementing/cloud-manager/assets/rde-reset-status-environments-card.png)

**개요** 페이지의 **환경** 카드에서 바로 줄임표 버튼을 사용하여 RDE를 재설정할 수도 있습니다.

![환경 카드에서 RDE 재설정](/help/implementing/cloud-manager/assets/rde-reset-environments-card.png)

Cloud Manager을 사용하여 환경을 관리하는 방법에 대한 자세한 내용은 [Cloud Manager 설명서](/help/implementing/cloud-manager/manage-environments.md)를 참조하세요.

## JSON 출력을 지원하는 명령 {#json-commands}

대부분의 명령은 콘솔 출력을 억제하고 스크립트에서 처리할 유효한 json을 반환하는 전역 ```--json``` 플래그를 지원합니다. 다음은 json 출력의 예와 함께 몇 가지 지원되는 명령입니다.

### 상태 {#status}

<details>
  <summary>를 확장하여 상태 예 보기</summary>

#### 깨끗한 RDE {#clean-rde}

```$ aio aem rde status --json```

```json
{
  "programId": "myProgram",
  "environmentId": "myEnv",
  "status": "Modification in progress | Deployment in progress | Upload in progress | Ready (instances are currently deploying) | Ready",
  "author": {
    "osgiBundles": [],
    "osgiConfigs": []
  },
  "publish": {
    "osgiBundles": [],
    "osgiConfigs": []
  }
}
```

#### 설치된 번들이 있는 RDE {#rde-installed-bundles}

```$ aio aem rde status --json```

```json
{
  "programId": "myProgram",
  "environmentId": "myEnv",
  "status": "Ready",
  "author": {
    "osgiBundles": [
      {
        "id": "author_osgi-bundle_com.adobe.granite.hotdev.demo",
        "updateId": "80",
        "service": "author",
        "type": "osgi-bundle",
        "metadata": {
          "name": "hotdev.demo.ui.apps.all-1.0.0-SNAPSHOT.zip",
          "bundleSymbolicName": "com.adobe.granite.hotdev.demo",
          "bundleName": "HotDev Bundle",
          "bundleVersion": "1.0.0.SNAPSHOT"
        }
      }
    ],
    "osgiConfigs": [
      {
        "id": "publish_osgi-config_com.adobe.granite.demo.MyServlet",
        "updateId": "80",
        "service": "publish",
        "type": "osgi-config",
        "metadata": {
          "name": "hotdev.demo.ui.apps.all-1.0.0-SNAPSHOT.zip",
          "configPid": "com.adobe.granite.demo.MyServlet"
        }
      }
    ]
  },
  "publish": {
    "osgiBundles": [
      {
        "id": "author_osgi-bundle_com.adobe.granite.hotdev.demo",
        "updateId": "80",
        "service": "author",
        "type": "osgi-bundle",
        "metadata": {
          "name": "hotdev.demo.ui.apps.all-1.0.0-SNAPSHOT.zip",
          "bundleSymbolicName": "com.adobe.granite.hotdev.demo",
          "bundleName": "HotDev Bundle",
          "bundleVersion": "1.0.0.SNAPSHOT"
        }
      }
    ],
    "osgiConfigs": [
      {
        "id": "publish_osgi-config_com.adobe.granite.demo.MyServlet",
        "updateId": "80",
        "service": "publish",
        "type": "osgi-config",
        "metadata": {
          "name": "hotdev.demo.ui.apps.all-1.0.0-SNAPSHOT.zip",
          "configPid": "com.adobe.granite.demo.MyServlet"
        }
      }
    ]
  }
}
```

</details>

### 설치 {#install}

<details>
  <summary>를 확장하여 설치 예 보기</summary>

```$ aio aem rde install ~/Downloads/hotdev.demo.ui.apps.all-1.0.0-SNAPSHOT.zip --json```

```json
{
  "programId": "myProgram",
  "environmentId": "myEnv",
  "items": [
    {
      "updateId": "4",
      "info": "deploy",
      "action": "deploy",
      "metadata": {
        "name": "hotdev.demo.ui.apps.all-1.0.0-SNAPSHOT.zip"
      },
      "services": [
        "author",
        "publish"
      ],
      "status": "completed",
      "timestamps": {
        "received": "2024-05-21T12:30:44.578Z",
        "processed": "2024-05-21T12:31:07.886468Z"
      },
      "user": "userId",
      "type": "content-package",
      "hash": "2ad73507",
      "logs": [
        "No logs available for this update."
      ]
    }
  ]
}
```

</details>

### 삭제 {#delete}

<details>
  <summary>를 확장하여 예제 삭제 를 참조하십시오.</summary>

```$ aio aem rde delete com.adobe.granite.hotdev.demo-1.0.0.SNAPSHOT --json```

```json
{
  "programId": "myProgram",
  "environmentId": "myEnv",
  "items": [
    {
      "updateId": "84",
      "info": "delete author_osgi-bundle_com.adobe.granite.hotdev.demo",
      "action": "delete",
      "metadata": {},
      "services": [
        "author"
      ],
      "status": "completed",
      "timestamps": {
        "received": "2024-05-21T11:49:16.889Z",
        "processed": "2024-05-21T11:49:18.188420Z"
      },
      "user": "userId",
      "type": "osgi-bundle",
      "deletedArtifact": {
        "id": "author_osgi-bundle_com.adobe.granite.hotdev.demo",
        "metadata": {
          "name": "hotdev.demo.ui.apps.all-1.0.0-SNAPSHOT.zip",
          "bundleSymbolicName": "com.adobe.granite.hotdev.demo",
          "bundleName": "HotDev Bundle",
          "bundleVersion": "1.0.0.SNAPSHOT"
        },
        "service": "author",
        "type": "osgi-bundle",
        "updateId": "83"
      },
      "hash": "636f6d2e",
      "logs": [
        "No logs available for this update."
      ]
    },
    {
      "updateId": "85",
      "info": "delete publish_osgi-bundle_com.adobe.granite.hotdev.demo",
      "action": "delete",
      "metadata": {},
      "services": [
        "publish"
      ],
      "status": "completed",
      "timestamps": {
        "received": "2024-05-21T11:49:23.857Z",
        "processed": "2024-05-21T11:49:25.237930Z"
      },
      "user": "userId",
      "type": "osgi-bundle",
      "deletedArtifact": {
        "id": "publish_osgi-bundle_com.adobe.granite.hotdev.demo",
        "metadata": {
          "name": "hotdev.demo.ui.apps.all-1.0.0-SNAPSHOT.zip",
          "bundleSymbolicName": "com.adobe.granite.hotdev.demo",
          "bundleName": "HotDev Bundle",
          "bundleVersion": "1.0.0.SNAPSHOT"
        },
        "service": "publish",
        "type": "osgi-bundle",
        "updateId": "83"
      },
      "hash": "636f6d2e",
      "logs": [
        "No logs available for this update."
      ]
    }
  ]
}
```

</details>

### 기록 {#history}

<details>
  <summary>를 확장하여 내역 예 보기</summary>

```$ aio aem rde history --json```

```json
{
  "programId": "myProgram",
  "environmentId": "myEnv",
  "status": "Ready",
  "items": [
    {
      "updateId": "112",
      "info": "delete publish_osgi-bundle_com.adobe.granite.hotdev.demo",
      "action": "delete",
      "metadata": {},
      "services": [
        "publish"
      ],
      "status": "completed",
      "timestamps": {
        "received": "2024-05-21T12:53:07.934Z",
        "processed": "2024-05-21T12:53:09.118766Z"
      },
      "user": "userId",
      "type": "osgi-bundle",
      "deletedArtifact": {
        "id": "publish_osgi-bundle_com.adobe.granite.hotdev.demo",
        "metadata": {
          "name": "hotdev.demo.ui.apps.all-1.0.0-SNAPSHOT.zip",
          "bundleSymbolicName": "com.adobe.granite.hotdev.demo",
          "bundleName": "HotDev Bundle",
          "bundleVersion": "1.0.0.SNAPSHOT"
        },
        "service": "publish",
        "type": "osgi-bundle",
        "updateId": "110"
      },
      "hash": "636f6d2e"
    },
    {
      "updateId": "111",
      "info": "delete author_osgi-bundle_com.adobe.granite.hotdev.demo",
      "action": "delete",
      "metadata": {},
      "services": [
        "author"
      ],
      "status": "completed",
      "timestamps": {
        "received": "2024-05-21T12:53:00.824Z",
        "processed": "2024-05-21T12:53:02.101560Z"
      },
      "user": "userId",
      "type": "osgi-bundle",
      "deletedArtifact": {
        "id": "author_osgi-bundle_com.adobe.granite.hotdev.demo",
        "metadata": {
          "name": "hotdev.demo.ui.apps.all-1.0.0-SNAPSHOT.zip",
          "bundleSymbolicName": "com.adobe.granite.hotdev.demo",
          "bundleName": "HotDev Bundle",
          "bundleVersion": "1.0.0.SNAPSHOT"
        },
        "service": "author",
        "type": "osgi-bundle",
        "updateId": "110"
      },
      "hash": "636f6d2e"
    },
    {
      "updateId": "110",
      "info": "deploy",
      "action": "deploy",
      "metadata": {
        "name": "hotdev.demo.ui.apps.all-1.0.0-SNAPSHOT.zip"
      },
      "services": [
        "author",
        "publish"
      ],
      "status": "completed",
      "timestamps": {
        "received": "2024-05-21T12:52:12.123Z",
        "processed": "2024-05-21T12:52:31.026147Z"
      },
      "user": "userId",
      "type": "content-package",
      "hash": "2ad73507"
    }
  ]
}
```

</details>

### 재설정 {#reset}

<details>
  <summary>를 확장하여 예제 재설정 보기</summary>

#### 불을 지르고 잊어라, 안 기다린다 {#fire-no-wait}

```$ aio aem rde reset --no-wait --json```

```json
{
  "programId": "myProgram",
  "environmentId": "myEnv",
  "status": "resetting"
}
```

#### 완료 대기, 재설정되었습니다. {#wait-success}

```$ aio aem rde reset --json```

```json
{
  "programId": "myProgram",
  "environmentId": "myEnv",
  "status": "reset"
}
```

#### 완료 대기, 재설정 실패 {#wait-failed}

```$ aio aem rde reset --json```

```json
{
  "programId": "myProgram",
  "environmentId": "myEnv",
  "status": "reset_failed"
}
```

</details>

### 다시 시작 {#restart}

<details>
  <summary>를 확장하여 다시 시작 예 보기</summary>

```$ aio aem rde restart --json```

```json
{
  "programId": "myProgram",
  "environmentId": "myEnv",
  "status": "restarted"
}
```

</details>

## 실행 모드 {#runmodes}

아래 예와 같이 폴더 이름에 접미사를 사용하여 RDE별 OSGI 구성을 적용할 수 있습니다.

* `config.rde`
* `config.author.rde`
* `config.publish.rde`

실행 모드에 대한 일반적인 정보는 [실행 모드 설명서](/help/implementing/deploying/overview.md#runmodes)를 참조하세요.

>[!NOTE]
>
>RDE OSGI 구성은 번들의 `dev` 실행 모드에서 선언된 모든 OSGI 속성 값을 상속한다는 점에서 고유합니다.

RDE는 콘텐츠를 `/apps`의 `install.rde` 폴더(또는 `install.author.rde` 또는 `install.publish.rde`)에 설치할 수 있다는 점에서 다른 환경과 구별됩니다. 이 기능을 사용하면 콘텐츠를 Git에 커밋하고 명령줄 도구를 사용하여 RDE에 전달할 수 있습니다.

## 콘텐츠로 채우기 {#populating-content}

RDE가 재설정되면 모든 컨텐츠가 제거되므로 원할 경우 컨텐츠를 추가하려면 명시적인 작업을 수행해야 합니다. RDE에서 기능의 유효성을 검사하거나 디버깅하기 위한 테스트 콘텐츠로 사용할 콘텐츠 세트를 어셈블하는 것이 좋습니다. 해당 콘텐츠로 RDE를 채우는 몇 가지 가능한 전략이 있습니다.

1. 명령줄 도구를 사용하여 콘텐츠 패키지를 RDE에 명시적으로 동기화

1. `/apps` 아래의 `install.rde` 폴더 내의 git에 샘플 콘텐츠를 배치하고 커밋한 다음 명령줄 도구를 사용하여 중요한 콘텐츠 패키지를 RDE에 동기화합니다.

1. [콘텐츠 복사 도구](/help/implementing/developing/tools/content-copy.md)를 사용하여 프로덕션, 스테이징, 개발 환경 또는 다른 RDE에서 정의된 콘텐츠 세트를 복사합니다.

1. 패키지 관리자 사용

콘텐츠 패키지를 동기화할 때는 1GB로 제한됩니다.


## RDE는 클라우드 개발 환경과 어떻게 다릅니까? {#how-are-rds-different-from-cloud-development-environments}

RDE는 여러 가지 면에서 클라우드 개발 환경과 유사하지만 코드를 빠르게 동기화할 수 있는 일부 사소한 아키텍처 차이점이 있습니다. RDE에 코드를 가져오는 메커니즘은 다릅니다. RDE의 경우 로컬 개발 환경에서 코드를 동기화하지만 클라우드 개발 환경의 경우 Cloud Manager을 통해 코드를 배포합니다.

이러한 이유로 RDE 환경에서 코드를 확인한 후 비프로덕션 파이프라인을 사용하여 클라우드 개발 환경에 코드를 배포하는 것이 좋습니다. 마지막으로 프로덕션 파이프라인으로 배포하기 전에 코드를 테스트합니다.

또한 다음 고려 사항을 참고하십시오.

* RDE에는 미리보기 계층이 포함되지 않음
* RDE는 현재 프리릴리스 채널을 지원하지 않습니다.


## 몇 개의 RDE가 필요합니까? {#how-many-rds-do-i-need}

RDE는 라이선스가 부여된 각 솔루션에 대해 사용할 수 있으며 Adobe에서는 프로덕션(샌드박스가 아닌) 프로그램에 대해 라이선스가 부여될 수 있는 추가 RDE도 제공합니다.

필요한 RDE 수는 조직의 구성과 프로세스에 따라 다릅니다. 가장 유연한 모델은 조직에서 각 AEM Cloud Service 개발자를 위한 전용 RDE를 구매하는 것입니다. 이 모델에서 각 개발자는 RDE 환경을 사용할 수 있는지 여부에 대해 다른 팀 구성원과 조정하지 않고 RDE에서 코드를 테스트할 수 있습니다.

반대로 하나의 RDE만 있는 팀은 주어진 시간에 환경을 사용하는 개발자를 결정하기 위해 내부 조정에 의존할 수 있습니다. 이 접근 방식은 개발자가 기능 이정표에 도달하고 신속하게 변경할 수 있는 유연성으로 클라우드 환경에서 작업의 유효성을 검사해야 할 때 잘 작동합니다.

중간 모델은 조직에서 여러 RDE를 구매하여 사용하지 않는 RDE를 사용할 수 있는 가능성이 높은 모델입니다. 한 가지 전략은 스크럼 팀 또는 주요 기능당 RDE를 할당하는 것입니다. 내부 프로세스들은 환경들의 사용을 조정하기 위해 사용될 수 있다.

## AEM Forms Cloud Service RDE는 다른 환경과 어떻게 다릅니까? {#how-are-forms-rds-different-from-cloud-development-environments}

Forms 개발자는 AEM Forms Cloud Service 빠른 개발 환경을 사용하여 적응형 Forms, 워크플로 및 핵심 구성 요소 맞춤화, 서드파티 시스템과의 통합 등과 같은 사용자 정의 기능을 신속하게 개발할 수 있습니다. AEM Forms Cloud Service RDE(Rapid Development Environment)에는 통신 API가 지원되지 않습니다. 또한 적응형 양식 제출 시 기록 문서 생성과 같이 기록 문서가 필요한 기능이 지원되지 않습니다. 아래에 나열된 AEM Forms 기능은 RDE(Rapid Development Environment)에서 사용할 수 없습니다.

* 적응형 양식을 위한 기록 문서 구성
* 적응형 양식 제출 시 또는 워크플로우 단계와 함께 기록 문서 생성
* 기록 문서를 전자 메일 제출 액션 또는 워크플로우의 전자 메일 단계를 사용하여 첨부 파일로 보내기
* 적응형 양식 또는 워크플로우 단계에서 Adobe Sign 사용
* 통신 API

>[!NOTE]
>
> RDE(Rapid Development Environment)의 UI와 Forms용 다른 Cloud Service 환경 간에는 차이가 없습니다. 적응형 양식에 대한 기록 문서 템플릿 선택과 같은 모든 기록 문서 관련 옵션이 UI에 계속 표시됩니다. 이러한 환경에는 이러한 옵션을 테스트할 통신 API 및 기록 문서 기능이 없습니다. 따라서 통신 API 또는 기록 문서 기능이 필요한 옵션을 선택하면 시스템이 작업을 수행하지 않습니다. 대신 오류 메시지가 표시됩니다.

## RDE 자습서

AEM as a Cloud Service의 RDE에 대해 알아보려면 [설정 방법, 사용 방법 및 개발 수명 주기(01:25)](https://experienceleague.adobe.com/ko/docs/experience-manager-learn/cloud-service/developing/rde/overview)를 보여 주는 비디오 튜토리얼을 참조하십시오.

## 문제 해결 {#troubleshooting}

### RDE 문제 해결(#rde-troublehooting)

#### 기존 RDE에 대한 최신 AEM 버전을 얻는 방법 {#get-latest-aem-version}

생성 시 RDE는 가장 최근에 사용할 수 있는 Adobe Experience Manager(AEM) 버전으로 설정됩니다. Cloud Manager 또는 `aio aem:rde:reset` 명령을 사용하여 수행할 수 있는 [RDE 재설정](#reset-rde)은(는) RDE를 순환하고 가장 최근에 사용 가능한 AEM 버전으로 설정합니다.

### aio RDE 플러그인 문제 해결 {#aio-rde-plugin-troubleshooting}

#### 권한 부족 관련 오류 {#insufficient-permissions}

RDE 플러그인을 사용하려면 Cloud Manager **개발자 - Cloud Service** 제품 프로필의 멤버여야 합니다. 자세한 내용은 [Cloud Manager 제품 프로필에 팀원 할당 - 개발자 제품 프로필 할당](/help/journey-onboarding/assign-profiles-cloud-manager.md#assign-developer)을 참조하십시오.

또는 다음 명령을 실행하여 개발자 콘솔에 로그인하는 경우 이 개발자 역할이 있는지 확인할 수 있습니다.

`aio cloudmanager:environment:open-developer-console`

>[!TIP]
>
>`Warning: cloudmanager:* is not a aio command.` 오류가 표시되면 다음 명령을 실행하여 [aio-cli-plugin-cloudmanager](https://github.com/adobe/aio-cli-plugin-cloudmanager)를 설치해야 합니다.
>
>```
>aio plugins:install @adobe/aio-cli-plugin-cloudmanager
>```

다음을 실행하여 로그인이 성공적으로 완료되었는지 확인합니다.

`aio cloudmanager:list-programs`

이 프로세스는 구성된 조직의 모든 프로그램을 나열하고 올바른 역할이 할당되었는지 확인합니다.

#### 사용되지 않는 컨텍스트 `aio-cli-plugin-cloudmanager` 사용 {#aio-rde-plugin-troubleshooting-deprecatedcontext}

`aio-cli-plugin-aem-rde`의 기록으로 인해 컨텍스트 이름 `aio-cli-plugin-cloudmanager`이(가) 한동안 사용되었습니다. 이제 RDE 플러그인은 컨텍스트 정보를 관리하기 위해 IMS 메서드를 사용하므로 컨텍스트를 전역 또는 로컬로 저장할 수 있습니다. 모든 AIO 호출에 자동으로 적용되도록 기본 컨텍스트를 구성할 수도 있습니다. 구성된 기본 컨텍스트는 로컬에 저장되고 개발자가 폴더 내에서 개별 컨텍스트 및 해당 정보를 추적하고 사용할 수 있도록 합니다. 자세한 내용을 보려면 위의 [예제](/help/implementing/developing/introduction/rapid-development-environments.md#installing-the-rde-command-line-tools)를 읽어 로컬 컨텍스트를 설정하십시오.

플러그인, `aio-cli-plugin-cloudmanager` 및 `aio-cli-plugin-aem-rde`을(를) 모두 사용하고 모든 정보를 동일한 컨텍스트에 보관하려는 개발자는 지금 다음 옵션을 사용해야 합니다.

##### `aio-cli-plugin-cloudmanager` 컨텍스트를 계속 사용

컨텍스트는 계속 사용할 수 있습니다. RDE 플러그인에 사용 중단 경고가 표시됩니다. ```--quiet``` 모드를 사용하면 이 경고를 생략할 수 있습니다. 최신 버전의 RDE 플러그인은 더 이상 컨텍스트 `aio-cli-plugin-cloudmanager`을(를) 읽을 대체 기능을 제공하지 않습니다. 기본 컨텍스트를 `aio-cli-plugin-cloudmanager`(으)로 구성하기만 하면 됩니다. 위의 [로컬 컨텍스트를 설정하는 예제](/help/implementing/developing/introduction/rapid-development-environments.md#installing-the-rde-command-line-tools)를 참조하십시오.

##### Cloud Manager 플러그인에도 다른 컨텍스트 이름 사용

Cloud Manager 플러그인은 사용할 컨텍스트를 정의하는 매개 변수를 제공합니다. 아직 IMS 기본 컨텍스트 구성을 지원하지 않습니다. 이렇게 하려면 [로컬 컨텍스트를 설정하는 예제](/help/implementing/developing/introduction/rapid-development-environments.md#installing-the-rde-command-line-tools)를 사용하여 RDE 플러그인을 구성하고 모든 호출에서 ```--imsContextName=myContext```과(와) 같은 `myContext`을(를) 사용하도록 Cloud Manager 플러그인에 지시합니다.
