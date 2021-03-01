---
title: 사용자 및 역할 추가 - 필요한 항목
description: 사용자 및 역할 추가 - 필요한 항목
translation-type: tm+mt
source-git-commit: 2c21414edd6c3178d05c818d2bf57aa152b5956b
workflow-type: tm+mt
source-wordcount: '274'
ht-degree: 2%

---


# 사용자 및 역할 추가 {#add-users-roles}


[!UICONTROL Cloud Manager]의 많은 기능을 사용하려면 특정 권한이 필요합니다.

[!UICONTROL 클라우드 ] 관리자는 현재 특정 기능의 가용성을 제어하는 4가지 역할을 정의합니다.

* 비즈니스 소유자
* 프로그램 관리자
* 배포 관리자
* 개발자

>[!CAUTION]
>
>[!UICONTROL Cloud Manager]를 사용하려면 Adobe ID 및 Adobe Experience Manager이 Cloud Service 제품 컨텍스트로 있어야 합니다.

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

## 통합 제품 프로필 {#integration-product-profile}

위의 내용 외에도 Cloud Manager는 &quot;통합 - Cloud Service&quot;라는 제품 프로필을 자동으로 생성합니다. 이 제품 프로필은 Adobe Experience Manager과 다른 Adobe 제품 간의 통합에 사용됩니다. 이 제품 프로필 **은(는)**&#x200B;을(를) 삭제할 수 없습니다. 이 프로필을 실수로 삭제한 경우에는 수동으로 다시 만들어야 합니다. 이 프로필 **의 표시 이름은**&#x200B;이(가) `CM_CS_DEFAULT`여야 합니다.
