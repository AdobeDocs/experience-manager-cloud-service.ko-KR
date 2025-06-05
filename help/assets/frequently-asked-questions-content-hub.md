---
title: Content Hub 자주 묻는 질문 (FAQ)
description: Content Hub에 대한 가장 자주 묻는 질문(FAQ)에 대한 답변을 받아 보십시오.
exl-id: 74b5c308-c1d3-4787-9f1f-f64cf09d298a
source-git-commit: 95c643151e4828fa2eae0725dc1081aeeabc42fb
workflow-type: ht
source-wordcount: '1367'
ht-degree: 100%

---

# Content Hub 자주 묻는 질문 {#content-hub-frequently-asked-questions}

<table>
    <tr>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>신규</i></sup> <a href="/help/assets/dynamic-media/dm-prime-ultimate.md"><b>Dynamic Media Prime 및 Ultimate</b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>신규</i></sup> <a href="/help/assets/assets-ultimate-overview.md"><b>AEM Assets Ultimate</b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>신규</i></sup> <a href="/help/assets/integrate-aem-assets-edge-delivery-services.md"><b>Edge Delivery Services와의 AEM Assets 통합</b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>신규</i></sup> <a href="/help/assets/aem-assets-view-ui-extensibility.md"><b>UI 확장성</b></a>
        </td>
          <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>신규</i></sup> <a href="/help/assets/dynamic-media/enable-dynamic-media-prime-and-ultimate.md"><b>Dynamic Media Prime 및 Ultimate 활성화</b></a>
        </td>
    </tr>
    <tr>
        <td>
            <a href="/help/assets/search-best-practices.md"><b>모범 사례 검색</b></a>
        </td>
        <td>
            <a href="/help/assets/metadata-best-practices.md"><b>메타데이터 모범 사례</b></a>
        </td>
        <td>
            <a href="/help/assets/product-overview.md"><b>Content Hub</b></a>
        </td>
        <td>
            <a href="/help/assets/dynamic-media-open-apis-overview.md"><b>OpenAPI 기능이 포함된 Dynamic Media</b></a>
        </td>
        <td>
            <a href="https://developer.adobe.com/experience-cloud/experience-manager-apis/"><b>AEM Assets 개발자 설명서</b></a>
        </td>
    </tr>
</table>

![Content Hub 자주 묻는 질문](assets/content-hub-faqs.png)

>[!AVAILABILITY]
>
>Content Hub 안내서가 이제 PDF 포맷으로 제공됩니다. 전체 안내서를 다운로드하고 Adobe Acrobat AI 어시스턴트를 사용하여 쿼리에 답변합니다.
>
>[!BADGE Content Hub 안내서 PDF]{type=Informative url="https://helpx.adobe.com/kr/content/dam/help/en/experience-manager/aem-assets/content-hub.pdf"}

## Content Hub란 무엇입니까? {#what-is-content-hub}

Content Hub는 Adobe Experience Manager Assets as a Cloud Service의 기능 중 하나입니다.

Content Hub를 통해 더 광범위한 팀이 직관적인 포털을 사용해 관련성 있고 승인된 자산을 쉽게 발견하고 필요에 따라 신속하게 자산을 조정할 수 있습니다.  또한 Content Hub는 사용자가 자산을 DAM에 업로드할 때 셀프서비스를 쉽게 이용할 수 있는 수집 메커니즘을 제공합니다. 이는 브랜드 일관성과 적절한 안전장치 준수를 유지하면서 콘텐츠 제작 속도를 높이고자 하는 조직의 요구를 직접적으로 충족할 수 있습니다.

## Cloud Manager 프로그램/환경에서 Content Hub를 활성화할 수 없는 이유는 무엇입니까? {#cannot-enable-content-hub}

현재 Content Hub는 자산 라이선스(Assets Cloud Service, Assets Ultimate, Assets Prime)를 포함한 AEM Cloud Manager 프로덕션 프로그램에서만 사용할 수 있습니다. [Content Hub](/help/assets/deploy-content-hub.md#enable-content-hub)를 클릭하여 활성화하면 Content Hub가 배포되고 해당 프로그램의 AEM 작성 프로덕션 환경과 연결됩니다. 자세한 내용과 사전 요구 사항은 [Content Hub 배포](/help/assets/deploy-content-hub.md)를 참조하십시오.

## 프로덕션 프로그램/환경에서 Content Hub를 활성화했는데, 비활성화할 수 있습니까? {#can-i-disable-content-hub}

프로덕션 프로그램에서 Content Hub를 활성화하면 프로덕션 인프라의 일부가 배포됩니다. AEM Cloud Manager는 사람의 실수로 인한 프로덕션 사용 위험을 최소화하기 위해 프로덕션 인프라를 제거하거나 비활성화할 수 없습니다.

Content Hub가 배포된 후 사용자에게 Content Hub를 제공하지 않으려면 Admin Console의 Content Hub 제품 프로필에 사용자를 할당하지 마십시오. 자세한 내용은 [Content Hub 배포](/help/assets/deploy-content-hub.md#content-hub-instance-product-profile)를 참조하십시오.

## Content Hub를 프로덕션 프로그램/프로덕션 작성 환경에서만 사용할 수 있는데 조직에서 Content Hub를 어떻게 평가할 수 있습니까? {#how-can-i-evaluate-content-hub}

Content Hub는 Adobe가 제공하고 유지 관리하는 기능으로, 개발/스테이징/프로덕션을 통해 일반적인 검증이 필요한 사용자 정의 코드가 없습니다. 또한 사용자용 기능에 대한 액세스 권한을 관리자가 완전히 제어하므로 모든 사용자에게 공개하지 않고도 평가할 수 있습니다.

AEM as a Cloud Service Assets에서 관리되는 사용자/프로덕션 콘텐츠에 영향을 미치지 않고 Content Hub를 평가할 수 있습니다. 평가 절차는 다음과 같습니다.

* 프로덕션 환경(Cloud Manager 프로그램)에서 [Content Hub 활성화](/help/assets/deploy-content-hub.md#enable-content-hub)
* 프로덕션 작성부터 Content Hub 제품 프로필까지 [AEM 관리자 사용자 추가](/help/assets/deploy-content-hub.md#onboard-content-hub-administrator).
* AEM 관리자 [Content Hub 구성](/help/assets/configure-content-hub-ui-options.md)
* AEM 프로덕션 작성자의 AEM 관리자 또는 AEM 사용자가 [Content Hub에 대한 여러 자산을 승인](/help/assets/approve-assets-content-hub.md)합니다. DAM에서 프로덕션 콘텐츠를 변경하지 않으려면 AEM 작성자 인스턴스에 별도의 평가 폴더를 만들고 DAM에서 일부 자산을 해당 폴더로 업로드/태그 또는 복사할 수 있습니다.
* Admin Console 관리자가 [일부 사용자를 선택해](/help/assets/deploy-content-hub.md#onboard-content-hub-users) Content Hub 제품 프로필에 추가하여 평가를 시작하도록 할 수 있습니다.
* 평가가 완료되면 작성자 인스턴스의 AEM 사용자가 테스트 자산에서 승인을 제거하고, Content Hub의 프로덕션 자산을 승인하면 Admin Console 관리자가 Content Hub 및 승인된 콘텐츠에 액세스해야 하는 모든 사용자를 추가할 수 있습니다. 축하합니다. 이제 Content Hub가 활성화되었습니다.

샌드박스 프로그램 및 해당 작성 프로덕션 환경에 Content Hub에 대한 얼리 액세스 프로그램이 있습니다. 자세한 내용은 [샌드박스 프로그램 소개](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/introduction-sandbox-programs.md)를 참조하십시오. 얼리 액세스 프로그램에 대해 자세히 알아보려면 Adobe 계정 팀에 문의하십시오.

Content Hub는 비프로덕션 환경(스테이징 및 개발)에서 아직 사용할 수 없습니다. Assets Ultimate의 스테이징/개발 환경은 2025년 3월에 출시될 예정입니다.

## Content Hub에 로그인한 후 자산이 표시되지 않는 이유는 무엇입니까? {#no-assets-in-content-hub}

Assets as a Cloud Service에 승인됨으로 표시된 자산은 Content Hub에서 자동으로 사용할 수 있습니다. Content Hub에 로그인한 후 자산이 보이지 않는 경우, AEM as a Cloud Service 작성자 환경을 사용하여 자산을 승인하면 Content Hub에서 사용할 수 있습니다. 자세한 내용은 [Content Hub에 대한 자산 승인](/help/assets/approve-assets-content-hub.md)을 참조하십시오.

## Content Hub로 직접 업로드하거나 Content Hub로 Dropbox 또는 OneDrive 계정에서 가져온 자산이 표시되지 않는 이유는 무엇입니까? {#no-assets-uploaded-from-content-hub}

Content Hub를 사용하여 업로드한 자산의 표시는 구성 사용자 인터페이스에서 사용 가능한 [자동 승인](/help/assets/configure-content-hub-ui-options.md#configure-import-options-content-hub) 토글을 활성화했는지 여부에 따라 달라집니다.

* **자동 승인** 토글이 활성화되어 있으면 Content Hub를 사용하여 업로드한 자산을 자동으로 사용할 수 있습니다.

* **자동 승인** 토글을 비활성화하면 Content Hub를 사용하여 업로드한 자산이 자동으로 표시되지 않습니다. 자산은 Assets as a Cloud Service 환경의 `hydrated-assets` 폴더에서 사용할 수 있습니다. 폴더로 이동하여 해당 자산을 `Approved` 상태로 [일괄 편집](/help/assets/approve-assets-content-hub.md)하여 Content Hub에 표시할 수 있습니다.

## AEM as a Cloud Service 환경에서 Content Hub를 사용하여 업로드한 자산을 빠르게 찾는 방법은 무엇입니까? {#find-uploaded-assets-on-aem-cloud}

다음에서 AEM as a Cloud Service 환경에서 Content Hub를 사용하여 업로드한 자산을 빠르게 찾을 수 있습니다.

1. `hydrated-assets` 폴더로 이동.

1. **[!UICONTROL 필터]**&#x200B;를 클릭하여 **[!UICONTROL 자산 상태]** 필드에 **[!UICONTROL 상태 없음]**&#x200B;을 설정.

1. **[!UICONTROL 수정 날짜]** 필드를 사용하여 자산 정렬.

## 자산 카드에서 Adobe Express 옵션을 사용하여 편집 내용을 조회하고 자산을 리믹스하여 새로운 변형을 만들 수 없는 이유는 무엇입니까? {#edit-using-express-not-available}

자산 카드에서 **Adobe Express 옵션을 사용하여 편집**&#x200B;한 내용을 조회하려면 [Content Hub 사용자가 자산을 리믹스하여 새 변형을 만들 수 있는 권한](#onboard-content-hub-users-add-assets) 외에도 해당 사용자에게 Adobe Express Enterprise 또는 Teams 권한([플랜](https://www.adobe.com/kr/express/pricing) 참조)이 있어야 합니다.

사용자가 [!DNL Content Hub] 및 [!DNL Adobe Express]에 할당되는 방식에는 다음과 같은 몇 가지 구성이 있습니다.

1. 조직이 [Assets Ultimate](/help/assets/assets-ultimate-overview.md) 또는 [Assets Prime](/help/assets/assets-prime.md) 라이선스를 보유하고 있으며, 사용자는 Adobe Express 권한(공동 작업자 또는 파워 유저)이 포함된 Admin console의 Experience Manager 프로필 중 하나에 할당되어 있습니다. 추가 구성 없이도 통합이 가능합니다.

1. [!DNL Adobe Express]가 [!DNL Content Hub]를 포함하는 [!DNL Experience Manager Assets]와 동일한 [!DNL Adobe Admin Console]에서 배포됩니다. 추가 구성 없이도 통합이 가능합니다.

1. [!DNL Adobe Express]가 [!DNL Content Hub]를 포함하는 [!DNL Experience Manager Assets]와 다른 [!DNL Adobe Admin Console]에서 배포됩니다. 이 경우 [!DNL Assets] 관리자는 통합이 작동하도록 이를 구성할 수 있습니다([설명서](/help/assets/connect-assets-with-creative-cloud.md) 참조).

   >[!NOTE]
   >
   >두 개의 Admin Console에서 Express 및 Assets 제품 프로필에 할당된 사용자는 동일한 이메일 주소를 가져야 하고, 비즈니스 **기업 또는 학교** 계정을 사용해야 하며, **개인** 계정을 사용해서는 안 됩니다. 이상적인 구성은 두 Admin Console을 모두 **Federated ID**&#x200B;로 설정하고 두 콘솔 간 트러스트 관계를 설정하여 사용자에게 원활한 SSO(Single Sign-On) 경험을 제공하도록 하는 것입니다. 일부 Express 플랜(예: Express Teams)은 Federated ID/SSO(Single Sign-On)를 지원하지 않습니다.

적절한 제품 권한 외에도 Content Hub에서 Adobe Express를 통합하려면 할당된 사용자에게 적어도 Content Hub를 구동하는 Assets 작성자 환경에서의 [!UICONTROL 편집 가능] 권한이 있어야 하며, 최소한 Content Hub 사용자가 Express를 사용하여 제작한 콘텐츠를 저장할 수 있는 **[#UICONTROL /content/dam/hydrated-assets/]** 폴더 계층 구조가 있어야 합니다. 관리자 보기(터치 UI)에서 [권한 관리](/help/security/touch-ui-principal-view.md)를 확인하거나 [자산 보기에서 간소화된 권한 관리](https://experienceleague.adobe.com/ko/docs/experience-manager-assets-essentials/help/get-started-admins/folder-access/manage-permissions)를 확인하십시오.

## 조직의 브랜드 지침이 홈 페이지에 링크로 표시되도록 Content Hub를 설정할 수 있습니까? {#content-hub-setup-brand-guidelines}

Content Hub 홈 페이지의 모든 표준 자산, 컬렉션 및 인사이트 탭 외에 사용자 정의 링크를 별도의 탭으로 추가할 수 있습니다. 설정 방법에 대한 자세한 내용은 [사용자 정의 링크](/help/assets/configure-content-hub-ui-options.md#configure-custom-links-content-hub)를 참조하십시오.

## 기존 Brand Portal 고객을 Content Hub로 마이그레이션할 계획이 있습니까? {#migration-brand-portal}

Adobe는 Adobe 지원 티켓을 생성하여 사용할 수 있는 Brand Portal에서 Content Hub로의 마이그레이션 지원을 제공합니다.

## Content Hub에서 제품 설정/구성 옵션이 표시되지 않는 이유는 무엇입니까? {#ui-configuration-option-missing}

[구성 사용자 인터페이스](/help/assets/configure-content-hub-ui-options.md)에 액세스하려면 [Content Hub 관리자](/help/assets/deploy-content-hub.md##onboard-content-hub-administrator)여야 합니다. Adobe Admin Console의 프로덕션 작성자 인스턴스에서 AEM 관리자 제품 프로필에 할당되었지만 여전히 구성 옵션이 표시되지 않는 경우, AEM 관리자 제품 프로필의 이름이 변경되지 않았는지 확인합니다. 자세한 내용은 [AEM as a Cloud Service 팀 및 제품 프로필](/help/onboarding/aem-cs-team-product-profiles.md)을 참조하십시오.
