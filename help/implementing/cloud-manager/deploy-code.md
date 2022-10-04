---
title: 코드 배포
description: AEM as a Cloud Service에서 Cloud Manager 파이프라인을 사용하여 코드를 배포하는 방법을 알아봅니다.
exl-id: 2c698d38-6ddc-4203-b499-22027fe8e7c4
source-git-commit: cb08fcbd6c1060466ca9e6b4639774d43b70c83c
workflow-type: tm+mt
source-wordcount: '1220'
ht-degree: 17%

---


# 코드 배포 {#deploy-your-code}

AEM as a Cloud Service에서 Cloud Manager 파이프라인을 사용하여 프로덕션에 코드를 배포하는 방법을 알아봅니다.

![프로덕션 파이프라인 다이어그램](./assets/configure-pipeline/production-pipeline-diagram.png)

코드를 스테이징에 원활하게 배포한 다음 프로덕션에 배포합니다. 프로덕션 파이프라인 실행은 두 개의 논리 단계로 분할됩니다.

1. 스테이지 환경에 배포
   * 이 코드는 자동화된 기능 테스트, UI 테스트, 경험 감사 및 UAT(사용자 수락 테스트)를 위해 스테이지 환경에 구축되고 배포됩니다.
1. 프로덕션 환경에 배포
   * 빌드가 스테이지에서 검증되고 프로덕션으로 승격되도록 승인되면 동일한 빌드 아티팩트가 프로덕션 환경에 배포됩니다.

_전체 스택 코드 파이프라인 유형만 코드 스캔, 함수 테스트, UI 테스트 및 경험 감사를 지원합니다._

## AEM에서 Cloud Manager와 함께 코드 배포 as a Cloud Service {#deploying-code-with-cloud-manager}

한번 드시면 [프로덕션 파이프라인 구성](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md) 저장소, 환경 및 테스트 환경을 포함하여 코드를 배포할 준비가 되었습니다.

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)에서 Cloud Manager에 로그인한 다음 적절한 조직을 선택합니다.

1. 코드를 배포할 프로그램을 클릭합니다.

1. 클릭 **배포** 의 클릭유도문안으로부터 **개요** 배포 프로세스를 시작하는 화면

   ![CTA](assets/deploy-code1.png)

1. **파이프라인 실행** 화면이 표시됩니다. **빌드**&#x200B;를 클릭하여 프로세스를 시작합니다.

   ![파이프라인 실행 화면](assets/deploy-code2.png)

빌드 프로세스는 3단계로 코드를 배포합니다.

1. [스테이지 배포](#stage-deployment)
1. [단계 테스트](#stage-testing)
1. [프로덕션 배포](#production-deployment)

>[!TIP]
>
>테스트 기준에 대한 로그를 보거나 결과를 검토하여 다양한 배포 프로세스의 단계를 검토할 수 있습니다.

## 단계 배포 단계 {#stage-deployment}

다음 **스테이지 배포** 단계. 에는 다음 단계가 포함됩니다.

* **유효성 검사**  - 이 단계에서는 파이프라인이 현재 사용 가능한 리소스를 사용하도록 구성됩니다. 예: 구성된 분기가 있고 환경을 사용할 수 있는지 테스트합니다.
* **빌드 및 단위 테스트** - 이 단계에서는 컨테이너화된 빌드 프로세스를 실행합니다.
   * 문서 보기 [빌드 환경 세부 정보](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/build-environment-details.md) 빌드 환경에 대한 자세한 내용을 참조하십시오.
* **코드 스캔** - 이 단계에서는 애플리케이션 코드의 품질을 평가합니다.
   * 문서 보기 [코드 품질 테스트](/help/implementing/cloud-manager/code-quality-testing.md) 를 참조하십시오.
* **이미지 작성** - 이 프로세스는 빌드 단계에서 생성된 컨텐츠 및 디스패처 패키지를 Docker 이미지 및 Kubernetes 구성으로 변환해야 합니다.
* **스테이지에 배포** - 이미지를 준비할 때 스테이징 환경에 배포됩니다. [단계 테스트 단계입니다.](#stage-testing)

![스테이지 배포](assets/stage-deployment.png)

## 단계 테스트 단계 {#stage-testing}

다음 **단계 테스트** 단계에는 다음 단계가 포함됩니다.

* **제품 기능 테스트** - Cloud Manager 파이프라인은 스테이지 환경에 대해 실행되는 테스트를 실행합니다.
   * 문서를 참조하십시오 [제품 기능 테스트](/help/implementing/cloud-manager/functional-testing.md#product-functional-testing) 자세한 내용

* **사용자 지정 기능 테스트** - 파이프라인의 이 단계는 항상 실행되며 건너뛸 수 없습니다. 빌드에 의해 테스트 JAR이 생성되지 않으면 기본적으로 테스트가 전달됩니다.
   * 문서를 참조하십시오 [사용자 지정 기능 테스트](/help/implementing/cloud-manager/functional-testing.md#custom-functional-testing) 자세한 내용

* **사용자 지정 UI 테스트** - 이 단계는 사용자 지정 애플리케이션용으로 생성된 UI 테스트를 자동으로 실행하는 선택 기능입니다.
   * UI 테스트는 Docker 이미지에 패키지된 Selenium 기반 테스트로, Java 및 Maven, Node 및 WebDriver.io와 같은 다양한 언어 및 프레임워크(또는 Selenium을 기반으로 구축된 기타 프레임워크 및 기술)를 사용할 수 있습니다.
   * 문서를 참조하십시오 [사용자 지정 UI 테스트](/help/implementing/cloud-manager/functional-testing.md#custom-ui-testing) 자세한 내용

* **경험 감사** - 파이프라인의 이 단계는 항상 실행되며 건너뛸 수 없습니다. 프로덕션 파이프라인이 실행되면 검사를 실행하는 사용자 지정 기능 테스트 후 경험 감사 단계가 포함됩니다.
   * 구성된 페이지는 서비스에 제출되고 평가됩니다.
   * 결과는 정보 제공용이며 현재 점수와 이전 점수 간의 점수 및 변경 사항을 보여줍니다.
   * 이 통찰력은 현재 배포와 함께 도입될 회귀 여부를 판별하는 데 유용합니다.
   * 문서를 참조하십시오 [경험 감사 결과 이해](/help/implementing/cloud-manager/experience-audit-testing.md) 자세한 내용

![단계 테스트](assets/stage-testing.png)

## 프로덕션 배포 단계 {#deployment-production}

AEM 사이트에 방문자가 미치는 영향을 최소화하기 위해 프로덕션 토폴로지에 배포하는 프로세스는 약간 다릅니다.

프로덕션 배포는 일반적으로 이전에 설명한 것과 동일한 단계를 따르지만, 롤링 방식으로 수행합니다.

1. AEM 패키지를 작성자에게 배포합니다.
1. 로드 밸런서에서 dispatcher1을 분리합니다.
1. AEM 패키지를 배포하여 publish1 및 dispatcher 패키지를 dispatcher1에 배포하고 디스패처 캐시를 플러시합니다.
1. dispatcher1을 로드 밸런서에 다시 넣습니다.
1. dispatcher1이 다시 작동하면 로드 밸런서에서 dispatcher2를 분리합니다.
1. AEM 패키지를 배포하여 publish2 및 dispatcher 패키지를 dispatcher2에 배포하고 디스패처 캐시를 플러시합니다.
1. dispatcher2를 로드 밸런서에 다시 넣습니다.

이 프로세스는 배포가 토폴로지의 모든 게시자 및 dispatcher에 도달할 때까지 계속됩니다.

![프로덕션 배포 단계](assets/production-deployment.png)

## 시간 초과 {#timeouts}

다음 단계는 사용자 피드백을 기다리는 동안 시간이 초과됩니다.

| 단계 | 시간 초과 |
|--- |--- |
| 코드 품질 테스트 | 14일 |
| 보안 테스트 | 14일 |
| 성능 테스트 | 14일 |
| 승인 신청 | 14일 |
| 프로덕션 배포 예약 | 14일 |
| CSE 지원 | 14일 |

## 배포 프로세스 {#deployment-process}

모든 Cloud Service 배포은 롤링 프로세스에 따라 다운타임 없이 시스템을 구축할 수 있습니다. 문서를 참조하십시오 [롤링 배포 작동 방식](/help/implementing/deploying/overview.md#how-rolling-deployments-work) 추가 정보

>[!NOTE]
>
>Dispatcher 캐시가 각 배포에서 지워집니다. 그런 다음 새 게시 노드가 트래픽을 허용하기 전에 데워집니다.

## 프로덕션 배포 재실행 {#Reexecute-Deployment}

프로덕션 배포 단계의 재실행은 프로덕션 배포 단계가 완료된 실행에 대해 지원됩니다. 완료 유형은 중요하지 않습니다. 배포를 취소하거나 실패할 수 있습니다. 즉, 기본 사용 사례는 일시적인 이유로 프로덕션 배포 단계가 실패한 경우일 것입니다. 재실행은 동일한 파이프라인을 사용하여 새 실행을 만듭니다. 이 새로운 실행은 세 단계로 구성됩니다.

1. 유효성 검사 단계 - 이는 기본적으로 일반적인 파이프라인 실행 중에 발생하는 것과 동일한 유효성 검사입니다.
1. 빌드 단계 - 재실행 컨텍스트에서 빌드 단계는 새 빌드 프로세스를 실제로 실행하는 것이 아니라 아티팩트를 복사하는 것입니다.
1. 프로덕션 배포 단계 - 일반적인 파이프라인 실행에서 프로덕션 배포 단계와 동일한 구성 및 옵션을 사용합니다.

빌드 단계는 아티팩트를 다시 빌드하지 않고 복사하는 것임을 반영하도록 UI에서 약간 다르게 레이블이 지정될 수 있습니다.

![재배포](assets/Re-deploy.png)

제한 사항:

* 프로덕션 배포 단계를 다시 실행하는 것은 마지막 실행에서만 사용할 수 있습니다.
* 푸시 업데이트 실행에는 다시 실행할 수 없습니다. 마지막 실행이 푸시 업데이트 실행인 경우 다시 실행할 수 없습니다.
* 마지막 실행이 푸시 업데이트 실행인 경우 다시 실행할 수 없습니다.
* 프로덕션 배포 단계 이전의 어느 시점에서 마지막 실행이 실패한 경우 재실행이 불가능합니다.

### API 재실행 {#Reexecute-API}

### 재실행 실행 실행 식별

실행이 재실행 실행인지 확인하기 위해 트리거 필드를 검사할 수 있습니다. 값은 다음과 같습니다 *RE_EXECUTE*.

### 새 실행 트리거

재실행을 트리거하려면 HAL 링크 &lt;(<https://ns.adobe.com/adobecloud/rel/pipeline/reExecute>)> 를 클릭하여 제품에서 사용할 수 있습니다. 이 링크가 있으면 해당 단계에서 재실행할 수 있습니다. 없는 경우 해당 단계에서 실행을 다시 시작할 수 없습니다. 초기 릴리스에서는 이 링크가 프로덕션 배포 단계에만 존재하지만 이후 릴리스에서는 다른 단계에서 파이프라인을 시작할 수 있습니다. 예:

```Javascript
 {
  "_links": {
    "https://ns.adobe.com/adobecloud/rel/pipeline/logs": {
      "href": "/api/program/4/pipeline/1/execution/953671/phase/1575676/step/2983530/logs",
      "templated": false
    },
    "https://ns.adobe.com/adobecloud/rel/pipeline/reExecute": {
      "href": "/api/program/4/pipeline/1/execution?stepId=2983530",
      "templated": false
    },
    "https://ns.adobe.com/adobecloud/rel/pipeline/metrics": {
      "href": "/api/program/4/pipeline/1/execution/953671/phase/1575676/step/2983530/metrics",
      "templated": false
    },
    "self": {
      "href": "/api/program/4/pipeline/1/execution/953671/phase/1575676/step/2983530",
      "templated": false
    }
  },
  "id": "6187842",
  "stepId": "2983530",
  "phaseId": "1575676",
  "action": "deploy",
  "environment": "weretail-global-b75-prod",
  "environmentType": "prod",
  "environmentId": "59254",
  "startedAt": "2022-01-20T14:47:41.247+0000",
  "finishedAt": "2022-01-20T15:06:19.885+0000",
  "updatedAt": "2022-01-20T15:06:20.803+0000",
  "details": {
  },
  "status": "FINISHED"
```


HAL 링크의 구문 _href_  위의 값은 참조 지점으로 사용되지 않습니다. 실제 값은 항상 HAL 링크에서 읽어야 하며 생성되지 않아야 합니다.

제출 *PUT* 이 종단점에 대한 요청은 결과를 생성합니다. *201년* 응답이 성공하면 응답 본문이 새 실행을 나타냅니다. 이는 API를 통해 일반 실행을 시작하는 것과 유사합니다.
