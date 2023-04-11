---
title: 사용자 매핑 및 주요 마이그레이션
description: 사용자 매핑 및 주체 마이그레이션 개요
source-git-commit: 5475f9995513d09e61bd8f52242b3e74b8d4694c
workflow-type: tm+mt
source-wordcount: '757'
ht-degree: 22%

---

# 사용자 매핑 및 주요 마이그레이션 {#user-mapping-and-principal-migration}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_usermapping"
>title="사용자 매핑"
>abstract="콘텐츠 전송 도구는 사용자 및 그룹을 기존 AEM 시스템에서 AEM as a Cloud Service로 이동하는 데 도움이 됩니다. 기존 사용자는 클라우드 서비스 작성자 인스턴스에서 중복되지 않도록 해당 IMS ID에 매핑되어야 합니다."

>[!NOTE]
>사용자 매핑 도구의 이전 버전에 대해서는 [이전 설명서](/help/journey-migration/content-transfer-tool/user-mapping-tool-legacy/considerations-user-mapping-tool-legacy.md).

## 소개 {#introduction}

Adobe Experience Manager(AEM) as a Cloud Service로의 전환 여정의 일부로 사용자 및 그룹을 기존 AEM 시스템에서 AEM as a Cloud Service로 이동해야 합니다. 이는 콘텐츠 전송 도구를 통해 수행됩니다.

AEM as a Cloud Service의 주요 변경 내용은 작성자 계층 액세스에 대한 Adobe ID 사용이 완전히 통합된다는 것입니다. 이를 위해서는 사용자 및 사용자 그룹 관리에 [Adobe Admin Console](https://helpx.adobe.com/kr/enterprise/using/admin-console.html)을 사용해야 합니다. 사용자 프로필 정보는 Adobe Identity Management System(IMS)에서 중앙 집중식으로 관리되어 모든 Adobe 클라우드 애플리케이션에 SSO(Single Sign-On)를 제공할 수 있습니다. 자세한 내용은 [Identity Management](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/overview/what-is-new-and-different.html#identity-management)를 참조하십시오. 이러한 변경으로 인해 기존 사용자는 Cloud Service 작성자 인스턴스에서 중복 사용자를 방지하기 위해 IMS ID에 매핑해야 합니다. 기존 AEM의 그룹은 IMS의 그룹과 기본적으로 다르므로 그룹은 매핑되지 않지만, 마이그레이션이 완료된 후 두 그룹 집합을 조정해야 합니다.

## 사용자 매핑 및 마이그레이션 세부 정보 {#user-mapping-detail}

컨텐츠 전송 도구 및 Cloud Acceleration Manager는 마이그레이션되는 컨텐츠와 관련된 모든 사용자를 마이그레이션합니다. 이 매핑은 자동으로 수행되며, 추출을 시작하기 전에 토글으로 수행할 수 있는지 여부를 제어할 수 있습니다. 추출을 시작할 때 사용자가 토글의 기본 설정을 재정의할 수 있습니다.

* 소스 시스템이 작성자 인스턴스인 경우 기본적으로 매핑을 수행할 선택은 다음과 같습니다 _on_: 권장되는 프로세스입니다.
* 소스 시스템이 게시 인스턴스인 경우 기본적으로 매핑을 수행할 선택은 다음과 같습니다 _해제_: 사용자가 일반적으로 게시 인스턴스에서 마이그레이션되거나 사용되지 않으므로

## 사용자 매핑 및 마이그레이션 시 중요 고려 사항 {#important-considerations}


### 예외적인 사례 {#exceptional-cases}

다음과 같은 특정 사례가 기록됩니다.

1. 사용자에게 `profile/email` 그들의 필드 *jcr* 해당 사용자 또는 그룹이 마이그레이션될 수 있지만 매핑되지 않습니다. 이는 이메일 주소가 로그인하기 위한 사용자 이름으로 사용되는 경우에도 마찬가지입니다.

1. 사용자가 비활성화되어 있으면 비활성화되지 않은 것처럼 처리됩니다. 매핑되고 일반으로 마이그레이션되며, 클라우드 인스턴스에서 비활성화된 상태로 유지됩니다.

1. 사용자가 소스 AEM 인스턴스의 사용자 이름(rep:principalName)과 동일한 사용자 이름을 가진 target AEM Cloud Service 인스턴스에 있으면 해당 사용자 또는 그룹은 마이그레이션되지 않습니다.

1. 사용자가 사용자 매핑을 통해 처음 매핑되지 않고 마이그레이션되거나, 이메일 주소가 IMS에 로그인하는 데 사용되는 이메일 주소와 일치하지 않는 경우 타겟 클라우드 시스템에서 IMS ID를 사용하여 로그인할 수 없습니다. 기존 AEM 방법을 사용하여 로그인할 수 있지만 일반적으로 이러한 방법이 필요하거나 예상된 것은 아닙니다.


## 추가 고려 사항 {#additional-considerations}

* 설정이 **수집하기 전에 클라우드 인스턴스에서 기존 컨텐츠를 지웁니다.** 이(가) 설정되어 있으면, Cloud Service 인스턴스에 이미 전송된 사용자가 전체 기존 저장소와 함께 삭제되고 컨텐츠를 수집하기 위한 새 저장소가 작성됩니다. 또한 이 작업은 Target Cloud Service 인스턴스에 대한 권한을 포함한 모든 설정을 재설정하며, Target에 추가된 관리자 사용자에 대해 True입니다. **관리자** 그룹에 속해 있어야 합니다. 관리자 사용자를 **관리자** 그룹 을 사용하여 CTT에 대한 액세스 토큰을 검색할 수 있습니다.
* 컨텐츠 추가를 수행할 때 컨텐츠가 이전 전송 이후 변경되지 않아 전송되지 않으면 해당 컨텐츠와 연관된 사용자 및 그룹도 그 동안 사용자와 그룹이 변경되었더라도 전송되지 않습니다. 사용자 및 그룹은 연결된 컨텐츠와 함께 마이그레이션되기 때문입니다.
* 대상 AEM Cloud Service 인스턴스에 다른 사용자 이름은 있지만 소스 AEM 인스턴스의 사용자 중 하나와 동일한 이메일 주소를 가진 사용자가 있고 사용자 매핑이 활성화되어 있으면 오류 메시지가 로그에 기록되고 소스 AEM 사용자는 전송되지 않습니다. 이는 지정된 이메일 주소를 가진 한 명의 사용자만 대상 시스템에서 허용되기 때문입니다.
