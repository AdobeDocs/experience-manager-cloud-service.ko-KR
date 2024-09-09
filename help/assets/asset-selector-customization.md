---
title: ' [!DNL Adobe Experience Manager] as a [!DNL Cloud Service]용 자산 선택기'
description: 함수를 사용하여 애플리케이션 내에서 에셋 선택기를 사용자 지정합니다.
role: Admin, User
exl-id: 0fd0a9f7-8c7a-4c21-9578-7c49409df609
source-git-commit: 575980320c1dbd32f799bf9c2fddf3d6773c838a
workflow-type: tm+mt
source-wordcount: '1243'
ht-degree: 24%

---

# 자산 선택기 사용자 지정 {#asset-selector-customization}

에셋 선택기를 사용하면 환경 설정, 요구 사항 또는 기능 요구 사항에 따라 다양한 구성 요소를 사용자 지정할 수 있습니다. 다음 구성 요소를 사용자 지정할 수 있습니다. [Micro-Frontend 자산 선택기](#overview-asset-selector.md):

* [필터 패널 사용자 지정](#customize-filter-panel)
* [모달 보기에서 정보 사용자 지정](#customize-info-in-modal-view)
* [드래그 앤 드롭 모드 활성화 또는 비활성화](#enable-disable-drag-and-drop)
* [Assets 선택](#selection-of-assets)
* [만료된 에셋 사용자 지정](#customize-expired-assets)
* [상황별 호출 필터](#contextual-invocation-filter)

[!DNL Experience Manager Assets] 저장소에 액세스하기 위한 인증 세부 정보를 정의하려면 응용 프로그램 구현 내의 **index.html** 파일 또는 유사한 파일에서 필수 구성 요소를 정의해야 합니다. 완료되면 요구 사항에 따라 코드 조각을 추가할 수 있습니다.

## 필터 패널 사용자 지정 {#customize-filter-panel}

`assetSelectorProps` 개체에 다음 코드 조각을 추가하여 필터 패널을 사용자 지정할 수 있습니다.

```
filterSchema: [
    {
    header: 'File Type',
    groupKey: 'TopGroup',
    fields: [
    {
    element: 'checkbox',
    name: 'type',
    options: [
    {
    label: 'Images',
    value: '<comma separated mimetypes, without space, that denote all images, for e.g., image/>',
    },
    {
    label: 'Videos',
    value: '<comma separated mimetypes, without space, that denote all videos for e.g., video/,model/vnd.mts,application/mxf>'
    }
    ]
    }
    ]
    },
    {
    fields: [
    {
    element: 'checkbox',
    name: 'type',
    options: [
    { label: 'JPG', value: 'image/jpeg' },
    { label: 'PNG', value: 'image/png' },
    { label: 'TIFF', value: 'image/tiff' },
    { label: 'GIF', value: 'image/gif' },
    { label: 'MP4', value: 'video/mp4' }
    ],
    columns: 3,
    },
    ],
    header: 'Mime Types',
    groupKey: 'MimeTypeGroup',
    },
    {
    fields: [
    {
    element: 'checkbox',
    name: 'property=metadata.application.xcm:keywords.value',
    options: [
    { label: 'Fruits', value: 'fruits' },
    { label: 'Vegetables', value: 'vegetables'}
    ],
    columns: 3,
    },
    ],
    header: 'Food Category',
    groupKey: 'FoodCategoryGroup',
    }
],
```

## 모달 보기에서 정보 사용자 지정 {#customize-info-in-modal-view}

![정보 아이콘](assets/info-icon.svg) 아이콘을 클릭하면 자산의 세부 정보 보기를 사용자 지정할 수 있습니다. 아래 코드를 실행합니다.

```
// Create an object infoPopoverMap and set the property `infoPopoverMap` with it in assetSelectorProps
const infoPopoverMap = (map) => {
// for example, to skip `path` from the info popover view
let defaultPopoverData = PureJSSelectors.getDefaultInfoPopoverData(map);
return defaultPopoverData.filter((i) => i.label !== 'Path')
};
assetSelectorProps.infoPopoverMap = infoPopoverMap;
```

## 드래그 앤 드롭 모드 활성화 또는 비활성화 {#enable-disable-drag-and-drop}

끌어서 놓기 모드를 사용하려면 `assetSelectorProp`에 다음 속성을 추가하십시오. 끌어서 놓기를 비활성화하려면 `true` 매개 변수를 `false`(으)로 바꾸십시오.

```
rail: true,
acvConfig: {
dragOptions: {
allowList: {
'*': true,
},
},
selectionType: 'multiple'
}

// the drop handler to be implemented
function drop(e) {
e.preventDefault();
// following helps you get the selected assets – an array of objects.
const data = JSON.parse(e.dataTransfer.getData('collectionviewdata'));
}
```

## Assets 선택 {#selection-of-assets}

선택된 자산 유형은 `handleSelection`, `handleAssetSelection` 및 `onDrop` 기능을 사용할 때 자산 정보를 포함하는 오브젝트의 배열입니다.

다음 단계를 실행하여 단일 또는 다중 에셋 선택을 구성합니다.

```
acvConfig: {
selectionType: 'multiple' // 'single' for single selection
}
// the `handleSelection` callback, always gets you the array of selected assets
```

**스키마 구문**

```
interface SelectedAsset {
    'repo:id': string;
    'repo:name': string;
    'repo:path': string;
    'repo:size': number;
    'repo:createdBy': string;
    'repo:createDate': string;
    'repo:modifiedBy': string; 
    'repo:modifyDate': string; 
    'dc:format': string; 
    'tiff:imageWidth': number;
    'tiff:imageLength': number;
    'repo:state': string;
    computedMetadata: Record<string, any>;
    _links: {
        'https://ns.adobe.com/adobecloud/rel/rendition': Array<{
            href: string;
            type: string;
            'repo:size': number;
            width: number;
            height: number;
            [others: string]: any;
        }>;
    };
}
```

다음 표에서는 선택한 자산 오브젝트의 몇 가지 중요한 속성에 대해 설명합니다.

| 속성 | 유형 | 설명 |
|---|---|---|
| *repo:repositoryId* | 문자열 | 자산이 저장된 저장소의 고유 식별자입니다. |
| *repo:id* | 문자열 | 자산의 고유 식별자입니다. |
| *repo:assetClass* | 문자열 | 자산의 분류입니다(예: 이미지 또는 비디오, 문서). |
| *repo:name* | 문자열 | 파일 확장명을 포함한 자산의 이름입니다. |
| *repo:size* | 숫자 | 자산의 크기입니다(바이트). |
| *repo:path* | 문자열 | 저장소 내 자산의 위치입니다. |
| *repo:ancestors* | `Array<string>` | 저장소에 있는 자산의 상위 항목 배열입니다. |
| *repo:state* | 문자열 | 저장소에 있는 에셋의 현재 상태(예: 활성, 삭제됨 등)입니다. |
| *repo:createdBy* | 문자열 | 자산을 생성한 사용자 또는 시스템입니다. |
| *repo:createDate* | 문자열 | 자산이 생성된 날짜 및 시간입니다. |
| *repo:modifiedBy* | 문자열 | 마지막으로 자산을 수정한 사용자 또는 시스템입니다. |
| *repo:modifyDate* | 문자열 | 자산이 마지막으로 수정된 날짜 및 시간입니다. |
| *dc:format* | 문자열 | 파일 유형(예: JPEG, PNG 등)과 같은 에셋의 형식입니다. |
| *tiff:imageWidth* | 숫자 | 자산의 폭입니다. |
| *tiff:imageLength* | 숫자 | 자산의 높이입니다. |
| *computedMetadata* | `Record<string, any>` | 모든 종류의 모든 자산 메타데이터(저장소, 애플리케이션 또는 임베드된 메타데이터)에 대한 버킷을 나타내는 오브젝트입니다. |
| *_links* | `Record<string, any>` | 관련 자산에 대한 하이퍼미디어 링크입니다. 메타데이터 및 렌디션과 같은 리소스에 대한 링크가 포함됩니다. |
| *`_links.<https://ns.adobe.com/adobecloud/rel/rendition>`* | `Array<Object>` | 자산의 렌디션에 대한 정보가 포함된 오브젝트 배열입니다. |
| *`_links.<https://ns.adobe.com/adobecloud/rel/rendition[].href>`* | 문자열 | 렌디션에 대한 URI입니다. |
| *`_links.<https://ns.adobe.com/adobecloud/rel/rendition[].type>`* | 문자열 | 렌디션의 MIME 유형입니다. |
| *`_links.<https://ns.adobe.com/adobecloud/rel/rendition[].repo:size>`* | 숫자 | 렌디션의 크기입니다(바이트). |
| *`_links.<https://ns.adobe.com/adobecloud/rel/rendition[].width>`* | 숫자 | 렌디션의 폭입니다. |
| *`_links.<https://ns.adobe.com/adobecloud/rel/rendition[].height>`* | 숫자 | 렌디션의 높이입니다. |

### 오브젝트 스키마를 사용한 자산 선택 처리 {#handling-selection}

`handleSelection` 속성은 자산 선택기에서 단일 또는 다중 자산 선택을 처리하는 데 사용됩니다. 아래 예는 `handleSelection`의 사용 구문을 나타냅니다.

![선택-처리](assets/handling-selection.png)

### Assets 선택 비활성화 {#disable-selection}

선택 해제 는 에셋 또는 폴더를 선택 가능하도록 숨기거나 비활성화하는 데 사용됩니다. 이 확인란을 선택하면 선택되지 않는 카드나 자산에 선택 확인란이 숨겨집니다. 이 기능을 사용하려면 배열에서 비활성화할 에셋 또는 폴더의 위치를 선언할 수 있습니다. 예를 들어 첫 번째 위치에 나타나는 폴더 선택을 비활성화하려면 다음 코드를 추가할 수 있습니다.
`disableSelection: [0]:folder`

이미지, 폴더, 파일 등의 MIME 형식이나 image/jpeg 등의 기타 MIME 형식 목록이 배열에 제공됩니다. 선언한 MIME 형식은 자산의 `data-card-type` 및 `data-card-mimetype` 특성에 매핑됩니다.

또한 선택 사항이 비활성화된 Assets은 드래그할 수 있습니다. 특정 에셋 유형의 끌어서 놓기를 비활성화하려면 `dragOptions.allowList` 속성을 사용합니다.

선택 사항 비활성화 구문은 다음과 같습니다.

```
(args)=> {
    return(
        <ASDialogWrapper
            {...args}
            disableSelection={args.disableSelection}
            handleAssetSelection={action('handleAssetSelection')}
            handleSelection={action('handleSelection')}
            selectionType={args.selectionType}
        />
    );
}
```

>[!NOTE]
>
> 에셋의 경우 선택 확인란이 숨겨지지만 폴더의 경우 폴더를 선택할 수 없지만 언급된 폴더의 탐색이 여전히 나타납니다.

<!--For a complete list of properties and detailed example, visit [Asset Selector Code Example](https://github.com/adobe/aem-assets-selectors-mfe-examples).-->

## 만료된 에셋 사용자 지정 {#customize-expired-assets}

에셋 선택기를 사용하여 만료된 에셋의 사용을 제어할 수 있습니다. 현재 날짜로부터 30일 이내에 만료되는 에셋에 대해 미리 알 수 있도록 **곧 만료** 배지로 만료된 에셋을 사용자 지정할 수 있습니다. 또한 이는 요구 사항에 따라 사용자 정의할 수 있습니다. 캔버스에서 만료된 에셋을 선택하거나 그 반대로 할 수도 있습니다. 만료된 에셋의 사용자 지정은 다양한 방법으로 일부 코드 조각을 사용하여 수행할 수 있습니다.

<!--{
    getExpiryStatus: function, // to control Expired/Expiring soon badges of the asset
    allowSelectionAndDrag: boolean, // set true to allow the selection of expired assets on canvas, set false, otherwise.
}-->

```
expiryOptions: {
    getExpiryStatus: getExpiryStatus;
}
```

### 만료된 에셋 선택 {#selection-of-expired-asset}

만료된 에셋의 사용을 선택 또는 선택 취소하도록 사용자 정의할 수 있습니다. 에셋 선택기 캔버스에서 만료된 에셋을 드래그하여 놓을 것인지 여부를 사용자 정의할 수 있습니다. 이렇게 하려면 다음 매개 변수를 사용하여 캔버스에서 에셋을 선택할 수 없도록 합니다.

```
expiryOptions:{
    allowSelectionAndDrop: false;
}
```
<!--
Additionally, To do this, navigate to **[!UICONTROL Disable default expiry behavior]** under the [!UICONTROL Controls] tab and set the boolean value to `true` or `false` as per the requirement. If `true` is selected, you can see the select box over the expired asset, otherwise it remains unselected. You can hover to the info icon of an asset to know the details of an expired asset. 

![Disable default expiry behavior](assets/disable-default-expiry-behavior.png)-->

### 만료된 에셋의 기간 설정 중 {#set-duration-of-expired-asset}

다음 코드 스니펫은 다음 5일 이내에 만료되는 자산에 대해 **곧 만료** 배지를 설정하는 데 도움이 됩니다. <!--The `expirationDate` property is used to set the expiration duration of an asset. Refer to the code snippet below:-->

```
/**
  const getExpiryStatus = async (asset) => {
  if (!asset.expirationDate) {
    return null;
  }
  const currentDate = new Date();
  const millisecondsInDay = 1000 * 60 * 60 * 24;
  const fiveDaysFromNow = new Date(value: currentDate.getTime() + 5 * millisecondsInDay);
  const expirationDate = new Date(asset.expirationDate);
  if (expirationDate.getTime() < currentDate.getTime()) {
    return 'EXPIRED';
  } else if (expirationDate.getTime() < fiveDaysFromNow.getTime()) {
    return 'EXPIRING_SOON';
  } else {
    return 'NOT_EXPIRED';
  }
};
```

<!--In the above code snippet, the `getExpiryStatus` function is used to show the **Expiring soon** badge that have expiration date stored in `customExpirationDate`. Additionally, it sets the expiration date of an asset to five days from the current date. The `millisecondsInDay` helps you set expiry of an asset by specifying the time range in milliseconds. You can replace milliseconds with hours directly or customize function as per the requirement. Whereas, the `getTime()` function returns the number of milliseconds for the mentioned date. See [properties](#asset-selector-properties) to know about `expirationDate` property.-->

속성이 현재 날짜 및 시간을 가져오는 데 작동하는 방식을 이해하려면 다음 예를 참조하십시오.

```
const currentData = new Date();
currentData.getTime(),
```

날짜 형식 2024-06-19T06:36:53.959Z에 따른 `1718779013959`을(를) 반환합니다.

### 만료된 에셋의 Toast 메시지 사용자 지정 {#customize-toast-message}

`showToast` 속성은 만료된 에셋에 표시할 Toast 메시지를 사용자 지정하는 데 사용됩니다.

구문:

```
{
    type: 'ERROR', 'NEUTRAL', 'INFO', 'SUCCESS',
    message: '<message to be shown>',
    timeout: optional,
}
```

기본 시간 제한은 500밀리초입니다. 반면 요구 사항에 따라 수정할 수 있습니다. 또한 값 `timeout: 0`을(를) 전달하면 교차 단추를 클릭할 때까지 toast가 열려 있습니다.

다음은 폴더 선택을 허용하지 않고 해당 메시지를 표시하는 데 필요한 경우 알림 메시지를 표시하는 예제입니다.

```
const showToast = {
    type: 'ERROR',
    message: 'Folder cannot be selected',
    timeout: 5000,
}
```

만료된 에셋 사용에 대한 toast 메시지를 표시하려면 다음 코드 조각을 사용하십시오.

```
(args) => {
    const [selectedAssets, setSelectedAssets] = useState([]);
    const [showToast, setShowToast] = React.useState(false);
    const handleAssetSelection = (assets) => {
        let directorySelectedFlag = false;
        const temp = assets.filter((asset) => {
            if (asset['repo:assetClass'] === 'directory') {
                directorySelectedFlag = true;
                setShowToast(true);
            }
            return !(asset['repo:assetClass'] === 'directory');
        });
        if (!directorySelectedFlag) {
            setShowToast(false);
        }
        setSelectedAssets(temp);
    };
    return (
        <ASDialogWrapper
            {...args}
            showToast={showToast ? args.showToast : null}
            selectedAssets={selectedAssets}
            handleAssetSelection={handleAssetSelection}
        />
    );
}
```

## 상황별 호출 필터{#contextual-invocation-filter}

자산 선택기를 사용하여 태그 선택기 필터를 추가할 수 있습니다. 모든 관련 태그를 특정 태그 그룹에 결합하는 태그 그룹을 지원합니다. 또한 찾고 있는 자산에 해당하는 추가 태그를 선택할 수 있습니다. 또한 사용자가 주로 사용하는 상황별 호출 필터 아래에 기본 태그 그룹을 설정하여 이동 중에 액세스할 수도 있습니다.

>
>
> * 검색에서 태그 지정 필터를 활성화하려면 상황별 호출 코드 조각을 추가해야 합니다.
> * 태그 그룹 형식 `(property=xcm:keywords.id=)`에 해당하는 이름 속성을 사용해야 합니다.

구문:

```
const filterSchema=useMemo(() => {
    return: [
        {
            element: 'taggroup',
            name: 'property=xcm:keywords.id='
        },
    ];
}, []);
```

필터 패널에서 태그 그룹을 추가하려면 기본적으로 하나 이상의 태그 그룹을 추가해야 합니다. 또한 아래 코드 조각을 사용하여 태그 그룹에서 미리 선택된 기본 태그를 추가하십시오.

```
export const WithAssetTags = (props) = {
const [selectedTags, setSelectedTags] = useState (
new Set(['orientation', 'color', 'facebook', 'experience-fragments:', 'dam', 'monochrome'])
const handleSelectTags = (selected) => {
setSelectedTags (new Set (selected)) ;
};
const filterSchema = useMemo ((); => {
    return {
        schema: [
            ｛
                fields: [
                    {
                    element: 'checkbox', 
                    name: 'property=xcm:keywords=', 
                    defaultValue: Array. from(selectedTags), 
                    options: assetTags, 
                    orientation: 'vertical',
                    },
                ],
    header: 'Asset Tags', 
    groupkey: 'AssetTagsGroup',
        ],
    },
｝；
}, [selectedTags]);
```

![태그 그룹 필터](assets/tag-group.gif)

## 자산 선택기에서 업로드 {#upload-in-asset-selector}

로컬 파일 시스템에서 파일 또는 폴더를 에셋 선택기에 업로드할 수 있습니다. 로컬 파일 시스템을 사용하여 파일을 업로드하려면 일반적으로 자산 선택기 마이크로 프론트엔드 애플리케이션에서 제공하는 업로드 기능을 사용해야 합니다. 자산 선택기에서 업로드를 호출하는 데 필요한 다양한 코드 조각은 다음과 같습니다.

* [기본 업로드 양식 코드 조각](#basic-upload)
* [메타데이터로 업로드](#upload-with-metadata)
* [사용자 지정된 업로드](#customized-upload)
* [타사 소스를 사용하여 업로드](#upload-using-third-party-source)

### 기본 업로드 양식 {#basic-upload}

```
import { AllInOneUpload } from '@assets/upload';
import { TextField, ContextualHelp } from '@adobe/react-spectrum';

const repoId = 'author-p52554-e145207-cmstg.adobeaemcloud.com'
const apiToken = 'eyJhbG....';
const targetUploadPath = '/content/dam/hydrated-assets/cq/as/cq-assets-upload-storybook-testing';

export const UploadExample = () => {
    return (
        <>
            <TextField
                marginStart="size-200"
                width="size-6000"
                isDisabled={true}
                label="Target Upload Path"
                value={targetUploadPath}
                contextualHelp={
                    <ContextualHelp>
                        <Content>Use Storybook Controls panel to change the default upload location</Content>
                    </ContextualHelp>
                }
            />
            <AllInOneUpload
                repositoryId={repoId}
                apiToken={apiToken}
                targetUploadPath={targetUploadPath}
            />
        <>
    )
}
```

### 메타데이터로 업로드 {#upload-with-metadata}

```
import { AllInOneUpload } from '@assets/upload';

const repoId = 'author-p52554-e145207-cmstg.adobeaemcloud.com'
const apiToken = 'eyJhbG....';
const targetUploadPath = '/content/dam/hydrated-assets/cq/as/cq-assets-upload-storybook-testing';

/**
 * see https://git.corp.adobe.com/CQ/assets-upload/blob/main/packages/@assets/upload/stories/data/SampleMetadataSchemas.ts
 * for full schema shape used in rendered example below
 */
const metadataSchema = [
    {
        mapToProperty: 'gmo:lineofBusiness',
        label: 'Line of Business',
        placeholder: 'Select one',
        required: true,
        element: 'dropdown',
        dropdownOptions: [
            {
                id: 'corporate',
                name: 'Corporate',
            },
            {
                id: 'digital-media-dme',
                name: 'Digital Media (DMe)',
            },
            {
                id: 'digital-experience-dx',
                name: 'Digital Experience (DX)',
            },
            {
                id: 'business-solutions',
                name: 'Business Solutions',
            },
        ],
    },
    // ... see link above for full schema
    {
        mapToProperty: 'dam:assetStatus',
        value: 'approved',
        // hidden metadata element, this metadata will be applied to the asset without rendering UI for user input
        element: 'hidden',
    },
];

const handleMetadataFormChange = (event: MetadataChangeEvent) => {
    const { property, value } = event;

    console.log({ property, value });
}

const UploadExampleWithMetadataForm = () => {
    return (
        <AllInOneUpload
            repositoryId={repoId}
            apiToken={apiToken}
            targetUploadPath={targetUploadPath}
            metadataSchema={sampleMetadataSchema}
            onMetadataFormChange={handleMetadataFormChange}
        />
    )
}
```

### 사용자 지정된 업로드 {#customized-upload}

```
const MultipleAllInOneUploadExample = () => {
    const mfeRef = React.useRef<{ iframeRef: { current: HTMLIFrameElement } }>(null);

    return (
        <>
            <Button
                onPress={() => UploadCoordinator.initiateUpload(mfeRef.current?.iframeRef?.current)}
            >
                External Initiate Upload
            </Button>
            <AllInOneUpload
                {...otherProps}
                ref={mfeRef}
            />
        <>
    );
}
```

### 타사 소스를 사용하여 업로드 {#upload-using-third-party-source}

```
import { useState, useRef } from 'react';
import { AllInOneUpload, UploadCoordinator } from '@assets/upload';
import { Button, Flex, Divider } from '@adobe/react-spectrum';
import { sampleMetadataSchema } from './SampleMetadataSchemas';

const repoId = 'author-p52554-e145207-cmstg.adobeaemcloud.com'
const apiToken = 'eyJhbG....';
const targetUploadPath = '/content/dam/hydrated-assets/cq/as/cq-assets-upload-storybook-testing';

const defaultFiles = [
    new File(['file-content'], 'Controlled File 1'),
    new File(['file-content-with-more'], 'Controlled File 2')
];

const ControlledUploadExample = () => {
    const [controlledFiles, setControlledFiles] = useState<File[]>(defaultFiles)
    const inputRef = React.useRef<HTMLInputElement>(null);

    const handleFileInputChange = useCallback((e: ChangeEvent<HTMLInputElement>) => {
        if (e.target.files) {
            setMyFiles([...e.target.files]);
        }
    }, []);

    return (
        <Flex height="100%" alignItems="center" direction="column">
            <Flex direction="row" alignItems="center" justifyContent="center">
                <Button
                    variant="accent"
                    onPress={() => UploadCoordinator.initiateUpload()}
                    isDisabled={files.length < 1}
                >
                    External Initiate Upload
                </Button>
                <Button
                    variant="secondary"
                    onPress={() => {
                        inputRef.current?.click();
                    }}
                >
                    External Browse files
                </Button>
            </Flex>
            <Divider size="M" marginTop="size-200" />
            <AllInOneUpload
                repositoryId={repoId}
                apiToken={apiToken}
                targetUploadPath={targetUploadPath}
                files={controlledFiles}
                onFilesChange={setControlledFiles}
                hideUploadButton={true}
                metadataSchema={sampleMetadataSchema}
            />
            <input
                ref={inputRef}
                type="file"
                style={{ display: 'none' }}
                onChange={handleFileInputChange}
                multiple={true}
            />
        </Flex>
    )
}
```

>[!MORELIKETHIS]
>
>* [자산 선택기 속성](/help/assets/asset-selector-properties.md)
>* [다양한 응용 프로그램과 자산 선택기 통합](/help/assets/integrate-asset-selector.md)
>* [자산 선택기 속성](/help/assets/asset-selector-properties.md)
>* [OpenAPI 기능을 사용하여 Dynamic Media과 자산 선택기 통합](/help/assets/integrate-asset-selector-dynamic-media-open-api.md)
