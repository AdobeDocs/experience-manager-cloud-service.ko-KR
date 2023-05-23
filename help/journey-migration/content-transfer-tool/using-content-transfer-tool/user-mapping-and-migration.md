---
title: 사용자 매핑 및 주요 마이그레이션
description: 사용자 매핑 및 사용자 마이그레이션 개요
exl-id: 4a35fc46-f641-46a4-b3ff-080d090c593b
source-git-commit: 25bfcd521e9bbc54bff3b87d17cdeb0f99a68511
workflow-type: tm+mt
source-wordcount: '788'
ht-degree: 21%

---

# 사용자 매핑 및 주요 마이그레이션 {#user-mapping-and-principal-migration}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_usermapping"
>title="사용자 매핑"
>abstract="콘텐츠 전송 도구는 사용자 및 그룹을 기존 AEM 시스템에서 AEM as a Cloud Service로 이동하는 데 도움이 됩니다. 기존 사용자는 클라우드 서비스 작성자 인스턴스에서 중복되지 않도록 해당 IMS ID에 매핑되어야 합니다."

>[!NOTE]
>이전 버전의 사용자 매핑 도구에 대해서는 [레거시 설명서](/help/journey-migration/content-transfer-tool/user-mapping-tool-legacy/considerations-user-mapping-tool-legacy.md).

## 소개 {#introduction}

Adobe Experience Manager(AEM) as a Cloud Service로의 전환 여정의 일부로 사용자 및 그룹을 기존 AEM 시스템에서 AEM as a Cloud Service로 이동해야 합니다. 이는 콘텐츠 전송 도구를 통해 수행됩니다.

AEM as a Cloud Service의 주요 변경 내용은 작성자 계층 액세스에 대한 Adobe ID 사용이 완전히 통합된다는 것입니다. 이를 위해서는 사용자 및 사용자 그룹 관리에 [Adobe Admin Console](https://helpx.adobe.com/kr/enterprise/using/admin-console.html)을 사용해야 합니다. 사용자 프로필 정보는 Adobe Identity Management System(IMS)에서 중앙 집중식으로 관리되어 모든 Adobe 클라우드 애플리케이션에 SSO(Single Sign-On)를 제공할 수 있습니다. 자세한 내용은 [Identity Management](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/overview/what-is-new-and-different.html#identity-management)를 참조하십시오. 이러한 변경 사항으로 인해 기존 사용자는 IMS ID에 매핑되어야 Cloud Service 작성자 인스턴스에서 중복 사용자를 방지할 수 있습니다. 기존 AEM의 그룹은 IMS의 그룹과 근본적으로 다르므로 그룹은 매핑되지 않지만 마이그레이션이 완료된 후에는 두 그룹 세트를 조정해야 합니다.

## 사용자 매핑 및 마이그레이션 세부 정보 {#user-mapping-detail}

컨텐츠 전송 도구 및 Cloud Acceleration Manager 는 마이그레이션 중인 컨텐츠와 관련된 모든 사용자를 마이그레이션합니다. 이 매핑은 자동으로 수행되며, 추출이 시작되기 전에 토글을 통해 매핑 여부를 제어할 수 있습니다. 추출을 시작할 때 사용자가 토글의 기본 설정을 재정의할 수 있습니다.

* 소스 시스템이 작성자 인스턴스인 경우 기본적으로 매핑을 수행하기 위한 선택은 입니다. _날짜_, 이는 권장되는 프로세스입니다.
* 소스 시스템이 게시 인스턴스인 경우 기본적으로 매핑을 수행하기 위한 선택은 입니다. _끔_, 사용자가 일반적으로 마이그레이션되거나 게시 인스턴스에서 사용되지 않기 때문입니다.

## 사용자 매핑 및 마이그레이션 시 중요 고려 사항 {#important-considerations}


### 예외적인 경우 {#exceptional-cases}

다음과 같은 특정 사례가 기록됩니다.

1. 사용자가에 이메일 주소가 없는 경우 `profile/email` 필드 *jcr* 해당 사용자 또는 그룹이 마이그레이션될 수 있지만 매핑되지 않습니다. 이메일 주소가 로그인을 위한 사용자 이름으로 사용되는 경우에도 마찬가지입니다.

1. 사용자가 비활성화된 경우 비활성화된 경우와 동일하게 처리됩니다. 정상적으로 매핑되고 마이그레이션되며 클라우드 인스턴스에서 비활성화됩니다.

1. 대상 AEM Cloud Service 인스턴스에 소스 AEM 인스턴스의 사용자 중 하나와 동일한 사용자 이름(rep:principalName)을 가진 사용자가 있는 경우 해당 사용자 또는 그룹은 마이그레이션되지 않습니다.

1. 사용자가 사용자 매핑을 통해 매핑되지 않고 마이그레이션되거나 이메일 주소가 IMS에 로그인하는 데 사용되는 이메일 주소와 일치하지 않으면 대상 클라우드 시스템에서 IMS ID를 사용하여 로그인할 수 없습니다. 기존 AEM 방법을 사용하여 로그인할 수 있지만 일반적으로 이 방법이 필요 없거나 예상과 다르다는 점을 유념하십시오.


## 추가 고려 사항 {#additional-considerations}

* 다음과 같은 경우 **수집하기 전에 클라우드 인스턴스의 기존 콘텐츠 지우기** 이(가) 설정되면, Cloud Service 인스턴스에서 이미 전송된 사용자가 기존 저장소 전체와 함께 삭제되고 새 저장소가 생성되어 콘텐츠를 (으)로 수집합니다. 또한 대상 Cloud Service 인스턴스에 대한 권한을 포함한 모든 설정이 재설정되며에 추가된 관리자의 경우 true입니다. **관리자** 그룹입니다. 관리자 사용자를 다음에 다시 추가해야 합니다. **관리자** 그룹: CTT에 대한 액세스 토큰을 검색합니다.
* 콘텐츠 추가 작업을 수행할 때 이전 전송 이후 변경되지 않아 콘텐츠가 전송되지 않으면 그동안 사용자 및 그룹이 변경되더라도 해당 콘텐츠와 연관된 사용자 및 그룹도 전송되지 않습니다. 사용자 및 그룹이 연결된 콘텐츠와 함께 마이그레이션되기 때문입니다.
* 대상 AEM Cloud Service 인스턴스에 소스 AEM 인스턴스의 사용자 중 하나와 동일한 이메일 주소를 사용하는 다른 사용자 이름이 있는 경우 사용자 매핑이 활성화되면 오류 메시지가 로그에 기록되고 지정된 이메일 주소를 갖는 한 명의 사용자만 대상 시스템에서 허용되므로 소스 AEM 사용자가 전송되지 않습니다.

## 최종 요약 및 보고서 {#final-report}

추출 및 수집이 완료되면 주체 마이그레이션 세부 사항을 표시하는 보고서가 생성됩니다. 다음을 참조하십시오 [주도자 마이그레이션의 유효성을 검사하는 방법](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/validating-content-transfers.md#how-to-validate-principal-migration) 자세한 내용.
