---
title: Go-Live
description: 코드와 컨텐츠가 클라우드에 준비되면 마이그레이션을 수행하는 방법을 알아봅니다
exl-id: 10ec0b04-6836-4e26-9d4c-306cf743224e
source-git-commit: 6e5743a1b31cf4992e6477050e434a651153fad1
workflow-type: tm+mt
source-wordcount: '1729'
ht-degree: 1%

---

# Go-Live {#go-live}

>[!CONTEXTUALHELP]
>id="aemcloud_golive_prep"
>title="Go-Live 준비"
>abstract="AEM as a Cloud Service에서 유연하고 성공적인 go-live를 수행하려면 코드 및 컨텐츠 고정 기간, 테스트 반복, 컨텐츠 추가, 성능 테스트, 보안 테스트 등을 계획해야 합니다."

여정의 이 부분에서 코드와 컨텐츠가 AEM as a Cloud Service 으로 이동할 준비가 되면 마이그레이션을 계획하고 수행하는 방법을 알아봅니다. 또한 마이그레이션을 수행할 때 모범 사례와 알려진 제한 사항을 학습하게 됩니다.

## 지금까지의 이야기 {#story-so-far}

여정의 이전 단계에서

* AEM as a Cloud Service으로 이동하는 방법을 배웠습니다 [시작하기](/help/journey-migration/getting-started.md) 페이지.
* 을(를) 읽고 배포가 클라우드로 이동할 준비가 되었는지 확인했습니다. [준비 단계](/help/journey-migration/readiness.md)
* 코드 및 컨텐츠 클라우드를 및에 대비할 수 있는 도구와 프로세스에 대해 숙지하십시오. [구현 단계](/help/journey-migration/implementation.md).

## 목표 {#objective}

이 문서는 여정의 이전 단계를 잘 알고 있으면 AEM as a Cloud Service으로 마이그레이션을 수행하는 방법을 이해하는 데 도움이 됩니다. AEM as a Cloud Service으로 마이그레이션할 때 따라야 할 모범 사례와 초기 프로덕션 마이그레이션을 수행하는 방법을 배웁니다.

## 초기 프로덕션 마이그레이션 {#initial-migration}

프로덕션 마이그레이션을 수행하려면 먼저 아래에 요약된 마이그레이션 절차 및 증명을 따르십시오 [컨텐츠 마이그레이션 전략 및 타임라인](/help/journey-migration/implementation.md##strategy-timeline) 섹션 [구현 단계](/help/journey-migration/implementation.md).

* 클론에 대해 수행된 AEM as a Cloud Service 스테이지 마이그레이션 중에 얻은 경험을 기반으로 프로덕션에서 마이그레이션을 시작합니다.
   * Author-Author
   * Publish-Publish

* 수집된 컨텐츠를 AEM as a Cloud Service 작성자 및 게시 계층 모두에 확인합니다.
* 수집이 완료될 때까지 소스와 대상 모두에서 컨텐츠를 이동하지 않도록 컨텐츠 작성 팀에 지시합니다
* 새 컨텐츠는 추가, 편집 또는 삭제할 수 있지만 이동하지 않습니다. 이는 소스와 대상에 모두 적용됩니다.
* 레코드 [소요 시간](/help/journey-migration/implementation.md#gathering-data) 전체 추출 및 수집이 향후 추가 마이그레이션 타임라인에 대한 예측을 갖도록 합니다.
* 만들기 [마이그레이션 계획자](/help/journey-migration/implementation.md#migration-plan) 작성자 및 게시 모두에 대해 해당.

## 증분 추가 {#top-up}

프로덕션에서 처음 마이그레이션 후 클라우드 인스턴스에서 컨텐츠를 최신 상태로 전환하려면 증분 추가를 수행해야 합니다. 따라서 다음 우수 사례를 따르는 것이 좋습니다.

* 컨텐츠 양에 대한 데이터를 수집합니다. 예: 1주, 2주 또는 1개월마다
* 48시간 이상의 컨텐츠 추출 및 수집을 방지하기 위해 추가 작업을 계획해야 합니다. 컨텐츠 추가 작업이 주말 시간대에 맞게 수행되도록 하는 것이 좋습니다.
* 필요한 추가 수를 계획하고 이러한 추정치를 사용하여 Go-Live 날짜를 계획합니다.

## 마이그레이션에 대한 코드 및 컨텐츠 고정 타임라인 식별 {#code-content-freeze}

앞에서 설명한 바와 같이, 코드 및 컨텐츠 고정 기간을 예약해야 합니다. 고정 기간을 계획하는 데 도움이 되도록 다음 질문을 사용합니다.

* 컨텐츠 작성 활동을 동결하려면 얼마나 기다려야 합니까?
* 게재 팀에 새 기능 추가를 얼마 동안 중단하도록 요청해야 합니까?

첫 번째 질문에 답변하려면 비프로덕션 환경에서 평가판 실행을 수행하는 데 걸린 시간을 고려해야 합니다. 두 번째 질문에 답변하려면 새로운 기능을 추가하고 있는 팀과 코드를 리팩터링하는 팀 간의 긴밀한 공동 작업이 필요합니다. 목표는 기존 배포에 추가된 모든 코드가 클라우드 서비스 분기에 추가, 테스트 및 배포되는지 확인하는 것입니다. 일반적으로 말해서, 이는 코드 동결의 양이 줄어든다는 것을 의미합니다.

또한 최종 컨텐츠 추가 작업이 예약될 때 컨텐츠가 동결되도록 계획해야 합니다.

## 모범 사례 {#best-practices}

마이그레이션을 계획하거나 수행할 때 다음 지침을 고려해야 합니다.

* 작성자에서 작성자로 마이그레이션 및 게시로 게시
* 다음 작업에 사용할 수 있는 운영 클론을 요청합니다.
   * 저장소 통계 캡처
   * 마이그레이션 활동 증명
   * 마이그레이션 계획 준비
   * 컨텐츠 고정 요구 사항 식별
   * 프로덕션에서 마이그레이션을 수행할 때 프로덕션에서 업사이징 요구 사항을 모두 파악합니다

**컨텐츠 전송 도구 우수 사례**

라이브로 전환할 때 클론 대신 프로덕션에서 컨텐츠 마이그레이션을 실행해야 합니다. 좋은 접근 방법은 [AZCopy](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/handling-large-content-repositories.md) 초기 마이그레이션의 경우 를 실행한 다음 추가 추출을 자주(심지어 매일) 실행하여 더 작은 청크를 추출하고 소스 AEM에서 장기 로드를 방지합니다.

프로덕션 마이그레이션을 수행할 때는 다음 이유로 클론에서 컨텐츠 전송 도구를 실행하지 않아야 합니다.

* 고객이 추가 마이그레이션 중에 컨텐츠 버전을 마이그레이션해야 하는 경우 클론에서 컨텐츠 전송 도구를 실행해도 버전이 마이그레이션되지 않습니다. 클론이 라이브 작성자로부터 자주 다시 생성되더라도 클론이 생성될 때마다 컨텐츠 전송 도구에서 델타를 계산하기 위해 사용할 체크포인트가 재설정됩니다.
* 클론을 전체적으로 새로 고칠 수 없으므로 프로덕션에서 클론으로 추가하거나 편집할 컨텐츠를 패키징하여 설치하는 데 ACL 쿼리 패키지를 사용해야 합니다. 이 접근 방식의 문제는 소스 인스턴스에서 삭제된 컨텐츠가 소스 및 클론에서 수동으로 삭제되지 않으면 소스 인스턴스에서 클론이 전송되지 않는다는 것입니다. 이렇게 하면 운영 중인 삭제된 컨텐츠가 클론 및 AEM as a Cloud Service에서 삭제되지 않을 수 있습니다.

**컨텐츠 마이그레이션을 수행하는 동안 AEM 소스에서 로드 최적화**

AEM 소스의 부하가 추출 단계 중에 더 크게 된다는 것을 기억하십시오. 다음 사항을 알고 있어야 합니다.

* 컨텐츠 전송 도구는 4GB의 JVM 힙을 사용하는 외부 Java 프로세스입니다
* AzCopy가 아닌 버전은 바이너리를 다운로드하고 소스 AEM 작성자의 임시 공간에 저장한 다음 디스크 I/O를 사용한 Azure 컨테이너로 업로드합니다
* [AzCopy](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/handling-large-content-repositories.md) blob를 blob 저장소에서 Azure 컨테이너로 직접 전송하여 디스크 I/O 및 네트워크 대역폭을 저장합니다. AzCopy 버전은 여전히 디스크 및 네트워크 대역폭을 사용하여 세그먼트 저장소에서 Azure 컨테이너로 데이터를 추출하고 업로드합니다
* 컨텐츠 전송 도구 프로세스는 수집 로그만 스트리밍하고 디스크 I/O 또는 네트워크 대역폭에 관한 한 소스 인스턴스에 많은 로드가 없으므로 수집 단계 동안 시스템 리소스에 대한 부담이 적습니다.

## 알려진 제한 사항 {#known-limitations}

추출된 마이그레이션 세트의 일부로 다음 제한 사항이 발견되면 전체 수집이 실패함을 고려하십시오.

* 이름이 150자를 초과하는 JCR 노드
* 16MB보다 큰 JCR 노드
* 다음을 사용하는 모든 사용자/그룹 `rep:AuthorizableID` AEM as a Cloud Service에 이미 있는 수집 중
* 추출 및 수집된 자산이 마이그레이션의 다음 반복 전에 소스 또는 대상의 다른 경로로 이동하는 경우.

## 자산 상태 {#asset-health}

섭취 위의 섹션과 비교 **포함하지 않음** 다음 자산 문제로 인해 실패합니다. 그러나 다음 시나리오에서는 적절한 단계를 수행하는 것이 좋습니다.

* 원본 표현물이 없는 모든 자산
* 누락된 폴더가 있는 모든 폴더 `jcr:content` 노드

위의 두 항목은 모두 [모범 사례 분석기](/help/journey-migration/best-practices-analyzer/overview-best-practices-analyzer.md) 보고서 세트에 대해 설명합니다.

## Go-Live 체크리스트 {#Go-Live-Checklist}

이 활동 목록을 검토하여 마이그레이션이 원활하고 성공했는지 확인하십시오.

* 기능 및 UI 테스트를 통해 종단 간 프로덕션 파이프라인을 실행하여 **항상 전류** AEM 제품 경험. 다음 리소스를 참조하십시오.
   * [AEM 버전 업데이트](/help/implementing/deploying/aem-version-updates.md)
   * [사용자 지정 기능 테스트](/help/implementing/cloud-manager/functional-testing.md#custom-functional-testing)
   * [UI 테스트](/help/implementing/cloud-manager/ui-testing.md)
* 컨텐츠를 프로덕션으로 마이그레이션하고 테스트용 스테이징에서 관련 하위 집합을 사용할 수 있는지 확인하십시오.
   * AEM에 대한 DevOps 우수 사례에서는 컨텐츠가 프로덕션 환경에서 아래로 이동하는 동안 코드가 개발 환경에서 프로덕션 환경으로 이동한다는 점을 참고하십시오.
* 코드 및 컨텐츠 고정 기간을 예약합니다.
   * 섹션을 참조하십시오 [마이그레이션을 위한 코드 및 컨텐츠 고정 타임라인](#code-content-freeze)
* 최종 컨텐츠 추가 를 수행합니다.
* Dispatcher 구성의 유효성을 검사합니다.
   * 로컬 Dispatcher 유효성 검사기를 사용하여 Dispatcher를 로컬에서 구성, 유효성 검사 및 시뮬레이션을 용이하게 합니다.
      * [로컬 Dispatcher 도구를 설정합니다.](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/dispatcher-tools.html?lang=en#prerequisites)
   * 가상 호스트 구성을 신중하게 검토하십시오.
      * 가장 쉬운(및 기본) 솔루션은 다음과 같습니다 `ServerAlias *` 가상 호스트 파일에서 `/dispatcher/src/conf.d/available_vhostsfolder`.
         * 이렇게 하면 제품 기능 테스트, 디스패처 캐시 무효화 및 클론에 사용되는 호스트 별칭이 작동할 수 있습니다.
      * 그러나 `ServerAlias *` 은(는) 허용되지 않으며, 최소한 다음 `ServerAlias` 사용자 지정 도메인 외에 항목을 사용할 수 있어야 합니다.
         * `localhost`
         * `*.local`
         * `publish*.adobeaemcloud.net`
         * `publish*.adobeaemcloud.com`
* CDN, SSL 및 DNS를 구성합니다.
   * 고유한 CDN을 사용하는 경우 지원 티켓을 입력하여 적절한 라우팅을 구성합니다.
      * 섹션을 참조하십시오 [고객 CDN은 AEM Managed CDN을 가리킵니다](/help/implementing/dispatcher/cdn.md#point-to-point-cdn) 참조하십시오.
      * CDN 공급업체의 설명서에 따라 SSL 및 DNS를 구성해야 합니다.
   * 추가 CDN을 사용하지 않는 경우 다음 설명서에 따라 SSL 및 DNS를 관리합니다.
      * SSL 인증서 관리
         * [SSL 인증서 관리 소개](/help/implementing/cloud-manager/managing-ssl-certifications/introduction.md)
         * [SSL 인증서 관리](/help/implementing/cloud-manager/managing-ssl-certifications/managing-certificates.md)
      * DNS(사용자 지정 도메인 이름) 관리
         * DNS 컷오버에서 예기치 않은 문제가 발생하지 않도록 하려면 라이브로 전환하고 UAT 테스트 라운드를 수행하기 전에 프로덕션 인스턴스를 연결하는 테스트 하위 도메인을 만드는 것이 가장 좋습니다. 따라서 도메인이 example.com인 경우 하위 도메인 test.example.com 을 만들어 프로덕션에 적용할 수 있습니다. 도메인을 UAT로 테스트하는 동안 적절한 링크 리디렉션, 캐싱 및 디스패처 구성과 같은 사항을 찾을 수 있습니다.
         * [사용자 지정 도메인 이름 소개](/help/implementing/cloud-manager/custom-domain-names/introduction.md)
         * [맞춤형 도메인 이름 추가](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md)
         * [사용자 지정 도메인 이름 관리](/help/implementing/cloud-manager/custom-domain-names/managing-custom-domain-names.md)
   * DNS 레코드에 대한 TTL 집합의 유효성을 검사해야 합니다.
      * TTL은 서버에서 업데이트를 요청하기 전에 DNS 레코드가 캐시에 남아 있는 시간입니다.
      * 매우 높은 TTL을 갖는 경우 DNS 레코드에 대한 업데이트를 전파하는 데 시간이 오래 걸립니다.
* 비즈니스 요구 사항 및 목표를 충족하는 성능 및 보안 테스트를 실행합니다.
* 마우스를 가져간 후 새 배포나 콘텐츠 업데이트 없이 실제 Go-Live가 수행되었는지 확인합니다.
* Admin Console 사용자 알림 그룹을 만듭니다. 자세한 내용은 [알림에 대한 사용자 그룹](/help/journey-onboarding/user-groups.md)

마이그레이션을 수행하는 동안 작업을 재조정해야 하는 경우 언제든지 목록을 참조할 수 있습니다.

## 다음 단계 {#what-is-next}

AEM as a Cloud Service로의 마이그레이션을 수행하는 방법을 이해하면 다음을 확인할 수 있습니다 [Go-Live 후](/help/journey-migration/post-go-live.md) 페이지를 사용하여 인스턴스를 원활하게 실행할 수 있습니다.
