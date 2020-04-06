---
title: 클라우드 서비스로 이동하는 복잡성 평가
description: 클라우드 서비스로 이동하는 복잡성 평가
translation-type: tm+mt
source-git-commit: 83f7a1d57fae92e6ce15e4d9d6e00682d4596d05

---


# 클라우드 서비스로 이동하는 복잡성 평가 {#accesing-complexity}

## 개요 {#overview}

CRA(클라우드 준비 분석기)를 사용하면 기존 AEM 인스턴스에서 다음 패턴을 감지하여 클라우드 서비스로 이동할 준비가 되었는지 확인할 수 있습니다.

* 현재 클라우드 서비스에서 지원되지 않는 AEM 6.x 기능 사용

* 클라우드 서비스로 이동하면 영향을 받는 특정 규칙을 위반합니다.

>[!NOTE]
>CRA의 출력은 Cloud Service로 전환하는 데 필요한 개발 노력에 대한 평가를 가속화합니다.

## 클라우드 준비 분석기 설정 {#setting-up-cra}

CRA는 XX 이상의 소스 AEM 버전에서 작동하는 패키지로 릴리스되어 Cloud Service로 전환을 모색하고 있습니다.

소프트웨어 배포 포털에서 제공되며 패키지 관리자를 사용하여 설치할 수 있습니다.

### 클라우드 준비 분석기 사용 {#using-cra}

>[!NOTE]
> CRA는 로컬 개발 인스턴스를 비롯한 모든 환경에서 실행할 수 있습니다.

>[중요]
>그러나 중요한 비즈니스 인스턴스에서 감지 비율을 높이고 작업 속도를 늦추지 않도록 하기 위해 사용자 애플리케이션, 컨텐츠 및 구성 영역의 운영 환경에 가능한 한 가까운 스테이징 환경에서 실행하는 것이 좋습니다

### 클라우드 준비 분석기의 출력 보기 {#viewing-output-cra}


1. 를 사용하여 Adobe Experience Manager 웹 콘솔 **구성으로 이동하여** AEM 웹 콘솔로 이동합니다 `https://serveraddress:serverport/system/console/configMgr`.

1. 아래 이미지와 같이 상태 - 클라우드 준비 분석기를 선택합니다.

1. 반응형 텍스트 기반 또는 정규 JSON 인터페이스를 통해 출력을 볼 수도 있습니다.

>[!NOTE]
> 이러한 [방법에 대한 자세한 내용은 패턴](https://docs.adobe.com/content/help/en/experience-manager-65/deploying/upgrading/pattern-detector.html) 탐지기(Pattern Detector)를 참조하십시오. CRA를 사용할 준비가 되면 이 섹션을 추가해야 합니다.

## 클라우드 준비의 다음 단계 {#the-next-steps}

Adobe에서 클라우드 서비스의 준비 상태에 대한 자세한 내용을 살펴보려면 CRA의 출력을 평가해야 합니다.

아래 절차에 따라 파일을 다시 전송합니다.

1. AEM 웹 콘솔로 이동하고 아래 이미지에 표시된 대로 xx 파일을 다운로드합니다.

1. DayCare 티켓을 열어 다음 방법으로 Adobe로 파일을 전송합니다.
   1. Cloud Readiness Analyzer Output이라는 **Daycare의 지원 티켓 로깅**
   1. 티켓에 출력 파일 첨부

