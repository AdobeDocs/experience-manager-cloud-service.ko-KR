---
title: Cloud Manager 저장소
description: Cloud Manager에서 Git 리포지토리를 생성, 보기 및 삭제하는 방법을 알아봅니다.
exl-id: 6e1cf636-78f5-4270-9a21-38b4d5e5a0b0
source-git-commit: 430179bf13c1fff077c515eed0676430e9e7f341
workflow-type: tm+mt
source-wordcount: '582'
ht-degree: 0%

---


# Cloud Manager 저장소 {#cloud-manager-repos}

Cloud Manager에서 Git 리포지토리를 생성, 보기 및 삭제하는 방법을 알아봅니다.

>[!NOTE]
>
>특정 회사 또는 IMS 조직의 모든 프로그램에 대해 리포지토리는 300개로 제한됩니다.

## 저장소 추가 및 관리 {#add-manage-repos}

다음 단계에 따라 Cloud Manager에서 저장소를 보고 관리합니다.

1. 에서 **프로그램 개요** 페이지를 클릭합니다. **저장소** 탭을 클릭하고 **저장소** 페이지.

1. 클릭 **저장소 추가** 마법사를 시작하려면 다음을 수행하십시오.

   ![저장소 추가 단추](/help/implementing/cloud-manager/assets/repos/create-repo2.png)

1. 원하는 이름과 설명을 입력하고 을 클릭합니다 **저장**.

   ![저장소 추가 대화 상자](/help/implementing/cloud-manager/assets/repos/repo-1.png)

마법사가 닫히면 새 저장소가 테이블에 표시됩니다.

테이블에서 리포지토리를 선택하고 줄임표 단추를 누른 다음 을 선택할 수 있습니다 **저장소 URL 복사**, **보기 및 업데이트**, 또는 **삭제**.

![저장소 옵션](/help/implementing/cloud-manager/assets/repos/create-repo3.png)

파이프라인을 추가하거나 편집할 때도 Cloud Manager에서 만든 저장소를 사용할 수 있습니다. 문서를 참조하십시오 [CI-CD 파이프라인](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md) 추가 정보

주어진 파이프라인에 대해 단일 기본 리포지토리 또는 분기가 있습니다. 사용 [git 하위 모듈 지원](#git-submodule-support)를 채울 때는 많은 보조 분기를 포함할 수 있습니다.

>[!NOTE]
>
>사용자에게 역할이 있어야 합니다. **배포 관리자** 또는 **비즈니스 소유자** 을 눌러 저장소를 추가할 수 있습니다.

## 저장소 삭제 {#delete-repo}

저장소를 삭제하면 다음 작업이 수행됩니다.

* 나중에 생성할 수 있는 새 저장소에 대해 삭제된 저장소 이름을 사용할 수 없도록 합니다.
   * 오류 메시지 `Repository name should be unique within organization.` 이 이러한 경우에 표시됩니다.
* 삭제된 저장소를 Cloud Manager에서 사용할 수 없으며 파이프라인에 연결할 수 없게 합니다.

Cloud Manager에서 저장소를 삭제하려면 다음을 수행합니다.

1. 에서 **프로그램 개요** 페이지를 클릭합니다. **저장소** 탭을 클릭하고 **저장소** 페이지.

1. 저장소를 선택하고 줄임표 버튼을 클릭하고 을 선택합니다 **삭제** 저장소를 삭제하려면

   ![저장소 삭제](/help/implementing/cloud-manager/assets/repos/delete-repo.png)

## Git 하위 모듈 지원 {#git-submodule-support}

Git 하위 모듈을 사용하여 빌드 시 Git 리포지토리에서 여러 분기의 콘텐츠를 병합할 수 있습니다.

Cloud Manager의 빌드 프로세스가 실행될 때 분기에 가 포함되어 있으면 파이프라인에 대해 구성된 리포지토리를 복제하고 구성된 분기를 체크 아웃한 후 `.gitmodules` 루트 디렉토리에 있는 파일에서 명령이 실행됩니다.

다음 명령은 각 하위 모듈을 적절한 디렉토리로 체크 아웃합니다.

```
$ git submodule update --init
```

이 기법은 문서에 설명된 솔루션에 대한 잠재적 대안입니다 [여러 소스 Git 리포지토리 작업](/help/implementing/cloud-manager/managing-code/working-with-multiple-source-git-repositories.md) git 하위 모듈 사용에 익숙하며 외부 병합 프로세스를 관리하지 않으려는 조직의 경우.

예를 들어 세 개의 리포지토리가 있으며, 각 리포지토리는 이름이 인 단일 분기를 포함합니다 `main`. 주 리포지토리에서, 즉 파이프라인에 구성된 저장소인 `main` 분기에는 `pom.xml` 다른 두 저장소에 포함된 프로젝트를 선언하는 파일입니다.

```xml
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="https://maven.apache.org/POM/4.0.0" xmlns:xsi="https://www.w3.org/2001/XMLSchema-instance"
    xsi:schemaLocation="https://maven.apache.org/POM/4.0.0 https://maven.apache.org/maven-v4_0_0.xsd">
    <modelVersion>4.0.0</modelVersion>
   
    <groupId>customer.group.id</groupId>
    <artifactId>customer-reactor</artifactId>
    <version>0.0.1-SNAPSHOT</version>
    <packaging>pom</packaging>
   
    <modules>
        <module>project-a</module>
        <module>project-b</module>
    </modules>
   
</project>
```

그런 다음 다른 두 저장소에 대한 하위 모듈을 추가합니다.

```shell
$ git submodule add -b main https://git.cloudmanager.adobe.com/ProgramName/projectA/ project-a
$ git submodule add -b main https://git.cloudmanager.adobe.com/ProgramName/projectB/ project-b
```

이 경우 `.gitmodules` 다음과 유사한 파일을 생성합니다.

```text
[submodule "project-a"]
    path = project-a
    url = https://git.cloudmanager.adobe.com/ProgramName/projectA/
    branch = main
[submodule "project-b"]
    path = project-b
    url = https://git.cloudmanager.adobe.com/ProgramName/projectB/
    branch = main
```

Git 하위 모듈에 대한 자세한 내용은 [Git 참조 설명서.](https://git-scm.com/book/en/v2/Git-Tools-Submodules)

### 제한 사항 및 권장 사항 {#limitations-recommendations}

Git 하위 모듈을 사용할 때는 다음 제한 사항을 알아 두십시오.

* Git URL은 이전 섹션에 설명된 구문에 정확히 포함되어야 합니다.
* 분기의 루트에 있는 하위 모듈만 지원됩니다.
* 보안상의 이유로 Git URL에 자격 증명을 포함하지 마십시오.
* 별도로 필요하지 않는 한 얕은 하위 모듈을 사용하는 것이 좋습니다.
   * 이렇게 하려면 를 실행합니다. `git config -f .gitmodules submodule.<submodule path>.shallow true` 각 하위 모듈용.
* Git 하위 모듈 참조는 특정 Git 커밋에 저장됩니다. 따라서 하위 모듈 리포지토리를 변경할 때 커밋 참조된 내용을 업데이트해야 합니다.
   * 예를 들어 `git submodule update --remote`
