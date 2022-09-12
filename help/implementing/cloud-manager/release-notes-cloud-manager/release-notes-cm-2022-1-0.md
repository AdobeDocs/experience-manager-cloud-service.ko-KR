---
title: AEM as a Cloud Service 릴리스 2022.01.0의 Cloud Manager 릴리스 노트
description: 다음은 AEM as a Cloud Service 릴리스의 Cloud Manager에 대한 릴리스 2022.01.0.
feature: Release Information
exl-id: 2dfdc943-0518-40ea-8712-1dabb97eeaa9
source-git-commit: 6e394aaabcb123aea53fba49684aaade3e6c87a6
workflow-type: tm+mt
source-wordcount: '246'
ht-degree: 62%

---

# Adobe Experience Manager as a Cloud Service 2022.01.0의 Cloud Manager 릴리스 노트 {#release-notes}

이 페이지에서는 AEM as a Cloud Service에서 Cloud Manager에 대한 릴리스 노트를 간략하게 설명합니다.

>[!NOTE]
>
>을(를) 참조하십시오. [이 페이지](/help/release-notes/release-notes-cloud/release-notes-current.md) Adobe Experience Manager as a Cloud Service에 대한 최신 릴리스 노트 를 참조하십시오.

## 릴리스 날짜 {#release-date}

AEM as a Cloud Service 2022.01.0의 Cloud Manager 릴리스 날짜는 2022년 1월 20일입니다. 다음 릴리스는 2022년 2월 10일에 예정되어 있습니다.

## 새로운 기능 {#what-is-new}

* Cloud Manager는 [동일한 Git Commit이 여러 전체 스택 파이프라인 실행에 사용되는 것을 감지하면 코드 베이스를 다시 빌드하지 않습니다](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/setting-up-project.md#build-artifact-reuse).
* 이제 AEM 환경 로그에 액세스하려면 **Deployment Manager** 제품 프로필이 필요합니다. 이 프로필이 없는 사용자에게는 사용자 인터페이스에서 비활성화된 버튼이 표시됩니다.
* UI는 Sites가 솔루션으로 활성화되지 않은 프로그램에 대한 프론트엔드 파이프라인 구성을 허용하지 않습니다.
* Git 암호 생성 시 만료 날짜가 표시됩니다.

## 버그 수정 {#bug-fixes}

* 일부 프론트엔드 파이프라인 배포에서 발생한 Null 포인터 예외가 수정되었습니다.
* 이제 환경에서 오래된 버전의 AEM을 실행할 때 환경 변수를 추가, 업데이트 및 삭제할 수 있습니다.
* 드문 경우지만 예약된 단계를 사용한 파이프라인에 대해 빌드 이미지 단계가 더 이상 오류로 표시되지 않습니다.
* 저장소가 하나만 있는 프로그램의 경우 이제 파이프라인 실행 화면에 저장소 이름이 표시됩니다.
