---
title: 클라우드 준비 분석기 사용
description: 클라우드 준비 분석기 사용
translation-type: tm+mt
source-git-commit: 47773a56f8bb24342281068a8c4d03d6edfb9277
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 0%

---


# 클라우드 준비 분석기 사용 {#using-cloud-readiness-analyzer}

## 클라우드 준비 분석기 사용에 대한 중요 고려 사항 {#imp-considerations}

CRA(클라우드 준비 분석기)를 실행하는 동안 중요한 고려 사항을 이해하려면 아래 섹션을 따르십시오.

* CRA는 버전 6.1 이상의 소스 AEM 인스턴스에서 지원됩니다.
* CRA는 모든 환경(가급적이면 *스테이지* 환경)에서 실행할 수 있습니다.

   >[!NOTE]
   >비즈니스 크리티컬 인스턴스의 감지 비율을 높이고 속도 저하를 방지하려면 사용자 정의, 구성, 컨텐츠 및 사용자 애플리케이션 영역의 제작 환경에 가능한 한 가까운 소스 작성자 스테이징 환경에서 CRA를 실행하는 것이 좋습니다. 또는 게시 환경의 클론에서도 실행할 *수* 있습니다.

## 사용 가능 {#availability}

클라우드 준비 분석기는 소프트웨어 배포 포털에서 zip 파일로 다운로드할 수 있습니다. 소스 AEM(Adobe Experience Manager) 인스턴스에 패키지 관리자를 통해 패키지를 설치할 수 있습니다.

>[!NOTE]
>Software Distribution Portal *pending*&#x200B;에서 Cloud Readance Analyzer를 다운로드합니다.

## 클라우드 준비 분석기 실행 {#running-tool}

클라우드 준비 분석기를 실행하는 방법을 알려면 다음 섹션을 따르십시오.

1. Adobe Experience Manager를 선택하고 도구 -> **작업** -> **클라우드 준비 분석기로 이동합니다**.

### 결과 보기 {#viewing-the-results}

>[!IMPORTANT]
>클라우드 준비 분석기에서 생성된 보고서는 패턴 탐지기를 기반으로 합니다. 자세한 내용은 [패턴 탐지기](https://docs.adobe.com/content/help/en/experience-manager-65/deploying/upgrading/pattern-detector.html) 를 참조하십시오.

클라우드 준비 분석기의 출력을 보는 방법은 두 가지가 있습니다.

1. **구성된 보고서 사용**

   >[!NOTE]
   >구성된 보고서는 AEM 버전 6.3 이상에서 사용할 수 있습니다.

   또는,

1. **CRA 출력 보기**

   클라우드 준비 분석기의 출력을 보려면 아래 단계를 따르십시오.

   >[!NOTE]
   >아래 단계는 AEM 버전 6.1 이상 버전에 적용됩니다.

   1. 를 사용하여 **AEM 웹 콘솔로** 이동합니다 `https://serveraddress:serverport/system/console/configMgr`.

   1. 아래 **그림에 표시된 상태 - 패턴 탐지기** 를 선택합니다.

#### AEM 6.1 인스턴스에서 보고서 보기 {#aem-instances-report}

AEM 6.1용 csv 보고서를 다운로드할 수 있습니다. 보류 중입니다.

#### 보고서의 중요도 수준 이해 {#importance-levels}

다음 표에서는 다양한 패턴 탐지 및 클라우드 준비 분석기 중요도 수준의 의미를 설명합니다.

| 중요도 수준 | 설명 |
|--- |--- |
| 정보/0 | 이 검색 결과는 정보용으로 제공됩니다. |
| 권고/1 | 이 검색 결과는 잠재적으로 업그레이드 문제가 될 수 있습니다. 추가 조사가 권장됩니다. |
| 주/2 | 이 문제는 해결해야 하는 업그레이드 문제가 될 수 있습니다. |
| 위험/3 | 이러한 검색 결과는 기능 또는 성능 손실을 방지하기 위해 해결해야 하는 업그레이드 문제가 될 가능성이 높습니다. |