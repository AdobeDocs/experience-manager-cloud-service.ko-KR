---
title: Brand Portal에 자산, 폴더 및 컬렉션 게시
description: Brand Portal에 자산, 폴더 및 컬렉션을 게시합니다.
contentOwner: Adobe
feature: Brand Portal, Asset Distribution, Configuration
role: User
exl-id: 1cc438bc-8cad-4421-af03-c1f6d750e0a8
source-git-commit: ab2cf8007546f538ce54ff3e0b92bb0ef399c758
workflow-type: tm+mt
source-wordcount: '1287'
ht-degree: 85%

---

# Publish assets를 Brand Portal으로 {#publish-assets-to-brand-portal}

| 버전 | 문서 링크 |
| -------- | ---------------------------- |
| AEM 6.5 | [여기 클릭](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/assets/brandportal/brand-portal-publish-assets) |
| AEM as a Cloud Service | 이 문서 |

AEM(Adobe Experience Manager) Assets 관리자는 자산, 폴더 및 컬렉션을 AEM Assets Brand Portal 인스턴스에 게시할 수 있습니다. 자산이나 폴더의 게시 워크플로우를 나중 날짜나 시간으로 예약할 수도 있습니다. 게시된 자산, 폴더 및 컬렉션은 Brand Portal 사용자가 액세스하고 다른 사용자에게 추가로 분배할 수 있습니다.

하지만 먼저 Brand Portal에서 AEM Assets를 구성해야 합니다. 자세한 내용은 [Brand Portal에서 AEM Assets 구성](configure-aem-assets-with-brand-portal.md)을 참조하십시오.

AEM Assets에서 원래 자산, 폴더 또는 컬렉션을 차후에 수정하는 경우 AEM Assets에서 다시 게시하기 전까지는 변경 내용이 Brand Portal에 반영되지 않습니다. 이 기능은 진행 중인 작업 변경 사항을 Brand Portal에서 사용할 수 없도록 합니다. 관리자가 게시한 승인된 변경 사항만 Brand Portal에서 사용할 수 있습니다.

* [Publish assets를 Brand Portal으로](#publish-assets-to-bp)
* [Publish 폴더를 Brand Portal으로](#publish-folders-to-brand-portal)
* [Brand Portal에 Publish 컬렉션](#publish-collections-to-brand-portal)

>[!NOTE]
>
>AEM 작성자가 초과 리소스를 차지하지 않도록 가급적이면 피크가 아닌 시간에, 시차 게시를 수행하는 것이 좋습니다.
>Assets은 일괄로 게시해야 합니다. 배치 크기에 대한 권장 사항은 15K입니다.
> [!DNL Experience Manager Assets]의 [!DNL Cloud Service]인 경우 랩 조건에서 관찰되는 전송 속도는 시간당 1,000개의 에셋입니다. 이 속도는 평균 10MB 에셋의 크기로 관찰됩니다.

## Publish assets를 Brand Portal으로 {#publish-assets-to-bp}

다음은 AEM Assets의 자산을 Brand Portal에 게시하는 절차입니다.

1. Assets 콘솔에서 상위 폴더를 열고 게시하려는 모든 자산을 선택하고 도구 모음에서 **[!UICONTROL 빠른 게시]** 옵션을 클릭합니다.

   ![publish2bp-2](assets/publish2bp.png)

1. 다음은 자산을 게시하는 두 가지 방법입니다.
   * [지금 게시](#publish-to-bp-now)(자산을 즉시 게시함)
   * [나중에 게시](#publish-to-bp-later)(자산 게시를 예약함)

### 지금 Publish 에셋 {#publish-to-bp-now}

선택한 자산을 Brand Portal에 게시하려면 다음 중 하나를 수행하십시오.

* 도구 모음에서 **[!UICONTROL 빠른 게시]**&#x200B;를 선택합니다. 그런 다음 메뉴에서 **[!UICONTROL Brand Portal에 게시]**&#x200B;를 클릭합니다.

* 도구 모음에서 **[!UICONTROL 게시 관리]**&#x200B;를 선택합니다.

   1. **[!UICONTROL 작업]**&#x200B;에서 **[!UICONTROL Brand Portal에 게시]**&#x200B;를 선택합니다.

      **[!UICONTROL 예약]**&#x200B;에서 **[!UICONTROL 지금]**&#x200B;을 선택합니다.

      **[!UICONTROL 다음]**&#x200B;을 클릭합니다.

   2. **[!UICONTROL 범위]**&#x200B;에서 선택 내용을 확인하고 **[!UICONTROL Brand Portal에 게시]**&#x200B;를 클릭합니다.

자산이 Brand Portal에 게시하기 위한 큐에 올라갔음을 나타내는 메시지가 나타납니다. Brand Portal 인터페이스에 로그인하여 게시된 자산을 확인합니다.

### 나중에 Publish 에셋 {#publish-to-bp-later}

나중 날짜 또는 시간에 Brand Portal에 자산을 게시하는 일정을 예약하려면,

1. 게시 일정을 예약하려는 자산을 선택하고 맨 위의 도구 모음에서 **[!UICONTROL 게시 관리]**&#x200B;를 클릭합니다.

1. **[!UICONTROL 게시 관리]** 페이지의 **[!UICONTROL 작업]**&#x200B;에서 **[!UICONTROL Brand Portal에 게시]**&#x200B;를 선택합니다.

   **[!UICONTROL 예약]**&#x200B;에서 **[!UICONTROL 나중에]**&#x200B;를 선택합니다.

   <!--![publishlaterbp-1](assets/publishlaterbp-1.png)-->

   ![나중에 게시](assets/publish-later.png)

1. **[!UICONTROL 활성화 날짜]**&#x200B;를 선택하고 시간을 지정합니다. **[!UICONTROL 다음]**&#x200B;을 클릭합니다.

1. **활성화 날짜**&#x200B;를 선택하고 시간을 지정합니다. **다음**&#x200B;을 클릭합니다.

1. **[!UICONTROL 워크플로우]**&#x200B;에서 **[!UICONTROL 워크플로우 제목]**&#x200B;을 지정합니다. **[!UICONTROL 나중에 게시]**&#x200B;를 클릭합니다.

   <!--![publishworkflow](assets/publishworkflow.png)-->

   ![워크플로 게시](assets/publish-workflow.png)

>[!NOTE]
>
> * DAM-Users 그룹의 기존 사용자 부분은 &quot;/conf/global/settings/cloudconfigs/mediaportal&quot; 경로에서 읽기 액세스 권한이 있습니다.
> * 새 사용자(또는 관리자가 아닌 사용자)는 brand portal에 게시하려면 다음 권한이 필요합니다.
> 경로:
> `"/conf/global/settings/cloudconfigs/mediaportal" : jcr:read `
>`/libs : jcr:read`
>`/conf : jcr:read`
>`/content : jcr:read, crx:replicate`
>`/content/dam/ : jcr:read,modify, crx:replicate`

## Publish 폴더를 Brand Portal으로 {#publish-folders-to-brand-portal}

자산 폴더를 즉시 게시 또는 게시 취소하거나 나중 날짜 또는 시간으로 예약할 수 있습니다.

### Publish 폴더를 Brand Portal으로 {#publish-folders-to-bp}

1. Assets 콘솔에서 게시하려는 폴더를 선택하고 도구 모음에서 **[!UICONTROL 빠른 게시]** 옵션을 클릭합니다.

   ![publish2bp](assets/publish2bp.png)

1. **지금 폴더 게시**

   선택한 폴더를 Brand Portal에 게시하려면 다음 중 하나를 수행하십시오.

   * 도구 모음에서 **[!UICONTROL 빠른 게시]**&#x200B;를 선택합니다.

     메뉴에서 **[!UICONTROL Brand Portal에 게시]**&#x200B;를 선택합니다.

   * 도구 모음에서 **[!UICONTROL 게시 관리]**&#x200B;를 선택합니다.

      1. **[!UICONTROL 작업]**&#x200B;에서 **[!UICONTROL Brand Portal에 게시]**&#x200B;를 선택합니다.

         **[!UICONTROL 예약]**&#x200B;에서 **[!UICONTROL 지금]**&#x200B;을 선택합니다.

         **다음**&#x200B;을 클릭합니다.

      1. **[!UICONTROL 범위]**&#x200B;에서 선택 내용을 확인하고 **[!UICONTROL Brand Portal에 게시]**&#x200B;를 클릭합니다.

   폴더가 Brand Portal에 게시하기 위한 큐에 올라갔음을 나타내는 메시지가 나타납니다. Brand Portal 인터페이스에 로그인하여 게시된 폴더를 확인합니다.

1. **나중에 Publish 폴더**
나중 날짜 또는 시간에 자산 폴더를 게시하는 일정을 예약하려면 다음 작업을 수행하십시오.

   1. 게시 일정을 예약하려는 폴더를 선택하고 맨 위의 도구 모음에서 **[!UICONTROL 게시 관리]**&#x200B;를 선택합니다.
   1. **[!UICONTROL 작업]**&#x200B;에서 **[!UICONTROL Brand Portal에 게시]**&#x200B;를 선택합니다.

      **[!UICONTROL 예약]**&#x200B;에서 **[!UICONTROL 나중에]**&#x200B;를 선택합니다.

   1. **[!UICONTROL 활성화 날짜]**&#x200B;를 선택하고 시간을 지정합니다. **[!UICONTROL 다음]**&#x200B;을 클릭합니다.

      <!--![publishlaterbp](assets/publishlaterbp.png)-->

   ![나중에 폴더 게시](assets/publish-later-folder.png)

   1. **[!UICONTROL 범위]**&#x200B;에서 선택 내용을 확인합니다. **[!UICONTROL 다음]**&#x200B;을 클릭합니다.

   1. **[!UICONTROL 워크플로우]**&#x200B;에서 워크플로우 제목을 지정합니다. **[!UICONTROL 나중에 게시]**&#x200B;를 클릭합니다.

      <!--![manageschedulepub](assets/manageschedulepub.png)-->

   ![워크플로 게시](assets/publish-workflow.png)

### Brand Portal에 게시된 파일 또는 폴더 보기 {#view-published-file-folder}

1. Brand Portal 인터페이스에 로그인하여 게시된 자산을 확인합니다(예약된 날짜 또는 시간에 따라 다름).

   ![bp_landingpage](assets/bp_landingpage.png)

1. 에셋의 현재 게시 상태를 보려면 목록 보기 ![목록 보기](assets/list-view.svg)(으)로 전환하십시오.

<!--2. On the [Asset Reports page](#https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/assets/admin/asset-reports), you can see the current state of the report job, for example, Success, Failed, Queued, or Scheduled.-->

![생성된 보고서 상태](assets/report-status.JPG)

### Brand Portal에서 폴더 게시 취소 {#unpublish-folders-from-brand-portal}

AEM Assets 인스턴스에서 게시를 취소하여 Brand Portal에 게시된 모든 자산 폴더를 제거할 수 있습니다. 원래 폴더를 게시 취소한 후에는 Brand Portal 사용자가 해당 복사본을 더 이상 사용할 수 없습니다.

자산 폴더를 Brand Portal에서 즉시 게시 취소하거나 나중 날짜 또는 시간으로 예약할 수 있습니다.

Brand Portal에서 자산 폴더의 게시를 취소하려면,

1. Assets 콘솔에서 게시를 취소하려는 자산 폴더를 선택하고 도구 모음에서 **[!UICONTROL 게시 관리]** 옵션을 클릭합니다.

   ![publish2bp-1](assets/publish2bp.png)

1. **지금 자산 폴더 게시 취소합니다**.

   Brand Portal에서 선택한 자산 폴더를 즉시 게시 취소하려면,

   1. 도구 모음에서 **[!UICONTROL 게시 관리]**&#x200B;를 선택합니다.

   1. **[!UICONTROL 작업]**&#x200B;에서 **[!UICONTROL Brand Portal에 게시 취소]**&#x200B;를 선택합니다.

      **[!UICONTROL 예약]**&#x200B;에서 **[!UICONTROL 지금]**&#x200B;을 선택합니다.

      **[!UICONTROL 다음]**&#x200B;을 클릭합니다.

   1. **[!UICONTROL 범위]**&#x200B;에서 선택 내용을 확인하고 **[!UICONTROL Brand Portal에 게시 취소]**&#x200B;를 클릭합니다.

      ![confirm-unpublish](assets/confirm-unpublish.png)

1. **나중에 자산 폴더를 게시 취소합니다**.

   자산 폴더의 게시 취소를 나중 날짜 및 시간으로 예약하려면,

   1. 도구 모음에서 **[!UICONTROL 게시 관리]**&#x200B;를 선택합니다.

   1. **[!UICONTROL 작업]**&#x200B;에서 **[!UICONTROL Brand Portal에 게시 취소]**&#x200B;를 선택합니다.

      **[!UICONTROL 예약]**&#x200B;에서 **[!UICONTROL 나중에]**&#x200B;를 선택합니다.

   1. **[!UICONTROL 활성화 날짜]**&#x200B;를 선택하고 시간을 지정합니다. **[!UICONTROL 다음]**&#x200B;을 클릭합니다.

   1. **[!UICONTROL 범위]**&#x200B;에서 선택 내용을 확인하고 **[!UICONTROL 다음]**&#x200B;을 클릭합니다.

   1. **[!UICONTROL 워크플로우]**&#x200B;에서 **[!UICONTROL 워크플로우 제목]**&#x200B;을 지정합니다. **[!UICONTROL 나중에 게시 취소]**&#x200B;를 클릭합니다.

      ![unpublishworkflows](assets/unpublishworkflows.png)

## Brand Portal에 Publish 컬렉션 {#publish-collections-to-brand-portal}

AEM Assets 클라우드 인스턴스에서 컬렉션을 게시하거나 게시 취소할 수 있습니다.

>[!NOTE]
>
>컨텐츠 조각은 Brand Portal에 게시할 수 없습니다. 따라서 AEM Assets에서 컨텐츠 조각을 선택한다면 **[!UICONTROL Brand Portal에 게시]** 동작을 사용할 수 없습니다.
>
>컨텐츠 조각이 포함된 컬렉션이 AEM Assets에서 Brand Portal로 게시되면 컨텐츠 조각을 제외한 폴더의 모든 컨텐츠가 Brand Portal 인터페이스에 복제됩니다.

### Publish 컬렉션 {#publish-collections}

다음은 AEM Assets의 컬렉션을 Brand Portal에 게시하는 절차입니다.

1. AEM Assets UI에서 AEM 로고를 클릭합니다.

1. **탐색** 페이지에서 **[!UICONTROL 자산]** > **[!UICONTROL 컬렉션]**&#x200B;으로 이동합니다.

1. **컬렉션** 콘솔에서 Brand Portal에 게시하려는 컬렉션을 선택합니다.

   ![select_collection](assets/select_collection.png)

1. 도구 모음에서 **[!UICONTROL Brand Portal에 게시]**&#x200B;를 클릭합니다.

1. 확인 대화 상자에서 **[!UICONTROL 게시]**&#x200B;를 클릭합니다.

1. 확인 메시지를 닫습니다.

   관리자로 Brand Portal에 로그인하십시오. 게시된 컬렉션은 컬렉션 콘솔에서 사용할 수 있습니다.

   ![게시된 컬렉션](assets/published_collection.png)

### 컬렉션 게시 취소 {#unpublish-collections}

AEM Assets 인스턴스에서 게시를 취소하여 Brand Portal에 게시된 모든 컬렉션을 제거할 수 있습니다. 원래 컬렉션을 게시 취소한 후에는 Brand Portal 사용자가 해당 복사본을 더 이상 사용할 수 없습니다.

다음은 컬렉션을 게시 취소하는 절차입니다.

1. AEM Assets 인스턴스의 **컬렉션** 콘솔에서 게시를 취소하려는 컬렉션을 선택합니다.

   ![select_collection](assets/select_collection-1.png)

1. 도구 모음에서 **[!UICONTROL Brand Portal에서 제거]** 아이콘을 클릭합니다.
1. 대화 상자에서 **[!UICONTROL 게시 취소]**&#x200B;를 클릭합니다.
1. 확인 메시지를 닫습니다. 컬렉션이 Brand Portal 인터페이스에서 제거됩니다.

위의 항목 외에도 AEM Assets의 메타데이터 스키마, 이미지 사전 설정, 검색 패싯 및 태그를 Brand Portal 포털에 게시할 수 있습니다.

* [사전 설정, 스키마 및 패싯을 Brand Portal에 게시](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/publish/publish-schema-search-facets-presets.html)
* [태그를 Brand Portal에 게시](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/publish/brand-portal-publish-tags.html)


자세한 내용은 [Brand Portal 설명서](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/home.html)를 참조하십시오.


<!--
   Comment Type: draft

   <li> </li>
   -->

<!--
   Comment Type: draft

   <li>Step text</li>
   -->

**추가 참조**

* [자산 번역](translate-assets.md)
* [Assets HTTP API](mac-api-assets.md)
* [자산이 지원되는 파일 형식](file-format-support.md)
* [자산 검색](search-assets.md)
* [연결된 자산](use-assets-across-connected-assets-instances.md)
* [자산 보고서](asset-reports.md)
* [메타데이터 스키마](metadata-schemas.md)
* [자산 다운로드](download-assets-from-aem.md)
* [메타데이터 관리](manage-metadata.md)
* [검색 패싯](search-facets.md)
* [컬렉션 관리](manage-collections.md)
* [일괄 메타데이터 가져오기](metadata-import-export.md)
* [AEM 및 Dynamic Media에 자산 게시](/help/assets/publish-assets-to-aem-and-dm.md)