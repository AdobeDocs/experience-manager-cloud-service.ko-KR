---
title: ' [!DNL Adobe Experience Manager] as a Cloud Service 최신 릴리스 정보'
description: ' [!DNL Adobe Experience Manager] as a Cloud Service 최신 릴리스 정보'
mini-toc-levels: 1
exl-id: a2d56721-502c-4f4e-9b72-5ca790df75c5
feature: Release Information
role: Admin
source-git-commit: 68e2f6867a2cbcaf52fa6de259fe118e31ee7573
workflow-type: tm+mt
source-wordcount: '1942'
ht-degree: 92%

---

# [!DNL Adobe Experience Manager] as a Cloud Service 최신 릴리스 정보 {#release-notes}

다음 섹션에서는 [!DNL Experience Manager] as a Cloud Service의 최신 버전 기능 릴리스 정보에 대해 간략히 소개합니다.

>[!NOTE]
>
>여기에서 2021년 또는 2022년과 같은 이전 버전의 릴리스 정보로 이동할 수 있습니다.
>
>[!DNL Experience Manager] as a Cloud Service의 향후 기능 활성화에 대해 알아보려면 [Experience Manager 릴리스 로드맵](https://experienceleague.adobe.com/ko/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap)을 살펴보십시오.

>[!NOTE]
>
>릴리스와 직접적으로 관련되지 않는 설명서 업데이트의 세부 정보는 [최신 설명서 업데이트](https://experienceleague.adobe.com/ko/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates)를 참조하십시오.

## 릴리스 일자 {#release-date}

[!DNL Adobe Experience Manager] as a [!DNL Cloud Service] 현재 기능 릴리스(2024.5.0)의 릴리스 일자는 2024년 5월 30일입니다. 다음 기능 릴리스(2024.6.0)는 2024년 6월 27일에 예정되어 있습니다.

## 유지 관리 릴리스 정보 {#maintenance}

[ 여기](/help/release-notes/maintenance/latest.md)에서 최신 유지 관리 릴리스 정보를 확인할 수 있습니다.

## 릴리스 비디오 {#release-video}

2024년 5월 릴리스 개요 비디오를 통해 2024.5.0 릴리스에 추가된 기능에 대한 간단한 요약을 살펴보십시오.

>[!VIDEO](https://video.tv.adobe.com/v/3429503?quality=12)

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### Sites의 새로운 기능 {#sites-new-features}

#### AEM 번역 통합 {#translation-integration}

이제 콘텐츠 번역 작업 및 워크플로는 이벤트를 트리거하여 외부 애플리케이션에서 관련 프로세스 단계 및 상태를 추적할 수 있습니다. 다음 이벤트가 생성되고 있습니다. 사용자는 Adobe Developer 콘솔을 사용하여 이벤트에 가입할 수 있습니다.

* `TRANSLATION_JOB_CREATED`
* `TRANSLATION_JOB_CONTENT_ADDITION_STARTED`
* `TRANSLATION_JOB_CONTENT_ADDITION_COMPLETED`
* `TRANSLATION_JOB_CONTENT_DELETION_STARTED`
* `TRANSLATION_JOB_CONTENT_DELETION_COMPLETED`
* `TRANSLATION_JOB_COMMITTED_FOR_TRANSLATION`
* `TRANSLATION_JOB_READY_FOR_REVIEW`
* `TRANSLATION_JOB_APPROVED`
* `TRANSLATION_JOB_COMPLETED`
* `TRANSLATION_JOB_CANCELLED`
* `TRANSLATION_JOB_ERROR`

#### RUM(Real Use Monitoring) 데이터 서비스 {#real-use-monitoring}

* **[실제 사용 모니터링(RUM) 데이터 서비스는 이제 GA](/help/sites-cloud/administering/real-use-monitoring-for-aem-as-a-cloud-service.md)**를 통해 AEM as a Cloud Service에 대한 클라이언트측 데이터 수집이 가능합니다.
클라이언트 측 컬렉션인 Real Use 모니터링 서비스는 상호 작용을 보다 정확하게 반영하여 웹 사이트 참여를 안정적으로 측정합니다. 이를 통해 고객은 페이지 트래픽 및 성능에 대한 향상된 인사이트를 얻을 수 있습니다. 페이지 성능에 대해 자세히 알아보고 이를 개선하기 위한 인사이트를 얻을 수 있는 좋은 기회입니다.

#### Edge Delivery Services을 위한 AEM 작성 {#edge-enhancements}

더 나은 저작 경험을 위해 안정성이 향상되고 다양한 개선이 이루어졌습니다.

### 얼리 어답터 프로그램 {#sites-early-adopter}

**변형 생성**

이제 클라우드 서비스에서 액세스 가능한 AEM의 새로운 기능인 [변형 생성](/help/generative-ai/generate-variations.md)을 통해 GenAI를 활용할 수 있습니다. 변형 생성은 생성형 AI를 사용하여 콘텐츠 제작을 생성하고 확장하는 데 도움이 됩니다. 프로그램 참여를 고려한다면 Adobe 계정 팀에 문의하십시오.

**콘텐츠 조각 콘솔에서 자산 찾아보기**

이제 콘텐츠 작성자는 콘텐츠 조각 콘솔을 종료하지 않고도 이미지 및 기타 자산을 찾아보고, 보고, 작업을 수행할 수 있습니다.

![자산 찾아보기](/help/sites-cloud/administering/content-fragments/assets/cf-console-assets-browse.png)

기능을 사용해 보고 피드백을 공유하고 싶으십니까? 공식 이메일 ID로 aemcs-headless-adopter@adobe.com에 이메일을 보내 얼리 어답터 프로그램에 대해 자세히 알아보십시오.

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### 관리자 보기의 새로운 기능 {#admin-view-new-features}

* WebM은 이제 비디오용 프로필을 처리할 때 지원되는 출력 파일입니다.
* 이제 MP4가 Express의 AEM 기본 통합에서 지원됩니다(가져오기 및 내보내기).

### Assets 보기의 새로운 기능 {#assets-view-new-features}

**AEM 및 Dynamic Media에 자산 게시**

이제 Experience Manager Assets를 사용하면 관리 보기로 전환하지 않고도 Assets 보기를 사용하여 [Experience Manager 및 Dynamic Media에 자산을 빠르게 게시](/help/assets/publish-assets-to-aem-and-dm.md)할 수 있습니다. 자산을 업로드, 찾아보기 및 검색하는 동안 자산을 게시할 수 있습니다.

![게시 상태 1 확인](/help/assets/assets/check-publish-status1.png)

## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

<!-- 

* **Configure a shard for Adobe Sign for AEM Forms**: Adobe distributes Acrobat Sign API around the globe in many deployment units called "shards." Each shard serves a customer's account, such as NA1, NA2, NA3, EU1, JP1, AU1, IN1, and others. The shard names correspond to geographic locations. You can now use more than one shard while using Adobe Sign integration with AEM Forms. 

-->

### AEM Forms의 새로운 프리릴리스 기능 {#forms-new-prerelease-features}

#### 핵심 구성 요소 기반의 적응형 양식을 위한 향상된 시각적 규칙 편집기

이 릴리스에서는 핵심 구성 요소 기반 적응형 양식을 위한 시각적 규칙 편집기가 대폭 업그레이드되었습니다. 이제 다음을 수행할 수 있습니다.

* 시각적 규칙 편집기에서 [기본 양식 제출 성공/실패 메시지를 재정의](/help/forms/create-and-use-custom-functions.md#use-case-override-form-submission-success-and-error-handlers)하는 규칙을 만듭니다.

* 적응형 양식 규칙 편집기에서 [WHEN 작업을 위해 다양한 유형의 필드를 선택](/help/forms/rule-editor-core-components.md#allowed-multiple-fields-in-when)할 수 있는 기능이 추가되었습니다.

* 이제 양식 작성자가 사용자 정의 기능을 적용하여 [제출 전에 데이터를 전처리](/help/forms/create-and-use-custom-functions.md#use-case-submit-altered-data-to-the-server)할 수 있습니다.

* [**초안으로 저장**](/help/forms/save-core-component-based-form-as-draft.md) 기능을 사용하여 부분적으로 완료된 양식을 나중에 제출할 수 있도록 저장합니다. 이는 사용자가 양식 작성을 중단하고 나중에 다시 작성해야 하는 시나리오에서 유용합니다.



### AEM Forms의 얼리 어답터 기능 {#forms-new-early-adopter-features}

AEM Forms 얼리 어답터 프로그램은 누구보다 먼저 최첨단 혁신에 독점적으로 액세스할 수 있는 특별한 기회를 제공하며, 혁신의 발전을 구체화하는 데 도움을 줍니다.
이 프로그램은 여러 혁신에 액세스할 수 있습니다.

이 릴리스 정보에는 현재 릴리스에서 제공되는 혁신 사항이 나열되어 있습니다. 얼리 어답터 프로그램에서 사용할 수 있는 전체 혁신 목록은 [AEM Forms 얼리 어답터 프로그램 설명서](/help/forms/early-adopter-ea-features.md)를 참조하십시오.

#### 향상된 봇 보호 방법

AEM Forms는 널리 사용되는 두 가지 CAPTCHA 솔루션인 Cloudflare Turnstile 및 hCaptcha에 대한 지원을 추가하여 보안 기능을 강화했습니다. 이미 사용 가능한 Google reCAPTCHA에 추가되어 봇 및 스팸 제출로부터 양식을 보호하는 데 있어 사용자에게 더 많은 선택권과 유연성을 제공합니다.

* **Cloudflare Turnstile**: 이 마찰 없는 CAPTCHA는 명시적인 상호 작용이 필요하지 않은 간단한 인증을 통해 사용자를 검증합니다. 양식에 완벽하게 통합되어 사용자 경험을 향상시킵니다.
* **hCaptcha**: 개인 정보 보호에 중점을 둔 이 CAPTCHA는 데이터 개인 정보 보호에 초점을 맞춘 사용자 친화적인 대안을 제공합니다. 보안과 사용자 경험 사이의 균형을 맞추는 것을 목표로 합니다.
* **Google reCAPTCHA**: AEM Forms는 reCAPTCHA v2와 reCAPTCHA Enterprise를 지속적으로 지원하여 안정적이고 잘 정립된 솔루션을 제공합니다.

AEM Forms는 다양한 CAPTCHA 옵션을 제공하여 특정 요구 사항에 가장 적합한 솔루션을 선택할 수 있도록 지원합니다.

이러한 CAPTCHA 솔루션을 적응형 양식과 통합할 준비가 되셨습니까? 설명서에는 [Cloudflare Turnstile](https://experienceleague.adobe.com/kr/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-core-components/create-an-adaptive-form-on-forms-cs/integrate-adaptive-forms-turnstile-core-components), [hCaptcha](https://experienceleague.adobe.com/kr/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-core-components/create-an-adaptive-form-on-forms-cs/integrate-adaptive-forms-hcaptcha-core-components) 및 [Google reCAPTCHA](https://experienceleague.adobe.com/kr/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-core-components/create-an-adaptive-form-on-forms-cs/captcha-adaptive-forms-core-components)에 대한 자세한 지침이 있습니다.


### Forms 서비스

Forms 서비스는 데이터 캡처를 위한 대화형 PDF 양식을 생성합니다. 또한 기존 대화형 PDF 양식에서 데이터를 가져오거나 내보내고 제출된 데이터의 유효성을 검사하는 데 사용할 수도 있습니다. 기능의 분류는 다음과 같습니다.

* **Forms 렌더링**: AEM Forms Designer를 사용하여 작성한 템플릿과 선택적으로 XML 데이터에서 대화형 PDF 양식을 생성합니다. 이를 통해 선택적으로 데이터를 미리 채운 채울 수 있는 PDF 양식을 기본적으로 생성합니다.
* **데이터 추출 및 가져오기**: 기존 PDF 양식으로 데이터를 가져올 뿐만 아니라 채워진 PDF 양식에서 데이터를 추출할 수 있습니다. XDP 및 XML 데이터 형식이 모두 지원되며, XFA가 아닌 PDF 형식(AcroForms라고도 함)으로 가져오기는 FDF 및 XFDF 데이터를 추가로 지원합니다.
* **데이터 유효성 검사**: AEM Forms Designer를 사용하여 만든 템플릿에 대해 제출된 데이터의 유효성을 XDP 또는 XML 형식으로 확인합니다.

>[!IMPORTANT]
>
> 얼리 어답터 혁신을 위해 얼리 어답터 프로그램에 참여하고 싶다면 공식 주소에서 [aem-forms-ea@adobe.com](mailto:aem-forms-ea@adobe.com)으로 이메일을 보내 액세스를 요청합니다. 전체 또는 특정 혁신에 대한 액세스를 요청할 수 있습니다.


## [!DNL Experience Manager] as a [!DNL Cloud Service] Foundation {#foundation}

### 다른 Adobe 솔루션과의 AEM 통합을 위한 OAuth 서버 간 자격 증명 지원 {#S2S-OAuth-credentials}

Adobe Developer Console은 다양한 API에 액세스하기 위한 자격 증명을 생성하는 데 사용됩니다. 이러한 자격 증명 유형 중 하나인 서비스 계정(JWT) 자격 증명은 OAuth 서버 간 자격 증명을 선호하여 사용되지 않으며, AEM Cloud Service는 현재 Adobe Analytics 및 Adobe Target과 같은 다른 Adobe 솔루션과의 통합을 지원합니다.

[지원 중단에 대해 읽고](/help/security/jwt-credentials-deprecation-in-adobe-developer-console.md) [AEM Author UI를 사용하여](/help/security/setting-up-ims-integrations-for-aem-as-a-cloud-service.md) 다른 Adobe 솔루션과의 통합을 구성하는 방법에 대해 알아보십시오.

### 원본 트래픽 스파이크 경고 {#traffic-spike-origin}

원본 트래픽 패턴이 DDoS 공격을 나타내는 경우 액션 센터를 통해 [사전 알림을 받아](/help/security/traffic-filter-rules-including-waf.md#traffic-spike-at-origin-alert) 트래픽 필터 규칙을 조사하고 구성할 수 있습니다.

### RDE의 새로운 기능 {#RDE-new-features}

[신속한 개발 환경(RDE)](/help/implementing/developing/introduction/rapid-development-environments.md)을 통해 개발자는 클라우드의 변경 사항을 신속하게 배포, 검토 및 테스트할 수 있습니다. 6월 한 달 동안 몇 가지 새로운 기능이 출시될 예정입니다. 또한 [RDE 디스코드 채널](https://discord.com/channels/1131492224371277874/1245304281184079872)에서 Adobe 엔지니어링에 직접 참여할 수 있도록 초대합니다


#### 사이트 테마 및 사이트 템플릿을 사용하는 프론트 엔드 코드에 대한 RDE 지원 {#rde-frontend}

[RDE는](/help/implementing/developing/introduction/rapid-development-environments.md#deploying-themes-to-rde) 이제 얼리 어답터에 대해 [사이트 테마](/help/sites-cloud/administering/site-creation/site-themes.md) 및 [사이트 템플릿](/help/sites-cloud/administering/site-creation/site-templates.md)을 기반으로 하는 프론트 엔드 코드를 지원합니다. RDE를 사용하면 [프론트 엔드 파이프라인](/help/sites-cloud/administering/site-creation/enable-front-end-pipeline.md)이 아닌 명령줄 지시문을 사용하여 이 작업이 수행됩니다.

#### RDE에 대한 향상된 로깅 {#rde-logging}

이제 개발자는 RDE에서 코드를 디버깅하는 동안 버전 제어에서 OSGI 속성을 수정하지 않고도 명령줄을 사용하여 [로그를 생산적으로 구성하고 스트리밍](/help/implementing/developing/introduction/rapid-development-environments.md#rde-logging)할 수 있습니다. 기능은 다음과 같습니다.

* 패키지별 또는 클래스 수준에서 로그 수준 선언
* 로그 출력 형식 사용자 정의
* 여러 로그를 병렬로 스트리밍

#### RDE CIF 향상된 기능 {#rde-cli-enhancements}

RDE 명령줄 인터페이스에는 개발자 환경을 개선하는 몇 가지 새로운 기능이 있습니다.

* [setup 명령어는 대화형으로](/help/implementing/developing/introduction/rapid-development-environments.md#installing-the-rde-command-line-tools-interactive), 조직, 프로그램 및 환경 중에서 선택하기 쉽습니다. 이제 명령줄에서 이러한 값을 재정의할 수도 있습니다.
* 덜 장황한 출력을 위한 [조용한 모드](/help/implementing/developing/introduction/rapid-development-environments.md#global-flags).
* [json 모드](/help/implementing/developing/introduction/rapid-development-environments.md#global-flags) 를 프로그래밍 방식으로 호출할 때 유용한 출력입니다.

### 새 액션 센터 알림 {#actions-center-notifications}

[액션 센터](/help/operations/actions-center.md)는 중요한 사고가 발생하거나 사용자가 사전 예방 조치를 취해야 할 코드 또는 구성에 대해 발견한 경우 이메일 알림을 보냅니다. 세 가지 새로운 유형의 알림이 있습니다.

* 고급 네트워킹 인프라를 통한 너무 많은 발신 연결
* 더 이상 사용되지 않는 서비스 사용자 매핑 형식 사용
* 잠재적인 DDoS 공격이 진행 중

### 얼리 어답터 프로그램 {#foundation-early-adopter}

이메일 **<aemcs-cdn-config-adopter@adobe.com>**, 아래의 얼리 어답터 프로그램 중 관심 있는 프로그램을 나타냅니다.

#### 셀프서비스 API 키(얼리 어답터 프로그램)로 CDN에서 콘텐츠 삭제 {#purge-cdn}

셀프서비스 방식으로 CDN 삭제 API 키를 등록하고, 이를 사용하여 전역적으로 또는 하나 이상의 리소스에 대해 CDN의 콘텐츠를 무효화합니다. [자세히 알아보기](/help/implementing/dispatcher/cdn-cache-purge.md).

<!-- Email **<aemcs-cdn-config-adopter@adobe.com>** with a request to be an early adopter. -->

#### 고객 관리형 CDN(BYOCDN)을 위한 X-AEM-Edge-Key 셀프서비스 생성(얼리 어답터 프로그램) {#byocdn-keys}

이전에는 고객 관리형 CDN 구성에 필요한 X-AEM-Edge-Key를 생성하려면 지원 티켓이 필요했습니다. 이제 구성 파이프라인을 사용하여 배포되는 구성 파일을 통해 셀프서비스 방식으로 이를 수행할 수 있으므로 새 환경에 대한 온보딩 작업이 지연되지 않습니다. [자세히 알아보기](/help/implementing/dispatcher/cdn-credentials-authentication.md#CDN-HTTP-value).

<!-- Email **<aemcs-cdn-config-adopter@adobe.com>** with a request to be an early adopter. -->

#### 클라이언트측 리디렉션(얼리 어답터 프로그램) {#client-side-redirects-early-adopter}

소스 제어에서 301/302 클라이언트측 리디렉션을 구성하고 CDN에 배포합니다. [자세히 알아보기](/help/implementing/dispatcher/cdn-configuring-traffic.md#client-side-redirectors).<!-- and join the early adopter program by emailing **<aemcs-cdn-config-adopter@adobe.com>**. --> 요청 및 응답 변환, AEM 외부 사이트로의 라우팅 트래픽 등 [CDN 구성](/help/implementing/dispatcher/cdn-configuring-traffic.md)과 관련하여 이미 사용 가능한 여러 다른 기능이 있습니다.

#### 트래픽 필터 규칙 경고(얼리 어답터 프로그램) {#traffic-filter-rules-alerts-early-adopter}

선택적으로 라이선스를 부여할 수 있는 WAF(웹 애플리케이션 방화벽) 규칙을 포함하는 최근 릴리스된 [트래픽 필터 규칙](/help/security/traffic-filter-rules-including-waf.md)을 통해 허용하거나 거부해야 하는 트래픽을 구성할 수 있습니다.

얼리 어답터 프로그램에 참여하면 트래픽 필터 규칙이 실행될 때마다 알림을 받을 수 있습니다. 액션 센터 이메일 알림은 특정 트래픽 상황이 발생할 때 적절한 조치를 취할 수 있도록 지속적으로 정보를 제공해 줍니다.

#### 비즈니스 사용자는 Git 외의 리디렉션을 선언할 수 있습니다(얼리 어답터 프로그램). {#apache-rewritemaps-early-adopter}

AEM 6.5와 유사하게 Apache/Dispatcher는 게시 저장소의 특정 위치에 배치된 재작성 맵을 수집하고 웹 계층 파이프라인 실행 없이 로드합니다. 이를 통해 비즈니스 사용자는 ACS Commons Redirect Map Manager에서 제공되거나 고객 애플리케이션의 일부로 생성된 것과 같은 스프레드시트 또는 UI를 사용하여 리디렉션을 선언할 수 있습니다. <!-- Please reach out to **<aemcs-cdn-config-adopter@adobe.com>** for more information. -->

#### 동적 콘텐츠 로드를 위한 ESI(에지측 포함)(얼리 어답터 프로그램) {#esi-early-adopter}

이제 Adobe Managed CDN은 에지 수준 동적 웹 콘텐츠 어셈블리를 위한 마크업 언어인 [ESI(에지측 포함)](/help/implementing/dispatcher/edge-side-includes.md)를 지원합니다. ESI 스니펫을 포함하면 더 높은 TTL을 사용하여 CDN에서 전체 HTML 페이지를 캐싱하는 동시에 더 높은 케이던스 업데이트(낮은 TTL)가 필요한 작은 섹션을 출처에서 더 자주 가져올 수 있습니다. <!--Please reach out to **<aemcs-cdn-config-adopter@adobe.com>** for more information.-->

## [!DNL Experience Manager] 안내서 {#guides}

* **주제 또는 해당 요소를 경험 조각에 게시**
이제 Experience Manager Guides를 사용하면 주제 또는 해당 요소를 경험 조각에 게시할 수 있습니다. 경험 조각은 콘텐츠와 레이아웃을 모두 통합하는 모듈식 콘텐츠 단위입니다.  경험 조각은 중요한 역할을 하며 일관되고 매력적인 경험을 만드는 데 도움이 될 수 있습니다.
* **주제 자산 메타데이터를 기본 PDF 출력으로 전달하는 기능**
기본 PDF 출력을 생성하면서 주제 자산 메타데이터를 추가할 수 있습니다. 이 기능을 사용하면 주제 제목, 작성자와 같은 다양한 주제에 대한 특정 메타데이터를 주제 페이지 머리글 및 바닥글에 추가할 수 있습니다.

릴리스에서 수정된 새로운 기능과 향상된 기능 및 문제에 대한 자세한 내용은 [Experience Manager Guides 릴리스 로드맵](https://experienceleague.adobe.com/kr/docs/experience-manager-guides/using/release-info/aem-guides-releases-roadmap)을 참조하십시오.

## Cloud Manager {#cloud-manager}

[여기](/help/implementing/cloud-manager/release-notes/current.md)에서 Cloud Manager 월별 릴리스의 전체 목록을 찾을 수 있습니다.

## 마이그레이션 도구 {#migration-tools}

[여기](/help/journey-migration/release-notes/release-notes-migration-tools-current.md)에서 마이그레이션 도구의 전체 목록을 찾을 수 있습니다.

## Experience Cloud 릴리스 정보 {#experience-cloud}

다른 Experience Cloud 응용 프로그램의 릴리스에 대한 정보를 찾을 수 있습니다 [여기](https://experienceleague.adobe.com/en/docs/release-notes/experience-cloud/current).
Experience Cloud 릴리스 정보 업데이트에 대한 월별 이메일 알림을 받으려면 [Adobe 우선 순위 제품 업데이트](https://www.adobe.com/kr/subscription/priority-product-update.html).
