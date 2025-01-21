---
title: AEM Forms as a Cloud Service용 Edge Delivery Services에 대한 URL 또는 다른 시트의 드롭다운 목록 옵션 로드
description: 드롭다운 목록 옵션은 별도의 스프레드시트에 포함되며, 이후 제공된 URL을 통해 기본 스프레드시트로 가져옵니다.
feature: Edge Delivery Services
exl-id: 5b0bc1b6-6e33-41f3-b7c1-4d997787b6cd
role: Admin, Architect, Developer
source-git-commit: cb914f76b0b785a89b20ef5eaacbc36e8217944b
workflow-type: tm+mt
source-wordcount: '506'
ht-degree: 87%

---


# AEM Forms as a Cloud Service용 Edge Delivery Services에 대한 URL 또는 다른 시트의 옵션

양식의 사전 정의 옵션 중에는 사용자가 선택할 수 있는 드롭다운 메뉴가 포함되어 있는 경우가 많습니다. 이러한 옵션은 일반적으로 양식 자체에서 정의되지만 긴 목록을 관리하는 것이 번거로울 수 있습니다. 이 안내서에서는 URL을 통해 개별 스프레드시트에서 드롭다운 옵션을 로드하여 양식 작성을 향상시키는 방법에 대해 설명합니다.


개별 스프레드시트에서 드롭다운 옵션을 로드하면 다음과 같은 이점이 있습니다.

* 단순화된 관리: 중앙 관리식으로 드롭다운 옵션을 유지하여 업데이트 및 추가를 쉽게 할 수 있습니다.
* 향상된 효율성: 양식 정의 내에서 긴 옵션 목록을 수동으로 추가할 필요가 없습니다.

![드롭다운 옵션](/help/forms/assets/drop-down-options.png)


이 문서가 작성되면 다음 방법을 파악할 수 있습니다.

* [개별 스프레드시트에서 옵션 정의](#define-options)
* [드롭다운 목록 옵션을 로드할 URL 추가](#add-url)

## 개별 시트에 옵션 정의 {#define-options}

개별 스프레드시트에서 옵션 정의

1. 스프레드시트 만들기:
   1. Microsoft® SharePoint 또는 Google Drive에서 AEM 프로젝트 폴더를 찾습니다.
   1. 새 시트를 추가합니다. 예를 들어 “shared-country”입니다.
1. 옵션 열 정의:
“옵션”과 “값”의 두 열을 추가합니다.
   * “옵션”은 드롭다운 메뉴에 표시되는 텍스트를 정의합니다.
   * “값”은 사용자가 옵션을 선택할 때 제출된 값을 정의합니다.

   >[!NOTE]
   >
   >옵션과 값이 모두 동일한 경우 “옵션” 열만 있으면 됩니다.

1. 스프레드시트 채우기:
“옵션” 열(및 필요한 경우 “값” 열)에 국가 옵션을 입력합니다.

   구조는 아래의 예를 참조하십시오.

   ![국가별 드롭다운](/help/forms/assets/drop-down-country-options.png)

1. [AEM Sidekick](https://www.aem.live/developer/tutorial#preview-and-publish-your-content)을 사용하여 `shared-country` 시트를 미리 보고 게시합니다.

   예를 들어 프로젝트의 저장소 이름이 &quot;wefinance&quot;인 경우 계정 소유자 &quot;wkndform&quot; 아래에 있으며 `shared-country` 시트를 표시하는 URL인 &quot;main&quot; 분기를 사용합니다.
   `https://main--wefinance--wkndform.aem.live/enquiry.json?sheet=country`
   <!--(https://main--wefinance--wkndform.aem.live/enquiry.json?sheet=country)  -->

>[!NOTE]
>
> `?sheet=country`는 URL에 추가되는 쿼리 매개변수입니다. 이 매개변수는 `shared-country` 시트를 기준으로 필터링된 JSON을 나타냅니다. 다양한 국가와 관련된 정보가 있는 JSON 파일로 리디렉션됩니다.

## 드롭다운 목록 옵션을 로드할 URL 추가{#add-url}

`select` 필드의 `Options` 속성은 URL을 허용합니다. URL은 `Destination` 드롭다운 목록의 옵션으로 사용되는 JSON 배열을 반환합니다. 드롭다운 목록 옵션을 로드할 URL을 추가하는 방법:

1. Microsoft® SharePoint 또는 Google Drive의 AEM 프로젝트 폴더로 이동하여 스프레드시트를 엽니다. 양식의 스프레드시트를 새로 만들 수도 있습니다.
1. `shared-country` 시트의 URL을 복사하여 `Destination` 필드의 `Options` 열에 붙여넣습니다.

   ![문의 스프레드시트](/help/forms/assets/drop-down-enquiry.png)

1. [AEM Sidekick](https://www.aem.live/developer/tutorial#preview-and-publish-your-content)을 사용하여 시트를 미리 보고 게시합니다.


   ![국가별 드롭다운](/help/forms/assets/load-dropdown-options-form.png)

드롭다운 목록 옵션을 로드하기 위해 URL을 추가하려면 [문의 스프레드시트](/help/edge/assets/enquiry.xlsx)를 참조하시기 바랍니다.

드롭다운 목록 옵션을 로드하기 위해 URL을 양식 정의에 통합한 후 `Destination` 드롭다운이 URL에 표시되기 시작합니다.

예를 들어 프로젝트의 저장소 이름이 &quot;wefinance&quot;이고 계정 소유자 &quot;wkndform&quot; 아래에 있으며 &quot;main&quot; 분기를 사용하는 경우 아래 URL에는 별도의 시트에 저장된 옵션을 표시하는 `enquiry` 양식이 표시됩니다.

`https://main--wefinance--wkndform.aem.live/enquiry-form`
<!--(https://main--wefinance--wkndform.aem.live/enquiry-form) 
-->

## 추가 참조

{{see-more-forms-eds}}


