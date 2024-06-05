---
title: ' [!DNL Adobe Experience Manager] as a Cloud Service 최신 릴리스 정보'
description: ' [!DNL Adobe Experience Manager] as a Cloud Service 최신 릴리스 정보'
mini-toc-levels: 1
exl-id: a2d56721-502c-4f4e-9b72-5ca790df75c5
feature: Release Information
role: Admin
source-git-commit: b7e8fd902bb2fe98e183b7d987b87fee69e48337
workflow-type: tm+mt
source-wordcount: '1865'
ht-degree: 22%

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

의 릴리스 날짜 [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] 현재 기능 릴리스(2024.5.0)는 2024년 5월 30일입니다. 다음 기능 릴리스(2024.6.0)는 2024년 6월 27일에 예정되어 있습니다.

## 유지 관리 릴리스 정보 {#maintenance}

[ 여기](/help/release-notes/maintenance/latest.md)에서 최신 유지 관리 릴리스 정보를 확인할 수 있습니다.

## 릴리스 비디오 {#release-video}

2024년 5월 릴리스 개요 비디오를 통해 2024.5.0 릴리스에 추가된 기능에 대한 간단한 요약을 살펴보십시오.

>[!VIDEO](https://video.tv.adobe.com/v/3429503?quality=12)

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### Sites의 새로운 기능 {#sites-new-features}

**Edge Delivery Services를 위한 AEM 작성**

향상된 작성 환경을 위해 안정성 및 다양한 개선 사항이 개선되었습니다.

### 얼리 어답터 프로그램 {#sites-early-adopter}

**변형 생성**

이제 클라우드 서비스에서 액세스 가능한 AEM의 새로운 기능인 [변형 생성](/help/generative-ai/generate-variations.md)을 통해 GenAI를 활용할 수 있습니다. 변형 생성은 생성형 AI를 사용하여 콘텐츠 제작을 생성하고 확장하는 데 도움이 됩니다. 프로그램 참여를 고려한다면 Adobe 계정 팀에 문의하십시오.

**콘텐츠 조각 콘솔에서 자산 찾아보기**

이제 콘텐츠 작성자는 콘텐츠 조각 콘솔을 종료하지 않고도 이미지 및 기타 자산을 찾아보고, 보고, 작업을 수행할 수 있습니다.

![자산 찾아보기](/help/sites-cloud/administering/content-fragments/assets/cf-console-assets-browse.png)

기능을 사용해 보고 피드백을 공유하고 싶으십니까? 공식 이메일 ID로 aemcs-headless-adopter@adobe.com에 이메일을 보내 얼리 어답터 프로그램에 대해 자세히 알아보십시오.

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### 관리자 보기의 새로운 기능 {#admin-view-new-features}

* 이제 WebM은 비디오용 프로필 처리에서 지원되는 출력 파일입니다.
* MP4는 이제 AEM in Express(가져오기 및 내보내기)의 기본 통합에서 지원됩니다.

### Assets 보기의 새로운 기능 {#assets-view-new-features}

**자산을 AEM 및 Dynamic Media에 게시**

이제 Experience Manager Assets을 통해 신속하게 [Experience Manager 및 Dynamic Media에 자산 게시](/help/assets/publish-assets-to-aem-and-dm.md) 관리자 보기로 전환하지 않고 자산 보기 사용. 에셋을 업로드하고, 탐색하고, 검색하는 동안 에셋을 게시할 수 있습니다.

![게시 상태 확인1](/help/assets/assets/check-publish-status1.png)

## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

<!-- 

* **Configure a shard for Adobe Sign for AEM Forms**: Adobe distributes Acrobat Sign API around the globe in many deployment units called "shards." Each shard serves a customer's account, such as NA1, NA2, NA3, EU1, JP1, AU1, IN1, and others. The shard names correspond to geographic locations. You can now use more than one shard while using Adobe Sign integration with AEM Forms. 

-->

### AEM Forms의 새로운 프리릴리스 기능 {#forms-new-prerelease-features}

#### 핵심 구성 요소 기반 적응형 Forms을 위한 향상된 시각적 규칙 편집기

이 릴리스에서는 핵심 구성 요소 기반 적응형 양식을 위한 시각적 규칙 편집기가 대폭 업그레이드되었습니다. 이제 다음을 수행할 수 있습니다.

* 시각적 규칙 편집기에서 규칙을 만들어 다음을 수행할 수 있습니다. [기본 양식 제출 성공/실패 메시지 재정의](/help/forms/create-and-use-custom-functions.md#use-case-override-form-submission-success-and-error-handlers).

* 적응형 Forms 규칙 편집기에서 [when 작업에 대해 다른 유형의 필드 선택](/help/forms/rule-editor-core-components.md#allowed-multiple-fields-in-when).

* 이제 양식 작성자는 사용자 정의 함수를 다음에 적용할 수 있습니다. [제출 전 데이터 사전 처리](/help/forms/create-and-use-custom-functions.md#use-case-submit-altered-data-to-the-server).

* 사용 [**초안으로 저장**](/help/forms/save-core-component-based-form-as-draft.md) 나중에 제출하기 위해 부분적으로 완료된 양식을 저장하는 기능입니다. 이 기능은 사용자가 양식 작성을 중단하고 나중에 다시 와야 하는 시나리오에서 유용합니다.



### AEM Forms의 얼리 어답터 기능 {#forms-new-early-adopter-features}

AEM Forms 얼리 어답터 프로그램(Early Adopter Program)은 다른 사람들보다 먼저 혁신적인 최신 기술에 독점적으로 액세스하고 개발을 구체화할 수 있는 특별한 기회를 제공합니다.
이 프로그램은 다양한 혁신적인 기능에 액세스할 수 있습니다.

이 릴리스 노트는 현재 릴리스에서 제공되는 혁신적인 기능을 나열합니다. 얼리어답터 프로그램에서 사용할 수 있는 혁신의 전체 목록은 다음을 참조하십시오. [AEM Forms 얼리 어답터 프로그램 설명서](/help/forms/early-adopter-ea-features.md).

#### 향상된 보트 보호 방법

AEM Forms은 널리 사용되는 두 가지 CAPTCHA 솔루션인 Cloudflare Turnstile 및 hCaptcha에 대한 지원을 추가하여 보안 기능을 강화했습니다. 이렇게 하면 이미 사용 가능한 Google reCAPTCHA가 추가되어 사용자에게 봇 및 스팸 제출로부터 양식을 보호할 수 있는 더 많은 선택권과 유연성을 제공합니다.

* **Cloudflare 턴스타일**: 이 마찰 없는 CAPTCHA는 명시적인 상호 작용이 필요하지 않은 간단한 문제를 통해 사용자를 확인합니다. 양식과 원활하게 통합되어 사용자 경험이 개선됩니다.
* **Captcha**: 이 개인정보 보호 중심 CAPTCHA는 데이터 개인정보 보호에 중점을 둔 사용자 친화적인 대안을 제공합니다. 보안과 사용자 경험 사이의 균형을 맞추는 것을 목표로 합니다.
* **Google recaptcha**: AEM Forms은 안정적이고 잘 구축된 솔루션을 제공하여 reCAPTCHA v2 및 reCAPTCHA Enterprise를 계속 지원합니다.

AEM Forms에서는 여러 CAPTCHA 옵션을 제공하여 특정 요구 사항에 가장 적합한 솔루션을 선택할 수 있도록 했습니다.

이러한 CAPTCHA 솔루션을 적응형 Forms과 통합할 준비가 되셨습니까? 설명서는 각각에 대한 자세한 지침을 제공합니다. [Cloudflare 턴스타일](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-core-components/create-an-adaptive-form-on-forms-cs/integrate-adaptive-forms-turnstile-core-components), [Captcha](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-core-components/create-an-adaptive-form-on-forms-cs/integrate-adaptive-forms-hcaptcha-core-components), 및 [Google recaptcha](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-core-components/create-an-adaptive-form-on-forms-cs/captcha-adaptive-forms-core-components).


### Forms 서비스

Forms 서비스는 데이터 캡처를 위한 대화형 PDF forms을 생성합니다. 또한 기존 대화형 PDF 양식에서 데이터 내보내기를 가져오고 제출된 데이터의 유효성을 검사하는 데 사용할 수도 있습니다. 다음은 기능의 분류입니다.

* **Forms 렌더링**: AEM Forms Designer 및 선택적으로 XML 데이터를 사용하여 만든 템플릿에서 대화형 PDF 양식을 생성합니다. 이는 필수적으로 선택적으로 데이터로 미리 채워진 입력 가능한 PDF 양식을 생성한다.
* **데이터 추출 및 가져오기**: 기존 PDF 양식으로 데이터를 가져오고 채워진 PDF 양식에서 데이터를 추출합니다. XDP 및 XML 데이터 형식이 모두 지원되며, XFA가 아닌 PDF forms(AcroForms라고도 함)으로 가져오기는 FDF 및 XFDF 데이터를 추가로 지원합니다.
* **데이터 유효성 검사**: AEM Forms Designer를 사용하여 만든 템플릿에 대해 제출된 데이터의 유효성을 XDP 또는 XML 형식으로 확인합니다.

>[!IMPORTANT]
>
> 얼리어답터 혁신을 위해 얼리어답터 프로그램에 참여하고자 하는 경우, 공식 주소로 이메일을 보내십시오. [aem-forms-ea@adobe.com](mailto:aem-forms-ea@adobe.com) 액세스 권한 요청. 모든 또는 특정 혁신에 대한 액세스를 요청할 수 있습니다.


## [!DNL Experience Manager] as a [!DNL Cloud Service] Foundation {#foundation}

### 다른 Adobe 솔루션과 AEM 통합을 위한 OAuth 서버 간 자격 증명 지원 {#S2S-OAuth-credentials}

Adobe Developer 콘솔은 다양한 API에 액세스하기 위한 자격 증명을 생성하는 데 사용됩니다. 이러한 자격 증명 유형 중 하나인 JWT(서비스 계정) 자격 증명은 더 이상 사용되지 않으며, 대신 AEM Cloud Service에서 Adobe Analytics 및 Adobe Target과 같은 다른 Adobe 솔루션과의 통합을 지원하는 OAuth 서버 간 자격 증명이 사용됩니다.

[사용 중단에 대해 읽어보기](/help/security/jwt-credentials-deprecation-in-adobe-developer-console.md) 및 [AEM 작성자 UI 사용 방법 알아보기](/help/security/setting-up-ims-integrations-for-aem-as-a-cloud-service.md) 다른 Adobe 솔루션과의 통합을 구성합니다.

### 원본 경고의 트래픽 스파이크 {#traffic-spike-origin}

[사전 알림 수신](/help/security/traffic-filter-rules-including-waf.md#traffic-spike-at-origin-alert) 원점의 트래픽 패턴이 DDoS 공격을 나타내는 경우 작업 센터를 통해 트래픽 필터 규칙을 조사하고 구성할 수 있습니다.

### RDE의 새로운 기능 {#RDE-new-features}

[신속한 개발 환경(RDE)](/help/implementing/developing/introduction/rapid-development-environments.md) 개발자가 클라우드에서 변경 사항을 신속하게 배포, 검토 및 테스트할 수 있습니다. 6월 한 달 동안 몇 가지 새로운 기능이 출시될 예정입니다. 또한 다음 사이트에서 Adobe 엔지니어링과 직접 협력하실 것을 권합니다. [RDE 디스코드 채널](https://discord.com/channels/1131492224371277874/1245304281184079872).


#### 사이트 테마 및 사이트 템플릿을 사용하는 프론트엔드 코드에 대한 RDE 지원 {#rde-frontend}

[이제 RDE에서 프론트엔드 코드 지원](/help/implementing/developing/introduction/rapid-development-environments.md#deploying-themes-to-rde) 기준 [사이트 테마](/help/sites-cloud/administering/site-creation/site-themes.md) 및 [사이트 템플릿](/help/sites-cloud/administering/site-creation/site-templates.md), 얼리 어답터용 RDE를 사용하면 이 작업은 RDE가 아닌 명령줄 지시문을 사용하여 수행됩니다. [프론트엔드 파이프라인](/help/sites-cloud/administering/site-creation/enable-front-end-pipeline.md).

#### RDE에 대한 로깅 개선 {#rde-logging}

이제 개발자는 RDE에서 코드를 디버깅하는 동안 [보다 생산적으로 로그 구성 및 스트리밍](/help/implementing/developing/introduction/rapid-development-environments.md#rde-logging), 명령줄 사용 및 버전 제어에서 OSGI 속성 수정 안 함 기능은 다음과 같습니다.

* 패키지 또는 클래스 수준별 로그 수준 선언
* 로그 출력 형식 사용자 정의
* 여러 로그를 동시에 스트리밍

#### RDE CLI 향상 {#rde-cli-enhancements}

RDE 명령줄 인터페이스에는 개발자 경험을 개선하는 몇 가지 새로운 기능이 있습니다.

* [setup 명령은 대화형입니다.](/help/implementing/developing/introduction/rapid-development-environments.md#installing-the-rde-command-line-tools-interactive)를 사용하면 조직, 프로그램 및 환경 중에서 선택하는 것이 더 쉬워집니다. 이제 명령줄에서 이러한 값을 재정의할 수도 있습니다.
* [자동 모드](/help/implementing/developing/introduction/rapid-development-environments.md#global-flags) 덜 자세한 출력입니다.
* [json 모드](/help/implementing/developing/introduction/rapid-development-environments.md#global-flags) 프로그래밍 방식으로 호출할 때 유용한 출력입니다.

### 새 작업 센터 알림 {#actions-center-notifications}

[작업 센터](/help/operations/actions-center.md) 중요한 인시던트가 발생하거나 사전 조치를 취해야 하는 코드 또는 구성에 대해 알리는 경우 이메일 알림을 보냅니다. 세 가지 새로운 유형의 알림이 있습니다.

* 고급 네트워킹 인프라를 통한 발신 연결이 너무 많음
* 더 이상 사용되지 않는 서비스 사용자 매핑 형식 사용
* 잠재적인 DDoS 공격이 진행 중입니다.

### 얼리 어답터 프로그램 {#foundation-early-adopter}

이메일 **<aemcs-cdn-config-adopter@adobe.com>**- 아래의 얼리어답터 프로그램 중 어떤 프로그램에 관심이 있는지 나타냅니다.

#### 셀프서비스 API 키(얼리어답터 프로그램)를 사용하여 CDN에서 컨텐츠 제거 {#purge-cdn}

CDN 삭제 API 키를 셀프서비스 방식으로 등록하고 이를 사용하여 전역적으로 또는 하나 이상의 리소스에 대해 CDN에서 콘텐츠를 무효화합니다. [자세히 알아보기](/help/implementing/dispatcher/cdn-cache-purge.md).

<!-- Email **<aemcs-cdn-config-adopter@adobe.com>** with a request to be an early adopter. -->

#### 고객 관리 CDN(BYOCDN)을 위한 X-AEM-Edge-Key 셀프서비스 생성(얼리어답터 프로그램) {#byocdn-keys}

이전에는 고객 관리 CDN 구성에 필요한 X-AEM-Edge-Key를 생성하는 데 지원 티켓이 필요했습니다. 이제 구성 파이프라인을 사용하여 배포되는 구성 파일을 통해 셀프서비스 방식으로 이를 수행할 수 있으므로 새 환경 온보딩에 대한 지연을 제거할 수 있습니다. [자세히 알아보기](/help/implementing/dispatcher/cdn-credentials-authentication.md#CDN-HTTP-value).

<!-- Email **<aemcs-cdn-config-adopter@adobe.com>** with a request to be an early adopter. -->

#### 클라이언트측 리디렉션(얼리 어답터 프로그램) {#client-side-redirects-early-adopter}

소스 제어에서 301/302 클라이언트측 리디렉션을 구성하고 CDN에 배포합니다. [자세히 알아보기](/help/implementing/dispatcher/cdn-configuring-traffic.md#client-side-redirectors).<!-- and join the early adopter program by emailing **<aemcs-cdn-config-adopter@adobe.com>**. --> 와 관련하여 이미 사용할 수 있는 몇 가지 다른 기능이 있습니다. [CDN 구성](/help/implementing/dispatcher/cdn-configuring-traffic.md): 요청 및 응답 변환, 오프 AEM 사이트로의 트래픽 라우팅 등을 포함합니다.

#### 트래픽 필터 규칙 경고(얼리 어답터 프로그램) {#traffic-filter-rules-alerts-early-adopter}

선택적으로 라이선스를 부여할 수 있는 WAF(웹 애플리케이션 방화벽) 규칙을 포함하는 최근 릴리스된 [트래픽 필터 규칙](/help/security/traffic-filter-rules-including-waf.md)을 통해 허용하거나 거부해야 하는 트래픽을 구성할 수 있습니다.

트래픽 필터 규칙이 트리거될 때마다 알림을 받을 수 있도록 얼리어답터 프로그램에 참여하십시오. 액션 센터 이메일 알림은 특정 트래픽 상황이 발생할 때 적절한 조치를 취할 수 있도록 지속적으로 정보를 제공해 줍니다.

#### 비즈니스 사용자는 Git(얼리 어답터 프로그램) 외부에서 리디렉션을 선언할 수 있습니다. {#apache-rewritemaps-early-adopter}

AEM 6.5와 유사하게 Apache/Dispatcher는 게시 저장소의 특정 위치에 배치된 재작성 맵을 수집하고 웹 계층 파이프라인 실행 없이 로드합니다. 이렇게 하면 비즈니스 사용자가 스프레드시트나 UI(예: ACS Commons 리디렉션 맵 관리자에서 제공하거나 고객 애플리케이션의 일부로 생성된 리디렉션)를 사용하여 리디렉션을 선언할 수 있습니다. <!-- Please reach out to **<aemcs-cdn-config-adopter@adobe.com>** for more information. -->

#### 동적 콘텐츠 로드를 위한 ESI(에지측 포함)(얼리 어답터 프로그램) {#esi-early-adopter}

이제 Adobe 관리 CDN은 을 지원합니다. [ESI(Edge Side Includes)](/help/implementing/dispatcher/edge-side-includes.md), 에지 수준의 동적 웹 콘텐츠 어셈블리에 대한 마크업 언어입니다. ESI 스니펫을 포함하면 더 높은 TTL로 CDN의 전체 HTML 페이지를 캐시하는 동시에 더 높은 케이던스 업데이트(더 낮은 TTL)가 필요한 더 작은 섹션을 원본에서 더 자주 가져올 수 있습니다. <!--Please reach out to **<aemcs-cdn-config-adopter@adobe.com>** for more information.-->

#### RUM(Real User Monitoring) 데이터 서비스(얼리 어답터 프로그램)

* **[RUM(Real Use Monitoring) 데이터 서비스가 이제 GA되었습니다.](/help/implementing/cloud-manager/content-requests.md#real-user-monitoring-for-aem-as-a-cloud-service)** AEM as a Cloud Service으로 클라이언트측 데이터 수집 활성화.
클라이언트측 컬렉션인 실제 사용 모니터링 서비스 는 상호 작용을 보다 정확하게 반영하여 웹 사이트 참여를 안정적으로 측정합니다. 이를 통해 페이지 트래픽 및 성능에 대한 고급 통찰력을 보유한 고객이 사용할 수 있습니다. 페이지 성능에 대해 자세히 알아보고 향상시킬 수 있는 통찰력을 얻을 수 있는 좋은 기회입니다.

## [!DNL Experience Manager] 안내서 {#guides}

* **주제 또는 해당 요소를 경험 조각에 게시**
이제 Experience Manager 안내서를 사용하여 주제 또는 해당 요소를 경험 조각에 게시할 수 있습니다. 경험 조각 은 콘텐츠와 레이아웃을 모두 통합하는 모듈식 콘텐츠 단위입니다.  경험 조각 은 중요한 역할을 하며 일관되고 매력적인 경험을 만드는 데 도움이 될 수 있습니다.
* **주제 에셋 메타데이터를 기본 PDF 출력에 전달하는 기능**
기본 PDF 출력을 생성하는 동안 주제 에셋 메타데이터를 추가할 수 있습니다. 이 기능을 사용하면 주제 제목 및 작성자와 같은 다양한 주제에 대한 특정 메타데이터를 주제 페이지 머리글과 바닥글에 추가할 수 있습니다.

릴리스에서 수정된 새로운 기능 및 향상된 기능에 대한 자세한 내용은 [Experience Manager 가이드 릴리스 로드맵](https://experienceleague.adobe.com/en/docs/experience-manager-guides/using/release-info/aem-guides-releases-roadmap).

## Cloud Manager {#cloud-manager}

[여기](/help/implementing/cloud-manager/release-notes/current.md)에서 Cloud Manager 월별 릴리스의 전체 목록을 찾을 수 있습니다.

## 마이그레이션 도구 {#migration-tools}

[여기](/help/journey-migration/release-notes/release-notes-migration-tools-current.md)에서 마이그레이션 도구의 전체 목록을 찾을 수 있습니다.
