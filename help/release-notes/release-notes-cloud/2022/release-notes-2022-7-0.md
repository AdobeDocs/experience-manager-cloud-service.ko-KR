---
title: ' [!DNL Adobe Experience Manager] as a Cloud Service의 2022.7.0 릴리스 정보입니다.'
description: ' [!DNL Adobe Experience Manager] as a Cloud Service의 2022.7.0 릴리스 정보입니다.'
exl-id: b339ab48-e836-4589-a573-9c50917b9280
source-git-commit: 599f924465552b2ef43827da8e139c239e47baed
workflow-type: tm+mt
source-wordcount: '955'
ht-degree: 98%

---

# [!DNL Adobe Experience Manager] as a Cloud Service 202278.0 릴리스 정보 {#release-notes}

다음 섹션에서는 의 2022.7.0 버전에 대한 기능 릴리스 노트를 간략하게 설명합니다 [!DNL Experience Manager] as a Cloud Service.

>[!NOTE]
>
>여기에서 2020, 2021 버전 등 이전 버전의 릴리스 정보로 이동할 수 있습니다.

>[!NOTE]
>
>릴리스와 직접적으로 관련되지 않는 설명서 업데이트의 세부 정보는 [설명서 업데이트](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html)를 참조하십시오.

## 릴리스 일자 {#release-date}

[!DNL Adobe Experience Manager] as a [!DNL Cloud Service]의 현재 릴리스(2022.7.0) 날짜는 2022년 8월 8일입니다.

다음 릴리스(2022.8.0)는 2022년 9월 1일에 예정되어 있습니다.

## 릴리스 비디오 {#release-video}

2022년 7월 릴리스 개요 비디오를 통해 2022.7.0 릴리스에 추가된 기능에 대한 간단한 요약을 살펴보십시오.

>[!VIDEO](https://video.tv.adobe.com/v/345409/?quality=12)

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### [!DNL Sites]의 새로운 기능 {#sites-features}

* [콘텐츠 조각 콘솔](/help/sites-cloud/administering/content-fragments/content-fragments-console.md)은 이제 [키보드 단축키](/help/sites-cloud/administering/content-fragments/content-fragments-console-keyboard-shortcuts.md)를 지원합니다.

* AEM as Cloud Service의 [웹 최적화 이미지 게재](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/web-optimized-image-delivery.html)는 WebP와 같은 형식을 제공함으로써 페이지 속도를 향상시킬 수 있습니다. 또한 이 새로운 서비스는 보다 유연한 이미지 크기 조정 및 변환 옵션을 제공합니다. 모든 버전의 [핵심 이미지 구성 요소](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/components/image.html)에서, 이 서비스를 사용하여 이미지 구성 요소 정책에서 옵션을 클릭하는 것으로 WebP로 이미지를 게재할 수 있습니다.

* AEM 개인화 활동에서 이제 레거시 오퍼 대신 경험 조각을 사용할 수 있습니다. 이 기능은 다음의 특징을 포함합니다.
   * 레거시 라이브러리가 아닌 AEM 콘텐츠가 경험 조각 오퍼를 촉진하는 마이그레이션 경로를 통해 향후 규모에 맞는 개인화에 적합한 스타일의 콘텐츠를 제공할 수 있습니다.
   * 콘텐츠 작성자가 사이트에서 스타일이 지정되지 않은 콘텐츠를 실수로 제공하는 것을 방지합니다.
   * 모든 구성 요소의 타겟팅 모드를 편집 가능한 템플릿을 사용하는 경험 조각(JSON 및 HTML 유형 모두)으로 변환할 수 있습니다.

>[!NOTE]
>
>이미 레거시 오퍼를 사용 중인 기존 개인화 활동은 계속해서 레거시 오퍼를 사용할 수 있으나 새 개인화 활동의 경우 경험 조각이 앞으로의 권장 접근법이기 때문에 경험 조각으로 생성해야 합니다.

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### [!DNL Assets] 프리릴리스 채널에서 사용할 수 있는 새로운 기능 {#prerelease-features-assets}

이제 [사용자가 MIME 유형에 따라 업로드할 수 있는 에셋 유형을 제한](/help/assets/configure-asset-upload-restrictions.md)하도록 Adobe Experience Manager Assets를 구성할 수 있습니다.

![에셋 업로드 제한 사항](/help/assets/assets/asset-upload-restrictions.png)

## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### [!DNL Forms]의 새로운 기능 {#forms-features}

* **[스크리블 서명을 위한 키보드 입력 지원](/help/forms/signing-forms-using-scribble.md)**: 적응형 양식은 터치 디바이스에서 점점 더 많이 사용되고 있으며, 한 가지 일반적인 요구사항은 서명을 지원하는 것입니다. 터치 디바이스에서 문서에 서명하는 것은 양식 서명에서 허용되는 방법이 되었습니다. 적응형 양식은 이러한 사용 사례에 대해 스크리블 서명 및 Adobe Sign을 기본 지원합니다. 이제 이미 지원되는 다른 옵션과 더불어 키보드를 사용하여 적응형 양식에 스크리블 서명을 할 수도 있습니다. 또한 접근성 규정 준수를 개선하는 데도 도움이 됩니다.

![iphone에서 스크리블 서명을 위한 키보드 입력 지원](/help/release-notes/assets/scribble-keyboard-mobile.png)

* **로컬 언어로 적응형 양식 마법사 사용**&quot; 선택한 언어로 마법사를 사용할 수 있습니다. 이제 Adobe Experience Manager에서 지원하는 모든 언어를 지원합니다.

### [!DNL Forms] 프리릴리스 채널에서 사용할 수 있는 새로운 기능 {#prerelease-features-forms}

<!-- 

* **[Launch Adaptive Form creation wizard from embed form component](/help/forms/using/embed-adaptive-form-aem-sites.md)**: You can now launch Adaptive Form creation wizard from embed form component. It helps improve content and forms authoring workflows for Sites and Forms practitioners trying to add enrollment experiences to a web page. 

![Keyboard input support for Scribble signatures on iphone](/help/release-notes/assets/froms-container.png) 

-->

* **[DDX 호출 - AEM 워크플로 단계](/help/forms/aem-forms-workflow-step-reference.md#invokeddx)**: DDX(Document Description XML)는 문서의 구성 요소를 나타내는 선언적 마크업 언어입니다. 이러한 구성 요소에는 PDF 및 XDP 문서는 물론 댓글, 책갈피 및 스타일이 지정된 텍스트와 같은 기타 요소가 포함됩니다. DDX 문서는 문서용 템플릿이며 결과 문서에 나타나야 하는 원본 문서의 원하는 특성을 설명합니다. 단일 DDX를 다양한 원본 문서와 함께 사용할 수 있습니다. AEM 워크플로 호출 단계를 사용하여 문서 어셈블/디스어셈블, Acrobat 및 XFA 양식 작성 및 수정, [DDX 참조](https://helpx.adobe.com/content/dam/help/en/experience-manager/forms-cloud-service/ddxRef.pdf) 설명서에 설명된 기타 작업과 같은 다양한 작업을 수행할 수 있습니다.

* **[PDF/A로 변환 - AEM 워크플로 단계](/help/forms/aem-forms-workflow-step-reference.md##convert-pdfa)**: PDF/A는 문서 내용을 장기간 보존하기 위한 보관 형식이며, 모든 글꼴이 임베드되어 있고 파일이 압축 해제되어 있습니다. 이제 AEM 워크플로의 PDF/A로 변환 단계를 사용하여 모든 형식의 문서 또는 파일을 PDF/A 형식으로 변환할 수 있습니다.


## CIF 추가 기능 {#cloud-services-cif}

### 새로운 기능 {#what-is-new-cif}

* 제품 카탈로그 보강으로 이제 AEM 페이지가 지원됩니다. 이에 따라 제작자가 페이지-제품 연계를 관리할 수 있습니다.

* 다양한 CIF 핵심 구성 요소 개선

### 버그 수정 {#bug-fixes-cif}

* 클라이언트측 가격 가져오기에 로그인 토큰 추가

* 데이터레이어 내 잘못된 페이지 구성 요소

## [!DNL Experience Manager] as a [!DNL Cloud Service] Foundation {#foundation}

### 새로운 기능 {#what-is-new-foundation}

* 이제 [저장소 브라우저](/help/implementing/developing/tools/repository-browser.md)에 경로 입력 필드가 있으므로 저장소 계층의 특정 폴더로 직접 이동할 수 있습니다.
* Sling 콘텐츠 배포(SCD)는 이제 해당 콘텐츠가 게시되지 않은 콘텐츠를 무효화하기 위해 명시적인 &quot;무효화&quot; 작업을 지원합니다. 자세한 내용은 [AEM as a Cloud Service의 캐싱](/help/implementing/dispatcher/caching.md#explicit-invalidation)을 참조하십시오.
* 이제 AEM as a Cloud Service에서 mod_macro를 이용할 수 있습니다. 지원되는 Apache 모듈의 목록은 [이 표](/help/implementing/dispatcher/disp-overview.md)를 참조하십시오.

### AEM as a Cloud Service SDK Dispatcher 도구 개선 사항 {#dispatcher-tools-enhancements}

* Apache 및 Dispatcher 구성에 대한 모든 변경 사항을 자동으로 로드하고 유효성을 검사하는 `docker_run_hot_reload.sh` 스크립트로 Apache를 시작할 수 있으므로 개발자 속도가 향상됩니다. Dispatcher 도구 유연한 모드에서만 지원됩니다. 자동 다시 로드 및 유효성 검사에 대한 자세한 내용은 [Apache 및 Dispatcher 구성 디버깅](/help/implementing/dispatcher/validation-debug.md#automatic-reloading)을 참조하십시오.
* 로컬 Apache/Dispatcher 구성이 클라우드 환경의 변화를 더욱 면밀히 추적하여 두 환경 간의 유사성을 증가시킵니다.

### [!DNL Experience Manager] 프리릴리스 채널에서 사용할 수 있는 새로운 기능 {#prerelease-features-foundation}

* 이제 AEM as a Cloud Service가 통합 쉘과 통합되어 사용자 경험을 개선하고 다른 모든 Experience Cloud 애플리케이션과 통합합니다. 자세한 내용은 [통합 쉘의 AEM as a Cloud Service](/help/overview/aem-cloud-service-on-unified-shell.md)를 참조하십시오.

## Adobe Learning Manager 커넥터 {#learn-manage}

* 새로운 Adobe Learning Manager에는 Adobe Experience Manager Sites, Marketo Engage 및 Adobe Commerce에 대한 커넥터가 있습니다. 자세한 내용은 [Adobe Learning Manager 사용 안내서](https://helpx.adobe.com/kr/learning-manager/user-guide.html)를 참조하십시오.

## Cloud Manager {#cloud-manager}

[여기](/help/implementing/cloud-manager/release-notes/current.md)에서 Cloud Manager 월별 릴리스의 전체 목록을 찾을 수 있습니다.

## 마이그레이션 도구 {#migration-tools}

[여기](/help/journey-migration/release-notes/release-notes-migration-tools-current.md)에서 마이그레이션 도구의 전체 목록을 찾을 수 있습니다.
