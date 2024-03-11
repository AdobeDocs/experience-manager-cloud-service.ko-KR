---
title: ' [!DNL Workfront for Experience Manager enhanced connector] 릴리스 정보'
description: ' [!DNL Workfront for Experience Manager enhanced connector] 릴리스 정보'
exl-id: 12de589d-fe5d-4bd6-b96b-48ec8f1ebcb6
source-git-commit: 411793f140a2a9cf482d820382d41de843a97e87
workflow-type: tm+mt
source-wordcount: '1648'
ht-degree: 97%

---

# [!DNL Workfront for Experience Manager enhanced connector] 릴리스 정보 {#release-notes-enhanced-connector-workfront}

다음 섹션에서는 [!DNL Workfront for Experience Manager enhanced connector]의 일반 릴리스 정보에 대해 간략히 설명합니다.

의 최신 버전 1.9.18에 대한 릴리스 날짜 [!DNL Workfront for Experience Manager enhanced connector] 는 2024년 3월 8일입니다.

## 릴리스 하이라이트 {#release-highlights}

의 최신 버전 [!DNL Workfront for Experience Manager enhanced connector] 에는 다음 버그 수정이 포함됩니다.

* Workfront에서 다중 자산 업로드를 처리하면 문제가 발생합니다.
* Workfront을 사용하여 Experience Manager에서 폴더를 검색할 때 닫는 따옴표를 추가하지 않음 `SERVER_ERROR`.

>[!NOTE]
>
>AEM 6.4는 확장 지원이 종료되었습니다. [ 기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html)을 참조하십시오. [여기](https://experienceleague.adobe.com/docs/?lang=en)에서 지원되는 버전을 확인하십시오.


>[!IMPORTANT]
>
>Adobe는 [!DNL Workfront for Experience Manager enhanced connector]의 [최신 1.9.18 버전으로 업그레이드](/help/assets/workfront-connector-install.md)할 것을 권장합니다.

## 알려진 문제 {#known-issues}

* AEM 6.4로 프로젝트 연결 폴더를 구성하는 동안 Experience Manager는 포트폴리오 필드가 있는 프로젝트에서 **[!UICONTROL 하위 폴더]** 및 **[!UICONTROL 연결 폴더 생성]**&#x200B;에 대한 값을 저장하지 않습니다. **[!UICONTROL 정의되지 않음]**&#x200B;으로 업데이트되는 **[!UICONTROL 하위 폴더]**&#x200B;의 값이고 구성을 저장한 후 포트폴리오 필드가 **[!UICONTROL 기본 포트폴리오]**&#x200B;로 자동 업데이트되는 **[!UICONTROL 프로젝트에 연결된 폴더 생성]**&#x200B;의 값입니다.

* 기존의 Workfront 경험을 사용하는 경우, **[!UICONTROL 추가]** 드롭다운 목록에서 사용할 수 있는 **[!UICONTROL 수신인]** 옵션을 사용하면 Experience Manager에서 타깃 대상을 선택할 수 없습니다. **[!UICONTROL 수신인]** 옵션은 **[!UICONTROL 문서 작업]** 드롭다운 목록을 사용하여 올바르게 작동합니다. The **[!UICONTROL 수신인]** 옵션은 새로운 Workfront 경험에서 사용할 수 있는 **[!UICONTROL 추가]** 드롭다운 목록 및 **[!UICONTROL 문서 작업]** 목록에서 올바르게 작동합니다.

## 이전 출시 버전 {#previous-releases}

### 2024년 2월 릴리스 {#february-2023-release}

* AEM Cloud 고객이 커넥터를 구성하고 설정할 수 있도록 토글 기능이 활성화되었습니다.

* 기본 세션을 명시적으로 닫지 않고 `resourceResolver`를 닫으면 AEM 인스턴스에서 세션 누출이 발생합니다. Resource Resolver가 자동으로 닫혀도 세션이 암시적으로 닫히지 않으므로 세션을 명시적으로 닫는 것이 중요합니다.

### 2024년 1월 릴리스 {#january-2023-release}

* 현재 [!DNL CRX DE]의 [!DNL Workfront] 구성은 `project ID`를 저장하지 않으므로, 읽기 전용 권한을 적용할 때 오류가 발생합니다. [권한 구성](https://experienceleague.adobe.com/docs/experience-manager-65/content/assets/integrations/workfront-connector-configure.html#linked-folders) 방법에 대해 자세히 알아보십시오.

* 기본 제공 색인 정의에 사용자 정의 속성을 추가하는 방법에 대한 공개 설명서가 없습니다. [사용자 정의 속성 추가](https://experienceleague.adobe.com/docs/experience-manager-65/content/assets/integrations/workfront-connector-configure.html#metadata-schema-mapping)에 대해 자세히 알아보십시오.

* 강화 커넥터에서 연결 구성을 삭제하면 이벤트 구독 및 기타 저장된 구성에 큰 영향을 미치며, 이전 URL을 가리키게 됩니다.

* Forms 추가 기능 패키지를 설치해도 **[!UICONTROL 토글 라우터]**&#x200B;가 설치되지 않아 [!DNL WFEC AMS environment Toggle] 기능이 실패하게 됩니다.

* EWC 설정에서 이벤트 구독을 활성화하면 처음 [!DNL Workfront] 강화 커넥터를 설정할 때 `HTTP 400` 오류와 함께 API 호출이 반복적으로 실패합니다.

* Workfront에서 연결된 폴더 자산에 대한 댓글을 삭제하면 AEM에서 연결된 폴더 경로를 찾지 못합니다.

* AEM에서 대용량 파일 자산에 대한 지원이 부족하면 4바이트 크기 문제가 발생합니다.

* 연결된 폴더, 문서 업데이트 및 메모 업데이트의 중요한 흐름에 대한 요청 시간 처리가 없습니다.

### 2023년 11월 릴리스 {#november-2023-release}

* AEM 폴더 목록을 확인할 경우, 대화 상자를 로드하는 데 1분 이상 걸립니다.
* 승인된[!DNL Workfront] 사용자가 계속 인증 실패 오류 로그를 받습니다.

### 2023년 10월 릴리스 {#october-2023-release}

* 이벤트 구독이 고급 설정에서 비활성화되면 **문서 업데이트 이벤트를 구독하는 옵션을 선택하여 AEM 자산 메타데이터를 업데이트**&#x200B;하고, **프로젝트가 완료되면 모든 프로젝트 자산을 Brand Portal에 게시**&#x200B;하고, **댓글 동기화를 활성화**&#x200B;할 수 있습니다.

* Workfront에서 자산을 미리 볼 때 Experience Manager에 저장된 일부 자산이 제대로 렌더링되지 않습니다.

* Experience Manager와 Workfront의 연결을 재구성하는 동안에는 댓글 동기화 업데이트, 삭제, 문서 업데이트 등 이벤트 구독이 제대로 생성되지 않습니다.

* 연결 폴더 생성, 업데이트, 연결 폴더 활성화, 댓글 동기화 활성화 및 비활성화, 커넥터에 대한 고급 설정 저장에 대한 주요 API 성능이 개선되었습니다.

### 2023년 9월 릴리스 {#september-2023-release}

* Experience Manager 강화 커넥터는 Workfront에서 모든 이벤트 구독을 가져오는 동시에 프로젝트에 대한 이벤트 구독을 삭제합니다. 이 경우 애플리케이션의 성능에 영향을 미칠 수 있습니다.

* Workfront의 자산이 Experience Manager로 전송되면 자산 MIME 유형이 Experience Manager 내의 `dc:format` 속성으로 설정되지 않습니다.

* Experience Manager 고급 커넥터에 저장된 Workfront 프로젝트 ID에 중복 항목이 포함됩니다.

### 2023년 8월 릴리스 {#august-2023-release}

* 연결된 폴더에 연결된 사용자 계정이 없으므로 Experience Manager에서 연결된 폴더를 만들 수 없습니다.

* Experience Manager에서 자산에 대한 메타데이터 업데이트 도중 경합 조건이 발생합니다.

### 2023년 6월 릴리스 {#june-2023-release}

* 고급 네트워킹을 구성한 경우, Adobe Workfront에서 AEM as a Cloud Service로 콘텐츠를 보내는 동안 문제가 발생합니다.


### 2023년 5월 릴리스 {#may-2023-release}

* Workfront는 Experience Manager에서 Workfront로의 REST 호출을 기반으로 중복 이벤트 구독에 대한 409 HTTP 응답을 반환하여 null 포인터 예외를 발생시킵니다.

### 2023년 4월 릴리스 {#april-2023-release}

2023년 4월 10일에 릴리스된 [!DNL Workfront for Experience Manager enhanced connector] 버전 1.9.9에는 다음과 같은 업데이트가 포함되어 있습니다.

* 연결된 폴더를 생성하는 동안 Experience Manager는 Workfront에서 마지막으로 수정된 날짜를 받으면 `DateTimeParseException` 예외를 표시합니다.

* 짧은 기간 내에 연결된 여러 프로젝트 폴더를 생성하는 동안 문제가 발생합니다.

* 새 프로젝트 연결 폴더 세트 수에는 임계값 제한을 구성할 수 없습니다.

### 2023년 3월 릴리스 {#march-2023-release}

2023년 3월 3일에 릴리스된 [!DNL Workfront for Experience Manager enhanced connector] 버전 1.9.8에는 다음과 같은 업데이트가 포함되어 있습니다.

* Workfront에서 프로젝트 연결 폴더를 생성하는 동안 Experience Manager의 성능이 향상되었습니다.

* 이제 Workfront의 댓글 삭제가 Experience Manager에 반영됩니다.

* Experience Manager as a Cloud Service의 신규 고객이 커넥터를 구성하지 못하도록 차단하는 기능입니다.


### 2023년 1월 릴리스 {#january-2022-release}

2023년 2월 2일에 릴리스된 [!DNL Workfront for Experience Manager enhanced connector] 버전 1.9.7에는 다음과 같은 업데이트가 포함되어 있습니다.

* 1.9.6 릴리스 설치 후 메타데이터 편집기에 Workfront 사용자 정의 양식 속성이 나열되지 않습니다.

* Workfront 강화 커넥터를 설치하고 자산 홈 페이지를 열면 개발자 콘솔에 `/content/dam/jcr:content/metadata/wfProjectURL not found` 오류 메시지가 표시됩니다.

### 2022년 12월 릴리스 {#december-2022-release}

12월 9일에 릴리스된 [!DNL Workfront for Experience Manager enhanced connector] 버전 1.9.6에는 다음과 같은 업데이트가 포함되어 있습니다.

**개선 사항**

<!--

* Workfront enhanced connector now lets you use new search parameters to be more specific while defining folder names on large repositories.

-->

* Workfront 강화 커넥터는 이제 자산 및 폴더에 대한 전체 텍스트 검색 수행을 지원합니다.

**버그 수정**

* 문서 버전 메타데이터가 Workfront와 Experience Manager 간에 적절하게 동기화되지 않습니다.
* 폴더가 전역 구성에서 정의가 누락된 스키마를 사용하는 경우 Workfront에서 Experience Manager에 연결된 폴더를 생성하는 동안 문제가 발생합니다.
* 예상보다 긴 로드 시간으로 인해 필드를 클릭하면 메타데이터 스키마 편집기 양식이 응답하지 않습니다. 문제를 해결하기 위해 사용자 정의 양식에 대한 특정 OSGi 구성을 추가했습니다. 메타데이터 스키마 편집기에 추가하는 사용자 정의 양식의 이름은 로그에서 확인할 수 있습니다.

### 2022년 11월 릴리스 {#november-2022-release}

11월 11일에 릴리스된 [!DNL Workfront for Experience Manager enhanced connector] 버전 1.9.5에는 다음과 같은 업데이트가 포함되어 있습니다.

* Workfront의 다중 값 필드에 대해 한 개의 값만 정의하면 필드 값이 Experience Manager에 적절히 매핑되지 않습니다.

* `/content/dam/collections`에서의 잘못된 권한으로 인해 자산 폴더에 액세스하는 동안 Experience Manager는 **[!UICONTROL 외부 파일 및 폴더 연결]** 화면에 `SERVER_ERROR`를 표시합니다.

* Workfront 강화 커넥터 구성 페이지에서 **[!UICONTROL Brand Portal에 자산 게시]** 옵션을 활성화하면 잘못된 이벤트가 생성됩니다. 옵션을 비활성화한 후에도 이벤트는 삭제되지 않습니다.

  문제를 해결하려면

   1. 강화 커넥터의 버전 1.9.5로 업그레이드하십시오.

   1. 고급 설정에서 **[!UICONTROL Brand Portal에 자산 게시]** 옵션을 비활성화하십시오.

   1. **[!UICONTROL Brand Portal에 자산 게시]** 옵션을 활성화하십시오.

   1. 잘못된 이벤트 구독을 삭제하십시오.

      1. `/attask/eventsubscription/api/v1/subscriptions?page=<page-number>`에 대한 GET 호출을 수행하십시오.

         각 페이지 번호에 대해 API 호출 한 개를 실행하십시오.

      1. 다음 텍스트를 검색하여 다음 URL과 일치하고 `objId`이 없는 이벤트 구독을 찾으십시오.

         ```
              "objId": "",
             "url": "<your-aem-domain>/bin/workfront-tools/events/linkedfolderprojectupdate<your-aem-domain>/
         ```

         `"objId": "",`와 `"url"` 간의 콘텐츠는 JSON 응답과 일치해야 합니다. 이를 위해 권장되는 메서드는 `objId`이 있는 이벤트 구독에서 복사한 다음 번호를 삭제하는 것입니다.

      1. 이벤트 구독 ID을 참고하십시오.

      1. 잘못된 이벤트 구독을 삭제하십시오. `<your-aem-domain>/attask/eventsubscription/api/v1/subscriptions/<event-subscription-ID-from-previous-step>`에 대해 삭제 API 호출을 수행하십시오.

         응답 코드로서 `200`은 잘못된 이벤트 구독이 성공적으로 삭제되었음을 의미합니다.
  >[!NOTE]
  >
  >이 절차의 설명에 따라 단계를 실행하기 전에 잘못된 이벤트 구독을 이미 삭제한 경우 이 절차의 마지막 단계를 건너뛸 수 있습니다.

### 2022년 10월 릴리스 {#october-2022-release}

10월 7일에 릴리스된 [!DNL Workfront for Experience Manager enhanced connector] 버전 1.9.4에는 다음과 같은 업데이트가 포함되어 있습니다.

* 많은 이벤트가 생성되어 강화 커넥터 구성 페이지에서 이벤트 구독 탭을 볼 수 없습니다.

* Workfront는 프로젝트에서 기존 폴더 목록을 가져올 수 없으므로 중복된 폴더가 생성됩니다.

### 2022년 9월 릴리스 {#september-2022-release}

9월 16일에 릴리스된 [!DNL Workfront for Experience Manager enhanced connector] 버전 1.9.3에는 다음과 같은 업데이트가 포함되어 있습니다.

* 8GB를 초과하는 파일을 업로드할 수 없습니다.
* Workfront에서 AEM으로 전송된 자산을 자동 게시하는 동안 문제가 발생합니다.
* 기본 메타데이터 스키마 양식을 편집하는 동안 태그 필드에 루트 경로 필드를 사용할 수 없습니다.
* AEM 워크플로를 사용하여 Workfront에서 새 버전을 추가하는 동안 문제가 발생합니다.
* Workfront에서 사용 가능한 자산에 대해 AEM 검색을 실행하면 AEM에 오류 메시지가 표시됩니다.
* 자산에서 작업 생성 시 AEM 워크플로를 생성하고 상위 작업 이름을 정의하지 않으면 작업이 Workfront에서 생성되지 않습니다.

### 2022년 8월 릴리스 {#august-2022-release}

8월 3일에 릴리스된 [!DNL Workfront for Experience Manager enhanced connector] 버전 1.9.2에는 다음과 같은 업데이트가 포함되어 있습니다.

* **[!UICONTROL 문서 업로드]** 워크플로 단계에서 문서를 Workfront에 첨부할 수 없습니다.

* **[!UICONTROL 문서 업로드]** 워크플로 단계에서 문서를 Workfront의 작업 및 문제에 첨부할 수 없습니다. 워크플로 단계에서 문서를 프로젝트에 정상적으로 첨부합니다.

### 2022년 7월 릴리스 {#july-2022-release}

[!DNL Workfront for Experience Manager enhanced connector] 버전 1.9.1에는 다음과 같은 업데이트가 포함되어 있습니다.

* Adobe IMS로 마이그레이션되는 인스턴스의 Workfront API 키를 사용하여 Experience Manager와 Workfront 애플리케이션 간 인증에 대한 지원을 추가했습니다.

* 외부 파일 또는 폴더를 연결하면 Workfront 애플리케이션에 `SERVER_ERROR` 오류 메시지가 표시됩니다. 오류 메시지는 API 키의 불일치로 인해 승인되지 않은 예외를 나타냅니다.

* 자산의 작업 만들기 워크플로를 실행하면 Null 포인터 예외가 로그 메시지에 표시됩니다.

* Experience Manager의 고급 설정에서 `Replace Spaces with DASH` 구성 옵션을 활성화하면 Workfront에서 중복된 폴더가 생성됩니다.

### 2022년 6월 릴리스 {#june-2022-release}

[!DNL Workfront for Experience Manager enhanced connector]에는 다음과 같은 업데이트가 포함되어 있습니다.

* Experience Manager as a Cloud Service로 자산을 업로드하기 위해 링크된 폴더를 통해 업로드하거나 Workfront에서 사용 가능한 `Send To` 작업을 사용하는 경우 자산이 손상되어 Adobe Photoshop에서 열 수 없습니다.

### 2022년 3월 릴리스 {#march-2022-release}

[!DNL Workfront for Experience Manager enhanced connector]에는 다음과 같은 업데이트가 포함되어 있습니다.

* 여러 프로젝트 연결 폴더 구성이 있는 경우에도 Adobe Workfront와 AEM Assets as a Cloud Service 간에 연결 폴더를 만들 수 있습니다.

* 이벤트 구독 페이지 매김에 대한 지원을 추가했습니다.

* AEM 6.4.x에 대한 지원을 추가했습니다.

* 프록시 환경에 대한 지원을 추가했습니다.

* 파트너 및 고객 피드백에 따라 몇 가지 버그가 수정되었습니다.

>[!MORELIKETHIS]
>
>* Experience Manager 6.5와 [통합 [!DNL Workfront for Experience Manager enhanced connector] ](https://experienceleague.adobe.com/docs/experience-manager-65/assets/integrations/workfront-integrations.html?lang=ko-KR)
