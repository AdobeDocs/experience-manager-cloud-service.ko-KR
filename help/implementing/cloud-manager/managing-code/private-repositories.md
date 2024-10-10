---
title: Cloud Manager에 개인 GitHub 저장소 추가
description: 개인 GitHub 저장소에서 작동하도록 Cloud Manager를 설정하는 방법에 대해 알아봅니다.
exl-id: 5232bbf5-17a5-4567-add7-cffde531abda
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 2fa4abca9823bbc62900023d637429f3fbfd894d
workflow-type: tm+mt
source-wordcount: '930'
ht-degree: 42%

---

# Cloud Manager에 개인 GitHub 저장소 추가 {#private-repositories}

Cloud Manager을 설정하여 개인 GitHub 리포지토리와 통합하면 Cloud Manager을 사용하여 GitHub 내에서 직접 코드를 확인할 수 있습니다. 이 구성은 코드를 Adobe 저장소와 정기적으로 동기화하기 위한 요구 사항을 제거합니다.

<!-- CONSIDER ADDING MORE DETAIL... THE WHY. Some key points about this capability include the following:

* **Direct Integration**: With this setup, you can directly link your private GitHub repositories to Cloud Manager, allowing for seamless code validation, deployment, and CI/CD (Continuous Integration/Continuous Deployment) pipelines without needing to maintain a separate sync process with Adobe's default Git repository.

* **Customization and Autonomy**: Companies often prefer managing their own source code repositories for security, control, and integration purposes. "Build your own GitHub" allows organizations to maintain their internal development processes while leveraging the full functionality of Cloud Manager for building, testing, and deploying AEM (Adobe Experience Manager) applications.

* **Simplified Workflow**: It reduces the overhead of synchronizing code between multiple repositories by allowing Cloud Manager to access the organization's private repository directly, making the development cycle faster and more efficient.

* **CI/CD Pipelines**: Teams can still benefit from Adobe Cloud Manager's automated build, test, and deployment processes, as the integration allows the CI/CD pipelines to pull code from the organization's own GitHub repository.

In essence, a "Build your own GitHub" in Adobe Cloud Manager empowers teams to manage their own GitHub repositories while still using the robust deployment and validation capabilities of Cloud Manager. -->

>[!NOTE]
>
>이 기능은 공개 GitHub 전용입니다. 자체 호스팅 GitHub에 대해서는 지원되지 않습니다.

## 구성 {#configuration}

Cloud Manager에서 개인 GitHub 저장소 구성은 다음 두 단계로 구성됩니다.

1. 선택한 프로그램에 [개인 GitHub 저장소를 추가](#add-repo)합니다.
1. 그런 다음 [개인 GitHub 리포지토리의 소유권을 확인](#validate-ownership)합니다.

### 프로그램에 개인 GitHub 저장소 추가 {#add-repo}

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)에서 Cloud Manager에 로그인한 다음 적절한 조직을 선택합니다.

1. **[내 프로그램](/help/implementing/cloud-manager/navigation.md#my-programs)** 콘솔에서 개인 Git 저장소를 연결할 프로그램을 선택합니다.

1. 측면 메뉴의 **서비스**&#x200B;에서 ![폴더 아이콘](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Folder_18_N.svg) **저장소**&#x200B;를 선택합니다.

   ![저장소 페이지](/help/implementing/cloud-manager/managing-code/assets/repositories-tab.png)

1. **저장소** 페이지의 오른쪽 상단 근처에서 **저장소 추가**&#x200B;를 클릭합니다.

1. **저장소 추가** 대화 상자에서 **비공개 저장소**&#x200B;를 저장소 유형으로 선택합니다.

   ![자체 저장소 추가](/help/implementing/cloud-manager/assets/repos/add-own-github.png)

1. 각 필드에 저장소에 대한 다음 세부 정보를 입력합니다.

   | 필드 | 설명 |
   | --- | --- |
   | 저장소 이름 | 새로운 저장소의 표현적인 이름. |
   | 저장소 URL | `.git`(으)로 끝나야 하는 개인 저장소의 URL.<br>예: *`https://github.com/org-name/repo-name.git`* (URL 경로는 설명 목적으로만 사용됨) |
   | 설명(선택 사항) | 저장소에 대한 자세한 설명. |

1. **저장**을 선택합니다.
이제 [개인 저장소의 소유권을 확인](#validate-ownership)할 수 있습니다.

>[!TIP]
>
>Cloud Manager의 저장소 관리에 대한 자세한 내용은 [Cloud Manager 저장소](/help/implementing/cloud-manager/managing-code/managing-repositories.md)를 참조하십시오.



### 개인 GitHub 저장소의 소유권 확인 {#validate-ownership}

이제 Cloud Manager는 GitHub 저장소에 대해 알게 되었지만, 여전히 이에 대한 액세스가 필요합니다. 액세스 권한을 부여하려면 Adobe GitHub 앱을 설치하고 지정된 저장소를 소유하고 있는지 확인해야 합니다.

**개인 GitHub 저장소의 소유권을 확인하려면:**

1. 고유한 저장소를 추가한 후 **개인 저장소 소유권 확인** 대화 상자의 나머지 단계를 따릅니다.

   ![비공개 저장소 소유권 유효성 검사](/help/implementing/cloud-manager/assets/repos/private-repo-validate.png)

   |  | 설명 |
   | --- | --- |
   | **1단계: GitHub 앱** | Cloud Manager은 GitHub 앱을 사용하여 개인 리포지토리와 안전하게 상호 작용합니다.<br>· GitHub 조직의 소유자는 `https://github.com/apps/cloud-manager-for-aem`에 있는 앱을 설치하고 저장소에 대한 액세스 권한을 부여해야 합니다.<br>· 설치 및 액세스 권한 부여에 대한 자세한 내용은 GitHub 설명서를 참조하십시오. |
   | **2단계: 암호 파일** | 보안을 강화하려면 저장소의 기본 분기에 비밀 파일을 만들어야 합니다.<br>· **생성**&#x200B;을 클릭한 다음 **확인**&#x200B;을 클릭합니다. Cloud Manager은 **암호 파일 내용** 텍스트 필드에 개인 파일의 내용을 생성합니다.<br>· 해당 필드의 내용을 복사하려면 ![복사 아이콘](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Copy_18_N.svg)을 클릭합니다. 시크릿 파일의 콘텐츠는 한 번만 표시됩니다. 이 대화 상자를 닫기 전에 콘텐츠를 복사하지 않으면 암호를 다시 생성합니다. |

1. GitHub 리포지토리의 기본 분기에 라는 새 파일을 만듭니다.

   `.well-known/adobe/cloud-manager-challenge`

1. 방금 만든 새 파일에 암호 파일 내용을 붙여넣고 저장합니다.

   앱이 설치되고 저장소에 비밀 파일이 있으면 단계를 계속합니다.

1. **개인 저장소 소유권 확인** 대화 상자에서 **확인**&#x200B;을 클릭합니다.

앱을 설치하고 암호 파일을 순서에 관계없이 만들 수 있습니다. 그러나 유효성을 검사하려면 두 단계를 모두 완료해야 합니다.

유효성 검사 전까지 저장소는 빨간색 아이콘으로 나열되며, 이는 아직 검증되지 않았고 사용할 수 없음을 나타냅니다.

![검증되지 않은 저장소](/help/implementing/cloud-manager/assets/repos/unvalidated-repo.png)

**저장소** 페이지의 표에 있는 **유형** 열은 Adobe이 제공한 저장소(**Adobe**)와 고유한 개인 저장소(**GitHub**)를 식별합니다.

나중에 저장소로 돌아가서 유효성 검사를 완료해야 하는 경우 **저장소** 페이지에서 방금 추가한 GitHub 저장소를 나타내는 행의 ![추가 아이콘](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg)을 클릭합니다. 드롭다운 목록에서 **소유권 확인**&#x200B;을 선택합니다.



## Cloud Manager에서 개인 GitHub 저장소 사용 {#using}

Cloud Manager에서 GitHub 리포지토리의 유효성을 검사하면 통합이 완료됩니다. Cloud Manager에서 저장소를 사용할 수 있습니다.

**Cloud Manager로 비공개 저장소를 사용하려면:**

1. 가져오기 요청을 만들면 GitHub 검사가 자동으로 시작됩니다.

   ![GitHub 검사](/help/implementing/cloud-manager/assets/repos/github-checks.png)

1. 각 가져오기 요청에 대해 [전체 스택 코드 품질 파이프라인](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md)이 자동으로 생성됩니다. 이 파이프라인은 가져오기 요청이 업데이트될 때마다 시작됩니다.

1. GitHub 검사는 코드 품질 검사가 완료될 때까지 실행 중 상태로 유지됩니다. 그러면 코드 품질 결과가 GitHub 검사에 반영됩니다.

   ![GitHub 코드 품질 검사](/help/implementing/cloud-manager/assets/repos/github-code-quality.png)

끌어오기 요청이 병합되거나 닫히면 생성된 전체 스택 코드 품질 파이프라인이 자동으로 삭제됩니다.

>[!TIP]
>
>끌어오기 요청 확인이 실행될 때 GitHub를 통해 제공되는 정보에 대한 자세한 내용은 [GitHub 확인 주석](github-annotations.md)을 참조하십시오.

>[!TIP]
>
>비공개 저장소에 대한 각각의 가져오기 요청 유효성 검사를 위해 자동으로 생성되는 파이프라인 제어할 수 있습니다. 자세한 내용은 [비공개 저장소에 대한 GitHub 검사 구성](github-check-config.md)을 참조하십시오.



## 비공개 저장소를 파이프라인과 연결 {#pipelines}

유효성이 확인된 비공개 저장소는 [전체 스택 및 프론트엔드 파이프라인](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md)과 연결될 수 있습니다.



## 제한 사항 {#limitations}

Cloud Manager으로 비공개 저장소를 사용하는 경우 특정 제한 사항이 있습니다.

* 웹 계층 및 구성 파이프라인은 비공개 저장소에서 지원되지 않습니다.
* 프로덕션 전체 스택 파이프라인에서 비공개 저장소를 사용할 때 Git 태그가 생성 및 푸시되지 않습니다.
* GitHub 조직에서 GitHub Adobe 앱을 제거하면 모든 저장소에 대한 가져오기 요청 유효성 검사 기능이 제거됩니다.
* 비공개 저장소와 커밋 시 빌드 트리거를 사용하는 파이프라인은 새 커밋이 선택한 분기에 푸시될 때 자동으로 시작되지 않습니다.
* [아티팩트 재사용 기능](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/setting-up-project.md#build-artifact-reuse)은 비공개 저장소에는 적용되지 않습니다.
* Cloud Manager에서 GitHub 검사를 사용하여 가져오기 요청 유효성 검사를 일시 중지할 수 없습니다.
Cloud Manager에서 GitHub 리포지토리의 유효성을 검사하는 경우 Cloud Manager은 항상 해당 리포지토리에 대해 만들어진 가져오기 요청의 유효성을 검사합니다.
