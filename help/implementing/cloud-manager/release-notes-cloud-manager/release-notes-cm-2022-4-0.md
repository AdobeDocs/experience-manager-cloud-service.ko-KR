---
title: Adobe Experience Manager as a Cloud Service Cloud Manager 2022.4.0의 릴리스 노트
description: 다음은 AEM as a Cloud Service의 Cloud Manager 2022.4.0에 대한 릴리스 노트입니다.
feature: Release Information
exl-id: e7ff623b-aeca-40a6-bf48-98af270a4117
source-git-commit: 458d63c27bb2ab4d09237aa3ecb96c0f6d5e67ed
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 3%

---

# Adobe Experience Manager as a Cloud Service Cloud Manager 2022.4.0의 릴리스 노트 {#release-notes}

이 페이지에서는 AEM as a Cloud Service의 Cloud Manager 2022.4.0에 대한 릴리스 노트를 문서화합니다.

>[!NOTE]
>
>을(를) 참조하십시오. [이 페이지](/help/release-notes/release-notes-cloud/release-notes-current.md) Adobe Experience Manager as a Cloud Service에 대한 최신 릴리스 노트 를 참조하십시오.

## 릴리스 날짜 {#release-date}

AEM as a Cloud Service의 Cloud Manager 릴리스 2022.4.0의 출시일은 2022년 4월 7일입니다. 다음 릴리스는 2022년 5월 5일에 예정되어 있습니다.

## 새로운 기능 {#what-is-new}

* 파이프라인 빌드 단계의 지속 시간 및 성공률에 대한 개선 사항이 구현되었으며 4월 말까지 모든 고객에게 점진적으로 출시됩니다.
* 이제 파이프라인 추가 및 편집 마법사의 입력 필드에 이름의 처음 몇 개의 문자를 입력하고 둘 다에 대해 제안된 일치 항목 중에서 선택하여 git 분기를 쉽게 찾을 수 있습니다 [production](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md) 및 [비프로덕션](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md) 파이프라인.
* 4월 릴리스 직후 인도는 환경 생성 중에 클라우드 영역을 정의할 때 선택할 수 있습니다.
* 다음 **파이프라인** 이제 페이지에 많은 파이프라인이 있는 프로그램에 대한 유용성을 개선하기 위해 페이지 매김이 있습니다.
   * 페이지당 50개의 행이 테이블에 표시됩니다.
* 버전 [AEM 프로젝트 원형](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html) cloud Manager에서 사용하는 버전이 버전 36으로 업데이트되었습니다.
* Oracle JDK는 이제 AEM 애플리케이션 개발 및 작업을 위한 기본 JDK입니다. Maven 도구 체인에서 대체 옵션을 명시적으로 선택한 경우에도 Cloud Manager 빌드 프로세스는 Oracle JDK를 사용하여 자동으로 로 전환됩니다.
   * oracle JDK로 전환하는 방법에 대한 자세한 내용은 [빌드 환경 설명서입니다.](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/build-environment-details.md#using-java-support)
   * 자세한 내용은 [Adobe Experience Manager에 대한 Java 지원 정책 FAQ](https://experienceleague.adobe.com/docs/experience-manager-65/assets/Java_Policy_for_Adobe_Experience_Manager.pdf) 이 변경에 대한 일반적인 질문에 답하기 위해
* 이제 유효성 검사 단계 동안 이전 AEM 버전을 감지하여 파이프라인 실행이 더 빨리 실패합니다. 사용자에게 안내하는 메시지가 UI에 표시됩니다.

## 버그 수정 {#bug-fixes}

* 이제 UI 테스트 단계에서 생성된 로그를 UI를 통해 다운로드할 수 있습니다.
* 이제 웹 계층 구성 파이프라인은 웹 계층 구성 실행의 패키지만 재사용할 수 있습니다.
* 오래된 환경에서 AEM을 업데이트하는 방법에 대해 UI의 메시지에 더 명확하게 추가되었습니다.
