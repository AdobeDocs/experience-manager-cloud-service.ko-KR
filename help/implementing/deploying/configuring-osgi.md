---
title: AEM as a Cloud Service에 대한 OSGi 구성
description: '비밀 값 및 환경별 값이 있는 OSGi 구성 '
translation-type: tm+mt
source-git-commit: a04935b3b71cff9f5f0fbc85b4d3db4dd96a28fc
workflow-type: tm+mt
source-wordcount: '2737'
ht-degree: 1%

---


# AEM as a Cloud Service에 대한 OSGi 구성 {#configuring-osgi-for-aem-as-a-cloud-service}

[OSG](https://www.osgi.org/) 는 AEM(Adobe Experience Manager)의 기술 스택에서 기본적인 요소입니다. AEM 및 해당 구성의 합성 번들을 제어하는 데 사용됩니다.

OSGi는 표준화된 프리미티브 값을 제공하므로 애플리케이션을 소규모의 재사용 및 공동 작업 구성 요소로 구성할 수 있습니다. 이러한 구성 요소는 애플리케이션으로 구성하고 배포할 수 있습니다. 이를 통해 OSGi 번들을 중단, 설치 및 개별적으로 시작할 수 있으므로 간편하게 관리할 수 있습니다. 상호 종속성은 자동으로 처리됩니다. 각 OSGi 구성 요소는 다양한 번들 중 하나에 포함됩니다. 자세한 내용은 [OSGi 사양](https://www.osgi.org/Specifications/HomePage)을 참조하십시오.

AEM 코드 프로젝트의 일부인 구성 파일을 통해 OSGi 구성 요소에 대한 구성 설정을 관리할 수 있습니다.

## OSGi 구성 파일 {#osgi-configuration-files}

구성 변경 사항은 AEM 프로젝트의 코드 패키지(`ui.apps`)에서 런타임 모드 특정 구성 폴더 아래의 구성 파일(`.cfg.json`)로 정의됩니다.

`/apps/example/config.<runmode>`

OSGi 구성 파일의 형식은 Apache Sling 프로젝트에 의해 정의된 `.cfg.json` 형식을 사용하는 JSON 기반입니다.

OSGi 구성은 OSGi 구성 요소의 Java 클래스 이름으로 기본적으로 설정되어 있는 PID(Persistent Identification)를 통해 OSGi 구성 요소를 대상으로 합니다. 예를 들어, 다음을 통해 구현된 OSGi 서비스에 대한 OSGi 구성을 제공하려면 다음을 수행합니다.

`com.example.workflow.impl.ApprovalWorkflow.java`

OSGi 구성 파일은 다음 위치에 정의됩니다.

`/apps/example/config/com.example.workflow.impl.ApprovalWorkflow.cfg.json`

cfg.json OSGi 구성 형식을 따릅니다.

>[!NOTE]
>
>이전 버전의 AEM에서는 .cfg, .config 및 XML sling:OsgiConfig 리소스 정의와 같은 다른 파일 형식을 사용하여 OSGi 구성 파일을 지원합니다. 이러한 형식은 cfg.json OSGi 구성 형식으로 대체됩니다.

## 실행 모드 해상도 {#runmode-resolution}

특정 OSGi 구성은 런타임 모드를 사용하여 특정 AEM 인스턴스로 타깃팅할 수 있습니다. 실행 모드를 사용하려면 `/apps/example`(예: 프로젝트 이름) 아래에 구성 폴더를 다음 형식으로 만드십시오.

`/apps/example/config.<author|publish>.<dev|stage|prod>/`

이러한 폴더의 모든 OSGi 구성은 구성 폴더 이름에 정의된 실행 모드가 AEM에서 사용하는 실행 모드와 일치하는 경우 사용됩니다.

예를 들어 AEM에서 런타임 모드 작성자 및 dev를 사용하는 경우 `/apps/example/config.author/` 및 `/apps/example/config.author.dev/`의 구성 노드가 적용되고 `/apps/example/config.publish/` 및 `/apps/example/config.author.stage/`의 구성 노드는 적용되지 않습니다.

동일한 PID에 대해 여러 구성을 적용할 경우 일치하는 실행 모드가 가장 많은 구성이 적용됩니다.

이 규칙의 세부기간은 PID 수준입니다. 즉, 동일한 PID에 대해 `/apps/example/config.author/` 및 `/apps/example/config.author.dev/`의 보다 구체적인 속성을 정의할 수 없습니다.  가장 많은 수의 일치 실행 모드를 가진 구성은 전체 PID에 대해 효과적입니다.

로컬에서 개발할 때 런타임 모드 시작 매개 변수를 전달하여 사용할 런타임 모드 OSGI 구성을 지정할 수 있습니다.

## OSGi 구성 값 유형 {#types-of-osgi-configuration-values}

AEM에서 Cloud Service으로 사용할 수 있는 OSGi 구성 값에는 3가지 종류가 있습니다.

1. **인라인 값**. OSGi 구성에 하드 코딩되어 Git에 저장된 값입니다. 예:

   ```json
   {
      "connection.timeout": 1000
   }
   ```

1. **보안 값** - 보안상의 이유로 Git에 저장하지 않아야 하는 값입니다. 예:

   ```json
   {
   "api-key": "$[secret:server-api-key]"
   } 
   ```

1. **환경별 값** - 개발 환경에 따라 달라서 실행 모드로 정확하게 타깃팅할 수 없습니다(Cloud Service에 단일  `dev` 실행 모드가 있으므로). 예:

   ```json
   {
    "url": "$[env:server-url]"
   }
   ```

   단일 OSGi 구성 파일은 이러한 구성 값 유형의 조합을 함께 사용할 수 있습니다. 예:

   ```json
   {
   "connection.timeout": 1000,
   "api-key": "$[secret:server-api-key]",
   "url": "$[env:server-url]"
   }
   ```

## 적절한 OSGi 구성 값 유형을 선택하는 방법 {#how-to-choose-the-appropriate-osgi-configuration-value-type}

OSGi의 일반적인 경우 인라인 OSGi 구성 값을 사용합니다. 환경별 구성은 개발 환경 간에 값이 다른 특정 사용 사례에만 사용됩니다.

![](assets/choose-configuration-value-type_res1.png)

환경별 구성은 인라인 값을 포함하는 기존의 정적으로 정의된 OSGi 구성을 확장하여 Cloud Manager API를 통해 외부에서 OSGi 구성 값을 관리하는 기능을 제공합니다. 인라인 값을 정의하고 Git에 저장하는 일반적인 방식과 기존 방식을 사용해야 하는 시기와 환경별 구성으로 값을 추출하는 방법을 이해하는 것이 중요합니다.

다음 지침에서는 비보안 및 비밀 환경별 구성을 사용할 때 다룹니다.

### 인라인 구성 값 {#when-to-use-inline-configuration-values} 사용 시기

인라인 구성 값은 표준 방법으로 간주되며 가능한 경우 사용해야 합니다. 인라인 구성은 다음과 같은 이점을 제공합니다.

* Git의 거버넌스 및 버전 내역을 통해 유지 관리됩니다
* 값은 코드 배포에 암시적으로 연결되어 있습니다.
* 추가 배포 고려 사항 또는 조정이 필요하지 않습니다.

OSGi 구성 값을 정의할 때마다 인라인 값으로 시작하면 사용 사례에 필요한 경우 비밀 또는 환경 특정 구성만 선택합니다.

### 비비밀 환경별 구성 값을 사용하는 경우 {#when-to-use-non-secret-environment-specific-configuration-values}

값이 개발 환경에 따라 다를 때 비보안 구성 값에 환경별 구성(`$[env:ENV_VAR_NAME]`)만 사용하십시오. 여기에는 로컬 개발 인스턴스와 Cloud Service 개발 환경으로 AEM이 포함됩니다. Cloud Service 스테이지 또는 프로덕션 환경에서 AEM에 대해 비비밀 환경별 구성을 사용하지 마십시오.

* 로컬 개발 인스턴스를 포함하여 개발 환경에 따라 다른 구성 값에 비비밀 환경별 구성만 사용하십시오.
* 대신 스테이지 및 프로덕션 비비밀 값에 대해 OSGi 구성에서 표준 인라인 값을 사용합니다.  이와 관련하여 런타임 시 스테이지 및 프로덕션 환경에 대한 구성 변경 작업을 용이하게 하기 위해 환경별 구성을 사용하지 않는 것이 좋습니다.이러한 변경 사항은 소스 코드 관리를 통해 도입해야 합니다.

### 보안 환경별 구성 값 {#when-to-use-secret-environment-specific-configuration-values} 사용 시기

Cloud Service의 경우 암호, 개인 API 키 또는 보안상의 이유로 Git에 저장할 수 없는 기타 모든 값과 같은 모든 비밀 OSGi 구성 값에 환경별 구성(`$[secret:SECRET_VAR_NAME]`)을 사용해야 합니다.

보안 환경별 구성을 사용하여 스테이지 및 프로덕션 등 Cloud Service 환경에서 모든 AEM에 기밀에 대한 가치를 저장할 수 있습니다.

<!-- ### Adding a New Configuration to the Repository {#adding-a-new-configuration-to-the-repository}

#### What You Need to Know {#what-you-need-to-know}

To add a new configuration to the repository you need to know the following:

1. The **Persistent Identity** (PID) of the service.

   Reference the **Configurations** field in the Web console. The name is shown in brackets after the bundle name (or in the **Configuration Information** towards the bottom of the page).

   For example, create a node `com.day.cq.wcm.core.impl.VersionManagerImpl.` to configure **AEM WCM Version Manager**.

   ![chlimage_1-141](assets/chlimage_1-141.png)

1. Whether a specific runmode is required. Create the folder:

    * `config` - for all run modes
    * `config.author` - for the author environment
    * `config.publish` - for the publish environment
    * `config.<run-mode>` - as appropriate

1. Whether a **Configuration** or **Factory Configuration** is necessary.
1. The individual parameters to be configured; including any existing parameter definitions that will need to be recreated.

   Reference the individual parameter field in the Web console. The name is shown in brackets for each parameter.

   For example, create a property
   `versionmanager.createVersionOnActivation` to configure **Create Version on Activation**.

   ![chlimage_1-142](assets/chlimage_1-142.png)

1. Does a configuration already exist in `/libs`? To list all configurations in your instance, use the **Query** tool in CRXDE Lite to submit the following SQL query:

   `select * from sling:OsgiConfig`

   If so, this configuration can be copied to ` /apps/<yourProject>/`, then customized in the new location. -->

## OSGi 구성 만들기 {#creating-sogi-configurations}

아래에 설명된 바와 같이 새 OSGi 구성을 만드는 방법은 두 가지가 있습니다. 이전 방법은 일반적으로 개발자에 의한 잘 알려진 OSGi 속성과 값을 갖는 사용자 지정 OSGi 구성 요소 및 AEM 제공 OSGi 구성 요소에 대한 후자를 구성하는 데 사용됩니다.

### OSGi 구성 작성 중 {#writing-osgi-configurations}

JSON 형식 OSGi 구성 파일은 AEM 프로젝트에서 직접 직접 작성할 수 있습니다. 널리 알려진 OSGi 구성 요소 및 구성을 정의하는 동일한 개발자에 의해 설계되고 개발된 맞춤형 OSGi 구성 요소에 대한 OSGi 구성을 만드는 가장 빠른 방법입니다. 또한 이 방법을 사용하여 다양한 런타임 모드 폴더에 있는 동일한 OSGi 구성 요소에 대한 구성을 복사/붙여 넣고 업데이트할 수 있습니다.

1. IDE에서 `ui.apps` 프로젝트를 열고 새 OSGi 구성이 적용되어야 하는 런타임 모드를 대상으로 하는 구성 폴더(`/apps/.../config.<runmode>`)를 찾거나 만듭니다
1. 이 구성 폴더에서 새 `<PID>.cfg.json` 파일을 만듭니다. PID는 OSGi 구성 요소의 영구 ID입니다. 일반적으로 OSGi 구성 요소 구현의 전체 클래스 이름입니다. 예:
   `/apps/.../config/com.example.workflow.impl.ApprovalWorkflow.cfg.json`
OSGi 구성 팩토리 파일 이름은  `<PID>-<factory-name>.cfg.json` 이름 지정 규칙을 사용합니다
1. 새 `.cfg.json` 파일을 열고 [JSON OSGi 구성 형식](https://sling.apache.org/documentation/bundles/configuration-installer-factory.html#configuration-files-cfgjson-1)에 따라 OSGi 속성 및 값 쌍의 키/값 조합을 정의합니다.
1. 변경 내용을 새 `.cfg.json` 파일에 저장합니다.
1. 새로운 OSGi 구성 파일을 Git에 추가 및 커밋

### AEM SDK Quickstart {#generating-osgi-configuratuions-using-the-aem-sdk-quickstart}을(를) 사용하여 OSGi 구성 생성

AEM SDK Quickstart Jar의 AEM 웹 콘솔을 사용하여 OSGi 구성 요소를 구성하고 OSGi 구성을 JSON으로 내보낼 수 있습니다. 이 기능은 AEM 프로젝트에서 OSGi 구성을 정의하는 개발자가 OSGi 속성 및 해당 값 형식을 제대로 이해하지 못할 수 있는 AEM 제공 OSGi 구성 요소를 구성하는 데 유용합니다. AEM 웹 콘솔의 구성 UI를 사용하면 `.cfg.json` 파일이 저장소에 작성되므로 AEM 프로젝트 정의 OSGi 구성이 생성된 구성과 다를 수 있으므로 로컬 개발 중에 예상치 못한 잠재적인 동작을 방지하기 위해 이 점을 주의하십시오.

1. AEM SDK Quickstart Jar의 AEM 웹 콘솔에 관리 사용자로 로그인합니다
1. OSGi > 구성으로 이동합니다.
1. 구성할 OSGi 구성 요소를 찾고 제목을 눌러 편집합니다.
   ![OSGi 구성](./assets/configuring-osgi/configuration.png)
1. 필요에 따라 웹 UI를 통해 OSGi 구성 속성 값 편집
1. PID(Persistent Id)를 안전한 위치에 기록합니다. 나중에 OSGi 구성 JSON을 생성하는 데 사용됩니다.
1. 저장을 탭합니다.
1. OSGi > OSGi 설치 프로그램 구성 프린터로 이동합니다.
1. 5단계에서 복사한 PID에 붙여넣기를 통해 일련화 형식이 &quot;OSGi Configurator JSON&quot;으로 설정되어 있는지 확인합니다.
1. 인쇄를 누릅니다.
1. JSON 형식의 OSGi 구성은 직렬화된 구성 속성 섹션에 표시됩니다.
   ![OSGi 설치 프로그램 구성 프린터](./assets/configuring-osgi/osgi-installer-configurator-printer.png)
1. IDE에서 `ui.apps` 프로젝트를 열고 새 OSGi 구성이 적용되어야 하는 런타임 모드를 대상으로 하는 구성 폴더(`/apps/.../config.<runmode>`)를 찾거나 만듭니다.
1. 이 구성 폴더에서 새 `<PID>.cfg.json` 파일을 만듭니다. PID는 5단계의 값과 동일합니다.
1. 10단계의 직렬화된 구성 속성을 `.cfg.json` 파일에 붙여 넣습니다.
1. 변경 내용을 새 `.cfg.json` 파일에 저장합니다.
1. 새로운 OSGi 구성 파일을 Git에 추가하고 커밋합니다.


## OSGi 구성 속성 형식 {#osgi-configuration-property-formats}

### 인라인 값 {#inline-values}

예상대로 인라인 값은 표준 JSON 구문에 따라 표준 이름-값 쌍으로 형식이 지정됩니다. 예:

```json
{
   "my_var1": "val",
   "my_var2": [ "abc", "def" ],
   "my_var3": 500
}
```

### 환경별 구성 값 {#environment-specific-configuration-values}

OSGi 구성은 환경에 따라 정의될 변수의 자리 표시자를 지정해야 합니다.

```
use $[env:ENV_VAR_NAME]
```

고객은 사용자 지정 코드와 관련된 OSGI 구성 속성에만 이 기술을 사용해야 합니다.Adobe 정의 OSGI 구성을 재정의하는 데 사용해서는 안 됩니다.

### 비밀 구성 값 {#secret-configuration-values}

OSGi 구성은 환경에 따라 정의될 수 있는 보안에 대한 자리 표시자를 지정해야 합니다.

```
use $[secret:SECRET_VAR_NAME]
```

### 변수 이름 지정 {#variable-naming}

다음은 환경별 및 비밀 구성 값 모두에 적용됩니다.

변수 이름은 다음 규칙을 따라야 합니다.

* 최소 길이:2
* 최대 길이:100년
* regex와 일치:`[a-zA-Z_][a-zA-Z_0-9]*`

변수의 값은 2048자를 초과할 수 없습니다.

### 기본값 {#default-values}

다음은 환경별 및 비밀 구성 값 모두에 적용됩니다.

환경별 값이 설정되지 않은 경우, 런타임 시 보간이 발생하지 않으므로 자리 표시자가 교체되지 않고 그대로 유지됩니다. 이를 방지하기 위해 다음 구문을 사용하여 자리 표시자의 일부로 기본값을 제공할 수 있습니다.

```
$[env:ENV_VAR_NAME;default=<value>]
```

기본값이 제공되면 자리 표시자는 제공된 경우 환경 단위 값 또는 제공된 기본값으로 대체됩니다.

### 로컬 개발 {#local-development}

다음은 환경별 및 비밀 구성 값 모두에 적용됩니다.

변수는 런타임 시 로컬 AEM에서 선택되도록 로컬 환경에서 정의할 수 있습니다. 예를 들어, Linux에서는:

```bash
export ENV_VAR_NAME=my_value
```

AEM을 시작하기 전에 구성에 사용된 환경 변수를 설정하고 이를 실행하는 간단한 배쉬 스크립트를 작성하는 것이 좋습니다. [https://direnv.net/](https://direnv.net/)과 같은 도구를 사용하여 이 방법을 단순화합니다. 값 유형에 따라 모든 사람 간에 공유할 수 있는 경우 소스 코드 관리에 체크 인할 수 있습니다.

비밀 값은 파일에서 읽습니다. 따라서 암호를 사용하는 각 자리 표시자에 대해 비밀 값이 포함된 텍스트 파일을 만들어야 합니다.

예를 들어 `$[secret:server_password]`을(를) 사용하는 경우 **server_password**&#x200B;라는 텍스트 파일을 만들어야 합니다. 이러한 모든 비밀 파일은 동일한 디렉토리에 저장해야 하며 프레임워크 속성 `org.apache.felix.configadmin.plugin.interpolation.secretsdir`은 해당 로컬 디렉터리로 구성해야 합니다.

### 작성자 및 게시 구성 {#author-vs-publish-configuration}

OSGI 속성에 작성자와 게시에 서로 다른 값이 필요한 경우:

* [런타임 모드 해상도 섹션](#runmode-resolution)에 설명된 대로 별도의 `config.author` 및 `config.publish` OSGi 폴더를 사용해야 합니다.
* 독립적인 변수 이름을 사용해야 합니다. 변수 이름이 동일한 `author_<variablename>` 및 `publish_<variablename>` 접두어를 사용하는 것이 좋습니다.

### 구성 예 {#configuration-examples}

아래 예에서 단계 및 prod 환경 외에 3개의 개발 환경이 있다고 가정합니다.

**예 1**

의도는 OSGI 속성 `my_var1` 값이 스테이지와 prod에 대해 동일하지만 3개의 개발 환경에 따라 다릅니다.

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
 "my_var1":"val",
 "my_var2":"abc",
 "my_var3":500년
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
 "my_var1" :"$[env:my_var1]"
 "my_var2":"abc",
 "my_var3":500년
}
</pre>
</td>
</tr>
</table>

**예 2**

의도는 OSGI 속성 `my_var1` 값이 단계, prod 및 3개의 개발 환경에 대해 각각 다르게 하기 위한 것입니다. 따라서 각 개발 env에 대해 `my_var1` 값을 설정하려면 클라우드 관리자 API를 호출해야 합니다.

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
 "my_var1":"val1",
 "my_var2":"abc",
 "my_var3":500년
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
 "my_var1":"val2",
 "my_var2":"abc",
 "my_var3":500년
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
 "my_var1" :"$[env:my_var1]"
 "my_var2":"abc",
 "my_var3":500년
}
</pre>
</td>
</tr>
</table>

**예 3**

의도하는 것은 OSGi 속성 `my_var1` 값이 스테이지, 프로덕션 및 개발 환경 중 하나에 대해 동일하지만 다른 두 개발 환경에 대해서는 다릅니다. 이 경우 준비 및 프로덕션과 동일한 값을 가져야 하는 개발 환경을 포함하여 각 개발 환경에 대해 `my_var1` 값을 설정하려면 클라우드 관리자 API를 호출해야 합니다. **config** 폴더에 설정된 값을 상속하지 않습니다.

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
 "my_var1":"val1",
 "my_var2":"abc",
 "my_var3":500년
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
 "my_var1" :"$[env:my_var1]"
 "my_var2":"abc",
 "my_var3":500년
}
</pre>
</td>
</tr>
</table>

이를 위한 또 다른 방법은 config.dev 폴더에 있는 교체 토큰의 기본값을 설정하여 **config** 폴더에 있는 값과 동일한 값을 설정합니다.

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
 "my_var1":"val1",
 "my_var2":"abc",
 "my_var3":500년
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
 "my_var1":"$[env:my_var1;default=val1]"
 "my_var2":"abc",
 "my_var3":500년
}
</pre>
</td>
</tr>
</table>

## 속성 설정 {#cloud-manager-api-format-for-setting-properties}에 대한 클라우드 관리자 API 형식

API를 구성해야 하는 방법에 대해서는 [이 페이지](https://www.adobe.io/apis/experiencecloud/cloud-manager/docs.html#!AdobeDocs/cloudmanager-api-docs/master/create-api-integration.md)을 참조하십시오.
>[!NOTE]
>
>사용된 클라우드 관리자 API에 &quot;배포 관리자 - Cloud Service&quot; 역할이 할당되었는지 확인합니다. 다른 역할은 아래 명령을 모두 실행할 수 없습니다.

### API {#setting-values-via-api}를 통해 값 설정

API를 호출하면 일반적인 고객 코드 배포 파이프라인과 유사한 새로운 변수와 값이 클라우드 환경에 배포됩니다. 작성자 및 게시 서비스가 다시 시작되고 새 값을 참조하며 일반적으로 몇 분 정도 걸립니다.

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

기본 변수는 API를 통해 설정되지 않고 OSGi 속성 자체에서 설정됩니다.

자세한 내용은 [이 페이지](https://www.adobe.io/apis/experiencecloud/cloud-manager/api-reference.html#/Environment_Variables/patchEnvironmentVariables)를 참조하십시오.

### API {#getting-values-via-api}를 통해 값 가져오기

```
GET /program/{programId}/environment/{environmentId}/variables
```

자세한 내용은 [이 페이지](https://www.adobe.io/apis/experiencecloud/cloud-manager/api-reference.html#/Environment_Variables/getEnvironmentVariables)를 참조하십시오.

### API {#deleting-values-via-api}를 통해 값 삭제

```
PATCH /program/{programId}/environment/{environmentId}/variables
```

변수를 삭제하려면 빈 값과 함께 포함하십시오.

자세한 내용은 [이 페이지](https://www.adobe.io/apis/experiencecloud/cloud-manager/api-reference.html#/Environment_Variables/patchEnvironmentVariables)를 참조하십시오.

### 명령줄 {#getting-values-via-cli}을(를) 통해 값 가져오기

```bash
$ aio cloudmanager:list-environment-variables ENVIRONMENT_ID
Name     Type         Value
MY_VAR1  string       plaintext value 
MY_VAR2  secretString ****
```


### 명령줄 {#setting-values-via-cli}을 통해 값 설정

```bash
$ aio cloudmanager:set-environment-variables ENVIRONMENT_ID --variable MY_VAR1 "plaintext value" --secret MY_VAR2 "some secret value"
```

### 명령줄 {#deleting-values-via-cli}을(를) 통해 값 삭제

```bash
$ aio cloudmanager:set-environment-variables ENVIRONMENT_ID --delete MY_VAR1 MY_VAR2
```

>[!NOTE]
>
>Adobe I/O CLI용 클라우드 관리자 플러그인을 사용하여 값을 구성하는 방법에 대한 자세한 내용은 [이 페이지](https://github.com/adobe/aio-cli-plugin-cloudmanager#aio-cloudmanagerset-environment-variables-environmentid)를 참조하십시오.

### 변수 수 {#number-of-variables}

환경당 최대 200개의 변수를 선언할 수 있습니다.

## 보안 및 환경별 구성 값에 대한 배포 고려 사항 {#deployment-considerations-for-secret-and-environment-specific-configuration-values}

보안 및 환경별 구성 값은 Git 외부에 있으므로 Cloud Service 배포 메커니즘으로서 정식 AEM에 속하지 않으므로 Cloud Service 배포 과정에서 고객은 AEM을 관리 및 제어하고 배포 프로세스로 통합해야 합니다.

위에 언급했듯이 API를 호출하면 일반적인 고객 코드 배포 파이프라인과 유사한 새로운 변수와 값이 클라우드 환경에 배포됩니다. 작성자 및 게시 서비스가 다시 시작되고 새 값을 참조하며 일반적으로 몇 분 정도 걸립니다. 일반적인 코드 배포 중 Cloud Manager에서 실행하는 품질 게이트와 테스트는 이 프로세스 동안 수행되지 않습니다.

일반적으로 고객은 Cloud Manager에서 해당 변수에 의존하는 코드를 배포하기 전에 API를 호출하여 환경 변수를 설정합니다. 코드가 이미 배포된 후 기존 변수를 수정할 수도 있습니다.

파이프라인이 사용 중인 경우, AEM 업데이트나 고객 배포 중 어느 쪽 끝 파이프라인이 현재 실행되고 있는지에 따라 API가 성공할 수 없습니다. 이 오류 응답에는 요청이 성공을 거두지 못했으나 구체적인 이유가 나타나지 않습니다.

예약된 고객 코드 배포가 기존 변수에 의존하여 현재 코드에 맞지 않는 새 값을 갖는 시나리오가 있을 수 있습니다. 이러한 문제가 발생하는 경우 부가적인 방식으로 변수를 수정하는 것이 좋습니다. 이렇게 하려면 이전 코드가 새 값을 참조하지 않도록 이전 변수의 값만 변경하는 대신 새 변수 이름을 만드십시오. 그런 다음 새 고객 릴리스가 안정적일 때 이전 값을 제거하도록 선택할 수 있습니다.

마찬가지로 변수 값의 버전이 관리되지 않으므로 코드를 롤백하면 문제를 일으키는 새 값을 참조할 수 있습니다. 앞서 언급한 추가 변수 전략도 여기에 도움이 될 것입니다.

이 추가 변수 전략은 재배포하기 며칠 전의 코드가 필요한 경우, 변수 이름과 참조하는 값이 그대로 유지되는 재해 복구 시나리오에 유용합니다. 이것은 고객이 이러한 이전 변수를 제거하기 전에 며칠 동안 대기하는 전략에 의존하며, 그렇지 않은 경우 이전 코드에 참조할 적절한 변수가 없을 수 있습니다.
