---
title: 릴리스 정보 [!DNL Workfront for Experience Manager enhanced connector]
description: 릴리스 정보 [!DNL Workfront for Experience Manager enhanced connector]
exl-id: 12de589d-fe5d-4bd6-b96b-48ec8f1ebcb6
source-git-commit: 5ad33f0173afd68d8868b088ff5e20fc9f58ad5a
workflow-type: tm+mt
source-wordcount: '1190'
ht-degree: 1%

---

#  릴리스 정보[!DNL Workfront for Experience Manager enhanced connector] {#release-notes-enhanced-connector-workfront}

다음 섹션에서는 의 일반 릴리스 정보에 대해 간략히 소개합니다. [!DNL Workfront for Experience Manager enhanced connector].

## 릴리스 일자 {#release-date}

의 최신 버전 1.9.12에 대한 릴리스 날짜 [!DNL Workfront for Experience Manager enhanced connector] 는 2023년 8월 9일입니다.

## 릴리스 특징 {#release-highlights}

의 최신 버전 [!DNL Workfront for Experience Manager enhanced connector] 에는 다음 업데이트가 포함됩니다.

* 연결된 폴더와 연결된 Experience Manager 계정이 없기 때문에 사용자 계정에 연결된 폴더를 만들 수 없습니다.

* Experience Manager 에셋에 대한 메타데이터 업데이트 중 경합 조건.


>[!NOTE]
>
>AEM 6.4는 확장 지원이 종료되었습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/?lang=en).


>[!IMPORTANT]
>
>Adobe은 다음을 권장합니다. [최신 1.9.12 버전으로 업그레이드](/help/assets/workfront-connector-install.md) / [!DNL Workfront for Experience Manager enhanced connector].

## 알려진 문제 {#known-issues}

* AEM 6.4로 프로젝트 연결 폴더를 구성하는 동안 Experience Manager에 대한 값이 저장되지 않습니다. **[!UICONTROL 하위 폴더]** 및 **[!UICONTROL 포트폴리오를 사용하여 프로젝트에 연결된 폴더 만들기]** 필드. 에 대한 값 **[!UICONTROL 하위 폴더]** 에 대한 필드 업데이트 **[!UICONTROL 정의되지 않음]** 및 의 값 **[!UICONTROL 포트폴리오를 사용하여 프로젝트에 연결된 폴더 만들기]** 에 대한 필드 업데이트 **[!UICONTROL 기본 Portfolio]** 구성을 저장한 후 자동으로 이동합니다.

* 클래식 Workfront 환경을 사용하는 경우 **[!UICONTROL 전송 대상]** 옵션이에서 사용할 수 있음 **[!UICONTROL 자세히]** 드롭다운 목록에서는 Experience Manager 내의 대상 을 선택할 수 없습니다. 다음 **[!UICONTROL 전송 대상]** 옵션은 **[!UICONTROL 문서 작업]** 드롭다운 목록입니다. 다음 **[!UICONTROL 전송 대상]** 옵션이에 대해 올바르게 작동합니다. **[!UICONTROL 자세히]** 드롭다운 목록 및 **[!UICONTROL 문서 작업]** 새로운 Workfront 경험에서 사용할 수 있는 드롭다운 목록입니다.

## 이전 릴리스 {#previous-releases}

### 2023년 6월 릴리스 {#june-2023-release}

* 고급 네트워킹을 구성했으면 Adobe WorkfrontAEM 에서 as a Cloud Service으로 콘텐츠를 전송하는 동안 문제가 발생합니다.


### 2023년 5월 릴리스 {#may-2023-release}

* Workfront은 Experience Manager에서 Workfront으로의 REST 호출을 기반으로 중복 이벤트 가입에 대한 409 HTTP 응답을 반환하며, 이로 인해 null 포인터 예외가 발생합니다.

### 2023년 4월 릴리스 {#april-2023-release}

[!DNL Workfront for Experience Manager enhanced connector] 2023년 4월 10일에 릴리스된 버전 1.9.9에는 다음 업데이트가 포함됩니다.

* Experience Manager에 `DateTimeParseException` 연결된 폴더를 만드는 동안 Workfront에서 마지막 수정 날짜를 받을 때 예외가 발생합니다.

* 짧은 기간 내에 연결된 프로젝트 폴더를 여러 개 만드는 동안 문제가 발생했습니다.

* 새 프로젝트 연결 폴더 세트의 수에 대한 임계값 제한을 구성할 수 없습니다.

### 2023년 3월 릴리스 {#march-2023-release}

[!DNL Workfront for Experience Manager enhanced connector] 2023년 3월 3일에 릴리스된 버전 1.9.8에는 다음 업데이트가 포함됩니다.

* Workfront에서 프로젝트 연결 폴더를 만드는 동안 Experience Manager 성능이 향상되었습니다.

* 이제 Workfront의 댓글 삭제가 Experience Manager에 반영됩니다.

* Experience Manager as a Cloud Service으로 신규 고객의 커넥터 구성을 차단하는 기능을 관리할 수 있습니다.


### 2023년 1월 릴리스 {#january-2022-release}

[!DNL Workfront for Experience Manager enhanced connector] 2023년 2월 2일에 릴리스된 버전 1.9.7에는 다음 업데이트가 포함됩니다.

* 1.9.6 릴리스를 설치한 후 메타데이터 편집기에 Workfront 사용자 정의 양식 속성이 나열되지 않습니다.

* 개발 콘솔이 표시됩니다 `/content/dam/jcr:content/metadata/wfProjectURL not found` Workfront enhanced 커넥터를 설치하고 Assets 홈 페이지를 연 후 오류 메시지가 표시됩니다.

### 2022년 12월 릴리스 {#december-2022-release}

[!DNL Workfront for Experience Manager enhanced connector] 12월 09일에 릴리스된 버전 1.9.6에는 다음 업데이트가 포함됩니다.

**개선 사항**

<!--

* Workfront enhanced connector now lets you use new search parameters to be more specific while defining folder names on large repositories.

-->

* Workfront 강화 커넥터는 이제 에셋 및 폴더에 대한 전체 텍스트 검색 수행을 지원합니다.

**버그 수정**

* 문서 버전 메타데이터가 Workfront과 Experience Manager 간에 적절하게 동기화되지 않습니다.
* 폴더가 전역 구성에서 정의가 누락된 스키마를 사용하는 경우 Workfront의 Experience Manager에 연결된 폴더를 생성하는 동안 문제가 발생합니다.
* 예상보다 긴 로드 시간으로 인해 필드를 클릭하면 메타데이터 스키마 편집기 양식이 응답하지 않습니다. 문제를 해결하기 위해 사용자 정의 양식에 대한 특정 OSGi 구성을 추가했습니다. 메타데이터 스키마 편집기에 추가하는 사용자 정의 양식의 이름은 로그에서 사용할 수 있습니다.

### 2022년 11월 릴리스 {#november-2022-release}

[!DNL Workfront for Experience Manager enhanced connector] 11월 11일에 릴리스된 버전 1.9.5에는 다음 업데이트가 포함됩니다.

* Workfront에서 다중 값 필드에 대해 값을 하나만 정의하는 경우 필드 값이 Experience Manager에 적절하게 매핑되지 않습니다.

* Experience Manager에 `SERVER_ERROR` 다음에 있음 **[!UICONTROL 외부 파일 및 폴더 연결]** 에 대한 잘못된 권한으로 인해 에셋 폴더에 액세스하는 중 화면 `/content/dam/collections`.

* 활성화 **[!UICONTROL Brand Portal에 자산 게시]** Workfront 강화 커넥터 구성 페이지의 옵션이 잘못된 이벤트를 생성합니다. 옵션을 비활성화한 후에도 이벤트가 삭제되지 않습니다.

  문제를 해결하려면:

   1. 향상된 커넥터 버전 1.9.5로 업그레이드하십시오.

   1. 비활성화 **[!UICONTROL Brand Portal에 자산 게시]** 고급 설정 아래의 옵션입니다.

   1. 활성화 **[!UICONTROL Brand Portal에 자산 게시]** 옵션을 선택합니다.

   1. 잘못된 이벤트 구독을 삭제합니다.

      1. GET 호출 수행 `/attask/eventsubscription/api/v1/subscriptions?page=<page-number>`

         각 페이지 번호에 대해 하나의 API 호출을 실행합니다.

      1. 다음 URL과 일치하지만 가 없는 이벤트 구독을 찾으려면 다음 텍스트를 검색합니다. `objId`:

         ```
              "objId": "",
             "url": "<your-aem-domain>/bin/workfront-tools/events/linkedfolderprojectupdate<your-aem-domain>/
         ```

         다음 사이에 콘텐츠가 있는지 확인합니다. `"objId": "",` 및 `"url"` 는 JSON 응답과 일치합니다. 이 작업을 수행하는 데 권장되는 방법은 가 있는 이벤트 구독에서 복사하는 것입니다. `objId` 숫자를 삭제합니다.

      1. 이벤트 구독 ID를 확인합니다.

      1. 잘못된 이벤트 구독을 삭제합니다. API 호출 삭제 `<your-aem-domain>/attask/eventsubscription/api/v1/subscriptions/<event-subscription-ID-from-previous-step>`

         `200` 응답 코드가 잘못된 이벤트 구독을 성공적으로 삭제했음을 의미하므로
  >[!NOTE]
  >
  >이 절차에서 언급된 단계를 실행하기 전에 잘못된 이벤트 구독을 이미 삭제한 경우 이 절차의 마지막 단계를 건너뛸 수 있습니다.

### 2022년 10월 릴리스 {#october-2022-release}

[!DNL Workfront for Experience Manager enhanced connector] 10월 07일에 릴리스된 버전 1.9.4에는 다음 업데이트가 포함됩니다.

* 많은 이벤트로 인해 향상된 커넥터 구성 페이지에서 이벤트 구독 탭을 볼 수 없습니다.

* Workfront에서 프로젝트의 기존 폴더 목록을 가져올 수 없으므로 중복 폴더가 생성됩니다.

### 2022년 9월 릴리스 {#september-2022-release}

[!DNL Workfront for Experience Manager enhanced connector] 9월 16일에 릴리스된 버전 1.9.3에는 다음 업데이트가 포함됩니다.

* 8GB를 초과하는 파일을 업로드할 수 없습니다.
* Workfront에서 AEM으로 전송된 자산을 자동 게시하는 동안 문제가 발생합니다.
* 기본 메타데이터 스키마 양식을 편집하는 동안 태그 필드에 루트 경로 필드를 사용할 수 없습니다.
* AEM 워크플로우를 사용하여 Workfront에서 새 버전을 추가하는 동안 문제가 발생합니다.
* Workfront에서 사용할 수 있는 에셋에 대해 AEM 검색을 실행하면 AEM에 오류 메시지가 표시됩니다.
* 에셋에서 작업 생성을 위한 AEM 워크플로우를 만들 때 상위 작업 이름을 정의하지 않으면 작업이 Workfront에서 생성되지 않습니다.

### 2022년 8월 릴리스 {#august-2022-release}

[!DNL Workfront for Experience Manager enhanced connector] 8월 3일에 릴리스된 버전 1.9.2에는 다음 업데이트가 포함됩니다.

* 다음 **[!UICONTROL 문서 업로드]** 워크플로 단계에서 Workfront에 문서를 첨부하지 못했습니다.

* 다음 **[!UICONTROL 문서 업로드]** 워크플로 단계가 Workfront의 작업 및 문제에 문서를 첨부하지 못했습니다. 워크플로 단계는 문서를 프로젝트에 성공적으로 첨부합니다.

### 2022년 7월 릴리스 {#july-2022-release}

[!DNL Workfront for Experience Manager enhanced connector] 버전 1.9.1에는 다음 업데이트가 포함되어 있습니다.

* Adobe IMS로 마이그레이션된 인스턴스에 대해 Workfront API 키를 사용하여 Experience Manager과 Workfront 애플리케이션 간의 인증에 대한 지원을 추가했습니다.

* 외부 파일 또는 폴더를 연결하면 Workfront 애플리케이션에 `SERVER_ERROR` 오류 메시지입니다. 오류 메시지는 API 키가 일치하지 않아 승인되지 않은 예외를 나타냅니다.

* 자산에 대해 작업 만들기 워크플로우를 실행할 때 로그 메시지에 Null 포인터 예외가 표시됩니다.

* 을(를) 활성화하면 `Replace Spaces with DASH` Experience Manager의 고급 설정 아래에 있는 구성 옵션으로 인해 Workfront에서 중복 폴더가 만들어집니다.

### 2022년 6월 릴리스 {#june-2022-release}

[!DNL Workfront for Experience Manager enhanced connector] 에는 이제 다음 업데이트가 포함됩니다.

* 연결된 폴더를 통해 업로드하거나 `Send To` Workfront에서 작업을 사용하여 자산을 Experience Manager as a Cloud Service으로 업로드할 수 있습니다. 자산이 손상되어 Adobe Photoshop에서 열 수 없습니다.

### 2022년 3월 릴리스 {#march-2022-release}

[!DNL Workfront for Experience Manager enhanced connector] 에는 이제 다음 업데이트가 포함됩니다.

* 이제 여러 개의 프로젝트로 연결된 폴더 구성이 있는 경우에도 Adobe Workfront과 AEM Assets as a Cloud Service 간에 연결된 폴더를 만들 수 있습니다.

* 이벤트 구독 페이지 매김에 대한 지원을 추가했습니다.

* AEM 6.4.x에 대한 지원이 추가되었습니다.

* 프록시 환경에 대한 지원이 추가되었습니다.

* 파트너 및 고객 피드백을 기반으로 몇 가지 버그가 수정되었습니다.

>[!MORELIKETHIS]
>
>* [통합 [!DNL Workfront for Experience Manager enhanced connector] Experience Manager 6.5 사용](https://experienceleague.adobe.com/docs/experience-manager-65/assets/integrations/workfront-integrations.html?lang=en)
