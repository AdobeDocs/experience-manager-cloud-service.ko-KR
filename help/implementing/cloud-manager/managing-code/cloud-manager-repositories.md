---
title: Cloud Manager 저장소
description: Cloud Manager에서 git 저장소를 생성, 확인 및 삭제하는 방법을 알아봅니다.
exl-id: 6e1cf636-78f5-4270-9a21-38b4d5e5a0b0
source-git-commit: 1994b90e3876f03efa571a9ce65b9fb8b3c90ec4
workflow-type: tm+mt
source-wordcount: '575'
ht-degree: 92%

---


# Cloud Manager 저장소 {#cloud-manager-repos}

Cloud Manager에서 git 저장소를 생성, 확인 및 삭제하는 방법을 알아봅니다.

>[!NOTE]
>
>특정 회사 또는 IMS 조직의 모든 프로그램에서 300개의 저장소로 제한됩니다.

## 저장소 추가 및 관리 {#add-manage-repos}

다음 단계에 따라 Cloud Manager에서 저장소를 보고 관리하십시오.

1. **프로그램 개요** 페이지에서 **저장소** 탭을 클릭하고 **저장소** 페이지로 이동합니다.

1. **저장소 추가**&#x200B;를 클릭하여 마법사를 시작합니다.

   ![저장소 추가 버튼](/help/implementing/cloud-manager/assets/repos/create-repo2.png)

1. 요청한 대로 이름과 설명을 입력하고 **저장**&#x200B;을 클릭합니다.

   ![저장소 추가 대화 상자](/help/implementing/cloud-manager/assets/repos/repo-1.png)

마법사가 닫히면 새 저장소가 표에 표시됩니다.

표에서 저장소를 선택하고 줄임표 버튼을 클릭한 다음 **저장소 URL 복사**, **보기 및 업데이트** 또는 **삭제**&#x200B;를 선택할 수 있습니다.

![저장소 옵션](/help/implementing/cloud-manager/assets/repos/create-repo3.png)

Cloud Manager에서 만들어진 저장소는 파이프라인을 추가하거나 편집할 때도 선택할 수 있습니다. 다음을 참조하십시오 [CI-CD 파이프라인](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md) 자세히 알아보십시오.

지정된 파이프라인에 대해 단일 주 저장소 또는 분기가 있습니다. [git 하위 모듈 지원](#git-submodule-support)을 통해 빌드 시 많은 보조 분기를 포함할 수 있습니다.

>[!NOTE]
>
>저장소를 추가하려면 사용자에게 **배포 관리자** 또는 **비즈니스 소유자** 역할이 있어야 합니다.

## 저장소 삭제 {#delete-repo}

저장소를 삭제하면 다음 결과가 발생합니다.

* 나중에 새 저장소를 만들 때 삭제된 저장소 이름을 사용할 수 없습니다.
   * 이 경우 `Repository name should be unique within organization.` 오류 메시지가 표시됩니다.
* 삭제된 저장소를 Cloud Manager에서 사용하거나 파이프라인에 연결할 수 없습니다.

Cloud Manager에서 저장소를 삭제하려면 다음을 따르십시오.

1. **프로그램 개요** 페이지에서 **저장소** 탭을 클릭하고 **저장소** 페이지로 이동합니다.

1. 저장소를 선택하고 줄임표 버튼을 클릭한 다음 **삭제**&#x200B;를 선택하여 저장소를 삭제합니다.

   ![저장소 삭제](/help/implementing/cloud-manager/assets/repos/delete-repo.png)

## git 하위 모듈 지원 {#git-submodule-support}

git 하위 모듈을 사용하여 빌드 시 git 저장소에 있는 여러 분기의 콘텐츠를 병합할 수 있습니다.

Cloud Manager의 빌드 프로세스가 실행되면 파이프라인에 대해 구성된 저장소를 복제하고 구성된 분기를 체크아웃한 후 분기의 루트 디렉터리에 `.gitmodules` 파일이 있으면 명령이 실행됩니다.

다음 명령은 각 하위 모듈을 적절한 디렉터리로 체크아웃합니다.

```
$ git submodule update --init
```

이 기술은 [다중 소스 Git 저장소를 사용하여 작업](/help/implementing/cloud-manager/managing-code/working-with-multiple-source-git-repositories.md) 문서에 설명된 솔루션에 대한 잠재적인 대안으로서, git 하위 모듈 사용에 익숙하고 외부 병합 프로세스를 관리하고 싶지 않은 조직에 적합합니다.

예를 들어 각각 `main`이라는 단일 분기를 포함하는 3개의 저장소가 있다고 가정해 보겠습니다. 기본 저장소, 즉 파이프라인에 구성된 저장소에서 `main` 지점에 다음 항목이 있음: `pom.xml` 다른 두 저장소에 포함된 프로젝트를 선언하는 파일입니다.

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

그러면 다음과 유사한 `.gitmodules` 파일이 생성됩니다.

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

git 하위 모듈에 대한 자세한 내용은 [git 참조 설명서](https://git-scm.com/book/en/v2/Git-Tools-Submodules)에서 확인할 수 있습니다.

### 제한 사항 및 권장 사항 {#limitations-recommendations}

git 하위 모듈을 사용할 때는 다음 제한 사항에 유의하십시오.

* git URL은 이전 섹션에서 설명한 구문과 정확히 일치해야 합니다.
* 분기의 루트에 있는 하위 모듈만 지원됩니다.
* 보안상의 이유로, git URL에 자격 증명을 임베드하지 마십시오.
* 달리 필요한 경우가 아니면 약식 하위 모듈을 사용하는 것이 좋습니다.
   * 이렇게 하려면 각 하위 모듈에 대해 `git config -f .gitmodules submodule.<submodule path>.shallow true`를 실행합니다.
* git 하위 모듈 참조는 특정 git 커밋에 저장됩니다. 결과적으로 하위 모듈 저장소가 변경되면 참조된 커밋을 업데이트해야 합니다.
   * 예를 들어 `git submodule update --remote`를 사용합니다.
