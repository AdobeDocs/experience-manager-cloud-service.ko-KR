---
title: 적응형 양식에 대해 사용자 지정 제출 작업을 만드는 방법
description: 적응형 Forms에 대한 사용자 지정 제출 작업을 만들어 데이터를 rest 종단점에 제출하기 전에 제출 및 처리를 지연하고, 데이터 저장소에 저장하고, 기타 사용자 지정 기능을 수행하는 방법을 알아봅니다.
feature: Adaptive Forms
role: User
level: Intermediate
exl-id: 77131cc2-9cb1-4a00-bbc4-65b1a66e76f5
source-git-commit: 391a9482cc6ed97984693c21b41910fdd32ff25d
workflow-type: tm+mt
source-wordcount: '1745'
ht-degree: 0%

---

# 적응형 Forms에 대한 사용자 지정 제출 작업 만들기 {#writing-custom-submit-action-for-adaptive-forms}

적응형 양식은 여러 전송 작업을 즉시 사용(OOTB)할 수 있도록 제공합니다. 제출 작업은 적응형 양식을 통해 수집된 데이터에 대해 수행할 작업의 세부 사항을 지정합니다. 예를 들어 이메일에 데이터를 보낼 수 있습니다.

사용자 지정 제출 작업을 만들어 에 포함되지 않은 기능을 추가할 수 있습니다. [즉시 사용 가능한 제출 작업](configuring-submit-actions.md) 또는 단일 OOTB 제출 작업을 통해 지원되지 않습니다. 예를 들어, 워크플로우에 데이터 제출, 데이터 저장소에 데이터 저장, 양식 제출 개인에게 이메일 알림을 보내고, 단일 제출 작업을 통해 승인 및 거부를 위해 제출된 양식을 처리할 책임이 있는 사람에게 이메일을 보냅니다.

## XML 데이터 형식 {#xml-data-format}

XML 데이터는 **`jcr:data`** 요청 매개 변수. 작업 제출은 매개 변수에 액세스하여 데이터를 처리할 수 있습니다. 다음 코드는 XML 데이터의 형식을 설명합니다. 양식 모델에 바인딩된 필드가 **`afBoundData`** 섹션을 참조하십시오. 바인딩되지 않은 필드는 `afUnoundData`섹션을 참조하십시오. <!--For more information about the format of the `data.xml` file, see [Introduction to prepopulating Adaptive Form fields](prepopulate-adaptive-form-fields.md).-->

```xml
<?xml ?>
<afData>
<afUnboundData>
<data>
<field1>value</field2>
<repeatablePanel>
    <field2>value</field2>
</repeatablePanel>
<repeatablePanel>
    <field2>value</field2>
</repeatablePanel>
</data>
</afUnboundData>
<afBoundData>
<!-- xml corresponding to the Form Model /XML Schema -->
</afBoundData>
</afData>
```

### 작업 필드 {#action-fields}

제출 작업은 HTML을 사용하여 숨겨진 입력 필드를 추가할 수 있습니다 [입력](https://developer.mozilla.org/en/docs/Web/HTML/Element/Input) 태그)를 클릭하여 렌더링된 양식 HTML에 추가할 수 있습니다. 이러한 숨김 필드에는 양식 제출을 처리하는 동안 필요한 값이 포함될 수 있습니다. 양식을 제출할 때 이러한 필드 값은 제출 작업 시 사용할 수 있는 요청 매개 변수로서 다시 게시됩니다. 입력 필드를 작업 필드라고 합니다.

예를 들어 양식을 채우는 데 걸린 시간도 캡처하는 제출 작업에서 숨겨진 입력 필드를 추가할 수 있습니다 `startTime` 및 `endTime`.

스크립트는 `startTime` 및 `endTime` 양식이 렌더링될 때와 양식 제출 전에 각각 필드를 작성합니다. 제출 작업 스크립트 `post.jsp` 그런 다음 요청 매개 변수를 사용하여 이러한 필드에 액세스하고 양식을 채우는 데 필요한 총 시간을 계산할 수 있습니다.

### 파일 첨부 파일 {#file-attachments}

작업 제출은 첨부 파일 구성 요소를 사용하여 업로드하는 첨부 파일을 사용할 수도 있습니다. 제출 작업 스크립트는 sling을 사용하여 이러한 파일에 액세스할 수 있습니다 [RequestParameter API](https://sling.apache.org/apidocs/sling5/org/apache/sling/api/request/RequestParameter.html). 다음 [isFormField](https://sling.apache.org/apidocs/sling5/org/apache/sling/api/request/RequestParameter.html#isFormField()) api의 메서드는 요청 매개 변수가 파일인지 양식 필드인지를 식별하는 데 도움이 됩니다. 제출 작업에서 요청 매개 변수를 반복하여 파일 첨부 매개 변수를 식별할 수 있습니다.

다음 샘플 코드는 요청에서 첨부 파일을 식별합니다. 그런 다음 를 사용하여 데이터를 파일에 읽습니다. [API 가져오기](https://sling.apache.org/apidocs/sling5/org/apache/sling/api/request/RequestParameter.html#get()). 마지막으로 데이터를 사용하여 Document 객체를 만들어 목록에 추가합니다.

```java
RequestParameterMap requestParameterMap = slingRequest.getRequestParameterMap();
for (Map.Entry<String, RequestParameter[]> param : requestParameterMap.entrySet()) {
    RequestParameter rpm = param.getValue()[0];
    if(!rpm.isFormField()) {
        fileAttachments.add(new Document(rpm.get()));
    }
}
```

적응형 양식에 파일을 첨부할 때 서버는 적응형 양식 제출 후 첨부 파일의 유효성을 검사하고 다음과 같은 경우 오류 메시지를 반환합니다.

* 파일 첨부 파일에는 (.)로 시작하는 파일 이름이 포함됩니다 문자, \ / : 포함 * ? &quot; &lt; > | ; % $ 문자 또는 Windows 운영 체제용으로 예약된 특수 파일 이름 포함(예: ) `nul`, `prn`, `con`, `lpt`, 또는 `com`.

* 첨부 파일의 크기는 0바이트입니다.

* 첨부 파일의 형식은 [지원되는 파일 형식](https://helpx.adobe.com/document-cloud/help/supported-file-formats-fill-sign.html#main-pars_text) 섹션에 이미지 요청을 완전히 채우는 방법을 설명합니다.

### 전달 경로 및 리디렉션 URL {#forward-path-and-redirect-url}

필요한 작업을 수행한 후 Submit 서블릿은 요청을 전달 경로에 전달합니다. 작업은 setForwardPath API를 사용하여 Guide Submit 서블릿에 전달 경로를 설정합니다.

작업에서 전달 경로를 제공하지 않으면 제출 서블릿은 리디렉션 URL을 사용하여 브라우저를 리디렉션합니다. 작성자는 적응형 양식 편집 대화 상자에서 감사 인사 페이지 구성을 사용하여 리디렉션 URL을 구성합니다. 또한 Guide Submit 서블릿에서 Submit Action 또는 setRedirectUrl API를 통해 리디렉션 URL을 구성할 수 있습니다. 안내서 제출 서블릿에서 setRedirectParameters API를 사용하여 리디렉션 URL에 전송되는 요청 매개 변수를 구성할 수도 있습니다.

>[!NOTE]
>
>작성자가 리디렉션 URL(감사 페이지 구성 사용)을 제공합니다. [OOTB 제출 작업](configuring-submit-actions.md) 리디렉션 URL 을 사용하여 전달 경로가 참조하는 리소스에서 브라우저를 리디렉션합니다.
>
>요청을 리소스 또는 서블릿에 전달하는 사용자 지정 제출 작업을 작성할 수 있습니다. Adobe은 전달 경로에 대해 리소스 처리를 수행하는 스크립트가 처리가 완료되면 요청을 리디렉션 URL로 리디렉션하는 것을 권장합니다.

## 제출 동작 {#submit-action}

제출 작업은 다음을 포함하는 sling:Folder입니다.

* **addfields.jsp**: 이 스크립트는 변환 중에 HTML 파일에 추가되는 작업 필드를 제공합니다. 이 스크립트를 사용하여 post.POST.jsp 스크립트에서 전송하는 동안 필요한 숨겨진 입력 매개 변수를 추가합니다.
* **dialog.xml**: 이 스크립트는 CQ 구성 요소 대화 상자와 유사합니다. 작성자가 사용자 지정하는 구성 정보를 제공합니다. 제출 작업을 선택하면 적응형 양식 편집 대화 상자의 제출 작업 탭에 필드가 표시됩니다.
* **post.POST.jsp**: 제출 서블릿은 제출한 데이터와 이전 섹션의 추가 데이터를 사용하여 이 스크립트를 호출합니다. 이 페이지에서 작업을 실행하는 것에 대한 언급은 post.POST.jsp 스크립트를 실행하는 것을 의미합니다. 적응형 양식 편집 대화 상자에 표시할 적응형 Forms에 제출 작업을 등록하려면 이러한 속성을 sling에 추가합니다:Folder:

   * **guideComponentType** 유형 및 값 **fd/af/components/guidesubmittype**
   * **guideDataModel** Submit 작업을 적용할 수 있는 적응형 양식의 유형을 지정하는 문자열 유형 <!--**xfa** is supported for XFA-based Adaptive Forms while -->**xsd** 은 XSD 기반 응용 Forms에 대해 지원됩니다. **기본** XDP 또는 XSD를 사용하지 않는 응용 Forms에 대해 이 지원됩니다. 여러 유형의 적응형 Forms에 작업을 표시하려면 해당 문자열을 추가합니다. 각 문자열을 쉼표로 구분합니다. 예를 들어 작업을 <!--XFA- and -->XSD 기반 응용 Forms에서 값을 <!--**xfa** and--> **xsd**.

   * **jcr:description** 유형 String. 이 속성의 값은 적응형 양식 편집 대화 상자의 작업 제출 탭에 있는 제출 작업 목록에 표시됩니다. OOTB 작업은 CRX 저장소의 위치에 있습니다 **/libs/fd/af/components/guidesubmittype**.

   * **submitService** 유형 String. 자세한 내용은 [사용자 지정 작업에 대한 적응형 양식 제출 예약](#schedule-adaptive-form-submission).

## 사용자 지정 제출 작업 만들기 {#creating-a-custom-submit-action}

다음 단계를 수행하여 CRX 저장소에 데이터를 저장한 다음 이메일을 보내는 사용자 지정 제출 작업을 만듭니다. 적응형 양식에는 CRX 저장소에 데이터를 저장하는 OOTB 제출 작업 저장소 컨텐츠(더 이상 사용되지 않음)가 포함되어 있습니다. 또한 AEM에서는 [메일](https://www.adobe.io/experience-manager/reference-materials/6-5/javadoc/com/day/cq/mailer/package-summary.html) 이메일을 전송하는 데 사용할 수 있는 API입니다. Mail API를 사용하기 전에 시스템 콘솔을 통해 Day CQ Mail 서비스를 구성합니다. 컨텐츠 저장(더 이상 사용되지 않음) 작업을 다시 사용하여 데이터를 저장소에 저장할 수 있습니다. 컨텐츠 저장(더 이상 사용되지 않음) 작업은 CRX 저장소의 /libs/fd/af/components/guidesubmittype/store 위치에서 사용할 수 있습니다.

1. URL https://에서 CRXDE Lite에 로그인합니다.&lt;server>:&lt;port>/crx/de/index.jsp /apps/custom_submit_action 폴더에 sling:Folder 및 name store_and_mail 속성을 사용하여 노드를 만듭니다. custom_submit_action 폴더가 아직 없는 경우 만듭니다.

   ![sling:Folder 속성을 사용하여 노드를 만드는 방법을 설명하는 스크린샷입니다.](assets/step1.png)

1. **필수 구성 필드를 제공합니다.**

   저장 작업에 필요한 구성을 추가합니다. 를 복사합니다. **cq:dialog** /libs/fd/af/components/guidesubmittype/store에서 /apps/custom_submit_action/store_and_email의 작업 폴더로 저장 작업의 노드입니다.

   ![작업 폴더에 대화 상자 노드를 복사하는 스크린샷입니다](assets/step2.png)

1. **작성자에게 이메일 구성을 묻는 메시지를 표시하는 구성 필드를 제공합니다.**

   적응형 양식도 사용자에게 이메일을 보내는 이메일 작업을 제공합니다. 요구 사항에 따라 이 작업을 사용자 지정합니다. /libs/fd/af/components/guidesubmittype/email/dialog로 이동합니다. cq:dialog 노드 내의 노드를 제출 작업의 cq:dialog 노드(/apps/custom_submit_action/store_and_email/dialog)에 복사합니다.

   ![이메일 작업 사용자 지정](assets/step3.png)

1. **해당 작업을 적응형 양식 편집 대화 상자에서 사용할 수 있도록 합니다.**

   store_and_email 노드에 다음 속성을 추가합니다.

   * **guideComponentType** 유형 **문자열** 및 값 **fd/af/components/guidesubmittype**

   * **guideDataModel** 유형 **문자열** 및 값 **<!--xfa, -->xsd, 기본**

   * **jcr:description** 유형 **문자열** 및 값 **저장 및 이메일 작업**

   * **submitService** 유형 **문자열** 및 값 **저장 및 이메일**. 자세한 내용은 [사용자 지정 작업에 대한 적응형 양식 제출 예약](#schedule-adaptive-form-submission).

1. 적응형 양식을 엽니다. 을(를) 클릭합니다. **편집** 다음 단추 **시작** 열다 **편집** 적응형 양식 컨테이너의 대화 상자. 새 작업은 **작업 제출** 탭. 선택 **저장 및 이메일 작업** 대화 상자 노드에 추가된 구성을 표시합니다.

   ![작업 구성 제출 대화 상자](assets/store_and_email_submit_action_dialog.jpg)

1. **작업을 사용하여 작업을 완료합니다.**

   post.POST.jsp 스크립트를 작업에 추가합니다. (/apps/custom_submit_action/store_and_mail/).

   OOTB 저장소 작업(post.POST.jsp 스크립트)을 실행합니다. 를 사용하십시오 [FormsHelper.runAction](https://www.adobe.io/experience-manager/reference-materials/6-5/javadoc/com/day/cq/wcm/foundation/forms/FormsHelper.html#runAction-java.lang.String-java.lang.String-org.apache.sling.api.resource.Resource-org.apache.sling.api.SlingHttpServletRequest-org.apache.sling.api.SlingHttpServletResponse-)(java.lang.String, java.lang.String, org.apache.sling.api.resource.Resource, org.apache.sling.api.SlingHttpServletRequest, org.apache.sling.api.SlingHttpServletResponse) CQ가 코드에서 제공하는 API입니다. JSP 파일에 다음 코드를 추가합니다.

   `FormsHelper.runAction("/libs/fd/af/components/guidesubmittype/store", "post", resource, slingRequest, slingResponse);`

   이메일을 보내려면 코드에서 구성에서 수신자의 이메일 주소를 읽습니다. 작업 스크립트에서 구성 값을 가져오려면 다음 코드를 사용하여 현재 리소스의 속성을 읽습니다. 마찬가지로 다른 구성 파일을 읽을 수 있습니다.

   `ValueMap properties = ResourceUtil.getValueMap(resource);`

   `String mailTo = properties.get("mailTo");`

   마지막으로 CQ Mail API를 사용하여 이메일을 보냅니다. 를 사용하십시오 [SimpleEmail](https://commons.apache.org/proper/commons-email/apidocs/org/apache/commons/mail/SimpleEmail.html) 아래 표시된 대로 이메일 개체를 만드는 클래스입니다.

   >[!NOTE]
   >
   >JSP 파일의 이름이 post.POST.jsp인지 확인합니다.

   ```java
   <%@include file="/libs/fd/af/components/guidesglobal.jsp" %>
   <%@page import="com.day.cq.wcm.foundation.forms.FormsHelper,
          org.apache.sling.api.resource.ResourceUtil,
          org.apache.sling.api.resource.ValueMap,
                   com.day.cq.mailer.MessageGatewayService,
     com.day.cq.mailer.MessageGateway,
     org.apache.commons.mail.Email,
                   org.apache.commons.mail.SimpleEmail" %>
   <%@taglib prefix="sling"
                   uri="https://sling.apache.org/taglibs/sling/1.0" %>
   <%@taglib prefix="cq"
                   uri="https://www.day.com/taglibs/cq/1.0"
   %>
   <cq:defineObjects/>
   <sling:defineObjects/>
   <%
           String storeContent =
                       "/libs/fd/af/components/guidesubmittype/store";
           FormsHelper.runAction(storeContent, "post", resource,
                                   slingRequest, slingResponse);
    ValueMap props = ResourceUtil.getValueMap(resource);
    Email email = new SimpleEmail();
    String[] mailTo = props.get("mailto", new String[0]);
    email.setFrom((String)props.get("from"));
           for (String toAddr : mailTo) {
               email.addTo(toAddr);
      }
    email.setMsg((String)props.get("template"));
    email.setSubject((String)props.get("subject"));
    MessageGatewayService messageGatewayService =
                       sling.getService(MessageGatewayService.class);
    MessageGateway messageGateway =
                   messageGatewayService.getGateway(SimpleEmail.class);
    messageGateway.send(email);
   %>
   ```

   적응형 양식에서 작업을 선택합니다. 작업은 이메일을 전송하고 데이터를 저장합니다.

## 사용자 지정 제출 작업에 submitService 속성 사용 {#submitservice-property}

사용자 지정 제출 작업을 설정할 때, 여기에는 `submitService` 속성을 설정하면 양식은 [FormSubmitActionService](https://helpx.adobe.com/experience-manager/6-5/forms/javadocs/com/adobe/aemds/guide/service/FormSubmitActionService.html) 제출 시 다음 `FormSubmitActionService` 사용 `getServiceName` 에 대한 값을 검색하는 방법 `submitService` 속성을 사용합니다. 의 값 기준 `submitService` 등록 정보인 서비스는 적절한 제출 메서드를 호출합니다. 다음을 포함합니다 `FormSubmitActionService` 를 업로드하는 사용자 지정 번들로 [!DNL AEM Forms] server.

추가 `submitService` 문자열 유형의 속성을 `sling:Folder` 사용자 지정 제출 작업 을 사용하여 [!DNL Adobe Sign] 추가 정보. 을(를) 선택할 수 있습니다 **[!UICONTROL Adobe Sign 활성화]** 옵션 **[!UICONTROL 전자 서명]** 섹션에 대한 값을 설정한 후에만 적응형 양식 컨테이너 속성의 섹션을 `submitService` 사용자 지정 제출 작업의 속성입니다.

<!--As a result of setting an appropriate value for the `submitService` property and enabling [!DNL Adobe Sign], you can schedule the submission of an Adaptive Form to ensure that all configured signers have taken an action on the form. [!DNL Adobe Sign] Configuration Service keeps polling [!DNL Adobe Sign] server at regular intervals to verify the status of signatures. If all the signers complete signing the form, the Submit Action service is started and the form is submitted.-->


![서비스 속성 제출](assets/submit-service-property.png)

<!-- You can't do comments within comments, so I changed comment tags to <start-comment> <end-comment> -->

<!--
## Workflow for a Submit Action {#workflow-for-a-submit-action}

The flowchart depicts the workflow for a Submit Action that is triggered when you click the **[!UICONTROL Submit]** button in an Adaptive Form. The files in the File Attachment component are uploaded to the server, and the form data is updated with the URLs of the uploaded files. Within the client, the data is stored in the JSON format. The client sends an Ajax request to an internal servlet that massages the data you specified and returns it in the XML format. The client collates this data with action fields. It submits the data to the final servlet (Guide Submit servlet) through a Form Submit Action. Then, the servlet forwards the control to the Submit Action. The Submit Action can forward the request to a different sling resource or redirect the browser to another URL.

![Flowchart depicting the workflow for Submit Action](assets/diagram1.png)

### XML data format {#xml-data-format}

The XML data is sent to the servlet using the **`jcr:data`** request parameter. Submit Actions can access the parameter to process the data. The following code describes the format of the XML data. The fields that are bound to the Form model appear in the **`afBoundData`** section. Unbound fields appear in the `afUnoundData`section. For more information about the format of the `data.xml` file, see [Introduction to prepopulating Adaptive Form fields](prepopulate-adaptive-form-fields.md).

```xml
<?xml ?>
<afData>
<afUnboundData>
<data>
<field1>value</field2>
<repeatablePanel>
    <field2>value</field2>
</repeatablePanel>
<repeatablePanel>
    <field2>value</field2>
</repeatablePanel>
</data>
</afUnboundData>
<afBoundData>
<start comment> xml corresponding to the Form Model /XML Schema <end comment>
<start comment> </afBoundData> <end comment>
</afData>
```

### Action fields {#action-fields}

A Submit Action can add hidden input fields (using the HTML [input](https://developer.mozilla.org/en/docs/Web/HTML/Element/Input) tag) to the rendered form HTML. These hidden fields can contain values that it needs while processing form submission. When submitting the form, these field values are posted back as request parameters that the Submit Action can use during submission handling. The input fields are called action fields.

For example, a Submit Action that also captures the time taken to fill a form can add the hidden input fields `startTime` and `endTime`.

A script can supply the values of the `startTime` and `endTime` fields when the form renders and before form submission, respectively. The Submit Action script `post.jsp` can then access these fields using request parameters and compute the total time required to fill the form.

### File attachments {#file-attachments}

Submit Actions can also use the file attachments you upload using the File Attachment component. Submit Action scripts can access these files using the sling [RequestParameter API](https://sling.apache.org/apidocs/sling5/org/apache/sling/api/request/RequestParameter.html). The [isFormField](https://sling.apache.org/apidocs/sling5/org/apache/sling/api/request/RequestParameter.html#isFormField()) method of the API helps identify whether the request parameter is a file or a form field. You can iterate over the Request parameters in a Submit Action to identify File Attachment parameters.

The following sample code identifies the file attachments in the request. Next, it reads the data into the file using the [Get API](https://sling.apache.org/apidocs/sling5/org/apache/sling/api/request/RequestParameter.html#get()). Finally, it creates a Document object using the data and appends it to a list.

```java
RequestParameterMap requestParameterMap = slingRequest.getRequestParameterMap();
for (Map.Entry<String, RequestParameter[]> param : requestParameterMap.entrySet()) {
    RequestParameter rpm = param.getValue()[0];
    if(!rpm.isFormField()) {
        fileAttachments.add(new Document(rpm.get()));
    }
}
```

### Forward path and Redirect URL {#forward-path-and-redirect-url}

After performing the required action, the Submit servlet forwards the request to the forward path. An action uses the setForwardPath API to set the forward path in the Guide Submit servlet.

If the action doesn't provide a forward path, the Submit servlet redirects the browser using the Redirect URL. The author configures the Redirect URL using the Thank You Page configuration in the Adaptive Form Edit dialog. You can also configure the Redirect URL through the Submit Action or the setRedirectUrl API in the Guide Submit servlet. You can also configure the Request parameters sent to the Redirect URL using the setRedirectParameters API in the Guide Submit servlet.

>[!NOTE]
>
>An author provides the Redirect URL (using the Thank You Page Configuration). [OOTB Submit Actions](configuring-submit-actions.md) use the Redirect URL to redirect the browser from the resource that the forward path references.
>
>You can write a custom Submit Action that forwards a request to a resource or servlet. Adobe recommends that the script that performs resource handling for the forward path redirect the request to the Redirect URL when the processing completes.

## Submit Action {#submit-action}

A Submit Action is a sling:Folder that includes the following:

* **addfields.jsp**: This script provides the action fields that are added to the HTML file during rendition. Use this script to add hidden input parameters required during submission in the post.POST.jsp script.
* **dialog.xml**: This script is similar to the CQ Component dialog. It provides configuration information that the author customizes. The fields are displayed in the Submit Actions Tab in the Adaptive Form Edit dialog when you select the Submit Action.
* **post.POST.jsp**: The Submit servlet calls this script with the data that you submit and the additional data in the previous sections. Any mention of running an action in this page implies running the post.POST.jsp script. To register the Submit Action with the Adaptive Forms to display in the Adaptive Form Edit dialog, add these properties to the sling:Folder:

    * **guideComponentType** of type String and value **fd/af/components/guidesubmittype**
    * **guideDataModel** of type String that specifies the type of Adaptive Form for which the Submit Action is applicable. **xfa** is supported for XFA-based Adaptive Forms while **xsd** is supported for XSD-based Adaptive Forms. **basic** is supported for Adaptive Forms that do not use XDP or XSD. To display the action on multiple types of Adaptive Forms, add the corresponding strings. Separate each string by a comma. For example, to make an action visible on XFA- and XSD-based Adaptive Forms, specify the values **xfa** and **xsd** respectively.

    * **jcr:description** of type String. The value of this property is displayed in the Submit Action list in the Submit Actions Tab of the Adaptive Form Edit dialog. The OOTB actions are present in the CRX repository at the location **/libs/fd/af/components/guidesubmittype**.

## Creating a custom Submit Action {#creating-a-custom-submit-action}

Perform the following steps to create a custom Submit Action that saves the data in the CRX repository and then sends you an email. The Adaptive Form contains the OOTB Submit Action Store Content (deprecated) that saves the data in the CRX repository. In addition, CQ provides a [Mail](https://www.adobe.io/experience-manager/reference-materials/6-5/javadoc/com/day/cq/mailer/package-summary.html) API that can be used to send emails. Before using the Mail API, configure the Day CQ Mail service through the system console. You can reuse the Store Content (deprecated) action to store the data in the repository. The Store Content (deprecated) action is available at the location /libs/fd/af/components/guidesubmittype/store in the CRX repository.

1. Log in to CRXDE Lite at the URL https://&lt;server&gt;:&lt;port&gt;/crx/de/index.jsp. Create a node with the property sling:Folder and name store_and_mail in the /apps/custom_submit_action folder. Create the custom_submit_action folder if it doesn't exist already.

   ![Screenshot depicting the creation of a node with the property sling:Folder](assets/step1.png)

1. **Provide the mandatory configuration fields.**

   Add the configuration the Store action requires. Copy the **cq:dialog** node of the Store action from /libs/fd/af/components/guidesubmittype/store to the action folder at /apps/custom_submit_action/store_and_email.

   ![Screenshot showing the copying of the dialog node to the action folder](assets/step2.png)

1. **Provide configuration fields to prompt the author for email configuration.**

   The Adaptive Form also provides an Email action that sends emails to users. Customize this action based on your requirements. Navigate to /libs/fd/af/components/guidesubmittype/email/dialog. Copy the nodes within the cq:dialog node to cq:dialog node of your Submit Action (/apps/custom_submit_action/store_and_email/dialog).

   ![Customizing the email action](assets/step3.png)

1. **Make the action available in the Adaptive Form Edit dialog.**

   Add the following properties in the store_and_email node:

    * **guideComponentType** of type **String** and value **fd/af/components/guidesubmittype**

    * **guideDataModel** of type **String** and value **xfa, xsd, basic**

    * **jcr:description** of type **String** and value **Store and Email Action**

1. Open any Adaptive Form. Click the **Edit** button next to **Start** to open the **Edit** dialog of the Adaptive Form container. The new action is displayed in the **Submit Actions** Tab. Selecting the **Store and Email Action** displays the configuration added in the dialog node.

   ![Submit Action configuration dialog](assets/store_and_email_submit_action_dialog.jpg)

1. **Use the action to complete a task.**

   Add the post.POST.jsp script to your action. (/apps/custom_submit_action/store_and_mail/).

   Run the OOTB Store action (post.POST.jsp script). Use the [FormsHelper.runAction](https://www.adobe.io/experience-manager/reference-materials/6-5/javadoc/com/day/cq/wcm/foundation/forms/FormsHelper.html#runAction-java.lang.String-java.lang.String-org.apache.sling.api.resource.Resource-org.apache.sling.api.SlingHttpServletRequest-org.apache.sling.api.SlingHttpServletResponse-(java.lang.String, java.lang.String, org.apache.sling.api.resource.Resource, org.apache.sling.api.SlingHttpServletRequest, org.apache.sling.api.SlingHttpServletResponse)) API that CQ provides in your code to run the Store action. Add the following code in your JSP file:

   `FormsHelper.runAction("/libs/fd/af/components/guidesubmittype/store", "post", resource, slingRequest, slingResponse);`

   To send the email, the code reads the recipient's email address from the configuration. To fetch the configuration value in the action's script, read the properties of the current resource using the following code. Similarly you can read the other configuration files.

   `ValueMap properties = ResourceUtil.getValueMap(resource);`

   `String mailTo = properties.get("mailTo");`

   Finally, use the CQ Mail API to send the email. Use the [SimpleEmail](https://commons.apache.org/proper/commons-email/apidocs/org/apache/commons/mail/SimpleEmail.html) class to create the Email Object as depicted below:

   >[!NOTE]
   >
   >Ensure that the JSP file has the name post.POST.jsp.

   ```java
   <%@include file="/libs/fd/af/components/guidesglobal.jsp" %>
   <%@page import="com.day.cq.wcm.foundation.forms.FormsHelper,
          org.apache.sling.api.resource.ResourceUtil,
          org.apache.sling.api.resource.ValueMap,
                   com.day.cq.mailer.MessageGatewayService,
     com.day.cq.mailer.MessageGateway,
     org.apache.commons.mail.Email,
                   org.apache.commons.mail.SimpleEmail" %>
   <%@taglib prefix="sling"
                   uri="https://sling.apache.org/taglibs/sling/1.0" %>
   <%@taglib prefix="cq"
                   uri="https://www.day.com/taglibs/cq/1.0"
   %>
   <cq:defineObjects/>
   <sling:defineObjects/>
   <%
           String storeContent =
                       "/libs/fd/af/components/guidesubmittype/store";
           FormsHelper.runAction(storeContent, "post", resource,
                                   slingRequest, slingResponse);
    ValueMap props = ResourceUtil.getValueMap(resource);
    Email email = new SimpleEmail();
    String[] mailTo = props.get("mailto", new String[0]);
    email.setFrom((String)props.get("from"));
           for (String toAddr : mailTo) {
               email.addTo(toAddr);
      }
    email.setMsg((String)props.get("template"));
    email.setSubject((String)props.get("subject"));
    MessageGatewayService messageGatewayService =
                       sling.getService(MessageGatewayService.class);
    MessageGateway messageGateway =
                   messageGatewayService.getGateway(SimpleEmail.class);
    messageGateway.send(email);
   %>
   ```

   Select the action in the Adaptive Form. The action sends an email and stores the data. 

-->
