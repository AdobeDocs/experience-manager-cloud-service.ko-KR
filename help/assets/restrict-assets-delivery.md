---
title: OpenAPI 기능을 사용하여 Dynamic Media으로 자산 배달 제한
description: OpenAPI 기능을 사용하여 에셋 전달을 제한하는 방법에 대해 알아봅니다.
role: User
exl-id: 3fa0b75d-c8f5-4913-8be3-816b7fb73353
source-git-commit: 6e9fa8301fba9cab1a185bf2d81917e45acfe3a3
workflow-type: tm+mt
source-wordcount: '1181'
ht-degree: 2%

---

# OpenAPI 기능을 사용하여 Dynamic Media으로 자산 배달 제한 {#restrict-access-to-assets}

| [모범 사례 검색](/help/assets/search-best-practices.md) | [메타데이터 모범 사례](/help/assets/metadata-best-practices.md) | [Content Hub](/help/assets/product-overview.md) | [OpenAPI 기능 포함 Dynamic Media](/help/assets/dynamic-media-open-apis-overview.md) | [AEM Assets 개발자 설명서](https://developer.adobe.com/experience-cloud/experience-manager-apis/) |
| ------------- | --------------------------- |---------|----|-----|

Experience Manager의 중앙 자산 거버넌스를 사용하면 DAM 관리자 또는 브랜드 관리자가 OpenAPI 기능을 통해 Dynamic Media을 통해 사용할 수 있는 자산에 대한 액세스를 관리할 수 있습니다. AEM as a Cloud Service 작성자 서비스의 에셋에 대한 특정 메타데이터를 구성하여 승인된 에셋(개별 에셋까지)을 선택한 [IMS(Identity Management 시스템) Adobe 사용자 또는 그룹](https://helpx.adobe.com/in/enterprise/using/users.html#user-mgt-strategy)(으)로 배달을 제한할 수 있습니다.

자산이 OpenAPI를 통해 Dynamic Media을 통해 제한되면 해당 자산에 액세스할 수 있는 권한이 있는 (Adobe IMS 온보딩된) 사용자만 액세스할 수 있습니다. 에셋에 액세스하려면 사용자는 OpenAPI를 사용하는 Dynamic Media의 [검색](search-assets-api.md) 및 [배달](deliver-assets-apis.md) 기능을 활용해야 합니다.

![자산에 대한 액세스 제한](/help/assets/assets/restricted-access.png)

Experience Manager Assets에서 IMS를 통한 제한된 전달에는 두 가지 주요 단계가 포함됩니다.

* 작성
* 제공

## 작성 {#authoring}

### IMS 전달자 토큰을 사용한 제한된 게재 {#restrict-delivery-ims-token}

IMS 사용자 및 그룹 ID 를 기준으로 [!DNL Experience Manager] 내의 자산 배달을 제한할 수 있습니다.

>[!NOTE]
>
> 이 기능은 현재 셀프 서비스가 아닙니다. IMS [사용자](https://helpx.adobe.com/in/enterprise/using/manage-directory-users.html) 및 [그룹](https://helpx.adobe.com/in/enterprise/using/user-groups.html)에 대한 자산 전달을 제한하려면 Enterprise 지원 팀에 연락하여 [Adobe Admin Console](https://adminconsole.adobe.com/) 포털에서 액세스를 제한하는 데 필요한 정보를 검색하는 방법과 AEM as a Cloud Service 작성자 서비스에서 액세스를 구성하는 방법에 대한 지침을 확인하십시오.

### 설정 및 해제 날짜 및 시간을 사용하여 에셋 게재 제한 {#restrict-delivery-assets-date-time}

DAM 작성자는 에셋 속성에서 사용할 수 있는 활성화 켜기 또는 끄기 시간을 정의하여 에셋 전달을 제한할 수도 있습니다.

에셋의 활성화를 위해 설정 시간을 정의하는 경우 정의된 시간에 에셋에 대한 게재 URL이 생성됩니다. 자산은 정의된 시간 이전에 비활성 상태로 유지됩니다. 마찬가지로, 에셋에 대해 해제 시간을 정의하는 경우 에셋은 정의된 시간에 비활성화되고 에셋의 게재 URL은 에셋 표시를 중단합니다.

다음 단계를 실행하여 에셋의 켜기 및 끄기 시간을 설정합니다.

1. 자산을 선택하고 **[!UICONTROL 속성]**&#x200B;을 클릭합니다.

1. **[!UICONTROL 기본]** 탭의 **[!UICONTROL 예약된(de) 활성화]** 섹션에서 요구 사항에 따라 설정 시간 또는 해제 시간을 정의합니다.

마찬가지로 Assets 보기에서 에셋을 선택하고 **[!UICONTROL 세부 정보]**&#x200B;를 클릭하여 에셋 속성을 보고 설정 시간 및 해제 시간을 정의할 수 있습니다.

필드는 기본 메타데이터 양식에서 사용할 수 있습니다. 에셋이 기본 메타데이터 스키마를 기반으로 하지 않으며 에셋 속성에서 설정 시간 및 해제 시간 필드를 사용할 수 없는 경우 관리자 보기에서 다음 단계를 수행하십시오.

1. **[!UICONTROL 도구]** > **[!UICONTROL Assets]** > **[!UICONTROL 메타데이터 스키마]**&#x200B;로 이동합니다.
1. 메타데이터 스키마를 선택하고 **[!UICONTROL 편집]**&#x200B;을 클릭합니다.
1. 오른쪽의 **[!UICONTROL 양식 작성]** 섹션에서 **[!UICONTROL 날짜]** 필드를 양식의 메타데이터 섹션에 추가합니다.
1. 새로 추가한 필드를 클릭한 다음 **[!UICONTROL 설정]** 패널에서 다음 업데이트를 수행합니다.
   1. **[!UICONTROL 필드 레이블]**&#x200B;을(를) **설정 시간** 또는 **해제 시간**(으)로 변경하십시오.
   1. **[!UICONTROL 속성에 매핑]**&#x200B;을(를) _(으)로 업데이트합니다.**설정 시간**필드 및_&#x200B;에 대한 /jcr:content/onTime _.**해제 시간**필드의 /jcr:content/offTime_.
1. **[!UICONTROL 저장]**&#x200B;을 클릭합니다.

마찬가지로, Assets 보기의 경우 에셋이 기본 메타데이터 스키마를 기반으로 하지 않으며 에셋 속성에서 설정 시간 및 해제 시간 필드를 사용할 수 없는 경우 다음 단계를 실행합니다.

1. **[!UICONTROL 설정]** 섹션에서 **[!UICONTROL 메타데이터 Forms]**&#x200B;을(를) 클릭합니다.
1. 메타데이터 양식을 선택하고 **[!UICONTROL 편집]**&#x200B;을 클릭합니다.
1. 왼쪽 창의 **[!UICONTROL 구성 요소]** 섹션에서 **[!UICONTROL 날짜]** 필드를 양식에 추가하십시오.
1. 새로 추가한 필드를 클릭하고 **[!UICONTROL 레이블]**&#x200B;을(를) **설정 시간** 또는 **해제 시간**(으)로 변경합니다.
1. **[!UICONTROL 메타데이터 속성]**&#x200B;을(를) _(으)로 업데이트합니다.**설정 시간**필드 및_&#x200B;에 대한 /jcr:content/onTime _.**해제 시간**필드의 /jcr:content/offTime_.
1. **[!UICONTROL 저장]**&#x200B;을 클릭합니다.



## 제한된 에셋 전달 {#delivery-restricted-assets}

제한된 에셋의 전달은 에셋에 액세스할 수 있는 성공적인 인증을 기반으로 합니다. 인증은 [IMS 전달자 토큰](https://developer.adobe.com/developer-console/docs/guides/authentication/UserAuthentication/IMS/)([AEM Asset 선택기](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/assets/manage/asset-selector/overview-asset-selector)에서 시작된 요청에 대한 애플리케이션) 또는 보안 쿠키( AEM Publish/미리보기 서비스에 사용자 지정 ID 공급자를 설정하고 페이지에 쿠키 생성 및 포함을 설정한 경우)를 통해 이루어집니다.

### AEM 작성자 또는 자산 선택기 요청 게재 {#delivery-aem-author-asset-selector}

AEM 작성자 서비스 또는 AEM Asset 선택기에서 요청이 전송되는 경우 제한된 에셋의 전달을 활성화하려면 유효한 IMS 전달자 토큰이 필요합니다.\
AEM Cloud Service 작성자 서비스와 Asset Selector에서 IMS 전달자 토큰은 로그인 성공 후 요청에 자동으로 생성되고 사용됩니다.

>[!NOTE]
>
>AEM Asset Selector 기반 통합에서 IMS 인증을 활성화하는 방법에 대한 자세한 내용은 엔터프라이즈 지원에 문의하십시오

1. 비 Asset Selector 기반 경험의 경우 현재 OpenAPI 기능이 있는 AEM as a Cloud Service 및 Dynamic Media에서 서버측 API 통합을 지원하고 IMS Bearer 토큰을 생성할 수 있습니다.
   * [여기](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/implementing/developing/generating-access-tokens-for-server-side-apis#the-server-to-server-flow)의 지침에 따라 [AEM as a Cloud Service Developer Console](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/implementing/developing/development-guidelines#crxde-lite-and-developer-console)을 통해 IMS Bearer 토큰을 검색할 수 있는 서비스 대 서버 API 통합을 수행합니다
   * 제한된 기간 동안 [여기](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/implementing/developing/generating-access-tokens-for-server-side-apis#developer-flow)의 지침에 따라 [AEM as a Cloud Service Developer Console](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/implementing/developing/development-guidelines#crxde-lite-and-developer-console)에서 인증된 사용자에 대한 로컬 개발자 액세스(프로덕션 사용 사례는 아님), 단기 IMS 전달자 토큰을 생성할 수 있습니다.

1. [Search](search-assets-api.md) 및 [Delivery](deliver-assets-apis.md) API 요청을 만드는 동안 가져온 IMS 전달자 토큰을 HTTP 요청의 **[!UICONTROL Authorization]** 헤더에 추가하십시오(**[!UICONTROL Bearer]** 접두사가 추가되었는지 확인).

1. 액세스 제한의 유효성을 검사하려면 **[!UICONTROL Authorization]** 헤더가 있거나 없는 배달 API 요청을 시작합니다.
   * IMS 전달자 토큰이 없거나 제공된 IMS 전달자 토큰이 자산에 대한 액세스 권한이 부여된 사용자(직접 또는 그룹 멤버십을 통해)에게 속하지 않는 경우 응답에서 `404` 오류 상태 코드를 생성합니다.
   * IMS 전달자 토큰이 자산에 대한 액세스 권한이 부여된 사용자 또는 그룹 중 하나인 경우 응답에서 자산의 이진 내용이 포함된 `200` 성공 상태 코드를 생성합니다.

### Publish 서비스에서 사용자 지정 ID 공급자에 대한 게재 {#delivery-custom-identity-provider}

OpenAPI 라이선스가 있는 AEM Sites, AEM Assets 및 Dynamic Media을 함께 사용할 수 있으며 AEM Publish 또는 미리보기 서비스를 통해 제공되는 웹 사이트에서 제한된 에셋 전달을 구성할 수 있습니다.
AEM Sites의 Publish 및 미리보기 서비스가 [사용자 지정 ID 공급자(IdP)](https://experienceleague.adobe.com/en/docs/experience-manager-learn/cloud-service/authentication/saml-2-0)를 사용하도록 구성된 경우 설정 프로세스 중에 보안 자산에 대한 액세스 권한이 있어야 하는 그룹이 `groupMembership` 특성에 포함될 수 있습니다.\
웹 사이트 사용자가 사용자 지정 ID 공급자에 로그온하여 Publish/미리보기 서비스에서 호스팅되는 웹 사이트에 액세스하면 `groupMembership` 특성이 읽히고 보안 쿠키가 만들어지고 웹 사이트에 전달된 후 인증이 성공적으로 게시됩니다. 이 보안 쿠키는 사용자 에이전트에게 웹 사이트 콘텐츠를 전달하기 위한 모든 후속 요청에 포함됩니다.

페이지에서 보안 자산이 요청되면 AEM Publish 및 미리보기 계층은 보안 쿠키에서 인증 자료를 추출하고 액세스를 확인합니다. 일치하는 항목이 있으면 자산이 표시됩니다.

>[!NOTE]
>
> [OpenAPI 기능을 사용하여 Dynamic Media을 활성화하는 지원 티켓](/help/assets/dynamic-media-open-apis-overview.md#how-to-enable-the-dynamic-media-with-openapi-capabilities)에서 사용 사례에 제한된 게재를 언급하십시오. Adobe 엔지니어링은 제한된 게재를 위한 필요한 설명 및/또는 프로세스 설정을 도와줍니다.