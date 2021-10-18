---
title: Adobe Experience Manager as a Cloud Service에 대한 OSGi 구성
description: '암호 값 및 환경별 값으로 OSGi 구성 '
feature: Deploying
exl-id: f31bff80-2565-4cd8-8978-d0fd75446e15
source-git-commit: 9f1183430255bd4f026eedff5c9e8f76ce68b76f
workflow-type: tm+mt
source-wordcount: '2936'
ht-degree: 0%

---

# Adobe Experience Manager as a Cloud Service에 대한 OSGi 구성 {#configuring-osgi-for-aem-as-a-cloud-service}

[](https://www.osgi.org/) OSG는 AEM(Adobe Experience Manager)의 기술 스택에서 기본 요소입니다. AEM 및 해당 구성의 복합 번들을 제어하는 데 사용됩니다.

OSGi는 소규모, 재사용 가능한, 공동 작업 구성 요소에서 애플리케이션을 구축할 수 있도록 해주는 표준화된 프리미티브(primitives)를 제공합니다. 이러한 구성 요소는 응용 프로그램으로 작성하고 배포할 수 있습니다. 이를 통해 OSGi 번들을 개별적으로 시작, 중지, 설치 및 설치할 수 있으므로 쉽게 관리할 수 있습니다. 상호 종속성은 자동으로 처리됩니다. 각 OSGi 구성 요소는 다양한 번들 중 하나에 포함되어 있습니다. 자세한 내용은 [OSGi 사양](https://www.osgi.org/Specifications/HomePage)을 참조하십시오.

AEM 코드 프로젝트의 일부인 구성 파일을 통해 OSGi 구성 요소에 대한 구성 설정을 관리할 수 있습니다.

## OSGi 구성 파일 {#osgi-configuration-files}

구성 변경 사항은 AEM Project의 코드 패키지(`ui.apps`)에서 실행 모드별 구성 폴더 아래의 구성 파일(`.cfg.json`)로 정의됩니다.

`/apps/example/config.<runmode>`

OSGi 구성 파일의 형식은 Apache Sling 프로젝트에 의해 정의된 `.cfg.json` 형식을 사용하여 JSON을 기반으로 합니다.

OSGi 구성은 OSGi 구성 요소의 Java™ 클래스 이름으로 기본 설정되는 PID(영구 ID)를 통해 OSGi 구성 요소를 타깃팅합니다. 예를 들어 다음을 통해 구현된 OSGi 서비스에 대한 OSGi 구성을 제공합니다.

`com.example.workflow.impl.ApprovalWorkflow.java`

osgI 구성 파일은 다음 위치에 정의되어 있습니다.

`/apps/example/config/com.example.workflow.impl.ApprovalWorkflow.cfg.json`

cfg.json OSGi 구성 형식을 따릅니다.

>[!NOTE]
>
>이전 버전의 AEM에서는 .cfg, .config 및 XML sling:OsgiConfig 리소스 정의와 같은 다양한 파일 형식을 사용하여 OSGi 구성 파일을 지원합니다. 이러한 형식은 cfg.json OSGi 구성 형식으로 대체됩니다.

## 런타임 모드 해상도 {#runmode-resolution}

특정 OSGi 구성은 런타임 모드를 사용하여 특정 AEM 인스턴스에 타깃팅할 수 있습니다. 실행 모드를 사용하려면 `/apps/example`(예: 프로젝트 이름)에 다음 형식으로 구성 폴더를 만드십시오.

`/apps/example/config.<author|publish>.<dev|stage|prod>/`

구성 폴더 이름에 정의된 실행 모드가 AEM에서 사용하는 실행 모드와 일치하는 경우 이러한 폴더의 모든 OSGi 구성이 사용됩니다.

예를 들어, AEM에서 런타임 모드 작성자 및 개발을 사용하는 경우 `/apps/example/config.author/` 및 `/apps/example/config.author.dev/`의 구성 노드가 적용되고, `/apps/example/config.publish/` 및 `/apps/example/config.author.stage/`의 구성 노드는 적용되지 않습니다.

동일한 PID에 대해 여러 구성을 적용할 수 있으면 일치하는 실행 모드가 가장 많은 구성이 적용됩니다.

이 규칙의 세부기간은 PID 수준입니다. 즉, 동일한 PID에 대해 `/apps/example/config.author/` 및 `/apps/example/config.author.dev/`에서 더 구체적인 속성을 동일한 PID에 대해 정의할 수 없습니다. 일치하는 실행 모드가 가장 많은 구성은 전체 PID에 적용됩니다.

>[!NOTE]
>
>`config.preview` OSGI 구성 폴더 **은(는) `config.publish`을(를) 선언할 수 없는 것과 같은 방식으로 선언할 수 없습니다.** 대신 미리 보기 계층은 게시 계층의 값에서 해당 OSGI 구성을 상속합니다.

로컬에서 개발할 때 런타임 모드 시작 매개 변수를 전달하여 어떤 런타임 모드 OSGI 구성이 사용되는지를 지시할 수 있습니다.

## OSGi 구성 값 유형 {#types-of-osgi-configuration-values}

Adobe Experience Manager as a Cloud Service에서 사용할 수 있는 OSGi 구성 값에는 세 가지 종류가 있습니다.

1. **인라인 값**: OSGi 구성으로 코딩되고 Git에 저장된 값입니다. 예:

   ```json
   {
      "connection.timeout": 1000
   }
   ```

1. **보안상의 이유로 Git에 저장해서는 안 되는 값인 비밀 값**. 예:

   ```json
   {
   "api-key": "$[secret:server-api-key]"
   } 
   ```

1. **환경 특정 값**(개발 환경에 따라 다른 값)이며, 따라서 실행 모드(Adobe Experience Manager as a Cloud Service에 단일  `dev` 실행 모드가 있으므로)별로 정확하게 타깃팅할 수 없습니다. 예:

   ```json
   {
    "url": "$[env:server-url]"
   }
   ```

   단일 OSGi 구성 파일은 이러한 구성 값 유형의 모든 조합을 함께 사용할 수 있습니다. 예:

   ```json
   {
   "connection.timeout": 1000,
   "api-key": "$[secret:server-api-key]",
   "url": "$[env:server-url]"
   }
   ```

## 적절한 OSGi 구성 값 유형을 선택하는 방법 {#how-to-choose-the-appropriate-osgi-configuration-value-type}

OSGi의 일반적인 사용 사례에서는 인라인 OSGi 구성 값을 사용합니다. 환경별 구성은 개발 환경 간에 값이 다른 특정 사용 사례에 대해서만 사용됩니다.

![](assets/choose-configuration-value-type_res1.png)

환경별 구성은 인라인 값을 포함하는 기존의 정적으로 정의된 OSGi 구성을 확장하여 Cloud Manager API를 통해 외부에서 OSGi 구성 값을 관리하는 기능을 제공합니다. 인라인 값을 정의하고 Git에 저장하는 일반적인 기존의 접근 방식과 환경 특정 구성으로 추상화하는 방법을 사용해야 하는 경우를 이해하는 것이 중요합니다.

다음 지침은 비보안 및 비밀 환경별 구성을 사용해야 하는 경우를 설명합니다.

### 인라인 구성 값을 사용해야 하는 경우 {#when-to-use-inline-configuration-values}

인라인 구성 값은 표준 접근 방식으로 간주되며 가능한 경우 사용해야 합니다. 인라인 구성은 다음과 같은 이점을 제공합니다.

* Git의 거버넌스 및 버전 내역을 통해 유지 관리됩니다
* 값은 코드 배포에 암묵적으로 연결됩니다
* 추가적인 배포 고려 사항이나 조정이 필요하지 않습니다

OSGi 구성 값을 정의할 때마다 인라인 값으로 시작하고 사용 사례에 필요한 경우 암호나 환경 특정 구성만 선택합니다.

### 비보안 환경별 구성 값을 사용해야 하는 경우 {#when-to-use-non-secret-environment-specific-configuration-values}

미리 보기 계층에 대해 값이 다르거나 개발 환경에 따라 다를 경우 비보안 구성 값에 환경 특정 구성(`$[env:ENV_VAR_NAME]`)만 사용하십시오. 여기에는 로컬 개발 인스턴스 및 모든 Adobe Experience Manager as a Cloud Service 개발 환경이 포함됩니다. 미리 보기 계층의 고유한 값을 설정하는 것 외에도 Adobe Experience Manager as a Cloud Service 스테이지 또는 프로덕션 환경에 비보안 환경별 구성을 사용하지 마십시오.

* 게시 및 미리 보기 계층 간에 다른 구성 값이나 로컬 개발 인스턴스를 포함하여 개발 환경이 서로 다른 값에 대해서만 비비밀 환경별 구성을 사용하십시오.
* 미리 보기 계층이 게시 계층과 달라야 하는 시나리오 외에도 스테이지 및 프로덕션 비비밀 값에 대한 OSGi 구성의 표준 인라인 값을 사용합니다. 이와 관련하여 런타임 시 스테이지 및 프로덕션 환경에 쉽게 구성을 변경할 수 있도록 환경별 구성을 사용하지 않는 것이 좋습니다. 이러한 변경 사항은 소스 코드 관리를 통해 가져와야 합니다.

### 보안 환경별 구성 값을 사용해야 하는 경우 {#when-to-use-secret-environment-specific-configuration-values}

Adobe Experience Manager as a Cloud Service에서는 보안상의 이유로 암호, 개인 API 키 또는 Git에 저장할 수 없는 다른 모든 값과 같은 비밀 OSGi 구성 값에 환경별 구성(`$[secret:SECRET_VAR_NAME]`)을 사용해야 합니다.

보안 환경별 구성을 사용하여 단계 및 프로덕션을 포함하여 모든 Adobe Experience Manager as a Cloud Service 환경에 기밀에 대한 값을 저장합니다.

## OSGi 구성 만들기 {#creating-sogi-configurations}

아래에 설명된 대로 OSGi 구성을 만드는 방법에는 두 가지가 있습니다. 이전의 접근 방식은 일반적으로 개발자가 잘 알려진 OSGi 속성 및 값을 가지고 있고 AEM에서 제공한 OSGi 구성 요소에 대해 후자가 있는 사용자 지정 OSGi 구성 요소를 구성하는 데 사용됩니다.

### OSGi 구성 작성 {#writing-osgi-configurations}

JSON 형식 OSGi 구성 파일은 AEM 프로젝트에서 직접 작성하여 사용할 수 있습니다. 이는 알려진 OSGi 구성 요소 및 특히 구성을 정의하는 동일한 개발자가 디자인하고 개발한 사용자 정의 OSGi 구성 요소에 대한 OSGi 구성을 만드는 가장 빠른 방법입니다. 이 접근 방식은 다양한 런타임 모드 폴더에서 동일한 OSGi 구성 요소에 대한 구성을 복사/붙여넣기와 업데이트하는 데도 사용할 수 있습니다.

1. IDE에서 `ui.apps` 프로젝트를 열고 새 OSGi 구성을 적용해야 하는 실행 모드를 대상으로 하는 구성 폴더(`/apps/.../config.<runmode>`)를 찾거나 만듭니다
1. 이 구성 폴더에서 새 `<PID>.cfg.json` 파일을 만듭니다. PID는 OSGi 구성 요소의 영구 ID입니다. 일반적으로 OSGi 구성 요소 구현의 전체 클래스 이름입니다. 예:
   `/apps/.../config/com.example.workflow.impl.ApprovalWorkflow.cfg.json`
OSGi 구성 팩토리 파일 이름은  `<factoryPID>-<name>.cfg.json` 이름 지정 규칙을 사용합니다
1. 새 `.cfg.json` 파일을 열고 [JSON OSGi 구성 형식](https://sling.apache.org/documentation/bundles/configuration-installer-factory.html#configuration-files-cfgjson-1)에 따라 OSGi 속성 및 값 쌍에 대한 키/값 조합을 정의합니다.
1. 새 `.cfg.json` 파일에 변경 내용을 저장합니다.
1. 새로운 OSGi 구성 파일을 Git에 추가 및 커밋

### AEM SDK Quickstart를 사용하여 OSGi 구성 생성 {#generating-osgi-configurations-using-the-aem-sdk-quickstart}

AEM SDK Quickstart Jar의 AEM Web Console을 사용하여 OSGi 구성 요소를 구성하고 OSGi 구성을 JSON으로 내보낼 수 있습니다. 이 구성 요소는 AEM 프로젝트에서 OSGi 구성을 정의하는 개발자가 OSGi 속성 및 해당 값 형식을 제대로 이해하지 못할 수 있는 AEM 제공 OSGi 구성 요소를 구성하는 데 유용합니다.

>[!NOTE]
>
>AEM 웹 콘솔의 구성 UI는 `.cfg.json` 파일을 저장소에 씁니다. 따라서 AEM 프로젝트 정의 OSGi 구성이 생성된 구성과 다를 수 있는 경우 로컬 개발 중에 예상치 못한 잠재적인 동작을 방지하기 위해 이러한 점에 유의하십시오.

1. 관리 사용자로 AEM SDK Quickstart Jar의 AEM 웹 콘솔에 로그인합니다
1. OSGi > 구성으로 이동합니다.
1. 구성하려면 OSGi 구성 요소를 찾아 편집할 제목을 누릅니다
   ![OSGi 구성](./assets/configuring-osgi/configuration.png)
1. 필요에 따라 웹 UI를 통해 OSGi 구성 속성 값을 편집합니다
1. 안전한 위치에 영구 ID(PID)를 기록합니다. 나중에 OSGi 구성 JSON을 생성하는 데 사용됩니다
1. Save 를 누릅니다
1. OSGi > OSGi 설치 프로그램 구성 프린터로 이동합니다.
1. 5단계에서 복사한 PID에 붙여넣습니다. 직렬화 형식이 &quot;OSGi Configurator JSON&quot;으로 설정되어 있는지 확인합니다.
1. 인쇄 탭
1. JSON 형식의 OSGi 구성은 직렬화된 구성 속성 섹션에 표시됩니다
   ![OSGi 설치 프로그램 구성 프린터](./assets/configuring-osgi/osgi-installer-configurator-printer.png)
1. IDE에서 `ui.apps` 프로젝트를 열고 새 OSGi 구성을 적용해야 하는 실행 모드를 대상으로 하는 구성 폴더(`/apps/.../config.<runmode>`)를 찾거나 만듭니다.
1. 이 구성 폴더에서 새 `<PID>.cfg.json` 파일을 만듭니다. PID는 5단계의 값과 동일합니다.
1. 10단계의 직렬화된 구성 속성을 `.cfg.json` 파일에 붙여넣습니다.
1. 변경 내용을 새 `.cfg.json` 파일에 저장합니다.
1. 새로운 OSGi 구성 파일을 Git에 추가하고 커밋합니다.


## OSGi 구성 속성 형식 {#osgi-configuration-property-formats}

### 인라인 값 {#inline-values}

인라인 값은 표준 JSON 구문에 따라 표준 이름-값 쌍으로 형식이 지정됩니다. 예:

```json
{
   "my_var1": "val",
   "my_var2": [ "abc", "def" ],
   "my_var3": 500
}
```

### 환경별 구성 값 {#environment-specific-configuration-values}

OSGi 구성은 환경별로 정의될 변수에 대한 자리 표시자를 지정해야 합니다.

```
use $[env:ENV_VAR_NAME]
```

고객은 사용자 지정 코드와 관련된 OSGI 구성 속성에만 이 기술을 사용해야 합니다. Adobe 정의 OSGI 구성을 재정의하는 데 이 구성 요소를 사용하지 않아야 합니다.

>[!NOTE]
>
>자리 표시자는 [포인터 문](/help/implementing/deploying/overview.md#repoinit)에 사용할 수 없습니다.

### 비밀 구성 값 {#secret-configuration-values}

OSGi 구성은 환경에 따라 정의될 암호로 대한 자리 표시자를 지정해야 합니다.

```
use $[secret:SECRET_VAR_NAME]
```

### 변수 이름 지정 {#variable-naming}

다음은 환경별 구성 값과 비밀 구성 값 모두에 적용됩니다.

변수 이름은 다음 규칙을 따라야 합니다.

* 최소 길이: 2개
* 최대 길이: 100년
* regex와 일치해야 함: `[a-zA-Z_][a-zA-Z_0-9]*`

변수의 값은 2048자를 초과할 수 없습니다.

>[!NOTE]
>
>`INTERNAL_` 접두사가 있는 변수 이름은 Adobe에 의해 예약됩니다. 이 접두사로 시작하는 모든 고객 설정 변수는 무시됩니다. 고객은 이러한 변수를 참조해서도 안 됩니다.

### 기본값 {#default-values}

다음은 환경별 구성 값과 비밀 구성 값 모두에 적용됩니다.

환경 별 값이 설정되지 않은 경우 런타임 시 자리 표시자는 교체되지 않고 보간이 발생하지 않으므로 그대로 유지됩니다. 이를 방지하기 위해 다음 구문을 사용하여 자리 표시자의 일부로 기본값을 제공할 수 있습니다.

```
$[env:ENV_VAR_NAME;default=<value>]
```

기본값이 제공되면 자리 표시자는 제공된 경우 환경 별 값으로 대체되거나 제공된 기본값으로 대체됩니다.

### 로컬 개발 {#local-development}

다음은 환경별 구성 값과 비밀 구성 값 모두에 적용됩니다.

변수는 런타임 시 로컬 AEM에서 선택하도록 로컬 환경에서 정의할 수 있습니다. 예를 들어 Linux®의 경우:

```bash
export ENV_VAR_NAME=my_value
```

AEM을 시작하기 전에 구성에 사용되는 환경 변수를 설정하고 실행하는 간단한 Bash 스크립트를 작성하는 것이 좋습니다. [https://direnv.net/](https://direnv.net/)와 같은 도구는 이 접근 방식을 단순화하는 데 도움이 됩니다. 값의 유형에 따라 모든 사람 간에 공유할 수 있는 경우 소스 코드 관리에 체크 인할 수 있습니다.

비밀의 값은 파일에서 읽습니다. 따라서 암호를 사용하는 각 자리 표시자에 대해 비밀 값이 포함된 텍스트 파일을 만들어야 합니다.

예를 들어 `$[secret:server_password]`을 사용하는 경우 **server_password**&#x200B;라는 텍스트 파일을 만들어야 합니다. 이러한 모든 비밀 파일은 동일한 디렉토리에 저장해야 하며 프레임워크 속성 `org.apache.felix.configadmin.plugin.interpolation.secretsdir`은 해당 로컬 디렉터리로 구성해야 합니다.

### 작성자 및 게시 구성 {#author-vs-publish-configuration}

OSGI 속성에 작성자와 게시에 대해 다른 값이 필요한 경우:

* [실행 모드 해상도 섹션](#runmode-resolution)에 설명된 대로 별도의 `config.author` 및 `config.publish` OSGi 폴더를 사용해야 합니다.
* 사용해야 하는 독립 변수 이름을 만드는 두 가지 옵션이 있습니다.
   * 첫 번째 옵션인 가 권장됩니다. 다른 값을 정의하도록 선언된 모든 OSGI 폴더(예: `config.author` 및 `config.publish`)에서 동일한 변수 이름을 사용하십시오. 예
      `$[env:ENV_VAR_NAME;default=<value>]`: 기본값이 해당 계층(작성자 또는 게시)의 기본값에 해당합니다. [Cloud Manager API](#cloud-manager-api-format-for-setting-properties)를 통해 또는 클라이언트를 통해 환경 변수를 설정할 때 이 [API 참조 설명서](https://www.adobe.io/apis/experiencecloud/cloud-manager/api-reference.html#/Variables/patchEnvironmentVariables)에 설명된 대로 &quot;service&quot; 매개 변수를 사용하여 계층을 구별하십시오. &quot;service&quot; 매개 변수는 변수의 값을 적절한 OSGI 계층에 바인딩합니다. &quot;작성자&quot;, &quot;게시&quot; 또는 &quot;미리 보기&quot;일 수 있습니다.
   * 두 번째 옵션은 `author_<samevariablename>` 및 `publish_<samevariablename>` 등의 접두사를 사용하여 고유 변수를 선언하는 것입니다.

### 구성 예 {#configuration-examples}

아래 예에서는 단계 및 prod 환경 외에 세 가지 개발 환경이 있다고 가정합니다.

**예제 1**

목적은 OSGI 속성 `my_var1` 값이 스테이지와 프로덕션에 대해 동일하기 위한 것이지만 세 가지 개발 환경에 따라 다릅니다.

<table>
<tr>
<td>
<b>폴더</b>
</td>
<td>
<b>myfile.cfg.json의 컨텐츠</b>
</td>
</tr>
<tr>
<td>
config
</td>
<td>
<pre>
{ 
 "my_var1": "val",
 "my_var2": "abc",
 "my_var3": 500년
}
</pre>
</td>
</tr>
<tr>
<td>
config.dev
</td>
<td>
<pre>
{ 
 "my_var1" : "$[env:my_var1]"
 "my_var2": "abc",
 "my_var3": 500년
}
</pre>
</td>
</tr>
</table>

**예제 2**

목적은 OSGI 속성 `my_var1` 값이 스테이지, prod 및 세 개발 환경에 대해 각각 다르기 위한 것입니다. 따라서 각 개발 환경에 대해 `my_var1` 값을 설정하려면 Cloud Manager API를 호출해야 합니다.

<table>
<tr>
<td>
<b>폴더</b>
</td>
<td>
<b>myfile.cfg.json의 컨텐츠</b>
</td>
</tr>
<tr>
<td>
config.stage
</td>
<td>
<pre>
{ 
 "my_var1": "val1",
 "my_var2": "abc",
 "my_var3": 500년
}
</pre>
</td>
</tr>
<tr>
<td>
config.prod
</td>
<td>
<pre>
{ 
 "my_var1": "val2",
 "my_var2": "abc",
 "my_var3": 500년
}
</pre>
</td>
</tr>
<tr>
<td>
config.dev
</td>
<td>
<pre>
{ 
 "my_var1" : "$[env:my_var1]"
 "my_var2": "abc",
 "my_var3": 500년
}
</pre>
</td>
</tr>
</table>

**예제 3**

목적은 OSGi 속성 `my_var1` 값이 스테이지, 프로덕션 및 개발 환경 중 하나에 대해 동일하지만 다른 두 개발 환경에 대해서는 다릅니다. 이 경우 스테이지 및 프로덕션과 동일한 값을 가져야 하는 개발 환경을 포함하여 각 개발 환경에 대해 `my_var1` 값을 설정하려면 Cloud Manager API를 호출해야 합니다. 이 구성 요소는 **config** 폴더에 설정된 값을 상속하지 않습니다.

<table>
<tr>
<td>
<b>폴더</b>
</td>
<td>
<b>myfile.cfg.json의 컨텐츠</b>
</td>
</tr>
<tr>
<td>
config
</td>
<td>
<pre>
{ 
 "my_var1": "val1",
 "my_var2": "abc",
 "my_var3": 500년
}
</pre>
</td>
</tr>
<tr>
<td>
config.dev
</td>
<td>
<pre>
{ 
 "my_var1" : "$[env:my_var1]"
 "my_var2": "abc",
 "my_var3": 500년
}
</pre>
</td>
</tr>
</table>

이 작업을 수행하는 다른 방법은 **config** 폴더와 동일한 값으로 config.dev 폴더에서 교체 토큰에 대한 기본값을 설정하는 것입니다.

<table>
<tr>
<td>
<b>폴더</b>
</td>
<td>
<b>myfile.cfg.json의 컨텐츠</b>
</td>
</tr>
<tr>
<td>
config
</td>
<td>
<pre>
{ 
 "my_var1": "val1",
 "my_var2": "abc",
 "my_var3": 500년
}
</pre>
</td>
</tr>
<tr>
<td>
config.dev
</td>
<td>
<pre>
{ 
 "my_var1": "$[env:my_var1;default=val1]"
 "my_var2": "abc",
 "my_var3": 500년
}
</pre>
</td>
</tr>
</table>

## 속성 설정을 위한 Cloud Manager API 형식 {#cloud-manager-api-format-for-setting-properties}

API를 구성하는 방법에 대해서는 [이 페이지](https://www.adobe.io/apis/experiencecloud/cloud-manager/docs.html#!AdobeDocs/cloudmanager-api-docs/master/create-api-integration.md)를 참조하십시오.
>[!NOTE]
>
>사용된 Cloud Manager API에 &quot;Deployment Manager - Cloud Service&quot; 역할이 할당되었는지 확인합니다. 다른 역할은 아래의 명령을 모두 실행할 수 없습니다.

### API를 통해 값 설정 {#setting-values-via-api}

API를 호출하면 일반적인 고객 코드 배포 파이프라인과 유사하게, 클라우드 환경에 새 변수 및 값을 배포합니다. 작성자 및 게시 서비스가 다시 시작되고 새 값을 참조합니다(일반적으로 몇 분 정도 걸립니다.).

```
PATCH /program/{programId}/environment/{environmentId}/variables
```

```
]
        {
                "name" : "MY_VAR1",
                "value" : "plaintext value",
                "type" : "string"  <---default
        },
        {
                "name" : "MY_VAR2",
                "value" : "<secret value>",
                "type" : "secretString"
        }
]
```

>[!NOTE]
>기본 변수는 API를 통해 설정되지 않고 OSGi 속성 자체에서 설정됩니다.
>
>자세한 내용은 [이 페이지](https://www.adobe.io/apis/experiencecloud/cloud-manager/api-reference.html#/Environment_Variables/patchEnvironmentVariables)를 참조하십시오.

### API를 통해 값 가져오기 {#getting-values-via-api}

```
GET /program/{programId}/environment/{environmentId}/variables
```

자세한 내용은 [이 페이지](https://www.adobe.io/apis/experiencecloud/cloud-manager/api-reference.html#/Environment_Variables/getEnvironmentVariables)를 참조하십시오.

### API를 통해 값 삭제 {#deleting-values-via-api}

```
PATCH /program/{programId}/environment/{environmentId}/variables
```

변수를 삭제하려면 빈 값과 함께 포함하십시오.

자세한 내용은 [이 페이지](https://www.adobe.io/apis/experiencecloud/cloud-manager/api-reference.html#/Environment_Variables/patchEnvironmentVariables)를 참조하십시오.

### 명령줄에서 값 가져오기 {#getting-values-via-cli}

```bash
$ aio cloudmanager:list-environment-variables ENVIRONMENT_ID
Name     Type         Value
MY_VAR1  string       plaintext value 
MY_VAR2  secretString ****
```


### 명령줄에서 값 설정 {#setting-values-via-cli}

```bash
$ aio cloudmanager:set-environment-variables ENVIRONMENT_ID --variable MY_VAR1 "plaintext value" --secret MY_VAR2 "some secret value"
```

### 명령줄에서 값 삭제 {#deleting-values-via-cli}

```bash
$ aio cloudmanager:set-environment-variables ENVIRONMENT_ID --delete MY_VAR1 MY_VAR2
```

>[!NOTE]
>
>Adobe I/O CLI용 Cloud Manager 플러그인을 사용하여 값을 구성하는 방법에 대한 자세한 내용은 [이 페이지](https://github.com/adobe/aio-cli-plugin-cloudmanager#aio-cloudmanagerset-environment-variables-environmentid)를 참조하십시오.

### 변수 수 {#number-of-variables}

환경당 최대 200개의 변수를 선언할 수 있습니다.

## 보안 및 환경별 구성 값에 대한 배포 고려 사항 {#deployment-considerations-for-secret-and-environment-specific-configuration-values}

보안 및 환경별 구성 값은 Git 외부에 있으므로 정식 Adobe Experience Manager as a Cloud Service 배포 메커니즘의 일부가 아니므로 고객은 Adobe Experience Manager as a Cloud Service 배포 프로세스를 관리, 제어 및 통합해야 합니다.

위에서 언급했듯이 API를 호출하면 일반적인 고객 코드 배포 파이프라인과 유사하게, 새 변수와 값을 클라우드 환경에 배포합니다. 작성자 및 게시 서비스가 다시 시작되고 새 값을 참조합니다(일반적으로 몇 분 정도 걸립니다.). 일반 코드 배포 중에 Cloud Manager에서 실행하는 품질 게이트와 테스트는 이 프로세스 동안 수행되지 않습니다.

일반적으로 고객은 Cloud Manager에서 API를 사용하는 코드를 배포하기 전에 API를 호출하여 환경 변수를 설정합니다. 코드가 이미 배포된 후 기존 변수를 수정할 수도 있습니다.

>[!NOTE]
>
>파이프라인이 사용 중일 때 해당 시점에 종료되는 파이프라인의 일부가 어떤 부분에 따라 AEM 업데이트 또는 고객 배포가 실행될 때 API가 실패할 수 있습니다. 이 오류 응답에는 특정 이유를 나타내지는 않지만 요청이 실패했음을 나타냅니다.

예약된 고객 코드 배포가 기존 변수를 사용하여 새 값을 가지는 시나리오가 있을 수 있으며, 이는 현재 코드에는 적합하지 않습니다. 이것이 우려되는 경우에는 첨가법을 사용하여 변수를 수정하는 것이 좋습니다. 이렇게 하려면 이전 코드가 새 값을 참조하지 않도록 이전 변수의 값을 변경하는 대신 새 변수 이름을 만드십시오. 그런 다음 새 고객 릴리스가 안정되어 표시되면 오래된 값을 제거하도록 선택할 수 있습니다.

마찬가지로 변수 값의 버전은 관리되지 않으므로 코드를 롤백하면 문제를 일으키는 최신 값을 참조할 수 있습니다. 이전에 언급된 첨가제 변수 전략도 여기에 도움이 될 것입니다.

이 추가 변수 전략은 또한 며칠 전의 코드를 다시 배포해야 하는 경우 참조하는 변수 이름과 값이 그대로 유지되는 재해 복구 시나리오에 유용합니다. 이는 고객이 이전 변수를 제거하기 전에 며칠 동안 대기하는 전략에 의존합니다. 그렇지 않으면 이전 코드에는 참조할 적절한 변수가 없습니다.
