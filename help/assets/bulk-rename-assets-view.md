---
title: ' [!DNL Assets view]에서 에셋 이름 바꾸기 및 벌크 이름 바꾸기'
description: 새로운 Assets UI(Assets 보기)를 사용하여 에셋의 이름을 일괄 변경하는 방법을 알아봅니다. 여러 에셋의 이름을 한 번에 바꿀 수 있는 기능을 제공합니다.
role: User
exl-id: e041811b-0246-408f-9246-248da55f66a1
source-git-commit: 188f60887a1904fbe4c69f644f6751ca7c9f1cc3
workflow-type: tm+mt
source-wordcount: '486'
ht-degree: 17%

---

# [!DNL Assets view]에서 에셋 또는 폴더 이름 바꾸기 {#rename-single-asset-or-folder}

<table>
    <tr>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>새로 만들기</i></sup> <a href="/help/assets/dynamic-media/dm-prime-ultimate.md"><b>Dynamic Media Prime 및 Ultimate</b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>새로 만들기</i></sup> <a href="/help/assets/assets-ultimate-overview.md"><b>AEM Assets Ultimate</b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>새로 만들기</i></sup> <a href="/help/assets/integrate-aem-assets-edge-delivery-services.md"><b>Edge Delivery Services과 AEM Assets 통합</b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>새로 만들기</i></sup> <a href="/help/assets/aem-assets-view-ui-extensibility.md"><b>UI 확장성</b></a>
        </td>
          <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>새로 만들기</i></sup> <a href="/help/assets/dynamic-media/enable-dynamic-media-prime-and-ultimate.md"><b>Dynamic Media Prime 및 Ultimate 사용</b></a>
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

이름을 바꾸면 콘텐츠나 위치를 변경하지 않고 에셋을 보다 효과적으로 구성, 분류 및 식별하는 데 도움이 될 수 있습니다. [!DNL Assets view]을(를) 사용하면 선택한 에셋 또는 폴더의 이름을 바꿀 수 있습니다.

에셋 또는 폴더의 이름을 변경하려면 아래 단계를 수행하십시오.

1. 이름을 바꿀 에셋 또는 폴더를 찾습니다.

1. 다음 방법 중 하나를 사용하여 에셋 또는 폴더의 이름을 변경합니다.

   * 에셋 또는 폴더를 선택하고 상단 메뉴에서 ![이름 바꾸기 아이콘](assets/do-not-localize/rename-icon.png) **[!UICONTROL 이름 바꾸기]**&#x200B;를 클릭합니다.
   * 에셋 또는 폴더에서 추가 옵션 `...`을(를) 클릭하고 **[!UICONTROL 이름 바꾸기]**&#x200B;를 선택합니다.
   * 에셋 또는 폴더의 제목을 클릭하여 이름을 변경합니다. **자산 이름 바꾸기** 텍스트 상자에 새 텍스트를 입력하고 **저장**&#x200B;을 클릭합니다. 이 기능은 격자 보기, 갤러리 보기, 워터폴 보기 및 목록 보기에서 사용할 수 있습니다.

## AI 기반 에셋의 벌크 이름 바꾸기 {#rename-bulk-assets-using-ai}

[!DNL Assets view]을(를) 사용하면 AI를 사용하여 여러 에셋의 이름을 한 번에 바꿀 수 있습니다. AI 벌크 이름 바꾸기 기능은 폴더가 아닌 파일에만 적용할 수 있습니다. 여러 파일을 한 번에 선택하고 이름을 모두 바꿀 수 있습니다.

AI가 생성한 프롬프트를 사용하여 한 번에 대량의 에셋의 이름을 변경하려면 아래 단계를 따르십시오.

1. 여러 자산을 선택하고 상단 메뉴에서 **[!UICONTROL 일괄 이름 변경]**&#x200B;을 클릭합니다.

1. 선택한 에셋의 이름을 변경하는 방법을 설명하는 프롬프트를 추가합니다. [AI 일괄 이름 바꾸기에 대한 몇 가지 예](#examples-ai-bulk-rename)를 참조하세요.

1. **[!UICONTROL 실행]**&#x200B;을 클릭하여 AI가 프롬프트에 언급된 대로 에셋의 이름을 바꿀 수 있도록 합니다.

1. [선택 사항] 마지막으로 수행한 작업을 취소하거나 취소하려면 ![실행 취소 아이콘](assets/do-not-localize/undo.svg)을 클릭합니다.

1. [!UICONTROL 새 이름 미리 보기] 열에서 변경 내용을 확인하고 **[!UICONTROL 저장]**&#x200B;을 클릭합니다.

   ![AI 일괄 이름 바꾸기](assets/ai-bulk-rename.png)

## AI 벌크 이름 변경을 보여 주는 몇 가지 예 {#examples-ai-bulk-rename}

다음은 AI를 사용하여 AI 프롬프트에 따라 에셋의 이름을 일괄적으로 변경하는 몇 가지 예입니다.

* 00, 01 등의 접두사와 오늘 날짜의 접미사를 붙입니다.
* 모든 파일을 &#39;my-file&#39;로 변경하고 증분 번호를 추가합니다.
* 접두어와 접미어를 제거하고 이름의 가운데 부분만 유지합니다.
* 파일 접두사로 001, 002 등을 사용합니다. 영어로 번역합니다.

>[!VIDEO](https://video.tv.adobe.com/v/3440975)

>[!NOTE]
>
> * 이모지를 텍스트로 변환할 수 없습니다.
> * 자산의 이름을 변경하는 동안 경고 메시지를 방지하려면 고유한 이름을 사용하십시오. 하지만 새 이름으로 다시 시도할 수 있습니다.
> * 유니코드 또는 영숫자가 아닌 문자를 텍스트로 변환할 수도 있습니다.

## 다음 단계 {#next-steps}

* [Assets 보기에서 메타데이터 양식을 관리하려면 비디오를 시청하십시오](https://experienceleague.adobe.com/docs/experience-manager-learn/assets-essentials/configuring/metadata-forms.html?lang=ko)

* Assets 보기 사용자 인터페이스에서 사용 가능한 [!UICONTROL 피드백] 옵션을 사용하여 제품 피드백 제공

* 오른쪽 사이드바에서 사용 가능한 [!UICONTROL 이 페이지 편집], ![페이지 편집](assets/do-not-localize/edit-page.png), [!UICONTROL 문제 기록] 또는 ![GitHub 문제 생성](assets/do-not-localize/github-issue.png)을 사용하여 설명서 피드백 제공

* [고객 지원 센터](https://experienceleague.adobe.com/ko?support-solution=General#support) 문의
