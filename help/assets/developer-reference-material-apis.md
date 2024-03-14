---
title: 개발자 참조 [!DNL Assets]
description: "[!DNL Assets] API 및 개발자 참조 콘텐츠를 사용하여 이진 파일, 메타데이터, 렌디션, 주석 및 [!DNL Content Fragments]."
contentOwner: AG
feature: APIs,Assets HTTP API
role: Developer,Architect,Admin
exl-id: c75ff177-b74e-436b-9e29-86e257be87fb
source-git-commit: bae9a5178c025b3bafa8ac2da75a1203206c16e1
workflow-type: tm+mt
source-wordcount: '1931'
ht-degree: 7%

---

# [!DNL Adobe Experience Manager Assets] 개발자 사용 사례, API 및 참조 자료 {#assets-cloud-service-apis}

이 문서에는 개발자를 위한 권장 사항, 참조 자료 및 리소스가 포함되어 있습니다. [!DNL Assets] as a [!DNL Cloud Service]. 여기에는 새로운 에셋 업로드 모듈, API 참조 및 사후 처리 워크플로우에서 제공되는 지원에 대한 정보가 포함됩니다.

## [!DNL Experience Manager Assets] API 및 작업 {#use-cases-and-apis}

[!DNL Assets] as a [!DNL Cloud Service] 은 디지털 에셋과 프로그래밍 방식으로 상호 작용하는 여러 API를 제공합니다. 각 API는 아래 표에 언급된 대로 특정 사용 사례를 지원합니다. 다음 [!DNL Assets] 사용자 인터페이스, [!DNL Experience Manager] 데스크탑 앱 및 [!DNL Adobe Asset Link] 작업의 전체 또는 일부를 지원합니다.

>[!CAUTION]
>
>일부 API는 계속 존재하지만 적극적으로 지원되지 않습니다(문자로 ×). 가능한 한 이러한 API를 사용하지 마십시오.

| 지원 수준 | 설명 |
| ------------- | --------------------------- |
| ✓ | 지원됨 |
| × | 지원되지 않습니다. 사용하지 마십시오. |
| - | 사용할 수 없음 |

| 사용 사례 | [aem 업로드](https://github.com/adobe/aem-upload) | [Experience Manager / Sling / JCR](https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/index.html) Java API | [Asset compute 서비스](https://experienceleague.adobe.com/docs/asset-compute/using/extend/understand-extensibility.html) | [[!DNL Assets] HTTP API](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/assets/admin/mac-api-assets.html#create-an-asset) | 슬링 [GET](https://sling.apache.org/documentation/bundles/rendering-content-default-get-servlets.html) / [POST](https://sling.apache.org/documentation/bundles/manipulating-content-the-slingpostservlet-servlets-post.html) 서블릿 | [GraphQL](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/graphql/overview.html) |
| ----------------|:---:|:---:|:---:|:---:|:---:|:---:|
| **원본 이진** |  |  |  |  |  |  |
| 원본 만들기 | ✓ | × | - | × | × | - |
| 원본 읽기 | - | × | ✓ | ✓ | ✓ | - |
| 원본 업데이트 | ✓ | × | ✓ | × | × | - |
| 원본 삭제 | - | ✓ | - | ✓ | ✓ | - |
| 원본 복사 | - | ✓ | - | ✓ | ✓ | - |
| 원본 이동 | - | ✓ | - | ✓ | ✓ | - |
| **메타데이터** |  |  |  |  |  |  |
| 메타데이터 만들기 | - | ✓ | ✓ | ✓ | ✓ | - |
| 메타데이터 읽기 | - | ✓ | - | ✓ | ✓ | - |
| 메타데이터 업데이트 | - | ✓ | ✓ | ✓ | ✓ | - |
| 메타데이터 삭제 | - | ✓ | ✓ | ✓ | ✓ | - |
| 메타데이터 복사 | - | ✓ | - | ✓ | ✓ | - |
| 메타데이터 이동 | - | ✓ | - | ✓ | ✓ | - |
| **컨텐츠 조각(CF)** |  |  |  |  |  |  |
| CF 만들기 | - | ✓ | - | ✓ | - | - |
| CF 읽기 | - | ✓ | - | ✓ | - | ✓ |
| CF 업데이트 | - | ✓ | - | ✓ | - | - |
| CF 삭제 | - | ✓ | - | ✓ | - | - |
| CF 복사 | - | ✓ | - | ✓ | - | - |
| CF 이동 | - | ✓ | - | ✓ | - | - |
| **버전** |  |  |  |  |  |  |
| 버전 만들기 | ✓ | ✓ | - | - | - | - |
| 버전 읽기 | - | ✓ | - | - | - | - |
| 버전 삭제 | - | ✓ | - | - | - | - |
| **폴더** |  |  |  |  |  |  |
| 폴더 만들기 | ✓ | ✓ | - | ✓ | - | - |
| 폴더 읽기 | - | ✓ | - | ✓ | - | - |
| 폴더 삭제 | ✓ | ✓ | - | ✓ | - | - |
| 폴더 복사 | ✓ | ✓ | - | ✓ | - | - |
| 폴더 이동 | ✓ | ✓ | - | ✓ | - | - |

## 에셋 업로드 {#asset-upload}

위치 [!DNL Experience Manager] as a [!DNL Cloud Service], HTTP API를 사용하여 자산을 클라우드 스토리지에 직접 업로드할 수 있습니다. 바이너리 파일을 업로드하는 단계는 아래에 나와 있습니다. 다음 단계를 내부가 아닌 외부 애플리케이션에서 실행합니다. [!DNL Experience Manager] JVM

1. [HTTP 요청 제출](#initiate-upload). 다음과 같이 표시됩니다. [!DNL Experience Manage]r 새 바이너리를 업로드하려는 의도의 배포입니다.
1. [바이너리의 내용 PUT](#upload-binary) 시작 요청에서 제공한 하나 이상의 URI에
1. [HTTP 요청 제출](#complete-upload) 바이너리의 콘텐츠가 성공적으로 업로드되었음을 서버에 알립니다.

![다이렉트 이진 업로드 프로토콜 개요](assets/add-assets-technical.png)

>[!IMPORTANT]
>
>위의 단계를 내부가 아닌 외부 애플리케이션에서 실행합니다. [!DNL Experience Manager] JVM

이 접근 방식은 자산 업로드의 확장 가능하고 더 성능 있는 처리를 제공합니다. 과 비교한 차이점 [!DNL Experience Manager] 6.5는 다음과 같습니다.

* 바이너리가 통과되지 않음 [!DNL Experience Manager]: 이제 배포용으로 구성된 바이너리 클라우드 스토리지로 업로드 프로세스를 간단히 조정합니다.
* 이진 클라우드 스토리지는 CDN(Content Delivery Network) 또는 Edge 네트워크와 함께 작동합니다. CDN은 클라이언트에 더 가까운 업로드 끝점을 선택합니다. 데이터가 가까운 엔드포인트로 더 짧은 거리를 이동할 때 특히 지리적으로 분산된 팀의 경우 업로드 성능과 사용자 경험이 개선됩니다.

>[!NOTE]
>
>오픈 소스에서 이 접근 방식을 구현하려면 클라이언트 코드 를 참조하십시오 [aem 업로드 라이브러리](https://github.com/adobe/aem-upload).
>
>[!IMPORTANT]
>
>경우에 따라 변경 사항이 Experience ManagerCloud Service 에 있는 스토리지의 일관적인 특성으로 인해 요청 간에 완전히 전파되지 않을 수 있습니다. 필수 폴더 생성이 전파되지 않아 업로드 호출을 시작하거나 완료하는 응답이 404개로 늘어납니다. 클라이언트는 404 개의 응답을 예상해야 하며, 백오프 전략을 사용하여 재시도를 구현하여 응답들을 처리해야 합니다.

### 업로드 시작 {#initiate-upload}

원하는 폴더에 HTTP POST 요청을 제출합니다. 이 폴더에서 에셋을 만들거나 업데이트합니다. 선택기 포함 `.initiateUpload.json` 요청이 이진 파일의 업로드를 시작함을 나타냅니다. 예를 들어 자산을 만들어야 하는 폴더의 경로는 입니다. `/assets/folder`. POST 요청은 다음과 같습니다. `POST https://[aem_server]:[port]/content/dam/assets/folder.initiateUpload.json`.

요청 본문의 콘텐츠 유형은 다음과 같아야 합니다. `application/x-www-form-urlencoded` 다음 필드가 포함된 양식 데이터:

* `(string) fileName`: 필수. 표시되는 에셋의 이름 [!DNL Experience Manager].
* `(number) fileSize`: 필수. 업로드할 자산의 파일 크기(바이트)입니다.

각 바이너리에 필수 필드가 포함되어 있는 한 단일 요청을 사용하여 여러 바이너리에 대한 업로드를 시작할 수 있습니다. 성공하면 요청이 다음으로 응답함 `201` 상태 코드 및 다음 형식의 JSON 데이터가 포함된 본문:

```json
{
    "completeURI": "(string)",
    "folderPath": "(string)",
    "files": [
        {
            "fileName": "(string)",
            "mimeType": "(string)",
            "uploadToken": "(string)",
            "uploadURIs": [
                "(string)"
            ],
            "minPartSize": (number),
            "maxPartSize": (number)
        }
    ]
}
```

* `completeURI` (문자열): 바이너리의 업로드가 완료되면 이 URI를 호출합니다. URI는 절대 또는 상대 URI일 수 있으며 클라이언트는 어느 것이든 처리할 수 있어야 합니다. 즉, 값은 다음과 같을 수 있습니다 `"https://[aem_server]:[port]/content/dam.completeUpload.json"` 또는 `"/content/dam.completeUpload.json"` 다음을 참조하십시오 [업로드 완료](#complete-upload).
* `folderPath` (문자열): 바이너리가 업로드되는 폴더의 전체 경로입니다.
* `(files)` (배열): 길이 및 순서가 initiate 요청에 제공된 이진 정보 목록의 길이 및 순서와 일치하는 요소의 목록입니다.
* `fileName` (문자열): 시작 요청에 제공된 해당 바이너리의 이름입니다. 이 값은 전체 요청에 포함해야 합니다.
* `mimeType` (문자열): 시작 요청에 제공된 해당 바이너리의 MIME 유형입니다. 이 값은 전체 요청에 포함해야 합니다.
* `uploadToken` (문자열): 해당 바이너리에 대한 업로드 토큰입니다. 이 값은 전체 요청에 포함해야 합니다.
* `uploadURIs` (배열): 값이 이진 콘텐츠를 업로드해야 하는 전체 URI인 문자열 목록입니다(참조) [바이너리 업로드](#upload-binary)).
* `minPartSize` (숫자): 다음 중 하나에 제공할 수 있는 데이터의 최소 길이(바이트) `uploadURIs`: URI가 두 개 이상인 경우.
* `maxPartSize` (숫자): 다음 중 하나에 제공할 수 있는 데이터의 최대 길이(바이트) `uploadURIs`: URI가 두 개 이상인 경우.

### 바이너리 업로드 {#upload-binary}

업로드를 시작하는 출력은 하나 이상의 업로드 URI 값을 포함한다. 하나 이상의 URI가 제공되는 경우, 클라이언트는 바이너리를 분할하여 제공된 PUT URI에 대해 순서대로 각 파트의 업로드 요청을 할 수 있다. 바이너리를 부분으로 분할하려면 다음 지침을 따르십시오.

* 마지막 부분을 제외한 각 부분의 크기는 다음 이상이어야 합니다. `minPartSize`.
* 각 부품의 크기는 다음과 같거나 작아야 합니다. `maxPartSize`.
* 바이너리의 크기가 을 초과하는 경우 `maxPartSize`를 클릭하고 바이너리를 분할하여 업로드합니다.
* 모든 URI를 사용해야 하는 것은 아닙니다.

바이너리의 크기가 보다 작거나 같은 경우 `maxPartSize`대신 전체 바이너리를 단일 업로드 URI에 업로드할 수 있습니다. 두 개 이상의 업로드 URI가 제공된 경우 첫 번째 URI를 사용하고 나머지는 무시합니다. 모든 URI를 사용해야 하는 것은 아닙니다.

CDN 에지 노드는 요청된 바이너리 업로드를 가속화하는 데 도움이 됩니다.

이를 수행하는 가장 쉬운 방법은 값을 사용하는 것입니다. `maxPartSize` 를 부품 크기로 지정합니다. API 계약은 사용자가 이 값을 부품 크기로 사용할 경우 바이너리를 업로드하기에 충분한 업로드 URI가 있음을 보장합니다. 이렇게 하려면 이진을 크기의 일부로 분할합니다 `maxPartSize`각 부품에 대해 순서대로 하나의 URI를 사용합니다. 최종 부품은 보다 작거나 같은 모든 크기일 수 있습니다. `maxPartSize`. 예를 들어 바이너리의 총 크기가 20,000바이트라고 가정할 때 `minPartSize` 은(는) 5,000바이트이며, `maxPartSize` 는 8,000바이트이고 업로드 URI의 수는 5입니다. 다음 단계를 실행합니다.

* 첫 번째 업로드 URI를 사용하여 바이너리의 처음 8,000바이트를 업로드합니다.
* 두 번째 업로드 URI를 사용하여 바이너리의 두 번째 8,000바이트를 업로드합니다.
* 세 번째 업로드 URI를 사용하여 바이너리의 마지막 4,000바이트를 업로드합니다. 마지막 부분이므로 다음보다 클 필요는 없습니다. `minPartSize`.
* 마지막 두 개의 업로드 URI를 사용할 필요는 없습니다. 무시해도 됩니다.

일반적인 오류는 API에서 제공하는 업로드 URI의 수를 기반으로 부품 크기를 계산하는 것입니다. API 계약은 이 접근 방식이 작동한다고 보장하지 않으며, 실제로 다음 사이의 범위를 벗어나는 부품 크기를 초래할 수 있습니다. `minPartSize` 및 `maxPartSize`. 이로 인해 이진 업로드가 실패할 수 있습니다.

다시 말하지만, 가장 쉽고 안전한 방법은 다음과 같은 크기의 부품을 사용하는 것입니다. `maxPartSize`.

업로드가 성공하면 서버는 각 요청에 `201` 상태 코드입니다.

>[!NOTE]
>
>업로드 알고리즘에 대한 자세한 내용은 [공식 기능 설명서](https://jackrabbit.apache.org/oak/docs/features/direct-binary-access.html#Upload) 및 [API 설명서](https://jackrabbit.apache.org/oak/docs/apidocs/org/apache/jackrabbit/api/binary/BinaryUpload.html) Apache Jackrabbit Oak 프로젝트에서.

### 업로드 완료 {#complete-upload}

이진 파일의 모든 부분이 업로드된 후 HTTP POST 요청을 시작 데이터가 제공하는 전체 URI에 제출합니다. 요청 본문의 콘텐츠 유형은 다음과 같아야 합니다. `application/x-www-form-urlencoded` 다음 필드가 포함된 양식 데이터.

| 필드 | 유형 | 필수 여부 | 설명 |
|---|---|---|---|
| `fileName` | 문자열 | 필수 | 시작 데이터에서 제공된 에셋의 이름입니다. |
| `mimeType` | 문자열 | 필수 | 시작 데이터에서 제공한 바이너리의 HTTP 콘텐츠 유형입니다. |
| `uploadToken` | 문자열 | 필수 | 시작 데이터에서 제공한 대로 바이너리에 대한 업로드 토큰입니다. |
| `createVersion` | 부울 | 옵션 | If `True` 지정된 이름의 자산이 있으면 [!DNL Experience Manager] 는 에셋의 새 버전을 만듭니다. |
| `versionLabel` | 문자열 | 옵션 | 새 버전이 만들어지면 에셋의 새 버전과 관련된 레이블입니다. |
| `versionComment` | 문자열 | 옵션 | 새 버전을 만드는 경우 버전과 관련된 주석입니다. |
| `replace` | 부울 | 옵션 | If `True` 지정된 이름의 자산이 있습니다. [!DNL Experience Manager] 에셋을 삭제한 다음 다시 만듭니다. |
| `uploadDuration` | 숫자 | 옵션 | 파일이 전부 업로드되는 총 시간(밀리초)입니다. 이 옵션을 지정하면 업로드 기간이 전송 속도 분석을 위해 시스템의 로그 파일에 포함됩니다. |
| `fileSize` | 숫자 | 옵션 | 파일의 크기(바이트)입니다. 지정하면 파일 크기가 전송 속도 분석을 위해 시스템의 로그 파일에 포함됩니다. |

>[!NOTE]
>
>에셋이 존재하고 모두 존재하지 않는 경우 `createVersion` nor `replace` 을 지정한 다음 [!DNL Experience Manager] 는 에셋의 현재 버전을 새 바이너리로 업데이트합니다.

시작 프로세스와 마찬가지로 전체 요청 데이터에는 두 개 이상의 파일에 대한 정보가 포함될 수 있습니다.

파일에 대해 전체 URL이 호출될 때까지 바이너리를 업로드하는 프로세스는 수행되지 않습니다. 업로드 프로세스가 완료된 후 자산이 처리됩니다. 에셋의 이진 파일이 완전히 업로드되더라도 업로드 프로세스가 완료되지 않아 처리가 시작되지 않습니다. 업로드가 성공하면 서버는 `200` 상태 코드입니다.

### 자산을 AEM에 as a Cloud Service으로 업로드하는 예제 셸 스크립트 {#upload-assets-shell-script}

다음 예제 셸 스크립트에서는 AEM as a Cloud Service 내에서 직접 이진 액세스를 위한 다단계 업로드 프로세스를 보여 줍니다 `aem-upload.sh`:

```bash
#!/bin/bash

# Check if pv is installed
if ! command -v pv &> /dev/null; then
    echo "Error: 'pv' command not found. Please install it before running the script."
    exit 1
fi

# Check if jq is installed
if ! command -v jq &> /dev/null; then
    echo "Error: 'jq' command not found. Please install it before running the script."
    exit 1
fi

# Set DEBUG to true to enable debug statements
DEBUG=true

# Function for printing debug statements
function debug() {
    if [ "${DEBUG}" = true ]; then
        echo "[DEBUG] $1"
    fi
}

# Function to check if a file exists
function file_exists() {
    [ -e "$1" ]
}

# Function to check if a path is a directory
function is_directory() {
    [ -d "$1" ]
}

# Check if the required number of parameters are provided
if [ "$#" -ne 4 ]; then
    echo "Usage: $0 <aem-url> <asset-folder> <file-to-upload> <bearer-token>"
    exit 1
fi

AEM_URL="$1"
ASSET_FOLDER="$2"
FILE_TO_UPLOAD="$3"
BEARER_TOKEN="$4"

# Extracting file name or folder name from the file path
NAME=$(basename "${FILE_TO_UPLOAD}")

# Step 1: Check if "file-to-upload" is a folder
if is_directory "${FILE_TO_UPLOAD}"; then
    echo "Uploading files from the folder recursively..."
    
    # Recursively upload files in the folder
    find "${FILE_TO_UPLOAD}" -type f | while read -r FILE_PATH; do
        FILE_NAME=$(basename "${FILE_PATH}")
        debug "Uploading file: ${FILE_PATH}"
        
        # You can choose to initiate upload for each file here
        # For simplicity, let's assume you use the same ASSET_FOLDER for all files
        ./aem-upload.sh "${AEM_URL}" "${ASSET_FOLDER}" "${FILE_PATH}" "${BEARER_TOKEN}"
    done
else
    # "file-to-upload" is a single file
    FILE_NAME="${NAME}"

    # Step 2: Calculate File Size
    FILE_SIZE=$(stat -c %s "${FILE_TO_UPLOAD}")

    # Step 3: Initiate Upload
    INITIATE_UPLOAD_ENDPOINT="${AEM_URL}/content/dam/${ASSET_FOLDER}.initiateUpload.json"

    debug "Initiating upload..."
    debug "Initiate Upload Endpoint: ${INITIATE_UPLOAD_ENDPOINT}"
    debug "File Name: ${FILE_NAME}"
    debug "File Size: ${FILE_SIZE}"

    INITIATE_UPLOAD_RESPONSE=$(curl -X POST \
        -H "Authorization: Bearer ${BEARER_TOKEN}" \
        -H "Content-Type: application/x-www-form-urlencoded; charset=UTF-8" \
        -d "fileName=${FILE_NAME}" \
        -d "fileSize=${FILE_SIZE}" \
        ${INITIATE_UPLOAD_ENDPOINT})

    # Continue with the rest of the script...
fi


# Check if the response body contains the specified HTML content for a 404 error
if echo "${INITIATE_UPLOAD_RESPONSE}" | grep -q "<title>404 Specified folder not found</title>"; then
    echo "Folder not found. Creating the folder..."

    # Attempt to create the folder
    CREATE_FOLDER_ENDPOINT="${AEM_URL}/api/assets/${ASSET_FOLDER}"

    debug "Creating folder..."
    debug "Create Folder Endpoint: ${CREATE_FOLDER_ENDPOINT}"

    CREATE_FOLDER_RESPONSE=$(curl -X POST \
        -H "Content-Type: application/json" \
        -H "Authorization: Bearer ${BEARER_TOKEN}" \
        -d '{"class":"'${ASSET_FOLDER}'","properties":{"title":"'${ASSET_FOLDER}'"}}' \
        ${CREATE_FOLDER_ENDPOINT})

    # Check the response code and inform the user accordingly
    STATUS_CODE_CREATE_FOLDER=$(echo "${CREATE_FOLDER_RESPONSE}" | jq -r '.properties."status.code"')
    case ${STATUS_CODE_CREATE_FOLDER} in
        201)
            echo "Folder created successfully. Initiating upload again..."

            # Retry Initiate Upload after creating the folder
            INITIATE_UPLOAD_RESPONSE=$(curl -X POST \
                -H "Authorization: Bearer ${BEARER_TOKEN}" \
                -H "Content-Type: application/x-www-form-urlencoded; charset=UTF-8" \
                -d "fileName=${FILE_NAME}" \
                -d "fileSize=${FILE_SIZE}" \
                ${INITIATE_UPLOAD_ENDPOINT})
            ;;
        409)
            echo "Error: Folder already exists."
            ;;
        412)
            echo "Error: Precondition failed. Root collection cannot be found or accessed."
            exit 1
            ;;
        500)
            echo "Error: Internal Server Error. Something went wrong."
            exit 1
            ;;
        *)
            echo "Error: Unexpected response code ${STATUS_CODE_CREATE_FOLDER}"
            exit 1
            ;;
    esac
fi

# Extracting values from the response
FOLDER_PATH=$(echo "${INITIATE_UPLOAD_RESPONSE}" | jq -r '.folderPath')
UPLOAD_URIS=($(echo "${INITIATE_UPLOAD_RESPONSE}" | jq -r '.files[0].uploadURIs[]'))
UPLOAD_TOKEN=$(echo "${INITIATE_UPLOAD_RESPONSE}" | jq -r '.files[0].uploadToken')
MIME_TYPE=$(echo "${INITIATE_UPLOAD_RESPONSE}" | jq -r '.files[0].mimeType')
MIN_PART_SIZE=$(echo "${INITIATE_UPLOAD_RESPONSE}" | jq -r '.files[0].minPartSize')
MAX_PART_SIZE=$(echo "${INITIATE_UPLOAD_RESPONSE}" | jq -r '.files[0].maxPartSize')
COMPLETE_URI=$(echo "${INITIATE_UPLOAD_RESPONSE}" | jq -r '.completeURI')

# Extracting "Affinity-cookie" from the response headers
AFFINITY_COOKIE=$(echo "${INITIATE_UPLOAD_RESPONSE}" | grep -i 'Affinity-cookie' | awk '{print $2}')

debug "Folder Path: ${FOLDER_PATH}"
debug "Upload Token: ${UPLOAD_TOKEN}"
debug "MIME Type: ${MIME_TYPE}"
debug "Min Part Size: ${MIN_PART_SIZE}"
debug "Max Part Size: ${MAX_PART_SIZE}"
debug "Complete URI: ${COMPLETE_URI}"
debug "Affinity Cookie: ${AFFINITY_COOKIE}"
if $DEBUG; then
    i=1
    for UPLOAD_URI in "${UPLOAD_URIS[@]}"; do
        debug "Upload URI $i: "$UPLOAD_URI
        i=$((i+1))
    done
fi


# Calculate the number of parts needed
NUM_PARTS=$(( (FILE_SIZE + MAX_PART_SIZE - 1) / MAX_PART_SIZE ))
debug "Number of Parts: $NUM_PARTS"

# Calculate the part size for the last chunk
LAST_PART_SIZE=$(( FILE_SIZE % MAX_PART_SIZE ))
if [ "${LAST_PART_SIZE}" -eq 0 ]; then
    LAST_PART_SIZE=${MAX_PART_SIZE}
fi

# Step 4: Upload binary to the blob store in parts
PART_NUMBER=1
for i in $(seq 1 $NUM_PARTS); do
    PART_SIZE=${MAX_PART_SIZE}
    if [ ${PART_NUMBER} -eq ${NUM_PARTS} ]; then
        PART_SIZE=${LAST_PART_SIZE}
        debug "Last part size: ${PART_SIZE}"
    fi

    PART_FILE="/tmp/${FILE_NAME}_part${PART_NUMBER}"

    # Creating part file 
    SKIP=$((PART_NUMBER - 1))
    SKIP=$((MAX_PART_SIZE * SKIP))
    dd if="${FILE_TO_UPLOAD}" of="${PART_FILE}"  bs="${PART_SIZE}" skip="${SKIP}" count="${PART_SIZE}" iflag=skip_bytes,count_bytes  > /dev/null 2>&1
    debug "Creating part file: ${PART_FILE} with size ${PART_SIZE}, skipping first ${SKIP} bytes."

    
    UPLOAD_URI=${UPLOAD_URIS[$PART_NUMBER-1]}

    debug "Uploading part ${PART_NUMBER}..."
    debug "Part Size: $PART_SIZE"
    debug "Part File: ${PART_FILE}"
    debug "Part File Size: $(stat -c %s "${PART_FILE}")"
    debug "Upload URI: ${UPLOAD_URI}"

    # Upload the part in the background
    if command -v pv &> /dev/null; then
        pv "${PART_FILE}" | curl --progress-bar -X PUT --data-binary "@-" "${UPLOAD_URI}" &
    else
        curl -# -X PUT --data-binary "@${PART_FILE}" "${UPLOAD_URI}" &
    fi

    PART_NUMBER=$((PART_NUMBER + 1))
done

# Wait for all background processes to finish
wait

# Step 5: Complete the upload in AEM
COMPLETE_UPLOAD_ENDPOINT="${AEM_URL}${COMPLETE_URI}"

debug "Completing the upload..."
debug "Complete Upload Endpoint: ${COMPLETE_UPLOAD_ENDPOINT}"

RESPONSE=$(curl -X POST \
    -H "Authorization: Bearer ${BEARER_TOKEN}" \
    -H "Content-Type: application/x-www-form-urlencoded; charset=UTF-8" \
    -H "Affinity-cookie: ${AFFINITY_COOKIE}" \
    --data-urlencode "uploadToken=${UPLOAD_TOKEN}" \
    --data-urlencode "fileName=${FILE_NAME}" \
    --data-urlencode "mimeType=${MIME_TYPE}" \
    "${COMPLETE_UPLOAD_ENDPOINT}")
    
debug $RESPONSE

echo "File upload completed successfully."
```

### 오픈 소스 업로드 라이브러리 {#open-source-upload-library}

업로드 알고리즘에 대해 자세히 알아보거나 자체 업로드 스크립트 및 도구를 빌드하기 위해 Adobe은 오픈 소스 라이브러리 및 도구를 제공합니다.

* [오픈 소스 AEM 업로드 라이브러리](https://github.com/adobe/aem-upload).
* [오픈 소스 명령줄 도구](https://github.com/adobe/aio-cli-plugin-aem).

>[!NOTE]
>
>aem 업로드 라이브러리와 명령줄 도구는 모두 [node-httptransfer 라이브러리](https://github.com/adobe/node-httptransfer/)

### 더 이상 사용되지 않는 에셋 업로드 API {#deprecated-asset-upload-api}

<!-- #ENGCHECK review / update the list of deprecated APIs below. -->

새 업로드 방법은 다음에만 지원됩니다. [!DNL Adobe Experience Manager] as a [!DNL Cloud Service]. 의 API [!DNL Adobe Experience Manager] 6.5는 더 이상 사용되지 않습니다. 에셋 또는 렌디션(바이너리 업로드) 업로드 또는 업데이트와 관련된 방법은 다음 API에서 더 이상 사용되지 않습니다.

* [EXPERIENCE MANAGER ASSETS HTTP API](mac-api-assets.md)
* `AssetManager` 과 같은 Java API `AssetManager.createAsset(..)`, `AssetManager.createAssetForBinary(..)`, `AssetManager.getAssetForBinary(..)`, `AssetManager.removeAssetForBinary(..)`, `AssetManager.createOrUpdateAsset(..)`, `AssetManager.createOrReplaceAsset(..)`

>[!MORELIKETHIS]
>
>* [오픈 소스 AEM 업로드 라이브러리](https://github.com/adobe/aem-upload).
>* [오픈 소스 명령줄 도구](https://github.com/adobe/aio-cli-plugin-aem).
>* [직접 업로드를 위한 Apache Jackrabbit Oak 설명서](https://jackrabbit.apache.org/oak/docs/features/direct-binary-access.html#Upload).

## 에셋 처리 및 사후 처리 워크플로 {#post-processing-workflows}

위치 [!DNL Experience Manager], 자산 처리는 다음을 기반으로 합니다. **[!UICONTROL 처리 프로필]** 를 사용하는 구성 [에셋 마이크로서비스](asset-microservices-configure-and-use.md#get-started-using-asset-microservices). 처리 시 개발자 확장이 필요하지 않습니다.

사후 처리 워크플로 구성의 경우, 사용자 지정 단계와 함께 확장이 있는 표준 워크플로를 사용하십시오.

## 사후 처리 워크플로우에서 워크플로우 단계 지원 {#post-processing-workflows-steps}

의 이전 버전에서 업그레이드하는 경우 [!DNL Experience Manager], 에셋 마이크로서비스 를 사용하여 에셋을 처리할 수 있습니다. 클라우드 기반 에셋 마이크로서비스 는 구성 및 사용이 더 간단합니다. 에 사용되는 몇 가지 워크플로우 단계 [!UICONTROL DAM 자산 업데이트] 이전 버전의 워크플로는 지원되지 않습니다. 지원되는 클래스에 대한 자세한 내용은 [Java API 참조 또는 JavaDoc](https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/index.html).

다음 기술 워크플로우 모델은 에셋 마이크로서비스로 대체되거나 지원을 사용할 수 없습니다.

* `com.day.cq.dam.cameraraw.process.CameraRawHandlingProcess`
* `com.day.cq.dam.core.process.CommandLineProcess`
* `com.day.cq.dam.pdfrasterizer.process.PdfRasterizerHandlingProcess`
* `com.day.cq.dam.core.process.AddPropertyWorkflowProcess`
* `com.day.cq.dam.core.process.CreateSubAssetsProcess`
* `com.day.cq.dam.core.process.DownloadAssetProcess`
* `com.day.cq.dam.word.process.ExtractImagesProcess`
* `com.day.cq.dam.word.process.ExtractPlainProcess`
* `com.day.cq.dam.ids.impl.process.IDSJobProcess`
* `com.day.cq.dam.indd.process.INDDMediaExtractProcess`
* `com.day.cq.dam.indd.process.INDDPageExtractProcess`
* `com.day.cq.dam.core.impl.lightbox.LightboxUpdateAssetProcess`
* `com.day.cq.dam.pim.impl.sourcing.upload.process.ProductAssetsUploadProcess`
* `com.day.cq.dam.core.process.SendDownloadAssetEmailProcess`
* `com.day.cq.dam.similaritysearch.internal.workflow.smarttags.StartTrainingProcess`
* `com.day.cq.dam.similaritysearch.internal.workflow.smarttags.TransferTrainingDataProcess`
* `com.day.cq.dam.switchengine.process.SwitchEngineHandlingProcess`
* `com.day.cq.dam.core.process.GateKeeperProcess`
* `com.day.cq.dam.s7dam.common.process.DMEncodeVideoWorkflowCompletedProcess`
* `com.day.cq.dam.core.process.DeleteImagePreviewProcess`
* `com.day.cq.dam.video.FFMpegTranscodeProcess`
* `com.day.cq.dam.core.process.ThumbnailProcess`
* `com.day.cq.dam.video.FFMpegThumbnailProcess`
* `com.day.cq.dam.core.process.CreateWebEnabledImageProcess`
* `com.day.cq.dam.core.process.CreatePdfPreviewProcess`
* `com.day.cq.dam.s7dam.common.process.VideoUserUploadedThumbnailProcess`
* `com.day.cq.dam.s7dam.common.process.VideoThumbnailDownloadProcess`
* `com.day.cq.dam.s7dam.common.process.VideoProxyServiceProcess`
* `com.day.cq.dam.scene7.impl.process.Scene7UploadProcess`
* `com.day.cq.dam.s7dam.common.process.S7VideoThumbnailProcess`
* `com.day.cq.dam.core.process.MetadataProcessorProcess`
* `com.day.cq.dam.core.process.AssetOffloadingProcess`
* `com.adobe.cq.dam.dm.process.workflow.DMImageProcess`

<!-- Commenting the previous list documented at the time of GA. Replacing it with the updated list via cqdoc-18231.

* `com.day.cq.dam.core.process.DeleteImagePreviewProcess`
* `com.day.cq.dam.s7dam.common.process.DMEncodeVideoWorkflowCompletedProcess`
* `com.day.cq.dam.core.process.GateKeeperProcess`
* `com.day.cq.dam.core.process.AssetOffloadingProcess`
* `com.day.cq.dam.core.process.MetadataProcessorProcess`
* `com.adobe.cq.dam.dm.process.workflow.DMImageProcess`
* `com.day.cq.dam.s7dam.common.process.S7VideoThumbnailProcess`
* `com.day.cq.dam.scene7.impl.process.Scene7UploadProcess`
* `com.day.cq.dam.s7dam.common.process.VideoProxyServiceProcess`
* `com.day.cq.dam.s7dam.common.process.VideoThumbnailDownloadProcess`
* `com.day.cq.dam.s7dam.common.process.VideoUserUploadedThumbnailProcess`
* `com.day.cq.dam.core.process.CreatePdfPreviewProcess`
* `com.day.cq.dam.core.process.CreateWebEnabledImageProcess`
* `com.day.cq.dam.video.FFMpegThumbnailProcess`
* `com.day.cq.dam.core.process.ThumbnailProcess`
* `com.day.cq.dam.cameraraw.process.CameraRawHandlingProcess`
* `com.day.cq.dam.core.process.CommandLineProcess`
* `com.day.cq.dam.pdfrasterizer.process.PdfRasterizerHandlingProcess`
* `com.day.cq.dam.core.process.AddPropertyWorkflowProcess`
* `com.day.cq.dam.core.process.CreateSubAssetsProcess`
* `com.day.cq.dam.core.process.DownloadAssetProcess`
* `com.day.cq.dam.word.process.ExtractImagesProcess`
* `com.day.cq.dam.word.process.ExtractPlainProcess`
* `com.day.cq.dam.video.FFMpegTranscodeProcess`
* `com.day.cq.dam.ids.impl.process.IDSJobProcess`
* `com.day.cq.dam.indd.process.INDDMediaExtractProcess`
* `com.day.cq.dam.indd.process.INDDPageExtractProcess`
* `com.day.cq.dam.core.impl.lightbox.LightboxUpdateAssetProcess`
* `com.day.cq.dam.pim.impl.sourcing.upload.process.ProductAssetsUploadProcess`
* `com.day.cq.dam.core.process.ScheduledPublishBPProcess`
* `com.day.cq.dam.core.process.ScheduledUnPublishBPProcess`
* `com.day.cq.dam.core.process.SendDownloadAssetEmailProcess`
-->

<!-- PPTX source: slide in add-assets.md - overview of direct binary upload section of
https://adobe-my.sharepoint.com/personal/gklebus_adobe_com/_layouts/15/guestaccess.aspx?guestaccesstoken=jexDC5ZnepXSt6dTPciH66TzckS1BPEfdaZuSgHugL8%3D&docid=2_1ec37f0bd4cc74354b4f481cd420e07fc&rev=1&e=CdgElS
-->

**추가 참조**

* [자산 번역](translate-assets.md)
* [Assets HTTP API](mac-api-assets.md)
* [자산이 지원되는 파일 형식](file-format-support.md)
* [자산 검색](search-assets.md)
* [연결된 자산](use-assets-across-connected-assets-instances.md)
* [자산 보고서](asset-reports.md)
* [메타데이터 스키마](metadata-schemas.md)
* [자산 다운로드](download-assets-from-aem.md)
* [메타데이터 관리](manage-metadata.md)
* [검색 패싯](search-facets.md)
* [컬렉션 관리](manage-collections.md)
* [일괄 메타데이터 가져오기](metadata-import-export.md)

>[!MORELIKETHIS]
>
>* [[!DNL Experience Cloud] as a [!DNL Cloud Service] SDK](/help/implementing/developing/introduction/aem-as-a-cloud-service-sdk.md).