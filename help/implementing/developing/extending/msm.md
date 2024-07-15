---
title: 다중 사이트 관리자 확장
description: 다중 사이트 관리자의 기능을 확장하는 방법에 대해 알아봅니다.
exl-id: 4b7a23c3-65d1-4784-9dea-32fcceca37d1
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 646ca4f4a441bf1565558002dcd6f96d3e228563
workflow-type: tm+mt
source-wordcount: '2337'
ht-degree: 93%

---

# 다중 사이트 관리자 확장 {#extending-the-multi-site-manager}

이 문서는 다중 사이트 관리자의 기능을 확장하는 방법을 이해하는 데 도움이 되며 다음 주제를 다룹니다.

* MSM Java API의 주요 멤버에 대해 알아보기
* 롤아웃 구성에서 사용할 수 있는 새 동기화 작업 만들기
* 기본 언어 및 국가 코드 수정

>[!TIP]
>
>이 페이지는 [콘텐츠 재사용: 다중 사이트 관리자](/help/sites-cloud/administering/msm/overview.md) 문서의 맥락에서 더 쉽게 이해할 수 있습니다.

>[!CAUTION]
>
>다중 사이트 관리자 및 해당 API는 웹 사이트를 작성할 때 사용되며 작성 환경에서만 사용할 수 있습니다.

## Java API 개요 {#overview-of-the-java-api}

다중 사이트 관리는 다음 패키지로 구성됩니다.

* [com.day.cq.wcm.msm.api](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/day/cq/wcm/msm/api/package-frame.html)
* [com.day.cq.wcm.msm.commons](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/day/cq/wcm/msm/commons/package-frame.html)

기본 MSM API 오브젝트는 다음과 같이 상호 작용합니다([사용된 용어](/help/sites-cloud/administering/msm/overview.md#terms-used) 섹션도 참조).

![기본 MSM API 오브젝트](assets/msm-api-interaction.png)

* **`Blueprint`** - `Blueprint`([블루프린트 구성](/help/sites-cloud/administering/msm/overview.md#source-blueprints-and-blueprint-configurations)에서와 같이)는 Live Copy가 콘텐츠를 상속할 수 있는 페이지를 지정합니다.

  ![블루프린트](assets/msm-blueprint-interaction.png)

   * 블루프린트 구성(`Blueprint`) 사용은 선택 사항이며, 이 구성은 다음과 같은 역할을 합니다.

      * 작성자가 소스에서 **롤아웃** 옵션을 사용하여 이 소스에서 상속되는 Live Copy에 수정 사항을 명시적으로 푸시할 수 있도록 합니다.
      * 작성자가 **사이트 만들기**&#x200B;를 사용하여 손쉽게 언어를 선택하고 Live Copy 구조를 구성할 수 있도록 합니다.
      * 결과 Live Copy에 대한 기본 롤아웃 구성을 정의합니다.

* **`LiveRelationship`** - `LiveRelationship`은 Live Copy 분기의 리소스와 이에 상응하는 소스/블루프린트 리소스 간의 연결(관계)을 지정합니다.

   * 이 관계는 상속 및 롤아웃을 실현할 때 사용됩니다.
   * `LiveRelationship` 오브젝트는 관계와 관련된 롤아웃 구성(`RolloutConfig`), `LiveCopy` 및 `LiveStatus` 오브젝트에 대한 액세스(참조)를 제공합니다.

   * 예를 들어 Live Copy는 `/content/wknd/language-masters`의 소스/블루프린트로 `/content/copy/us`에 만들어집니다. 리소스 `/content/wknd/language-masters/en/jcr:content` 및 `/content/copy/us/en/jcr:content`는 관계를 형성합니다.

* **`LiveCopy`** - `LiveCopy`는 Live Copy 리소스와 해당 소스/블루프린트 리소스 간의 관계(`LiveRelationship`)에 대한 구성 세부 정보를 보유합니다.

   * `LiveCopy` 클래스를 사용하여 페이지 경로, 소스/블루프린트 페이지 경로, 롤아웃 구성, `LiveCopy`에 하위 페이지도 포함되는지 여부에 액세스합니다.

   * `LiveCopy` 노드는 **사이트 만들기** 또는 **Live Copy 만들기**&#x200B;를 사용할 때마다 만들어집니다.

* **`LiveStatus`** - `LiveStatus` 오브젝트는 `LiveRelationship`의 런타임 상태에 대한 액세스를 제공합니다. Live Copy의 동기화 상태를 쿼리하는 데 사용합니다.

* **`LiveAction`** - `LiveAction`은 롤아웃과 관련된 각 리소스에서 실행되는 작업입니다.

   * `LiveAction`은 `RolloutConfig`에 의해서만 생성됩니다.

* **`LiveActionFactory`** - `LiveActionFactory`는 `LiveAction` 구성이 있을 때 `LiveAction` 오브젝트를 만듭니다. 구성은 저장소에 리소스로 저장됩니다.

* **`RolloutConfig`** - `RolloutConfig`는 트리거되었을 때 사용될 `LiveActions`의 목록을 보유합니다. `LiveCopy`는 `RolloutConfig`를 상속하며 결과는 `LiveRelationship`에 표시됩니다.

   * Live Copy를 처음 설정하는 경우에도 `RolloutConfig`를 사용합니다(`LiveAction`을 트리거하는 역할).

## 새 동기화 작업 만들기 {#creating-a-new-synchronization-action}

롤아웃 구성에 사용할 사용자 정의 동기화 작업을 만들 수 있습니다. 이는 [설치된 작업](/help/sites-cloud/administering/msm/live-copy-sync-config.md#installed-synchronization-actions)이 특정 애플리케이션 요구 사항을 충족하지 않을 때 유용할 수 있습니다.

이렇게 하려면 다음과 같이 두 개의 클래스를 만듭니다.

* 작업을 수행하는 [`com.day.cq.wcm.msm.api.LiveAction`](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/day/cq/wcm/msm/api/LiveAction.html) 인터페이스의 구현.
* [`com.day.cq.wcm.msm.api.LiveActionFactory`](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/day/cq/wcm/msm/api/LiveActionFactory.html) 인터페이스를 구현하고 `LiveAction` 클래스의 인스턴스를 만드는 OSGi 구성 요소.

`LiveActionFactory`는 주어진 구성에 대한 `LiveAction` 클래스의 인스턴스를 만듭니다.

* `LiveAction` 클래스에는 다음 메서드가 포함됩니다.

   * `getName` - 작업의 이름을 반환합니다.

      * 이 이름은 작업을 참조하는 데 사용됩니다(예: 롤아웃 구성).

   * `execute` - 작업의 내용을 수행합니다.

* `LiveActionFactory` 클래스에는 다음과 같은 멤버가 포함됩니다.

   * `LIVE_ACTION_NAME` - 연결된 `LiveAction`의 이름을 포함하는 필드입니다.

      * 이 이름은 `LiveAction` 클래스의 `getName` 메서드에 의해 반환되는 값과 일치합니다.

   * `createAction` - `LiveAction`의 인스턴스를 만듭니다.

      * 선택 사항인 `Resource` 매개변수를 사용하여 구성 정보를 제공할 수 있습니다.

   * `createsAction` - 연결된 `LiveAction`의 이름을 반환합니다.

### LiveAction 구성 노드에 액세스 {#accessing-the-liveaction-configuration-node}

저장소의 `LiveAction` 구성 노드를 사용하여 `LiveAction` 인스턴스의 런타임 동작에 영향을 미치는 정보를 저장합니다. `LiveAction` 구성을 저장하는 저장소의 노드는 런타임 시 `LiveActionFactory` 오브젝트에 사용할 수 있습니다. 따라서 구성 노드에 속성을 추가하여 필요에 따라 `LiveActionFactory` 구현에서 사용할 수 있습니다.

예를 들어 `LiveAction`은(는) 블루프린트 작성자의 이름을 저장해야 합니다. 구성 노드의 속성에는 정보를 저장하는 블루프린트 페이지의 속성 이름이 포함됩니다. 런타임 시 `LiveAction`이 구성에서 속성 이름을 검색한 다음 속성 값을 가져옵니다.

[`LiveActionFactory.createAction`](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/day/cq/wcm/msm/api/LiveActionFactory.html) 메서드의 매개변수는 `Resource` 오브젝트입니다. 이 `Resource` 오브젝트는 롤아웃 구성에서 이 라이브 작업에 대한 `cq:LiveSyncAction` 노드를 나타냅니다.

자세한 내용은 [롤아웃 구성 만들기](/help/sites-cloud/administering/msm/live-copy-sync-config.md#creating-a-rollout-configuration)를 참조하십시오.

평소와 같이 구성 노드를 사용할 때 이를 `ValueMap` 오브젝트에 맞게 조정해야 합니다.

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

### 대상 노드, 소스 노드 및 LiveRelationship 액세스 {#accessing-target-nodes-source-nodes-and-the-liverelationship}

`LiveAction` 오브젝트의 `execute` 메서드의 매개변수로 다음 오브젝트가 제공됩니다.

* Live Copy의 소스를 나타내는 [`Resource`](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/org/apache/sling/api/resource/Resource.html) 오브젝트.
* Live Copy의 대상을 나타내는 `Resource` 오브젝트.
* Live Copy용 [`LiveRelationship`](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/wcm/msm/api/LiveRelationship.html) 오브젝트
   * `autoSave` 값은 `LiveAction`이 저장소의 변경 사항을 저장해야 하는지 여부를 나타냅니다.
   * `reset` 값은 롤아웃 재설정 모드를 나타냅니다.

이러한 개체에서 `LiveCopy`에 대한 정보를 가져올 수 있습니다. 또한 `Resource` 오브젝트를 사용하여 `ResourceResolver`, `Session` 및 `Node` 오브젝트를 얻을 수 있습니다. 이러한 오브젝트는 저장소 콘텐츠를 조작하는 데 유용합니다.

다음 코드의 첫 번째 줄에서 소스는 소스 페이지의 `Resource` 오브젝트입니다.

```java
ResourceResolver resolver = source.getResourceResolver();
Session session = resolver.adaptTo(javax.jcr.Session.class);
Node sourcenode = source.adaptTo(javax.jcr.Node.class);
```

>[!NOTE]
>
>`Resource` 인수는 [`NonExistingResource`](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/org/apache/sling/api/resource/NonExistingResource.html) 오브젝트와 같이 `Node` 오브젝트에 적응하지 않는 `null` 또는 `Resources` 오브젝트일 수 있습니다.

## 새 롤아웃 구성 만들기 {#creating-a-new-rollout-configuration}

설치된 롤아웃 구성이 애플리케이션 요구 사항을 충족하지 않을 경우 다음 두 단계에 따라 롤아웃 구성을 만들 수 있습니다.

* [롤아웃 구성 만들기](#create-the-rollout-configuration)
* [롤아웃 구성에 동기화 작업 추가](#add-synchronization-actions-to-the-rollout-configuration)

새 롤아웃 구성을 만들었다면 블루프린트 또는 Live Copy 페이지에서 롤아웃 구성을 설정할 때 사용할 수 있습니다.

>[!TIP]
>
>[롤아웃 사용자 정의를 위한 모범 사례](/help/sites-cloud/administering/msm/best-practices.md#customizing-rollouts)도 참조하십시오.

### 롤아웃 구성 만들기 {#create-the-rollout-configuration}

롤아웃 구성을 만들려면 다음 작업을 수행하십시오.

1. `https://<host>:<port>/crx/de`에서 CRXDE Lite를 엽니다.

1. 프로젝트의 `/libs/msm/wcm/rolloutconfigs` 사용자 정의 버전인 `/apps/msm/<your-project>/rolloutconfigs`로 이동합니다.

   * 이것이 최초의 구성인 경우 이 `/libs` 분기를 템플릿으로 사용해 `/apps` 아래에 새 분기를 만들어야 합니다.

1. 이 위치 아래에서 다음 속성을 사용하여 노드를 만듭니다.

   * **이름**: 롤아웃 구성의 노드 이름(예: `contentCopy` 또는 `workflow`)
   * **유형**: `cq:RolloutConfig`

1. 이 노드에 다음 속성을 추가합니다.

   * **이름**: `jcr:title`
     **유형**: `String`
     **값**: UI에 표시되는 식별 제목입니다.

   * **이름**: `jcr:description`
     **유형**: `String`
     **값**: 선택적 설명입니다.

   * **이름**: `cq:trigger`
     **유형**: `String`
     **값**: 사용할 [롤아웃 트리거](/help/sites-cloud/administering/msm/live-copy-sync-config.md#rollout-triggers)입니다.
      * `rollout`
      * `modification`
      * `publish`
      * `deactivate`

1. **모두 저장**&#x200B;을 클릭합니다.

### 롤아웃 구성에 동기화 작업 추가 {#add-synchronization-actions-to-the-rollout-configuration}

롤아웃 구성은 `/apps/msm/<your-project>/rolloutconfigs` 노드 아래에서 만든 [롤아웃 구성 노드](#create-the-rollout-configuration) 아래에 저장됩니다.

`cq:LiveSyncAction` 유형의 하위 노드를 추가하여 롤아웃 구성에 동기화 작업을 추가합니다. 동기화 작업 노드의 순서에 따라 작업이 발생하는 순서가 결정됩니다.

1. CRXDE Lite에서 [롤아웃 구성](#create-the-rollout-configuration) 노드를 선택합니다(예: `/apps/msm/myproject/rolloutconfigs/myrolloutconfig`).

1. 다음 노드 속성을 사용하여 노드를 만듭니다.

   * **이름**: 동기화 작업의 노드 이름입니다.
      * 이름은 [동기화 작업](/help/sites-cloud/administering/msm/live-copy-sync-config.md#installed-synchronization-actions) 아래의 테이블에 있는 **작업 이름**&#x200B;과 동일해야 합니다(예: `contentCopy` 또는 `workflow`).
   * **유형**: `cq:LiveSyncAction`

1. 필요한 만큼 동기화 작업 노드를 추가하고 구성합니다.

1. 작업 노드의 순서가 원하는 순서와 일치하도록 작업 노드를 재정렬합니다.
   * 최상위 작업 노드가 먼저 발생합니다.

## 간단한 LiveActionFactory 클래스 만들기 및 사용 {#creating-and-using-a-simple-liveactionfactory-class}

이 섹션의 절차에 따라 `LiveActionFactory`를 개발하여 롤아웃 구성에서 사용하십시오. 이 절차에서는 Maven 및 Eclipse를 사용하여 `LiveActionFactory`를 개발하고 배포합니다.

1. [Maven 프로젝트를 만들어](#create-the-maven-project) Eclipse로 가져옵니다.
1. POM 파일에 [종속성을 추가](#add-dependencies-to-the-pom-file)합니다.
1. [`LiveActionFactory` 인터페이스를 구현](#implement-liveactionfactory)하고 OSGi 번들을 배포합니다.
1. [롤아웃 구성을 만듭니다](#create-the-example-rollout-configuration).
1. [Live Copy를 만듭니다](#create-the-live-copy).

[Maven 프로젝트 및 Java 클래스의 소스 코드](https://github.com/Adobe-Marketing-Cloud/experiencemanager-java-msmrollout)는 공개 Git 저장소에서 사용할 수 있습니다.

### Maven 프로젝트 만들기 {#create-the-maven-project}

다음 절차를 수행하려면 먼저 Maven 설정 파일에 `adobe-public` 프로필을 추가해야 합니다.

* adobe-public 프로필에 대한 자세한 내용은 [콘텐츠 패키지 Maven 플러그인 얻기](/help/implementing/developing/tools/maven-plugin.md#obtaining-the-content-package-maven-plugin)를 참조하십시오.
* Maven 설정 파일에 대한 내용은 Maven [설정 참조](https://maven.apache.org/settings.html)를 참조하십시오.

1. 터미널 또는 명령줄 세션을 열고 디렉터리를 변경하여 프로젝트를 만들 위치를 가리키도록 합니다.
1. 다음 명령을 입력합니다.

   ```text
   mvn archetype:generate -DarchetypeGroupId=com.day.jcr.vault -DarchetypeArtifactId=multimodule-content-package-archetype -DarchetypeVersion=1.0.0 -DarchetypeRepository=adobe-public-releases
   ```

1. 대화형 프롬프트에서 다음 값을 지정합니다.

   * **`groupId`**: `com.adobe.example.msm`
   * **`artifactId`**: `MyLiveActionFactory`
   * **`version`**: `1.0-SNAPSHOT`
   * **`package`**: `MyPackage`
   * **`appsFolderName`**: `myapp`
   * **`artifactName`**: `MyLiveActionFactory package`
   * **`packageGroup`**: `myPackages`

1. Eclipse를 시작하고 [Maven 프로젝트를 가져옵니다](/help/implementing/developing/tools/eclipse.md#import-the-maven-project-into-eclipse).

### POM 파일에 종속성 추가 {#add-dependencies-to-the-pom-file}

Eclipse 컴파일러가 `LiveActionFactory` 코드에서 사용되는 클래스를 참조할 수 있도록 종속성을 추가합니다.

1. Eclipse 프로젝트 탐색기에서 `MyLiveActionFactory/pom.xml` 파일을 엽니다.

1. 편집기에서 `pom.xml` 탭을 클릭하고 `project/dependencyManagement/dependencies` 섹션을 찾습니다.

1. `dependencyManagement` 요소 내에 다음 XML을 추가한 다음 파일을 저장합니다.

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

1. **프로젝트 탐색기**&#x200B;의 `MyLiveActionFactory-bundle/pom.xml`에서 번들의 POM 파일을 엽니다.

1. 편집기에서 `pom.xml` 탭을 클릭하고 프로젝트/종속성 섹션을 찾습니다. 종속성 요소 내에 다음 XML을 추가한 다음 파일을 저장합니다.

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

다음 `LiveActionFactory` 클래스는 소스 및 대상 페이지에 대한 메시지를 로깅하고 소스 노드에서 대상 노드로 `cq:lastModifiedBy` 속성을 복사하는 `LiveAction`을 구현합니다. 라이브 작업의 이름은 `exampleLiveAction`입니다.

1. Eclipse 프로젝트 탐색기에서 `MyLiveActionFactory-bundle/src/main/java/com.adobe.example.msm` 패키지를 마우스 오른쪽 단추로 클릭하고 **새로 만들기** > **클래스**&#x200B;를 클릭합니다.

1. **이름**&#x200B;으로 `ExampleLiveActionFactory`를 입력한 다음 **마침**&#x200B;을 클릭합니다.

1. `ExampleLiveActionFactory.java` 파일을 열고 내용을 다음 코드로 바꾼 후 파일을 저장합니다.

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

1. 터미널 또는 명령 세션을 사용하여 디렉터리를 `MyLiveActionFactory` 디렉터리(Maven 프로젝트 디렉터리)로 변경합니다. 이어서 다음 명령을 입력합니다.

   ```shell
   mvn -PautoInstallPackage clean install
   ```

1. AEM `error.log` 파일은 번들이 시작되었음을 나타내야 하며 `https://<host>:<port>/system/console/status-slinglogs`의 로그에 표시되어야 합니다.

   ```text
   13.08.2013 14:34:55.450 *INFO* [OsgiInstallerImpl] com.adobe.example.msm.MyLiveActionFactory-bundle BundleEvent RESOLVED
   13.08.2013 14:34:55.451 *INFO* [OsgiInstallerImpl] com.adobe.example.msm.MyLiveActionFactory-bundle BundleEvent STARTING
   13.08.2013 14:34:55.451 *INFO* [OsgiInstallerImpl] com.adobe.example.msm.MyLiveActionFactory-bundle BundleEvent STARTED
   13.08.2013 14:34:55.453 *INFO* [OsgiInstallerImpl] com.adobe.example.msm.MyLiveActionFactory-bundle Service [com.adobe.example.msm.ExampleLiveActionFactory,2188] ServiceEvent REGISTERED
   13.08.2013 14:34:55.454 *INFO* [OsgiInstallerImpl] org.apache.sling.audit.osgi.installer Started bundle com.adobe.example.msm.MyLiveActionFactory-bundle [316]
   ```

### 롤아웃 구성 예 만들기 {#create-the-example-rollout-configuration}

앞서 만든 `LiveActionFactory`를 사용하는 MSM 롤아웃 구성을 만듭니다.

1. 다음 속성을 사용해 [표준 절차에 따른 롤아웃 구성](/help/sites-cloud/administering/msm/live-copy-sync-config.md#creating-a-rollout-configuration)을 만들고 구성합니다.

   * **제목**: Example Rollout Configuration
   * **이름**: examplerolloutconfig
   * **cq:trigger**: `publish`

### 롤아웃 구성 예에 라이브 작업 추가 {#add-the-live-action-to-the-example-rollout-configuration}

이전 절차에서 만든 롤아웃 구성을 `ExampleLiveActionFactory` 클래스를 사용하도록 구성합니다.

1. CRXDE Lite를 엽니다.

1. `/apps/msm/rolloutconfigs/examplerolloutconfig/jcr:content` 아래에 다음 노드를 만듭니다.

   * **이름**: `exampleLiveAction`
   * **유형**: `cq:LiveSyncAction`

1. **모두 저장**&#x200B;을 클릭합니다.

1. `exampleLiveAction` 노드를 선택하고 `cq:LastModifiedBy` 속성이 소스에서 대상 노드로 복제되어야 함을 `ExampleLiveAction` 클래스에 표시하는 속성을 추가합니다.

   * **이름**: `repLastModBy`
   * **유형**: `Boolean`
   * **값**: `true`

1. **모두 저장**&#x200B;을 클릭합니다.

### Live Copy 만들기 {#create-the-live-copy}

롤아웃 구성을 사용하여 WKND 참조 사이트의 영어/제품 분기의 [Live Copy를 만듭니다](/help/sites-cloud/administering/msm/creating-live-copies.md#creating-a-live-copy-of-a-page).

* **소스**: `/content/wknd/language-masters/en/products`

* **롤아웃 구성**: Example Rollout Configuration

소스 분기의 **제품**(영어) 페이지를 활성화하고 `LiveAction` 클래스가 생성하는 로그 메시지를 관찰합니다.

```xml
16.08.2013 10:53:33.055 *INFO* [Thread-444535] com.adobe.example.msm.ExampleLiveActionFactory$ExampleLiveAction  ***ExampleLiveAction has been executed.***
16.08.2013 10:53:33.055 *INFO* [Thread-444535] com.adobe.example.msm.ExampleLiveActionFactory$ExampleLiveAction  ***Target node lastModifiedBy property updated: admin ***
```

## 언어 이름 및 기본 국가 변경 {#changing-language-names-and-default-countries}

AEM은 기본 언어 및 국가 코드 세트를 사용합니다.

* 기본 언어 코드는 ISO-639-1에서 정의한 소문자 두 자리 코드입니다.
* 기본 국가 코드는 ISO 3166에서 정의된 소문자 또는 대문자 두 자리 코드입니다.

MSM은 저장된 언어 및 국가 코드 목록을 사용하여 페이지의 언어 버전 이름과 연결된 국가 이름을 결정합니다. 필요한 경우 목록의 다음 측면을 변경할 수 있습니다.

* 언어 제목
* 국가 이름
* 언어의 기본 국가(예: `en`, `de` 등)

언어 목록은 `/libs/wcm/core/resources/languages` 노드 아래에 저장됩니다. 각 하위 노드는 언어 또는 언어 국가를 나타냅니다.

* 노드의 이름은 언어 코드(예: `en` 또는 `de`) 또는 언어_국가 코드(예: `en_us` 또는 `de_ch`)입니다.

* 노드의 `language` 속성은 코드 언어의 전체 이름을 저장합니다.
* 노드의 `country` 속성은 코드 국가의 전체 이름을 저장합니다.
* 노드 이름이 언어 코드로만 구성된 경우(예: `en`) 국가 속성은 `*`이며, 추가 `defaultCountry` 속성에 사용할 국가를 나타내는 언어 국가 코드가 저장됩니다.

![언어 정의](assets/msm-language-manager.png)

언어를 수정하려면 다음 작업을 수행하십시오.

1. CRXDE Lite를 엽니다.
1. `/apps` 폴더를 선택하고 **만들기**&#x200B;를 클릭한 다음 **폴더 만들기**&#x200B;를 클릭합니다.

1. 새 폴더의 이름을 `wcm`으로 지정합니다.

1. 이전 단계를 반복하여 `/apps/wcm/core` 폴더 트리를 만듭니다. `core`에서 이름이 `resources`인 `sling:Folder` 유형 노드를 만듭니다.

1. 마우스 오른쪽 버튼으로 `/libs/wcm/core/resources/languages` 노드를 클릭하고 **복사**&#x200B;를 클릭합니다.
1. 마우스 오른쪽 버튼으로 `/apps/wcm/core/resources` 폴더를 클릭하고 **붙여넣기**&#x200B;를 클릭합니다. 필요에 따라 하위 노드를 수정합니다.
1. **모두 저장**&#x200B;을 클릭합니다.
1. **도구**, **작업**&#x200B;을 클릭한 다음 **웹 콘솔**&#x200B;을 클릭합니다. 이 콘솔에서 **OSGi**&#x200B;를 클릭한 다음 **구성**&#x200B;을 클릭합니다.
1. **일별 CQ WCM 언어 관리자**&#x200B;를 찾아 클릭하고 **언어 목록**&#x200B;의 값을 `/apps/wcm/core/resources/languages`로 변경한 다음 **저장**&#x200B;을 클릭합니다.

   ![일별 CQ WCM 언어 관리자](assets/msm-language-manager.png)

## 페이지 속성에서 MSM 잠금 구성 {#configuring-msm-locks-on-page-properties}

사용자 정의 페이지 속성을 만들 때 새 속성이 모든 Live Copy에 롤아웃될 수 있는지 여부를 고려해야 할 수 있습니다.

다음과 같이 새 페이지 속성 두 개를 추가하는 경우를 예로 들 수 있습니다.

* 연락처 이메일:

   * 이 속성은 각 국가(또는 브랜드 등)에서 다르므로 롤아웃할 필요가 없습니다.

* 주요 시각 스타일:

   * 프로젝트 요구 사항은 이 속성이 모든 국가(또는 브랜드 등)에 (일반적으로) 공통된 상태로 롤아웃되어야 한다는 것입니다.

그렇다면 다음과 같이 작업해야 합니다.

* 연락처 이메일:

   * 롤아웃된 속성에서 제외되도록 합니다.
   * 자세한 내용은 [Live Copy 동기화 구성](/help/sites-cloud/administering/msm/live-copy-sync-config.md#excluding-properties-and-node-types-from-synchronization)을 참조하십시오.

* 주요 시각 스타일:

   * 상속이 취소되지 않는 한 이 속성을 편집할 수 없도록 해야 합니다.
   * 또한 상속이 취소되었을 때 상속을 복원할 수 있도록 해야 합니다. 이 부분은 체인 고리/끊어진 체인 고리를 클릭하여 제어하며, 체인 모양이 전환되어 연결 상태를 나타냅니다.

페이지 속성이 롤아웃 대상인지 여부와 편집 시 상속 취소/복원 대상인지 여부는 다음과 같은 대화 상자 속성에 의해 제어됩니다.

* `cq-msm-lockable`

   * 대화 상자에 체인 고리 기호를 만듭니다.
   * 상속이 취소된 경우(체인 고리가 끊어진 경우)에만 편집을 허용합니다.
   * 리소스의 첫 번째 하위 수준에만 적용됩니다.
      * **유형**: `String`
      * **값**: 고려 중인 속성의 이름을 보유하며, `name` 속성의 값과 비교할 수 있습니다.
         * 예:
           `/libs/foundation/components/page/cq:dialog/content/items/tabs/items/basic/items/column/items/title/items/title`

`cq-msm-lockable`이 정의된 경우 체인을 끊거나 닫으면 다음과 같은 방식으로 MSM과 상호 작용합니다.

* `cq-msm-lockable`의 값이 다음과 같은 경우:

   * **상대**(예: `myProperty` 또는 `./myProperty`)

      * 체인을 끊으면 `cq:propertyInheritanceCancelled`에서 속성이 추가되고 제거됩니다.

   * **절대**(예: `/image`)

      * 체인을 끊으면 `cq:LiveSyncCancelled` 믹스인을 `./image`에 추가하고 `cq:isCancelledForChildren`을 `true`로 설정하여 상속을 취소합니다.

      * 체인을 닫으면 상속을 되돌립니다.

>[!NOTE]
>
>`cq-msm-lockable`은 편집할 리소스의 첫 번째 하위 수준에 적용되며, 값이 절대 또는 상대로 정의되었는지 여부에 관계없이 더 깊은 수준의 상위 항목에서는 작동하지 않습니다.

>[!NOTE]
>
>상속을 다시 시작해도 Live Copy 페이지 속성은 자동으로 소스 속성과 동기화되지 않습니다. 필요한 경우 수동으로 동기화를 요청할 수 있습니다.
