---
title: 실행 단계
description: 실행 단계
translation-type: tm+mt
source-git-commit: 0dd05c1f6dc197daf154d4df6e6661e00455b233
workflow-type: tm+mt
source-wordcount: '1020'
ht-degree: 100%

---


# 실행 {#execution-phase}

실행 단계를 시작하기 전에 클라우드 서비스에 온보드해야 합니다. 또한 AEM Cloud Service에 코드를 배포하는 유일한 메커니즘이므로 Cloud Manager를 숙지해야 합니다.

조직에서 Cloud Manager를 사용하여 클라우드에서 AEM을 자체 관리할 수 있습니다. IT팀 및 구현 파트너가 성능 또는 보안을 손상하지 않고 사용자 지정 내용 또는 업데이트를 신속하게 전달할 수 있는 CI/CD(지속적 통합 및 지속적 배포) 프레임워크가 포함되어 있습니다.

자세한 내용은 아래 리소스를 참조하십시오.

* [Experience Manager as a Cloud Service에 온보딩](https://docs.adobe.com/content/help/ko-KR/experience-manager-cloud-service/onboarding/home.html): Experience Manager as a Cloud Service에 온보딩에 대한 셀프 헬프 리소스를 이해합니다.

* [Git와 Adobe Cloud Manager 통합](https://docs.adobe.com/content/help/ko-KR/experience-manager-cloud-service/implementing/managing-code/integrating-with-git.html): 단일 Git 저장소를 사용하여 코드 배포에 대해 자세히 알아봅니다.

* [Adobe Experience as a Cloud Service 구성](https://docs.adobe.com/content/help/ko-KR/experience-manager-cloud-service/security/ims-support.html#aem-configuration): Admin Console에서 제품 및 사용자 액세스 관리에 대해 알아봅니다.


## 소개 {#introduction}

클라우드 서비스로 전환하는 정확한 단계는 구입한 시스템과 사용자가 따르는 소프트웨어 개발 수명 주기 방침에 따라 다릅니다.

다음 그림은 실행 단계에 관련된 주요 단계를 보여줍니다.

![이미지](/help/move-to-cloud-service/assets/exec-image1.png)

## 컨텐츠 전송 {#content-transfer}

현재 AEM 인스턴스의 컨텐츠를 클라우드 서비스 인스턴스로 전송하기 위해 Adobe의 컨텐츠 전송 도구를 사용할 수 있습니다.

이 도구를 사용하여 소스 AEM 인스턴스에서 AEM 클라우드 서비스 인스턴스로 전송하려는 컨텐츠 하위 집합을 지정할 수 있습니다.

>[!NOTE]
>클라우드 서비스에서 라이브로 전환되기 전에 최종 차등 컨텐츠 전송에 대한 컨텐츠 고정 기간을 단축하기 위해 자주 차등 컨텐츠 추가를 수행하는 것이 좋습니다.

자세한 내용은 [컨텐츠 전송 도구](/help/move-to-cloud-service/content-transfer-tool/overview-content-transfer-tool.md)를 참조하십시오.

>[!IMPORTANT]
>컨텐츠 전송 도구의 최소 시스템 요구 사항은 AEM 6.3 이상 및 JAVA 8입니다. 더 낮은 AEM 버전을 사용하는 경우 컨텐츠 저장소를 AEM 6.5로 업그레이드해야 컨텐츠 전송 도구를 사용할 수 있습니다.

## 코드 리팩터링 {#code-refactor}

AEM as a Cloud Service에서 코드를 개발하고 실행하려면 사고방식을 변경해야 합니다. 특히 인스턴스가 언제든지 중지될 수 있으므로 코드가 복원력이 있어야 합니다. 클라우드 서비스에서 실행 중인 코드는 항상 클러스터에서 실행되고 있다는 것을 알고 있어야 합니다. 즉, 실행되는 인스턴스가 항상 두 개 이상 있습니다.

AEM Maven 프로젝트가 AEM as a Cloud Service와 호환되도록 하려면 특정 변경이 필요합니다. AEM as a Cloud Service를 사용하려면 AEM에 배포할 수 있도록 *컨텐츠*&#x200B;와 *코드*&#x200B;를 개별 패키지로 분리해야 합니다.

* `/apps` 및 `/libs`는 AEM이 시작된 후(예: 런타임 시) 변경(만들기, 업데이트, 삭제)할 수 없으므로 AEM에서 변경할 수 없는 영역으로 간주됩니다. 런타임 시 변경할 수 없는 영역을 변경하려고 하면 오류가 발생합니다.

* 저장소에서 `/content` , `/conf` , `/var` , `/home` , `/etc` , `/oak:index` , `/system` , `/tmp` 등은 모두 변경할 수 있는 영역입니다. 즉, 런타임 시 변경될 수 있습니다.

자세한 내용은 [권장 패키지 구조](https://docs.adobe.com/content/help/ko-KR/experience-manager-cloud-service/implementing/developing/aem-project-content-package-structure.html#recommended-package-structure)를 참조하십시오.

AEM as a Cloud Service를 개발할 때 알고 있어야 할 몇 가지 추가 개발 지침이 있습니다. 자세한 내용은 [AEM as a Cloud Service 개발 지침](https://docs.adobe.com/content/help/ko-KR/experience-manager-cloud-service/implementing/developing/development-guidelines.html)을 참조하십시오.

계획 단계에서 클라우드 서비스와 호환되도록 리팩터링해야 하는 영역 목록이 있어야 합니다. 또한 [개발 지침](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/implementing/developing/development-guidelines.html)에서 클라우드 서비스로 이동하기 위해 코드를 리팩터링 및 최적화하는 방법에 대한 자세한 내용을 검토해야 합니다.

코드 리팩터링 작업 중 일부를 가속화하기 위해 다음 도구를 사용할 수 있습니다.

* [자산 워크플로우 마이그레이션](/help/move-to-cloud-service/moving-to-aem-assets/asset-workflow-migration-tool.md)
* [Dispatcher 변환기](/help/move-to-cloud-service/refactoring-tools/dispatcher-transformation-utility-tools.md)
* [현대화 도구](/help/move-to-cloud-service/refactoring-tools/aem-modernization-tools.md)

Cloud Manager Git을 통해 코드를 클라우드 서비스 환경에 푸시하기 전에 로컬로 리팩터링하고 테스트하는 것이 좋습니다.

자세한 내용은 [AEM SDK](https://docs.adobe.com/content/help/ko-KR/experience-manager-cloud-service/implementing/deploying/overview.html#aem-as-a-cloud-service-sdk) 설명서를 참조하십시오.

다음은 몇 가지 추가 리소스입니다.

* Dispatcher SDK 설치를 시청하고 Dispatcher SDK를 설치하는 방법을 알아보십시오.

   >[!VIDEO](https://video.tv.adobe.com/v/30601)

* Dispatcher SDK 구성을 시청하고 Dispatcher SDK를 구성하는 방법을 알아보십시오.

   >[!VIDEO](https://video.tv.adobe.com/v/30602)

* [로컬 개발 설정](https://docs.adobe.com/content/help/en/experience-manager-learn/cloud-service/local-development-environment-set-up/overview.html) 설명서를 검토하여 로컬 개발 환경을 설정하는 방법을 알아보십시오.


전환 여정의 일부로 코드 리팩터링 작업과 함께 활성 AEM에서 진행 중인 코드 개발을 관리하려면, AEM as a Cloud Service와 호환되도록 Maven 프로젝트 재구성을 완료할 때까지 코드 동결 기간을 예약하는 것이 좋습니다.

프로젝트 재구성이 완료되면 이 새 구조를 바탕으로 새로운 코드 개발을 재개할 수 있습니다. 이렇게 하면 코드 배포 및 테스트 중 Cloud Manager 파이프라인 오류가 줄어듭니다.

>[!NOTE]
>컨텐츠 전송 및 코드 리팩터링 작업은 순차적으로 수행하지 않아도 됩니다. 이러한 작업은 서로 독립적으로 수행할 수 있습니다. 그러나 컨텐츠가 클라우드 서비스 환경에서 성공적으로 렌더링되도록 하려면 올바른 프로젝트 구조가 필요합니다.

## 코드 배포 및 테스트 우수 사례 {#best-practices}

클라우드 서비스에 대한 Cloud Manager 파이프라인 실행은 스테이지 환경에서 실행되는 테스트 실행을 지원합니다.

테스트 스크립트 작성 및 최소 50%의 권장 적용 범위에 대해 알아보려면 [코드 품질 테스트](https://docs.adobe.com/content/help/ko-KR/experience-manager-cloud-service/implementing/developing/understand-test-results.html#code-quality-testing)를 참조하십시오.

또한 AEM Engineering의 우수 사례를 기반으로 작성된 Cloud Manager에서 실행되는 사용자 지정 코드 품질 규칙에 대한 자세한 내용은 [사용자 지정 코드 품질 규칙 이해](https://docs.adobe.com/content/help/ko-KR/experience-manager-cloud-service/implementing/using-cloud-manager/custom-code-quality-rules.html)를 참조하십시오.

Cloud Manager 사용은 클라우드 서비스 환경에 코드를 배포하는 유일한 메커니즘입니다.

아래 리소스를 참조하여 Cloud Manager를 사용하여 코드를 관리하고 배포하는 방법을 알아보십시오.

* [환경 관리](https://docs.adobe.com/content/help/ko-KR/experience-manager-cloud-service/implementing/using-cloud-manager/manage-environments.html)

* [CI-CD 파이프라인 구성](https://docs.adobe.com/content/help/ko-KR/experience-manager-cloud-service/implementing/using-cloud-manager/configure-pipeline.html)

* [코드 배포](https://docs.adobe.com/content/help/ko-KR/experience-manager-cloud-service/implementing/using-cloud-manager/deploy-code.html)

## Go-Live 준비 우수 사례 {#go-live}

AEM as a Cloud Service에서 유연하고 성공적인 go-live를 수행하려면 다음 단계를 실행하는 것이 좋습니다.

* 코드 및 컨텐츠 고정 기간 예약
* 최종 컨텐츠 추가 수행
* 전체 테스트 반복
* 성능 및 보안 테스트 실행
* 잘라내기
