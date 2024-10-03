---
title: Cloud Manager에서 외부 저장소 추가(얼리 어답터)
description: Cloud Manager에 외부 저장소를 추가하는 방법을 알아봅니다. Cloud Manager은 GitHub, GitLab 및 Bitbucket 저장소와의 통합을 지원합니다.
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: b90ace2250277005d8ac250c841104c93298a605
workflow-type: tm+mt
source-wordcount: '742'
ht-degree: 5%

---


# Cloud Manager에서 외부 저장소 추가 {#external-repositories}

Cloud Manager에 외부 저장소를 추가하는 방법을 알아봅니다. Cloud Manager은 GitHub, GitLab 및 Bitbucket 저장소와의 통합을 지원합니다.

>[!NOTE]
>
>이 기능은 [얼리 어답터 프로그램](/help/implementing/cloud-manager/release-notes/current.md#early-adoption)에만 사용할 수 있습니다.

## 외부 저장소 구성

Cloud Manager에서 외부 저장소를 구성하는 단계는 다음 세 단계로 구성됩니다.

1. 선택한 프로그램에 [외부 저장소를 추가](#add-external-repo)합니다.
1. 외부 저장소에 액세스 토큰을 제공합니다.
1. 개인 GitHub 저장소의 소유권을 확인합니다.


## 외부 저장소 추가 {#add-ext-repo}

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)에서 Cloud Manager에 로그인한 다음 적절한 조직을 선택합니다.

1. **[내 프로그램](/help/implementing/cloud-manager/navigation.md#my-programs)** 콘솔에서 외부 리포지토리를 연결할 프로그램을 선택합니다.

1. 사이드 메뉴의 **서비스**&#x200B;에서 ![폴더 아이콘](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Folder_18_N.svg) **저장소**&#x200B;를 선택합니다.

   ![저장소 페이지](/help/implementing/cloud-manager/managing-code/assets/repositories-tab.png)

1. **저장소** 페이지의 오른쪽 상단 모서리에서 **저장소 추가**&#x200B;를 클릭합니다.

1. **저장소 추가** 대화 상자에서 **개인 저장소**&#x200B;를 선택하여 외부 Git 저장소를 프로그램에 연결합니다.

   ![자체 저장소 추가](/help/implementing/cloud-manager/managing-code/assets/repositories-private-repo-type.png)

1. 각 필드에 저장소에 대한 다음 세부 정보를 입력합니다.

   | 필드 | 설명 |
   | --- | --- |
   | **저장소 이름** | 필수. 새 저장소의 표현식 이름입니다. |
   | **저장소 URL** | 필수. 저장소의 URL입니다.<br><br> GitHub 호스팅 리포지토리를 사용하는 경우 경로는 `.git`에서 끝나야 합니다.<br>예: *`https://github.com/org-name/repo-name.git`*(URL 경로는 일러스트레이션 목적으로만 사용)<br><br>외부 리포지토리를 사용하는 경우 다음 URL 경로 형식을 사용해야 합니다.<br>`https://git-vendor-name.com/org-name/repo-name.git`<br> 또는<br>`https://self-hosted-domain/org-name/repo-name.git`<br>Git 공급업체와 일치해야 합니다. |
   | S **저장소 유형 선택** | 필수. 사용 중인 저장소 유형을 선택하십시오. **GitHub**, **GitLab** 또는 **BitBucket**. 위의 저장소 URL 경로에 GitLab 또는 Bitbucket과 같은 Git 공급업체 이름이 포함되어 있는 경우 저장소 유형이 이미 사전 선택되어 있습니다. |
   | **설명** | 선택 사항입니다. 저장소에 대한 자세한 설명입니다. |

1. 저장소를 추가하려면 **저장**&#x200B;을(를) 선택하십시오.

1. **개인 저장소 소유권 확인** 대화 상자에서 외부 저장소에 액세스할 수 있도록 외부 저장소의 소유권을 확인하는 액세스 토큰을 제공하십시오.

   ![저장소에 대한 기존 액세스 토큰 선택](/help/implementing/cloud-manager/managing-code/assets/repositories-exisiting-access-token.png)
   *BitBucket 저장소에 대한 기존 액세스 토큰을 선택하는 중입니다.*

   | 토큰 유형 | 설명 |
   | --- | --- |
   | **기존 액세스 토큰 사용** | 조직에 대한 저장소 액세스 토큰을 이미 제공하고 여러 저장소에 대한 액세스 권한이 있는 경우 기존 토큰을 선택할 수 있습니다. **토큰 이름** 드롭다운 목록을 사용하여 저장소에 적용할 토큰을 선택하십시오. 그렇지 않으면 새 액세스 토큰을 추가합니다. |
   | **새 액세스 토큰 추가** | **저장소 유형: GitHub**<br>· **토큰 이름** 텍스트 필드에 만들고 있는 액세스 토큰의 이름을 입력하십시오.<br>· [GitHub 설명서](https://docs.github.com/en/enterprise-server@3.14/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens)의 지침에 따라 개인 액세스 토큰을 만듭니다.<br>· 권한 필요:<br>  · `Read access to metadata`.<br>  · `Read and write access to code and pull requests`.<br>· **액세스 토큰** 필드에 방금 만든 토큰을 붙여 넣습니다. |
   |  | **저장소 유형: GitLab**<br>· **토큰 이름** 텍스트 필드에 만들고 있는 액세스 토큰의 이름을 입력합니다.<br>· [GitLab 설명서](https://docs.gitlab.com/ee/user/profile/personal_access_tokens.html)의 지침에 따라 개인 액세스 토큰을 만듭니다.<br>· 권한 필요:<br>  · `api`<br>  · `read_api`<br>  · `read_repository`<br>  · `write_repository`<br>· **액세스 토큰** 필드에 방금 만든 토큰을 붙여 넣습니다. |
   |  | **저장소 유형: Bitbucket**<br>· **토큰 이름** 텍스트 필드에 만들고 있는 액세스 토큰의 이름을 입력하십시오.<br>· [Bitbucket 설명서](https://support.atlassian.com/bitbucket-cloud/docs/create-a-repository-access-token/)를 사용하여 저장소 액세스 토큰을 만듭니다.<br>· 권한 필요:<br>  · `Read and write access to code and pull requests`. |

   >[!NOTE]
   >
   >**새 액세스 토큰 추가** 기능은 현재 얼리어답터 단계에 있습니다. 추가적인 기능을 계획하고 있습니다. 따라서 액세스 토큰에 필요한 권한이 변경될 수 있습니다. 추가로, 토큰들을 관리하기 위한 사용자 인터페이스는 토큰 만료 일자들과 같은 특징들을 잠재적으로 포함하여 업데이트될 수 있다. 그리고 저장소에 연결된 토큰이 계속 유효한지 자동으로 확인합니다.

1. **유효성 검사**&#x200B;를 클릭합니다.

유효성 검사 후 외부 저장소는 파이프라인을 사용하고 연결할 준비가 되었습니다.

## 검증된 외부 저장소를 파이프라인에 연결 {#validate-ext-repo}

1. 파이프라인 추가 또는 편집:
   * [프로덕션 파이프라인 추가](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md)
   * [비프로덕션 파이프라인 추가](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md)
   * [파이프라인 편집](/help/implementing/cloud-manager/configuring-pipelines/managing-pipelines.md#editing-pipelines)

   ![파이프라인의 소스 코드 저장소 및 Git 분기](/help/implementing/cloud-manager/managing-code/assets/pipeline-repo-gitbranch.png)
   *선택한 저장소 및 Git 분기가 있는 비프로덕션 파이프라인 추가 대화 상자,*

1. 파이프라인을 추가하거나 편집할 때 새 또는 기존 파이프라인에 대한 **Source 코드** 위치를 지정하려면 **저장소** 드롭다운 목록에서 사용할 외부 저장소를 선택합니다.

1. **Git 분기** 드롭다운 목록에서 분기를 파이프라인의 소스로 선택합니다.

1. **저장**&#x200B;을 클릭합니다.


>[!TIP]
>
>Cloud Manager의 저장소 관리에 대한 자세한 내용은 [Cloud Manager 저장소](/help/implementing/cloud-manager/managing-code/managing-repositories.md)를 참조하십시오.


## 제한 사항

* 외부 저장소를 구성 파이프라인에 연결할 수 없습니다.
* 외부 저장소(GitHub 호스팅 저장소 제외) 및 **배포 트리거** 옵션 [!UICONTROL **Git 변경 시**] 트리거를 사용하는 파이프라인은 자동으로 시작되지 않습니다. 수동으로 시작해야 합니다.




