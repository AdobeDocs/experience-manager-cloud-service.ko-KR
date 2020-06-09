---
title: 클라우드 준비 분석기 사용
description: 클라우드 준비 분석기 사용
translation-type: tm+mt
source-git-commit: 317dd08600df9c7127cf8502341f93758ac8ce0b
workflow-type: tm+mt
source-wordcount: '256'
ht-degree: 0%

---


# 클라우드 준비 분석기 사용 {#using-cloud-readiness-analyzer}

## 클라우드 준비 분석기 사용에 대한 중요 고려 사항 {#imp-considerations}

CRA(클라우드 준비 분석기)를 실행하는 동안 중요한 고려 사항을 이해하려면 아래 섹션을 따르십시오.

* CRA는 버전 6.1 이상의 소스 AEM 인스턴스에서 지원됩니다.
* CRA는 모든 환경에서 실행할 수 있습니다. 그러나 중요한 비즈니스 인스턴스의 감지 비율을 높이고 속도 저하를 방지하려면 사용자 지정, 구성, 컨텐츠 및 사용자 애플리케이션 영역의 제작 환경에 가능한 한 가까운 소스 작성자 스테이징 환경에서 이 설정을 실행하는 것이 좋습니다. 또는 게시 환경의 클론에서도 실행할 수 있습니다.

## 사용 가능 {#availability}

CRA(클라우드 준비 분석기)는 소프트웨어 배포 포털에서 zip 파일로 다운로드할 수 있습니다. 소스 AEM(Adobe Experience Manager) 인스턴스에 패키지 관리자를 통해 패키지를 설치할 수 있습니다.

>[!NOTE]
>보류 중인 CRA(Cloud Readance Analyzer)를 다운로드합니다.

## 클라우드 준비 분석기 실행 {#running-tool}

클라우드 준비 분석기를 실행하는 방법을 알려면 다음 섹션을 따르십시오.

1. Adobe Experience Manager를 선택하고 도구 -> **작업** -> **클라우드 준비 분석기로 이동합니다**.

### 결과 보기 {#viewing-the-results}

두 가지 방법으로 CRA의 출력을 볼 수 있습니다.

1. 구성된 보고서(AEM 버전 6.3 이상에서 사용 가능)보고서에서 중요도 수준을 설명하려면 CRA 문서 계획 및 상태를 참조하십시오

CRA의 출력을 보려면(AEM 버전 6.1 이상에서 사용할 수 있음):

1. 탐색하여 AEM 웹 콘솔로 이동합니다.

1. 아래 이미지와 같이 상태 - 클라우드 준비 분석기를 선택합니다.