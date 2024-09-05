---
title: 마이그레이션 후 주체 관리
description: IMS 및 AEM에서 사용자 및 그룹을 설정하는 방법 알아보기
exl-id: 46c4abfb-7e28-4f18-a6d4-f729dd42ea7b
source-git-commit: a5bec2c05b46f8db55762b7ee1f346f3bb099d24
workflow-type: tm+mt
source-wordcount: '773'
ht-degree: 5%

---

# 마이그레이션 후 주체 관리 {#managing-principals-after-migration}

>[!CONTEXTUALHELP]
>id="managing-principals"
>title="마이그레이션 후 주체 관리"
>abstract="IMS 및 AEM에서 사용자 및 그룹을 설정하는 방법 알아보기"

이 문서에서는 고객이 AEM as a Cloud Service 환경에서 작동하도록 IMS 및 AEM에서 사용자 및 그룹을 설정하는 데 수행해야 하는 높은 수준의 절차에 대해 설명합니다.

## 주체 관리 {#managing-principals}

AEM as a Cloud Service의 경우 주로 Admin Console을 사용하여 사용자와 그룹을 관리해야 합니다.  마이그레이션을 고려할 때 이러한 작업 중 일부는 콘텐츠 마이그레이션이 수행되기 전에 수행할 수 있습니다.  기본적으로 이러한 주요 임무 그룹 중

* IMS에서 사용자 및 그룹 만들기
* IMS의 그룹에 사용자 할당
* IMS 그룹을 AEM 그룹에 할당(필요한 경우)

처음 두 작업은 콘텐츠 마이그레이션 전이나 후에 수행할 수 있습니다.  Active Directory 또는 LDAP와 같은 외부 IDP와의 통합을 포함하여 IMS에서만 사용자 및 그룹에 영향을 주는 단계입니다.  이러한 단계는 [Admin Console을 사용하여 IMS의 보안 주체 관리](/help/journey-migration/managing-principals.md)에 설명되어 있습니다.

콘텐츠가 AEM as a Cloud Service 환경으로 마이그레이션되면 세 번째 단계를 수행할 수 있습니다.

### 그룹 마이그레이션

마이그레이션의 수집 단계 동안 마이그레이션된 콘텐츠에 대한 ACL 또는 CUG 정책을 충족해야 하는 경우 그룹이 마이그레이션됩니다.  자세한 내용은 [그룹 마이그레이션](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/group-migration.md)을 참조하세요.

마이그레이션된 그룹(Assets 컬렉션 생성으로 생성되지 않은 그룹 - 아래 컬렉션 참조)은 IMS 그룹으로 구성됩니다.  즉, IMS에서 (예를 들어 Admin Console을 통해) 생성된 동일한 이름의 모든 그룹은 AEM의 그룹에 연결되고 IMS 그룹의 멤버인 사용자도 AEM의 그룹의 멤버가 됩니다.  이 연결이 수행되도록 하려면 IMS에서 그룹도 먼저 만들어야 합니다.  [Admin Console을 사용하여 IMS에서 보안 주체 관리](/help/journey-migration/managing-principals.md)에 설명된 대로 Admin Console을 사용하여 AEM 인스턴스에서 개별적으로 또는 대량으로 그룹을 만듭니다.

AEM 보안 UI를 사용하여 IMS 그룹을 로컬 AEM 그룹에 할당합니다.  [그룹 만들기 및 구성](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/forms/administrator-help/setup-organize-users/creating-configuring-groups#edit-a-group)을 참조하세요.  이 문서는 AEM 6.5용이지만 AEM as a Cloud Service의 다른 그룹에 그룹을 추가하는 경우에도 적용됩니다.

### IMS 사용자

사용자는 마이그레이션되지 않으므로 AEM에서 사용할 수 있도록 IMS에서 만들어야 합니다.  여러 가지 방법으로 이 작업을 수행할 수 있지만, 사용자가 이전 AEM 시스템에서 보유했던 콘텐츠에 동일하게 액세스할 수 있도록 만든 사용자를 올바른 IMS 그룹에 할당하는 것이 중요합니다.  이에 사용할 수 있는 도구 중 하나는 Admin Console의 일괄 업로드 기능입니다. 일괄 업로더를 사용하여 멤버여야 하는 그룹과 함께 사용자를 업로드합니다.  이 작업을 수행하기 전에 위에서 설명한 대로 먼저 그룹을 IMS에서 만들어야 합니다.

각 사용자가 속해야 하는 그룹을 알기 위해 사용자 보고서를 사용할 수 있습니다([그룹 마이그레이션](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/group-migration.md) 참조).  이 보고서는 각 사용자가 멤버로 있어야 하는 그룹을 나열하며 이 목록은 Admin Console 일괄 업로드 기능의 입력 파일에 포함될 수 있습니다.

### 컬렉션

또한 Assets 컬렉션을 만들면 해당 컬렉션에 대한 액세스를 관리할 일부 그룹이 자동으로 만들어집니다.  이러한 그룹은 마이그레이션된 컬렉션에서 언급되지만 IMS 그룹에 직접 연결하도록 구성되지 않은 경우 마이그레이션됩니다. AEM에서 이러한 그룹은 &quot;로컬 그룹&quot;으로 유지되며 IMS를 통해 관리할 수 없습니다.

이러한 그룹은 IMS에 없으므로 일괄 업로드 도구를 사용하여 사용자를 직접 구성원으로 만들 수 없습니다.  AEM에 있는 IMS 사용자를 이러한 그룹에 개별적으로 추가할 수 있지만, 일괄 작업을 수행하려면 추가 단계가 필요합니다.  이 작업을 수행하는 한 가지 방법은 다음과 같습니다.
* 컬렉션에 액세스할 수 있도록 Admin Console/IMS에서 새 그룹을 만들고 AEM에 대해 구성합니다.
* AEM에 그룹이 생성되도록 그룹의 멤버로 로그인합니다.
* 마이그레이션된 컬렉션의 경우 Assets 컬렉션 UI를 사용하여 새 그룹을 편집기/소유자/뷰어로 추가합니다.
* Admin Console의 새 그룹에 사용자를 추가(또는 일괄 업로드)합니다.
* 사용자가 처음 로그인하면 IMS 사용자가 AEM에 생성되고 새 그룹 및 이에 따라 원래 컬렉션 그룹에 액세스할 수 있습니다.

참고: 사용자를 일괄 할당하는 경우 위의 단계를 사용하여 IMS에서 사용자를 만들어야 합니다. IMS에 이미 있는 사용자는 일괄 업로드로 다시 만들 수 없습니다.
