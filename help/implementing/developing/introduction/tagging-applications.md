---
title: AEM 애플리케이션에 태그 지정 구축
description: 프로그래밍 방식으로 사용자 지정 AEM 애플리케이션 내에서 태그를 사용하거나 태그를 확장하는 작업을 합니다
exl-id: a106dce1-5d51-406a-a563-4dea83987343
source-git-commit: ca849bd76e5ac40bc76cf497619a82b238d898fa
workflow-type: tm+mt
source-wordcount: '762'
ht-degree: 1%

---

# AEM 애플리케이션에 태그 지정 구축 {#building-tagging-into-aem-applications}

사용자 지정 AEM 애플리케이션 내에서 태그를 프로그래밍 방식으로 사용하거나 태그를 확장하는 목적으로 이 문서에서는

* [태깅 API](https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/tagging/package-summary.html)

와 상호 작용함

* [태깅 프레임워크](tagging-framework.md)

태깅 관련 정보는 다음과 같습니다.

* 자세한 내용은 [태그 사용](/help/sites-cloud/authoring/features/tags.md) 컨텐츠 작성자로서 컨텐츠를 태깅하는 방법에 대한 정보입니다.
* 태그 작성 및 관리 방법과 컨텐츠 태그가 적용되는 항목에 대한 관리자의 관점에서 태그 관리를 참조하십시오.

## 태깅 API 개요 {#overview-of-the-tagging-api}

의 구현 [태그 프레임워크](tagging-framework.md) AEM에서 JCR API를 사용하여 태그 및 태그 컨텐츠를 관리할 수 있습니다. `TagManager` 는 태그가 `cq:tags` 문자열 배열 속성은 중복되지 않고 제거됩니다. `TagID`기존 태그가 아닌 태그 및 업데이트를 가리킵니다. `TagID`이동 또는 병합된 태그의 경우입니다. `TagManager` 은 잘못된 변경 사항을 되돌리는 JCR 관찰 수신기를 사용합니다. 기본 클래스는 [com.day.cq.tagging](https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/tagging/package-summary.html) 패키지:

* `JcrTagManagerFactory` - 의 JCR 기반 구현을 반환합니다. `TagManager`. 태깅 API의 참조 구현입니다.
* `TagManager` - 경로 및 이름으로 태그를 확인하고 만들 수 있습니다.
* `Tag` - 태그 개체를 정의합니다.

### JCR 기반 TagManager 가져오기 {#getting-a-jcr-based-tagmanager}

를 검색하려면 `TagManager` 예를 들어 JCR이 있어야 합니다 `Session` 및 `getTagManager(Session)`:

```java
@Reference
JcrTagManagerFactory jcrTagManagerFactory;

TagManager tagManager = jcrTagManagerFactory.getTagManager(session);
```

일반적인 Sling 컨텍스트에서 를 사용하여 `TagManager` 에서 `ResourceResolver`:

```java
TagManager tagManager = resourceResolver.adaptTo(TagManager.class);
```

### 태그 개체 검색 {#retrieving-a-tag-object}

A `Tag` 는 `TagManager`기존 태그를 해결하거나 새 태그를 만들어

```java
Tag tag = tagManager.resolve("my/tag"); // for existing tags

Tag tag = tagManager.createTag("my/tag"); // for new tags
```

를 매핑하는 JCR 기반 구현의 경우 `Tags` JCR `Nodes`를 채울 때는 Sling을 직접 사용할 수 있습니다 `adaptTo` 리소스가 있는 경우(예: `/content/cq:tags/default/my/tag`):

```java
Tag tag = resource.adaptTo(Tag.class);
```

반면에 태그는 *변환 전:* 리소스(노드가 아님), 태그를 변환할 수 있습니다 *to* 노드와 리소스 모두:

```java
Node node = tag.adaptTo(Node.class);
Resource node = tag.adaptTo(Resource.class);
```

>[!NOTE]
>
>직접 채택 `Node` to `Tag` 왜냐하면 `Node` Sling을 구현하지 않습니다. `Adaptable.adaptTo(Class)` 메서드를 사용합니다.

### 태그 가져오기 및 설정 {#getting-and-setting-tags}

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
>유효한 `RangeIterator` 를 사용하려면
>
>`com.day.cq.commons.RangeIterator`

### 태그 삭제 {#deleting-tags}

```java
tagManager.deleteTag(tag);
```

### 태그 복제 {#replicating-tags}

복제 서비스(`Replicator`) 태그 유형이 `nt:hierarchyNode`:

```java
replicator.replicate(session, replicationActionType, tagPath);
```

## 태그 가비지 수집기 {#the-tag-garbage-collector}

태그 가비지 수집기는 숨겨지고 사용하지 않는 태그를 정리하는 백그라운드 서비스입니다. 숨겨진 태그와 사용하지 않는 태그는 아래에 있는 태그입니다 `/content/cq:tags` 그거 `cq:movedTo` 속성 및 이 컨텐츠 노드에서 사용되지 않습니다. 그들은 0을 가지고 있다. 이러한 지연 삭제 프로세스를 사용하여 컨텐츠 노드(즉, `cq:tags` 속성)은 이동 또는 병합 작업의 일부로 업데이트할 필요가 없습니다. 의 참조 `cq:tags` 속성은 `cq:tags` 예를 들어 페이지 속성 대화 상자를 통해 속성이 업데이트됩니다.

태그 가비지 수집기는 기본적으로 하루에 한 번 실행됩니다. 다음 위치에서 구성할 수 있습니다.

`http://<host>:<port>/system/console/configMgr/com.day.cq.tagging.impl.TagGarbageCollector`

## 태그 검색 및 태그 목록 {#tag-search-and-tag-listing}

태그 검색 및 태그 목록은 다음과 같이 작동합니다.

* 검색 대상 `TagID` 속성이 있는 태그를 검색합니다 `cq:movedTo` 설정 `TagID` 그리고 `cq:movedTo` `TagID`s.
* 태그 제목을 검색하면 `cq:movedTo` 속성을 사용합니다.

## 다른 언어의 태그 {#tags-in-different-languages}

태그 `title` 다른 언어로 정의할 수 있습니다. 그런 다음 언어 구분 속성이 태그 노드에 추가됩니다. 이 속성은 형식입니다 `jcr:title.<locale>`예: `jcr:title.fr` 프랑스어 번역을 위해. `<locale>` 소문자 ISO 로케일 문자열이어야 하며 밑줄( )을 사용해야 합니다.`_`하이픈/대시( ) 대신`-`) 내의 예를 들면 다음과 같습니다. `de_ch`.

예를 들어 **동물** 태그에 추가 **제품** 페이지, 값 `stockphotography:animals` 이 속성에 추가됩니다 `cq:tags` 노드 `/content/wknd/en/products/jcr:content`. 번역이 태그 노드에서 참조됩니다.

서버측 API가 현지화되었습니다 `title`관련 메서드:

* [`com.day.cq.tagging.Tag`](https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/tagging/Tag.html)
   * `getLocalizedTitle(Locale locale)`
   * `getLocalizedTitlePaths()`
   * `getLocalizedTitles()`
   * `getTitle(Locale locale)`
   * `getTitlePath(Locale locale)`
* [`com.day.cq.tagging.TagManager`](https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/tagging/TagManager.html)
   * `canCreateTagByTitle(String tagTitlePath, Locale locale)`
   * `createTagByTitle(String tagTitlePath, Locale locale)`
   * `resolveByTitle(String tagTitlePath, Locale locale)`

AEM에서 언어는 페이지 언어나 사용자 언어로 가져올 수 있습니다.

태깅의 경우 현지화는 태그로 컨텍스트에 따라 다릅니다 `titles` 페이지 언어, 사용자 언어 또는 다른 언어로 표시할 수 있습니다.

### 태그 편집 대화 상자에 새 언어 추가 {#adding-a-new-language-to-the-edit-tag-dialog}

다음 절차에서는 새 언어(예: 핀란드어)를 **태그 편집** 대화 상자:

1. in **CRXDE**, multi-value 속성 편집 `languages` 노드 `/content/cq:tags`.
1. 추가 `fi_fi`- 핀란드어 로케일을 나타내고 변경 사항을 저장합니다.

이제 페이지 속성의 태그 대화 상자 및 **태그 편집** 대화 상자에서 태그를 편집할 때 **태깅** 콘솔.

>[!NOTE]
>
>새 언어는 AEM에서 인식하는 언어 중 하나여야 합니다. 즉, 아래 노드로 사용할 수 있어야 합니다 `/libs/wcm/core/resources/languages`.
