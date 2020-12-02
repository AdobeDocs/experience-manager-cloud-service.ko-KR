---
title: 여러 소스 Git 리포지토리를 사용한 작업
description: 여러 소스 Git 리포지토리를 사용한 작업 - Cloud Services
translation-type: tm+mt
source-git-commit: 8e470ed1ea30fd2fa59617fdb6755abf9a0d74a2
workflow-type: tm+mt
source-wordcount: '762'
ht-degree: 0%

---


# 여러 소스 Git 리포지토리를 사용한 작업 {#working-with-multiple-source-git-repos}


## 고객이 관리하는 Git 리포지토리 동기화 {#syncing-customer-managed-git-repositories}

고객은 Cloud Manager의 Git 리포지토리를 직접 사용하는 대신 고유한 Git 리포지토리 또는 여러 개의 고유한 Git 리포지토리를 사용하여 작업할 수 있습니다. 이러한 경우 자동 동기화 프로세스를 설정하여 Cloud Manager의 Git 리포지토리가 항상 최신 상태로 유지되도록 해야 합니다. 고객의 Git 리포지토리가 호스팅되는 위치에 따라 GitHub 작업 또는 Jenkins와 같은 지속적인 통합 솔루션을 사용하여 자동화를 설정할 수 있습니다. 자동화 기능을 통해 고객 소유의 Git 리포지토리에 대한 모든 푸시를 Cloud Manager의 Git 리포지토리로 자동으로 전달할 수 있습니다.

단일 고객 소유의 Git 저장소에 대한 이러한 자동화는 바로 진행되지만, 여러 저장소에 대해 이렇게 설정하려면 초기 설정이 필요합니다. 여러 Git 리포지토리의 컨텐츠를 단일 Cloud Manager의 Git 저장소 내의 다른 디렉토리에 매핑해야 합니다.  Cloud Manager의 Git 리포지토리는 루트 Maven 폼으로 제공되어야 하며, 아래의 모듈 섹션에 다른 하위 프로젝트를 나열하는 것은 두 명의 고객이 소유한 git 리포지토리를 위한 샘플 프로세스입니다.첫 번째 프로젝트가 `project-a`이라는 디렉토리에 삽입되고 두 번째 프로젝트가 `project-b` 디렉토리에 추가됩니다.

```xml
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/maven-v4_0_0.xsd">
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

이러한 루트 폼은 Cloud Manager의 git 저장소의 분기에 푸시됩니다. 그러면 Cloud Manager의 git 리포지토리에 변경 내용을 자동으로 전달하려면 두 프로젝트를 설정해야 합니다. 예를 들어 프로젝트 A의 분기에 대한 푸시에 의해 GitHub 작업을 트리거할 수 있습니다. 이 작업은 프로젝트 A 및 클라우드 관리자 Git 리포지토리를 체크아웃하고 프로젝트 A의 모든 컨텐츠를 Cloud Manager Git 저장소의 디렉토리 `project-a`에 복사한 다음 변경 내용을 커밋합니다. 예를 들어 프로젝트 A의 기본 분기에 대한 변경 사항은 Cloud Manager의 git 저장소의 기본 분기로 자동 푸시됩니다. 물론, 프로젝트 A의 &quot;dev&quot;라는 분기로 푸시하는 것과 같은 분기가 Cloud Manager의 Git 리포지토리의 &quot;개발&quot;이라는 분기로 푸시되는 경우도 있습니다.  프로젝트 B에 대해 유사한 설정을 수행해야 합니다.

분기 전략 및 워크플로우에 따라 서로 다른 분기에 대해 동기화를 구성할 수 있습니다. 사용된 Git 리포지토리에서 GitHub 동작과 유사한 개념을 제공하지 않는 경우 Jenkins(또는 유사)를 통한 통합도 가능합니다. 이 경우 웹 후크는 작업을 수행하는 젠킨스 작업을 트리거합니다.

아래 절차에 따라 새(세 번째) 소스 또는 저장소를 추가합니다.

1. 새 GitHub 동작을 새 리포지토리에 추가하여 변경 내용을 Cloud Manager의 Git 리포지토리로 푸시합니다.
1. 프로젝트 코드가 Cloud Manager의 Git 저장소에 있는지 확인하려면 해당 작업을 최소한 한 번 수행하십시오.
1. Cloud Manager Git 저장소의 루트 Maven 포m의 새 디렉토리에 대한 참조를 추가합니다.


## 부록 A:샘플 GitHub 작업 {#sample-github-action}

기본 분기에 푸시를 한 다음 Cloud Manager의 Git 저장소의 하위 디렉토리에 푸시하여 트리거되는 샘플 GitHub 작업입니다. Cloud Manager의 Git 저장소에 연결하고 푸시할 수 있으려면 Github 작업에 `MAIN_USER` 및 `MAIN_PASSWORD` 두 개의 비밀이 제공되어야 합니다.

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
          git clone -b ${MAIN_BRANCH} https://${{ secrets.PAT }}@github.com/${MAIN_REPOSITORY}.git main 
      # Move sub project
      - name: Move project to main project
        run: |
          rm -rf main/${PROJECT_DIR} 
          mv sub main/${PROJECT_DIR}
      - name: Commit Changes
        run: |
          git -C main add -f ${PROJECT_DIR}
          git -C main commit -F ../commit.txt
          git -C main push
```

위에서 보듯이 GitHub 동작을 사용하는 것은 매우 유연합니다. Git 리포지토리의 분기 간 모든 매핑을 수행할 수 있을 뿐만 아니라 별도의 git 프로젝트를 기본 프로젝트의 디렉토리 레이아웃으로 매핑할 수 있습니다.

>[!NOTE]
>위의 스크립트에서는 `git add`을(를) 사용하여 제거가 포함되어 있다고 가정하는 저장소를 업데이트합니다. 이 작업은 Git의 기본 구성에 따라 `git add --all`로 대체되어야 합니다.

## 부록 B:샘플 젠킨스 작업 {#sample-jenkins-job}

이 스크립트는 Jenkins 작업 또는 유사한 작업에서 사용할 수 있는 샘플 스크립트입니다. Git 저장소의 변경으로 트리거됩니다. Jenkins 작업은 해당 프로젝트 또는 분기의 최신 상태를 확인한 다음 이 스크립트를 트리거합니다.

이 스크립트는 Cloud Manager의 Git 리포지토리를 체크 아웃하고 프로젝트 코드를 하위 디렉토리에 커밋합니다.

Cloud Manager의 Git 리포지토리에 연결하고 푸시할 수 있으려면 Jenkins 작업에 `MAIN_USER` 및 `MAIN_PASSWORD` 두 개의 비밀이 제공되어야 합니다.

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

위에서 볼 수 있듯이, 젠킨스 작업을 사용하는 것은 매우 유연하다. Git 리포지토리의 분기 간 모든 매핑을 수행할 수 있을 뿐만 아니라 별도의 git 프로젝트를 기본 프로젝트의 디렉토리 레이아웃으로 매핑할 수 있습니다.

>[!NOTE]
>위의 스크립트에서는 `git add`을(를) 사용하여 제거가 포함되어 있다고 가정하는 저장소를 업데이트합니다. 이 작업은 Git의 기본 구성에 따라 `git add --all`로 대체되어야 합니다.