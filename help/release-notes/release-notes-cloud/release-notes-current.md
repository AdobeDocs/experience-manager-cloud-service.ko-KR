---
title: ' [!DNL Adobe Experience Manager] as a Cloud Service 최신 릴리스 정보'
description: ' [!DNL Adobe Experience Manager] as a Cloud Service 최신 릴리스 정보'
mini-toc-levels: 1
exl-id: a2d56721-502c-4f4e-9b72-5ca790df75c5
feature: Release Information
role: Admin
source-git-commit: 07b957374dcc513050c48bb320e8d639385c3344
workflow-type: tm+mt
source-wordcount: '2350'
ht-degree: 91%

---

# [!DNL Adobe Experience Manager] as a Cloud Service 최신 릴리스 정보 {#release-notes}

다음 섹션에서는 [!DNL Experience Manager] as a Cloud Service의 최신 기능 릴리스 정보에 대해 간략히 소개합니다.

>[!NOTE]
>
>여기에서 2023년 또는 2024년과 같은 이전 버전의 릴리스 정보로 이동할 수 있습니다.
>
>[!DNL Experience Manager] as a Cloud Service의 향후 기능 활성화에 대해 알아보려면 [Experience Manager 릴리스 로드맵](https://experienceleague.adobe.com/ko/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap)을 살펴보십시오.

>[!NOTE]
>
>Experience Cloud 릴리스 정보의 업데이트에 대한 월별 이메일 알림을 받아 보려면 [Adobe 우선순위 제품 업데이트](https://www.adobe.com/kr/subscription/priority-product-update.html)를 구독하십시오.

## 릴리스 일자 {#release-date}

[!DNL Adobe Experience Manager] as a [!DNL Cloud Service]의 현재 기능 릴리스(2025.7.0) 일자는 2025년 8월 7일입니다. 다음 기능 릴리스(2025.8.0)는 2025년 8월 28일에 예정되어 있습니다.

## 유지 관리 릴리스 정보 {#maintenance}

[여기](/help/release-notes/maintenance/latest.md)에서 최신 유지 관리 릴리스 정보를 확인할 수 있습니다.

<!-- 

## Release Video {#release-video}

Have a look at the July 2025 Release Overview video for a summary of the features added in the 2025.7.0 release:

>[!VIDEO](https://video.tv.adobe.com/v/3440927?quality=12&captions=kor)

-->

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### Experience Manager Sites의 새로운 기능 {#enhancements-sites}

* 이제 참조된 조각(하위)이 있는 콘텐츠 조각을 한 번의 작업으로 복사할 수 있습니다. 이를 통해 기존 콘텐츠 조각 구조를 재사용하여 새로운 콘텐츠를 만들 수 있습니다.
* 콘텐츠 조각 관리자 UI에서 이제 콘텐츠 조각의 워크플로 상태를 확인할 수 있으며, 선택한 조각에 대한 과거 및 현재 실행 중인 워크플로에 대한 자세한 정보를 제공합니다.
* live copy 소스 페이지의 이름을 바꾸거나 이동하면 이제 해당 이름이 바뀌거나 이동된 live copy 페이지가 다시 게시됩니다.

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

**Dynamic Media 템플릿에 모양 추가**

이제 Experience Manager Assets에서 [Dynamic Media 템플릿에 모양 레이어를 추가](/help/assets/dynamic-media/dynamic-media-templates.md#add-shapes-to-the-canvas)할 수 있습니다. 이미지 및 텍스트 레이어와 유사하게 모양 레이어는 템플릿 URL을 통해 실시간 업데이트를 위한 매개변수를 지원합니다. 템플릿의 모양에 대한 콜 투 액션(CTA) 링크를 포함시킬 수도 있습니다.

![Dynamic Media 템플릿에 모양 추가](/help/assets/assets/enable-uniform-radius-shape.png)

**AI 생성 메타데이터의 개선 사항**

이제 AEM Assets를 사용하면 자산 찾아보기 페이지에서 [카드 보기 또는 목록 보기에서 자산 제목 표시를 구성](/help/assets/smart-tags.md#configure-ai-generated-titles)할 수 있습니다. 자산에 대한 기존 제목이 없는 경우에만 자신이 정의한 자산 제목을 표시하거나, AI를 사용하여 생성된 제목을 표시하거나, AI로 생성된 제목을 사용하도록 선택할 수 있습니다.

![AI로 생성된 제목 구성](/help/assets/assets/configure-title-ai-generated.png)

이제 폴더 수준에서 AI 생성 메타데이터를 비활성화하도록 선택할 수도 있습니다.

### Content Hub의 새로운 기능 {#new-features-content-hub}

**콘텐츠 허브의 향상된 브랜딩 유연성**

기존의 개인화 기능을 기반으로 Content Hub를 사용하면 관리자가 사용자 정의 로고 이미지를 추가하여 배포를 더욱 세부적으로 조정할 수 있습니다. 배너와 로고 이미지 모두에 TIFF 파일 형식에 대한 지원이 추가되어 디자인의 유연성이 더욱 높아졌습니다.

**제목 링크를 통한 더욱 스마트한 공유**

이제 자산 세부 정보 보기에서 또는 하나 이상의 자산을 선택한 후에 공유 링크를 생성할 때 제목을 추가할 수 있습니다. 이를 통해 수신자는 특히 여러 공유 자산을 수신할 때 각 링크의 목적을 쉽게 파악할 수 있습니다.

![비공개 및 공개 링크](/help/assets/assets/shared-link-for-assets.png)

**개선된 필터 탐색**

Content Hub에는 이제 필터 내에 **모두 표시** 옵션이 포함되어 있어 사용자는 현재 최대 10개의 패싯만 볼 수 있는 제한에서 자산 수와 함께 모든 사용 가능한 패싯을 볼 수 있습니다. 각 필터 내에서 향상된 검색 및 정렬 기능을 통해 자산을 보다 효율적으로 검색하고 관리할 수 있습니다.

### AEM 데스크탑 앱 릴리스 3.0.0 {#desktop-app-release-3.0.0}

새로운 파일 및 폴더의 자동 업로드, 향상된 파일 작업, 더욱 스마트해진 자산 검색, AEM과의 원활한 통합을 경험해 보십시오. 콘텐츠 관리가 더욱 빠르고 명확하고 직관적으로 이루어집니다.

전체 기능 목록을 보려면 [데스크탑 앱 릴리스 정보](https://experienceleague.adobe.com/ko/docs/experience-manager-desktop-app/using/release-notes)를 참조하십시오.

### OpenAPI 기능을 갖춘 Dynamic Media의 새로운 기능 {#new-features-dynamic-media-with-openapi}

**게시 전 자산 미리보기**

[!DNL Dynamic Media with OpenAPI capabilities]가 이제 자산을 공개적으로 제공하기 전에 [!DNL AEM Sites] 작성자 페이지 내에서의 직접 미리보기를 허용합니다. 이해 당사자들과 미리보기 페이지를 공유하여 시각적 품질과 상황별 적합성에 대한 피드백을 수집합니다. 검토 주기 동안 여러 자산 버전을 생성 및 관리 후 최종적으로 공개할 수 있습니다.

**OpenAPI 이미지 요청에 대한 향상된 스마트 이미징**

이제 모든 OpenAPI 이미지 요청은 자동 프로모션 및 대체 논리를 통해 스마트 이미징을 최대한 활용합니다. 이 향상된 기능은 디바이스 및 네트워크 상황에 따라 이미지를 최적화하여 시각적 품질을 유지하면서 페이지 로드 속도를 높이고 대역폭 사용량을 줄입니다.


## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### AEM Forms의 새로운 기능 {#forms-new-features}

* **적응형 양식 및 양식 조각을 위한 범용 편집기**

  [범용 편집기](/help/edge/docs/forms/universal-editor/overview-universal-editor-for-edge-delivery-services-for-forms.md)는 이제 적응형 양식과 재사용 가능한 양식 조각을 모두 생성할 수 있도록 지원합니다. 작성자는 간소화된 WYSIWYG 작성 환경에서 시각적으로 양식을 작성하고, 제출 작업을 구성하고, reCAPTCHA 유효성 검사를 추가할 수 있습니다. 이 기능을 사용하면 양식 생성 속도가 빨라지고, 일관성이 향상되고, 스팸 및 자동화된 남용에 대한 보호 기능이 향상됩니다.

  ![범용 편집기](/help/edge/docs/forms/universal-editor/assets/universal-editor.png){width=80%, align-center}


* **Edge Delivery Services 양식 제출 Services 양식**

  [Forms 제출 서비스](/help/forms/forms-submission-service.md)를 사용하면 적응형 양식 제출의 데이터를 Google Sheets, Microsoft OneDrive 또는 SharePoint과 같이 인기 있는 스프레드시트 플랫폼에 바로 저장할 수 있습니다. 이 통합은 양식 데이터를 선택한 스프레드시트로 직접 제출할 수 있게 함으로써 데이터 관리를 간소화하므로 수동 데이터 전송을 방지하고 오류를 줄일 수 있습니다.주요 이점은 다음과 같습니다.

   * **직접 통합:** 지정된 스프레드시트에 데이터를 직접 제출하도록 양식을 구성합니다.
   * **사용자 정의 데이터 매핑:** 양식 필드를 해당 스프레드시트 열에 매핑하여 구성된 저장 공간을 확보합니다.
   * **Access 제어:** 기존 스프레드시트 권한을 활용하여 제출된 데이터에 누가 액세스하거나 수정할 수 있는지 관리합니다.

* **Adaptive Forms에서 AFP 렌디션 생성 및 동기화**

  [AFP 출력 동기화 API](/help/forms/document-generation-afp-api.md)를 사용하면 관리자와 사용자가 적응형 양식에서 AFP(Advanced Function Presentation) 출력을 생성하고 외부 시스템이나 저장 위치와 동기화할 수 있습니다. AFP는 인쇄에 최적화된 고성능 문서 형식으로, 대규모 기업 환경에서 자주 사용됩니다.

* **적응형 양식 조각에 대한 자동 매핑 지원**

  적응형 Forms은 이제 [적응형 양식 조각의 자동 매핑](/help/forms/adaptive-form-fragments-core-components.md#auto-mapping-support-for-fragments-in-an-adaptive-form)을 지원합니다. 이 개선 사항을 통해 스키마 객체가 정의된 조각 구조와 일치하면 일치하는 조각이 자동으로 삽입됩니다. 양식 생성을 단순화하고, 조각을 재사용할 수 있도록 개선하며, 데이터가 통합된 양식 전반에 걸쳐 일관성을 보장합니다.

* 기록 문서의 **사용자 정의 양식 제목**

  작성자는 이제 사용자 정의 양식 제목을 편집하여 기록 문서에서 [사용자 정의 양식 제목](/help/forms/generate-document-of-record-core-components.md#customize-the-branding-information-in-document-of-record)을 정의할 수 있습니다. 사용자 지정 제목은 PDF 헤더, PDF의 문서 속성에 표시되며, PDF을 열 때 초기 보기 제목으로 표시되어 명확한 식별과 일관된 브랜딩을 보장합니다.

* **제한된 파일 형식에 대한 향상된 오류 처리**

  [제한된 파일 형식에 대한 오류 처리](https://experienceleague.adobe.com/ko/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/file-attachment#validation-tab)이(가) 지원되며 지원되지 않는 파일 업로드를 차단합니다. 사용자가 지원되지 않는 형식으로 형식을 변경하여 파일을 제출하려고 하면 제출 중에 오류가 발생합니다.


<!--
### Pre-release features in AEM Forms {#forms-new-pre-release-features}

**Enhancements in Rule Editor**

* The `validate` / `reset` method in the function list now supports validation at the panel, field, and form levels.
* Client-side custom function parsing now supports ES10+ JavaScript features and static imports.
* The button to download Document of Record (DoR) is now available as an out-of-the-box (OOTB) option in the rule editor.
* Rules now support the use of dynamic variables.
* Custom event-based rules are now supported.
* Repeatable panel rules are now executed based on context, rather than only on the last panel instance.
* Rules can now be triggered based on query parameters, UTM parameters, and browser parameters.
* Form-specific custom function scripts are now supported for Adaptive Forms in Edge Delivery Services.

### New Early Access Features in AEM Forms {#forms-new-early-access-features}

The AEM Forms Early Access Program offers a unique opportunity for you to get exclusive access to cutting-edge innovations and help shape their development.

These release notes list the innovations delivered in the current release. For the complete list of innovations available under the Early Access Program, see [AEM Forms Early Access Program documentation](/help/forms/early-access-ea-features.md). 


**Forms Optimization opportunities**

Forms Optimization uses AI to analyze your forms and suggest improvements for better performance. It highlights forms with low engagement, flags accessibility issues, and generates AI-powered variations to help increase conversion rates and compliance with WCAG standards.

>[!VIDEO](https://video.tv.adobe.com/v/3469472/) 

Key optimization opportunities include:

* Increasing visibility for forms with low views
* Improving completion rates for forms with low conversions
* Addressing accessibility compliance issues
* Streamlining navigation to enhance user experience

With Forms Optimization, you get automated, data-driven recommendations and variations, making it easier to boost engagement and ensure your forms are effective and inclusive. -->

**인터랙티브 통신 편집기용 규칙 편집기**

직관적인 마우스로 수행할 수 있는 인터페이스를 사용하여 문서 내에서 동적이고 데이터 기반의 작업을 직접 빌드하십시오. 코드를 작성하지 않고도 조건 논리를 쉽게 정의하고, 워크플로를 자동화하고, 콘텐츠를 개인화할 수 있습니다.

**사용자 정의 구성 요소를 위한 AEM Forms Scaffolder CLI**

>[!VIDEO]&#x200B;(https://video.tv.adobe.com/v/3470514/aem-forms 스캐폴딩-aem-사용자 정의 구성 요소 생성기-aem-forms cli-aem-forms 사용자 정의 구성 요소-aem-forms 개발 도구)

이 CLI 도구를 사용하여 AEM Forms Edge Delivery Services 개발을 가속화하십시오. 사용자 정의 구성 요소 개발을 시작하는 데 필요한 코드와 배선을 즉시 생성합니다. 보일러플레이트나 번거로움이 없습니다.

**동적 양식 데이터를 위한 API 통합 도구**

API 통합 도구를 사용하면 양식 작성자가 사용자 상호 작용을 기반으로 외부 REST API에서 데이터를 자동으로 가져와 채우는 동적이고 지능형 양식을 만들 수 있습니다. 코드가 필요 없는 통합 기능은 정적 양식을 반응형 데이터 수집 인터페이스로 변환합니다.

## [!DNL Experience Manager] as a [!DNL Cloud Service] Foundation {#foundation}

### 권한 관리에 대한 노드 보기 {#node-view}

AEM에서는 노드 보기 권한 관리를 도입했습니다. 주요 기능은 기존 UI와 동일하지만 사용자 친화성과 효율성이 향상되었습니다. 자세한 내용은 [전용 문서](/help/security/touch-ui-principal-view.md)를 참조하십시오.

### 업데이트된 사용 중단 프로세스 {#updated-deprecation-process}

Adobe는 정기적으로 기능, 라이브러리, API 및 구성을 검토하여 성능, 보안 및 가치에 대한 기준을 충족하는지 확인합니다. 기능이 더 이상 이 기준을 충족하지 못하면 더 이상 사용되지 않으며 지정된 제거 날짜까지 사용을 중단해야 합니다. 이 날짜까지 Adobe는 이메일 알림을 통해 고객에게 알리고, 새 빌드를 진행하거나 배포하기 전에 Cloud Manager에서 수행해야 할 작업을 알려 드립니다. 필요한 조치를 취하지 않으면 AEM의 새 버전으로 업그레이드할 수 없게 되어 보안, 성능, 안정성 및 가용성에 잠재적인 영향을 미칠 수 있습니다.

자세한 내용은 [사용 중단 문서](/help/release-notes/deprecated-removed-features.md)를 참조하십시오.

#### 제거 날짜가 다가옴에 따라 사용 중단된 Java API 및 OSGi 구성 {#deprecated-near-removals}

아래 목록을 확장하여 사용 중단된 API와 OSGi 구성을 확인하십시오. 제거 일정을 포함한 자세한 내용은 사용 중단 문서를 참조하십시오.

<details>
  <summary>사용 중단 항목을 보려면 확장하십시오.</summary>

Java API:

* `org.apache.sling.commons.auth`
* `org.apache.felix.webconsole`
* `org.eclipse.jetty`
* `com.mongodb`
* `org.apache.abdera`
* `org.apache.felix.http.whiteboard`
* `org.apache.cocoon.xml`
* `ch.qos.logback`
* `org.slf4j.spi`
* `org.slf4j.event`
* `org.apache.log4j`
* `com.google.common`
* `com.drew`
* `org.bson`
* `org.apache.jackrabbit.oak.plugins.blob`
* `org.apache.jackrabbit.oak.plugins.memory`

OSGi 속성:

* `org.apache.sling.commons.log.LogManager` (모든 속성)
* `org.apache.sling.commons.log.LogManager.factory.config` (`org.apache.sling.commons.log.file`, `org.apache.sling.commons.log.pattern`)

</details>

### Java 11 런타임 사용 중단 {#java11-runtime-deprecation}

*Java 11 런타임*&#x200B;은 이제 더 이상 사용되지 않으며, 대부분의 환경은 이미 성능이 더 좋은 **Java 21 런타임**&#x200B;으로 업그레이드되었습니다.

지원되지 않는 종속성으로 인해 환경을 업그레이드할 수 없는 경우([Java 21 런타임 요구 사항](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/build-environment-details.md#runtime-requirements) 참조), Adobe로부터 구체적인 다음 단계가 포함된 이메일을 받았을 것입니다. 모든 필수 업데이트가 **2025년 8월 28일**&#x200B;까지 완료되어 중단 없이 환경을 업그레이드할 수 있도록 해 주시기 바랍니다.

참고: 런타임 버전은 코드의 빌드 버전과 별도입니다. Java 21을 사용한 빌드를 권장하지만 현재로서는 Java 11 빌드도 여전히 지원됩니다. Java 11 빌드에 대한 별도의 사용 중단 공지는 앞으로 공유될 예정입니다.

### AEM Java 로그 구성 시행 {#logconfig-policy}

4월 릴리스 정보에서 언급된 대로 AEM Java 로그는 모든 고객 환경에서 안정적인 모니터링을 보장하기 위해 표준 형식을 따라야 합니다. 로그 형식 변경, 출력 파일 또는 기본 로그 수준과 같은 사용자 정의 로그 구성은 더 이상 지원되지 않습니다. 로그는 기본 파일로 전달되어야 하며, AEM 제품 코드의 기본 로그 수준은 유지되어야 합니다. 자세한 내용은 [로깅 문서](/help/implementing/developing/introduction/logging.md#configuration-loggers)를 참조하십시오.

**8월 말**&#x200B;부터 지원되지 않는 사용자 정의 로깅 재정의는 무시됩니다. 분석에 따르면 대부분의 고객은 영향을 받지 않으며 현재 구성에 영향을 받을 수 있는 고객에게는 Adobe에서 개별적으로 안내를 드렸습니다.

사용자 정의 로깅 동작에 의존하는 모든 다운스트림 프로세스를 검토하고 업데이트해 주시기 바랍니다. 예:

* 로그 전달 시스템이 사용자 정의 로그 형식을 기대하는 경우, 수집 규칙을 조정해야 할 수도 있습니다.
* 이전에 로그 수준을 변경하여 로그의 세부 정보를 줄인 적이 있는 경우 기본 수준으로 되돌리면 로그 볼륨이 증가할 수 있습니다.

### 이전 버전 및 감사 로그의 기본 삭제 {#mt-defaults}

현재 콘텐츠 버전과 감사 로그는 기본적으로 해당 삭제 유지 관리 작업이 비활성화되어 있으므로 명시적으로 구성하지 않는 한 데이터가 제거되지 않습니다.

그러나 저장소 성능을 최적화하기 위해 다음 지침에 따라 향후 발표된 날짜에 기본적으로 삭제가 활성화됩니다.

#### 콘텐츠 버전 {#mt-content}

* *새로운 환경* (향후 날짜 이후에 생성됨(나중에 전달))
   * *30일* 이전 버전은 주기적으로 삭제됩니다.
   * 지난 30일 이내의 최신 버전 5개는 보관 기간에 관계없이 가장 최신 버전 및 현재 버전도 함께 유지됩니다.

* *기존 환경*(향후 날짜 이전에 생성됨):
   * *7년* 이전 버전은 주기적으로 삭제됩니다.
   * 지난 7년 이내의 모든 버전이 보존됩니다.
   * 이 높은 기본 임계값은 최근 데이터가 의도치 않게 제거되는 것을 방지합니다. 그러나 저장소 성능을 최적화하려면 더 낮은 값을 구성하는 것이 좋습니다.

* 해당 기본값은 구성 파이프라인을 사용해 배포된 YAML 구성으로 수정할 수 있습니다.

#### 감사 로그 {#mt-auditlogs}

* *새로운 환경*(향후 날짜가 정해지면 별도 공지 예정):
   * 복제, DAM 및 페이지 감사 로그는 *7일* 이상 주기적으로 삭제됩니다.
   * 모든 이벤트는 기본적으로 기록됩니다.

* *기존 환경*(향후 날짜 이전에 생성됨):
   * 복제, DAM 및 페이지 감사 로그는 *7년* 이상 주기적으로 삭제됩니다.
   * 모든 이벤트는 기본적으로 기록됩니다.
   * 이 높은 기본 임계값은 최근 데이터가 의도치 않게 제거되는 것을 방지합니다. 그러나 저장소 성능을 최적화하려면 더 낮은 값을 구성하는 것이 좋습니다.

* 해당 기본값은 구성 파이프라인을 사용해 배포된 YAML 구성으로 수정할 수 있습니다.

자세한 내용은[유지 관리 작업 문서](/help/operations/maintenance.md#defaults)를 참조하십시오.

### 에지 컴퓨팅 (Alpha 프로그램) {#edge-computing}

에지 컴퓨팅을 사용하면 CDN 계층에서 JavaScript를 실행할 수 있어 데이터 처리가 최종 사용자에게 더 가까워집니다. 이렇게 하면 지연 시간이 줄어들고 에지에서 반응성이 뛰어나고 역동적인 경험을 할 수 있습니다.

일반적인 사용 사례는 다음과 같습니다.

* 콘텐츠 접근 권한을 부여하기 전에 ID 공급자를 통해 사용자 인증
* 지리적 위치, 디바이스 유형 또는 사용자 속성에 따라 콘텐츠 개인화
* CDN과 원본 사이의 미들웨어 역할
* 브라우저에 제공하기 전에 서드파티 API의 응답(및 여러 API 응답 집계)을 다시 포맷
* 다양한 백엔드에서 결합된 콘텐츠를 사용하여 에지에서 서버 렌더링 HTML을 구성하고 제공
* ChatGPT 및 Claude와 같은 LLM을 위한 MCP 서버를 사용자 정의 도구에 액세스하도록 노출

라이브 프로덕션 사이트를 위한 AEM Publish Delivery 또는 Edge Delivery Services 프로젝트에 사용할 수 있는 기회는 제한적입니다. 참여에 관심이 있거나 보다 자세히 알아보려면 사용 사례에 대한 간략한 설명과 함께 [aemcs-edgecompute-feedback@adobe.com](mailto:aemcs-edgecompute-feedback@adobe.com)으로 이메일을 보내 주시기 바랍니다.

### Edge Delivery Services를 위한 CDN 구성 (Beta 프로그램) {#cdn-eds-beta}

Adobe 관리 CDN은 [구성 파이프라인 문서](/help/operations/config-pipeline.md#configurations)에 설명된 대로 유연한 구성 옵션을 제공합니다.

이제 Beta 버전에서는 CDN 원본 선택기, 응답 및 요청 변환, CDN 로그 전달 등을 포함한 기능에 대한 구성 파이프라인을 배포합니다. 사용 사례에 대한 자세한 내용은 [aemcs-cdn-config-adopter@adobe.com](mailto:aemcs-cdn-config-adopter@adobe.com)에 문의해 주십시오.

### RDE용 스냅샷 (Alpha 프로그램) {#rde-snapshot-beta}

알파 버전에서는 신속한 개발 환경(RDEs)에서 현재 코드와 콘텐츠 상태의 스냅샷을 찍는 기능을 지원하며, 이는 나중에 복원할 수 있습니다. 이것은 반환이 필요할 수 있는 코드를 동기화하거나, 서로 다른 기능의 개발을 전환할 때 유용할 수 있습니다. 테스트를 위한 알려진 시작점으로 변경 가능한 콘텐츠만 복원하는 것도 가능합니다.

이 기능에 대한 피드백을 제공하는 데 관심이 있으시면 [aemcs-rde-support@adobe.com](mailto:aemcs-rde-support@adobe.com)으로 이메일을 보내주십시오.

### 더 많은 대상으로 AEM 로그 전달 (Beta 프로그램) {#log-forwarding-beta}

로그는 Cloud Manager에서 다운로드할 수 있지만 많은 조직에서 이러한 로그를 선호하는 로깅 대상으로 스트리밍하는 것이 유용하다고 생각합니다. AEM은 이미 Azure Blob Storage, Datadog, HTTPS, Elasticsearch(및 OpenSearch), Splunk로의 AEM 및 CDN 로그 전달을 지원합니다. 이 기능은 셀프서비스 방식으로 구성하고 구성 파이프라인을 사용하여 배포합니다.

이제 Beta 버전에서는 AEM 로그를 Amazon S3, Sumo Logic, Dynatrace 및 사용자의 New Relic 계정(Adobe 제공 계정이 아닌 경우)으로 전달할 수 있습니다. AEM 로그(Apache/Dispatcher 포함)가 이러한 로깅 대상에 대해 지원되지만 CDN 로그는 지원되지 않습니다. 액세스하려면 이메일 [aemcs-logforwarding-beta@adobe.com](mailto:aemcs-logforwarding-beta@adobe.com)으로 문의하십시오.

자세한 내용은 [로그 전달 설명서](/help/implementing/developing/introduction/log-forwarding.md)에서 확인하십시오.

## [!DNL Experience Manager] 안내서 {#guides}

[여기](https://experienceleague.adobe.com/ko/docs/experience-manager-guides/using/release-info/aem-guides-releases-roadmap)에서 Adobe Experience Manager Guides 최신 릴리스의 새로운 기능과 향상된 기능의 전체 목록을 찾을 수 있습니다.

## Cloud Manager {#cloud-manager}

[여기](/help/implementing/cloud-manager/release-notes/current.md)에서 Cloud Manager 월별 릴리스의 전체 목록을 찾을 수 있습니다.

## 마이그레이션 도구 {#migration-tools}

[여기](/help/journey-migration/release-notes/release-notes-migration-tools-current.md)에서 마이그레이션 도구의 전체 목록을 찾을 수 있습니다.

## 범용 편집기 {#universal-editor}

[여기](/help/release-notes/universal-editor/current.md)에서 범용 편집기의 전체 목록을 찾을 수 있습니다.

## 변형 생성 {#generate-variations}

[여기](/help/generative-ai/release-notes-generate-variations.md)에서 변형 생성의 전체 목록을 찾을 수 있습니다.

## Experience Cloud 릴리스 정보 {#experience-cloud}

기타 Experience Cloud 애플리케이션 릴리스에 대한 정보는 [여기](https://experienceleague.adobe.com/ko/docs/release-notes/experience-cloud/current)에서 확인할 수 있습니다.
