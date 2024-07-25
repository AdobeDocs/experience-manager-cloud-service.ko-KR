---
title: CDN 오류 페이지 구성
description: Amazon S3 또는 Azure Blob Storage와 같은 자체 호스팅 저장소에서 정적 파일을 호스팅하고 Cloud Manager 구성 파이프라인을 사용하여 배포된 구성 파일에서 참조하여 기본 오류 페이지를 재정의하는 방법에 대해 알아봅니다.
feature: Dispatcher
exl-id: 1ecc374c-b8ee-41f5-a565-5b36445d3c7c
role: Admin
source-git-commit: 3a10a0b8c89581d97af1a3c69f1236382aa85db0
workflow-type: tm+mt
source-wordcount: '365'
ht-degree: 1%

---


# CDN 오류 페이지 구성 {#cdn-error-pages}

[Adobe 관리 CDN](/help/implementing/dispatcher/cdn.md#aem-managed-cdn)이(가) AEM 원본에 도달할 수 없는 경우에는 기본적으로 CDN에 서버에 도달할 수 없음을 나타내는 브랜드가 없는 일반 오류 페이지가 표시됩니다. Amazon S3 또는 Azure Blob Storage와 같은 자체 호스팅 저장소에서 정적 파일을 호스팅하고 Cloud Manager [구성 파이프라인을 사용하여 배포된 구성 파일에서 참조하여 기본 오류 페이지를 재정의할 수 있습니다.](/help/operations/config-pipeline.md#managing-in-cloud-manager)

## 설정 {#setup}

기본 오류 페이지를 재정의하려면 먼저 다음을 수행해야 합니다.

1. 아래 구문 섹션을 참조하여 이름이 `cdn.yaml`이거나 유사한 파일을 만드십시오.

1. [구성 파이프라인 문서](/help/operations/config-pipeline.md#folder-structure)에 설명된 대로 파일을 *config* 또는 유사한 최상위 폴더 아래에 배치합니다.

1. [구성 파이프라인 문서](/help/operations/config-pipeline.md#managing-in-cloud-manager)에 설명된 대로 Cloud Manager에서 구성 파이프라인을 만듭니다.

1. 구성 배포.

### 구문 {#syntax}

오류 페이지는 단일 페이지 애플리케이션(SPA)으로 구현되며 아래 예와 같이 몇 가지 속성을 참조합니다.  URL에서 참조하는 정적 파일은 Amazon S3 또는 Azure Blob Storage와 같이 인터넷에 액세스할 수 있는 서비스에서 호스팅해야 합니다.

구성 예:

```
kind: "CDN"
version: "1"
metadata:
  envTypes: ["dev"]
data:
  errorPages:
    spa:
      title: the error page
      icoUrl: https://www.example.com/error.ico
      cssUrl: https://www.example.com/error.css
      jsUrl: https://www.example.com/error.js
```
데이터 노드 위의 속성에 대한 설명은 [구성 파이프라인 문서](/help/operations/config-pipeline.md#common-syntax)를 참조하십시오. 종류 속성 값은 *CDN*&#x200B;이어야 하며 `version` 속성은 *1*(으)로 설정해야 합니다.


| 이름 | 허용된 속성 | 의미 |
|-----------|--------------------------|-------------|
| **spa** | 제목 | 오류 페이지 제목 |
|     | icoUrl | 아이콘 파일에 대한 URL. |
|     | cssUrl | CSS 파일의 URL. |
|     | jsUrl | JavaScript 파일에 대한 URL. |

### 샘플 생성 HTML {#sample-generated-html}

CDN에서 생성되어 브라우저와 같이 클라이언트에 제공되는 HTML 코드는 다음 코드 조각과 비슷하지만 동일하지는 않습니다.

```
<!DOCTYPE html>
<html lang="en">
    <head>
        ...
        <title>the error page</title>
        <link rel="icon" href="https://www.example.com/error.ico">
        <link rel="stylesheet" href="https://www.example.com/error.css">
    </head>
    <body>
        ...
        <div id="root" status="403"></div>
        <script src="https://www.example.com/error.js"> </script>
    </body>
</html>
```

### 테스트 {#testing}

테스트 목적으로 지원되는 오류 코드와 함께 전용 엔드포인트를 호출하십시오. 예:

```
curl "https://publish-pXXXXX-eXXXXXX.adobeaemcloud.com/cdnstatus?code=403"
```

지원되는 코드는 403, 404, 406, 500 및 503입니다.

이러한 방식으로, 주어진 오류 코드에 대한 합성 응답을 테스트하기 위해 CDN의 오류 핸들러를 직접 트리거합니다.
