---
title: ' [!DNL Adobe Experience Manager] as a Cloud Service의 2024.7.0 릴리스 정보입니다.'
description: ' [!DNL Adobe Experience Manager] as a Cloud Service의 2024.7.0 릴리스 정보입니다.'
feature: Release Information
role: Admin
source-git-commit: 2edaca5637c735645e2b761377b9681d9b48daa1
workflow-type: tm+mt
source-wordcount: '1518'
ht-degree: 100%

---

# [!DNL Adobe Experience Manager] as a Cloud Service 2024.7.0 릴리스 정보 {#release-notes}

다음 섹션에서는 [!DNL Experience Manager] as a Cloud Service의 2024.7.0 버전 기능 릴리스 정보에 대해 간략히 소개합니다.

>[!NOTE]
>
>여기에서 2022년 또는 2023년과 같은 이전 버전의 릴리스 정보로 이동할 수 있습니다.
>
>[!DNL Experience Manager] as a Cloud Service의 향후 기능 활성화에 대해 알아보려면 [Experience Manager 릴리스 로드맵](https://experienceleague.adobe.com/ko/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap)을 살펴보십시오.

>[!NOTE]
>
>Experience Cloud 릴리스 정보의 업데이트에 대한 월별 이메일 알림을 받아 보려면 [Adobe 우선 순위 제품 업데이트](https://www.adobe.com/kr/subscription/priority-product-update.html)를 구독하십시오.

## 릴리스 일자 {#release-date}

[!DNL Adobe Experience Manager] as a [!DNL Cloud Service] 현재 기능 릴리스(2024.7.0)의 릴리스 일자는 2024년 7월 25일입니다. 다음 기능 릴리스(2024.8.0)는 2023년 8월 29일에 예정되어 있습니다.

## 유지 관리 릴리스 정보 {#maintenance}

[ 여기](/help/release-notes/maintenance/latest.md)에서 최신 유지 관리 릴리스 정보를 확인할 수 있습니다.

## 릴리스 비디오 {#release-video}

2023년 7월 릴리스 개요 비디오를 통해 2024.7.0 릴리스에 추가된 기능에 대한 간단한 요약을 살펴보십시오.

>[!VIDEO](https://video.tv.adobe.com/v/3431707?quality=12)

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### Experience Manager Sites의 새로운 기능 {#new-feature-sites}

### 얼리 어답터 프로그램 {#sites-early-adopter}

**변형 생성**

이제 클라우드 서비스에서 액세스 가능한 AEM의 새로운 기능인 [변형 생성](/help/generative-ai/generate-variations.md)을 통해 GenAI를 활용할 수 있습니다. 변형 생성은 생성형 AI를 사용하여 콘텐츠 제작을 생성하고 확장하는 데 도움이 됩니다. 프로그램 참여를 고려한다면 Adobe 계정 팀에 문의하십시오.

**콘텐츠 조각 콘솔에서 자산 찾아보기**

이제 콘텐츠 작성자는 콘텐츠 조각 콘솔을 종료하지 않고도 이미지 및 기타 자산을 찾아보고, 보고, 작업을 수행할 수 있습니다.

![자산 찾아보기](/help/sites-cloud/administering/content-fragments/assets/cf-console-assets-browse.png)

기능을 사용해 보고 피드백을 공유하고 싶으십니까? 공식 이메일 ID로 aemcs-headless-adopter@adobe.com에 이메일을 보내 얼리 어답터 프로그램에 대해 자세히 알아보십시오.

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

**자산 선택기를 사용하여 자산 업로드**

이제 자산 선택기는 콘텐츠 작성자가 드래그하거나 로컬 파일 시스템에서 검색하여 최종 자산을 선택기에 직접 업로드할 수 있는 기능을 제공합니다. 이를 통해 선택한 애플리케이션에서 최종 자산을 DAM에 업로드할 수 있습니다.

### Assets 보기의 새로운 기능 {#assets-view-new-features}

**콘텐츠 자격 증명 통합**

이제 Experience Manager Assets는 지원되는 이미지 형식에 대해 콘텐츠 자격 증명을 지원합니다. 이를 통해 생성형 AI를 사용하여 수정되었는지 여부 등 자산의 계보와 생성 방법에 대한 정보를 제공합니다.

![콘텐츠 자격 증명](/help/assets/assets/content-credentials.png)

**폴더 콘텐츠의 시각적 미리보기**

이제 Experience Manager Assets는 콘텐츠를 탐색하거나 검색할 때 폴더 썸네일에 폴더 내용의 시각적 미리보기를 표시하므로 AEM Assets 저장소 내에서 사용할 수 있는 자산의 검색 가능성이 향상됩니다.

<!--


**Content Credentials**

Content Credentials feature in Assets view now provides detailed asset provenance data adhered to an asset. This helps to trace the enroute edits along the asset's lifecycle to prevent users from deception through deliberately tempered assets. This ensures content authenticity among users and fosters trust through transparency.

When looking at the asset details, any image with content credentials added, such as those created with GenAI, displays the manifest details in a dedicated panel. If the asset is downloaded, published, or shared, the credentials remain intact with the asset.

![check publish status1](/help/release-notes/assets/content-credentials.png)

-->

## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### AEM Forms의 새로운 기능 {#forms-new-prerelease-features}

#### 핵심 구성 요소 기반의 적응형 양식을 위한 향상된 시각적 규칙 편집기

적응형 양식 작성자는 사용자 정의나 개발 팀의 도움 없이도 핵심 구성 요소에 대해 시각적 규칙 편집기에서 사용할 수 있는 반복 가능한 양식 필드를 사용하여 양식의 복잡한 비즈니스 로직을 구축할 수 있습니다.

### AEM Forms의 얼리 액세스 기능 {#forms-new-early-access-features}

AEM Forms 얼리 액세스 프로그램은 누구보다 먼저 최첨단 혁신에 독점적으로 액세스할 수 있는 특별한 기회를 제공하며, 혁신의 발전을 구체화하는 데 도움을 줍니다. 이 프로그램은 여러 혁신에 액세스할 수 있습니다.

이 릴리스 정보에는 현재 릴리스에서 제공되는 혁신 사항이 나열되어 있습니다. 얼리 액세스 프로그램에서 사용할 수 있는 전체 혁신 목록은 [AEM Forms 얼리 액세스 프로그램 설명서](/help/forms/early-access-ea-features.md)를 참조하십시오.

#### 범용 편집기를 사용하여 적응형 양식 작성

Adobe Experience Manager [범용 편집기](https://experienceleague.adobe.com/ko/docs/experience-manager-cloud-service/content/implementing/developing/universal-editor/introduction)를 사용하여 Edge Delivery Service를 통해 제공되는 헤드리스 및 헤드풀 등록 경험 모두에서 WYSIWYG 드래그 앤 드롭 작성 기능을 사용하여 적응형 양식을 만듭니다. 적응형 양식 작성자는 웹 페이지에서 양식의 변형에 대한 실험을 쉽게 만들고 실행할 수 있으며 최종 사용자를 위한 최상의 성능 경험을 결정할 수 있습니다.

>[!IMPORTANT]
>
> 얼리 액세스 혁신을 위해 Adobe의 얼리 액세스 프로그램에 참여하고 싶다면 공식 주소에서 [aem-forms-ea@adobe.com](mailto:aem-forms-ea@adobe.com)으로 이메일을 보내 액세스 권한을 요청하십시오. 전체 또는 특정 혁신에 대한 액세스를 요청할 수 있습니다.

## [!DNL Experience Manager] as a [!DNL Cloud Service] Foundation {#foundation}

### 셀프서비스 API 키로 콘텐츠 전송 네트워크에서 콘텐츠 삭제 {#purge-cdn}

HTTP Cache-Control 헤더를 사용하여 TTL을 설정하는 것은 콘텐츠 게재 성능과 콘텐츠 신선도의 균형을 맞추는 효과적인 방법입니다. 그러나 업데이트된 콘텐츠를 즉시 서비스하는 것이 중요한 상황에서는 콘텐츠 전송 네트워크 캐시를 직접 제거하는 것이 유용할 수 있습니다.

Cloud Manager 구성 파이프라인을 사용하여 삭제 API 토큰을 셀프서비스로 구성하는 방법에 대해 [자세히 알아보십시오](/help/implementing/dispatcher/cdn-credentials-authentication.md#purge-API-token). 다음과 같은 변형을 사용하여 [삭제 API를 호출](/help/implementing/dispatcher/cdn-cache-purge.md)할 수 있습니다.
* 단일 URL
* 태그를 사용한 여러 URL
* 전체 콘텐츠 전송 네트워크 캐시 삭제

### 고객 관리 콘텐츠 전송 네트워크를 위한 X-AEM-Edge-Key의 셀프서비스 구성 {#customermanaged-keys}

이전에는 고객 관리형 콘텐츠 전송 네트워크 구성에 필요한 X-AEM-Edge-Key를 생성하려면 지원 티켓이 필요했습니다. 이제 구성 파이프라인을 사용하여 배포되는 구성 파일에서 키 값을 선언하여 셀프서비스를 수행할 수 있으므로 새 환경에 대한 온보딩 작업이 지연되지 않습니다. [자세히 알아보기](/help/implementing/dispatcher/cdn-credentials-authentication.md#CDN-HTTP-value).

### 트래픽 필터 규칙 경고 {#traffic-filter-rules-alerts}

선택적으로 라이선스를 부여할 수 있는 WAF(웹 애플리케이션 방화벽) 규칙을 포함하는 트래픽 필터 규칙을 통해 차단되는 트래픽을 구성할 수 있습니다.

이제 트래픽 필터 규칙이 트리거될 때마다 [경고를 구독](/help/security/traffic-filter-rules-including-waf.md#traffic-filter-rules-alerts)할 수 있습니다. 액션 센터 이메일 알림은 특정 트래픽 상황이 발생할 때 적절한 조치를 취할 수 있도록 지속적으로 정보를 제공해 줍니다.

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

### 콘텐츠 상태 관련 액션 센터 알림 얼리 어답터 프로그램 {#actions-center-notifications}

[액션 센터](/help/operations/actions-center.md)는 중요한 사고가 발생하거나 사용자가 사전 예방 조치를 취해야 할 코드 또는 구성에 대해 발견한 경우 이메일 알림을 보냅니다. Adobe는 이제 콘텐츠 상태와 관련된 몇 가지 새로운 유형의 알림을 도입했습니다. 이 기능은 얼리 어답터 프로그램을 통해 사용할 수 있습니다. 참여하려면 Adobe 고객 지원 센터에 문의하십시오.

#### 페이지에 많은 수의 노드가 포함됨 {#page-nodes}

노드 수가 많으면 렌더링 성능이 저하되고 페이지 로드 시간이 단축될 수 있습니다. 페이지에서 많은 수의 노드가 감지되면 액션 센터를 통해 사전 알림을 받아 페이지 내 총 노드 수를 줄이는 데 필요한 조치를 취할 수 있습니다.

#### 실행 중인 워크플로 인스턴스 수가 너무 많음 {#running-workflows}

작성자 환경에서 실행 중인 워크플로 수가 많으면 워크플로 엔진 성능이 영향을 받습니다. 실행 중인 워크플로 인스턴스가 너무 많이 감지되면 액션 센터를 통해 사전 알림을 받습니다. 이 프로세스를 통해 불필요하게 실행 중인 워크플로를 종료하도록 제거 작업을 구성할 수 있습니다.

#### 사용자 정의 그룹에 사용자가 바로 추가됨 {#users-customgroups}

사용자가 사용자 정의 그룹에 바로 추가되면 액션 센터를 통해 사전 알림을 받습니다. 이 프로세스를 통해 관련 IMS 그룹에 사용자를 추가한 다음 해당 IMS 그룹을 AEM 그룹의 멤버로 포함하여 IMS 모범 사례를 따를 수 있습니다.

#### JCR 콘텐츠 누락 {#jcr-content}

JCR 콘텐츠 누락이 감지되면 액션 센터를 통해 사전 알림을 받습니다. 이러한 접근 방식을 통해 누락된 콘텐츠를 추가하고 특정 AEM Assets 기능의 실패를 방지할 수 있습니다.

#### 완료된 워크플로가 제거되지 않음 {#workflows}

완료된 지 90일이 넘은 워크플로가 제거되지 않은 경우 액션 센터를 통해 사전 알림을 받습니다. 이러한 접근 방식은 워크플로 인스턴스 수를 줄여 워크플로 엔진의 성능을 개선하는 데 도움이 됩니다.

#### Sling 리소스 누락 {#sling-resource}

Sling 리소스 누락이 감지되면 액션 센터를 통해 사전 알림을 받습니다. 이러한 접근 방식을 통해 누락된 리소스를 추가하고 특정 AEM Assets 기능의 실패를 방지할 수 있습니다.

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
