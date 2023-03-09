---
title: 사용자 매핑 도구 개요 (기존)
description: 사용자 매핑 도구 개요(이전)
exl-id: 17ed5721-093e-4491-b8c4-3dadcaa6598b
hide: true
hidefromtoc: true
source-git-commit: 69dfe7f98628ab67cc3a994c32b1530550ec6a01
workflow-type: tm+mt
source-wordcount: '282'
ht-degree: 97%

---

# 사용자 매핑 도구 개요 {#overview-user-mapping-tool}


<!-- Alexandru: drafting this for now

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_usermapping"
>title="User Mapping Tool"
>abstract="The Content Transfer Tool helps you move users and groups from your existing AEM system to AEM as a Cloud Service. Existing users and groups need to be mapped to their IMS IDs to avoid duplicate users and groups on the Cloud Service author instance."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-user-mapping-tool.html?lang=en#important-considerations" text="Important Considerations for using User Mapping Tool"
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-user-mapping-tool.html?lang=en#using-user-mapping-tool" text="Using User Mapping Tool"

-->

## 소개 {#introduction}

Adobe Experience Manager(AEM) as a Cloud Service로의 전환 여정의 일부로 사용자 및 그룹을 기존 AEM 시스템에서 AEM as a Cloud Service로 이동해야 합니다. 이는 콘텐츠 전송 도구를 통해 수행됩니다.

AEM as a Cloud Service의 주요 변경 내용은 작성자 계층 액세스에 대한 Adobe ID 사용이 완전히 통합된다는 것입니다.  이를 위해서는 사용자 및 사용자 그룹 관리에 [Adobe Admin Console](https://helpx.adobe.com/kr/enterprise/using/admin-console.html)을 사용해야 합니다. 사용자 프로필 정보는 Adobe Identity Management System(IMS)에서 중앙 집중식으로 관리되어 모든 Adobe 클라우드 애플리케이션에 SSO(Single Sign-On)를 제공할 수 있습니다. 자세한 내용은 [Identity Management](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/overview/what-is-new-and-different.html?lang=en#identity-management)를 참조하십시오. 해당 변경으로 인해 기존 사용자 및 그룹을 해당 IMS ID에 매핑하여 Cloud Service 작성자 인스턴스의 사용자 및 그룹 중복을 방지해야 합니다.

## 사용자 매핑 도구 {#mapping-tool}

콘텐츠 전송 도구(사용자 매핑 없음)는 마이그레이션되는 콘텐츠와 연결된 모든 사용자 및 그룹을 마이그레이션합니다. 사용자 매핑 도구는 콘텐츠 전송 도구의 일부이고 사용자를 수정하여 AEM as a Cloud Service에서 사용하는 SSO(Single Sign-On) 기능인 IMS로 사용자를 올바르게 인식할 수 있도록 하기 위한 목적으로만 사용됩니다. 수정 작업이 완료되면 콘텐츠 전송 도구는 평소와 같이 지정된 콘텐츠 사용자 및 그룹을 마이그레이션합니다.

### 다음 단계 {#whats-next}

사용자 매핑 도구에 대해 알아보았다면 이제 사용자 매핑 도구를 사용하기 전에 중요 고려 사항과 예외적인 사례를 검토할 준비가 완료되었습니다. 자세한 내용은 [사용자 매핑 도구에 대한 중요 고려 사항](/help/journey-migration/content-transfer-tool/user-mapping-tool-legacy/considerations-user-mapping-tool-legacy.md)을 참조하십시오.
