---
title: Best Practices Analyzer 사용
description: Best Practices Analyzer 사용
exl-id: e8498e17-f55a-4600-87d7-60584d947897
source-git-commit: 1994b90e3876f03efa571a9ce65b9fb8b3c90ec4
workflow-type: tm+mt
source-wordcount: '2474'
ht-degree: 46%

---

# Best Practices Analyzer 사용 {#using-best-practices-analyzer}

>[!CONTEXTUALHELP]
>id="aemcloud_bpa_using"
>title="모범 사례 분석기 사용"
>abstract="모범 사례 분석기(이전의 Cloud Readiness Analyzer)와 생성된 보고서 사용 설명서를 검토합니다. 모범 사례 분석기 보고서는 일반적인 업그레이드 준비 상태를 세부적으로 파악하는 데 사용됩니다."
>additional-url="https://my.adobeconnect.com/pqgrfezoxghs?proto=true" text="[웨비나] Adobe Experience Manager as a Cloud Service로의 여정을 가속화하는 도구 소개"

## Best Practices Analyzer 사용에 대한 중요 고려 사항 {#imp-considerations}

Best Practices Analyzer(BPA) 실행을 위한 중요한 고려 사항을 이해하려면 아래 섹션을 따르십시오.

* BPA 보고서는 Adobe Experience Manager(AEM)의 출력을 사용하여 작성됩니다 [패턴 탐지기](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/upgrading/pattern-detector.html). BPA에서 사용하는 패턴 탐지기 버전은 BPA 설치 패키지에 포함되어 있습니다.

* BPA는 **admin** 사용자 또는 의 사용자 **관리자** 그룹입니다.

* BPA는 버전 6.1 이상의 AEM 인스턴스에서 지원됩니다.

  >[!NOTE]
  >다음을 참조하십시오 [AEM 6.1에 설치](#installing-on-aem61) AEM 6.1에 BPA를 설치하기 위한 특별 요구 사항.

* BPA는 모든 환경에서 실행할 수 있지만 *단계* 환경.

  >[!NOTE]
  >비즈니스 크리티컬 인스턴스에 영향을 주지 않도록 다음에서 BPA를 실행하는 것이 좋습니다. *작성자* 에 최대한 가까운 환경 *프로덕션* 사용자 정의, 구성, 콘텐츠 및 사용자 애플리케이션 영역의 환경. 또는 프로덕션 *작성* 환경의 복제본에서 실행할 수 있습니다.

* BPA 보고서 컨텐츠를 생성하는 데 몇 분에서 몇 시간까지 상당한 시간이 걸릴 수 있습니다. 필요한 시간은 AEM 저장소 컨텐츠, AEM 버전 및 기타 요소에 따라 크게 달라집니다.

* 보고서 컨텐츠를 생성하는 데 필요한 상당한 시간으로 인해 백그라운드 프로세스에 의해 생성되고 캐시에 보관됩니다. 보고서가 만료되거나 보고서가 명시적으로 새로 고쳐질 때까지 컨텐츠 캐시를 활용하므로 보고서를 보고 다운로드하는 작업이 상대적으로 빨라야 합니다. 보고서 컨텐츠를 생성하는 동안 브라우저 탭을 닫고 나중에 돌아와서 컨텐츠가 캐시에서 사용 가능하게 되면 보고서를 볼 수 있습니다.

## 사용 가능 {#availability}

>[!CONTEXTUALHELP]
>id="aemcloud_bpa_download"
>title="모범 사례 분석기 다운로드"
>abstract="소프트웨어 배포 포털에서 모범 사례 분석기를 zip 파일로 다운로드할 수 있습니다. 패키지 관리자를 통해 소스 AEM(Adobe Experience Manager) 인스턴스에 패키지를 설치할 수 있습니다."

소프트웨어 배포 포털에서 모범 사례 분석기를 zip 파일로 다운로드할 수 있습니다. 다음을 통해 패키지를 설치할 수 있습니다. [패키지 관리자](/help/implementing/developing/tools/package-manager.md) 소스 Adobe Experience Manager(AEM) 인스턴스에서 다음을 수행합니다.

>[!NOTE]
>에서 모범 사례 분석기 다운로드 [소프트웨어 배포](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html) 포털.

## 모범 사례 분석기 보고서 보기 {#viewing-report}

### Adobe Experience Manager 6.3.0 이상 {#aem-later-versions}

모범 사례 분석기 보고서를 보는 방법에 대해 알아보려면 이 섹션을 따르십시오.

1. Adobe Experience Manager 를 선택하고 도구 -> 로 이동합니다. **작업** -> **모범 사례 분석기**.

   ![이미지](/help/journey-migration/best-practices-analyzer/assets/BPA_pic1.png)

1. 클릭 **보고서 생성** 를 클릭하여 모범 사례 분석기를 실행하십시오.

   ![이미지](/help/journey-migration/best-practices-analyzer/assets/BPA_pic2.png)

1. BPA가 보고서를 생성하는 동안 도구에서 수행한 진행 상황을 화면에 볼 수 있습니다. 분석된 항목 수와 발견된 검색 결과 수를 표시합니다.

   ![이미지](/help/journey-migration/best-practices-analyzer/assets/BPA_pic3.png)

1. BPA 보고서가 생성되면 요약 및 결과 수가 검색 유형 및 중요도 수준별로 구성된 표 형식으로 표시됩니다. 특정 검색 결과에 대한 자세한 내용을 보려면 테이블에서 검색 유형에 해당하는 숫자를 클릭합니다.

   ![이미지](/help/journey-migration/best-practices-analyzer/assets/BPA_pic4.png)

   위의 작업은 보고서에서 해당 검색 결과의 위치로 자동 스크롤됩니다.

   ![이미지](/help/journey-migration/best-practices-analyzer/assets/BPA_pic5.png)

1. 을 클릭하여 쉼표로 구분된 값(CSV) 형식으로 보고서를 다운로드할 수 있는 옵션이 있습니다. **CSV로 내보내기**&#x200B;을 참조하십시오.

   ![이미지](/help/journey-migration/best-practices-analyzer/assets/BPA_pic6.png)

   >[!NOTE]
   >를 클릭하여 BPA가 캐시를 지우고 보고서를 다시 생성하도록 할 수 있습니다. **보고서 새로 고침**.

   ![이미지](/help/journey-migration/best-practices-analyzer/assets/BPA_pic7.png)

   >[!NOTE]
   >보고서가 다시 생성되는 동안 아래 이미지에 표시된 대로 완료율 측면에서 진행률이 표시됩니다.

   ![이미지](/help/journey-migration/best-practices-analyzer/assets/BPA_pic8.png)

#### 모범 사례 분석기 보고서에서 필터 사용 {#bpa-filters}

관련 결과를 필터링하려면 [ACS 커먼즈](https://adobe-consulting-services.github.io/acs-aem-commons/)을(를) 클릭하고 아래 단계를 수행합니다.

1. 페이지 왼쪽에 있는 왼쪽 레일 아이콘을 클릭합니다. 이 경우 **ACS Commons 필터**. 을(를) 클릭합니다 **ACS Commons 필터** 아래 이미지에 표시된 대로 대화형 확인란을 표시합니다.

   ![이미지](/help/journey-migration/best-practices-analyzer/assets/report_filter_1.png)

   >[!NOTE]
   >왼쪽 레일 아이콘은 BPA가 ACS Commons 사용을 감지한 경우에만 나타납니다.

1. ACS Commons와 관련된 모든 검색 결과를 필터링하려면 상자를 선택 취소합니다. 다음이 표시됩니다. **필터링된 검색 횟수** 아래 그림과 같이 보고서에 표시합니다. 필터는 CSV(쉼표로 구분된 값) 형식으로 내보낼 때도 보고서에 적용됩니다.

   ![이미지](/help/journey-migration/best-practices-analyzer/assets/report_filter_2.png)

   >[!NOTE]
   >ACS Commons 결과를 무시해서는 안 됩니다. 다음을 참조하십시오 [설명서](https://adobe-consulting-services.github.io/acs-aem-commons/pages/compatibility.html#aem-as-a-cloud-service-feature-incompatibility) AEMas a Cloud Service 과의 호환성을 확인합니다.

<!--
### Adobe Experience Manager 6.2 and 6.1 {#aem-specific-versions}
 
The Best Practices Analyzer tool is limited in Adobe Experience Manager 6.2 to a link that generates and downloads the CSV report.

For Adobe Experience Manager 6.1, the tool is not functional and only the HTTP interface may be used.

>[!NOTE]
>In all versions, the included Pattern Detector may run independently.
-->

## 모범 사례 분석기 보고서 해석 {#cra-report}

>[!CONTEXTUALHELP]
>id="aemcloud_bpa_interpreting"
>title="모범 사례 분석기 보고서 해석"
>abstract="UI와 CSV와 같이 BPA 보고서 출력을 볼 수 있는 두 가지 옵션이 있습니다. AEM 인스턴스에서 모범 사례 분석기 도구를 실행하면 UI 보고서가 도구 창의 결과로 표시됩니다. 보고서의 CSV 형식에는 패턴 탐지기 출력에서 생성된 정보가 포함되어 있으며 카테고리 유형, 하위 유형 및 중요도 수준별로 정렬 및 구성됩니다."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-acceleration-manager/using-cam/cam-readiness-phase.html?lang=ko-KR#analysis-report" text="Best Practices Analysis 보고서 검토"
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-pattern-detection/table-of-contents/aso.html?lang=ko-KR" text="모범 사례 분석기 보고서 범주 이해"

AEM 인스턴스에서 모범 사례 분석기 도구를 실행하면 보고서가 도구 창의 결과로 표시됩니다.

보고서의 형식은 다음과 같습니다.

* **보고서 개요**: 다음 정보를 포함하는 보고서 자체에 대한 정보:
   * **보고서 시간**: 보고서 컨텐츠가 생성되어 처음 사용할 수 있게 된 시기
   * **만료 시간**: 보고서 내용 캐시가 만료되는 시기
   * **생성 기간**: 보고서 내용 생성 프로세스의 체류 시간
   * **검색 횟수**: 보고서에 포함된 총 결과 수
* **시스템 개요**: BPA가 실행된 AEM 시스템에 대한 정보
* **카테고리 찾기**: 각 섹션에서 동일한 카테고리의 하나 이상의 발견을 처리하는 여러 섹션. 각 섹션에는 카테고리 이름, 하위 유형, 검색 횟수 및 중요도, 요약, 카테고리 설명서 링크 및 개별 검색 정보가 포함됩니다.

작업의 대략적인 우선순위를 나타내기 위해 각 검색 결과에 중요도 수준이 지정됩니다.

>[!NOTE]
>각 검색 카테고리에 대한 자세한 내용은 [패턴 탐지기 카테고리](https://experienceleague.adobe.com/docs/experience-manager-pattern-detection/table-of-contents/aso.html).

아래 표에 따라 중요도 수준을 파악하십시오.

| 중요 | 설명 |
|--- |--- |
| 정보 | 이 검색 결과는 정보용으로 제공됩니다. |
| 권고 조치 | 이 검색 결과는 잠재적으로 업그레이드 문제가 될 수 있습니다. 추가 조사가 권장됩니다. |
| 주요 | 이 검색 결과는 해결해야 하는 업그레이드 문제가 될 수 있습니다. |
| 위험 | 이 검색 결과는 기능 또는 성능 손실을 방지하기 위해 해결해야 하는 업그레이드 문제가 될 가능성이 높습니다. |

## 모범 사례 분석기 CSV 보고서 해석 {#cra-csv-report}

다음을 클릭하면 **CSV** AEM 인스턴스의 옵션인 모범 사례 분석기 보고서의 CSV 형식은 콘텐츠 캐시에서 만들어지고 브라우저에 반환됩니다. 브라우저 설정에 따라 이 보고서는 기본 이름이 인 파일로 자동 다운로드됩니다. `results.csv`.

캐시가 만료된 경우 CSV 파일을 빌드하고 다운로드하기 전에 보고서가 다시 생성됩니다.

보고서의 CSV 형식에는 패턴 탐지기 출력에서 생성된 정보가 포함되어 있으며 카테고리 유형, 하위 유형 및 중요도 수준별로 정렬 및 구성됩니다. 이 형식은 Microsoft Excel과 같은 애플리케이션에서 보고 편집하는 데 적합합니다. 진행 상황을 측정하기 위해 시간 경과에 따른 보고서를 비교할 때 유용할 수 있는 모든 검색 정보를 반복 가능한 형식으로 제공하기 위한 것입니다.

CSV 형식 보고서의 열은 다음과 같습니다.

* **코드**: 카테고리 코드
* **유형**: 카테고리 이름
* **하위 유형**: 카테고리 하위 유형
* **중요도**: 중요 수준
* **식별자**: 검색 결과의 기본 식별자
* **기타**: 검색 결과에 대한 추가 정보
* **메시지**: 검색 결과에 대해 제공된 메시지
* **추가 정보**: 카테고리에 대한 온라인 도움말에 액세스하는 데 사용할 수 있는 링크
* **컨텍스트**: 데이터를 찾기 위한 JSON 문자열

개별 검색 열에 있는 &quot;\N&quot;의 값은 제공된 데이터가 없음을 나타냅니다.

## HTTP 인터페이스 {#http-interface}

BPA는 AEM 내의 사용자 인터페이스 대신 사용할 수 있는 HTTP 인터페이스를 제공합니다. 인터페이스는 HEAD 및 GET 명령을 모두 지원합니다. BPA 보고서를 생성하고 다음 세 형식 중 하나로 반환하는 데 사용할 수 있습니다. JSON, CSV 및 탭으로 구분된 값(TSV).

HTTP 액세스에 사용할 수 있는 URL은 다음과 같습니다. `<host>` 는 BPA가 설치된 서버의 호스트 이름이며 필요한 경우 포트입니다.
* JSON 형식용 `http://<host>/apps/best-practices-analyzer/analysis/report.json`
* CSV 형식용 `http://<host>/apps/best-practices-analyzer/analysis/report.csv`
* TSV 형식용 `http://<host>/apps/best-practices-analyzer/analysis/report.tsv`

### HTTP 요청 실행 {#executing-http-request}

HTTP 인터페이스는 다양한 방법으로 사용될 수 있습니다.

한 가지 간단한 방법은 관리자로 AEM에 이미 로그인되어 있는 동일한 브라우저에서 브라우저 탭을 여는 것입니다. 브라우저 탭에 URL을 입력하고 결과를 브라우저가 표시하거나 다운로드하도록 할 수 있습니다.

다음과 같은 명령줄 도구를 사용할 수도 있습니다. `curl` 또는 `wget` 및 모든 HTTP 클라이언트 응용 프로그램 인증된 세션에서 브라우저 탭을 사용하지 않는 경우 주석의 일부로 관리 사용자 이름과 암호를 제공해야 합니다.

다음은 이 작업을 수행하는 방법의 예입니다.
`curl -u admin:admin 'http://localhost:4502/apps/best-practices-analyzer/analysis/report.csv' > report.csv`.

### 헤더 및 매개 변수 {#http-headers-and-parameters}

이 인터페이스에서는 다음 HTTP 헤더를 사용합니다.

* `Cache-Control: max-age=<seconds>`: 캐시 새로 고침 수명을 초 단위로 지정합니다. ([RFC 7234](https://tools.ietf.org/html/rfc7234#section-5.2.2.8)를 참조하십시오.)
* `Prefer: respond-async`: 서버가 비동기적으로 응답하도록 지정합니다. ([RFC 7240](https://tools.ietf.org/html/rfc7240#section-4.1)을 참조하십시오.)
* `Prefer: return=minimal`: 서버가 최소 응답을 반환하도록 지정합니다. ([RFC 7240](https://tools.ietf.org/html/rfc7240#section-4.2)을 참조하십시오.)

다음 HTTP 쿼리 매개 변수는 HTTP 헤더를 쉽게 사용할 수 없을 때 편리하게 사용할 수 있습니다.

* `max-age` (숫자, 선택 사항): 캐시 새로 고침 수명을 초 단위로 지정합니다. 이 숫자는 0보다 커야 합니다. 기본 새로 고침 수명은 86400초입니다. 이 매개 변수 또는 해당 헤더가 없으면 새 캐시를 사용하여 24시간 동안 요청을 제공하고 이 시점에서 캐시를 다시 생성해야 합니다. 사용 `max-age=0` 는 새로 생성된 캐시에 대해 0이 아닌 이전 새로 고침 수명을 사용하여 캐시를 강제로 지우고 보고서 재생성을 시작합니다.
* `respond-async` (부울, 선택 사항): 응답이 비동기식으로 제공되도록 지정합니다. 사용 `respond-async=true` 캐시가 오래된 경우 서버가 다음의 응답을 반환합니다. `202 Accepted` 캐시를 새로 고치고 보고서가 생성될 때까지 기다리지 않고 캐시를 새로 고치면 이 매개 변수는 영향을 주지 않습니다. 기본값은 입니다. `false`. 이 매개 변수 또는 해당 헤더가 없으면 서버가 동기적으로 응답하므로 상당한 시간이 필요하고 HTTP 클라이언트에 대한 최대 응답 시간을 조정해야 합니다.
* `may-refresh-cache` (부울, 선택 사항): 현재 캐시가 비어 있거나 오래된 경우 또는 곧 오래된 경우 서버가 요청에 응답하여 캐시를 새로 고칠 수 있도록 지정합니다. If `may-refresh-cache=true`또는 지정되지 않은 경우 서버는 패턴 감지기를 호출하고 캐시를 새로 고치는 백그라운드 작업을 시작할 수 있습니다. If `may-refresh-cache=false` 그러면 서버는 캐시가 비어 있거나 오래된 경우 수행되었을 새로 고침 작업을 시작하지 않으며, 이 경우 보고서가 비어 있습니다. 이미 진행 중인 새로 고침 작업은 이 매개 변수의 영향을 받지 않습니다.
* `return-minimal` (부울, 선택 사항): 서버의 응답에 JSON 형식의 진행 표시와 캐시 상태가 포함된 상태만 포함하도록 지정합니다. If `return-minimal=true`를 입력하면 응답 본문이 상태 개체로 제한됩니다. If `return-minimal=false`또는 지정되지 않은 경우 전체 응답이 제공됩니다.
* `log-findings` (부울, 선택 사항): 서버가 캐시를 처음 빌드하거나 새로 고칠 때 캐시의 내용을 기록하도록 지정합니다. 캐시의 각 검색 결과는 JSON 문자열로 기록됩니다. 이 로깅은 다음과 같은 경우에만 발생합니다. `log-findings=true` 요청이 새 캐시를 생성합니다.

HTTP 헤더와 해당 쿼리 매개 변수가 모두 있으면 쿼리 매개 변수가 우선시됩니다.

HTTP 인터페이스를 통해 보고서의 생성을 시작하는 간단한 방법은 다음 명령을 사용하는 것입니다.
`curl -u admin:admin 'http://localhost:4502/apps/best-practices-analyzer/analysis/report.json?max-age=0&respond-async=true'`.

요청이 수행된 후 보고서가 생성되도록 클라이언트가 활성 상태를 유지할 필요가 없습니다. HTTP GET 요청을 사용하는 하나의 클라이언트로 보고서 생성을 시작할 수 있으며 보고서가 생성되면 다른 클라이언트와 함께 캐시에서 보거나 AEM 사용자 인터페이스의 BPA 도구를 통해 볼 수 있습니다.

### 응답 {#http-responses}

다음 응답 값이 가능합니다.

* `200 OK`: 응답이 캐시의 새로 고침 수명 내에 생성된 패턴 탐지기 결과를 포함함을 나타냅니다.
* `202 Accepted`: 캐시가 오래된 것을 나타내는 데 사용됩니다. 날짜 `respond-async=true` 및 `may-refresh-cache=true` 이 응답은 새로 고침 작업이 진행 중임을 나타냅니다. 날짜 `may-refresh-cache=false` 이 응답은 캐시가 오래된 상태임을 나타냅니다.
* `400 Bad Request`: 요청에 오류가 있음을 나타냅니다. 문제 세부 정보 형식의 메시지(참조) [RFC 7807](https://tools.ietf.org/html/rfc7807))에서 자세한 내용을 확인할 수 있습니다.
* `401 Unauthorized`: 요청이 승인되지 않았음을 나타냅니다.
* `500 Internal Server Error`: 내부 서버 오류가 발생했음을 나타냅니다. 자세한 내용은 문제 세부 정보 형식의 메시지를 참조하십시오.
* `503 Service Unavailable`: 서버가 다른 응답으로 사용 중이어서 이 요청을 적시에 처리할 수 없음을 나타냅니다. 이는 동기 요청이 수행된 경우에만 발생합니다. 자세한 내용은 문제 세부 정보 형식의 메시지를 참조하십시오.

## 관리자 정보

### 캐시 새로 고침 조정 {#cache-adjustment}

기본 BPA 캐시 수명은 24시간입니다. 보고서를 새로 고치고 캐시를 다시 생성하는 옵션과 함께 AEM 인스턴스와 HTTP 인터페이스 모두에서 이 기본값은 BPA의 대부분의 사용에 적절할 수 있습니다. 보고서 생성 시간이 AEM 인스턴스에 대해 특히 긴 경우 보고서 재생성을 최소화하기 위해 캐시 수명을 조정할 수 있습니다.

캐시 수명 값은 다음 저장소 노드의 `maxCacheAge` 속성으로 저장됩니다.
`/apps/best-practices-analyzer/content/BestPracticesReport/jcr:content`

이 속성의 값은 캐시 수명(초)입니다. 관리자는 CRX/DE Lite를 사용하여 캐시 수명을 조정할 수 있습니다.

### AEM 6.1에 설치 {#installing-on-aem61}

BPA는 이름이 인 시스템 서비스 사용자 계정을 사용합니다. `repository-reader-service` 패턴 감지기를 실행합니다. 이 계정은 AEM 6.2 이상에서 사용할 수 있습니다. AEM 6.1에서 이 계정을 만들어야 합니다 *이전* 다음 단계를 수행하여 BPA 설치:

1. 사용자를 만들려면 [새 서비스 사용자 만들기](https://experienceleague.adobe.com/docs/experience-manager-65/administering/security/security-service-users.html#creating-a-new-service-user)의 지침을 따르십시오. UserID를 `repository-reader-service`로 설정하고 중간 경로를 비워 둔 다음 녹색 확인 표시를 클릭합니다.

2. [사용자 및 그룹 관리](https://experienceleague.adobe.com/docs/experience-manager-65/administering/security/security.html#managing-users-and-groups)의 지침, 특히 그룹에 사용자 추가 지침을 따라 `repository-reader-service` 사용자를 `administrators` 그룹에 추가합니다.

3. 소스 AEM 인스턴스에서 패키지 관리자를 통해 BPA 패키지를 설치합니다. (`repository-reader-service` 시스템 서비스 사용자에 대한 ServiceUserMapper 구성에 필요한 구성 수정을 추가합니다.)
