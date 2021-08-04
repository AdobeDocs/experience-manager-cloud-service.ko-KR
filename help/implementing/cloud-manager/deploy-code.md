---
title: 코드 배포 - Cloud Services
description: 코드 배포 - Cloud Services
exl-id: 2c698d38-6ddc-4203-b499-22027fe8e7c4
source-git-commit: bcd106a39bec286e2a09ac7709758728f76f9544
workflow-type: tm+mt
source-wordcount: '616'
ht-degree: 0%

---

# 코드 배포 {#deploy-your-code}

## AEM에서 Cloud Service으로 Cloud Manager와 함께 코드 배포 {#deploying-code-with-cloud-manager}

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

   * 유효성 검사: 이 단계에서는 파이프라인이 현재 사용 가능한 리소스(예: 구성된 분기가 존재하며 환경을 사용할 수 있도록 구성됩니다.
   * 빌드 및 단위 테스트: 이 단계에서는 컨테이너화된 빌드 프로세스를 실행합니다. 빌드 환경에 대한 자세한 내용은 [빌드 환경 세부 정보](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/build-environment-details.md)를 참조하십시오.
   * 코드 스캔: 이 단계에서는 애플리케이션 코드의 품질을 평가합니다. 테스트 프로세스에 대한 자세한 내용은 [코드 품질 테스트](/help/implementing/cloud-manager/code-quality-testing.md)를 참조하십시오.
   * 이미지 작성: 이 단계에는 이미지를 작성하는 데 사용되는 프로세스의 로그 파일이 있습니다. 이 프로세스는 빌드 단계에서 생성된 컨텐츠 및 디스패처 패키지를 Docker 이미지 및 Kubernetes 구성으로 변환해야 합니다.
   * 스테이지에 배포

      ![](assets/stage-deployment.png)
   **스테이지 테스트**&#x200B;에는 다음 단계가 포함됩니다.

   * **제품 기능 테스트**: Cloud Manager 파이프라인 실행은 스테이지 환경에서 실행되는 테스트 실행을 지원합니다.
자세한 내용은 [제품 기능 테스트](/help/implementing/cloud-manager/functional-testing.md#product-functional-testing)를 참조하십시오.

   * **사용자 지정 기능 테스트**: 파이프라인의 이 단계는 항상 존재하며 건너뛸 수 없습니다. 그러나 빌드에 의해 테스트 JAR이 생성되지 않으면 테스트가 기본적으로 전달됩니다.\
      자세한 내용은 [사용자 지정 기능 테스트](/help/implementing/cloud-manager/functional-testing.md#custom-functional-testing)를 참조하십시오.

   * **사용자 지정 UI 테스트**: 이 단계는 고객이 애플리케이션에 대한 UI 테스트를 만들고 자동으로 실행할 수 있도록 하는 선택 기능입니다. UI 테스트는 Java 및 Maven, Node 및 WebDriver.io와 같은 다양한 언어 및 프레임워크(또는 Selenium을 기반으로 구축된 기타 프레임워크 및 기술)를 사용할 수 있도록 Docker 이미지에 패키지된 Selenium 기반 테스트입니다.
자세한 내용은 [사용자 지정 UI 테스트](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/test-results/functional-testing.html?lang=en#custom-ui-testing)를 참조하십시오.


   * **경험 감사**: 파이프라인의 이 단계는 항상 존재하며 건너뛸 수 없습니다. 프로덕션 파이프라인이 실행되면 검사를 실행하는 사용자 지정 기능 테스트 후 경험 감사 단계가 포함됩니다. 구성된 페이지는 서비스에 제출되고 평가됩니다. 결과는 정보 제공용이며 사용자가 현재 점수와 이전 점수 간의 변경 사항을 확인할 수 있도록 합니다. 이 통찰력은 현재 배포와 함께 도입될 회귀 여부를 판별하는 데 유용합니다.
자세한 내용은 [경험 감사 결과 이해](/help/implementing/cloud-manager/experience-audit-testing.md)를 참조하십시오.

      ![](assets/stage-testing.png)





## 배포 프로세스 {#deployment-process}

모든 Cloud Service 배포은 롤링 프로세스에 따라 다운타임 없이 시스템을 구축할 수 있습니다. 자세한 내용은 [롤링 배포 작동 방식](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/deploying/overview.html#how-rolling-deployments-work)을 참조하십시오.

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
