---
title: 실행 체크리스트
description: AEM as a Cloud Service에서 성공적인 실행을 위해 갖춰야 할 모든 요소에 대해 알아보기
exl-id: b424a9db-0f3b-4a8d-be84-365d68df46ca
feature: Onboarding
role: Admin, User, Developer
source-git-commit: 646ca4f4a441bf1565558002dcd6f96d3e228563
workflow-type: ht
source-wordcount: '575'
ht-degree: 100%

---

# 실행 체크리스트 {#Go-Live-Checklist}

원활하고 성공적인 성공을 수행하려면 이 활동 목록을 검토하십시오.

* 기능 및 UI 테스트를 통해 엔드투엔드 프로덕션 파이프라인을 실행하여 AEM 제품 경험을 **항상 최신 상태**&#x200B;로 유지합니다. 다음 리소스를 참조하십시오.
   * [AEM 버전 업데이트](/help/implementing/deploying/aem-version-updates.md)
   * [사용자 정의 기능 테스트](/help/implementing/cloud-manager/functional-testing.md#custom-functional-testing)
   * [UI 테스트](/help/implementing/cloud-manager/ui-testing.md)
* AEM 6.5에서 마이그레이션하는 경우 콘텐츠를 프로덕션으로 마이그레이션하고, 테스트를 위해 스테이징에서 관련 하위 세트를 사용할 수 있는지 확인해야 합니다.
   * AEM에 대한 DevOps 모범 사례는 콘텐츠가 프로덕션 환경에서 아래로 이동하는 동안 코드가 개발에서 프로덕션 환경으로, 즉 위로 이동한다는 것을 의미합니다.
* 코드 및 컨텐츠 고정 기간을 예약합니다.
   * [마이그레이션을 위한 코드 및 콘텐츠 고정 기간 일정](#code-content-freeze) 섹션도 참조하십시오.
* 최종 콘텐츠 추가를 수행합니다.
* Dispatcher 구성의 유효성을 검사합니다.
   * 로컬에서 Dispatcher 구성, 유효성 검사 및 시뮬레이션을 용이하게 하는 로컬 Dispatcher 유효성 검사기를 사용합니다.
      * [로컬 Dispatcher 도구를 설정](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/dispatcher-tools.html#prerequisites)합니다.
   * 가상 호스트 구성을 주의 깊게 검토합니다.
      * 가장 쉬운(기본) 솔루션은 `ServerAlias *`를 `/dispatcher/src/conf.d/available_vhostsfolder`의 가상 호스트 파일에 포함시키는 것입니다.
         * 이렇게 하면 제품 기능 테스트, Dispatcher 캐시 무효화 및 클론 작동에 사용되는 호스트 별칭이 허용됩니다.
      * 그러나 `ServerAlias *`가 허용되지 않는 경우 사용자 정의 도메인 외에 최소한 다음 `ServerAlias` 항목을 허용해야 합니다.
         * `localhost`
         * `*.local`
         * `publish*.adobeaemcloud.net`
         * `publish*.adobeaemcloud.com`
* CDN, SSL 및 DNS를 구성합니다.
   * 자체 CDN을 사용하는 경우 지원 티켓을 입력하여 적절한 라우팅을 구성합니다.
      * 자세한 내용은 CDN 설명서의 [고객 CDN은 AEM Managed CDN에 지정](/help/implementing/dispatcher/cdn.md#point-to-point-cdn) 섹션을 참조하십시오.
      * CDN 공급업체의 설명서에 따라 SSL 및 DNS를 구성합니다.
   * 추가 CDN을 사용하지 않는 경우 다음 문서에 따라 SSL 및 DNS를 관리합니다.
      * SSL 인증서 관리
         * [SSL 인증서 관리 소개](/help/implementing/cloud-manager/managing-ssl-certifications/introduction.md)
         * [SSL 인증서 관리](/help/implementing/cloud-manager/managing-ssl-certifications/managing-certificates.md)
      * 맞춤형 도메인 이름(DNS) 관리
         * DNS 컷오버로 인해 예기치 않은 문제가 발생하지 않도록 하려면 실행 후 UAT 테스트를 수행하기 전에 프로덕션 인스턴스를 연결할 테스트 하위 도메인을 만드는 것이 가장 좋습니다. 즉, 도메인이 example.com인 경우 하위 도메인 test.example.com을 만들어 프로덕션에 적용할 수 있습니다. 도메인의 UAT 테스트 중에 적절한 링크 리디렉션, 캐싱 및 Dispatcher 구성과 같은 항목을 찾아 보는 것이 좋습니다.
         * [사용자 정의 도메인 이름 소개](/help/implementing/cloud-manager/custom-domain-names/introduction.md)
         * [사용자 정의 도메인 이름 추가](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md)
         * [사용자 정의 도메인 이름 관리](/help/implementing/cloud-manager/custom-domain-names/managing-custom-domain-names.md)
   * DNS 레코드에 대해 설정된 TTL의 유효성을 검사해야 합니다.
      * TTL은 DNS 레코드가 서버에 업데이트를 요청하기 전에 캐시에 머무르는 시간입니다.
      * TTL이 매우 높은 경우 DNS 레코드 업데이트가 전파되는 데 시간이 더 오래 걸립니다.
* 비즈니스 요구 사항 및 목표를 충족하는 성능 및 보안 테스트를 실행합니다.
   * 스테이징 환경에서 테스트를 수행합니다.  이는 프로덕션 크기와 동일합니다.
   * 개발 환경은 스테이징 및 프로덕션과 크기가 동일하지 않습니다.
* 중단하고 새로운 배포나 콘텐츠 업데이트 없이 실제 실행이 수행되는지 확인합니다.
* Admin Console 사용자 알림 프로필을 만듭니다. [알림 프로필](/help/journey-onboarding/notification-profiles.md)을 참조하십시오.
* 웹 사이트에서 허용되지 않아야 하는 트래픽을 제어하려면 트래픽 필터 규칙을 구성하는 것이 좋습니다.
   * 속도 제한 트래픽 필터 규칙은 DDoS 공격에 대비하는 효과적인 도구가 될 수 있습니다. WAF 규칙이라고 하는 특별한 범주의 트래픽 필터 규칙에는 별도의 라이선스가 필요합니다.
   * [제안된 스타터 규칙](/help/security/traffic-filter-rules-including-waf.md#recommended-starter-rules)에 대한 설명서를 참조하십시오.

실행 중에 작업을 재수정해야 하는 경우 언제든지 목록을 참조할 수 있습니다.
