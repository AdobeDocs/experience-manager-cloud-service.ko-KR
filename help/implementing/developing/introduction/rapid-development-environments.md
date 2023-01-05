---
title: 신속한 개발 환경
description: 클라우드 환경에서 빠른 개발 반복을 위해 빠른 개발 환경을 활용하는 방법을 알아봅니다.
hidefromtoc: true
source-git-commit: 983901387d059a98942b4f7c533770a55dd4ff4a
workflow-type: tm+mt
source-wordcount: '2114'
ht-degree: 7%

---


# 신속한 개발 환경 {#rapid-development-environments}

>[!AVAILABILITY]
>
>이 기능은 아직 사용할 수 없습니다.

변경 사항을 배포하려면 현재 클라우드 개발 환경에서 CI/CD 파이프라인이라는 광범위한 코드 보안 및 품질 규칙을 사용하는 프로세스를 사용해야 합니다. Adobe은 빠르고 반복적인 변경이 필요한 상황에서 RDE(Rapid Development Environments)를 도입했습니다.

RDE를 통해 개발자는 변경 사항을 신속하게 배포하고 검토할 수 있으므로 로컬 개발 환경에서 작동하는 것으로 입증된 기능을 테스트하는 데 필요한 시간을 최소화할 수 있습니다.

RDE에서 변경 사항을 테스트하면 Cloud Manager 파이프라인을 통해 일반적인 클라우드 개발 환경에 배포할 수 있습니다.

## 소개 {#introduction}

RDE는 코드, 컨텐츠, Apache 또는 Dispatcher 구성에 사용할 수 있습니다. 일반적인 클라우드 개발 환경과 달리 개발자는 로컬 명령줄 도구를 사용하여 로컬로 빌드된 코드를 RDE에 동기화할 수 있습니다.

모든 프로그램에 RDE가 제공됩니다. 샌드박스 계정의 경우 몇 시간 동안 사용하지 않으면 최대 절전 모드로 전환됩니다.

일반적으로 RDE는 특정 기능을 테스트하고 디버깅하기 위해 특정 시간에 단일 개발자가 사용합니다. 개발 세션이 완료되면 다음 사용을 위해 RDE를 기본 상태로 재설정할 수 있습니다.

<!-- Temporarily hiding this. See CQDOC-19795 for more details

Additional RDEs may be purchased for Production programs -->

## 프로그램에서 RDE 활성화 {#enabling-rde-in-a-program}

Cloud Manager를 사용하여 프로그램에 대한 RDE를 만들려면 다음 단계를 따르십시오.

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)에서 Cloud Manager에 로그인한 다음 적절한 조직을 선택합니다.

1. RDE를 추가할 프로그램을 클릭하여 세부 정보를 표시합니다.

   * RDE를 둘 다에 추가할 수 있습니다 [샌드박스 프로그램](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-sandbox-programs.md) 및 [제작 프로그램.](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/introduction-production-programs.md)

1. **프로그램 개요** 페이지에서 **환경** 카드의 **환경 추가**&#x200B;를 클릭하여 환경을 추가합니다.

   ![환경 카드](/help/implementing/cloud-manager/assets/no-environments.png)

   * **환경 추가** 옵션은 **환경** 탭에서도 사용할 수 있습니다.

      ![환경 탭](/help/implementing/cloud-manager/assets/environments-tab.png)

   * 사용 권한이 없거나 사용 허가된 리소스에 따라 **환경 추가** 옵션이 비활성화될 수 있습니다.

1. **환경 추가** 대화 상자가 나타나면 다음 작업을 수행하십시오.

   * 선택 **신속한 개발** 아래에 **환경 유형 선택** 제목.
      * 사용 가능한/사용된 환경 수는 환경 유형 뒤에 괄호로 표시됩니다.
   * 다음을 제공합니다. **이름** 환경.
   * 선택 사항을 제공합니다 **설명** 환경.
   * **클라우드 영역**&#x200B;을 선택합니다.

   ![환경 추가 대화 상자](/help/implementing/cloud-manager/assets/add-environment-wizard.png)

1. **저장**&#x200B;을 클릭하여 지정된 환경을 추가합니다.

이제 **개요** 화면의 **환경** 카드에 새 환경이 표시됩니다.

Cloud Manager를 사용하여 환경을 만들고, 환경에 액세스할 수 있는 사용자를 관리하고 사용자 지정 도메인을 지정하는 방법에 대한 자세한 내용은 다음을 참조하십시오 [Cloud Manager 설명서.](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/program-types.md)

## RDE 명령줄 도구 설치 {#installing-the-rde-command-line-tools}

Cloud Manager를 사용하여 프로그램에 대한 RDE를 추가한 후에는 다음 단계에 설명된 대로 명령줄 도구를 설정하여 상호 작용할 수 있습니다.

1. 절차에 따라 Adobe I/O CLI 도구를 설치합니다 [여기](https://developer.adobe.com/runtime/docs/guides/tools/cli_install/).
1. Adobe I/O CLI tools cloud manager 플러그인을 설치하고 설명된 대로 구성합니다 [여기](https://github.com/adobe/aio-cli-plugin-cloudmanager).
1. 다음 명령을 실행하여 Adobe I/O CLI tools AEM RDE 플러그인을 설치합니다.

   ```
   aio plugins:install @adobe/aio-cli-plugin-aem-rde
   aio plugins:update
   ```

1. 조직 ID에 대한 클라우드 관리자 플러그인을 구성합니다.

   `aio config:set cloudmanager_orgid 4E03EQC05D34GL1A0B49421C@AdobeOrg`

   를 사용하여 조회할 수 있는 자체 조직 ID로 영숫자 문자열을 바꿉니다 [여기](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html#concept_EA8AEE5B02CF46ACBDAD6A8508646255).

1. 다음으로 프로그램 ID를 구성합니다.

   `aio config:set cloudmanager_programid 12345`

1. 그런 다음 RDE를 연결할 환경 ID를 구성합니다.

   `aio config:set cloudmanager_environmentid 123456`

1. 플러그인 구성을 마치면 다음을 수행하여 로그인합니다

   `aio login`

   성공적인 로그인 시 응답은 아래 출력과 유사해야 하지만 표시되는 값을 무시할 수 있습니다.

   ```
   ...
   You are currently in:
   1. Org: <no org selected>
   2. Project: <no project selected>
   3. Workspace: <no workspace selected>
   ```

1. 를 실행하여 로그인이 성공적으로 완료되었는지 확인합니다

   `aio cloudmanager:list-programs`

   구성된 조직의 모든 프로그램을 나열해야 합니다.

   위의 사항을 사용하려면 Cloud Manager의 구성원이어야 합니다 **개발자 - Cloud Service** 제품 프로필. 자세한 내용은 [이 페이지](/help/journey-onboarding/assign-profiles-cloud-manager.md#assign-developer) 자세한 내용

   또는 이 명령을 실행하여 개발자 콘솔에 로그인할 수 있는 경우 이 개발자 역할이 있는지 확인할 수 있습니다.

   `aio cloudmanager:environment:open-developer-console`

## 새 기능을 개발할 때 RDE 사용 {#using-rde-while-developing-a-new-feature}

Adobe은 새 기능을 개발하기 위해 다음 워크플로우를 권장합니다.

* 중간 이정표에 도달하여 AEM as a Cloud Service SDK를 사용하여 로컬로 유효성이 확인되면 git에 커밋하는 것은 선택 사항이지만, 아직 기본 줄의 일부가 아닌 Git 기능 분기로 코드를 커밋해야 합니다. 중간 이정표를 구성하는 것은 팀 습관에 따라 다릅니다. 예로는 몇 가지 새로운 코드 줄, 반일 작업 또는 하위 기능 완료가 있습니다.

* RDE가 다른 기능에서 사용되어 다음 작업을 수행하려는 경우 재설정합니다 [기본 상태로 재설정합니다.](#reset-rde). <!-- Alexandru: hiding for now, please don't delete This can be done via [Cloud Manager](#reset-the-rde-cloud-manager) or via the [command line](#reset-the-rde-command-line). -->재설정하는 데 몇 분 정도 걸리고 기존의 모든 콘텐츠와 코드가 삭제됩니다. RDE 상태 명령을 사용하여 RDE가 준비되었는지 확인할 수 있습니다.

* RDE 명령줄 인터페이스를 사용하여 로컬 코드를 RDE에 동기화합니다. 옵션에는 컨텐츠 패키지, 특정 번들, OSGI 구성 파일, 컨텐츠 파일 및 Apache/Dispatcher 구성의 zip 파일을 설치하는 것이 포함됩니다. 원격 콘텐츠 패키지를 참조할 수도 있습니다. 자세한 내용은 [RDE 명령줄 도구](#rde-cli-commands) 섹션을 참조하십시오. 상태 명령을 사용하여 배포가 성공했는지 확인할 수 있습니다. 선택적으로 패키지 관리자를 사용하여 컨텐츠 패키지를 설치합니다.

* RDE에서 코드를 테스트합니다. 작성자 및 게시 URL은 Cloud Manager에서 사용할 수 있습니다.

* 코드가 예상대로 작동하지 않으면 표준 디버깅 기술을 사용하여 문제를 이해하고 적절한 변경을 수행합니다. Git에 코드 수정 사항을 커밋하지 않고(아직 확인되지 않았으므로) 로컬 CLI를 사용하여 코드를 RDE에 동기화하십시오. 문제가 해결될 때까지 계속 반복합니다.

* 코드가 예상대로 동작하면 코드를 Git 기능 분기에 커밋합니다.

* RDE에 동기화된 코드는 Cloud Manager 파이프라인을 사용하지 않으므로 이제 Cloud Manager 비프로덕션 파이프라인을 사용하여 Cloud Development 환경에 Git 기능 분기를 배포해야 합니다. 코드가 Cloud Manager 품질 게이트를 통과하는지 확인하고 나중에 Cloud Manager 프로덕션 파이프라인을 사용하여 코드가 성공적으로 배포될 것임을 확인할 수 있습니다.

* 기능에 대한 모든 코드가 준비될 때까지 각 중간 이정표에 대해 위의 단계를 반복하여 RDE 및 클라우드 개발 환경에서 모두 잘 실행됩니다.

* Cloud Manager 프로덕션 파이프라인을 통해 프로덕션에 코드를 배포합니다.

## RDE를 사용하여 기존 기능 디버그 {#use-rde-to-debug-an-existing-feature}

워크플로우는 새 기능을 개발하는 것과 유사합니다. 차이점은 RDE에 동기화되는 코드가 문제가 발견된 환경에 푸시된 모든 항목의 Git 레이블을 반영한다는 것입니다. 또한 업스트림 환경과 일치하는 콘텐츠를 배포하는 것이 유용할 수 있습니다. 컨텐츠 패키지를 내보내고 가져와서 이를 수행할 수 있습니다.

## 동일한 RDE를 기반으로 공동으로 작업하는 여러 개발자 {#multiple-developers-collaborating-on-the-same-rde}

RDE는 한 번에 하나의 프로젝트를 지원합니다. 코드는 로컬 개발 환경에서 RDE 환경으로 동기화되므로 한 개발자가 지정된 시간에 직접 코드를 사용할 수 있는 것이 가장 자연스러운 방법입니다.

그러나 신중하게 조정하면 두 명 이상의 개발자가 특정 기능을 확인하거나 특정 문제를 디버깅할 수 있습니다. 즉, 각 개발자가 로컬 프로젝트를 계속 동기화하여 특정 개발자가 변경한 코드를 다른 개발자에게 병합하는 방식입니다. 그렇지 않으면 한 개발자가 실수로 다른 개발자의 코드를 덮어쓸 수 있습니다. 권장 전략은 각 개발자가 RDE에 동기화하기 전에 공유 Git 분기에 변경 사항을 커밋하여 다른 개발자가 직접 변경 작업을 수행하도록 하는 것입니다.

## RDE 명령줄 도구 명령 {#rde-cli-commands}

### 도움말/일반 정보 {#help}

* 명령 목록에 대해서는 다음을 입력합니다.

   `aio aem:rde`

* 명령에 대한 자세한 도움말을 보려면 다음을 입력합니다.

   `aio aem rde <command> --help`

### RDE에 배포 {#deploying-to-rde}

이 섹션에서는 번들, OSGI 구성, 컨텐츠 패키지, 개별 컨텐츠 파일 및 Apache 또는 Dispatcher 구성을 배포, 설치 또는 업데이트하는 데 RDE CLI를 사용하는 방법에 대해 설명합니다.

일반적인 사용 패턴은 다음과 같습니다 `aio aem:rde:install <artifact>`.

아래에서 몇 가지 예를 확인할 수 있습니다.

<u>컨텐츠 패키지 배포</u>

`aio aem:rde:install sample.demo.ui.apps.all-1.0.0-SNAPSHOT.zip`

성공적인 배포에 대한 응답은 다음과 같습니다.

```
...
#1: deploy completed for content-package sample.demo.ui.apps.all-1.0.0-SNAPSHOT.zip on author,publish - done by 9E072FC75D54FE1A2B49431C@AdobeID at 2022-09-13T11:32:06.229Z
```

원격 저장소를 참조할 수도 있습니다(선택 사항).

`aio aem:rde:install 'https://repo1.maven.org/maven2/com/adobe/aem/guides/aem-guides-wknd.all/2.1.0/aem-guides-wknd.all-2.1.0.zip'`

<u>OSGI 구성 배포</u>

`aio aem:rde:install com.adobe.granite.demo.MyServlet.cfg.json`

성공적인 배포에 대한 응답은 다음과 유사합니다.

```
...
#2: deploy completed for osgi-config com.adobe.granite.demo.MyServlet.cfg.json on author,publish - done by 9E0725C05D54FE1A0B49431C@AdobeID at 2022-09-13T11:54:36.390Z
```

<u>번들 배포</u>

번들을 배포하려면 다음을 사용합니다.

`aio aem:rde:install ~/.m2/repository/org/apache/felix/org.apache.felix.gogo.jline/1.1.8/org.apache.felix.gogo.jline-1.1.8.jar`

성공적인 배포에 대한 응답은 다음과 유사합니다.

```
...
#3: deploy staged for osgi-bundle org.apache.felix.gogo.jline-1.1.8.jar on author,publish - done by 9E0725C05D53BE1A0B49431C@AdobeID at 2022-09-14T07:54:28.882Z
```

<u>콘텐츠 파일 배포</u>

컨텐츠 파일을 배포하려면 다음을 사용합니다.

`aio aem:rde:install world.txt -p /apps/hello.txt`

성공적인 배포에 대한 응답은 다음과 유사합니다.

```
..
#4: deploy completed for content-file world.txt on author,publish - done by 9E0729C05C54FE1A0B49431C@AdobeID at 2022-09-14T07:49:30.644Z
```

<u>Apache/Dispatcher 구성 배포</u>

전체 폴더 구조는 이러한 유형의 구성에 대해 zip 파일 형식이어야 합니다. 디스패처 구성 폴더의 루트에서 이 명령을 실행하여 압축할 수 있습니다.

`zip -y -r dispatcher.zip`

그런 다음 이 명령으로 구성을 배포합니다.

`aio aem:rde:install -t dispatcher-config dispatcher-wknd-2.1.0.zip`

성공적으로 배포하면 다음과 유사한 응답이 생성됩니다.

```
..
#5 deploy completed for dispatcher-config dispatcher.zip on author,publish - done by 9E0735C05T54FE1A0B49431C@AdobeID at 2022-10-03T10:26:31.286Z
Logs:
  Cloud manager validator 2.0.49
  2022/10/03 10:26:37 No issues found
  Syntax OK
```

RDE에 배포된 코드는 Cloud Manager 파이프라인과 관련 품질 게이트를 수행하지 않지만, 코드는 아래 코드 샘플에 표시된 대로 오류를 보고하는 일부 분석을 수행합니다.

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

위의 코드 샘플은 번들이 확인되지 않는 경우 동작을 보여 줍니다. 이 경우 &quot;준비된&quot; 상태이며 다른 코드 설치를 통해 해당 요구 사항(이 경우 가져오기 누락)이 충족되는 경우에만 설치됩니다.

### RDE 상태 확인 {#checking-rde-status}

RDE CLI를 사용하여 환경을 배포할 준비가 되었는지, RDE 플러그인을 통해 배포되었는지 확인할 수 있습니다.

실행 중:

`aio aem:rde:status`

반환:

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

명령이 인스턴스 배포에 대한 메모를 반환하는 경우 계속 진행하여 다음 업데이트를 수행할 수 있지만 마지막 업데이트가 아직 인스턴스에 표시되지 않을 수 있습니다.

### 배포 기록 표시 {#show-deployment-history}

다음을 실행하여 RDE에 대한 배포 내역을 확인할 수 있습니다.

`aio aem:rde:history`

는 다음 형식으로 응답을 반환합니다.

`#1: deploy completed for content-package aem-guides-wknd.all-2.1.0.zip on author,publish - done by 029039A55D4DE16A0A494025@AdobeID at 2022-09-12T14:41:55.393Z`

### RDE에서 삭제 {#deleting-from-rde}

CLI 툴을 통해 이전에 RDE에 배포된 구성 및 번들을 삭제할 수 있습니다. 를 사용하십시오 `status` 삭제할 수 있는 목록, 즉 `bsn` 번들 및 `pid` delete 명령에서 참조할 구성

예를 들어 `com.adobe.granite.demo.MyServlet.cfg.json` 이 설치되었고, `bsn` is just `com.adobe.granite.demo.MyServlet`, **cfg.json** 접미사.

콘텐츠 패키지 또는 콘텐츠 파일은 삭제할 수 없습니다. 이러한 RDE를 제거하려면 RDE를 재설정해야 합니다. 이 RDE는 기본 상태로 돌아갑니다.

자세한 내용은 아래 예를 참조하십시오.

```
aio aem:rde:delete com.adobe.granite.csrf.impl.CSRFFilter
#13: delete completed for osgi-config com.adobe.granite.csrf.impl.CSRFFilter on author - done by karl at 2022-09-12T22:01:01.955Z
#14: delete completed for osgi-config com.adobe.granite.csrf.impl.CSRFFilter on publish - done by karl at 2022-09-12T22:01:12.979Z
```

## 재설정 {#reset-rde}

RDE를 재설정하면 작성 인스턴스와 게시 인스턴스 모두에서 모든 사용자 지정 코드, 구성 및 컨텐츠가 제거됩니다. 이 기능은 예를 들어, RDE를 사용하여 특정 기능을 테스트하고 다른 기능을 테스트하기 위해 기본 상태로 재설정하려는 경우 유용합니다.

<!-- Alexandru: hiding for now, please don't delete

Resetting can be done via [Cloud Manager](#reset-the-rde-cloud-manager) or via the [command line](#reset-the-rde-command-line). Resetting takes a few minutes and all existing content and code will be deleted from the RDE.

>[NOTE!]
>
>You must be assigned the Cloud Manager Developer role in order to be able to use the reset feature. If not, a reset action will result in an error.

### Reset the RDE via Command Line {#reset-the-rde-command-line}

You can reset the RDE and return it to a default state by running:

`aio aem:rde:reset`

This usually takes a few minutes. Use the [status command](#checking-rde-status) to check when the environment is ready again.

### Reset the RDE in Cloud Manager {#reset-the-rde-cloud-manager} -->

아래 절차에 따라 Cloud Manager를 사용하여 RDE를 재설정할 수 있습니다.

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)에서 Cloud Manager에 로그인한 다음 적절한 조직을 선택합니다.

1. RDE를 재설정할 프로그램을 클릭합니다.

1. **개요** 페이지에서 화면 상단의 **환경** 탭을 클릭합니다.

   ![환경 탭](/help/implementing/cloud-manager/assets/environments-tab2.png)

   * 또는 **환경** 카드에서 **모두 표시** 버튼을 클릭하여 **환경** 탭으로 직접 이동합니다.

      ![모두 표시 옵션](/help/implementing/cloud-manager/assets/environment-showall.png)

1. 다음 **환경** 창이 열리고 프로그램의 모든 환경이 표시됩니다.

   ![환경 탭](/help/implementing/cloud-manager/assets/environments-tab-populated.png)

1. 재설정할 RDE의 줄임표 단추를 클릭한 다음 을 선택합니다 **재설정**.

   ![환경 세부 정보 보기](/help/implementing/cloud-manager/assets/rde-reset.png)

1. 를 클릭하여 RDE를 재설정할지 확인합니다. **재설정** 클릭합니다.

   ![재설정 확인](/help/implementing/cloud-manager/assets/rde-reset-confirm.png)

1. Cloud Manager는 배너 알림을 통해 재설정 프로세스가 시작되었음을 확인합니다.

   ![배너 알림 재설정](/help/implementing/cloud-manager/assets/rde-reset-banner.png)

RDE 재설정 프로세스가 시작되면 일반적으로 완료하고 환경을 기본 상태로 되돌리는 데 몇 분이 걸립니다. 재설정 프로세스의 상태는 언제든지 **상태** 열 **환경** 카드 또는 **환경** 창을 엽니다.

![RDE 재설정 상태](/help/implementing/cloud-manager/assets/rde-reset-status-environments-card.png)

에서 직접 생략 부호 단추를 사용하여 RDE를 재설정할 수도 있습니다 **환경** 카드 **개요** 페이지.

![환경 카드에서 RDE 재설정](/help/implementing/cloud-manager/assets/rde-reset-environments-card.png)

Cloud Manager를 사용하여 환경을 관리하는 방법에 대한 자세한 내용은 [Cloud Manager 설명서.](/help/implementing/cloud-manager/manage-environments.md)

## 로깅 {#logging}

OSGi 구성을 수정하여 로그 수준을 설정할 수 있습니다. 을(를) 확인합니다. [설명서](/help/implementing/developing/introduction/logging.md) 추가 정보.

## RDE는 클라우드 개발 환경과 어떻게 다릅니까? {#how-are-rds-different-from-cloud-development-environments}

RDE는 클라우드 개발 환경과 유사한 여러 가지 방식으로 사용되지만, 코드를 빠르게 동기화할 수 있도록 몇 가지 아키텍처 차이점이 있습니다. RDE에 코드를 가져오는 메커니즘은 다릅니다. RDE의 경우 로컬 개발 환경에서 코드를 동기화하는 반면 클라우드 개발 환경의 경우 Cloud Manager를 통해 코드를 배포합니다.

이러한 이유로 RDE 환경에서 코드를 확인한 후 비프로덕션 파이프라인을 사용하여 클라우드 개발 환경에 코드를 배포해야 합니다. 마지막으로 프로덕션 파이프라인과 함께 배포하기 전에 코드를 테스트합니다.

<!-- Temporarily hiding this. See CQDOC-19795 for more details

## How many RDEs do I need? {#how-many-rds-do-i-need}

The purchase of additional RDEs for Production programs will be possible beginning with late January.

The number of RDEs needed depends on the make-up and processes of an organization. The most flexible model is where an organization purchases a dedicated RDE for each one of their AEM CS developers. In this model, each developer can test their code on the RDE without needing to coordinate with other team members around whether an RDE environment is available.

At the other extreme, a team with a single RDE may use internal processes to coordinate which developer can use the environment at a given time. This can possibly be whenever a developer has hit an intermediate feature milestone and is ready to validate in a Cloud environment where they can quickly make the changes they need.

An intermediate model is one where an organization purchases a number of RDEs that will create a situation in which not every developer will have a dedicated environment, but there is a greater likelihood of an unused RDE being available. One strategy could be to allocate an RDE per scrum team or major feature. Internal processes may be used to coordinate usage of the environments. -->
