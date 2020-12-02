---
title: 프로젝트 워크플로우 작업
description: 다양한 프로젝트 워크플로우를 즉시 사용할 수 있습니다.
translation-type: tm+mt
source-git-commit: 16725342c1a14231025bbc1bafb4c97f0d7cfce8
workflow-type: tm+mt
source-wordcount: '546'
ht-degree: 71%

---


# 프로젝트 워크플로우 작업 {#working-with-project-workflows}

즉시 사용 가능한 프로젝트 워크플로우는 다음과 같습니다.

* **프로젝트 승인 워크플로우**  - 이 워크플로우를 통해 사용자에게 컨텐츠를 지정하고 검토한 다음 승인할 수 있습니다.
* **론치**  요청 - 론치를 요청하는 워크플로우입니다.
* **랜딩 페이지 요청**  - 이 워크플로우는 랜딩 페이지를 요청합니다.
* **요청 이메일** - 이메일을 요청하는 워크플로입니다.
* **DAM 언어 사본 작성 및 번역과 DAM 언어 사본 작성** - 자산 및 폴더에 대한 번역된 바이너리, 메타데이터 및 태그를 생성합니다.

선택하는 프로젝트 템플릿에 따라 사용 가능한 워크플로우가 달라집니다.

|  | **간단한 프로젝트** | **미디어 프로젝트** | **번역 프로젝트** |
|---|:-:|:-:|:-:|
| 사본 요청 |  | x |  |
| 제품 사진 촬영 |  | x |  |
| 프로젝트 승인 | x |  |  |
| 론치 요청 | x |  |  |
| 랜딩 페이지 요청 | x |  |  |
| 이메일 요청 | x |  |  |
| DAM 언어 사본 만들기;ast; |  |  | x |
| DAM 언어 복사 및 번역;ast; |  |  | x |

>[!NOTE]
>
>&amp;ast;이러한 워크플로우는 프로젝트의 **워크플로우** 타일에서 시작하지 않습니다. 자산을 위한 언어 사본 만들기를 참조하십시오.
<!--
>&ast; These workflows are not started from the **Workflow** tile in Projects. See [Creating Language Copies for Assets.](/help/sites-administering/tc-manage.md)
-->

워크플로우 시작 및 완료 단계는 선택하는 워크플로우와 상관없이 동일합니다. 단계만 변경됩니다.

[프로젝트]에서 바로 워크플로우를 시작합니다([DAM 언어 사본 작성]이나 [DAM 언어 사본 작성 및 번역] 제외). 프로젝트에서 아직 처리되지 않은 작업에 대한 정보는 **작업** 타일에 나열됩니다. 완료해야 하는 작업에 대한 알림은 사용자 아이콘 옆에 표시됩니다.

AEM의 워크플로우 작업에 대한 자세한 내용은 다음을 참조하십시오.

* [워크플로우에 참여](/help/sites-cloud/authoring/workflows/participating.md)
* [페이지에 워크플로우 적용](/help/sites-cloud/authoring/workflows/applying.md)
* 워크플로우 구성 <!--* [Configuring workflows](/help/sites-administering/workflows.md)-->

이 섹션에서는 [프로젝트]에 사용 가능한 워크플로우에 대해 설명합니다.

## 사본 요청 워크플로우 {#request-copy-workflow}

이 워크플로우에서는 사용자의 원고를 요청한 다음, 이를 승인할 수 있습니다. 사본 요청 워크플로우를 시작하려면 다음을 수행하십시오.

1. 미디어 프로젝트에서 **워크플로우** 타일의 **+** 기호를 선택하고 **사본 요청 워크플로우**&#x200B;를 선택합니다.
1. 원고 제목과 요청하는 내용에 대한 간단한 요약을 입력합니다. 해당하는 경우 타겟 단어 수, 작업 우선순위 및 기한을 입력하십시오.

   ![복사 요청 워크플로우](/help/sites-cloud/authoring/assets/projects-request-copy.png)

1. **만들기**&#x200B;를 클릭합니다. 워크플로우가 시작됩니다. 작업이 **작업** 타겟에 나타납니다.

   ![요청 카피 추가됨](/help/sites-cloud/authoring/assets/projects-request-copy-add.png)

## 프로젝트 승인 워크플로우 {#project-approval-workflow}

프로젝트 승인 워크플로우에서는 사용자에게 컨텐츠를 지정하고 검토한 다음 컨텐츠를 승인합니다.

1. 단순 프로젝트에서 **워크플로우** 타일의 **`+`** 기호를 선택하고 **프로젝트 승인 워크플로우**&#x200B;를 선택합니다.
1. 제목을 입력하고 팀 목록에서 지정할 사용자를 선택합니다. 해당하는 경우 설명, 컨텐츠 경로, 작업 우선순위 및 기한을 입력하십시오.

   ![승인 요청](/help/sites-cloud/authoring/assets/projects-approval.png)

1. **만들기**&#x200B;를 클릭합니다. 워크플로우가 시작됩니다. 작업이 **작업** 타겟에 나타납니다.

   ![요청 승인 추가됨](/help/sites-cloud/authoring/assets/projects-approval-add.png)

## 론치 요청 워크플로우 {#request-launch-workflow}

이 워크플로우에서는 론치를 요청할 수 있습니다.

1. 간단한 프로젝트에서 **워크플로우** 타일의 **+** 기호를 선택하고 **론치 요청 워크플로우**&#x200B;를 선택합니다.
1. 론치의 제목을 입력하고 론치 소스 경로를 제공합니다. 해당하는 경우 설명과 활성 날짜를 추가할 수도 있습니다. 론치가 동작하는 방식에 따라 [소스 페이지의 라이브 데이터 가져오기]나 [하위 페이지 제외]를 선택하십시오.

   ![론치 요청](/help/sites-cloud/authoring/assets/projects-request-launch.png)

1. **만들기**&#x200B;를 클릭합니다. 워크플로우가 시작됩니다. 워크플로가 **워크플로** 목록에 나타납니다(**줄임표 클릭)...이 목록에 액세스하려면**&#x200B;워크플로&#x200B;**타일의**).

## 자산에 대한 언어 복사 워크플로우 생성(및 번역){#create-and-translate-language-copy-workflow-for-assets}

**언어 사본 만들기** 및 **언어 사본 작성 및 번역 워크플로우는 자산에 대한 언어 사본 만들기에 대해 자세히 다룹니다.**
