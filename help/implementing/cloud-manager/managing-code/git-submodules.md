---
title: Git 하위 모듈 지원
description: Git 하위 모듈을 사용하여 빌드 시 Git 저장소에 있는 여러 분기의 콘텐츠를 병합할 수 있는 방법을 알아봅니다.
exl-id: fa5b0f49-4b87-4f39-ad50-7e62094d85f4
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 5d6d3374f2dd95728b2d3ed0cf6fab4092f73568
workflow-type: tm+mt
source-wordcount: '436'
ht-degree: 90%

---

# Adobe 저장소에 대한 Git 하위 모듈 지원 {#git-submodule-support}

git 하위 모듈을 사용하여 빌드 시 git 저장소에 있는 여러 분기의 콘텐츠를 병합할 수 있습니다.

Cloud Manager의 빌드 프로세스가 실행되면 파이프라인에 대해 구성된 저장소를 복제하고 구성된 분기를 체크아웃한 후 분기의 루트 디렉터리에 `.gitmodules` 파일이 있으면 명령이 실행됩니다.

다음 명령은 각 하위 모듈을 적절한 디렉터리로 체크아웃합니다.

```
$ git submodule update --init
```

이 기술은 [다중 소스 Git 저장소를 사용하여 작업](/help/implementing/cloud-manager/managing-code/working-with-multiple-source-git-repositories.md) 문서에 설명된 솔루션에 대한 잠재적인 대안으로서, git 하위 모듈 사용에 익숙하고 외부 병합 프로세스를 관리하고 싶지 않은 조직에 적합합니다.

예를 들어 각각 `main`이라는 단일 분기를 포함하는 3개의 저장소가 있다고 가정해 보겠습니다. 기본 저장소, 즉 파이프라인에 구성된 저장소에서 `main` 분기에는 다른 두 저장소에 포함된 프로젝트를 선언하는 `pom.xml` 파일이 있습니다.

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

git 하위 모듈에 대한 자세한 내용은 [Git 참조 설명서](https://git-scm.com/book/en/v2/Git-Tools-Submodules)를 참조하세요.

### 제한 사항 및 권장 사항 {#limitations-recommendations}

Adobe 관리 저장소와 함께 git 하위 모듈을 사용할 때는 다음 제한 사항에 유의하십시오.

* git URL은 이전 섹션에서 설명한 구문과 정확히 일치해야 합니다.
* 분기의 루트에 있는 하위 모듈만 지원됩니다.
* 보안상의 이유로, git URL에 자격 증명을 임베드하지 마십시오.
* 달리 필요한 경우가 아니면 약식 하위 모듈을 사용하는 것이 좋습니다.
   * 이렇게 하려면 각 하위 모듈에 대해 `git config -f .gitmodules submodule.<submodule path>.shallow true`를 실행합니다.
* git 하위 모듈 참조는 특정 git 커밋에 저장됩니다. 따라서 하위 모듈 저장소가 변경되면 참조된 커밋을 업데이트해야 합니다.
   * 예를 들어 `git submodule update --remote`를 사용합니다.

## 비공개 저장소에 대한 Git 하위 모듈 지원 {#private-repositories}

[비공개 저장소](private-repositories.md)를 사용할 때 git 하위 모듈에 대한 지원은 Adobe 저장소를 사용할 때와 대부분 동일합니다.

그러나 `pom.xml` 파일을 설정하고 `git submodule` 명령을 실행한 후에는 `.gitmodules` 파일을 Cloud Manager용 집계기 저장소의 루트 디렉터리에 추가하여 하위 모듈 설정을 감지해야 합니다.

![.gitmodules 파일](assets/gitmodules.png)

![집계기](assets/aggregator.png)

### 제한 사항 및 권장 사항 {#limitations-recommendations-private-repos}

비공개 저장소에 git 하위 모듈을 사용할 때는 다음 제한 사항에 유의하십시오.

* 하위 모듈의 git URL은 HTTPS 또는 SSH 형식일 수 있지만 github.com 저장소에 연결해야 합니다
   * Adobe 저장소 하위 모듈을 GitHub 집계기 저장소에 추가하거나 그 반대로 추가하는 것은 작동하지 않습니다.
* GitHub 하위 모듈은 Adobe GitHub 애플리케이션에 액세스할 수 있어야 합니다.
* [Adobe 관리 저장소의 git 하위 모듈 사용 시 제한 사항](#limitations-recommendations)도 적용됩니다.
