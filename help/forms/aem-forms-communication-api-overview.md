---
title: AEM Forms Communications API - 개요
description: 인증 방법 및 전체 API 참조를 포함한 AEM Forms Communications API 개요
role: Developer, User
feature: Adaptive Forms, APIs & Integrations
hide: true
hidefromtoc: true
index: false
source-git-commit: 580d6505ffdf25f7bfb3a3a84f054dcf76c05cdd
workflow-type: tm+mt
source-wordcount: '1098'
ht-degree: 4%

---


# AEM Forms Communications API - 개요

AEM Forms Communications API는 기업이 문서 워크플로를 자동화할 수 있도록 설계된 포괄적인 클라우드 기반 API 제품군을 제공합니다.

AEM Forms API는 두 개의 기본 콘솔을 통해 구조화되고 액세스됩니다.

* [Adobe Developer Console(ADC)](https://developer.adobe.com/developer-console/) - Adobe Developer Console은 Adobe API, 이벤트, 런타임 및 App Builder의 게이트웨이입니다.

* [AEM Developer Console](https://experienceleague.adobe.com/en/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/developer-console) - AEM Developer Console은 AEM as a Cloud Service 환경을 디버깅하고 검사하는 도구를 제공합니다.

각 콘솔에서는 문서 처리, 생성, 변환, 암호화 및 통신 작업을 위해 다양한 API 및 서비스에 액세스할 수 있습니다. API는 다양한 [인증 방법](#authentication-methods)을 지원합니다.

## 인증 방법

API는 애플리케이션과 Adobe 서비스 간의 안전한 통합을 위해 여러 인증 방법을 지원합니다.

| 측면 | OAuth 서버 간(권장) | JWT (JSON 웹 토큰) |
|-------------|------------------------------------------|---------------------------|
| 설명 | 사용자 인터랙션 없이 API 액세스를 위한 현대적이고 안전한 방법입니다. | 액세스를 위해 서명된 토큰을 사용하는 이전 방법입니다. |
| 설정 위치 | Adobe Developer Console 및 AEM Developer Console | AEM Developer Console 전용 |
| 보안 | 높음 - 클라이언트 자격 증명 및 범위를 사용합니다. | 중재 - 키 관리에 따라 다름 |
| 확장성 | 백엔드 통합을 위한 뛰어난 확장성 | 제한적, 기존 용도에 적합 |
| 토큰 관리 | 자동 생성 및 갱신 | 수동 토큰 서명 및 순환 |
| 상태 | 추천 | 사용되지 않음 |


>[!NOTE]
>
> :-에 대해 자세히 알아보려면 아래 링크를 클릭하십시오.
> 
> * [OAuth 서버 간(권장)](/help/forms/oauth-api-authetication.md)
> * [JWT(JSON 웹 토큰)](/help/forms/jwt-api-authentication.md)

<!--### Execution Models

The following table highlights the key differences between Synchronous (On-Demand) and Asynchronous (Batch) execution models supported in AEM Forms Communications APIs:

| Feature | Synchronous (On-Demand) | Batch (Asynchronous) |
|---------|-------------------------|----------------------|
| **Execution Model** | Real-time, immediate | Queued, scheduled |
| **Response Time** | Seconds | Minutes to hours |
| **Volume** | Single or few documents | Hundreds to thousands |
| **Testing Environment** | Author & Publish | Author Only |
| **Use Case** | User-triggered actions | Scheduled bulk operations |
| **Console Access** | ADC & AEM Developer Console | AEM Developer Console Only |-->

## API 분류 개요

모든 AEM Forms API는 두 가지 주요 부분으로 나뉘어져 있습니다.

* [적응형 양식 배달 및 런타임 API](https://developer-stage.adobe.com/experience-cloud/experience-manager-apis/api/stable/forms/)

* [AEM Forms 통신 API](#aem-forms-communications-apis)

| 세부 사항 | 적응형 양식 전달 및 런타임 API | 통신 API |
|--------------|----------------------------|--------------------------|
| 목적 | 적응형 양식 전달 및 런타임 작업 처리 | 문서 생성 및 조작 |
| 사용 사례 | - 양식 렌더링<br>- 데이터 미리 채우기<br>- 양식 제출<br>- 초안 관리 | - PDF 생성<br>- 문서 병합<br>- 일괄 처리<br>- 인쇄 작업 |
| 인증 방법 | OAuth 서버 간/사용자 인증 방법을 지원합니다. | 는 OAuth 서버 간 인증만 지원합니다. |

### AEM Forms Communications API

커뮤니케이션 API는 문서 중심 작업을 위한 주요 요소입니다.

아래 표에는 모든 [AEM Forms Communications API](https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/api/)가 지원되는 인증 방법 및 실행 모델과 함께 나열되어 있습니다.

#### 문서 생성 API


| API 엔드포인트 | 설명 | 실행 모델 | 인증 방법 |
| ----- | ------ |------- | ------ |
| [/adobe/forms/batch/output/config](https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/api/output-batch/#tag/Batch-Configuration/operation/CreateBatchConfig) | 문서 생성 작업을 위한 새 일괄 처리 구성을 만듭니다. | 비동기/일괄 처리 | 서버에 대한 [OAuth 서버](/help/forms/oauth-api-authetication.md)/[JWT](/help/forms/jwt-api-authentication.md) |
| [/adobe/forms/batch/output/config/{configName}](https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/api/output-batch/#tag/Batch-Configuration/operation/GetBatchConfigbyName) | 특정 일괄 처리 구성의 세부 정보를 검색합니다. | 비동기/일괄 처리 | 서버에 대한 [OAuth 서버](/help/forms/oauth-api-authetication.md)/[JWT](/help/forms/jwt-api-authentication.md) |
| [/adobe/forms/batch/output/config/configs](https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/api/output-batch/#tag/Batch-Configuration/operation/GetAllBatchConfigs) | 사용 가능한 모든 일괄 처리 구성 목록을 반환합니다. | 비동기/일괄 처리 | 서버에 대한 [OAuth 서버](/help/forms/oauth-api-authetication.md)/[JWT](/help/forms/jwt-api-authentication.md) |
| [/adobe/forms/batch/output/config/{configName}/execution](https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/api/output-batch/#tag/Batch-Execution/operation/StartBatchRun) | 구성을 사용하여 일괄 출력 생성 실행을 시작합니다. | 비동기/일괄 처리 | 서버에 대한 [OAuth 서버](/help/forms/oauth-api-authetication.md)/[JWT](/help/forms/jwt-api-authentication.md) |
| [/adobe/forms/batch/output/config/{configName}/execution/{executionId}](https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/api/output-batch/#tag/Batch-Execution/operation/GetBatchRunInstanceState) | 일괄 처리 작업의 실행 상태를 검색합니다. | 비동기/일괄 처리 | 서버에 대한 [OAuth 서버](/help/forms/oauth-api-authetication.md)/[JWT](/help/forms/jwt-api-authentication.md) |
| [/adobe/forms/batch/output/config/{configName}/execution](https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/api/output-batch/#tag/Batch-Execution/operation/GetAllRunningInstancesForBatch) | 특정 일괄 처리 구성에 대해 실행 중인 모든 인스턴스를 나열합니다. | 비동기/일괄 처리 | 서버에 대한 [OAuth 서버](/help/forms/oauth-api-authetication.md)/[JWT](/help/forms/jwt-api-authentication.md) |
| [/adobe/forms/doc/v1/generatePDFOutput](https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/api/output-sync/#tag/Communications-Services/paths/~1adobe~1forms~1doc~1v1~1generatePDFOutput/post) | 템플릿 및 데이터를 기반으로 동기적으로 PDF 출력을 생성합니다. | 동기 | 서버에 대한 [OAuth 서버](/help/forms/oauth-api-authetication.md)/[JWT](/help/forms/jwt-api-authentication.md) |
| [/adobe/forms/doc/v1/generatePrintedOutput](https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/api/output-sync/#tag/Batch-Execution/operation/GetAllRunningInstancesForBatch) | 인쇄가 가능한 출력 형식(예: PCL, PostScript)을 생성합니다. | 동기 | 서버에 대한 [OAuth 서버](/help/forms/oauth-api-authetication.md)/[JWT](/help/forms/jwt-api-authentication.md) |
| [/adobe/forms/doc/v1/generate/afp](https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/api/output-sync/#tag/Communications-Services/paths/~1adobe~1forms~1doc~1v1~1generate~1afp/post) | 대용량 인쇄를 위해 AFP 출력을 생성합니다. | 동기 | 서버에 대한 [OAuth 서버](/help/forms/oauth-api-authetication.md)/[JWT](/help/forms/jwt-api-authentication.md) |
| [/adobe/document/generate/pdfform](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/document/#operation/renderPDFForm) | 병합된 데이터로 PDF 양식(XFA/XDP)을 렌더링합니다. | 동기 | 서버에 대한 [OAuth 서버](/help/forms/oauth-api-authetication.md) |
| [/adobe/document/generate/pdfform/jobs/{id}/status](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/document/#operation/renderPDFFormJobStatus) | PDF 양식 생성 작업의 상태를 검색합니다. | 동기 | 서버에 대한 [OAuth 서버](/help/forms/oauth-api-authetication.md) |
| [/adobe/document/generate/pdfform/jobs/{id}/result](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/document/#operation/renderPDFFormJobResult) | 완료된 PDF 양식 작업의 출력/결과를 가져옵니다. | 동기 | 서버에 대한 [OAuth 서버](/help/forms/oauth-api-authetication.md) |


#### 문서 조작 API

| API 엔드포인트 | 설명 | 실행 모델 | 인증 방법 |
| ------------------ | ---------------- | ----------| ---------- |
| [/adobe/forms/assembler/ddx/invoke](https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/api/assembler-sync/#tag/DDX-execution/operation/InvokeDDX) | DDX 명령을 실행하여 PDF를 결합, 분할 또는 조작합니다. | 동기 | 서버에 대한 [OAuth 서버](/help/forms/oauth-api-authetication.md)/[JWT](/help/forms/jwt-api-authentication.md) |
| [/adobe/forms/assembler/pdfa/convert](https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/api/assembler-sync/#tag/Document-conversion/operation/ConvertToPDFA) | PDF 문서를 PDF/A 형식으로 변환합니다. | 동기 | 서버에 대한 [OAuth 서버](/help/forms/oauth-api-authetication.md)/[JWT](/help/forms/jwt-api-authentication.md) |
| [/adobe/forms/assembler/pdfa/validate](https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/api/assembler-sync/#tag/Document-validation/operation/CheckIsPDFA) | PDF이 PDF/A 표준을 준수하는지 확인합니다. | 동기 | 서버에 대한 [OAuth 서버](/help/forms/oauth-api-authetication.md)/[JWT](/help/forms/jwt-api-authentication.md) |

#### 문서 변환 API

| API 엔드포인트 | 설명 | 실행 모델 | 인증 방법 |
|--------- | -------|---------|----------------------|
| [/adobe/document/convert/pdftoxdp](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/document/#tag/Document-Conversion/paths/~1convert~1pdftoxdp/post) | PDF 양식을 XDP 형식으로 변환합니다. | 동기 | 서버에 대한 [OAuth 서버](/help/forms/oauth-api-authetication.md) |

#### 문서 추출 API

| API 엔드포인트 | 설명 | 실행 모델 | 인증 방법 |
|---------| -------|---------|----------------------|
| [/adobe/forms/doc/v1/extract/pdfproperties](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/document/#tag/Document-Extraction/paths/~1extract~1pdfproperties/post) | PDF에서 속성 및 구조 정보를 추출합니다. | 동기 | 서버에 대한 [OAuth 서버](/help/forms/oauth-api-authetication.md) |
| [/adobe/forms/doc/v1/extract/usagerights](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/document/#operation/extractUsageRights) | PDF에 포함된 사용 권한을 추출합니다. | 동기 | 서버에 대한 [OAuth 서버](/help/forms/oauth-api-authetication.md) |
| [/adobe/forms/doc/v1/extract/metadata](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/document/#tag/Document-Extraction/paths/~1extract~1metadata/post) | 제목, 작성자 및 키워드와 같은 메타데이터를 추출합니다. | 동기 | 서버에 대한 [OAuth 서버](/help/forms/oauth-api-authetication.md) |
| [/adobe/forms/doc/v1/extract/data](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/document/#operation/exportData) | PDF forms에서 양식 데이터(XML/JSON)를 추출합니다. | 동기 | 서버에 대한 [OAuth 서버](/help/forms/oauth-api-authetication.md) |
| [/adobe/document/extract/security](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/document/#tag/Document-Extraction/paths/~1extract~1security/post) | 권한 및 암호화와 같은 보안 설정을 추출합니다. | 동기 | 서버에 대한 [OAuth 서버](/help/forms/oauth-api-authetication.md) |

#### 문서 변환 API


| API 엔드포인트 | 설명 | 실행 모델 | 인증 방법 |
|--------|---------|---------|----------------------|
| [/adobe/document/transform/metadata](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/document/#tag/Document-Transformation/paths/~1transform~1metadata/post) | PDF 문서에서 메타데이터를 업데이트하거나 추가합니다. | 동기 | 서버에 대한 [OAuth 서버](/help/forms/oauth-api-authetication.md) |
| [/adobe/document/field/signature/add](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/document/#tag/Document-Transformation/paths/~1field~1signature~1add/post) | PDF에 디지털 서명 필드를 추가합니다. | 동기 | 서버에 대한 [OAuth 서버](/help/forms/oauth-api-authetication.md) |
| [/adobe/document/field/signature/clear](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/document/#tag/Document-Transformation/paths/~1field~1signature~1clear/post) | 서명 필드의 내용을 지웁니다. | 동기 | 서버에 대한 [OAuth 서버](/help/forms/oauth-api-authetication.md) |
| [/adobe/document/field/signature/remove](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/document/#tag/Document-Transformation/paths/~1field~1signature~1remove/post) | PDF에서 서명 필드를 제거합니다. | 동기 | 서버에 대한 [OAuth 서버](/help/forms/oauth-api-authetication.md) |

#### 문서 Assurance API

| API 엔드포인트 | 설명 | 실행 모델 | 인증 방법 |
|---------|-------|---------|----------------------|
| [/adobe/document/assure/usagerights](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/document/#operation/applyUsageRights) | PDF에 사용 권한(예: 댓글, 채우기, 서명)을 적용합니다. | 동기 | 서버에 대한 [OAuth 서버](/help/forms/oauth-api-authetication.md) |
| [/adobe/document/assure/encrypt](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/document/#tag/Document-Assurance/paths/~1assure~1encrypt/post) | 암호 또는 인증서 보안으로 PDF을 암호화합니다. | 동기 | 서버에 대한 [OAuth 서버](/help/forms/oauth-api-authetication.md) |
| [/adobe/document/assure/decrypt](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/document/#tag/Document-Assurance/paths/~1assure~1decrypt/post) | 보안 PDF 문서의 암호를 해독합니다. | 동기 | 서버에 대한 [OAuth 서버](/help/forms/oauth-api-authetication.md) |
| [/adobe/document/assure/sign](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/document/#tag/Document-Assurance/paths/~1assure~1sign/post) | PDF 문서에 디지털 서명합니다. | 동기 | 서버에 대한 [OAuth 서버](/help/forms/oauth-api-authetication.md) |
| [/adobe/document/assure/certify](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/document/#tag/Document-Assurance/paths/~1assure~1certify/post) | 디지털 인증서로 PDF을 인증합니다. | 동기 | 서버에 대한 [OAuth 서버](/help/forms/oauth-api-authetication.md) |


## 다음 단계

동기식(온디맨드) 및 비동기식(일괄 처리) Forms Communications API에 대한 환경을 설정하는 방법에 대해 알아봅니다.

<!-- START CARDS HTML - DO NOT MODIFY BY HAND -->
<div class="columns">
    <!-- Synchronous APIs Card -->
    <div class="column is-half-tablet is-half-desktop is-one-third-widescreen" aria-label="AEM Forms Communications APIs - Synchronous">
        <div class="card" style="height: 100%; display: flex; flex-direction: column;">
            <div class="card-image">
                <figure class="image x-is-16by9">
                    <a href="/help/forms/aem-forms-cloud-service-communications-on-demand-processing.md" title="동기 API" target="_self" rel="referrer">
                        <img class="is-bordered-r-small" src="/help/forms/assets/sync-api.png" alt="동기 API"
                             style="width: 100%; aspect-ratio: 16 / 9; object-fit: cover; overflow: hidden; display: block; margin: auto;">
                    </a>
                </figure>
            </div>
            <div class="card-content is-padded-small" style="display: flex; flex-direction: column; flex-grow: 1; justify-content: space-between;">
                <div class="top-card-content">
                    <p class="headline is-size-6 has-text-weight-bold">
                        <a href="/help/forms/aem-forms-cloud-service-communications-on-demand-processing.md" target="_self" rel="referrer" title="AEM Forms Communications API - 동기">AEM Forms Communications API - 동기</a>
                    </p>
                    <p class="is-size-6">문서를 즉시 생성하거나 처리하는 동기식(온디맨드) Forms Communications API용 환경을 설정하는 방법에 대해 알아봅니다. </p>
                </div>
                <a href="/help/forms/aem-forms-cloud-service-communications-on-demand-processing.md" target="_self" rel="referrer" class="spectrum-Button spectrum-Button--outline spectrum-Button--primary spectrum-Button--sizeM" style="align-self: flex-start; margin-top: 1rem;">
                    <span class="spectrum-Button-label has-no-wrap has-text-weight-bold">자세히 알아보기</span>
                </a>
            </div>
        </div>
    </div>
    <!-- Asynchronous APIs Card -->
    <div class="column is-half-tablet is-half-desktop is-one-third-widescreen" aria-label="AEM Forms Communications APIs - Asynchronous">
        <div class="card" style="height: 100%; display: flex; flex-direction: column;">
            <div class="card-image">
                <figure class="image x-is-16by9">
                    <a href="/help/forms/aem-forms-cloud-service-communications-batch-processing.md" title="AEM Forms Communications API - 비동기" target="_self" rel="referrer">
                        <img class="is-bordered-r-small" src="/help/forms/assets/async-api.png" alt="비동기 API"
                             style="width: 100%; aspect-ratio: 16 / 9; object-fit: cover; overflow: hidden; display: block; margin: auto;">
                    </a>
                </figure>
            </div>
            <div class="card-content is-padded-small" style="display: flex; flex-direction: column; flex-grow: 1; justify-content: space-between;">
                <div class="top-card-content">
                    <p class="headline is-size-6 has-text-weight-bold">
                        <a href="/help/forms/aem-forms-cloud-service-communications-batch-processing.md" target="_self" rel="referrer" title="비동기 API">AEM Forms Communications API - 비동기(일괄 처리)</a>
                    </p>
                    <p class="is-size-6">예약된 방식으로 여러 문서를 생성하거나 처리하는 비동기(일괄 처리) Forms Communications API에 대한 환경을 설정하는 방법에 대해 알아봅니다.</p>
                </div>
                <a href="/help/forms/aem-forms-cloud-service-communications-batch-processing.md" target="_self" rel="referrer" class="spectrum-Button spectrum-Button--outline spectrum-Button--primary spectrum-Button--sizeM" style="align-self: flex-start; margin-top: 1rem;">
                    <span class="spectrum-Button-label has-no-wrap has-text-weight-bold">자세히 알아보기</span>
                </a>
            </div>
        </div>
    </div>
</div>
<!-- END CARDS HTML - DO NOT MODIFY BY HAND -->


>[!MORELIKETHIS]
>
>* [AEM Forms as a Cloud Service Communications 소개](/help/forms/aem-forms-cloud-service-communications-introduction.md)
>* 적응형 Forms 및 통신 API를 위한 [AEM Forms as a Cloud Service 아키텍처](/help/forms/aem-forms-cloud-service-architecture.md)
>* [통신 처리 - 동기 API](/help/forms/aem-forms-cloud-service-communications.md)
>* [통신 처리 - 일괄 처리 API](/help/forms/aem-forms-cloud-service-communications-batch-processing.md)
>* [통신 처리 - 온디맨드 API](/help/forms/aem-forms-cloud-service-communications-on-demand-processing.md)