---
title: Adobe Experience Manager as a Cloud Service의 Cloud Manager 2023.1.0 릴리스 정보
description: AEM as a Cloud Service의 Cloud Manager 2024.1.0 릴리스 정보입니다.
feature: Release Information
exl-id: 9c73d7ab-c2c2-4803-a07b-e9054220c6b2
source-git-commit: 5aabdf22a040a031a3fa2a1a9f70247cf2e38f2e
workflow-type: tm+mt
source-wordcount: '190'
ht-degree: 36%

---


# Adobe Experience Manager as a Cloud Service의 Cloud Manager 2023.1.0 릴리스 정보 {#release-notes}

이 페이지에서는 AEM as a Cloud Service의 Cloud Manager 릴리스 2023.1.0에 대한 릴리스 노트를 문서화합니다.

>[!NOTE]
>
>Adobe Experience Manager as a Cloud Service의 최신 릴리스 정보는 [이 페이지](/help/release-notes/release-notes-cloud/release-notes-current.md)를 참조하십시오.

## 릴리스 일자 {#release-date}

AEM as a Cloud Service의 Cloud Manager 릴리스 2023.1.0의 릴리스 날짜는 2023년 1월 19일입니다. 다음 릴리스는 2023년 2월 16일에 예정되어 있습니다.

## 새로운 기능 {#what-is-new}

* 사용 편의성 향상은 사용자가 작업을 수행할 수 있는 위치와 기본 포인터를 구분하는 커서 스타일을 업데이트함으로써 수행되었습니다.

* 이제 사용자 지정 UI 테스트 보고서가 Cloud Manager 저장소에 복사되며 Cloud Manager API 호출을 통해 액세스할 수 있습니다.

* 이제 사용자는 왼쪽 오른쪽 화살표를 사용하여 go-live 위젯 상태 간을 전환할 수 있습니다.

   ![Go-live 위젯 전환](assets/go-live-transitions.gif)

* 셀프서비스 [HIPAA 지원 프로그램 생성](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md) 이제 해당 권한 및 권한을 사용할 수 있을 때 가능합니다.

## 버그 수정 {#bug-fixes}

* Cloud Manager는 두 개의 파이프라인 실행이 동시에(또는 거의 동시에) 시작되지 않도록 차단하여 파이프라인 실패를 방지합니다.
