---
title: AEM as a Cloud Service 릴리스 2021.5.0의 Cloud Manager 릴리스 노트
description: AEM as a Cloud Service 릴리스 2021.5.0의 Cloud Manager 릴리스 노트
feature: 릴리스 정보
source-git-commit: 3f579f6871da8e8b2fcea921e5abf57dfc14f5f8
workflow-type: tm+mt
source-wordcount: '394'
ht-degree: 3%

---


# Adobe Experience Manager as a Cloud Service 2021.6.0 {#release-notes} 의 Cloud Manager 릴리스 노트

이 페이지에서는 AEM as a Cloud Service 2021.6.0 Cloud Manager 릴리스 노트를 간략하게 설명합니다.

>[!NOTE]
>Adobe Experience Manager as a Cloud Service에 대한 현재 릴리스 노트를 보려면 [여기](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/release-notes/release-notes/release-notes-current.html?lang=ko-KR)를 클릭하십시오.

## 릴리스 날짜 {#release-date}

AEM as a Cloud Service 2021.6.0의 Cloud Manager 릴리스 날짜는 2021년 6월 10일입니다.
다음 릴리스는 2021년 7월 15일에 예정되어 있습니다.

### 새로운 기능 {#what-is-new}

* 미리 보기 서비스는 모든 프로그램에 롤링 기반으로 배포됩니다. 미리 보기 서비스에 대해 프로그램이 활성화되면 고객에게 제품 내 알림을 보냅니다. 자세한 내용은 [미리 보기 서비스 액세스](/help/implementing/cloud-manager/manage-environments.md#access-preview-service)를 참조하십시오.

* 이제 빌드 단계 중에 다운로드한 Maven 종속성이 파이프라인 실행 간에 캐시됩니다. 이 기능은 다음 몇 주 동안 고객에 대해 활성화됩니다.

* 이제 프로그램 편집 대화 상자를 통해 프로그램 이름을 편집할 수 있습니다.

* 프로젝트를 만드는 동안 및 git 워크플로우 관리를 통한 기본 푸시 명령에 사용된 기본 분기 이름이 `main`(으)로 변경되었습니다.

* UI에서 프로그램 편집 환경을 새로 고쳤습니다.

* `/oak:index` 노드를 변경할 수 없는 것으로 분류하도록 품질 규칙 `ImmutableMutableMixCheck`이 업데이트되었습니다.

* 품질 규칙 `CQBP-84` 및 `CQBP-84--dependencies`이(가) 단일 규칙으로 통합되었습니다.

* 혼동을 방지하기 위해 환경 세부 사항 페이지의 AEM 게시 및 Dispatcher 세그먼트 행이 통합되었습니다.

   ![](/help/onboarding/release-notes-cloud-manager/assets/aem-dispatcher.png)

* `damAssetLucene` 인덱스 구조의 유효성을 확인하기 위해 새 코드 품질 규칙이 추가되었습니다. 자세한 내용은 [사용자 지정 DAM Asset Lucene Oak 색인](/help/implementing/cloud-manager/custom-code-quality-rules.md#oakpal-damAssetLucene-sanity-check)을 참조하십시오.

* 이제 환경 세부 사항 페이지에 게시 및 미리 보기 서비스의 여러 도메인 이름이 표시됩니다(해당하는 경우). 자세한 내용은 [환경 세부 정보](/help/implementing/cloud-manager/manage-environments.md#viewing-environment) 를 참조하십시오.

### 버그 수정 {#bug-fixes}

* 루트 요소 이름을 올바르게 구문 분석한 후 새 행을 포함하는 JCR 노드 정의가 있습니다.

* 목록 저장소 API는 삭제된 저장소를 필터링하지 않습니다.

* 예약 단계에 잘못된 값을 제공한 경우 잘못된 오류 메시지가 표시되었습니다.

* 구성이 배포되지 않은 경우에도 IP 허용 목록 옆에 녹색 *활성* 상태가 표시될 수 있습니다.

* 일부 프로그램 편집 시퀀스는 프로덕션 파이프라인을 만들거나 편집할 수 없게 될 수 있습니다.

* 일부 프로그램 편집 시퀀스는 **개요** 페이지에 프로그램 설정을 다시 실행하기 위한 잘못된 메시지가 표시될 수 있습니다.
