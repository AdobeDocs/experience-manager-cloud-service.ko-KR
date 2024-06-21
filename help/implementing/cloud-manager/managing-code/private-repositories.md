---
title: Cloud Manager에서 비공개 저장소 추가
description: 개인 GitHub 저장소에서 작동하도록 Cloud Manager를 설정하는 방법에 대해 알아봅니다.
exl-id: 5232bbf5-17a5-4567-add7-cffde531abda
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: f9ba9fefc61876a60567a40000ed6303740032e1
workflow-type: tm+mt
source-wordcount: '836'
ht-degree: 77%

---

# Cloud Manager에서 비공개 저장소 추가 {#private-repositories}

개인 GitHub 저장소와 작동하도록 Cloud Manager를 구성하면 Cloud Manager를 통해 GitHub 저장소 내에서 직접 코드를 검증할 수 있으므로 코드를 Adobe 저장소와 지속적으로 동기화할 필요가 없습니다.

>[!NOTE]
>
>이 기능은 공개 GitHub 전용입니다. 자체 호스팅 GitHub에 대해서는 지원되지 않습니다.

## 구성 {#configuration}

구성은 두 가지 기본 단계로 구성됩니다.

1. [저장소 추가](#add-repo)
1. [비공개 저장소 소유권 유효성 검사](#validate-ownership)

### 저장소 추가 {#add-repo}

1. Cloud Manager의 **프로그램 개요** 페이지에서 **저장소** 탭을으로 전환합니다. **저장소** 페이지 및 클릭 **저장소 추가**.

1. **저장소 추가** 대화 상자에서 **비공개 저장소**&#x200B;를 저장소 유형으로 선택합니다.

1. 저장소의 세부 정보 제공

   * **저장소 이름** - 표현적인 이름
   * **저장소 URL** - `.git`으로 끝나는 저장소 URL
   * **설명**(옵션) - 필요에 따라 저장소에 대한 자세한 설명

   ![자체 저장소 추가](/help/implementing/cloud-manager/assets/repos/add-own-github.png)

1. **저장**&#x200B;을 선택합니다.

>[!TIP]
>
>Cloud Manager에서 저장소 관리에 대한 자세한 내용은 [Cloud Manager 저장소](/help/implementing/cloud-manager/managing-code/managing-repositories.md).

### 비공개 저장소 소유권 유효성 검사 {#validate-ownership}

이제 Cloud Manager는 GitHub 저장소에 대해 알게 되었지만, 여전히 이에 대한 액세스가 필요합니다. 액세스 권한을 부여하려면 Adobe GitHub 앱을 설치하고 지정된 저장소를 소유하고 있는지 확인해야 합니다.

1. 고유한 저장소를 추가한 후 **개인 저장소 소유권 확인** 대화 상자가 열립니다.

   ![비공개 저장소 소유권 유효성 검사](/help/implementing/cloud-manager/assets/repos/private-repo-validate.png)

1. Cloud Manager는 GitHub 앱을 사용하여 저장소와 안전하게 상호 작용합니다.
   * GitHub 조직의 소유자는 `https://github.com/apps/cloud-manager-for-aem`에 있는 앱을 설치하고 저장소에 대한 액세스 권한을 부여해야 합니다.
   * 이 작업을 수행하는 방법에 대한 자세한 내용은 GitHub 설명서 를 참조하십시오.

1. 보안 강화를 위해 저장소의 기본 분기에 시크릿 파일을 만들어야 합니다. 선택 **생성**.

1. **확인**&#x200B;을 탭하거나 클릭하여 시크릿 파일이 생성되었는지 확인합니다.

   ![비밀 생성 확인](/help/implementing/cloud-manager/assets/repos/confirm-generation.png)

1. **비공개 저장소 소유권 유효성 검사** 창으로 돌아가면 Cloud Manager가 **시크릿 파일 콘텐츠** 필드에 비공개 파일 콘텐츠를 생성했습니다. 해당 필드의 콘텐츠를 복사합니다.

   * 시크릿 파일의 콘텐츠는 한 번만 표시됩니다. 이 창을 닫기 전에 콘텐츠를 복사하지 않으면 암호를 다시 생성합니다.

   ![시크릿 파일 콘텐츠 복사](/help/implementing/cloud-manager/assets/repos/new-secret.png)

1. `.well-known/adobe/cloud-manager-challenge`라는 GitHub 저장소의 기본 분기에 새 파일을 만들고 시크릿 파일 콘텐츠를 해당 파일에 붙여넣어 저장합니다.

1. 앱이 설치되고 저장소에 비밀 파일이 있으면 다음을 선택할 수 있습니다. **유효성 검사** 다음에서 **개인 저장소 소유권 확인** 대화 상자.

앱을 설치하고 시크릿 파일을 순서에 관계없이 만들 수 있습니다. 그러나 유효성을 검사하려면 두 단계를 모두 완료해야 합니다.

유효성 검사 전까지 저장소는 빨간색 아이콘으로 표시되며 이는 아직 유효성이 검사되지 않았으며 아직 사용할 수 없음을 나타냅니다.

![검증되지 않은 저장소](/help/implementing/cloud-manager/assets/repos/unvalidated-repo.png)

다음 **유형** 열은 Adobe 제공 저장소를 쉽게 식별합니다(**Adobe**) 및 고유한 GitHub 저장소(**GitHub**).

나중에 저장소로 돌아가 검증을 완료해야 하는 경우 **저장소** 페이지에서 방금 추가한 GitHub 저장소를 나타내는 행의 줄임표 버튼을 선택하고 을(를) 선택합니다 **소유권 유효성 검사** 드롭다운 메뉴에서 을(를) 선택합니다.

## Cloud Manager로 비공개 저장소 사용 {#using}

Cloud Manager에서 GitHub 저장소의 유효성을 검사하면 통합이 완료되고 Cloud Manager에서 저장소를 사용할 수 있습니다.

1. 가져오기 요청을 만들면 GitHub 검사가 자동으로 시작됩니다.

   ![GitHub 검사](/help/implementing/cloud-manager/assets/repos/github-checks.png)

1. 각 가져오기 요청에 대해 [전체 스택 코드 품질 파이프라인](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md)이 자동으로 생성됩니다. 이 파이프라인은 가져오기 요청이 업데이트될 때마다 시작됩니다.

1. GitHub 검사는 코드 품질 검사가 완료될 때까지 실행 상태로 유지됩니다. 그러면 코드 품질 결과가 GitHub 검사에 반영됩니다.

   ![GitHub 코드 품질 검사](/help/implementing/cloud-manager/assets/repos/github-code-quality.png)

가져오기 요청이 닫히거나 병합되면 생성된 전체 스택 코드 품질 파이프라인이 자동으로 삭제됩니다.

>[!TIP]
>
>가져오기 요청 검사가 실행될 때 GitHub를 통해 제공되는 정보에 대한 자세한 내용은 [GitHub 검사 주석](github-annotations.md) 문서를 참조하십시오.

>[!TIP]
>
>비공개 저장소에 대한 각각의 가져오기 요청 유효성 검사를 위해 자동으로 생성되는 파이프라인 제어할 수 있습니다. 자세한 내용은 [비공개 저장소에 대한 GitHub 검사 구성](github-check-config.md) 문서를 참조하십시오.

## 비공개 저장소를 파이프라인과 연결 {#pipelines}

유효성이 확인된 비공개 저장소는 [전체 스택 및 프론트엔드 파이프라인](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md)과 연결될 수 있습니다.

>[!NOTE]
>
>웹 계층 및 구성 파이프라인은 비공개 저장소에서 지원되지 않습니다.

## 제한 사항 {#limitations}

Cloud Manager으로 비공개 저장소를 사용하는 경우 특정 제한 사항이 있습니다.

* Cloud Manager의 GitHub 검사를 사용하여 가져오기 요청 유효성 검사를 일시 중지할 수 없습니다.
   * GitHub 저장소가 Cloud Manager에서 검증되면 Cloud Manager는 항상 해당 저장소에 대해 생성된 가져오기 요청의 유효성 검사를 시도합니다.
* Adobe GitHub 애플리케이션이 GitHb 조직에서 제거되면 모든 저장소에 대한 가져오기 요청 유효성 검사 기능이 제거됩니다.
* 웹 계층 및 구성 파이프라인은 비공개 저장소에서 지원되지 않습니다.
* 프로덕션 전체 스택 파이프라인에서 비공개 저장소를 사용할 때 git 태그가 생성 및 푸시되지 않습니다.
* 비공개 저장소와 커밋 시 빌드 트리거를 사용하는 파이프라인은 새 커밋이 선택한 분기에 푸시될 때 자동으로 시작되지 않습니다.
* [아티팩트 재사용 기능](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/setting-up-project.md#build-artifact-reuse)은 비공개 저장소에는 적용되지 않습니다.
