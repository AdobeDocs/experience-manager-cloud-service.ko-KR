---
title: 프로젝트
description: 프로젝트를 사용하면 리소스를 하나의 엔티티로 그룹화하여 공통, 공유 환경에서 프로젝트를 쉽게 관리할 수 있습니다.
translation-type: tm+mt
source-git-commit: fee73b5f5ba69422494efe554ac5aa62c046ad86
workflow-type: tm+mt
source-wordcount: '1269'
ht-degree: 76%

---


# 프로젝트 {#projects}

프로젝트를 사용하면 리소스를 하나의 엔티티로 그룹화할 수 있습니다. 공통되는 공유 환경을 사용하면 프로젝트 관리가 쉬워집니다. 프로젝트와 연결할 수 있는 리소스 유형은 AEM에서 타일이라고 합니다. 타일에는 [프로젝트 타일에 자세히 설명된 대로 프로젝트 및 팀 정보, 자산, 워크플로우 및 기타 유형의 정보가 포함될 수 있습니다.](#project-tiles)

>[!CAUTION]
>
>프로젝트 사용자가 프로젝트 만들기, 작업/워크플로우 만들기, 팀 보기 및 관리와 같은 프로젝트 기능을 사용하는 동안 다른 사용자/그룹을 보려면 해당 사용자는 `/home/users` 및 `/home/groups`에 대한 읽기 권한이 있어야 합니다. 이를 구현하는 가장 쉬운 방법은 **projects-users** 그룹에 `/home/users` 및 `/home/groups`에 대한 읽기 액세스 권한을 제공하는 것입니다.

사용자라면, 다음을 수행할 수 있습니다.

* 프로젝트 만들기
* 컨텐츠 및 자산 폴더를 프로젝트에 연결
* 프로젝트 삭제
* 프로젝트에서 컨텐츠 링크 제거

다음 추가 항목을 참조하십시오.

* [프로젝트 관리](/help/sites-cloud/authoring/projects/managing.md)
* [작업](/help/sites-cloud/authoring/projects/tasks.md)
* [프로젝트 워크플로우 작업](/help/sites-cloud/authoring/projects/workflows.md)

## 프로젝트 콘솔 {#projects-console}

프로젝트 콘솔은 AEM 내 프로젝트를 액세스하고 관리하는 곳입니다.

![프로젝트 콘솔](/help/sites-cloud/authoring/assets/projects-console.png)

* 타임라인을 보려면 **타임라인**&#x200B;을 선택한 다음, 프로젝트를 선택합니다.
* 선택 모드로 전환하려면 **선택**&#x200B;을 클릭/탭합니다.
* 프로젝트를 추가하려면 **만들기**&#x200B;를 클릭합니다.
* **활성 프로젝트 전환**&#x200B;을 사용하면 모든 프로젝트 표시와 활성 상태 프로젝트만 표시 사이를 전환할 수 있습니다.
* **통계 보기 표시**&#x200B;를 사용하면 작업 완료에 관련된 프로젝트 통계를 볼 수 있습니다.

## 프로젝트 타일 {#project-tiles}

프로젝트 콘솔에서는 다양한 유형의 정보를 프로젝트와 연결할 수 있습니다. 이것을 **타일**&#x200B;이라고 합니다. 각 타일과 타일이 포함하는 정보의 종류는 이 섹션에 설명되어 있습니다.

다음 타일을 프로젝트와 연결할 수 있습니다. 각 타일은 다음에 나오는 섹션들에서 설명합니다.

* 자산 및 자산 컬렉션
* 경험
* 링크
* 프로젝트 정보
* 팀
* 랜딩 페이지
* 이메일
* 워크플로우
* 론치
* 작업

### 자산 {#assets}

**자산** 타일에서는 특정 프로젝트에 사용하는 모든 자산을 수집할 수 있습니다.

![자산 타일](/help/sites-cloud/authoring/assets/projects-assets-tile.png)

타일에서 바로 자산을 업로드할 수 있습니다. 또한 Dynamic Media 추가 기능이 있는 경우 이미지 세트, 스핀 세트 또는 혼합 미디어 집합을 만들 수 있습니다.

![이미지 세트](/help/sites-cloud/authoring/assets/projects-image-sets.png)

### 자산 컬렉션 {#asset-collections}

자산과 유사하게 [자산 컬렉션](/help/assets/manage-collections.md)도 프로젝트에 바로 추가할 수 있습니다. [자산]에서 컬렉션을 정의합니다.

![자산 수집](/help/sites-cloud/authoring/assets/projects-asset-collections.png)

**컬렉션 추가**&#x200B;를 클릭하고 목록에서 적절한 컬렉션을 선택하여 컬렉션을 추가하십시오.

### 경험  {#experiences}

**경험** 타일에서는 모바일 앱, 웹 사이트 또는 발행을 프로젝트에 추가할 수 있습니다.

![경험](/help/sites-cloud/authoring/assets/project-experiences.png)

아이콘은 표시되는 경험의 종류(웹 사이트, 모바일 애플리케이션 또는 발행)를 나타냅니다. + 부호를 클릭하거나 **경험 추가**&#x200B;를 클릭하고 경험 유형을 선택하여 경험을 추가하십시오.

![경험 추가](/help/sites-cloud/authoring/assets/projects-add-experience.png)

썸네일 경로를 선택하고, 해당하는 경우에는 경험의 썸네일을 변경합니다. 경험은 **경험** 타겟에서 함께 그룹화됩니다.

### 링크 {#links}

링크 타일을 사용하면 외부 링크를 프로젝트와 연결할 수 있습니다.

![링크](/help/sites-cloud/authoring/assets/project-links.png)

링크 이름을 알아채기 쉬운 이름으로 지정할 수도 있고 썸네일을 변경할 수도 있습니다.

![링크 추가](/help/sites-cloud/authoring/assets/projects-add-link.png)

### 프로젝트 정보 {#project-info}

프로젝트 정보 타일은 설명, 프로젝트 상태(비활성 또는 활성), 기한 및 구성원을 포함하여 프로젝트에 대한 일반 정보를 제공합니다. 또한 메인 프로젝트 페이지에 표시되는 프로젝트 썸네일을 추가할 수도 있습니다.

![프로젝트 정보](/help/sites-cloud/authoring/assets/project-info.png)

팀 구성원은 팀 타일뿐만 아니라 이 타일에서도 지정 및 삭제될 수 있습니다(또는 자신의 역할을 변경할 수 있습니다.).

![프로젝트에 팀 구성원 추가](/help/sites-cloud/authoring/assets/projects-add-team.png)

### 번역 작업 {#translation-job}

번역 작업 타일은 번역을 시작하는 곳이며 번역 상태도 볼 수 있는 곳이기도 합니다. 번역을 설정하려면 [번역 프로젝트 만들기](/help/assets/translate-assets.md)를 참조하십시오.

![번역 작업](/help/sites-cloud/authoring/assets/projects-translation-job.png)

번역 워크플로우에서 자산을 보려면 **번역 작업** 카드의 하단에 있는 줄임표를 클릭합니다. 번역 작업 목록에는 자산 메타데이터 및 태그에 대한 항목도 표시됩니다. 이 항목들은 자산의 메타데이터와 태그도 번역됨을 나타냅니다.

![번역 작업 세부 사항](/help/sites-cloud/authoring/assets/projects-translation-job-detail.png)

### 팀 {#team}

이 타일에서는 프로젝트 팀의 구성원을 지정할 수 있습니다. 편집 시에는 팀 구성원의 이름을 입력하고 사용자 역할을 지정할 수 있습니다.

![팀 타일](/help/sites-cloud/authoring/assets/projects-team-tile.png)

팀에서 팀 구성원을 추가하고 삭제할 수 있습니다. 또한 팀 구성원에게 지정된 [사용자 역할](#user-roles-in-a-project)을 편집할 수도 있습니다.

![목록에서 팀 추가](/help/sites-cloud/authoring/assets/projects-add-team-list.png)

### 워크플로우 {#workflows}

특정 워크플로우를 따르도록 프로젝트를 지정할 수 있습니다. 실행 중인 워크플로우가 있는 경우 워크플로우 상태가 [프로젝트]의 **워크플로우** 타일에 표시됩니다.

![워크플로우](/help/sites-cloud/authoring/assets/project-workflows.png)

특정 워크플로우를 따르도록 프로젝트를 지정할 수 있습니다. 선택하는 프로젝트에 따라 다른 워크플로우를 사용할 수 있습니다.

이에 대해서는 [프로젝트 워크플로우 작업](/help/sites-cloud/authoring/projects/workflows.md)에 설명되어 있습니다.

### 론치 {#launches}

론치 타일에는 [론치 요청 워크플로우](/help/sites-cloud/authoring/projects/workflows.md)에서 요청한 론치가 표시됩니다.

![론치](/help/sites-cloud/authoring/assets/project-launches.png)

### 작업 {#tasks}

작업을 사용하면 워크플로우를 포함하여 프로젝트 관련 작업의 상태를 모니터링할 수 있습니다. 작업은 [작업](/help/sites-cloud/authoring/projects/tasks.md)에서 자세히 다룹니다.

![작업](/help/sites-cloud/authoring/assets/projects-tasks.png)

## 프로젝트 템플릿 {#project-templates}

AEM은 다음과 같은 세 가지 서로 다른 템플릿을 제공합니다.

* 간단한 프로젝트 - 다른 카테고리에 맞지 않는 모든 프로젝트에 대한 참조 샘플입니다(모두 포함). 여기에는 세 개의 기본 역할(소유자, 편집자 및 옵저버)과 네 개의 워크플로우(프로젝트 승인, 론치 요청, 랜딩 페이지 요청 및 이메일 요청)가 포함됩니다.
* 미디어 프로젝트 - 미디어 관련 활동을 위한 참조 샘플 프로젝트입니다. 여기에는 몇 가지의 미디어 관련 프로젝트 역할(사진사, 편집자, 카피라이터, 디자이너, 소유자 및 옵저버)이 포함되며, 또한 미디어 컨텐츠와 관련된 두 가지 워크플로우인 사본 요청(텍스트 요청 및 검토용) 및 제품 사진 촬영(제품 관련 사진 관리용)이 포함되어 있습니다.
* 번역 프로젝트 - 번역 관련 활동을 관리하기 위한 참조 샘플입니다. 여기에는 세 개의 기본 역할(소유자, 편집자 및 옵저버)이 포함됩니다. 또한 워크플로우 사용자 인터페이스에서 액세스하는 두 개의 워크플로우도 포함됩니다. <!--* [A translation project](/help/sites-administering/translation.md) - A reference sample for managing translation related activities. It includes three basic roles (Owners, Editors, and Observers). It includes two workflows that are accessed in the Workflows user interface.-->

선택하는 템플릿에 따라, 특히 사용자 역할 및 워크플로우와 관련하여 사용할 수 있는 선택 사항들이 다릅니다.

## 프로젝트의 사용자 역할  {#user-roles-in-a-project}

다양한 사용자 역할이 프로젝트 템플릿에서 설정되며 다음의 두 가지 기본 이유로 사용됩니다.

1. 권한. 사용자 역할은 옵저버, 편집자, 소유자, 이렇게 세 범주 중 하나에 속합니다. 예를 들어, 사진사나 카피라이터는 편집자와 동일한 권한을 가집니다. 권한은 사용자가 프로젝트의 컨텐츠에 수행할 수 있는 작업을 결정합니다.
1. 워크플로우. 워크플로우는 프로젝트에서 작업을 지정받을 사용자를 결정합니다. 작업은 프로젝트 역할과 연결할 수 있습니다. 예를 들어, 작업을 [사진사]에게 지정할 수 있으므로 사진사 역할을 하는 모든 팀 구성원이 작업을 받게 됩니다.

모든 프로젝트는 보안을 관리하고 권한을 제어할 수 있도록 다음의 기본 역할을 지원합니다.

| 역할 | 설명 | 권한 | 그룹 구성원 |
|---|---|---|---|
| 관찰자 | 이 역할의 사용자는 프로젝트 상태를 포함하여 프로젝트 세부 사항을 볼 수 있습니다. | 프로젝트에 대한 읽기 전용 권한 | `workflow-users` 그룹 |
| 편집자 | 이 역할의 사용자는 프로젝트 컨텐츠를 업로드하고 편집할 수 있습니다. | 프로젝트, 관련 메타데이터 및 관련 자산에 대한 읽기 및 쓰기 액세스촬영 목록 업로드, 사진 촬영, 자산 검토 및 승인 권한/etc/commerce;특정 프로젝트에 대한 권한 수정 | workflow-users 그룹 |
| 소유자 | 이 역할의 사용자는 프로젝트를 시작할 수 있습니다. 소유자는 프로젝트를 만들고, 프로젝트에서 작업을 시작하고, 승인된 자산을 프로덕션 폴더로 이동할 수도 있습니다. 하지만, 프로젝트의 다른 모든 작업은 소유자가 보고 수행할 수도 있습니다. | `/etc/commerce`에 쓰기 권한 | `dam-users` 그룹(프로젝트 만들기) 프로젝트-관리자 그룹(자산 이동 가능) |

>[!NOTE]
>
>프로젝트를 생성하고 사용자를 다양한 역할에 추가하면 연결된 권한을 관리하도록 프로젝트와 연결된 그룹이 자동으로 생성됩니다. 예를 들어 Myproject라는 프로젝트에는 세 개의 그룹 **Myproject 소유자**, **Myproject 편집자**, **Myproject 관찰자**&#x200B;가 있습니다. 그러나 프로젝트가 삭제되는 경우에는 해당 그룹이 자동으로 삭제되지 않습니다. 관리자는 **도구** > **보안** > **그룹**&#x200B;에서 직접 그룹을 삭제해야 합니다.
