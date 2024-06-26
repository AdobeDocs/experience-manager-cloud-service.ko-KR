---
title: Experience Manager에서 에셋 전달 제한
description: 에서 에셋 전달을 제한하는 방법 알아보기 [!DNL Experience Manager].
role: User
source-git-commit: 540aa876ba7ea54b7ef4324634f6c5e220ad19d3
workflow-type: tm+mt
source-wordcount: '1125'
ht-degree: 0%

---

# 에서 에셋에 대한 액세스 제한 [!DNL Experience Manager] {#restrict-access-to-assets}

Experience Manager의 중앙 자산 거버넌스를 사용하면 DAM 관리자 또는 브랜드 관리자가 자산에 대한 액세스를 관리할 수 있습니다. 작성 측, 특히 AEM as a Cloud Service 작성자 인스턴스에서 승인된 에셋에 대한 역할을 구성하여 액세스를 제한할 수 있습니다.

사용자 [검색 중](search-assets-api.md) 또는 활용 [게재 URL](deliver-assets-apis.md) 은 인증 프로세스를 성공적으로 통과하면 제한된 에셋에 액세스할 수 있습니다.

![자산에 대한 제한된 액세스](/help/assets/assets/restricted-access.png)

## IMS 토큰을 사용한 제한된 게재 {#restrict-delivery-ims-token}

Experience Manager 시 IMS를 통한 제한된 전달에는 두 가지 주요 단계가 포함됩니다.

* 작성
* 제공

### 작성 {#authoring}

내에서 에셋 전달을 제한할 수 있습니다. [!DNL Experience Manager] 역할 기반. 역할을 구성하려면 다음 단계를 수행하십시오.

1. 로 이동 [!DNL Experience Manager] DAM 관리자로서.
1. 역할을 구성해야 하는 자산을 선택합니다.
1. 다음으로 이동 **[!UICONTROL 속성]** > **[!UICONTROL 고급]**, 및 **[!UICONTROL 역할]** 필드가 다음에 있음: [!UICONTROL 고급 메타데이터] 탭.

   ![역할 메타데이터](/help/assets/assets/roles_metadata.jpg)
필드를 사용할 수 없는 경우 다음 단계를 사용하여 필드를 추가합니다.

   1. 다음으로 이동 **[!UICONTROL 도구]** > **[!UICONTROL Assets]** > **[!UICONTROL 메타데이터 스키마]**.
   1. 메타데이터 스키마를 선택하고 **[!UICONTROL 편집 _마._]**.
   1. 추가 **[!UICONTROL 다중 값 텍스트]** 의 필드 **[!UICONTROL 양식 작성]** 섹션에 있는 마지막 항목이 될 필요가 없습니다.
   1. 새로 추가한 필드를 클릭한 다음  **[!UICONTROL 설정]** 패널:
      1. 변경 **[!UICONTROL 필드 레이블]** 끝 _역할_.
      1. 업데이트 **[!UICONTROL 속성에 매핑]** 끝 _./jcr:content/metadata/dam:roles_.

1. 에셋의 역할 메타데이터에 추가할 IMS 그룹을 가져옵니다. IMS 그룹을 가져오려면 다음 단계를 따르십시오.
   1. https://adminconsole.adobe.com/에 로그인합니다.
   1. 해당 조직으로 이동한 다음 로 이동합니다. **[!UICONTROL 사용자 그룹]**.
   1. 다음 항목 선택 **[!UICONTROL 사용자 그룹]** 다음을 추가하고 추출해야 합니다. **[!UICONTROL orgID]** 및 **[!UICONTROL 사용자 그룹 ID]** 을 사용하거나 조직 ID를 사용하십시오. `{orgID}@AdobeOrg:{usergroupID}`.

1. 에 그룹 ID 추가 **[!UICONTROL 역할]** 자산 속성 필드. <br>
에 정의된 그룹 ID **[!UICONTROL 역할]** 필드는 에셋에 액세스할 수 있는 유일한 사용자입니다. IMS 클라이언트 ID 및 IMS 프로필 ID를에 추가할 수도 있습니다. **[!UICONTROL 역할]** 필드. 예: `{orgId}@AdobeOrg:{profileId}`

   >[!NOTE]
   >
   >새 Assets 보기의 경우 폴더 수준까지만 액세스 권한을 부여할 수 있으며 개별 사용자가 아닌 그룹에만 액세스 권한을 부여할 수 있습니다. 자세히 알아보기 [Experience Manager Assets 내 권한 관리](https://experienceleague.adobe.com/en/docs/experience-manager-assets-essentials/help/get-started-admins/folder-access/manage-permissions).

   >[!VIDEO](https://video.tv.adobe.com/v/3427429)

#### 설정 및 해제 날짜 및 시간을 사용하여 에셋 게재 제한 {#restrict-delivery-assets-date-time}

DAM 작성자는 에셋 속성에서 사용할 수 있는 활성화 켜기 또는 끄기 시간을 정의하여 에셋 전달을 제한할 수도 있습니다.

에셋의 활성화를 위해 설정 시간을 정의하는 경우 정의된 시간에 에셋에 대한 게재 URL이 생성됩니다. 자산은 정의된 시간 이전에 비활성 상태로 유지됩니다. 마찬가지로, 에셋에 대해 해제 시간을 정의하는 경우 에셋은 정의된 시간에 비활성화되고 에셋의 게재 URL은 에셋 표시를 중단합니다.

다음 단계를 실행하여 에셋의 켜기 및 끄기 시간을 설정합니다.

1. 에셋을 선택하고 **[!UICONTROL 속성]**.

1. 다음에서 **[!UICONTROL 예약된 (비) 활성화]** 의 섹션 **[!UICONTROL 기본]** 탭에서 요구 사항에 따라 설정 시간 또는 해제 시간을 정의합니다.

마찬가지로 Assets 보기에서 에셋을 선택하고 **[!UICONTROL 세부 사항]** 에셋 속성을 보고 설정 시간 및 해제 시간을 정의합니다.

필드는 기본 메타데이터 양식에서 사용할 수 있습니다. 에셋이 기본 메타데이터 스키마를 기반으로 하지 않으며 에셋 속성에서 설정 시간 및 해제 시간 필드를 사용할 수 없는 경우 관리자 보기에서 다음 단계를 수행하십시오.

1. 다음으로 이동 **[!UICONTROL 도구]** > **[!UICONTROL Assets]** > **[!UICONTROL 메타데이터 스키마]**.
1. 메타데이터 스키마를 선택하고 **[!UICONTROL 편집]**.
1. 추가 **[!UICONTROL 날짜]** 의 필드 **[!UICONTROL 양식 작성]** 섹션에 있는 마지막 항목이 될 필요가 없습니다.
1. 새로 추가한 필드를 클릭한 다음  **[!UICONTROL 설정]** 패널:
   1. 변경 **[!UICONTROL 필드 레이블]** 끝 **정시** 또는 **해제 시간**.
   1. 업데이트 **[!UICONTROL 속성에 매핑]** 끝 _./jcr:content/onTime_ 대상 **정시** 필드 및 _./jcr:content/offTime_ 대상 **해제 시간** 필드.
1. **[!UICONTROL 저장]**&#x200B;을 클릭합니다.

마찬가지로, Assets 보기의 경우 에셋이 기본 메타데이터 스키마를 기반으로 하지 않으며 에셋 속성에서 설정 시간 및 해제 시간 필드를 사용할 수 없는 경우 다음 단계를 실행합니다.

1. 클릭 **[!UICONTROL 메타데이터 Forms]** 다음에서 **[!UICONTROL 설정]** 섹션.
1. 메타데이터 양식을 선택하고 **[!UICONTROL 편집]**.
1. 추가 **[!UICONTROL 날짜]** 의 필드 **[!UICONTROL 구성 요소]** 섹션에 있는 섹션을 참조하십시오.
1. 새로 추가한 필드를 클릭하고 **[!UICONTROL 레이블]** 끝 **정시** 또는 **해제 시간**.
1. 업데이트 **[!UICONTROL 메타데이터 속성]** 끝 _./jcr:content/onTime_ 대상 **정시** 필드 및 _./jcr:content/offTime_ 대상 **해제 시간** 필드.
1. **[!UICONTROL 저장]**&#x200B;을 클릭합니다.



### 제한된 에셋 전달 {#delivery-restricted-assets}

제한된 에셋의 전달은 에셋에 액세스할 수 있는 성공적인 인증을 기반으로 합니다. 요청이 AEM 작성자 인스턴스 또는 에셋 선택기에서 전송된 경우 인증은 IMS 토큰을 기반으로 하거나 Publish 또는 미리보기 인스턴스에 사용자 지정 ID 공급자를 설정한 경우 특수 쿠키를 기반으로 합니다.

#### AEM 작성자 또는 자산 선택기 요청 게재 {#delivery-aem-author-asset-selector}

AEM 작성자 인스턴스 또는 에셋 선택기에서 요청이 전송되는 경우 제한된 에셋의 전달을 활성화하려면 유효한 IMS 토큰이 필요합니다. 다음 단계를 수행합니다.

1. [액세스 토큰 생성](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/generating-access-tokens-for-server-side-apis.html?lang=en#generating-the-access-token).
   * AEM as a Cloud Service 환경의 개발 콘솔에 로그인합니다.

   * 다음으로 이동 **[!UICONTROL 환경]** > **[!UICONTROL 통합]** > **[!UICONTROL 로컬 토큰]** > **[!UICONTROL 로컬 개발 토큰 가져오기]** > **[!UICONTROL accessToken 값 복사]**. 자세히 알아보기 [토큰 및 관련 측면에 액세스하는 방법](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/generating-access-tokens-for-server-side-apis.html?lang=en#generating-the-access-token)

1. 획득한 액세스 토큰을 **[!UICONTROL 인증]** 헤더, 해당 값 접두사 사용 **[!UICONTROL 전달자]**.

1. 요청을 시작하여 액세스 토큰의 기능을 확인합니다. IMS 액세스 토큰이 없거나 제공된 액세스 토큰에 자산의 메타데이터에 추가된 것과 동일한 주체 또는 그룹이 없는 경우 404 오류를 산출해야 합니다.

#### Publish 인스턴스의 사용자 지정 ID 공급자에 대한 게재 {#delivery-custom-identity-provider}

Publish 또는 미리보기 인스턴스에 설정된 사용자 정의 ID 공급자의 경우 내의 보안 에셋에 대한 액세스 권한이 있어야 하는 그룹을 언급할 수 있습니다 `groupMembership` 속성 을 설정합니다. 다음을 통해 사용자 정의 ID 공급자에 로그온할 때 [SAML 통합](https://experienceleague.adobe.com/en/docs/experience-manager-learn/cloud-service/authentication/saml-2-0), `groupMembership` 속성을 읽고 모든 인증 요청에서 전송되는 쿠키를 구성하는 데 사용됩니다. 이는 AEM 작성자 또는 자산 선택기의 요청 시 IMS 토큰과 유사합니다.

보안 자산을 페이지에서 사용할 수 있고 게재 URL에 자산 렌더링이 요청되면 AEM은 쿠키 또는 IMS 토큰에 있는 역할을 확인하여 와 일치시킵니다. `dam:roles property` 에셋을 작성하는 동안 적용됩니다. 일치하는 항목이 있으면 자산이 표시됩니다.

>[!NOTE]
>
> 다음에서 [OpenAPI 기능을 사용하여 Dynamic Media을 활성화하는 티켓 지원](/help/assets/dynamic-media-open-apis-overview.md#how-to-enable-the-dynamic-media-with-openapi-capabilities)사용 사례에서 제한된 게재를 언급하십시오. Adobe 엔지니어링은 제한된 게재를 위한 필요한 설명 및/또는 프로세스 설정을 도와줍니다.
