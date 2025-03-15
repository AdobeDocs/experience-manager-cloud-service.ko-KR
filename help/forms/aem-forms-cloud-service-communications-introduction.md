---
title: AEM Forms as a Cloud Service 통신 API
description: 클라우드에서 AEM Forms Communication API를 사용하여 문서 생성, 조작 및 보안
Keywords: document generation, PDF manipulation, document security, batch processing, document conversion, PDF/A compliance
feature: Adaptive Forms, APIs & Integrations, Document Services
role: Admin, Developer, User
exl-id: b6f05b2f-5665-4992-8689-d566351d54f1
source-git-commit: a9eed5b6219163e721d81c9d77a31604666a2ac5
workflow-type: tm+mt
source-wordcount: '1432'
ht-degree: 3%

---


# AEM Forms as a Cloud Service 통신 API {#communications-apis-overview}

> **버전 가용성**
>
> * **AEM 6.5**: [AEM 문서 서비스 개요](https://experienceleague.adobe.com/docs/experience-manager-65/forms/use-document-services/overview-aem-document-services.html)
> * **AEM as a Cloud Service**: 이 문서

## 소개

AEM Forms as a Cloud Service의 커뮤니케이션 API를 통해 비즈니스 요구 사항에 맞게 브랜드에서 승인하고 개인화된 표준화된 문서를 만들 수 있습니다. 이러한 강력한 API를 사용하면 온디맨드 프로세스이든, 대용량 배치 프로세스에서든 프로그래밍 방식으로 문서를 생성하고, 조작하고, 보호할 수 있습니다.


### 주요 이점

* **문서 생성 간소화** - 템플릿을 고객 데이터와 병합하여 개인화된 문서를 만듭니다.
* **강력한 문서 조작** - PDF 문서를 프로그래밍 방식으로 결합, 재배열 및 유효성 검사
* **유연한 배포 옵션** - 대기 시간이 짧은 요구 시 온디맨드 API를 사용하거나 처리량이 많은 작업을 위한 일괄 처리 API를 사용합니다.
* **향상된 보안** - 디지털 서명, 인증 및 암호화를 적용하여 중요한 문서를 보호합니다.
* **클라우드 기반 아키텍처** - 유지 관리 부담 없이 확장 가능하고 안전한 클라우드 인프라 활용

## 주요 기능

커뮤니케이션 API는 다음 기능 영역으로 구성된 포괄적인 문서 처리 기능 세트를 제공합니다.


| 문서 생성 | 문서 조작 | 문서 추출 | 문서 변환 | 문서 Assurance |
|---------------------|----------------------|---------------------|---------------------|-------------------|
| 템플릿을 PDF 및 인쇄 형식을 비롯한 다양한 형식의 데이터와 병합하여 개인화된 문서를 생성합니다. | PDF 문서를 프로그래밍 방식으로 결합, 재배열 및 확인하여 새 문서 패키지를 만듭니다. | 추가 처리를 위해 PDF 문서에서 속성, 메타데이터 및 컨텐츠를 추출합니다. | 아카이브 요구 사항에 대한 PDF/A 규정 준수 검증을 포함하여 문서를 형식 간에 변환할 수 있습니다. | 디지털 서명, 인증 및 암호화를 적용하여 문서를 보호하고 보호합니다. |

## 문서 생성

커뮤니케이션 문서 생성 API는 템플릿(XFA 또는 PDF)을 고객 데이터(XML)와 결합하여 PDF 및 다양한 인쇄 형식(PS, PCL, DPL, IPL, ZPL)으로 개인화된 문서를 생성합니다.

### 문서 생성 작동 방식

일반적인 워크플로우는 다음과 같습니다.

1. [Designer](use-forms-designer.md)을(를) 사용하여 템플릿 만들기
2. 템플릿을 채울 XML 데이터 준비
3. 통신 API를 사용하여 템플릿과 데이터 병합
4. 원하는 형식으로 출력 문서 생성

![통신 문서 생성 워크플로](assets/communicaions-workflow.png)

### PDF 문서 만들기

문서 생성 API를 사용하면 XML 데이터를 양식 템플릿과 병합하여 비대화형 PDF 문서를 만들 수 있습니다.

![PDF 문서 만들기](assets/outPutPDF_popup.png)

생성된 PDF를 다운로드를 통해 사용자에게 제공하거나 저장소에 저장하거나 필요에 따라 Azure Blob Storage에 업로드할 수 있습니다.

<span class="preview">생성된 PDF를 Azure Blob 저장소에 업로드하는 작업은 [얼리 어답터 프로그램](/help/forms/early-access-ea-features.md)을 통해 사용할 수 있습니다. 가입하려면 공식 이메일에서 aem-forms-ea@adobe.com으로 연락하십시오.</span>

### 인쇄 형식 문서 만들기

다음과 같은 인쇄 형식의 문서를 생성합니다.
* PostScript (PS)
* PCL(프린터 명령 언어)
* ZPL(Zebra Printing Language)

이러한 형식은 대량 인쇄 작업 및 특수 인쇄 요구에 이상적입니다.

### 여러 문서에 대한 일괄 처리

일괄 처리 API를 사용하여 대량의 문서를 효율적으로 처리:

![일괄 처리 워크플로](assets/ou_OutputBatchMany_popup.png)

일괄 처리를 통해 다음을 수행할 수 있습니다.

* XML 데이터 소스의 각 레코드에 대해 별도의 문서 생성
* 성능 향상을 위해 문서를 비동기적으로 처리
* 배치 프로세스에 대한 다양한 전환 매개변수 구성

## 문서 조작

문서 조작 API를 사용하면 PDF 문서를 프로그래밍 방식으로 결합, 재배열 및 변환할 수 있습니다.

### 문서 어셈블리

여러 PDF 또는 XDP 문서를 단일 통합 문서로 결합:

![여러 PDF 문서에서 간단한 PDF 문서 어셈블](assets/as_document_assembly.png)

문서 어셈블리 기능은 다음과 같습니다.
* 여러 소스에서 간단한 PDF 문서 만들기
* PDF 포트폴리오 작성
* 암호화된 문서 어셈블
* 법적 문서에 대한 베이츠 번호 추가
* 인터랙티브 양식 병합 및 어셈블

### 문서 디스어셈블리

대형 PDF 문서를 보다 작고 관리하기 쉬운 구성 요소로 나눕니다.

![책갈피를 기반으로 소스 문서를 여러 문서로 나누기](assets/as_intro_pdfsfrombookmarks.png)

문서 디스어셈블리를 사용하면 다음 작업을 수행할 수 있습니다.
* 소스 문서에서 특정 페이지 추출
* 책갈피를 기준으로 문서 나누기
* 대규모 컴파일에서 논리 문서 집합 만들기

>[!NOTE]
>
> AEM Forms에는 PDF 파일과 원활하게 통합되는 많은 내장 글꼴이 포함되어 있습니다. 지원되는 글꼴의 전체 목록을 보려면 [여기를 클릭하세요](/help/forms/supported-out-of-the-box-fonts.md).

## 문서 추출

<span class="preview">문서 추출은 [얼리어답터 프로그램](/help/forms/early-access-ea-features.md)을 통해 사용할 수 있습니다. 가입하려면 공식 이메일에서 aem-forms-ea@adobe.com으로 연락하십시오.</span>

문서 추출 API를 사용하면 다음을 포함하여 PDF 문서에서 정보를 검색할 수 있습니다.

* 문서 속성(입력 가능한 양식인지, 첨부 파일이 있는지 여부 등)
* 사용 권한 및 권한
* Adobe 확장 가능한 메타데이터 플랫폼(XMP)을 사용한 메타데이터 정보

이 기능은 문서 관리 시스템, 아카이빙 솔루션 및 워크플로 자동화에 특히 유용합니다.

## 문서 변환

### PDF/A 전환 및 유효성 검사

장기 보관 목적으로 표준 PDF 문서를 PDF/A 형식으로 변환합니다.

* PDF/A-1a, 1b, 2a, 2b, 3a 및 3b 규정 준수 표준 지원
* PDF/A 규정 준수 여부 확인
* 임베드된 글꼴 및 압축 해제된 콘텐츠를 사용하여 문서 무결성 유지

### PDF에서 XDP로 전환

<span class="preview">PDF에서 XDP로 전환은 [얼리 어답터 프로그램](/help/forms/early-access-ea-features.md)을 통해 사용할 수 있습니다. 가입하려면 공식 이메일에서 aem-forms-ea@adobe.com으로 연락하십시오.</span>

템플릿 편집 및 재사용을 위해 XFA 스트림이 포함된 PDF 문서를 XDP 형식으로 변환합니다.

## 문서 Assurance {#doc-assurance}

Document Assurance에는 Signature 및 Encryption API가 포함되어 있어 문서의 수명주기 전반에 걸쳐 문서를 보호할 수 있습니다.

### 서명 API

디지털 서명 및 인증을 통해 PDF 문서를 보호합니다.

* 표시 또는 보이지 않는 서명 필드 추가
* 서명 필드의 디지털 서명
* 무결성을 위해 문서 인증
* 문서에서 서명 제거
* 문서에서 서명 필드 삭제

<span class="preview">서명 제거 및 서명 필드 삭제는 [얼리 어답터 프로그램](/help/forms/early-access-ea-features.md)을 통해 사용할 수 있습니다. 가입하려면 공식 이메일에서 aem-forms-ea@adobe.com으로 연락하십시오.</span>

### 암호화 API

암호화를 사용하여 문서 콘텐츠 보안:

* 암호로 PDF 문서 암호화
* 암호 기반 암호화 제거
* 문서에 적용되는 보안 유형 결정
* 보호된 문서에서 보안 정보 검색

### 문서 유틸리티 {#doc-utility}

문서 유틸리티는 PDF 문서 작업을 위한 추가 기능을 제공합니다.

#### 사용 권한 API(Reader 확장)

<span class="preview">사용 권한(Reader 확장)은 [얼리어답터 프로그램](/help/forms/early-access-ea-features.md)을 통해 사용할 수 있습니다. 가입하려면 공식 이메일에서 aem-forms-ea@adobe.com으로 연락하십시오.</span>

PDF 문서에 사용 권한을 추가하여 다음과 같은 기능을 활성화하여 Adobe Reader의 기능을 확장합니다.

* 양식 작성 및 저장
* 주석 및 주석 추가
* 디지털 서명
* 첨부 파일
* 양식 데이터 가져오기/내보내기
* 웹 서비스 및 데이터베이스 액세스

사용 가능한 사용 권한은 다음과 같습니다.

* **양식 상호 작용**: 양식 채우기, 양식 데이터 가져오기/내보내기, 동적 양식 필드/페이지
* **주석**: 댓글(온라인 및 오프라인), 디지털 서명
* **문서 처리**: 포함된 파일, 독립 실행형 제출, 바코드 디코딩
* **온라인 서비스**: 온라인 Forms, 웹 서비스 액세스

## 커뮤니케이션 API 유형 {#types}

커뮤니케이션은 다양한 사용 사례에 맞게 두 가지 유형의 API를 제공합니다.

### 동기 API

**최적의 대상**: 온디맨드, 짧은 대기 시간, 단일 문서 생성
**사용 사례**: 사용자 트리거된 문서 생성, 대화형 응용 프로그램
**설명서**: [동기 API 참조](https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/)

### 일괄 처리 API(비동기)

**최적의 대상**: 예약됨, 처리량이 많음, 여러 문서 생성
**사용 사례**: 월별 명세서, 청구서, 알림, 예약된 보고서
**설명서**: [일괄 처리 API 참조](https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/)

## 통신 API 시작하기

### 온보딩 프로세스

커뮤니케이션은 Forms as a Cloud Service 사용자를 위한 독립 실행형 모듈 또는 추가 기능으로 사용할 수 있습니다.

1. 액세스 권한을 요청하려면 Adobe Sales 또는 Adobe 담당자에게 문의하십시오
2. Adobe이 조직에 대한 액세스 권한을 활성화하고 관리자 권한을 부여합니다.
3. 그런 다음 관리자는 조직의 개발자에게 액세스 권한을 부여할 수 있습니다

### 사용자 환경에서 커뮤니케이션 활성화

Forms as a Cloud Service 환경에 대한 커뮤니케이션을 활성화하려면 다음 단계를 따르십시오.

1. Cloud Manager에 로그인하고 AEM Forms as a Cloud Service 인스턴스를 엽니다
2. 프로그램 편집 옵션을 열고 솔루션 및 추가 기능 탭으로 이동합니다.
3. **[!UICONTROL Forms - 통신]** 옵션 선택

   ![커뮤니케이션](assets/communications.png)

   **[!UICONTROL Forms - 디지털 등록]**&#x200B;을 이미 사용하도록 설정한 경우 대신 **[!UICONTROL Forms - 통신 추가 기능]** 옵션을 선택하십시오.

   ![추가 기능](assets/add-on.png)

4. **[!UICONTROL 업데이트]** 클릭
5. 빌드 파이프라인 실행 - 성공적으로 완료되면 통신 API가 활성화됩니다

>[!NOTE]
>
> 문서 조작 API를 사용하려면 [Dispatcher 구성](setup-local-development-environment.md#forms-specific-rules-to-dispatcher)에 다음 규칙을 추가하십시오.
>
> `# Allow Forms Doc Generation requests`
> `/0062 { /type "allow" /method "POST" /url "/adobe/forms/assembler/*" }`

## API 참조 설명서 {#api-reference}

커뮤니케이션 API는 몇 가지 기능 카테고리로 구성되며 각각 자세한 참조 설명서가 제공됩니다. 이러한 API 참조는 끝점, 매개 변수, 요청/응답 형식 및 인증 요구 사항에 대한 포괄적인 정보를 제공합니다.

### 문서 생성 API

| API | 설명 | 참조 링크 |
|-----|-------------|----------------|
| 문서 생성 - 동기 | 대화형 시나리오에 대해 대기 시간이 짧은 온디맨드 문서 생성 | [API 참조](https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/api/output-sync/) |
| 문서 생성 - 일괄 처리 | 예약된 작업을 위해 많은 양의 문서를 비동기적으로 처리 | [API 참조](https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/api/output-batch/) |

### 문서 조작 API

| API | 설명 | 참조 링크 |
|-----|-------------|----------------|
| 문서 조작 - 동기 | DDX 명령을 사용하여 PDF 문서를 결합, 분할 및 변형합니다. | [API 참조](https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/api/assembler-sync/) |

### 문서 Assurance API

| API | 설명 | 참조 링크 |
|-----|-------------|----------------|
| DocAssurance - 동기 | 디지털 서명, 인증, 암호화 및 리더 확장 적용 | [API 참조](https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/api/docassurance/) |

### 일반 API 매개 변수

각 API 카테고리에는 특정 매개 변수가 있지만 몇 가지 일반적인 매개 변수에는 다음이 포함됩니다.

#### 문서 생성 매개 변수

| 매개변수 | 유형 | 필수 | 설명 |
|-----------|------|----------|-------------|
| `template` | 문자열 | 예 | XDP 또는 PDF 템플릿 파일 경로 |
| `data` | 문자열 | 아니요 | 템플릿과 병합할 XML 데이터 |
| `outputOptions` | 오브젝트 | 아니요 | 출력 문서에 대한 구성 옵션 |

#### 문서 조작 매개 변수

| 매개변수 | 유형 | 필수 | 설명 |
|-----------|------|----------|-------------|
| `ddx` | 문자열 | 예 | 문서 어셈블리 또는 디스어셈블리에 대한 DDX 지침 |
| `inputDocuments` | 오브젝트 | 예 | 처리할 입력 문서 맵 |
| `outputOptions` | 오브젝트 | 아니요 | 출력 문서에 대한 구성 옵션 |

#### 문서 Assurance 매개 변수

| 매개변수 | 유형 | 필수 | 설명 |
|-----------|------|----------|-------------|
| `inputPDF` | 문자열 | 예 | 보안 또는 서명할 PDF 문서 입력 |
| `certificateAlias` | 문자열 | 조건부 | 서명 작업을 위한 인증서 별칭 |
| `credentialPassword` | 문자열 | 조건부 | 서명에 사용된 자격 증명의 암호 |

전체 매개 변수 세부 사항, 인증 요구 사항 및 예제 요청/응답은 위의 표에 링크된 특정 API 참조 설명서를 참조하십시오.

## 추가 리소스 {#see-also}

* [통신 처리 - 동기 API](/help/forms/aem-forms-cloud-service-communications.md)
* [통신 처리 - 일괄 처리 API](/help/forms/aem-forms-cloud-service-communications-batch-processing.md)
* [AEM Forms as a Cloud Service 아키텍처](/help/forms/aem-forms-cloud-service-architecture.md)
* [API 참조 설명서](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/document/)
* [얼리 어답터 프로그램 기능](/help/forms/early-access-ea-features.md)
