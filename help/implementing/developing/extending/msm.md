---
title: 다중 사이트 관리자 확장
description: 다중 사이트 관리자의 기능을 확장하는 방법을 알아봅니다.
source-git-commit: f159f0ef86c2b82da4e7308a0892b4947b6e43fb
workflow-type: tm+mt
source-wordcount: '2436'
ht-degree: 1%

---


# 다중 사이트 관리자 확장 {#extending-the-multi-site-manager}

이 문서는 다중 사이트 관리자의 기능을 확장하는 방법을 이해하는 데 도움이 되며 다음 항목을 다룹니다.

* MSM Java API의 주요 멤버에 대해 알아봅니다
* 롤아웃 구성에서 사용할 수 있는 새 동기화 작업 만들기
* 기본 언어 및 국가 코드 수정

>[!TIP]
>
>이 페이지는 문서의 맥락에서 보다 쉽게 이해할 수 있습니다 [콘텐츠 재사용: 다중 사이트 관리자.](/help/sites-cloud/administering/msm/overview.md)

>[!CAUTION]
>
>다중 사이트 관리자 및 해당 API는 웹 사이트를 작성할 때 사용되며 작성 환경에서만 사용됩니다.

## Java API 개요 {#overview-of-the-java-api}

다중 사이트 관리는 다음 패키지로 구성됩니다.

* [com.day.cq.wcm.msm.api](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/day/cq/wcm/msm/api/package-frame.html)
* [com.day.cq.wcm.msm.commons](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/day/cq/wcm/msm/commons/package-frame.html)

기본 MSM API 개체는 다음과 같이 상호 작용합니다( 섹션 참조) [사용된 용어](/help/sites-cloud/administering/msm/overview.md#terms-used)):

![기본 MSM API 개체](assets/msm-api-interaction.png)

* **`Blueprint`** - A `Blueprint` (에서와 같이) [블루프린트 구성](/help/sites-cloud/administering/msm/overview.md#source-blueprints-and-blueprint-configurations)) live copy가 콘텐츠를 상속할 수 있는 페이지를 지정합니다.

  ![블루프린트](assets/msm-blueprint-interaction.png)

   * 블루프린트 구성 사용( `Blueprint`)는 선택 사항이지만,

      * 이를 통해 작성자는 **롤아웃** 이 소스에서 상속되는 라이브 카피에 수정 사항을 명시적으로 푸시하기 위한 소스의 옵션입니다.
      * 이를 통해 작성자는 **사이트 생성**: 사용자가 손쉽게 언어를 선택하고 라이브 카피 구조를 구성할 수 있습니다.
      * 결과 라이브 카피에 대한 기본 롤아웃 구성을 정의합니다.

* **`LiveRelationship`** - `LiveRelationship` 라이브 카피 분기에 있는 리소스와 이에 상응하는 소스/블루프린트 리소스 간의 연결(관계)을 지정합니다.

   * 관계는 상속 및 롤아웃을 실현할 때 사용됩니다.
   * `LiveRelationship` 개체는 롤아웃 구성에 대한 액세스(참조)를 제공합니다. ( `RolloutConfig`), `LiveCopy`, 및 `LiveStatus` 관계와 관련된 개체입니다.

   * 예를 들어 라이브 카피는에 생성됩니다. `/content/copy/us` 의 소스/블루프린트에서 `/content/wknd/language-masters`. 리소스 `/content/wknd/language-masters/en/jcr:content` 및 `/content/copy/us/en/jcr:content` 관계를 형성합니다.

* **`LiveCopy`** - A `LiveCopy` 관계에 대한 구성 세부 정보를 보유합니다(`LiveRelationship`) 라이브 카피 리소스와 소스/블루프린트 리소스 간의 매핑에 사용됩니다.

   * 사용 `LiveCopy` 클래스의 하위 페이지 포함 여부, 소스/블루프린트 페이지 경로, 롤아웃 구성 등을 확인할 수 있습니다. `LiveCopy`.

   * A `LiveCopy` 노드는 매번 만들어짐 **사이트 생성** 또는 **Live Copy 만들기** 를 사용합니다.

* **`LiveStatus`** - `LiveStatus` 개체는 의 런타임 상태에 대한 액세스를 제공합니다. `LiveRelationship`. 라이브 카피의 동기화 상태를 쿼리하는 데 사용합니다.

* **`LiveAction`** - A `LiveAction` 은 롤아웃과 관련된 각 리소스에서 실행되는 작업입니다.

   * `LiveAction`s은(는) 다음 대상으로만 생성됩니다. `RolloutConfig`s.

* **`LiveActionFactory`** - A `LiveActionFactory` 생성 `LiveAction` 지정된 오브젝트 `LiveAction` 구성. 구성은 저장소의 리소스로 저장됩니다.

* **`RolloutConfig`** - `RolloutConfig` 목록 보관 `LiveActions`: 트리거될 때 사용됩니다. 다음 `LiveCopy` 을 상속합니다. `RolloutConfig` 결과가 다음에 있습니다. `LiveRelationship`.

   * 처음 Live Copy를 설정하는 경우에도 `RolloutConfig` (다음을 트리거함: `LiveAction`s).

## 새 동기화 작업 만들기 {#creating-a-new-synchronization-action}

롤아웃 구성에 사용할 사용자 지정 동기화 작업을 만들 수 있습니다. 이 기능은 다음과 같은 경우에 유용합니다. [설치된 작업](/help/sites-cloud/administering/msm/live-copy-sync-config.md#installed-synchronization-actions) 특정 애플리케이션 요구 사항을 충족하지 않습니다.

이렇게 하려면 두 개의 클래스를 만듭니다.

* 의 구현 [`com.day.cq.wcm.msm.api.LiveAction`](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/day/cq/wcm/msm/api/LiveAction.html) 작업을 수행하는 인터페이스입니다.
* 를 구현하는 OSGi 구성 요소 [`com.day.cq.wcm.msm.api.LiveActionFactory`](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/day/cq/wcm/msm/api/LiveActionFactory.html) 인터페이스 및 의 인스턴스 만들기 `LiveAction` 클래스

다음 `LiveActionFactory` 의 인스턴스를 생성합니다. `LiveAction` 지정된 구성에 대한 클래스:

* `LiveAction` 클래스에는 다음 메서드가 포함됩니다.

   * `getName` - 작업의 이름을 반환합니다.

      * 이 이름은 작업을 참조하는 데 사용됩니다(예: 롤아웃 구성).

   * `execute` - 작업 수행

* `LiveActionFactory` 클래스에는 다음 멤버가 포함됩니다.

   * `LIVE_ACTION_NAME` - 연결된 이름이 포함된 필드 `LiveAction`

      * 이 이름은 가 반환하는 값과 일치해야 합니다. `getName` 방법 `LiveAction` 클래스.

   * `createAction` - 의 인스턴스를 만듭니다. `LiveAction`

      * 선택 사항 `Resource` 매개 변수를 사용하여 구성 정보를 제공할 수 있습니다.

   * `createsAction` - 연결된 이름을 반환합니다. `LiveAction`

### LiveAction 구성 노드 액세스 {#accessing-the-liveaction-configuration-node}

사용 `LiveAction` 런타임 동작에 영향을 주는 정보를 저장할 저장소의 구성 노드 `LiveAction` 인스턴스. 를 저장하는 저장소의 노드 `LiveAction` 구성은 다음에서 사용할 수 있습니다. `LiveActionFactory` 런타임 시 개체. 따라서 구성 노드에 속성을 추가하고 `LiveActionFactory` 필요에 따라 구현합니다.

예: `LiveAction` 블루프린트 작성자의 이름을 저장해야 합니다. 구성 노드의 속성에는 정보를 저장하는 블루프린트 페이지의 속성 이름이 포함됩니다. 런타임 시 `LiveAction` 구성에서 속성 이름을 검색한 다음 속성 값을 얻습니다.

의 매개 변수 [`LiveActionFactory.createAction`](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/day/cq/wcm/msm/api/LiveActionFactory.html) 메서드는 입니다. `Resource` 개체. 이 `Resource` 개체는 다음을 나타냅니다. `cq:LiveSyncAction` 롤아웃 구성에서 이 라이브 작업에 대한 노드입니다.

문서를 참조하십시오. [롤아웃 구성 만들기](/help/sites-cloud/administering/msm/live-copy-sync-config.md#creating-a-rollout-configuration) 추가 정보.

구성 노드를 사용할 때처럼 로 조정해야 합니다 `ValueMap` 개체:

```java
public LiveAction createAction(Resource resource) throws WCMException {
        ValueMap config;
        if (resource == null || resource.adaptTo(ValueMap.class) == null) {
            config = new ValueMapDecorator(Collections.<String, Object>emptyMap());
        } else {
            config = resource.adaptTo(ValueMap.class);
        }
        return new MyLiveAction(config, this);
}
```

### Target 노드, 소스 노드 및 LiveRelationship 액세스 {#accessing-target-nodes-source-nodes-and-the-liverelationship}

다음 개체는 의 매개 변수로 제공됩니다. `execute` 방법 `LiveAction` 개체:

* A [`Resource`](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/org/apache/sling/api/resource/Resource.html) 라이브 카피의 소스를 나타내는 개체
* A `Resource` 라이브 카피의 대상을 나타내는 개체입니다.
* 다음 [`LiveRelationship`](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/wcm/msm/api/LiveRelationship.html) 라이브 카피용 개체
   * 다음 `autoSave` 값은 다음 여부를 나타냅니다. `LiveAction` 저장소에 변경 사항을 저장해야 함
   * 다음 `reset` 값은 롤아웃 재설정 모드를 나타냅니다.

이러한 오브젝트에서 다음에 대한 모든 정보를 가져올 수 있습니다. `LiveCopy`. 다음을 사용할 수도 있습니다 `Resource` 가져올 오브젝트 `ResourceResolver`, `Session`, 및 `Node` 개체. 이러한 객체는 리포지토리 컨텐츠를 조작하는 데 유용합니다.

다음 코드의 첫 번째 행에서 source 는 `Resource` 소스 페이지의 개체:

```java
ResourceResolver resolver = source.getResourceResolver();
Session session = resolver.adaptTo(javax.jcr.Session.class);
Node sourcenode = source.adaptTo(javax.jcr.Node.class);
```

>[!NOTE]
>
>다음 `Resource` 인수는 다음과 같습니다. `null` 또는 `Resources` 에 적응하지 않는 오브젝트 `Node` 오브젝트(예: ) [`NonExistingResource`](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/org/apache/sling/api/resource/NonExistingResource.html) 개체.

## 새 롤아웃 구성 만들기 {#creating-a-new-rollout-configuration}

설치된 롤아웃 구성이 애플리케이션 요구 사항을 충족하지 않는 경우 롤아웃 구성을 생성할 수 있는 두 단계는 다음과 같습니다.

* [롤아웃 구성 만들기](#create-the-rollout-configuration)
* [롤아웃 구성에 동기화 작업 추가](#add-synchronization-actions-to-the-rollout-configuration)

블루프린트 또는 라이브 카피 페이지에서 롤아웃 구성을 설정할 때 새 롤아웃 구성을 사용할 수 있습니다.

>[!TIP]
>
>다음 항목도 참조하십시오. [롤아웃 사용자 지정 우수 사례](/help/sites-cloud/administering/msm/best-practices.md#customizing-rollouts).

### 롤아웃 구성 만들기 {#create-the-rollout-configuration}

새 롤아웃 구성을 만들려면 다음 작업을 수행하십시오.

1. 다음 위치에서 CRXDE Lite 열기 `https://<host>:<port>/crx/de`.

1. 다음으로 이동 `/apps/msm/<your-project>/rolloutconfigs`, 프로젝트의 사용자 지정된 버전 `/libs/msm/wcm/rolloutconfigs`.

   * 첫 번째 구성인 경우 `/libs` 새 분기를 만들려면 분기를 템플릿으로 사용해야 합니다. `/apps`.

1. 이 위치 아래에 다음 속성을 사용하여 노드를 만듭니다.

   * **이름**: 롤아웃 구성의 노드 이름(예: ) `contentCopy` 또는 `workflow`
   * **유형**: `cq:RolloutConfig`

1. 이 노드에 다음 속성을 추가합니다.

   * **이름**: `jcr:title`
     **유형**: `String`
     **값**: UI에 표시되는 식별 제목

   * **이름**: `jcr:description`
     **유형**: `String`
     **값**: 선택적 설명입니다.

   * **이름**: `cq:trigger`
     **유형**: `String`
     **값**: [롤아웃 트리거](/help/sites-cloud/administering/msm/live-copy-sync-config.md#rollout-triggers) 사용 예정
      * `rollout`
      * `modification`
      * `publish`
      * `deactivate`

1. 클릭 **모두 저장**.

### 롤아웃 구성에 동기화 작업 추가 {#add-synchronization-actions-to-the-rollout-configuration}

롤아웃 구성은 아래에 저장됩니다. [롤아웃 구성 노드](#create-the-rollout-configuration) 을(를) 생성했습니다. `/apps/msm/<your-project>/rolloutconfigs` 노드.

유형의 하위 노드 추가 `cq:LiveSyncAction` 을 클릭하여 롤아웃 구성에 동기화 작업을 추가합니다. 동기화 작업 노드의 순서는 작업이 발생하는 순서를 결정합니다.

1. CRXDE Lite에서 [롤아웃 구성](#create-the-rollout-configuration) 노드(예: `/apps/msm/myproject/rolloutconfigs/myrolloutconfig`.

1. 다음 노드 속성을 사용하여 노드를 만듭니다.

   * **이름**: 동기화 작업의 노드 이름
      * 이름은 과(와) 같아야 합니다. **작업 이름** 아래 표에서 [동기화 작업](/help/sites-cloud/administering/msm/live-copy-sync-config.md#installed-synchronization-actions) 과 같은 `contentCopy` 또는 `workflow`.
   * **유형**: `cq:LiveSyncAction`

1. 필요한 만큼 동기화 작업 노드를 추가하고 구성합니다.

1. 작업 노드의 순서를 원하는 순서와 일치하도록 작업 노드를 재배열합니다.
   * 맨 위 작업 노드가 먼저 발생합니다.

## 간단한 LiveActionFactory 클래스 만들기 및 사용 {#creating-and-using-a-simple-liveactionfactory-class}

이 섹션의 절차를 따라 다음을 개발하십시오. `LiveActionFactory` 롤아웃 구성에서 사용합니다. 이 절차에서는 Maven 및 Eclipse를 사용하여 `LiveActionFactory`:

1. [Maven 프로젝트 만들기](#create-the-maven-project) Eclipse로 가져옵니다.
1. [종속성 추가](#add-dependencies-to-the-pom-file) POM 파일로 이동합니다.
1. [구현 `LiveActionFactory` 인터페이스](#implement-liveactionfactory) 및 를 배포합니다.
1. [롤아웃 구성 만들기](#create-the-example-rollout-configuration).
1. [라이브 카피 만들기](#create-the-live-copy).

[Maven 프로젝트 및 Java 클래스의 소스 코드](https://github.com/Adobe-Marketing-Cloud/experiencemanager-java-msmrollout) 는 공개 Git 저장소에서 사용할 수 있습니다.

### Maven 프로젝트 만들기 {#create-the-maven-project}

다음 절차를 수행하려면 를 추가해야 합니다. `adobe-public` Maven 설정 파일에 대한 프로필

* adobe-public 프로필에 대한 자세한 내용은 [콘텐츠 패키지 Maven 플러그인 가져오기](/help/implementing/developing/tools/maven-plugin.md#obtaining-the-content-package-maven-plugin)
* Maven 설정 파일에 대한 자세한 내용은 Maven 을 참조하십시오 [설정 참조](https://maven.apache.org/settings.html).

1. 터미널 또는 명령줄 세션을 열고 프로젝트를 만들 위치를 가리키도록 디렉터리를 변경합니다.
1. 다음 명령을 입력합니다.

   ```text
   mvn archetype:generate -DarchetypeGroupId=com.day.jcr.vault -DarchetypeArtifactId=multimodule-content-package-archetype -DarchetypeVersion=1.0.0 -DarchetypeRepository=adobe-public-releases
   ```

1. 대화형 프롬프트에서 다음 값을 지정하십시오.

   * **`groupId`**: `com.adobe.example.msm`
   * **`artifactId`**: `MyLiveActionFactory`
   * **`version`**: `1.0-SNAPSHOT`
   * **`package`**: `MyPackage`
   * **`appsFolderName`**: `myapp`
   * **`artifactName`**: `MyLiveActionFactory package`
   * **`packageGroup`**: `myPackages`

1. Eclipse 시작 및 [Maven 프로젝트를 가져옵니다.](/help/implementing/developing/tools/eclipse.md#import-the-maven-project-into-eclipse)

### POM 파일에 종속성 추가 {#add-dependencies-to-the-pom-file}

Eclipse 컴파일러에서 `LiveActionFactory` 코드.

1. Eclipse 프로젝트 탐색기에서 파일을 엽니다 `MyLiveActionFactory/pom.xml`.

1. 편집기에서 `pom.xml` 탭을 클릭하고 `project/dependencyManagement/dependencies` 섹션.

1. 다음 XML을 `dependencyManagement` 요소를 입력한 다음 파일을 저장합니다.

   ```xml
    <dependency>
     <groupId>com.day.cq.wcm</groupId>
     <artifactId>cq-msm-api</artifactId>
     <version>5.6.2</version>
     <scope>provided</scope>
    </dependency>
    <dependency>
     <groupId>org.apache.sling</groupId>
     <artifactId>org.apache.sling.api</artifactId>
     <version>2.4.3-R1488084</version>
     <scope>provided</scope>
    </dependency>
    <dependency>
     <groupId>com.day.cq.wcm</groupId>
     <artifactId>cq-wcm-api</artifactId>
     <version>5.6.6</version>
     <scope>provided</scope>
    </dependency>
    <dependency>
     <groupId>org.apache.sling</groupId>
     <artifactId>org.apache.sling.commons.json</artifactId>
     <version>2.0.6</version>
     <scope>provided</scope>
    </dependency>
    <dependency>
     <groupId>com.day.cq</groupId>
     <artifactId>cq-commons</artifactId>
     <version>5.6.4</version>
     <scope>provided</scope>
    </dependency>
    <dependency>
     <groupId>org.apache.sling</groupId>
     <artifactId>org.apache.sling.jcr.jcr-wrapper</artifactId>
     <version>2.0.0</version>
     <scope>provided</scope>
    </dependency>
    <dependency>
     <groupId>com.day.cq</groupId>
     <artifactId>cq-commons</artifactId>
     <version>5.6.4</version>
     <scope>provided</scope>
    </dependency>
   ```

1. 에서 번들에 대한 POM 파일을 엽니다. **프로젝트 탐색기** 위치: `MyLiveActionFactory-bundle/pom.xml`.

1. 편집기에서 `pom.xml` 을 탭하고 프로젝트/종속성 섹션을 찾습니다. dependencies 요소 내에 다음 XML을 추가한 다음 파일을 저장합니다.

   ```xml
    <dependency>
     <groupId>com.day.cq.wcm</groupId>
     <artifactId>cq-msm-api</artifactId>
    </dependency>
    <dependency>
     <groupId>org.apache.sling</groupId>
     <artifactId>org.apache.sling.api</artifactId>
    </dependency>
    <dependency>
     <groupId>com.day.cq.wcm</groupId>
     <artifactId>cq-wcm-api</artifactId>
    </dependency>
    <dependency>
     <groupId>org.apache.sling</groupId>
     <artifactId>org.apache.sling.commons.json</artifactId>
    </dependency>
    <dependency>
     <groupId>com.day.cq</groupId>
     <artifactId>cq-commons</artifactId>
    </dependency>
    <dependency>
     <groupId>org.apache.sling</groupId>
     <artifactId>org.apache.sling.jcr.jcr-wrapper</artifactId>
    </dependency>
    <dependency>
     <groupId>com.day.cq</groupId>
     <artifactId>cq-commons</artifactId>
    </dependency>
   ```

### LiveActionFactory 구현 {#implement-liveactionfactory}

다음 `LiveActionFactory` 클래스는 `LiveAction` 소스 및 타겟 페이지에 대한 메시지를 기록하고 `cq:lastModifiedBy` 소스 노드에서 대상 노드로의 속성. 라이브 작업의 이름은 입니다. `exampleLiveAction`.

1. Eclipse 프로젝트 탐색기에서 `MyLiveActionFactory-bundle/src/main/java/com.adobe.example.msm` 패키지 및 클릭 **신규** -> **클래스**.

1. 의 경우 **이름**, 입력 `ExampleLiveActionFactory` 그런 다음 을 클릭합니다. **완료**.

1. 를 엽니다. `ExampleLiveActionFactory.java` 파일, 내용을 다음 코드로 바꾸고 파일을 저장합니다.

   ```java
   package com.adobe.example.msm;
   
   import java.util.Collections;
   
   import org.apache.felix.scr.annotations.Component;
   import org.apache.felix.scr.annotations.Property;
   import org.apache.felix.scr.annotations.Service;
   import org.apache.sling.api.resource.Resource;
   import org.apache.sling.api.resource.ResourceResolver;
   import org.apache.sling.api.resource.ValueMap;
   import org.apache.sling.api.wrappers.ValueMapDecorator;
   import org.apache.sling.commons.json.io.JSONWriter;
   import org.apache.sling.commons.json.JSONException;
   
   import org.slf4j.Logger;
   import org.slf4j.LoggerFactory;
   
   import javax.jcr.Node;
   import javax.jcr.RepositoryException;
   import javax.jcr.Session;
   
   import com.day.cq.wcm.msm.api.ActionConfig;
   import com.day.cq.wcm.msm.api.LiveAction;
   import com.day.cq.wcm.msm.api.LiveActionFactory;
   import com.day.cq.wcm.msm.api.LiveRelationship;
   import com.day.cq.wcm.api.WCMException;
   
   @Component(metatype = false)
   @Service
   public class ExampleLiveActionFactory implements LiveActionFactory<LiveAction> {
    @Property(value="exampleLiveAction")
    static final String actionname = LiveActionFactory.LIVE_ACTION_NAME;
   
    public LiveAction createAction(Resource config) {
     ValueMap configs;
     /* Adapt the config resource to a ValueMap */
           if (config == null || config.adaptTo(ValueMap.class) == null) {
               configs = new ValueMapDecorator(Collections.<String, Object>emptyMap());
           } else {
               configs = config.adaptTo(ValueMap.class);
           }
   
     return new ExampleLiveAction(actionname, configs);
    }
    public String createsAction() {
     return actionname;
    }
    /************* LiveAction ****************/
    private static class ExampleLiveAction implements LiveAction {
     private String name;
     private ValueMap configs;
     private static final Logger log = LoggerFactory.getLogger(ExampleLiveAction.class);
   
     public ExampleLiveAction(String nm, ValueMap config){
      name = nm;
      configs = config;
     }
   
     public void execute(Resource source, Resource target,
       LiveRelationship liverel, boolean autoSave, boolean isResetRollout)
         throws WCMException {
   
      String lastMod = null;
   
      log.info(" *** Executing ExampleLiveAction *** ");
   
      /* Determine if the LiveAction is configured to copy the cq:lastModifiedBy property */
      if ((Boolean) configs.get("repLastModBy")){
   
       /* get the source's cq:lastModifiedBy property */
       if (source != null && source.adaptTo(Node.class) !=  null){
        ValueMap sourcevm = source.adaptTo(ValueMap.class);
        lastMod = sourcevm.get(com.day.cq.wcm.msm.api.MSMNameConstants.PN_PAGE_LAST_MOD_BY, String.class);
       }
   
       /* set the target node's la-lastModifiedBy property */
       Session session = null;
       if (target != null && target.adaptTo(Node.class) !=  null){
        ResourceResolver resolver = target.getResourceResolver();
        session = resolver.adaptTo(javax.jcr.Session.class);
        Node targetNode;
        try{
         targetNode=target.adaptTo(javax.jcr.Node.class);
         targetNode.setProperty("la-lastModifiedBy", lastMod);
         log.info(" *** Target node lastModifiedBy property updated: {} ***",lastMod);
        }catch(Exception e){
         log.error(e.getMessage());
        }
       }
       if(autoSave){
        try {
         session.save();
        } catch (Exception e) {
         try {
          session.refresh(true);
         } catch (RepositoryException e1) {
          e1.printStackTrace();
         }
         e.printStackTrace();
        }
       }
      }
     }
     public String getName() {
      return name;
     }
   
     /************* Deprecated *************/
     @Deprecated
     public void execute(ResourceResolver arg0, LiveRelationship arg1,
       ActionConfig arg2, boolean arg3) throws WCMException {
     }
     @Deprecated
     public void execute(ResourceResolver arg0, LiveRelationship arg1,
       ActionConfig arg2, boolean arg3, boolean arg4)
         throws WCMException {
     }
     @Deprecated
     public String getParameterName() {
      return null;
     }
     @Deprecated
     public String[] getPropertiesNames() {
      return null;
     }
     @Deprecated
     public int getRank() {
      return 0;
     }
     @Deprecated
     public String getTitle() {
      return null;
     }
     @Deprecated
     public void write(JSONWriter arg0) throws JSONException {
     }
    }
   }
   ```

1. 터미널 또는 명령 세션을 사용하여 디렉터리를 `MyLiveActionFactory` 디렉터리(Maven 프로젝트 디렉터리). 그런 다음 다음 다음 명령을 입력합니다.

   ```shell
   mvn -PautoInstallPackage clean install
   ```

1. 더 AEM `error.log` 파일은 번들이 시작되었음을 나타내야 하며, 다음 위치의 로그에 표시됩니다. `https://<host>:<port>/system/console/status-slinglogs`.

   ```text
   13.08.2013 14:34:55.450 *INFO* [OsgiInstallerImpl] com.adobe.example.msm.MyLiveActionFactory-bundle BundleEvent RESOLVED
   13.08.2013 14:34:55.451 *INFO* [OsgiInstallerImpl] com.adobe.example.msm.MyLiveActionFactory-bundle BundleEvent STARTING
   13.08.2013 14:34:55.451 *INFO* [OsgiInstallerImpl] com.adobe.example.msm.MyLiveActionFactory-bundle BundleEvent STARTED
   13.08.2013 14:34:55.453 *INFO* [OsgiInstallerImpl] com.adobe.example.msm.MyLiveActionFactory-bundle Service [com.adobe.example.msm.ExampleLiveActionFactory,2188] ServiceEvent REGISTERED
   13.08.2013 14:34:55.454 *INFO* [OsgiInstallerImpl] org.apache.sling.audit.osgi.installer Started bundle com.adobe.example.msm.MyLiveActionFactory-bundle [316]
   ```

### 예제 롤아웃 구성 만들기 {#create-the-example-rollout-configuration}

다음을 사용하는 MSM 롤아웃 구성 만들기 `LiveActionFactory` 생성한 항목:

1. 만들기 및 구성 [표준 절차를 사용한 롤아웃 구성](/help/sites-cloud/administering/msm/live-copy-sync-config.md#creating-a-rollout-configuration) 속성 사용:

   * **제목**: 롤아웃 구성 예
   * **이름**: examplerlolloutconfig
   * **cq:trigger**: `publish`

### 예제 롤아웃 구성에 라이브 작업 추가 {#add-the-live-action-to-the-example-rollout-configuration}

이전 절차에서 만든 롤아웃 구성을 구성하여 `ExampleLiveActionFactory` 클래스.

1. CRXDE Lite 열기.

1. 아래에 다음 노드를 만듭니다. `/apps/msm/rolloutconfigs/examplerolloutconfig/jcr:content`:

   * **이름**: `exampleLiveAction`
   * **유형**: `cq:LiveSyncAction`

1. 클릭 **모두 저장**.

1. 다음 항목 선택 `exampleLiveAction` 노드 및에 표시할 속성 추가 `ExampleLiveAction` 클래스 `cq:LastModifiedBy` 속성은 소스에서 대상 노드로 복제되어야 합니다.

   * **이름**: `repLastModBy`
   * **유형**: `Boolean`
   * **값**: `true`

1. 클릭 **모두 저장**.

### 라이브 카피 만들기 {#create-the-live-copy}

[라이브 카피 만들기](/help/sites-cloud/administering/msm/creating-live-copies.md#creating-a-live-copy-of-a-page) 롤아웃 구성을 사용하는 WKND 참조 사이트의 영어/제품 분기:

* **소스**: `/content/wknd/language-masters/en/products`

* **롤아웃 구성**: 롤아웃 구성 예

활성화 **제품** (영어) 소스 분기 페이지를 참조하고 `LiveAction` 클래스는 다음을 생성합니다.

```xml
16.08.2013 10:53:33.055 *INFO* [Thread-444535] com.adobe.example.msm.ExampleLiveActionFactory$ExampleLiveAction  ***ExampleLiveAction has been executed.***
16.08.2013 10:53:33.055 *INFO* [Thread-444535] com.adobe.example.msm.ExampleLiveActionFactory$ExampleLiveAction  ***Target node lastModifiedBy property updated: admin ***
```

## 언어 이름 및 기본 국가 변경 {#changing-language-names-and-default-countries}

AEM에서는 기본 언어 및 국가 코드 세트를 사용합니다.

* 기본 언어 코드는 ISO-639-1에서 정의된 소문자 두 자리 코드입니다.
* 기본 국가 코드는 ISO 3166에서 정의된 소문자 또는 대문자 두 자리 코드입니다.

MSM은 저장된 언어 및 국가 코드 목록을 사용하여 페이지의 언어 버전 이름과 연관된 국가의 이름을 결정합니다. 필요한 경우 목록의 다음 측면을 변경할 수 있습니다.

* 언어 제목
* 국가 이름
* 언어의 기본 국가(예: 코드) `en`, `de`, 기타)

언어 목록은 `/libs/wcm/core/resources/languages` 노드. 각 하위 노드는 언어 또는 언어 국가를 나타냅니다.

* 노드의 이름은 언어 코드입니다(예: `en` 또는 `de`) 또는 language_country 코드(예: `en_us` 또는 `de_ch`).

* 다음 `language` 노드의 속성은 코드에 대한 언어의 전체 이름을 저장합니다.
* 다음 `country` 노드의 속성은 코드에 대한 국가의 전체 이름을 저장합니다.
* 노드 이름이 언어 코드로만 구성된 경우(예: `en`), 국가 속성은 다음과 같습니다 `*`및 추가 `defaultCountry` 속성은 사용할 국가를 나타내는 언어 국가의 코드를 저장합니다.

![언어 정의](assets/msm-language-manager.png)

언어를 수정하려면 다음을 수행합니다.

1. CRXDE Lite 열기.
1. 다음 항목 선택 `/apps` 폴더 및 클릭 **만들기**, 그런 다음 **폴더를 만듭니다.**

1. 새 폴더 이름 지정 `wcm`.

1. 이전 단계를 반복하여 `/apps/wcm/core` 폴더 트리. 유형의 노드 만들기 `sling:Folder` 위치: `core` 호출됨 `resources`.

1. 마우스 오른쪽 단추 클릭 `/libs/wcm/core/resources/languages` 노드 및 클릭 **복사**.
1. 마우스 오른쪽 단추 클릭 `/apps/wcm/core/resources` 폴더 및 클릭 **붙여넣기**. 필요에 따라 하위 노드를 수정합니다.
1. 클릭 **모두 저장**.
1. 클릭 **도구**, **작업** 그러면 **웹 콘솔**. 이 콘솔에서 **OSGi**, 그런 다음 **구성**.
1. 를 찾아 클릭합니다. **일별 CQ WCM 언어 관리자**, 값 변경 **언어 목록** 끝 `/apps/wcm/core/resources/languages`을 클릭한 다음 을 클릭합니다 **저장**.

   ![일별 CQ WCM 언어 관리자](assets/msm-language-manager.png)

## 페이지 속성에서 MSM 잠금 구성 {#configuring-msm-locks-on-page-properties}

사용자 지정 페이지 속성을 만들 때 새 속성을 라이브 카피에 롤아웃할 수 있는지 여부를 고려해야 할 수 있습니다.

예를 들어 두 개의 새 페이지 속성이 추가되는 경우:

* 연락처 이메일:

   * 이 속성은 각 국가(또는 브랜드 등)에서 다르므로 롤아웃할 필요가 없습니다.

* 주요 비주얼 스타일:

   * 프로젝트 요구 사항은 이 속성이 모든 국가 (또는 브랜드 등)에 (일반적으로) 공통된 상태로 롤아웃되어야 한다는 것입니다.

그런 다음 다음을 확인해야 합니다.

* 연락처 이메일:

   * 롤아웃된 속성에서 제외됩니다.
   * 문서를 참조하십시오. [라이브 카피 동기화 구성](/help/sites-cloud/administering/msm/live-copy-sync-config.md#excluding-properties-and-node-types-from-synchronization) 추가 정보.

* 주요 비주얼 스타일:

   * 상속이 취소되지 않는 한 이 속성을 편집할 수 없도록 하십시오.
   * 또한 상속을 복원할 수 있는지 확인합니다. 이는 연결의 상태를 나타내도록 전환하는 체인/끊어진 체인 링크를 클릭하여 제어합니다.

페이지 속성이 롤아웃의 대상인지, 따라서 편집할 때 상속을 취소/복원할 대상인지 여부는 대화 상자 속성에 의해 제어됩니다.

* `cq-msm-lockable`

   * 이렇게 하면 대화 상자에 체인 링크 기호가 만들어집니다.
   * 상속이 취소(체인 연결이 끊어진 경우)된 경우에만 편집할 수 있습니다.
   * 이는 리소스의 첫 번째 하위 수준에만 적용됩니다
      * **유형**: `String`
      * **값**: 고려 중인 재산의 이름을 보유하고 있으며 재산 가치와 비슷합니다 `name`
         * 예를 들어 다음을 참조하십시오.
           `/libs/foundation/components/page/cq:dialog/content/items/tabs/items/basic/items/column/items/title/items/title`

날짜 `cq-msm-lockable` 가 정의되었으므로 체인을 끊거나 닫는 것은 다음과 같은 방식으로 MSM과 상호 작용합니다.

* 다음 값: `cq-msm-lockable` 은(는)

   * **상대** (예: `myProperty` 또는 `./myProperty`)

      * 체인을 끊으면 속성이 추가 및 제거됩니다. `cq:propertyInheritanceCancelled`.

   * **절대** (예: `/image`)

      * 체인을 끊으면 상속을 취소하고 `cq:LiveSyncCancelled` mixin 대상 `./image` 및 설정 `cq:isCancelledForChildren` 끝 `true`.

      * 체인을 닫으면 상속이 취소됩니다.

>[!NOTE]
>
>`cq-msm-lockable` 편집할 리소스의 첫 번째 하위 수준에 적용되며, 값이 절대 또는 상대로 정의되었는지 여부에 관계없이 더 깊은 상위 항목에서 작동하지 않습니다.

>[!NOTE]
>
>상속을 다시 활성화하면 라이브 카피 페이지 속성이 소스 속성과 자동으로 동기화되지 않습니다. 필요한 경우 수동으로 동기화를 요청할 수 있습니다.
