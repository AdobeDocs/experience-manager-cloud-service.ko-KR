---
title: CDN 오류 페이지 구성
description: Amazon S3 또는 Azure Blob Storage와 같은 자체 호스팅 저장소에서 정적 파일을 호스팅하고 Cloud Manager 구성 파이프라인을 사용하여 배포된 구성 파일에서 참조하여 기본 오류 페이지를 재정의하는 방법에 대해 알아봅니다.
feature: Dispatcher
exl-id: 1ecc374c-b8ee-41f5-a565-5b36445d3c7c
source-git-commit: 69ffcccae150a5e49c6344973890733f3e5b74ae
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 5%

---

# CDN 오류 페이지 구성 {#cdn-error-pages}

혹시나 해서 [Adobe 관리 CDN](/help/implementing/dispatcher/cdn.md#aem-managed-cdn) AEM 원본에 연결할 수 없습니다. 기본적으로 CDN은 서버에 연결할 수 없음을 나타내는 브랜딩되지 않은 일반 오류 페이지를 제공합니다. Amazon S3 또는 Azure Blob Storage와 같은 자체 호스팅 저장소에서 정적 파일을 호스팅하고 를 사용하여 배포된 구성 파일에서 이를 참조하여 기본 오류 페이지를 재정의할 수 있습니다. [Cloud Manager 구성 파이프라인](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md#config-deployment-pipeline).

## 설정 {#setup}

기본 오류 페이지를 재정의하려면 먼저 다음을 수행해야 합니다.

* Git 프로젝트의 최상위 수준 폴더에서 이 폴더 및 파일 구조를 만듭니다.

```
config/
     cdn.yaml
```

* 다음 `cdn.yaml` 구성 파일에는 아래 예제에 설명된 메타데이터와 규칙이 모두 포함되어야 합니다. 다음 `kind` 매개 변수는 다음으로 설정해야 합니다. `CDN` 및 버전은 현재 인 스키마 버전으로 설정해야 합니다. `1`.

* Cloud Manager에서 타깃팅된 배포 구성 파이프라인을 만듭니다. 다음을 참조하십시오 [프로덕션 파이프라인 구성](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md) 및 [비프로덕션 파이프라인 구성](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md).

**메모**

* RDE는 현재 구성 파이프라인을 지원하지 않습니다.
* `yq`을 사용하여 구성 파일(예: `yq cdn.yaml`)의 YAML 서식을 로컬에서 확인할 수 있습니다.

### 구성 {#configuration}

오류 페이지는 단일 페이지 애플리케이션(SPA)으로 구현되며 아래 예와 같이 몇 가지 속성을 참조합니다.  URL에서 참조하는 정적 파일은 Amazon S3 또는 Azure Blob Storage와 같이 인터넷에 액세스할 수 있는 서비스에서 호스팅해야 합니다.

구성 예:

```
kind: "CDN"
version: "1"
metadata:
  envTypes: ["dev"]
data:
  experimental_errorPages:
    spa:
      title: the error page
      icoUrl: https://www.example.com/error.ico
      cssUrl: https://www.example.com/error.css
      jsUrl: https://www.example.com/error.js
```

| 이름 | 허용된 속성 | 의미 |
|-----------|--------------------------|-------------|
| **spa** | 제목 | 오류 페이지 제목 |
|     | icoUrl | 아이콘 파일에 대한 URL. |
|     | cssUrl | CSS 파일의 URL. |
|     | jsUrl | JavaScript 파일의 URL입니다. |

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
