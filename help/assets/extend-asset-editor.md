---
title: 확장된 에셋 편집기
description: 사용자 지정 구성 요소를 사용하여 자산 편집기의 기능을 확장하는 방법을 알아봅니다.
contentOwner: AG
translation-type: tm+mt
source-git-commit: c978be66702b7f032f78a1509f2a11315d1ed89f
workflow-type: tm+mt
source-wordcount: '713'
ht-degree: 0%

---


# 자산 편집기 확장 {#extending-asset-editor}

자산 편집기는 사용자가 메타데이터, 축소판, 제목 및 태그와 같은 에셋 측면을 편집할 수 있도록 자산 공유를 통해 찾은 에셋을 클릭할 때 열리는 페이지입니다.

사전 정의된 편집 구성 요소를 사용하는 편집기의 구성은 자산 편집기 페이지 [만들기 및 구성에서 다룹니다](https://helpx.adobe.com/experience-manager/6-5/assets/using/assets-finder-editor.html).

기존 편집기 구성 요소를 사용하는 것 외에도 AEM(Adobe Experience Manager) 개발자는 자체 구성 요소를 만들 수 있습니다.

## 자산 편집기 템플릿 만들기 {#creating-an-asset-editor-template}

다음 샘플 페이지가 geometrixx에 포함되어 있습니다.

* Geometrixx 샘플 페이지: `/content/geometrixx/en/press/asseteditor.html`
* 샘플 템플릿: `/apps/geometrixx/templates/asseteditor`
* 샘플 페이지 구성 요소: `/apps/geometrixx/components/asseteditor`

### Clientlib 구성 {#configuring-clientlib}

AEM Assets 구성 요소는 WCM 편집 clientlib의 확장을 사용합니다. The clientlibs are usually loaded in `init.jsp`.

기본 clientlib 로딩(코어의 경우)과 비교하여 AEM 자산 템플릿에는 다음이 `init.jsp`포함되어야 합니다.

* 템플릿에는 clientlib(대신)이 `cq.dam.edit` 포함되어야 `cq.wcm.edit`합니다.

* clientlib은 예측, 작업 및 렌즈를 렌더링할 수 있도록 비활성화된 WCM 모드(예: **게시**&#x200B;시 로드)에도 포함되어야 합니다.

대부분의 경우 기존 샘플 `init.jsp` (`/apps/geometrixx/components/asseteditor/init.jsp`)을 복사하는 것은 이러한 요구 사항을 충족해야 합니다.

### JS 작업 구성 {#configuring-js-actions}

일부 AEM 자산 구성 요소에는 에서 정의된 JS 함수가 필요합니다 `component.js`. 이 파일을 구성 요소 디렉토리에 복사하고 연결합니다.

```javascript
<script type="text/javascript" src="<%= component.getPath() %>/component.js"></script>
```

이 샘플은 이 javascript 소스를 `head.jsp`(`/apps/geometrixx/components/asseteditor/head.jsp`)에 로드합니다.

### 추가 스타일 시트 {#additional-style-sheets}

일부 AEM 자산 구성 요소는 AEM 위젯 라이브러리를 사용합니다. 컨텐츠 컨텍스트에서 제대로 렌더링하려면 추가 스타일 시트를 로드해야 합니다. 태그 작업 구성 요소에는 하나 더 필요합니다.

```css
<link href="/etc/designs/geometrixx/ui.widgets.css" rel="stylesheet" type="text/css">
```

### Geometrixx Style Sheet {#geometrixx-style-sheet}

샘플 페이지 구성 요소에서는 모든 선택기가 ( `.asseteditor` )로 `static.css` 시작되어야`/etc/designs/geometrixx/static.css`합니다. 모범 사례: 모든 `.asseteditor` 선택기를 스타일 시트로 복사하고 원하는 대로 규칙을 조정합니다.

### FormChooser: 최종 로딩에 대한 조정 리소스 {#formchooser-adjustments-for-eventually-loaded-resources}

자산 편집기는 양식 선택기를 사용하여 동일한 양식 페이지에서 자산의 URL에 양식 선택기 및 양식의 경로를 추가하면 리소스를 편집할 수 있습니다(이 경우 자산).

예:

* 일반 양식 페이지: [http://localhost:4502/content/geometrixx/en/press/asseteditor.html](http://localhost:4502/content/geometrixx/en/press/asseteditor.html)
* 양식 페이지에 로드된 자산: [http://localhost:4502/content/dam/geometrixx/icons/diamond.png.form.html/content/geometrixx/en/press/asseteditor.html](http://localhost:4502/content/dam/geometrixx/icons/diamond.png.form.html/content/geometrixx/en/press/asseteditor.html)

샘플 핸들은 `head.jsp` (`/apps/geometrixx/components/asseteditor/head.jsp`)에서 다음을 수행합니다.

* 자산이 로드되었는지 또는 일반 양식이 표시되어야 하는지 감지합니다.
* 자산이 로드되면 parsys는 일반 양식 페이지에서만 편집할 수 있으므로 WCM 모드를 비활성화합니다.
* 자산이 로드되면 양식 페이지의 자산 대신 해당 제목이 사용됩니다.

```javascript
 List<Resource> resources = FormsHelper.getFormEditResources(slingRequest);
    if (resources != null) {
        if (resources.size() == 1) {
            // single resource
            FormsHelper.setFormLoadResource(slingRequest, resources.get(0));
        } else if (resources.size() > 1) {
            // multiple resources
            // not supported by CQ 5.3
        }
    }
    Resource loadResource = (Resource) request.getAttribute("cq.form.loadresource");
    String title;
    if (loadResource != null) {
        // an asset is loaded: disable WCM
        WCMMode.DISABLED.toRequest(request);

        String path = loadResource.getPath();
        Asset asset = loadResource.adaptTo(Asset.class);
        try {
            // it might happen that the adobe xmp lib creates an array
            Object titleObj = asset.getMetadata("dc:title");
            if (titleObj instanceof Object[]) {
                Object[] titleArray = (Object[]) titleObj;
                title = (titleArray.length > 0) ? titleArray[0].toString() : "";
            } else {
                title = titleObj.toString();
            }
        }
        catch (NullPointerException e) {
            title = path.substring(path.lastIndexOf("/") + 1);
        }
    }
    else {
        title = currentPage.getTitle() == null ? currentPage.getName() : currentPage.getTitle();
    }
```

HTML 부분에서 이전 제목 세트(자산 또는 페이지 제목)를 사용합니다.

```html
<title><%= title %></title>
```

## 간단한 양식 필드 구성 요소 만들기 {#creating-a-simple-form-field-component}

이 예에서는 로드된 자산의 메타데이터를 표시하고 표시하는 구성 요소를 만드는 방법을 설명합니다.

1. 프로젝트 디렉토리에 구성 요소 폴더를 만듭니다(예: ) `/apps/geometrixx/components/samplemeta`.
1. 다음 코드 조각 `content.xml` 을 사용하여 추가합니다.

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <jcr:root xmlns:sling="https://sling.apache.org/jcr/sling/1.0" xmlns:cq="https://www.day.com/jcr/cq/1.0" xmlns:jcr="https://www.jcp.org/jcr/1.0"
       jcr:primaryType="cq:Component"
       jcr:title="Image Dimension"
       sling:resourceSuperType="foundation/components/parbase"
       allowedParents="[*/parsys]"
       componentGroup="Asset Editor"/>
   ```

1. 다음 코드 조각 `samplemeta.jsp` 을 사용하여 추가합니다.

   ```javascript
   <%--
   
     Sample metadata field comopnent
   
   --%><%@ page import="com.day.cq.dam.api.Asset,
                    java.security.AccessControlException" %><%
   %><%@include file="/libs/foundation/global.jsp"%><%
   
       String value = "";
       String name = "dam:sampleMetadata";
       boolean readOnly = false;
   
       // If the form page is requested for an asset loadResource will be the asset.
       Resource loadResource = (Resource) request.getAttribute("cq.form.loadresource");
   
       if (loadResource != null) {
   
           // Determine if the loaded asset is read only.
           Session session = slingRequest.getResourceResolver().adaptTo(Session.class);
           try {
               session.checkPermission(loadResource.getPath(), "set_property");
               readOnly = false;
           }
           catch (AccessControlException ace) {
               // checkPermission throws exception if asset is read only
               readOnly = true;
           }
           catch (RepositoryException re) {}
   
           // Get the value of the metadata.
           Asset asset = loadResource.adaptTo(Asset.class);
           try {
               value = asset.getMetadata(name).toString();
           }
           catch (NullPointerException npe) {
               // no metadata dc:description available
           }
       }
   %>
   <div class="form_row">
       <div class="form_leftcol">
           <div class="form_leftcollabel">Sample Metadata</div>
       </div>
       <div class="form_rightcol">
           <%
           if (readOnly) {
               %><c:out value="<%= value %>"/><%
           }
           else {
               %><input class="text" type="text" name="./jcr:content/metadata/<%= name %>" value="<c:out value="<%= value %>" />"><%
           }%>
       </div>
   </div>
   ```

1. 구성 요소를 사용할 수 있게 하려면 구성 요소를 편집할 수 있어야 합니다. 구성 요소를 편집 가능하도록 하려면 CRXDE Lite에서 기본 유형의 노드 `cq:editConfig` 를 추가합니다 `cq:EditConfig`. 단락을 제거하고 단일 값으로 다중 값 속성 `cq:actions` 을 추가할 수 있습니다 `DELETE`.

1. 브라우저로 이동하고 샘플 페이지(예:)에서 디자인 모드로 전환하고 단락 시스템에 대해 새 구성 요소를 활성화할 수 `asseteditor.html`있습니다.

1. 이제 **편집** 모드에서 새 구성 요소(예: **샘플 메타데이터**)를 사이드 킥에서 사용할 수 있습니다( **자산 편집기** 그룹에 있음). 구성 요소를 삽입합니다. 메타데이터를 저장하려면 메타데이터 양식에 메타데이터를 추가해야 합니다.

## 메타데이터 옵션 수정 {#modifying-metadata-options}

메타데이터 양식에서 사용할 수 있는 [네임스페이스를 수정할 수 있습니다](https://helpx.adobe.com/experience-manager/6-5/assets/using/assets-finder-editor.html).

현재 사용 가능한 메타데이터는 다음 위치에 정의되어 있습니다. `/libs/dam/options/metadata`

* 이 디렉터리 내의 첫 번째 수준에 네임스페이스가 포함되어 있습니다.
* 각 네임스페이스 내의 항목은 로컬 부품 항목의 결과와 같은 메타데이터를 나타냅니다.
* 메타데이터 내용에는 형식 및 다중 값 옵션에 대한 정보가 포함됩니다.

옵션은 다음 형식으로 덮어쓸 수 있습니다 `/apps/dam/options/metadata`.

1. 디렉토리를 다음 위치에 `/libs` 복사합니다 `/apps`.

1. 항목을 제거, 수정 또는 추가합니다.

>[!NOTE]
>
>새 네임스페이스를 추가하는 경우 저장소/CRX에 등록해야 합니다. 그렇지 않으면 메타데이터 양식을 제출하면 오류가 발생합니다.
