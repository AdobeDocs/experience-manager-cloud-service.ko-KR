---
title: ' [!DNL Adobe Experience Manager] as a Cloud Service 최신 릴리스 정보'
description: ' [!DNL Adobe Experience Manager] as a Cloud Service 최신 릴리스 정보'
mini-toc-levels: 1
exl-id: a2d56721-502c-4f4e-9b72-5ca790df75c5
source-git-commit: 758960006bd1e58530fdf7b20cdd761853170366
workflow-type: tm+mt
source-wordcount: '981'
ht-degree: 41%

---

# [!DNL Adobe Experience Manager] as a Cloud Service 최신 릴리스 정보 {#release-notes}

다음 섹션에서는 [!DNL Experience Manager] as a Cloud Service의 최신 버전 기능 릴리스 정보에 대해 간략히 소개합니다.

>[!NOTE]
>
>여기에서 2021년 또는 2022년과 같은 이전 버전의 릴리스 정보로 이동할 수 있습니다.
>
>[!DNL Experience Manager] as a Cloud Service의 향후 기능 활성화에 대해 알아보려면 [Experience Manager 릴리스 로드맵](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html)을 살펴보십시오.

>[!NOTE]
>
>릴리스와 직접적으로 관련되지 않는 설명서 업데이트의 세부 정보는 [설명서 업데이트](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html)를 참조하십시오.

## 릴리스 일자 {#release-date}

의 릴리스 날짜 [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] 현재 기능 릴리스(2023.7.0)는 2023년 7월 27일입니다. 다음 기능 릴리스(2023.8.0)는 2023년 8월 31일에 예정되어 있습니다.

## 릴리스 비디오 {#release-video}

2023년 7월 릴리스 개요 비디오를 통해 2023.6.0 릴리스에 추가된 기능에 대한 간단한 요약을 살펴보십시오.

>[!VIDEO](https://video.tv.adobe.com/v/3422016/?quality=12)

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### [!DNL Experience Manager Sites]의 새로운 기능 {#sites-features}

* 콘텐츠 조각용 MSM. 이제 콘텐츠 조각에 AEM Multisite Manager를 사용할 수 있으며 벌크 콘텐츠 배포를 위해 콘텐츠 조각 라이브 카피를 만들 수 있습니다. 세분화된 상속 컨트롤은 콘텐츠 조각 요소 및 변형 수준까지 사용할 수 있습니다.

### [!DNL Experience Manager Sites] 프리릴리스의 새로운 기능 {#prerelease-sites}

* 다음 [콘텐츠 조각 콘솔](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/sites/administering/content-fragments/content-fragments-console.html?lang=ko) 이제 사용자는 태그를 보고 콘텐츠 조각에 메타데이터로 적용된 태그로 검색할 수 있습니다. 사용자는 이 기능을 위해 더 이상 Assets UI로 전환할 필요가 없어 컨텍스트 전환이 줄어들고 효율성이 향상됩니다.

![콘텐츠 조각 콘솔의 태깅](/help/assets/content-fragments-console-tags.png)

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### Assets 보기의 새로운 기능 {#assets-view-features}

**폴더에 메타데이터 양식 할당**

이제 Assets Essentials 배포 내의 특정 폴더에 메타데이터 양식을 할당할 수 있습니다. 하위 폴더의 에셋을 포함하여 폴더의 모든 에셋은 할당된 메타데이터 양식에 정의된 속성을 표시합니다.

![폴더에 메타데이터 양식 할당](/help/release-notes/assets/assign-to-folder.png)

**이미지 스마트 태그를 위한 인공 지능 프레임워크 개선**

Experience Manager Assets는 이제 이미지 스마트 태그에 대해 향상된 인공 지능 프레임워크를 사용합니다. 이 콘텐츠 인텔리전스는 수집 시 모든 이미지 에셋에 사용할 수 있는 스마트 태그의 관련성과 정확성을 향상시킵니다.

**자산 목록 보기에 대한 열 표시 구성**

이제 Assets Essentials은 상태, 형식, Dimension, 크기 등과 같이 에셋 목록 보기에 표시되는 열을 선택하는 기능을 제공합니다.

![열 구성](/help/release-notes/assets/configure-columns.png)

**관련성을 기준으로 검색 결과 정렬**

이제 Assets Essentials은 기본적으로 관련성을 기준으로 검색 결과를 정렬합니다. 검색된 자산을 `Name`, `Relevance`, `Size`, `Modified` 및 `Created`의 오름차순 또는 내림차순으로 정렬할 수 있습니다.


## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### [!DNL Forms] 프리릴리스에서 사용 가능한 새로운 기능 {#new-features-available-in-forms-channel}

* [**기본 제공 테마**](/help/forms/using-themes-in-core-components.md) **및 템플릿**: 숙련된 전문가와 새로운 양식 작성자 모두에게 권한을 부여하도록 맞춤화된 즉시 사용할 수 있는 OOTB 테마 및 템플릿을 사용하여 양식 작성 프로세스를 시작하십시오. 적응형 Forms 핵심 구성 요소를 사용하여 간편하게 빌드된 이 세심하게 조정된 테마와 템플릿을 사용하면 일반적인 사용 사례에서 신속하게 양식을 만들 수 있습니다.

!![기본 제공 템플릿](/help/forms/assets/form-templates-ootb.png)

* **Headless Forms용 React 구성 요소**: 이제 즉시 제공된 React 구성 요소로 Headless 적응형 양식 렌디션을 미리 보고 사용자 정의할 수 있습니다. 이러한 구성 요소는 스타일을 지정하기 위해 적응형 Forms 핵심 구성 요소의 BEM 클래스를 활용하므로 특정 요구 사항에 따라 모양을 손쉽게 사용자 지정할 수 있습니다.

* [**반복 가능한 섹션이 포함된 적응형 Forms 만들기**](/help/forms/create-forms-repeatable-sections.md): 이제 다음을 수행할 수 있습니다. [어코디언](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/accordion.html), [마법사](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/wizard.html), [패널](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/panel-container.html), 및 [가로 탭](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/horizontal-tabs.html) 여러 데이터 레코드 캡처를 위한 적응형 양식 기반 구성 요소.  이러한 반복 가능한 섹션을 통해 여러 데이터 항목을 쉽게 제공할 수 있습니다. 필요한 데이터 인스턴스를 미리 알 수 없는 경우에 유용합니다. 양식 작성기를 사용하면 섹션을 쉽게 추가하거나 제거할 수 있으므로 양식을 다양한 데이터 입력 시나리오에 맞게 조정할 수 있으며 동일한 데이터 레코드의 여러 항목을 간편하게 수집할 수 있습니다.


### 에서 사용할 수 있는 프리릴리스 기능 [!DNL Forms] {#pre-release-features-available-in-forms-channel}

* [**Google reCAPTCHA 엔터프라이즈 지원**](/help/forms/captcha-adaptive-forms.md): 적응형 양식에서 Google reCAPTCHA Enterprise를 사용하여 사기 활동 및 스팸에 대한 향상된 보호를 제공하여 보다 안전한 사용자 경험을 제공합니다. 고급 위험 분석과 원활한 통합을 통해 정품 사용자는 손쉽게 양식을 제출할 수 있으며 봇은 효과적으로 차단됩니다.

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

즉각적인 조치가 필요한 중요한 사고가 발생할 때 경고하는 이메일 알림을 구독하고 사이트를 최적화하기 위한 개인화된 권장 사항을 제공합니다. [작업 센터](/help/operations/actions-center.md) 복제 큐 차단 또는 자격 증명 만료 등 이러한 경고를 검토하고 해결됨으로 표시할 수 있는 허브 역할을 합니다.

![작업 센터 스크린샷](/help/assets/assets/actions-center.png)

### CDN 및 WAF 규칙 얼리 어답터 프로그램 {#waf-early-adopter}

다음을 기반으로 CDN의 트래픽 필터링:
* 요청 헤더 및 속성(예: IP 주소)
* 악성 트래픽과 관련된 것으로 알려진 트래픽 패턴

기능을 테스트하고 피드백을 공유하는 데 관심이 있으십니까? 다음으로 이메일 보내기 **aemcs-waf-adopter@adobe.com** 얼리어답터 프로그램에 대한 자세한 내용은 공식 이메일 ID에서 확인하십시오. 공간이 제한되어 있습니다.

문서의 기능에 대해 자세히 알아보기 [여기](/help/security/cdn-and-waf-rules.md).

### 기타 기초 변경 사항 {#other-foundation-changes}

* 8월 7일이 있는 주 동안 AEM 인스턴스에 대한 요청이 정상 수준을 초과하면 AEM은 오류 코드 503 대신 오류 코드 429를 반환합니다. [자세히 알아보기](/help/implementing/developing/introduction/development-guidelines.md).

## 유지 관리 릴리스 정보 {#maintenance}

[ 여기](/help/release-notes/maintenance/latest.md)에서 최신 유지 관리 릴리스 정보를 확인할 수 있습니다.

## Cloud Manager {#cloud-manager}

[여기](/help/implementing/cloud-manager/release-notes/current.md)에서 Cloud Manager 월별 릴리스의 전체 목록을 찾을 수 있습니다.

## 마이그레이션 도구 {#migration-tools}

[여기](/help/journey-migration/release-notes/release-notes-migration-tools-current.md)에서 마이그레이션 도구의 전체 목록을 찾을 수 있습니다.
