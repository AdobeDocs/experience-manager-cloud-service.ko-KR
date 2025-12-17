---
title: 관리 보기에서 AI 생성 메타데이터를 통해 콘텐츠 검색 기능 향상
description: 관리 보기에서 AI 생성 메타데이터를 사용하여 콘텐츠 검색을 향상시키는 방법에 대해 알아봅니다
feature: Smart Tags,Tagging
role: Admin,User
source-git-commit: 3f44e74488fc73c406fefb6decc41782859d029b
workflow-type: tm+mt
source-wordcount: '669'
ht-degree: 9%

---


# AI 생성 메타데이터를 통해 콘텐츠 검색 향상 {#ai-smart-tags}

| UI | 문서 링크 |
| -------- | ---------------------------- |
| 자산 보기 | [여기 클릭](/help/assets/ai-generated-metadata-assets-view.md) |
| 관리자 보기 | 이 문서 |

AI는 수동 입력에 의존하는 대신 디지털 에셋에 설명 태그를 자동으로 할당합니다. 이러한 AI 생성 태그는 메타데이터의 품질을 높여 자산을 검색, 분류 및 추천하기 쉽게 만들어 줍니다. 이러한 접근 방식은 수동 태깅을 제거함으로써 효율성을 향상시킬 뿐만 아니라 대량의 디지털 컨텐츠 전반에 걸쳐 일관성과 확장성을 보장합니다. 예를 들어, 자산이 이미지인 경우 AI는 객체, 장면, 감정 또는 브랜드 로고까지 식별하고 &quot;일몰&quot;, &quot;해변&quot;, &quot;휴가&quot; 또는 &quot;스마일&quot;과 같은 관련 태그를 생성할 수 있습니다. AI가 생성한 콘텐츠는 의미론적 검색과 어휘 검색 기술을 모두 활용해 자산 검색을 강화할 수 있다. 더 보기 [Assets 검색](search-assets.md). <!--If the asset is a document, AI reads and interprets the text to assign meaningful keywords that summarize its content—such as "climate change," "policy," or "renewable energy.-->

![향상된 스마트 태그](assets/enhanced-smart-tags1.png)

## AI가 생성한 메타데이터를 활성화하는 방법 {#enable-ai-generated-metadata}

AI 생성 메타데이터를 활성화하려면 다음을 수행합니다.

* 필요한 최소 AEM 릴리스 버전은 `20626`입니다.

## AI 생성 제목 구성 {#configure-ai-generated-titles}

AEM을 사용하면 [자산 찾아보기] 페이지의 [카드 보기] 또는 [목록 보기]에서 자산 제목의 표시를 구성할 수 있습니다. 자산에 대한 기존 제목이 없는 경우에만 자신이 정의한 자산 제목을 표시하거나, AI를 사용하여 생성된 제목을 표시하거나, AI로 생성된 제목을 사용하도록 선택할 수 있습니다.

AI 생성 제목을 구성하려면 다음을 수행합니다.

1. **[!UICONTROL 도구 > Assets > Assets 구성 > 스마트 태그 개선 구성으로 이동합니다]**.

1. 다음 옵션 중 하나를 선택하십시오.

   * **DC 제목 표시(기본값)**: 자산 속성에서 사용할 수 있는 **[!UICONTROL 제목]** 필드에 제목을 지정하여 카드 보기 또는 목록 보기에서 표시합니다. 에셋 제목이 정의되지 않으면 AEM Assets에 파일 이름이 표시됩니다.

   * **AI 생성 제목 표시**: AI 생성 제목을 표시하고 자산 속성에 지정된 제목을 무시합니다. 에셋에 AI 생성 제목을 사용할 수 없는 경우 AEM Assets의 속성에 사용할 수 있는 기본 에셋 제목이 표시됩니다.

   * **DC 제목이 없는 경우에만 AI 생성 제목 표시**: AEM Assets은 에셋에 대한 에셋 제목이 정의되지 않은 경우에만 AI 생성 제목을 표시합니다.

     ![AI로 생성된 제목 구성](assets/configure-title-ai-generated.png)

## AI가 생성한 메타데이터 사용 {#using-ai-generated-smart-tags}

<!--[!NOTE]
>
>The enhanced smart tags capability is available only for the newly uploaded assets.
-->

향상된 스마트 태그 기능을 사용하려면 다음 단계를 수행하십시오.

1. [!DNL Experience Manager] 인터페이스에서 원하는 폴더로 이동한 다음 **[!UICONTROL Assets 추가]**&#x200B;를 클릭합니다. <!--Alternatively, to update enhanced smart tags in an existing content, click **[!UICONTROL reprocess]**.--> 호환되는 이미지 파일 형식은 `png`, `jpg`, `jpeg`,`psd`, `tiff`, `gif`, `webp`, `crw`, `cr2`, `3fr`, `nef`, `arw` 및 `bmp`입니다.

1. 새로 업로드한 자산이 처리될 때까지 기다립니다. 완료되면 자산 속성으로 이동합니다.

1. **[!UICONTROL AI 생성]** 탭으로 이동합니다. [!DNL Experience Manager] 버전이 호환되지 않거나 업데이트되지 않으면 이 탭이 표시되지 않습니다. 다음 필드가 있습니다.

   * **[!UICONTROL 생성된 제목]:** 제목은 업로드된 에셋의 핵심 아이디어를 캡처하는 명확하고 간결한 헤드라인을 제공하므로 한 눈에 쉽게 이해할 수 있습니다. 에셋을 추가할 때 `dc:title`에 제목을 입력하면 에셋 찾아보기 보기에 표시됩니다. 비워 두면 AI가 생성한 제목이 자동으로 할당됩니다.
   * **[!UICONTROL 생성된 설명]:** 설명은 자산의 내용에 대한 간단하면서도 유용한 요약을 제공하여 사용자 및 검색 모듈이 관련성을 빠르게 파악할 수 있도록 합니다.
   * **[!UICONTROL 생성된 키워드]:** 키워드는 자산의 주요 테마를 나타내는 타깃팅된 용어이며 태그 지정 및 콘텐츠 필터링에 도움이 됩니다.

1. [선택 사항] 관련 태그가 누락된 경우 태그를 추가하거나 직접 만들 수 있습니다. 이렇게 하려면 **[!UICONTROL 생성된 키워드]** 필드에 태그를 쓰고 **[!UICONTROL 저장]**&#x200B;을 클릭하세요.

## AI 생성 메타데이터 비활성화 {#disable-ai-generated-metadata}

AEM as a Cloud Service 환경에 대한 AI 생성 메타데이터를 비활성화하거나 폴더 수준에서 비활성화할 수 있습니다.

AEM as a Cloud Service 환경에 대해 AI 생성 메타데이터를 비활성화하려면

1. **[!UICONTROL 도구 > Assets > Assets 구성 > 스마트 태그 개선 구성으로 이동합니다]**.

1. **[!UICONTROL 스마트 태그 개선 사용 안 함]**&#x200B;을 선택합니다.

1. **[!UICONTROL 저장]** 을 클릭합니다.

AEM Assets에 업로드하는 새 에셋 또는 폴더에 대해 AI 생성 메타데이터가 비활성화됩니다. 이미 AI가 생성한 메타데이터 필드가 있는 기존 에셋 또는 폴더에는 이러한 필드가 계속 표시됩니다.

### 폴더에 대해 AI 생성 메타데이터 비활성화 {#disable-ai-generated-metadata-folder-level}

폴더 수준에서 AI 생성 메타데이터를 비활성화하려면 다음을 수행합니다.

1. 폴더를 선택하고 **[!UICONTROL 속성]**&#x200B;을 클릭하세요.

1. **[!UICONTROL 자산 처리]** 탭을 선택합니다.

1. **[!UICONTROL 이미지에 대한 스마트 태그 개선]** 섹션의 드롭다운 메뉴에서 **[!UICONTROL 비활성화]**&#x200B;를 선택합니다.

1. 선택한 폴더에 대해 AI 생성 메타데이터를 비활성화하려면 **[!UICONTROL 저장 및 닫기]**&#x200B;를 클릭하십시오.