---
title: Cloud Manager에서 외부 저장소 추가
description: Cloud Manager에 외부 저장소를 추가하는 방법을 알아보십시오. Cloud Manager은 GitHub Enterprise, GitLab, Bitbucket 및 Azure DevOps 저장소와의 통합을 지원합니다.
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
badge: label="비공개 베타" type="Positive" url="/help/implementing/cloud-manager/release-notes/current.md#gitlab-bitbucket"
exl-id: aebda813-2eb0-4c67-8353-6f8c7c72656c
source-git-commit: b4bbf73cd49f6d7beb47d2edce0910d957879e39
workflow-type: tm+mt
source-wordcount: '2322'
ht-degree: 27%

---

# Cloud Manager에서 외부 저장소 추가 {#external-repositories}

Cloud Manager에 외부 저장소를 추가하는 방법을 알아보십시오. Cloud Manager은 GitHub Enterprise, GitLab 및 Bitbucket 저장소와의 통합을 지원합니다.

이제 고객은 최신 Azure DevOps 및 레거시 VSTS(Visual Studio Team Services) 저장소를 모두 지원하여 Azure DevOps Git 저장소를 Cloud Manager에 온보딩할 수도 있습니다.

* Edge Delivery Services 사용자의 경우 온보딩된 저장소를 사용하여 사이트 코드를 동기화하고 배포할 수 있습니다.
* AEM as a Cloud Service와 Adobe Managed Services(AMS) 사용자의 경우 저장소를 전체 스택 파이프라인과 프론트엔드 파이프라인 모두에 연결할 수 있습니다.

>[!NOTE]
>
>이 문서에 설명된 기능은 개인 베타 프로그램을 통해서만 사용할 수 있습니다. 자세한 내용을 알고 개인 Beta에 등록하려면 [나만의 Git 가져오기](/help/implementing/cloud-manager/release-notes/current.md#gitlab-bitbucket)를 참조하세요.


## 외부 저장소 구성

Cloud Manager에서 외부 저장소를 구성하는 단계는 다음과 같습니다.

1. 선택한 프로그램에 [외부 저장소 추가](#add-external-repo)
1. [검증된 외부 저장소를 파이프라인에 연결](#validate-ext-repo)
   <!-- 1. Provide an access token to the external repository.
    1. Validate ownership of the private GitHub repository. -->
1. 외부 저장소에 [웹후크를 구성](#configure-webhook)합니다.


## 외부 저장소 추가 {#add-ext-repo}

>[!NOTE]
>
>외부 저장소는 구성 파이프라인에 연결할 수 없습니다.

<!-- THIS BULLET REMOVED AS PER https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+2024.12.0+Release. THEY CAN NOW START AUTOMATICALLY>
* Pipelines using external repositories (excluding GitHub-hosted repositories) and the **Deployment Trigger** option [!UICONTROL **On Git Changes**], triggers are not automatically started. They must be manually started. -->


1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)에서 Cloud Manager에 로그인한 다음 적절한 조직을 선택합니다.

1. **[내 프로그램](/help/implementing/cloud-manager/navigation.md#my-programs)** 콘솔에서 외부 리포지토리를 연결할 프로그램을 선택합니다.

1. 사이드 메뉴의 **프로그램**&#x200B;에서 ![폴더 개요 아이콘](https://spectrum.adobe.com/static/icons/workflow_18/Smock_FolderOutline_18_N.svg) **저장소**&#x200B;를 클릭합니다.

   ![저장소 페이지](/help/implementing/cloud-manager/managing-code/assets/repositories-tab.png)

1. **저장소** 페이지의 오른쪽 상단 근처에서 **저장소 추가**&#x200B;를 클릭합니다.

1. **저장소 추가** 대화 상자에서 **비공개 저장소**&#x200B;를 선택하여 외부 Git 저장소를 프로그램에 연결합니다.

   ![자체 저장소 추가](/help/implementing/cloud-manager/managing-code/assets/repositories-private-repo-type.png)

1. 각 필드에 저장소에 대한 다음 세부 정보를 입력합니다.

   | 필드 | 설명 |
   | --- | --- |
   | **저장소 이름** | 필수. 새로운 저장소의 표현적인 이름. |
   | **저장소 URL** | 필수. 저장소의 URL.<br><br>GitHub 호스팅 리포지토리를 사용하는 경우 경로는 `.git`에서 끝나야 합니다.<br>예: *`https://github.com/org-name/repo-name.git`* (URL 경로는 설명 목적으로만 사용됨)<br><br>외부 저장소를 사용하는 경우 다음 URL 경로 형식을 사용해야 합니다. <br>`https://git-vendor-name.com/org-name/repo-name.git`<br> 또는 <br>`https://self-hosted-domain/org-name/repo-name.git`<br> 그리고 Git 공급업체와 일치해야 합니다. |
   | **저장소 유형 선택** | 필수. 사용 중인 저장소 유형을 선택합니다. 저장소 URL 경로에 GitLab 또는 Bitbucket과 같은 Git 공급업체 이름이 포함되어 있는 경우 저장소 유형이 이미 사전 선택되어 있습니다.:<ul><li>**GitHub**(GitHub Enterprise 및 GitHub의 자체 호스팅 버전)</li><li>**GitLab**(`gitlab.com` 및 자체 호스팅 버전의 GitLab 모두) </li><li>**Bitbucket**(`bitbucket.org` - 클라우드 버전만)이 지원됩니다. 자체 호스팅되는 Bitbucket 버전은 2024년 2월 15일부터 더 이상 사용되지 않습니다.)</li><li>**Azure DevOps**(`dev.azure.com`) </ul> |
   | **설명** | 선택 사항. 저장소에 대한 자세한 설명. |

1. **저장**&#x200B;을 선택하여 저장소를 추가합니다.

   이제 액세스 토큰을 제공하여 외부 저장소의 소유권을 확인합니다.

1. **개인 저장소 소유권 확인** 대화 상자에서 액세스할 수 있도록 외부 저장소의 소유권을 확인하는 액세스 토큰을 제공한 다음 **확인**&#x200B;을 클릭합니다.

   ![저장소에 대한 기존 액세스 토큰 선택](/help/implementing/cloud-manager/managing-code/assets/repositories-exisiting-access-token.png)
   *Bitbucket 리포지토리에 대한 기존 액세스 토큰 선택(일러스트레이션에만 해당)*

>[!BEGINTABS]

>[!TAB GitHub Enterprise]

<!-- https://git.corp.adobe.com/pages/experience-platform/cloud-manager-repository-service/#/./git-vendors/github -->

| 액세스 토큰 옵션 | 설명 |
| --- | --- |
| **기존 액세스 토큰 사용** | 조직에 대한 저장소 액세스 토큰을 이미 입력했고 여러 저장소에 대한 액세스 권한이 있는 경우 기존 토큰을 선택할 수 있습니다. **토큰 이름** 드롭다운 목록을 사용하여 저장소에 적용할 토큰을 선택합니다. 그렇지 않은 경우 새로운 액세스 토큰을 추가합니다. |
| **새로운 액세스 토큰 추가** | <ul><li> **토큰 이름** 텍스트 필드에 만들고 있는 액세스 토큰의 이름을 입력하십시오.<li>[GitHub 설명서](https://docs.github.com/en/enterprise-server@3.14/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens)의 지침에 따라 개인 액세스 토큰을 만듭니다.<li>GitHub Enterprise PAT(개인 액세스 토큰)에 필요한 권한<br>이러한 권한을 통해 Cloud Manager은 가져오기 요청의 유효성을 확인하고 커밋 상태 검사를 관리하며 필요한 저장소 세부 정보에 액세스할 수 있습니다.<br>GitHub Enterprise에서 PAT를 생성할 때 다음 저장소 권한이 포함되어 있는지 확인하십시오.<ul><li>가져오기 요청(읽기 및 쓰기)<li>커밋 상태(읽기 및 쓰기)<li>저장소 메타데이터(읽기 전용)</li></li></ul></li></ul></ul></ul><ul><li>**액세스 토큰** 필드에 방금 만든 토큰을 붙여 넣습니다. |

유효성 검사 후에는 외부 저장소를 사용하여 파이프라인에 연결할 준비가 됩니다.

[액세스 토큰 관리](/help/implementing/cloud-manager/managing-code/manage-access-tokens.md)도 참조하세요.

>[!TAB GitLab]

<!-- https://git.corp.adobe.com/pages/experience-platform/cloud-manager-repository-service/#/./git-vendors/gitlab -->

| 액세스 토큰 옵션 | 설명 |
| --- | --- |
| **기존 액세스 토큰 사용** | 조직에 대한 저장소 액세스 토큰을 이미 입력했고 여러 저장소에 대한 액세스 권한이 있는 경우 기존 토큰을 선택할 수 있습니다. **토큰 이름** 드롭다운 목록을 사용하여 저장소에 적용할 토큰을 선택합니다. 그렇지 않은 경우 새로운 액세스 토큰을 추가합니다. |
| **새로운 액세스 토큰 추가** | <ul><li>**토큰 이름** 텍스트 필드에 만들고 있는 액세스 토큰의 이름을 입력하십시오.<li>[GitLab 설명서](https://docs.gitlab.com/user/profile/personal_access_tokens/)의 지침에 따라 개인 액세스 토큰을 만듭니다.<li>GitLab PAT(개인 액세스 토큰)에 대한 필수 권한<br>이러한 범위를 통해 Cloud Manager은 유효성 검사 및 웹후크 통합에 필요한 저장소 데이터 및 사용자 정보에 액세스할 수 있습니다.<br>GitLab에서 PAT를 생성할 때 다음 토큰 범위가 포함되어 있는지 확인하십시오.<ul><li>api<li>read_user</li></li></ul></li></li></ul></ul></ul><ul><li>**액세스 토큰** 필드에 방금 만든 토큰을 붙여 넣습니다. |

유효성 검사 후에는 외부 저장소를 사용하여 파이프라인에 연결할 준비가 됩니다.

[액세스 토큰 관리](/help/implementing/cloud-manager/managing-code/manage-access-tokens.md)도 참조하세요.

>[!TAB Bitbucket]

<!-- https://git.corp.adobe.com/pages/experience-platform/cloud-manager-repository-service/#/./git-vendors/bitbucket -->

| 액세스 토큰 옵션 | 설명 |
| --- | --- |
| **기존 액세스 토큰 사용** | 조직에 대한 저장소 액세스 토큰을 이미 입력했고 여러 저장소에 대한 액세스 권한이 있는 경우 기존 토큰을 선택할 수 있습니다. **토큰 이름** 드롭다운 목록을 사용하여 저장소에 적용할 토큰을 선택합니다. 그렇지 않은 경우 새로운 액세스 토큰을 추가합니다. |
| **새로운 액세스 토큰 추가** | <ul><li>**토큰 이름** 텍스트 필드에 만들고 있는 액세스 토큰의 이름을 입력하십시오.<li>[Bitbucket 설명서](https://support.atlassian.com/bitbucket-cloud/docs/create-a-repository-access-token/)를 사용하여 저장소 액세스 토큰을 만듭니다.<li>Bitbucket PAT(개인 액세스 토큰)에 필요한 권한<br>이러한 권한을 사용하면 Cloud Manager에서 저장소 콘텐츠에 액세스하고, 끌어오기 요청을 관리하며, 웹후크 이벤트를 구성하거나 이에 대응할 수 있습니다.<br>Bitbucket에서 앱 암호를 만들 때 다음 필수 앱 암호 사용 권한이 포함되어 있는지 확인하십시오.<ul><li>저장소(읽기 전용)<li>가져오기 요청(읽기 및 쓰기)<li>웹 후크(읽기 및 쓰기)</li></li></ul></li></li></ul></ul></ul><ul><li>**액세스 토큰** 필드에 방금 만든 토큰을 붙여 넣습니다. |

유효성 검사 후에는 외부 저장소를 사용하여 파이프라인에 연결할 준비가 됩니다.

[액세스 토큰 관리](/help/implementing/cloud-manager/managing-code/manage-access-tokens.md)도 참조하세요.

>[!TAB Azure DevOps]

<!-- https://git.corp.adobe.com/pages/experience-platform/cloud-manager-repository-service/#/./git-vendors/azure_devops -->

| 액세스 토큰 옵션 | 설명 |
| --- | --- |
| **기존 액세스 토큰 사용** | 조직에 대한 저장소 액세스 토큰을 이미 입력했고 여러 저장소에 대한 액세스 권한이 있는 경우 기존 토큰을 선택할 수 있습니다. **토큰 이름** 드롭다운 목록을 사용하여 저장소에 적용할 토큰을 선택합니다. 그렇지 않은 경우 새로운 액세스 토큰을 추가합니다. |
| **새로운 액세스 토큰 추가** | <ul><li>**토큰 이름** 텍스트 필드에 만들고 있는 액세스 토큰의 이름을 입력하십시오.<li>[Azure DevOps 설명서](https://learn.microsoft.com/en-us/azure/devops/organizations/accounts/use-personal-access-tokens-to-authenticate?view=azure-devops&tabs=Windows)를 사용하여 저장소 액세스 토큰을 만듭니다.<li>Azure DevOps Personal Access Token(PAT)에 필요한 권한.<br>이러한 권한을 통해 Cloud Manager은 저장소 콘텐츠에 액세스하고 끌어오기 요청을 관리하며 웹후크 이벤트를 구성하거나 이에 대응할 수 있습니다.<br>Azure DevOps에서 앱 암호를 만들 때 다음 필수 앱 암호 권한이 포함되어 있는지 확인하십시오.<ul><li>저장소(읽기 전용)</li></ul></li></li></ul></ul></ul><ul><li>**액세스 토큰** 필드에 방금 만든 토큰을 붙여 넣습니다. |

유효성 검사 후에는 외부 저장소를 사용하여 파이프라인에 연결할 준비가 됩니다.

[액세스 토큰 관리](/help/implementing/cloud-manager/managing-code/manage-access-tokens.md)도 참조하세요.

>[!ENDTABS]


## 검증된 외부 저장소를 파이프라인에 연결 {#validate-ext-repo}

1. 파이프라인 추가 또는 편집:
   * [프로덕션 파이프라인 추가](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md)
   * [비프로덕션 파이프라인 추가](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md)
   * [파이프라인 편집](/help/implementing/cloud-manager/configuring-pipelines/managing-pipelines.md#editing-pipelines)

   <!-- Add an Edge Delivery Pipeline -->

   ![파이프라인의 소스 코드 저장소 및 Git 분기](/help/implementing/cloud-manager/managing-code/assets/pipeline-repo-gitbranch.png)
   *선택된 저장소 및 Git 분기가 있는 비프로덕션 파이프라인 대화 상자 추가*

1. 파이프라인을 추가하거나 편집할 때 새 파이프라인 또는 기존 파이프라인의 **소스 코드** 위치를 지정하려면 **저장소** 드롭다운 목록에서 사용할 외부 저장소를 선택합니다.

1. **Git 분기** 드롭다운 목록에서 파이프라인의 소스로 사용할 분기를 선택합니다.

1. **저장**&#x200B;을 클릭합니다.


>[!TIP]
>
>Cloud Manager의 저장소 관리에 대한 자세한 내용은 [Cloud Manager 저장소](/help/implementing/cloud-manager/managing-code/managing-repositories.md)를 참조하십시오.


## 외부 저장소에 대한 웹후크 구성 {#configure-webhook}

Cloud Manager을 사용하면 추가한 외부 Git 저장소에 대한 웹후크를 구성할 수 있습니다. [외부 저장소 추가](#add-ext-repo)를 참조하십시오. 이러한 웹후크를 사용하면 Cloud Manager이 Git 공급업체 솔루션 내의 다양한 작업과 관련된 이벤트를 수신할 수 있습니다.

예를 들어 웹 후크를 사용하면 Cloud Manager에서 다음과 같은 이벤트를 기반으로 작업을 트리거할 수 있습니다.

* 끌어오기 요청(PR) 만들기 - PR 유효성 검사 기능을 시작합니다.
* 푸시 이벤트 - &quot;Git Commit 시&quot; 트리거가 켜지면(활성화됨) 파이프라인을 시작합니다.
* 향후 댓글 기반 작업 - PR에서 신속한 개발 환경(RDE)으로 직접 배포하는 것과 같은 워크플로우를 허용합니다.

Cloud Manager은 GitHub 앱을 통해 직접 통합되므로 `GitHub.com`에서 호스팅되는 저장소에 대해 Webhook 구성이 필요하지 않습니다.

GitHub Enterprise, GitLab, Bitbucket 및 Azure DevOps 등 액세스 토큰과 함께 온보딩되는 다른 모든 외부 저장소의 경우 웹후크 구성을 사용할 수 있으며 수동으로 설정해야 합니다.

**외부 저장소에 대한 웹후크를 구성하려면:**

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)에서 Cloud Manager에 로그인한 다음 적절한 조직을 선택합니다.

1. **[내 프로그램](/help/implementing/cloud-manager/navigation.md#my-programs)** 콘솔에서 외부 Git 저장소에 대한 웹후크를 구성할 프로그램을 선택합니다.

1. 페이지의 왼쪽 상단에서 ![메뉴 표시 아이콘](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg)을 클릭하여 왼쪽 사이드 메뉴를 표시합니다.

1. 왼쪽 메뉴에서 **프로그램** 제목 아래의 ![폴더 개요 아이콘](https://spectrum.adobe.com/static/icons/workflow_18/Smock_FolderOutline_18_N.svg) **저장소**&#x200B;을 클릭합니다.

1. **저장소** 페이지에서 **유형** 열을 사용하여 선택 항목을 안내하고 원하는 저장소를 찾은 다음 그 옆에 있는 ![줄임표 - 기타 아이콘](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg)을 클릭합니다.

   ![선택한 저장소의 드롭다운 메뉴에서 Webhook 옵션 구성](/help/implementing/cloud-manager/managing-code/assets/repository-config-webhook.png)

1. 드롭다운 메뉴에서 **Webhook 구성**&#x200B;을 클릭합니다.

   ![Webhook 구성 대화 상자](/help/implementing/cloud-manager/managing-code/assets/config-webhook.png)

1. **Webhook 구성** 대화 상자에서 다음을 수행합니다.

   1. **Webhook URL** 필드 옆에 있는 ![복사 아이콘](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Copy_18_N.svg)을 클릭합니다.
URL을 일반 텍스트 파일에 붙여넣습니다. 복사된 URL은 Git 공급업체의 Webhook 설정에 필요합니다.
   1. **Webhook 암호** 토큰/키 필드 옆에 있는 **생성**&#x200B;을 클릭한 다음 ![복사 아이콘](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Copy_18_N.svg)을 클릭합니다.
암호를 일반 텍스트 파일에 붙여넣습니다. 복사된 암호는 Git 공급업체의 Webhook 설정에 필요합니다.
1. **닫기**&#x200B;를 클릭합니다.
1. Git 공급업체 솔루션(GitHub Enterpriser, GitLab, Bitbucket 또는 Azure DevOps)으로 이동합니다.

   Webhook 구성에 대한 모든 세부 정보와 각 공급업체에 필요한 이벤트는 [외부 저장소 추가](#add-ext-repo)에서 확인할 수 있습니다. 8단계에서 탭 테이블을 참조하십시오.

1. 솔루션의 **Webhook** 설정 섹션을 찾습니다.
1. 이전에 복사한 웹후크 URL을 URL 텍스트 필드에 붙여넣습니다.
   1. Webhook URL의 `api_key` 쿼리 매개 변수를 고유한 실제 API 키로 바꾸십시오.

      API 키를 생성하려면 Adobe Developer Console에서 통합 프로젝트를 만들어야 합니다. 자세한 내용은 [API 통합 프로젝트 만들기](https://developer.adobe.com/experience-cloud/cloud-manager/guides/getting-started/create-api-integration/)를 참조하십시오.

1. 이전에 복사한 웹후크 암호를 **암호**(또는 **암호 키** 또는 **암호 토큰**) 텍스트 필드에 붙여 넣으십시오.
1. Cloud Manager에 필요한 이벤트를 전송하도록 웹후크를 구성합니다. 다음 표를 사용하여 Git 공급자에 대한 올바른 이벤트를 결정하십시오.

>[!BEGINTABS]

>[!TAB GitHub Enterprise]

<!-- https://git.corp.adobe.com/pages/experience-platform/cloud-manager-repository-service/#/./git-vendors/github -->

| 필수 웹후크 이벤트 |
| --- |
| 이러한 이벤트를 사용하면 Cloud Manager에서 끌어오기 요청 유효성 검사, 파이프라인용 푸시 기반 트리거 또는 Edge Delivery Services 코드 동기화와 같은 GitHub 활동에 응답할 수 있습니다.<br>다음 필수 웹후크 이벤트를 트리거하도록 웹후크가 설정되어 있는지 확인하십시오.<ul><li>가져오기 요청<li>푸시<li>문제 주석</li></li></li></ul></ul></ul> |

>[!TAB GitLab]

<!-- https://git.corp.adobe.com/pages/experience-platform/cloud-manager-repository-service/#/./git-vendors/gitlab -->

| 필수 웹후크 이벤트 |
| --- |
| 이러한 웹후크 이벤트를 사용하면 코드가 푸시되거나 병합 요청이 제출될 때 Cloud Manager에서 파이프라인을 트리거할 수 있습니다. 또한 메모 이벤트를 통해 끌어오기 요청 유효성 검사와 관련된 댓글도 추적합니다.<br>다음 필수 웹후크 이벤트를 트리거하도록 웹후크가 설정되어 있는지 확인하십시오<ul><li>푸시 이벤트<li>요청 이벤트 병합<li>메모 이벤트</li></li></li></ul></ul></ul> |

>[!TAB Bitbucket]

<!-- https://git.corp.adobe.com/pages/experience-platform/cloud-manager-repository-service/#/./git-vendors/bitbucket -->

| 필수 웹후크 이벤트 |
| --- |
| 이러한 이벤트를 통해 Cloud Manager은 가져오기 요청의 유효성을 검사하고, 코드 푸시에 응답하고, 파이프라인 조정을 위한 댓글과 상호 작용할 수 있습니다.<br>다음 필수 웹후크 이벤트를 트리거하도록 웹후크가 설정되어 있는지 확인하십시오<ul><li>끌어오기 요청: 생성됨<li>끌어오기 요청: 업데이트됨<li>가져오기 요청: 병합됨<li>끌어오기 요청: 댓글<li>저장소: 푸시</li></li></li></ul></ul></ul> |

>[!TAB Azure DevOps]

<!-- https://git.corp.adobe.com/pages/experience-platform/cloud-manager-repository-service/#/./git-vendors/azure_devops -->

| 필수 웹후크 이벤트 및 인증 |
| --- |
| 이러한 이벤트를 통해 Cloud Manager은 가져오기 요청의 유효성을 검사하고, 코드 푸시에 응답하고, 파이프라인 조정을 위한 댓글과 상호 작용할 수 있습니다.<br>다음 필수 웹후크 이벤트를 트리거하도록 웹후크가 설정되어 있는지 확인하십시오<ul><li>저장소: 푸시</li></ul>인증 설정:<br>1. **기본 인증 사용자 이름** 필드에 `cloudmanager`을(를) 입력합니다.<br>2. **기본 인증 암호** 필드에 Cloud Manager 사용자 인터페이스에서 생성한 Webhook 암호를 입력합니다. |

>[!ENDTABS]


### 웹후크를 사용한 풀 요청 유효성 검사

웹후크가 올바르게 구성되면 Cloud Manager은 저장소에 대한 파이프라인 실행 또는 PR 유효성 검사를 자동으로 트리거합니다.

동작은 아래 설명된 대로 사용하는 Git 공급자에 따라 다릅니다.

>[!BEGINTABS]


>[!TAB GitHub Enterprise]

<!-- https://git.corp.adobe.com/pages/experience-platform/cloud-manager-repository-service/#/./git-vendors/github -->

검사가 생성되면 아래 스크린샷과 같이 표시됩니다. `GitHub.com`과(와) 중요한 차이점은 `GitHub.com`이(가) 확인 실행을 사용하는 반면 GitHub Enterprise(개인 액세스 토큰 사용)는 커밋 상태를 생성한다는 것입니다.

![GitHub Enterprise에서 PR 유효성 검사 프로세스를 나타내는 커밋 상태](/help/implementing/cloud-manager/managing-code/assets/repository-webhook-github-pr-validation.png)


>[!TAB GitLab]

<!-- https://git.corp.adobe.com/pages/experience-platform/cloud-manager-repository-service/#/./git-vendors/gitlab -->

GitLab 상호 작용은 주석에만 의존합니다. 유효성 검사가 시작되면 댓글이 추가됩니다. 유효성 검사가 완료되면(성공 또는 실패) 초기 주석을 제거하고 유효성 검사 결과 또는 오류 세부 정보가 포함된 새 주석으로 대체합니다.

코드 품질 유효성 검사가 실행 중인 경우:

![코드 품질 유효성 검사를 실행하는 경우](/help/implementing/cloud-manager/managing-code/assets/repository-webhook-gitlab1.png)

냉간 품질 유효성 검사가 완료되면:

![냉기 품질 유효성 검사가 완료되면](/help/implementing/cloud-manager/managing-code/assets/repository-webhook-gitlab2.png)

코드 품질 유효성 검사에 실패하고 오류가 발생하는 경우:

![오류와 함께 코드 품질 유효성 검사에 실패하는 경우](/help/implementing/cloud-manager/managing-code/assets/repository-webhook-gitlab3.png)

고객 문제로 인해 코드 품질 유효성 검사가 실패하면:

![고객 문제로 인해 코드 품질 유효성 검사에 실패하는 경우](/help/implementing/cloud-manager/managing-code/assets/repository-webhook-gitlab4.png)


>[!TAB Bitbucket]

<!-- https://git.corp.adobe.com/pages/experience-platform/cloud-manager-repository-service/#/./git-vendors/bitbucket -->

코드 품질 유효성 검사가 실행 중인 경우:

![코드 품질 유효성 검사를 실행하는 동안 상태](/help/implementing/cloud-manager/managing-code/assets/repository-webhook-bitbucket1.png)

PR 유효성 검사 진행 추적을 위해 커밋 상태를 사용합니다. 다음의 경우 스크린샷은 고객 문제로 인해 코드 품질 유효성 검사가 실패하면 어떻게 되는지 보여 줍니다. 자세한 오류 정보가 포함된 댓글이 추가되고 실패를 표시하는 커밋 검사가 만들어집니다(오른쪽에 표시).

![Bitbucket에 대한 끌어오기 요청 유효성 검사 상태](/help/implementing/cloud-manager/managing-code/assets/repository-webhook-bitbucket2.png)



>[!ENDTABS]


## Webhook 문제 해결

* Webhook URL에 유효한 API 키가 포함되어 있는지 확인합니다.
* Git 공급업체 설정에 웹후크 이벤트가 올바르게 구성되어 있는지 확인합니다.
* PR 유효성 검사 또는 파이프라인 트리거가 작동하지 않는 경우 Cloud Manager 및 Git 공급업체 모두에서 웹후크 비밀이 최신 상태인지 확인하십시오.


