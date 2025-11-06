---
title: 마이그레이션 후 주체 관리
description: IMS 및 AEM에서 사용자 및 그룹을 설정하는 방법 알아보기
exl-id: 46c4abfb-7e28-4f18-a6d4-f729dd42ea7b
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '851'
ht-degree: 100%

---

# 마이그레이션 후 주체 관리 {#managing-principals-after-migration}

>[!CONTEXTUALHELP]
>id="managing-principals"
>title="마이그레이션 후 주체 관리"
>abstract="IMS 및 AEM에서 사용자 및 그룹을 설정하는 방법 알아보기"

이 문서에서는 AEM as a Cloud Service 환경을 사용하기 위해 IMS 및 AEM에서 사용자 및 그룹을 설정하는 데 취해야 할 주요 단계를 설명합니다.

그룹 마이그레이션 및 각 수집과 함께 제공되는 주체 마이그레이션 보고서에 대한 정보는 [그룹 마이그레이션](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/group-migration.md)을 참조하십시오.

Admin Console에서 대량 그룹 및 사용자 파일을 사용하는 방법에 대한 안내서는 [CTT 사용 후 IMS에 주체 일괄 업로드](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/bulk-principal-uploading.md)를 참조하십시오.

## 주체 관리 {#managing-principals}

AEM as a Cloud Service의 경우 사용자와 그룹은 주로 Admin Console을 사용하여 관리해야 합니다.  마이그레이션을 고려할 때 이러한 작업 중 일부는 콘텐츠 마이그레이션이 이루어지기 전에 수행할 수 있습니다.  기본적으로 이러한 주요 작업 그룹에는 다음과 같은 것이 있습니다.

* IMS에서 사용자 및 그룹 만들기
* IMS에서 그룹에 사용자 할당
* IMS 그룹을 AEM 그룹에 할당 (필요한 경우)

앞의 두 개는 콘텐츠 마이그레이션 전 또는 후에 수행할 수 있습니다.  이러한 단계는 IMS의 사용자 및 그룹에만 영향을 미치는 단계이며, Active Directory 또는 LDAP와 같은 외부 IDP와의 통합도 포함할 수 있습니다.  이들 단계는 [Admin Console을 사용하는 IMS의 주체 관리](/help/journey-migration/managing-principals.md)에 설명되어 있습니다.

콘텐츠가 AEM as a Cloud Service 환경으로 마이그레이션되면 세 번째 단계를 수행할 수 있습니다.

### 그룹 마이그레이션

마이그레이션의 수집 단계에서 마이그레이션된 콘텐츠에 대한 ACL 또는 CUG 정책을 충족해야 하는 경우 그룹이 마이그레이션됩니다.  자세한 내용은 [그룹 마이그레이션](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/group-migration.md)을 참조하십시오.

마이그레이션된 그룹(Assets 컬렉션 또는 비공개 폴더 생성에 의해 생성되지 않은 그룹 - 아래 컬렉션 및 비공개 폴더 참조)은 IMS 그룹으로 구성됩니다.  즉, IMS에서 생성된 동일한 이름의 그룹(예: Admin Console을 통해)은 AEM의 그룹에 연결되며, IMS 그룹의 멤버인 사용자도 AEM의 그룹 멤버가 됩니다.  이 연결이 이루어지려면 먼저 IMS에서 그룹을 만들어야 합니다.  [Admin Console을 사용하는 IMS의 주체 관리](/help/journey-migration/managing-principals.md)에 설명된 대로 Admin Console을 사용하여 AEM 인스턴스에서 개별적으로 또는 일괄로 그룹을 생성합니다.

AEM 보안 UI를 사용하여 로컬 AEM 그룹에 IMS 그룹을 할당합니다. 이렇게 하려면 AEM의 [도구] 페이지로 이동하여 [보안]을 클릭한 다음 [그룹]을 선택합니다.

### IMS 사용자

사용자는 마이그레이션되지 않으므로 AEM에서 사용할 수 있도록 IMS에서 생성해야 합니다.  이를 달성하는 방법은 여러 가지가 있지만 생성된 사용자가 이전 AEM 시스템에서 사용했던 콘텐츠에 동일하게 액세스할 수 있도록 올바른 IMS 그룹에 할당하는 것이 중요합니다.  여기에 사용할 수 있는 도구 중 하나는 Admin Console의 일괄 업로드 기능입니다. 일괄 업로더를 사용하여 멤버로 소속되어야 할 그룹과 함께 사용자를 업로드할 수 있습니다.  이 작업을 수행하기 전에 위에서 설명한 대로 먼저 IMS에서 그룹을 만들어야 합니다.

각 사용자가 멤버로 소속되어야 할 그룹을 확인하기 위해 사용자 보고서를 활용할 수 있습니다([그룹 마이그레이션](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/group-migration.md) 참조).  이 보고서에는 각 사용자가 멤버로 소속되어야 할 그룹이 나열되어 있으며, 이 목록은 일반적으로 Admin Console 일괄 업로드 기능을 사용하는 대량 사용자 입력 파일에 포함됩니다.

### 컬렉션 및 비공개 폴더

Assets 컬렉션 또는 비공개 폴더를 만들면 해당 자산 콘텐츠에 대한 액세스를 관리할 일부 그룹도 자동으로 생성됩니다.  이러한 그룹은 마이그레이션된 콘텐츠에서 언급된 경우에만 마이그레이션되지만 IMS 그룹에 직접 연결하도록 구성되지 않습니다. 따라서 AEM에서는 “로컬 그룹”으로 남아 있으며 IMS를 통해 관리할 수 없습니다.

이 그룹들은 IMS에 존재하지 않기 때문에, 일괄 업로드 도구를 사용하여 사용자를 직접 멤버로 만들 수 없습니다.  AEM에 속한 IMS 사용자는 이러한 그룹에 개별적으로 추가할 수 있지만 이 작업을 일괄로 수행하려면 추가 단계가 필요합니다.  이 작업을 수행할 수 있는 한 가지 방법은 다음과 같습니다.

* Admin Console/IMS에서 컬렉션/비공개 폴더에 액세스할 수 있는 새 그룹 또는 그룹을 생성하고 AEM에 맞게 구성합니다.
* 그룹의 멤버로 로그인하면 그룹이 AEM에 생성됩니다.
* 마이그레이션된 컬렉션 또는 비공개 폴더의 경우 Assets UI를 사용하여 새 그룹을 편집자/소유자/뷰어로 추가합니다.
* Admin Console에서 새 그룹에 사용자를 추가(또는 일괄 업로드)합니다.
* 사용자가 처음 로그인하면 IMS 사용자가 AEM에 생성되며, 사용자는 새 그룹과 원래 컬렉션 또는 비공개 폴더 그룹에 액세스할 수 있게 됩니다.

참고: 사용자를 일괄 할당하려면 위의 단계를 사용하여 IMS에서 사용자를 만들어야 합니다. IMS에 이미 존재하는 사용자는 일괄 업로드를 통해 다시 만들 수 없지만 일괄 편집기를 사용하여 이러한 종류의 변경을 적용할 수 있습니다(**사용자 세부 정보 편집**&#x200B;의 [Admin Console 일괄 사용자 업로드](https://helpx.adobe.com/kr/enterprise/using/bulk-upload-users.html) 참조).
