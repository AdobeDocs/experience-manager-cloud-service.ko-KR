---
title: 사용자 매핑 및 주요 마이그레이션
description: AEMas a Cloud Service 의 사용자 매핑 및 사용자 마이그레이션 개요.
exl-id: 4a35fc46-f641-46a4-b3ff-080d090c593b
source-git-commit: 8c73805b6ed1b7a03c65b4d21a4252c1412a5742
workflow-type: tm+mt
source-wordcount: '837'
ht-degree: 10%

---

# 사용자 매핑 및 주요 마이그레이션 {#user-mapping-and-principal-migration}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_usermapping"
>title="사용자 매핑"
>abstract="콘텐츠 전송 도구는 사용자 및 그룹을 기존 AEM(Adobe Experience Manager) 시스템에서 AEM as a Cloud Service로 이동하는 데 유용합니다. 기존 사용자는 클라우드 서비스 작성자 인스턴스에서 중복되지 않도록 해당 IMS ID에 매핑되어야 합니다."

>[!NOTE]
>이전 버전의 사용자 매핑 도구에 대해서는 [레거시 설명서](/help/journey-migration/content-transfer-tool/user-mapping-tool-legacy/considerations-user-mapping-tool-legacy.md).

## 소개 {#introduction}

Adobe Experience Manager(AEM) as a Cloud Service으로 전환 여정의 일부로 기존 AEM AEM 시스템의 사용자와 그룹을 as a Cloud Service으로 이동해야 합니다. 이 작업은 콘텐츠 전송 도구에서 수행합니다.

AEM as a Cloud Service의 주요 변경 내용은 작성자 계층 액세스에 대한 Adobe ID 사용이 완전히 통합된다는 것입니다. 이 프로세스에는 [Adobe Admin Console](https://helpx.adobe.com/enterprise/using/admin-console.html) 사용자 및 사용자 그룹 관리. 사용자 프로필 정보는 모든 Adobe 클라우드 애플리케이션에서 단일 사인온을 제공하는 IMS(Adobe Identity Management System)에서 중앙 집중화됩니다. 자세한 내용은 [Identity Management](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/overview/what-is-new-and-different.html#identity-management). 이러한 변경 사항으로 인해 Cloud Service 작성자 인스턴스에서 중복 사용자를 방지하려면 기존 사용자를 해당 IMS ID에 매핑해야 합니다. 기존 AEM의 그룹은 IMS의 그룹과 근본적으로 다르므로 그룹은 매핑되지 않지만 마이그레이션이 완료된 후에는 두 그룹 세트를 조정해야 합니다.

## 사용자 마이그레이션 세부 정보 {#user-migration-detail}

컨텐츠 전송 도구 및 Cloud Acceleration Manager 는 마이그레이션 중인 컨텐츠와 관련된 모든 사용자를 클라우드 시스템으로 마이그레이션합니다.

## 사용자 매핑 세부 정보 {#user-mapping-detail}

AEM 사용자는 동일한 이메일 주소로 해당 Adobe IMS 사용자에게 매핑될 수 있습니다.  이 매핑은 CTT에서 자동으로 수행할 수 있으며, 추출을 시작하기 전에 전환을 통해 매핑 여부를 제어할 수 있습니다. 추출을 시작할 때 사용자가 토글의 기본 설정을 재정의할 수 있습니다.

* 소스 시스템이 작성자 인스턴스인 경우 기본적으로 매핑을 수행하기 위한 선택은 입니다. _날짜_, 이는 권장되는 프로세스이기 때문입니다.
* 소스 시스템이 게시 인스턴스인 경우 기본적으로 매핑을 수행하기 위한 선택은 입니다. _끔_, 사용자가 일반적으로 마이그레이션되거나 게시 인스턴스에서 사용되지 않기 때문입니다.

## 사용자 매핑 및 마이그레이션 시 중요 고려 사항 {#important-considerations}


### 예외적인 경우 {#exceptional-cases}

다음과 같은 특정 사례가 기록됩니다.

1. 사용자가에 이메일 주소가 없는 경우 `profile/email` 필드 *jcr* 노드, 해당 사용자 또는 그룹이 마이그레이션될 수 있지만 매핑되지 않았습니다. 이 시나리오는 이메일 주소가 로그인을 위한 사용자 이름으로 사용되는 경우에도 적용됩니다.

1. 사용자가 비활성화된 경우 비활성화된 경우와 동일하게 처리됩니다. 정상적으로 매핑되고 마이그레이션되며 클라우드 인스턴스에서 비활성화됩니다.

1. 소스 AEM 인스턴스의 사용자 중 하나와 동일한 사용자 이름(rep:principalName)을 가진 사용자가 대상 AEM Cloud Service 인스턴스에 있는 경우 해당 사용자는 마이그레이션되지 않습니다.

1. 사용자가 사용자 매핑을 통해 매핑되지 않고 마이그레이션되는 경우 대상 클라우드 시스템에서 IMS ID를 사용하여 로그온할 수 없습니다. 또는 이메일 주소가 IMS에 로그인하는 데 사용되는 이메일 주소와 일치하지 않으면 타겟 클라우드 시스템에서 IMS ID를 사용하여 로그온할 수도 없습니다. 기존 AEM 메서드를 사용하여 로그온할 수 있지만 일반적으로 이 메서드는 원하는 메서드 또는 예상과 다릅니다.


## 추가 고려 사항 {#additional-considerations}

* 다음과 같은 경우 **수집하기 전에 클라우드 인스턴스의 기존 콘텐츠 지우기** 가 설정되어 있으면 Cloud Service 인스턴스에서 이미 전송된 사용자가 기존 저장소 전체와 함께 삭제됩니다. 콘텐츠가 수집되는 새 저장소가 생성됩니다. 또한 이 프로세스는 대상 Cloud Service 인스턴스에 대한 권한을 포함한 모든 설정을 재설정하며에 추가된 관리자에 대해 true입니다. **관리자** 그룹입니다. 관리자 를 읽으려면 **관리자** 그룹: CTT에 대한 액세스 토큰을 검색합니다.
* 컨텐츠 추가를 수행할 때 이전 전송 이후 변경되지 않아 컨텐츠가 전송되지 않으면 해당 컨텐츠와 연관된 사용자 및 그룹도 전송되지 않습니다. 이 규칙은 그동안 사용자 및 그룹이 변경되었더라도 적용됩니다. 그 이유는 사용자 및 그룹이 연결된 콘텐츠와 함께 마이그레이션되기 때문입니다.
* 대상 AEM Cloud Service 인스턴스에 소스 AEM 인스턴스의 사용자 중 하나와 동일한 이메일 주소를 가지지만 다른 사용자 이름이 있는 사용자가 있을 경우, 사용자 매핑이 활성화되면 로그에 오류 메시지가 기록됩니다. 또한 지정된 이메일 주소를 가진 한 명의 사용자만 대상 시스템에서 허용되므로 소스 AEM 사용자는 전송되지 않습니다.

## 최종 요약 및 보고서 {#final-report}

추출 및 수집이 완료되면 주체 마이그레이션 세부 사항을 표시하는 보고서가 생성됩니다. 다음을 참조하십시오 [주도자 마이그레이션의 유효성을 검사하는 방법](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/validating-content-transfers.md#how-to-validate-principal-migration) 자세한 내용.
