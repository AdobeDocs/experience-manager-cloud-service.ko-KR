---
title: ' [!DNL Adobe Experience Manager] as a Cloud Service의 2023.8.0 릴리스 정보입니다.'
description: ' [!DNL Adobe Experience Manager] as a Cloud Service의 2023.8.0 릴리스 정보입니다.'
exl-id: a0ffa6cf-64ae-468c-93f4-ac6805ef907e
feature: Release Information
role: Admin
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '1691'
ht-degree: 100%

---

# [!DNL Adobe Experience Manager] as a Cloud Service 2023.8.0 릴리스 정보 {#release-notes}

다음 섹션에서는 [!DNL Experience Manager] as a Cloud Service의 2023.8.0 버전 기능 릴리스 정보에 대해 간략히 소개합니다.

## 릴리스 일자 {#release-date}

[!DNL Adobe Experience Manager] as a [!DNL Cloud Service] 현재 기능 릴리스(2023.8.0)의 릴리스 일자는 2023년 8월 31일입니다. 다음 기능 릴리스(2023.9.0)는 2023년 9월 28일에 예정되어 있습니다.

## 릴리스 비디오 {#release-video}

2023년 8월 릴리스 개요 비디오를 통해 2023.8.0 릴리스에 추가된 기능에 대한 간단한 요약을 살펴보십시오.

>[!VIDEO](https://video.tv.adobe.com/v/3423535/?quality=12)

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### [!DNL Experience Manager Sites]의 새로운 기능 {#sites-features}

* 이제 사용자는 [콘텐츠 조각 콘솔](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/sites/administering/content-fragments/content-fragments-console.html)을 사용하여 콘텐츠 조각에 메타데이터로 적용된 태그를 보고 검색할 수 있습니다. 사용자가 더 이상 이 기능을 사용하기 위해 자산 UI로 전환할 필요가 없으므로 컨텍스트 전환이 줄어들고 효율성이 향상됩니다.

  ![콘텐츠 조각 콘솔에서 태그 지정](/help/assets/content-fragments-console-tags.png)
* 이제 AEM as a Cloud Service에서 새 콘텐츠 조각 편집기를 사용할 수 있습니다. 이를 통해 콘텐츠 작성자는 콘텐츠를 편집하는 동안 작성 작업을 간소화하고 다른 앱 간 전환의 필요성을 줄여 생산성을 높일 수 있습니다.
  ![새 콘텐츠 조각 편집기](/help/release-notes/assets/newCFEditor.png)

새 콘텐츠 조각 편집기는 원본 편집기에서 사용할 수 없는 다음과 같은 이점을 제공합니다.
* 자동 저장을 통해 작성 효율성을 개선하고 실수로 편집된 내용이 손실되는 일이 없도록 합니다.
* 구조 트리를 사용하는 콘텐츠 조각 및 참조의 계층적 보기를 통해 심층적으로 구조화된 조각 내에서 빠르게 탐색합니다.
  ![콘텐츠 조각 편집기의 구조 트리](/help/release-notes/assets/newCFEditor_StructureTree.png)

* 먼저 자산 DAM에 업로드하지 않고 자산을 콘텐츠 참조로 인라인 업로드
* 작성자가 프론트엔드 앱에서 콘텐츠의 모양과 느낌을 시각화할 수 있도록 콘텐츠 조각에서 제공하는 렌더링된 경험에 대한 애드혹 미리보기
* 클릭 한 번으로 편집기에서 콘텐츠 조각 게시 및 게시 취소
* 콘텐츠 조각을 편집하는 동안 언어 사본 조회 및 언어 사본으로 이동
  ![콘텐츠 조각 편집기의 언어 사본](/help/release-notes/assets/newCFEditor_LanguageCopies.PNG)

* 콘텐츠 조각의 타임라인을 추적할 수 있는 버전 보기

  ![콘텐츠 조각 편집기의 버전](/help/release-notes/assets/newCFEditor_Versionhistory.PNG)

* 작성자가 편집 내용이 미치는 영향력을 파악할 수 있도록 상위 참조 보기

  ![콘텐츠 조각 편집기의 상위 참조](/help/release-notes/assets/newCFEditor_Parentreferences.PNG)

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### Assets 보기의 새로운 기능 {#assets-view-features}

<!--

**Assign metadata form to a folder**

You can now assign metadata form to a specific folder within your Assets Essentials deployment. All assets in the folder, including assets in the sub-folders, then display properties defined in the assigned metadata form.

![assign metadata form to a folder](/help/release-notes/assets/assign-to-folder.png)

-->

* **데이터 소스에서 자산 일괄 가져오기**: 이제 관리자는 데이터 소스에서 AEM Assets로 [수많은 자산을 가져올 수](/help/assets/bulk-import-assets-view.md) 있습니다. 관리자는 더 이상 개별 자산 또는 폴더를 AEM Assets에 업로드할 필요가 없습니다. 일괄 가져오기에 지원되는 데이터 소스에는 Azure, AWS, Google Cloud 및 Dropbox가 포함됩니다.

  ![데이터 소스에서 자산 일괄 가져오기](/help/release-notes/assets/bulk-import.png)

* **Adobe Express에서 제공하는 이미지 편집 도구**: AEM Assets 내에서 바로 사용할 수 있는 [Adobe Express 기반의 쉽고 직관적인 이미지 편집 도구](/help/assets/edit-images-assets-view.md)를 사용하면 콘텐츠 재사용률과 콘텐츠 속도를 높일 수 있습니다.

  ![Adobe Express를 사용하여 이미지 편집](/help/release-notes/assets/edit-adobe-express.png)

* **내 작업 영역 바로 가기 항목을 고정하면서 유연성 유지**: 원하는 경우 [내 작업 영역의 바로 가기 섹션](/help/assets/my-workspace-assets-view.md)에 표시되도록 전체 조직 또는 그룹 목록에 맞는 항목을 선택하고 고정할 수 있는 기능입니다.

  ![그룹에 맞는 항목 고정](/help/release-notes/assets/pin-items-for-groups.png)

### 관리자 보기의 새로운 기능 {#admin-view-features}

**검색 개선 사항**

* 관리자는 검색을 수행할 때 표시되는 [자산의 배치 크기를 구성](/help/assets/search-assets.md#configure-asset-batch-size)할 수 있습니다. 아래로 스크롤하여 결과를 로드하는 경우 자산 검색 결과는 구성된 여러 배치 크기 번호로 표시됩니다. 200, 500, 1,000개 자산의 사용 가능한 배치 크기 중에서 선택할 수 있습니다. 낮은 배치 크기 번호를 설정하면 검색 응답 시간이 빨라집니다.

  ![자산 배치 크기 구성](/help/release-notes/assets/assets-batch-size-configuration.png)

* 이제 Experience Manager Assets에 `damAssetLucene` 색인의 새로운 버전 9가 포함됩니다. `damAssetLucene-9` Oak 쿼리 패싯 계산의 동작을 [로 변경하여 더 이상 기본 검색 색인에서 반환된 패싯 수](/help/assets/search-assets.md)에 대한 액세스 제어를 평가하지 않도록 합니다. 이로써 색 응답 시간이 빨라집니다.

### [!DNL Experience Manager Assets]에서 사용할 수 있는 프리릴리스 기능 {#prerelease-features-assets}

* **Dynamic Media**: [Dynamic Media로 비디오의 다중 캡션 및 다중 오디오 트랙 지원](/help/assets/dynamic-media/video.md#about-msma) — 이제 기본 비디오에 여러 개의 캡션과 오디오 트랙을 손쉽게 추가할 수 있습니다. 즉, 이러한 기능을 통해 글로벌 대상자는 비디오에 액세스할 수 있습니다. 여러 언어로 글로벌 대상자에게 게시된 하나의 기본 비디오를 사용자 정의하고 지역별 액세스 가능성 가이드라인을 준수할 수 있습니다. 작성자는 사용자 인터페이스의 단일 탭에서 캡션 및 오디오 트랙을 관리할 수도 있습니다.

  ![선택한 비디오 자산의 속성 페이지에 있는 캡션 및 오디오 트랙 탭입니다.](/help/release-notes/assets/msma-aem-cs.png)*선택한 비디오 자산의 속성 페이지에 있는 캡션 및 오디오 트랙 탭입니다.*

* **자산**: Experience Manager에서 관리하는 ZIP 아카이브를 선택하고, 다운로드하지 않고도 [Experience Manager로 직접 파일을 추출하는](/help/assets/manage-digital-assets.md#extract-zip-archives) 기능.

  ![그룹에 맞는 항목 고정](/help/release-notes/assets/extract-archive.png)


## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### [!DNL Forms] 프리릴리스에서 사용 가능한 새로운 기능 {#new-features-available-in-forms-channel}

* [**Google reCAPTCHA 엔터프라이즈 지원**](/help/forms/captcha-adaptive-forms.md): 적응형 양식에서 Google reCAPTCHA Enterprise를 사용해 사기 행위 및 스팸 방지 기능을 강화하여 보다 안전한 사용자 환경을 제공합니다. 고급 위험 분석 및 원활한 통합을 통해 실제 사용자가 양식을 쉽게 제출할 수 있는 동시에 봇이 효과적으로 차단됩니다.


### [!DNL Forms]에서 사용할 수 있는 프리릴리스 기능 {#pre-release-features-available-in-forms-channel}

* **양식용 Experience Cloud 설정 자동화를 사용하는 Adobe Analytics**: 이제 버튼 클릭 몇 번이면 Experience Cloud 설정 자동화를 사용하여 Adobe Analytics를 활성화할 수 있습니다. 이를 통해 AEM Forms as a Cloud Service를 Experience Platform 태그 및 Adobe Analytics와 연결하여 게시된 양식에 대한 성능 지표를 캡처하고 추적할 수 있습니다.

* **적응형 양식용 Adobe Analytics 보고서 템플릿**: 이제 Forms as a Cloud Service는 Adobe Analytics 보고서 OOTB를 제공합니다. 이렇게 하면 양식의 성능을 손쉽게 이해할 수 있습니다. 양식 수준 지표를 통해 렌디션, 방문자, 제출, 평균 채우기 시간 등 여러 주요 성과 지표(KPI)에서 양식이 어떻게 수행되는지에 대한 인사이트를 얻습니다. 사용자 행동 및 피드백을 추적하여 혼동을 주는 양식의 영역을 식별하고 양식의 디자인 및 기능을 개선할 수 있습니다.

  ![적응형 사용자 참여 Adobe Analytics 보고서](/help/forms/assets/forms-analytics-report.png)

* **[핵심 구성 요소 기반 적응형 양식의 양식 조각](/help/forms/adaptive-form-fragments-core-components.md)**: 양식 조각으로 양식 작성 경험을 높이면서 중복을 제거하고, 디지털 인벤토리를 최적화하고, 공동 작업을 개선합니다. 이러한 재사용 가능한 구성 요소는 여러 양식에 원활하게 통합되어 일관성 있게 전문가 수준의 양식 작성을 간소화합니다. 양식 조각의 “한번 변경하여 전체 반영” 기능을 통해 재사용성, 표준화와 브랜드 일관성을 보장합니다. 한 위치에서의 업데이트가 이러한 조각을 활용하는 모든 양식에 자동으로 전파되므로 유지 관리 가능성과 효율성이 개선됩니다.

* **[개선된 Adobe Sign 워크플로 단계](/help/forms/aem-forms-workflow-step-reference.md#sign-document-step-sign-document-step)**: Adobe Sign 워크플로 단계는 다음을 포함하도록 개선되었습니다.
   * **Adobe Sign의 정부 ID 기반 인증**: Adobe Acrobat Sign의 정부 ID 기반 인증은 사용자가 정부에서 발급한 ID(운전면허증, 주민등록증, 여권)를 사용하여 자신의 ID를 인증할 수 있도록 추가 확인 계층을 제공합니다. 신뢰할 수 있는 식별 문서를 사용하여 이 개선된 기능은 서명 프로세스에 신뢰도를 추가하여 보안, 규정 준수 및 사용자 유효성 검사 강화에 필요한 시나리오에 적합합니다.

   * **Adobe Sign 문서의 감사 추적**: 감사 추적 기능을 사용하여 Adobe Sign 문서의 수명 주기에 대한 세부 인사이트를 얻을 수 있습니다. 감사 추적을 사용하여 이제 문서와 관련된 모든 작업과 상호 작용에 대한 포괄적인 기록을 유지 관리할 수 있습니다. 여기에는 각 이벤트의 타임스탬프와 함께 문서를 조회하고, 편집하거나 서명한 사람 등과 같은 세부 정보가 포함됩니다. 이러한 개선된 기능은 규정 준수를 유지하고, 분쟁을 해결하고, 디지털 계약의 무결성을 보장하는 데 중요합니다.

   * **계약 수신자의 새 역할이 서명자 이상으로 확장**: Adobe Acrobat Sign은 계약 수신자의 역할을 서명자 이상으로 확장하여 워크플로 요구 사항에 보다 잘 부합하도록 할 수 있습니다. 활성화되면 계약의 각 수신자는 자신의 역할을 개별 구성할 수 있으며 서명자는 기본 역할입니다.

* **[Document Assurance API(커뮤니케이션 API의 일부)로 문서 보호](/help/forms/aem-forms-cloud-service-communications-introduction.md#document-assurance-doc-assurance)**: Document Assurance API를 사용하여 문서에 서명하고 암호화하여 민감한 정보를 보호할 수 있습니다. 문서의 콘텐츠는 암호화를 통해 읽을 수 없는 포맷으로 변환되어 권한이 있는 사용자만 액세스할 수 있습니다. 이 보호 계층이 강화되면 중요 데이터를 승인되지 않은 사용자로부터 보호할 뿐만 아니라 고객들이 안심할 수 있습니다. 서명 API를 통해 조직에서 배포하고 수신하는 Adobe PDF 문서의 보안 및 개인정보를 보호할 수 있습니다. 이 서비스는 의도한 수신자만 문서를 변경할 수 있도록 디지털 서명과 인증을 사용합니다.

* **커뮤니케이션 API의 페이지 카운트 지원**: 이제 커뮤니케이션 API를 통해 문서를 검색하는 동시에 문서 내 포함된 페이지의 수에 대한 중요한 정보를 받을 수도 있습니다.

* **[규칙 편집기의 사용자 정의 오류 핸들러로 오류 처리](/help/forms/add-custom-error-handler-adaptive-forms-core-components.md)**: 이제 외부 서비스에서 반환되는 오류에 따라 사용자 정의 함수를 호출하여 맞춤형 응답을 최종 사용자에게 제공할 수 있습니다. 예를 들어 특정 오류 코드의 백엔드에서 사용자 정의 워크플로를 호출하거나 서비스가 중단되었음을 고객에게 알려 줄 수 있습니다.


### Headless 적응형 양식 얼리 어답터 프로그램 {#forms-early-adopter}

[Headless 적응형 양식](https://experienceleague.adobe.com/docs/experience-manager-headless-adaptive-forms/using/overview.html)을 사용하여 개발자가 기존의 그래픽 사용자 인터페이스가 아닌 API를 통해 액세스하고 상호 작용할 수 있는 대화형 양식을 만들고, 게시하고, 관리할 수 있습니다. Headless 적응형 양식은 다음에 도움이 됩니다.

* 선택한 프로그래밍 언어로 고품질 다중 채널 양식 작성
* 양식을 데스크탑 및 모바일 앱, 웹 사이트 및 채팅 애플리케이션에 기본적으로 통합
* 양식 애플리케이션과 함께 독점 UI 구성 요소 재사용
* Adobe Experience Manager Forms의 기능 사용

공식 이메일 ID에서 `aem-forms-headless@adobe.com`으로 이메일을 보내 얼리 어답터 프로그램에 참여할 수 있습니다.


## [!DNL Experience Manager] as a [!DNL Cloud Service] Foundation {#foundation}

### CDN 로그 {#cdn-logs}

Cloud Manager에서 CDN 로그를 다운로드합니다. 이는 캐시 적중률을 최적화하고 콘텐츠 게재 흐름의 가시성을 높이는 데 유용합니다. CDN 로그 포맷에 [대해 알아보기](/help/implementing/developing/introduction/logging.md#cdn-log). 이 기능은 9월 초부터 고객에게 점진적으로 제공될 예정입니다.

### CDN 및 WAF 규칙 얼리 어답터 프로그램 {#waf-early-adopter}

다음을 기준으로 CDN에서 트래픽을 필터링할 수 있습니다.

* 요청 헤더 및 속성(예: IP 주소)
* 악성 트래픽과 관련된 것으로 알려진 트래픽 패턴

기능을 사용해 보고 피드백을 공유하고 싶으십니까? 공식 이메일 ID로 **aemcs-waf-adopter@adobe.com**&#x200B;에 이메일을 보내 얼리 어답터 프로그램에 대해 자세히 알아보십시오. 인원이 한정되어 있습니다.

[여기](/help/security/traffic-filter-rules-including-waf.md)에 있는 문서에서 기능에 대해 자세히 알아보십시오.


## 유지 관리 릴리스 정보 {#maintenance}

[ 여기](/help/release-notes/maintenance/latest.md)에서 최신 유지 관리 릴리스 정보를 확인할 수 있습니다.

## Cloud Manager {#cloud-manager}

[여기](/help/implementing/cloud-manager/release-notes/current.md)에서 Cloud Manager 월별 릴리스의 전체 목록을 찾을 수 있습니다.

## 마이그레이션 도구 {#migration-tools}

[여기](/help/journey-migration/release-notes/release-notes-migration-tools-current.md)에서 마이그레이션 도구의 전체 목록을 찾을 수 있습니다.
