---
title: Universal Editor를 사용하는 로컬 AEM 개발
description: Universal Editor가 개발 목적으로 로컬 AEM 인스턴스 편집을 지원하는 방법에 대해 알아봅니다.
exl-id: ba1bf015-7768-4129-8372-adfb86e5a120
source-git-commit: bbb7e7d9023f8326980196923bfab77c3968ead4
workflow-type: tm+mt
source-wordcount: '699'
ht-degree: 64%

---


# Universal Editor를 사용하는 로컬 AEM 개발 {#local-dev-ue}

Universal Editor가 개발 목적으로 로컬 AEM 인스턴스 편집을 지원하는 방법에 대해 알아봅니다.

{{universal-editor-status}}

## 개요 {#overview}

Universal Editor Service는 Universal Editor와 백엔드 시스템을 바인딩하는 서비스입니다. 범용 편집기에서 로컬로 개발하려면 범용 편집기 서비스의 로컬 복사본을 실행해야 합니다. 이유는 다음과 같습니다.

* Adobe의 공식 범용 편집기 서비스는 전 세계적으로 호스팅되며 로컬 AEM 인스턴스를 인터넷에 노출해야 합니다.
* 로컬 AEM SDK를 사용하여 개발하는 동안 인터넷에서 Adobe의 Universal Editor 서비스에 액세스할 수 없습니다.
* AEM 인스턴스에 IP 제한이 있고 Adobe의 Universal Editor 서비스가 정의된 IP 범위에 있지 않은 경우 직접 호스팅할 수 있습니다.

이 문서에서는 범용 편집기에서 사용할 AEM을 AEM에서 로컬로 개발할 수 있도록 범용 편집기 서비스의 로컬 복사본과 함께 HTTPS로 를 실행하는 방법을 설명합니다.

## HTTPS에서 실행할 AEM 설정 {#aem-https}

HTTPS로 보호되는 외부 프레임 내에서 비보안 HTTP 프레임을 로드할 수 없습니다. Universal Editor Service가 HTTPS에서 실행되므로 AEM 또는 다른 원격 페이지도 HTTPS에서 실행되어야 합니다.

이를 위해 HTTPS에서 실행하려면 AEM을 설정해야 합니다. 개발 목적으로 자체 서명된 인증서를 사용할 수 있습니다.

[이 문서 보기](https://experienceleague.adobe.com/docs/experience-manager-learn/foundation/security/use-the-ssl-wizard.html) 자체 서명된 인증서를 포함하여 HTTPS에서 실행되는 AEM을 설정하는 방법에 대해 설명합니다.

## Universal Editor Service 설치 {#install-ue-service}

범용 편집기 서비스는 범용 편집기의 전체 복사본이 아니라 로컬 AEM 환경의 호출이 인터넷을 통해 라우팅되지 않고 사용자가 제어하는 정의된 끝점에서 라우팅되도록 하는 기능의 하위 집합일 뿐입니다.

[NodeJS 버전 16](https://nodejs.org/en/download/releases) 범용 편집기 서비스의 로컬 복사본을 실행하는 데 필요합니다.

Universal Editor Service는 AEM Engineering에서 직접 배포합니다. 로컬 사본은 VIP 프로그램의 엔지니어에게 문의하십시오.

엔지니어링 담당자는 `universal-editor-service.cjs` 파일을 제공합니다. 이를 로컬 개발 환경으로 저장합니다.

## HTTPS를 사용하여 Universal Editor Service를 실행할 인증서 만들기 {#ue-https}

또한 Universal Editor Service를 사용하려면 개발 환경의 HTTPS에서 실행할 인증서가 필요합니다.

다음 명령을 실행합니다.

```text
$ openssl req -newkey rsa:2048 -nodes -keyout key.pem -x509 -days 365 -out certificate.pem
```

명령은 `key.pem` 및 `certificate.pem` 파일을 생성합니다. 이 파일을 `universal-editor-service.cjs` 파일과 같은 경로로 저장합니다.

## Universal Editor Service 구성 설정 {#setting-up-service}

Universal Editor Service를 로컬에서 실행하려면 NodeJS에서 여러 환경 변수를 설정해야 합니다.

`universal-editor-service.cjs`, `key.pem` 및 `certificate.pem` 파일과 같은 경로에서 다음 콘텐츠로 `.env` 파일을 만듭니다.

```text
EXPRESS_PORT=8000
EXPRESS_PRIVATE_KEY=./key.pem
EXPRESS_CERT=./certificate.pem
NODE_TLS_REJECT_UNAUTHORIZED=0
```

변수의 의미는 다음과 같습니다.

* `EXPRESS_PORT`: Universal Editor Service에서 수신하는 포트 정의
* `EXPRESS_PRIVATE`: [이전에 만든 비공개 키 ](#ue-https) `key.pem`을 가리킴
* `EXPRESS_CERT`: [이전에 만든 인증서, ](#ue-https) `certificate.pem`을 가리킴
* `NODE_TLS_REJECT_UNAUTHORIZED=0`: 자체 서명된 인증서 허용

## Universal Editor Service 실행 {#running-ue}

Universal Editor 서비스를 시작하려면 다음 명령을 실행합니다.

```text
$ node ./universal-editor-service.cjs
```

터미널로 다음 항목이 출력되어야 합니다.

```text
Universal Editor Service listening on port 8000 as HTTPS Server
```

서비스가 HTTP 서버가 아닌 HTTPS 서버를 시작하는지 확인합니다.

## 글로벌 서비스 대신 로컬 Universal Editor Service 사용 {#using-local-ue}

Universal Editor는 페이지 구성 방식에 따라 페이지를 편집하는 데 사용할 Universal Editor Service를 인식합니다. 이는 Universal Editor에 로드된 페이지의 메타 태그를 통해 수행됩니다.

로컬 Universal Editor Service를 사용하여 페이지를 편집하려면 다음 메타 태그를 설정해야 합니다.

```html
<meta name="urn:adobe:aue:config:service" content="https://localhost:8000">
```

설정되면 모든 콘텐츠 업데이트 호출이 기본 Universal Editor Service 대신 `https://localhost:8000`으로 이동하는 것을 확인할 수 있습니다.

>[!NOTE]
>
>직접 액세스 시도 중 `https://localhost:8000` 다음에 결과: `404` 오류. 이는 예상되는 비헤이비어입니다.
>
>로컬 유니버설 편집기 서비스에 액세스를 테스트하려면 `https://localhost:8000/corslib/LATEST`. 다음을 참조하십시오. [다음 섹션](#editing) 을 참조하십시오.

>[!TIP]
>
>페이지를 구성하여 글로벌 Universal Editor Service를 사용하는 방법에 대한 자세한 내용은 [AEM에서 Universal Editor 시작하기](/help/implementing/universal-editor/getting-started.md#instrument-page) 문서를 참조하십시오.

## 로컬 Universal Editor Service를 사용하여 페이지 편집 {#editing}

[Universal Editor Service가 로컬에서 실행](#running-ue)하고 [콘텐츠 페이지를 구성하여 로컬 서비스를 사용](#using-loca-ue)하면 편집기를 시작할 수 있습니다.

1. 브라우저를 열고 `https://localhost:8000/corslib/LATEST`으로 이동합니다.
1. [자체 서명된 인증서](#ue-https)를 허용하도록 브라우저를 내보냅니다.
1. 자체 서명된 인증서를 신뢰하는 경우 로컬 Universal Editor Service를 사용하여 페이지를 편집할 수 있습니다.
