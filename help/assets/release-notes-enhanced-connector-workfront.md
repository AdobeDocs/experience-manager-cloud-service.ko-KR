---
title: 릴리스 정보 [!DNL Workfront for Experience Manager enhanced connector]
description: 릴리스 정보 [!DNL Workfront for Experience Manager enhanced connector]
exl-id: 12de589d-fe5d-4bd6-b96b-48ec8f1ebcb6
source-git-commit: 20e54ff697c0dc7ab9faa504d9f9e0e6ee585464
workflow-type: tm+mt
source-wordcount: '948'
ht-degree: 1%

---

#  릴리스 정보[!DNL Workfront for Experience Manager enhanced connector] {#release-notes-enhanced-connector-workfront}

다음 섹션에서는 다음에 대한 일반 릴리스 노트를 간략하게 설명합니다 [!DNL Workfront for Experience Manager enhanced connector].

## 릴리스 일자 {#release-date}

최신 버전 1.9.6의 릴리스 날짜 [!DNL Workfront for Experience Manager enhanced connector] 은 2022년 12월 09일입니다.

## 릴리스 특징 {#release-highlights}

최신 버전의 [!DNL Workfront for Experience Manager enhanced connector] 에는 다음과 같은 개선 사항 및 버그 수정 사항이 포함되어 있습니다.

**개선 사항**

<!--

* Workfront enhanced connector now allows you to use new search parameters to be more specific while defining folder names on large repositories.

-->

* Workfront enhanced connector에서 이제 자산 및 폴더에서 전체 텍스트 검색을 수행할 수 있습니다.

**버그 수정**

* 문서 버전 메타데이터는 Workfront과 Experience Manager 간에 적절히 동기화되지 않습니다.
* 폴더가 글로벌 구성에 정의가 없는 스키마를 사용하는 경우 Workfront의 Experience Manager에 연결된 폴더를 만들 때 문제가 발생합니다.
* 예상보다 긴 로드 시간으로 인해 임의의 필드를 클릭하면 메타데이터 스키마 편집기 양식이 응답하지 않습니다. 이 문제를 해결하기 위해 사용자 지정 양식에 대한 특정 OSGi 구성을 추가했습니다. 메타데이터 스키마 편집기에 추가하는 사용자 지정 양식의 이름은 로그에서 사용할 수 있습니다.

>[!IMPORTANT]
>
>Adobe은 다음을 수행하는 것을 권장합니다. [최신 1.9.6 버전으로 업그레이드](../assets/update-workfront-enhanced-connector.md) 의 [!DNL Workfront for Experience Manager enhanced connector].

## 알려진 문제 {#known-issues}

* AEM 6.4로 프로젝트 연결 폴더를 구성하는 동안 Experience Manager은 **[!UICONTROL 하위 폴더]** 및 **[!UICONTROL 포트폴리오를 사용하여 프로젝트에서 연결된 폴더 만들기]** 필드. 에 대한 값 **[!UICONTROL 하위 폴더]** 필드 업데이트 **[!UICONTROL 정의되지 않음]** 및 **[!UICONTROL 포트폴리오를 사용하여 프로젝트에서 연결된 폴더 만들기]** 필드 업데이트 **[!UICONTROL 기본 Portfolio]** 구성을 저장한 후 자동으로 수행합니다.

* 클래식 Workfront 경험을 사용하는 경우 **[!UICONTROL 보내기]** 선택 사항은 **[!UICONTROL 자세히]** 드롭다운 목록에서 Experience Manager 내에서 대상 대상을 선택할 수 없습니다. 다음 **[!UICONTROL 보내기]** 옵션은 **[!UICONTROL 문서 작업]** 드롭다운 목록. 다음 **[!UICONTROL 보내기]** 옵션이 올바르게 작동합니다. **[!UICONTROL 자세히]** 드롭다운 목록 및 **[!UICONTROL 문서 작업]** 새 Workfront 경험에서 사용할 수 있는 드롭다운 목록입니다.

## 이전 릴리스 {#previous-releases}

### 2022년 11월 릴리스 {#november-2022-release}

[!DNL Workfront for Experience Manager enhanced connector] 11월 11일에 릴리스된 버전 1.9.5에는 다음 업데이트가 포함됩니다.

* Workfront에서 다중 값 필드에 대해 하나의 값만 정의하면 필드 값이 Experience Manager에 적절하게 매핑되지 않습니다.

* Experience Manager은 `SERVER_ERROR` on **[!UICONTROL 외부 파일 및 폴더 연결]** 에 대한 잘못된 권한으로 인해 자산 폴더에 액세스하는 동안 화면 `/content/dam/collections`.

* 활성화 **[!UICONTROL Brand Portal에 자산 게시]** Workfront 향상된 커넥터 구성 페이지의 옵션에서 잘못된 이벤트를 만듭니다. 옵션을 비활성화한 후에도 이벤트가 삭제되지 않습니다.

   문제를 해결하려면

   1. 향상된 커넥터 버전 1.9.5로 업그레이드하십시오.

   1. 비활성화 **[!UICONTROL Brand Portal에 자산 게시]** 고급 설정 아래의 옵션.

   1. 를 활성화합니다 **[!UICONTROL Brand Portal에 자산 게시]** 선택 사항입니다.

   1. 잘못된 이벤트 구독을 삭제합니다.

      1. 에 대한 GET 호출 수행 `/attask/eventsubscription/api/v1/subscriptions?page=<page-number>`

         각 페이지 번호에 대해 하나의 API 호출을 실행합니다.

      1. 다음 텍스트를 검색하여 다음 URL과 일치하고 URL이 없는 이벤트 구독을 찾습니다 `objId`:

         ```
              "objId": "",
             "url": "<your-aem-domain>/bin/workfront-tools/events/linkedfolderprojectupdate<your-aem-domain>/
         ```

         다음 사이 의 `"objId": "",` 및 `"url"` 는 JSON 응답과 일치합니다. 이 작업을 수행하는 데 권장되는 방법은 를 포함하는 모든 이벤트 구독에서 복사하는 것입니다 `objId` 번호를 삭제합니다.

      1. 이벤트 구독 ID를 확인합니다.

      1. 잘못된 이벤트 구독을 삭제합니다. 에 대한 삭제 API 호출 만들기 `<your-aem-domain>/attask/eventsubscription/api/v1/subscriptions/<event-subscription-ID-from-previous-step>`

         `200` 응답 코드가 잘못된 이벤트 구독을 성공적으로 삭제했음을 의미하므로
   >[!NOTE]
   >
   >이 절차에서 언급된 단계를 실행하기 전에 잘못된 이벤트 구독을 이미 삭제한 경우 이 절차의 마지막 단계를 건너뛸 수 있습니다.

### 2022년 10월 릴리스 {#october-2022-release}

[!DNL Workfront for Experience Manager enhanced connector] 10월 7일에 릴리스된 버전 1.9.4에는 다음 업데이트가 포함됩니다.

* 많은 수의 이벤트로 인해 향상된 커넥터 구성 페이지에서 이벤트 구독 탭을 볼 수 없습니다.

* Workfront이 프로젝트에 있는 기존 폴더 목록을 가져올 수 없으므로 중복 폴더가 생성됩니다.

### 2022년 9월 릴리스 {#september-2022-release}

[!DNL Workfront for Experience Manager enhanced connector] 9월 16일에 릴리스된 버전 1.9.3에는 다음 업데이트가 포함됩니다.

* 크기가 8GB를 초과하는 파일을 업로드할 수 없습니다.
* Workfront에서 AEM으로 전송되는 자산을 자동으로 게시하는 동안 문제가 발생합니다.
* 기본 메타데이터 스키마 양식을 편집하는 동안 태그 필드에 루트 경로 필드를 사용할 수 없습니다.
* AEM 워크플로우를 사용하여 Workfront에서 새 버전을 추가하는 동안 문제가 발생합니다.
* Workfront에서 사용할 수 있는 자산에 대한 AEM 검색을 실행하면 AEM에 오류 메시지가 표시됩니다.
* 자산에서 작업 생성을 위한 AEM 워크플로우를 만들고 상위 작업 이름을 정의하지 않으면 작업이 Workfront에 생성되지 않습니다.

### 2022년 8월 릴리스 {#august-2022-release}

[!DNL Workfront for Experience Manager enhanced connector] 버전 1.9.2는 8월 3일에 릴리스되었습니다.

* 다음 **[!UICONTROL 문서 업로드]** 워크플로우 단계에서 Workfront에 문서를 첨부할 수 없습니다.

* 다음 **[!UICONTROL 문서 업로드]** 워크플로우 단계에서 Workfront의 작업 및 문제에 문서를 첨부하지 못했습니다. 워크플로우 단계에서는 문서를 프로젝트에 첨부합니다.

### 2022년 7월 릴리스 {#july-2022-release}

[!DNL Workfront for Experience Manager enhanced connector] 버전 1.9.1에는 다음 업데이트가 포함되어 있습니다.

* Adobe IMS로 마이그레이션된 인스턴스에 대해 Workfront API 키를 사용하는 Experience Manager과 Workfront 애플리케이션 간 인증 지원이 추가되었습니다.

* 외부 파일 또는 폴더를 연결하면 Workfront 애플리케이션에서 `SERVER_ERROR` 오류 메시지. 오류 메시지가 API 키의 불일치로 인해 허가되지 않은 예외를 참조합니다.

* 자산에 대한 작업 만들기 워크플로우를 실행하면 로그 메시지에 Null 포인터 예외가 표시됩니다.

* 를 활성화하면 `Replace Spaces with DASH` 구성 옵션이 Experience Manager의 고급 설정에서 제공되면 Workfront에 중복 폴더가 생성됩니다.

### 2022년 6월 릴리스 {#june-2022-release}

[!DNL Workfront for Experience Manager enhanced connector] 이제 다음 업데이트가 포함됩니다.

* 연결된 폴더를 통해 업로드하거나 `Send To` Workfront에서 자산을 Experience Manager as a Cloud Service에 업로드하는 데 사용할 수 있는 작업이 손상된 자산이며 Adobe Photoshop에서 열 수 없습니다.

### 2022년 3월 릴리스 {#march-2022-release}

[!DNL Workfront for Experience Manager enhanced connector] 이제 다음 업데이트가 포함됩니다.

* 이제 여러 프로젝트에 연결된 폴더 구성이 있더라도 Adobe Workfront과 AEM Assets as a Cloud Service 간에 연결된 폴더를 만들 수 있습니다.

* 이벤트 구독 페이지 매김에 대한 지원이 추가되었습니다.

* AEM 6.4.x에 대한 지원이 추가되었습니다.

* 프록시 환경에 대한 지원이 추가되었습니다.

* 파트너 및 고객 피드백을 기반으로 몇 가지 버그 수정.

>[!MORELIKETHIS]
>
>* [통합 [!DNL Workfront for Experience Manager enhanced connector] Experience Manager 6.5 사용](https://experienceleague.adobe.com/docs/experience-manager-65/assets/integrations/workfront-integrations.html?lang=en)
>* [통합 [!DNL Workfront for Experience Manager enhanced connector] Experience Manager 6.4 사용](https://experienceleague.adobe.com/docs/experience-manager-64/assets/integrations/workfront-integrations.html?lang=en)