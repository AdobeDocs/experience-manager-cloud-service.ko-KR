---
title: ' [!DNL Adobe Experience Manager] as a Cloud Service의 2024.9.0 릴리스 정보입니다.'
description: ' [!DNL Adobe Experience Manager] as a Cloud Service의 2024.9.0 릴리스 정보입니다.'
feature: Release Information
role: Admin
exl-id: 75ecd154-112a-4468-9962-de50bb1f4cd0
source-git-commit: b0208964fc193e0e839bccaaf8245c86f280767d
workflow-type: tm+mt
source-wordcount: '1324'
ht-degree: 91%

---

# [!DNL Adobe Experience Manager] as a Cloud Service 2024.9.0 릴리스 정보 {#release-notes}

다음 섹션에서는 [!DNL Experience Manager] as a Cloud Service의 2024.9.0 버전 기능 릴리스 정보에 대해 간략히 소개합니다.

>[!NOTE]
>
>여기에서 2022년 또는 2023년과 같은 이전 버전의 릴리스 정보로 이동할 수 있습니다.
>
>[!DNL Experience Manager] as a Cloud Service의 향후 기능 활성화에 대해 알아보려면 [Experience Manager 릴리스 로드맵](https://experienceleague.adobe.com/ko/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap)을 살펴보십시오.

>[!NOTE]
>
>Experience Cloud 릴리스 정보의 업데이트에 대한 월별 이메일 알림을 받아 보려면 [Adobe 우선순위 제품 업데이트](https://www.adobe.com/kr/subscription/priority-product-update.html)를 구독하십시오.

## 릴리스 일자 {#release-date}

[!DNL Adobe Experience Manager]인 [!DNL Cloud Service]의 현재 기능 릴리스(2024.9.0)의 날짜는 2024년 9월 26일입니다. 다음 기능 릴리스(2024.10.0)는 2024년 10월 31일에 예정되어 있습니다.

## 유지 관리 릴리스 정보 {#maintenance}

[ 여기](/help/release-notes/maintenance/latest.md)에서 최신 유지 관리 릴리스 정보를 확인할 수 있습니다.

## 릴리스 비디오 {#release-video}

2024년 9월 릴리스 개요 비디오를 통해 2024.9.0 릴리스에 추가된 기능에 대한 간단한 요약을 살펴보십시오.

>[!VIDEO](https://video.tv.adobe.com/v/3434847?quality=12)

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### Experience Manager Sites의 새로운 기능 {#new-feature-sites}

#### 번역 관리 {#translation-management}

AEM 번역 워크플로와 API 액션은 이제 이벤트를 트리거하여 번역 작업 상태 변경에 대한 인사이트를 제공합니다. 사용자는 Adobe Developer Console을 통해 이러한 이벤트를 구독할 수 있습니다. AEM 번역 관리 API에 대한 자세한 내용은 [여기](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/translation/)에서 확인하십시오.

### 얼리 어답터 프로그램 {#sites-early-adopter}

**변형 생성**

이제 Cloud Service에서 액세스 가능한 AEM의 새로운 기능인 [변형 생성](/help/generative-ai/generate-variations.md)을 통해 GenAI를 활용할 수 있습니다. 변형 생성은 생성형 AI를 사용하여 콘텐츠 제작을 생성하고 확장하는 데 도움이 됩니다. 프로그램 참여를 고려한다면 Adobe 계정 팀에 문의하십시오.


## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### Dynamic Media의 얼리 액세스 기능 {#dm-early-access}

**AI 생성 비디오 캡션**

Adobe Dynamic Media의 AI 생성 비디오 캡션은 인공 지능을 통해 비디오 콘텐츠에 대한 캡션을 자동으로 생성합니다. 이 기능은 정확한 실시간 캡션을 제공하여 접근성을 개선하고 사용자 경험을 향상시킬 수 있도록 설계되었습니다. AI는 비디오의 오디오 트랙을 분석하여 음성을 기록하고 캡션을 생성하며, 정확성이나 사용자 정의를 위해 해당 캡션을 편집할 수 있습니다. 이러한 캡션은 접근성 요구 사항을 충족하며, 텍스트 기반 비디오 지원에 의존하거나 이를 선호하는 대상자의 비디오 참여를 개선하는 데 도움이 됩니다.

Dynamic Media 계정에서 AI 생성 캡션 지원에 얼리 액세스하려면 [Adobe 고객 지원 사례를 작성하고 제출](/help/assets/dynamic-media/video.md##enable-dash)하십시오.

### 자산 선택기의 새로운 기능 {#asset-selector-new-features}

이제 자산 선택기에서 컬렉션을 탐색하여 원하는 자산을 찾을 수 있습니다.
![자산 선택기 컬렉션](/help/assets/assets/collections-rail-modal-view.png)

### Content Hub의 새로운 기능 {#content-hub-new-features}

이제 관리자는 만료된 자산을 Content Hub에 표시할지 여부를 제어할 수 있습니다. 만료된 자산이 표시되면 사용자가 해당 자산을 다운로드할 수 있는지 여부도 정의할 수 있습니다.

![Content Hub의 만료된 자산](/help/assets/assets/view-download-expired-assets.png)

## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### AEM Forms의 새로운 프리릴리스 기능 {#forms-new-prerelease-features}

#### 핵심 구성 요소 기반 적응형 양식의 초안 자동 저장

이제 사용자는 부분적으로 완료된 양식을 초안으로 자동 저장하는 자동 저장 기능을 활용할 수 있습니다. 나중에 돌아와 동일한 디바이스 또는 다른 디바이스에서 작성을 마칠 수 있습니다. 이 기능을 통해 사용자가 처음부터 양식을 작성할 필요가 없으므로 양식 폐기를 방지하여 전환율을 높일 수 있습니다.


### AEM Forms의 얼리 액세스 기능 {#forms-new-early-access-features}

AEM Forms 얼리 액세스 프로그램은 최첨단 혁신에 독점적으로 액세스할 수 있는 특별한 기회를 제공하며, 혁신의 발전을 구체화하는 데 도움을 줍니다.

이 릴리스 정보에는 현재 릴리스에서 제공되는 혁신 사항이 나열되어 있습니다. 얼리 액세스 프로그램에서 사용할 수 있는 전체 혁신 목록은 [AEM Forms 얼리 액세스 프로그램 설명서](/help/forms/early-access-ea-features.md)를 참조하십시오.

#### AEM Forms AI 어시스턴트

적응형 양식에 생성형 AI를 사용하면 양식 개발 프로세스에 새로운 수준의 기능과 편의성이 구현됩니다. 그 어느 때보다 빠르게 효율적인 양식을 빌드할 수 있습니다.

![생성형 AI 어시스턴트, 적응형 양식](/help/forms/assets/generative-ai-assistant.png)

제공되는 생성형 AI 기능은 다음과 같습니다.

* **제품 쿼리용 AI 어시스턴트**: AEM 양식 관련 질문에 대한 즉각적인 답변을 얻습니다. AI 어시스턴트는 사용자 개인의 기술 자료로서 플랫폼 내에서 바로 통찰력 있는 가이드와 추천 사항을 제공해 줍니다.

* **적응형 양식 생성**: 생성형 AI 프롬프트를 사용하여 완전한 양식을 손쉽게 만듭니다. Adobe의 생성형 AI는 드롭오프를 줄이고 경험을 개인화하는 사용자 친화적인 양식을 자동으로 생성합니다.

* **양식용 패널 생성**: 특정 데이터 수집 요구에 맞춰 양식 섹션을 생성합니다. 예를 들어 결제 정보, 고객 선호도, 여행 세부 정보를 수집하는 섹션을 생성합니다.

* **양식 레이아웃 변경**: 생성형 AI 프롬프트를 사용하여 다양한 레이아웃과 디자인을 실험합니다. 마법사 또는 탭 보기 등 다양한 레이아웃을 사용하여 양식에 가장 잘 맞는 디자인을 찾아보십시오. 생성형 AI 프롬프트를 사용하여 모바일 응답성을 위해 양식을 최적화하고 사용자의 마음에 드는 시각적으로 매력적인 양식을 만듭니다.

* **제출 액션 구성**: 생성형 AI 프롬프트를 사용하여 양식의 제출 액션을 간편하게 구성합니다. 사전 빌드된 제출 액션 라이브러리에서 선택하거나, 자체 개발 팀에서 만들고 배포한 사용자 정의 제출 액션에서 선택합니다.

>[!IMPORTANT]
>
> Forms 혁신을 위한 얼리 액세스 프로그램에 참여하는 데 관심이 있으십니까? 공식 주소에서 [aem-forms-ea@adobe.com](mailto:aem-forms-ea@adobe.com)으로 관심 있는 기능 목록을 포함하여 이메일을 보내 주십시오.

## CIF 추가 기능 {#cloud-services-cif}

### 개선 사항 {#improvements-fixes-cif}

* 범주 제한을 사용자 지정할 수 있게 만듭니다.

### 버그 수정 {#bug-fixes-cif}

* Commerce 필드가 자산 메타데이터 스키마 편집기와 제대로 통합되지 않았습니다.
* 드래그 앤 드롭을 위한 슬라이드 제품 다중 필드 관련 문제.
* 드래그 앤 드롭을 위한 슬라이드 카테고리 다중 필드 관련 문제.
* 카테고리 및 제품 편집기 페이지의 페이지 정보에 있는 메뉴에 대해서는 클릭 시 작동하지 않습니다.
* 주문 번호가 주문 확인 페이지에 표시되지 않습니다.

## [!DNL Experience Manager] as a [!DNL Cloud Service] Foundation {#foundation}

### 다이내믹 콘텐츠 로딩을 위한 ESI (에지측 포함) {#esi}

이제 Adobe에서 관리하는 콘텐츠 전송 네트워크는 에지 수준 동적 웹 콘텐츠 어셈블리를 위한 마크업 언어인 [ESI(에지측 포함)](/help/implementing/dispatcher/edge-side-includes.md)를 지원합니다. ESI 스니펫을 포함하면 더 높은 TTL을 사용하여 콘텐츠 전송 네트워크에서 전체 HTML 페이지를 캐싱하는 동시에 더 높은 케이던스 업데이트(낮은 TTL)가 필요한 작은 섹션을 출처에서 더 자주 가져올 수 있습니다. 이 기능은 점진적으로 제공되고 있습니다.

### 콘텐츠 전송 네트워크에서의 기본 인증 {#basicauth-cdn}

사용자 이름과 암호를 요구하는 기본 인증 대화 상자를 표시하여 특정 콘텐츠 리소스를 보호합니다. 이 기능은 최종 사용자 액세스 권한에 대한 포괄적인 솔루션 역할을 하기보다는 주로 비즈니스 관련자가 콘텐츠를 검토하는 것과 같은 간단한 인증 사용 사례를 대상으로 합니다. 사용자 이름 및 암호 목록은 구성 파이프라인을 통해 배포된 Git의 구성 파일을 통해 관리되며, 비밀 유형 Cloud Manager 환경 변수를 참조합니다. [자세히 알아보기](/help/implementing/dispatcher/cdn-credentials-authentication.md#basic-auth).

### 클라이언트측 리디렉션 {#client-side-redirects}

CDN에서 배포 및 평가되는 구성 파일 Git에서 [브라우저 리디렉션](/help/implementing/dispatcher/cdn-configuring-traffic.md#client-side-redirectors)을 선언합니다. 이 기능은 페이지 삭제, 변경된 사이트 구조 및 SEO 최적화를 포함한 시나리오에 유용할 수 있습니다.

### 새로운 AEM Developer Console (공개 Beta) {#aem-developer-console-beta}

클라우드 환경에서 코드 디버깅을 위한 보다 인터랙티브한 경험을 제공하는 개선된 [AEM Developer Console](/help/implementing/developing/introduction/aem-developer-console.md)을 사용해 보십시오.

현재 AEM Developer Console에서 *새 콘솔 사용 가능* 버튼을 클릭하여 누구나 공개 Beta에 액세스할 수 있습니다. Adobe에서는 피드백을 환영합니다. 피드백은 **<aemcs-new-devconsole-ui-beta@adobe.com>**&#x200B;으로 이메일을 보내주십시오.

![AEM Developer Console의 OSGi 번들 화면](/help/implementing/developing/introduction/assets/osgi-bundles.png)

### 비즈니스 사용자는 Git 외의 리디렉션을 선언할 수 있습니다(얼리 어답터 프로그램). {#apache-rewritemaps-early-adopter}

AEM 6.5와 유사하게 Apache/Dispatcher는 게시 저장소의 특정 위치에 배치된 재작성 맵을 수집하고 웹 계층 파이프라인 실행 없이 로드합니다. 이 접근 방식을 통해 비즈니스 사용자는 ACS Commons Redirect Map Manager 또는 사용자 정의 애플리케이션과 같은 스프레드시트나 UI를 사용하여 리디렉션을 선언할 수 있습니다. **<aemcs-cdn-config-adopter@adobe.com>**&#x200B;으로 이메일을 보내 얼리 어답터 프로그램에 참여하십시오.

### RDE(얼리 어답터 프로그램)에 대한 파이프라인 구성 {#config-pipeline-rdes-early-adopter}

[Config Pipeline](/help/operations/config-pipeline.md)은(는) CDN 옵션(트래픽 필터 규칙, 요청/응답 변환 등)을 포함한 YAML 파일 구성을 배포하는 데 사용됩니다. **<aemcs-cdn-config-adopter@adobe.com>**&#x200B;으로 이메일을 보내 CLI를 사용하는 RDE(신속한 개발 환경)에 이러한 동일한 구성을 배포하여 얼리 어답터 프로그램에 참여하십시오.

## [!DNL Experience Manager] 안내서 {#guides}

[여기](https://experienceleague.adobe.com/ko/docs/experience-manager-guides/using/release-info/aem-guides-releases-roadmap)서 Adobe Experience Manager Guides 최신 릴리스의 새로운 기능과 향상된 기능의 전체 목록을 찾을 수 있습니다.

## Cloud Manager {#cloud-manager}

[여기](/help/implementing/cloud-manager/release-notes/current.md)서 Cloud Manager 월별 릴리스의 전체 목록을 찾을 수 있습니다.

## 마이그레이션 도구 {#migration-tools}

[여기](/help/journey-migration/release-notes/release-notes-migration-tools-current.md)서 마이그레이션 도구의 전체 목록을 찾을 수 있습니다.

## 범용 편집기 {#universal-editor}

[여기](/help/release-notes/universal-editor/current.md)서 범용 편집기의 전체 목록을 찾을 수 있습니다.

## 변형 생성 {#generate-variations}

[여기](/help/generative-ai/release-notes-generate-variations.md)서 변형 생성의 전체 목록을 찾을 수 있습니다.

## Experience Cloud 릴리스 정보 {#experience-cloud}

다른 Experience Cloud 애플리케이션 릴리스에 대한 정보는 [여기](https://experienceleague.adobe.com/ko/docs/release-notes/experience-cloud/current)서 확인할 수 있습니다.
