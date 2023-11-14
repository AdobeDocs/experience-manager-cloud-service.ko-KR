---
title: Cloud Manager에서 자체 GitHub 저장소 작업
description: GitHub 저장소를 사용하여 작동하도록 Cloud Manager를 설정하는 방법에 대해 알아봅니다.
feature: Release Information
source-git-commit: 8d689ea08ab7caf9cb0fa84df23d7e0fd906f379
workflow-type: tm+mt
source-wordcount: '753'
ht-degree: 2%

---


# Cloud Manager에서 자체 GitHub 저장소 작업 {#byo-github}

자체 GitHub 리포지토리와 작동하도록 Cloud Manager를 구성하면 Cloud Manager를 통해 GitHub 리포지토리 내에서 직접 코드를 확인할 수 있으므로 코드를 Adobe 리포지토리와 일관되게 동기화할 필요가 없습니다.

>[!NOTE]
>
>이 기능은 [얼리 어답터 프로그램](/help/implementing/cloud-manager/release-notes/current.md#early-adoption)에만 사용할 수 있습니다.

## 구성 {#configuration}

구성은 다음 두 가지 주요 단계로 구성됩니다.

1. [저장소 추가](#add-repo)
1. [개인 저장소 소유권 유효성 검사](#validate-ownership)

### 저장소 추가 {#add-repo}

1. Cloud Manager의 **프로그램 개요** 페이지, 탭 또는 클릭 **저장소** 탭을으로 전환합니다. **저장소** 페이지 및 클릭 **저장소 추가**.

1. 다음에서 **저장소 추가** 대화 상자, 선택 **개인 저장소** 를 저장소 유형으로 사용하십시오.

1. 저장소 세부 정보 제공

   * **저장소 이름** - 표현식 이름
   * **저장소 URL** - 다음으로 끝나야 하는 저장소의 URL `.git`
   * **설명** (선택 사항) - 필요한 경우 저장소에 대한 자세한 설명

   ![자신의 저장소 추가](/help/implementing/cloud-manager/assets/repos/add-own-github.png)

1. **저장**&#x200B;을 탭하거나 클릭합니다.

>[!TIP]
>
>Cloud Manager에서 저장소 관리에 대한 자세한 내용은 문서를 참조하십시오. [Cloud Manager 저장소.](/help/implementing/cloud-manager/managing-code/cloud-manager-repositories.md)

### 개인 저장소 소유권 확인 {#validate-ownership}

이제 Cloud Manager가 GitHub 저장소에 대해 알고 있지만 여전히 액세스할 필요가 있습니다. 액세스 권한을 부여하려면 Adobe GitHub 앱을 설치하고 지정된 리포지토리가 있는지 확인해야 합니다.

1. 고유한 저장소를 추가한 후 **개인 저장소 소유권 확인** 대화 상자가 열립니다.

   ![개인 저장소 소유권 확인](/help/implementing/cloud-manager/assets/repos/private-repo-validate.png)

1. Cloud Manager는 GitHub 앱을 사용하여 저장소와 안전하게 상호 작용합니다.
   * GitHub 조직의 소유자는 다음 위치에 있는 앱을 설치해야 합니다. `https://github.com/apps/cloud-manager-for-aem-stage` 저장소에 대한 액세스 권한을 부여합니다.
   * 자세한 내용은 GitHub 설명서 를 참조하십시오.

1. 보안을 강화하려면 저장소의 기본 분기에 비밀 파일을 만들어야 합니다. 탭 또는 클릭 **생성**.

1. 탭하거나 클릭하여 비밀 파일 생성 확인 **확인**.

   ![암호 생성 확인](/help/implementing/cloud-manager/assets/repos/confirm-generation.png)

1. 뒤로 이동 **개인 저장소 소유권 확인** 창, Cloud Manager는에서 개인 파일의 컨텐츠를 생성했습니다. **암호 파일 콘텐츠** 필드. 해당 필드에서 콘텐츠를 복사합니다.

   * 비밀 파일의 내용은 한 번만 표시됩니다. 이 창을 닫기 전에 콘텐츠를 복사하지 않으면 암호를 다시 생성해야 합니다.

   ![암호 파일 콘텐츠 복사](/help/implementing/cloud-manager/assets/repos/new-secret.png)

1. GitHub 저장소의 기본 분기에 (이)라는 이름의 새 파일 만들기 `.well-known/adobe/cloud-manager-challenge` 그리고 비밀 파일 내용을 해당 파일에 붙여 넣고 저장합니다.

1. 앱이 설치되고 저장소에 비밀 파일이 있으면 탭하거나 클릭할 수 있습니다. **유효성 검사** 다음에서 **개인 저장소 소유권 확인** 대화 상자.

앱은 설치할 수 있으며 비밀 파일은 순서에 관계없이 만들 수 있습니다. 그러나 두 단계를 모두 완료해야 유효성을 검사할 수 있습니다.

유효성 검사 전까지 저장소는 아직 확인되지 않았으며 아직 사용할 수 없음을 나타내는 빨간색 아이콘으로 나열됩니다.

![확인되지 않은 저장소](/help/implementing/cloud-manager/assets/repos/unvalidated-repo.png)

다음 사항에 주의하십시오. **유형** 열은 Adobe 제공 저장소를 쉽게 식별합니다(**Adobe**) 및 고유한 GitHub 저장소(**GitHub**).

유효성 검사를 완료하기 위해 나중에 저장소로 돌아가야 하는 경우 **저장소** 방금 추가한 GitHub 저장소를 나타내는 행에서 페이지, 탭하거나 줄임표 버튼 클릭 및 선택 **소유권 유효성 검사** 드롭다운 메뉴에서 을(를) 선택합니다.

## Cloud Manager와 함께 고유한 GitHub 저장소 사용 {#using}

Cloud Manager에서 GitHub 저장소의 유효성을 검사한 후 통합이 완료되고 Cloud Manager에서 저장소를 사용할 수 있습니다.

1. 가져오기 요청을 만들면 GitHub 확인이 자동으로 시작됩니다.

   ![GitHub 확인](/help/implementing/cloud-manager/assets/repos/github-checks.png)

1. 각 가져오기 요청에 대해 [전체 스택 코드 품질 파이프라인](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md) 이(가) 자동으로 만들어집니다. 이 파이프라인은 각 가져오기 요청 업데이트 시 시작됩니다.

1. GitHub 검사는 코드 품질 검사가 완료될 때까지 실행 중 상태로 유지됩니다. 그런 다음 코드 품질 결과가 GitHub 확인에 전파됩니다.

   ![GitHub 코드 품질 검사](/help/implementing/cloud-manager/assets/repos/github-code-quality.png)

끌어오기 요청이 닫히거나 병합되면 생성된 전체 스택 코드 품질 파이프라인이 자동으로 삭제됩니다.

## 제한 사항 {#limitations}

Cloud Manager와 함께 고유한 GitHub 저장소를 사용할 때 다음 제한 사항을 염두에 두십시오.

* GitHub 리포지토리를 관리하는 파이프라인의 직접 리포지토리 소스로 사용할 수는 없습니다.
   * 이 기능은 계획된 기능입니다.
* cloud manager의 GitHub 검사를 사용하여 가져오기 요청 유효성 검사를 일시 중지할 수 없습니다.
   * GitHub 리포지토리의 유효성을 Cloud Manager에서 확인하면 Cloud Manager는 항상 해당 리포지토리에 대해 생성된 가져오기 요청의 유효성을 검사합니다.
GitHub 조직에서 GitHub Adobe 앱을 제거하면 모든 저장소에 대한 가져오기 요청 유효성 검사 기능이 제거됩니다.
