---
title: 타임라인의 활동 스트림
description: 이 문서에서는 타임라인에 자산에 대한 활동 로그를 표시하는 방법에 대해 설명합니다.
contentOwner: AG
feature: Asset Reports,Asset Management
role: Admin,User
exl-id: 8dd82c31-f88e-4407-9b6d-c87033d7a823
source-git-commit: 8bdd89f0be5fe7c9d4f6ba891d7d108286f823bb
workflow-type: tm+mt
source-wordcount: '237'
ht-degree: 32%

---

# 활동 스트림에서 자산 작업 로그 보기 {#activity-stream-in-timeline}

이 기능은 타임라인에 자산에 대한 활동 로그를 표시합니다. 에서 다음 자산 관련 작업을 수행하는 경우 [!DNL Experience Manager Assets], 활동 스트림 기능은 활동을 반영하도록 타임라인을 업데이트합니다.

다음 작업이 활동 스트림에 기록됩니다.

* 만들기
* 삭제
* 다운로드(표현물 포함)
* 게시
* 게시 취소
* 승인
* 거부
* 이동

The activity logs to be displayed in the timeline are fetched from the location `/var/audit/com.day.cq.dam/content/dam` in CRX, where log files are stored.  또한 새 자산을 업로드하거나 기존 자산을 수정 및 체크 인하면 타임라인 활동이 기록됩니다 [!DNL Experience Manager] via [Adobe 자산 링크](https://helpx.adobe.com/kr/enterprise/using/manage-assets-using-adobe-asset-link.html) 또는 [[!DNL Experience Manager] 데스크탑 앱](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/release-notes.html).

>[!NOTE]
>
>이러한 워크플로우에 대한 내역 정보가 저장되지 않으므로 임시 워크플로우는 타임라인에 표시되지 않습니다.

활동 스트림을 보려면 자산에서 하나 이상의 작업을 수행하고 자산을 선택한 다음 선택합니다 **[!UICONTROL 타임라인]** GlobalNav 목록에서 삭제할 수 있습니다.

<!-- ![timeline-2](assets/timeline-2.png) -->

타임라인에는 자산에서 수행하는 작업에 대한 활동 스트림이 표시됩니다.

<!-- ![activity_stream](assets/activity_stream.png) -->

>[!NOTE]
>
>The default log storage location for **[!UICONTROL Publish]** and **[!UICONTROL Unpublish]** tasks is `/var/audit/com.day.cq.replication/content`. For **[!UICONTROL Move]** tasks, the default location is `/var/audit/com.day.cq.wcm.core.page`.

**추가 참조**

* [에셋 번역](translate-assets.md)
* [Assets HTTP API](mac-api-assets.md)
* [자산 지원 파일 형식](file-format-support.md)
* [에셋 검색](search-assets.md)
* [연결된 자산](use-assets-across-connected-assets-instances.md)
* [에셋 보고서](asset-reports.md)
* [메타데이터 스키마](metadata-schemas.md)
* [에셋 다운로드](download-assets-from-aem.md)
* [메타데이터 관리](manage-metadata.md)
* [검색 패싯](search-facets.md)
* [컬렉션 관리](manage-collections.md)
* [벌크 메타데이터 가져오기](metadata-import-export.md)
