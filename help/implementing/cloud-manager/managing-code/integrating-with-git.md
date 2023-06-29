---
title: Cloud Manager와 함께 git 사용
description: Cloud Manager의 git 저장소를 사용하는 방법과 자체 On-Premise 고객 관리 git 저장소를 Cloud Manager와 통합하는 방법을 알아봅니다.
exl-id: 57e71b8a-4546-4d7f-825c-a1637d08e608
source-git-commit: bceec9ea6858b1c4c042ecd96f13ae5cac1bbee5
workflow-type: ht
source-wordcount: '316'
ht-degree: 100%

---

# Cloud Manager와 함께 git 사용 {#git-integration}

Adobe Cloud Manager는 Cloud Manager의 CI/CD 파이프라인을 사용하여 코드를 배포하는 데 사용되는 단일 git 저장소와 함께 제공됩니다.

Cloud Manager의 git 저장소를 즉시 사용할 수 있지만 고객 관리 git 저장소를 Cloud Manager와 통합하는 옵션도 있습니다.

## Git 통합 개요 {#git-integration-overview}

이 비디오 시리즈에서는 다음을 포함하여 고객 관리 git 저장소를 Cloud Manager와 통합할 때의 여러 사용 사례를 살펴봅니다.

* [최초 동기화](#initial-sync)
* [기본 분기 전략](#branching-strategy)
* [기능 분기 개발](#feature-development)
* [프로덕션 배포](#production-deployment)
* [릴리스 태그 동기화](#sync-tags)

이 비디오 시리즈는 git 및 소스 제어 관리에 대한 기본 지식이 있다고 가정합니다. git에 대한 자세한 내용은 [아래의 추가 리소스](#additional-resources)를 참조하십시오.

>[!VIDEO](https://video.tv.adobe.com/v/28710/)

이 비디오 시리즈에 설명된 단계 및 명명 규칙은 Cloud Manager에서 고객 관리 git 저장소를 사용하기 위한 몇 가지 모범 사례를 나타냅니다. 표시된 규칙과 워크플로는 개별 사용 사례에 맞게 조정되어야 합니다.

## 최초 동기화 {#initial-sync}

이 비디오에서는 고객 관리 Git 저장소를 Cloud Manager의 Git 저장소와 동기화하는 첫 번째 단계를 알아봅니다.

>[!VIDEO](https://video.tv.adobe.com/v/28711/?quality=12)

## 기본 분기 전략 {#branching-strategy}

이 비디오에서는 기본적인 분기 전략을 배웁니다.

>[!VIDEO](https://video.tv.adobe.com/v/28712/?quality=12)

## 기능 분기 개발 {#feature-development}

기능 분기를 사용하여 고객 관리 git 저장소에서 코드 변경 사항을 격리하고 Cloud Manager의 git 저장소와 동기화하여 비프로덕션 파이프라인을 통해 코드 품질 및 유효성 검사 테스트를 수행합니다.

>[!VIDEO](https://video.tv.adobe.com/v/28723/?quality=12)

## 프로덕션 배포 {#production-deployment}

고객 관리 git 저장소에서 프로덕션 릴리스용 코드를 준비하고 Cloud Manager의 git 저장소와 동기화하여 스테이지 및 프로덕션 환경에 배포합니다.

>[!VIDEO](https://video.tv.adobe.com/v/28724/?quality=12)

## 릴리스 태그 동기화 {#sync-tags}

스테이지 및 프로덕션 환경에 배포된 코드를 확인할 수 있도록 Cloud Manager git 저장소의 릴리스 태그를 고객 관리 git 저장소로 동기화합니다.

>[!VIDEO](https://video.tv.adobe.com/v/28725/?quality=12)

## 추가 리소스 {#additional-resources}

* [GitHub 리소스](https://try.github.io)
* [Atlassian Git 튜토리얼](https://www.atlassian.com/git/tutorials/what-is-version-control)
* [Git 치트 시트](https://education.github.com/git-cheat-sheet-education.pdf)
