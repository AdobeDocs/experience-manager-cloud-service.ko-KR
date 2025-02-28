---
title: Cloud Manager에서 외부 저장소 추가 (얼리 어답터)
description: Cloud Manager에 외부 저장소를 추가하는 방법을 알아보십시오. Cloud Manager는 GitHub, GitLab 및 Bitbucket 저장소와의 통합을 지원합니다.
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
exl-id: aebda813-2eb0-4c67-8353-6f8c7c72656c
source-git-commit: bd05433bb4d92a4120b19ad99d211a4a5e1f06ca
workflow-type: tm+mt
source-wordcount: '763'
ht-degree: 87%

---

# Cloud Manager에서 외부 저장소 추가 {#external-repositories}

Cloud Manager에 외부 저장소를 추가하는 방법을 알아보십시오. Cloud Manager는 GitHub, GitLab 및 Bitbucket 저장소와의 통합을 지원합니다.

>[!NOTE]
>
>이 기능은 조기 채택 프로그램을 통해서만 사용할 수 있습니다. 자세한 내용을 알고 얼리 어답터로 등록하려면 [GitLab 및 Bitbucket에 대한 지원을 통해 지금 자신의 Git을 가져오세요](/help/implementing/cloud-manager/release-notes/2024/2024-10-0.md#gitlab-bitbucket)를 참조하세요.

## 외부 저장소 구성

Cloud Manager에서 외부 저장소를 구성하는 작업은 세 단계로 구성됩니다.

1. 선택한 프로그램에 [외부 저장소를 추가](#add-external-repo)합니다.
1. 외부 저장소에 액세스 토큰을 입력합니다.
1. 개인 GitHub 저장소의 소유권을 확인합니다.


## 외부 저장소 추가 {#add-ext-repo}

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)에서 Cloud Manager에 로그인한 다음 적절한 조직을 선택합니다.

1. **[내 프로그램](/help/implementing/cloud-manager/navigation.md#my-programs)** 콘솔에서 외부 리포지토리를 연결할 프로그램을 선택합니다.

1. 측면 메뉴의 **서비스**&#x200B;에서 ![폴더 아이콘](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Folder_18_N.svg) **저장소**&#x200B;를 선택합니다.

   ![저장소 페이지](/help/implementing/cloud-manager/managing-code/assets/repositories-tab.png)

1. **저장소** 페이지의 오른쪽 상단 근처에서 **저장소 추가**&#x200B;를 클릭합니다.

1. **저장소 추가** 대화 상자에서 **비공개 저장소**&#x200B;를 선택하여 외부 Git 저장소를 프로그램에 연결합니다.

   ![자체 저장소 추가](/help/implementing/cloud-manager/managing-code/assets/repositories-private-repo-type.png)

1. 각 필드에 저장소에 대한 다음 세부 정보를 입력합니다.

   | 필드 | 설명 |
   | --- | --- |
   | **저장소 이름** | 필수. 새로운 저장소의 표현적인 이름. |
   | **저장소 URL** | 필수. 저장소의 URL.<br><br>GitHub 호스팅 리포지토리를 사용하는 경우 경로는 `.git`에서 끝나야 합니다.<br>예: *`https://github.com/org-name/repo-name.git`* (URL 경로는 설명 목적으로만 사용됨)<br><br>외부 저장소를 사용하는 경우 다음 URL 경로 형식을 사용해야 합니다. <br>`https://git-vendor-name.com/org-name/repo-name.git`<br> 또는 <br>`https://self-hosted-domain/org-name/repo-name.git`<br> 그리고 Git 공급업체와 일치해야 합니다. |
   | **저장소 유형 선택** | 필수. 다음 중 사용하는 저장소 유형을 선택합니다. **GitHub**, **GitLab** 또는 **BitBucket**. 위의 저장소 URL 경로에 GitLab이나 Bitbucket과 같은 Git 공급업체 이름이 포함되어 있는 경우 저장소 유형이 미리 선택됩니다. |
   | **설명** | 선택 사항. 저장소에 대한 자세한 설명. |

1. **저장**&#x200B;을 선택하여 저장소를 추가합니다.

1. **비공개 저장소 소유권 유효성 검사** 대화 상자에서 액세스 토큰을 입력하여 외부 저장소에 액세스할 수 있도록 소유권 유효성을 검사합니다.

   ![저장소에 대한 기존 액세스 토큰 선택](/help/implementing/cloud-manager/managing-code/assets/repositories-exisiting-access-token.png)
   *BitBucket 저장소에 대한 기존 액세스 토큰 선택.*

   | 토큰 유형 | 설명 |
   | --- | --- |
   | **기존 액세스 토큰 사용** | 조직에 대한 저장소 액세스 토큰을 이미 입력했고 여러 저장소에 대한 액세스 권한이 있는 경우 기존 토큰을 선택할 수 있습니다. **토큰 이름** 드롭다운 목록을 사용하여 저장소에 적용할 토큰을 선택합니다. 그렇지 않은 경우 새로운 액세스 토큰을 추가합니다. |
   | **새로운 액세스 토큰 추가** | **저장소 유형: GitHub**<br>• **토큰 이름** 텍스트 필드에 생성하려는 액세스 토큰의 이름을 입력합니다.<br>• [GitHub 설명서](https://docs.github.com/en/enterprise-server@3.14/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens)의 지침에 따라 개인 액세스 토큰을 만듭니다.<br>• 필요 권한:<br>  • `Read access to metadata`.<br>  • `Read and write access to code and pull requests`.<br>• **액세스 토큰** 필드에 방금 만든 토큰을 붙여넣습니다. |
   |  | **저장소 유형: GitLab**<br>• **토큰 이름** 텍스트 필드에 생성하려는 액세스 토큰의 이름을 입력합니다.<br>• [GitLab 설명서](https://docs.gitlab.com/user/profile/personal_access_tokens/)의 지침에 따라 개인 액세스 토큰을 만듭니다.<br>• 필요 권한:<br>  • `api`<br>  • `read_api`<br>  • `read_repository`<br>  • `write_repository`<br>• **액세스 토큰** 필드에 방금 만든 토큰을 붙여넣습니다. |
   |  | **저장소 유형: Bitbucket**<br>• **토큰 이름** 텍스트 필드에 생성하려는 액세스 토큰의 이름을 입력합니다.<br>• [Bitbucket 설명서](https://support.atlassian.com/bitbucket-cloud/docs/create-a-repository-access-token/)를 사용하여 저장소 액세스 토큰을 만듭니다.<br>• 필요 권한:<br>  • `Read and write access to code and pull requests`. |

   >[!NOTE]
   >
   >**새로운 액세스 토큰 추가** 기능은 현재 얼리 어답터 단계에 있습니다. 추가 기능이 계획 중입니다. 따라서 액세스 토큰에 필요한 권한이 변경될 수 있습니다. 또한 토큰을 관리하기 위한 사용자 인터페이스가 업데이트될 수 있으며, 토큰 만료일과 같은 기능이 포함될 수 있습니다. 또한 저장소에 연결된 토큰이 유효한지 자동으로 확인하는 검사도 제공됩니다.

1. **유효성 검사**&#x200B;를 클릭합니다.

유효성 검사 후에는 외부 저장소를 사용하여 파이프라인에 연결할 준비가 됩니다.

## 검증된 외부 저장소를 파이프라인에 연결 {#validate-ext-repo}

1. 파이프라인 추가 또는 편집:
   * [프로덕션 파이프라인 추가](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md)
   * [비프로덕션 파이프라인 추가](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md)
   * [파이프라인 편집](/help/implementing/cloud-manager/configuring-pipelines/managing-pipelines.md#editing-pipelines)

   ![파이프라인의 소스 코드 저장소 및 Git 분기](/help/implementing/cloud-manager/managing-code/assets/pipeline-repo-gitbranch.png)
   *선택된 저장소 및 Git 분기가 있는 비프로덕션 파이프라인 대화 상자 추가*

1. 파이프라인을 추가하거나 편집할 때 새 파이프라인 또는 기존 파이프라인의 **소스 코드** 위치를 지정하려면 **저장소** 드롭다운 목록에서 사용할 외부 저장소를 선택합니다.

1. **Git 분기** 드롭다운 목록에서 파이프라인의 소스로 사용할 분기를 선택합니다.

1. **저장**&#x200B;을 클릭합니다.


>[!TIP]
>
>Cloud Manager의 저장소 관리에 대한 자세한 내용은 [Cloud Manager 저장소](/help/implementing/cloud-manager/managing-code/managing-repositories.md)를 참조하십시오.


## 제한 사항

* 외부 저장소는 구성 파이프라인에 연결할 수 없습니다.
* 외부 저장소(GitHub에서 호스팅되지 않음) 및 &quot;Git 변경 시&quot; 트리거가 있는 파이프라인은 자동으로 시작되지 않습니다. 수동으로 시작할 수만 있습니다.


<!-- THIS BULLET REMOVED AS PER https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+2024.12.0+Release. THEY CAN NOW START AUTOMATICALLY>
* Pipelines using external repositories (excluding GitHub-hosted repositories) and the **Deployment Trigger** option [!UICONTROL **On Git Changes**], triggers are not automatically started. They must be manually started. -->
