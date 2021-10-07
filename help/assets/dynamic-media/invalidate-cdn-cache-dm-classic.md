---
title: Dynamic Media Classic을 통해 CDN(Content Delivery Network) 캐시를 무효화합니다
description: CDN(Content Delivery Network) 캐시 콘텐츠를 무효화하여 캐시가 만료될 때까지 기다리는 대신 Dynamic Media에서 제공하는 자산을 빠르게 업데이트하는 방법을 알아봅니다.
feature: Asset Management,Dynamic Media Classic
role: Admin,User
exl-id: 7e488699-5633-437f-9e2e-58c98aa13145
source-git-commit: 7d67bdb5e0571d2bfee290ed47d2d7797a91e541
workflow-type: tm+mt
source-wordcount: '693'
ht-degree: 0%

---

# Dynamic Media Classic을 통해 CDN 캐시 무효화 {#invalidating-your-cdn-cached-content}

Dynamic Media 자산은 CDN(Content Delivery Network)에서 캐시하여 빠른 배달을 제공합니다. 그러나 자산을 업데이트할 때에는 이러한 변경 사항을 즉시 적용할 수 있습니다. CDN 캐시 콘텐츠를 무효화하면 캐시가 만료될 때까지 기다리지 않고 Dynamic Media에서 전달하는 자산을 빠르게 업데이트할 수 있습니다.

>[!NOTE]
>
>이 기능을 사용하려면 Adobe Experience Manager Dynamic Media과 함께 번들로 제공되는 기본 CDN을 사용해야 합니다. 다른 모든 사용자 지정 CDN은 이 기능에서 지원되지 않습니다.

>[!IMPORTANT]
>
>이 단계는 Adobe Experience Manager 6.5, 서비스 팩 5 이하의 Dynamic Media에만 적용됩니다. <!-- If you are using Dynamic Media in AEM as a Cloud Service, [use the new steps found here](/help/assets/invalidate-cdn-cache-dynamic-media.md). -->

Dynamic Media Classic](https://helpx.adobe.com/experience-manager/scene7/kb/base/caching-questions/scene7-caching-overview.html)의 [캐시 개요 를 참조하십시오.

**Dynamic Media Classic을 통해 CDN 캐시를 무효화하려면 다음을 수행하십시오.**

1. [Dynamic Media Classic 데스크탑 응용 프로그램](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/getting-started/signing-out.html#getting-started)을 연 다음 계정에 로그인합니다.

   자격 증명 및 로그인 세부 정보는 프로비저닝 시 Adobe이 제공했습니다. 이 정보가 없는 경우 기술 지원 센터에 문의하십시오.

1. **[!UICONTROL 설정]** > **[!UICONTROL 응용 프로그램 설정]** > **[!UICONTROL 일반 설정]**&#x200B;으로 이동합니다.
1. 응용 프로그램 일반 설정 페이지의 서버 그룹 제목 아래에서 **[!UICONTROL CDN 무효화 템플릿]** 텍스트 상자를 찾습니다.

1. CDN(Content Delivery Network) 캐시를 무효화하는 데 사용되는 템플릿을 지정합니다.

   예를 들어 다음 예제와 같이 특정 이미지 ID 대신 `<ID>`을 참조하는 이미지 URL(이미지 사전 설정 또는 수정자 포함)을 입력한다고 가정합니다.

   `https://server.com/is/image/Company/<ID>?$product$`

   템플릿에 `<ID>`만 포함되어 있으면 Dynamic Media은 `https://<server>/is/image`로 채워집니다. 여기서 `<server>`는 일반 설정에 정의된 게시 서버 이름이고 &lt;ID>는 무효화되도록 선택한 자산입니다.

1. 페이지의 오른쪽 아래 모서리에서 **[!UICONTROL 닫기]**&#x200B;를 선택합니다.
1. Dynamic Media Classic(Scene7) UI에서 자산을 한 개 이상 선택한 다음 **[!UICONTROL 파일]** > **[!UICONTROL CDN 무효화]**&#x200B;로 이동합니다. 만든 템플릿과 선택한 자산에서 생성된 하나 이상의 URL 목록이 표시됩니다. 응용 프로그램 일반 설정 아래의 &quot;게시된 서버 이름&quot; 아래에 나열된 서버 URL을 사용합니다.

   예를 들어 이전 단계에서 CDN 무효화 템플릿 을 설정한 경우 `Backpack_B` 이라는 단일 이미지 자산 이미지를 선택했다고 가정해 보겠습니다. **[!UICONTROL 파일]** > **[!UICONTROL CDN]**&#x200B;무효화 로 이동하면 CDN 무효화 사용자 인터페이스에 다음과 같이 생성된 URL이 생성됩니다.

   `https://server.com/is/image/Company/Backpack_B?$product$`

1. URL 목록 상자에서 **[!UICONTROL 계속]**&#x200B;을 선택하여 각 특정 URL에 대한 캐시를 지웁니다. URL을 편집하거나 URL 목록 상자에 URL을 입력하거나 붙여넣어 URL을 추가할 수 있습니다. cdn 무효화 템플릿을 미리 설정할 필요가 없습니다.

   **[!UICONTROL 계속]**&#x200B;을 선택하면 캐시를 지우는 데 걸리는 시간을 예상할 수 있는 표시기가 표시됩니다.

   여러 자산을 선택한 경우 **[!UICONTROL 파일]** > **[!UICONTROL CDN 무효화]**&#x200B;로 이동한 경우, 각 자산은 저장된 **[!UICONTROL 템플릿 URL]**&#x200B;에서 참조됩니다. 따라서 제품 세부 사항 및 검색 결과와 같이 웹 사이트에서 참조되는 각 URL 이미지 사전 설정을 참조하는 **[!UICONTROL CDN Invalidate Template]**&#x200B;을 정의할 수 있습니다. 그런 다음 캐시에서 무효화에 사용할 이미지를 선택하면 URL이 자동으로 인터페이스를 채웁니다.

   >[!NOTE]
   >
   >자산을 선택한 다음 **[!UICONTROL 파일]** > **[!UICONTROL CDN 무효화]**&#x200B;로 이동하면 Dynamic Media은 무효화 CDN 템플릿을 사용하여 CDN에서 무효화할 URL을 자동으로 생성합니다. **[!UICONTROL CDN 템플릿 무효화]** 텍스트 상자에 아무 것도 없으면 빈 URL 목록이 표시됩니다. CDN의 캐싱은 자산 기반이 아닙니다. URL을 기반으로 합니다. 따라서 웹 사이트에 있는 전체 URL을 알고 있어야 합니다. 이러한 URL을 결정한 후 단계 앞부분에서 **[!UICONTROL CDN 템플릿 무효화]** 텍스트 상자에 추가할 수 있습니다. 그런 다음 해당 자산을 선택하고 한 단계에서 URL을 무효화할 수 있습니다.
   >
   >다른 옵션은 전체 URL을 **[!UICONTROL CDN 무효화]** 목록에 추가하는 것입니다. 이 접근 방식을 따르는 경우 **[!UICONTROL 파일]** > **[!UICONTROL CDN]** 무효화 옵션으로 이동하기 전에 Dynamic Media Classic에서 자산을 선택할 필요가 없습니다.
