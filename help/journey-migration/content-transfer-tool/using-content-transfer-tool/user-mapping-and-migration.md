---
title: 사용자 매핑 및 주요 마이그레이션
description: AEM as a Cloud Service의 사용자 매핑 및 사용자 마이그레이션 개요.
exl-id: 4a35fc46-f641-46a4-b3ff-080d090c593b
feature: Migration
role: Admin
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '1060'
ht-degree: 5%

---

# 사용자 매핑 및 주요 마이그레이션 {#user-mapping-and-principal-migration}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_usermapping"
>title="사용자 마이그레이션"
>abstract="콘텐츠 전송 도구는 사용자 및 그룹을 기존 AEM(Adobe Experience Manager) 시스템에서 AEM as a Cloud Service로 이동하는 데 유용합니다. 기존 사용자는 IMS ID를 통해 로그인할 수 있도록 매핑되어야 합니다."

>[!NOTE]
>이전 버전의 사용자 매핑 도구에 대해서는 [레거시 설명서](/help/journey-migration/content-transfer-tool/user-mapping-tool-legacy/considerations-user-mapping-tool-legacy.md)를 참조하십시오.

## 소개 {#introduction}

Adobe Experience Manager(AEM as a Cloud Service)로 전환 여정의 일부로 사용자 및 그룹(또는 &#39;주체&#39;)은 기존 AEM 시스템에서 AEM as a Cloud Service으로 마이그레이션해야 합니다. 이 작업은 콘텐츠 전송 도구에서 수행합니다.

AEM as a Cloud Service의 주요 변경 사항은 작성자 계층 액세스에 대한 Adobe ID의 완전히 통합된 사용입니다. 이 프로세스에서는 사용자 및 사용자 그룹을 관리하기 위해 [Adobe Admin Console](https://helpx.adobe.com/kr/enterprise/using/admin-console.html)을(를) 사용해야 합니다. 사용자 프로필 정보는 모든 Adobe 클라우드 애플리케이션에서 단일 사인온을 제공하는 IMS(Adobe Identity Management System)에 중앙 집중화됩니다. 자세한 내용은 [Identity Management](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/overview/what-is-new-and-different.html#identity-management)을 참조하세요. 이 변경 사항으로 인해 기존 사용자는 IMS 프로필을 사용하여 AEMaaCS에 액세스할 수 있도록 IMS ID에 매핑되어야 합니다. 기존 AEM의 그룹은 IMS의 그룹과 근본적으로 다르므로 그룹은 매핑되지 않지만 마이그레이션이 완료된 후에는 두 그룹 세트를 조정해야 합니다.

## 사용자 마이그레이션 세부 정보 {#principal-migration-detail}

컨텐츠 전송 도구 및 Cloud Acceleration Manager은 마이그레이션 중인 컨텐츠와 관련된 모든 주도자를 클라우드 시스템으로 마이그레이션합니다. 컨텐츠 전송 도구는 추출 프로세스 중에 소스 AEM 시스템의 모든 주도자를 복사하여 이 작업을 수행합니다. 그런 다음 CAM 수집은 수집 중인 콘텐츠와 연관된 주도자만 선택하고 마이그레이션합니다. 사용자가 마이그레이션된 컨텐츠의 ACL 또는 CUG 정책에 있는 경우 해당 사용자 및 해당 사용자가 속한 모든 그룹과 상위(상위) 그룹이 모두 마이그레이션됩니다. 또한 콘텐츠의 주도자가 그룹인 경우 모든 하위(하위) 그룹 및 사용자도 마이그레이션됩니다.

## 사용자 매핑 세부 정보 {#user-mapping-detail}

AEM 사용자는 동일한 이메일 주소로 해당 Adobe IMS 사용자에게 매핑될 수 있습니다. 이 매핑은 CTT에서(추출 단계 동안) 자동으로 수행할 수 있으며, 추출 시작 전에 전환으로 매핑 여부를 제어할 수 있습니다. 추출을 시작할 때 사용자가 토글의 기본 설정을 재정의할 수 있습니다.

* 소스 시스템이 작성자 인스턴스인 경우, 권장되는 프로세스이므로 기본적으로 매핑을 수행하기 위한 선택은 _on_&#x200B;입니다.
* 소스 시스템이 게시 인스턴스인 경우 사용자가 일반적으로 마이그레이션되거나 게시 인스턴스에서 사용되지 않으므로 기본적으로 매핑을 수행하기 위한 선택은 _off_&#x200B;입니다. 또는 사용자가 사용되는 경우 일반적으로 다른 인증 시스템(즉, IMS가 아님)이 사용됩니다.

사용자가 추출 중에 매핑되는지 여부에 관계없이 마이그레이션 중인 콘텐츠와 연결된 경우 그룹은 수집 중에 클라우드 시스템으로 마이그레이션됩니다.

## 사용자 매핑 및 마이그레이션 시 중요 고려 사항 {#important-considerations}

### 예외적인 경우 {#exceptional-cases}

다음과 같은 특정 사례가 기록됩니다.

1. 사용자에게 *jcr* 노드의 `profile/email` 필드에 전자 메일 주소가 없는 경우 해당 사용자가 마이그레이션될 수 있지만 매핑되지 않았습니다. 이 시나리오는 이메일 주소가 로그인을 위한 사용자 이름으로 사용되는 경우에도 적용됩니다.
2. 사용자가 비활성화된 경우 다른 사용자와 동일하게 처리됩니다. 정상적으로 매핑 및 마이그레이션되고 클라우드 인스턴스에서 비활성화된 상태로 유지됩니다.
3. 원본 AEM 인스턴스와 대상 AEM Cloud Service 인스턴스 둘 다에 동일한 고유성 제약 데이터(rep:principalName, rep:authorizableId, jcr:uuid 또는 rep:externalId)가 있는 주도자가 존재하는 경우 해당 주도자는 마이그레이션되지 않고 클라우드 시스템의 이전에 존재했던 주도자는 변경되지 않은 상태로 유지됩니다. 주도자 마이그레이션 보고서에 기록됩니다.
4. 사용자가 사용자 매핑을 통해 IMS에 매핑되지 않으면 Cloud AEM 시스템의 사용자 프로필이 IMS에 인식되지 않습니다. 이 경우 IMS를 통해 로그인하면 AEM에 새(중복) 프로필이 생성되지만 이전 프로필 정보가 포함되지 않습니다. 원래 사용자 프로필은 cloud AEM 시스템에 존재하지만 기존 AEM 방법(로컬 로그인)을 사용해야만 IMS를 통해 로그인할 수 있습니다. 따라서 모든 작성자 마이그레이션에 모든 사용자를 매핑하는 것이 좋습니다.

## 추가 고려 사항 {#additional-considerations}

* **수집 전에 클라우드 인스턴스에서 기존 콘텐츠 지우기** 설정이 설정된 경우 Cloud Service 인스턴스로 이전에 전송된 주도자가 전체 기존 저장소와 함께 삭제됩니다. 즉, 콘텐츠가 수집되는 새 저장소가 만들어집니다. 또한 이 프로세스는 대상 Cloud Service 인스턴스에 대한 권한을 포함한 모든 설정을 재설정하며 **administrators** 그룹에 추가된 관리자 사용자에 대해서도 true입니다. CTT/CAM 수집에 대한 액세스 토큰을 검색하려면 관리자 사용자를 **관리자** 그룹에 다시 추가해야 합니다.
* 지우기 안 함 수집을 수행할 때(**기존 콘텐츠 지우기**&#x200B;가 설정되지 않음) 이전 전송 이후 콘텐츠가 변경되지 않아 콘텐츠가 전송되지 않으면 해당 콘텐츠와 연결된 사용자 및 그룹도 전송되지 않습니다. 이 규칙은 소스 시스템에서 사용자 및 그룹이 변경된 경우에도 적용됩니다. 사용자 및 그룹은 연결된 콘텐츠와 함께 마이그레이션되어야 하기 때문입니다. 따라서 소스 시스템의 그룹에 새로 추가된 주도자는 마이그레이션 중인 다른 그룹이나 마이그레이션 중인 다른 컨텐츠의 ACL에 포함되지 않는 한 마이그레이션되지 않습니다. 이후 이러한 주도자를 마이그레이션하려면 패키지 사용을 고려하거나, 대상에서 주도자를 삭제하고 관련 콘텐츠를 다시 마이그레이션하십시오(덮어쓰기로 추출 및 지우기로 수집).
* 중복 이메일 주소는 IMS에서 허용되지 않지만 AEM(온-프레미스 및 클라우드 모두)에서 허용됩니다. 사용자는 이메일 주소를 사용하여 IMS를 통해 AEM에 로그인할 수 있으며, IMS에서 참조하는 사용자 프로필에 로그인됩니다.
* CUG(폐쇄형 사용자 그룹) 정책에 사용된 주체에 대한 추가 고려 사항은 [폐쇄형 사용자 그룹 마이그레이션](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/closed-user-groups-migration.md)을 참조하십시오.

## 최종 요약 및 보고서 {#final-report}

추출 및 수집이 완료되면 주체 마이그레이션 세부 사항을 표시하는 보고서가 생성됩니다. 자세한 내용은 [사용자 마이그레이션의 유효성을 검사하는 방법](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/validating-content-transfers.md#how-to-validate-principal-migration)을 참조하십시오.
