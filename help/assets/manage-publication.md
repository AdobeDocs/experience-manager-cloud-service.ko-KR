---
title: 게시 관리
description: Experience Manager Assets, Dynamic Media 및 Brand Portal에 자산 게시 또는 게시 취소
contentOwner: Vishabh Gupta
mini-toc-levels: 1
feature: Asset Management, Publishing, Collaboration, Asset Processing
role: User, Architect, Admin
exl-id: 691a0925-0061-4c62-85ac-8257b96dddf2
source-git-commit: 8bdd89f0be5fe7c9d4f6ba891d7d108286f823bb
workflow-type: tm+mt
source-wordcount: '1465'
ht-degree: 10%

---

# Experience Manager Assets에서 게시 관리 {#manage-publication-in-aem}

(으)로 [!DNL Adobe Experience Manager Assets] 관리자: 작성자 인스턴스의 에셋 및 에셋이 포함된 폴더를 [!DNL Experience Manager Assets], [!DNL Dynamic Media], 및 [!DNL Brand Portal]. 자산이나 폴더의 게시 워크플로우를 나중 날짜나 시간으로 예약할 수도 있습니다. 게시되면 사용자는 에셋에 액세스하고 다른 사용자에게 에셋을 추가로 배포할 수 있습니다. 기본적으로 에셋 및 폴더를 게시할 수 있습니다. [!DNL Experience Manager Assets]. 그러나 다음을 구성할 수 있습니다. [!DNL Experience Manager Assets] 에 게시를 활성화하려면 [[!DNL Dynamic Media]](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/dynamicmedia/config-dm.html) 및 [[!DNL Brand Portal]](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/brand-portal/configure-aem-assets-with-brand-portal.html).

다음 중 하나를 사용하여 에셋 또는 폴더 수준에서 에셋을 게시하거나 게시를 취소할 수 있습니다 **[!UICONTROL 빠른 게시]** 또는 **[!UICONTROL 게시 관리]** 옵션이에서 사용할 수 있음 [!DNL Experience Manager Assets] 인터페이스. 의 원본 에셋 또는 폴더를 추가로 수정하는 경우 [!DNL Experience Manager Assets]에서 다시 게시할 때까지 변경 사항이 게시 인스턴스에 반영되지 않습니다 [!DNL Experience Manager Assets]. 진행 중인 작업 변경 사항을 게시 인스턴스에서 사용할 수 없도록 합니다. 관리자가 게시한 승인된 변경 사항만 게시 인스턴스에서 사용할 수 있습니다.

* [빠른 게시를 사용하여 자산 게시](#quick-publish)
* [게시 관리를 사용하여 자산 게시](#manage-publication)
* [나중에 자산 게시](#publish-assets-later)
* [Dynamic Media에 자산 게시](#publish-assets-to-dynamic-media)
* [자산을 Brand Portal에 게시](#publish-assets-to-brand-portal)
* [제한 사항 및 팁](#limitations-and-tips)

## 빠른 게시를 사용하여 자산 게시 {#quick-publish}

빠른 게시를 사용하면 콘텐츠를 선택한 대상에 즉시 게시할 수 있습니다. 다음에서 [!DNL Experience Manager Assets] 콘솔에서 상위 폴더로 이동하고 게시할 모든 에셋 또는 폴더를 선택합니다. 클릭 **[!UICONTROL 빠른 게시]** 도구 모음에서 옵션을 선택하고 드롭다운 목록에서 자산을 게시하려는 대상 을 선택합니다.

![빠른 게시](assets/quick-publish-to-aem.png)

## 게시 관리를 사용하여 자산 게시 {#manage-publication}

게시 관리를 사용하면 선택한 대상에서 콘텐츠를 게시하거나 게시를 취소할 수 있습니다. [콘텐츠 추가](#add-content) 을 DAM 저장소의 게시 목록에 추가합니다. [폴더 설정 포함](#include-folder-settings) 선택한 폴더의 콘텐츠를 게시하고 필터를 적용하려면 [게시 예약](#publish-assets-later) 이후 날짜 또는 시간으로.

다음에서 [!DNL Experience Manager Assets] 콘솔에서 상위 폴더로 이동하고 게시할 모든 에셋 또는 폴더를 선택합니다. 클릭 **[!UICONTROL 게시 관리]** 도구 모음의 옵션입니다. 없는 경우 [!DNL Dynamic Media] 및 [!DNL Brand Portal] 에서 구성됨 [!DNL Experience Manager Assets] 에셋 및 폴더만 게시할 수 있습니다. [!DNL Experience Manager Assets].

![게시 관리](assets/manage-publication-aem.png)

다음 옵션은에서 사용할 수 있습니다. [!UICONTROL 게시 관리] 인터페이스:

* [!UICONTROL 작업]
   * `Publish`: 선택한 대상에 에셋 및 폴더 게시
   * `Unpublish`: 대상에서 에셋 및 폴더 게시 취소

* [!UICONTROL 대상]
   * `Publish`: 에셋 및 폴더 게시 위치 [!DNL Experience Manager Assets] (`AEM`)
   * `Dynamic Media`[!DNL Dynamic Media]: 에 자산 게시 
   * `Brand Portal`: 에셋 및 폴더 게시 위치 [!DNL Brand Portal]

* [!UICONTROL 예약]
   * `Now`: 자산을 즉시 게시합니다.
   * `Later`: 를 기반으로 자산 게시 `Activation` 날짜 또는 시간

계속하려면 다음을 클릭하십시오. **[!UICONTROL 다음]**. 선택한 항목에 따라 **[!UICONTROL 범위]** 탭은 다른 옵션을 반영합니다. 다음 옵션: **[!UICONTROL 콘텐츠 추가]** 및 **[!UICONTROL 폴더 설정 포함]** 에셋 및 폴더를 게시하는 데만 사용할 수 있습니다. [!DNL Experience Manager Assets] (`Destination: Publish`).

![게시 범위 관리](assets/manage-publication-aem-scope.png)

### 콘텐츠 추가 {#add-content}

게시 위치 [!DNL Experience Manager Assets] 게시 목록에 더 많은 콘텐츠(에셋 및 폴더)를 추가할 수 있습니다. dam-repository의 목록에 더 많은 에셋 또는 폴더를 추가할 수 있습니다. 클릭 **[!UICONTROL 콘텐츠 추가]** 단추를 클릭하여 더 많은 콘텐츠를 추가합니다.

폴더에서 여러 자산을 추가하거나 한 번에 여러 폴더를 추가할 수 있습니다. 그러나 한 번에 여러 폴더에서 에셋을 추가할 수는 없습니다.

![콘텐츠 추가](assets/manage-publication-add-content.png)

### 폴더 설정 포함 {#include-folder-settings}

기본적으로 폴더 게시 위치 [!DNL Experience Manager Assets] 는 모든 에셋, 하위 폴더 및 해당 참조를 게시합니다.

게시할 폴더 콘텐츠를 필터링하려면 **[!UICONTROL 폴더 설정 포함]**:

* `Include folder contents`

   * 활성화됨: 선택한 폴더의 모든 에셋, 하위 폴더(하위 폴더의 모든 에셋 포함) 및 참조가 게시됩니다.
   * 비활성화됨: 선택한 폴더(비어 있음) 및 참조만 게시됩니다. 선택한 폴더의 자산이 게시되지 않습니다.

* `Include folder contents` 및 `Include only immediate folder contents`

   두 옵션을 모두 선택하면 선택한 폴더의 모든 에셋, 하위 폴더(비어 있음) 및 참조가 게시됩니다. 하위 폴더의 자산은 게시되지 않습니다.

<!--
* [!UICONTROL Include only immediate folder contents]: Only the subfolders content and references are published. 

Only the selected folder content and references are published.
-->

![폴더 설정 포함](assets/manage-publication-include-folder-settings.png)

필터를 적용한 후 다음을 클릭: **[!UICONTROL 확인]**&#x200B;을 클릭한 다음 을 클릭합니다 **[!UICONTROL 게시]**. 게시 버튼을 클릭하면 확인 메시지가 표시됩니다 `Resource(s) have been scheduled for publication` 가 표시됩니다. 그리고 선택한 에셋 및(또는) 폴더는 스케줄러를 기반으로 정의된 대상에 게시됩니다(`Now` 또는 `Later`). 게시 인스턴스에 로그인하여 자산 및 폴더가 성공적으로 게시되었는지 확인합니다.

![AEM에 게시](assets/manage-publication-publish-aem.png)

위의 그림에서 **[!UICONTROL Target 게시]** 특성. 에 게시를 선택했다는 사실을 기억하겠습니다. [!DNL Experience Manager Assets] (`Destination: Publish`). 그러면 폴더와 에셋만 게시되는 이유는 무엇입니까? `AEM`, 그리고 다른 두 자산은 두 자산 모두에 게시됩니다 `AEM` 및 `Dynamic Media`?

여기에서 폴더 속성의 역할을 이해해야 합니다. 폴더 **[!UICONTROL Dynamic Media 게시 모드]** 속성은 발행에 중요한 역할을 합니다. 폴더의 속성을 보려면 폴더를 선택하고 **[!UICONTROL 속성]** 을 클릭합니다. 에셋의 경우 상위 폴더의 속성을 참조하십시오.

다음 표에서는 정의된 항목에 따라 게시가 발생하는 방식을 설명합니다. **[!UICONTROL 대상]** 및 **[!UICONTROL Dynamic Media 게시 모드]**:

| [!UICONTROL 대상] | [!UICONTROL Dynamic Media 게시 모드] | [!UICONTROL 게시 대상] | 허용된 컨텐츠 |
| --- | --- | --- | --- |
| 게시 | 선택적 게시 | `AEM` | 에셋 및 폴더 |
| 게시 | 즉시 | `AEM` 및 `Dynamic Media` | 에셋 및 폴더 |
| 게시 | 활성화 시 | `AEM` 및 `Dynamic Media` | 에셋 및 폴더 |
| Dynamic Media | 선택적 게시 | `Dynamic Media` | Assets |
| Dynamic Media | 즉시 | `None` | 자산을 게시할 수 없음 |
| Dynamic Media | 활성화 시 | `None` | 자산을 게시할 수 없음 |

>[!NOTE]
>
>에셋만 게시됩니다. [!DNL Dynamic Media].
>
>폴더 게시 위치 [!DNL Dynamic Media] 은(는) 지원되지 않습니다.
>
>폴더를 선택하는 경우(`Selective Publish`) 및 을(를) 선택합니다 [!DNL Dynamic Media] 대상, [!UICONTROL Target 게시] 속성이 다음을 반영함 `None`.


이제 을(를) 변경합니다. **[!UICONTROL 대상]** 위의 사용 사례에서 **[!UICONTROL Dynamic Media]** 결과를 확인합니다. 이렇게 하면 의 자산만 `Selective Publish` 폴더를에 게시합니다. [!DNL Dynamic Media]. 의 자산 `Immediate` 및 `Upon Activation` 폴더가 게시되지 않고 반영됩니다. `None`.

![Dynamic Media에 게시](assets/manage-publication-dynamic-media.png)

>[!NOTE]
>
>If [!DNL Dynamic Media] 이(가) 다음에 구성되어 있지 않습니다. [!DNL Experience Manager Assets] 인스턴스 및 **[!UICONTROL 대상]** 은(는) **[!UICONTROL 게시]**, 에셋 및 폴더는 항상 (으)로 게시됨 `AEM`.
>
>게시 위치 [!DNL Brand Portal] 은 폴더 속성과는 별개입니다. 모든 에셋, 폴더 및 컬렉션을 Brand Portal에 게시할 수 있습니다. 다음을 참조하십시오 [Brand Portal에 자산 게시](#publish-assets-to-brand-portal).

>[!NOTE]
>
>을(를) 사용자 지정한 경우 [!DNL Manage Publication] 마법사에서 사용자 지정은 기존 기능에서 계속 작동합니다.
>
>그러나 기존 사용자 지정을 제거하여 새 사용자 지정을 사용할 수 있습니다 [!DNL Manager Publication] 기능.


## 나중에 자산 게시 {#publish-assets-later}

자산의 게시 워크플로우를 나중 날짜 또는 시간으로 예약하려면 다음 작업을 수행하십시오.

1. 다음에서 [!UICONTROL Experience Manager Assets] 콘솔에서 상위 폴더로 이동하고 게시 일정을 예약하려는 모든 에셋 또는 폴더를 선택합니다.
1. 클릭 **[!UICONTROL 게시 관리]** 도구 모음의 옵션입니다.
1. 클릭 **[!UICONTROL 게시]** 출처: **[!UICONTROL 작업]**&#x200B;을(를) 선택한 다음 **[!UICONTROL 대상]** 콘텐츠를 게시할 위치입니다.
1. **[!UICONTROL 예약]**&#x200B;에서 **[!UICONTROL 나중에]**&#x200B;를 선택합니다.
1. 선택 **[!UICONTROL 활성화 날짜]** 날짜 및 시간을 지정합니다. **[!UICONTROL 다음]**&#x200B;을 클릭합니다.

   ![게시 관리 워크플로우](assets/manage-publication-workflow.png)

1. 다음에서 **[!UICONTROL 범위]** 탭, **[!UICONTROL 콘텐츠 추가]** (필요한 경우). **[!UICONTROL 다음]**&#x200B;을 클릭합니다.
1. 다음에서 **[!UICONTROL 워크플로]** 탭에서 워크플로 제목을 지정합니다. **[!UICONTROL 나중에 게시]**&#x200B;를 클릭합니다.

   ![워크플로 제목](assets/manage-publication-workflow-title.png)

   대상 인스턴스에 로그인하여 게시된 자산을 확인합니다(예약된 날짜 또는 시간에 따라 다름).

## Dynamic Media에 자산 게시 {#publish-assets-to-dynamic-media}

에셋만 게시됩니다. [!DNL Dynamic Media]. 그러나 게시 동작은 폴더 속성에 따라 다릅니다. 폴더에는 다음이 포함될 수 있습니다. **[!UICONTROL Dynamic Media 게시 모드]** 다음 중 하나일 수 있는 선택적 게시용으로 구성됩니다.

* `Selective Publish`
* `Immediate`
* `Upon Activation`

의 게시 프로세스 **[!UICONTROL 즉시]** 및 **[!UICONTROL 활성화 시]** 모드는 일관되지만 에는 다릅니다. **[!UICONTROL 선택적 게시]**. 다음을 참조하십시오 [Dynamic Media의 폴더 수준에서 선택적 게시 구성](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/dynamicmedia/selective-publishing.html). 폴더에서 선택적 게시를 구성한 후 다음 중 하나를 수행할 수 있습니다.

* [게시 관리를 사용하여 자산을 Dynamic Media 또는 Experience Manager에 선택적으로 게시](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/dynamicmedia/selective-publishing.html?lang=en#selective-publish-manage-publication)
* [게시 관리를 사용하여 Dynamic Media 또는 Experience Manager에서 에셋을 선택적으로 게시 취소합니다.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/dynamicmedia/selective-publishing.html?lang=en#selective-unpublish-manage-publication)
* [빠른 게시를 사용하여 Dynamic Media 또는 Experience Manager에 에셋 게시](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/dynamicmedia/selective-publishing.html?lang=en#quick-publish-aem-dm)
* [검색 결과를 통해 에셋을 선택적으로 게시 또는 게시 취소](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/dynamicmedia/selective-publishing.html?lang=en#selective-publish-unpublish-search-results)

## 자산을 Brand Portal에 게시 {#publish-assets-to-brand-portal}

에셋, 폴더 및 컬렉션을 [!DNL Experience Manager Assets Brand Portal] 인스턴스.

* [자산을 Brand Portal에 게시](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/brand-portal/publish-to-brand-portal.html?lang=en#publish-assets-to-bp)
* [폴더를 Brand Portal에 게시](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/brand-portal/publish-to-brand-portal.html?lang=en#publish-folders-to-brand-portal)
* [컬렉션을 Brand Portal에 게시](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/brand-portal/publish-to-brand-portal.html?lang=en#publish-collections-to-brand-portal)

## 제한 사항 및 팁 {#limitations-and-tips}

* 다음에 대한 옵션: [!UICONTROL 게시 관리] 복제 권한이 있는 사용자 계정만 사용할 수 있습니다.
* 빈 폴더는 게시되지 않습니다.
* 처리 중인 자산을 게시하는 경우 원래 콘텐츠만 게시됩니다. 렌디션이 누락되었습니다. 처리가 완료될 때까지 기다린 다음 처리가 완료되면 자산을 게시하거나 다시 게시합니다.
* 복잡한 에셋의 게시를 취소하는 동안 에셋만 게시 취소합니다. 게시된 다른 에셋에서 참조할 수 있으므로 참조 게시를 취소하지 마십시오.

**추가 참조**

* [에셋 번역](translate-assets.md)
* [Assets HTTP API](mac-api-assets.md)
* [에셋이 지원되는 파일 형식](file-format-support.md)
* [에셋 검색](search-assets.md)
* [연결된 에셋](use-assets-across-connected-assets-instances.md)
* [에셋 보고서](asset-reports.md)
* [메타데이터 스키마](metadata-schemas.md)
* [에셋 다운로드](download-assets-from-aem.md)
* [메타데이터 관리](manage-metadata.md)
* [검색 패싯](search-facets.md)
* [컬렉션 관리](manage-collections.md)
* [일괄 메타데이터 가져오기](metadata-import-export.md)
