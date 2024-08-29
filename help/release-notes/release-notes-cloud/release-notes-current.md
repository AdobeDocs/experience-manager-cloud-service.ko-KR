---
title: ' [!DNL Adobe Experience Manager] as a Cloud Service 최신 릴리스 정보'
description: ' [!DNL Adobe Experience Manager] as a Cloud Service 최신 릴리스 정보'
mini-toc-levels: 1
exl-id: a2d56721-502c-4f4e-9b72-5ca790df75c5
feature: Release Information
role: Admin
source-git-commit: 9cc49bf83d278d4064faa1d0157201226a067cb1
workflow-type: tm+mt
source-wordcount: '1142'
ht-degree: 51%

---

# [!DNL Adobe Experience Manager] as a Cloud Service 최신 릴리스 정보 {#release-notes}

다음 섹션에서는 [!DNL Experience Manager] as a Cloud Service의 최신 버전 기능 릴리스 정보에 대해 간략히 소개합니다.

>[!NOTE]
>
>여기에서 2022년 또는 2023년과 같은 이전 버전의 릴리스 정보로 이동할 수 있습니다.
>
>[!DNL Experience Manager] as a Cloud Service의 향후 기능 활성화에 대해 알아보려면 [Experience Manager 릴리스 로드맵](https://experienceleague.adobe.com/ko/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap)을 살펴보십시오.

>[!NOTE]
>
>Experience Cloud 릴리스 정보의 업데이트에 대한 월별 이메일 알림을 받아 보려면 [Adobe 우선 순위 제품 업데이트](https://www.adobe.com/kr/subscription/priority-product-update.html)를 구독하십시오.

## 릴리스 일자 {#release-date}

[!DNL Cloud Service] 현재 기능 릴리스(2024.8.0)인 [!DNL Adobe Experience Manager]의 릴리스 날짜는 2024년 8월 29일입니다. 다음 기능 릴리스(2024.9.0)는 2024년 9월 26일에 예정되어 있습니다.

## 유지 관리 릴리스 정보 {#maintenance}

[ 여기](/help/release-notes/maintenance/latest.md)에서 최신 유지 관리 릴리스 정보를 확인할 수 있습니다.

<!-- ## Release Video {#release-video}

Have a look at the August 2024 Release Overview video for a summary of the features added in the 2024.8.0 release:

>[!VIDEO](https://video.tv.adobe.com/v/3431707?quality=12)

-->

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### Experience Manager Sites의 새로운 기능 {#new-feature-sites}

**Edge Delivery Services를 위한 AEM 작성**

기존 사이트 [상속](/help/sites-cloud/authoring/universal-editor/inheritance.md) 기능은 이제 다음을 포함하여 지원됩니다.

* [AEM 론치](/help/sites-cloud/authoring/launches/overview.md)
* 페이지 수준의 [MSM](/help/sites-cloud/administering/msm/overview.md)

또한 다음과 같은 페이지 관리 기능이 지원됩니다.

* [AEM 태그](/help/sites-cloud/authoring/sites-console/tags.md)를 [분류](/help/edge/wysiwyg-authoring/taxonomy.md)(으)로 Edge Delivery Services에 내보낼 수 있습니다.
* Edge Delivery Services에 대한 [템플릿](/help/edge/wysiwyg-authoring/templates.md)이 곧 제공됩니다!

### 얼리 어답터 프로그램 {#sites-early-adopter}

**변형 생성**

이제 클라우드 서비스에서 액세스 가능한 AEM의 새로운 기능인 [변형 생성](/help/generative-ai/generate-variations.md)을 통해 GenAI를 활용할 수 있습니다. 변형 생성은 생성형 AI를 사용하여 콘텐츠 제작을 생성하고 확장하는 데 도움이 됩니다. 프로그램 참여를 고려한다면 Adobe 계정 팀에 문의하십시오.


## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### Assets 보기의 새로운 기능 {#assets-view-new-features}

**업데이트된 Adobe Firefly 이미지 생성**

Assetsas a Cloud Service 에서는 이제 Adobe Firefly을 사용하여 다양한 스타일의 Firefly 위젯을 생성합니다. 스타일, 컴포지션, 차원 등을 정의하고 내장된 Firefly 편집기를 사용하여 즉시 사용할 수 있도록 AEM Assets 저장소 내에서 직접 필요한 에셋을 빠르게 생성하고 저장할 수 있습니다.

![Adobe Firefly 이미지 생성](/help/assets/assets/bugatti-type-57.png)

**PSB 파일 지원**

Assetsas a Cloud Service 는 기존 PSD 파일 지원 외에도 Photoshop 대용량 문서(SB 파일)를 지원합니다.

### Content Hub의 새로운 개선 사항 {#content-hub-new-enhancements}

* 긴 파일 이름을 더 잘 처리하고 툴팁을 통해 전체 이름을 쉽게 확장할 수 있습니다.
* 컨텐츠 종횡비에 맞게 썸네일을 개선하고 더 넓은 컨텐츠 영역을 커버했습니다.
* 콘텐츠 허브에 지원되는 AEM의 사용자 지정 썸네일 경험.
* 색상 검색 개선.
* 향상된 구성 덕분에 경험을 저장할 수 있습니다.
* 작성자 이름을 반영하도록 컬렉션의 정보 페이지가 개선되었습니다.


## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### AEM Forms의 새로운 프리릴리스 기능 {#forms-new-prerelease-features}

#### 적응형 Forms 기반의 핵심 구성 요소에 대한 초안 자동 저장

이제 부분적으로 완료된 양식을 초안으로 자동으로 저장하는 자동 저장 기능을 사용할 수 있습니다. 나중에 다시 돌아와 동일한 장치나 다른 장치에서 작성을 완료할 수 있습니다. 이 기능은 사용자가 처음부터 양식 채우기를 다시 시작할 필요가 없으므로 양식 포기를 줄여 조직의 전환율을 개선합니다.


### AEM Forms의 얼리 액세스 기능 {#forms-new-early-access-features}

AEM Forms 조기 액세스 프로그램 은 혁신적인 최신 기술에 독점적으로 액세스하고 개발 환경을 구축할 수 있는 특별한 기회를 제공합니다.

이 릴리스 정보에는 현재 릴리스에서 제공되는 혁신 사항이 나열되어 있습니다. 얼리 액세스 프로그램에서 사용할 수 있는 전체 혁신 목록은 [AEM Forms 얼리 액세스 프로그램 설명서](/help/forms/early-access-ea-features.md)를 참조하십시오.

#### AEM Forms AI Assistant

적응형 Forms을 위한 생성 AI는 양식 개발 프로세스에 완전히 새로운 수준의 권한과 편의성을 제공합니다. 이를 통해 이전보다 더 나은 양식을 더 빠르게 작성할 수 있습니다.

![생성 AI 도우미, 적응형 Forms](/help/forms/assets/generative-ai-assistant.png)

오퍼의 생성 AI 기능은 다음과 같습니다.

* **제품 쿼리에 대한 AI 도우미**: AEM 양식 관련 질문에 대한 답변을 즉시 받아 보십시오. AI 비서는 고유한 개인 지식 기반 역할을 하며 플랫폼 내에서 직접 통찰력 있는 지침과 추천을 제공합니다.

* **적응형 양식 생성**: 생성 AI 프롬프트가 있는 완전한 양식을 쉽게 만들 수 있습니다. 생성 AI는 드롭오프를 줄이고 경험을 개인화하는 사용자 친화적인 양식을 자동으로 생성합니다.

* **Forms에 대한 패널 생성**: 특정 데이터 수집 요구에 맞는 양식 섹션을 생성합니다. 예를 들어 결제 정보, 고객 환경 설정 또는 여행 세부 정보를 수집하기 위한 섹션을 생성합니다.

* **양식 레이아웃 변경**: 생성 AI 프롬프트를 사용하여 다양한 레이아웃 및 디자인을 실험해 보십시오. 마법사나 탭 보기와 같은 다양한 레이아웃을 사용하여 폼에 가장 적합한 레이아웃을 선택하십시오. 생성 AI 프롬프트 를 사용하여 모바일 응답성에 대한 양식을 최적화하고 사용자가 좋아하는 시각적으로 매력적인 양식을 만들 수 있습니다.

* **제출 동작 구성**: 양식에 대한 제출 동작을 쉽게 구성하려면 생성 AI 프롬프트를 사용합니다. 사전 빌드된 제출 액션 라이브러리 또는 자체 개발 팀에서 만들고 배포한 사용자 지정 제출 액션 목록에서 선택합니다.

>[!IMPORTANT]
>
> 혁신적인 기능을 위해 조기 액세스 프로그램에 참여하려면 공식 주소에서 [aem-forms-ea@adobe.com](mailto:aem-forms-ea@adobe.com)(으)로 관심 있는 기능 목록과 함께 전자 메일을 보내면 됩니다.


## [!DNL Experience Manager] as a [!DNL Cloud Service] Foundation {#foundation}

### 콘텐츠 게재 관련 얼리 어답터 프로그램 {#foundation-early-adopter}

아래의 얼리 어답터 프로그램 중 관심 있는 프로그램을 이 이메일 주소(**<aemcs-cdn-config-adopter@adobe.com>**)로 알려 주십시오.

#### 콘텐츠 전송 네트워크의 기본 인증(얼리 어답터 프로그램) {#basicauth-cdn}

사용자 이름과 암호를 요구하는 기본 인증 대화 상자를 표시하여 특정 콘텐츠 리소스를 보호합니다. 이 기능은 최종 사용자 액세스 권한에 대한 포괄적인 솔루션 역할을 하기보다는 주로 비즈니스 관련자가 콘텐츠를 검토하는 것과 같은 간단한 인증 사용 사례를 대상으로 합니다. 사용자 이름과 암호는 비밀 유형 Cloud Manager 환경 변수를 참조하여 구성 파이프라인을 통해 배포되는 git의 구성 파일을 통해 관리됩니다. [자세히 알아보기](/help/implementing/dispatcher/cdn-credentials-authentication.md#basic-auth).

#### 클라이언트측 리디렉션(얼리 어답터 프로그램) {#client-side-redirects-early-adopter}

소스 제어에서 301/302 클라이언트측 리디렉션을 구성하고 콘텐츠 전송 네트워크에 배포합니다. [자세히 알아보기](/help/implementing/dispatcher/cdn-configuring-traffic.md#client-side-redirectors).<!-- and join the early adopter program by emailing **<aemcs-cdn-config-adopter@adobe.com>**. --> 요청 및 응답 변환, AEM 외부 사이트로의 라우팅 트래픽 등 [CDN 구성](/help/implementing/dispatcher/cdn-configuring-traffic.md)과 관련하여 이미 사용 가능한 여러 다른 기능이 있습니다.

#### 비즈니스 사용자는 Git 외의 리디렉션을 선언할 수 있습니다(얼리 어답터 프로그램). {#apache-rewritemaps-early-adopter}

AEM 6.5와 유사하게 Apache/Dispatcher는 게시 저장소의 특정 위치에 배치된 재작성 맵을 수집하고 웹 계층 파이프라인 실행 없이 로드합니다. 이 접근 방식을 통해 비즈니스 사용자는 ACS Commons Redirect Map Manager 또는 사용자 정의 애플리케이션과 같은 스프레드시트나 UI를 사용하여 리디렉션을 선언할 수 있습니다. <!-- Please reach out to **<aemcs-cdn-config-adopter@adobe.com>** for more information. -->

#### 동적 콘텐츠 로드를 위한 ESI(에지측 포함)(얼리 어답터 프로그램) {#esi-early-adopter}

이제 Adobe Managed CDN은 에지 수준 동적 웹 콘텐츠 어셈블리를 위한 마크업 언어인 [ESI(에지측 포함)](/help/implementing/dispatcher/edge-side-includes.md)를 지원합니다. ESI 스니펫을 포함하면 더 높은 TTL을 사용하여 CDN에서 전체 HTML 페이지를 캐싱하는 동시에 더 높은 케이던스 업데이트(낮은 TTL)가 필요한 작은 섹션을 출처에서 더 자주 가져올 수 있습니다. <!--Please reach out to **<aemcs-cdn-config-adopter@adobe.com>** for more information.-->


## [!DNL Experience Manager] 안내서 {#guides}

[여기](https://experienceleague.adobe.com/ko/docs/experience-manager-guides/using/release-info/release-notes/cloud-release-notes/2024-releases/2406-release/whats-new-2024-06-0)에서 Adobe Experience Manager Guides 최신 릴리스의 새로운 기능과 향상된 기능의 전체 목록을 찾을 수 있습니다.

## Cloud Manager {#cloud-manager}

[여기](/help/implementing/cloud-manager/release-notes/current.md)에서 Cloud Manager 월별 릴리스의 전체 목록을 찾을 수 있습니다.

## 마이그레이션 도구 {#migration-tools}

[여기](/help/journey-migration/release-notes/release-notes-migration-tools-current.md)에서 마이그레이션 도구의 전체 목록을 찾을 수 있습니다.

## 범용 편집기 {#universal-editor}

[여기](/help/release-notes/universal-editor/current.md)에서 범용 편집기의 전체 목록을 찾을 수 있습니다.

## 변형 생성 {#generate-variations}

[여기](/help/generative-ai/release-notes-generate-variations.md)에서 변형 생성의 전체 목록을 찾을 수 있습니다.

## Experience Cloud 릴리스 정보 {#experience-cloud}

다른 Experience Cloud 애플리케이션 릴리스에 대한 정보는 [여기](https://experienceleague.adobe.com/ko/docs/release-notes/experience-cloud/current)에서 확인할 수 있습니다.
