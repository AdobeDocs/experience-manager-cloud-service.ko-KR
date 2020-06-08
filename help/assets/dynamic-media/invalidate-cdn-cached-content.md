---
title: CDN 캐시 콘텐츠 무효화
description: CDN(Content Delivery Network) 캐시 컨텐츠를 무효화할 수 있으므로 캐시 만료가 기다리는 대신 다이내믹 미디어에서 제공하는 자산을 신속하게 업데이트할 수 있습니다.
translation-type: tm+mt
source-git-commit: 6224d193adfb87bd9b080f48937e0af1f03386d6
workflow-type: tm+mt
source-wordcount: '634'
ht-degree: 1%

---


# CDN 캐시 콘텐츠 무효화 {#invalidating-your-cdn-cached-content}

CDN은 다이내믹 미디어 자산을 캐시하여 빠른 배달을 수행합니다. 그러나 자산을 업데이트할 때 이러한 변경 사항이 즉시 적용되도록 할 수 있습니다. CDN(Content Delivery Network) 캐시 컨텐츠를 무효화할 수 있으므로 캐시 만료가 기다리는 대신 다이내믹 미디어에서 제공하는 자산을 신속하게 업데이트할 수 있습니다.

Dynamic Media [Classic(Scene7)의 캐시 개요를 참조하십시오](https://helpx.adobe.com/experience-manager/scene7/kb/base/caching-questions/scene7-caching-overview.html).

**CDN 캐시된 컨텐츠를 무효화하려면:**

1. Dynamic Media Classic(Scene7) 계정에 로그온합니다.

   [https://www.adobe.com/marketing-cloud/experience-manager/scene7-login.html](https://www.adobe.com/marketing-cloud/experience-manager/scene7-login.html)

   자격 증명 및 로그온은 프로비저닝 시점에 Adobe에서 제공되었습니다. 이 정보가 없는 경우 기술 지원에 문의하십시오.

1. 설정 **[!UICONTROL > 응용 프로그램 설정 > 일반 설정을 클릭합니다]**.
1. [응용 프로그램 일반 설정] 페이지의 [서버] 그룹 머리글 아래에서 **[!UICONTROL CDN 무효화 템플릿]** 텍스트 상자를 찾습니다.

1. CDN(Content Delivery Network) 캐시를 무효화하는 데 사용되는 템플릿을 지정합니다.

   예를 들어 다음 예제와 같이 특정 이미지 ID 대신 참조하는 이미지 URL(이미지 사전 설정 또는 수정자 포함) `<ID>`을 입력한다고 가정합니다.

   `https://server.com/is/image/Company/<ID>?$product$`

   템플릿에 포함된 `<ID>`경우, 일반 설정에 정의된 게시 서버 이름 `https://<server>/is/image` 과 무효화되도록 선택된 자산이 다이내믹 미디어 `<server>` 에 채워집니다.

1. 페이지의 오른쪽 아래 모서리에서 닫기를 **[!UICONTROL 클릭합니다]**.
1. Dynamic Media Classic(Scene7) UI에서 하나 이상의 자산을 선택한 다음 **[!UICONTROL 파일 > CDN 무효화를 클릭합니다]**. 작성한 템플릿 및 선택한 자산에서 생성된 하나 이상의 URL 목록이 표시됩니다. 응용 프로그램 일반 설정 아래의 &quot;게시된 서버 이름&quot; 아래에 나열된 서버 URL을 사용합니다.

   예를 들어 이전 단계에서 CDN 무효화 템플릿이 설정되어 있으면 이름이 지정된 단일 이미지 자산 이미지를 선택했다고 가정합니다 `Backpack_B`. [ **[!UICONTROL 파일] > [CDN 무효화]를]** 클릭하면 CDN 무효화 사용자 인터페이스에 다음 URL이 생성됩니다.

   `https://server.com/is/image/Company/Backpack_B?$product$`

1. URL 목록 상자에서 **[!UICONTROL 계속]** 을 클릭하여 각 특정 URL에 대한 캐시를 지웁니다. URL을 편집하거나 URL 목록 상자에 입력하거나 붙여 넣어 URL을 추가할 수 있습니다. cdn 무효화를 사전에 설정할 필요는 없습니다.

   [ **[!UICONTROL 계속]**]을 클릭하면 캐시를 지우는 데 걸리는 예상 시간을 알려주는 표시기가 표시됩니다.

   여러 자산을 선택한 다음 **[!UICONTROL 파일 > CDN 무효화를]**&#x200B;클릭하면, 각 자산은 저장된 템플릿 URL에서 **[!UICONTROL 참조됩니다]**. 따라서 웹 사이트에서 참조되는 각 URL 이미지 사전 설정을 참조하는 **[!UICONTROL CDN 무효화 템플릿을]** 정의할 수 있습니다(예: 제품 세부 사항, 검색 결과 등). 그런 다음 캐시에서 무효화할 이미지를 선택하면 URL이 자동으로 인터페이스를 채웁니다.

   >[!NOTE]
   >
   >자산을 선택한 다음 **[!UICONTROL 파일 > CDN 무효화를]**&#x200B;클릭하면, 다이내믹 미디어는 CDN 템플릿을 무효화하여 URL을 자동으로 생성하여 CDN(Content Delivery Network)에서 무효화합니다. CDN 무효화 템플릿 **** 텍스트 상자에 아무 것도 없으면 빈 URL 목록이 표시됩니다. CDN의 캐싱은 자산 기반이 아닙니다. URL 기반입니다. 따라서 웹 사이트에 있는 전체 URL을 알고 있어야 합니다. 이러한 URL을 결정한 후 단계 앞의 **[!UICONTROL CDN 템플릿]** 무효화 텍스트 상자에 추가할 수 있습니다. 그런 다음 이러한 자산을 선택하고 한 번에 URL을 무효화할 수 있습니다.
   >
   >또 다른 옵션은 CDN 무효화 목록에 전체 URL을 **[!UICONTROL 추가하는]** 것입니다. 이 방법을 따를 경우 [ **[!UICONTROL 파일] > [CDN 무효화] 옵션으로 가기 전에 Dynamic Media Classic에서 자산을 선택할 필요가]** 없습니다.

