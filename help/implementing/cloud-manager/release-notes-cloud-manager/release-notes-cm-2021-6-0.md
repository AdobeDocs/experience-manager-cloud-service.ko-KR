---
title: AEM as a Cloud Service 릴리스 2021.6.0의 Cloud Manager 릴리스 정보
description: AEM as a Cloud Service 릴리스 2021.5.0의 Cloud Manager 릴리스 정보
feature: Release Information
exl-id: 9a0a53d3-31d4-493d-ba2e-b4bb22f60351
source-git-commit: 4b76fbbb1b58324065b39d6928027759b0897246
workflow-type: tm+mt
source-wordcount: '420'
ht-degree: 100%

---

# Adobe Experience Manager as a Cloud Service 2021.6.0의 Cloud Manager 릴리스 정보 {#release-notes}

이 페이지에서는 AEM as a Cloud Service 2021.6.0의 Cloud Manager 릴리스 정보에 대해 간략히 설명합니다.

>[!NOTE]
>Adobe Experience Manager as a Cloud Service의 최신 릴리스 정보를 보려면 [여기](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/release-notes/release-notes/release-notes-current.html)를 클릭하십시오.

## 릴리스 일자 {#release-date}

AEM as a Cloud Service 2021.6.0의 Cloud Manager 릴리스 일자는 2021년 6월 10일입니다.

### 새로운 기능 {#what-is-new}

* 미리보기 서비스가 모든 프로그램에 순차적으로 배포됩니다. 고객은 미리보기 서비스에 대해 프로그램이 활성화될 때 제품 내에서 알림을 받게 됩니다. 자세한 내용은 [미리보기 서비스 액세스](/help/implementing/cloud-manager/manage-environments.md#access-preview-service)를 참조하십시오.

* 이제 빌드 단계 중 다운로드된 Maven 종속 항목이 파이프라인 실행 사이에 캐시됩니다. 이 기능은 다음 몇 주 이내에 고객에 대해 활성화됩니다.

* 이제 프로그램 편집 대화 상자를 통해 프로그램 이름을 편집할 수 있습니다.

* 프로젝트 생성 중 및 git 워크플로 관리를 통한 기본 푸시 명령에 사용된 기본 분기 이름이 `main`으로 변경되었습니다.

* UI의 프로그램 편집 환경이 새로워졌습니다.

* 품질 규칙 `ImmutableMutableMixCheck`가 `/oak:index` 노드를 변경 불가로 분류하도록 업데이트되었습니다.

* 품질 규칙 `CQBP-84` 및 `CQBP-84--dependencies`가 단일 규칙으로 통합되었습니다. 이 통합의 일부로 종속 항목의 스캐닝이 AEM 런타임에 배포되는 서드파티 종속 항목의 문제를 보다 정확하게 식별할 수 있습니다.

* 혼란을 방지하기 위해 환경 세부 정보 페이지의 Publish AEM 행 및 Publish Dispatcher 세그먼트 행이 통합되었습니다.

   ![](/help/implementing/cloud-manager/release-notes-cloud-manager/assets/aem-dispatcher.png)

* `damAssetLucene` 인덱스 구조를 확인하기 위해 새 코드 품질 규칙이 추가되었습니다. [사용자 정의 DAM Asset Lucene Oak 인덱스](/help/implementing/cloud-manager/custom-code-quality-rules.md#oakpal-damAssetLucene-sanity-check)를 참조하십시오.

* 이제 해당되는 경우 환경 세부 정보 페이지에 Publish 및 미리보기 서비스에 대한 여러 도메인 이름이 표시됩니다. 자세한 내용은 [환경 세부 정보](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/manage-environments.html?lang=ko#viewing-environment)를 참조하십시오.

### 버그 수정 {#bug-fixes}

* 루트 요소 이름 뒤에 새 줄이 포함된 JCR 노드 정의가 올바르게 구문 분석되지 않았습니다.

* 목록 저장소 API가 삭제된 저장소를 필터링하지 않았습니다.

* 예약 단계에 잘못된 값이 제공되었을 때 잘못된 오류 메시지가 표시되었습니다.

* 해당 구성이 배포되지 않은 경우에도 IP 허용 목록 옆에 녹색 *활성* 상태가 표시되는 경우가 있었습니다.

* 일부 프로그램 편집 시퀀스로 인해 프로덕션 파이프라인을 만들거나 편집하지 못할 수 있습니다.

* 일부 프로그램 편집 시퀀스로 인해 **개요** 페이지에 프로그램 설정을 다시 실행하라는 잘못된 메시지가 표시될 수 있습니다.
