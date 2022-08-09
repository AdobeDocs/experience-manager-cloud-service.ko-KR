---
title: ' [!DNL Adobe Experience Manager] as a Cloud Service 최신 릴리스 정보'
description: ' [!DNL Adobe Experience Manager] as a Cloud Service 최신 릴리스 정보'
exl-id: a2d56721-502c-4f4e-9b72-5ca790df75c5
mini-toc-levels: 1
source-git-commit: f947a328897387d37e2092580e6992f14a344eb2
workflow-type: tm+mt
source-wordcount: '956'
ht-degree: 21%

---


# [!DNL Adobe Experience Manager] as a Cloud Service 최신 릴리스 정보 {#release-notes}

다음 섹션에서는 [!DNL Experience Manager] as a Cloud Service의 최신 버전 일반 릴리스 정보에 대해 간략히 소개합니다.

>[!NOTE]
>
>여기에서 2020, 2021 버전 등 이전 버전의 릴리스 정보로 이동할 수 있습니다.

>[!NOTE]
>
>릴리스와 직접적으로 관련되지 않는 설명서 업데이트의 세부 정보는 [설명서 업데이트](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html)를 참조하십시오.

## 릴리스 날짜 {#release-date}

의 릴리스 날짜 [!DNL Adobe Experience Manager] 로서의 [!DNL Cloud Service] 현재 릴리스(2022.7.0)는 2022년 8월 8일입니다.

다음 릴리스(2022.8.0)는 2022년 8월 25일에 예정되어 있습니다.

## 릴리스 비디오 {#release-video}

2022.7.0 릴리스에 추가된 기능에 대한 요약을 보려면 2022년 7월 릴리스 개요 비디오를 보십시오.

>[!VIDEO](https://video.tv.adobe.com/v/345409/?quality=12)

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### [!DNL Sites]의 새로운 기능 {#sites-features}

* 다음 [컨텐츠 조각 콘솔](/help/sites-cloud/administering/content-fragments/content-fragments-console.md) 이제에서 지원 [키보드 단축키](/help/sites-cloud/administering/content-fragments/content-fragments-console-keyboard-shortcuts.md).

* AEM as Cloud Service [웹에 최적화된 이미지 제공](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/web-optimized-image-delivery.html) 를 사용하면 WebP와 같은 형식을 제공하여 페이지 속도를 크게 향상시킬 수 있습니다. 또한 이 새로운 서비스는 보다 유연한 이미지 크기 조정 및 변환 옵션을 제공합니다. 모든 버전의 [코어 이미지 구성 요소](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/components/image.html) 이 서비스를 활용하고 이미지 구성 요소의 정책에 있는 옵션을 클릭하여 이미지를 WebP로 제공할 수 있습니다.

* 이제 AEM 개인화 활동은 이전 오퍼를 대신하여 경험 조각을 활용할 수 있습니다. 이 기능:
   * AEM 컨텐츠가 이전 라이브러리 오퍼가 아닌 경험 조각 오퍼를 홍보하는 마이그레이션 경로를 활성화하여 향후 개인화에 맞게 적절히 스타일이 지정된 콘텐츠를 제공할 수 있습니다.
   * 콘텐츠 작성자가 실수로 자신의 사이트에서 스타일이 지정되지 않은 콘텐츠를 제공하지 않도록 합니다.
   * 모든 구성 요소의 타깃팅 모드를 편집 가능한 템플릿을 사용하는 경험 조각(JSON 및 HTML 유형 모두)으로 변환할 수 있습니다.

>[!NOTE]
>
>이미 이전 오퍼를 사용하고 있는 기존 개인화 활동은 계속 수행할 수 있지만 앞으로 권장되는 접근 방법이므로 새 개인화 활동을 경험 조각으로 만들어야 합니다.

## [!DNL Experience Manager Assets] 로서의 [!DNL Cloud Service] {#assets}

### [!DNL Assets] 프리릴리스 채널에서 사용할 수 있는 새로운 기능 {#prerelease-features-assets}

이제 Adobe Experience Manager Assets을에 구성할 수 있습니다. [MIME 유형에 따라 사용자가 업로드할 수 있는 자산 유형을 제한합니다](/help/assets/configure-asset-upload-restrictions.md).

![자산 업로드 제한](/help/assets/assets/asset-upload-restrictions.png)

## [!DNL Experience Manager Forms] 로서의 [!DNL Cloud Service] {#forms}

### [!DNL Forms]의 새로운 기능 {#forms-features}

* **[스크리블 서명에 대한 키보드 입력 지원](/help/forms/signing-forms-using-scribble.md)**: 적응형 Forms이 터치 장치에서 점점 더 많이 사용되고 있으며, 한 가지 일반적인 요구 사항은 서명을 지원하는 것입니다. 터치 장치에서 문서에 서명하는 것은 허용되는 양식 서명 방법이 되었다. 적응형 Forms에는 스크리블 서명 및 Adobe Sign에 대한 기본 지원 기능이 있습니다. 이제 이미 지원되는 다른 옵션과 함께 키보드를 사용하여 적응형 양식에서 스크리블 서명을 사용할 수도 있습니다. 또한 접근성 준수를 강화하는 데에도 도움이 됩니다.

![iphone에서 스크리블 서명을 위한 키보드 입력 지원](/help/release-notes/assets/scribble-keyboard-mobile.png)

* **로컬 언어로 적응형 Forms 마법사 사용**: 선택한 언어로 마법사를 사용할 수 있습니다. 이제 Adobe Experience Manager에서 지원하는 모든 언어를 지원합니다.

### [!DNL Forms] 프리릴리스 채널에서 사용할 수 있는 새로운 기능 {#prerelease-features-forms}

<!-- 

* **[Launch Adaptive Form creation wizard from embed form component](/help/forms/using/embed-adaptive-form-aem-sites.md)**: You can now launch Adaptive Form creation wizard from embed form component. It helps improve content and forms authoring workflows for Sites and Forms practitioners trying to add enrollment experiences to a web page. 

![Keyboard input support for Scribble signatures on iphone](/help/release-notes/assets/froms-container.png) 

-->

* **[DDX 호출 - AEM 워크플로우 단계](/help/forms/aem-forms-workflow-step-reference.md#invokeddx)**: DDX(Document Description XML)는 요소가 문서 빌딩 블록을 나타내는 선언적 마크업 언어입니다. 이러한 빌딩 블록에는 PDF 및 XDP 문서와 주석, 책갈피 및 스타일이 지정된 텍스트와 같은 기타 요소가 포함됩니다. DDX 문서는 문서의 템플릿이며 결과 문서에 표시되어야 하는 소스 문서의 원하는 특성을 설명합니다. 하나의 DDX를 다양한 소스 문서와 함께 사용할 수 있습니다. 호출 단계 및 AEM Workflow를 사용하여 문서 조립, Acrobat 및 XFA Forms 작성 및 수정, 및 [DDX 참조](https://helpx.adobe.com/content/dam/help/en/experience-manager/forms-cloud-service/ddxRef.pdf) 설명서.

* **[PDF/A로 변환 - AEM 워크플로우 단계](/help/forms/aem-forms-workflow-step-reference.md##convert-pdfa)**: PDF/A는 문서의 컨텐츠를 장기 보존하기 위한 보관 형식이며 모든 글꼴이 포함되고 파일의 압축이 해제됩니다. 이제 AEM Workflow에서 PDF/A로 변환 단계를 사용하여 문서 또는 파일을 어떤 형식의 형식으로든 PDF/A 형식으로 변환할 수 있습니다.


## CIF 추가 기능 {#cloud-services-cif}

### 새로운 기능 {#what-is-new-cif}

* 제품 카탈로그 강화는 이제 AEM 페이지를 지원합니다. 이렇게 하면 작성자가 페이지 - 제품 연결을 관리할 수 있습니다.

* 다양한 CIF 코어 구성 요소 개선 사항

### 버그 수정 {#bug-fixes-cif}

* 클라이언트측 가격 가져오기에 로그인 토큰 추가

* 데이터 계층에 잘못된 페이지 구성 요소가 있습니다.

## [!DNL Experience Manager] as a [!DNL Cloud Service] Foundation {#foundation}

### 새로운 기능 {#what-is-new-foundation}

* 다음 [저장소 브라우저](/help/implementing/developing/tools/repository-browser.md) 이제 경로 입력 필드가 있으므로 저장소 계층 구조의 특정 폴더로 바로 이동할 수 있습니다
* Sling 컨텐츠 배포(SCD)는 이제 게시되지 않은 컨텐츠를 무효화하기 위해 명시적 &quot;무효화&quot; 작업을 지원합니다. 자세한 내용은 [AEM as a Cloud Service 캐싱](/help/implementing/dispatcher/caching.md#explicit-invalidation) 페이지를 참조하십시오.
* 이제 AEM as a Cloud Service에서 mod_macro를 사용할 수 있습니다. 을(를) 참조하십시오. [이 표](/help/implementing/dispatcher/disp-overview.md) 지원되는 Apache 모듈 목록입니다.

### AEM as a Cloud Service SDK Dispatcher 도구 개선 사항 {#dispatcher-tools-enhancements}

* Apache는 `update_sdk.sh` 스크립트. apache 및 dispatcher 구성에 대한 후속 변경 사항을 자동으로 로드 및 확인하므로 개발자 속도가 향상됩니다. 디스패처 도구 유연한 모드에서만 지원됩니다. 또한, [Apache 및 Dispatcher 구성 디버깅](/help/implementing/dispatcher/validation-debug.md#automatic-loading) 자동 로드 및 유효성 검사에 대한 자세한 내용은 를 참조하십시오.
* 로컬 Apache/Dispatcher 구성은 클라우드 환경의 변경 사항을 보다 밀접하게 추적하여 두 환경 간의 패리티를 증가시킵니다.

### [!DNL Experience Manager] 프리릴리스 채널에서 사용할 수 있는 새로운 기능 {#prerelease-features-foundation}

* 이제 AEM as a Cloud Service가 통합 쉘과 통합되어 사용자 경험을 개선하고 다른 모든 Experience Cloud 애플리케이션과 통합합니다. 자세한 내용은 [통합 쉘의 AEM as a Cloud Service](/help/overview/aem-cloud-service-on-unified-shell.md)를 참조하십시오.

## Adobe Learning Manager 커넥터 {#learn-manage}

* 새로운 Adobe Learning Manager에는 Adobe Experience Manager Sites, Marketo Engage 및 Adobe Commerce에 대한 커넥터가 있습니다. 자세한 내용은 다음을 참조하십시오. [Adobe Learning Manager 사용 안내서](https://helpx.adobe.com/learning-manager/user-guide.html).


## Cloud Manager {#cloud-manager}

[여기](/help/implementing/cloud-manager/release-notes-cloud-manager/release-notes-cm-current.md)에서 Cloud Manager 월별 릴리스의 전체 목록을 찾을 수 있습니다.

## 마이그레이션 도구 {#migration-tools}

[여기](/help/journey-migration/release-notes/release-notes-migration-tools-current.md)에서 마이그레이션 도구의 전체 목록을 찾을 수 있습니다.
