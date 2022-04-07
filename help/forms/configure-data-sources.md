---
title: 데이터 소스를 구성하는 방법
description: Experience Manager Forms 데이터 통합을 사용하면 서로 다른 데이터 소스를 구성하고 연결할 수 있습니다. RESTful 웹 서비스, SOAP 기반 웹 서비스 및 OData 서비스를 데이터 소스로 구성하고 양식 데이터 모델을 만드는 방법을 알아봅니다.
feature: Form Data Model
role: User, Developer
level: Beginner
exl-id: cb77a840-d705-4406-a94d-c85a6efc8f5d
source-git-commit: b6c654f5456e1a7778b453837f04cbed32a82a77
workflow-type: tm+mt
source-wordcount: '1536'
ht-degree: 3%

---

# 데이터 소스 구성 {#configure-data-sources}

![데이터 통합](do-not-localize/data-integeration.png)

[!DNL Experience Manager Forms] 데이터 통합을 사용하면 서로 다른 데이터 소스를 구성하고 연결할 수 있습니다. 기본적으로 지원되는 유형은 다음과 같습니다. 그러나 사용자 지정이 거의 없는 경우에도 다른 데이터 소스를 통합할 수 있습니다.

<!-- * Relational databases - MySQL, [!DNL Microsoft SQL Server], [!DNL IBM DB2], and [!DNL Oracle RDBMS] 
* [!DNL Experience Manager] user profile  -->
* RESTful 웹 서비스
* SOAP 기반 웹 서비스
* OData 서비스

데이터 통합은 OAuth2.0, 기본 인증 및 API 키 인증 유형을 즉시 지원하며, 웹 서비스에 액세스하기 위한 사용자 지정 인증을 구현할 수 있습니다. RESTful, SOAP 기반 및 OData 서비스는 [!DNL Experience Manager] as a Cloud Service <!--, JDBC for relational databases --> 및 커넥터 [!DNL Experience Manager] 사용자 프로필은 [!DNL Experience Manager] 웹 콘솔.

>[!NOTE]
>
>[!UICONTROL Experience Manager Forms] 은 관계형 데이터베이스를 지원하지 않습니다.

<!-- ## Configure relational database {#configure-relational-database}

You can configure relational databases using [!DNL Experience Manager] Web Console Configuration. Do the following:

1. Go to [!DNL Experience Manager] web console at `https://server:host/system/console/configMgr`.
1. Look for **[!UICONTROL Apache Sling Connection Pooled DataSource]** configuration. Tap to open the configuration in edit mode.
1. In the configuration dialog, specify the details for the database you want to configure, such as:

    * Name of the data source
    * Data source service property that stores the data source name
    * Java class name for the JDBC driver
    * JDBC connection URI
    * Username and password to establish connection with the JDBC driver

   >[!NOTE]
   >
   >Ensure that you encrypt sensitive information like passwords before configuring the data source. To encrypt:
   >
   >    
   >    
   >    1. Go to https://'[server]:[port]'/system/console/crypto.
   >    1. In the **[!UICONTROL Plain Text]** field, specify the password or any string to encrypt and tap **[!UICONTROL Protect]**.
   >    
   >    
   >    
   >The encrypted text appears in the Protected Text field that you can specify in the configuration.

1. Enable **[!UICONTROL Test on Borrow]** or **[!UICONTROL Test on Return]** to specify that the objects are validated before being borrowed or returned from and to the pool, respectively.
1. Specify a SQL SELECT query in the **[!UICONTROL Validation Query]** field to validate connections from the pool. The query must return at least one row. Based on your database, specify one of the following:

    * SELECT 1 (MySQL and MS SQL) 
    * SELECT 1 from dual (Oracle)

1. Tap **[!UICONTROL Save]** to save the configuration. -->

<!-- ## Configure [!DNL Experience Manager] user profile {#configure-aem-user-profile}

You can configure [!DNL Experience Manager] user profile using User Profile Connector configuration in [!DNL Experience Manager] Web Console. Do the following:

1. Go to [!DNL Experience Manager] web console at `https://[server]:[port]/system/console/configMgr`.
1. Look for **[!UICONTROL AEM Forms Data Integrations - User Profile Connector Configuration]** and tap to open the configuration in edit mode.
1. In the User Profile Connector Configuration dialog, you can add, remove, or update user profile properties. The specified properties will be available for use in form data model. Use the following format to specify user profile properties:

   `name=[property_name_with_location_in_user_profile],type=[property_type]`

   Examples:

    * `name=profile/phoneNumber,type=string`
    * `name=profile/empLocation/*/city,type=string`

   >[!NOTE]
   >
   >The **&#42;** in the above example denotes all nodes under the `profile/empLocation/` node in [!DNL Experience Manager] user profile in CRXDE structure. It means that the Form Data Model can access the `city` property of type `string` present in any node under the `profile/empLocation/` node. However, the nodes that contain the specified property must follow a consistent structure.

1. Tap **[!UICONTROL Save]** to save the configuration. -->

## 클라우드 서비스 구성에 대한 폴더 구성 {#cloud-folder}

RESTful, SOAP 및 OData 서비스에 대한 클라우드 서비스를 구성하려면 클라우드 서비스 폴더를 구성해야 합니다.

의 모든 클라우드 서비스 구성 [!DNL Experience Manager] 는 `/conf` 폴더 [!DNL Experience Manager] 저장소. 기본적으로 `conf` 폴더에는 다음이 포함됩니다 `global` 클라우드 서비스 구성을 만들 수 있는 폴더. 그러나 클라우드 구성에 대해서는 수동으로 활성화해야 합니다. 에서 추가 폴더를 만들 수도 있습니다 `conf` 클라우드 서비스 구성을 만들고 구성하려면 다음을 수행하십시오.

클라우드 서비스 구성에 대한 폴더를 구성하려면 다음을 수행하십시오.

1. 이동 **[!UICONTROL 도구 > 일반 > 구성 브라우저]**.
   * 자세한 내용은 [구성 브라우저](https://experienceleague.adobe.com/docs/experience-manager-65/administering/introduction/configurations.html) 설명서 를 참조하십시오.
1. 클라우드 구성에 대한 글로벌 폴더를 활성화하려면 다음을 수행하십시오. 또는 이 단계를 건너뛰고 클라우드 서비스 구성에 대한 다른 폴더를 만들고 구성하려면 다음을 수행하십시오.

   1. 에서 **[!UICONTROL 구성 브라우저]**&#x200B;에서 을(를) 선택합니다. `global` 폴더 및 탭 **[!UICONTROL 속성]**.

   1. 에서 **[!UICONTROL 구성 속성]** 대화 상자, 활성화 **[!UICONTROL 클라우드 구성]**.

   1. 탭 **[!UICONTROL 저장 및 닫기]** 구성을 저장하고 대화 상자를 종료합니다.

1. 에서 **[!UICONTROL 구성 브라우저]**, 탭 **[!UICONTROL 만들기]**.
1. 에서 **[!UICONTROL 구성 만들기]** 대화 상자에서 폴더의 제목을 지정하고 **[!UICONTROL 클라우드 구성]**.
1. 탭 **[!UICONTROL 만들기]** 클라우드 서비스 구성에 대해 활성화된 폴더를 만들려면

## RESTful 웹 서비스 구성 {#configure-restful-web-services}

RESTful 웹 서비스는 [Swagger 사양](https://swagger.io/specification/) JSON 또는 YAML 형식으로 [!DNL Swagger] 정의 파일입니다. 에서 RESTful 웹 서비스를 구성하려면 [!DNL Experience Manager] as a Cloud Service, [!DNL Swagger] 파일 시스템 또는 파일이 호스팅되는 URL의 파일입니다.

RESTful 서비스를 구성하려면 다음을 수행하십시오.

1. 이동 **[!UICONTROL 도구 > Cloud Services > 데이터 소스]**. 클라우드 구성을 만들 폴더를 선택하려면 탭합니다.

   자세한 내용은 [클라우드 서비스 구성에 대한 폴더 구성](configure-data-sources.md#cloud-folder) 클라우드 서비스 구성용 폴더 만들기 및 구성에 대한 자세한 내용은 을 참조하십시오.

1. 탭 **[!UICONTROL 만들기]** 열다 **[!UICONTROL 데이터 소스 구성 만들기 마법사]**. 구성 이름과 선택적으로 제목을 지정하고 **[!UICONTROL RESTful 서비스]** 에서 **[!UICONTROL 서비스 유형]** 드롭다운, 원하는 경우 구성에 대한 축소판 이미지를 찾아 선택한 다음 탭합니다 **[!UICONTROL 다음]**.
1. RESTful 서비스에 대해 다음 세부 정보를 지정합니다.

   * 에서 URL 또는 파일 을 선택합니다 [!UICONTROL Swagger 소스] 드롭다운 및 그에 따라 [!DNL Swagger URL] 변환 후[!DNL  Swagger] 정의 파일 또는 업로드 [!DNL Swagger] 파일을 로컬 파일 시스템에서 가져옵니다.
   * 기준[!DNL  Swagger] 소스 입력, 다음 필드는 값으로 미리 채워집니다.

      * 구성표: REST API에서 사용하는 전송 프로토콜입니다. 드롭다운 목록에 표시되는 체계 유형의 수는 [!DNL Swagger] 소스.
      * 호스트: REST API를 제공하는 호스트의 도메인 이름 또는 IP 주소입니다. 필수 필드입니다.
      * 기본 경로: 모든 API 경로의 URL 접두사입니다. 선택적 필드입니다.\
         필요한 경우 이러한 필드에 대해 미리 채워진 값을 편집합니다.
   * 인증 유형(없음, OAuth2.0, 기본 인증, API 키 또는 사용자 지정 인증)을 선택하여 RESTful 서비스에 액세스하고 그에 따라 인증에 대한 세부 정보를 제공합니다.

   선택하는 경우 **[!UICONTROL API 키]** 인증 유형으로 API 키의 값을 지정합니다. API 키는 요청 헤더로 또는 쿼리 매개 변수로 보낼 수 있습니다. 다음 옵션 중 하나를 선택합니다 **[!UICONTROL 위치]** 드롭다운 목록에서 헤더 또는 쿼리 매개 변수의 이름을 지정합니다 **[!UICONTROL 매개 변수 이름]** 그에 따라 필드가 표시됩니다.

   <!--If you select **[!UICONTROL Mutual Authentication]** as the authentication type, see [Certificate-based mutual authentication for RESTful and SOAP web services](#mutual-authentication).-->

1. 탭 **[!UICONTROL 만들기]** RESTful 서비스에 대한 클라우드 구성을 만듭니다.

### 성능 최적화를 위한 양식 데이터 모델 HTTP 클라이언트 구성 {#fdm-http-client-configuration}

[!DNL Experience Manager Forms] 데이터 소스로 RESTful 웹 서비스와 통합할 때 양식 데이터 모델에 성능 최적화를 위한 HTTP 클라이언트 구성이 포함됩니다.
양식 데이터 모델 HTTP 클라이언트를 구성하려면 다음 단계를 수행하십시오.

1. 에 로그인합니다. [!DNL Experience Manager Forms] 관리자로 작성자 인스턴스 및 다음 위치로 이동 [!DNL Experience Manager] 웹 콘솔 번들. 기본 URL은 [https://localhost:4502/system/console/configMgr](https://localhost:4502/system/console/configMgr).

1. 탭 **[!UICONTROL REST 데이터 소스에 대한 양식 데이터 모델 HTTP 클라이언트 구성]**.

1. 에서 [!UICONTROL REST 데이터 소스에 대한 양식 데이터 모델 HTTP 클라이언트 구성] 대화 상자:

   * 에서 양식 데이터 모델과 RESTful 웹 서비스 간에 허용되는 최대 연결 수를 지정합니다 **[!UICONTROL 총 연결 제한]** 필드. 기본값은 20개의 연결입니다.

   * 각 경로에 대해 허용되는 최대 연결 수를 **[!UICONTROL 경로별 연결 제한]** 필드. 기본값은 2개의 연결입니다.

   * 영구 HTTP 연결이 유지되는 기간을 **[!UICONTROL 살아있도록 유지]** 필드. 기본값은 15초입니다.

   * 지속 기간을 지정합니다. [!DNL Experience Manager Forms] 서버는 연결이 설정될 때까지 기다렸다가 **[!UICONTROL 연결 시간 초과]** 필드. 기본값은 10초입니다.

   * 에서 두 데이터 패킷 간에 비활성 상태에 대한 최대 기간을 지정합니다 **[!UICONTROL 소켓 시간 제한]** 필드. 기본값은 30초입니다.


## SOAP 웹 서비스 구성 {#configure-soap-web-services}

SOAP 기반 웹 서비스는 [WSDL(웹 서비스 설명 언어) 사양](https://www.w3.org/TR/wsdl). [!DNL Experience Manager Forms] RPC 스타일 WSDL 모델을 지원하지 않습니다.

에서 SOAP 기반 웹 서비스를 구성하려면 [!DNL Experience Manager] as a Cloud Service 웹 서비스용 WSDL URL이 있는지 확인하고 다음을 수행합니다.

1. 이동 **[!UICONTROL 도구 > Cloud Services > 데이터 소스]**. 클라우드 구성을 만들 폴더를 선택하려면 탭합니다.

   자세한 내용은 [클라우드 서비스 구성에 대한 폴더 구성](configure-data-sources.md#cloud-folder) 클라우드 서비스 구성용 폴더 만들기 및 구성에 대한 자세한 내용은 을 참조하십시오.

1. 탭 **[!UICONTROL 만들기]** 열다 **[!UICONTROL 데이터 소스 구성 만들기 마법사]**. 구성 이름과 선택적으로 제목을 지정하고 **[!UICONTROL SOAP 웹 서비스]** 에서 **[!UICONTROL 서비스 유형]** 드롭다운, 원하는 경우 구성에 대한 축소판 이미지를 찾아 선택한 다음 탭합니다 **[!UICONTROL 다음]**.
1. SOAP 웹 서비스에 대해 다음을 지정합니다.

   * 웹 서비스의 WSDL URL입니다.
   * 서비스 엔드포인트. WSDL에 언급된 서비스 끝점을 무시하려면 이 필드에 값을 지정하십시오.
   * 인증 유형(없음, OAuth2.0, 기본 인증 또는 사용자 지정 인증)을 선택하여 SOAP 서비스에 액세스하고 그에 따라 인증에 대한 세부 정보를 제공합니다.

      <!--If you select **[!UICONTROL X509 Token]** as the Authentication type, configure the X509 certificate. For more information, see [Set up certificates](install-configure-document-services.md#set-up-certificates-for-reader-extension-and-encryption-service).-->
      <!--Specify the KeyStore alias for the X509 certificate in the **[!UICONTROL Key Alias]** field. Specify the time, in seconds, until the authentication request remains valid, in the **[!UICONTROL Time To Live]** field. Optionally, select to sign the message body or timestamp header or both.-->

      <!--If you select **[!UICONTROL Mutual Authentication]** as the authentication type, see [Certificate-based mutual authentication for RESTful and SOAP web services](#mutual-authentication).-->

1. 탭 **[!UICONTROL 만들기]** SOAP 웹 서비스에 대한 클라우드 구성을 만들려면

### SOAP 웹 서비스 WSDL에서 가져오기 구문을 사용할 수 있도록 설정 {#enable-import-statements}

SOAP 웹 서비스 WSDL의 가져오기 구문으로 허용되는 절대 URL의 필터 역할을 하는 정규 표현식을 지정할 수 있습니다. 기본적으로 이 필드에 값이 없습니다. 결과적으로 [!DNL Experience Manager] wsdl에서 사용할 수 있는 모든 가져오기 구문을 차단합니다. 지정한 경우 `.*` 이 필드의 값으로, [!DNL Experience Manager] 모든 가져오기 구문을 허용합니다.

설정 `importAllowlistPattern` 속성 **[!UICONTROL 양식 데이터 모델 SOAP 웹 서비스 가져오기 허용 목록에 추가하다]** 정규 표현식을 지정하는 구성입니다. 다음 JSON 파일에는 샘플이 표시됩니다.

```json
{
  "importAllowlistPattern": ".*"
}
```

구성의 값을 설정하려면 [AEM SDK를 사용해 OSGi 구성을 생성](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/deploying/configuring-osgi.html?lang=en#generating-osgi-configurations-using-the-aem-sdk-quickstart)하고 Cloud Service 인스턴스에 [구성을 배포](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/deploy-code.html?lang=en#deployment-process)하십시오.

## OData 서비스 구성 {#config-odata}

OData 서비스는 서비스 루트 URL로 식별됩니다. 에서 OData 서비스를 구성하려면 [!DNL Experience Manager] as a Cloud Service 서비스에 대한 서비스 루트 URL이 있는지 확인하고 다음을 수행합니다.

>[!NOTE]
>
> 양식 데이터 모델은 [OData 버전 4](https://www.odata.org/documentation/).
>구성을 위한 단계별 안내서입니다. [!DNL Microsoft Dynamics 365], 온라인 또는 온프레미스에서 다음을 참조하십시오. [[!DNL Microsoft Dynamics] OData 구성](ms-dynamics-odata-configuration.md).

1. 이동 **[!UICONTROL 도구 > Cloud Services > 데이터 소스]**. 클라우드 구성을 만들 폴더를 선택하려면 탭합니다.

   자세한 내용은 [클라우드 서비스 구성에 대한 폴더 구성](#cloud-folder) 클라우드 서비스 구성용 폴더 만들기 및 구성에 대한 자세한 내용은 을 참조하십시오.

1. 탭 **[!UICONTROL 만들기]** 열다 **[!UICONTROL 데이터 소스 구성 만들기 마법사]**. 구성 이름과 선택적으로 제목을 지정하고 **[!UICONTROL OData 서비스]** 에서 **[!UICONTROL 서비스 유형]** 드롭다운, 원하는 경우 구성에 대한 축소판 이미지를 찾아 선택한 다음 탭합니다 **[!UICONTROL 다음]**.
1. OData 서비스에 대해 다음 세부 정보를 지정합니다.

   * 구성할 OData 서비스의 서비스 루트 URL입니다.
   * 인증 유형(없음, OAuth2.0, 기본 인증, API 키 또는 사용자 지정 인증)을 선택하여 OData 서비스에 액세스하고 그에 따라 인증 세부 사항을 제공합니다.

   선택하는 경우 **[!UICONTROL API 키]** 인증 유형으로 API 키의 값을 지정합니다. API 키는 요청 헤더로 또는 쿼리 매개 변수로 보낼 수 있습니다. 다음 옵션 중 하나를 선택합니다 **[!UICONTROL 위치]** 드롭다운 목록에서 헤더 또는 쿼리 매개 변수의 이름을 지정합니다 **[!UICONTROL 매개 변수 이름]** 그에 따라 필드가 표시됩니다.

   >[!NOTE]
   >
   >연결하려면 OAuth 2.0 인증 유형을 선택해야 합니다 [!DNL Microsoft Dynamics] OData 끝점을 서비스 루트로 사용하는 서비스입니다.

1. 탭 **[!UICONTROL 만들기]** OData 서비스에 대한 클라우드 구성을 만들려면

<!--## Certificate-based mutual authentication for RESTful and SOAP web services {#mutual-authentication}

When you enable mutual authentication for form data model, both the data source and [!DNL Experience Manager] Server running Form Data Model authenticate each other’s identity before sharing any data. You can use mutual authentication for REST and SOAP-based connections (data sources). To configure mutual authentication for a Form Data Model on your [!DNL Experience Manager Forms] environment:

1. Upload the private key (certificate) to [!DNL Experience Manager Forms] server. To upload the private key:
   1. Log in to your [!DNL Experience Manager Forms] server as an administrator.
   1. Navigate to **[!UICONTROL Tools]** > **[!UICONTROL Security]** > **[!UICONTROL Users]**. Select the `fd-cloudservice` user and tap **[!UICONTROL Properties]**.
   1. Open the **[!UICONTROL Keystore]** tab, expand the **[!UICONTROL Add Private Key from KeyStore file]** option, upload the KeyStore File, specify the aliases, passwords, and tap **[!UICONTROL Submit]**. The Certificate is uploaded.  The private key alias is mentioned in the certificate and set while creating the certificate.
1. Upload trust certificate to Global Trust Store. To upload the certificate:
   1. Navigate to **[!UICONTROL Tools]** > **[!UICONTROL Security]** > **[!UICONTROL Trust Store]**.
   1. Expand the **[!UICONTROL Add Certificate from CER file]** option, tap **[!UICONTROL Select Certificate File]**, upload the certificate, and tap **[!UICONTROL Submit]**.
1. Configure [SOAP](#configure-soap-web-services) or [RESTful](#configure-restful-web-services) web services as the data source and select **[!UICONTROL Mutual authentication]** as the authentication type. If you configure multiple self-signed certificates for `fd-cloudservice` user, specify the Key Alias name for the certificate.-->

## 다음 단계 {#next-steps}

데이터 소스를 구성했습니다. 다음으로 양식 데이터 모델을 만들거나 데이터 소스 없이 양식 데이터 모델을 이미 만든 경우 방금 구성한 데이터 소스와 연결할 수 있습니다. 자세한 내용은 [양식 데이터 모델 만들기](create-form-data-models.md) 자세한 내용
