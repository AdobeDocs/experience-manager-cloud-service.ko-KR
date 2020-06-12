---
title: 클라우드 준비 분석기 사용
description: 클라우드 준비 분석기 사용
translation-type: tm+mt
source-git-commit: 1739f81d4894f3e04cc4119f344a3bea5bd042d8
workflow-type: tm+mt
source-wordcount: '556'
ht-degree: 1%

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

   ![이미지](/help/move-to-cloud-service/cloud-readiness-analyzer/assets/cra-1.png)

1. 클라우드 준비 분석기를 ****&#x200B;클릭하면 도구가 보고서 생성을 시작하고 몇 분 후 AEM 인스턴스에서 요약 보고서를 사용할 수 있습니다.

   >[!NOTE]
   >전체 보고서를 보려면 페이지를 아래로 스크롤해야 합니다.

   ![이미지](/help/move-to-cloud-service/cloud-readiness-analyzer/assets/cra-2.png)

### 요약 보고서에서 결과 보기 {#viewing-the-results}

>[!IMPORTANT]
>클라우드 준비 분석기에서 생성된 보고서는 패턴 탐지기를 기반으로 합니다. 자세한 내용은 [패턴 탐지기](https://docs.adobe.com/content/help/en/experience-manager-65/deploying/upgrading/pattern-detector.html) 를 참조하십시오.

페이지를 아래로 스크롤하여 전체 요약 보고서를 보고 나면 보고서에서 강조 표시된 각 카테고리에 대해 다음 정보를 볼 수 있습니다.

1. **중요도 수준**

   다음 표에서는 다양한 패턴 탐지 및 클라우드 준비 분석기 중요도 수준의 의미를 설명합니다.

   | 중요도 수준 | 설명 |
   |--- |--- |
   | 정보/0 | 이 검색 결과는 정보용으로 제공됩니다. |
   | 권고/1 | 이 검색 결과는 잠재적으로 업그레이드 문제가 될 수 있습니다. 추가 조사가 권장됩니다. |
   | 주/2 | 이 문제는 해결해야 하는 업그레이드 문제가 될 수 있습니다. |
   | 위험/3 | 이러한 검색 결과는 기능 또는 성능 손실을 방지하기 위해 해결해야 하는 업그레이드 문제가 될 가능성이 높습니다. |

1. **설명**&#x200B;은 보고된 카테고리에 대한 정보를 제공합니다.

1. **설명서 URL**&#x200B;문서 URL을 사용하면 관련 유형에 대한 기술 설명서를 볼 수 있습니다.

1. **메시지**&#x200B;단일 메시지에서 찾는 방법에 대한 설명입니다.

### CSV 형식으로 결과 보기 {#viewing-the-results-csv}

요약 보고서는 AEM 사용자 인터페이스에서 사용할 수 있습니다. 리팩토링 프로세스 중에 유용한 CSV(쉼표로 구분된 값) 형식으로 전체 보고서를 다운로드할 수 있습니다.

아래 절차에 따라 요약 보고서의 CSV 형식을 생성합니다.

1. 
   1. Adobe Experience Manager를 선택하고 도구 -> **작업** -> **클라우드 준비 분석기로 이동합니다**.

1. 보고서를 사용할 수 있게 되면 **CSV를** 클릭하여 아래 그림과 같이, 전체 요약 보고서를 쉼표로 구분된 값(CSV) 형식으로 다운로드합니다.

![이미지](/help/move-to-cloud-service/cloud-readiness-analyzer/assets/cra-3.png)


#### AEM 6.1 인스턴스에서 보고서 보기 {#aem-instances-report}

아래 절차에 따라 AEM(Adobe Experience Manager) 6.1용 CSV 보고서를 다운로드하십시오.

1.를 사용하여 **Adobe Experience Manager 웹 콘솔** 구성으로 이동합니다 `https://serveraddress:serverport/system/console/configMgr`.

1. 아래 그림과 같이 **상태** 탭을 선택하고 드롭다운 목록에서 **패턴** 탐지기를 검색합니다.

   ![이미지](/help/move-to-cloud-service/cloud-readiness-analyzer/assets/cra-4.png)

1. 요약 보고서는 zip 폴더 또는 JSON 형식으로 다운로드할 수 있습니다.


