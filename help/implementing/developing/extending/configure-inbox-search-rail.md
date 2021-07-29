---
title: 받은 편지함에 대한 검색 필터를 구성하는 방법
description: 받은 편지함 항목에 대한 검색 필터를 구성하는 방법을 알아봅니다.
source-git-commit: ee32ab3659ee4696caa55b945b6b7895d94914a9
workflow-type: tm+mt
source-wordcount: '1001'
ht-degree: 0%

---

# 받은 편지함에 대한 검색 필터 구성 {#configure-search-filters-inbox}

받은 편지함 항목에 대한 검색 필터를 구성할 수 있습니다. 특정 받은 편지함 열에 검색 기준을 기반으로 결과를 필터링합니다.

예를 들어, 받은 편지함 날짜 열 범위를 기반으로 받은 편지함 항목을 필터링하려면 날짜 범위 설명을 사용하여 날짜 범위를 정의할 수 있습니다.

다음은 받은 편지함에 사용할 수 있는 설명 유형입니다.

* 범위 조건자

* 텍스트 술어

* 날짜 범위 조건자

* 옵션 속성 조건자

>[!NOTE]
>
>받은 편지함에 대한 검색 필터를 구성할 `workflow-administrators` 그룹의 구성원인지 확인합니다.

## 사용자 지정된 구성 만들기 또는 열기 {#creating-opening-customized-configuration}

1. **[!UICONTROL 도구]**, **[!UICONTROL 일반]**, **[!UICONTROL Forms 검색]**&#x200B;으로 이동합니다.

1. **[!UICONTROL 받은 편지함 검색 레일]** 구성을 선택하고 **[!UICONTROL 편집]**&#x200B;을 탭합니다.
1. **[!UICONTROL 검색 편집 Forms]**&#x200B;을 사용하여 설명 구성 변경 사항을 통합합니다.
1. **[!UICONTROL 완료]**&#x200B;를 선택하여 구성을 저장합니다.

## 사용자 지정된 구성 삭제 {#delete-customized-configuration}

사용자 지정된 구성을 삭제하려면

1. **[!UICONTROL 도구]**, **[!UICONTROL 일반]**, **[!UICONTROL Forms 검색]**&#x200B;으로 이동합니다.

1. **[!UICONTROL 받은 편지함 검색 레일]** 구성을 선택하고 **[!UICONTROL 삭제]**&#x200B;를 탭합니다.

## 범위 설명 구성 {#range-predicate}

범위 설명을 사용하여 받은 편지함 열에서 숫자 범위를 검색하도록 받은 편지함 항목을 필터링할 수 있습니다. 숫자에 대한 십진수 값을 포함하도록 선택할 수도 있습니다.

범위 설명을 구성하려면

1. 구성](#creating-opening-customized-configuration)에 대해 [양식을 엽니다.
1. **[!UICONTROL 조건자 선택]** 탭을 탭하고 **[!UICONTROL 범위 설명]**&#x200B;을 폼으로 드래그합니다.
1. **[!UICONTROL 설정]** 탭에서 **[!UICONTROL 열 이름]** 필드에서 검색 기반으로 사용할 받은 편지함 열 이름을 선택합니다.
1. **[!UICONTROL 필터 레이블]** 필드에 필터의 레이블을 지정합니다. **[!UICONTROL 소수점 값 활성화]** 확인란을 선택하여 범위를 정의하는 동안 숫자의 소수점 값을 적용합니다.
1. 구성에 대한 선택적 설명을 지정하고 **[!UICONTROL 완료]**&#x200B;를 눌러 저장합니다.

구성 변경 사항은 필터 페이지를 열 때 반영됩니다. 4단계에서 지정한 필터 레이블은 최대 및 최소 값을 정의하는 옵션이 있는 레이블로 표시됩니다. Enter 키를 누르면 [!DNL Experience Manager]이 3단계에서 지정한 열 이름에 대한 검색 기준을 적용하고 받은 편지함 항목을 반환합니다.

>[!NOTE]
>
>문서에 최신 사용자 인터페이스 옵션이 나열됩니다. 옵션 이름은 향후 릴리스의 사용자 인터페이스에서 업데이트됩니다.

## 텍스트 설명 구성 {#text-predicate}

받은 편지함 항목을 필터링하여 텍스트 설명을 사용하여 받은 편지함 열 내에서 텍스트 문자열을 검색합니다.

텍스트 설명을 구성하려면:

1. 구성](#creating-opening-customized-configuration)에 대해 [양식을 엽니다.
1. **[!UICONTROL 조건자 선택]** 탭을 탭하고 **[!UICONTROL 텍스트 조건자]**&#x200B;를 양식으로 드래그합니다.
1. **[!UICONTROL 설정]** 탭에서 **[!UICONTROL 열 이름]** 필드에서 검색 기반으로 사용할 받은 편지함 열 이름을 선택합니다.
1. **[!UICONTROL 검색 텍스트 상자 자리 표시자]** 필드에 자리 표시자 텍스트로 검색 텍스트 상자에 표시되는 텍스트를 지정합니다.
1. 구성에 대한 선택적 설명을 지정하고 **[!UICONTROL 완료]**&#x200B;를 눌러 저장합니다.

구성 변경 사항은 필터 페이지를 열 때 반영됩니다. Enter 키를 누르면 [!DNL Experience Manager] 키를 누르면 3단계에서 지정한 열 이름의 4단계에서 지정한 검색 텍스트가 적용되고 받은 편지함 항목이 반환됩니다.

## 날짜 범위 설명 구성 {#date-range-predicate}

날짜 범위 설명을 사용하여 받은 편지함 열 내에서 날짜 범위를 검색하도록 받은 편지함 항목을 필터링할 수 있습니다.

날짜 범위 설명을 구성하려면:

1. 구성](#creating-opening-customized-configuration)에 대해 [양식을 엽니다.
1. **[!UICONTROL 조건자 선택]** 탭을 탭하고 **[!UICONTROL 날짜 범위 설명]**&#x200B;을 양식으로 드래그합니다.
1. **[!UICONTROL 설정]** 탭에서 **[!UICONTROL 열 이름]** 필드에서 검색 기반으로 사용할 받은 편지함 열 이름을 선택합니다.
1. **[!UICONTROL 필터 레이블]** 필드에 날짜 범위 필터의 레이블을 지정합니다.
1. 필터의 시작 날짜 및 종료 날짜 레이블을 지정합니다.
1. 구성에 대한 선택적 설명을 지정하고 **[!UICONTROL 완료]**&#x200B;를 눌러 저장합니다.

구성 변경 사항은 필터 페이지를 열 때 반영됩니다. 4단계에서 지정한 필터 레이블은 5단계에서 지정한 시작 날짜 및 종료 날짜 레이블과 함께 날짜 범위 필터의 레이블로 표시됩니다. [!DNL Experience Manager] 3단계에서 지정한 열 이름에 검색 기준을 적용하고 받은 편지함 항목을 반환합니다.

## 사용자 지정 열 옵션 설명 구성 {#custom-column-options-predicate}

사용자 지정 열 옵션 설명을 사용하여 받은 편지함 열 내에서 사용자 지정 옵션을 검색하도록 받은 편지함 항목을 필터링할 수 있습니다.

사용자 지정 열 옵션 설명을 구성하려면:

1. 구성](#creating-opening-customized-configuration)에 대해 [양식을 엽니다.
1. **[!UICONTROL 조건자 선택]** 탭을 탭하고 **[!UICONTROL 사용자 지정 열 옵션 설명]**&#x200B;을 양식으로 드래그합니다.
1. **[!UICONTROL 설정]** 탭에서 **[!UICONTROL 열 이름]** 필드에서 검색 기반으로 사용할 받은 편지함 열 이름을 선택합니다.
1. **[!UICONTROL 필터 레이블]** 필드에 사용자 지정 열 옵션 필터의 레이블을 지정합니다.
1. **[!UICONTROL 단일 선택]** 확인란을 선택하여 받은 편지함 열에 필터를 적용하는 동안 하나의 옵션만 선택할 수 있습니다.
1. **[!UICONTROL 옵션 추가]** 섹션에서 다음을 수행합니다.
   1. **[!UICONTROL 수동]**&#x200B;을 선택하여 필터 검색 옵션을 수동으로 정의합니다. **[!UICONTROL 필터 옵션 추가]**&#x200B;를 탭하여 첫 번째 옵션을 정의합니다. 열 옵션의 레이블과 검색할 옵션 값 텍스트를 지정합니다. 예를 들어 **Female**&#x200B;을 받은 편지함 열에서 값으로 검색하려면 열 옵션의 레이블로 **F**&#x200B;을 지정하고 옵션 값 텍스트로 **Female**&#x200B;을 추가할 수 있습니다. 마찬가지로 필터 옵션을 더 추가할 수 있습니다.
   1. JSON 파일 경로를 사용하여 옵션을 정의하려면 **[!UICONTROL JSON 경로]**&#x200B;를 선택합니다. 다음은 필터 옵션을 정의하는 샘플 JSON 파일입니다.

      ```JSON
          {
         "options":[
            {
            "text":"Female",
            "value":"F"
            },
            {
            "text":"Male",
            "value":"M"
            }
          ]
        }
      ```

   1. **[!UICONTROL CRX 옵션 경로]**&#x200B;를 선택하여 CRX 저장소 경로를 사용하여 옵션을 정의합니다. **[!UICONTROL 옵션 경로 추가]**&#x200B;를 눌러 여러 경로를 추가합니다. 다음은 `Male` 및 `Female` 필터 옵션을 정의하는 샘플입니다.

      ```JSON
         <gender jcr:primaryType="sling:OrderedFolder">
                        <male
                            jcr:primaryType="nt:unstructured"
                            jcr:title="Male"
                            value="M"/>
                        <female
                            jcr:primaryType="nt:unstructured"
                            jcr:title="Female"
                            value="F"/>
                    </gender>
      ```

1. 구성에 대한 선택적 설명을 지정하고 **[!UICONTROL 완료]**&#x200B;를 눌러 저장합니다.

구성 변경 사항은 필터 페이지를 열 때 반영됩니다. 4단계에서 지정한 필터 레이블은 사용자 지정 열 옵션 조건부의 레이블로 표시됩니다. [!DNL Experience Manager] 6단계에서 정의한 검색 기준을 3단계에서 지정한 열 이름에 적용하고 받은 편지함 항목을 반환합니다.

다음 비디오에서는 `true` 및 `false` 옵션 값을 기반으로 열을 필터링하는 단계를 보여줍니다.

>[!VIDEO](https://video.tv.adobe.com/v/335679)

## 조건자에 따라 검색 필터 보기 {#view-search-filters-for-predicates}

조건자에 따라 검색 필터를 볼 수 있습니다. 받은 편지함 페이지에서 **[!UICONTROL 필터]**&#x200B;을 선택합니다. 필터가 왼쪽 창에 표시됩니다. 그런 다음 검색 기준을 지정하여 받은 편지함 항목을 필터링할 수 있습니다.

![필터 페이지](assets/apply-filters.png)

설명 구성 관리에 대한 자세한 내용은 [검색 Forms 구성](search-forms.md)을 참조하십시오.


