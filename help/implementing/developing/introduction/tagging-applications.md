---
title: AEM 애플리케이션에 태그 지정 빌드
description: 프로그래밍 방식으로 사용자 지정 AEM 애플리케이션 내에서 태그를 사용하거나 태그를 확장하십시오
exl-id: a106dce1-5d51-406a-a563-4dea83987343
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 646ca4f4a441bf1565558002dcd6f96d3e228563
workflow-type: tm+mt
source-wordcount: '717'
ht-degree: 1%

---

# AEM 애플리케이션에 태그 지정 빌드 {#building-tagging-into-aem-applications}

사용자 지정 AEM 응용 프로그램 내에서 태그를 프로그래밍 방식으로 작업하거나 태그를 확장하기 위해 이 문서에서는

* [API 태그 지정](https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/tagging/package-summary.html)

와 상호 작용하는

* [태깅 프레임워크](tagging-framework.md)

태그 지정에 대한 관련 정보:

* 콘텐츠 작성자로 콘텐츠에 태그를 지정하는 방법에 대한 자세한 내용은 [태그 사용](/help/sites-cloud/authoring/sites-console/tags.md)을 참조하세요.
* 태그 작성 및 관리 방법과 컨텐츠 태그가 적용되는 항목에 대한 관리자 관점의 태그 관리를 참조하십시오.

## 태깅 API 개요 {#overview-of-the-tagging-api}

AEM에서 [태그 지정 프레임워크](tagging-framework.md)를 구현하면 JCR API를 사용하여 태그와 태그 콘텐츠를 관리할 수 있습니다. `TagManager`은(는) `cq:tags` 문자열 배열 속성에 값으로 입력된 태그가 중복되지 않도록 하고, 존재하지 않는 태그를 가리키는 `TagID`을(를) 제거하고, 이동하거나 병합된 태그에 대해 `TagID`을(를) 업데이트합니다. `TagManager`은(는) 잘못된 변경 내용을 되돌리는 JCR 관찰 수신기를 사용합니다. 기본 클래스는 [com.day.cq.tagging](https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/tagging/package-summary.html) 패키지에 있습니다.

* `JcrTagManagerFactory` - `TagManager`의 JCR 기반 구현을 반환합니다. 태깅 API의 참조 구현입니다.
* `TagManager` - 경로 및 이름별로 태그를 확인하고 만들 수 있습니다.
* `Tag` - 태그 개체를 정의합니다.

### JCR 기반 TagManager 가져오기 {#getting-a-jcr-based-tagmanager}

`TagManager` 인스턴스를 검색하려면 JCR `Session`이(가) 있어야 하며 `getTagManager(Session)`을(를) 호출해야 합니다.

```java
@Reference
JcrTagManagerFactory jcrTagManagerFactory;

TagManager tagManager = jcrTagManagerFactory.getTagManager(session);
```

일반적인 Sling 컨텍스트에서는 `ResourceResolver`의 `TagManager`에 적용할 수도 있습니다.

```java
TagManager tagManager = resourceResolver.adaptTo(TagManager.class);
```

### Tag 개체 검색 {#retrieving-a-tag-object}

기존 태그를 확인하거나 태그를 만들어 `TagManager`을(를) 통해 `Tag`을(를) 검색할 수 있습니다.

```java
Tag tag = tagManager.resolve("my/tag"); // for existing tags

Tag tag = tagManager.createTag("my/tag"); // for new tags
```

`Tags`을(를) JCR `Nodes`에 매핑하는 JCR 기반 구현의 경우 리소스가 있는 경우(예: `/content/cq:tags/default/my/tag`) Sling의 `adaptTo` 메커니즘을 직접 사용할 수 있습니다.

```java
Tag tag = resource.adaptTo(Tag.class);
```

태그는 리소스(노드가 아님)에서만 *from*&#x200B;으로 변환할 수 있지만 태그는 노드 및 리소스 모두에서 *to*(으)로 변환할 수 있습니다.

```java
Node node = tag.adaptTo(Node.class);
Resource node = tag.adaptTo(Resource.class);
```

>[!NOTE]
>
>`Node`에서 Sling `Adaptable.adaptTo(Class)` 메서드를 구현하지 않으므로 `Node`에서 `Tag`(으)로 직접 조정할 수 없습니다.

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
>사용할 올바른 `RangeIterator`:
>
>`com.day.cq.commons.RangeIterator`

### 태그 삭제 {#deleting-tags}

```java
tagManager.deleteTag(tag);
```

### 태그 복제 {#replicating-tags}

태그가 `nt:hierarchyNode` 형식이므로 태그에 복제 서비스(`Replicator`)를 사용할 수 있습니다.

```java
replicator.replicate(session, replicationActionType, tagPath);
```

## 태그 가비지 수집기 {#the-tag-garbage-collector}

태그 가비지 수집기는 숨겨진 태그와 사용되지 않은 태그를 정리하는 백그라운드 서비스입니다. 숨겨진 태그와 사용되지 않은 태그는 `/content/cq:tags` 아래 태그이며 `cq:movedTo` 속성이 있고 콘텐츠 노드에서 사용되지 않습니다. 그들은 셀 수가 0이다. 이 지연 삭제 프로세스를 사용하면 이동 또는 병합 작업의 일부로 콘텐츠 노드(`cq:tags` 속성)를 업데이트할 필요가 없습니다. `cq:tags` 속성이 업데이트되면(예: 페이지 속성 대화 상자) `cq:tags` 속성의 참조가 자동으로 업데이트됩니다.

태그 가비지 수집기는 기본적으로 하루에 한 번 실행됩니다. 다음에서 구성할 수 있습니다.

`http://<host>:<port>/system/console/configMgr/com.day.cq.tagging.impl.TagGarbageCollector`

## 태그 검색 및 태그 목록 {#tag-search-and-tag-listing}

태그 검색 및 태그 목록은 다음과 같이 작동합니다.

* `TagID` 검색은 `cq:movedTo` 속성이 `TagID`(으)로 설정되어 `cq:movedTo` `TagID`까지 이어지는 태그를 검색합니다.
* 태그 제목 검색은 `cq:movedTo` 속성이 없는 태그만 검색합니다.

## 다른 언어로 된 태그 {#tags-in-different-languages}

`title` 태그는 다른 언어로 정의할 수 있습니다. 그런 다음 언어 구분 속성이 태그 노드에 추가됩니다. 이 속성은 프랑스어 번역의 경우 `jcr:title.<locale>` 형식(예: `jcr:title.fr`)을 갖습니다. `<locale>`은(는) 소문자 ISO 로케일 문자열이어야 하며 하이픈/대시(`-`) 대신 밑줄(`_`)을 사용해야 합니다(예: `de_ch`).

예를 들어 **Animals** 태그가 **Products** 페이지에 추가되면 `stockphotography:animals` 값이 `/content/wknd/en/products/jcr:content` 노드의 `cq:tags` 속성에 추가됩니다. 번역은 태그 노드에서 참조됩니다.

서버측 API에 지역화된 `title` 관련 메서드가 있습니다.

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

AEM에서 언어는 페이지 언어 또는 사용자 언어에서 가져올 수 있습니다.

태그 지정의 경우 지역화는 컨텍스트에 따라 달라집니다. 태그 `titles`은(는) 페이지 언어, 사용자 언어 또는 다른 언어로 표시될 수 있습니다.

### 태그 편집 대화 상자에 새 언어 추가 {#adding-a-new-language-to-the-edit-tag-dialog}

다음 절차에서는 **태그 편집** 대화 상자에 새로운 언어(예: 핀란드어)를 추가하는 방법을 설명합니다.

1. **CRXDE**&#x200B;에서 `/content/cq:tags` 노드의 다중 값 속성 `languages`을(를) 편집합니다.
1. 핀란드어 로케일을 나타내는 `fi_fi`을(를) 추가하고 변경 내용을 저장합니다.

핀란드어는 이제 **태그 지정** 콘솔에서 태그를 편집할 때 페이지 속성의 태그 대화 상자와 **태그 편집** 대화 상자에서 사용할 수 있습니다.

>[!NOTE]
>
>새 언어는 AEM에서 인식하는 언어 중 하나여야 합니다. 즉, `/libs/wcm/core/resources/languages` 아래의 노드로 사용할 수 있어야 합니다.
