---
title: AEM as a Cloud Service 릴리스 2021.5.0의 Cloud Manager 릴리스 노트
description: AEM as a Cloud Service 릴리스 2021.5.0의 Cloud Manager 릴리스 노트
feature: Release Information
exl-id: 9a0a53d3-31d4-493d-ba2e-b4bb22f60351
source-git-commit: 940a01cd3b9e4804bfab1a5970699271f624f087
workflow-type: tm+mt
source-wordcount: '420'
ht-degree: 3%

---

# Adobe Experience Manager as a Cloud Service 2021.6.0의 Cloud Manager 릴리스 노트 {#release-notes}

이 페이지에서는 AEM as a Cloud Service 2021.6.0에 있는 Cloud Manager 릴리스 노트를 간략하게 설명합니다.

>[!NOTE]
>Adobe Experience Manager as a Cloud Service의 현재 릴리스 노트를 보려면 [여기](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/release-notes/release-notes/release-notes-current.html).

## 릴리스 날짜 {#release-date}

AEM as a Cloud Service 2021.6.0의 Cloud Manager 릴리스 날짜는 2021년 6월 10일입니다.

### 새로운 기능 {#what-is-new}

* 미리 보기 서비스는 모든 프로그램에 롤링 기반으로 배포됩니다. 미리 보기 서비스에 대해 프로그램이 활성화되면 고객에게 제품 내 알림을 보냅니다. 을(를) 참조하십시오. [미리 보기 서비스 액세스](/help/implementing/cloud-manager/manage-environments.md#access-preview-service) 자세한 내용

* 이제 빌드 단계 중에 다운로드한 Maven 종속성이 파이프라인 실행 간에 캐시됩니다. 이 기능은 다음 몇 주 동안 고객에 대해 활성화됩니다.

* 이제 프로그램 편집 대화 상자를 통해 프로그램 이름을 편집할 수 있습니다.

* 프로젝트를 만드는 동안 및 git 워크플로우 관리를 통한 기본 푸시 명령에 사용된 기본 분기 이름이 `main`.

* UI에서 프로그램 편집 환경을 새로 고쳤습니다.

* 품질 규칙 `ImmutableMutableMixCheck` 을(를) 분류하도록 업데이트했습니다 `/oak:index` 노드를 변경할 수 없습니다.

* 품질 규칙 `CQBP-84` 및 `CQBP-84--dependencies` 는 단일 규칙으로 통합되었습니다. 이 통합의 일부로, 종속성을 스캔하면 AEM 런타임으로 배포되는 타사 종속성의 문제를 보다 정확하게 식별할 수 있습니다.

* 혼동을 방지하기 위해 환경 세부 사항 페이지의 AEM 게시 및 Dispatcher 세그먼트 행이 통합되었습니다.

   ![](/help/implementing/cloud-manager/release-notes-cloud-manager/assets/aem-dispatcher.png)

* 구조의 유효성을 확인하기 위해 새 코드 품질 규칙이 추가되었습니다 `damAssetLucene` 인덱스. 을(를) 참조하십시오. [사용자 지정 DAM 자산 Lucene Oak 색인](/help/implementing/cloud-manager/custom-code-quality-rules.md#oakpal-damAssetLucene-sanity-check) 자세한 내용

* 이제 환경 세부 사항 페이지에 게시 및 미리 보기 서비스의 여러 도메인 이름이 표시됩니다(해당하는 경우). 을(를) 참조하십시오. [환경 세부 사항](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/manage-environments.html?lang=en#viewing-environment) 추가 정보.

### 버그 수정 {#bug-fixes}

* 루트 요소 이름을 올바르게 구문 분석한 후 새 행을 포함하는 JCR 노드 정의가 있습니다.

* 목록 저장소 API는 삭제된 저장소를 필터링하지 않습니다.

* 예약 단계에 잘못된 값을 제공한 경우 잘못된 오류 메시지가 표시되었습니다.

* 경우에 따라 사용자가 녹색으로 표시될 수 있습니다 *활성* 구성을 배포하지 않은 경우에도 IP 허용 목록 옆에 표시됩니다.

* 일부 프로그램 편집 시퀀스는 프로덕션 파이프라인을 만들거나 편집할 수 없게 될 수 있습니다.

* 일부 프로그램 편집 시퀀스는 **개요** 프로그램 설정을 다시 실행하는 데 잘못된 메시지가 표시되는 페이지입니다.
