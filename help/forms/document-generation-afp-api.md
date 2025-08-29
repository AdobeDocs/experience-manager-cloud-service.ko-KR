---
title: AFP 출력 동기화 API를 사용하는 방법
description: AFP Output Sync API를 사용하여 출력 표현물을 검색하고 동기화하는 방법에 대해 알아봅니다.
feature: Adaptive Forms, APIs & Integrations, Document Services
role: Admin, User
exl-id: 5602fc63-ef74-44eb-b3be-61b8f8a2795a
source-git-commit: 03e46bb43e684a6b7057045cf298f40f9f1fe622
workflow-type: tm+mt
source-wordcount: '237'
ht-degree: 14%

---

# AEM Forms API를 사용하여 AFP 출력 생성

<span class="preview"> 이는 프리릴리스 기능이고 [프리릴리스 채널](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/release-notes/prerelease.html?lang=ko#new-features)을 통해 액세스할 수 있습니다. </span>

AFP(Advanced Function Presentation)는 주로 인쇄용으로 설계된 고성능 문서 형식입니다.\
이 안내서에서는 AEM Forms을 사용하여 AFP 출력을 생성하는 데 필요한 모든 단계 및 구성을 간략하게 설명합니다.

<!--
## Prerequisites

To support AFP output generation, the following OSGi bundles must be present and in an **active** state:

* **AFP Core Bundle** – Available in the AFP repository
* **Forms Output Core** – Found in the Forms Output comments package
* **Bedrock Connector** – Provided by the Forms Output API
* **Cloud Ready Implementation** – Available through the Forms installer

>[!NOTE]
>
> * If any bundle is inactive, resolve dependency issues or reinstall manually.
> * To enable AFP generation, the `FT_FORMS-17887` toggle configurations must be set in AEM configuration manager.-->

## AFP 생성 API

XDP 템플릿과 입력 데이터를 사용하여 AFP(Advanced Function Presentation) 파일을 생성합니다.

### 승인

로컬 환경에 대해 **BasicAuth**(관리자 자격 증명)를 사용하거나 AEM Cloud 인스턴스에 대해 **BearerAuth** 인증을 사용할 수 있습니다.

### 요청

**끝점:**
`POST http://<server>:<port>/adobe/forms/document/generate/afp`

### 헤더

| 키 | 값 |
| --------------- | ------------------------------------------------------ |
| `Content-Type` | `application/pdf` |
| `Authorization` | `(Bearer Access token)` |

### 요청 본문

**콘텐츠 형식: multipart/form-data**

| 키 | 유형 | 필수 | 설명 |
| ---------- | ---- | -------- | ------------------------------------------------------------------------- |
| `template` | 파일/텍스트 | 예 | AFP 생성용 템플릿으로 사용되는 XDP 파일(예: `demo.xdp`) |
| `data` | 파일/텍스트 | 아니요 | 템플릿에 병합할 데이터 파일(XML 또는 JSON)(예: `data.xml`) |
| `options` | 텍스트 | 아니요 | AFP 출력을 제어하는 옵션이 포함된 JSON 문자열(예: 해상도, 로케일) |

**예 `options` JSON(텍스트 필드):**

```json
{
  "pdfVersion": "1.7",
  "resolution": 300,
  "locale": "en-US",
  "embedFonts": true,
  "contentRoot": "/usr/tmp"
}
```

### 응답

| 코드 | 설명 |
| ----- | ------------------------------------------------------------------------- |
| `200` | 작업이 완료되었습니다. AFP 문서 스트림을 반환합니다. |
| `400` | 잘못된 요청. 요청 페이로드의 형식이 잘못되었거나 필수 필드가 누락되었습니다. |
| `500` | 내부 서버 오류. 잠시 후 다시 시도하십시오. |

### Curl 명령

```
curl --location 'http://<server>:<port>/adobe/forms/document/generate/afp' \
--header 'Authorization: Bearertoken <base64-encoded-credentials>' \
--form 'template=@"<path-to-template>.xdp"' \
--form 'data=@"<path-to-data-file>.xml"' \
--form 'options=<JSON-options-string>'
```

### API 테스트

.yaml 파일을 다운로드하고 Postman에 업로드하여 API의 기능을 확인할 수 있습니다.

![AFP Postman 이미지](/help/forms/assets/afp-postman.png)

응답을 저장하고 저장된 파일을 AFP 판독기에서 열어 볼 수 있습니다.

![PDF reader](/help/forms/assets/afp-pdf.png)
