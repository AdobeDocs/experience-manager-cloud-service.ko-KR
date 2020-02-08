---
title: Adobe Experience Manager Assets에서 검색 옵션 및 기능 확장
description: 자산의 검색 기능을 확장합니다.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 991d4900862c92684ed92c1afc081f3e2d76c7ff

---


# 자산 검색 확장 {#extend-assets-search}

AEM(Adobe Experience Manager) 자산 검색 기능을 확장할 수 있습니다. 기본적으로 AEM Assets는 문자열별로 자산을 검색합니다.

검색은 QueryBuilder 인터페이스를 통해 수행되므로 여러 조건자로 검색을 사용자 정의할 수 있습니다. 다음 디렉토리에 기본 예측 세트를 오버레이할 수 있습니다. `/apps/dam/content/search/searchpanel/facets`Adobe

AEM 자산 관리 패널에 탭을 추가할 수도 있습니다.

## 오버레이 {#overlay}

미리 구성된 조건자를 오버레이하려면 `facets` 노드를 `/libs/dam/content/search/searchpanel` 에서 `/apps/dam/content/search/searchpanel/` 복사하거나 검색 패널 구성에서 다른 `facetURL` 속성을 지정합니다(기본값은 다음 `/libs/dam/content/search/searchpanel/facets.overlay.infinity.json`위치).

>[!NOTE]
>
>기본적으로 아래 디렉토리 구조가 `/apps` 없으므로 만들어야 합니다. 노드 유형이 아래에서 해당 유형과 일치하는지 `/libs`확인합니다.

### 탭 추가 {#add-tabs}

AEM 자산 관리에서 탭을 구성하여 추가 검색 탭을 추가할 수 있습니다. 추가 탭을 만들려면

1. 폴더 구조가 아직 `/apps/wcm/core/content/damadmin/tabs,`없는 경우 폴더 구조를 만들고 `tabs` 노드를 복사한 다음 `/libs/wcm/core/content/damadmin` 붙여넣습니다.
1. 원하는 대로 두 번째 탭을 만들고 구성합니다.

   >[!NOTE]
   >
   >두 번째 `siteadminsearchpanel`서식을 만들 때는 양식 충돌을 방지하기 위해 `id` 속성을 설정해야 합니다.

### 사용자 정의 설명 만들기 {#create-custom-predicates}

AEM Assets에는 자산 공유 페이지를 사용자 지정하는 데 사용할 수 있는 사전 정의된 예측 세트가 포함되어 있습니다.
<!-- In addition to using pre-existing predicates, AEM developers can also create their own predicates using the [Query Builder API](/help/sites-developing/querybuilder-api.md). -->

사용자 정의 조건자를 만들려면 위젯 프레임워크에 대한 기본적인 [지식이](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html)필요합니다.

가장 좋은 방법은 기존 술어를 복사하고 조정하는 것입니다. 샘플 예측자는 **/libs/cq/search/components/predicates에**&#x200B;있습니다.

#### 예:간단한 속성 설명 만들기 {#example-build-a-simple-property-predicate}

속성 조건자를 빌드하려면

1. 프로젝트 디렉토리에 구성 요소 폴더를 만듭니다(예: **/apps/geometrixx/components/titledicate**).
1. content.xml **추가**:

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <jcr:root xmlns:sling="https://sling.apache.org/jcr/sling/1.0" xmlns:cq="https://www.day.com/jcr/cq/1.0" xmlns:jcr="https://www.jcp.org/jcr/1.0"
       jcr:primaryType="cq:Component"
       jcr:title="Title Predicate"
       sling:resourceSuperType="foundation/components/parbase"
       allowedParents="[*/parsys]"
       componentGroup="Search"/>
   ```

1. 페이지 URL에 `titlepredicate.jsp`.

   ```xml
   <%--
   
     Sample title predicate component
   
   --%><%@ page import="java.util.Calendar" %><%
   %><%@include file="/libs/foundation/global.jsp"%><%
   
       // A unique id is necessary in case this predicate is inserted multiple times on the same page
       String elemId = "cq-predicate-" +  Long.toString(Calendar.getInstance().getTimeInMillis());
   
   %><div class="predicatebox">
   
       <div class="title">Title</div>
   
       <%-- The wrapper for the form elements. All items will be append to this wrapper. --%>
       <div id="<%= elemId %>" class="content"></div>
   
   </div><script type="text/javascript">
   
       CQ.Ext.onLoad(function() {
   
           var predicateName = "property";
           var propertyName = "jcr:content/metadata/dc:title";
           var elemId = "<%= elemId %>";
   
           // Get the page wide available QueryBuilder.
           var qb = CQ.search.Util.getQueryBuilder();
   
           // createId adds a counter to the predicate name - useful in case this predicate
           // is inserted multiple times on the same page.
           var id = qb.createId(predicateName);
   
           // Hidden field that defines the property to search for; in our case this
           // is the "dc:title" metadata. The name "property" (or "1_property", "2_property" etc.)
           // indicates the server to use the property predicate
           // (com.day.cq.search.eval.JcrPropertyPredicateEvaluator).
           qb.addField({
               "xtype": "hidden",
               "renderTo": elemId,
               "name": id,
               "value": propertyName
           });
   
           // The visible text field. The name has to be like the one of the hidden field above
           // plus the ".value" suffix.
           qb.addField({
               "xtype": "textfield",
               "renderTo": elemId,
               "name": id + ".value"
           });
   
           // Depending on the predicate additional parameters allow to configure the
           // predicate. Here we add an operation parameter to create a "like" query.
           // Again note the name set to the id and a suffix.
           qb.addField({
               "xtype": "hidden",
               "renderTo": elemId,
               "name": id + ".operation",
               "value": "like"
           });
       });
   </script>
   ```

1. 구성 요소를 사용 가능하게 하려면 구성 요소를 편집할 수 있어야 합니다. 구성 요소를 편집 가능하도록 하려면 CRXDE에서 기본 유형 **cq:EditConfig** 노드를 **추가합니다**. 단락을 제거하려면 단일 DELETE 값으로 **cq:actions** 다중 값 속성을 **추가합니다**.
1. 브라우저로 이동하고 샘플 페이지(예: **press.html**)에서 디자인 모드로 전환하고 설명 단락 시스템(예: **왼쪽**)에 대한 새 구성 요소를 활성화합니다.

1. 편집 **모드에서** 이제 새 구성 요소를 사이드킥에서 사용할 수 있습니다(검색 그룹에 **있음** ). 조건자 열에 구성 요소를 **삽입하고** 검색어(예: 다이아몬드)를 **입력하고** 확대경을 클릭하여 검색을 시작합니다.

   >[!NOTE]
   >
   >검색할 때는 올바른 대/소문자를 포함하여 정확하게 용어를 입력해야 합니다.

#### 예:간단한 그룹 설명 작성 {#example-build-a-simple-group-predicate}

그룹 조건자를 만들려면

1. 프로젝트 디렉토리에 구성 요소 폴더를 만듭니다(예: **/apps/geometrixx/components/picspredicate).**
1. content.xml **추가**:

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <jcr:root xmlns:sling="https://sling.apache.org/jcr/sling/1.0" xmlns:cq="https://www.day.com/jcr/cq/1.0" xmlns:jcr="https://www.jcp.org/jcr/1.0"
       jcr:primaryType="cq:Component"
       jcr:title="Image Formats"
       sling:resourceSuperType="foundation/components/parbase"
       allowedParents="[*/parsys]"
       componentGroup="Search"/>
   ```

1. title **조건자.jsp**&#x200B;추가:

   ```xml
   <%--
   
     Sample group predicate component
   
   --%><%@ page import="java.util.Calendar" %><%
   %><%@include file="/libs/foundation/global.jsp"%><%
   
       // A unique id is necessary in case this predicate is inserted multiple times on the same page.
       String elemId = "cq-predicate-" +  Long.toString(Calendar.getInstance().getTimeInMillis());
   
   %><div class="predicatebox">
   
       <div class="title">Image Formats</div>
   
       <%-- The wrapper for the form elements. All items will be append to this wrapper. --%>
       <div id="<%= elemId %>" class="content"></div>
   
   </div><script type="text/javascript">
   
       CQ.Ext.onLoad(function() {
   
           var predicateName = "property";
           var propertyName = "jcr:content/metadata/dc:format";
           var elemId = "<%= elemId %>";
   
           // Get the page wide available QueryBuilder.
           var qb = CQ.search.Util.getQueryBuilder();
   
           // Create a unique group ID; will return e.g. "1_group".
           var groupId = qb.createGroupId();
   
           // Hidden field that defines the property to search for  - in our case "dc:format" -
           // and declares the group of predicates. "property" in the name ("1_group.property")
           // indicates to the server to use the "property predicate"
           // (com.day.cq.search.eval.JcrPropertyPredicateEvaluator).
           qb.addField({
               "xtype": "hidden",
               "renderTo": "<%= elemId %>",
               "name": groupId + "." + predicateName, // 1_group.property
               "value": propertyName
           });
   
           // Declare to combine the multiple values using OR.
           qb.add(new CQ.Ext.form.Hidden({
               "name": groupId + ".p.or",  // 1_group.p.or
               "value": "true"
           }));
   
           // The options
           var options = [
               { "label":"JPEG", "value":"image/jpeg"},
               { "label":"PNG",  "value":"image/png" },
               { "label":"GIF",  "value":"image/gif" }
           ];
   
           // Build a checkbox for each option.
           for (var i = 0; i < options.length; i++) {
               qb.addField({
                   "xtype": "checkbox",
                   "renderTo": "<%= elemId %>",
                   // 1_group.property.0_value, 1_group.property.1_value etc.
                   "name": groupId + "." +  predicateName + "." + i + "_value",
                   "inputValue": options[i].value,
                   "boxLabel": options[i].label,
                   "listeners": {
                       "check": function() {
                           // Submit the search form when checking/unchecking a checkbox.
                           qb.submit();
                       }
                   }
               });
           }
       });
   ```

1. 구성 요소를 사용 가능하게 하려면 구성 요소를 편집할 수 있어야 합니다. 구성 요소를 편집 가능하도록 하려면 CRXDE에서 기본 유형 **cq:EditConfig** 노드를 **추가합니다**. 단락을 제거하려면 단일 DELETE 값으로 **cq:actions** 다중 값 속성을 **추가합니다**.
1. 브라우저로 이동하고 샘플 페이지(예: **press.html**)에서 디자인 모드로 전환하고 설명 단락 시스템(예: **왼쪽**)에 대한 새 구성 요소를 활성화합니다.
1. 편집 **모드에서** 이제 새 구성 요소를 사이드킥에서 사용할 수 있습니다(검색 그룹에 **있음** ). 조건자 열에 구성 요소를 **삽입합니다** .

### 설치된 설명 위젯 {#installed-predicate-widgets}

다음 예제는 미리 구성된 ExtJS 위젯으로 사용할 수 있습니다.

#### 전체 텍스트 설명 {#fulltextpredicate}

<table>
 <tbody>
  <tr>
   <td><strong>속성<br /> </strong></td>
   <td><strong>유형</strong></td>
   <td><strong>설명</strong></td>
  </tr>
  <tr>
   <td>조건자 이름</td>
   <td>문자열</td>
   <td>조건자의 이름입니다. 기본값은 'fulltext'입니다.</td>
  </tr>
  <tr>
   <td>searchCallback</td>
   <td>함수</td>
   <td>이벤트 'keyup'에서 검색을 트리거하기 위한 콜백입니다. 기본값은 'CQ.wcm.SiteAdmin.doSearch'입니다.</td>
  </tr>
 </tbody>
</table>

#### 속성 설명 {#propertypredicate}

<table>
 <tbody>
  <tr>
   <td><strong>속성<br /> </strong></td>
   <td><strong>유형</strong></td>
   <td><strong>설명</strong></td>
  </tr>
  <tr>
   <td>조건자 이름</td>
   <td>문자열</td>
   <td>조건자의 이름입니다. 기본값은 'property'입니다.</td>
  </tr>
  <tr>
   <td>propertyName</td>
   <td>문자열 </td>
   <td>JCR 속성의 이름입니다. 기본값은 'jcr:title'입니다.</td>
  </tr>
  <tr>
   <td>defaultValue<br /> </td>
   <td>String<br /> </td>
   <td>프리플라이트 기본값.<br /> </td>
  </tr>
 </tbody>
</table>

#### 경로 설명 {#pathpredicate}

<table>
 <tbody>
  <tr>
   <td><strong>속성<br /> </strong></td>
   <td><strong>유형</strong></td>
   <td><strong>설명</strong></td>
  </tr>
  <tr>
   <td>조건자 이름</td>
   <td>문자열</td>
   <td>조건자의 이름입니다. 기본값은 'path'입니다.</td>
  </tr>
  <tr>
   <td>rootPath</td>
   <td>문자열 </td>
   <td>술어의 루트 경로입니다. 기본값은 '/content/dam'입니다.</td>
  </tr>
  <tr>
   <td>pathFieldPredicateName</td>
   <td>문자열</td>
   <td>기본값은 '폴더'입니다.</td>
  </tr>
  <tr>
   <td>showFlatOption</td>
   <td>부울</td>
   <td>확인란 '하위 폴더에서 검색'을 표시하는 플래그. 기본값은 true입니다.</td>
  </tr>
 </tbody>
</table>

#### 날짜 설명 {#datepredicate}

<table>
 <tbody>
  <tr>
   <td><strong>속성<br /> </strong></td>
   <td><strong>유형</strong></td>
   <td><strong>설명</strong></td>
  </tr>
  <tr>
   <td>조건자 이름</td>
   <td>문자열</td>
   <td>조건자의 이름입니다. 기본값은 '날짜 범위'입니다.</td>
  </tr>
  <tr>
   <td>propertyname</td>
   <td>문자열</td>
   <td>JCR 속성의 이름입니다. 기본값은 'jcr:content/jcr:lastModified'입니다.</td>
  </tr>
  <tr>
   <td>defaultValue </td>
   <td>문자열 </td>
   <td>프리플라이트 기본값 </td>
  </tr>
 </tbody>
</table>

#### 옵션설명 {#optionspredicate}

<table>
 <tbody>
  <tr>
   <td><strong>속성<br /> </strong></td>
   <td><strong>유형</strong></td>
   <td><strong>설명</strong></td>
  </tr>
  <tr>
   <td>제목 </td>
   <td>문자열 </td>
   <td>추가 상위 제목 추가 </td>
  </tr>
  <tr>
   <td>조건자 이름</td>
   <td>문자열</td>
   <td>조건자의 이름입니다. 기본값은 '날짜 범위'입니다.</td>
  </tr>
  <tr>
   <td>propertyname</td>
   <td>문자열</td>
   <td>JCR 속성의 이름입니다. 기본값은 'jcr:content/metadata/cq:tags'입니다.</td>
  </tr>
  <tr>
   <td>축소</td>
   <td>문자열</td>
   <td>축소 수준. 기본값은 'level1'입니다.</td>
  </tr>
  <tr>
   <td>triggerSearch</td>
   <td>부울 </td>
   <td>확인 시 검색을 트리거하는 플래그. 기본값은 false입니다.</td>
  </tr>
  <tr>
   <td>searchCallback</td>
   <td>함수</td>
   <td>검색을 트리거하기 위한 콜백입니다. 기본값은 'CQ.wcm.SiteAdmin.doSearch'입니다.</td>
  </tr>
  <tr>
   <td>searchTimeoutTime</td>
   <td>번호</td>
   <td>searchCallback이 실행되기 전에 시간이 초과되었습니다. 기본값은 800ms입니다.</td>
  </tr>
 </tbody>
</table>
