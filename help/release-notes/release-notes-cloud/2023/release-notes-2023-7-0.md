---
title: ' [!DNL Adobe Experience Manager] as a Cloud Service의 2023.7.0 릴리스 정보입니다.'
description: ' [!DNL Adobe Experience Manager] as a Cloud Service의 2023.7.0 릴리스 정보입니다.'
exl-id: 7866d94c-e54c-4bb2-aaa6-66c019e46336
source-git-commit: a77e5dc4273736b969e9a4a62fcac75664495ee6
workflow-type: ht
source-wordcount: '896'
ht-degree: 100%

---

# [!DNL Adobe Experience Manager] as a Cloud Service 2023.7.0 릴리스 정보 {#release-notes}

다음 섹션에서는 [!DNL Experience Manager] as a Cloud Service의 2023.7.0 버전 기능 릴리스 정보에 대해 간략히 소개합니다.

>[!NOTE]
>
>여기에서 2021년 또는 2022년과 같은 이전 버전의 릴리스 정보로 이동할 수 있습니다.
>
>[!DNL Experience Manager] as a Cloud Service의 향후 기능 활성화에 대해 알아보려면 [Experience Manager 릴리스 로드맵](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html)을 살펴보십시오.

>[!NOTE]
>
>릴리스와 직접적으로 관련되지 않는 설명서 업데이트의 세부 정보는 [최신 설명서 업데이트](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html)를 참조하십시오.

## 릴리스 일자 {#release-date}

[!DNL Adobe Experience Manager] as a [!DNL Cloud Service] 현재 기능 릴리스(2023.7.0)의 릴리스 일자는 2023년 7월 27일입니다. 다음 기능 릴리스(2023.8.0)는 2023년 8월 31일에 예정되어 있습니다.

## 릴리스 비디오 {#release-video}

2023년 7월 릴리스 개요 비디오를 통해 2023.7.0 릴리스에 추가된 기능에 대한 간단한 요약을 살펴보십시오.

>[!VIDEO](https://video.tv.adobe.com/v/3422016/?quality=12)

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### [!DNL Experience Manager Sites]의 새로운 기능 {#sites-features}

* 콘텐츠 조각의 MSM. 이제 AEM Multisite Manager를 콘텐츠 조각에 사용할 수 있으므로 대량 콘텐츠 배포를 위한 콘텐츠 조각 라이브 카피를 만들 수 있습니다. 콘텐츠 조각 요소 및 변형 수준까지 세분화된 상속 제어를 사용할 수 있습니다.

### [!DNL Experience Manager Sites] 프리릴리스의 새로운 기능 {#prerelease-sites}

* 이제 사용자는 [콘텐츠 조각 콘솔](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/sites/administering/content-fragments/content-fragments-console.html)을 사용하여 콘텐츠 조각에 메타데이터로 적용된 태그를 보고 검색할 수 있습니다. 사용자가 더 이상 이 기능을 사용하기 위해 자산 UI로 전환할 필요가 없으므로 컨텍스트 전환이 줄어들고 효율성이 향상됩니다.

![콘텐츠 조각 콘솔에서 태그 지정](/help/assets/content-fragments-console-tags.png)

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### Assets 보기의 새로운 기능 {#assets-view-features}

<!--

**Assign metadata form to a folder**

You can now assign metadata form to a specific folder within your Assets Essentials deployment. All assets in the folder, including assets in the sub-folders, then display properties defined in the assigned metadata form.

![assign metadata form to a folder](/help/release-notes/assets/assign-to-folder.png)

-->

**이미지 스마트 태그에 대해 개선된 인공 지능 프레임워크**

Experience Manager Assets는 이제 이미지 스마트 태그에 대해 향상된 인공 지능 프레임워크를 사용합니다. 이 콘텐츠 인텔리전스는 수집 시 모든 이미지 자산에 사용할 수 있는 스마트 태그의 관련성과 정확성을 향상시킵니다.

**자산 목록 보기에 대한 열 표시 구성**

이제 Assets Essentials가 상태, 형식, 차원, 크기 등과 같이 자산 목록 보기에 표시되는 열을 선택할 수 있는 기능을 제공합니다.

![열 구성](/help/release-notes/assets/configure-columns.png)

**관련성을 기준으로 검색 결과 정렬**

이제 Assets Essentials는 기본적으로 관련성을 기준으로 검색 결과를 정렬합니다. 검색된 자산을 `Name`, `Relevance`, `Size`, `Modified` 및 `Created`의 오름차순 또는 내림차순으로 정렬할 수 있습니다.


## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### [!DNL Forms] 프리릴리스에서 사용 가능한 새로운 기능 {#new-features-available-in-forms-channel}

* [**기본 제공 테마**](/help/forms/using-themes-in-core-components.md)**및 템플릿**: 바로 사용할 수 있으며 노련한 전문가와 초보 양식 작성자 모두의 역량을 강화하도록 맞춤화된 OOTB 테마 및 템플릿으로 양식 작성 프로세스를 시작하십시오. 적응형 양식 핵심 구성 요소를 사용하여 원활하게 구축되었으며 세심하게 선별된 이 테마 및 템플릿을 사용하면 일반적인 사용 사례에 대한 양식을 신속하게 작성할 수 있습니다.

* **[Headless 양식용 React 구성 요소](https://github.com/adobe/aem-forms-headless-components/tree/main/packages/react-vanilla-components)**: 이제 기본 제공 React 구성 요소를 사용하여 Headless 적응형 양식 렌디션을 미리 보고 사용자 정의할 수 있습니다. 이러한 구성 요소는 스타일 지정을 위해 적응형 양식 핵심 구성 요소의 BEM 클래스를 사용하므로 특정 요구 사항에 따라 형태를 쉽게 사용자 정의할 수 있습니다.

* [**반복 가능한 섹션으로 적응형 양식 만들기**](/help/forms/create-forms-repeatable-sections.md): 이제 [아코디언](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/accordion.html), [마법사](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/wizard.html), [패널](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/panel-container.html) 및 [가로 탭](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/horizontal-tabs.html) 구성 요소에 기반한 반복 가능 적응형 양식을 만들어 여러 데이터 레코드 캡처에 사용할 수 있습니다. 이러한 반복 가능한 섹션을 사용하면 여러 데이터 항목을 쉽게 제공할 수 있습니다. 필요한 데이터 인스턴스를 미리 알 수 없는 경우에 유용합니다. 양식 작성기에서 섹션을 쉽게 추가하거나 제거할 수 있으므로, 양식을 다양한 데이터 입력 시나리오에 맞게 조정하고 동일한 데이터 레코드의 여러 항목 수집을 단순화할 수 있습니다.


### [!DNL Forms]에서 사용할 수 있는 프리릴리스 기능 {#pre-release-features-available-in-forms-channel}

* [**Google reCAPTCHA 엔터프라이즈 지원**](/help/forms/captcha-adaptive-forms.md): 적응형 양식에서 Google reCAPTCHA Enterprise를 사용해 사기 행위 및 스팸 방지 기능을 강화하여 보다 안전한 사용자 환경을 제공합니다. 고급 위험 분석 및 원활한 통합을 통해 실제 사용자가 양식을 쉽게 제출할 수 있는 동시에 봇이 효과적으로 차단됩니다.

  >[!VIDEO](https://video.tv.adobe.com/v/3422097/adaptive-forms-recaptcha-core-components-captcha/?quality=12&learn=on)

### Headless 적응형 양식 얼리 어답터 프로그램 {#forms-early-adopter}

[Headless 적응형 양식](https://experienceleague.adobe.com/docs/experience-manager-headless-adaptive-forms/using/overview.html)을 사용하여 개발자가 기존의 그래픽 사용자 인터페이스가 아닌 API를 통해 액세스하고 상호 작용할 수 있는 대화형 양식을 만들고, 게시하고, 관리할 수 있습니다. Headless 적응형 양식은 다음에 도움이 됩니다.

* 선택한 프로그래밍 언어로 고품질 다중 채널 양식 작성
* 양식을 데스크탑 및 모바일 앱, 웹 사이트 및 채팅 애플리케이션에 기본적으로 통합
* 양식 애플리케이션과 함께 독점 UI 구성 요소 재사용
* Adobe Experience Manager Forms의 기능 사용

공식 이메일 ID에서 `aem-forms-headless@adobe.com`으로 이메일을 보내 얼리 어답터 프로그램에 참여할 수 있습니다.

## [!DNL Experience Manager] as a [!DNL Cloud Service] Foundation {#foundation}

### 액션 센터 {#actions-center}

즉각적인 조치가 필요한 중대 인시던트가 발생할 때 알려 주는 이메일 알림과 사이트 최적화를 위한 개인화된 권장 사항을 구독할 수 있습니다. [액션 센터](/help/operations/actions-center.md)는 차단된 복제 대기열 또는 자격 증명 만료와 같은 경고를 검토하고 해결 상태로 표시할 수 있는 허브 역할을 합니다.

![액션 센터 스크린샷](/help/assets/assets/actions-center.png)

### CDN 및 WAF 규칙 얼리 어답터 프로그램 {#waf-early-adopter}

다음을 기준으로 CDN에서 트래픽을 필터링할 수 있습니다.
* 요청 헤더 및 속성(예: IP 주소)
* 악성 트래픽과 관련된 것으로 알려진 트래픽 패턴

기능을 사용해 보고 피드백을 공유하고 싶으십니까? 공식 이메일 ID로 **aemcs-waf-adopter@adobe.com**&#x200B;에 이메일을 보내 얼리 어답터 프로그램에 대해 자세히 알아보십시오. 인원이 한정되어 있습니다.

[여기](/help/security/traffic-filter-rules-including-waf.md)에 있는 문서에서 기능에 대해 자세히 알아보십시오.

### 기타 Foundation 변경 사항 {#other-foundation-changes}

* 8월 7일이 속한 한 주 동안 AEM 인스턴스에 대한 요청이 정상 수준을 초과하면 AEM에서 오류 코드 503 대신 오류 코드 429를 반환합니다. [자세히 알아보기](/help/implementing/developing/introduction/development-guidelines.md).

## 유지 관리 릴리스 정보 {#maintenance}

[ 여기](/help/release-notes/maintenance/latest.md)에서 최신 유지 관리 릴리스 정보를 확인할 수 있습니다.

## Cloud Manager {#cloud-manager}

[여기](/help/implementing/cloud-manager/release-notes/current.md)에서 Cloud Manager 월별 릴리스의 전체 목록을 찾을 수 있습니다.

## 마이그레이션 도구 {#migration-tools}

[여기](/help/journey-migration/release-notes/release-notes-migration-tools-current.md)에서 마이그레이션 도구의 전체 목록을 찾을 수 있습니다.
