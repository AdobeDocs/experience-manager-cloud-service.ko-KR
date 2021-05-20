---
title: 코드 배포 - Cloud Services
description: 코드 배포 - Cloud Services
exl-id: 2c698d38-6ddc-4203-b499-22027fe8e7c4
source-git-commit: 782035708467693ec7648b1fd701c329a0b5f7c8
workflow-type: tm+mt
source-wordcount: '1071'
ht-degree: 0%

---

# 코드 배포 {#deploy-your-code}

## AEM에서 Cloud Manager와 함께 코드를 Cloud Service {#deploying-code-with-cloud-manager} 로 배포

프로덕션 파이프라인(저장소, 환경 및 테스트 환경)을 구성했으면 코드를 배포할 준비가 된 것입니다.

1. Cloud Manager에서 **배포**&#x200B;를 클릭하여 배포 프로세스를 시작합니다.

   ![](assets/deploy-code1.png)


1. **파이프라인 실행** 화면이 표시됩니다.

   **빌드**&#x200B;를 클릭하여 프로세스를 시작합니다.

   ![](assets/deploy-code2.png)

1. 전체 빌드 프로세스에서 코드를 배포합니다.

   다음 단계는 빌드 프로세스에 관련되어 있습니다.

   1. 스테이지 배포
   1. 단계 테스트
   1. 프로덕션 배포

   >[!NOTE]
   >
   >또한 테스트 기준에 대한 로그를 보거나 결과를 검토하여 다양한 배포 프로세스의 단계를 검토할 수 있습니다.

   **스테이지 배포**&#x200B;에는 다음 단계가 포함됩니다.

   * 유효성 검사:이 단계에서는 파이프라인이 현재 사용 가능한 리소스(예: 구성된 분기가 존재하며 환경을 사용할 수 있도록 구성됩니다.
   * 빌드 및 단위 테스트:이 단계에서는 컨테이너화된 빌드 프로세스를 실행합니다. 빌드 환경에 대한 자세한 내용은 [빌드 환경 세부 정보](/help/onboarding/getting-access-to-aem-in-cloud/build-environment-details.md)를 참조하십시오.
   * 코드 스캔:이 단계에서는 애플리케이션 코드의 품질을 평가합니다. 테스트 프로세스에 대한 자세한 내용은 [코드 품질 테스트](/help/implementing/cloud-manager/code-quality-testing.md)를 참조하십시오.
   * 이미지 작성:이 단계에는 이미지를 작성하는 데 사용되는 프로세스의 로그 파일이 있습니다. 이 프로세스는 빌드 단계에서 생성된 컨텐츠 및 디스패처 패키지를 Docker 이미지 및 Kubernetes 구성으로 변환해야 합니다.
   * 스테이지에 배포

      ![](assets/stage-deployment.png)
   **스테이지 테스트**&#x200B;에는 다음 단계가 포함됩니다.

   * **제품 기능 테스트**:Cloud Manager 파이프라인 실행은 스테이지 환경에서 실행되는 테스트 실행을 지원합니다.
자세한 내용은 [제품 기능 테스트](/help/implementing/cloud-manager/functional-testing.md#product-functional-testing)를 참조하십시오.

   * **사용자 지정 기능 테스트**:파이프라인의 이 단계는 항상 존재하며 건너뛸 수 없습니다. 그러나 빌드에 의해 테스트 JAR이 생성되지 않으면 테스트가 기본적으로 전달됩니다.\
      자세한 내용은 [사용자 지정 기능 테스트](/help/implementing/cloud-manager/functional-testing.md#custom-functional-testing)를 참조하십시오.

   * **사용자 지정 UI 테스트**:이 단계는 고객이 애플리케이션에 대한 UI 테스트를 만들고 자동으로 실행할 수 있도록 하는 선택 기능입니다. UI 테스트는 Java 및 Maven, Node 및 WebDriver.io와 같은 다양한 언어 및 프레임워크(또는 Selenium을 기반으로 구축된 기타 프레임워크 및 기술)를 사용할 수 있도록 Docker 이미지에 패키지된 Selenium 기반 테스트입니다.
자세한 내용은 [사용자 지정 UI 테스트](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/test-results/functional-testing.html?lang=en#custom-ui-testing)를 참조하십시오.


   * **경험 감사**:파이프라인의 이 단계는 항상 존재하며 건너뛸 수 없습니다. 프로덕션 파이프라인이 실행되면 검사를 실행하는 사용자 지정 기능 테스트 후 경험 감사 단계가 포함됩니다. 구성된 페이지는 서비스에 제출되고 평가됩니다. 결과는 정보 제공용이며 사용자가 현재 점수와 이전 점수 간의 변경 사항을 확인할 수 있도록 합니다. 이 통찰력은 현재 배포와 함께 도입될 회귀 여부를 판별하는 데 유용합니다.
자세한 내용은 [경험 감사 결과 이해](/help/implementing/cloud-manager/experience-audit-testing.md)를 참조하십시오.

      ![](assets/stage-testing.png)





## 배포 프로세스 {#deployment-process}

다음 섹션에서는 AEM 및 Dispatcher 패키지가 단계 및 프로덕션 단계에서 배포되는 방법을 설명합니다.

Cloud Manager는 빌드 프로세스에서 생성된 모든 target/*.zip 파일을 저장 위치에 업로드합니다.  이러한 가공물은 파이프라인의 배포 단계 동안 이 위치에서 검색됩니다.

Cloud Manager가 비프로덕션 토폴로지에 배포될 때 목표는 가능한 한 빨리 배포를 완료하여 아티팩트가 다음과 같이 모든 노드에 동시에 배포되는 것입니다.

1. Cloud Manager는 각 아티팩트가 AEM 패키지인지 또는 디스패처 패키지인지를 결정합니다.
1. Cloud Manager는 배포 중에 환경을 격리하기 위해 로드 밸런서에서 모든 디스패처를 제거합니다.

   별도로 구성되지 않은 경우 스테이지 환경에서 비프로덕션 파이프라인, 개발 환경 및 프로덕션 파이프라인의 로드 밸런서 변경 사항 즉, 단계를 분리하고 연결할 수 있습니다.

   >[!NOTE]
   >
   >이 기능은 주로 1-1-1 고객이 사용할 것입니다.

1. 각 AEM 아티팩트는 패키지 관리자 API를 통해 각 AEM 인스턴스에 배포되며 패키지 종속성이 배포 순서를 결정합니다.

   패키지를 사용하여 새 기능을 설치하고 인스턴스 간에 컨텐츠를 전송하며 저장소 컨텐츠를 백업하는 방법에 대한 자세한 내용은 패키지 사용 방법 을 참조하십시오.

   >[!NOTE]
   >
   >모든 AEM 가공물은 작성자와 게시자 모두에 배포됩니다. 실행 모드는 노드별 구성이 필요할 때 활용해야 합니다. 실행 모드에서 특정 목적으로 AEM 인스턴스를 튜닝할 수 있는 방법에 대한 자세한 내용은 실행 모드를 참조하십시오.

1. 디스패처 아티팩트는 다음과 같이 각 디스패처에 배포됩니다.

   1. 현재 구성이 백업되어 임시 위치에 복사됩니다.
   1. 변경할 수 없는 파일을 제외하고 모든 구성이 삭제됩니다. 자세한 내용은 Dispatcher 구성 관리 를 참조하십시오. 이렇게 하면 분리된 파일이 남아 있지 않도록 디렉토리를 지웁니다.
   1. 아티팩트가 `httpd` 디렉토리에 추출됩니다.  변경할 수 없는 파일은 덮어쓰지 않습니다. 배포 시 Git 리포지토리에서 변경할 수 없는 파일을 변경하면 변경 사항이 무시됩니다.  이러한 파일은 AMS 디스패처 프레임워크의 핵심이며 변경할 수 없습니다.
   1. Apache가 구성 테스트를 수행합니다. 오류가 없으면 서비스가 다시 로드됩니다. 오류가 발생하면 구성이 백업에서 복원되고 서비스가 다시 로드되며 오류가 Cloud Manager로 다시 보고됩니다.
   1. 파이프라인 구성에 지정된 각 경로는 디스패처 캐시에서 무효화되거나 플러시됩니다.

   >[!NOTE]
   >
   >Cloud Manager에서는 디스패처 아티팩트에 전체 파일 세트가 포함되어야 합니다.  모든 Dispatcher 구성 파일은 Git 저장소에 있어야 합니다. 파일 또는 폴더가 누락되면 배포 오류가 발생합니다.

1. 모든 AEM 및 Dispatcher 패키지를 모든 노드에 성공적으로 배포한 후 Dispatcher가 로드 밸런서에 다시 추가되고 배포가 완료됩니다.

   >[!NOTE]
   >
   >개발 및 스테이지 배포에서 로드 밸런서 변경을 건너뛸 수 있습니다. 즉, 스테이지 환경에서 비프로덕션 파이프라인, 개발자 환경 및 프로덕션 파이프라인에 대해 단계를 분리 및 연결할 수 있습니다.

### 프로덕션 단계에 배포 {#deployment-production-phase}

AEM 사이트 방문자에 대한 영향을 최소화하기 위해 프로덕션 토폴로지에 배포하는 프로세스는 약간 다릅니다.

프로덕션 배포는 일반적으로 위와 동일한 단계를 따르지만, 롤링 방식으로 수행합니다.

1. 작성자에게 AEM 패키지를 배포합니다.
1. 로드 밸런서에서 dispatcher1을 분리합니다.
1. AEM 패키지를 배포하여 publish1 및 dispatcher 패키지를 dispatcher1에 배포하고 디스패처 캐시를 플러시합니다.
1. dispatcher1을 로드 밸런서에 다시 넣습니다.
1. dispatcher1이 다시 서비스를 제공되면 로드 밸런서에서 dispatcher2를 분리하십시오.
1. AEM 패키지를 배포하여 publish2 및 dispatcher 패키지를 dispatcher2에 배포하고 디스패처 캐시를 플러시합니다.
1. dispatcher2를 로드 밸런서에 다시 넣습니다.
이 프로세스는 배포가 토폴로지의 모든 게시자 및 디스패처에 도달할 때까지 계속됩니다.
