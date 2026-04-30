---
title: 콘텐츠 관리자 속성
description: 속성을 사용하여 응용 프로그램과 통합할 때 콘텐츠 관리자가 렌더링하는 방법을 사용자 지정합니다.
role: Admin, User
badgeSaas: label="AEM Assets" type="Positive" tooltip="AEM Assets에 적용됩니다)."
exl-id: cd5ec1de-36b0-48a5-95c9-9bd22fac9719
source-git-commit: c92611e4b815e49887e175943b81177e60623067
workflow-type: tm+mt
source-wordcount: '2506'
ht-degree: 24%

---

# Content Advisor 설치 및 속성 {#content-advisor-installation-properties}

또한 Content Advisor를 타사 애플리케이션과 통합하여 Adobe 애플리케이션 이상의 지능형 에셋 검색을 확장할 수도 있습니다. AI 기반 검색, 컨텍스트 인식 권장 사항, Campaign Brief 기반 검색, Dynamic Media 렌디션에 대한 액세스, 콘텐츠 조각 검색, 필터 및 에셋 메타데이터를 비롯한 동일한 다양한 기능 세트가 서드파티 통합에서 지원됩니다.

## 사전 요구 사항{#prereqs}

다음 커뮤니케이션 방법을 보장해야 합니다.

* 호스트 애플리케이션이 HTTPS에서 실행 중입니다.
* 해당 애플리케이션을 `localhost`에서 실행할 수 없습니다. 로컬 컴퓨터에서 콘텐츠 관리자를 통합하려면 `[https://<your_campany>.localhost.com:<port_number>]`과(와) 같은 사용자 지정 도메인을 만들고 `redirectUrl list`에 이 사용자 지정 도메인을 추가해야 합니다.
* clientID를 구성하여 각각의 `imsClientId`로 AEM Cloud Service 환경 변수에 추가할 수 있습니다.
<!--
* You can configure and add `ADOBE_PROVIDED_CLIENT_ID` into the AEM Cloud Service environment variable with the respective `imsClientId`.
![Asset Selector IMS Client id environment](assets/asset-selector-ims-client-id-env.png)
-->
* IMS 범위 목록은 환경 구성에서 정의되어야 합니다.
* 애플리케이션의 URL이 IMS 클라이언트가 허용하는 리디렉션 URL 목록에 있습니다.
* IMS 로그인 흐름은 웹 브라우저의 팝업을 사용하여 구성 및 렌더링됩니다. 따라서 타깃 브라우저에서 팝업을 활성화하거나 허용해야 합니다.

Content Advisor의 IMS 인증 워크플로가 필요한 경우 위의 사전 요구 사항을 사용하십시오. 또는 이미 IMS 워크플로로 인증된 경우 대신 IMS 정보를 추가할 수 있습니다.

>[!IMPORTANT]
>
> 이 저장소는 Content Advisor를 통합하기 위해 사용 가능한 API 및 사용 예를 설명하는 보조 설명서로 사용됩니다. Content Advisor를 설치하거나 사용하기 전에 조직에서 Experience Manager Assets as a Cloud Service 프로필의 일부로 Content Advisor에 대한 액세스 권한이 제공되었는지 확인하십시오. 프로비저닝되지 않은 경우 이러한 구성 요소를 통합하거나 사용할 수 없습니다. 프로비저닝을 요청하려면 프로그램 관리자가 Admin Console에서 P2로 표시된 지원 티켓을 올리고 다음 정보를 포함해야 합니다.
>
>* 통합 애플리케이션이 호스팅되는 도메인 이름.
>* 프로비저닝 후 조직에는 콘텐츠 관리자 구성에 필요한 요청된 환경에 해당하는 `imsClientId`, `imsScope` 및 `redirectUrl`이(가) 제공됩니다. 이러한 유효한 속성이 없으면 설치 단계를 실행할 수 없습니다.

## 설치 {#content-advisor-installation}

Content Advisor는 ESM CDN(예: [esm.sh](https://esm.sh/)/[skypack](https://www.skypack.dev/))과 [UMD](https://github.com/umdjs/umd) 버전 모두를 통해 사용할 수 있습니다.

**UMD 버전**&#x200B;을 사용하는 브라우저의 경우(권장됨):

```
<script src="https://experience.adobe.com/solutions/CQ-assets-selectors/static-assets/resources/assets-selectors.js"></script>

<script>
  const { renderAssetSelector } = PureJSSelectors;
</script>
```

**ESM CDN 버전**&#x200B;을 사용하며 `import maps`가 지원되는 브라우저의 경우:

```
<script type="module">
  import { AssetSelector } from 'https://experience.adobe.com/solutions/CQ-assets-selectors/static-assets/resources/@assets/selectors/index.js'
</script>
```

**ESM CDN 버전**&#x200B;을 사용하는 Deno/Webpack Module Federation의 경우:

```
import { AssetSelector } from 'https://experience.adobe.com/solutions/CQ-assets-selectors/static-assets/resources/@assets/selectors/index.js'
```

## 콘텐츠 관리자 속성 {#content-advisor-propertiess}

콘텐츠 관리자 속성을 사용하여 콘텐츠 관리자가 렌더링되는 방식을 사용자 지정할 수 있습니다. 다음 표는 콘텐츠 관리자를 사용자 정의하고 사용하는 데 사용할 수 있는 속성을 보여 줍니다.

| 속성 | 유형 | 필수 | 기본값 | 설명 |
|---|---|---|---|---|
| *레일* | 부울 | 아니요 | 거짓 | `true`(으)로 표시된 경우 콘텐츠 관리자가 왼쪽 레일 보기에서 렌더링됩니다. `false`(으)로 표시되어 있으면 콘텐츠 관리자가 모달 보기에서 렌더링됩니다. |
| *imsOrg* | 문자열 | 예 | | 조직에 [!DNL Adobe Experience Manager] as a [!DNL Cloud Service]를 프로비저닝하는 중에 할당된 Adobe IMS(Identity Management System)입니다. 액세스 중인 조직이 Adobe IMS에 속해 있는지 여부를 인증하려면 `imsOrg` 키가 필요합니다. |
| *imsToken* | 문자열 | 아니요 | | 인증에 사용되는 IMS 전달자 토큰입니다. 통합을 위해 [!DNL Adobe] 응용 프로그램을 사용하는 경우 `imsToken`이(가) 필요합니다. |
| *apiKey* | 문자열 | 아니요 | | AEM Discovery 서비스에 액세스하는 데 사용되는 API 키입니다. [!DNL Adobe] 응용 프로그램 통합을 사용하는 경우 `apiKey`이(가) 필요합니다. |
| *externalBrief* | 문자열 | 아니요 | | 캠페인 개요 문서를 업로드하여 검색 키워드를 수동으로 입력하지 않고도 관련 에셋을 검색할 수 있습니다. 콘텐츠 관리자는 캠페인 개요의 정보를 분석하여 캠페인의 의도를 파악하고 AEM Assets에서 사용할 수 있는 관련 에셋을 권장합니다. |
| *filterSchema* | 배열 | 아니요 | | 필터 속성을 구성하는 데 사용되는 모델입니다. 이 기능은 콘텐츠 권고자에서 특정 필터 옵션을 제한하려는 경우 유용합니다. |
| *filterFormProps* | 오브젝트 | 아니요 | | 검색을 세분화하는 데 사용해야 하는 필터 속성을 지정합니다. 대상! 예: MIME 유형 JPG, PNG, GIF. |
| *selectedAssets* | 배열 `<Object>` | 아니요 |                 | 컨텐츠 권고자가 렌더링될 때 선택한 Assets을 지정합니다. 자산의 ID 속성을 포함하는 오브젝트 배열이 필요합니다. 그 예로는 `[{id: 'urn:234}, {id: 'urn:555'}]` 등이 있습니다. 또한 현재 디렉터리에서 자산을 사용할 수 있어야 합니다. 다른 디렉터리를 사용해야 하는 경우 `path` 속성 값도 제공하십시오. |
| *acvConfig* | 오브젝트 | 아니요 | | 기본값을 재정의하기 위한 사용자 지정 구성이 포함된 개체를 포함하는 자산 컬렉션 보기 속성입니다. 또한 이 속성은 `rail` 속성과 함께 사용되어 자산 뷰어의 레일 보기를 사용할 수 있습니다. |
| *i18nSymbols* | `Object<{ id?: string, defaultMessage?: string, description?: string}>` | 아니요 |                 | OOTB 번역이 응용 프로그램의 요구 사항에 충분하지 않은 경우 `i18nSymbols` prop을 통해 사용자 지정 지역화된 값을 전달할 수 있는 인터페이스를 표시할 수 있습니다. 이 인터페이스를 통해 값을 전달하면 제공된 기본 번역이 재정의되며 사용자 고유의 번역이 대신 사용됩니다. 재정의를 수행하려면 유효한 재정의하려는 `i18nSymbols`의 키에 [메시지 설명자](https://formatjs.io/docs/react-intl/api/#message-descriptor) 오브젝트를 전달해야 합니다. |
| *intl* | 오브젝트 | 아니요 | | 콘텐츠 관리자는 기본 OOTB 번역을 제공합니다. `intl.locale` 속성을 통해 유효한 로케일 문자열을 제공하여 번역 언어를 선택할 수 있습니다. 예: `intl={{ locale: "es-es" }}` </br></br> 지원되는 로케일 문자열은 언어 표준 이름 표현에 대한 [ISO 639 - 코드](https://www.iso.org/iso-639-language-codes.html)를 따릅니다. </br></br> 지원되는 로케일 목록: 영어 - &#39;en-us&#39;(기본값) 스페인어 - &#39;es-es&#39; 독일어 - &#39;de-de&#39; 프랑스어 - &#39;fr-fr&#39; 이탈리아어 - &#39;it-it&#39; 일본어 - &#39;ja-jp&#39; 한국어 - &#39;ko-kr&#39; 포르투갈어 - &#39;pt-br&#39; 중국어(번체) - &#39;zh-cn&#39; 중국어(대만) - &#39;zh-tw&#39; |
| *repositoryId* | 문자열 | 아니요 | &#39;&#39; | 콘텐츠 권고자가 콘텐츠를 로드하는 저장소입니다. |
| *additionalAemSolutions* | `Array<string>` | 아니요 | [ ] | 추가 AEM 저장소 목록을 추가할 수 있습니다. 이 속성에 정보를 제공하지 않으면 미디어 라이브러리 또는 AEM Assets 저장소만 고려됩니다. |
| *hideTreeNav* | 부울 | 아니요 |  | 자산 트리 탐색 사이드바를 표시할지 또는 숨길지 지정합니다. 모달 보기에서만 사용되므로 레일 보기에서는 이 속성이 영향을 미치지 않습니다. |
| *onDrop* | 함수 | 아니요 | | 놓기 기능은 에셋을 드래그하여 지정된 놓기 영역에 놓는 데 사용됩니다. 자산을 원활하게 이동 및 처리할 수 있는 대화형 사용자 인터페이스를 제공합니다. |
| *dropOptions* | `{allowList?: Object}` | 아니요 | | “allowList”를 사용하여 드롭 옵션을 구성합니다. |
| *테마* | 문자열 | 아니요 | 기본값 | `default`에서 `express` 사이의 콘텐츠 관리자 응용 프로그램에 테마를 적용합니다. `@react-spectrum/theme-express`도 지원합니다. |
| *handleSelection* | 함수 | 아니요 | | 자산을 선택하고 모달의 `Select` 버튼을 클릭하면 자산 항목 배열과 함께 호출됩니다. 이 함수는 모달 보기에서만 호출됩니다. 레일 보기의 경우 `handleAssetSelection` 또는 `onDrop` 함수를 사용하십시오. 예: <pre>handleSelection=(자산: 자산[])=> {...}</pre> 자세한 내용은 [자산 선택](/help/assets/content-advisor-customization.md#selection-of-assets)을 참조하세요. |
| *handleAssetSelection* | 함수 | 아니요 | | 자산을 선택하거나 선택 취소할 때 항목 배열과 함께 호출됩니다. 이 속성은 사용자가 자산을 선택할 때 자산을 수신하려는 경우에 유용합니다. 예: <pre>handleAssetSelection=(자산: 자산[])=> {...}</pre> 자세한 내용은 [자산 선택](/help/assets/content-advisor-customization.md#selection-of-assets)을 참조하세요. |
| *onClose* | 함수 | 아니요 | | 모달 보기에서 `Close` 버튼을 누르면 호출됩니다. 이 속성은 `modal` 보기에서만 호출되며 `rail` 보기에서는 무시됩니다. |
| *onFilterSubmit* | 함수 | 아니요 | | 사용자가 다른 필터 조건을 변경할 때 필터 항목과 함께 호출됩니다. |
| *selectionType* | 문자열 | 아니요 | 미혼 | 한 번에 `single` 자산을 선택할지 또는 `multiple` 자산을 선택할지에 대한 구성입니다. |
| *dragOptions.drag* | 부울 | 아니요 | | 속성은 선택할 수 없는 에셋의 드래그를 허용하거나 거부하는 데 사용됩니다. [dragOptions 속성](/help/assets/content-advisor-customization.md#drag-options-property)을 참조하세요. |
| *aemTierType* | 문자열 | 아니요 |  | 게재 계층, 작성자 계층 또는 둘 다의 자산을 표시할지 여부를 선택할 수 있습니다. <br><br> 구문: `aemTierType: "author"  "delivery"` <br><br> 예를 들어 두 `["author","delivery"]`을(를) 모두 사용하는 경우 저장소 전환기에 작성자와 게재 모두에 대한 옵션이 표시됩니다. |
| *handleNavigateToAsset* | 함수 | 아니요 | | 에셋 선택을 처리하는 콜백 함수입니다. |
| *noWrap* | 부울 | 아니요 | | *noWrap* 속성을 사용하면 콘텐츠 관리자가 대화 상자에서 래핑되지 않습니다. 이 속성이 언급되지 않으면 기본적으로 *대화 상자 보기*&#x200B;가 렌더링됩니다. |
| *dialogSize* | S, M, L, fullscreen, fullscreenTakeover | 문자열 | 선택 사항 | 제공된 옵션을 사용하여 크기를 지정하여 레이아웃을 제어할 수 있습니다. |
| *colorScheme* | 문자열(밝게, 어둡게) | 아니요 | | 이 속성은 콘텐츠 관리자 응용 프로그램의 테마를 설정하는 데 사용됩니다. 밝은 테마 또는 어두운 테마 중에서 선택할 수 있습니다. |
| *filterRepoList* | 함수 | 아니요 | | 저장소 목록을 수신하고 필터링된 목록을 반환하는 함수입니다. |
| *만료 옵션* | 함수 | | | 만료된 에셋의 상태를 제공하는 **getExpiryStatus** 속성 사이에서 사용할 수 있습니다. 함수는 제공한 에셋의 만료 날짜에 따라 `EXPIRED`, `EXPIRING_SOON` 또는 `NOT_EXPIRED`을(를) 반환합니다. [만료된 에셋 사용자 지정](/help/assets/content-advisor-customization.md#customize-expired-assets)을 참조하십시오. 또한 함수 값이 `true` 또는 `false`일 수 있는 **allowSelectionAndDrag**&#x200B;을(를) 사용할 수 있습니다. 값을 `false`(으)로 설정하면 만료된 에셋을 캔버스에서 선택하거나 드래그할 수 없습니다. |
| *showToast* | | 아니요 | | 콘텐츠 관리자는 만료된 에셋에 대해 사용자 지정된 toast 메시지를 표시할 수 있습니다. |
| *uploadConfig* | 오브젝트 | | | 이 개체는 업로드에 대한 사용자 지정된 구성을 포함합니다. 유용성은 [업로드 구성](#content-advisor-customization.md#upload-config)을 참조하십시오. |
| *uploadConfig* > *metadataSchema* | 배열 | 아니요 | | 이 속성은 `uploadConfig` 속성에 중첩되어 있습니다. 사용자로부터 메타데이터를 수집하기 위해 제공하는 필드 배열을 추가합니다. 이 속성을 사용하면 자산에 자동으로 할당되지만 사용자에게 표시되지 않는 숨겨진 메타데이터를 사용할 수도 있습니다. |
| *uploadConfig* > *onMetadataFormChange* | 콜백 함수 | 아니요 | | 이 속성은 `uploadConfig` 속성에 중첩되어 있습니다. `property`과(와) `value`(으)로 구성됩니다. `Property`은(는) 값이 업데이트되는 *metadataSchema*&#x200B;에서 전달된 필드의 *mapToProperty*&#x200B;과(와) 같습니다. 반면, `value`은(는) 새 값이 입력으로 제공됩니다. |
| *uploadConfig* > *targetUploadPath* | 문자열 |  | `"/content/dam"` | 이 속성은 `uploadConfig` 속성에 중첩되어 있습니다. 에셋 저장소의 루트로 기본 설정되는 파일의 대상 업로드 경로입니다. |
| *uploadConfig* > *hideUploadButton* | 부울 | | 거짓 | 내부 업로드 단추를 숨길지 여부를 확인합니다. 이 속성은 `uploadConfig` 속성에 중첩되어 있습니다. |
| *uploadConfig* > *onUploadStart* | 함수 | 아니요 |  | Dropbox, OneDrive 또는 local 간에 업로드 소스를 전달하는 데 사용되는 콜백 함수입니다. 구문은 `(uploadInfo: UploadInfo) => void`입니다. 이 속성은 `uploadConfig` 속성에 중첩되어 있습니다. |
| *uploadConfig* > *importSettings* | 함수 | | | 서드파티 소스에서 에셋을 가져올 수 있습니다. `sourceTypes`은(는) 사용할 가져오기 소스의 배열을 사용합니다. 지원되는 소스는 Onedrive 및 Dropbox입니다. 구문은 `{ sourceTypes?: ImportSourceType[]; apiKey?: string; }`입니다. 또한 이 속성은 `uploadConfig` 속성에 중첩되어 있습니다. |
| *uploadConfig* > *onUploadComplete* | 함수 | 아니요 | | 성공, 실패 또는 복제 중 파일 업로드 상태를 전달하는 데 사용되는 콜백 함수입니다. 구문은 `(uploadStats: UploadStats) => void`입니다. 또한 이 속성은 `uploadConfig` 속성에 중첩되어 있습니다. |
| *uploadConfig* > *onFilesChange* | 함수 | 아니요 | | 이 속성은 `uploadConfig` 속성에 중첩되어 있습니다. 파일이 변경될 때 업로드의 동작을 표시하는 데 사용되는 콜백 함수입니다. 업로드를 위해 보류 중인 새 파일 배열과 업로드의 소스 유형을 전달합니다. 오류가 발생한 경우 Source 유형은 null일 수 있습니다. 구문은 `(newFiles: File[], uploadType: UploadType) => void`입니다. |
| *uploadConfig* > *uploadPlaceholder* | 문자열 | | | 에셋 업로드가 시작되면 메타데이터 양식을 대체하는 자리 표시자 이미지입니다. 구문은 `{ href: string; alt: string; }`입니다. 또한 이 속성은 `uploadConfig` 속성 아래에 중첩됩니다. |
| *기능 집합* | 배열 | 문자열 | | `featureSet:[ ]` 속성은 콘텐츠 관리자 응용 프로그램에서 특정 기능을 활성화하거나 비활성화하는 데 사용됩니다. 구성 요소 또는 기능을 활성화하려면 배열에 문자열 값을 전달하거나 추가된 기능을 비활성화하도록 배열을 비워 두고 기본 기능만 사용할 수 있습니다. 예를 들어 콘텐츠 관리자에서 업로드 기능을 활성화하려면 `featureSet:["upload"]` 구문을 사용합니다. 마찬가지로 `featureSet:["content-fragments"]`을(를) 사용하여 콘텐츠 관리자에서 콘텐츠 조각을 사용할 수 있습니다. 여러 기능을 함께 사용하려면 featureSet:[&quot;upload&quot;, &quot;content-fragments&quot;] 구문을 사용합니다. |

<!--
| *selectedRendition* | Object | | | This property allows users to define and control which renditions of an asset are displayed when the panel is accessed. This customization enhances user experience by filtering out unnecessary renditions and showcasing only the most relevant renditions. For example, `CopyUrlHref` allows you to use Dynamic Media renditions in your Asset Selector application (delivery URL). |
| *featureSet* | Array | String | | The `featureSet:[ ]` property is used to enable or disable a particular functionaly in the Asset Selector application. To enable the component or a feature, you can pass a string value in the array or leave the array empty to disable that component. For example, you want to enable upload functionality in the Asset Selector, use the syntax `featureSet:[0:"upload"]`. Similarly, you can use `featureSet:[0:"collections"]` to enable collections in the Asset Selector. Addidionally, use `featureSet:[0:"detail-panel"]` to enable [details panel](overview-asset-selector.md#asset-details-and-metadata) of an asset. Also, `featureSet:[0:"dm-renditions"]` to show Dynamic Media renditions of an asset.|
| *rootPath* | String | No | /content/dam/ | Folder path from which Asset Selector displays your assets. `rootPath` can also be used in the form of encapsulation. For example, given the following path, `/content/dam/marketing/subfolder/`, Asset Selector does not allow you to traverse through any parent folder, but only displays the children folders. |
| *path* | String | No | | Path that is used to navigate to a specific directory of assets when the Asset Selector is rendered. |
| *expirationDate* | Function | No | | This function is used to set the usability period of an asset. |
| *disableDefaultBehaviour* | Boolean | No | False | It is a function that is used to enable or disable the selection of an expired asset. You can customize the default behavior of an asset that is set to expire. See [customize expired assets](/help/assets/asset-selector-customization.md#customize-expired-assets). |
-->

### ImsAuthProps {#ims-auth-props}

`ImsAuthProps` 속성은 콘텐츠 관리자가 `imsToken`을(를) 가져오는 데 사용하는 인증 정보 및 흐름을 정의합니다. 이러한 속성을 설정하여 인증 플로우의 동작 방법을 제어하고 다양한 인증 이벤트에 대한 리스너를 등록할 수 있습니다.

| 속성 이름 | 설명 |
|---|---|
| `imsClientId` | 인증 용도로 사용되는 IMS 클라이언트 ID를 나타내는 문자열 값입니다. 이 값은 Adobe에서 제공하며 Adobe AEM CS 조직에만 해당됩니다. |
| `imsScope` | 인증에 사용되는 범위를 설명합니다. 범위는 응용 프로그램이 조직 리소스에 대해 갖는 액세스 수준을 결정합니다. 여러 범위는 쉼표로 구분할 수 있습니다. |
| `redirectUrl` | 인증 후 사용자가 리디렉션되는 URL을 나타냅니다. 이 값은 일반적으로 애플리케이션의 현재 URL로 설정됩니다. `redirectUrl`이(가) 제공되지 않으면 `ImsAuthService`에서 `imsClientId`을(를) 등록하는 데 사용되는 redirectUrl을 사용합니다. |
| `modalMode` | 인증 흐름을 모달(팝업)로 표시할지 여부를 나타내는 부울. `true`(으)로 설정하면 인증 흐름이 팝업에 표시됩니다. `false`(으)로 설정하면 전체 페이지를 다시 로드할 때 인증 흐름이 표시됩니다. 향상된 UX를 위해 브라우저 팝업이 비활성화된 경우 이 값을 동적으로 제어할 수 있습니다(_Note :_). |
| `onImsServiceInitialized` | Adobe IMS 인증 서비스가 초기화될 때 호출되는 콜백 함수입니다. 이 함수는 Adobe IMS 서비스를 나타내는 개체인 `service` 매개 변수 하나를 사용합니다. 자세한 내용은 [`ImsAuthService`](#imsauthservice-ims-auth-service)을(를) 참조하십시오. |
| `onAccessTokenReceived` | Adobe IMS 인증 서비스에서 `imsToken`을(를) 받을 때 호출되는 콜백 함수입니다. 이 함수는 액세스 토큰을 나타내는 문자열인 `imsToken` 매개 변수 하나를 사용합니다. |
| `onAccessTokenExpired` | 액세스 토큰이 만료된 경우 호출되는 콜백 함수입니다. 이 함수는 일반적으로 새 액세스 토큰을 얻기 위해 새 인증 흐름을 트리거하는 데 사용됩니다. |
| `onErrorReceived` | 인증 중에 오류가 발생할 때 호출되는 콜백 함수입니다. 이 함수는 오류 유형과 오류 메시지의 두 매개 변수를 사용합니다. 오류 유형은 오류의 유형을 나타내는 문자열이고, 오류 메시지는 오류 메시지를 나타내는 문자열이다. |

### ImsAuthService {#ims-auth-service}

`ImsAuthService` 클래스는 콘텐츠 관리자에 대한 인증 흐름을 처리합니다. Adobe IMS 인증 서비스에서 `imsToken`을(를) 가져옵니다. `imsToken`은(는) 사용자를 인증하고 [!DNL Adobe Experience Manager]에 대한 액세스를 [!DNL Cloud Service] Assets 저장소로 승인하는 데 사용됩니다. ImsAuthService는 `ImsAuthProps` 속성을 사용하여 인증 흐름을 제어하고 다양한 인증 이벤트에 대한 수신기를 등록합니다. 편리한 [`registerAssetsSelectorsAuthService`](#purejsselectorsregisterassetsselectorsauthservice) 함수를 사용하여 콘텐츠 관리자에 _ImsAuthService_ 인스턴스를 등록할 수 있습니다. 다음 함수는 `ImsAuthService` 클래스에서 사용할 수 있습니다. 그러나 _registerAssetsSelectorsAuthService_ 함수를 사용하는 경우에는 이러한 함수를 직접 호출할 필요가 없습니다.

| 함수 이름 | 설명 |
|---|---|
| `isSignedInUser` | 사용자가 현재 서비스에 로그인되어 있는지 여부를 확인하고 그에 따라 부울 값을 반환합니다. |
| `getImsToken` | 자산 렌디션 생성과 같은 다른 서비스에 대한 요청을 인증하는 데 사용할 수 있는 현재 로그인한 사용자에 대한 인증 `imsToken`을(를) 검색합니다. |
| `signIn` | 사용자의 로그인 프로세스를 시작합니다. 이 함수는 `ImsAuthProps`을(를) 사용하여 팝업 또는 전체 페이지 다시 로드 시 인증을 표시합니다. |
| `signOut` | 사용자를 서비스에서 로그아웃하고 인증 토큰을 무효화하며 보호된 리소스에 액세스하려면 다시 로그인해야 합니다. 이 함수를 호출하면 현재 페이지가 다시 로드됩니다. |
| `refreshToken` | 현재 로그인한 사용자에 대한 인증 토큰을 새로 고침하여 만료되지 않도록 하고 보호된 리소스에 대한 액세스를 중단하지 않도록 합니다. 후속 요청에 사용할 수 있는 새 인증 토큰을 반환합니다. |

### contentFragmentSelectorProps {#content-fragment-selector-properties}

`contentFragmentSelectorProps`을(를) 사용하면 콘텐츠 조각이 콘텐츠 관리자 내에서 액세스 및 표시되는 방법을 구성할 수 있습니다. `featureSet`에서 콘텐츠 조각 기능을 활성화하고 필요한 구성을 제공하면 에셋과 함께 콘텐츠 조각 선택을 원활하게 통합할 수 있습니다. 이를 통해 사용자는 동일한 통합 인터페이스 내에서 콘텐츠 조각을 검색 및 선택할 수 있으므로 에셋 및 구조화된 콘텐츠 전반에서 일관된 콘텐츠 선택 환경을 보장할 수 있습니다.

```
const assetSelectorProps = {
     featureSet: [
       'upload',            /* Include upload or other featureSet values to ensure no missing functionality */
       'content-fragments', /* Content Fragments pill will be shown */
     ],
     contentFragmentSelectorProps: {
       /* Configures the Content Fragments Pill experience */
       /* ...props @aem-sites/content-fragment-selector MFE supports */
    }
}

<AssetSelector {...assetSelectorProps} />
```

`contentFragmentSelectorProps`에서 [콘텐츠 조각 선택기 속성](/help/headless/content-fragment-selector/properties.md)에서 사용할 수 있는 모든 속성을 언급할 수 있습니다.

Content Advisor를 Angular, React 및 JavaScript 애플리케이션과 통합하는 방법에 대한 자세한 내용은 [Content Advisor 통합 예](https://github.com/adobe/aem-assets-selectors-mfe-examples/tree/consolidate-docs-to-experience-league/examples)를 참조하십시오.


