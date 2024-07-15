---
title: 사용자 매핑 도구 개요(레거시)
description: 사용자 매핑 도구 개요(레거시)
exl-id: 17ed5721-093e-4491-b8c4-3dadcaa6598b
hide: true
hidefromtoc: true
feature: Migration
role: Admin
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '292'
ht-degree: 21%

---

# 사용자 매핑 도구 개요(레거시) {#overview-user-mapping-tool}

>[!INFO]
>
>이 설명서는 더 이상 사용되지 않는 버전의 도구를 참조합니다. 최신 버전에 대한 자세한 내용은 [사용자 매핑 및 사용자 마이그레이션](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/user-mapping-and-migration.md)을 참조하십시오.

<!-- Alexandru: drafting this for now

NOTE: "LEGACY" for user mapping includes everything before (that is, not including) 2.0.16 of CTT.

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_usermapping"
>title="User Mapping Tool"
>abstract="The Content Transfer Tool helps you move users and groups from your existing AEM system to AEM as a Cloud Service. Existing users and groups need to be mapped to their IMS IDs to avoid duplicate users and groups on the Cloud Service author instance."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-user-mapping-tool.html#important-considerations" text="Important Considerations for using User Mapping Tool"
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-user-mapping-tool.html#using-user-mapping-tool" text="Using User Mapping Tool"

-->

## 소개 {#introduction}

AEM as a Cloud Service(Adobe Experience Manager)로 전환 여정의 일부로 기존 AEM 시스템에서 AEM as a Cloud Service으로 사용자 및 그룹을 이동해야 합니다. 이 마이그레이션은 콘텐츠 전송 도구에 의해 수행됩니다.

AEM as a Cloud Service의 주요 변경 사항은 작성자 계층 액세스에 대한 Adobe ID의 완전히 통합된 사용입니다. 이 통합을 사용하려면 사용자 및 사용자 그룹 관리에 [Adobe Admin Console](https://helpx.adobe.com/kr/enterprise/using/admin-console.html)을(를) 사용해야 합니다. 사용자 프로필 정보는 모든 Adobe 클라우드 애플리케이션에서 단일 사인온을 제공하는 IMS(Adobe Identity Management System)에서 중앙 집중화됩니다. 자세한 내용은 [Identity Management](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/overview/what-is-new-and-different.html#identity-management)을 참조하세요. 이러한 변경 사항으로 인해 Cloud Service 작성자 인스턴스에서 기존 사용자 및 그룹을 중복하지 않도록 기존 사용자 및 그룹을 해당 IMS ID에 매핑해야 합니다.

## 사용자 매핑 도구 {#mapping-tool}

콘텐츠 전송 도구 (사용자 매핑 없음)는 마이그레이션되는 콘텐츠와 관련된 모든 사용자 및 그룹을 마이그레이션합니다. 사용자 매핑 도구는 컨텐츠 전송 도구의 일부입니다. 유일한 목적은 AEM as a Cloud Service에서 사용하는 SSO(Single Sign-On) 기능인 IMS에서 사용자를 올바르게 인식하도록 편집하는 것입니다. 이러한 수정이 완료되면, 콘텐츠 전송 도구는 지정된 콘텐츠의 사용자 및 그룹을 평소대로 마이그레이션합니다.

### 다음 단계 {#whats-next}

사용자 매핑 도구에 대해 알아보았다면 이제 사용자 매핑 도구를 사용하기 전에 중요 고려 사항과 예외적인 사례를 검토할 준비가 완료되었습니다. 자세한 내용은 [사용자 매핑 도구에 대한 중요 고려 사항](/help/journey-migration/content-transfer-tool/user-mapping-tool-legacy/considerations-user-mapping-tool-legacy.md)을 참조하십시오.
