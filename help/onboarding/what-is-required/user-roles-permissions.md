---
title: 사용자 역할 및 권한
description: 이 페이지에서는 사용자 역할 및 권한을 설명합니다. 사용자를 추가하고 Cloud Manager 역할에 할당하는 방법을 알려면 이 페이지를 따르십시오.
translation-type: tm+mt
source-git-commit: f1f5766a41763634e0aaba44e55471ac2ea5dc8f
workflow-type: tm+mt
source-wordcount: '624'
ht-degree: 6%

---


# 사용자 역할 및 권한 {#user-roles-permissions}

Adobe은 IMS(Adobe Identity Management System)에서 회사에 대한 **조직** 식별자를 만들어 모든 사용자와 해당 권한을 관리할 수 있습니다. 이 조직의 구성원이 되어야 하고 [!UICONTROL Experience Cloud] 서비스에 대한 액세스 권한을 받는 각 사용자는 자신의 **[Adobe ID](/help/onboarding/what-is-required/get-your-adobe-id.md)**&#x200B;을(를) 가지고 있어야 합니다.

## 사용자 역할 {#user-roles}

Cloud Manager의 많은 기능을 사용하려면 특정 권한이 필요합니다.

Cloud Manager의 많은 기능은 특정 권한을 필요로 하며, 할당된 역할 및 권한에 따라 사용자 인터페이스에서 수행하는 작업을 제한합니다. 경우에 따라 작업을 수행할 권한이 없으면 인터페이스 컨트롤이 있지만 비활성화됩니다.

수행할 작업이 있지만 수행할 수 없는 경우에는 역할 정의](#permissions)에 연결된 [권한을 확인하십시오. 목표에 따라 시스템 관리자에게 연락하여 필요한 역할을 요청할 수 있습니다.

Cloud Manager는 현재 특정 기능의 가용성을 제어하는 4개의 역할을 정의합니다.

* 비즈니스 소유자
* 배포 관리자
* 프로그램 관리자
* 개발자

>[!NOTE]
>Admin Console의 개발자 모습은 [!UICONTROL 클라우드 관리자]의 개발자 역할과 관련이 없습니다.

## 역할 정의 {#role-definitions}

다음 표에 역할이 요약되어 있습니다.

| [!UICONTROL 클라우드 ] 관리자 역할 | 설명 |
|--- |--- |
| 비즈니스 소유자 | KPI 정의, 제작 배포 승인 및 중요한 3-계층 오류 덮어쓰기에 대한 책임입니다. |
| 프로그램 관리자 | [!UICONTROL 클라우드 관리자]를 사용하여 팀 설정을 수행하고, 상태를 검토하고 KPI를 봅니다. 중요한 3-계층 오류를 승인할 수 있습니다. |
| 배포 관리자 | 배포 작업을 관리합니다. [!UICONTROL 클라우드 관리자]를 사용하여 스테이지/프로덕션 배포를 실행합니다. CI/CD 파이프라인을 편집할 수 있습니다. 중요한 3-계층 오류를 승인할 수 있습니다. Git 리포지토리에 액세스할 수 있습니다. |
| 개발자 | 사용자 정의 응용 프로그램 코드를 개발하고 테스트합니다. 주로 [!UICONTROL 클라우드 관리자]를 사용하여 상태를 봅니다. 코드 커밋을 위해 Git 리포지토리에 액세스할 수 있습니다. |
| 컨텐츠 작성자 | 일반적으로 [!UICONTROL 클라우드 관리자]와 상호 작용하지 않습니다. [!UICONTROL 클라우드 관리자] 프로그램 전환기([!UICONTROL Experience Cloud]에서 이동)를 사용하여 AEM에 액세스할 수 있습니다. |

### 역할 보기 {#view-roles}

Cloud Manager에서 역할을 보려면 Cloud Manager UI에 로그인하고 오른쪽 상단 모서리에서 프로필 아이콘을 선택하고 아래 그림과 같이 **사용자 역할**&#x200B;을 선택합니다.

![](/help/onboarding/what-is-required/assets/admin-console-9.png)

### 통합 제품 프로필 {#integration-product-profile}

위의 내용 외에도 Cloud Manager는 &quot;통합 - Cloud Service&quot;라는 제품 프로필을 자동으로 생성합니다. 이 제품 프로필은 Adobe Experience Manager과 다른 Adobe 제품 간의 통합에 사용됩니다. 이 제품 프로필 **은(는)**&#x200B;을(를) 삭제할 수 없습니다. 이 프로필을 실수로 삭제한 경우에는 수동으로 다시 만들어야 합니다. 이 프로필 **의 표시 이름은**&#x200B;이(가) `CM_CS_DEFAULT`여야 합니다.


## 역할 정의와 연결된 권한 {#permissions}

[!UICONTROL Cloud Manager에는 적절한 권한이 있는 미리 구성된 역할이 있습니다. ] 예를 들어 개발자는 코드를 개발하고 **Git 리포지토리**&#x200B;에 코드를 푸시할 권한이 있습니다. 또는 비즈니스 소유자는 KPI(Key Performance Indicator)를 정의하고 배포를 승인할 수 있는 다양한 권한을 갖습니다.


각 역할에는 각 역할과 연관된 특정 권한이 있습니다. 다음 표는 역할을 요약하고 사용 가능한 함수 및 함수를 실행할 수 있는 역할을 나열합니다.

| 권한 | 설명 | 비즈니스 소유자 | 배포 관리자 | 프로그램 관리자 | 개발자 |
|--- |--- |--- |--- |--- |--- |
| 프로그램 추가 | 새 프로그램 추가를 참조하십시오. | x |  |  |  |
| 환경 만들기 | Prod+Stage, Dev, Environment를 작성합니다. | x | x |  |  |
| 환경 업데이트 | Prod+Stage, Dev, 환경을 업데이트합니다. | x | x |  |  |
| 환경 삭제 | 비제품, 개발, 환경 삭제를 참조하십시오. | x | x |  |  |
| 파이프라인 설정 | 파이프라인 설정 또는 편집을 참조하십시오. |  | x |  |  |
| 파이프라인 실행 | 파이프라인을 시작합니다. | x | x |  |  |
| 파이프라인 실행 | 중요한 3계층 오류 거부/승인 | x | x | x |  |
| 파이프라인 실행 | GoLive 승인을 제공합니다. | x | x | x |  |
| 파이프라인 실행 | 프로덕션 배포 일정을 참조하십시오. | x | x | x |  |
| 파이프라인 삭제 | 파이프라인 삭제를 허용합니다. |  | x |  |  |
| 실행 취소 | 현재 실행 취소를 참조하십시오. |  | x |  |  |
| 개인 액세스 토큰 생성 | Git 액세스. |  | x |  | x |