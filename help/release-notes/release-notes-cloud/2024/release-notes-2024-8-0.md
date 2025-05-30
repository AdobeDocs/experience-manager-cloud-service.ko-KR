---
title: ' [!DNL Adobe Experience Manager] as a Cloud Service의 2024.8.0 릴리스 정보입니다.'
description: ' [!DNL Adobe Experience Manager] as a Cloud Service의 2024.8.0 릴리스 정보입니다.'
feature: Release Information
role: Admin
exl-id: dd1d4b8f-8331-4e97-a754-37e720974db6
source-git-commit: 4b8086920bc3e3b9c5ed2a74934645fbc69acf71
workflow-type: tm+mt
source-wordcount: '1173'
ht-degree: 98%

---

# [!DNL Adobe Experience Manager] as a Cloud Service 2024.8.0 릴리스 정보 {#release-notes}

다음 섹션에서는 [!DNL Experience Manager] as a Cloud Service의 2024.8.0 버전 기능 릴리스 정보에 대해 간략히 소개합니다.

>[!NOTE]
>
>여기에서 2022년 또는 2023년과 같은 이전 버전의 릴리스 정보로 이동할 수 있습니다.
>
>[!DNL Experience Manager] as a Cloud Service의 향후 기능 활성화에 대해 알아보려면 [Experience Manager 릴리스 로드맵](https://experienceleague.adobe.com/ko/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap)을 살펴보십시오.

>[!NOTE]
>
>Experience Cloud 릴리스 정보의 업데이트에 대한 월별 이메일 알림을 받아 보려면 [Adobe 우선순위 제품 업데이트](https://www.adobe.com/kr/subscription/priority-product-update.html)를 구독하십시오.

## 릴리스 일자 {#release-date}

[!DNL Adobe Experience Manager] as a [!DNL Cloud Service] 현재 기능 릴리스(2024.8.0)의 릴리스 일자는 2024년 8월 29일입니다. 다음 기능 릴리스(2024.9.0)는 2024년 9월 26일에 예정되어 있습니다.

## 유지 관리 릴리스 정보 {#maintenance}

[ 여기](/help/release-notes/maintenance/latest.md)에서 최신 유지 관리 릴리스 정보를 확인할 수 있습니다.

## 릴리스 비디오 {#release-video}

2024년 8월 릴리스 개요 비디오를 통해 2024.8.0 릴리스에 추가된 기능에 대한 간단한 요약을 살펴보십시오.

>[!VIDEO](https://video.tv.adobe.com/v/3433381?quality=12)

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### Experience Manager Sites의 새로운 기능 {#new-feature-sites}

**Edge Delivery Services를 위한 AEM 작성**

이제 다음이 포함된 기존 사이트 [상속](/help/sites-cloud/authoring/universal-editor/inheritance.md) 기능이 지원됩니다.

* [AEM 론치](/help/sites-cloud/authoring/launches/overview.md)
* 페이지 수준의 [MSM](/help/sites-cloud/administering/msm/overview.md)

또한 다음 페이지 관리 기능이 지원됩니다.

* [AEM 태그](/help/sites-cloud/authoring/sites-console/tags.md)는[분류 체계](/help/edge/wysiwyg-authoring/taxonomy.md)로서 Edge Delivery Services로 내보낼 수 있습니다.
* Edge Delivery Services용 [템플릿](/help/sites-cloud/authoring/universal-editor/templates.md)이 곧 제공될 예정입니다.

### 얼리 어답터 프로그램 {#sites-early-adopter}

**변형 생성**

이제 Cloud Service에서 액세스 가능한 AEM의 새로운 기능인 [변형 생성](/help/generative-ai/generate-variations.md)을 통해 GenAI를 활용할 수 있습니다. 변형 생성은 생성형 AI를 사용하여 콘텐츠 제작을 생성하고 확장하는 데 도움이 됩니다. 프로그램 참여를 고려한다면 Adobe 계정 팀에 문의하십시오.


## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### Assets 보기의 새로운 기능 {#assets-view-new-features}

**업데이트된 Adobe Firefly 이미지 생성**

이제 Assets as a Cloud Service는 Adobe Firefly를 통해 다양한 스타일의 이미지를 생성할 수 있는 Firefly에서 최신 위젯을 사용합니다. 내장된 Firefly 편집기를 사용하여 스타일, 구성, 차원 등을 정의하면 AEM Assets 저장소에서 직접 필요한 자산을 빠르게 만들고 저장하여 즉시 사용할 수 있습니다.

![Adobe Firefly 이미지 생성](/help/assets/assets/bugatti-type-57.png)

**PSB 파일 지원**

이제 Assets as a Cloud Service는 기존 PSD 파일 지원 외에도 Photoshop 대용량 문서(PSB 파일)을 지원합니다.

### Content Hub에 대한 새로운 개선 사항 {#content-hub-new-enhancements}

* 긴 파일 이름을 처리하고, 작업 도구 설명을 통해 전체 이름을 간단히 확장할 수 있습니다.
* 콘텐츠 종횡비에 맞게 큰 콘텐츠 영역을 포함하도록 썸네일을 개선합니다.
* 콘텐츠 허브를 통해 지원되는 AEM에서 썸네일 경험을 사용자 정의합니다.
* 색상 검색이 개선되었습니다.
* 구성 저장 경험이 개선되었습니다.
* 작성자 이름을 반영하기 위해 컬렉션의 정보 페이지가 개선되었습니다.


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

* **제품 쿼리용 AI 어시스턴트**: AEM 양식 관련 질문에 대한 즉각적인 답변을 얻습니다. AI 어시스턴트는 사용자 개인의 기술 자료로서 플랫폼에서 직접 통찰력 있는 지침 및 권장 사항을 제공합니다.

* **적응형 양식 생성**: 생성형 AI 프롬프트를 사용하여 완전한 양식을 손쉽게 만듭니다. 생성형 AI는 드롭오프를 줄이고 경험을 개인화하는 사용자 친화적인 양식을 자동으로 생성합니다.

* **양식용 패널 생성**: 특정 데이터 수집 요구에 맞춰 양식 섹션을 생성합니다. 예를 들어 결제 정보, 고객 선호도, 여행 세부 정보를 수집하는 섹션을 생성합니다.

* **양식 레이아웃 변경**: 생성형 AI 프롬프트를 사용하여 다양한 레이아웃과 디자인을 실험합니다. 마법사 또는 탭 보기 등 다양한 레이아웃을 사용하여 양식에 가장 잘 맞는 디자인을 찾아보십시오. 생성형 AI 프롬프트를 사용하여 모바일 응답성을 위해 양식을 최적화하고 사용자의 마음에 드는 시각적으로 매력적인 양식을 만듭니다.

* **제출 액션 구성**: 생성형 AI 프롬프트를 사용하여 양식의 제출 액션을 간편하게 구성합니다. 사전 빌드된 제출 액션 라이브러리에서 선택하거나, 자체 개발 팀에서 만들고 배포한 사용자 정의 제출 액션 목록에서 선택합니다.

>[!IMPORTANT]
>
> 얼리 액세스 혁신을 위해 얼리 액세스 프로그램에 참여하고 싶다면 관심 있는 기능 목록과 함께 공식 주소에서 [aem-forms-ea@adobe.com](mailto:aem-forms-ea@adobe.com)으로 이메일을 보내면 됩니다.


## [!DNL Experience Manager] as a [!DNL Cloud Service] Foundation {#foundation}

### 콘텐츠 게재 관련 얼리 어답터 프로그램 {#foundation-early-adopter}

아래의 얼리 어답터 프로그램 중 관심 있는 프로그램을 이 이메일 주소(**<aemcs-cdn-config-adopter@adobe.com>**)로 알려 주십시오.

#### 콘텐츠 전송 네트워크의 기본 인증(얼리 어답터 프로그램) {#basicauth-cdn}

사용자 이름과 암호를 요구하는 기본 인증 대화 상자를 표시하여 특정 콘텐츠 리소스를 보호합니다. 이 기능은 최종 사용자 액세스 권한에 대한 포괄적인 솔루션 역할을 하기보다는 주로 비즈니스 관련자가 콘텐츠를 검토하는 것과 같은 간단한 인증 사용 사례를 대상으로 합니다. 사용자 이름과 암호는 비밀 유형 Cloud Manager 환경 변수를 참조하여 구성 파이프라인을 통해 배포되는 git의 구성 파일을 통해 관리됩니다. [자세히 알아보기](/help/implementing/dispatcher/cdn-credentials-authentication.md#basic-auth).

#### 서버측 리디렉션(얼리 어답터 프로그램) {#server-side-redirects-early-adopter}

소스 제어에서 301/302 서버측 리디렉션을 구성하고 CDN에 배포합니다. [자세히 알아보기](/help/implementing/dispatcher/cdn-configuring-traffic.md#server-side-redirectors).<!-- and join the early adopter program by emailing **<aemcs-cdn-config-adopter@adobe.com>**. --> 요청 및 응답 변환, AEM 외부 사이트로의 라우팅 트래픽 등 [CDN 구성](/help/implementing/dispatcher/cdn-configuring-traffic.md)과 관련하여 이미 사용 가능한 여러 다른 기능이 있습니다.

#### 비즈니스 사용자는 Git 외의 리디렉션을 선언할 수 있습니다(얼리 어답터 프로그램). {#apache-rewritemaps-early-adopter}

AEM 6.5와 유사하게 Apache/Dispatcher는 게시 저장소의 특정 위치에 배치된 재작성 맵을 수집하고 웹 계층 파이프라인 실행 없이 로드합니다. 이 접근 방식을 통해 비즈니스 사용자는 ACS Commons Redirect Map Manager 또는 사용자 정의 애플리케이션과 같은 스프레드시트나 UI를 사용하여 리디렉션을 선언할 수 있습니다. <!-- Please reach out to **<aemcs-cdn-config-adopter@adobe.com>** for more information. -->

#### 동적 콘텐츠 로드를 위한 ESI(에지측 포함)(얼리 어답터 프로그램) {#esi-early-adopter}

이제 Adobe Managed CDN은 에지 수준 동적 웹 콘텐츠 어셈블리를 위한 마크업 언어인 [ESI(에지측 포함)](/help/implementing/dispatcher/edge-side-includes.md)를 지원합니다. ESI 스니펫을 포함하면 더 높은 TTL을 사용하여 CDN에서 전체 HTML 페이지를 캐싱하는 동시에 더 높은 케이던스 업데이트(낮은 TTL)가 필요한 작은 섹션을 출처에서 더 자주 가져올 수 있습니다. <!--Please reach out to **<aemcs-cdn-config-adopter@adobe.com>** for more information.-->

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
