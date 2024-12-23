---
title: 마이그레이션 후 주체 관리
description: IMS 및 AEM에서 사용자 및 그룹을 설정하는 방법 알아보기
exl-id: 46c4abfb-7e28-4f18-a6d4-f729dd42ea7b
source-git-commit: a5bec2c05b46f8db55762b7ee1f346f3bb099d24
workflow-type: ht
source-wordcount: '773'
ht-degree: 100%

---

# 마이그레이션 후 주체 관리 {#managing-principals-after-migration}

>[!CONTEXTUALHELP]
>id="managing-principals"
>title="마이그레이션 후 주체 관리"
>abstract="IMS 및 AEM에서 사용자 및 그룹을 설정하는 방법 알아보기"

이 문서에서는 AEM as a Cloud Service 환경을 사용하기 위해 IMS 및 AEM에서 사용자 및 그룹을 설정하는 데 취해야 할 주요 단계를 설명합니다.

## 주체 관리 {#managing-principals}

AEM as a Cloud Service의 경우 사용자와 그룹은 주로 Admin Console을 사용하여 관리해야 합니다.  마이그레이션을 고려할 때 이러한 작업 중 일부는 콘텐츠 마이그레이션이 이루어지기 전에 수행할 수 있습니다.  기본적으로 이러한 주요 작업 그룹에는 다음과 같은 것이 있습니다.

* IMS에서 사용자 및 그룹 만들기
* IMS에서 그룹에 사용자 할당
* IMS 그룹을 AEM 그룹에 할당(필요한 경우)

앞의 두 개는 콘텐츠 마이그레이션 전 또는 후에 수행할 수 있습니다.  이러한 단계는 IMS의 사용자 및 그룹에만 영향을 미치는 단계이며, Active Directory 또는 LDAP와 같은 외부 IDP와의 통합도 포함할 수 있습니다.  이들 단계는 [Admin Console을 사용하는 IMS의 주체 관리](/help/journey-migration/managing-principals.md)에 설명되어 있습니다.

콘텐츠가 AEM as a Cloud Service 환경으로 마이그레이션되면 세 번째 단계를 수행할 수 있습니다.

### 그룹 마이그레이션

마이그레이션의 수집 단계에서 마이그레이션된 콘텐츠에 대한 ACL 또는 CUG 정책을 충족해야 하는 경우 그룹이 마이그레이션됩니다.  자세한 내용은 [그룹 마이그레이션](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/group-migration.md)을 참조하십시오.

마이그레이션된 그룹(Assets 컬렉션 생성에 의해 생성되지 않은 그룹 - 아래 컬렉션 참조)은 IMS 그룹으로 구성됩니다.  즉, IMS에서 생성된 동일한 이름의 그룹(예: Admin Console을 통해)은 AEM의 그룹에 연결되며, IMS 그룹의 멤버인 사용자도 AEM의 그룹 멤버가 됩니다.  이 연결이 이루어지려면 먼저 IMS에서 그룹을 만들어야 합니다.  [Admin Console을 사용하는 IMS의 주체 관리](/help/journey-migration/managing-principals.md)에 설명된 대로 Admin Console을 사용하여 AEM 인스턴스에서 개별적으로 또는 일괄로 그룹을 생성합니다.

AEM 보안 UI를 사용하여 로컬 AEM 그룹에 IMS 그룹을 할당합니다.  [그룹 생성 및 구성](https://experienceleague.adobe.com/ko/docs/experience-manager-65/content/forms/administrator-help/setup-organize-users/creating-configuring-groups#edit-a-group)을 참조하십시오.  이 문서는 AEM 6.5용이지만 AEM as a Cloud Service의 다른 그룹에 그룹을 추가하는 경우에도 적용됩니다.

### IMS 사용자

사용자는 마이그레이션되지 않으므로 AEM에서 사용할 수 있도록 IMS에서 생성해야 합니다.  이를 달성하는 방법은 여러 가지가 있지만, 생성된 사용자가 이전 AEM 시스템에서 사용했던 콘텐츠에 동일하게 액세스할 수 있도록 올바른 IMS 그룹에 할당하는 것이 중요합니다.  여기에 사용할 수 있는 도구 중 하나는 Admin Console의 일괄 업로드 기능입니다. 일괄 업로더를 사용하여 멤버로 소속되어야 할 그룹과 함께 사용자를 업로드할 수 있습니다.  이 작업을 수행하기 전에 위에서 설명한 대로 먼저 IMS에서 그룹을 만들어야 합니다.

각 사용자가 멤버로 소속되어야 할 그룹을 확인하기 위해 사용자 보고서를 활용할 수 있습니다([그룹 마이그레이션](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/group-migration.md) 참조).  이 보고서에는 각 사용자가 멤버로 소속되어야 할 그룹이 나열되어 있으며, 이 목록은 Admin Console 일괄 업로드 기능의 입력 파일에 포함될 수 있습니다.

### 컬렉션

Assets 컬렉션을 만들면 해당 컬렉션에 대한 액세스를 관리할 일부 그룹도 자동으로 생성됩니다.  이러한 그룹은 마이그레이션된 컬렉션에서 언급된 경우에만 마이그레이션되지만, IMS 그룹에 직접 연결하도록 구성되지 않습니다. 따라서, AEM에서는 “로컬 그룹”으로 남아 있으며 IMS를 통해 관리할 수 없습니다.

이 그룹들은 IMS에 존재하지 않기 때문에, 일괄 업로드 도구를 사용하여 사용자를 직접 멤버로 만들 수 없습니다.  AEM에 속한 IMS 사용자는 이러한 그룹에 개별적으로 추가할 수 있지만, 이 작업을 일괄로 수행하려면 추가 단계가 필요합니다.  이 작업을 수행할 수 있는 한 가지 방법은 다음과 같습니다.
* Admin Console/IMS에서 컬렉션에 액세스할 수 있는 새 그룹 또는 그룹을 생성하고 AEM에 맞게 구성합니다.
* 그룹의 멤버로 로그인하면 그룹이 AEM에 생성됩니다.
* 마이그레이션된 컬렉션의 경우 Assets 컬렉션 UI를 사용하여 새 그룹을 편집자/소유자/뷰어로 추가합니다.
* Admin Console에서 새 그룹에 사용자를 추가(또는 일괄 업로드)합니다.
* 사용자가 처음 로그인하면 IMS 사용자가 AEM에 생성되며, 사용자는 새 그룹과 원래 컬렉션 그룹에 액세스할 수 있게 됩니다.

참고: 사용자를 일괄로 할당하려면 위의 단계를 사용하여 IMS에서 사용자를 만들어야 하며, 일괄 업로드를 통해 이미 IMS에 존재하는 사용자를 다시 만들 수 없습니다.
