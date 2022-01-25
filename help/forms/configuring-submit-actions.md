---
title: 적응형 양식에 대한 제출 작업을 구성하는 방법
description: 적응형 양식은 여러 제출 작업을 제공합니다. 제출 작업은 제출 후 적응형 양식을 처리하는 방법을 정의합니다. 기본 제공 제출 작업을 사용하거나 직접 만들 수 있습니다.
exl-id: a4ebedeb-920a-4ed4-98b3-2c4aad8e5f78
source-git-commit: 895290aa0080e159549cd2de70f0e710c4a0ee34
workflow-type: tm+mt
source-wordcount: '1886'
ht-degree: 3%

---

# 적응형 양식 제출 작업 {#configuring-the-submit-action}

사용자가 을 클릭하면 제출 작업이 트리거됩니다 **[!UICONTROL 제출]** 단추를 클릭합니다. 적응형 Forms은 즉시 일부 제출 작업을 제공합니다. 즉시 사용 가능한 제출 작업 은 다음과 같습니다.

* [REST 엔드포인트에 제출](#submit-to-rest-endpoint)
* [이메일 보내기](#send-email)
* [양식 데이터 모델을 사용하여 제출](#submit-using-form-data-model)
* [AEM 워크플로우 호출](#invoke-an-aem-workflow)

다음을 수행할 수도 있습니다 [기본 제출 작업 확장](custom-submit-action-form.md) 을 눌러 고유한 제출 작업을 생성합니다.

에서 제출 작업을 구성할 수 있습니다 **[!UICONTROL 제출]** 섹션에 있는 세로 막대에서 적응형 양식 컨테이너 속성의 섹션을 참조하십시오.

![제출 작업 구성](assets/submission.png)


<!-- [!NOTE]
>
>Send PDF via Email Submit Action is applicable only to Adaptive Forms that use XFA template as form model. 

>[!NOTE]
>
>Ensure that the [AEM_Installation_Directory]\crx-quickstart\temp\datamanager\ASM folder
>exists. The directory is required to temporarily store attachments. If the directory does not exist, create it. -->

<!--

>[!CAUTION]
>
>If you  [prefill](prepopulate-adaptive-form-fields.md) a form template,  a Form Data Model or schema based Adaptive Form with XML or JSON data complaint to a schema (XML schema, JSON schema , form template, or form data model) that is data does not contain &lt;afData&gt;, &lt;afBoundData&gt;, and &lt;/afUnboundData&gt; tags, then the data of unbounded fields (Unbounded fields are Adaptive Form fields without [bindref](prepopulate-adaptive-form-fields.md) property) of the Adaptive Form is lost. 

>[!CAUTION]
>
>If you [prefill](prepopulate-adaptive-form-fields.md) a form template, a Form Data Model or schema based Adaptive Form with XML or JSON data complaint to a schema (XML schema, JSON schema, or form data model) that does not contain &lt;afData&gt;, &lt;afBoundData&gt;, and &lt;/afUnboundData&gt; tags, then the data of unbounded fields (Unbounded fields are Adaptive Form fields without [bindref](prepopulate-adaptive-form-fields.md) property) of the Adaptive Form is lost.


-->




## REST 엔드포인트에 제출 {#submit-to-rest-endpoint}

를 사용하십시오 **[!UICONTROL REST 끝점에 제출]** 작업을 수행하여 제출된 데이터를 rest URL에 게시합니다. URL은 내부(양식이 렌더링되는 서버) 또는 외부 서버일 수 있습니다.

내부 서버에 데이터를 게시하려면 리소스의 경로를 제공합니다. 데이터는 리소스의 경로를 게시합니다. 예: /content/restEndPoint. 이러한 post 요청의 경우 제출 요청의 인증 정보가 사용됩니다.

외부 서버에 데이터를 게시하려면 URL을 제공합니다. URL의 형식은 다음과 같습니다 `https://host:port/path_to_rest_end_point`. POST 요청을 익명으로 처리하도록 경로를 구성해야 합니다.

![감사 인사 페이지 매개 변수로 전달된 필드 값에 대한 매핑](assets/post-enabled-actionconfig.png)

위의 예에서는 사용자가 `textbox` 는 매개 변수를 사용하여 캡처됩니다. `param1`. 를 사용하여 캡처한 데이터를 게시하기 위한 구문 `param1` is:

`String data=request.getParameter("param1");`

마찬가지로 XML 데이터 및 첨부 파일을 게시하는 데 사용하는 매개변수는 다음과 같습니다 `dataXml` 및 `attachments`.

예를 들어, 스크립트에서 이 두 매개 변수를 사용하여 데이터를 나머지 종료 지점으로 구문 분석합니다. 다음 구문을 사용하여 데이터를 저장하고 구문 분석합니다.

`String data=request.getParameter("dataXml");`
`String att=request.getParameter("attachments");`

이 예제에서는 `data` 는 XML 데이터를 저장하고 `att` 첨부 파일 데이터를 저장합니다.

다음 **[!UICONTROL REST 엔드포인트에 제출]** 작업 제출은 양식에 입력된 데이터를 HTTP GET 요청의 일부로 구성된 확인 페이지에 제출합니다. 요청할 필드의 이름을 추가할 수 있습니다. 요청 형식은 다음과 같습니다.

`{fieldName}={request parameter name}`

아래 이미지에 표시된 대로, `param1` 및 `param2` 에서 복사한 값을 사용하여 매개 변수로 전달됩니다 **텍스트 상자** 및 **numericbox** 다음 작업에 대한 필드입니다.

![Rest 끝점 전송 작업 구성](assets/action-config.png)

다음을 수행할 수도 있습니다 **[!UICONTROL POST 요청 활성화]** 요청을 게시할 URL을 제공합니다. 양식을 호스팅하는 AEM 서버에 데이터를 제출하려면 AEM 서버의 루트 경로에 해당하는 상대 경로를 사용합니다. 예, `/content/forms/af/SampleForm.html`. 다른 서버에 데이터를 제출하려면 절대 경로를 사용합니다.

>[!NOTE]
>
>필드를 REST URL에서 매개 변수로 전달하려면 필드가 다른 패널에 배치되더라도 모든 필드에 다른 요소 이름이 있어야 합니다.

## 이메일 보내기 {#send-email}

를 사용할 수 있습니다 **[!UICONTROL 이메일 보내기]** 양식 전송 성공 시 하나 이상의 수신자에게 이메일을 전송하려면 작업을 제출하십시오. 생성된 이메일에는 양식 데이터가 사전 정의된 형식으로 포함될 수 있습니다. 예를 들어 다음 템플릿의 경우 고객 이름, 배송 주소, 상태 이름 및 우편 번호가 제출된 양식 데이터에서 검색됩니다.

    &quot;
    
    안녕하세요. ${customer_Name},
    
    다음은 기본 배송 주소로 설정됩니다.
    ${customer_Name},
    ${customer_Shipping_Address},
    ${customer_State},
    ${customer_ZIPCode}
    
    감사합니다
    WKND
    
    &quot;

>[!NOTE]
>
> * 필드가 적응형 양식의 다른 패널에 배치되더라도 모든 양식 필드에는 다른 요소 이름이 있어야 합니다.
> * AEM as a Cloud Service을 사용하려면 아웃바운드 메일을 암호화해야 합니다. 기본적으로 아웃바운드 이메일은 비활성화되어 있습니다. 이 기능을 활성화하려면 지원 티켓을 제출하십시오. [액세스 요청](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/development-guidelines.html?lang=en#sending-email).


전자 메일에 첨부 파일과 DoR(Document of Record)를 포함할 수도 있습니다. 활성화하려면 **[!UICONTROL 레코드 문서 첨부]** 옵션을 선택하면 적응형 양식을 구성하여 기록 문서(DoR)를 생성합니다. 적응형 양식 속성에서 레코드 문서를 생성하는 옵션을 활성화할 수 있습니다.



<!-- ## Send PDF via Email {#send-pdf-via-email}

The **Send PDF via Email** Submit Action sends an email with a PDF containing form data, to one or more recipients on successful submission of the form.

>[!NOTE]
>
>This Submit Action is available for XFA-based Adaptive Forms and XSD-based adaption forms that have the Document of Record template. -->

<!-- ## Invoke a forms workflow {#invoke-a-forms-workflow}

The **Submit to Forms workflow** submit option sends a data xml and file attachments (if any) to an existing Adobe LiveCycle or [!DNL AEM Forms] on JEE process.

For information about how to configure the Submit to forms workflow Submit Action, see [Submitting and processing your form data using forms workflows](submit-form-data-livecycle-process.md). -->

## 양식 데이터 모델을 사용하여 제출 {#submit-using-form-data-model}

다음 **[!UICONTROL 양식 데이터 모델을 사용하여 제출]** 제출 작업은 양식 데이터 모델의 지정된 데이터 모델 개체에 대해 제출된 적응형 양식 데이터를 해당 데이터 소스에 기록합니다. 제출 작업을 구성할 때 제출된 데이터를 해당 데이터 소스에 다시 쓸 데이터 모델 개체를 선택할 수 있습니다.

또한 양식 데이터 모델 및 레코드 문서(DoR)를 사용하여 양식 첨부 파일을 데이터 소스에 제출할 수 있습니다. 양식 데이터 모델에 대한 자세한 내용은 [[!DNL AEM Forms] 데이터 통합](data-integration.md).

<!--
## Forms Portal Submit Action {#forms-portal-submit-action}

The **Forms Portal Submit Action** option makes form data available through an [!DNL AEM Forms] portal.

For more information about the Forms Portal and Submit Action, see [Drafts and submissions component](draft-submission-component.md). -->

## AEM 워크플로우 호출 {#invoke-an-aem-workflow}

다음 **[!UICONTROL AEM 워크플로우 호출]** 제출 작업은 적응형 양식을 [AEM 워크플로우](https://experienceleague.adobe.com/docs/experience-manager-65/developing/extending-aem/extending-workflows/workflows-models.html?lang=en#extending-aem). 양식이 제출되면 연결된 워크플로우가 작성자 인스턴스에서 자동으로 시작됩니다. 데이터 파일, 첨부 파일 및 기록 문서를 워크플로우의 페이로드 위치 또는 변수에 저장할 수 있습니다. 워크플로우가 외부 데이터 저장소에 대해 표시되고 외부 데이터 저장소에 대해 구성된 경우 변수 옵션만 사용할 수 있습니다. 워크플로우 모델에 사용할 수 있는 변수 목록에서 선택할 수 있습니다. 워크플로우가 워크플로우 생성 시점이 아니라 이후 단계에서 외부 데이터 스토리지에 대해 표시된다면 필요한 변수 구성이 있는지 확인합니다.

제출 작업은 워크플로우의 페이로드 위치에 다음을 배치하거나, 워크플로우가 외부 데이터 저장소에 대해 표시된 경우 변수를 지정합니다.

* **데이터 파일**: 여기에는 적응형 양식에 전송된 데이터가 포함되어 있습니다. 를 사용할 수 있습니다 **[!UICONTROL 데이터 파일 경로]** 옵션을 사용하여 페이로드를 기준으로 파일 이름과 파일 경로를 지정합니다. 예: `/addresschange/data.xml` 경로: 라는 폴더를 만듭니다. `addresschange` 페이로드를 기준으로 하여 배치합니다. 만 지정할 수도 있습니다 `data.xml` 폴더 계층 구조를 만들지 않고 제출된 데이터만 보냅니다. 워크플로우가 외부 데이터 저장소에 대해 표시된 경우 변수 옵션을 사용하고 워크플로우 모델에 사용할 수 있는 변수 목록에서 변수를 선택합니다.

* **첨부 파일**: 를 사용할 수 있습니다 **[!UICONTROL 첨부 경로]** 적응형 양식에 업로드된 첨부 파일을 저장할 폴더 이름을 지정하는 옵션. 페이로드를 기준으로 폴더가 만들어집니다. 워크플로우가 외부 데이터 저장소에 대해 표시된 경우 변수 옵션을 사용하고 워크플로우 모델에 사용할 수 있는 변수 목록에서 변수를 선택합니다.

* **기록 문서**: 여기에는 적응형 양식에 대해 생성된 레코드 문서가 포함되어 있습니다. 를 사용할 수 있습니다 **[!UICONTROL 레코드 경로 문서]** [레코드 문서] 파일의 이름과 페이로드를 기준으로 파일 경로를 지정하는 옵션입니다. 예: `/addresschange/DoR.pdf` 경로: 라는 폴더를 만듭니다. `addresschange` 를 페이로드에 대해 관련되고, `DoR.pdf` 을 페이로드에 대해 상대적으로 설정합니다. 만 지정할 수도 있습니다 `DoR.pdf` 폴더 계층을 만들지 않고 레코드 문서만 저장하려면 워크플로우가 외부 데이터 저장소에 대해 표시된 경우 변수 옵션을 사용하고 워크플로우 모델에 사용할 수 있는 변수 목록에서 변수를 선택합니다.

를 사용하기 전에 **[!UICONTROL AEM 워크플로우 호출]** 작업 제출 에는 **[!UICONTROL AEM DS 설정 서비스]** 구성:

* **[!UICONTROL 처리 서버 URL]**: 처리 서버는 Forms 또는 AEM Workflow가 트리거되는 서버입니다. AEM 작성자 인스턴스 또는 다른 서버의 URL과 같을 수 있습니다.

* **[!UICONTROL 처리 서버 사용자 이름]**: 워크플로우 사용자의 사용자 이름

* **[!UICONTROL 처리 서버 암호]**: 워크플로우 사용자 암호

구성의 값을 설정하려면 [AEM SDK를 사용해 OSGi 구성을 생성](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/deploying/configuring-osgi.html?lang=en#generating-osgi-configurations-using-the-aem-sdk-quickstart)하고 Cloud Service 인스턴스에 [구성을 배포](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/deploy-code.html?lang=en#deployment-process)하십시오.

## 동기 또는 비동기 제출 사용 {#use-synchronous-or-asynchronous-submission}

제출 작업은 동기 또는 비동기 제출을 사용할 수 있습니다.

**동기 제출**: 일반적으로 웹 양식은 동기식으로 제출되도록 구성됩니다. 동기 제출 시 사용자가 양식을 제출하면 수신 확인 페이지, 감사 인사 페이지로 리디렉션되거나 제출 실패 시 오류 페이지가 표시됩니다. 을(를) 선택할 수 있습니다 **[!UICONTROL 비동기 제출 사용]** 사용자를 웹 페이지로 리디렉션하거나 제출 시 메시지를 표시하는 옵션입니다.

![제출 작업 구성](assets/thank-you-setting.png)

**비동기 제출**: 단일 페이지 애플리케이션과 같은 최신 웹 경험은 웹 페이지가 정적 상태로 유지되면서 백그라운드에서 클라이언트 서버 상호 작용이 발생하는 경우 큰 인기를 얻고 있습니다. 이제 다음을 통해 응용 Forms에 이 경험을 제공할 수 있습니다 [비동기 제출 구성](asynchronous-submissions-adaptive-forms.md).

## 적응형 양식의 서버측 재유효성 검사 {#server-side-revalidation-in-adaptive-form}

일반적으로 온라인 데이터 캡처 시스템에서 개발자는 일부 JavaScript 유효성 검사를 클라이언트 측에 배치하여 몇 가지 비즈니스 규칙을 적용합니다. 그러나 최신 브라우저에서 최종 사용자는 이러한 유효성 검사를 건너뛰고 웹 브라우저 개발 도구 콘솔 등의 다양한 기술을 사용하여 수동으로 제출을 수행할 수 있습니다. 이러한 기법은 적응형 Forms에도 유효합니다. Forms 개발자는 다양한 유효성 검사 논리를 만들 수 있지만, 기술적으로 최종 사용자는 이러한 유효성 검사 논리를 무시하고 잘못된 데이터를 서버에 제출할 수 있습니다. 잘못된 데이터는 양식 작성자가 적용한 비즈니스 규칙을 손상시킵니다.

서버측 유효성 검사 기능은 서버에서 적응형 양식을 디자인하는 동안 적응형 Forms 작성자가 제공한 유효성 검사를 실행하는 기능도 제공합니다. 양식 유효성 검사 측면에서 나타내는 데이터 제출 및 비즈니스 규칙 위반의 발생 가능성을 방지합니다.

### 서버에서 유효성을 검사하려면 어떻게 해야 합니까? {#what-to-validate-on-server-br}

서버에서 다시 실행되는 적응형 양식의 모든 기본(OOTB) 필드 유효성 검사는 다음과 같습니다.

* 필수
* 유효성 검사 그림 절
* 유효성 검사 표현식

### 서버측 유효성 검사 활성화 {#enabling-server-side-validation-br}

를 사용하십시오 **[!UICONTROL 서버에서 유효성 검사]** 사이드바의 적응형 양식 컨테이너 아래에 있는 현재 양식에 대한 서버측 유효성 검사를 활성화하거나 비활성화합니다.

![서버측 유효성 검사 활성화](assets/revalidate-on-server.png)

서버측 유효성 검사 활성화

최종 사용자가 이러한 유효성 검사를 무시하고 양식을 제출하면 서버에서 다시 유효성 검사를 수행합니다. 서버 끝에서 유효성 검사가 실패하면 제출 트랜잭션이 중지됩니다. 최종 사용자에게 원본 양식이 다시 표시됩니다. 캡처된 데이터와 제출된 데이터가 오류로 사용자에게 표시됩니다.

>[!NOTE]
>
>서버측 유효성 검사는 양식 모델의 유효성을 검사합니다. 유효성 검사를 위해 별도의 클라이언트 라이브러리를 만들고 동일한 클라이언트 라이브러리에서 HTML 스타일 및 DOM 조작과 같은 다른 항목과 혼합하지 않는 것이 좋습니다.

### 유효성 검사 표현식에서 사용자 지정 함수 지원 {#supporting-custom-functions-in-validation-expressions-br}

경우에 **복잡한 유효성 검사 규칙**, 정확한 유효성 검사 스크립트는 사용자 지정 함수에 있고 작성자는 필드 유효성 검사 표현식에서 이러한 사용자 지정 함수를 호출합니다. 서버측 유효성 검사를 수행하는 동안 이 사용자 지정 함수 라이브러리를 알고 사용할 수 있도록 하기 위해 양식 작성자는 아래에 AEM 클라이언트 라이브러리의 이름을 구성할 수 있습니다. **[!UICONTROL 기본]** 아래에 표시된 것처럼 적응형 양식 컨테이너 속성의 탭입니다.

![유효성 검사 표현식에서 사용자 지정 함수 지원](assets/clientlib-cat.png)

유효성 검사 표현식에서 사용자 지정 함수 지원

작성자는 적응형 양식에 따라 사용자 지정 JavaScript 라이브러리를 구성할 수 있습니다. 라이브러리에서는 jquery 및 underscore.js 타사 라이브러리에 대한 종속성이 있는 재사용 가능한 함수만 유지합니다.

## 제출 작업 시 오류 처리 {#error-handling-on-submit-action}

AEM 보안 및 강화 지침의 일부로, 400.jsp, 404.jsp 및 500.jsp와 같은 사용자 지정 오류 페이지를 구성합니다. 이러한 처리기는 양식 제출 시 400, 404 또는 500 오류가 나타날 때 호출됩니다. 이러한 오류 코드가 게시 노드에서 트리거될 때도 핸들러가 호출됩니다. 다른 HTTP 오류 코드에 대한 JSP 페이지를 만들 수도 있습니다.

XML 또는 JSON 데이터를 사용하여 양식 데이터 모델 또는 스키마 기반의 적응형 양식을 데이터가 포함되지 않은 스키마에 미리 채울 때 `<afData>`, `<afBoundData>`, 및 `</afUnboundData>` 태그를 지정하면 적응형 양식의 경계 필드 데이터가 유실됩니다. 스키마는 XML 스키마, JSON 스키마 또는 양식 데이터 모델일 수 있습니다. 경계 없는 필드는 `bindref` 속성을 사용합니다.

<!-- For more information, see [Customizing Pages shown by the Error Handler](/help/sites-developing/customizing-errorhandler-pages.md). -->
