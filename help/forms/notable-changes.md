---
title: AEM 6.5 Forms과 AEM 클라우드 서비스 간에 변경된 사항
description: Experience Manager Forms 사용자로서 Adobe Experience Manager Forms as a Cloud Service으로 업그레이드하려고 합니까? Cloud Service으로 업그레이드하거나 마이그레이션하기 전에 가장 눈에 띄는 변경 사항에 대해 알아봅니다.
contentOwner: khsingh
exl-id: 46fcc1b4-8fd5-40e1-b0fc-d2bc9df3802e
source-git-commit: 7163eb2551f5e644f6d42287a523a7dfc626c1c4
workflow-type: tm+mt
source-wordcount: '1214'
ht-degree: 5%

---

# 기존 Adobe Experience Manager Forms 사용자의 주요 변경 사항  {#notable-changes-for-existing-AEM-Forms-users}

Adobe Experience Manager Forms은 Adobe Experience Manager FormsOn-Premise 및 [!DNL Adobe-Managed Service] 환경. 주요 차이점은 아래에 나와 있습니다.

* 이 서비스는 로컬 및 클라우드 기반의 개발 환경을 제공합니다. 을(를) 사용할 수 있습니다 [로컬 개발 환경](setup-local-development-environment.md) 클라우드 환경에 이러한 자산을 배포하기 전에 사용자 지정 코드, 구성 요소, 템플릿, 테마, 응용 Forms 및 기타 자산을 개발하고 테스트하려면 다음을 수행하십시오. 개발 프로세스를 가속화하는 데 도움이 됩니다.
* [!DNL AEM] 는 내장 CDN과 함께 Cloud Service이 제공됩니다. 주요 목적은 브라우저 근처 가장자리에 CDN 노드에서 캐시 가능 콘텐츠를 전달하여 지연 시간을 줄이는 것입니다. AEM 애플리케이션 최적의 성능을 위해 완벽하게 관리 및 구성됩니다.
* 클라우드 기본 환경에는 웹 콘솔(구성 관리자)이 없습니다. 다음을 사용할 수 있습니다 [[!DNL AEM Forms] 구성을 생성할 as a Cloud Service SDK](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/deploying/configuring-osgi.html?lang=en#generating-osgi-configurations-using-the-aem-sdk-quickstart) 및에 대한 CI/CD 파이프라인 [구성 배포](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/deploy-code.html?lang=en#deployment-process) Cloud Service 인스턴스에 매핑해야 합니다.

* 현지화된 적응형 Forms의 URL 규칙은 이제 URL에서 로케일 지정을 지원합니다. 새 URL 규칙을 사용하면 Dispatcher 또는 CDN에 현지화된 양식을 캐싱할 수 있습니다. Cloud Service 환경에서 URL 형식을 사용합니다 `http://host:port/content/forms/af/<afName>.<locale>.html` 를 입력하여 대신 현지화된 적응형 양식 버전을 요청합니다. `http://host:port/content/forms/af/afName.html?afAcceptLang=<locale>`. Adobe은 Dispatcher 또는 CDN 캐싱을 사용하는 것을 권장합니다. 미리 입력된 양식의 렌더링 속도를 개선하는 데 도움이 됩니다.
* 미리 채우기 서비스는 클라이언트의 적응형 양식과 데이터를 병합합니다. 적응형 양식을 미리 채우는 데 필요한 시간을 개선하는 데 도움이 됩니다. 항상 Adobe Experience Manager FormsServer에서 병합 작업을 실행하도록 구성할 수 있습니다.
* 이메일은 기본적으로 HTTP 및 HTTP 프로토콜만 지원합니다. [지원 팀에 문의](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/development-guidelines.html#sending-email) 전자 메일 전송을 위한 포트를 활성화하고 환경에 대해 SMTP 프로토콜을 사용하도록 설정합니다.
* Adobe Experience Manager Forms은 as a Cloud Service AEM 프로젝트에 많은 새로운 기능과 가능성을 제공합니다. 그러나 AEM Cloud Service과 호환되도록 Adobe Experience Manager Maven 프로젝트에 필요한 몇 가지 변경 사항이 있습니다. 높은 수준에서 AEM은 가변 콘텐츠와 변경할 수 없는 컨텐츠 간의 분할을 준수하기 위해 콘텐츠와 코드를 개별 하위 패키지로 분리해야 합니다. 를 사용하십시오 [Repository Modernizer](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/refactoring-tools/repo-modernizer.html) Adobe Experience Manager as a Cloud Service에 대해 정의된 프로젝트 구조와 호환되도록 컨텐츠 및 코드를 개별 패키지로 분리하여 기존 프로젝트 패키지를 재구성하는 도구입니다.

<!--  If your Cloud Configuration contains a secret (password), create a separate Cloud Configuration for every Author instance (Developer, Stage, and Production). If a Cloud Configuration is also required on Publish instances, publish/replicate a separate Cloud Configuration for every Publish instance (Developer, Stage, and Production). 

* When you create a Cloud Configuration that contains a secret, each Cloud Service instance (Developer, Stage, and Production) uses its own encryption key to encrypt the password before storing it. So, manually create such Cloud Configuration for every Cloud Service instance (Developer, Stage, and Production). Also, do not store secrets used in a Cloud Configuration to your Cloud Manager Git repository.

* Use [!DNL Cloud Manager] [APIs to convert and provide your passwords as secrets](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/deploying/configuring-osgi.html?lang=en#setting-values-via-api). Do not store plain text password or secrets on your environments. -->

* 암호, 개인 API 키 또는 기타 값과 같은 보안 OSGi 구성 값에 환경별 구성을 사용합니다. 보안상의 이유로 Git에 저장할 수 없습니다. [보안 환경별 구성을 사용하여 단계 및 프로덕션을 포함하여 모든 Adobe Experience Manager as a Cloud Service 환경에 기밀에 대한 값을 저장합니다](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/deploying/configuring-osgi.html?lang=en#when-to-use-secret-environment-specific-configuration-values).

Adobe Experience Manager as a Cloud Service의 변경 사항에 대한 포괄적인 목록이 필요하면 [새로운 기능 및 차이점](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/overview/what-is-new-and-different.html).

<!-- ## Feature comparison {#comparison}

[!DNL AEM Forms] as a Cloud Service and Experience Manager 6.5 Forms share a common set of features: Adaptive Forms, data integration, integration with [!DNL Adobe Sign], themes, templates, and forms management interface are identical. You can easily port your existing Adaptive Forms from an Experience Manager 6.5 Forms or an earlier version to [!DNL AEM Forms] as a Cloud Service.

### Features of AEM 6.5 Forms and [!DNL AEM Forms] as a Cloud Service {#feature-comparison}

The following table lists the major features of Experience Manager 6.5 Forms and provides information about whether the feature is partially or fully supported in [!DNL AEM Forms] as a Cloud Service, with a link to more information about the feature. The table also lists extra features available in [!DNL AEM Forms] as a Cloud Service.


| Feature/Capability | AEM 6.5 Forms | [!DNL AEM Forms] as a Cloud Service |
| - | - | - |
| Adaptive Forms | &#x2611; | &#x2611; |
| Data Integration | &#x2611; | &#x2611;(With some changes) |
| Automated Forms Conversion Service | &#x2611; | &#x2611; |
| Integration with Adobe Sign | &#x2611; | &#x2611;(With some changes) |
| Themes and Templates | &#x2611; | &#x2611; ([With some changes](themes.md#difference-in-themes))|
| Rule editor | &#x2611; | &#x2611; (With some changes) |
| Forms Portal | &#x2611; | --- |
| Integration with Adobe Analytics | &#x2611; | &#x2612; |
| Document Security | &#x2611; | &#x2612; | -->

<!-- ## New features {#comparison} -->



## 주요 개선 사항 {#whats-new}

<!-- [!DNL AEM Forms] as a Cloud Service offers benefits like auto-scaling, cost-effectiveness, zero downtime for upgrades, and cloud-native development environment and more. The list does not stop here. The following features are are start and are available only for [!DNL AEM Forms] as a Cloud Service: -->

다음 기능 및 개선 사항은 [!DNL AEM Forms] as a Cloud Service:

**향상된 시각적 규칙 편집기**
그 서비스는 경화된 것을 제공한다 [시각적 규칙 편집기](rule-editor.md#visual-rule-editor). 이 서비스는 사용 가능한 규칙을 작성하는 데 도움이 되도록 시각적 규칙 편집기에 다음 기능을 추가했습니다.

* [새 제출 이벤트](working-with-adobe-sign.md#available-operator-types-and-events-in-rule-editor): `Navigation`, `Step Completion`, `Successful Submission`, 및 `Error`

* [새 데이터 유형 `scope`](rule-editor.md#custom-functions). 를 사용할 수 있습니다 `scope` 양식의 전체 범위를 전달하기 위한 사용자 지정 함수에 데이터 형식을 입력합니다.

* 사용 기능 [@this 를 사용하여 사용자 지정 함수에 JSDoc를 지정합니다.](rule-editor.md#custom-functions). 활성 구성 요소에서 @this 를 사용하여 사용자 지정 함수를 호출할 수 있습니다.

* 속성 기반 규칙에 대한 조건을 추가하는 기능.

**핵심 구성 요소**
다음 [핵심 구성 요소](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=ko-KR) 는 개발 시간을 단축하고 유지 관리 비용을 절감할 수 있도록 AEM용 표준화된 WCM(Web Content Management) 구성 요소 세트입니다. [!DNL AEM Forms] as a Cloud Service 지원 **[!UICONTROL AEM Forms 컨테이너]** 코어 구성 요소. 구성 요소를 사용하여 적응형 양식을 AEM Sites 페이지에 포함할 수 있습니다.

**AEM Archetype for Forms as a Cloud Service**
[AEM Archetype](https://github.com/adobe/aem-project-archetype/releases/tag/aem-project-archetype-27) 은 다음에 대한 개발을 시작하는 데 도움이 됩니다. [!DNL AEM Forms] as a Cloud Service. Archetype 버전 27 이상을 사용하여 와 호환되는 프로젝트 템플릿을 만들 수 있습니다 [!DNL AEM Forms] as a Cloud Service 환경. Archetype에는 빠르게 시작할 수 있도록 몇 가지 샘플 테마 및 템플릿이 포함되어 있습니다.

**양식 및 Sign 간의 보안 및 향상된 정보 흐름**
[적응형 Forms 및 Adobe Sign 통합](working-with-adobe-sign.md) Cloud Service에서 데이터 및 서명 활동을 동시에 제출할 수 있습니다. 서명 상태 포장과 상관없이 양식을 제출함으로써 보다 신속하게 제출할 수 있습니다. 또한 이 서비스에서는 서명 프로세스를 안전하게 만드는 Cloud Service 인스턴스에 데이터를 저장하지 않습니다.

**모범 사례 분석기 및 마이그레이션 툴**
모범 사례 분석기는 현재 AEM 구현에 대한 평가를 제공합니다. 전에 도구 실행 [Forms as a Cloud Service으로 마이그레이션](migrate-to-forms-as-a-cloud-service.md). 기존 Adobe Experience Manager(AEM) 배포에서 AEM as a Cloud Service으로 이동할 준비를 처리합니다.

이 서비스는 또한 [향상된 마이그레이션 경험](migrate-to-forms-as-a-cloud-service.md) 을 통해 [!DNL AEM 6.4 Forms] 및 [!DNL AEM 6.5 Forms] to [!DNL AEM Forms] as a Cloud Service.

**더 빠른 양식 변환 및 빠른 서버측 유효성 검사**
이 서비스는 CDN 및 Dispatcher 캐싱을 사용하여 적응형 Forms에 대한 빠른 표현물과 서버측 유효성 검사를 제공합니다.

**향상된 CAPTCHA**
이제 다음을 수행할 수 있습니다 [CAPTCHA 유효성 검사](captcha-adaptive-forms.md) 적응형 양식 제출 또는 비즈니스 논리에 따라 선택할 수 있습니다. 사용자 작업에서 CAPTCHA의 유효성을 검사하는 조건을 추가하고 규칙을 기반으로 적응형 양식에 CAPTCHA 구성 요소를 표시하거나 숨길 수도 있습니다.

CAPTCHA 구성 요소는 Google reCAPTCHA와 기본적으로 통합됩니다. 필요한 경우 구성 요소에 대해 더 많은 CAPTCHA 서비스를 구성할 수도 있습니다.

**레코드 문서에 대한 여러 마스터 페이지**
이제 페이지 매김 옵션이 있는 레코드 문서에서 기록 문서의 각 페이지에 대해 다른 마스터 페이지를 사용하고 적응형 양식 패널의 배치를 제어할 수 있습니다.

**헤드리스 테이블에 열 추가**
머리글 없이 테이블에 열을 추가하고 삭제할 수 있습니다. 열을 추가 및 삭제하는 데 도움이 되도록 숨겨진 머리글이 해당 테이블에 추가됩니다. 이러한 헤더는 작성 중에 볼 수 있지만 게시된 양식에 숨겨진 상태로 유지됩니다. 헤더가 없는 테이블은 대부분 Automated forms conversion 서비스를 사용하여 만든 적응형 Forms에서 찾을 수 있습니다.

**향상된 제출 작업**
를 사용할 수 있습니다 [이메일 보내기](configuring-submit-actions.md#send-email#send-email) 작업을 제출하여 레코드 문서(DoR) PDF을 첨부 파일로 보냅니다.

**워크플로우에 대한 전자 메일 그룹**
선택할 수 있습니다 [알림 이메일 보내기](aem-forms-workflow-step-reference.md#assign-task-step) 작업 지정 단계에서 개인 또는 그룹에 이르기까지

**향상된 양식 데이터 모델 호출 단계**
이제 양식 데이터 모델 호출 단계에서 입력 서비스 인수의 페이로드에 대한 상대 옵션 폴더 경로를 지정할 수 있습니다. 이렇게 하면 정확한 파일 이름을 지정하지 않고 지정된 폴더에 있는 파일을 서비스 인수에 매핑하는 데 도움이 됩니다.

**번역 파일의 가독성이 개선됨**
Forms as a Cloud Service에서 적응형 양식의 필드 및 패널의 읽기 순서와 해당 번역 파일(.XLIFF 파일)의 메시지 키는 비슷한 구조를 갖습니다. 수동 번역 속도를 향상시키는 데 도움이 됩니다.

<!-- ## Feature comparison {#feature-comparison}

[!DNL AEM Forms] as a Cloud Service and [!DNL AEM 6.5 Forms] share some features like Adaptive Forms, Data Integration, and Forms Portal. You can easily port your existing Adaptive Forms from an [!DNL AEM 6.5 Forms] or an earlier version to [!DNL AEM Forms] as a Cloud Service.

### Features of [!DNL AEM 6.5 Forms] and [!DNL AEM Forms] as a Cloud Service {#aem-6.5-vs-aem-forms-as-a-cloud-service}

The following table lists the major features of [!DNL AEM 6.5 Forms] and provides information about the features coming soon to [!DNL AEM Forms] as a Cloud Service:

| Feature/Capability | AEM 6.5 Forms  | [!DNL AEM Forms] as a Cloud Service |
|---|---|---|
| Cloud-native architecture | &#x2612; | &#x2611;  |
| Auto-scaling based on load | &#x2612; | &#x2611;  |
| Zero downtime for upgrades | &#x2612; | &#x2611;  |
| Feature roll-out frequency | Quarterly | Agile*  |
| CDN (content delivery network) included | &#x2612; | &#x2611;  |
| Topologies optimized for maximum resilience and efficiency | &#x2612; | &#x2611;  |
| Cloud-native development environment | &#x2612; | &#x2611;  |
| Self-Service via Cloud Manager | &#x2612; | &#x2611;  |
| Automated upgrades with Continuous Integration and Continuous Delivery (CI/CD)| &#x2611; | &#x2611;  |
| Adaptive Forms | &#x2611; | &#x2611; |
| Data Integration | &#x2611; | &#x2611; |
| Automated Forms Conversion Service | &#x2611; | &#x2611; |
| Integration with [!DNL Adobe Sign] | &#x2611; | &#x2611; |
| Integration with [!DNL AEM Sites] | &#x2611; | &#x2611; |
| Enhanced Visual Rule editor | &#x2612; | &#x2611; |
| Forms Portal | &#x2611; | Coming Soon |
| Integration with [!DNL Adobe Analytics] | &#x2611; | Coming Soon |
| Integration with [!DNL Adobe Target] | &#x2611; | Coming Soon |
| Document Security | &#x2611; | &#x2612; |

`*` New features every month and bug fix updates on daily basis.

For a comprehensive list of changes in AEM as a Cloud Service, See [What is New and What is Different](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/overview/what-is-new-and-different.html) and [Notable changes in [!DNL AEM Forms] as a Cloud Service](notable-changes.md) -->
