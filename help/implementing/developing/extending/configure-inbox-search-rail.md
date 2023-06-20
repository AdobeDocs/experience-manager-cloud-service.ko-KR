---
title: 받은 편지함용 검색 필터를 구성하는 방법
description: 받은 편지함 항목에 대한 검색 필터를 구성하는 방법을 알아봅니다.
exl-id: 0e82d7ad-7a82-4d67-8eb8-9af6936652d8
source-git-commit: f7525b6b37e486a53791c2331dc6000e5248f8af
workflow-type: tm+mt
source-wordcount: '1000'
ht-degree: 1%

---

# 받은 편지함용 검색 필터 구성 {#configure-search-filters-inbox}

받은 편지함 항목에 대한 검색 필터를 구성할 수 있습니다. 결과를 필터링하려면 특정 받은 편지함 열에 검색 기준을 지정합니다.

예를 들어 생일 받은 편지함 열 범위를 기반으로 받은 편지함 항목을 필터링하려면 날짜 범위 조건자를 사용하여 날짜 범위를 정의할 수 있습니다.

받은 편지함에 사용할 수 있는 술어 유형은 다음과 같습니다.

* 범위 조건자

* 텍스트 술어

* 날짜 범위 조건자

* 옵션 속성 조건자

>[!NOTE]
>
>의 구성원인지 확인합니다. `workflow-administrators` 그룹화하여 받은 편지함에 대한 검색 필터를 구성합니다.

## 사용자 지정된 구성 만들기 또는 열기 {#creating-opening-customized-configuration}

1. 다음으로 이동 **[!UICONTROL 도구]**, **[!UICONTROL 일반]**, **[!UICONTROL Forms 검색]**.

1. 다음 항목 선택 **[!UICONTROL 받은 편지함 검색 레일]** 구성 및 탭 **[!UICONTROL 편집]**.
1. 다음을 사용하여 술어 구성 변경 사항 통합 **[!UICONTROL 검색 Forms 편집]**.
1. 선택 **[!UICONTROL 완료]** 구성을 저장합니다.

## 사용자 지정된 구성 삭제 {#delete-customized-configuration}

사용자 정의된 구성을 삭제하려면

1. 다음으로 이동 **[!UICONTROL 도구]**, **[!UICONTROL 일반]**, **[!UICONTROL Forms 검색]**.

1. 다음 항목 선택 **[!UICONTROL 받은 편지함 검색 레일]** 구성 및 탭 **[!UICONTROL 삭제]**.

## 범위 설명 구성 {#range-predicate}

범위 술어를 사용하여 받은 편지함 항목을 필터링하여 받은 편지함 열 내에서 숫자 범위를 검색할 수 있습니다. 숫자의 십진수 값을 포함하도록 선택할 수도 있습니다.

범위 술어를 구성하려면 다음을 수행합니다.

1. 를 엽니다. [구성을 위한 양식](#creating-opening-customized-configuration).
1. 탭 **[!UICONTROL 조건자 선택]** 탭하고 드래그 **[!UICONTROL 범위 조건자]** 을 양식으로 변환.
1. 다음에서 **[!UICONTROL 설정]** 탭에서 검색 기준으로 사용할 받은 편지함 열 이름을 선택합니다. **[!UICONTROL 열 이름]** 필드.
1. 에서 필터에 대한 레이블을 지정합니다. **[!UICONTROL 필터 레이블]** 필드. 다음 항목 선택 **[!UICONTROL 십진수 값 활성화]** 범위를 정의하는 동안 숫자의 십진수 값을 수락하는 확인란입니다.
1. 구성에 대한 선택적 설명을 지정하고 을 누릅니다 **[!UICONTROL 완료]** 저장하려고.

구성 변경 사항은 필터 페이지를 열 때 반영됩니다. 4단계에서 지정한 필터 레이블은 최대값과 최소값을 정의하는 옵션이 있는 레이블로 표시됩니다. Enter 키를 누르면 [!DNL Experience Manager] 3단계에서 지정된 열 이름에 검색 기준을 적용하고 받은 편지함 항목을 반환합니다.

>[!NOTE]
>
>이 문서에는 최신 사용자 인터페이스 옵션이 나열되어 있습니다. 옵션 이름은 향후 릴리스의 사용자 인터페이스에 업데이트됩니다.

## 텍스트 조건자 구성 {#text-predicate}

텍스트 술어를 사용하여 받은 편지함 항목을 필터링하여 받은 편지함 열 내에서 텍스트 문자열을 검색합니다.

텍스트 술어를 구성하려면 다음을 수행합니다.

1. 를 엽니다. [구성을 위한 양식](#creating-opening-customized-configuration).
1. 탭 **[!UICONTROL 조건자 선택]** 탭하고 드래그 **[!UICONTROL 텍스트 조건자]** 을 양식으로 변환.
1. 다음에서 **[!UICONTROL 설정]** 탭에서 검색 기준으로 사용할 받은 편지함 열 이름을 선택합니다. **[!UICONTROL 열 이름]** 필드.
1. 검색 텍스트 상자에 표시되는 텍스트를 **[!UICONTROL 검색 텍스트 상자 자리 표시자]** 필드.
1. 구성에 대한 선택적 설명을 지정하고 을 누릅니다 **[!UICONTROL 완료]** 저장하려고.

구성 변경 사항은 필터 페이지를 열 때 반영됩니다. Enter 키를 누르면 [!DNL Experience Manager] 4단계에서 지정된 검색 텍스트를 3단계에서 지정된 열 이름에 적용하고 받은 편지함 항목을 반환합니다.

## 날짜 범위 설명 구성 {#date-range-predicate}

날짜 범위 술어를 사용하여 받은 편지함 항목을 필터링하여 받은 편지함 열 내에서 날짜 범위를 검색할 수 있습니다.

날짜 범위 술어를 구성하려면 다음을 수행합니다.

1. 를 엽니다. [구성을 위한 양식](#creating-opening-customized-configuration).
1. 탭 **[!UICONTROL 조건자 선택]** 탭하고 드래그 **[!UICONTROL 날짜 범위 조건자]** 을 양식으로 변환.
1. 다음에서 **[!UICONTROL 설정]** 탭에서 검색 기준으로 사용할 받은 편지함 열 이름을 선택합니다. **[!UICONTROL 열 이름]** 필드.
1. 에서 날짜 범위 필터의 레이블을 지정합니다. **[!UICONTROL 필터 레이블]** 필드.
1. 필터의 시작 날짜 및 종료 날짜 레이블을 지정합니다.
1. 구성에 대한 선택적 설명을 지정하고 을 누릅니다 **[!UICONTROL 완료]** 저장하려고.

구성 변경 사항은 필터 페이지를 열 때 반영됩니다. 4단계에서 지정한 필터 레이블은 5단계에서 지정한 시작 날짜 및 종료 날짜 레이블과 함께 날짜 범위 필터의 레이블로 표시됩니다. [!DNL Experience Manager] 3단계에서 지정된 열 이름에 검색 기준을 적용하고 받은 편지함 항목을 반환합니다.

## 사용자 정의 열 옵션 술어 구성 {#custom-column-options-predicate}

사용자 지정 열 옵션 술어를 사용하여 받은 편지함 항목을 필터링하여 받은 편지함 열 내에서 사용자 지정 옵션을 검색할 수 있습니다.

사용자 정의 열 옵션 술어를 구성하려면 다음을 수행합니다.

1. 를 엽니다. [구성을 위한 양식](#creating-opening-customized-configuration).
1. 탭 **[!UICONTROL 조건자 선택]** 탭하고 드래그 **[!UICONTROL 사용자 정의 열 옵션 조건자]** 을 양식으로 변환.
1. 다음에서 **[!UICONTROL 설정]** 탭에서 검색 기준으로 사용할 받은 편지함 열 이름을 선택합니다. **[!UICONTROL 열 이름]** 필드.
1. 에서 사용자 지정 열 옵션 필터의 레이블을 지정합니다. **[!UICONTROL 필터 레이블]** 필드.
1. 다음 항목 선택 **[!UICONTROL 단일 선택]** 확인란을 선택하여 받은 편지함 열에 필터를 적용하는 동안 하나의 옵션만 선택할 수 있습니다.
1. 다음에서 **[!UICONTROL 옵션 추가]** 섹션:
   1. 선택 **[!UICONTROL 수동]** 필터 검색 옵션을 수동으로 정의합니다. 누르기 **[!UICONTROL 필터 옵션 추가]** 을 클릭하여 첫 번째 옵션을 정의합니다. 열 옵션의 레이블과 검색할 옵션 값 텍스트를 지정합니다. 예를 들어 을 검색하려는 경우 **여성** 받은 편지함 열의 값으로 **F** 열 옵션의 레이블로 사용하고 추가 **여성** 를 옵션 값 텍스트로 사용합니다. 마찬가지로 필터 옵션을 더 추가할 수 있습니다.
   1. 선택 **[!UICONTROL JSON 경로]** JSON 파일 경로를 사용하여 옵션을 정의합니다. 다음은 필터 옵션을 정의하는 샘플 JSON 파일입니다.

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

   1. 선택 **[!UICONTROL CRX 옵션 경로]** crx 저장소 경로를 사용하여 옵션을 정의합니다. 누르기 **[!UICONTROL 옵션 경로 추가]** 여러 경로를 추가합니다. 다음은 을(를) 정의하는 샘플입니다. `Male` 및 `Female` 필터 옵션:

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

1. 구성에 대한 선택적 설명을 지정하고 을 누릅니다 **[!UICONTROL 완료]** 저장하려고.

구성 변경 사항은 필터 페이지를 열 때 반영됩니다. 4단계에서 지정한 필터 레이블은 사용자 정의 열 옵션 술어에 대한 레이블로 표시됩니다. [!DNL Experience Manager] 3단계에서 지정된 열 이름에 6단계에서 정의된 검색 기준을 적용하고 받은 편지함 항목을 반환합니다.

다음 비디오는 를 기반으로 열을 필터링하는 단계를 보여 줍니다. `true` 및 `false` 옵션 값.

>[!VIDEO](https://video.tv.adobe.com/v/335679)

## 술어에 따라 검색 필터 보기 {#view-search-filters-for-predicates}

술어에 따라 검색 필터를 볼 수 있습니다. 선택 **[!UICONTROL 필터]** 받은 편지함 페이지에서 참조할 수 있습니다. 필터가 왼쪽 창에 표시됩니다. 그런 다음 검색 조건을 지정하여 받은 편지함 항목을 필터링할 수 있습니다.

![필터 페이지](assets/apply-filters.png)

술어 구성 관리에 대한 자세한 내용은 [검색 Forms 구성](search-forms.md).
