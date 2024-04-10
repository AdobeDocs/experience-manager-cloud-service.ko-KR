---
title: URL에서 드롭다운 목록 옵션 로드
description: 드롭다운 목록 옵션은 개별 스프레드시트에 포함된 다음 제공된 URL을 통해 기본 스프레드시트로 가져옵니다.
feature: Edge Delivery Services
hide: true
hidefromtoc: true
source-git-commit: eadfc3d448bd2fadce08864ab65da273103a6212
workflow-type: tm+mt
source-wordcount: '520'
ht-degree: 2%

---


# URL에서 드롭다운 목록 옵션 로드

Edge Delivery Services 양식에서는 사전 정의된 옵션 세트에서 값을 선택할 수 있는 옵션이 제공됩니다. 양식 작성자는 `select` 요소: 선택 항목 목록을 제공합니다.
예를 들어 `enquiry` form에는 국가를 선택할 수 있는 드롭다운 메뉴가 있으며, 사용자가 선택할 수 있는 사전 정의된 국가의 범위를 제공합니다. 이 목록은 쉼표로 구분된 긴 국가 목록으로 구성되어 있습니다.

![드롭다운 옵션](/help/forms/assets/drop-down-options.png)

드롭다운 메뉴에 대한 긴 옵션 목록은 양식의 정의가 포함된 시트에 직접 추가할 때 관리가 번거로울 수 있습니다. 이러한 드롭다운 옵션을 저장할 별도의 시트를 만들면 프로세스를 간소화하고 간소화할 수 있습니다. 이 시트는 구조화된 형식으로 배열된 모든 드롭다운 옵션에 대한 중앙 집중식 저장소 역할을 합니다. 각 옵션은 고유한 행에 나열되므로 쉽게 관리하고 업데이트할 수 있습니다.

URL을 통해 다른 스프레드시트에서 옵션 목록을 로드하여 양식 작성 프로세스를 개선해 보겠습니다.

이 문서가 작성되면 다음 방법을 파악할 수 있습니다.

* [별도의 스프레드시트에서 옵션 정의](#define-options)
* [드롭다운 목록 옵션을 로드할 URL 추가](#add-url)

## 별도의 시트에서 옵션 정의 {#define-options}

다음 두 개의 열이 있는 시트를 만듭니다.`Option` 및 `Value`옵션을 정의하려면 다음을 수행하십시오.

1. Microsoft® SharePoint 또는 Google 드라이브 폴더의 AEM 프로젝트 폴더로 이동합니다.
2. 이름이 인 시트 추가 `shared-country` Microsoft® SharePoint 사이트 또는 Google 드라이브 폴더에 다음을 추가합니다.

   * **옵션**: 드롭다운 메뉴에 있는 옵션의 표시 값을 나타냅니다.
   * **값**: 사용자가 옵션을 선택할 때 제출된 값을 나타냅니다.

   >[!NOTE]
   >
   > 드롭다운 옵션의 값과 옵션이 동일한 경우 스프레드시트에는 **옵션** 열.

   새 시트를 추가하겠습니다. [공유 국가](/help/forms/assets/enquiry-options.xlsx) 에 표시되는 옵션용 `Destination` 드롭다운 목록 `enquiry` 양식.

   다음 그림을 참조하여 다음을 수행하십시오. `shared-country` 스프레드시트:

   ![국가별 드롭다운](/help/forms/assets/drop-down-country-options.png)
3. 미리보기 및 게시 `shared-country` 시트 사용 [AEM Sidekick](https://www.aem.live/developer/tutorial#preview-and-publish-your-content).

   다음을 보여주는 URL 참조 `shared-country` 시트: https://main--wefinance--wkndforms.hlx.live/enquiry.json?sheet=country

>[!NOTE]
>
> `?sheet=country` 는 URL에 추가된 쿼리 매개 변수입니다. 이 매개 변수는 다음을 기반으로 필터링된 JSON을 나타냅니다. `shared-country` 시트. 다른 국가와 관련된 정보가 포함된 JSON 파일로 리디렉션됩니다.

## 드롭다운 목록 옵션을 로드할 URL 추가{#add-url}

다음 `Options` 의 속성 `select` 필드는 URL을 허용합니다. 이 URL은 의 옵션으로 사용되는 JSON 배열을 반환합니다. `Destination` 드롭다운 목록입니다. 로드할 URL 드롭다운 목록 옵션을 추가하려면 다음을 수행합니다.

1. Microsoft® SharePoint 또는 Google 드라이브의 AEM 프로젝트 폴더로 이동하여 스프레드시트를 엽니다. 양식에 대한 새 스프레드시트를 만들 수도 있습니다.
1. 의 URL 복사 `shared-country` 을(를) 시트에 붙여 넣습니다. `Options` 열 `Destination` 필드.

   ![문의 스프레드시트](/help/forms/assets/drop-down-enquiry.png)

1. 다음을 사용하여 시트 미리보기 및 게시 [AEM Sidekick](https://www.aem.live/developer/tutorial#preview-and-publish-your-content).


   ![국가별 드롭다운](/help/forms/assets/load-dropdown-options-form.png)

다음을 참조할 수 있습니다 [조회 스프레드시트](/help/forms/assets/enquiry-options.xlsx) 을 클릭하여 로드할 URL 드롭다운 목록 옵션을 추가합니다.

양식 정의에 URL을 통합하여 드롭다운 목록 옵션을 로드한 후에는 `Destination` URL에서 드롭다운이 나타나기 시작합니다.

을 표시하는 아래 URL을 참조하십시오. `enquiry` 별도의 시트에 저장된 옵션을 표시하는 양식:

https://main--wefinance--wkndforms.hlx.live/enquiry-form

## 추가 참조

{{see-more-forms-eds}}


