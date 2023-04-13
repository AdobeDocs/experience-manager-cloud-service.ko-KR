---
title: Adobe Experience Manager as a Cloud Service의 Cloud Manager 2023.4.0 릴리스 정보
description: AEM as a Cloud Service의 Cloud Manager 2023.4.0 릴리스 정보입니다.
feature: Release Information
exl-id: 9c73d7ab-c2c2-4803-a07b-e9054220c6b2
source-git-commit: be39b09b609cccff916db462af9a84149d23a698
workflow-type: tm+mt
source-wordcount: '186'
ht-degree: 50%

---


# Adobe Experience Manager as a Cloud Service의 Cloud Manager 2023.4.0 릴리스 정보 {#release-notes}

이 페이지에서는 AEM as a Cloud Service의 Cloud Manager 2023.4.0 릴리스 정보에 대해 설명합니다.

>[!NOTE]
>
>Adobe Experience Manager as a Cloud Service의 최신 릴리스 정보는 [이 페이지](/help/release-notes/release-notes-cloud/release-notes-current.md)를 참조하십시오.

## 릴리스 일자 {#release-date}

AEM as a Cloud Service의 Cloud Manager 릴리스 2023.4.0의 릴리스 날짜는 2023년 4월 13일입니다. 다음 릴리스는 2023년 11월 5일에 예정되어 있습니다.

## 새로운 기능 {#what-is-new}

* [AEM 프로젝트 원형](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html) 이 버전 41로 업데이트되었습니다.

## 버그 수정 {#bug-fixes}

* 다음의 경우 [인증서](/help/implementing/cloud-manager/managing-ssl-certifications/introduction.md) 만료, [도메인 이름](/help/implementing/cloud-manager/custom-domain-names/introduction.md) 및 [IP 허용 목록](/help/implementing/cloud-manager/ip-allow-lists/introduction.md) 인증서와 연결된 인증서는 CDN에서 더 이상 제거되지 않습니다.  이런 경우 사이트에 계속 도달할 수 있습니다.
* Cloud Manager UI는 [SSL 인증서](/help/implementing/cloud-manager/managing-ssl-certifications/introduction.md) 이(가) 곧 만료됩니다.
* 고객이 새 환경을 만들거나 환경을 삭제할 수 없는 드문 상황이 수정되었습니다.
