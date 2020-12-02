---
title: Cloud Service 릴리스 2020.6.0으로서 AEM의 Cloud Manager에 대한 릴리스 노트
description: Cloud Service 릴리스 2020.6.0으로서 AEM의 Cloud Manager에 대한 릴리스 노트
translation-type: tm+mt
source-git-commit: ca690144a8254d5ffba354f0f96d9ef1c5202533
workflow-type: tm+mt
source-wordcount: '612'
ht-degree: 89%

---


# Cloud Service 2020.6.0인 Adobe Experience Manager의 클라우드 관리자에 대한 릴리스 노트 {#release-notes}

이 페이지에서는 AEM의 Cloud Manager 릴리스 노트를 Cloud Service 2020.6.0으로 간략하게 설명합니다.

## 릴리스 날짜 {#release-date}

2020.6.0 Cloud Service으로 AEM에서 Cloud Manager의 릴리스 날짜는 2020년 6월 4일입니다.

## 새로운 기능 {#whats-new-cloud-manager}

* Cloud Manager의 *비즈니스 소유자* 역할의 사용자는 이제 랜딩 페이지(프로그램 카드의 빠른 작업 단추)나 프로그램 내에서 샌드박스 프로그램을 삭제할 수 있습니다.

   자세한 내용은 [샌드박스 프로그램 삭제](https://docs.adobe.com/content/help/ko-KR/experience-manager-cloud-service/onboarding/getting-access/cloud-service-programs/creating-a-program.html)를 참조하십시오.

* Cloud Manager의 *비즈니스 소유자* 또는 *배포 관리자* 역할의 샌드박스 프로그램 사용자는 이제 클라우드 관리자 UI를 통해 프로덕션 및 스테이지 환경 세트를 삭제할 수 있습니다. 이제 **프로그램 개요** 페이지와 **환경** 페이지의 환경 카드 모두에서 삭제 옵션을 사용할 수 있습니다 . 프로덕션 또는 스테이지에서 삭제 옵션을 선택하면 세트에 있는 다른 옵션도 삭제됩니다.

   자세한 내용은 [샌드박스 프로그램 삭제](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/onboarding/getting-access/cloud-service-programs/creating-a-program.html)를 참조하십시오.

* 랜딩 페이지의 코치 표시를 사용하여 사용자에게 기본 탐색에 대해 알리고 지시합니다.

* **프로그램 개요** 페이지의 코치 표시의 내용을 참조하여 Cloud Manager 내의 기본 탐색에 대해 알리고 지시할 수 있습니다.

* 이제 **LEARN** 페이지를 Cloud Manager에서 사용할 수 있으며 위쪽 탐색을 통해 액세스할 수 있습니다. 이 페이지에는 Cloud Manager에서 할당된 역할과 관련하여 가장 자주 사용되는 워크플로우에 대한 사용자 학습을 돕는 리소스가 포함되어 있습니다.

* 이제 샌드박스 프로그램은 **프로그램 개요** 페이지의 프로그램 이름 옆에 있을 뿐 아니라 랜딩 페이지의 프로그램 카드에 표시될 **샌드박스** 배지로 식별됩니다.

* 이제 SysAdmin 역할의 사용자는 Cloud Manager에 대한 사용자 역할이나 권한을 관리할 수 있는 Admin Console의 위치에 클릭 한 번으로 액세스할 수 있습니다. 이제 **액세스 관리** 단추를 **프로그램 추가** 단추 옆에 있는 랜딩 페이지에서 사용할 수 있습니다.

   자세한 내용은 [SysAdmin 작업](https://docs.adobe.com/content/help/ko-KR/experience-manager-cloud-service/onboarding/getting-access/navigation.html#sysadmin-tasks)을 참조하십시오.

* 이제 SysAdmin 역할의 사용자는 Cloud Manager에서 직접 작성자 인스턴스에 한 번의 클릭으로 액세스할 수 있습니다.

   자세한 내용은 [작성자 인스턴스에 대한 액세스 관리](https://docs.adobe.com/content/help/ko-KR/experience-manager-cloud-service/onboarding/getting-access/navigation.html#manage-access-aem)를 참조하십시오.

* 이제 빌드 로그에는 생략된 컨텐츠 패키지를 포함하여 검색된 객체 목록이 포함됩니다.

* 빌드 단계에서 이제 생성된 모든 컨텐츠 패키지에 이름, 그룹 및 버전과 같은 모든 필수 속성이 포함되어 있는지 확인합니다.

* 빌드 단계에서 이제 빌드가 하나 이상의 컨텐츠 패키지를 생성했는지 확인합니다.

### 버그 수정 {#bug-fixes-cm}

* **프로그램 만들기** 대화 상자의 아이콘이 잘못 정렬된 경우가 있었습니다.

* AEM 릴리스 식별자가 **프로그램 개요** 페이지에 일관되게 표시되지 않았습니다.

* 프로덕션 파이프라인을 구성할 때 일부 고객은 **예약된 배포** 옵션을 볼 수 없었습니다.

### 알려진 문제 {#known-issues-cm}

* 샌드박스 프로그램 내의 환경은 특정 기간에 활동이 감지되지 않으면 최대 절전 모드로 전환됩니다. 이 상태는 Cloud Manager에서 관찰되지 않습니다. 하지만 개발자 콘솔을 통해 상태를 확인할 수 있습니다. 이 문제는 향후 릴리스에서 해결될 예정입니다.

* Cloud Manager에서 직접 개발자 콘솔로 연결되는 링크에는 샌드박스 프로그램 환경의 최대 절전 모드 해제/최대 절전 모드 해제 옵션이 표시되지 않습니다. 이 문제를 해결하려면 개발자 콘솔에서 `#release-cm-p1234-e5678` 패턴을 URL 끝에 추가합니다. 여기서 *1234*&#x200B;를 프로그램 ID이고 *5678*&#x200B;은 환경 ID입니다. 이 문제는 향후 릴리스에서 해결될 예정입니다.
