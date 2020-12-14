---
title: 사용자 및 역할 추가 - 필요한 항목
description: 사용자 및 역할 추가 - 필요한 항목
translation-type: tm+mt
source-git-commit: 936e42f273b75f0ea7776c51f57af44ec9e6d96f
workflow-type: tm+mt
source-wordcount: '228'
ht-degree: 3%

---


# 사용자 및 역할 추가 {#add-users-roles}


[!UICONTROL Cloud Manager]의 많은 기능을 사용하려면 특정 권한이 필요합니다. 예를 들어 특정 사용자만 프로그램의 주요 성능 지표(KPI)를 설정할 수 있습니다. 이러한 권한은 논리적으로 역할로 그룹화됩니다.

[!UICONTROL 클라우드 ] 관리자는 현재 특정 기능의 가용성을 제어하는 4가지 역할을 정의합니다.

* 비즈니스 소유자
* 프로그램 관리자
* 배포 관리자
* 개발자

>[!CAUTION]
>
>[!UICONTROL 클라우드 관리자]를 사용하려면 Adobe ID 및 Adobe Managed Services 제품 컨텍스트가 있어야 합니다.

## 역할 정의 {#role-definitions}

>[!NOTE]
>
>Admin Console의 개발자 모습은 [!UICONTROL 클라우드 관리자]의 개발자 역할과 관련이 없습니다.

다음 표에 역할이 요약되어 있습니다.

| [!UICONTROL 클라우드 ] 관리자 역할 | 설명 |
|--- |--- |
| 비즈니스 소유자 | KPI 정의, 제작 배포 승인 및 중요한 3-계층 오류 덮어쓰기에 대한 책임입니다. |
| 프로그램 관리자 | [!UICONTROL 클라우드 관리자]를 사용하여 팀 설정을 수행하고, 상태를 검토하고 KPI를 봅니다. 중요한 3-계층 오류를 승인할 수 있습니다. |
| 배포 관리자 | 배포 작업을 관리합니다. [!UICONTROL 클라우드 관리자]를 사용하여 스테이지/프로덕션 배포를 실행합니다. CI/CD 파이프라인을 편집할 수 있습니다. 중요한 3-계층 오류를 승인할 수 있습니다. Git 리포지토리에 액세스할 수 있습니다. |
| 개발자 | 사용자 정의 응용 프로그램 코드를 개발하고 테스트합니다. 주로 [!UICONTROL 클라우드 관리자]를 사용하여 상태를 봅니다. 코드 커밋을 위해 Git 리포지토리에 액세스할 수 있습니다. |
| 컨텐츠 작성자 | 일반적으로 [!UICONTROL 클라우드 관리자]와 상호 작용하지 않습니다. [!UICONTROL 클라우드 관리자] 프로그램 전환기([!UICONTROL Experience Cloud]에서 이동)를 사용하여 AEM에 액세스할 수 있습니다. |