---
title: ' 릴리스 정보 [!DNL Workfront for Experience Manager enhanced connector]'
description: ' 릴리스 정보 [!DNL Workfront for Experience Manager enhanced connector]'
exl-id: 12de589d-fe5d-4bd6-b96b-48ec8f1ebcb6
source-git-commit: d763bacb0844a438ebea6ef206dfa184a49993fe
workflow-type: tm+mt
source-wordcount: '397'
ht-degree: 3%

---

#  릴리스 정보[!DNL Workfront for Experience Manager enhanced connector] {#release-notes-enhanced-connector-workfront}

다음 섹션에서는 다음에 대한 일반 릴리스 노트를 간략하게 설명합니다 [!DNL Workfront for Experience Manager enhanced connector].

## 릴리스 날짜 {#release-date}

최신 버전 1.9.1의 릴리스 날짜 [!DNL Workfront for Experience Manager enhanced connector] 은 2022년 7월 1일입니다.

## 릴리스 특징 {#release-highlights}

최신 버전의 [!DNL Workfront for Experience Manager enhanced connector] 에는 다음과 같은 개선 사항 및 버그 수정 사항이 포함되어 있습니다.

* Adobe IMS로 마이그레이션된 인스턴스에 대해 Workfront API 키를 사용하는 Experience Manager과 Workfront 애플리케이션 간 인증 지원이 추가되었습니다.

* 외부 파일 또는 폴더를 연결하면 Workfront 애플리케이션에서 `SERVER_ERROR` 오류 메시지. 오류 메시지가 API 키의 불일치로 인해 허가되지 않은 예외를 참조합니다.

* 자산에 대한 작업 만들기 워크플로우를 실행하면 로그 메시지에 Null 포인터 예외가 표시됩니다.

* 를 활성화하면 `Replace Spaces with DASH` 구성 옵션이 Experience Manager의 고급 설정에서 제공되면 Workfront에 중복 폴더가 생성됩니다.

>[!IMPORTANT]
>
>Adobe은 다음을 수행하는 것을 권장합니다. [최신 1.9.1 버전으로 업그레이드](../assets/update-workfront-enhanced-connector.md) 의 [!DNL Workfront for Experience Manager enhanced connector].

## 알려진 문제 {#known-issues}

* AEM 6.4로 프로젝트 연결 폴더를 구성하는 동안 Experience Manager은 **[!UICONTROL 하위 폴더]** 및 **[!UICONTROL 포트폴리오를 사용하여 프로젝트에서 연결된 폴더 만들기]** 필드. 에 대한 값 **[!UICONTROL 하위 폴더]** 필드 업데이트 **[!UICONTROL 정의되지 않음]** 및 **[!UICONTROL 포트폴리오를 사용하여 프로젝트에서 연결된 폴더 만들기]** 필드 업데이트 **[!UICONTROL 기본 Portfolio]** 구성을 저장한 후 자동으로 수행합니다.

* 클래식 Workfront 경험을 사용하는 경우 **[!UICONTROL 보내기]** 선택 사항은 **[!UICONTROL 자세히]** 드롭다운 목록에서 Experience Manager 내에서 대상 대상을 선택할 수 없습니다. 다음 **[!UICONTROL 보내기]** 옵션은 **[!UICONTROL 문서 작업]** 드롭다운 목록. 다음 **[!UICONTROL 보내기]** 옵션이 올바르게 작동합니다. **[!UICONTROL 자세히]** 드롭다운 목록 및 **[!UICONTROL 문서 작업]** 새 Workfront 경험에서 사용할 수 있는 드롭다운 목록입니다.

## 이전 릴리스 {#previous-releases}

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

