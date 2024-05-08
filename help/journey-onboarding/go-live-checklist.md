---
title: 실행 체크리스트
description: AEM as a Cloud Service으로 Go-Live를 성공적으로 수행하기 위해 필요한 모든 요소에 대해 알아봅니다
source-git-commit: 4a03e2fe3519fd9e0d8d646526ea6c9cc6637f52
workflow-type: tm+mt
source-wordcount: '575'
ht-degree: 6%

---


# 실행 체크리스트 {#Go-Live-Checklist}

이 활동 목록을 검토하여 원활하고 성공적인 Go-Live를 수행하도록 하십시오.

* 기능 및 UI 테스트를 통해 엔드 투 엔드 프로덕션 파이프라인을 실행하여 **항상 최신** AEM 제품 경험입니다. 다음 리소스를 참조하십시오.
   * [AEM 버전 업데이트](/help/implementing/deploying/aem-version-updates.md)
   * [사용자 정의 기능 테스트](/help/implementing/cloud-manager/functional-testing.md#custom-functional-testing)
   * [UI 테스트](/help/implementing/cloud-manager/ui-testing.md)
* AEM 6.5에서 마이그레이션하는 경우 콘텐츠를 프로덕션으로 마이그레이션하고 스테이징에서 관련 하위 집합을 테스트용으로 사용할 수 있는지 확인해야 합니다.
   * AEM에 대한 DevOps 우수 사례는 코드가 개발 환경에서 프로덕션 환경으로 이동하는 반면 콘텐츠는 프로덕션 환경에서 이동하는 것을 의미합니다.
* 코드 및 컨텐츠 고정 기간을 예약합니다.
   * 섹션 참조 [마이그레이션에 대한 코드 및 컨텐츠 고정 타임라인](#code-content-freeze)
* 최종 컨텐츠 추가 작업을 수행합니다.
* Dispatcher 구성의 유효성을 검사합니다.
   * 로컬에서 Dispatcher 구성, 유효성 검사 및 시뮬레이션을 용이하게 하는 로컬 Dispatcher 유효성 검사기를 사용하십시오
      * [로컬 Dispatcher 도구를 설정합니다.](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/dispatcher-tools.html#prerequisites)
   * 가상 호스트 구성을 주의 깊게 검토하십시오.
      * 가장 쉬운(그리고 기본) 솔루션은 다음을 포함하는 것입니다. `ServerAlias *` 의 가상 호스트 파일에서 `/dispatcher/src/conf.d/available_vhostsfolder`.
         * 이렇게 하면 제품 기능 테스트, Dispatcher 캐시 무효화 및 클론이 사용하는 호스트 별칭이 작동할 수 있습니다.
      * 그러나 다음과 같은 경우에는 `ServerAlias *` 은(는) 허용되지 않으며, 최소한 다음과 같습니다 `ServerAlias` 사용자 정의 도메인 외에 항목을 허용해야 합니다.
         * `localhost`
         * `*.local`
         * `publish*.adobeaemcloud.net`
         * `publish*.adobeaemcloud.com`
* CDN, SSL 및 DNS를 구성합니다.
   * 자체 CDN을 사용하는 경우 지원 티켓을 입력하여 적절한 라우팅을 구성합니다.
      * 섹션 보기 [고객 CDN이 AEM Managed CDN을 가리킴](/help/implementing/dispatcher/cdn.md#point-to-point-cdn) 자세한 내용은 CDN 설명서 를 참조하십시오.
      * CDN 공급업체의 설명서에 따라 SSL 및 DNS를 구성합니다.
   * 추가 CDN을 사용하지 않는 경우 다음 설명서에 따라 SSL 및 DNS를 관리합니다.
      * SSL 인증서 관리
         * [SSL 인증서 관리 소개](/help/implementing/cloud-manager/managing-ssl-certifications/introduction.md)
         * [SSL 인증서 관리](/help/implementing/cloud-manager/managing-ssl-certifications/managing-certificates.md)
      * 사용자 정의 도메인 이름(DNS) 관리
         * DNS 컷오버로 예기치 않은 문제가 발생하지 않도록 하려면 Go-Live 및 UAT 테스트를 수행하기 전에 프로덕션 인스턴스를에 연결하는 테스트 하위 도메인을 만드는 것이 좋습니다. 따라서 도메인이 example.com이면 하위 도메인 test.example.com 을 만들어 프로덕션에 적용할 수 있습니다. 도메인을 UAT 테스트하는 동안 적절한 링크 리디렉션, 캐싱 및 Dispatcher 구성과 같은 것을 찾아야 합니다.
         * [사용자 정의 도메인 이름 소개](/help/implementing/cloud-manager/custom-domain-names/introduction.md)
         * [사용자 정의 도메인 이름 추가](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md)
         * [사용자 정의 도메인 이름 관리](/help/implementing/cloud-manager/custom-domain-names/managing-custom-domain-names.md)
   * DNS 레코드에 대한 TTL 집합의 유효성을 검사해야 합니다.
      * TTL은 서버에 업데이트를 요청하기 전에 DNS 레코드가 캐시에 남아 있는 시간입니다.
      * TTL이 매우 높은 경우 DNS 레코드 업데이트가 전파되는 데 시간이 더 오래 걸립니다.
* 비즈니스 요구 사항 및 목표를 충족하는 성능 및 보안 테스트를 실행합니다.
   * 스테이지 환경에서 테스트를 수행합니다.  이는 프로덕션 크기와 동일합니다.
   * 개발 환경의 크기가 단계 및 프로덕션과 동일하지 않습니다.
* 잘라내어 새로운 배포나 콘텐츠 업데이트 없이 실제 Go-Live가 수행되도록 하십시오.
* Admin Console 사용자 알림 프로필을 만듭니다. 다음을 참조하십시오 [알림 프로필](/help/journey-onboarding/notification-profiles.md)
* 웹 사이트에서 허용해서는 안 되는 트래픽을 제어하도록 트래픽 필터 규칙 을 구성하는 것이 좋습니다.
   * 속도 제한 트래픽 필터 규칙은 DDoS 공격에 효과적인 도구가 될 수 있습니다. WAF 규칙이라고 하는 특별한 범주의 트래픽 필터 규칙에는 별도의 라이센스가 필요합니다.
   * 자세한 내용은 설명서 를 참조하십시오 [제안된 시작 규칙](/help/security/traffic-filter-rules-including-waf.md#recommended-starter-rules).

Go-Live 중에 작업을 다시 수정해야 하는 경우 언제든지 목록을 참조할 수 있습니다.