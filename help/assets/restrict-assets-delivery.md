---
title: Experience Manager에서 에셋 전달 제한
description: ' [!DNL Experience Manager]에서 에셋 전달을 제한하는 방법에 대해 알아봅니다.'
role: User
exl-id: 3fa0b75d-c8f5-4913-8be3-816b7fb73353
source-git-commit: 16b313a4fb79f915613044d12d29e618209113ec
workflow-type: tm+mt
source-wordcount: '1125'
ht-degree: 0%

---

# [!DNL Experience Manager]의 자산에 대한 액세스 제한 {#restrict-access-to-assets}

Experience Manager의 중앙 자산 거버넌스를 사용하면 DAM 관리자 또는 브랜드 관리자가 자산에 대한 액세스를 관리할 수 있습니다. 작성 측, 특히 AEM as a Cloud Service 작성자 인스턴스에서 승인된 에셋에 대한 역할을 구성하여 액세스를 제한할 수 있습니다.

사용자 [검색](search-assets-api.md) 또는 [배달 URL](deliver-assets-apis.md)을(를) 사용하는 사용자는 인증 프로세스를 통과하면 제한된 자산에 액세스할 수 있습니다.

![자산에 대한 액세스 제한](/help/assets/assets/restricted-access.png)

## IMS 토큰을 사용한 제한된 게재 {#restrict-delivery-ims-token}

Experience Manager Assets에서 IMS를 통한 제한된 전달에는 두 가지 주요 단계가 포함됩니다.

* 작성
* 제공

### 작성 {#authoring}

역할에 따라 [!DNL Experience Manager] 내의 자산 배달을 제한할 수 있습니다. 역할을 구성하려면 다음 단계를 수행하십시오.

1. DAM 관리자로 [!DNL Experience Manager](으)로 이동합니다.
1. 역할을 구성해야 하는 자산을 선택합니다.
1. **[!UICONTROL 속성]** > **[!UICONTROL 고급]**(으)로 이동하고 [!UICONTROL 고급 메타데이터] 탭에 **[!UICONTROL 역할]** 필드가 있는지 확인합니다.

   ![역할 메타데이터](/help/assets/assets/roles_metadata.jpg)
필드를 사용할 수 없는 경우 다음 단계를 사용하여 필드를 추가합니다.

   1. **[!UICONTROL 도구]** > **[!UICONTROL Assets]** > **[!UICONTROL 메타데이터 스키마]**&#x200B;로 이동합니다.
   1. 메타데이터 스키마를 선택하고 **[!UICONTROL 편집 __]**을(를) 클릭합니다.
   1. 오른쪽의 **[!UICONTROL 양식 작성]** 섹션에서 **[!UICONTROL 다중 값 텍스트]** 필드를 양식의 메타데이터 섹션에 추가합니다.
   1. 새로 추가한 필드를 클릭한 다음 **[!UICONTROL 설정]** 패널에서 다음 업데이트를 수행합니다.
      1. **[!UICONTROL 필드 레이블]**&#x200B;을(를) _역할_(으)로 변경합니다.
      1. **[!UICONTROL 속성에 매핑]**&#x200B;을(를) _(으)로 업데이트합니다./jcr:content/metadata/dam:roles_.

1. 에셋의 역할 메타데이터에 추가할 IMS 그룹을 가져옵니다. IMS 그룹을 가져오려면 다음 단계를 따르십시오.
   1. `https://adminconsole.adobe.com/.`에 로그인
   1. 해당 조직으로 이동한 다음 **[!UICONTROL 사용자 그룹]**(으)로 이동합니다.
   1. 추가해야 하는 **[!UICONTROL 사용자 그룹]**&#x200B;을(를) 선택하고 URL에서 **[!UICONTROL 조직 ID]** 및 **[!UICONTROL 사용자 그룹 ID]**&#x200B;을(를) 추출하거나 조직 ID(예: `{orgID}@AdobeOrg:{usergroupID}`)를 사용하십시오.

1. 그룹 ID를 자산 속성의 **[!UICONTROL 역할]** 필드에 추가하십시오. <br>
**[!UICONTROL 역할]** 필드에 정의된 그룹 ID만 자산에 액세스할 수 있습니다. **[!UICONTROL 역할]** 필드에 IMS 클라이언트 ID와 IMS 프로필 ID를 추가할 수도 있습니다. 예: `{orgId}@AdobeOrg:{profileId}`

   >[!NOTE]
   >
   >새 Assets 보기의 경우 폴더 수준까지만 액세스 권한을 부여할 수 있으며 개별 사용자가 아닌 그룹에만 액세스 권한을 부여할 수 있습니다. [Experience Manager Assets 내 권한 관리](https://experienceleague.adobe.com/en/docs/experience-manager-assets-essentials/help/get-started-admins/folder-access/manage-permissions)에 대해 자세히 알아보세요.

   >[!VIDEO](https://video.tv.adobe.com/v/3427429)

#### 설정 및 해제 날짜 및 시간을 사용하여 에셋 게재 제한 {#restrict-delivery-assets-date-time}

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



### 제한된 에셋 전달 {#delivery-restricted-assets}

제한된 에셋의 전달은 에셋에 액세스할 수 있는 성공적인 인증을 기반으로 합니다. 요청이 AEM 작성자 인스턴스 또는 에셋 선택기에서 전송된 경우 인증은 IMS 토큰을 기반으로 하거나 Publish 또는 미리보기 인스턴스에 사용자 지정 ID 공급자를 설정한 경우 특수 쿠키를 기반으로 합니다.

#### AEM 작성자 또는 자산 선택기 요청 게재 {#delivery-aem-author-asset-selector}

AEM 작성자 인스턴스 또는 에셋 선택기에서 요청이 전송되는 경우 제한된 에셋의 전달을 활성화하려면 유효한 IMS 토큰이 필요합니다. 다음 단계를 수행합니다.

1. [액세스 토큰 생성](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/generating-access-tokens-for-server-side-apis.html?lang=en#generating-the-access-token).
   * AEM as a Cloud Service 환경의 개발 콘솔에 로그인합니다.

   * **[!UICONTROL 환경]** > **[!UICONTROL 통합]** > **[!UICONTROL 로컬 토큰]** > **[!UICONTROL 로컬 개발 토큰 가져오기]** > **[!UICONTROL 액세스 토큰 값 복사]**&#x200B;로 이동합니다. [토큰 및 관련 측면에 액세스하는 방법](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/generating-access-tokens-for-server-side-apis.html?lang=en#generating-the-access-token)에 대해 자세히 알아보기

1. 가져온 액세스 토큰을 **[!UICONTROL Authorization]** 헤더에 통합하여 해당 값이 **[!UICONTROL Bearer]** 접두사로 추가되었는지 확인하십시오.

1. 요청을 시작하여 액세스 토큰의 기능을 확인합니다. IMS 액세스 토큰이 없거나 제공된 액세스 토큰에 자산의 메타데이터에 추가된 것과 동일한 주체 또는 그룹이 없는 경우 404 오류를 산출해야 합니다.

#### Publish 인스턴스의 사용자 지정 ID 공급자에 대한 게재 {#delivery-custom-identity-provider}

Publish 또는 미리보기 인스턴스에 설정된 사용자 지정 ID 공급자의 경우 설정 프로세스 중에 `groupMembership` 특성 내의 보안 자산에 대한 액세스 권한이 있어야 하는 그룹을 언급할 수 있습니다. [SAML 통합](https://experienceleague.adobe.com/en/docs/experience-manager-learn/cloud-service/authentication/saml-2-0)을 통해 사용자 지정 ID 공급자에 로그온하면 `groupMembership` 특성을 읽고 쿠키를 구성하는 데 사용됩니다. 이 쿠키는 AEM 작성자 또는 자산 선택기의 요청 시 IMS 토큰과 유사하게 인증을 위한 모든 요청에서 전송됩니다.

페이지에서 보안 에셋을 사용할 수 있고 에셋을 렌더링하도록 게재 URL에 요청이 이루어지면 AEM은 쿠키 또는 IMS 토큰에 있는 역할을 확인하여 에셋을 작성하는 동안 적용된 `dam:roles property`과(와) 일치합니다. 일치하는 항목이 있으면 자산이 표시됩니다.

>[!NOTE]
>
> [OpenAPI 기능을 사용하여 Dynamic Media을 활성화하는 지원 티켓](/help/assets/dynamic-media-open-apis-overview.md#how-to-enable-the-dynamic-media-with-openapi-capabilities)에서 사용 사례에 제한된 게재를 언급하십시오. Adobe 엔지니어링은 제한된 게재를 위한 필요한 설명 및/또는 프로세스 설정을 도와줍니다.
