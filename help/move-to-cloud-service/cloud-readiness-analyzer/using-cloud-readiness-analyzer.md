---
title: 클라우드 준비 분석기 사용
description: 클라우드 준비 분석기 사용
translation-type: tm+mt
source-git-commit: 2064dd6c647780dc149c51b7ff166779ba0a2212
workflow-type: tm+mt
source-wordcount: '1713'
ht-degree: 0%

---


# 클라우드 준비 분석기 사용 {#using-cloud-readiness-analyzer}

## 클라우드 준비 분석기 사용에 대한 중요 고려 사항 {#imp-considerations}

CRA(클라우드 준비 분석기)를 실행하는 동안 중요한 고려 사항을 이해하려면 아래 섹션을 따르십시오.

* CRA 보고서는 Adobe Experience Manager(AEM) [패턴 탐지기 출력을 사용하여 만듭니다](https://docs.adobe.com/content/help/en/experience-manager-65/deploying/upgrading/pattern-detector.html). CRA에서 사용하는 패턴 탐지기 버전은 CRA 설치 패키지에 포함되어 있습니다.

* CRA는 관리자 **사용자** 또는 관리자의 사용자만 실행할 수 **있습니다**.

* CRA는 버전 6.1 이상의 AEM 인스턴스에서 지원됩니다.

* CRA는 모든 환경에서 실행할 수 있지만 *스테이지* 환경에서 실행되는 것이 좋습니다.

   >[!NOTE]
   >비즈니스 크리티컬 인스턴스에 영향을 주지 않도록 사용자 지정, 구성, 컨텐츠 및 사용자 애플리케이션 영역에서 가능한 한 *프로덕션* ** 환경과 가까운 작성 환경에서 CRA를 실행하는 것이 좋습니다. 또는 프로덕션 작성자 환경의 클론에서 실행할 *수* 있습니다.

* CRA 보고서 컨텐츠를 만드는 데 몇 분에서 몇 시간 정도의 시간이 걸릴 수 있습니다. 필요한 시간은 AEM 리포지토리 컨텐츠, AEM 버전 및 기타 요소에 크게 의존합니다.

* 보고서 컨텐츠를 생성하는 데 필요한 상당한 시간 때문에 백그라운드 프로세스에 의해 생성되고 캐시에 보관됩니다. 보고서가 만료되거나 보고서가 명시적으로 새로 고쳐질 때까지 컨텐츠 캐시를 활용하므로 보고서를 보고 다운로드하는 작업이 상대적으로 빨라야 합니다. 보고서 컨텐츠를 생성하는 동안 브라우저 탭을 닫고 나중에 돌아와서 컨텐츠가 캐시에서 사용 가능하게 되면 보고서를 볼 수 있습니다.

## 사용 가능 {#availability}

클라우드 준비 분석기는 소프트웨어 배포 포털에서 zip 파일로 다운로드할 수 있습니다. 소스 Adobe Experience Manager(AEM) 인스턴스에 패키지 관리자를 통해 패키지를 설치할 수 있습니다.

>[!NOTE]
>Software Distribution Portal에서 Cloud Readance Analyzer를 다운로드합니다.

## 클라우드 준비 분석기 보고서 보기 {#viewing-report}

### Adobe Experience Manager 6.3 and later {#aem-later-versions}

클라우드 준비 분석기 보고서를 보는 방법을 알려면 다음 섹션을 따르십시오.

1. Adobe Experience Manager을 선택하고 도구 -> **작업** -> **클라우드 준비 분석기로 이동합니다**.

   ![이미지](/help/move-to-cloud-service/cloud-readiness-analyzer/assets/cra-1.png)

1. 클라우드 준비 분석기를 클릭하면 **도구**&#x200B;가 보고서 생성을 시작하고 사용 가능한 경우 보고서를 표시합니다.

   >[!NOTE]
   >전체 보고서를 보려면 페이지를 아래로 스크롤해야 합니다.

   ![이미지](/help/move-to-cloud-service/cloud-readiness-analyzer/assets/cra-tool-1.png)

1. CRA 보고서가 생성되고 표시되면 보고서를 쉼표로 구분된 값(CSV)으로 다운로드하는 옵션이 있습니다. 아래 그림과 같이 **CSV** 를 클릭하여 전체 CRA 보고서를 쉼표로 구분된 값(CSV) 형식으로 다운로드합니다.

   ![이미지](/help/move-to-cloud-service/cloud-readiness-analyzer/assets/cra-tool-2.png)

   >[!NOTE]
   >보고서 새로 고침을 클릭하여 CRA가 캐시를 지우고 보고서를 다시 **생성하도록 할 수 있습니다**.

### Adobe Experience Manager 6.2 및 6.1 {#aem-specific-versions}

클라우드 준비 분석기는 Adobe Experience Manager 6.2에서 CSV 보고서를 생성하고 다운로드하는 링크로 제한됩니다.

Adobe Experience Manager 6.1의 경우 도구가 작동하지 않으며 HTTP 인터페이스만 사용할 수 있습니다.

>[!NOTE]
>모든 버전에서 포함된 패턴 탐지기는 독립적으로 실행될 수 있습니다.

## 클라우드 준비 분석기 보고서 해석 {#cra-report}

AEM 인스턴스에서 클라우드 준비 분석기 도구를 실행하면 보고서가 도구 창의 결과로 표시됩니다.

보고서의 형식은 다음과 같습니다.

* **보고서 개요**: 보고서 자체에 대한 정보 및 다음과 같은 정보
   * *보고서 시간*: 보고서 컨텐츠가 생성되어 처음 사용할 수 있게 되었을 때.
   * *만료 시간*: 보고서 내용 캐시가 만료될 때.
   * *생성 기간*: 보고서 내용 생성 프로세스의 체류 시간.
   * *Finding Count*: The total number of findings included in the report.
* **시스템 개요**: CRA가 실행된 AEM 시스템에 대한 정보입니다.
* **카테고리 찾기**: 각 섹션에서 동일한 카테고리의 하나 이상의 발견을 처리하는 여러 섹션입니다. 각 섹션에는 다음이 포함됩니다. 카테고리 이름, 하위 유형, 검색 횟수 및 중요도, 요약, 카테고리 설명서 링크 및 개별 검색 정보

작업의 대략적인 우선순위를 나타내기 위해 각 검색 결과에 중요도 수준이 지정됩니다.

아래 표에 따라 중요도 수준을 파악하십시오.

| 중요 | 설명 |
|--- |--- |
| 정보 | 이 검색 결과는 정보용으로 제공됩니다. |
| 권고 조치 | 이 검색 결과는 잠재적으로 업그레이드 문제가 될 수 있습니다. 추가 조사가 권장됩니다. |
| 주요 | 이 문제는 해결해야 하는 업그레이드 문제가 될 수 있습니다. |
| 위험 | 이러한 검색 결과는 기능 또는 성능 손실을 방지하기 위해 해결해야 하는 업그레이드 문제가 될 가능성이 높습니다. |


## 클라우드 준비 분석기 CSV 보고서 해석 {#cra-csv-report}

AEM 인스턴스에서 **CSV** 옵션을 클릭하면 클라우드 준비 분석기 보고서의 CSV 형식이 컨텐츠 캐시에서 만들어지고 브라우저에 반환됩니다. 브라우저 설정에 따라 이 보고서는 기본 이름이 인 파일로 자동으로 다운로드됩니다 `results.csv`.

캐시가 만료되면 CSV 파일을 빌드하고 다운로드하기 전에 보고서가 다시 생성됩니다.

보고서의 CSV 형식에는 패턴 탐지기 출력에서 생성된 정보가 포함되어 있으며 카테고리 유형, 하위 유형 및 중요도 수준별로 정렬 및 구성됩니다. Microsoft Excel과 같은 애플리케이션에서 보고 편집하는 데 적합합니다. 진행 상황을 측정하기 위해 시간 경과에 따른 보고서를 비교할 때 유용할 수 있는 모든 검색 정보를 반복 가능한 형식으로 제공하기 위한 것입니다.

CSV 형식 보고서의 열은 다음과 같습니다.

* **코드**: 범주 코드
* **type**: 범주 이름
* **하위 유형**: 범주 하위 유형
* **중요도**: 중요도
* **식별자**: 검색 결과의 기본 식별자
* **기타**: 검색 결과에 대한 추가 정보
* **메시지**: 검색을 위해 제공된 메시지
* **moreInfo**: 카테고리에 대한 온라인 도움말에 액세스하는 데 사용할 수 있는 링크
* **컨텍스트**: 데이터를 찾는 JSON 문자열

개별 검색 열에 있는 &quot;\N&quot;의 값은 제공된 데이터가 없음을 나타냅니다.

## HTTP 인터페이스 {#http-interface}

CRA는 AEM 내의 사용자 인터페이스 대신 사용할 수 있는 HTTP 인터페이스를 제공합니다. 인터페이스는 HEAD 및 GET 명령을 모두 지원합니다. CRA 보고서를 생성하고 다음 세 형식 중 하나로 반환하는 데 사용할 수 있습니다. JSON, CSV 및 탭으로 구분된 값(TSV).

다음 URL은 CRA가 설치된 서버의 호스트 이름 `<host>` 과 포트(필요한 경우)인 HTTP 액세스에 사용할 수 있습니다.
* `http://<host>/apps/readiness-analyzer/analysis/result.json` for JSON format
* `http://<host>/apps/readiness-analyzer/analysis/result.csv` for CSV format
* `http://<host>/apps/readiness-analyzer/analysis/result.tsv` for TSV format

### HTTP 요청 실행 {#executing-http-request}

HTTP 인터페이스는 다양한 방법으로 사용될 수 있습니다.

한 가지 간단한 방법은 관리자로 AEM에 이미 로그인되어 있는 동일한 브라우저에서 브라우저 탭을 여는 것입니다. 브라우저 탭에 URL을 입력하고 결과를 브라우저가 표시하거나 다운로드하도록 할 수 있습니다.

또한 HTTP 클라이언트 응용 프로그램 `curl` 또는 기타 `wget` 와 같은 명령줄 도구를 사용할 수 있습니다. 인증된 세션에서 브라우저 탭을 사용하지 않는 경우 주석의 일부로 관리 사용자 이름과 암호를 제공해야 합니다.

다음은 이 작업을 수행하는 방법의 예입니다.
`curl -u admin:admin 'http://localhost:4502/apps/readiness-analyzer/analysis/result.csv' > result.csv`.

### 머리글 및 매개 변수 {#http-headers-and-parameters}

이 인터페이스에서는 다음 HTTP 헤더를 사용합니다.

* `Cache-Control: max-age=<seconds>`: 캐시 신선도 수명을 초 단위로 지정합니다. (RFC [7234](https://tools.ietf.org/html/rfc7234#section-5.2.2.8)참조)
* `Prefer: respond-async`: 서버가 비동기적으로 응답해야 함을 나타냅니다. (RFC [7240을](https://tools.ietf.org/html/rfc7240#section-4.1)참조하십시오.)

다음 HTTP 쿼리 매개 변수는 HTTP 헤더를 쉽게 사용하지 않을 때 편리하게 사용할 수 있습니다.

* `max-age` (숫자, 선택 사항): 캐시 신선도 수명을 초 단위로 지정합니다. 이 숫자는 0보다 커야 합니다. 기본 신선도 수명은 86400초입니다. 즉, 이 매개 변수 또는 해당 헤더가 없으면 새 캐시가 24시간 동안 요청을 제공하는 데 사용되어 보고서를 다시 생성해야 합니다. 을 사용하면 캐시 `max-age=0` 가 지워지고 보고서의 재재생이 시작됩니다. 이 요청 직후 신선도 라이프타임은 이전의 0이 아닌 값으로 재설정됩니다.
* `respond-async` (부울, 선택 사항): 응답이 비동기식으로 제공되도록 지정합니다. 캐시가 오래된 `respond-async=true` 경우 서버가 보고서가 생성되어 캐시가 새로 고쳐질 때까지 기다리지 않고 응답을 `202 Accepted, processing cache` 반환합니다. 캐시를 새로 고치면 이 매개 변수는 영향을 주지 않습니다. 기본값은 `false`입니다. 즉, 이 매개 변수 또는 해당 헤더가 없으면 서버가 동기적으로 응답합니다. 이 경우 상당한 시간이 필요하고 HTTP 클라이언트에 대한 최대 응답 시간을 조정해야 합니다.

HTTP 헤더와 해당 쿼리 매개 변수가 모두 있으면 쿼리 매개 변수가 우선합니다.

HTTP 인터페이스를 통해 보고서의 생성을 시작하는 간단한 방법은 다음 명령을 사용하는 것입니다.
`curl -u admin:admin 'http://localhost:4502/apps/readiness-analyzer/analysis/result.json?max-age=0&respond-async=true'`.

요청이 수행된 후 보고서가 생성되도록 클라이언트가 활성 상태를 유지할 필요가 없습니다. HTTP GET 요청을 사용하는 하나의 클라이언트로 보고서 생성을 시작할 수 있으며 보고서가 생성되면 다른 클라이언트의 캐시에서 보거나 AEM 내의 사용자 인터페이스의 CSV 도구에서 볼 수 있습니다.

### 응답(#http-responses)

다음 응답 값이 가능합니다.

* `200 OK`: 이 응답에는 캐시의 최신 수명 내에 생성된 패턴 탐지기 결과를 포함합니다.
* `202 Accepted, processing cache`: 캐시가 오래된 상태이고 새로 고침이 진행 중임을 나타내는 비동기 응답에 대해 제공됩니다.
* `400 Bad Request`: 요청에 오류가 있음을 나타냅니다. 자세한 내용은 문제 세부 정보 형식( [RFC 7807](https://tools.ietf.org/html/rfc7807)참조)의 메시지를 참조하십시오.
* `401 Unauthorized`: 요청이 승인되지 않았습니다.
* `500 Internal Server Error`: 내부 서버 오류가 발생했음을 나타냅니다. 자세한 내용은 문제 세부 정보 형식의 메시지를 참조하십시오.
* `503 Service Unavailable`: 서버가 다른 응답으로 사용 중이어서 이 요청을 적시에 처리할 수 없음을 나타냅니다. 이는 동기 요청이 수행된 경우에만 발생합니다. 자세한 내용은 문제 세부 정보 형식의 메시지를 참조하십시오.

## 캐시 수명 조정 {#cache-adjustment}

기본 CRA 캐시 수명은 24시간입니다. 보고서를 새로 고치고 캐시를 다시 생성하는 옵션과 함께 AEM 인스턴스와 HTTP 인터페이스 모두에서 이 기본값은 CRA의 대부분의 사용에 적절할 것입니다. 보고서 생성 시간이 AEM 인스턴스에 특히 긴 경우 보고서 재생성을 최소화하기 위해 캐시 수명을 조정할 수 있습니다.

캐시 라이프타임 값은 다음 저장소 노드의 `maxCacheAge` 속성으로 저장됩니다.
`/apps/readiness-analyzer/content/CloudReadinessReport/jcr:content`

이 속성의 값은 캐시 수명(초)입니다. 관리자는 CRXDE Lite를 사용하여 캐시 수명을 조정할 수 있습니다.





