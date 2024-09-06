---
title: ' [!DNL Adobe Experience Manager] as a [!DNL Cloud Service]용 자산 선택기'
description: 자산 선택기를 사용하여 애플리케이션 내에서 자산의 메타데이터와 렌디션을 검색하고 찾을 수 있습니다.
role: Admin, User
exl-id: cd5ec1de-36b0-48a5-95c9-9bd22fac9719
source-git-commit: f9f5b2a25933e059cceacf2ba69e23d528858d4b
workflow-type: tm+mt
source-wordcount: '1277'
ht-degree: 42%

---

# 자산 선택기 속성 {#asset-selector-properties}

자산 선택기 속성을 사용하여 자산 선택기가 렌더링되는 방식을 사용자 정의할 수 있습니다. 다음 표에는 자산 선택기를 사용자 정의하고 사용하는 데 사용할 수 있는 속성이 나열되어 있습니다.

| 속성 | 유형 | 필수 | 기본값 | 설명 |
|---|---|---|---|---|
| *레일* | 부울 | 아니요 | 거짓 | `true`(으)로 표시된 경우 자산 선택기가 왼쪽 레일 보기에서 렌더링됩니다. `false`(으)로 표시되어 있으면 자산 선택기가 모달 보기에서 렌더링됩니다. |
| *imsOrg* | 문자열 | 예 | | 조직에 [!DNL Adobe Experience Manager] as a [!DNL Cloud Service]를 프로비저닝하는 중에 할당된 Adobe IMS(Identity Management System)입니다. 액세스 중인 조직이 Adobe IMS에 속해 있는지 여부를 인증하려면 `imsOrg` 키가 필요합니다. |
| *imsToken* | 문자열 | 아니요 | | 인증에 사용되는 IMS 전달자 토큰입니다. 통합을 위해 [!DNL Adobe] 응용 프로그램을 사용하는 경우 `imsToken`이(가) 필요합니다. |
| *apiKey* | 문자열 | 아니요 | | AEM Discovery 서비스에 액세스하는 데 사용되는 API 키입니다. [!DNL Adobe] 응용 프로그램 통합을 사용하는 경우 `apiKey`이(가) 필요합니다. |
| *filterSchema* | 배열 | 아니요 | | 필터 속성을 구성하는 데 사용되는 모델입니다. 자산 선택기에서 특정 필터 옵션을 제한하려는 경우에 유용합니다. |
| *filterFormProps* | 오브젝트 | 아니요 | | 검색을 세분화하는 데 사용해야 하는 필터 속성을 지정합니다. 대상! 예: MIME 유형 JPG, PNG, GIF. |
| *selectedAssets* | 배열 `<Object>` | 아니요 |                 | 자산 선택기가 렌더링될 때 선택된 자산을 지정합니다. 자산의 ID 속성을 포함하는 오브젝트 배열이 필요합니다. 그 예로는 `[{id: 'urn:234}, {id: 'urn:555'}]` 등이 있습니다. 또한 현재 디렉터리에서 자산을 사용할 수 있어야 합니다. 다른 디렉터리를 사용해야 하는 경우 `path` 속성 값도 제공하십시오. |
| *acvConfig* | 오브젝트 | 아니요 | | 기본값을 재정의하기 위한 사용자 지정 구성이 포함된 개체를 포함하는 자산 컬렉션 보기 속성입니다. 또한 이 속성은 `rail` 속성과 함께 사용되어 자산 뷰어의 레일 보기를 사용할 수 있습니다. |
| *i18nSymbols* | `Object<{ id?: string, defaultMessage?: string, description?: string}>` | 아니요 |                 | OOTB 번역이 응용 프로그램의 요구 사항에 충분하지 않은 경우 `i18nSymbols` prop을 통해 사용자 지정 지역화된 값을 전달할 수 있는 인터페이스를 표시할 수 있습니다. 이 인터페이스를 통해 값을 전달하면 제공된 기본 번역이 무시되고 대신 자체 번역이 사용됩니다. 재정의를 수행하려면 유효한 재정의하려는 `i18nSymbols`의 키에 [메시지 설명자](https://formatjs.io/docs/react-intl/api/#message-descriptor) 오브젝트를 전달해야 합니다. |
| *intl* | 오브젝트 | 아니요 | | 자산 선택기는 기본 OOTB 번역을 제공합니다. `intl.locale` 속성을 통해 유효한 로케일 문자열을 제공하여 번역 언어를 선택할 수 있습니다. 예를 들어 `intl={{ locale: "es-es" }}`의 경우 </br></br> 지원되는 로케일 문자열은 언어 표준의 이름을 표현하기 위해 [ISO 639 - 코드](https://www.iso.org/iso-639-language-codes.html)를 따릅니다. </br></br> 지원되는 로케일 목록: 영어 - “en-us”(기본값) 스페인어 - “es-es” 독일어 - “de-de” 프랑스어 - “fr-fr” 이탈리아어 - “it-it” 일본어 - “ja-jp” 한국어 - “ko-kr” 포르투갈어 - “pt-br” 중국어(번체) - “zh-cn” 중국어(대만) - “zh-tw” |
| *repositoryId* | 문자열 | 아니요 | &#39;&#39; | 자산 선택기가 콘텐츠를 로드하는 저장소입니다. |
| *additionalAemSolutions* | `Array<string>` | 아니요 | [ ] | 추가 AEM 저장소 목록을 추가할 수 있습니다. 이 속성에 정보를 제공하지 않으면 미디어 라이브러리 또는 AEM Assets 저장소만 고려됩니다. |
| *hideTreeNav* | 부울 | 아니요 |  | 자산 트리 탐색 사이드바를 표시할지 또는 숨길지 지정합니다. 모달 보기에서만 사용되므로 레일 보기에서는 이 속성이 영향을 미치지 않습니다. |
| *onDrop* | 함수 | 아니요 | | 이 속성은 자산의 드롭 기능을 허용합니다. |
| *dropOptions* | `{allowList?: Object}` | 아니요 | | “allowList”를 사용하여 드롭 옵션을 구성합니다. |
| *colorScheme* | 문자열 | 아니요 | | 자산 선택기에 대한 테마를 구성합니다(`light` 또는 `dark`). |
| *테마* | 문자열 | 아니요 | 기본값 | `default`에서 `express` 사이의 자산 선택기 응용 프로그램에 테마를 적용합니다. `@react-spectrum/theme-express`도 지원합니다. |
| *handleSelection* | 함수 | 아니요 | | 자산을 선택하고 모달의 `Select` 버튼을 클릭하면 자산 항목 배열과 함께 호출됩니다. 이 함수는 모달 보기에서만 호출됩니다. 레일 보기의 경우 `handleAssetSelection` 또는 `onDrop` 함수를 사용하십시오. 예: <pre>handleSelection=(assets: Asset[])=> {...}</pre> 자세한 내용은 [자산 선택](/help/assets/asset-selector-customization.md#selection-of-assets)을 참조하세요. |
| *handleAssetSelection* | 함수 | 아니요 | | 자산을 선택하거나 선택 취소할 때 항목 배열과 함께 호출됩니다. 이 속성은 사용자가 자산을 선택할 때 자산을 수신하려는 경우에 유용합니다. 예: <pre>handleSelection=(assets: Asset[])=> {...}</pre> 자세한 내용은 [자산 선택](/help/assets/asset-selector-customization.md#selection-of-assets)을 참조하세요. |
| *onClose* | 함수 | 아니요 | | 모달 보기에서 `Close` 버튼을 누르면 호출됩니다. 이 속성은 `modal` 보기에서만 호출되며 `rail` 보기에서는 무시됩니다. |
| *onFilterSubmit* | 함수 | 아니요 | | 사용자가 다른 필터 조건을 변경할 때 필터 항목과 함께 호출됩니다. |
| *selectionType* | 문자열 | 아니요 | 미혼 | 한 번에 `single` 자산을 선택할지 또는 `multiple` 자산을 선택할지에 대한 구성입니다. |
| 허용 목록에 추가하다 *dragOptions.drag* | 부울 | 아니요 | | 속성은 선택할 수 없는 에셋의 드래그를 허용하거나 거부하는 데 사용됩니다. |
| *aemTierType* | 문자열 | 아니요 |  | 게재 계층, 작성자 계층 또는 둘 다의 자산을 표시할지 여부를 선택할 수 있습니다. <br><br> 구문: `aemTierType:[0]: "author" 1: "delivery"` <br><br> 예를 들어 `["author","delivery"]`을(를) 모두 사용하는 경우 저장소 전환기에 작성자와 게재 모두에 대한 옵션이 표시됩니다. |
| *handleNavigateToAsset* | 함수 | 아니요 | | 에셋 선택을 처리하는 콜백 함수입니다. |
| *noWrap* | 부울 | 아니요 | | *noWrap* 속성은 측면 레일 패널에서 자산 선택기를 렌더링하는 데 도움이 됩니다. 이 속성이 언급되지 않으면 기본적으로 *대화 상자 보기*&#x200B;가 렌더링됩니다. |
| *dialogSize* | 소형, 중형, 대형, 전체 화면 또는 전체 화면 인계 | 문자열 | 옵션 | 제공된 옵션을 사용하여 크기를 지정하여 레이아웃을 제어할 수 있습니다. |
| *colorScheme* | 밝은 색 또는 어두운 색 | 아니요 | | 이 속성은 자산 선택기 응용 프로그램의 테마를 설정하는 데 사용됩니다. 밝은 테마 또는 어두운 테마 중에서 선택할 수 있습니다. |
| *filterRepoList* | 함수 | 아니요 |  | Experience Manager 저장소를 호출하고 필터링된 저장소 목록을 반환하는 `filterRepoList` 콜백 함수를 사용할 수 있습니다. |
| *만료 옵션* | 함수 | | | 만료된 에셋의 상태를 제공하는 **getExpiryStatus** 속성 사이에서 사용할 수 있습니다. 함수는 제공한 에셋의 만료 날짜에 따라 `EXPIRED`, `EXPIRING_SOON` 또는 `NOT_EXPIRED`을(를) 반환합니다. [만료된 에셋 사용자 지정](/help/assets/asset-selector-customization.md#customize-expired-assets)을 참조하십시오. 또한 함수 값이 `true` 또는 `false`일 수 있는 **allowSelectionAndDrag**&#x200B;을(를) 사용할 수 있습니다. 값을 `false`(으)로 설정하면 만료된 에셋을 캔버스에서 선택하거나 드래그할 수 없습니다. |
| *showToast* | | 아니요 | | 이를 통해 에셋 선택기에서 만료된 에셋에 대한 사용자 지정 Toast 메시지를 표시할 수 있습니다. |
| *metadataSchema* | 배열 | 아니요 | | 사용자로부터 메타데이터를 수집하기 위해 제공하는 필드 배열을 추가합니다. 이 속성을 사용하면 자산에 자동으로 할당되지만 사용자에게 표시되지 않는 숨겨진 메타데이터를 사용할 수도 있습니다. |
| *onMetadataFormChange* | 콜백 함수 | 아니요 | | `property`과(와) `value`(으)로 구성됩니다. `Property`은(는) 값이 업데이트되는 *metadataSchema*&#x200B;에서 전달된 필드의 *mapToProperty*&#x200B;과(와) 같습니다. 반면, `value`은(는) 새 값이 입력으로 제공됩니다. |
| *targetUploadPath* | 문자열 |  | `"/content/dam"` | 에셋 저장소의 루트로 기본 설정되는 파일의 대상 업로드 경로입니다. |
| *hideUploadButton* | 부울 | | 거짓 | 내부 업로드 단추를 숨길지 여부를 확인합니다. |
| *onUploadStart* | 함수 | 아니요 |  | Dropbox, OneDrive 또는 로컬 간에 업로드 소스를 전달하는 데 사용되는 콜백 함수입니다. 구문은 `(uploadInfo: UploadInfo) => void`입니다. |
| *importSettings* | 함수 | | | 서드파티 소스에서 에셋을 가져올 수 있습니다. `sourceTypes`은(는) 사용할 가져오기 소스의 배열을 사용합니다. 지원되는 소스는 Onedrive 및 Dropbox입니다. 구문은 `{ sourceTypes?: ImportSourceType[]; apiKey?: string; }`입니다. |
| *onUploadComplete* | 함수 | 아니요 | | 성공, 실패 또는 복제 중 파일 업로드 상태를 전달하는 데 사용되는 콜백 함수입니다. 구문은 `(uploadStats: UploadStats) => void`입니다. |
| *onFilesChange* | 함수 | 아니요 | | 파일이 변경될 때 업로드의 동작을 표시하는 데 사용되는 콜백 함수입니다. 업로드를 위해 보류 중인 새 파일 배열과 업로드의 소스 유형을 전달합니다. 오류가 발생한 경우 Source 유형은 null일 수 있습니다. 구문은 `(newFiles: File[], uploadType: UploadType) => void`입니다. |
| *uploadingPlaceholder* | 문자열 | | | 에셋 업로드가 시작되면 메타데이터 양식을 대체하는 자리 표시자 이미지입니다. 구문은 `{ href: string; alt: string; } `입니다. |
| *uploadConfig* | 오브젝트 | | | 이 개체는 업로드에 대한 사용자 지정된 구성을 포함합니다. |
| *기능 집합* | 배열 | 문자열 | | `featureSet:[ ]` 속성은 자산 선택기 응용 프로그램에서 특정 기능을 활성화하거나 비활성화하는 데 사용됩니다. 구성 요소 또는 기능을 활성화하기 위해 배열에 문자열 값을 전달하거나 배열을 비워 두어 해당 구성 요소를 비활성화할 수 있습니다. 예를 들어 자산 선택기에서 업로드 기능을 활성화하려면 `featureSet:[0:"upload"]` 구문을 사용합니다. |

<!--
| *rootPath* | String | No | /content/dam/ | Folder path from which Asset Selector displays your assets. `rootPath` can also be used in the form of encapsulation. For example, given the following path, `/content/dam/marketing/subfolder/`, Asset Selector does not allow you to traverse through any parent folder, but only displays the children folders. |
| *path* | String | No | | Path that is used to navigate to a specific directory of assets when the Asset Selector is rendered. |
| *expirationDate* | Function | No | | This function is used to set the usability period of an asset. |
| *disableDefaultBehaviour* | Boolean | No | False | It is a function that is used to enable or disable the selection of an expired asset. You can customize the default behavior of an asset that is set to expire. See [customize expired assets](/help/assets/asset-selector-customization.md#customize-expired-assets). |
-->
