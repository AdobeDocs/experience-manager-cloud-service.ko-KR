---
title: AEM 애플리케이션에 Tagging 작성
description: 사용자 정의 AEM 애플리케이션 내에서 태그를 사용하여 프로그래밍 방식으로 작업
translation-type: tm+mt
source-git-commit: ce55065c3ae6a2350ed06811af76477df7c11291
workflow-type: tm+mt
source-wordcount: '769'
ht-degree: 0%

---


# AEM 응용 프로그램에 Tagging 작성 {#building-tagging-into-aem-applications}

이 문서에서는 사용자 정의 AEM 응용 프로그램 내에서 태그를 사용하여 프로그래밍 방식으로 작업하거나 태그를 확장하기 위해

* [태깅 API](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/tagging/package-summary.html)

그리고

* [태깅 프레임워크](tagging-framework.md)

태그 지정에 대한 관련 정보

* 컨텐츠 작성자의 컨텐츠 태그 지정에 대한 자세한 내용은 [태그 사용](/help/sites-cloud/authoring/features/tags.md)을 참조하십시오.
* 태그 만들기 및 관리와 컨텐츠 태그가 적용된 관리자 관점에서는 태그 관리를 참조하십시오.

## Tagging API {#overview-of-the-tagging-api} 개요

AEM에서 [태깅 프레임워크](tagging-framework.md)을 구현하면 JCR API를 사용하여 태그 및 태그 컨텐츠를 관리할 수 있습니다. `TagManager` 문자열 배열 속성에 값으로 입력한 태그가 중복되지 않도록 하고, 비기존 태그 `cq:tags` 를 가리키는 태그를 제거하며, 이동되거나 병합된 태그에 대한 업데이트 `TagID`  `TagID`를 제거합니다. `TagManager` 잘못된 변경 사항을 되돌리는 JCR 관측 수신기를 사용합니다. 기본 클래스는 [com.day.cq.taging](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/index.html?com/day/cq/tagging/package-summary.html) 패키지에 있습니다.

* `JcrTagManagerFactory` - a의 JCR 기반 구현을 반환합니다 `TagManager`. Tagging API의 참조 구현입니다.
* `TagManager` - 경로 및 이름별로 태그를 확인하고 만들 수 있습니다.
* `Tag` - 태그 개체를 정의합니다.

### JCR 기반 TagManager 가져오기 {#getting-a-jcr-based-tagmanager}

`TagManager` 인스턴스를 검색하려면 JCR `Session`이 있어야 하며 `getTagManager(Session)`를 호출해야 합니다.

```java
@Reference
JcrTagManagerFactory jcrTagManagerFactory;

TagManager tagManager = jcrTagManagerFactory.getTagManager(session);
```

일반적인 Sling 컨텍스트에서는 `ResourceResolver`의 `TagManager`에도 적용할 수 있습니다.

```java
TagManager tagManager = resourceResolver.adaptTo(TagManager.class);
```

### 태그 개체 {#retrieving-a-tag-object} 검색

기존 태그를 확인하거나 새 태그를 만들어 `Tag`을(를) 통해 검색할 수 있습니다.`TagManager`

```java
Tag tag = tagManager.resolve("my/tag"); // for existing tags

Tag tag = tagManager.createTag("my/tag"); // for new tags
```

`Tags`을(를) JCR `Nodes`에 매핑하는 JCR 기반 구현의 경우, 리소스가 있는 경우(예: `/content/cq:tags/default/my/tag`) Sling의 `adaptTo` 메커니즘을 직접 사용할 수 있습니다.

```java
Tag tag = resource.adaptTo(Tag.class);
```

태그는 노드가 아닌 *부터*&#x200B;리소스로만 변환할 수 있지만, 태그는 노드 및 리소스 모두 *로 변환할 수 있습니다.*

```java
Node node = tag.adaptTo(Node.class);
Resource node = tag.adaptTo(Resource.class);
```

>[!NOTE]
>
>`Node`은(는) Sling `Adaptable.adaptTo(Class)` 메서드를 구현하지 않으므로 `Node`에서 `Tag`에 직접 적용할 수 없습니다.

### 태그 {#getting-and-setting-tags} 가져오기 및 설정

```java
// Getting the tags of a Resource:
Tag[] tags = tagManager.getTags(resource);

// Setting tags to a Resource:
tagManager.setTags(resource, tags);
```

### 태그 검색 {#searching-for-tags}

```java
// Searching for the Resource objects that are tagged with the tag object:
Iterator<Resource> it = tag.find();

// Retrieving the usage count of the tag object:
long count = tag.getCount();

// Searching for the Resource objects that are tagged with the tagID String:
 RangeIterator<Resource> it = tagManager.find(tagID);
```

>[!NOTE]
>
>사용할 유효한 `RangeIterator`은 다음과 같습니다.
>
>`com.day.cq.commons.RangeIterator`

### 태그 삭제 {#deleting-tags}

```java
tagManager.deleteTag(tag);
```

### {#replicating-tags} 태그 복제

태그는 `nt:hierarchyNode` 유형이므로 태그와 함께 복제 서비스(`Replicator`)를 사용할 수 있습니다.

```java
replicator.replicate(session, replicationActionType, tagPath);
```

## 태그 가비지 수집기 {#the-tag-garbage-collector}

태그 가비지 수집기는 숨겨지고 사용하지 않는 태그를 정리하는 백그라운드 서비스입니다. 숨겨진 태그와 사용하지 않는 태그는 `/content/cq:tags` 아래에 있는 태그로, `cq:movedTo` 속성이 있으며 컨텐트 노드에서 사용되지 않습니다. 그들은 0의 카운트를 가지고 있다. 이 지연 삭제 프로세스를 사용하면 컨텐츠 노드(즉, `cq:tags` 속성)가 이동 또는 병합 작업의 일부로 업데이트되지 않아도 됩니다. `cq:tags` 속성의 참조는 페이지 속성 대화 상자를 통해 `cq:tags` 속성이 업데이트되면 자동으로 업데이트됩니다.

태그 가비지 수집기는 기본적으로 하루에 한 번 실행됩니다. 다음 위치에서 구성할 수 있습니다.

`http://<host>:<port>/system/console/configMgr/com.day.cq.tagging.impl.TagGarbageCollector`

## 태그 검색 및 태그 목록 {#tag-search-and-tag-listing}

태그 및 태그 목록 검색은 다음과 같이 작동합니다.

* `TagID`을 검색하면 `cq:movedTo` 속성이 `TagID`로 설정되고 `cq:movedTo` `TagID`s를 통해 뒤따르는 태그를 검색합니다.
* 태그 제목을 검색하면 `cq:movedTo` 속성이 없는 태그만 검색됩니다.

## 다른 언어의 태그 {#tags-in-different-languages}

`title` 태그는 다른 언어로 정의할 수 있습니다. 그런 다음 언어 구분 속성이 태그 노드에 추가됩니다. 이 속성의 형식은 `jcr:title.<locale>`입니다(예:프랑스어 번역용 `jcr:title.fr` `<locale>` 은(는) 소문자 ISO 로케일 문자이고 하이픈/대시(`_`) 대신 밑줄(`-`)을 사용해야 합니다. 예: `de_ch`.

예를 들어 **Animals** 태그가 **Products** 페이지에 추가되면 `stockphotography:animals` 값이 `/content/wknd/en/products/jcr:content` 노드의 `cq:tags` 속성에 추가됩니다. 변환은 태그 노드에서 참조됩니다.

서버측 API가 `title` 관련 메서드를 지역화했습니다.

* [`com.day.cq.tagging.Tag`](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/index.html?com/day/cq/tagging/Tag.html)
   * `getLocalizedTitle(Locale locale)`
   * `getLocalizedTitlePaths()`
   * `getLocalizedTitles()`
   * `getTitle(Locale locale)`
   * `getTitlePath(Locale locale)`
* [`com.day.cq.tagging.TagManager`](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/index.html?com/day/cq/tagging/TagManager.html)
   * `canCreateTagByTitle(String tagTitlePath, Locale locale)`
   * `createTagByTitle(String tagTitlePath, Locale locale)`
   * `resolveByTitle(String tagTitlePath, Locale locale)`

AEM에서는 페이지 언어 또는 사용자 언어로 언어를 얻을 수 있습니다.

태깅의 경우 현지화는 페이지 언어, 사용자 언어 또는 다른 언어로 태그 `titles`를 표시할 수 있으므로 컨텍스트에 따라 달라집니다.

### 태그 편집 대화 상자에 새 언어 추가 {#adding-a-new-language-to-the-edit-tag-dialog}

다음 절차에서는 **태그 편집** 대화 상자에 새 언어(예: 핀란드어)를 추가하는 방법에 대해 설명합니다.

1. **CRXDE**&#x200B;에서 노드 `/content/cq:tags`의 다중 값 속성 `languages`을 편집합니다.
1. 핀란드어 로케일을 나타내는 `fi_fi`을(를) 추가하고 변경 사항을 저장합니다.

이제 페이지 속성의 태그 대화 상자와 **Tagging** 콘솔에서 태그를 편집할 때 **태그 편집** 대화 상자에서 핀란드어를 사용할 수 있습니다.

>[!NOTE]
>
>새 언어는 AEM 인식 언어 중 하나여야 합니다. 즉, `/libs/wcm/core/resources/languages` 아래의 노드로 사용할 수 있어야 합니다.
