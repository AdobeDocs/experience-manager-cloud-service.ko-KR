---
title: 다이내믹 미디어를 통해 CDN 캐시 무효화
description: CDN(Content Delivery Network) 캐시 컨텐츠를 무효화할 수 있으므로 캐시 만료가 기다리는 대신 다이내믹 미디어에서 제공하는 자산을 신속하게 업데이트할 수 있습니다.
translation-type: tm+mt
source-git-commit: 77e270b354e7e99aa2e7ab88ddc8528ad0c4ade0
workflow-type: tm+mt
source-wordcount: '1300'
ht-degree: 1%

---


# 다이내믹 미디어 {#invalidating-cdn-cache-for-dm-assets-in-aem-cs}를 통해 CDN 캐시 무효화

다이내믹 미디어 자산은 CDN(Content Delivery Network)에 의해 캐시되어 고객에게 빠르게 배달됩니다. 그러나 이러한 에셋을 업데이트할 때 해당 변경 사항이 웹 사이트에서 즉시 적용될 수 있습니다. CDN 캐시를 지우거나 무효화하면 Dynamic Media에서 제공하는 자산을 신속하게 업데이트할 수 있습니다. TTL(Time To Live) 값(기본값은 10시간)을 사용하여 캐시가 만료되기를 기다리는 대신 Dynamic Media 사용자 인터페이스에서 몇 분 내에 캐시가 만료되도록 요청을 보낼 수 있습니다.

>[!IMPORTANT]
>
>이 기능을 사용하려면 AEM Dynamic Media와 번들로 제공되는 기본 CDN을 사용해야 합니다.기타 모든 사용자 지정 CDN은 지원되지 않습니다.<!-- If you are using Dynamic Media in AEM 6.5, Service Pack 5 or earlier to invalidate the CDN cache [use the steps found here](/help/assets/invalidate-cdn-cache-dm-classic.md). -->

Dynamic Media](https://helpx.adobe.com/experience-manager/scene7/kb/base/caching-questions/scene7-caching-overview.html)의 [캐싱 개요를 참조하십시오.

**다이내믹 미디어 방식으로 CDN 캐시를 무효화하려면**

*2부 1부:CDN 무효화 템플릿 만들기*

1. AEM에서 Cloud Service으로 **[!UICONTROL 도구 > 자산 > CDN 무효화 템플릿을 누릅니다.]**

   ![CDN 유효성 검사 기능](/help/assets/assets-dm/cdn-invalidation-template.png)

1. **[!UICONTROL CDN 무효화 템플릿]** 페이지에서 시나리오에 따라 다음 옵션 중 하나를 수행합니다.

   | 시나리오 | 옵션 |
   | --- | --- |
   | 이전에 Dynamic Media Classic을 사용하여 CDN 무효화 템플릿을 이미 만들었습니다. | **[!UICONTROL 템플릿 만들기]** 텍스트 필드는 템플릿 데이터로 미리 채워집니다. 이러한 경우 템플릿을 편집하거나 다음 단계를 계속 진행할 수 있습니다. |
   | 템플릿을 만들어야 합니다. 무엇을 입력해야 합니까? | **[!UICONTROL 템플릿 만들기]** 텍스트 필드에 다음 예제와 같이 특정 이미지 ID 대신 `<ID>`를 참조하는 이미지 URL(이미지 사전 설정 또는 수정자 포함)을 입력합니다.<br>`https://my.publishserver.com/is/image/company_name/<ID>?$product$`<br>템플릿에 `<ID>`만 포함되어 있으면 Dynamic Media는 `https://<publishserver_name>/is/image/<company_name>/<ID>`로 채워집니다. 여기서 `<publishserver_name>`은 사용자의 게시 서버 이름입니다 Dynamic Media Classic의 일반 설정에서 정의됨;`<company_name>`은 이 AEM 인스턴스와 연결된 회사 루트의 이름이고, `<ID>`은 무효화할 자산 선택기를 통해 선택된 자산입니다.<br>모든 사전 설정/수정자 게시물 `<ID>` 이 URL 정의에 있는 그대로 복사됩니다.<br>템플릿을 기반으로 자동으로  `/is/image`만들 수 있는 이미지만<br>예를  `/is/content/`들어 자산 선택기를 사용하여 비디오 또는 PDF와 같은 에셋을 추가해도 URL이 자동으로 생성되지 않습니다. 대신, CDN 무효화 템플릿에서 이러한 자산을 지정해야 하거나, *파트 2:CDN 무효화 옵션 설정*.<br>**예:**<br>&#x200B;이 첫 번째 예에서 무효화 템플릿에는 자산 URL과  `<ID>` 함께 포함되어  `/is/content`있습니다. 예, `http://my.publishserver.com:8080/is/content/dms7snapshot/<ID>`. Dynamic Media는 이를 기반으로 한 URL을 형성하며, 무효화할 에셋 선택기를 통해 `<ID>`이 선택되는 에셋입니다.<br>이 두 번째 예에서 무효화 템플릿에는 자산 선택기에 종속되지 않고 웹 속성에 사용된 자산의 전체 URL이  `/is/content` 포함되어 있습니다. 예를 들어, `http://my.publishserver.com:8080/is/content/dms7snapshot/backpack` where backpack은 자산 ID입니다.<br>Dynamic Media에서 지원되는 자산 형식은 무효화할 수 있습니다. CDN 무효화에 대해 지원되지 *않는 에셋 파일 유형에는 Postscript, Encapsulated Postscript, Adobe Illustrator, Adobe InDesign, Microsoft Powerpoint, Microsoft Excel, Microsoft Word 및 리치 텍스트 형식이 포함됩니다.*<br>템플릿을 만들 때는 구문과 오타 문자에 주의를 기울여야 합니다.Dynamic Media에서는 템플릿 유효성 검사가 수행되지 않습니다.<br>이 CDN 무효화 템플릿 또는 제2부의  **[!UICONTROL URL]** 추가 텍스트 필드에서 이미지 스마트 자르기에 대한 URL을 지정해야  *합니다.CDN 무효화 옵션 설정을 참조하십시오.*<br>**중요:**CDN 무효화 템플릿의 각 항목은 해당 줄에 있어야 합니다.<br>*다음 템플릿 예는 그림 목적으로만 사용됩니다.* |

   ![CDN 무효화 템플릿 - 만들기](/help/assets/assets-dm/cdn-invalidation-template-create-2.png)

1. **[!UICONTROL CDN 무효화 템플릿]** 페이지의 오른쪽 맨 위에서 **[!UICONTROL 저장]**&#x200B;을 누른 다음 **[!UICONTROL 확인을 누릅니다.]**<br>

   *2부:CDN 무효화 옵션 설정*
   <br>

1. AEM에서 Cloud Service으로 **[!UICONTROL 도구 > 자산 > CDN 무효화를 누릅니다.]**

   ![CDN 유효성 검사 기능](/help/assets/assets-dm/cdn-invalidation-path.png)

1. **[!UICONTROL CDN 무효화]** - **[!UICONTROL 세부 사항 추가]** 페이지에서 CDN 무효화에 대한 자산을 선택합니다.

   ![CDN 무효화 - 세부 사항 추가](/help/assets/assets-dm/cdn-invalidation-add-details-2.png)

   >[!NOTE]
   >
   >CDN ****&#x200B;및&#x200B;**&#x200B;템플릿&#x200B;**[!UICONTROL 을 기준으로 무효화 옵션을 선택하지 않으면 선택한 자산의 기본 URL이 무효화를 위해 만들어집니다.]** 이미지만 이 옵션 배열을 사용해야 합니다.


   | 옵션 | 설명 |
   | --- | --- |
   | **[!UICONTROL CDN에서 자산 관련 이미지 사전 설정 무효화]** | (선택 사항) 이 옵션을 선택하면 선택한 자산과 관련된 모든 이미지 사전 설정 URL이 캐시 무효화를 위해 자동 구성됩니다.<br>에셋 및 관련 사전 정의된 사전 설정 URL은 무효화를 위해 자동 구성됩니다. 이 옵션은 이미지 에셋에만 작동합니다. |
   | **[!UICONTROL 템플릿을 기반으로 한 무효화]** | (선택 사항) URL 정보에 대해 정의된 템플릿만 사용하려면 이 옵션을 선택합니다. |
   | **[!UICONTROL 자산 추가]** | 자산 선택기를 사용하여 무효화할 자산을 선택합니다. 게시되었거나 게시 취소된 자산을 선택할 수 있습니다.<br>CDN의 캐싱은 자산 기반이 아닌 URL 기반입니다. 따라서 웹 사이트에 있는 전체 URL을 알고 있어야 합니다. 해당 URL을 결정한 후 템플릿에 추가할 수 있습니다. 그런 다음 해당 자산을 선택하여 추가하고 한 번에 URL을 무효화할 수 있습니다. <br>CDN의 자산 관련 이미지 사전 설정  **[!UICONTROL 무효화 또는 템플릿]** 기반  **[!UICONTROL 무효화]** 또는 둘 다와 함께 이 옵션을 사용합니다. |
   | **[!UICONTROL URL 추가]** | 무효화하려는 CDN 캐시가 있는 다이내믹 미디어 자산에 전체 URL 경로를 수동으로 추가하거나 붙여 넣습니다. ***파트 1/2:CDN 무효화 템플릿***&#x200B;을 만들고 무효화할 자산이 몇 개만 있습니다.<br>**중요: 추가하는** 각 URL은 해당 줄에 있어야 합니다.<br>한 번에 최대 1000개의 URL을 무효화할 수 있습니다. **[!UICONTROL URL 추가]** 텍스트 필드의 URL 수가 1000보다 큰 경우 **[!UICONTROL 다음]**&#x200B;을(를) 탭할 수 없습니다. 이러한 경우 선택한 자산의 오른쪽에 있는 **[!UICONTROL X]**&#x200B;을 누르거나 수동으로 추가한 URL을 눌러 무효화 목록에서 삭제해야 합니다.<br>CDN 무효화 템플릿 또는 이  **[!UICONTROL URL텍스트 추가 필드에서 이미지 스마트 자르기의 URL을 지정해야]** 합니다. |

1. 페이지의 오른쪽 위 모서리 근처에 있는 **[!UICONTROL Next.]**
1. **[!UICONTROL CDN 무효화]** - **[!UICONTROL 확인]** 페이지의 **[!UICONTROL URL]** 목록 상자에서 이전에 만든 CDN 무효화 템플릿 및 방금 추가한 자산에서 생성된 하나 이상의 URL 목록이 표시됩니다.

   예를 들어, 이전 단계에 표시된 CDN 무효화 템플릿 예제를 사용하여 `spinset`이라는 단일 자산을 추가했다고 가정합니다. **[!UICONTROL 도구 > 자산 > CDN 무효화]**&#x200B;를 탭하면 **[!UICONTROL CDN 무효화 - 확인]** 사용자 인터페이스에 다음 5개의 생성된 URL이 생성됩니다.

   ![CDN 무효화 - 확인](/help/assets/assets-dm/cdn-invalidation-confirm-2.png)

   필요한 경우 URL 오른쪽의 **X**&#x200B;을 눌러 무효화 프로세스에서 삭제합니다.

1. 페이지의 오른쪽 위 모서리 근처에 있는 **[!UICONTROL Submit]**&#x200B;을 눌러 CDN 무효화 프로세스를 시작합니다.

## CDN 무효화 오류 문제 해결

모든 경우, 전체 배치가 무효화되도록 처리되거나 전체 배치가 실패합니다.

| 오류 | 설명 |
| --- | --- |
| *선택한 자산에 대한 URL을 검색하지 못했습니다.* | 다음 시나리오가 충족되는 경우 발생합니다.<br>- 다이내믹 미디어 구성을 찾을 수 없습니다.<br>- Dynamic Media 구성을 읽은 서비스 사용자를 검색하는 동안 예외가 있습니다.<br>- URL을 구성하는 데 사용되는 게시 서버 또는 회사 루트가 Dynamic Media 구성에 없습니다. |
| *일부 URL이 올바르게 정의되지 않았습니다. 수정하고 다시 제출하십시오.* | IPS CDN 캐시 무효화 API가 URL이 다른 회사를 참조하고 있거나 IPS cdnCacheInvalidation API가 수행하는 유효성 검사에 대해 URL이 유효하지 않은 오류를 반환하는 경우 발생합니다. |
| *CDN 캐시를 무효화하지 못했습니다.* | 다른 이유로 CDN 캐시 무효화 요청이 실패하는 경우 발생합니다. |
| *무효화할 URL이 입력되어 있지 않습니다.* | **[!UICONTROL CDN 무효화]** - **[!UICONTROL 확인]** 페이지에 있는 URL이 없고 **[!UICONTROL 제출을 탭하면 발생합니다.]** |


<!--  | I do not want to create a template. | Near the upper-right corner of the page, tap **[!UICONTROL Cancel]**, then continue with ***Part 2: Working with CDN Invalidation***. Note that while you are not required to create a template to use CDN Invalidation, Adobe recommends that you create one, especially if you have numerous assets that you need to update immediately, on a regular basis. The template is used at the time you set CDN invalidation options. | -->
