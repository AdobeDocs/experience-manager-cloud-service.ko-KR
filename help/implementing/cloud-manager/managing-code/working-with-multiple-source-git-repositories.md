---
title: 여러 저장소 사용
description: Cloud Manager로 작업할 때 여러 git 저장소를 관리하는 방법을 알아봅니다.
exl-id: 1b9cca36-c2d7-4f9e-9733-3f1f4f8b2c7a
source-git-commit: 5ea5c3f03642ae2f7471165d4d0ee33c2cc31b6b
workflow-type: ht
source-wordcount: '757'
ht-degree: 100%

---

# 여러 저장소 사용 {#working-with-multiple-source-git-repos}

Cloud Manager로 작업할 때 여러 git 저장소를 관리하는 방법을 알아봅니다.

## 고객이 관리하는 Git 저장소 동기화 {#syncing-customer-managed-git-repositories}

고객은 Cloud Manager의 git 저장소를 직접 사용하는 대신 [자체 git 저장소](integrating-with-git.md) 또는 여러 개의 git 저장소로 작업할 수 있습니다. 이러한 경우 Cloud Manager의 git 저장소를 항상 최신 상태로 유지할 수 있도록 자동 동기화 프로세스를 설정해야 합니다.

고객의 git 저장소를 호스팅하는 위치에 따라 GitHub 작업이나 Jenkins와 같은 지속적인 통합 솔루션을 사용하여 자동화를 설정할 수 있습니다. 자동화를 통해 고객이 소유한 저장소에 대한 모든 푸시를 자동으로 Cloud Manager의 git 저장소로 전달할 수 있습니다.

단일 고객 소유 git 저장소에 대한 이러한 자동화는 간단하지만 다중 저장소에 대해 이를 구성하려면 초기 설정이 필요합니다. 다중 git 저장소의 콘텐츠를 단일 Cloud Manager의 git 저장소 내에 있는 다른 디렉터리에 매핑해야 합니다.  Cloud Manager의 git 저장소를 루트 Maven `pom.xml`로 프로비저닝하고 모듈 섹션에 여러 하위 프로젝트를 나열해야 합니다.

다음은 두 고객 소유 git 저장소용 샘플 `pom.xml` 파일입니다.

* 첫 번째 프로젝트는 `project-a`라는 디렉터리에 저장됩니다.
* 두 번째 프로젝트는 `project-b`라는 디렉터리에 저장됩니다.

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

이러한 루트 `pom.xml`은 Cloud Manager의 git 저장소에 있는 분기로 푸시됩니다. 그런 다음 Cloud Manager의 git 저장소에 변경 사항을 자동으로 전달하도록 두 프로젝트를 설정해야 합니다.

가능한 해결 방법은 다음과 같습니다.

1. GitHub 작업을 프로젝트 A의 분기로 푸시하여 트리거할 수 있습니다.
1. 이 작업은 프로젝트 A와 Cloud Manager git 저장소를 체크아웃하고 프로젝트 A의 모든 콘텐츠를 Cloud Manager의 git 저장소에 있는 `project-a` 디렉터리로 복사합니다.
1. 그런 다음 작업은 변경 사항을 커밋-푸시합니다.

예를 들어 프로젝트 A의 기본 분기에 대한 변경 사항은 Cloud Manager의 git 저장소에 있는 기본 분기에 자동으로 푸시됩니다. 물론 프로젝트 A의 `dev`라는 분기에 대한 푸시가 Cloud Manager의 git 저장소에 있는 `development`라는 분기로 푸시되는 것처럼 분기 간에 매핑이 있을 수 있습니다. 프로젝트 B에도 유사한 단계가 필요합니다.

분기 전략 및 워크플로에 따라 다른 분기에 대해 동기화를 구성할 수 있습니다. 사용하는 git 저장소가 GitHub 작업과 유사한 개념을 제공하지 않는 경우 Jenkins(또는 이와 유사한)를 통한 통합도 가능합니다. 이 경우 웹후크는 작업을 수행하는 Jenkins 작업을 트리거합니다.

새 세 번째 소스 또는 저장소를 추가하려면 다음 단계를 수행합니다.

1. 해당 저장소에서 Cloud Manager의 git 저장소로 변경 사항을 푸시하는 새 GitHub 작업을 새 저장소에 추가합니다.
1. 이 작업을 한 번 이상 수행하여 프로젝트 코드가 Cloud Manager의 git 저장소에 있는지 확인합니다.
1. Cloud Manager git 저장소의 루트 Maven `pom.xml`에 새 디렉터리에 대한 참조를 추가합니다.

## 샘플 GitHub 작업 {#sample-github-action}

다음은 기본 분기로 푸시한 다음 Cloud Manager의 git 저장소의 하위 디렉터리로 푸시하여 트리거되는 샘플 GitHub 작업입니다. GitHub 작업에는 Cloud Manager의 git 저장소에 연결하고 푸시할 수 있도록 `MAIN_USER` 및 `MAIN_PASSWORD`라는 두 가지 비밀이 제공되어야 합니다.

```java
name: SYNC
env:
  # Username/email used to commit to Cloud Manager's Git repository
  USER_NAME: <NAME>
  USER_EMAIL: <EMAIL>
  # Directory within the Cloud Manager Git repository
  PROJECT_DIR: project-a
  # Cloud Manager's Git repository
  MAIN_REPOSITORY: https://$MAIN_USER:$MAIN_PASSWORD@git.cloudmanager.adobe.com/<PATH>
  # The branch in Cloud Manager's Git repository to push to
  MAIN_BRANCH : <BRANCH_NAME>
 
# Only run on a push to this branch
on:
  push:
     branches: [ main ]
 
jobs:
  build:
    runs-on: ubuntu-latest
 
    steps:
      # Checkout this project into a sub folder
      - uses: actions/checkout@v2
        with:
          path: sub
      # Cleanup sub project
      - name: Clean project
        run: |
          git -C sub log --format="%an : %s" -n 1 > commit.txt
          rm -rf sub/.git
          rm -rf sub/.github
      # Set global git configuration
      - name: Set git config
        run: |
          git config --global credential.helper cache
          git config --global user.email ${USER_EMAIL}
          git config --global user.name ${USER_NAME}
      # Checkout the main project
      - name: Checkout main project
        run:
          git clone -b ${MAIN_BRANCH} ${MAIN_REPOSITORY} ${MAIN_BRANCH} 
      # Move sub project
      - name: Move project to main project
        run: |
          rm -rf ${MAIN_BRANCH}/${PROJECT_DIR} 
          mv sub ${MAIN_BRANCH}/${PROJECT_DIR}
      - name: Commit Changes
        run: |
          git -C ${MAIN_BRANCH} add -f ${PROJECT_DIR}
          git -C ${MAIN_BRANCH} commit -F ../commit.txt
          git -C ${MAIN_BRANCH} push
```

GitHub 작업 사용은 매우 유연합니다. git 저장소 분기 간의 모든 매핑은 물론 별도의 git 프로젝트를 기본 프로젝트의 디렉터리 레이아웃으로 매핑할 수 있습니다.

>[!NOTE]
>
>샘플 스크립트는 `git add`를 사용하여 저장소를 업데이트합니다. 여기에 제거가 포함되어 있다고 가정합니다. git의 기본 구성에 따라 `git add --all`로 대체해야 할 수도 있습니다.

## 샘플 Jenkins 작업 {#sample-jenkins-job}

Jenkins 작업 또는 이와 유사한 작업에서 사용할 수 있는 샘플 스크립트이며 다음과 같은 흐름이 있습니다.

1. git 저장소의 변경으로 인해 트리거됩니다.
1. Jenkins 작업은 해당 프로젝트 또는 분기의 최신 상태를 확인합니다.
1. 그런 다음 작업은 이 스크립트를 트리거합니다.
1. 이 스크립트는 Cloud Manager의 git 저장소를 체크아웃하고 프로젝트 코드를 하위 디렉터리에 커밋합니다.

Jenkins 작업에는 Cloud Manager의 git 저장소에 연결하고 푸시할 수 있도록 `MAIN_USER` 및 `MAIN_PASSWORD`라는 두 가지 비밀이 제공되어야 합니다.

```java
# Username/email used to commit to Cloud Manager's Git repository
export USER_NAME=<NAME>
export USER_EMAIL=<EMAIL>
# Directory within the Cloud Manager Git repository
export PROJECT_DIR=project-a
# Cloud Manager's Git repository
export MAIN_REPOSITORY=https://$MAIN_USER:$MAIN_PASSWORD@git.cloudmanager.adobe.com/<PATH>
# The branch in Cloud Manager's Git repository to push to
export MAIN_BRANCH=<BRANCH_NAME>
 
# clean up and init
rm -rf target
mkdir target
 
# mv project to sub folder
mkdir target/sub
for f in .* *
do
    if [ "$f" != "." -a "$f" != ".." -a "$f" != "target" ]
    then
        mv "$f" target/sub
    fi
done
cd target
 
# capture log and remove git info
cd sub
git log --format="%an : %s" -n 1 > ../commit.txt
rm -rf .git
rm -rf .github
cd ..
 
# checkout main repository
git clone -b $MAIN_BRANCH $MAIN_REPOSITORY main
cd main
 
# configure main repository
git config credential.helper cache
git config user.email $USER_EMAIL
git config user.name $USER_NAME
 
# update project in main
rm -rf $PROJECT_DIR
mv ../sub $PROJECT_DIR
 
# commit changes to main
git add -f $PROJECT_DIR
git commit -F ../commit.txt
git push
```

Jenkins 작업 사용은 매우 유연합니다. git 저장소 분기 간의 모든 매핑은 물론 별도의 git 프로젝트를 기본 프로젝트의 디렉터리 레이아웃으로 매핑할 수 있습니다.

>[!NOTE]
>
>샘플 스크립트는 `git add`를 사용하여 저장소를 업데이트합니다. 여기에 제거가 포함되어 있다고 가정합니다. git의 기본 구성에 따라 `git add --all`로 대체해야 할 수도 있습니다.
