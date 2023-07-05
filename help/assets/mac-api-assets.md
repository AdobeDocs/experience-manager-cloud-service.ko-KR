---
title: Assets HTTP API
description: 에서 HTTP API를 사용하여 디지털 에셋을 생성, 읽기, 업데이트, 삭제 및 관리 [!DNL Experience Manager Assets].
contentOwner: AG
feature: Assets HTTP API,APIs
role: Developer,Architect,Admin
exl-id: a3b7374d-f24b-4d6f-b6db-b9c9c962bb8d
source-git-commit: a01583483fa89f89b60277c2ce4e1c440590e96c
workflow-type: tm+mt
source-wordcount: '1562'
ht-degree: 3%

---

# [!DNL Adobe Experience Manager Assets] HTTP API {#assets-http-api}

| 버전 | 문서 링크 |
| -------- | ---------------------------- |
| AEM 6.5 | [여기를 클릭하십시오.](https://experienceleague.adobe.com/docs/experience-manager-65/assets/extending/mac-api-assets.html?lang=en) |
| AEM as a Cloud Service | 이 문서 |

## 개요 {#overview}

다음 [!DNL Assets] HTTP API를 사용하면 를 사용하여 구조화된 컨텐츠와 함께 메타데이터, 렌디션 및 댓글을 포함하여 디지털 에셋에서 만들기-읽기-업데이트-삭제(CRUD) 작업을 수행할 수 있습니다. [!DNL Experience Manager] 컨텐츠 조각. 다음에서 노출됩니다. `/api/assets` REST API로 구현됩니다. 여기에는 다음이 포함됩니다 [콘텐츠 조각 지원](/help/assets/content-fragments/assets-api-content-fragments.md).

API에 액세스하려면:

1. 다음 위치에서 API 서비스 문서를 엽니다. `https://[hostname]:[port]/api.json`.
1. 다음 [!DNL Assets] 다음으로 이어지는 서비스 링크 `https://[hostname]:[server]/api/assets.json`.

API 응답은 일부 MIME 유형에 대한 JSON 파일이며 모든 MIME 유형에 대한 응답 코드입니다. JSON 응답은 선택 사항이며 예를 들어 PDF 파일에 사용하지 못할 수 있습니다. 추가적인 분석 또는 작업을 위해 응답 코드를 사용합니다.

>[!NOTE]
>
>일반적으로 에셋 또는 바이너리 업로드 또는 업데이트와 관련된 모든 API 호출(예: 렌디션)은 더 이상 사용되지 않습니다. [!DNL Experience Manager] as a [!DNL Cloud Service] 배포. 바이너리를 업로드하려면 다음을 사용합니다. [다이렉트 바이너리 업로드 API](developer-reference-material-apis.md#asset-upload) 대신,

## 콘텐츠 조각 {#content-fragments}

A [컨텐츠 조각](/help/assets/content-fragments/content-fragments.md) 는 특별한 유형의 자산입니다. 텍스트, 숫자, 날짜 등 구조화된 데이터에 액세스하는 데 사용할 수 있습니다. 다음과 같은 몇 가지 차이점이 있습니다. `standard` 에셋(이미지 또는 문서 등), 일부 추가 규칙은 콘텐츠 조각 처리에 적용됩니다.

자세한 내용은 [에서 콘텐츠 조각 지원 [!DNL Experience Manager Assets] HTTP API](/help/assets/content-fragments/assets-api-content-fragments.md).

## 데이터 모델 {#data-model}

다음 [!DNL Assets] HTTP API는 두 개의 주요 요소, 폴더 및 자산(표준 자산의 경우)을 노출합니다. 또한 콘텐츠 조각의 구조화된 콘텐츠를 설명하는 사용자 지정 데이터 모델에 대해 보다 자세한 요소를 노출합니다. 다음을 참조하십시오 [컨텐츠 조각 데이터 모델](/help/assets/content-fragments/assets-api-content-fragments.md#content-models-and-content-fragments) 추가 정보.

### 폴더 {#folders}

폴더는 기존 파일 시스템에서처럼 디렉토리와 같습니다. 폴더에는 에셋, 폴더 또는 폴더와 에셋만 포함될 수 있습니다. 폴더에는 다음과 같은 구성 요소가 있습니다.

**엔티티**: 폴더의 엔티티는 하위 요소이며 폴더 및 에셋이 될 수 있습니다.

**속성**:

* `name` 는 폴더 이름입니다. 확장이 없는 URL 경로의 마지막 세그먼트와 동일합니다.
* `title` 는 이름 대신 표시할 수 있는 폴더의 선택적 제목입니다.

>[!NOTE]
>
>폴더 또는 에셋의 일부 속성이 다른 접두사에 매핑됩니다. 다음 `jcr` 접두사 `jcr:title`, `jcr:description`, 및 `jcr:language` (으)로 대체됨 `dc` 접두사입니다. 따라서 반환된 JSON에서는 `dc:title` 및 `dc:description` 다음 값 포함 `jcr:title` 및 `jcr:description`, 각각

**링크** 폴더에는 세 개의 링크가 표시됩니다.

* `self`: 자체 링크.
* `parent`: 상위 폴더에 대한 링크입니다.
* `thumbnail`: (선택 사항) 폴더 썸네일 이미지에 대한 링크입니다.

### 자산 {#assets}

위치 [!DNL Experience Manager] 자산에는 다음 요소가 포함되어 있습니다.

* 에셋의 속성 및 메타데이터.
* 원래 자산의 바이너리 파일입니다.
* 구성된 여러 렌디션. 다른 크기의 이미지, 다른 인코딩의 비디오 또는 PDF 또는 [!DNL Adobe InDesign] 파일.
* 선택적 주석입니다.

콘텐츠 조각의 요소에 대한 자세한 내용은 [Experience Manager Assets HTTP API의 콘텐츠 조각 지원](/help/assets/content-fragments/assets-api-content-fragments.md).

위치 [!DNL Experience Manager] 폴더에는 다음 구성 요소가 있습니다.

* 엔티티: 에셋의 하위 항목이 렌디션입니다.
* 속성.
* 링크.

## 사용 가능한 기능 {#available-features}

다음 [!DNL Assets] HTTP API에는 다음 기능이 포함되어 있습니다.

* [폴더 목록 검색](#retrieve-a-folder-listing).
* [폴더를 만듭니다](#create-a-folder).
* [자산 만들기(삭제 예정)](#create-an-asset)
* [자산 바이너리 업데이트(더 이상 사용되지 않음)](#update-asset-binary).
* [자산 메타데이터 업데이트](#update-asset-metadata).
* [에셋 렌디션 만들기](#create-an-asset-rendition).
* [에셋 렌디션 업데이트](#update-an-asset-rendition).
* [자산 주석 만들기](#create-an-asset-comment).
* [폴더 또는 자산 복사](#copy-a-folder-or-asset).
* [폴더 또는 자산 이동](#move-a-folder-or-asset).
* [폴더, 에셋 또는 렌디션 삭제](#delete-a-folder-asset-or-rendition).

>[!NOTE]
>
>쉽게 읽을 수 있도록 다음 예제에서는 전체 cURL 표기법을 생략합니다. 표기법은 와 상호 연관됩니다 [레스티](https://github.com/micha/resty) cURL의 스크립트 래퍼입니다.

<!-- TBD: The Console Manager is not available now. So how to configure the below? 

**Prerequisites**

* Go to `https://[aem_server]:[port]/system/console/configMgr`.
* Navigate to **Adobe Granite CSRF Filter**.
* Make sure the property **Filter Methods** includes: POST, PUT, DELETE.
-->

## 폴더 목록 검색 {#retrieve-a-folder-listing}

기존 폴더 및 하위 엔티티(하위 폴더 또는 에셋)의 Siren 표현을 검색합니다.

**요청**: `GET /api/assets/myFolder.json`

**응답 코드**: 응답 코드는 다음과 같습니다.

* 200 - 확인 - 성공.
* 404 - 찾을 수 없음 - 폴더가 없거나 액세스할 수 없습니다.
* 500 - 내부 서버 오류 - 다른 문제가 발생한 경우.

**응답**: 반환된 엔티티의 클래스가 에셋 또는 폴더입니다. 포함된 엔티티의 등록 정보는 각 엔티티의 전체 등록 정보 세트의 하위 집합입니다. 엔티티의 전체 표현을 가져오려면 클라이언트는 링크가 가리키는 URL의 콘텐츠를 `rel` / `self`.

## 폴더를 만듭니다 {#create-a-folder}

를 만듭니다. `sling`: `OrderedFolder` 지정된 경로에서. If `*` 가 노드 이름 대신 제공되면 서블릿은 매개 변수 이름을 노드 이름으로 사용합니다. 요청은 다음 중 하나를 수락합니다.

* 새 폴더의 Siren 표현
* 다음과 같이 인코딩된 이름-값 쌍 세트 `application/www-form-urlencoded` 또는 `multipart`/ `form`- `data`. HTML 양식에서 직접 폴더를 만드는 데 유용합니다.

또한 폴더의 속성을 URL 쿼리 매개 변수로 지정할 수 있습니다.

API 호출이 실패하고 `500` 제공된 경로의 상위 노드가 없는 경우 응답 코드. 호출이 응답 코드를 반환합니다. `409` 폴더가 있는 경우

**매개 변수**: `name` 는 폴더 이름입니다.

**요청**

* `POST /api/assets/myFolder -H"Content-Type: application/json" -d '{"class":"assetFolder","properties":{"title":"My Folder"}}'`
* `POST /api/assets/* -F"name=myfolder" -F"title=My Folder"`

**응답 코드**: 응답 코드는 다음과 같습니다.

* 201 - 작성됨 - 작성됨.
* 409 - 충돌 - 폴더가 있는 경우.
* 412 - 사전 조건 실패 - 루트 컬렉션을 찾거나 액세스할 수 없는 경우.
* 500 - 내부 서버 오류 - 다른 문제가 발생한 경우.

## 에셋 만들기 {#create-an-asset}

다음을 참조하십시오 [에셋 업로드](developer-reference-material-apis.md) 에셋을 만드는 방법에 대한 정보입니다. HTTP API를 사용하여 에셋을 만들 수 없습니다.

## 자산 바이너리 업데이트 {#update-asset-binary}

다음을 참조하십시오 [에셋 업로드](developer-reference-material-apis.md) 자산 바이너리를 업데이트하는 방법에 대한 자세한 내용. HTTP API를 사용하여 자산 바이너리를 업데이트할 수 없습니다.

## 에셋의 메타데이터 업데이트 {#update-asset-metadata}

자산 메타데이터 속성을 업데이트합니다. 에서 속성을 업데이트하는 경우 `dc:` 네임스페이스를 사용하면 API가 `jcr` 네임스페이스입니다. API가 두 네임스페이스 아래의 속성을 동기화하지 않습니다.

**요청**: `PUT /api/assets/myfolder/myAsset.png -H"Content-Type: application/json" -d '{"class":"asset", "properties":{"dc:title":"My Asset"}}'`

**응답 코드**: 응답 코드는 다음과 같습니다.

* 200 - 확인 - 에셋이 성공적으로 업데이트된 경우.
* 404 - 찾을 수 없음 - 제공된 URI에서 에셋을 찾거나 액세스할 수 없는 경우.
* 412 - 사전 조건 실패 - 루트 컬렉션을 찾거나 액세스할 수 없는 경우.
* 500 - 내부 서버 오류 - 다른 문제가 발생한 경우.

## 에셋 렌디션 만들기 {#create-an-asset-rendition}

에셋에 대한 렌디션을 만듭니다. 요청 매개변수 이름이 제공되지 않으면 파일 이름이 렌디션 이름으로 사용됩니다.

**매개 변수**: 매개 변수는 다음과 같습니다 `name` 렌디션 이름 및 `file` 를 파일 참조로 사용하십시오.

**요청**

* `POST /api/assets/myfolder/myasset.png/renditions/web-rendition -H"Content-Type: image/png" --data-binary "@myRendition.png"`
* `POST /api/assets/myfolder/myasset.png/renditions/* -F"name=web-rendition" -F"file=@myRendition.png"`

**응답 코드**

* 201 - 작성됨 - 표현물이 성공적으로 작성된 경우.
* 404 - 찾을 수 없음 - 제공된 URI에서 에셋을 찾거나 액세스할 수 없는 경우.
* 412 - 사전 조건 실패 - 루트 컬렉션을 찾거나 액세스할 수 없는 경우.
* 500 - 내부 서버 오류 - 다른 문제가 발생한 경우.

## 에셋 렌디션 업데이트 {#update-an-asset-rendition}

업데이트는 각각 에셋 렌디션을 새 바이너리 데이터로 바꿉니다.

**요청**: `PUT /api/assets/myfolder/myasset.png/renditions/myRendition.png -H"Content-Type: image/png" --data-binary @myRendition.png`

**응답 코드**: 응답 코드는 다음과 같습니다.

* 200 - 확인 - 표현물이 성공적으로 업데이트된 경우.
* 404 - 찾을 수 없음 - 제공된 URI에서 에셋을 찾거나 액세스할 수 없는 경우.
* 412 - 사전 조건 실패 - 루트 컬렉션을 찾거나 액세스할 수 없는 경우.
* 500 - 내부 서버 오류 - 다른 문제가 발생한 경우.

## 자산에 주석 추가 {#create-an-asset-comment}

**매개 변수**: 매개 변수는 다음과 같습니다 `message` 주석 및 의 메시지 본문용 `annotationData` JSON 형식의 주석 데이터용

**요청**: `POST /api/assets/myfolder/myasset.png/comments/* -F"message=Hello World." -F"annotationData={}"`

**응답 코드**: 응답 코드는 다음과 같습니다.

* 201 - 작성됨 - 주석이 성공적으로 생성된 경우.
* 404 - 찾을 수 없음 - 제공된 URI에서 에셋을 찾거나 액세스할 수 없는 경우.
* 412 - 사전 조건 실패 - 루트 컬렉션을 찾거나 액세스할 수 없는 경우.
* 500 - 내부 서버 오류 - 다른 문제가 발생한 경우.

## 폴더 또는 에셋 복사 {#copy-a-folder-or-asset}

제공된 경로에서 사용할 수 있는 폴더 또는 에셋을 새 대상에 복사합니다.

**요청 헤더**: 매개 변수는 다음과 같습니다.

* `X-Destination` - 리소스를 복사할 API 솔루션 범위 내의 새 대상 URI입니다.
* `X-Depth` - 다음 중 하나 `infinity` 또는 `0`. 사용 `0` 는 리소스 및 해당 속성만 복사하고 하위 속성은 복사하지 않습니다.
* `X-Overwrite` - 사용 `F` 기존 대상에서 에셋을 덮어쓰지 않도록 합니다.

**요청**: `COPY /api/assets/myFolder -H"X-Destination: /api/assets/myFolder-copy"`

**응답 코드**: 응답 코드는 다음과 같습니다.

* 201 - 생성됨 - 폴더/에셋이 존재하지 않는 대상에 복사된 경우.
* 204 - 콘텐츠 없음 - 폴더/에셋이 기존 대상에 복사된 경우.
* 412 - PRECONDITION FAILED - 요청 헤더가 누락된 경우
* 500 - 내부 서버 오류 - 다른 문제가 발생한 경우.

## 폴더 또는 자산 이동 {#move-a-folder-or-asset}

지정된 경로의 폴더 또는 자산을 새 대상으로 이동합니다.

**요청 헤더**: 매개 변수는 다음과 같습니다.

* `X-Destination` - 리소스를 복사할 API 솔루션 범위 내의 새 대상 URI입니다.
* `X-Depth` - 다음 중 하나 `infinity` 또는 `0`. 사용 `0` 는 리소스 및 해당 속성만 복사하고 하위 속성은 복사하지 않습니다.
* `X-Overwrite` - 다음 중 하나를 사용합니다. `T` 기존 리소스를 강제로 삭제하거나 `F` 기존 리소스를 덮어쓰지 않도록 합니다.

**요청**: `MOVE /api/assets/myFolder -H"X-Destination: /api/assets/myFolder-moved"`

**응답 코드**: 응답 코드는 다음과 같습니다.

* 201 - 생성됨 - 폴더/에셋이 존재하지 않는 대상에 복사된 경우.
* 204 - 콘텐츠 없음 - 폴더/에셋이 기존 대상에 복사된 경우.
* 412 - PRECONDITION FAILED - 요청 헤더가 누락된 경우
* 500 - 내부 서버 오류 - 다른 문제가 발생한 경우.

## 폴더, 에셋 또는 렌디션 삭제 {#delete-a-folder-asset-or-rendition}

제공된 경로에서 리소스(-트리)를 삭제합니다.

**요청**

* `DELETE /api/assets/myFolder`
* `DELETE /api/assets/myFolder/myAsset.png`
* `DELETE /api/assets/myFolder/myAsset.png/renditions/original`

**응답 코드**: 응답 코드는 다음과 같습니다.

* 200 - 확인 - 폴더가 성공적으로 삭제된 경우.
* 412 - 사전 조건 실패 - 루트 컬렉션을 찾거나 액세스할 수 없는 경우.
* 500 - 내부 서버 오류 - 다른 문제가 발생한 경우.

## 팁, 모범 사례 및 제한 사항 {#tips-limitations}

* 다음 이후 [!UICONTROL 해제 시간], 에셋 및 해당 렌디션은 [!DNL Assets] 웹 인터페이스 및 HTTP API를 통해. 다음 경우에 API가 404 오류 메시지를 반환합니다. [!UICONTROL 정시] 은(는) 미래이거나 [!UICONTROL 해제 시간] 은(는) 과거입니다.

* Assets HTTP API는 전체 메타데이터를 반환하지 않습니다. 네임스페이스는 하드코딩되고 해당 네임스페이스만 반환됩니다. 전체 메타데이터에 대해서는 에셋 경로 를 참조하십시오. `/jcr_content/metadata.json`.

* 폴더 또는 에셋의 일부 속성은 API를 사용하여 업데이트할 때 다른 접두사에 매핑됩니다. 다음 `jcr` 접두사 `jcr:title`, `jcr:description`, 및 `jcr:language` (으)로 대체됨 `dc` 접두사입니다. 따라서 반환된 JSON에서는 `dc:title` 및 `dc:description` 다음 값 포함 `jcr:title` 및 `jcr:description`, 각각

**추가 참조**

* [자산 번역](translate-assets.md)
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
>* [의 개발자 참조 문서 [!DNL Assets]](/help/assets/developer-reference-material-apis.md)
