---
title: 데이터 소스를 구성하는 방법
description: RESTful 웹 서비스, SOAP 기반 웹 서비스 및 OData 서비스를 양식 데이터 모델(FDM)의 데이터 소스로 구성하는 방법에 대해 알아봅니다.
feature: Adaptive Forms, Form Data Model
role: User, Developer
level: Beginner
exl-id: cb77a840-d705-4406-a94d-c85a6efc8f5d
source-git-commit: 7b31a2ea016567979288c7a8e55ed5bf8dfc181d
workflow-type: tm+mt
source-wordcount: '2129'
ht-degree: 2%

---


# 데이터 소스 구성 {#configure-data-sources}

| 버전 | 문서 링크 |
| -------- | ---------------------------- |
| AEM 6.5 | [여기 클릭](https://experienceleague.adobe.com/docs/experience-manager-65/forms/form-data-model/configure-data-sources.html) |
| AEM as a Cloud Service | 이 문서 |

![데이터 통합](do-not-localize/data-integeration.png)

[!DNL Experience Manager Forms] 데이터 통합을 통해 서로 다른 데이터 소스를 구성하고 연결할 수 있습니다. 기본적으로 지원되는 유형은 다음과 같습니다.

* 관계형 데이터베이스 - MySQL, [!DNL Microsoft® SQL Server], [!DNL IBM® DB2®], postgreSQL 및 [!DNL Oracle RDBMS]
* RESTful 웹 서비스
* SOAP 기반 웹 서비스
* OData 서비스(버전 4.0)
* Microsoft® Dynamics
* SalesForce
* Microsoft® Azure Blob 저장소

데이터 통합은 OAuth2.0([인증 코드](https://oauth.net/2/grant-types/authorization-code/), [클라이언트 자격 증명](https://oauth.net/2/grant-types/client-credentials/)), 기본 인증 및 API 키 인증 유형을 즉시 사용할 수 있도록 지원하며, 이를 통해 웹 서비스에 액세스하기 위한 사용자 지정 인증을 구현할 수 있습니다. RESTful, SOAP as a Cloud Service 기반 및 OData 서비스가 [!DNL Experience Manager]에 구성되어 있지만 [!DNL Experience Manager] 사용자 프로필에 대한 관계형 데이터베이스의 JDBC 및 커넥터는 [!DNL Experience Manager] 웹 콘솔에 구성되어 있습니다.

## 관계형 데이터베이스 구성 {#configure-relational-database}

### 사전 요구 사항

[!DNL Experience Manager] 웹 콘솔 구성을 사용하여 관계형 데이터베이스를 구성하기 전에 다음을 수행해야 합니다.
* 포트가 기본적으로 비활성화되어 있으므로 [Cloud Manager API를 통해 고급 네트워킹을 활성화](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/networking/advanced-networking.html)하십시오.
* [Maven에 JDBC 드라이버 종속성을 추가합니다](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/networking/examples/sql-datasourcepool.html?lang=en#mysql-driver-dependencies).


### 관계형 데이터베이스를 구성하는 단계

[!DNL Experience Manager] 웹 콘솔 구성을 사용하여 관계형 데이터베이스를 구성할 수 있습니다. 다음 작업을 수행합니다.

1. `https://server:host/system/console/configMgr`의 [!DNL Experience Manager] 웹 콘솔로 이동합니다.
1. **[!UICONTROL Day Commons JDBC 연결 풀]** 구성을 찾습니다. 을(를) 선택하여 편집 모드로 구성을 엽니다.

   ![JDBC 커넥터 풀](/help/forms/assets/jdbc_connector.png)

1. 구성 대화 상자에서 다음과 같이 구성할 데이터베이스에 대한 세부 정보를 지정합니다.

   * JDBC 드라이버의 Java™ 클래스 이름
   * JDBC 연결 URI
   * JDBC 드라이버와의 연결을 설정하는 사용자 이름 및 암호
   * **[!UICONTROL 유효성 검사 쿼리]** 필드에 SQL SELECT 쿼리를 지정하여 풀로부터의 연결을 검증하십시오. 쿼리는 하나 이상의 행을 반환해야 합니다. 데이터베이스를 기반으로 다음 중 하나를 지정합니다.
      * 1(MySQL 및 MS® SQL) 선택
      * 이중 (Oracle)에서 1 선택
   * 데이터 소스 이름

   관계형 데이터베이스를 구성하기 위한 샘플 문자열:

   ```text
      "datasource.name": "sqldatasourcename-mysql",
      "jdbc.driver.class": "com.mysql.jdbc.Driver",
      "jdbc.connection.uri": "jdbc:mysql://$[env:AEM_PROXY_HOST;default=proxy.tunnel]:30001/sqldatasourcename"
   ```

   >[!NOTE]
   >
   > 자세한 내용은 [JDBC DataSourcePool을 사용한 SQL 연결](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/networking/examples/sql-datasourcepool.html)을 참조하십시오.

1. **[!UICONTROL 저장]**&#x200B;을 선택하여 구성을 저장합니다.

이제 구성된 관계형 데이터베이스를 양식 데이터 모델(FDM)과 함께 사용할 수 있습니다.

<!-- ## Configure [!DNL Experience Manager] user profile {#configure-aem-user-profile}

You can configure [!DNL Experience Manager] user profile using User Profile Connector configuration in [!DNL Experience Manager] Web Console. Do the following:

1. Go to [!DNL Experience Manager] web console at `https://[server]:[port]/system/console/configMgr`.
1. Look for **[!UICONTROL AEM Forms Data Integrations - User Profile Connector Configuration]** and select to open the configuration in edit mode.
1. In the User Profile Connector Configuration dialog, you can add, remove, or update user profile properties. The specified properties are available for use in form data model (FDM). Use the following format to specify user profile properties:

   `name=[property_name_with_location_in_user_profile],type=[property_type]`

   Examples:

    * `name=profile/phoneNumber,type=string`
    * `name=profile/empLocation/*/city,type=string`

   >[!NOTE]
   >
   >The **&#42;** in the above example denotes all nodes under the `profile/empLocation/` node in [!DNL Experience Manager] user profile in CRXDE structure. It means that the Form Data Model (FDM) can access the `city` property of type `string` present in any node under the `profile/empLocation/` node. However, the nodes that contain the specified property must follow a consistent structure.

1. Select **[!UICONTROL Save]** to save the configuration. -->

## 클라우드 서비스 구성을 위한 폴더 구성 {#cloud-folder}

RESTful, SOAP 및 OData 서비스에 대한 클라우드 서비스를 구성하려면 클라우드 서비스 폴더에 대한 구성이 필요합니다.

[!DNL Experience Manager]의 모든 클라우드 서비스 구성이 [!DNL Experience Manager] 저장소의 `/conf` 폴더에 통합되었습니다. 기본적으로 `conf` 폴더에는 클라우드 서비스 구성을 만들 수 있는 `global` 폴더가 있습니다. 그러나 클라우드 구성에 대해서는 수동으로 활성화해야 합니다. `conf`에서 추가 폴더를 만들어 클라우드 서비스 구성을 만들고 구성할 수도 있습니다.

클라우드 서비스 구성에 대한 폴더를 구성하려면 다음을 수행합니다.

1. **[!UICONTROL 도구 > 일반 > 구성 브라우저]**&#x200B;로 이동합니다.
   * 자세한 내용은 [구성 브라우저](https://experienceleague.adobe.com/docs/experience-manager-65/administering/introduction/configurations.html) 설명서를 참조하십시오.
1. 클라우드 구성에 대한 전역 폴더를 활성화하려면 다음을 수행하거나 클라우드 서비스 구성에 대한 다른 폴더를 만들고 구성하려면 이 단계를 건너뜁니다.

   1. **[!UICONTROL 구성 브라우저]**&#x200B;에서 `global` 폴더를 선택하고 **[!UICONTROL 속성]**&#x200B;을 선택합니다.

   1. **[!UICONTROL 구성 속성]** 대화 상자에서 **[!UICONTROL 클라우드 구성]**&#x200B;을 사용하도록 설정합니다.

   1. 구성을 저장하고 대화 상자를 종료하려면 **[!UICONTROL 저장 및 닫기]**&#x200B;를 선택하십시오.

1. **[!UICONTROL 구성 브라우저]**&#x200B;에서 **[!UICONTROL 만들기]**&#x200B;를 선택합니다.
1. **[!UICONTROL 구성 만들기]** 대화 상자에서 폴더의 제목을 지정하고 **[!UICONTROL 클라우드 구성]**&#x200B;을 사용하도록 설정합니다.
1. 클라우드 서비스 구성에 사용할 수 있는 폴더를 만들려면 **[!UICONTROL 만들기]**&#x200B;를 선택하십시오.

## RESTful 웹 서비스 구성 {#configure-restful-web-services}

RESTful 웹 서비스는 [!DNL Swagger] 정의 파일에서 JSON 또는 YAML 형식의 [Swagger 사양](https://swagger.io/specification/v2/)을 사용하여 설명할 수 있습니다. as a Cloud Service [!DNL Experience Manager]에서 RESTful 웹 서비스를 구성하려면 [!DNL Swagger] 파일([Swagger 버전 2.0](https://swagger.io/specification/v2/)) 또는 [!DNL Swagger] 파일([Swagger 버전 3.0](https://swagger.io/specification/v3/))이 파일 시스템 또는 파일이 호스팅된 URL에 있는지 확인하십시오.

### Open API 사양 버전 2.0에 대한 RESTful 서비스 구성 {#configure-restful-services-open-api-2.0}

1. **[!UICONTROL 도구 > Cloud Service > 데이터 원본]**(으)로 이동합니다. 클라우드 구성을 만들 폴더를 선택하려면 를 선택합니다.

   클라우드 서비스 구성을 위한 폴더를 만들고 구성하는 방법에 대한 자세한 내용은 [클라우드 서비스 구성을 위한 폴더 구성](configure-data-sources.md#cloud-folder)을 참조하십시오.

1. **[!UICONTROL 만들기]**&#x200B;를 선택하여 **[!UICONTROL 데이터 Source 구성 만들기 마법사]**&#x200B;를 엽니다. 구성의 이름 및 제목(선택 사항)을 지정하고, **[!UICONTROL 서비스 유형]** 드롭다운에서 **[!UICONTROL RESTful 서비스]**&#x200B;를 선택하고, 선택 사항으로 구성의 썸네일 이미지를 검색하여 선택한 후 **[!UICONTROL 다음]**&#x200B;을 선택합니다.
1. RESTful 서비스에 대해 다음 세부 정보를 지정합니다.

   * [!UICONTROL Swagger Source] 드롭다운에서 URL 또는 파일을 선택한 다음 [!DNL  Swagger] 정의 파일에 [!DNL Swagger URL]을(를) 지정하거나 로컬 파일 시스템에서 [!DNL Swagger] 파일을 업로드하십시오.
   * [!DNL  Swagger] Source 입력을 기반으로 다음 필드가 값으로 미리 채워집니다.

      * 체계: REST API에서 사용하는 전송 프로토콜입니다. 드롭다운 목록에 표시되는 구성표 유형의 수는 [!DNL Swagger] 소스에 정의된 구성표에 따라 다릅니다.
      * 호스트: REST API를 제공하는 호스트의 도메인 이름 또는 IP 주소입니다. 필수 필드입니다.
      * 기본 경로: 모든 API 경로의 URL 접두어. 선택 필드입니다.\
        필요한 경우 이러한 필드에 대해 미리 채워진 값을 편집합니다.

   * RESTful 서비스에 액세스하고 그에 따라 인증에 대한 세부 정보를 제공하려면 인증 유형 없음, OAuth2.0([인증 코드](https://oauth.net/2/grant-types/authorization-code/), [클라이언트 자격 증명](https://oauth.net/2/grant-types/client-credentials/)), 기본 인증, API 키 또는 사용자 지정 인증을 선택하십시오.

   인증 유형으로 **[!UICONTROL API 키]**&#x200B;을(를) 선택한 경우 API 키 값을 지정하십시오. API 키는 요청 헤더 또는 쿼리 매개 변수로 전송될 수 있습니다. **[!UICONTROL 위치]** 드롭다운 목록에서 이러한 옵션 중 하나를 선택하고 **[!UICONTROL 매개 변수 이름]** 필드에 헤더 이름 또는 쿼리 매개 변수를 적절하게 지정합니다.

   <!--If you select **[!UICONTROL Mutual Authentication]** as the authentication type, see [Certificate-based mutual authentication for RESTful and SOAP web services](#mutual-authentication).-->

1. RESTful 서비스에 대한 클라우드 구성을 만들려면 **[!UICONTROL 만들기]**&#x200B;를 선택하십시오.

### Open API 사양 버전 3.0에 대한 RESTful 서비스 구성 {#configure-restful-services-open-api-3.0}

1. **[!UICONTROL 도구 > Cloud Service > 데이터 원본]**(으)로 이동합니다. 클라우드 구성을 만들 폴더를 선택하려면 를 선택합니다.

   클라우드 서비스 구성을 위한 폴더를 만들고 구성하는 방법에 대한 자세한 내용은 [클라우드 서비스 구성을 위한 폴더 구성](configure-data-sources.md#cloud-folder)을 참조하십시오.

1. **[!UICONTROL 만들기]**&#x200B;를 선택하여 **[!UICONTROL 데이터 Source 구성 만들기 마법사]**&#x200B;를 엽니다. 구성의 이름 및 제목(선택 사항)을 지정하고, **[!UICONTROL 서비스 유형]** 드롭다운에서 **[!UICONTROL RESTful 서비스]**&#x200B;를 선택하고, 선택 사항으로 구성의 썸네일 이미지를 검색하여 선택한 후 **[!UICONTROL 다음]**&#x200B;을 선택합니다.
1. RESTful 서비스에 대해 다음 세부 정보를 지정합니다.

   * [!UICONTROL Swagger Source] 드롭다운에서 URL 또는 파일을 선택한 다음 [!DNL  Swagger] 정의 파일에 [!DNL Swagger 3.0 URL]을(를) 지정하거나 로컬 파일 시스템에서 [!DNL Swagger] 파일을 업로드하십시오.
   * [!DNL  Swagger] Source 입력을 기반으로 대상 서버와의 연결 정보가 표시됩니다.
   * RESTful 서비스에 액세스하고 그에 따라 인증에 대한 세부 정보를 제공하려면 인증 유형 없음, OAuth2.0([인증 코드](https://oauth.net/2/grant-types/authorization-code/), [클라이언트 자격 증명](https://oauth.net/2/grant-types/client-credentials/)), 기본 인증, API 키 또는 사용자 지정 인증을 선택하십시오.

   인증 유형으로 **[!UICONTROL API 키]**&#x200B;을(를) 선택한 경우 API 키 값을 지정하십시오. API 키는 요청 헤더 또는 쿼리 매개 변수로 전송될 수 있습니다. **[!UICONTROL 위치]** 드롭다운 목록에서 이러한 옵션 중 하나를 선택하고 **[!UICONTROL 매개 변수 이름]** 필드에 헤더 이름 또는 쿼리 매개 변수를 적절하게 지정합니다.

   <!--If you select **[!UICONTROL Mutual Authentication]** as the authentication type, see [Certificate-based mutual authentication for RESTful and SOAP web services](#mutual-authentication).-->

1. RESTful 서비스에 대한 클라우드 구성을 만들려면 **[!UICONTROL 만들기]**&#x200B;를 선택하십시오.

RESTful 서비스 Open API 사양 버전 3.0에서 지원되지 않는 일부 작업은 다음과 같습니다.
* 콜백
* oneof/anyof
* 원격 참조
* 링크
* 단일 작업에 대해 서로 다른 MIME 유형에 대해 서로 다른 요청 본문

자세한 내용은 [OpenAPI 3.0 사양](https://swagger.io/specification/v3/)을 참조하십시오.

### 성능을 최적화하기 위한 양식 데이터 모델(FDM) HTTP 클라이언트 구성 {#fdm-http-client-configuration}

[!DNL Experience Manager Forms]은(는) 데이터 원본에 성능 최적화를 위한 HTTP 클라이언트 구성이 포함되어 있으므로 RESTful 웹 서비스와 통합할 때 데이터 모델을 형성합니다.

REST 데이터 원본에 대한 **[!UICONTROL 양식 데이터 모델 HTTP 클라이언트 구성]** 구성의 다음 속성을 설정하여 정규식을 지정하십시오.

* `http.connection.max.per.route` 속성을 사용하여 FDM(양식 데이터 모델)과 RESTful 웹 서비스 간에 허용되는 최대 연결 수를 설정합니다. 기본값은 20개 연결입니다.

* 각 경로에 대해 허용되는 최대 연결 수를 지정하려면 `http.connection.max` 속성을 사용하십시오. 기본값은 40개 연결입니다.

* `http.connection.keep.alive.duration` 속성을 사용하여 영구 HTTP 연결이 활성 상태로 유지되는 기간을 지정하십시오. 기본값은 15초입니다.

* `http.connection.timeout` 속성을 사용하여 [!DNL Experience Manager Forms] 서버가 연결을 설정할 때까지 기다리는 기간을 지정합니다. 기본값은 10초입니다.

* `http.socket.timeout` 속성을 사용하여 두 데이터 패킷 간 비활성 최대 기간을 지정하십시오. 기본값은 30초입니다.

다음 JSON 파일에는 샘플이 표시됩니다.


```json
{   
   "http.connection.keep.alive.duration":"15",   
   "http.connection.max.per.route":"20",   
   "http.connection.timeout":"10",   
   "http.socket.timeout":"30",   
   "http.connection.idle.connection.timeout":"15",   
   "http.connection.max":"40" 
} 
```

1. REST 데이터 원본에 대한 **[!UICONTROL 양식 데이터 모델 HTTP 클라이언트 구성]**&#x200B;을 선택하십시오.

1. [!UICONTROL REST 데이터 원본에 대한 양식 데이터 모델 HTTP 클라이언트 구성] 대화 상자에서 다음을 수행합니다.

   * 총 **[!UICONTROL 연결 제한]** 필드에서 FDM(양식 데이터 모델)과 RESTful 웹 서비스 간 허용되는 최대 연결 수를 지정합니다. 기본값은 20개 연결입니다.

   * **[!UICONTROL 경로별 연결 제한]** 필드에 각 경로에 대해 허용되는 최대 연결 수를 지정합니다. 기본값은 두 개의 연결입니다.

   * **[!UICONTROL 활성 상태 유지]** 필드에 영구 HTTP 연결이 활성 상태로 유지되는 기간을 지정하십시오. 기본값은 15초입니다.

   * **[!UICONTROL 연결 시간 초과]** 필드에 [!DNL Experience Manager Forms] 서버가 연결을 설정할 때까지 기다리는 기간을 지정합니다. 기본값은 10초입니다.

   * **[!UICONTROL 소켓 시간 제한]** 필드에 두 데이터 패킷 간 비활성 최대 기간을 지정합니다. 기본값은 30초입니다.

## SOAP 웹 서비스 구성 {#configure-soap-web-services}

SOAP 기반 웹 서비스는 [WSDL(Web Services Description Language) 사양](https://www.w3.org/TR/wsdl)을 사용하여 설명합니다. [!DNL Experience Manager Forms]은(는) RPC 스타일의 WSDL 모델을 지원하지 않습니다.

[!DNL Experience Manager]에서 SOAP as a Cloud Service 기반 웹 서비스를 구성하려면 웹 서비스에 대한 WSDL URL이 있는지 확인하고 다음을 수행합니다.

1. **[!UICONTROL 도구 > Cloud Service > 데이터 원본]**(으)로 이동합니다. 클라우드 구성을 만들 폴더를 선택하려면 를 선택합니다.

   클라우드 서비스 구성을 위한 폴더를 만들고 구성하는 방법에 대한 자세한 내용은 [클라우드 서비스 구성을 위한 폴더 구성](configure-data-sources.md#cloud-folder)을 참조하십시오.

1. **[!UICONTROL 만들기]**&#x200B;를 선택하여 **[!UICONTROL 데이터 Source 구성 만들기 마법사]**&#x200B;를 엽니다. 구성의 이름 및 제목(선택 사항)을 지정하고, **[!UICONTROL 서비스 유형]** 드롭다운에서 **[!UICONTROL SOAP 웹 서비스]**&#x200B;를 선택하고, 선택 사항으로 구성의 썸네일 이미지를 찾아 선택한 후 **[!UICONTROL 다음]**&#x200B;을 선택합니다.
1. SOAP 웹 서비스에 대해 다음을 지정합니다.

   * 웹 서비스용 WSDL URL입니다.
   * 서비스 엔드포인트. WSDL에 언급된 서비스 끝점을 재정의하려면 이 필드에 값을 지정하십시오.
   * 인증 유형(없음, OAuth2.0([인증 코드](https://oauth.net/2/grant-types/authorization-code/), [클라이언트 자격 증명](https://oauth.net/2/grant-types/client-credentials/)), 기본 인증 또는 사용자 지정 인증)을 선택하여 SOAP 서비스에 액세스하고 그에 따라 인증에 대한 세부 정보를 제공합니다.

     <!--If you select **[!UICONTROL X509 Token]** as the Authentication type, configure the X509 certificate. For more information, see [Set up certificates](install-configure-document-services.md#set-up-certificates-for-reader-extension-and-encryption-service).-->
     <!--Specify the KeyStore alias for the X509 certificate in the **[!UICONTROL Key Alias]** field. Specify the time, in seconds, until the authentication request remains valid, in the **[!UICONTROL Time To Live]** field. Optionally, select to sign the message body or timestamp header or both.-->

     <!--If you select **[!UICONTROL Mutual Authentication]** as the authentication type, see [Certificate-based mutual authentication for RESTful and SOAP web services](#mutual-authentication).-->

1. SOAP 웹 서비스에 대한 클라우드 구성을 만들려면 **[!UICONTROL 만들기]**&#x200B;를 선택하십시오.

### SOAP 웹 서비스 WSDL에서 가져오기 문 사용 활성화 {#enable-import-statements}

SOAP 웹 서비스 WSDL에서 가져오기 문으로 허용되는 절대 URL에 대한 필터 역할을 하는 정규 표현식을 지정할 수 있습니다. 기본적으로 이 필드에는 값이 없습니다. 따라서 [!DNL Experience Manager]은(는) WSDL에서 사용할 수 있는 모든 가져오기 문을 차단합니다. `.*`을(를) 이 필드의 값으로 지정하면 [!DNL Experience Manager]에서 모든 가져오기 문을 허용합니다.

**[!UICONTROL 양식 데이터 모델 웹 서비스 가져오기 SOAP 허용 목록에 추가하다]** 구성의 `importAllowlistPattern` 속성을 설정하여 정규 표현식을 지정하십시오. 다음 JSON 파일에는 샘플이 표시됩니다.

```json
{
  "importAllowlistPattern": ".*"
}
```

구성의 값을 설정하려면 [AEM SDK를 사용하여 OSGi 구성을 생성](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/deploying/configuring-osgi.html?lang=ko#generating-osgi-configurations-using-the-aem-sdk-quickstart)하고 Cloud Service 인스턴스에 [구성을 배포](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/deploy-code.html?lang=ko#deployment-process)합니다.

## OData 서비스 구성 {#config-odata}

OData 서비스는 서비스 루트 URL로 식별됩니다. as a Cloud Service [!DNL Experience Manager] OData 서비스를 구성하려면 서비스에 대한 서비스 루트 URL이 있는지 확인하고 다음을 수행합니다.

>[!NOTE]
>
> 양식 데이터 모델(FDM)은 [OData 버전 4](https://www.odata.org/documentation/)을 지원합니다.
>온라인 또는 온-프레미스에서 [!DNL Microsoft®® Dynamics 365]을(를) 구성하기 위한 단계별 안내서는 [[!DNL Microsoft® Dynamics] OData 구성](ms-dynamics-odata-configuration.md)을 참조하십시오.

1. **[!UICONTROL 도구 > Cloud Service > 데이터 원본]**(으)로 이동합니다. 클라우드 구성을 만들 폴더를 선택하려면 를 선택합니다.

   클라우드 서비스 구성을 위한 폴더를 만들고 구성하는 방법에 대한 자세한 내용은 [클라우드 서비스 구성을 위한 폴더 구성](#cloud-folder)을 참조하십시오.

1. **[!UICONTROL 만들기]**&#x200B;를 선택하여 **[!UICONTROL 데이터 Source 구성 만들기 마법사]**&#x200B;를 엽니다. 구성의 이름 및 제목(선택 사항)을 지정하고, **[!UICONTROL 서비스 유형]** 드롭다운에서 **[!UICONTROL 데이터 서비스]**&#x200B;를 선택하고, 선택 사항으로 구성의 썸네일 이미지를 찾아 선택한 후 **[!UICONTROL 다음]**&#x200B;을 선택합니다.
1. OData 서비스에 대해 다음 세부 정보를 지정합니다.

   * 구성할 OData 서비스의 서비스 루트 URL입니다.
   * 인증 유형(없음, OAuth2.0([인증 코드](https://oauth.net/2/grant-types/authorization-code/), [클라이언트 자격 증명](https://oauth.net/2/grant-types/client-credentials/)), 기본 인증, API 키 또는 사용자 지정 인증)을 선택하여 OData 서비스에 액세스하고 그에 따라 인증에 대한 세부 정보를 제공합니다.

   인증 유형으로 **[!UICONTROL API 키]**&#x200B;을(를) 선택한 경우 API 키 값을 지정하십시오. API 키는 요청 헤더 또는 쿼리 매개 변수로 전송될 수 있습니다. **[!UICONTROL 위치]** 드롭다운 목록에서 이러한 옵션 중 하나를 선택하고 **[!UICONTROL 매개 변수 이름]** 필드에 헤더 이름 또는 쿼리 매개 변수를 적절하게 지정합니다.

   >[!NOTE]
   >
   >OData 끝점을 서비스 루트로 사용하여 [!DNL Microsoft®® Dynamics] 서비스와 연결할 OAuth 2.0 인증 유형을 선택하십시오.

1. OData 서비스에 대한 클라우드 구성을 만들려면 **[!UICONTROL 만들기]**&#x200B;를 선택하십시오.

<!--
## Configure Microsoft® SharePoint List {#config-sharepoint-list}

<span class="preview"> This is a pre-release feature and accessible through our [pre-release channel](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/release-notes/prerelease.html#new-features). </span>

To save data in a tabular form use, Microsoft® SharePoint List. To configure a Microsoft SharePoint List in [!DNL Experience Manager] as a Cloud Service, do the following:

1. Go to **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** >  **[!UICONTROL Microsoft® SharePoint]**.   
1. Select a **Configuration Container**. The configuration is stored in the selected Configuration Container. 
1. Click **[!UICONTROL Create]** > **[!UICONTROL SharePoint List]** from the drop-down list. The SharePoint configuration wizard appears.  
1. Specify the **[!UICONTROL Title]**, **[!UICONTROL Client ID]**, **[!UICONTROL Client Secret]** and **[!UICONTROL OAuth URL]**. For information on how to retrieve Client ID, Client Secret, Tenant ID for OAuth URL, see [Microsoft&reg; Documentation](https://learn.microsoft.com/en-us/graph/auth-register-app-v2).
    * You can retrieve the `Client ID` and `Client Secret` of your app from the Microsoft&reg; Azure portal.
    * In the Microsoft&reg; Azure portal, add the Redirect URI as `https://[author-instance]/libs/cq/sharepointlist/content/configurations/wizard.html`. Replace `[author-instance]` with the URL of your Author instance.
    * Add the API permissions `offline_access` and `Sites.Manage.All` in the **Microsoft® Graph** tab to provide read/write permissions. Add `AllSites.Manage` permission in the **Sharepoint** tab to interact remotely with SharePoint data.
    * Use OAuth URL: `https://login.microsoftonline.com/tenant-id/oauth2/v2.0/authorize`. Replace `<tenant-id>` with the `tenant-id` of your app from the Microsoft&reg; Azure portal.

      >[!NOTE]
      >
      > The **client secret** field is mandatory or optional depends upon your Azure Active Directory application configuration. If your application is configured to use a client secret, it is mandatory to provide the client secret.

1. Click **[!UICONTROL Connect]**. On a successful connection, the `Connection Successful` message appears.
1. Select **[!UICONTROL SharePoint Site]** and **[!UICONTROL SharePoint List]** from the drop-down list.
1. Select **[!UICONTROL Create]** to create the cloud configuration for the Microsoft® SharePointList.

-->

<!--## Certificate-based mutual authentication for RESTful and SOAP web services {#mutual-authentication}

When you enable mutual authentication for form data model (FDM), both the data source and [!DNL Experience Manager] Server running Form Data Model (FDM) authenticate each other's identity before sharing any data. You can use mutual authentication for REST and SOAP-based connections (data sources). To configure mutual authentication for a Form Data Model (FDM) on your [!DNL Experience Manager Forms] environment:

1. Upload the private key (certificate) to [!DNL Experience Manager Forms] server. To upload the private key:
   1. Log in to your [!DNL Experience Manager Forms] server as an administrator.
   1. Navigate to **[!UICONTROL Tools]** > **[!UICONTROL Security]** > **[!UICONTROL Users]**. Select the `fd-cloudservice` user and select **[!UICONTROL Properties]**.
   1. Open the **[!UICONTROL Keystore]** tab, expand the **[!UICONTROL Add Private Key from KeyStore file]** option, upload the KeyStore File, specify the aliases, passwords, and select **[!UICONTROL Submit]**. The Certificate is uploaded.  The private key alias is mentioned in the certificate and set while creating the certificate.
1. Upload trust certificate to Global Trust Store. To upload the certificate:
   1. Navigate to **[!UICONTROL Tools]** > **[!UICONTROL Security]** > **[!UICONTROL Trust Store]**.
   1. Expand the **[!UICONTROL Add Certificate from CER file]** option, select **[!UICONTROL Select Certificate File]**, upload the certificate, and select **[!UICONTROL Submit]**.
1. Configure [SOAP](#configure-soap-web-services) or [RESTful](#configure-restful-web-services) web services as the data source and select **[!UICONTROL Mutual authentication]** as the authentication type. If you configure multiple self-signed certificates for `fd-cloudservice` user, specify the Key Alias name for the certificate.-->

## 다음 단계 {#next-steps}

데이터 소스를 구성했습니다. 그런 다음 양식 데이터 모델(FDM)을 만들거나 데이터 소스 없이 이미 양식 데이터 모델(FDM)을 만든 경우 구성한 데이터 소스와 연결할 수 있습니다. 자세한 내용은 [양식 데이터 모델 만들기](create-form-data-models.md)를 참조하십시오.


<!--

>[!MORELIKETHIS]
>
>* [Configure Azure storage for AEM Forms](/help/forms/configure-azure-storage.md)
>* [Integrate Microsoft Dynamics 365 and Salesforce with Adaptive Forms](/help/forms/configure-msdynamics-salesforce.md)
>*  [Add Forms Portal to an AEM Sites page](/help/forms/configure-forms-portal.md)

-->