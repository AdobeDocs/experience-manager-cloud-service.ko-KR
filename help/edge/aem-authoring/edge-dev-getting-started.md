---
title: Edge Delivery Services를 사용한 AEM 작성을 위한 개발자 시작 안내서
description: 이 안내서는 콘텐츠 작성을 위한 Edge Delivery Services 및 Universal Editor를 사용하여 새로운 Adobe Experience Manager 사이트를 시작하고 실행하는 데 도움이 됩니다.
feature: Edge Delivery Services
exl-id: a71184a7-c954-442e-b276-99edc6d2acd8
source-git-commit: 8bdca5357666841c4471170ab3b97476b6be63b6
workflow-type: tm+mt
source-wordcount: '1296'
ht-degree: 96%

---


# Edge Delivery Services를 사용한 AEM 작성을 위한 개발자 시작 안내서 {#edge-dev-getting-started}

이 안내서는 콘텐츠 작성을 위한 Edge Delivery Services 및 Universal Editor를 사용하여 새로운 Adobe Experience Manager 사이트를 시작하고 실행하는 데 도움이 됩니다.

## 사전 요구 사항 {#prerequisites}

이 안내서를 시작하기 전에 다음을 포함한 Edge Delivery Services의 기본 사항을 숙지하고 액세스할 수 있어야 합니다.

* [Edge Delivery Service 튜토리얼](/help/edge/developer/tutorial.md)이 완료되었습니다.
* [AEM Cloud Service 샌드박스](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/introduction-sandbox-programs.md)에 액세스할 수 있습니다.
* [동일한 샌드박스 환경에서 Universal Editor를 활성화](/help/implementing/universal-editor/getting-started.md)했습니다.

## 적합한 편집기 선택 {#editor-choice}

AEM은 두 가지 콘텐츠 편집기를 제공하며 상황에 따라 사용할 항목을 선택할 수 있도록 지원합니다.

* **Universal Editor** - 새 사이트의 기본 선택 항목이어야 합니다.
* **AEM 페이지 편집기** - Edge Delivery Services로의 기존 AEM Sites 마이그레이션을 위해 선택해야 합니다.

이 안내서는 Universal Editor를 사용하는 Edge Delivery Services의 AEM 프로젝트에 중점을 둡니다. 적합한 편집기를 선택하는 방법 및 기존 AEM Sites를 Edge Delivery Services로 마이그레이션하는 방법에 대한 자세한 내용은 [AEM과 함께 Edge Delivery Services 사용](/help/edge/using.md) 문서를 참조하십시오.

## Edge Delivery Services 개발 시 핵심 개념 {#core-concepts}

Edge Delivery Services는 블록 개념을 기반으로 합니다. AEM에는 프로젝트 요구 사항을 충족하도록 확장할 수 있는 사전 정의된 블록의 포괄적인 라이브러리가 함께 제공됩니다. Edge Delivery Services 프로젝트의 코드는 GitHub에서 관리됩니다.

### 블록 {#blocks}

블록은 Edge Delivery Services에서 제공하는 페이지의 가장 기본적인 부분입니다. 블록은 콘텐츠 페이지의 논리적 구성 요소를 실행하는 스타일과 코드를 캡슐화합니다.

AEM은 프로젝트 상용구 내에서 표준 블록을 제품의 일부로 제공합니다. 이러한 블록에는 제목, 텍스트, 이미지, 링크 및 목록 등이 포함됩니다.

>[!TIP]
>
>Edge Delivery Services용 블록 및 개발 방법에 대한 자세한 내용은 Edge Delivery Services 설명서의 [빌드 섹션](/help/edge/developer/block-collection.md)을 참조하십시오.

### Edge Delivery Services 및 GitHub {#github-edge}

Edge Delivery는 GitHub를 활용하므로 GitHub 저장소에서 바로 코드를 관리 및 배포할 수 있습니다.

작성자는 Universal Editor를 통해 문서 기반 작성 또는 AEM 콘텐츠를 사용하여 콘텐츠를 생성할 수 있습니다. 개발자는 작성자가 콘텐츠를 생성하는 방법에 관계없이 GitHub에서 CSS 및 JavaScript를 사용하여 사이트 기능을 사용자 정의할 수 있습니다.

콘텐츠 미리보기부터 프로덕션까지 각 분기별로 웹 사이트가 자동으로 생성됩니다. GitHub 저장소에 저장된 모든 리소스는 빌드 프로세스 없이 웹 사이트에서 제공됩니다.

>[!TIP]
>
>Edge Delivery Services용 블록 및 개발 방법에 대한 자세한 내용은 Edge Delivery Services 설명서의 [빌드 섹션](/help/edge/developer/block-collection.md)을 참조하십시오.

## AEM 작성 및 Edge Delivery Services 시작하기 {#getting-started}

[사전 요구 사항](#prerequisites)을 충족하고 [Universal Editor를 사용](#editor-choice)하기로 했다면 이제 나만의 프로젝트를 시작할 수 있습니다.

### GitHub 프로젝트 만들기 {#create-github-project}

먼저 Adobe 템플릿을 기반으로 GitHub에서 새 프로젝트를 만들어야 합니다.

1. [`https://github.com/adobe-rnd/aem-boilerplate-xwalk`](https://github.com/adobe-rnd/aem-boilerplate-xwalk)로 이동하여 **이 템플릿 사용**&#x200B;을 클릭하고 **새 저장소 생성**&#x200B;을 선택합니다.

   * 이 옵션을 보려면 GitHub에 로그인해야 합니다.

   ![저장소 프로젝트 복사](assets/edge-dev-getting-started/use-template-project.png)

1. 기본적으로 저장소는 사용자에게 할당됩니다. 필요에 따라 이를 변경하고 저장소 이름과 설명을 입력한 후 **저장소 생성**&#x200B;을 클릭합니다.

   ![저장소 생성](assets/edge-dev-getting-started/create-repo.png)

1. 동일한 브라우저의 새 탭에서 [`https://github.com/apps/aem-code-sync`](https://github.com/apps/aem-code-sync)로 이동하여 **구성**&#x200B;을 클릭합니다.

   ![Code Sync](assets/edge-dev-getting-started/configure-code-sync.png)

1. 이전 단계에서 새 저장소를 생성한 조직에 대해 **구성**&#x200B;을 클릭합니다.

   ![코드 동기화를 위한 조직 선택](assets/edge-dev-getting-started/code-sync-org.png)

1. AEM Code Sync GitHub 페이지의 **저장소 액세스** 아래에서 **저장소만 선택**&#x200B;을 선택하고, 이전 단계에서 생성한 저장소를 선택한 다음 **저장**&#x200B;을 클릭합니다.

   ![AEM Code Sync 액세스 권한 부여](assets/edge-dev-getting-started/grant-code-sync-acces.png)

1. AEM Code Sync가 설치되면 확인 화면이 표시됩니다. 새 저장소의 브라우저 탭으로 돌아갑니다.

   ![Code Sync 설치 확인](assets/edge-dev-getting-started/confirmation.png)

1. `fstab.yaml` 파일을 클릭하여 열고 **이 파일 편집** 아이콘을 클릭하여 편집합니다.

   ![fstab.yaml](assets/edge-dev-getting-started/fstab.png)

1. `fstab.yaml` 파일을 편집하여 프로젝트의 마운트 지점을 업데이트합니다. 기본 Google Docs URL을 AEM as a Cloud Service 작성 인스턴스의 URL로 바꾼 다음 **변경 사항 커밋...**&#x200B;을 클릭합니다.

   * `https://<aem-author>/bin/franklin.delivery/<owner>/<repository>/main`
   * 마운트 지점을 변경하면 Edge Delivery Services에 사이트의 콘텐츠를 찾을 수 있는 위치가 알려집니다.

   ![fstab 업데이트](assets/edge-dev-getting-started/fstab-update.png)

1. 원하는 대로 커밋 메시지를 추가한 다음 **변경 사항 커밋**&#x200B;을 클릭하여 `main` 분기에 직접 커밋합니다.

   ![변경 사항 커밋](assets/edge-dev-getting-started/commit-fstab-changes.png)

1. 저장소 루트로 돌아가서 `paths.json`를 클릭한 다음 **이 파일 편집** 아이콘을 클릭합니다.

   ![paths.json](assets/edge-dev-getting-started/paths.png)

1. 기본 매핑은 저장소 이름을 사용합니다. `/content/<site-name>/:/`를 사용하여 프로젝트에 필요한 기본 매핑을 업데이트하고 **변경 사항 커밋...**&#x200B;을 클릭합니다.

   * 자체 `<site-name>`을 입력합니다. 이는 이후 단계에서 필요합니다.
   * 매핑은 Edge Delivery Services에 AEM 저장소의 콘텐츠를 사이트 URL에 매핑하는 방법을 알려 줍니다.

   ![paths.json 업데이트](assets/edge-dev-getting-started/paths-update.png)

1. 원하는 대로 커밋 메시지를 추가한 다음 **변경 사항 커밋**&#x200B;을 클릭하여 `main` 분기에 직접 커밋합니다.

   ![변경 사항 커밋](assets/edge-dev-getting-started/commit-paths-changes.png)

### 새 AEM 사이트 만들기 및 편집 {#create-aem-site}

이제 GitHub 프로젝트가 있으므로 프로젝트에서 사용할 수 있는 새 AEM 사이트를 만들어야 합니다.

>[!NOTE]
>
>Universal Editor를 사용하여 사이트를 편집하려면 Chromium 기반 브라우저를 사용해야 합니다.

1. GitHub의 Edge Delivery Services 사이트 템플릿을 사용하여 최신 AEM 작성 다운로드: [`https://github.com/adobe-rnd/aem-boilerplate-xwalk/releases`](https://github.com/adobe-rnd/aem-boilerplate-xwalk/releases).

1. AEM as a Cloud Service 작성 인스턴스에 로그인하고 사이트 콘솔로 이동하여 **만들기** -> **템플릿으로 사이트 생성**&#x200B;을 탭하거나 클릭합니다.

   ![콘솔에서 새 사이트 만들기](assets/edge-dev-getting-started/create-site-console.png)

1. 사이트 생성 마법사의 **사이트 템플릿 선택** 탭에서 **가져오기** 버튼을 클릭하여 새 템플릿을 가져옵니다.

   ![템플릿 가져오기](assets/edge-dev-getting-started/site-templates.png)

1. GitHub에서 다운로드한 Edge Delivery Services 사이트 템플릿을 사용하여 AEM 작성 을 업로드합니다.

   * 템플릿은 한 번만 업로드해야 합니다. 업로드한 후에는 다시 사용하여 추가 사이트를 만들 수 있습니다.

1. 템플릿을 가져오면 마법사에 표시됩니다. 탭하거나 클릭하여 선택한 후 **다음**&#x200B;을 탭하거나 클릭합니다.

   ![템플릿 선택](assets/edge-dev-getting-started/select-template.png)

1. 다음 필드를 입력하고 **만들기**&#x200B;를 탭하거나 클릭합니다.

   * **사이트 제목** - 사이트를 설명하는 제목을 추가합니다.
   * **사이트 제목** - [이전 단계](#create-github-project)에서 정의한 `<site-name>`을(를) 사용합니다.
   * **GitHub URL** - 이전 단계에서 생성한 GitHub 프로젝트의 URL을 사용합니다.

   ![사이트 세부 정보](assets/edge-dev-getting-started/create-site-details.png)

1. AEM은 대화 상자를 통해 사이트 생성을 확인합니다. **확인**&#x200B;을 탭하거나 클릭하여 닫습니다.

   ![사이트 생성 확인](assets/edge-dev-getting-started/site-creation-confirmation.png)

1. 사이트 콘솔에서 새로 생성된 사이트의 `index.html`로 이동하고 도구 모음에서 **편집**&#x200B;을 탭하거나 클릭합니다.

   ![새 사이트 편집](assets/edge-dev-getting-started/new-site.png)

1. Universal Editor가 새 탭에서 열립니다. 페이지를 편집하기 위해 **Adobe에 로그인**&#x200B;을 탭하거나 클릭하여 인증해야 할 수도 있습니다.

   ![Universal Editor](assets/edge-dev-getting-started/universal-editor.png)

이제 Universal Editor를 사용하여 사이트를 편집할 수 있습니다. 자세한 내용은 [Universal Editor 설명서](/help/sites-cloud/authoring/universal-editor/authoring.md)를 참조하십시오.

### 새 사이트 게시 {#publishing}

Universal Editor를 사용하여 새 사이트 편집을 마쳤다면 콘텐츠를 게시할 수 있습니다.

1. 사이트 콘솔에서 새 사이트에 대해 생성한 모든 페이지를 선택하고 도구 모음에서 **빠른 게시**&#x200B;를 탭하거나 클릭합니다.

   ![게시할 페이지 선택](assets/edge-dev-getting-started/publishing.png)

1. 확인 대화 상자에서 **게시**&#x200B;를 탭하거나 클릭하여 프로세스를 시작합니다.

   ![게시 대화 상자](assets/edge-dev-getting-started/publish-confirmation.png)

1. 동일한 브라우저에서 새 탭을 열고 새 사이트의 URL로 이동합니다.

   * `https://main--<site-name>--<owner>.hlx.page`

1. 게시된 콘텐츠를 확인합니다.

   ![게시된 콘텐츠](assets/edge-dev-getting-started/published-site.png)

## 다음 단계 {#next-steps}

Edge Delivery Services 프로젝트와 함께 AEM이 작성되어 있으며, 자체 블록을 만들고 스타일을 지정할 수 있습니다.

자세한 내용은 [Universal Editor에 사용하도록 구성된 블록 만들기](/help/edge/aem-authoring/create-block.md) 안내서를 참조하십시오.

>[!TIP]
>
>AEM as a Cloud Service를 콘텐츠 소스로 사용하여 AEM 작성에 활성화된 새로운 Edge Delivery Services 프로젝트를 만드는 방법에 대한 전체 연습을 보려면 [이 AEM GEM 웨비나](https://experienceleague.adobe.com/en/docs/events/experience-manager-gems-recordings/gems2024/aem-authoring-and-edge-delivery)를 시청하십시오.

