---
title: 사용자 매핑 도구 개요
description: 사용자 매핑 도구 개요
source-git-commit: 9d131daf5b6a0b1530ebff48627f6130ef716f3e
workflow-type: tm+mt
source-wordcount: '324'
ht-degree: 1%

---


# 사용자 매핑 도구 개요 {#overview-user-mapping-tool}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_usermapping"
>title="사용자 매핑 도구"
>abstract="컨텐츠 전송 도구를 사용하면 기존 AEM 시스템에서 AEM as a Cloud Service으로 사용자 및 그룹을 이동할 수 있습니다. 기존 사용자 및 그룹을 IMS ID에 매핑해야 Cloud Service 작성자 인스턴스에서 사용자와 그룹이 중복되지 않습니다."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-user-mapping-tool.html?lang=en#important-considerations" text="사용자 매핑 도구 사용에 대한 중요한 고려 사항"
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-user-mapping-tool.html?lang=en#using-user-mapping-tool" text="사용자 매핑 도구 사용"

## 소개 {#introduction}

Adobe Experience Manager(AEM) as a Cloud Service으로 전환 여정의 일부로서, 사용자와 그룹을 기존 AEM 시스템에서 AEM으로 이동해야 합니다. 이 작업은 컨텐츠 전송 도구에서 수행합니다.

AEM as a Cloud Service에 대한 주요 변경 사항은 작성 계층에 액세스하기 위해 Adobe ID를 완벽하게 통합한 것입니다.  이렇게 하려면 사용자 및 사용자 그룹을 관리하기 위해 [Adobe Admin Console](https://helpx.adobe.com/kr/enterprise/using/admin-console.html)을 사용해야 합니다. 사용자 프로필 정보는 모든 Adobe 클라우드 애플리케이션에서 단일 사인온을 제공하는 IMS(Adobe Identity Management System)에서 중앙 집중화됩니다. 자세한 내용은 [Identity Management](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/overview/what-is-new-and-different.html?lang=en#identity-management)을 참조하십시오. 이러한 변경으로 인해 기존 사용자 및 그룹을 IMS ID에 매핑하여 Cloud Service 작성자 인스턴스에서 사용자와 그룹이 중복되지 않도록 해야 합니다.

## 사용자 매핑 도구 {#mapping-tool}

사용자 매핑 없이 컨텐츠 전송 도구는 마이그레이션되는 컨텐츠와 연결된 사용자 및 그룹을 마이그레이션하게 됩니다. 사용자 매핑 도구는 컨텐츠 전송 도구의 일부이며 유일한 목적은 AEM에서 사용하는 단일 사인온 기능인 IMS에서 올바르게 인식할 수 있도록 사용자 및 그룹을 수정하는 것입니다. 이러한 수정 사항이 완료되면 컨텐츠 전송 도구는 지정된 컨텐츠의 사용자 및 그룹을 평소대로 마이그레이션합니다.
