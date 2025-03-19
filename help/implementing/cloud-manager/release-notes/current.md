---
title: Adobe Experience Manager as a Cloud Service의 Cloud Manager 2025.3.0 릴리스 정보
description: AEM as a Cloud Service의 Cloud Manager 2025.3.0 릴리스에 대해 알아봅니다.
feature: Release Information
role: Admin
exl-id: 24d9fc6f-462d-417b-a728-c18157b23bbe
source-git-commit: 663234640f16e6aa653251399751abf5daa17f82
workflow-type: tm+mt
source-wordcount: '329'
ht-degree: 31%

---

# Adobe Experience Manager as a Cloud Service의 Cloud Manager 2025.3.0 릴리스 정보 {#release-notes}

<!-- https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+2025.03.0+Release -->

AEM (Adobe Experience Manager) as a Cloud Service의 Cloud Manager 2025.3.0 릴리스에 대해 알아봅니다.


또한 [최신 Adobe Experience Manager as a Cloud Service 릴리스 정보](/help/release-notes/release-notes-cloud/release-notes-current.md)도 살펴보십시오.

## 릴리스 일자 {#release-date}

AEM as a Cloud Service의 Cloud Manager 2025.3.0 릴리스 일자는 2025년 3월 13일 금요일입니다.

다음 릴리스는 2025년 4월 10일 금요일에 예정되어 있습니다.

## 새로운 기능 {#what-is-new}

* **여러 파이프라인 실행**

  여러 파이프라인을 동시에 실행하는 기능이 파이프라인 페이지에 도입되었습니다. 사용자는 최소 하나 이상 10개 이하의 파이프라인을 선택해야 합니다. 파이프라인 페이지의 오른쪽 상단 모서리에서 **선택한 항목 실행(x)**&#x200B;을 클릭합니다. 시작할 수 없는 파이프라인을 나열하는 모달 대화 상자가 나타납니다. 유효한 모든 파이프라인을 시작하려면 **실행**&#x200B;을 클릭하세요.

  ![선택한 파이프라인 실행 대화 상자](/help/implementing/cloud-manager/release-notes/assets/run-selected-pipelines.png)

  [여러 파이프라인 실행](/help/implementing/cloud-manager/configuring-pipelines/managing-pipelines.md#run-multiple-pipelines)도 참조하세요.

* **Node.js 버전으로 확장 지원**

  이제 프론트엔드 빌드 환경이 다음 `Node.js` 버전을 지원합니다.

   * 23
   * 22
   * 20

  [프론트엔드 파이프라인으로 사이트 개발](/help/implementing/developing/introduction/developing-with-front-end-pipelines.md#node-versions)도 참조하세요. <!-- CMGR-65307 -->

<!--
## Early adoption program {#early-adoption}

Be a part of Cloud Manager's early adoption program and have a chance to test upcoming features. -->


## 버그 수정

* Cloud Manager의 &#39;고급 네트워크 구성&#39; 업데이트에 대한 **(UI) 수정**

  &quot;업데이트 사용 가능&quot; 알림이 있을 때 **고급 네트워크 구성**&#x200B;에 대한 업데이트를 수행할 수 없는 드문 문제가 해결되었습니다. 이전에는 Cloud Manager에서 업데이트 중에 충돌을 방지하기 위해 고급 네트워킹 설정을 포함한 구성 수정을 잠갔습니다. 이제 고객은 보류 중인 업데이트를 수동으로 트리거하여 제한 없이 필요한 변경 사항을 적용할 수 있습니다. <!-- CMGR-65913 and CMGR-65788 -->

* **(UI) IP 허용 목록 업데이트에 대한 수정 사항이 &quot;업데이트 중&quot; 상태에서 중단됨**

  환경에 대한 중복 활성 허용 목록 구성으로 인해 Cloud Manager의 IP 도메인 업데이트가 &quot;업데이트 중&quot; 상태에서 발생한 드문 문제가 해결되었습니다. 이전에는 고객이 IP 허용 목록을 업데이트할 때 처리가 무기한 지연되어 필요한 네트워크 액세스가 조정되지 않았습니다. 이 수정 사항을 통해 중단 없이 IP 허용 목록 업데이트를 완료할 수 있습니다. <!-- CMGR-65786 -->




<!-- ## Known issues {#known-issues} -->
