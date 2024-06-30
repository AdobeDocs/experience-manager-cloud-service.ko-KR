---
title: ' [!DNL Adobe Experience Manager] as a Cloud Service 최신 릴리스 정보'
description: 의 최신 릴리스 정보 [!DNL Adobe Experience Manager] As a Cloud Service
mini-toc-levels: 1
exl-id: a2d56721-502c-4f4e-9b72-5ca790df75c5
source-git-commit: 9d0ef963dfe2d81da09a7195540de87245e71a67
workflow-type: tm+mt
source-wordcount: '1932'
ht-degree: 42%

---

# [!DNL Adobe Experience Manager] as a Cloud Service 최신 릴리스 정보 {#release-notes}

다음 섹션에서는 [!DNL Experience Manager] as a Cloud Service의 최신 버전 기능 릴리스 정보에 대해 간략히 소개합니다.

>[!NOTE]
>
>여기에서 2022 또는 2023과 같은 이전 버전의 릴리스 정보로 이동할 수 있습니다.
>
>[!DNL Experience Manager] as a Cloud Service의 향후 기능 활성화에 대해 알아보려면 [Experience Manager 릴리스 로드맵](https://experienceleague.adobe.com/ko/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap)을 살펴보십시오.

>[!NOTE]
>
>릴리스와 직접적으로 관련되지 않는 설명서 업데이트의 세부 정보는 [최신 설명서 업데이트](https://experienceleague.adobe.com/ko/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates)를 참조하십시오.

## 릴리스 일자 {#release-date}

의 릴리스 날짜 [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] 현재 기능 릴리스(2024.6.0)는 2024년 6월 27일입니다. 다음 기능 릴리스(2024.7.0)는 2024년 7월 25일에 예정되어 있습니다.

## 유지 관리 릴리스 정보 {#maintenance}

[ 여기](/help/release-notes/maintenance/latest.md)에서 최신 유지 관리 릴리스 정보를 확인할 수 있습니다.

<!--  ## Release Video {#release-video}

Have a look at the June 2024 Release Overview video for a summary of the features added in the 2024.6.0 release:

>[!VIDEO](https://video.tv.adobe.com/v/3429503?quality=12)

-->

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### Experience Manager Sites의 새로운 기능 {#new-feature-sites}

**RUM(Real Use Monitoring) 데이터 서비스** {#real-use-monitoring}

다음 [RUM(Real Use Monitoring) 데이터 서비스](https://git.corp.adobe.com/AdobeDocs/experience-manager-cloud-service.en/blob/shwetad-patch-1/help/implementing/cloud-manager/content-requests.md#real-user-monitoring-for-aem-as-a-cloud-service) 는 이제 일반적으로 사용할 수 있으며, AEM as a Cloud Service에 대해 클라이언트측 데이터 수집을 활성화합니다. 이 서비스는 사용자 상호 작용을 보다 정확하게 반영하여 웹 사이트 참여에 대한 신뢰할 수 있는 측정을 보장합니다. 이는 고객에게 페이지 트래픽 및 성능에 대한 고급 통찰력을 제공하여 페이지 성능을 이해하고 향상시킬 수 있는 귀중한 기회를 제공합니다.

### 얼리 어답터 프로그램 {#sites-early-adopter}

**변형 생성**

이제 클라우드 서비스에서 액세스 가능한 AEM의 새로운 기능인 [변형 생성](/help/generative-ai/generate-variations.md)을 통해 GenAI를 활용할 수 있습니다. 변형 생성은 생성형 AI를 사용하여 콘텐츠 제작을 생성하고 확장하는 데 도움이 됩니다. 프로그램 참여를 고려한다면 Adobe 계정 팀에 문의하십시오.

**콘텐츠 조각 콘솔에서 자산 찾아보기**

이제 콘텐츠 작성자는 콘텐츠 조각 콘솔을 종료하지 않고도 이미지 및 기타 자산을 찾아보고, 보고, 작업을 수행할 수 있습니다.

![자산 찾아보기](/help/sites-cloud/administering/content-fragments/assets/cf-console-assets-browse.png)

기능을 사용해 보고 피드백을 공유하고 싶으십니까? 공식 이메일 ID로 aemcs-headless-adopter@adobe.com에 이메일을 보내 얼리 어답터 프로그램에 대해 자세히 알아보십시오.

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### Experience Manager Assets의 새로운 기능 {#new-features-assets}



**Content Hub**

Content Hub은 조직 및 비즈니스 파트너를 위한 온브랜드 콘텐츠에 대한 액세스를 민주화하기 위해 Experience Manager Assets as a Cloud Service의 일부로 사용할 수 있습니다. Content Hub을 사용하면 자산을 쉽게 찾아 배포하고, 새로운 브랜드 내 변형을 재사용 및 만들 수 있으며, 규모에 맞게 활성화를 가속화할 수 있습니다.

![Content Hub 사용자 인터페이스](/help/release-notes/assets/content-hub-ui.png)

**OpenAPI 기능이 포함된 Dynamic Media**

OpenAPI 기능이 포함된 Dynamic Media은 Adobe 및 서드파티 애플리케이션에서 DAM을 확장하여 에셋 선택기 또는 OpenAPI 스택을 통해 모든 채널에서 브랜드로 승인된 디지털 에셋에 액세스할 수 있습니다. 주요 개념 - 바이너리 복제본이 없으며 에셋이 최적화 및 변환되어 빠른 성능을 보장받고 에셋을 공개하거나 안전하게 제공할 수 있습니다.

![새 Dynamic Media 데이터 흐름 다이어그램](/help/assets/assets/dm-openapi-dfd.png)


### Assets 보기의 새로운 기능 {#assets-view-new-features}

**Assets Insights 대시보드에서 더 많은 옵션을 사용할 수 있습니다**

이제 Assets Insights 대시보드에서 자산 유형 및 크기별 자산 개수를 사용할 수 있습니다. 이러한 옵션은 Assets 보기 환경에서 실시간 데이터를 제공합니다. 크기 범위 및 에셋 유형별로 에셋의 개수 및 비율을 자세히 설명합니다.

**포함된 Adobe Express 편집기 업데이트**

* 새 버전으로 저장하는 것과 비교하여 새 에셋으로 저장하는 것에 대한 사용자 경험이 개선되었습니다.

* 다중 페이지 PDF 및 이미지 형식 모두로 다중 페이지 Express 문서(이전에는 단일 페이지만 지원됨)를 내보냅니다. 이미지 형식을 선택하면 각 페이지가 다운스트림 배포를 위해 DAM에 개별 자산으로 저장됩니다.

* 에셋을 저장하는 동안 저장 대화 상자에서 메타데이터 추가를 지원합니다.

<!--


**Content Credentials**

Content Credentials feature in Assets view now provides detailed asset provenance data adhered to an asset. This helps to trace the enroute edits along the asset's lifecycle to prevent users from deception through deliberately tempered assets. This ensures content authenticity among users and fosters trust through transparency.

When looking at the asset details, any image with content credentials added, such as those created with GenAI, displays the manifest details in a dedicated panel. If the asset is downloaded, published, or shared, the credentials remain intact with the asset.

![check publish status1](/help/release-notes/assets/content-credentials.png)

-->

## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

<!-- 

* **Configure a shard for Adobe Sign for AEM Forms**: Adobe distributes Acrobat Sign API around the globe in many deployment units called "shards." Each shard serves a customer's account, such as NA1, NA2, NA3, EU1, JP1, AU1, IN1, and others. The shard names correspond to geographic locations. You can now use more than one shard while using Adobe Sign integration with AEM Forms. 

-->

### AEM Forms의 새로운 기능 {#forms-new-prerelease-features}

#### 핵심 구성 요소 기반의 적응형 양식을 위한 향상된 시각적 규칙 편집기

이 릴리스에서는 핵심 구성 요소 기반의 적응형 양식에 대한 시각적 규칙 편집기를 크게 업그레이드했습니다. 이제 다음을 수행할 수 있습니다.

* 시각적 규칙 편집기에서 규칙을 만들어 다음을 수행할 수 있습니다. [기본 양식 제출 성공/실패 메시지 재정의](/help/forms/create-and-use-custom-functions.md#use-case-override-form-submission-success-and-error-handlers).

* 적응형 양식 규칙 편집기에서 [WHEN 작업을 위해 다양한 유형의 필드를 선택](/help/forms/rule-editor-core-components.md#allowed-multiple-fields-in-when)할 수 있는 기능이 추가되었습니다.

* 이제 양식 작성자가 사용자 정의 기능을 적용하여 [제출 전에 데이터를 전처리](/help/forms/create-and-use-custom-functions.md#use-case-submit-altered-data-to-the-server)할 수 있습니다.

* [**초안으로 저장**](/help/forms/save-core-component-based-form-as-draft.md) 기능을 사용하여 부분적으로 완료된 양식을 나중에 제출할 수 있도록 저장합니다. 이 기능은 사용자가 양식 작성을 중단하고 나중에 다시 와야 하는 시나리오에서 유용합니다.

### AEM Forms의 얼리 액세스 기능 {#forms-new-early-access-features}

AEM Forms 조기 액세스 프로그램 은 다른 사람들보다 먼저 최신 혁신 기술에 독점적으로 액세스하고 개발을 구체화할 수 있는 특별한 기회를 제공합니다. 이 프로그램은 여러 혁신에 액세스할 수 있습니다.

이 릴리스 노트는 현재 릴리스에 제공된 혁신적인 기능을 나열합니다. 얼리 액세스 프로그램에서 사용할 수 있는 전체 혁신 목록은 [AEM Forms 얼리 액세스 프로그램 설명서](/help/forms/early-access-ea-features.md)를 참조하십시오.

#### 향상된 봇 보호 방법

AEM Forms는 널리 사용되는 두 가지 CAPTCHA 솔루션인 Cloudflare Turnstile 및 hCaptcha에 대한 지원을 추가하여 보안 기능을 강화했습니다. 이 기능은 기존 Google reCAPTCHA를 보완하여 사용자에게 추가 옵션을 제공합니다. 봇과 스팸 제출로부터 양식을 보호하는 유연성을 향상시킵니다.

* **Cloudflare 턴스타일**: 이 마찰 없는 CAPTCHA는 명시적인 상호 작용이 필요하지 않은 간단한 문제를 통해 사용자를 확인합니다. 양식에 완벽하게 통합되어 사용자 경험을 향상시킵니다.
* **hCaptcha**: 개인 정보 보호에 중점을 둔 이 CAPTCHA는 데이터 개인 정보 보호에 초점을 맞춘 사용자 친화적인 대안을 제공합니다. 보안과 사용자 경험 사이의 균형을 맞추는 것을 목표로 합니다.
* **Google reCAPTCHA**: AEM Forms는 reCAPTCHA v2와 reCAPTCHA Enterprise를 지속적으로 지원하여 안정적이고 잘 정립된 솔루션을 제공합니다.

AEM Forms는 다양한 CAPTCHA 옵션을 제공하여 특정 요구 사항에 가장 적합한 솔루션을 선택할 수 있도록 지원합니다.

이러한 CAPTCHA 솔루션을 적응형 Forms과 통합할 준비가 되셨습니까? Adobe 설명서는 각각에 대한 자세한 지침을 제공합니다. [Cloudflare 턴스타일](https://experienceleague.adobe.com/ko/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-core-components/create-an-adaptive-form-on-forms-cs/integrate-adaptive-forms-turnstile-core-components), [Captcha](https://experienceleague.adobe.com/ko/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-core-components/create-an-adaptive-form-on-forms-cs/integrate-adaptive-forms-hcaptcha-core-components), 및 [Google recaptcha](https://experienceleague.adobe.com/ko/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-core-components/create-an-adaptive-form-on-forms-cs/captcha-adaptive-forms-core-components).


### Forms 서비스

Forms 서비스는 데이터 캡처를 위한 대화형 PDF 양식을 생성합니다. 또한 기존의 대화형 PDF 양식으로 데이터를 가져오거나 내보내고 제출된 데이터를 검증하는 데 사용할 수 있습니다. 기능의 분류는 다음과 같습니다.

* **Forms 렌더링**: AEM Forms Designer를 사용하여 작성한 템플릿과 선택적으로 XML 데이터에서 대화형 PDF 양식을 생성합니다. 이 기능은 선택적으로 데이터로 미리 채워진 입력 가능한 PDF 양식을 생성합니다.
* **데이터 추출 및 가져오기**: 기존 PDF 양식으로 데이터를 가져올 뿐만 아니라 채워진 PDF 양식에서 데이터를 추출할 수 있습니다. XDP 및 XML 데이터 형식이 모두 지원되며, XFA가 아닌 PDF 형식(AcroForms라고도 함)으로 가져오기는 FDF 및 XFDF 데이터를 추가로 지원합니다.
* **데이터 유효성 검사**: AEM Forms Designer를 사용하여 만든 템플릿에 대해 XDP 또는 XML 형식으로 제출된 데이터의 유효성을 검사합니다.

>[!IMPORTANT]
>
> 초기 액세스 혁신을 위해 Adobe의 초기 액세스 프로그램에 참여하고자 하는 경우 공식 주소에서 다음으로 이메일을 보내면 됩니다. [aem-forms-ea@adobe.com](mailto:aem-forms-ea@adobe.com) 액세스 권한 요청. 전체 또는 특정 혁신에 대한 액세스를 요청할 수 있습니다.


## [!DNL Experience Manager] as a [!DNL Cloud Service] Foundation {#foundation}

### 콘텐츠 상태 관련 작업 센터 알림 얼리 어답터 프로그램 {#actions-center-notifications}

[작업 센터](/help/operations/actions-center.md) 중요한 인시던트가 발생하거나 사전 조치를 취해야 하는 코드 또는 구성에 대해 인지된 경우 이메일 알림을 보냅니다. 이제 Adobe에 콘텐츠 상태와 관련된 몇 가지 새로운 유형의 알림이 도입되었습니다. 이 기능은 얼리어답터 프로그램을 통해 사용할 수 있습니다. 참여하려면 Adobe 고객 지원 센터에 문의하십시오.

#### 페이지에 많은 노드가 포함됨 {#page-nodes}

노드가 많으면 렌더링 성능이 저하되고 페이지 로드 시간이 단축될 수 있습니다. 페이지에서 많은 노드가 감지되면 작업 센터를 통해 사전 알림을 받아 페이지 내의 총 노드 수를 줄이는 데 필요한 단계를 수행할 수 있습니다.

#### 실행 중인 많은 워크플로 인스턴스 {#running-workflows}

작성 환경에서 실행 중인 워크플로가 많을 경우 워크플로 엔진 성능이 영향을 받습니다. 실행 중인 워크플로 인스턴스가 많이 감지되면 작업 센터를 통해 사전 알림을 받게 됩니다. 이 프로세스를 사용하면 불필요한 실행 중인 워크플로우를 종료하도록 제거 작업을 구성할 수 있습니다.

#### 사용자 정의 그룹에 직접 추가된 사용자 {#users-customgroups}

사용자가 사용자 정의 그룹에 직접 추가되면 작업 센터를 통해 사전 알림을 받습니다. 이 프로세스를 사용하면 관련 IMS 그룹에 사용자를 추가한 다음 해당 IMS 그룹을 AEM 그룹의 구성원으로 포함하여 IMS 모범 사례를 따를 수 있습니다.

#### 누락된 JCR 콘텐츠 {#jcr-content}

JCR 콘텐츠 누락이 감지되면 작업 센터에서 이를 미리 알려줍니다. 이 접근 방식을 사용하면 누락된 콘텐츠를 추가하고 특정 AEM Assets 기능의 실패를 방지할 수 있습니다.

#### 완료된 워크플로가 삭제되지 않음 {#workflows}

Actions Center는 90일 이상 경과한 완료된 워크플로우가 삭제되지 않은 경우 이를 미리 알려줍니다. 이 접근 방식은 워크플로 인스턴스의 수를 줄여 워크플로 엔진의 성능을 개선하는 데 도움이 됩니다.

#### Sling 리소스 누락 {#sling-resource}

작업 센터에서는 누락된 Sling 리소스가 감지되면 이를 미리 알려줍니다. 이 접근 방식을 사용하면 누락된 리소스를 추가하고 특정 AEM Assets 기능의 실패를 방지할 수 있습니다.

### 컨텐츠 전달 관련 얼리 어답터 프로그램 {#foundation-early-adopter}

이메일 **<aemcs-cdn-config-adopter@adobe.com>**, 아래의 얼리 어답터 프로그램 중 관심 있는 프로그램을 나타냅니다.

#### CDN에서의 기본 인증(얼리 어답터 프로그램) {#basicauth-cdn}

Protect 사용자 이름과 암호가 필요한 기본 인증 대화 상자를 열어 특정 콘텐츠 리소스를 확인합니다. 이 기능은 최종 사용자 액세스 권한을 위한 포괄적인 솔루션 역할보다는 비즈니스 이해 당사자의 콘텐츠 검토와 같은 가벼운 인증 사용 사례를 주요 대상으로 합니다. 보안 유형 Cloud Manager 환경 변수를 참조하여 구성 파이프라인을 통해 배포되는 git의 구성 파일을 통해 관리되는 사용자 이름 및 암호 목록입니다. [자세히 알아보기](/help/implementing/dispatcher/cdn-credentials-authentication.md#basic-auth).

#### 셀프서비스 API 키를 사용하여 CDN에서 컨텐츠 제거(조기 채택자 프로그램) {#purge-cdn}

셀프서비스 방식으로 CDN 삭제 API 키를 등록하고, 이를 사용하여 전역적으로 또는 하나 이상의 리소스에 대해 CDN의 콘텐츠를 무효화합니다. [자세히 알아보기](/help/implementing/dispatcher/cdn-cache-purge.md).

<!-- Email **<aemcs-cdn-config-adopter@adobe.com>** with a request to be an early adopter. -->

#### BYOCDN(Customer-Managed CDN)을 위한 X-AEM-Edge-Key 셀프서비스 생성(얼리어답터 프로그램) {#byocdn-keys}

이전에는 고객 관리형 CDN 구성에 필요한 X-AEM-Edge-Key를 생성하려면 지원 티켓이 필요했습니다. 이제 구성 파이프라인을 사용하여 배포되는 구성 파일을 통해 셀프서비스 방식으로 이러한 결과를 수행할 수 있으므로 새 환경 온보딩에 대한 지연을 제거할 수 있습니다. [자세히 알아보기](/help/implementing/dispatcher/cdn-credentials-authentication.md#CDN-HTTP-value).

<!-- Email **<aemcs-cdn-config-adopter@adobe.com>** with a request to be an early adopter. -->

#### 클라이언트측 리디렉션(얼리 어답터 프로그램) {#client-side-redirects-early-adopter}

소스 제어에서 301/302 클라이언트측 리디렉션을 구성하고 CDN에 배포합니다. [자세히 알아보기](/help/implementing/dispatcher/cdn-configuring-traffic.md#client-side-redirectors).<!-- and join the early adopter program by emailing **<aemcs-cdn-config-adopter@adobe.com>**. --> 요청 및 응답 변환, AEM 외부 사이트로의 라우팅 트래픽 등 [CDN 구성](/help/implementing/dispatcher/cdn-configuring-traffic.md)과 관련하여 이미 사용 가능한 여러 다른 기능이 있습니다.

#### 트래픽 필터 규칙 경고(얼리 어답터 프로그램) {#traffic-filter-rules-alerts-early-adopter}

선택적으로 라이선스를 부여할 수 있는 WAF(웹 애플리케이션 방화벽) 규칙을 포함하는 최근 릴리스된 [트래픽 필터 규칙](/help/security/traffic-filter-rules-including-waf.md)을 통해 허용하거나 거부해야 하는 트래픽을 구성할 수 있습니다.

얼리 어답터 프로그램에 참여하면 트래픽 필터 규칙이 실행될 때마다 알림을 받을 수 있습니다. Actions Center 이메일 알림은 특정 트래픽 상태가 발생할 때 사용자에게 계속 알려주므로 적절한 조치를 취할 수 있습니다.

#### 비즈니스 사용자는 Git(얼리 어답터 프로그램) 외부에서 리디렉션을 선언할 수 있습니다. {#apache-rewritemaps-early-adopter}

AEM 6.5와 마찬가지로 Apache/Dispatcher는 게시 저장소의 특정 위치에 배치된 재작성 맵을 수집하여 웹 계층 파이프라인 실행 없이도 로드할 수 있습니다. 이 접근 방식을 사용하면 비즈니스 사용자가 ACS Commons 리디렉션 맵 관리자 또는 사용자 지정 애플리케이션과 같은 스프레드시트 또는 UI를 사용하여 리디렉션을 선언할 수 있습니다. <!-- Please reach out to **<aemcs-cdn-config-adopter@adobe.com>** for more information. -->

#### 동적 콘텐츠 로드를 위한 ESI(에지측 포함)(얼리 어답터 프로그램) {#esi-early-adopter}

이제 Adobe Managed CDN은 에지 수준 동적 웹 콘텐츠 어셈블리를 위한 마크업 언어인 [ESI(에지측 포함)](/help/implementing/dispatcher/edge-side-includes.md)를 지원합니다. ESI 스니펫을 포함하면 더 높은 TTL을 사용하여 CDN에서 전체 HTML 페이지를 캐싱하는 동시에 더 높은 케이던스 업데이트(낮은 TTL)가 필요한 작은 섹션을 출처에서 더 자주 가져올 수 있습니다. <!--Please reach out to **<aemcs-cdn-config-adopter@adobe.com>** for more information.-->

## [!DNL Experience Manager] 안내서 {#guides}

Adobe Experience Manager Guides 최신 릴리스의 새로운 기능 및 향상된 기능의 전체 목록을 확인할 수 있습니다 [여기](https://experienceleague.adobe.com/en/docs/experience-manager-guides/using/release-info/release-notes/cloud-release-notes/2024-releases/2406-release/whats-new-2024-06-0).

## Cloud Manager {#cloud-manager}

[여기](/help/implementing/cloud-manager/release-notes/current.md)에서 Cloud Manager 월별 릴리스의 전체 목록을 찾을 수 있습니다.

## 마이그레이션 도구 {#migration-tools}

[여기](/help/journey-migration/release-notes/release-notes-migration-tools-current.md)에서 마이그레이션 도구의 전체 목록을 찾을 수 있습니다.

## Experience Cloud 릴리스 정보 {#experience-cloud}

다른 Experience Cloud 애플리케이션 릴리스에 대한 정보는 [여기](https://experienceleague.adobe.com/ko/docs/release-notes/experience-cloud/current)에서 확인할 수 있습니다.
Experience Cloud 릴리스 정보의 업데이트에 대한 월별 이메일 알림을 받아 보려면 [Adobe 우선 순위 제품 업데이트](https://www.adobe.com/kr/subscription/priority-product-update.html)를 구독하십시오.
