---
title: 사용자 매핑 및 주요 마이그레이션
description: AEMas a Cloud Service 의 사용자 매핑 및 사용자 마이그레이션 개요.
exl-id: 4a35fc46-f641-46a4-b3ff-080d090c593b
source-git-commit: 2fdfb65543fa2942e809aa5d379f4000e40bd517
workflow-type: tm+mt
source-wordcount: '952'
ht-degree: 9%

---

# 사용자 매핑 및 주요 마이그레이션 {#user-mapping-and-principal-migration}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_usermapping"
>title="사용자 매핑"
>abstract="콘텐츠 전송 도구는 사용자 및 그룹을 기존 AEM(Adobe Experience Manager) 시스템에서 AEM as a Cloud Service로 이동하는 데 유용합니다. 기존 사용자는 Cloud Service 작성자 인스턴스에서 중복되지 않도록 해당 IMS ID에 매핑되어야 합니다."

>[!NOTE]
>이전 버전의 사용자 매핑 도구에 대해서는 [레거시 설명서](/help/journey-migration/content-transfer-tool/user-mapping-tool-legacy/considerations-user-mapping-tool-legacy.md).

## 소개 {#introduction}

Adobe Experience Manager(AEM) as a Cloud Service으로 전환 여정의 일부로, 사용자 및 그룹(또는 &#39;주도자&#39;)은 기존 AEM AEM 시스템에서 as a Cloud Service으로 마이그레이션해야 합니다. 이 작업은 콘텐츠 전송 도구에서 수행합니다.

AEM as a Cloud Service의 주요 변경 내용은 작성자 계층 액세스에 대한 Adobe ID 사용이 완전히 통합된다는 것입니다. 이 프로세스에는 [Adobe Admin Console](https://helpx.adobe.com/kr/enterprise/using/admin-console.html) 사용자 및 사용자 그룹 관리. 사용자 프로필 정보는 모든 Adobe 클라우드 애플리케이션에서 단일 사인온을 제공하는 IMS(Adobe Identity Management System)에서 중앙 집중화됩니다. 자세한 내용은 [Identity Management](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/overview/what-is-new-and-different.html#identity-management). 이러한 변경 사항으로 인해 Cloud Service 작성자 인스턴스에 중복 사용자가 생성되지 않도록 기존 사용자를 해당 IMS ID에 매핑해야 합니다. 기존 AEM의 그룹은 IMS의 그룹과 근본적으로 다르므로 그룹은 매핑되지 않지만 마이그레이션이 완료된 후에는 두 그룹 세트를 조정해야 합니다.

## 사용자 마이그레이션 세부 정보 {#principal-migration-detail}

컨텐츠 전송 도구 및 Cloud Acceleration Manager 는 마이그레이션 중인 컨텐츠와 관련된 모든 주체를 클라우드 시스템으로 마이그레이션합니다.  컨텐츠 전송 도구는 추출 프로세스 중에 소스 AEM 시스템의 모든 주도자를 복사하여 이 작업을 수행합니다.  그런 다음 CAM 수집은 수집 중인 콘텐츠와 연관된 주도자만 선택하고 마이그레이션합니다.

## 사용자 매핑 세부 정보 {#user-mapping-detail}

AEM 사용자는 동일한 이메일 주소로 해당 Adobe IMS 사용자에게 매핑될 수 있습니다.  이 매핑은 CTT에서(추출 단계 동안) 자동으로 수행할 수 있으며, 추출 시작 전에 전환으로 매핑 여부를 제어할 수 있습니다. 추출을 시작할 때 사용자가 토글의 기본 설정을 재정의할 수 있습니다.

* 소스 시스템이 작성자 인스턴스인 경우 기본적으로 매핑을 수행하기 위한 선택은 입니다. _날짜_, 이는 권장되는 프로세스이기 때문입니다.
* 소스 시스템이 게시 인스턴스인 경우 기본적으로 매핑을 수행하기 위한 선택은 입니다. _끔_, 사용자는 일반적으로 마이그레이션되거나 게시 인스턴스에서 사용되지 않으므로 또는 사용된 경우 일반적으로 다른 인증 시스템(즉, IMS가 아님)이 사용됩니다.

사용자가 추출 중에 매핑되는지 여부에 관계없이 마이그레이션 중인 콘텐츠와 연결된 경우 그룹은 수집 중에 클라우드 시스템으로 마이그레이션됩니다.

## 사용자 매핑 및 마이그레이션 시 중요 고려 사항 {#important-considerations}

### 예외적인 경우 {#exceptional-cases}

다음과 같은 특정 사례가 기록됩니다.

1. 사용자가에 이메일 주소가 없는 경우 `profile/email` 필드 *jcr* 노드, 해당 사용자 또는 그룹이 마이그레이션될 수 있지만 매핑되지 않았습니다. 이 시나리오는 이메일 주소가 로그인을 위한 사용자 이름으로 사용되는 경우에도 적용됩니다.
2. 사용자가 비활성화된 경우 다른 사용자와 동일하게 처리됩니다. 정상적으로 매핑 및 마이그레이션되고 클라우드 인스턴스에서 비활성화된 상태로 유지됩니다.
3. 원본 AEM 인스턴스와 대상 AEM Cloud Service 인스턴스 모두에 동일한 이름(rep:principalName)을 가진 주도자가 존재하는 경우 해당 주도자는 마이그레이션되지 않고 클라우드 시스템에 있는 이전의 주도자는 변경되지 않습니다.
4. 사용자가 사용자 매핑을 통해 매핑되지 않고 마이그레이션되는 경우 대상 클라우드 시스템에서 사용자는 IMS ID를 사용하여 로그인할 수 없습니다. 또는 이메일 주소가 IMS에 로그인하는 데 사용되는 이메일 주소와 일치하지 않으면 타겟 클라우드 시스템에서 IMS ID를 사용하여 로그인할 수도 없습니다. 기존 AEM 방법(로컬 로그인)을 사용하여 로그온할 수 있지만 일반적으로 이 방법은 필요 또는 예상과 다릅니다.

## 추가 고려 사항 {#additional-considerations}

* 다음과 같은 경우 **수집하기 전에 클라우드 인스턴스의 기존 콘텐츠 지우기** 가 설정되면, Cloud Service 인스턴스에서 이미 전송된 사용자가 기존 저장소 전체와 함께 삭제됩니다. 콘텐츠가 수집되는 새 저장소가 생성됩니다. 또한 이 프로세스는 대상 Cloud Service 인스턴스에 대한 권한을 포함한 모든 설정을 재설정하며에 추가된 관리자에 대해 true입니다. **관리자** 그룹입니다. 관리자 사용자를 다음에 다시 추가해야 합니다. **관리자** CTT/CAM 수집에 대한 액세스 토큰을 검색할 그룹입니다.
* 컨텐츠 추가를 수행할 때 이전 전송 이후 변경되지 않아 컨텐츠가 전송되지 않으면 해당 컨텐츠와 연관된 사용자 및 그룹도 전송되지 않습니다. 이 규칙은 소스 시스템에서 사용자 및 그룹이 변경된 경우에도 적용됩니다. 그 이유는 사용자 및 그룹이 연결된 콘텐츠와 함께 마이그레이션될 뿐이기 때문입니다.
* 대상 AEM Cloud Service 인스턴스에 소스 AEM 인스턴스의 사용자 중 하나와 동일한 이메일 주소를 가지지만 다른 사용자 이름이 있는 사용자가 있을 경우, 사용자 매핑이 활성화되면 로그에 오류 메시지가 기록됩니다. 또한 지정된 이메일 주소를 가진 한 명의 사용자만 대상 시스템에서 허용되므로 소스 AEM 사용자는 전송되지 않습니다.
* 다음을 참조하십시오 [폐쇄된 사용자 그룹 마이그레이션](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/closed-user-groups-migration.md) CUG(폐쇄형 사용자 그룹) 정책에 사용된 주도자에 대한 추가 고려 사항.

## 최종 요약 및 보고서 {#final-report}

추출 및 수집이 완료되면 주체 마이그레이션 세부 사항을 표시하는 보고서가 생성됩니다. 다음을 참조하십시오 [주도자 마이그레이션의 유효성을 검사하는 방법](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/validating-content-transfers.md#how-to-validate-principal-migration) 자세한 내용.
