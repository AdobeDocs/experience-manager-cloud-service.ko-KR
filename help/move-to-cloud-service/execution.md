---
title: 실행 단계
description: 실행 단계
translation-type: tm+mt
source-git-commit: 3478827949356c4a4f5133b54c6cf809f416efef
workflow-type: tm+mt
source-wordcount: '1020'
ht-degree: 4%

---


# 실행 {#execution-phase}

실행 단계를 시작하기 전에 Cloud Service에 온보드 방식으로 연결되어 있어야 합니다. 또한 AEM Cloud Service에 코드를 배포하는 유일한 메커니즘인 Cloud Manager에 익숙해져야 합니다.

클라우드 관리자를 사용하면 조직에서 클라우드에서 AEM을 자체 관리할 수 있습니다. IT팀 및 구현 파트너가 성능 또는 보안을 손상하지 않고 사용자 지정 내용 또는 업데이트를 신속하게 전달할 수 있는 CI/CD(지속적 통합 및 지속적 배포) 프레임워크가 포함되어 있습니다.

자세한 내용은 아래 리소스를 참조하십시오.

* [클라우드 서비스로서 Experience Manager의 온보딩에 대한 자체 도움말 리소스를 파악하기](https://docs.adobe.com/content/help/ko-KR/experience-manager-cloud-service/onboarding/home.html) 위해 Experience Manager에 온보딩을 제공합니다.

* [Git과 Adobe Cloud Manager](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/implementing/managing-code/integrating-with-git.html) 통합을 통해 단일 Git 리포지토리를 사용하여 코드 배포에 대한 자세한 내용을 살펴볼 수 있습니다.

* [Adobe Experience as a Cloud Service Configuration](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/security/ims-support.html#aem-configuration) to learn about Managing Products and User Access in Admin Console.


## 소개 {#introduction}

Cloud Service로 전환하는 정확한 단계는 구입한 시스템과 사용자가 따르는 소프트웨어 개발 라이프사이클 방침에 따라 다릅니다.

다음 그림은 실행 단계에 관련된 주요 단계를 보여줍니다.

![이미지](/help/move-to-cloud-service/assets/exec-image1.png)

## 컨텐츠 전송 {#content-transfer}

현재 AEM 인스턴스의 콘텐츠를 클라우드 서비스 인스턴스로 전송하려면 Adobe의 콘텐츠 전송 도구를 사용할 수 있습니다.

이 도구를 사용하여 소스 AEM 인스턴스에서 AEM Cloud 서비스 인스턴스로 전송할 원하는 컨텐츠 하위 집합을 지정할 수 있습니다.

>[!NOTE]
>Cloud Service에서 라이브하기 전에 마지막으로 차등 컨텐츠 전송에 대한 컨텐츠 고정 기간을 줄이려면 자주 차등 컨텐츠 상위를 수행하는 것이 좋습니다.

자세한 내용은 [컨텐츠 전송](/help/move-to-cloud-service/content-transfer-tool/overview-content-transfer-tool.md) 도구를 참조하십시오.

>[!IMPORTANT]
>컨텐츠 전송 도구에 대한 최소 시스템 요구 사항은 AEM 6.3 + 및 JAVA 8입니다. 더 낮은 AEM 버전을 사용하는 경우 콘텐츠 저장소를 AEM 6.5로 업그레이드하여 콘텐츠 전송 도구를 사용해야 합니다.

## 코드 리팩토링 {#code-refactor}

클라우드 서비스로 AEM에서 코드를 개발 및 실행하려면 마인드 세트가 필요합니다. 특히 인스턴스가 언제든지 중지될 수 있으므로 코드는 복원력이 있어야 합니다. 클라우드 서비스에서 실행 중인 코드는 항상 클러스터에서 실행 중임을 알고 있어야 합니다. 즉, 실행되는 인스턴스가 두 개 이상 있습니다.

AEM Maven 프로젝트가 클라우드 서비스로 AEM과 호환되도록 하려면 특정 변경 사항이 필요합니다. 클라우드 서비스로서 AEM을 사용하려면 *컨텐츠* 및 *코드를 개별 패키지로 분리해야* AEM에 배포할 수 있습니다.

* `/apps` 및 `/libs` 는 AEM이 시작된 후(예: 런타임 시) 변경(만들기, 업데이트, 삭제)할 수 없으므로 AEM에서 변경할 수 없는 영역으로 간주됩니다. 실행 시 변경할 수 없는 영역을 변경하려는 시도가 실패합니다.

* 저장소의 다른 모든 것, `/content` , `/conf` `/var` , `/home` , `/etc` , `/oak:index` , `/system` , `/tmp` ,, 등에 있습니다. 은 모두 변경할 수 있는 영역이므로 런타임 시 변경할 수 있습니다.

자세한 내용은 [권장](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/implementing/developing/aem-project-content-package-structure.html#recommended-package-structure) 패키지 구조를 참조하십시오.

클라우드 서비스로 AEM에서 개발할 때 알아야 할 몇 가지 추가 개발 가이드라인이 있습니다. 자세한 내용은 [AEM을 클라우드 서비스 개발 가이드라인으로](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/implementing/developing/development-guidelines.html) 참조하십시오.

계획 단계에서 클라우드 서비스와 호환되도록 리팩토링해야 하는 영역 목록이 있어야 합니다. 또한 [개발 가이드라인을](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/implementing/developing/development-guidelines.html) 검토하여 Cloud Service로 전환하기 위해 코드를 리팩터링 및 최적화하는 방법에 대한 자세한 내용을 살펴보십시오.

코드 리팩토링 작업 중 일부를 가속화하기 위해 다음 도구를 사용할 수 있습니다.

* [자산 워크플로우 마이그레이션](/help/move-to-cloud-service/moving-to-aem-assets/asset-workflow-migration-tool.md)
* [Dispatcher Converter](/help/move-to-cloud-service/refactoring-tools/dispatcher-transformation-utility-tools.md)
* [최신 툴](/help/move-to-cloud-service/refactoring-tools/aem-modernization-tools.md)

Cloud Manager Git을 통해 클라우드 서비스 환경에 코드를 푸시하기 전에 로컬로 리팩터링하고 테스트하는 것이 좋습니다.

자세한 [내용은 AEM SDK](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/implementing/deploying/overview.html#aem-as-a-cloud-service-sdk) 설명서를 참조하십시오.

다음은 일부 추가 리소스입니다.

* Dispatcher SDK를 설치하여 Dispatcher SDK를 설치하는 방법을 알아보십시오.

   > [!VIDEO](https://video.tv.adobe.com/v/30601)

* Dispatcher SDK 구성:

   > [!VIDEO](https://video.tv.adobe.com/v/30602)

* 로컬 [개발 설정](https://docs.adobe.com/content/help/en/experience-manager-learn/cloud-service/local-development-environment-set-up/overview.html) 설명서를 검토하여 로컬 개발 환경 설정


전환 과정의 일부로 코드 리팩토링 작업과 함께 활성 AEM에서 진행 중인 코드 개발을 관리하려면, AEM과 클라우드 서비스로 호환되도록 Maven 프로젝트를 재구조화하지 않는 한 코드 정지 기간을 예약하는 것이 좋습니다.

프로젝트 구조조정이 완료되면 이 새로운 구조를 바탕으로 새로운 코드 개발을 재개할 수 있습니다. 이렇게 하면 코드 배포 및 테스트 중 Cloud Manager 파이프라인 오류가 줄어듭니다.

>[!NOTE]
>컨텐츠 전송 및 코드 리팩터 작업은 순차적으로 수행되지 않았습니다. 이러한 작업은 서로 독립적으로 수행할 수 있습니다. 그러나 콘텐츠가 클라우드 서비스 환경에서 성공적으로 렌더링되도록 하려면 올바른 프로젝트 구조가 필요합니다.

## 코드 배포 및 테스트 모범 사례 {#best-practices}

Cloud Manager for Cloud Services 파이프라인 실행은 스테이지 환경에 대해 실행되는 테스트 실행을 지원합니다.

테스트 스크립트 작성 및 최소 50%의 권장 적용 범위에 대해 알려면 [코드 품질 테스트를](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/implementing/developing/understand-test-results.html#code-quality-testing) 참조하십시오.

또한 AEM Engineering의 [우수 사례를 기반으로 만들어진 Cloud Manager에서 실행되는 사용자 지정 코드 품질 규칙에](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/implementing/using-cloud-manager/custom-code-quality-rules.html) 대한 자세한 내용은 사용자 지정 코드 품질 규칙 이해를 참조하십시오.

클라우드 관리자 사용은 클라우드 서비스 환경에 코드를 배포하는 유일한 메커니즘입니다.

아래 리소스를 참고하여 Cloud Manager를 사용하여 코드를 관리하고 배포하는 방법을 살펴보십시오.

* [환경 관리](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/implementing/using-cloud-manager/manage-environments.html)

* [CI-CD 파이프라인 구성](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/implementing/using-cloud-manager/configure-pipeline.html)

* [코드 배포](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/implementing/using-cloud-manager/deploy-code.html)

## 실시간 준비 모범 사례 {#go-live}

AEM을 클라우드 서비스로 매끄럽고 성공적인 go-live로 만들려면 다음 단계를 실행하는 것이 좋습니다.

* 코드 및 컨텐츠 고정 기간 예약
* 최종 컨텐츠 팝업 수행
* 전체 테스트 반복
* 성능 및 보안 테스트 실행
* 잘라내기
